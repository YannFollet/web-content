---
id: use_ColPALI_with_milvus.md
summary: >-
  Neste caderno, referimo-nos a este tipo de representação multi-vetorial como
  "ColBERT embeddings" por uma questão de generalidade. No entanto, o modelo que
  está a ser utilizado é o modelo ColPALI. Vamos demonstrar como utilizar o
  Milvus para a recuperação multi-vetorial. Com base nisso, apresentaremos como
  utilizar o ColPALI para recuperar páginas com base numa determinada consulta.
title: Use ColPALI para recuperação multimodal com Milvus
---
<h1 id="Use-ColPALI-for-Multi-Modal-Retrieval-with-Milvus" class="common-anchor-header">Use ColPALI para recuperação multimodal com Milvus<button data-href="#Use-ColPALI-for-Multi-Modal-Retrieval-with-Milvus" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h1><p><a href="https://colab.research.google.com/github/milvus-io/bootcamp/blob/master/bootcamp/tutorials/quickstart/use_ColPALI_with_milvus.ipynb" target="_parent">
<img translate="no" src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>
<a href="https://github.com/milvus-io/bootcamp/blob/master/bootcamp/tutorials/quickstart/use_ColPALI_with_milvus.ipynb" target="_blank">
<img translate="no" src="https://img.shields.io/badge/View%20on%20GitHub-555555?style=flat&logo=github&logoColor=white" alt="GitHub Repository"/>
</a></p>
<p>Os modelos modernos de recuperação utilizam normalmente um único embedding para representar texto ou imagens. O ColBERT, no entanto, é um modelo neural que utiliza uma lista de embeddings para cada instância de dados e emprega uma operação "MaxSim" para calcular a semelhança entre dois textos. Para além dos dados textuais, as figuras, tabelas e diagramas também contêm informações ricas, que são frequentemente ignoradas na recuperação de informações baseada em texto.</p>
<p>$$ S_{q,d} := \sum_{i \in |E_q|} \max_{j \in |E_d|} E_{q_i} \cdot E_{d_j}^T $$ A função MaxSim compara uma consulta com um documento (aquilo em que está a pesquisar) observando os seus token embeddings. Para cada palavra na consulta, seleciona a palavra mais semelhante do documento (utilizando a semelhança de cosseno ou a distância L2 ao quadrado) e soma estas semelhanças máximas entre todas as palavras na consulta</p>
<p>O ColPALI é um método que combina a representação multi-vetorial do ColBERT com o PaliGemma (um modelo de linguagem multimodal de grande dimensão) para tirar partido das suas fortes capacidades de compreensão. Esta abordagem permite que uma página com texto e imagens seja representada utilizando uma incorporação multi-vetorial unificada. As incorporações dentro desta representação multi-vetorial podem capturar informações detalhadas, melhorando o desempenho da geração aumentada de recuperação (RAG) para dados multimodais.</p>
<p>Neste caderno, referimo-nos a este tipo de representação multi-vetorial como "ColBERT embeddings" por uma questão de generalidade. No entanto, o modelo real que está a ser utilizado é o <strong>modelo ColPALI</strong>. Vamos demonstrar como utilizar o Milvus para a recuperação multi-vetorial. Com base nisso, apresentaremos como utilizar o ColPALI para recuperar páginas com base numa determinada consulta.</p>
<h2 id="Preparation" class="common-anchor-header">Preparação<button data-href="#Preparation" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><pre><code translate="no" class="language-shell">$ pip install pdf2image
$ pip pymilvus
$ pip install colpali_engine
$ pip install tqdm
$ pip instal pillow
<button class="copy-code-btn"></button></code></pre>
<h2 id="Prepare-the-data" class="common-anchor-header">Preparar os dados<button data-href="#Prepare-the-data" class="anchor-icon" translate="no">
      <svg translate="no"
        aria-hidden="true"
        focusable="false"
        height="20"
        version="1.1"
        viewBox="0 0 16 16"
        width="16"
      >
        <path
          fill="#0092E4"
          fill-rule="evenodd"
          d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"
        ></path>
      </svg>
    </button></h2><p>Utilizaremos o PDF RAG como exemplo. Pode descarregar o documento <a href="https://arxiv.org/pdf/2004.12832">ColBERT</a> e colocá-lo em <code translate="no">./pdf</code>. O ColPALI não processa diretamente o texto; em vez disso, toda a página é rasterizada numa imagem. O modelo ColPALI é excelente para compreender a informação textual contida nestas imagens. Portanto, converteremos cada página do PDF em uma imagem para processamento.</p>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">from</span> pdf2image <span class="hljs-keyword">import</span> convert_from_path

pdf_path = <span class="hljs-string">&quot;pdfs/2004.12832v2.pdf&quot;</span>
images = convert_from_path(pdf_path)

<span class="hljs-keyword">for</span> i, image <span class="hljs-keyword">in</span> <span class="hljs-built_in">enumerate</span>(images):
    image.save(<span class="hljs-string">f&quot;pages/page_<span class="hljs-subst">{i + <span class="hljs-number">1</span>}</span>.png&quot;</span>, <span class="hljs-string">&quot;PNG&quot;</span>)
<button class="copy-code-btn"></button></code></pre>
<p>De seguida, vamos inicializar uma base de dados utilizando o Milvus Lite. Pode mudar facilmente para uma instância completa do Milvus definindo o uri para o endereço apropriado onde o seu serviço Milvus está alojado.</p>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">from</span> pymilvus <span class="hljs-keyword">import</span> <span class="hljs-title class_">MilvusClient</span>, <span class="hljs-title class_">DataType</span>
<span class="hljs-keyword">import</span> numpy <span class="hljs-keyword">as</span> np
<span class="hljs-keyword">import</span> concurrent.<span class="hljs-property">futures</span>

client = <span class="hljs-title class_">MilvusClient</span>(uri=<span class="hljs-string">&quot;milvus.db&quot;</span>)
<button class="copy-code-btn"></button></code></pre>
<div class="alert note">
<ul>
<li>Se apenas necessitar de uma base de dados vetorial local para dados de pequena escala ou prototipagem, definir o uri como um ficheiro local, por exemplo<code translate="no">./milvus.db</code>, é o método mais conveniente, uma vez que utiliza automaticamente <a href="https://milvus.io/docs/milvus_lite.md">o Milvus Lite</a> para armazenar todos os dados neste ficheiro.</li>
<li>Se tiver uma grande escala de dados, digamos mais de um milhão de vectores, pode configurar um servidor Milvus mais eficiente em <a href="https://milvus.io/docs/quickstart.md">Docker ou Kubernetes</a>. Nesta configuração, use o endereço e a porta do servidor como seu uri, por exemplo,<code translate="no">http://localhost:19530</code>. Se ativar a funcionalidade de autenticação no Milvus, utilize "&lt;your_username&gt;:&lt;your_password&gt;" como token, caso contrário não defina o token.</li>
<li>Se utilizar <a href="https://zilliz.com/cloud">o Zilliz Cloud</a>, o serviço de nuvem totalmente gerido para o Milvus, ajuste os endereços <code translate="no">uri</code> e <code translate="no">token</code>, que correspondem ao <a href="https://docs.zilliz.com/docs/on-zilliz-cloud-console#cluster-details">Public Endpoint e</a> à <a href="https://docs.zilliz.com/docs/on-zilliz-cloud-console#cluster-details">chave API</a> no Zilliz Cloud.</li>
</ul>
</div>
<p>Vamos definir uma classe MilvusColbertRetriever para envolver o cliente Milvus na recuperação de dados multi-vectoriais. A implementação aplaina os embeddings ColBERT e insere-os numa coleção, em que cada linha representa um embedding individual da lista de embeddings ColBERT. Também regista o doc_id e o seq_id para rastrear a origem de cada embedding.</p>
<p>Ao pesquisar com uma lista de inserções ColBERT, serão efectuadas várias pesquisas - uma para cada inserção ColBERT. Os doc_ids recuperados serão então deduplicados. Será efectuado um processo de nova classificação, em que as incorporações completas para cada doc_id são obtidas e a pontuação MaxSim é calculada para produzir os resultados finais classificados.</p>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">class</span> <span class="hljs-title class_">MilvusColbertRetriever</span>:
    <span class="hljs-keyword">def</span> <span class="hljs-title function_">__init__</span>(<span class="hljs-params">self, milvus_client, collection_name, dim=<span class="hljs-number">128</span></span>):
        <span class="hljs-comment"># Initialize the retriever with a Milvus client, collection name, and dimensionality of the vector embeddings.</span>
        <span class="hljs-comment"># If the collection exists, load it.</span>
        <span class="hljs-variable language_">self</span>.collection_name = collection_name
        <span class="hljs-variable language_">self</span>.client = milvus_client
        <span class="hljs-keyword">if</span> <span class="hljs-variable language_">self</span>.client.has_collection(collection_name=<span class="hljs-variable language_">self</span>.collection_name):
            <span class="hljs-variable language_">self</span>.client.load_collection(collection_name)
        <span class="hljs-variable language_">self</span>.dim = dim

    <span class="hljs-keyword">def</span> <span class="hljs-title function_">create_collection</span>(<span class="hljs-params">self</span>):
        <span class="hljs-comment"># Create a new collection in Milvus for storing embeddings.</span>
        <span class="hljs-comment"># Drop the existing collection if it already exists and define the schema for the collection.</span>
        <span class="hljs-keyword">if</span> <span class="hljs-variable language_">self</span>.client.has_collection(collection_name=<span class="hljs-variable language_">self</span>.collection_name):
            <span class="hljs-variable language_">self</span>.client.drop_collection(collection_name=<span class="hljs-variable language_">self</span>.collection_name)
        schema = <span class="hljs-variable language_">self</span>.client.create_schema(
            auto_id=<span class="hljs-literal">True</span>,
            enable_dynamic_fields=<span class="hljs-literal">True</span>,
        )
        schema.add_field(field_name=<span class="hljs-string">&quot;pk&quot;</span>, datatype=DataType.INT64, is_primary=<span class="hljs-literal">True</span>)
        schema.add_field(
            field_name=<span class="hljs-string">&quot;vector&quot;</span>, datatype=DataType.FLOAT_VECTOR, dim=<span class="hljs-variable language_">self</span>.dim
        )
        schema.add_field(field_name=<span class="hljs-string">&quot;seq_id&quot;</span>, datatype=DataType.INT16)
        schema.add_field(field_name=<span class="hljs-string">&quot;doc_id&quot;</span>, datatype=DataType.INT64)
        schema.add_field(field_name=<span class="hljs-string">&quot;doc&quot;</span>, datatype=DataType.VARCHAR, max_length=<span class="hljs-number">65535</span>)

        <span class="hljs-variable language_">self</span>.client.create_collection(
            collection_name=<span class="hljs-variable language_">self</span>.collection_name, schema=schema
        )

    <span class="hljs-keyword">def</span> <span class="hljs-title function_">create_index</span>(<span class="hljs-params">self</span>):
        <span class="hljs-comment"># Create an index on the vector field to enable fast similarity search.</span>
        <span class="hljs-comment"># Releases and drops any existing index before creating a new one with specified parameters.</span>
        <span class="hljs-variable language_">self</span>.client.release_collection(collection_name=<span class="hljs-variable language_">self</span>.collection_name)
        <span class="hljs-variable language_">self</span>.client.drop_index(
            collection_name=<span class="hljs-variable language_">self</span>.collection_name, index_name=<span class="hljs-string">&quot;vector&quot;</span>
        )
        index_params = <span class="hljs-variable language_">self</span>.client.prepare_index_params()
        index_params.add_index(
            field_name=<span class="hljs-string">&quot;vector&quot;</span>,
            index_name=<span class="hljs-string">&quot;vector_index&quot;</span>,
            index_type=<span class="hljs-string">&quot;HNSW&quot;</span>,  <span class="hljs-comment"># or any other index type you want</span>
            metric_type=<span class="hljs-string">&quot;IP&quot;</span>,  <span class="hljs-comment"># or the appropriate metric type</span>
            params={
                <span class="hljs-string">&quot;M&quot;</span>: <span class="hljs-number">16</span>,
                <span class="hljs-string">&quot;efConstruction&quot;</span>: <span class="hljs-number">500</span>,
            },  <span class="hljs-comment"># adjust these parameters as needed</span>
        )

        <span class="hljs-variable language_">self</span>.client.create_index(
            collection_name=<span class="hljs-variable language_">self</span>.collection_name, index_params=index_params, sync=<span class="hljs-literal">True</span>
        )

    <span class="hljs-keyword">def</span> <span class="hljs-title function_">create_scalar_index</span>(<span class="hljs-params">self</span>):
        <span class="hljs-comment"># Create a scalar index for the &quot;doc_id&quot; field to enable fast lookups by document ID.</span>
        <span class="hljs-variable language_">self</span>.client.release_collection(collection_name=<span class="hljs-variable language_">self</span>.collection_name)

        index_params = <span class="hljs-variable language_">self</span>.client.prepare_index_params()
        index_params.add_index(
            field_name=<span class="hljs-string">&quot;doc_id&quot;</span>,
            index_name=<span class="hljs-string">&quot;int32_index&quot;</span>,
            index_type=<span class="hljs-string">&quot;INVERTED&quot;</span>,  <span class="hljs-comment"># or any other index type you want</span>
        )

        <span class="hljs-variable language_">self</span>.client.create_index(
            collection_name=<span class="hljs-variable language_">self</span>.collection_name, index_params=index_params, sync=<span class="hljs-literal">True</span>
        )

    <span class="hljs-keyword">def</span> <span class="hljs-title function_">search</span>(<span class="hljs-params">self, data, topk</span>):
        <span class="hljs-comment"># Perform a vector search on the collection to find the top-k most similar documents.</span>
        search_params = {<span class="hljs-string">&quot;metric_type&quot;</span>: <span class="hljs-string">&quot;IP&quot;</span>, <span class="hljs-string">&quot;params&quot;</span>: {}}
        results = <span class="hljs-variable language_">self</span>.client.search(
            <span class="hljs-variable language_">self</span>.collection_name,
            data,
            limit=<span class="hljs-built_in">int</span>(<span class="hljs-number">50</span>),
            output_fields=[<span class="hljs-string">&quot;vector&quot;</span>, <span class="hljs-string">&quot;seq_id&quot;</span>, <span class="hljs-string">&quot;doc_id&quot;</span>],
            search_params=search_params,
        )
        doc_ids = <span class="hljs-built_in">set</span>()
        <span class="hljs-keyword">for</span> r_id <span class="hljs-keyword">in</span> <span class="hljs-built_in">range</span>(<span class="hljs-built_in">len</span>(results)):
            <span class="hljs-keyword">for</span> r <span class="hljs-keyword">in</span> <span class="hljs-built_in">range</span>(<span class="hljs-built_in">len</span>(results[r_id])):
                doc_ids.add(results[r_id][r][<span class="hljs-string">&quot;entity&quot;</span>][<span class="hljs-string">&quot;doc_id&quot;</span>])

        scores = []

        <span class="hljs-keyword">def</span> <span class="hljs-title function_">rerank_single_doc</span>(<span class="hljs-params">doc_id, data, client, collection_name</span>):
            <span class="hljs-comment"># Rerank a single document by retrieving its embeddings and calculating the similarity with the query.</span>
            doc_colbert_vecs = client.query(
                collection_name=collection_name,
                <span class="hljs-built_in">filter</span>=<span class="hljs-string">f&quot;doc_id in [<span class="hljs-subst">{doc_id}</span>, <span class="hljs-subst">{doc_id + <span class="hljs-number">1</span>}</span>]&quot;</span>,
                output_fields=[<span class="hljs-string">&quot;seq_id&quot;</span>, <span class="hljs-string">&quot;vector&quot;</span>, <span class="hljs-string">&quot;doc&quot;</span>],
                limit=<span class="hljs-number">1000</span>,
            )
            doc_vecs = np.vstack(
                [doc_colbert_vecs[i][<span class="hljs-string">&quot;vector&quot;</span>] <span class="hljs-keyword">for</span> i <span class="hljs-keyword">in</span> <span class="hljs-built_in">range</span>(<span class="hljs-built_in">len</span>(doc_colbert_vecs))]
            )
            score = np.dot(data, doc_vecs.T).<span class="hljs-built_in">max</span>(<span class="hljs-number">1</span>).<span class="hljs-built_in">sum</span>()
            <span class="hljs-keyword">return</span> (score, doc_id)

        <span class="hljs-keyword">with</span> concurrent.futures.ThreadPoolExecutor(max_workers=<span class="hljs-number">300</span>) <span class="hljs-keyword">as</span> executor:
            futures = {
                executor.submit(
                    rerank_single_doc, doc_id, data, client, <span class="hljs-variable language_">self</span>.collection_name
                ): doc_id
                <span class="hljs-keyword">for</span> doc_id <span class="hljs-keyword">in</span> doc_ids
            }
            <span class="hljs-keyword">for</span> future <span class="hljs-keyword">in</span> concurrent.futures.as_completed(futures):
                score, doc_id = future.result()
                scores.append((score, doc_id))

        scores.sort(key=<span class="hljs-keyword">lambda</span> x: x[<span class="hljs-number">0</span>], reverse=<span class="hljs-literal">True</span>)
        <span class="hljs-keyword">if</span> <span class="hljs-built_in">len</span>(scores) &gt;= topk:
            <span class="hljs-keyword">return</span> scores[:topk]
        <span class="hljs-keyword">else</span>:
            <span class="hljs-keyword">return</span> scores

    <span class="hljs-keyword">def</span> <span class="hljs-title function_">insert</span>(<span class="hljs-params">self, data</span>):
        <span class="hljs-comment"># Insert ColBERT embeddings and metadata for a document into the collection.</span>
        colbert_vecs = [vec <span class="hljs-keyword">for</span> vec <span class="hljs-keyword">in</span> data[<span class="hljs-string">&quot;colbert_vecs&quot;</span>]]
        seq_length = <span class="hljs-built_in">len</span>(colbert_vecs)
        doc_ids = [data[<span class="hljs-string">&quot;doc_id&quot;</span>] <span class="hljs-keyword">for</span> i <span class="hljs-keyword">in</span> <span class="hljs-built_in">range</span>(seq_length)]
        seq_ids = <span class="hljs-built_in">list</span>(<span class="hljs-built_in">range</span>(seq_length))
        docs = [<span class="hljs-string">&quot;&quot;</span>] * seq_length
        docs[<span class="hljs-number">0</span>] = data[<span class="hljs-string">&quot;filepath&quot;</span>]

        <span class="hljs-comment"># Insert the data as multiple vectors (one for each sequence) along with the corresponding metadata.</span>
        <span class="hljs-variable language_">self</span>.client.insert(
            <span class="hljs-variable language_">self</span>.collection_name,
            [
                {
                    <span class="hljs-string">&quot;vector&quot;</span>: colbert_vecs[i],
                    <span class="hljs-string">&quot;seq_id&quot;</span>: seq_ids[i],
                    <span class="hljs-string">&quot;doc_id&quot;</span>: doc_ids[i],
                    <span class="hljs-string">&quot;doc&quot;</span>: docs[i],
                }
                <span class="hljs-keyword">for</span> i <span class="hljs-keyword">in</span> <span class="hljs-built_in">range</span>(seq_length)
            ],
        )
<button class="copy-code-btn"></button></code></pre>
<p>Utilizaremos o <a href="https://github.com/illuin-tech/colpali">motor colpali_engine</a> para extrair listas de incorporação para duas consultas e obter as informações relevantes das páginas PDF.</p>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">from</span> colpali_engine.models <span class="hljs-keyword">import</span> ColPali
<span class="hljs-keyword">from</span> colpali_engine.models.paligemma.colpali.processing_colpali <span class="hljs-keyword">import</span> ColPaliProcessor
<span class="hljs-keyword">from</span> colpali_engine.utils.processing_utils <span class="hljs-keyword">import</span> BaseVisualRetrieverProcessor
<span class="hljs-keyword">from</span> colpali_engine.utils.torch_utils <span class="hljs-keyword">import</span> ListDataset, get_torch_device
<span class="hljs-keyword">from</span> torch.utils.data <span class="hljs-keyword">import</span> DataLoader
<span class="hljs-keyword">import</span> torch
<span class="hljs-keyword">from</span> typing <span class="hljs-keyword">import</span> <span class="hljs-type">List</span>, cast

device = get_torch_device(<span class="hljs-string">&quot;cpu&quot;</span>)
model_name = <span class="hljs-string">&quot;vidore/colpali-v1.2&quot;</span>

model = ColPali.from_pretrained(
    model_name,
    torch_dtype=torch.bfloat16,
    device_map=device,
).<span class="hljs-built_in">eval</span>()

queries = [
    <span class="hljs-string">&quot;How to end-to-end retrieval with ColBert?&quot;</span>,
    <span class="hljs-string">&quot;Where is ColBERT performance table?&quot;</span>,
]

processor = cast(ColPaliProcessor, ColPaliProcessor.from_pretrained(model_name))

dataloader = DataLoader(
    dataset=ListDataset[<span class="hljs-built_in">str</span>](queries),
    batch_size=<span class="hljs-number">1</span>,
    shuffle=<span class="hljs-literal">False</span>,
    collate_fn=<span class="hljs-keyword">lambda</span> x: processor.process_queries(x),
)

qs: <span class="hljs-type">List</span>[torch.Tensor] = []
<span class="hljs-keyword">for</span> batch_query <span class="hljs-keyword">in</span> dataloader:
    <span class="hljs-keyword">with</span> torch.no_grad():
        batch_query = {k: v.to(model.device) <span class="hljs-keyword">for</span> k, v <span class="hljs-keyword">in</span> batch_query.items()}
        embeddings_query = model(**batch_query)
    qs.extend(<span class="hljs-built_in">list</span>(torch.unbind(embeddings_query.to(<span class="hljs-string">&quot;cpu&quot;</span>))))
<button class="copy-code-btn"></button></code></pre>
<p>Além disso, precisamos de extrair a lista de incorporação para cada página e esta mostra que existem 1030 incorporações de 128 dimensões para cada página.</p>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">from</span> tqdm <span class="hljs-keyword">import</span> tqdm
<span class="hljs-keyword">from</span> PIL <span class="hljs-keyword">import</span> Image
<span class="hljs-keyword">import</span> os

images = [Image.<span class="hljs-built_in">open</span>(<span class="hljs-string">&quot;./pages/&quot;</span> + name) <span class="hljs-keyword">for</span> name <span class="hljs-keyword">in</span> os.listdir(<span class="hljs-string">&quot;./pages&quot;</span>)]

dataloader = DataLoader(
    dataset=ListDataset[<span class="hljs-built_in">str</span>](images),
    batch_size=<span class="hljs-number">1</span>,
    shuffle=<span class="hljs-literal">False</span>,
    collate_fn=<span class="hljs-keyword">lambda</span> x: processor.process_images(x),
)

ds: <span class="hljs-type">List</span>[torch.Tensor] = []
<span class="hljs-keyword">for</span> batch_doc <span class="hljs-keyword">in</span> tqdm(dataloader):
    <span class="hljs-keyword">with</span> torch.no_grad():
        batch_doc = {k: v.to(model.device) <span class="hljs-keyword">for</span> k, v <span class="hljs-keyword">in</span> batch_doc.items()}
        embeddings_doc = model(**batch_doc)
    ds.extend(<span class="hljs-built_in">list</span>(torch.unbind(embeddings_doc.to(<span class="hljs-string">&quot;cpu&quot;</span>))))

<span class="hljs-built_in">print</span>(ds[<span class="hljs-number">0</span>].shape)
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no">  0%|          | 0/10 [00:00&lt;?, ?it/s]

100%|██████████| 10/10 [01:22&lt;00:00,  8.24s/it]

torch.Size([1030, 128])
</code></pre>
<p>Vamos criar uma coleção chamada "colpali" utilizando o MilvusColbertRetriever.</p>
<pre><code translate="no" class="language-python">retriever = <span class="hljs-title class_">MilvusColbertRetriever</span>(collection_name=<span class="hljs-string">&quot;colpali&quot;</span>, milvus_client=client)
retriever.<span class="hljs-title function_">create_collection</span>()
retriever.<span class="hljs-title function_">create_index</span>()
<button class="copy-code-btn"></button></code></pre>
<p>Vamos inserir as listas de ligações na base de dados Milvus.</p>
<pre><code translate="no" class="language-python">filepaths = [<span class="hljs-string">&quot;./pages/&quot;</span> + name <span class="hljs-keyword">for</span> name <span class="hljs-keyword">in</span> os.listdir(<span class="hljs-string">&quot;./pages&quot;</span>)]
<span class="hljs-keyword">for</span> i <span class="hljs-keyword">in</span> <span class="hljs-built_in">range</span>(<span class="hljs-built_in">len</span>(filepaths)):
    data = {
        <span class="hljs-string">&quot;colbert_vecs&quot;</span>: ds[i].<span class="hljs-built_in">float</span>().numpy(),
        <span class="hljs-string">&quot;doc_id&quot;</span>: i,
        <span class="hljs-string">&quot;filepath&quot;</span>: filepaths[i],
    }
    retriever.insert(data)
<button class="copy-code-btn"></button></code></pre>
<p>Agora, podemos procurar a página mais relevante utilizando a lista de incorporação da consulta.</p>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">for</span> query <span class="hljs-keyword">in</span> qs:
    query = query.<span class="hljs-built_in">float</span>().numpy()
    result = retriever.search(query, topk=<span class="hljs-number">1</span>)
    <span class="hljs-built_in">print</span>(filepaths[result[<span class="hljs-number">0</span>][<span class="hljs-number">1</span>]])
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no">./pages/page_5.png
./pages/page_7.png
</code></pre>
<p>Por fim, recuperamos o nome da página original. Com o ColPALI, podemos recuperar documentos multimodais sem a necessidade de técnicas de processamento complexas para extrair texto e imagens dos documentos. Ao utilizar modelos de visão de grande dimensão, é possível analisar mais informações - como tabelas e figuras - sem perda significativa de informação.</p>
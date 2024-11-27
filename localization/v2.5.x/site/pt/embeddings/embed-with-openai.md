---
id: embed-with-openai.md
order: 2
summary: >-
  O Milvus integra-se nos modelos da OpenAI através da classe
  OpenAIEmbeddingFunction.
title: OpenAI
---
<h1 id="OpenAI" class="common-anchor-header">OpenAI<button data-href="#OpenAI" class="anchor-icon" translate="no">
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
    </button></h1><p>O Milvus integra-se com os modelos da OpenAI através da classe <strong>OpenAIEmbeddingFunction</strong>. Esta classe fornece métodos para codificar documentos e consultas utilizando os modelos pré-treinados da OpenAI e devolver os embeddings como vectores densos compatíveis com a indexação Milvus. Para utilizar esta funcionalidade, obtenha uma chave de API da <a href="https://openai.com/api/">OpenAI</a> criando uma conta na sua plataforma.</p>
<p>Para utilizar esta funcionalidade, instale as dependências necessárias:</p>
<pre><code translate="no" class="language-bash">pip install --upgrade pymilvus
pip install <span class="hljs-string">&quot;pymilvus[model]&quot;</span>
<button class="copy-code-btn"></button></code></pre>
<p>De seguida, instancie a <strong>OpenAIEmbeddingFunction</strong>:</p>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">from</span> pymilvus <span class="hljs-keyword">import</span> model

openai_ef = model.dense.OpenAIEmbeddingFunction(
    model_name=<span class="hljs-string">&#x27;text-embedding-3-large&#x27;</span>, <span class="hljs-comment"># Specify the model name</span>
    api_key=<span class="hljs-string">&#x27;YOUR_API_KEY&#x27;</span>, <span class="hljs-comment"># Provide your OpenAI API key</span>
    dimensions=<span class="hljs-number">512</span> <span class="hljs-comment"># Set the embedding dimensionality</span>
)
<button class="copy-code-btn"></button></code></pre>
<p><strong>Parâmetros</strong>:</p>
<ul>
<li><p><strong>nome_do_modelo</strong><em>(string</em>)</p>
<p>O nome do modelo OpenAI a utilizar para a codificação. As opções válidas são <strong>text-embedding-3-small</strong>, <strong>text-embedding-3-large</strong> e <strong>text-embedding-ada-002</strong> (predefinição).</p></li>
<li><p><strong>api_key</strong><em>(string</em>)</p>
<p>A chave da API para aceder à API OpenAI.</p></li>
<li><p><strong>dimensões</strong><em>(int</em>)</p>
<p>O número de dimensões que os embeddings de saída resultantes devem ter. Suportado apenas em modelos <strong>text-embedding-3</strong> e posteriores.</p></li>
</ul>
<p>Para criar embeddings para documentos, use o método <strong>encode_documents()</strong>:</p>
<pre><code translate="no" class="language-python">docs = [
    <span class="hljs-string">&quot;Artificial intelligence was founded as an academic discipline in 1956.&quot;</span>,
    <span class="hljs-string">&quot;Alan Turing was the first person to conduct substantial research in AI.&quot;</span>,
    <span class="hljs-string">&quot;Born in Maida Vale, London, Turing was raised in southern England.&quot;</span>,
]

docs_embeddings = openai_ef.encode_documents(docs)

<span class="hljs-comment"># Print embeddings</span>
<span class="hljs-built_in">print</span>(<span class="hljs-string">&quot;Embeddings:&quot;</span>, docs_embeddings)
<span class="hljs-comment"># Print dimension and shape of embeddings</span>
<span class="hljs-built_in">print</span>(<span class="hljs-string">&quot;Dim:&quot;</span>, openai_ef.dim, docs_embeddings[<span class="hljs-number">0</span>].shape)
<button class="copy-code-btn"></button></code></pre>
<p>O resultado esperado é semelhante ao seguinte:</p>
<pre><code translate="no" class="language-python">Embeddings: [array([ 1.76741909e-02, -2.04964578e-02, -1.09788161e-02, -5.27223349e-02,
        4.23139781e-02, -6.64533582e-03,  4.21088142e-03,  1.04644023e-01,
        5.10009527e-02,  5.32827862e-02, -3.26061808e-02, -3.66494283e-02,
...
       -8.93232748e-02,  6.68255147e-03,  3.55093405e-02, -5.09071983e-02,
        3.74144339e-03,  4.72541340e-02,  2.11916920e-02,  1.00753829e-02,
       -5.76633997e-02,  9.68257990e-03,  4.62721288e-02, -4.33261096e-02])]
Dim: 512 (512,)
<button class="copy-code-btn"></button></code></pre>
<p>Para criar embeddings para consultas, utilize o método <strong>encode_queries()</strong>:</p>
<pre><code translate="no" class="language-python">queries = [<span class="hljs-string">&quot;When was artificial intelligence founded&quot;</span>, 
           <span class="hljs-string">&quot;Where was Alan Turing born?&quot;</span>]

query_embeddings = openai_ef.encode_queries(queries)

<span class="hljs-comment"># Print embeddings</span>
<span class="hljs-built_in">print</span>(<span class="hljs-string">&quot;Embeddings:&quot;</span>, query_embeddings)
<span class="hljs-comment"># Print dimension and shape of embeddings</span>
<span class="hljs-built_in">print</span>(<span class="hljs-string">&quot;Dim&quot;</span>, openai_ef.dim, query_embeddings[<span class="hljs-number">0</span>].shape)
<button class="copy-code-btn"></button></code></pre>
<p>O resultado esperado é semelhante ao seguinte:</p>
<pre><code translate="no" class="language-python">Embeddings: [array([ 0.00530251, -0.01907905, -0.01672608, -0.05030033,  0.01635982,
       -0.03169853, -0.0033602 ,  0.09047844,  0.00030747,  0.11853652,
       -0.02870182, -0.01526102,  0.05505067,  0.00993909, -0.07165466,
...
       -9.78106782e-02, -2.22669560e-02,  1.21873049e-02, -4.83198799e-02,
        5.32377362e-02, -1.90469325e-02,  5.62430918e-02,  1.02650477e-02,
       -6.21757433e-02,  7.88027793e-02,  4.91846527e-04, -1.51633881e-02])]
Dim 512 (512,)
<button class="copy-code-btn"></button></code></pre>
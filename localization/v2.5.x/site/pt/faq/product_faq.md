---
id: product_faq.md
summary: >-
  Encontre respostas às perguntas mais frequentes sobre a base de dados de
  vectores mais avançada do mundo.
title: FAQ do produto
---
<h1 id="Product-FAQ" class="common-anchor-header">FAQ do produto<button data-href="#Product-FAQ" class="anchor-icon" translate="no">
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
    </button></h1><h4 id="How-much-does-Milvus-cost" class="common-anchor-header">Quanto é que o Milvus custa?</h4><p>O Milvus é um projeto open-source 100% gratuito.</p>
<p>Por favor, cumpra a <a href="http://www.apache.org/licenses/LICENSE-2.0">Licença Apache 2.0</a> quando utilizar o Milvus para fins de produção ou distribuição.</p>
<p>A Zilliz, a empresa por detrás do Milvus, também oferece uma versão cloud totalmente gerida da plataforma para aqueles que não querem construir e manter a sua própria instância distribuída. <a href="https://zilliz.com/cloud">A Zilliz Cloud</a> mantém automaticamente a fiabilidade dos dados e permite que os utilizadores paguem apenas pelo que utilizam.</p>
<h4 id="Does-Milvus-support-non-x86-architectures" class="common-anchor-header">O Milvus suporta arquitecturas não-x86?</h4><p>O Milvus não pode ser instalado ou executado em plataformas não-x86.</p>
<p>Sua CPU deve suportar um dos seguintes conjuntos de instruções para executar o Milvus: SSE4.2, AVX, AVX2, AVX512. Estes são todos conjuntos de instruções SIMD dedicados ao x86.</p>
<h4 id="Where-does-Milvus-store-data" class="common-anchor-header">Onde é que o Milvus armazena os dados?</h4><p>O Milvus lida com dois tipos de dados, dados inseridos e metadados.</p>
<p>Os dados inseridos, incluindo os dados vectoriais, os dados escalares e o esquema específico da coleção, são armazenados no armazenamento persistente como registo incremental. Milvus suporta múltiplos backends de armazenamento de objectos, incluindo <a href="https://min.io/">MinIO</a>, <a href="https://aws.amazon.com/s3/?nc1=h_ls">AWS S3</a>, <a href="https://cloud.google.com/storage?hl=en#object-storage-for-companies-of-all-sizes">Google Cloud Storage</a> (GCS), <a href="https://azure.microsoft.com/en-us/products/storage/blobs">Azure Blob Storage</a>, <a href="https://www.alibabacloud.com/product/object-storage-service">Alibaba Cloud OSS</a> e <a href="https://www.tencentcloud.com/products/cos">Tencent Cloud Object Storage</a> (COS).</p>
<p>Os metadados são gerados no Milvus. Cada módulo do Milvus tem os seus próprios metadados que são armazenados no etcd.</p>
<h4 id="Why-is-there-no-vector-data-in-etcd" class="common-anchor-header">Porque não existem dados vectoriais no etcd?</h4><p>O etcd armazena os metadados do módulo Milvus; o MinIO armazena as entidades.</p>
<h4 id="Does-Milvus-support-inserting-and-searching-data-simultaneously" class="common-anchor-header">O Milvus suporta a inserção e pesquisa de dados em simultâneo?</h4><p>Sim. As operações de inserção e as operações de consulta são tratadas por dois módulos separados que são mutuamente independentes. Do ponto de vista do cliente, uma operação de inserção está concluída quando os dados inseridos entram na fila de mensagens. No entanto, os dados inseridos não podem ser pesquisados até serem carregados no nó de consulta. Se o tamanho do segmento não atingir o limite de construção de índice (512 MB por padrão), o Milvus recorre à pesquisa de força bruta e o desempenho da consulta pode ser reduzido.</p>
<h4 id="Can-vectors-with-duplicate-primary-keys-be-inserted-into-Milvus" class="common-anchor-header">Os vectores com chaves primárias duplicadas podem ser inseridos no Milvus?</h4><p>Sim. O Milvus não verifica se as chaves primárias dos vectores são duplicadas.</p>
<h4 id="When-vectors-with-duplicate-primary-keys-are-inserted-does-Milvus-treat-it-as-an-update-operation" class="common-anchor-header">Quando são inseridos vectores com chaves primárias duplicadas, o Milvus trata-os como uma operação de atualização?</h4><p>Não. Milvus não suporta atualmente operações de atualização e não verifica se as chaves primárias das entidades são duplicadas. O utilizador é responsável por garantir que as chaves primárias das entidades são únicas e, se não forem, o Milvus pode conter várias entidades com chaves primárias duplicadas.</p>
<p>Se isto acontecer, a cópia de dados que será devolvida quando consultada continua a ser um comportamento desconhecido. Esta limitação será corrigida em versões futuras.</p>
<h4 id="What-is-the-maximum-length-of-self-defined-entity-primary-keys" class="common-anchor-header">Qual é o comprimento máximo das chaves primárias de entidades auto-definidas?</h4><p>As chaves primárias de entidade devem ser inteiros não negativos de 64 bits.</p>
<h4 id="What-is-the-maximum-amount-of-data-that-can-be-added-per-insert-operation" class="common-anchor-header">Qual é a quantidade máxima de dados que pode ser adicionada por operação de inserção?</h4><p>Uma operação de inserção não pode exceder 1.024 MB de tamanho. Este é um limite imposto pelo gRPC.</p>
<h4 id="Does-collection-size-impact-query-performance-when-searching-in-a-specific-partition" class="common-anchor-header">O tamanho da coleção tem impacto no desempenho da consulta quando se pesquisa numa partição específica?</h4><p>Não. Se forem especificadas partições para uma pesquisa, o Milvus pesquisa apenas nas partições especificadas.</p>
<h4 id="Does-Milvus-need-to-load-the-entire-collection-when-partitions-are-specified-for-a-search" class="common-anchor-header">O Milvus precisa de carregar toda a coleção quando as partições são especificadas para uma pesquisa?</h4><p>Depende de quais dados são necessários para a pesquisa. Todas as partições que podem aparecer no resultado da pesquisa devem ser carregadas antes da pesquisa.</p>
<ul>
<li>Por exemplo, se só quiser pesquisar uma ou mais partições específicas, não precisa de carregar todas. Chame <code translate="no">load_partition()</code> para carregar a(s) partição(ões) pretendida(s) <em>e, em seguida,</em> especifique a(s) partição(ões) na chamada do método <code translate="no">search()</code>.</li>
<li>Se pretender pesquisar todas as partições, chame <code translate="no">load_collection()</code> para carregar toda a coleção, incluindo todas as partições.</li>
<li>Se não conseguir carregar a coleção ou as partições específicas antes de efetuar a pesquisa, o Milvus apresentará um erro.</li>
</ul>
<h4 id="Can-indexes-be-created-after-inserting-vectors" class="common-anchor-header">Podem ser criados índices após a inserção de vectores?</h4><p>Sim. Se já tiver sido criado um índice para uma coleção em <code translate="no">create_index()</code>, o Milvus criará automaticamente um índice para os vectores inseridos posteriormente. No entanto, o Milvus não cria um índice até que os novos vectores inseridos preencham um segmento inteiro e o ficheiro de índice recém-criado seja separado do anterior.</p>
<h4 id="How-are-the-FLAT-and-IVFFLAT-indexes-different" class="common-anchor-header">Quais são as diferenças entre os índices FLAT e IVF_FLAT?</h4><p>O índice IVF_FLAT divide o espaço vetorial em clusters de lista. No valor de lista predefinido de 16.384, o Milvus compara as distâncias entre o vetor alvo e os centróides de todos os 16.384 clusters para devolver os clusters mais próximos da sonda. Em seguida, o Milvus compara as distâncias entre o vetor alvo e os vectores nos clusters selecionados para obter os vectores mais próximos. Ao contrário do IVF_FLAT, o FLAT compara diretamente as distâncias entre o vetor alvo e todos os outros vectores.</p>
<p>Quando o número total de vectores é aproximadamente igual a nlist, há pouca distância entre o IVF_FLAT e o FLAT em termos de requisitos de cálculo e desempenho da pesquisa. No entanto, como o número de vetores excede nlist por um fator de dois ou mais, IVF_FLAT começa a demonstrar vantagens de desempenho.</p>
<p>Consulte <a href="/docs/pt/index.md">Índice de vetores</a> para obter mais informações.</p>
<h4 id="How-does-Milvus-flush-data" class="common-anchor-header">Como é que o Milvus descarrega os dados?</h4><p>O Milvus retorna sucesso quando os dados inseridos são ingeridos na fila de mensagens. No entanto, os dados ainda não foram transferidos para o disco. Em seguida, o nó de dados do Milvus escreve os dados na fila de mensagens para o armazenamento persistente como registos incrementais. Se <code translate="no">flush()</code> for chamado, o nó de dados é forçado a escrever todos os dados na fila de mensagens para o armazenamento persistente imediatamente.</p>
<h4 id="What-is-normalization-Why-is-normalization-needed" class="common-anchor-header">O que é normalização? Por que a normalização é necessária?</h4><p>A normalização se refere ao processo de conversão de um vetor para que sua norma seja igual a 1. Se o produto interno for usado para calcular a similaridade do vetor, os vetores devem ser normalizados. Após a normalização, o produto interno é igual à similaridade de cosseno.</p>
<p>Consulte <a href="https://en.wikipedia.org/wiki/Unit_vector">a Wikipedia</a> para obter mais informações.</p>
<h4 id="Why-do-Euclidean-distance-L2-and-inner-product-IP-return-different-results" class="common-anchor-header">Por que a distância euclidiana (L2) e o produto interno (IP) retornam resultados diferentes?</h4><p>Para vectores normalizados, a distância euclidiana (L2) é matematicamente equivalente ao produto interno (IP). Se estas métricas de semelhança devolverem resultados diferentes, verifique se os seus vectores estão normalizados</p>
<h4 id="Is-there-a-limit-to-the-total-number-of-collections-and-partitions-in-Milvus" class="common-anchor-header">Existe um limite para o número total de colecções e partições no Milvus?</h4><p>Sim. É possível criar até 65.535 colecções numa instância do Milvus. Ao calcular o número de colecções existentes, o Milvus conta todas as colecções com shards e partições.</p>
<p>Por exemplo, vamos supor que já criou 100 colecções, com 2 fragmentos e 4 partições em 60 delas e com 1 fragmento e 12 partições nas restantes 40 colecções. O número atual de colecções pode ser calculado da seguinte forma:</p>
<pre><code translate="no">60 * 2 * 4 + 40 * 1 * 12 = 960
<button class="copy-code-btn"></button></code></pre>
<h4 id="Why-do-I-get-fewer-than-k-vectors-when-searching-for-topk-vectors" class="common-anchor-header">Porque obtenho menos de k vectores quando procuro por <code translate="no">topk</code> vectores?</h4><p>Entre os índices que o Milvus suporta, o IVF_FLAT e o IVF_SQ8 implementam o método de agrupamento k-means. Um espaço de dados é dividido em <code translate="no">nlist</code> clusters e os vectores inseridos são distribuídos por estes clusters. O Milvus seleciona então os <code translate="no">nprobe</code> clusters mais próximos e compara as distâncias entre o vetor-alvo e todos os vectores nos clusters selecionados para obter os resultados finais.</p>
<p>Se <code translate="no">nlist</code> e <code translate="no">topk</code> forem grandes e nprobe for pequeno, o número de vectores nos clusters nprobe pode ser inferior a <code translate="no">k</code>. Por conseguinte, quando procura os vectores mais próximos de <code translate="no">topk</code>, o número de vectores devolvidos é inferior a <code translate="no">k</code>.</p>
<p>Para evitar esta situação, tente definir <code translate="no">nprobe</code> maior e <code translate="no">nlist</code> e <code translate="no">k</code> menor.</p>
<p>Consulte <a href="/docs/pt/index.md">Índice de vetores</a> para obter mais informações.</p>
<h4 id="What-is-the-maximum-vector-dimension-supported-in-Milvus" class="common-anchor-header">Qual é a dimensão máxima do vetor suportada pelo Milvus?</h4><p>Por predefinição, o Milvus pode gerir vectores com um máximo de 32.768 dimensões. Pode aumentar o valor de <code translate="no">Proxy.maxDimension</code> para permitir um vetor de maior dimensão.</p>
<h4 id="Does-Milvus-support-Apple-M1-CPU" class="common-anchor-header">O Milvus suporta o CPU Apple M1?</h4><p>A versão atual do Milvus não suporta diretamente o CPU Apple M1. Após Milvus 2.3, Milvus fornece imagens Docker para a arquitetura ARM64.</p>
<h4 id="What-data-types-does-Milvus-support-on-the-primary-key-field" class="common-anchor-header">Que tipos de dados o Milvus suporta no campo de chave primária?</h4><p>Na versão atual, o Milvus suporta INT64 e string.</p>
<h4 id="Is-Milvus-scalable" class="common-anchor-header">O Milvus é escalável?</h4><p>Sim. Pode implementar o cluster Milvus com vários nós através do Helm Chart no Kubernetes. Consulte o <a href="/docs/pt/scaleout.md">Guia de Escala</a> para obter mais instruções.</p>
<h4 id="What-are-growing-segment-and-sealed-segment" class="common-anchor-header">O que são segmento crescente e segmento selado?</h4><p>Quando um pedido de pesquisa chega, Milvus pesquisa tanto dados incrementais como dados históricos. Os dados incrementais são actualizações recentes, são armazenados nos segmentos crescentes, que são armazenados em buffer na memória antes de atingirem o limiar para serem persistidos no armazenamento de objectos e é criado um índice mais eficiente para eles, enquanto os dados históricos são actualizações de há algum tempo atrás. Encontram-se nos segmentos selados que foram persistidos no armazenamento de objectos. Os dados incrementais e os dados históricos constituem, em conjunto, todo o conjunto de dados para pesquisa. Esta conceção torna qualquer dado ingerido no Milvus instantaneamente pesquisável. No caso do Milvus Distributed, existem factores mais complexos que decidem quando é que um registo que acabou de ser ingerido pode aparecer no resultado da pesquisa. Saiba mais sobre isso nos <a href="https://milvus.io/docs/consistency.md">níveis de consistência</a>.</p>
<h4 id="Is-Milvus-available-for-concurrent-search" class="common-anchor-header">O Milvus está disponível para pesquisa simultânea?</h4><p>Sim. Para pesquisas na mesma coleção, o Milvus pesquisa simultaneamente os dados incrementais e históricos. No entanto, as consultas em diferentes colecções são realizadas em série. Considerando que os dados históricos podem ser um conjunto de dados extremamente grande, as pesquisas nos dados históricos são relativamente mais demoradas e essencialmente efectuadas em série.</p>
<h4 id="Why-does-the-data-in-MinIO-remain-after-the-corresponding-collection-is-dropped" class="common-anchor-header">Porque é que os dados no MinIO permanecem após a eliminação da coleção correspondente?</h4><p>Os dados no MinIO foram concebidos para permanecerem durante um determinado período de tempo para conveniência da reversão de dados.</p>
<h4 id="Does-Milvus-support-message-engines-other-than-Pulsar" class="common-anchor-header">O Milvus suporta outros motores de mensagens para além do Pulsar?</h4><p>Sim. Kafka é suportado no Milvus 2.1.0.</p>
<h4 id="Whats-the-difference-between-a-search-and-a-query" class="common-anchor-header">Qual é a diferença entre uma pesquisa e uma consulta?</h4><p>No Milvus, uma pesquisa por similaridade de vetores recupera vetores com base no cálculo de similaridade e na aceleração do índice de vetores. Ao contrário de uma pesquisa de semelhança de vectores, uma consulta de vectores recupera vectores através de uma filtragem escalar baseada numa expressão booleana. A expressão booleana filtra os campos escalares ou o campo de chave primária e recupera todos os resultados que correspondem aos filtros. Numa consulta, não estão envolvidos nem a métrica de semelhança nem o índice de vectores.</p>
<h4 id="Why-does-a-float-vector-value-have-a-precision-of-7-decimal-digits-in-Milvus" class="common-anchor-header">Porque é que um valor de vetor float tem uma precisão de 7 dígitos decimais no Milvus?</h4><p>O Milvus suporta o armazenamento de vectores como arrays Float32. Um valor Float32 tem uma precisão de 7 casas decimais. Mesmo com um valor Float64, como 1.3476964684980388, Milvus armazena-o como 1.347696. Assim, quando recupera um vetor deste tipo do Milvus, a precisão do valor Float64 perde-se.</p>
<h4 id="How-does-Milvus-handle-vector-data-types-and-precision" class="common-anchor-header">Como é que o Milvus lida com os tipos de dados vectoriais e com a precisão?</h4><p>O Milvus suporta os tipos de vectores Binary, Float32, Float16 e BFloat16.</p>
<ul>
<li>Vectores binários: Armazenam dados binários como sequências de 0s e 1s, utilizados no processamento de imagens e na recuperação de informações.</li>
<li>Vectores Float32: Armazenamento predefinido com uma precisão de cerca de 7 dígitos decimais. Mesmo os valores Float64 são armazenados com a precisão Float32, o que leva a uma potencial perda de precisão aquando da recuperação.</li>
<li>Vectores Float16 e BFloat16: Oferecem precisão e utilização de memória reduzidas. O Float16 é adequado para aplicações com largura de banda e armazenamento limitados, enquanto o BFloat16 equilibra o alcance e a eficiência, normalmente utilizado na aprendizagem profunda para reduzir os requisitos computacionais sem afetar significativamente a precisão.</li>
</ul>
<h4 id="Does-Milvus-support-specifying-default-values-for-scalar-or-vector-fields" class="common-anchor-header">O Milvus suporta a especificação de valores padrão para campos escalares ou vetoriais?</h4><p>Atualmente, o Milvus 2.4.x não suporta a especificação de valores padrão para campos escalares ou vetoriais. Esta funcionalidade está planeada para futuras versões.</p>
<h4 id="Still-have-questions" class="common-anchor-header">Ainda tem dúvidas?</h4><p>Você pode:</p>
<ul>
<li>Verificar <a href="https://github.com/milvus-io/milvus/issues">o Milvus</a> no GitHub. É bem-vindo para levantar questões, partilhar ideias e ajudar os outros.</li>
<li>Junte-se à nossa <a href="https://slack.milvus.io/">comunidade Slack</a> para obter apoio e envolver-se com a nossa comunidade de código aberto.</li>
</ul>
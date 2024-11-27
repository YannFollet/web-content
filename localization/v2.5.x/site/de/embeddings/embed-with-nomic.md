---
id: embed-with-nomic.md
order: 12
summary: >-
  Dieser Artikel beschreibt, wie die NomicEmbeddingFunction verwendet wird, um
  Dokumente und Abfragen mit dem Nomic Embedding Model zu kodieren.
title: Nomic
---
<h1 id="Nomic" class="common-anchor-header">Nomic<button data-href="#Nomic" class="anchor-icon" translate="no">
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
    </button></h1><p><a href="https://atlas.nomic.ai/">Nomic-Modelle</a> sind eine Reihe von fortschrittlichen Text- und Bildeinbettungslösungen, die von Nomic AI entwickelt wurden, um verschiedene Formen von Daten in dichte numerische Vektoren zu konvertieren, die ihre semantische Bedeutung erfassen.</p>
<p>Milvus lässt sich über die Klasse NomicEmbeddingFunction mit den Einbettungsmodellen von Nomic integrieren. Diese Klasse bietet Methoden zur Kodierung von Dokumenten und Abfragen unter Verwendung der Nomic-Einbettungsmodelle und gibt die Einbettungen als dichte Vektoren zurück, die mit der Milvus-Indizierung kompatibel sind. Um diese Funktionalität zu nutzen, erhalten Sie einen API-Schlüssel von <a href="https://atlas.nomic.ai/">Nomic Atlas</a>.</p>
<p>Um diese Funktion zu nutzen, installieren Sie die notwendigen Abhängigkeiten:</p>
<pre><code translate="no" class="language-python">pip install --upgrade pymilvus
pip install <span class="hljs-string">&quot;pymilvus[model]&quot;</span>
<button class="copy-code-btn"></button></code></pre>
<p>Dann instanziieren Sie die NomicEmbeddingFunction:</p>
<pre><code translate="no" class="language-python"><span class="hljs-comment"># Before accessing the Nomic Atlas API, configure your Nomic API token</span>
<span class="hljs-keyword">import</span> nomic
nomic.login(<span class="hljs-string">&#x27;YOUR_NOMIC_API_KEY&#x27;</span>)

<span class="hljs-comment"># Import Nomic embedding function</span>
<span class="hljs-keyword">from</span> pymilvus.model.dense <span class="hljs-keyword">import</span> NomicEmbeddingFunction

ef = NomicEmbeddingFunction(
    model_name=<span class="hljs-string">&quot;nomic-embed-text-v1.5&quot;</span>, <span class="hljs-comment"># Defaults to `mistral-embed`</span>
)
<button class="copy-code-btn"></button></code></pre>
<p><strong>Parameter</strong>:</p>
<ul>
<li><p><code translate="no">model_name</code> <em>(String</em>)</p>
<p>Der Name des Nomic-Einbettungsmodells, das für die Kodierung verwendet werden soll. Der Wert ist standardmäßig <code translate="no">nomic-embed-text-v1.5</code>. Weitere Informationen finden Sie in der <a href="https://docs.nomic.ai/atlas/models/image-embedding">offiziellen Nomic-Dokumentation</a>.</p></li>
</ul>
<p>Um Einbettungen für Dokumente zu erstellen, verwenden Sie die Methode <code translate="no">encode_documents()</code>:</p>
<pre><code translate="no" class="language-python">docs = [
    <span class="hljs-string">&quot;Artificial intelligence was founded as an academic discipline in 1956.&quot;</span>,
    <span class="hljs-string">&quot;Alan Turing was the first person to conduct substantial research in AI.&quot;</span>,
    <span class="hljs-string">&quot;Born in Maida Vale, London, Turing was raised in southern England.&quot;</span>,
]

docs_embeddings = ef.encode_documents(docs)

<span class="hljs-comment"># Print embeddings</span>
<span class="hljs-built_in">print</span>(<span class="hljs-string">&quot;Embeddings:&quot;</span>, docs_embeddings)
<span class="hljs-comment"># Print dimension and shape of embeddings</span>
<span class="hljs-built_in">print</span>(<span class="hljs-string">&quot;Dim:&quot;</span>, ef.dim, docs_embeddings[<span class="hljs-number">0</span>].shape)
<button class="copy-code-btn"></button></code></pre>
<p>Die erwartete Ausgabe ist ähnlich wie die folgende:</p>
<pre><code translate="no" class="language-python">Embeddings: [array([ 5.59997560e-02, 7.23266600e-02, -1.51977540e-01, -4.53491200e-02,
        6.49414060e-02, 4.33654800e-02, 2.26593020e-02, -3.51867680e-02,
        3.49998470e-03, 1.75571440e-03, -4.30297850e-03, 1.81274410e-02,
        ...
       -1.64337160e-02, -3.85437000e-02, 6.14318850e-02, -2.82745360e-02,
       -7.25708000e-02, -4.15563580e-04, -7.63320900e-03, 1.88446040e-02,
       -5.78002930e-02, 1.69830320e-02, -8.91876200e-03, -2.37731930e-02])]
Dim: 768 (768,)
<button class="copy-code-btn"></button></code></pre>
<p>Um Einbettungen für Abfragen zu erstellen, verwenden Sie die Methode <code translate="no">encode_queries()</code>:</p>
<pre><code translate="no" class="language-python">queries = [<span class="hljs-string">&quot;When was artificial intelligence founded&quot;</span>,
           <span class="hljs-string">&quot;Where was Alan Turing born?&quot;</span>]

query_embeddings = ef.encode_queries(queries)

<span class="hljs-built_in">print</span>(<span class="hljs-string">&quot;Embeddings:&quot;</span>, query_embeddings)
<span class="hljs-built_in">print</span>(<span class="hljs-string">&quot;Dim&quot;</span>, ef.dim, query_embeddings[<span class="hljs-number">0</span>].shape)
<button class="copy-code-btn"></button></code></pre>
<p>Die erwartete Ausgabe ist ähnlich wie die folgende:</p>
<pre><code translate="no" class="language-python">Embeddings: [array([ 3.24096680e-02, 7.35473600e-02, -1.63940430e-01, -4.45556640e-02,
        7.83081050e-02, 2.64587400e-02, 1.35898590e-03, -1.59606930e-02,
       -3.33557130e-02, 1.05056760e-02, -2.35290530e-02, 2.23388670e-02,
        ...
        7.67211900e-02, 4.54406740e-02, 9.70459000e-02, 4.00161740e-03,
       -3.12805180e-02, -7.05566400e-02, 5.04760740e-02, 5.22766100e-02,
       -3.87878400e-02, -3.03649900e-03, 5.90515140e-03, -1.95007320e-02])]
Dim 768 (768,)
<button class="copy-code-btn"></button></code></pre>
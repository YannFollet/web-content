---
id: upgrade_milvus_cluster-docker.md
summary: Scoprite come aggiornare il cluster Milvus con Docker Compose.
title: Aggiornamento del cluster Milvus con Docker Compose
---
<div class="tab-wrapper"><a href="/docs/it/upgrade_milvus_standalone-operator.md" class=''>Milvus OperatorMilvus</a><a href="/docs/it/upgrade_milvus_cluster-operator.md" class=''>OperatorMilvus</a><a href="/docs/it/configure-helm.md" class=''>OperatorHelmDocker</a><a href="/docs/it/upgrade_milvus_standalone-helm.md" class=''>ComposeHelmDocker</a><a href="/docs/it/upgrade_milvus_cluster-helm.md" class=''>ComposeHelm</a></div>
<h1 id="Upgrade-Milvus-Cluster-with-Docker-Compose" class="common-anchor-header">Aggiornamento del cluster Milvus con Docker Compose<button data-href="#Upgrade-Milvus-Cluster-with-Docker-Compose" class="anchor-icon" translate="no">
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
    </button></h1><p>Questo argomento descrive come aggiornare Milvus utilizzando Docker Compose.</p>
<p>In casi normali, è possibile <a href="#Upgrade-Milvus-by-changing-its-image">aggiornare Milvus cambiando la sua immagine</a>. Tuttavia, è necessario <a href="#Migrate-the-metadata">migrare i metadati</a> prima di qualsiasi aggiornamento da v2.1.x a v2.4.9.</p>
<h2 id="Upgrade-Milvus-by-changing-its-image" class="common-anchor-header">Aggiornare Milvus cambiando l'immagine<button data-href="#Upgrade-Milvus-by-changing-its-image" class="anchor-icon" translate="no">
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
    </button></h2><p>In casi normali, è possibile aggiornare Milvus come segue:</p>
<ol>
<li><p>Cambiare i tag dell'immagine di Milvus in <code translate="no">docker-compose.yaml</code>.</p>
<p>Si noti che è necessario modificare i tag immagine per il Proxy, tutti i coordinatori e tutti i nodi worker.</p>
<pre><code translate="no" class="language-yaml">...
rootcoord:
  container_name: milvus-rootcoord
  image: milvusdb/milvus:v2.4.9
...
proxy:
  container_name: milvus-proxy
  image: milvusdb/milvus:v2.4.9
...
querycoord:
  container_name: milvus-querycoord
  image: milvusdb/milvus:v2.4.9  
...
querynode:
  container_name: milvus-querynode
  image: milvusdb/milvus:v2.4.9
...
indexcoord:
  container_name: milvus-indexcoord
  image: milvusdb/milvus:v2.4.9
...
indexnode:
  container_name: milvus-indexnode
  image: milvusdb/milvus:v2.4.9 
...
datacoord:
  container_name: milvus-datacoord
  image: milvusdb/milvus:v2.4.9   
...
datanode:
  container_name: milvus-datanode
  image: milvusdb/milvus:v2.4.9
<button class="copy-code-btn"></button></code></pre></li>
<li><p>Eseguire i seguenti comandi per eseguire l'aggiornamento.</p>
<pre><code translate="no" class="language-shell">docker compose down
docker compose up -d
<button class="copy-code-btn"></button></code></pre></li>
</ol>
<h2 id="Migrate-the-metadata" class="common-anchor-header">Migrazione dei metadati<button data-href="#Migrate-the-metadata" class="anchor-icon" translate="no">
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
    </button></h2><ol>
<li><p>Arrestare tutti i componenti di Milvus.</p>
<pre><code translate="no">docker stop &lt;milvus-component-docker-container-name&gt;
<button class="copy-code-btn"></button></code></pre></li>
<li><p>Preparare il file di configurazione <code translate="no">migrate.yaml</code> per la migrazione dei metadati.</p>
<pre><code translate="no" class="language-yaml"><span class="hljs-comment"># migration.yaml</span>
cmd:
  <span class="hljs-comment"># Option: run/backup/rollback</span>
  <span class="hljs-built_in">type</span>: run
  runWithBackup: true
config:
  sourceVersion: <span class="hljs-number">2.1</span><span class="hljs-number">.4</span>   <span class="hljs-comment"># Specify your milvus version</span>
  targetVersion: <span class="hljs-number">2.4</span><span class="hljs-number">.9</span>
  backupFilePath: /tmp/migration.bak
metastore:
  <span class="hljs-built_in">type</span>: etcd
etcd:
  endpoints:
    - milvus-etcd:<span class="hljs-number">2379</span>  <span class="hljs-comment"># Use the etcd container name</span>
  rootPath: by-dev <span class="hljs-comment"># The root path where data is stored in etcd</span>
  metaSubPath: meta
  kvSubPath: kv
<button class="copy-code-btn"></button></code></pre></li>
<li><p>Eseguire il contenitore di migrazione.</p>
<pre><code translate="no"><span class="hljs-comment"># Suppose your docker-compose run with the default milvus network,</span>
<span class="hljs-comment"># and you put migration.yaml in the same directory with docker-compose.yaml.</span>
docker run --<span class="hljs-built_in">rm</span> -it --network milvus -v $(<span class="hljs-built_in">pwd</span>)/migration.yaml:/milvus/configs/migration.yaml milvus/meta-migration:v2.2.0 /milvus/bin/meta-migration -config=/milvus/configs/migration.yaml
<button class="copy-code-btn"></button></code></pre></li>
<li><p>Avviare nuovamente i componenti Milvus con la nuova immagine Milvus.</p>
<pre><code translate="no">Update the milvus image tag in the docker-compose.yaml
docker compose down
docker compose up -d
<button class="copy-code-btn"></button></code></pre></li>
</ol>
<h2 id="Whats-next" class="common-anchor-header">Cosa fare dopo<button data-href="#Whats-next" class="anchor-icon" translate="no">
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
    </button></h2><ul>
<li>Potreste anche voler imparare come:<ul>
<li><a href="/docs/it/scaleout.md">Scalare un cluster Milvus</a></li>
</ul></li>
<li>Se siete pronti a distribuire il vostro cluster su cloud:<ul>
<li>Imparare a <a href="/docs/it/eks.md">distribuire Milvus su Amazon EKS con Terraform</a></li>
<li>Imparare a <a href="/docs/it/gcp.md">distribuire il cluster Milvus su GCP con Kubernetes</a></li>
<li>Imparare a <a href="/docs/it/azure.md">distribuire Milvus su Microsoft Azure con Kubernetes</a></li>
</ul></li>
</ul>
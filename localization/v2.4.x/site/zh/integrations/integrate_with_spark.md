---
id: integrate_with_spark.md
summary: 本页讨论 Spark-Milvus 连接器。
title: 斯帕克-Milvus连接器用户指南
---

<h1 id="Spark-Milvus-Connector-User-Guide" class="common-anchor-header">Spark-Milvus 连接器用户指南<button data-href="#Spark-Milvus-Connector-User-Guide" class="anchor-icon" translate="no">
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
    </button></h1><p>Spark-Milvus Connector (https://github.com/zilliztech/spark-milvus) 提供 Apache Spark 和 Milvus 之间的无缝集成，将 Apache Spark 的数据处理和 ML 功能与 Milvus 的向量数据存储和搜索功能相结合。这种集成可实现各种有趣的应用，包括</p>
<ul>
<li>高效地将向量数据大批量加载到 Milvus 中、</li>
<li>在 Milvus 和其他存储系统或数据库之间移动数据、</li>
<li>利用 Spark MLlib 和其他人工智能工具分析 Milvus 中的数据。</li>
</ul>
<h2 id="Quick-start" class="common-anchor-header">快速启动<button data-href="#Quick-start" class="anchor-icon" translate="no">
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
    </button></h2><h3 id="Preparation" class="common-anchor-header">准备工作</h3><p>Spark-Milvus 连接器支持 Scala 和 Python 编程语言。用户可以使用<strong>Pyspark</strong>或<strong>Spark-shell</strong>。要运行此演示，请按以下步骤设置包含 Spark-Milvus Connector 依赖关系的 Spark 环境：</p>
<ol>
<li><p>安装 Apache Spark（版本 &gt;= 3.3.0）</p>
<p>您可以参考<a href="https://spark.apache.org/docs/latest/">官方文档</a>安装 Apache Spark。</p></li>
<li><p>下载<strong>spark-milvus</strong>jar 文件。</p>
<pre><code translate="no">wget https://github.com/zilliztech/spark-milvus/raw/1.0.0-SNAPSHOT/output/spark-milvus-1.0.0-SNAPSHOT.jar
<button class="copy-code-btn"></button></code></pre></li>
<li><p>将<strong>spark-milvus</strong>jar 作为依赖项之一启动 Spark 运行时。</p>
<p>要使用 Spark-Milvus 连接器启动 Spark 运行时，请将下载的<strong>spark-milvus</strong>作为依赖项添加到命令中。</p>
<ul>
<li><p><strong>pyspark</strong></p>
<pre><code translate="no">./<span class="hljs-built_in">bin</span>/pyspark --jars spark-milvus-<span class="hljs-number">1.0</span><span class="hljs-number">.0</span>-SNAPSHOT.jar
<button class="copy-code-btn"></button></code></pre></li>
<li><p><strong>spark-shell</strong></p>
<pre><code translate="no">./<span class="hljs-built_in">bin</span>/spark-shell --jars spark-milvus-<span class="hljs-number">1.0</span><span class="hljs-number">.0</span>-SNAPSHOT.jar
<button class="copy-code-btn"></button></code></pre></li>
</ul></li>
</ol>
<h3 id="Demo" class="common-anchor-header">演示</h3><p>在本演示中，我们将创建一个包含向量数据的示例 Spark DataFrame，并通过 Spark-Milvus Connector 将其写入 Milvus。Milvus 将根据模式和指定选项自动创建一个集合。</p>
<div class="multipleCode">
 <a href="#python">Python </a> <a href="#scala">Scala</a></div>
<pre><code translate="no" class="language-python"><span class="hljs-keyword">from</span> pyspark.sql <span class="hljs-keyword">import</span> SparkSession

columns = [<span class="hljs-string">&quot;id&quot;</span>, <span class="hljs-string">&quot;text&quot;</span>, <span class="hljs-string">&quot;vec&quot;</span>]
data = [(<span class="hljs-number">1</span>, <span class="hljs-string">&quot;a&quot;</span>, [<span class="hljs-number">1.0</span>,<span class="hljs-number">2.0</span>,<span class="hljs-number">3.0</span>,<span class="hljs-number">4.0</span>,<span class="hljs-number">5.0</span>,<span class="hljs-number">6.0</span>,<span class="hljs-number">7.0</span>,<span class="hljs-number">8.0</span>]),
(<span class="hljs-number">2</span>, <span class="hljs-string">&quot;b&quot;</span>, [<span class="hljs-number">1.0</span>,<span class="hljs-number">2.0</span>,<span class="hljs-number">3.0</span>,<span class="hljs-number">4.0</span>,<span class="hljs-number">5.0</span>,<span class="hljs-number">6.0</span>,<span class="hljs-number">7.0</span>,<span class="hljs-number">8.0</span>]),
(<span class="hljs-number">3</span>, <span class="hljs-string">&quot;c&quot;</span>, [<span class="hljs-number">1.0</span>,<span class="hljs-number">2.0</span>,<span class="hljs-number">3.0</span>,<span class="hljs-number">4.0</span>,<span class="hljs-number">5.0</span>,<span class="hljs-number">6.0</span>,<span class="hljs-number">7.0</span>,<span class="hljs-number">8.0</span>]),
(<span class="hljs-number">4</span>, <span class="hljs-string">&quot;d&quot;</span>, [<span class="hljs-number">1.0</span>,<span class="hljs-number">2.0</span>,<span class="hljs-number">3.0</span>,<span class="hljs-number">4.0</span>,<span class="hljs-number">5.0</span>,<span class="hljs-number">6.0</span>,<span class="hljs-number">7.0</span>,<span class="hljs-number">8.0</span>])]
sample_df = spark.sparkContext.parallelize(data).toDF(columns)
sample_df.write \
 .mode(<span class="hljs-string">&quot;append&quot;</span>) \
 .option(<span class="hljs-string">&quot;milvus.host&quot;</span>, <span class="hljs-string">&quot;localhost&quot;</span>) \
 .option(<span class="hljs-string">&quot;milvus.port&quot;</span>, <span class="hljs-string">&quot;19530&quot;</span>) \
 .option(<span class="hljs-string">&quot;milvus.collection.name&quot;</span>, <span class="hljs-string">&quot;hello_spark_milvus&quot;</span>) \
 .option(<span class="hljs-string">&quot;milvus.collection.vectorField&quot;</span>, <span class="hljs-string">&quot;vec&quot;</span>) \
 .option(<span class="hljs-string">&quot;milvus.collection.vectorDim&quot;</span>, <span class="hljs-string">&quot;8&quot;</span>) \
 .option(<span class="hljs-string">&quot;milvus.collection.primaryKeyField&quot;</span>, <span class="hljs-string">&quot;id&quot;</span>) \
 .<span class="hljs-built_in">format</span>(<span class="hljs-string">&quot;milvus&quot;</span>) \
 .save()
<button class="copy-code-btn"></button></code></pre>

<pre><code translate="no" class="language-scala"><span class="hljs-keyword">import</span> org.apache.spark.sql.{SaveMode, SparkSession}

object Hello <span class="hljs-keyword">extends</span> <span class="hljs-title class_">App</span> {

  <span class="hljs-type">val</span> <span class="hljs-variable">spark</span> <span class="hljs-operator">=</span> SparkSession.builder().master(<span class="hljs-string">&quot;local[*]&quot;</span>)
    .appName(<span class="hljs-string">&quot;HelloSparkMilvus&quot;</span>)
    .getOrCreate()

  <span class="hljs-keyword">import</span> spark.implicits._

  <span class="hljs-comment">// Create DataFrame</span>
  <span class="hljs-type">val</span> <span class="hljs-variable">sampleDF</span> <span class="hljs-operator">=</span> Seq(
    (<span class="hljs-number">1</span>, <span class="hljs-string">&quot;a&quot;</span>, Seq(<span class="hljs-number">1.0</span>,<span class="hljs-number">2.0</span>,<span class="hljs-number">3.0</span>,<span class="hljs-number">4.0</span>,<span class="hljs-number">5.0</span>)),
    (<span class="hljs-number">2</span>, <span class="hljs-string">&quot;b&quot;</span>, Seq(<span class="hljs-number">1.0</span>,<span class="hljs-number">2.0</span>,<span class="hljs-number">3.0</span>,<span class="hljs-number">4.0</span>,<span class="hljs-number">5.0</span>)),
    (<span class="hljs-number">3</span>, <span class="hljs-string">&quot;c&quot;</span>, Seq(<span class="hljs-number">1.0</span>,<span class="hljs-number">2.0</span>,<span class="hljs-number">3.0</span>,<span class="hljs-number">4.0</span>,<span class="hljs-number">5.0</span>)),
    (<span class="hljs-number">4</span>, <span class="hljs-string">&quot;d&quot;</span>, Seq(<span class="hljs-number">1.0</span>,<span class="hljs-number">2.0</span>,<span class="hljs-number">3.0</span>,<span class="hljs-number">4.0</span>,<span class="hljs-number">5.0</span>))
  ).toDF(<span class="hljs-string">&quot;id&quot;</span>, <span class="hljs-string">&quot;text&quot;</span>, <span class="hljs-string">&quot;vec&quot;</span>)

  <span class="hljs-comment">// set milvus options</span>
  <span class="hljs-type">val</span> <span class="hljs-variable">milvusOptions</span> <span class="hljs-operator">=</span> Map(
      <span class="hljs-string">&quot;milvus.host&quot;</span> -&gt; <span class="hljs-string">&quot;localhost&quot;</span> -&gt; uri,
      <span class="hljs-string">&quot;milvus.port&quot;</span> -&gt; <span class="hljs-string">&quot;19530&quot;</span>,
      <span class="hljs-string">&quot;milvus.collection.name&quot;</span> -&gt; <span class="hljs-string">&quot;hello_spark_milvus&quot;</span>,
      <span class="hljs-string">&quot;milvus.collection.vectorField&quot;</span> -&gt; <span class="hljs-string">&quot;vec&quot;</span>,
      <span class="hljs-string">&quot;milvus.collection.vectorDim&quot;</span> -&gt; <span class="hljs-string">&quot;5&quot;</span>,
      <span class="hljs-string">&quot;milvus.collection.primaryKeyField&quot;</span>, <span class="hljs-string">&quot;id&quot;</span>
    )
    
  sampleDF.write.format(<span class="hljs-string">&quot;milvus&quot;</span>)
    .options(milvusOptions)
    .mode(SaveMode.Append)
    .save()
}
<button class="copy-code-btn"></button></code></pre>
<p>执行上述代码后，你可以使用 SDK 或 Attu（Milvus 控制面板）在 Milvus 中查看插入的数据。您可以看到一个名为<code translate="no">hello_spark_milvus</code> 的集合，其中已插入了 4 个实体。</p>
<h2 id="Features--concepts" class="common-anchor-header">功能和概念<button data-href="#Features--concepts" class="anchor-icon" translate="no">
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
    </button></h2><h3 id="Milvus-options" class="common-anchor-header">Milvus 选项</h3><p>在 "<a href="#Quick-start">快速入门</a> <a href="#Quick-start">"</a>部分，我们展示了 Milvus 操作过程中的选项设置。这些选项被抽象为 Milvus 选项。它们用于创建与 Milvus 的连接，并控制 Milvus 的其他行为。并非所有选项都是强制性的。</p>
<table>
<thead>
<tr><th>选项键</th><th>默认值</th><th>说明</th></tr>
</thead>
<tbody>
<tr><td><code translate="no">milvus.host</code></td><td><code translate="no">localhost</code></td><td>Milvus 服务器主机。详见<a href="https://milvus.io/docs/manage_connection.md">管理 Milvus 连接</a>。</td></tr>
<tr><td><code translate="no">milvus.port</code></td><td><code translate="no">19530</code></td><td>Milvus 服务器端口。详见<a href="https://milvus.io/docs/manage_connection.md">管理 Milvus 连接</a>。</td></tr>
<tr><td><code translate="no">milvus.username</code></td><td><code translate="no">root</code></td><td>Milvus 服务器的用户名。详见<a href="https://milvus.io/docs/manage_connection.md">管理 Milvus 连接</a>。</td></tr>
<tr><td><code translate="no">milvus.password</code></td><td><code translate="no">Milvus</code></td><td>Milvus 服务器密码。详见<a href="https://milvus.io/docs/manage_connection.md">管理 Milvus 连接</a>。</td></tr>
<tr><td><code translate="no">milvus.uri</code></td><td><code translate="no">--</code></td><td>Milvus 服务器 URI。详见<a href="https://milvus.io/docs/manage_connection.md">管理 Milvus 连接</a>。</td></tr>
<tr><td><code translate="no">milvus.token</code></td><td><code translate="no">--</code></td><td>Milvus 服务器令牌。详见<a href="https://milvus.io/docs/manage_connection.md">管理 Milvus 连接</a>。</td></tr>
<tr><td><code translate="no">milvus.database.name</code></td><td><code translate="no">default</code></td><td>要读取或写入的 Milvus 数据库名称。</td></tr>
<tr><td><code translate="no">milvus.collection.name</code></td><td><code translate="no">hello_milvus</code></td><td>要读取或写入的 Milvus 集合名称。</td></tr>
<tr><td><code translate="no">milvus.collection.primaryKeyField</code></td><td><code translate="no">None</code></td><td>集合中主键字段的名称。如果集合不存在，则为必填项。</td></tr>
<tr><td><code translate="no">milvus.collection.vectorField</code></td><td><code translate="no">None</code></td><td>集合中向量字段的名称。如果集合不存在，则为必填项。</td></tr>
<tr><td><code translate="no">milvus.collection.vectorDim</code></td><td><code translate="no">None</code></td><td>集合中向量字段的尺寸。如果集合不存在，则为必填项。</td></tr>
<tr><td><code translate="no">milvus.collection.autoID</code></td><td><code translate="no">false</code></td><td>如果集合不存在，该选项指定是否自动为实体生成 ID。更多信息，请参阅<a href="https://milvus.io/docs/create_collection.md">create_collection</a></td></tr>
<tr><td><code translate="no">milvus.bucket</code></td><td><code translate="no">a-bucket</code></td><td>Milvus 存储中的存储桶名称。该名称应与<a href="https://github.com/milvus-io/milvus/blob/master/configs/milvus.yaml">milvus.yaml</a> 中的<code translate="no">minio.bucketName</code> 相同。</td></tr>
<tr><td><code translate="no">milvus.rootpath</code></td><td><code translate="no">files</code></td><td>Milvus 存储的根路径。应与<a href="https://github.com/milvus-io/milvus/blob/master/configs/milvus.yaml">milvus.yaml</a> 中的<code translate="no">minio.rootpath</code> 相同。</td></tr>
<tr><td><code translate="no">milvus.fs</code></td><td><code translate="no">s3a://</code></td><td>Milvus 存储的文件系统。<code translate="no">s3a://</code> 适用于开源 Spark。Databricks 使用<code translate="no">s3://</code> 。</td></tr>
<tr><td><code translate="no">milvus.storage.endpoint</code></td><td><code translate="no">localhost:9000</code></td><td>Milvus 存储的端点。该值应与<a href="https://github.com/milvus-io/milvus/blob/master/configs/milvus.yaml">milvus.yaml</a> 中的<code translate="no">minio.address</code>:<code translate="no">minio.port</code> 相同。</td></tr>
<tr><td><code translate="no">milvus.storage.user</code></td><td><code translate="no">minioadmin</code></td><td>Milvus 存储的用户。应与<a href="https://github.com/milvus-io/milvus/blob/master/configs/milvus.yaml">milvus.yaml</a> 中的<code translate="no">minio.accessKeyID</code> 相同。</td></tr>
<tr><td><code translate="no">milvus.storage.password</code></td><td><code translate="no">minioadmin</code></td><td>Milvus 存储的密码。应与<a href="https://github.com/milvus-io/milvus/blob/master/configs/milvus.yaml">milvus.yaml</a> 中的<code translate="no">minio.secretAccessKey</code> 相同。</td></tr>
<tr><td><code translate="no">milvus.storage.useSSL</code></td><td><code translate="no">false</code></td><td>是否为 Milvus 存储使用 SSL。应与<a href="https://github.com/milvus-io/milvus/blob/master/configs/milvus.yaml">milvus.yaml</a> 中的<code translate="no">minio.useSSL</code> 相同。</td></tr>
</tbody>
</table>
<h2 id="Milvus-data-format" class="common-anchor-header">Milvus 数据格式<button data-href="#Milvus-data-format" class="anchor-icon" translate="no">
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
    </button></h2><p>Spark-Milvus 连接器支持以下列 Milvus 数据格式读写数据：</p>
<ul>
<li><code translate="no">milvus</code>:用于从 Spark DataFrame 无缝转换为 Milvus 实体的 Milvus 数据格式。</li>
<li><code translate="no">milvusbinlog</code>:用于读取 Milvus 内置 binlog 数据的 Milvus 数据格式。</li>
<li><code translate="no">mjson</code>:用于向 Milvus 批量插入数据的 Milvus JSON 格式。</li>
</ul>
<h3 id="milvus" class="common-anchor-header">Milvus</h3><p>在<a href="#Quick-start">快速入门</a>中，我们使用<strong>milvus</strong>格式将样本数据写入 Milvus 集群。<strong>milvus</strong>格式是一种新的数据格式，支持将 Spark DataFrame 数据无缝写入 Milvus 集合。这是通过批量调用 Milvus SDK 的插入 API 来实现的。如果 Milvus 中不存在集合，则会根据数据帧的模式创建新的集合。不过，自动创建的集合可能不支持集合模式的所有功能。因此，建议先通过 SDK 创建一个集合，然后再使用 spark-milvus 进行编写。有关详细信息，请参阅<a href="https://github.com/zilliztech/spark-milvus/blob/main/examples/src/main/scala/InsertDemo.scala">演示</a>。</p>
<h3 id="milvusbinlog" class="common-anchor-header">milvusbinlog</h3><p>新数据格式<strong>milvusbinlog</strong>用于读取 Milvus 内置的 binlog 数据。Binlog 是 Milvus 基于 parquet 的内部数据存储格式。除非你熟悉<strong>Milvus</strong>内部存储的细节，否则不建议直接使用<strong>milvusbinlog</strong>。我们建议使用下一节将介绍的<a href="#MilvusUtils">MilvusUtils</a>函数。</p>
<pre><code translate="no" class="language-scalar">val df = spark.read
  .<span class="hljs-built_in">format</span>(<span class="hljs-string">&quot;milvusbinlog&quot;</span>)
  .load(path)
  .withColumnRenamed(<span class="hljs-string">&quot;val&quot;</span>, <span class="hljs-string">&quot;embedding&quot;</span>)
<button class="copy-code-btn"></button></code></pre>
<h3 id="mjson" class="common-anchor-header">mjson</h3><p>Milvus 提供<a href="https://milvus.io/docs/bulk_insert.md">Bulkinsert</a>功能，以便在处理大型数据集时提高写入性能。然而，Milvus 使用的 JSON 格式与 Spark 的默认 JSON 输出格式略有不同。 为了解决这个问题，我们引入了<strong>mjson</strong>数据格式，以生成符合 Milvus 要求的数据。下面的示例展示了 JSON-lines 和<strong>mjson</strong> 之间的区别：</p>
<ul>
<li><p>JSON-lines：</p>
<pre><code translate="no" class="language-json">{<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">101</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">13</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">1.1</span>, <span class="hljs-number">1.2</span>]}
{<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">102</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">25</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">2.1</span>, <span class="hljs-number">2.2</span>]}
{<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">103</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">7</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">3.1</span>, <span class="hljs-number">3.2</span>]}
{<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">104</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">12</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">4.1</span>, <span class="hljs-number">4.2</span>]}
{<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">105</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">34</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">5.1</span>, <span class="hljs-number">5.2</span>]}
<button class="copy-code-btn"></button></code></pre></li>
<li><p>mjson（Milvus Bulkinsert 要求）：</p>
<pre><code translate="no" class="language-json">{
    <span class="hljs-string">&quot;rows&quot;</span>:[
        {<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">101</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">13</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">1.1</span>, <span class="hljs-number">1.2</span>]},
        {<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">102</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">25</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">2.1</span>, <span class="hljs-number">2.2</span>]},
        {<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">103</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">7</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">3.1</span>, <span class="hljs-number">3.2</span>]},
        {<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">104</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">12</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">4.1</span>, <span class="hljs-number">4.2</span>]},
        {<span class="hljs-string">&quot;book_id&quot;</span>: <span class="hljs-number">105</span>, <span class="hljs-string">&quot;word_count&quot;</span>: <span class="hljs-number">34</span>, <span class="hljs-string">&quot;book_intro&quot;</span>: [<span class="hljs-number">5.1</span>, <span class="hljs-number">5.2</span>]}
    ]
}
<button class="copy-code-btn"></button></code></pre></li>
</ul>
<p>未来将对此进行改进。如果您的 Milvus 版本是 v2.3.7 或更高，且支持使用 Parquet 格式的 Bulkinsert，我们建议您在 spark-milvus 集成中使用 parquet 格式。请参见 Github 上的<a href="https://github.com/zilliztech/spark-milvus/blob/main/examples/src/main/scala/BulkInsertDemo.scala">演示</a>。</p>
<h2 id="MilvusUtils" class="common-anchor-header">MilvusUtils<button data-href="#MilvusUtils" class="anchor-icon" translate="no">
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
    </button></h2><p>MilvusUtils 包含多个有用的 util 函数。目前仅支持 Scala 语言。更多使用示例请参见<a href="#Advanced-Usage">高级使用</a>部分。</p>
<h3 id="MilvusUtilsreadMilvusCollection" class="common-anchor-header">MilvusUtils.readMilvusCollection</h3><p><strong>MilvusUtils.readMilvusCollection</strong>是将整个<strong>Milvus</strong>数据集加载到 Spark 数据帧的简单接口。它封装了各种操作，包括调用 Milvus SDK、读取<strong>milvusbinlog</strong>和常见的联合/连接操作。</p>
<pre><code translate="no" class="language-scala"><span class="hljs-type">val</span> <span class="hljs-variable">collectionDF</span> <span class="hljs-operator">=</span> MilvusUtils.readMilvusCollection(spark, milvusOptions)
<button class="copy-code-btn"></button></code></pre>
<h3 id="MilvusUtilsbulkInsertFromSpark" class="common-anchor-header">MilvusUtils.bulkInsertFromSpark</h3><p><strong>MilvusUtils.bulkInsertFromSpark</strong>提供了将 Spark 输出文件大批量导入 Milvus 的便捷方法。它封装了 Milvus SDK 的<strong>Bullkinsert</strong>API。</p>
<pre><code translate="no" class="language-scala">df.write.<span class="hljs-built_in">format</span>(<span class="hljs-string">&quot;parquet&quot;</span>).save(outputPath)
MilvusUtils.bulkInsertFromSpark(spark, milvusOptions, outputPath, <span class="hljs-string">&quot;parquet&quot;</span>)
<button class="copy-code-btn"></button></code></pre>
<h2 id="Advanced-Usage" class="common-anchor-header">高级用法<button data-href="#Advanced-Usage" class="anchor-icon" translate="no">
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
    </button></h2><p>在本节中，您将找到 Spark-Milvus 连接器用于数据分析和迁移的高级使用示例。更多演示，请参阅<a href="https://github.com/zilliztech/spark-milvus/tree/main/examples/src/main/scala">示例</a>。</p>
<h3 id="MySQL---embedding---Milvus" class="common-anchor-header">MySQL -&gt; 嵌入 -&gt; Milvus</h3><p>在本演示中，我们将</p>
<ol>
<li>通过 Spark-MySQL 连接器从 MySQL 读取数据、</li>
<li>生成嵌入（以 Word2Vec 为例），以及</li>
<li>将嵌入数据写入 Milvus。</li>
</ol>
<p>要启用 Spark-MySQL 连接器，需要在 Spark 环境中添加以下依赖项：</p>
<pre><code translate="no">spark-shell --jars spark-milvus-1.0.0-SNAPSHOT.jar,mysql-connector-j-x.x.x.jar
<button class="copy-code-btn"></button></code></pre>
<pre><code translate="no" class="language-scala"><span class="hljs-keyword">import</span> org.apache.spark.ml.feature.{Tokenizer, Word2Vec}
<span class="hljs-keyword">import</span> org.apache.spark.sql.functions.udf
<span class="hljs-keyword">import</span> org.apache.spark.sql.{SaveMode, SparkSession}
<span class="hljs-keyword">import</span> zilliztech.spark.milvus.MilvusOptions._

<span class="hljs-keyword">import</span> org.apache.spark.ml.linalg.Vector

object Mysql2MilvusDemo <span class="hljs-keyword">extends</span> <span class="hljs-title class_">App</span> {

<span class="hljs-type">val</span> <span class="hljs-variable">spark</span> <span class="hljs-operator">=</span> SparkSession.builder().master(<span class="hljs-string">&quot;local[*]&quot;</span>)
.appName(<span class="hljs-string">&quot;Mysql2MilvusDemo&quot;</span>)
.getOrCreate()

<span class="hljs-keyword">import</span> spark.implicits.\_

<span class="hljs-comment">// Create DataFrame</span>
<span class="hljs-type">val</span> <span class="hljs-variable">sampleDF</span> <span class="hljs-operator">=</span> Seq(
(<span class="hljs-number">1</span>, <span class="hljs-string">&quot;Milvus was created in 2019 with a singular goal: store, index, and manage massive embedding vectors generated by deep neural networks and other machine learning (ML) models.&quot;</span>),
(<span class="hljs-number">2</span>, <span class="hljs-string">&quot;As a database specifically designed to handle queries over input vectors, it is capable of indexing vectors on a trillion scale. &quot;</span>),
(<span class="hljs-number">3</span>, <span class="hljs-string">&quot;Unlike existing relational databases which mainly deal with structured data following a pre-defined pattern, Milvus is designed from the bottom-up to handle embedding vectors converted from unstructured data.&quot;</span>),
(<span class="hljs-number">4</span>, <span class="hljs-string">&quot;As the Internet grew and evolved, unstructured data became more and more common, including emails, papers, IoT sensor data, Facebook photos, protein structures, and much more.&quot;</span>)
).toDF(<span class="hljs-string">&quot;id&quot;</span>, <span class="hljs-string">&quot;text&quot;</span>)

<span class="hljs-comment">// Write to MySQL Table</span>
sampleDF.write
.mode(SaveMode.Append)
.format(<span class="hljs-string">&quot;jdbc&quot;</span>)
.option(<span class="hljs-string">&quot;driver&quot;</span>,<span class="hljs-string">&quot;com.mysql.cj.jdbc.Driver&quot;</span>)
.option(<span class="hljs-string">&quot;url&quot;</span>, <span class="hljs-string">&quot;jdbc:mysql://localhost:3306/test&quot;</span>)
.option(<span class="hljs-string">&quot;dbtable&quot;</span>, <span class="hljs-string">&quot;demo&quot;</span>)
.option(<span class="hljs-string">&quot;user&quot;</span>, <span class="hljs-string">&quot;root&quot;</span>)
.option(<span class="hljs-string">&quot;password&quot;</span>, <span class="hljs-string">&quot;123456&quot;</span>)
.save()

<span class="hljs-comment">// Read from MySQL Table</span>
<span class="hljs-type">val</span> <span class="hljs-variable">dfMysql</span> <span class="hljs-operator">=</span> spark.read
.format(<span class="hljs-string">&quot;jdbc&quot;</span>)
.option(<span class="hljs-string">&quot;driver&quot;</span>,<span class="hljs-string">&quot;com.mysql.cj.jdbc.Driver&quot;</span>)
.option(<span class="hljs-string">&quot;url&quot;</span>, <span class="hljs-string">&quot;jdbc:mysql://localhost:3306/test&quot;</span>)
.option(<span class="hljs-string">&quot;dbtable&quot;</span>, <span class="hljs-string">&quot;demo&quot;</span>)
.option(<span class="hljs-string">&quot;user&quot;</span>, <span class="hljs-string">&quot;root&quot;</span>)
.option(<span class="hljs-string">&quot;password&quot;</span>, <span class="hljs-string">&quot;123456&quot;</span>)
.load()

<span class="hljs-type">val</span> <span class="hljs-variable">tokenizer</span> <span class="hljs-operator">=</span> <span class="hljs-keyword">new</span> <span class="hljs-title class_">Tokenizer</span>().setInputCol(<span class="hljs-string">&quot;text&quot;</span>).setOutputCol(<span class="hljs-string">&quot;tokens&quot;</span>)
<span class="hljs-type">val</span> <span class="hljs-variable">tokenizedDf</span> <span class="hljs-operator">=</span> tokenizer.transform(dfMysql)

<span class="hljs-comment">// Learn a mapping from words to Vectors.</span>
<span class="hljs-type">val</span> <span class="hljs-variable">word2Vec</span> <span class="hljs-operator">=</span> <span class="hljs-keyword">new</span> <span class="hljs-title class_">Word2Vec</span>()
.setInputCol(<span class="hljs-string">&quot;tokens&quot;</span>)
.setOutputCol(<span class="hljs-string">&quot;vectors&quot;</span>)
.setVectorSize(<span class="hljs-number">128</span>)
.setMinCount(<span class="hljs-number">0</span>)
<span class="hljs-type">val</span> <span class="hljs-variable">model</span> <span class="hljs-operator">=</span> word2Vec.fit(tokenizedDf)

<span class="hljs-type">val</span> <span class="hljs-variable">result</span> <span class="hljs-operator">=</span> model.transform(tokenizedDf)

<span class="hljs-type">val</span> <span class="hljs-variable">vectorToArrayUDF</span> <span class="hljs-operator">=</span> udf((v: Vector) =&gt; v.toArray)
<span class="hljs-comment">// Apply the UDF to the DataFrame</span>
<span class="hljs-type">val</span> <span class="hljs-variable">resultDF</span> <span class="hljs-operator">=</span> result.withColumn(<span class="hljs-string">&quot;embedding&quot;</span>, vectorToArrayUDF($<span class="hljs-string">&quot;vectors&quot;</span>))
<span class="hljs-type">val</span> <span class="hljs-variable">milvusDf</span> <span class="hljs-operator">=</span> resultDF.drop(<span class="hljs-string">&quot;tokens&quot;</span>).drop(<span class="hljs-string">&quot;vectors&quot;</span>)

milvusDf.write.format(<span class="hljs-string">&quot;milvus&quot;</span>)
.option(MILVUS_HOST, <span class="hljs-string">&quot;localhost&quot;</span>)
.option(MILVUS_PORT, <span class="hljs-string">&quot;19530&quot;</span>)
.option(MILVUS_COLLECTION_NAME, <span class="hljs-string">&quot;text_embedding&quot;</span>)
.option(MILVUS_COLLECTION_VECTOR_FIELD, <span class="hljs-string">&quot;embedding&quot;</span>)
.option(MILVUS_COLLECTION_VECTOR_DIM, <span class="hljs-string">&quot;128&quot;</span>)
.option(MILVUS_COLLECTION_PRIMARY_KEY, <span class="hljs-string">&quot;id&quot;</span>)
.mode(SaveMode.Append)
.save()
}
<button class="copy-code-btn"></button></code></pre>

<h3 id="Milvus---Transform---Milvus" class="common-anchor-header">Milvus -&gt; 转换 -&gt; Milvus</h3><p>在本演示中，我们将</p>
<ol>
<li>从 Milvus 数据集中读取数据、</li>
<li>应用转换（以 PCA 为例），以及</li>
<li>通过 Bulkinsert API 将转换后的数据写入另一个 Milvus。</li>
</ol>
<div class="alert notes">
<p>PCA 模型是一种可降低嵌入向量维度的变换模型，是机器学习中的常见操作。 你可以在变换步骤中添加任何其他处理操作，如过滤、连接或归一化。</p>
</div>
<pre><code translate="no" class="language-scala"><span class="hljs-keyword">import</span> org.apache.spark.ml.feature.PCA
<span class="hljs-keyword">import</span> org.apache.spark.ml.linalg.{Vector, Vectors}
<span class="hljs-keyword">import</span> org.apache.spark.SparkConf
<span class="hljs-keyword">import</span> org.apache.spark.sql.SparkSession
<span class="hljs-keyword">import</span> org.apache.spark.sql.functions.udf
<span class="hljs-keyword">import</span> org.apache.spark.sql.util.CaseInsensitiveStringMap
<span class="hljs-keyword">import</span> zilliztech.spark.milvus.{MilvusOptions, MilvusUtils}

<span class="hljs-keyword">import</span> scala.collection.JavaConverters.\_

object TransformDemo <span class="hljs-keyword">extends</span> <span class="hljs-title class_">App</span> {
<span class="hljs-type">val</span> <span class="hljs-variable">sparkConf</span> <span class="hljs-operator">=</span> <span class="hljs-keyword">new</span> <span class="hljs-title class_">SparkConf</span>().setMaster(<span class="hljs-string">&quot;local&quot;</span>)
<span class="hljs-type">val</span> <span class="hljs-variable">spark</span> <span class="hljs-operator">=</span> SparkSession.builder().config(sparkConf).getOrCreate()

<span class="hljs-keyword">import</span> spark.implicits.\_

<span class="hljs-type">val</span> <span class="hljs-variable">host</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;localhost&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">port</span> <span class="hljs-operator">=</span> <span class="hljs-number">19530</span>
<span class="hljs-type">val</span> <span class="hljs-variable">user</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;root&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">password</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;Milvus&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">fs</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;s3a://&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">bucketName</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;a-bucket&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">rootPath</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;files&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">minioAK</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;minioadmin&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">minioSK</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;minioadmin&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">minioEndpoint</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;localhost:9000&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">collectionName</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;hello_spark_milvus1&quot;</span>
<span class="hljs-type">val</span> <span class="hljs-variable">targetCollectionName</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;hello_spark_milvus2&quot;</span>

<span class="hljs-type">val</span> <span class="hljs-variable">properties</span> <span class="hljs-operator">=</span> Map(
MilvusOptions.MILVUS_HOST -&gt; host,
MilvusOptions.MILVUS_PORT -&gt; port.toString,
MilvusOptions.MILVUS_COLLECTION_NAME -&gt; collectionName,
MilvusOptions.MILVUS_BUCKET -&gt; bucketName,
MilvusOptions.MILVUS_ROOTPATH -&gt; rootPath,
MilvusOptions.MILVUS_FS -&gt; fs,
MilvusOptions.MILVUS_STORAGE_ENDPOINT -&gt; minioEndpoint,
MilvusOptions.MILVUS_STORAGE_USER -&gt; minioAK,
MilvusOptions.MILVUS_STORAGE_PASSWORD -&gt; minioSK,
)

<span class="hljs-comment">// 1, configurations</span>
<span class="hljs-type">val</span> <span class="hljs-variable">milvusOptions</span> <span class="hljs-operator">=</span> <span class="hljs-keyword">new</span> <span class="hljs-title class_">MilvusOptions</span>(<span class="hljs-keyword">new</span> <span class="hljs-title class_">CaseInsensitiveStringMap</span>(properties.asJava))

<span class="hljs-comment">// 2, batch read milvus collection data to dataframe</span>
<span class="hljs-comment">// Schema: dim of `embeddings` is 8</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-comment">// | | field name | field type | other attributes |</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-comment">// |1| &quot;pk&quot; | Int64 | is_primary=True |</span>
<span class="hljs-comment">// | | | | auto_id=False |</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-comment">// |2| &quot;random&quot; | Double | |</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-comment">// |3|&quot;embeddings&quot;| FloatVector| dim=8 |</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-type">val</span> <span class="hljs-variable">arrayToVectorUDF</span> <span class="hljs-operator">=</span> udf((arr: Seq[Double]) =&gt; Vectors.dense(arr.toArray[Double]))
<span class="hljs-type">val</span> <span class="hljs-variable">collectionDF</span> <span class="hljs-operator">=</span> MilvusUtils.readMilvusCollection(spark, milvusOptions)
.withColumn(<span class="hljs-string">&quot;embeddings_vec&quot;</span>, arrayToVectorUDF($<span class="hljs-string">&quot;embeddings&quot;</span>))
.drop(<span class="hljs-string">&quot;embeddings&quot;</span>)

<span class="hljs-comment">// 3. Use PCA to reduce dim of vector</span>
<span class="hljs-type">val</span> <span class="hljs-variable">dim</span> <span class="hljs-operator">=</span> <span class="hljs-number">4</span>
<span class="hljs-type">val</span> <span class="hljs-variable">pca</span> <span class="hljs-operator">=</span> <span class="hljs-keyword">new</span> <span class="hljs-title class_">PCA</span>()
.setInputCol(<span class="hljs-string">&quot;embeddings_vec&quot;</span>)
.setOutputCol(<span class="hljs-string">&quot;pca_vec&quot;</span>)
.setK(dim)
.fit(collectionDF)
<span class="hljs-type">val</span> <span class="hljs-variable">vectorToArrayUDF</span> <span class="hljs-operator">=</span> udf((v: Vector) =&gt; v.toArray)
<span class="hljs-comment">// embeddings dim number reduce to 4</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-comment">// | | field name | field type | other attributes |</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-comment">// |1| &quot;pk&quot; | Int64 | is_primary=True |</span>
<span class="hljs-comment">// | | | | auto_id=False |</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-comment">// |2| &quot;random&quot; | Double | |</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-comment">// |3|&quot;embeddings&quot;| FloatVector| dim=4 |</span>
<span class="hljs-comment">// +-+------------+------------+------------------+</span>
<span class="hljs-type">val</span> <span class="hljs-variable">pcaDf</span> <span class="hljs-operator">=</span> pca.transform(collectionDF)
.withColumn(<span class="hljs-string">&quot;embeddings&quot;</span>, vectorToArrayUDF($<span class="hljs-string">&quot;pca_vec&quot;</span>))
.select(<span class="hljs-string">&quot;pk&quot;</span>, <span class="hljs-string">&quot;random&quot;</span>, <span class="hljs-string">&quot;embeddings&quot;</span>)

<span class="hljs-comment">// 4. Write PCAed data to S3</span>
<span class="hljs-type">val</span> <span class="hljs-variable">outputPath</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;s3a://a-bucket/result&quot;</span>
pcaDf.write
.mode(<span class="hljs-string">&quot;overwrite&quot;</span>)
.format(<span class="hljs-string">&quot;parquet&quot;</span>)
.save(outputPath)

<span class="hljs-comment">// 5. Config MilvusOptions of target table </span>
<span class="hljs-type">val</span> <span class="hljs-variable">targetProperties</span> <span class="hljs-operator">=</span> Map(
MilvusOptions.MILVUS*HOST -&gt; host,
MilvusOptions.MILVUS_PORT -&gt; port.toString,
MilvusOptions.MILVUS_COLLECTION_NAME -&gt; targetCollectionName,
MilvusOptions.MILVUS_BUCKET -&gt; bucketName,
MilvusOptions.MILVUS_ROOTPATH -&gt; rootPath,
MilvusOptions.MILVUS_FS -&gt; fs,
MilvusOptions.MILVUS_STORAGE_ENDPOINT -&gt; minioEndpoint,
MilvusOptions.MILVUS_STORAGE_USER -&gt; minioAK,
MilvusOptions.MILVUS_STORAGE_PASSWORD -&gt; minioSK,
)
<span class="hljs-type">val</span> <span class="hljs-variable">targetMilvusOptions</span> <span class="hljs-operator">=</span> <span class="hljs-keyword">new</span> <span class="hljs-title class*">MilvusOptions</span>(<span class="hljs-keyword">new</span> <span class="hljs-title class_">CaseInsensitiveStringMap</span>(targetProperties.asJava))

<span class="hljs-comment">// 6. Bulkinsert Spark output files into milvus</span>
MilvusUtils.bulkInsertFromSpark(spark, targetMilvusOptions, outputPath, <span class="hljs-string">&quot;parquet&quot;</span>)
}
<button class="copy-code-btn"></button></code></pre>

<h3 id="Databricks---Zilliz-Cloud" class="common-anchor-header">Databricks -&gt; Zilliz Cloud</h3><p>如果您使用的是 Zilliz Cloud（Milvus 托管服务），您可以利用其便捷的数据导入 API。Zilliz Cloud 提供全面的工具和文档，帮助您高效地从各种数据源（包括 Spark 和 Databricks）移动数据。只需将 S3 存储桶设置为中介，并开放其对 Zilliz Cloud 账户的访问。Zilliz Cloud 的数据导入 API 会自动将 S3 存储桶中的整批数据加载到 Zilliz Cloud 集群。</p>
<p><strong>准备工作</strong></p>
<ol>
<li><p>将 jar 文件添加到 Databricks 集群，加载 Spark 运行时。</p>
<p>您可以通过不同方式安装库。本截图显示的是从本地向集群上传 jar 文件。更多信息，请参阅 Databricks 文档中的<a href="https://docs.databricks.com/en/libraries/cluster-libraries.html">集群库</a>。</p>
<p>
  
   <span class="img-wrapper"> <img translate="no" src="/docs/v2.4.x/assets/install-databricks-library.png" alt="Install Databricks Library" class="doc-image" id="install-databricks-library" />
   </span> <span class="img-wrapper"> <span>安装 Databricks 库</span> </span></p></li>
<li><p>创建一个 S3 bucket，并将其配置为 Databricks 集群的外部存储位置。</p>
<p>Bulkinsert 要求将数据存储在临时存储桶中，以便 Zilliz Cloud 能批量导入数据。您可以创建一个 S3 存储桶，并将其配置为 Databricks 的外部位置。详情请参阅<a href="https://docs.databricks.com/en/sql/language-manual/sql-ref-external-locations.html">外部位置</a>。</p></li>
<li><p>确保 Databricks 凭据的安全。</p>
<p>有关详细信息，请参阅博客 "<a href="https://www.databricks.com/blog/2018/06/04/securely-managing-credentials-in-databricks.html">在 Databricks 中安全管理凭据 "中</a>的说明。</p></li>
</ol>
<p><strong>演示</strong></p>
<p>下面是展示批量数据迁移过程的代码片段。与上述 Milvus 示例类似，你只需替换凭证和 S3 存储桶地址。</p>
<pre><code translate="no" class="language-scala"><span class="hljs-comment">// Write the data in batch into the Milvus bucket storage.</span>
<span class="hljs-type">val</span> <span class="hljs-variable">outputPath</span> <span class="hljs-operator">=</span> <span class="hljs-string">&quot;s3://my-temp-bucket/result&quot;</span>
df.write
  .mode(<span class="hljs-string">&quot;overwrite&quot;</span>)
  .format(<span class="hljs-string">&quot;mjson&quot;</span>)
  .save(outputPath)
<span class="hljs-comment">// Specify Milvus options.</span>
<span class="hljs-type">val</span> <span class="hljs-variable">targetProperties</span> <span class="hljs-operator">=</span> Map(
  MilvusOptions.MILVUS_URI -&gt; zilliz_uri,
  MilvusOptions.MILVUS_TOKEN -&gt; zilliz_token,
  MilvusOptions.MILVUS_COLLECTION_NAME -&gt; targetCollectionName,
  MilvusOptions.MILVUS_BUCKET -&gt; bucketName,
  MilvusOptions.MILVUS_ROOTPATH -&gt; rootPath,
  MilvusOptions.MILVUS_FS -&gt; fs,
  MilvusOptions.MILVUS_STORAGE_ENDPOINT -&gt; minioEndpoint,
  MilvusOptions.MILVUS_STORAGE_USER -&gt; minioAK,
  MilvusOptions.MILVUS_STORAGE_PASSWORD -&gt; minioSK,
)
<span class="hljs-type">val</span> <span class="hljs-variable">targetMilvusOptions</span> <span class="hljs-operator">=</span> <span class="hljs-keyword">new</span> <span class="hljs-title class_">MilvusOptions</span>(<span class="hljs-keyword">new</span> <span class="hljs-title class_">CaseInsensitiveStringMap</span>(targetProperties.asJava))
  
<span class="hljs-comment">// Bulk insert Spark output files into Milvus</span>
MilvusUtils.bulkInsertFromSpark(spark, targetMilvusOptions, outputPath, <span class="hljs-string">&quot;mjson&quot;</span>)
<button class="copy-code-btn"></button></code></pre>
<h2 id="Hands-on" class="common-anchor-header">实际操作<button data-href="#Hands-on" class="anchor-icon" translate="no">
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
    </button></h2><p>为了帮助您快速上手 Spark-Milvus Connector，我们准备了一本笔记本，指导您使用 Milvus 和 Zilliz Cloud 完成流式和批量数据传输过程。</p>
<ul>
<li><a href="https://zilliz.com/databricks_zilliz_demos">Spark-Milvus 连接器实践</a></li>
</ul>
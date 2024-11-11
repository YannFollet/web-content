---
id: release_notes.md
summary: Note di rilascio di Milvus
title: Note di rilascio
---
<h1 id="Release-Notes" class="common-anchor-header">Note di rilascio<button data-href="#Release-Notes" class="anchor-icon" translate="no">
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
    </button></h1><p>Scoprite le novità di Milvus! Questa pagina riassume le nuove funzionalità, i miglioramenti, i problemi noti e le correzioni di bug di ogni versione. In questa sezione si trovano le note di rilascio per ogni versione rilasciata dopo la v2.4.0. Si consiglia di visitare regolarmente questa pagina per conoscere gli aggiornamenti.</p>
<h2 id="v2415" class="common-anchor-header">v2.4.15<button data-href="#v2415" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 5 novembre 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.15</td><td>2.4.9</td><td>2.4.8</td><td>2.4.9</td></tr>
</tbody>
</table>
<p>Milvus 2.4.15 è stata una release critica per la correzione di bug, incentrata sul miglioramento della stabilità, delle prestazioni e della compatibilità del sistema. Questa versione ha risolto un grave problema di deadlock che poteva verificarsi durante gli arresti anomali di QueryNode e ha introdotto aggiornamenti di compatibilità per lo strumento di backup con la funzione database. Inoltre, Milvus 2.4.15 ha migliorato le prestazioni e la stabilità della cancellazione grazie a significative ottimizzazioni nella gestione di L0. L <strong>'aggiornamento alla versione 2.4.15 è fortemente consigliato</strong> per beneficiare di questi miglioramenti critici.</p>
<h3 id="Critical-bug-fixes" class="common-anchor-header">Correzioni di bug critici</h3><ul>
<li>Risolto un problema di deadlock se il QueryNode si bloccava durante l'inizializzazione del client shard<a href="https://github.com/milvus-io/milvus/pull/37354">(#37354</a>).</li>
<li>Ripristinato il miglioramento per il supporto dei database per l'inserimento massivo (<a href="https://github.com/milvus-io/milvus/pull/37421">#37421</a>).</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Corretto un bug per cui alcune espressioni non analizzavano correttamente i valori<a href="https://github.com/milvus-io/milvus/pull/37342">(#37342</a>).</li>
<li>Migliorato il Proxy per riprovare a ottenere il leader dello shard su collezioni non caricate<a href="https://github.com/milvus-io/milvus/pull/37326">(#37326</a>).</li>
<li>Corretto un problema per cui il valore delle metriche del conteggio delle righe L0 era sempre vuoto<a href="https://github.com/milvus-io/milvus/pull/37307">(#37307</a>).</li>
<li>Saltato il timeout della compattazione per gli scenari di compattazione mista e L0<a href="https://github.com/milvus-io/milvus/pull/37194">(#37194</a>).</li>
<li>Rettificata la logica di contenimento di OffsetOrderedArray (<a href="https://github.com/milvus-io/milvus/pull/37309">#37309</a>).</li>
<li>Aggiunto un controllo delle risorse durante il caricamento dei log delta (<a href="https://github.com/milvus-io/milvus/pull/37263">#37263</a>).</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Spostata la logica L0 al di fuori del blocco delta per migliorare le prestazioni<a href="https://github.com/milvus-io/milvus/pull/37340">(#37340</a>).</li>
<li>Rilasciati i segmenti in crescita compattati se presenti nell'elenco degli eliminati (<a href="https://github.com/milvus-io/milvus/pull/37266">#37266</a>).</li>
<li>Introdotto un middleware per monitorare le statistiche RESTful V2 input/output RPC<a href="https://github.com/milvus-io/milvus/pull/37224">(#37224</a>, <a href="https://github.com/milvus-io/milvus/pull/37440">#37440</a>).</li>
</ul>
<h2 id="v2414" class="common-anchor-header">v2.4.14<button data-href="#v2414" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 31 ottobre 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.14</td><td>2.4.9</td><td>2.4.7</td><td>2.4.9</td></tr>
</tbody>
</table>
<p>Milvus 2.4.14 risolve un problema critico della versione 2.4.13 che poteva causare la perdita di informazioni sulla raccolta dopo la garbage collection di <code translate="no">snapshotKV</code>. Ha anche risolto un paio di perdite di risorse. Inoltre, questa versione include numerosi miglioramenti volti a migliorare la stabilità delle operazioni di cancellazione su larga scala e le prestazioni di compattazione.</p>
<h3 id="Features" class="common-anchor-header">Caratteristiche</h3><ul>
<li>Supporto della modalità di memoria chunk cache<a href="https://github.com/milvus-io/milvus/pull/35836">(#35836</a>)</li>
<li>Supporto del db per bulkinsert<a href="https://github.com/milvus-io/milvus/pull/37017">(#37017</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Ottimizzazione di cancellazione/compattazione<ul>
<li>Abilitata l'esecuzione parallela delle compattazioni l0<a href="https://github.com/milvus-io/milvus/pull/36985">(#36985</a>)</li>
<li>Cancellazione in batch quando si usa l'inoltro diretto (<a href="https://github.com/milvus-io/milvus/pull/37107">#37107</a>)</li>
<li>Saltato il caricamento dei dati delta nel delegatore quando si usa remoteload (<a href="https://github.com/milvus-io/milvus/pull/37112">#37112</a>)</li>
<li>Inoltro diretto delta escludendo i segmenti l0<a href="https://github.com/milvus-io/milvus/pull/36914">(#36914</a>)</li>
<li>Aggiunta la prioritizzazione dei compiti di compattazione in DataCoord<a href="https://github.com/milvus-io/milvus/pull/36979">(#36979</a>)</li>
<li>Tracciato il tasso di cancellazioni complesse<a href="https://github.com/milvus-io/milvus/pull/36958">(#36958</a>)</li>
</ul></li>
<li>Rifatto CreateCollection nell'API RESTFul<a href="https://github.com/milvus-io/milvus/pull/36885">(#36885</a>)</li>
<li>Fusione di più operazioni 'and' e 'or' in un'unica operazione (<a href="https://github.com/milvus-io/milvus/pull/36973">#36973</a>)</li>
<li>Fatto in modo che lo skip load funzioni per tutti i rami<a href="https://github.com/milvus-io/milvus/pull/37161">(#37161</a>)</li>
<li>Aggiornata la dipendenza da Minio per supportare le identità EKS Pod (<a href="https://github.com/milvus-io/milvus/pull/37089">#37089</a>)</li>
<li>Riordinate le opzioni di importazione (<a href="https://github.com/milvus-io/milvus/pull/37078">#37078</a>)</li>
<li>Limitato il numero massimo di lavori di importazione<a href="https://github.com/milvus-io/milvus/pull/36892">(#36892</a>)</li>
<li>Preallocata la slice dei dati per evitare di riallocare la memoria<a href="https://github.com/milvus-io/milvus/pull/37044">(#37044</a>)</li>
<li>Impedito al DataNode di caricare il bf<a href="https://github.com/milvus-io/milvus/pull/37027">(#37027</a>)</li>
<li>Evitato di limitare ripetutamente le operazioni ddl (<a href="https://github.com/milvus-io/milvus/pull/37011">#37011</a>)</li>
<li>Ha reso la voce di configurazione <code translate="no">datanode.import.maxconcurrenttasknum</code> regolabile dinamicamente<a href="https://github.com/milvus-io/milvus/pull/37103">(#37103</a>)</li>
<li>Utilizzato <code translate="no">queryNode.mmap.growingMmapEnabled</code> per controllare il comportamento dell'indice intermedio<a href="https://github.com/milvus-io/milvus/pull/36391">(#36391</a>)</li>
<li>Popolato i campi <code translate="no">Level</code> e <code translate="no">StartPosition</code> in segmentLoadInfo del segmento in crescita<a href="https://github.com/milvus-io/milvus/pull/36911">(#36911</a>)</li>
<li>Forzato l'arresto dei messaggi di buffer quando si riceve il messaggio di drop collection (<a href="https://github.com/milvus-io/milvus/pull/36917">#36917</a>)</li>
<li>Aggiunte metriche per le informazioni sul buffer di cancellazione del querynode (<a href="https://github.com/milvus-io/milvus/pull/37097">#37097</a>)</li>
<li>Aggiunta l'etichetta del nome della raccolta per alcune metriche<a href="https://github.com/milvus-io/milvus/pull/37159">(#37159</a>)</li>
<li>Usato middleware per osservare le statistiche RESTful v2 in/out rpc (<a href="https://github.com/milvus-io/milvus/pull/37224">#37224</a>)</li>
<li>Modificata la dimensione del pool di memoria predefinito della GPU<a href="https://github.com/milvus-io/milvus/pull/36969">(#36969</a>)</li>
<li>Aggiornata la versione di Knowhere a 2.3.12<a href="https://github.com/milvus-io/milvus/pull/37132">(#37132</a>)</li>
<li>Consentita la cancellazione dei dati quando la quota del disco è esaurita<a href="https://github.com/milvus-io/milvus/pull/37139">(#37139</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Corrette le informazioni sulla raccolta che non potevano essere recuperate da metakv dopo il riavvio se tutte le istantanee erano state garbage collected<a href="https://github.com/milvus-io/milvus/pull/36950">(#36950</a>)</li>
<li>Corretto il codice di errore rpc per evitare un tentativo non valido nel client<a href="https://github.com/milvus-io/milvus/pull/37025">(#37025</a>)</li>
<li>Ignorato l'errore db not found in quota center (<a href="https://github.com/milvus-io/milvus/pull/36850">#36850</a>)</li>
<li>Corretta la perdita di goroutine in QueryNode usando un pool di cancellazione singleton (<a href="https://github.com/milvus-io/milvus/pull/37225">#37225</a>)</li>
<li>Corretta la perdita di raccolta in querynode<a href="https://github.com/milvus-io/milvus/pull/37079">(#37079</a>)</li>
<li>Corretta la perdita del task di compattazione del cluster (<a href="https://github.com/milvus-io/milvus/pull/36803">#36803</a>)</li>
<li>Vietato rinominare una collezione che aveva un alias<a href="https://github.com/milvus-io/milvus/pull/37208">(#37208</a>)</li>
<li>Assicurato che l'alias fosse memorizzato nella cache (<a href="https://github.com/milvus-io/milvus/pull/36808">#36808</a>)</li>
<li>La ricerca/query poteva fallire durante l'aggiornamento della cache del delegatore<a href="https://github.com/milvus-io/milvus/pull/37174">(#37174</a>)</li>
<li>Esclusa la compattazione di l0 durante l'esecuzione del clustering (<a href="https://github.com/milvus-io/milvus/pull/37142">#37142</a>)</li>
<li>Riferimento al meta della raccolta quando si caricava solo il meta del segmento l0<a href="https://github.com/milvus-io/milvus/pull/37179">(#37179</a>)</li>
<li>Il delegatore potrebbe essere diventato inservibile dopo il riavvio di querycoord<a href="https://github.com/milvus-io/milvus/pull/37100">(#37100</a>)</li>
<li>La partizione di rilascio dinamico potrebbe aver fallito la ricerca/query<a href="https://github.com/milvus-io/milvus/pull/37099">(#37099</a>)</li>
<li>Rettificato il valore della quota del conteggio delle righe del buffer di cancellazione (<a href="https://github.com/milvus-io/milvus/pull/37068">#37068</a>)</li>
<li>Passato l'elenco completo dei campi quando era abilitato il carico parziale (<a href="https://github.com/milvus-io/milvus/pull/37063">#37063</a>)</li>
<li>Si verificava un panico del nodo di query durante l'invio di rpc al worker<a href="https://github.com/milvus-io/milvus/pull/36988">(#36988</a>)</li>
<li>Datacoord si bloccava all'arresto dell'avanzamento<a href="https://github.com/milvus-io/milvus/pull/36961">(#36961</a>)</li>
<li>Corretto l'accesso fuori limite nel segmento in crescita quando i dati grezzi erano sostituiti da un indice intermedio<a href="https://github.com/milvus-io/milvus/pull/36938">(#36938</a>)</li>
<li>Rootcoord si bloccava all'arresto anticipato (<a href="https://github.com/milvus-io/milvus/pull/36881">#36881</a>)</li>
</ul>
<h2 id="v2413-hotfix" class="common-anchor-header">v2.4.13-fotografia<button data-href="#v2413-hotfix" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 17 ottobre 2024</p>
<table>
<thead>
<tr><th>Versione di Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.13-hotfix</td><td>2.4.8</td><td>2.4.5</td><td>2.4.9</td></tr>
</tbody>
</table>
<p>Milvus v2.4.13-hotfix risolve un problema critico specifico della v2.4.13, a causa del quale Milvus potrebbe non riuscire a recuperare le informazioni sulla raccolta dopo un riavvio se tutte le istantanee MetaKV sono state raccolte come spazzatura<a href="https://github.com/milvus-io/milvus/pull/36933">(#36933</a>). <strong>Si consiglia agli utenti che attualmente utilizzano la versione 2.4.13 di eseguire l'aggiornamento alla versione 2.4.13-hotfix il prima possibile per evitare potenziali interruzioni</strong>.</p>
<h3 id="Critical-fixes" class="common-anchor-header">Correzioni critiche</h3><ul>
<li>Carica la chiave originale se il timestamp è MaxTimestamp<a href="https://github.com/milvus-io/milvus/pull/36935">(#36935</a>)</li>
</ul>
<h2 id="Deprecated-v2413" class="common-anchor-header">[Deprecato] v2.4.13<button data-href="#Deprecated-v2413" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 12 ottobre 2024</p>
<table>
<thead>
<tr><th>Versione di Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.13</td><td>2.4.8</td><td>2.4.5</td><td>2.4.9</td></tr>
</tbody>
</table>
<p>Milvus 2.4.13 introduce il carico dinamico delle repliche, consentendo agli utenti di regolare il numero di repliche della collezione senza dover rilasciare e ricaricare la collezione. Questa versione risolve anche diversi bug critici relativi all'importazione in blocco, all'analisi delle espressioni, al bilanciamento del carico e al recupero dei guasti. Inoltre, sono stati apportati miglioramenti significativi all'utilizzo delle risorse MMAP e alle prestazioni di importazione, migliorando l'efficienza complessiva del sistema. Si consiglia vivamente di passare a questa versione per migliorare le prestazioni e la stabilità.</p>
<h3 id="Features" class="common-anchor-header">Caratteristiche</h3><ul>
<li>Regolazione dinamica delle repliche per le collezioni caricate<a href="https://github.com/milvus-io/milvus/pull/36417">(#36417</a>)</li>
<li>MMAP vettoriale sparse in tipi di segmento crescenti<a href="https://github.com/milvus-io/milvus/pull/36565">(#36565</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Corretto un problema di prestazioni del flush (<a href="https://github.com/milvus-io/milvus/pull/36741">#36741</a>)</li>
<li>Corretto un bug con le espressioni JSON in &quot;[]&quot;<a href="https://github.com/milvus-io/milvus/pull/36722">(#36722</a>)</li>
<li>Rimossi i vicini se il target compatto non è indicizzato<a href="https://github.com/milvus-io/milvus/pull/36694">(#36694</a>)</li>
<li>Migliorate le prestazioni di Rocksmq quando il canale è pieno<a href="https://github.com/milvus-io/milvus/pull/36618">(#36618</a>)</li>
<li>Corretto un problema per cui gli errori durante l'impacchettamento non venivano differiti (<a href="https://github.com/milvus-io/milvus/pull/36665">#36665</a>)</li>
<li>Risolta una perdita di memoria per i segmenti importati nel gestore dei segmenti<a href="https://github.com/milvus-io/milvus/pull/36631">(#36631</a>)</li>
<li>Saltati i controlli sanitari non necessari per i nodi di query nel proxy (<a href="https://github.com/milvus-io/milvus/pull/36553">#36553</a>)</li>
<li>Risolto un problema di overflow con le espressioni di termine<a href="https://github.com/milvus-io/milvus/pull/36534">(#36534</a>)</li>
<li>Registrato l'ID del nodo prima di assegnare i compiti per evitare un'errata allocazione dei compiti (<a href="https://github.com/milvus-io/milvus/pull/36493">#36493</a>)</li>
<li>Risolti i problemi di corsa ai dati nella compattazione del clustering (<a href="https://github.com/milvus-io/milvus/pull/36499">#36499</a>)</li>
<li>Aggiunto un controllo per la lunghezza massima dell'array di stringhe dopo la corrispondenza dei tipi (<a href="https://github.com/milvus-io/milvus/pull/36497">#36497</a>)</li>
<li>Risolte le condizioni di gara in modalità mix o standalone (<a href="https://github.com/milvus-io/milvus/pull/36459">#36459</a>)</li>
<li>Corretto lo sbilanciamento dei segmenti dopo ripetute operazioni di caricamento e rilascio<a href="https://github.com/milvus-io/milvus/pull/36543">(#36543</a>)</li>
<li>Corretto un caso d'angolo in cui i segmenti non potevano essere spostati da un nodo di arresto (<a href="https://github.com/milvus-io/milvus/pull/36475">#36475</a>)</li>
<li>Aggiornate correttamente le informazioni sui segmenti anche se alcuni segmenti erano mancanti<a href="https://github.com/milvus-io/milvus/pull/36729">(#36729</a>)</li>
<li>Impedito che le transazioni etcd superino il limite massimo nello snapshot KV (<a href="https://github.com/milvus-io/milvus/pull/36773">#36773</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Migliorata la stima delle risorse MMAP:<ul>
<li>Migliorato il codice relativo a MMAP in column.h<a href="https://github.com/milvus-io/milvus/pull/36521">(#36521</a>)</li>
<li>Raffinata la stima delle risorse durante il caricamento delle raccolte<a href="https://github.com/milvus-io/milvus/pull/36728">(#36728</a>)</li>
</ul></li>
<li>Miglioramenti delle prestazioni:<ul>
<li>Migliorata l'efficienza dell'analisi delle espressioni convertendo Unicode in ASCII<a href="https://github.com/milvus-io/milvus/pull/36676">(#36676</a>).</li>
<li>Abilitata la produzione parallela di messaggi per più argomenti<a href="https://github.com/milvus-io/milvus/pull/36462">(#36462</a>)</li>
<li>Ridotto l'overhead della CPU nel calcolo della dimensione del file indice<a href="https://github.com/milvus-io/milvus/pull/36580">(#36580</a>)</li>
<li>Recuperato il tipo di messaggio dall'intestazione per ridurre al minimo l'unmarshalling (<a href="https://github.com/milvus-io/milvus/pull/36454">#36454</a>)</li>
<li>Ottimizzata la politica di selezione delle repliche basata sul carico di lavoro (<a href="https://github.com/milvus-io/milvus/pull/36384">#36384</a>)</li>
</ul></li>
<li>Suddivisione dei messaggi delle attività di cancellazione per rientrare nei limiti di dimensione massima dei messaggi<a href="https://github.com/milvus-io/milvus/pull/36574">(#36574</a>)</li>
<li>Aggiunto un nuovo URL RESTful per descrivere i lavori di importazione<a href="https://github.com/milvus-io/milvus/pull/36754">(#36754</a>)</li>
<li>Ottimizzata la pianificazione delle importazioni e aggiunta una metrica del costo del tempo<a href="https://github.com/milvus-io/milvus/pull/36684">(#36684</a>)</li>
<li>Aggiunto il log dei rapporti di bilanciamento per il bilanciatore del coordinatore delle query<a href="https://github.com/milvus-io/milvus/pull/36749">(#36749</a>)</li>
<li>Passato all'uso di una configurazione GC comune (<a href="https://github.com/milvus-io/milvus/pull/36670">#36670</a>)</li>
<li>Aggiunto l'interruttore della politica di streaming forward per il delegatore<a href="https://github.com/milvus-io/milvus/pull/36712">(#36712</a>)</li>
<li>Abilitata la compattazione manuale per le raccolte senza indici<a href="https://github.com/milvus-io/milvus/pull/36581">(#36581</a>)</li>
<li>Abilitato il bilanciamento del carico sui nodi di query con capacità di memoria variabile<a href="https://github.com/milvus-io/milvus/pull/36625">(#36625</a>)</li>
<li>Caso unificato per le etichette in entrata usando metrics.label<a href="https://github.com/milvus-io/milvus/pull/36616">(#36616</a>)</li>
<li>Rese idempotenti le operazioni di trasferimento di canali/segmenti (<a href="https://github.com/milvus-io/milvus/pull/36552">#36552</a>)</li>
<li>Aggiunte metriche per monitorare il throughput delle importazioni e il conteggio delle righe importate<a href="https://github.com/milvus-io/milvus/pull/36588">(#36588</a>)</li>
<li>Impedita la creazione di oggetti timer multipli nei target<a href="https://github.com/milvus-io/milvus/pull/36573">(#36573</a>)</li>
<li>Aggiornata la versione delle espressioni e la formattazione della risposta HTTP per le espressioni<a href="https://github.com/milvus-io/milvus/pull/36467">(#36467</a>)</li>
<li>Migliorata la garbage collection in KV snapshot (<a href="https://github.com/milvus-io/milvus/pull/36793">#36793</a>)</li>
<li>Aggiunto il supporto per l'esecuzione di metodi con parametri contestuali<a href="https://github.com/milvus-io/milvus/pull/36798">(#36798</a>)</li>
</ul>
<h2 id="v2412" class="common-anchor-header">v2.4.12<button data-href="#v2412" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 26 settembre 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.12</td><td>2.4.7</td><td>2.4.4</td><td>2.4.9</td></tr>
</tbody>
</table>
<p>Milvus 2.4.12 introduce miglioramenti significativi e correzioni di bug critici. Questa versione risolve i problemi di duplicazione dei dati e migliora la velocità di recupero dei guasti, in particolare quando si gestisce un gran numero di cancellazioni. Tuttavia, persiste un problema noto per cui il recupero dei guasti può essere lento quando si eliminano grandi quantità di dati. Stiamo lavorando attivamente per risolvere questo problema.</p>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Implementato l'arresto graduale per il gestore del flowgraph<a href="https://github.com/milvus-io/milvus/pull/36358">(#36358</a>).</li>
<li>Disabilitato il controllo degli indici per i campi vettoriali non caricati<a href="https://github.com/milvus-io/milvus/pull/36280">(#36280</a>)</li>
<li>Filtrati i record di cancellazione non colpiti durante il caricamento delta (<a href="https://github.com/milvus-io/milvus/pull/36272">#36272</a>)</li>
<li>Migliorata la gestione degli errori per le eccezioni di std::stoi<a href="https://github.com/milvus-io/milvus/pull/36296">(#36296</a>)</li>
<li>Disconosciute le parole chiave come nomi di campo o nomi di campo dinamici<a href="https://github.com/milvus-io/milvus/pull/36108">(#36108</a>)</li>
<li>Aggiunte metriche per la cancellazione di voci nei segmenti L0<a href="https://github.com/milvus-io/milvus/pull/36227">(#36227</a>)</li>
<li>Implementata la politica di inoltro L0 per supportare il caricamento remoto<a href="https://github.com/milvus-io/milvus/pull/36208">(#36208</a>)</li>
<li>Aggiunto controllo del caricamento del campo RNA nel proxy (<a href="https://github.com/milvus-io/milvus/pull/36194">#36194</a>)</li>
<li>Abilitato il supporto per le righe vuote sparse (<a href="https://github.com/milvus-io/milvus/pull/36061">#36061</a>)</li>
<li>Corretta una vulnerabilità di sicurezza<a href="https://github.com/milvus-io/milvus/pull/36156">(#36156</a>)</li>
<li>Implementato un gestore di statistiche per le metriche delle dimensioni di richiesta/risposta<a href="https://github.com/milvus-io/milvus/pull/36118">(#36118</a>)</li>
<li>Corretta la stima delle dimensioni per i dati codificati degli array (<a href="https://github.com/milvus-io/milvus/pull/36379">#36379</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Risolti gli errori di tipo di metrica per le raccolte con due campi vettoriali<a href="https://github.com/milvus-io/milvus/pull/36473">(#36473</a>)</li>
<li>Corretti i problemi di buffering lungo che causano errori di ricezione della coda di messaggi<a href="https://github.com/milvus-io/milvus/pull/36425">(#36425</a>)</li>
<li>Implementato il corretto ritorno di compact-to-segments dopo il supporto della divisione (<a href="https://github.com/milvus-io/milvus/pull/36429">#36429</a>)</li>
<li>Risolti i problemi di corsa ai dati con la goroutine di controllo dell'ID del nodo (<a href="https://github.com/milvus-io/milvus/pull/36377">#36377</a>)</li>
<li>Rimosso il controllo del tipo di elemento (<a href="https://github.com/milvus-io/milvus/pull/36324">#36324</a>)</li>
<li>Risolti i problemi di accesso concorrente per i segmenti in crescita e sigillati<a href="https://github.com/milvus-io/milvus/pull/36288">(#36288</a>)</li>
<li>Implementato un futuro blocco statico (<a href="https://github.com/milvus-io/milvus/pull/36333">#36333</a>)</li>
<li>Corretto l'uso degli offset in HybridSearch<a href="https://github.com/milvus-io/milvus/pull/36287">(#36287</a>, <a href="https://github.com/milvus-io/milvus/pull/36253">#36253</a>)</li>
<li>Risolte le perdite di segmenti/canali sporchi su QueryNode<a href="https://github.com/milvus-io/milvus/pull/36259">(#36259</a>)</li>
<li>Corretta la gestione della duplicazione delle chiavi primarie<a href="https://github.com/milvus-io/milvus/pull/36274">(#36274</a>)</li>
<li>Applicata l'impostazione del tipo di metrica nelle richieste di ricerca<a href="https://github.com/milvus-io/milvus/pull/36279">(#36279</a>)</li>
<li>Corretto il problema di cancellazione della metrica stored_index_files_size<a href="https://github.com/milvus-io/milvus/pull/36161">(#36161</a>)</li>
<li>Corretto il comportamento del gruppo di privilegi di lettura per l'accesso globale all'API<a href="https://github.com/milvus-io/milvus/pull/36145">(#36145</a>)</li>
</ul>
<h2 id="v2411" class="common-anchor-header">v2.4.11<button data-href="#v2411" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 11 settembre 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.11</td><td>2.4.6</td><td>2.4.3</td><td>2.4.8</td></tr>
</tbody>
</table>
<p>Milvus 2.4.11 è una release che risolve diversi problemi critici relativi all'indice delle trie MARISA, alla compattazione e alle operazioni di caricamento. Questa release introduce nuove funzionalità per la visualizzazione delle espressioni e migliora la stabilità delle cancellazioni. Si consiglia a tutti gli utenti della serie 2.4.x di aggiornare a questa versione per beneficiare di questi miglioramenti e correzioni.</p>
<h3 id="Features" class="common-anchor-header">Caratteristiche</h3><ul>
<li>Aggiunta la visualizzazione statica per le espressioni in 2.4<a href="https://github.com/milvus-io/milvus/pull/35954">(#35954</a>)</li>
<li>Implementata la logica delle quote relative al buffer di cancellazione (<a href="https://github.com/milvus-io/milvus/pull/35997">#35997</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Risolto il problema del funzionamento dell'intervallo di indici Trie per i confronti GreaterThan e GreaterThanEqual (<a href="https://github.com/milvus-io/milvus/pull/36126">#36126</a>)</li>
<li>Corretto l'uso di <code translate="no">marisa_label_order</code> nella costruzione dell'indice Trie<a href="https://github.com/milvus-io/milvus/pull/36060">(#36060</a>)</li>
<li>Migliorato il controllo del valore per <code translate="no">trie.predictive_search</code> <a href="https://github.com/milvus-io/milvus/pull/35999">(#35999</a>)</li>
<li>Abilitato il supporto delle espressioni aritmetiche binarie sugli indici invertiti<a href="https://github.com/milvus-io/milvus/pull/36097">(#36097</a>)</li>
<li>Corretto l'errore di segmento causato da Skipindex<a href="https://github.com/milvus-io/milvus/pull/35908">(#35908</a>)</li>
<li>Risolta la perdita di memoria nella meta-cache del proxy (<a href="https://github.com/milvus-io/milvus/pull/36076">#36076</a>)</li>
<li>Rinominato il percorso del file mmap per evitare conflitti di directory<a href="https://github.com/milvus-io/milvus/pull/35975">(#35975</a>)</li>
<li>Migliorato il logging e la pulizia dei task falliti/timeout nella compattazione mix<a href="https://github.com/milvus-io/milvus/pull/35967">(#35967</a>)</li>
<li>Risolti i deadlock logici durante l'uso elevato di memoria da parte del delegatore<a href="https://github.com/milvus-io/milvus/pull/36066">(#36066</a>)</li>
<li>Implementata la creazione di segmenti vuoti quando la compattazione cancella tutti gli inserti<a href="https://github.com/milvus-io/milvus/pull/36045">(#36045</a>)</li>
<li>Corretto il popolamento dell'elenco dei campi di carico dalle informazioni di carico della vecchia versione in 2.4<a href="https://github.com/milvus-io/milvus/pull/36018">(#36018</a>)</li>
<li>Corretta la logica di aggiornamento della configurazione di tracciamento in 2.4<a href="https://github.com/milvus-io/milvus/pull/35998">(#35998</a>)</li>
<li>Risolti i fallimenti delle richieste di ricerca/query durante il rilascio di partizioni dinamiche (<a href="https://github.com/milvus-io/milvus/pull/36019">#36019</a>)</li>
<li>Impedito l'override dei parametri di fallback (<a href="https://github.com/milvus-io/milvus/pull/36006">#36006</a>)</li>
<li>Assicurata la corretta registrazione dei gruppi di privilegi per la convalida<a href="https://github.com/milvus-io/milvus/pull/35938">(#35938</a>)</li>
<li>Impedita la pulizia errata dei nodi del limitatore di db (<a href="https://github.com/milvus-io/milvus/pull/35992">#35992</a>)</li>
<li>Risolto il problema delle repliche che non partecipano alle query dopo il ripristino dei guasti<a href="https://github.com/milvus-io/milvus/pull/35925">(#35925</a>)</li>
<li>Risolta la corsa ai dati nello scrittore di compattazione del clustering (<a href="https://github.com/milvus-io/milvus/pull/35958">#35958</a>)</li>
<li>Corretto il riferimento a una variabile dopo un'operazione di spostamento (<a href="https://github.com/milvus-io/milvus/pull/35904">#35904</a>)</li>
<li>Implementato il controllo del comportamento di caricamento del salto della chiave di clustering (<a href="https://github.com/milvus-io/milvus/pull/35899">#35899</a>)</li>
<li>Assicurato l'avvio singolo degli osservatori querycoord in 2.4<a href="https://github.com/milvus-io/milvus/pull/35817">(#35817</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Aggiornata la versione di Milvus e proto a 2.4.11<a href="https://github.com/milvus-io/milvus/pull/36069">(#36069</a>)</li>
<li>Risolta la perdita di memoria nei test unitari e abilitata l'opzione use_asan per le build unittest<a href="https://github.com/milvus-io/milvus/pull/35857">(#35857</a>)</li>
<li>Adeguati i limiti di l0segmentsrowcount a valori più appropriati<a href="https://github.com/milvus-io/milvus/pull/36015">(#36015</a>)</li>
<li>Modificato il fattore di stima della memoria di deltalog a uno<a href="https://github.com/milvus-io/milvus/pull/36035">(#36035</a>)</li>
<li>Implementato slicesetequal per i confronti degli elenchi dei campi di carico (<a href="https://github.com/milvus-io/milvus/pull/36062">#36062</a>)</li>
<li>Ridotta la frequenza dei log per le operazioni di cancellazione<a href="https://github.com/milvus-io/milvus/pull/35981">(#35981</a>)</li>
<li>Aggiornata la versione di etcd a 3.5.14<a href="https://github.com/milvus-io/milvus/pull/35977">(#35977</a>)</li>
<li>Ottimizzata la riduzione di mmap-rss dopo il riscaldamento<a href="https://github.com/milvus-io/milvus/pull/35965">(#35965</a>)</li>
<li>Rimosso il periodo di raffreddamento nel limitatore di velocità per le richieste di lettura<a href="https://github.com/milvus-io/milvus/pull/35936">(#35936</a>)</li>
<li>Migliorato il controllo dei campi di carico per le raccolte caricate in precedenza<a href="https://github.com/milvus-io/milvus/pull/35910">(#35910</a>)</li>
<li>Aggiunto il supporto per l'eliminazione dei ruoli legati alle liste di privilegi in 2.4<a href="https://github.com/milvus-io/milvus/pull/35863">(#35863</a>)</li>
<li>Implementate regole di depguard per proibire l'uso di librerie proto deprecate<a href="https://github.com/milvus-io/milvus/pull/35818">(#35818</a>)</li>
</ul>
<h3 id="Others" class="common-anchor-header">Altri</h3><ul>
<li>Aggiornata la versione di Knowhere<a href="https://github.com/milvus-io/milvus/pull/36067">(#36067</a>)</li>
</ul>
<h2 id="v2410" class="common-anchor-header">v2.4.10<button data-href="#v2410" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 30 agosto 2024</p>
<table>
<thead>
<tr><th>Versione di Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.10</td><td>2.4.6</td><td>2.4.3</td><td>2.4.6</td></tr>
</tbody>
</table>
<p>Milvus 2.4.10 introduce miglioramenti significativi in termini di funzionalità e stabilità. Le caratteristiche principali includono il supporto per le operazioni di upsert su collezioni abilitate all'AutoID, capacità di caricamento parziale delle collezioni e varie configurazioni memory-mapped (MMAP) per ottimizzare l'uso della memoria. Questa versione risolve anche diversi bug che causano panico, core dump e perdite di risorse. Si consiglia di eseguire l'aggiornamento per trarre il massimo vantaggio da questi miglioramenti.</p>
<h3 id="Features" class="common-anchor-header">Caratteristiche</h3><ul>
<li><strong>Upsert con ID automatico</strong>: Supporto per le operazioni di upsert con generazione automatica di ID<a href="https://github.com/milvus-io/milvus/pull/34633">(#34633</a>).</li>
<li><strong>Caricamento parziale dei campi della raccolta</strong> [Anteprima beta]: Permette di caricare campi specifici di una raccolta<a href="https://github.com/milvus-io/milvus/pull/35696">(#35696</a>)</li>
<li><strong>Miglioramenti RBAC</strong>:<ul>
<li>Aggiunto il supporto per i messaggi RBAC per il Change Data Capture (CDC)<a href="https://github.com/milvus-io/milvus/pull/35562">(#35562</a>).</li>
<li>Introdotti gruppi di privilegi readonly/readwrite/admin per semplificare il processo di concessione RBAC (<a href="https://github.com/milvus-io/milvus/pull/35543">#35543</a>)</li>
<li>Nuova API per il backup e il ripristino delle configurazioni RBAC<a href="https://github.com/milvus-io/milvus/pull/35513">(#35513</a>)</li>
<li>Aggiornamento della cache proxy dopo il ripristino dei metadati RBAC<a href="https://github.com/milvus-io/milvus/pull/35636">(#35636</a>)</li>
</ul></li>
<li><strong>Configurazione MMAP migliorata</strong>: Più opzioni di configurazione generale per controllare il comportamento di MMAP<a href="https://github.com/milvus-io/milvus/pull/35609">(#35609</a>)</li>
<li><strong>Restrizioni di accesso ai database</strong>: Nuove proprietà per limitare l'accesso in lettura ai database<a href="https://github.com/milvus-io/milvus/pull/35754">(#35754</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Corretto il problema del client Arrow Go che non restituisce errori<a href="https://github.com/milvus-io/milvus/pull/35820">(#35820</a>)</li>
<li>Corretta la limitazione imprecisa della velocità (<a href="https://github.com/milvus-io/milvus/pull/35700">#35700</a>)</li>
<li>Risolto il panico del proxy dopo i fallimenti dell'API legati all'importazione (<a href="https://github.com/milvus-io/milvus/pull/35559">#35559</a>)</li>
<li>Corrette potenziali cancellazioni errate durante i checkpoint del canale GC (<a href="https://github.com/milvus-io/milvus/pull/35708">#35708</a>)</li>
<li>Risolto il panico dovuto a segmenti di importazione candidati vuoti (<a href="https://github.com/milvus-io/milvus/pull/35674">#35674</a>)</li>
<li>Corretta la deallocazione della memoria mmap (<a href="https://github.com/milvus-io/milvus/pull/35726">#35726</a>)</li>
<li>Assicurato il corretto controllo dei canali per gli aggiornamenti da 2.2 a 2.4<a href="https://github.com/milvus-io/milvus/pull/35695">(#35695</a>)</li>
<li>Corretta la funzione di rilascio del canale da parte del DataNode unwatching (<a href="https://github.com/milvus-io/milvus/pull/35657">#35657</a>)</li>
<li>Corretto il conteggio delle partizioni nei metadati RootCoord (<a href="https://github.com/milvus-io/milvus/pull/35601">#35601</a>)</li>
<li>Risolti i problemi con gli aggiornamenti dinamici della configurazione per alcuni parametri<a href="https://github.com/milvus-io/milvus/pull/35637">(#35637</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><h4 id="Performance" class="common-anchor-header">Prestazioni</h4><ul>
<li>Ottimizzato il recupero dei campi dinamici<a href="https://github.com/milvus-io/milvus/pull/35602">(#35602</a>)</li>
<li>Migliorate le prestazioni del bitset per AVX512<a href="https://github.com/milvus-io/milvus/pull/35480">(#35480</a>)</li>
<li>Rilettura del valore dopo l'inizializzazione di <code translate="no">once</code> per una migliore efficienza<a href="https://github.com/milvus-io/milvus/pull/35643">(#35643</a>)</li>
</ul>
<h4 id="Rolling-upgrade-improvements" class="common-anchor-header">Miglioramenti all'aggiornamento continuo</h4><ul>
<li>Contrassegnato il nodo di query come di sola lettura dopo la sospensione<a href="https://github.com/milvus-io/milvus/pull/35586">(#35586</a>)</li>
<li>Impedita la coesistenza del vecchio coordinatore con il nuovo nodo/proxy (<a href="https://github.com/milvus-io/milvus/pull/35760">#35760</a>)</li>
</ul>
<h4 id="Others" class="common-anchor-header">Altri</h4><ul>
<li>Ottimizzato il processo di costruzione del nucleo di Milvus (<a href="https://github.com/milvus-io/milvus/pull/35660">#35660</a>)</li>
<li>Aggiornato a protobuf-go v2<a href="https://github.com/milvus-io/milvus/pull/35555">(#35555</a>)</li>
<li>Migliorato il tracciamento con la codifica di stringhe esadecimali per traceid e spanid<a href="https://github.com/milvus-io/milvus/pull/35568">(#35568</a>)</li>
<li>Aggiunta la metrica del numero di segmenti hit per l'hook delle query (<a href="https://github.com/milvus-io/milvus/pull/35619">#35619</a>)</li>
<li>Migliorata la compatibilità con il vecchio SDK per la funzione configure load param (<a href="https://github.com/milvus-io/milvus/pull/35573">#35573</a>)</li>
<li>Aggiunto il supporto per il throttling HTTP v1/v2<a href="https://github.com/milvus-io/milvus/pull/35504">(#35504</a>)</li>
<li>Corretta la stima della memoria dell'indice (<a href="https://github.com/milvus-io/milvus/pull/35670">#35670</a>)</li>
<li>Possibilità di scrivere più segmenti nel compattatore di mix per evitare la generazione di segmenti di grandi dimensioni<a href="https://github.com/milvus-io/milvus/pull/35648">(#35648</a>)</li>
</ul>
<h2 id="v249" class="common-anchor-header">v2.4.9<button data-href="#v249" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 20 agosto 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.9</td><td>2.4.5</td><td>2.4.3</td><td>2.4.4</td></tr>
</tbody>
</table>
<p>Milvus v2.4.9 risolve un problema critico che poteva restituire risultati inferiori al limite (topk) in alcuni casi particolari e include diversi miglioramenti chiave per migliorare le prestazioni e l'usabilità della piattaforma.</p>
<h3 id="Critical-fixes" class="common-anchor-header">Correzioni critiche</h3><ul>
<li>Esclusione del segmento l0 dallo snapshot leggibile<a href="https://github.com/milvus-io/milvus/pull/35510">(#35510</a>).</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Eliminata la creazione di helper di schema duplicati nel proxy<a href="https://github.com/milvus-io/milvus/pull/35502">(#35502</a>).</li>
<li>Aggiunto il supporto per la compilazione di Milvus su Ubuntu 20.04<a href="https://github.com/milvus-io/milvus/pull/35457">(#35457</a>).</li>
<li>Ottimizzato l'uso dei lock ed evitato il doppio flush del buffer writer del clustering (<a href="https://github.com/milvus-io/milvus/pull/35490">#35490</a>).</li>
<li>Rimosso il log non valido<a href="https://github.com/milvus-io/milvus/pull/35473">(#35473</a>).</li>
<li>Aggiunta una guida all'uso della compattazione del clustering (<a href="https://github.com/milvus-io/milvus/pull/35428">#35428</a>).</li>
<li>Aggiunto il supporto per i campi dinamici nello schema helper<a href="https://github.com/milvus-io/milvus/pull/35469">(#35469</a>).</li>
<li>Aggiunta la sezione msgchannel nello YAML generato<a href="https://github.com/milvus-io/milvus/pull/35466">(#35466</a>).</li>
</ul>
<h2 id="v248" class="common-anchor-header">v2.4.8<button data-href="#v248" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 14 agosto 2024</p>
<table>
<thead>
<tr><th>Versione di Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.8</td><td>2.4.5</td><td>2.4.3</td><td>2.4.4</td></tr>
</tbody>
</table>
<p>Milvus 2.4.8 ha introdotto diversi miglioramenti significativi alle prestazioni e alla stabilità del sistema. La caratteristica più importante è stata l'implementazione della compattazione del clustering, un meccanismo che migliora l'efficienza della ricerca e delle interrogazioni ridistribuendo i dati in grandi collezioni in base a una chiave di clustering designata, riducendo la quantità di dati scansionati. La compattazione è stata anche disaccoppiata dallo shard DataNode, consentendo a qualsiasi DataNode di eseguire la compattazione in modo indipendente, migliorando la tolleranza agli errori, la stabilità, le prestazioni e la scalabilità. Inoltre, l'interfaccia tra i componenti Go e C++ è stata rifattorizzata per utilizzare chiamate CGO asincrone, risolvendo problemi come i timeout di sessione, mentre sono state apportate diverse altre ottimizzazioni delle prestazioni basate sulla profilazione. Le dipendenze dell'applicazione sono state aggiornate per risolvere le vulnerabilità di sicurezza note. Inoltre, questa versione include anche numerose ottimizzazioni delle prestazioni e correzioni di bug critici.</p>
<h3 id="Features" class="common-anchor-header">Caratteristiche</h3><ul>
<li>Implementata la compattazione del clustering, che consente di ridistribuire i dati in base a una chiave di clustering designata per migliorare l'efficienza delle query<a href="https://github.com/milvus-io/milvus/pull/34326">(#34326</a>),<a href="https://github.com/milvus-io/milvus/pull/34363">(#34363</a>).</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Implementate le funzionalità di ricerca e recupero asincrono in CGO.<a href="https://github.com/milvus-io/milvus/pull/34200">(#34200</a>)</li>
<li>Separato il processo di compattazione dallo Shard DataNode per migliorare la modularità del sistema.<a href="https://github.com/milvus-io/milvus/pull/34157">(#34157</a>)</li>
<li>Aggiunto il supporto per il pooling dei client in QueryNode all'interno del proxy/delegatore per migliorare le prestazioni.<a href="https://github.com/milvus-io/milvus/pull/35195">(#35195</a>)</li>
<li>Integrato Sonic per minimizzare l'overhead della CPU durante il marshaling e l'unmarshaling di JSON nei gestori Gin e RestfulV1.<a href="https://github.com/milvus-io/milvus/pull/35018">(#35018</a>)</li>
<li>Introdotta una cache in memoria per ottimizzare il recupero dei risultati dell'autenticazione.<a href="https://github.com/milvus-io/milvus/pull/35272">(#35272</a>)</li>
<li>Modificato il tipo di metrica predefinito per l'autoindex.<a href="https://github.com/milvus-io/milvus/pull/34277">[#34277</a>, <a href="https://github.com/milvus-io/milvus/pull/34479">#34479</a>]</li>
<li>Rifatto il formato della memoria di runtime per le colonne variabili, con conseguente riduzione dell'uso della memoria.<a href="https://github.com/milvus-io/milvus/pull/34367">[#34367</a>, <a href="https://github.com/milvus-io/milvus/pull/35012">#35012</a>, <a href="https://github.com/milvus-io/milvus/pull/35041">#35041</a>]</li>
<li>Ritoccati i processi di compattazione per consentire la memorizzazione persistente dei dati.<a href="https://github.com/milvus-io/milvus/pull/34268">(#34268</a>)</li>
<li>Abilitato il supporto di file mappati in memoria per segmenti crescenti, migliorando la gestione della memoria.<a href="https://github.com/milvus-io/milvus/pull/34110">(#34110</a>)</li>
<li>Migliorati i registri di accesso aggiungendo il supporto per le API RESTful, i livelli di consistenza dei registri e la distinzione tra errori di sistema e errori dell'utente.<a href="https://github.com/milvus-io/milvus/pull/34295">[#34295</a>, <a href="https://github.com/milvus-io/milvus/pull/34352">#34352</a>, <a href="https://github.com/milvus-io/milvus/pull/34396">#34396</a>]</li>
<li>Utilizzato il nuovo parametro <code translate="no">range_search_k</code> in Knowhere per velocizzare le ricerche di intervallo.<a href="https://github.com/milvus-io/milvus/pull/34709">(#34709</a>)</li>
<li>Applicati i filtri Bloom bloccati per migliorare la velocità di costruzione dei filtri e di interrogazione.<a href="https://github.com/milvus-io/milvus/pull/34377">[#34377</a>, <a href="https://github.com/milvus-io/milvus/pull/34922">#34922</a>]</li>
<li>Miglioramenti nell'uso della memoria:<ul>
<li>Spazio preallocato per i buffer di inserimento dei DataNode.<a href="https://github.com/milvus-io/milvus/pull/34205">(#34205</a>)</li>
<li>Preallocazione di <code translate="no">FieldData</code> per le operazioni di riduzione.<a href="https://github.com/milvus-io/milvus/pull/34254">(#34254</a>)</li>
<li>Rilasciati i record nel codec di cancellazione per evitare perdite di memoria.<a href="https://github.com/milvus-io/milvus/pull/34506">(#34506</a>)</li>
<li>Controllato il livello di concorrenza del file manager del disco durante il caricamento dei file.<a href="https://github.com/milvus-io/milvus/pull/35282">(#35282</a>)</li>
<li>Ottimizzata la logica di garbage collection del runtime di Go per un rilascio tempestivo della memoria.<a href="https://github.com/milvus-io/milvus/pull/34950">(#34950</a>)</li>
<li>Implementata una nuova politica di tenuta per i segmenti in crescita.<a href="https://github.com/milvus-io/milvus/pull/34779">(#34779</a>)</li>
</ul></li>
<li>Miglioramenti a DataCoord:<ul>
<li>Riduzione dell'uso della CPU.<a href="https://github.com/milvus-io/milvus/pull/34231">[#34231</a>, <a href="https://github.com/milvus-io/milvus/pull/34309">#34309</a>]</li>
<li>Implementata una logica di uscita dalla garbage collection più veloce.<a href="https://github.com/milvus-io/milvus/pull/35051">(#35051</a>)</li>
<li>Migliorati gli algoritmi di pianificazione dei nodi worker.<a href="https://github.com/milvus-io/milvus/pull/34382">(#34382</a>)</li>
<li>Migliorato l'algoritmo di controllo delle dimensioni dei segmenti, in particolare per le operazioni di importazione.<a href="https://github.com/milvus-io/milvus/pull/35149">(#35149</a>)</li>
</ul></li>
<li>Miglioramenti all'algoritmo di bilanciamento del carico:<ul>
<li>Riduzione del fattore di sovraccarico della memoria sul delegatore.<a href="https://github.com/milvus-io/milvus/pull/35164">(#35164</a>)</li>
<li>Allocazione di una dimensione di memoria fissa per il delegatore.<a href="https://github.com/milvus-io/milvus/pull/34600">(#34600</a>)</li>
<li>Evitata l'allocazione eccessiva di segmenti e canali per i nuovi nodi di interrogazione.<a href="https://github.com/milvus-io/milvus/pull/34245">(#34245</a>)</li>
<li>Riduzione del numero di compiti per ciclo di pianificazione da parte del Query Coordinator, pur aumentando la frequenza di pianificazione.<a href="https://github.com/milvus-io/milvus/pull/34987">(#34987</a>)</li>
<li>Migliorato l'algoritmo di bilanciamento dei canali sul DataNode (<a href="https://github.com/milvus-io/milvus/pull/35033">#35033</a>).</li>
</ul></li>
<li>Espansione delle metriche di sistema: Aggiunte nuove metriche su vari componenti per monitorare aspetti specifici, tra cui:<ul>
<li>stato di force-deny-writing.<a href="https://github.com/milvus-io/milvus/pull/34989">(#34989</a>)</li>
<li>Latenza della coda.<a href="https://github.com/milvus-io/milvus/pull/34788">(#34788</a>)</li>
<li>Quota disco.<a href="https://github.com/milvus-io/milvus/pull/35306">(#35306</a>)</li>
<li>Tempo di esecuzione dei task.<a href="https://github.com/milvus-io/milvus/pull/35141">(#35141</a>)</li>
<li>Dimensione del Binlog.<a href="https://github.com/milvus-io/milvus/pull/35235">(#35235</a>)</li>
<li>Velocità di inserimento.<a href="https://github.com/milvus-io/milvus/pull/35188">(#35188</a>)</li>
<li>Livello alto della memoria.<a href="https://github.com/milvus-io/milvus/pull/35188">(#35188</a>)</li>
<li>Metriche API RESTful.<a href="https://github.com/milvus-io/milvus/pull/35083">(#35083</a>)</li>
<li>Latenza di ricerca.<a href="https://github.com/milvus-io/milvus/pull/34783">(#34783</a>)</li>
</ul></li>
</ul>
<h3 id="Changes" class="common-anchor-header">Modifiche</h3><ul>
<li><p>Per gli utenti open-source, questa versione cambia i tipi di metrica in AutoIndex per <code translate="no">FloatVector</code> e <code translate="no">BinaryVector</code> in <code translate="no">Cosine</code> e <code translate="no">Hamming</code>, rispettivamente.</p></li>
<li><p><strong>Versioni fisse di dipendenze di terze parti</strong>:</p>
<ul>
<li>Questa versione introduce versioni fisse per alcune librerie di dipendenza di terze parti, migliorando in modo significativo la gestione della catena di fornitura del software di Milvus.</li>
<li>Isolando il progetto dalle modifiche a monte, salvaguarda le build quotidiane da potenziali interruzioni.</li>
<li>L'aggiornamento garantisce la stabilità ospitando esclusivamente pacchetti C++ convalidati di terze parti su JFrog Cloud e utilizzando Conan Recipe Revisions (RREV).</li>
<li>Questo approccio attenua il rischio di rottura delle modifiche derivanti dagli aggiornamenti in ConanCenter.</li>
<li>Gli sviluppatori che utilizzano Ubuntu 22.04 beneficeranno immediatamente di queste modifiche. Tuttavia, gli sviluppatori che utilizzano altri sistemi operativi potrebbero dover aggiornare la versione di <code translate="no">glibc</code> per evitare problemi di compatibilità.</li>
</ul></li>
</ul>
<h3 id="Critical-bug-fixes" class="common-anchor-header">Correzioni di bug critici</h3><ul>
<li>Corretto un problema per cui i dati di cancellazione andavano persi a causa dell'omissione di segmenti durante la compattazione L0.<a href="https://github.com/milvus-io/milvus/pull/33980">[#33980</a>, <a href="https://github.com/milvus-io/milvus/pull/34363">#34363</a>]</li>
<li>Corretto un problema per cui i messaggi di cancellazione non venivano inoltrati a causa di una gestione errata dell'ambito dei dati.<a href="https://github.com/milvus-io/milvus/pull/35313">(#35313</a>)</li>
<li>Risolta un'eccezione SIGBUS che si verificava a causa di un uso non corretto di <code translate="no">mmap</code>.<a href="https://github.com/milvus-io/milvus/pull/34455">[#34455</a>, <a href="https://github.com/milvus-io/milvus/pull/34530">#34530</a>]</li>
<li>Corretti gli arresti anomali causati da espressioni di ricerca illegali.<a href="https://github.com/milvus-io/milvus/pull/35307">(#35307</a>)</li>
<li>Corretto un problema per cui l'orologio DataNode falliva a causa di un'impostazione errata del timeout nel contesto dell'orologio.<a href="https://github.com/milvus-io/milvus/pull/35017">(#35017</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Risolte le vulnerabilità di sicurezza aggiornando alcune dipendenze.<a href="https://github.com/milvus-io/milvus/pull/33927">[#33927</a>, <a href="https://github.com/milvus-io/milvus/pull/34693">#34693</a>]</li>
<li>Corretto un errore di parsing causato da espressioni troppo lunghe.<a href="https://github.com/milvus-io/milvus/pull/34957">(#34957</a>)</li>
<li>Risolta una perdita di memoria che si verificava durante l'analisi del piano di query.<a href="https://github.com/milvus-io/milvus/pull/34932">(#34932</a>)</li>
<li>Corretto un problema per cui le modifiche al livello di log dinamico non avevano effetto.<a href="https://github.com/milvus-io/milvus/pull/34777">(#34777</a>)</li>
<li>Risolto un problema per cui le query group by su dati in crescita fallivano a causa di offset di segmento non inizializzati.<a href="https://github.com/milvus-io/milvus/pull/34750">(#34750</a>)</li>
<li>Corretta l'impostazione dei parametri di ricerca quando si usa l'iteratore Knowhere.<a href="https://github.com/milvus-io/milvus/pull/34732">(#34732</a>)</li>
<li>Rivista la logica per il controllo dello stato del caricamento della partizione.<a href="https://github.com/milvus-io/milvus/pull/34305">(#34305</a>)</li>
<li>Corretto un problema per cui gli aggiornamenti della cache dei privilegi non riuscivano a causa di errori di richiesta non gestiti.<a href="https://github.com/milvus-io/milvus/pull/34697">(#34697</a>)</li>
<li>Risolto un errore nel recupero della collezione caricata dopo il riavvio di QueryCoord.<a href="https://github.com/milvus-io/milvus/pull/35211">(#35211</a>)</li>
<li>Risolto un problema di idempotenza del carico eliminando la convalida non necessaria dei parametri dell'indice.<a href="https://github.com/milvus-io/milvus/pull/35179">(#35179</a>)</li>
<li>Assicurata l'esecuzione di <code translate="no">compressBinlog</code> per consentire a <code translate="no">reloadFromKV</code> di riempire correttamente <code translate="no">logID</code> di binlog dopo il riavvio di DataCoord.<a href="https://github.com/milvus-io/milvus/pull/34062">(#34062</a>)</li>
<li>Corretto un problema per cui i metadati della raccolta non venivano rimossi dopo la garbage collection in DataCoord.<a href="https://github.com/milvus-io/milvus/pull/34884">(#34884</a>)</li>
<li>Risolta una perdita di memoria in SegmentManager all'interno di DataCoord rimuovendo i segmenti flussati generati attraverso le importazioni.<a href="https://github.com/milvus-io/milvus/pull/34651">(#34651</a>)</li>
<li>Risolto un problema di panico quando la compattazione era disabilitata e una raccolta veniva abbandonata.<a href="https://github.com/milvus-io/milvus/pull/34206">(#34206</a>)</li>
<li>Corretto un problema di esaurimento della memoria in DataNode migliorando l'algoritmo di stima dell'uso della memoria.<a href="https://github.com/milvus-io/milvus/pull/34203">(#34203</a>)</li>
<li>Impedito l'utilizzo a raffica della memoria quando più richieste di recupero di vettori hanno un miss della cache, implementando il singleflight per la cache dei chunk.<a href="https://github.com/milvus-io/milvus/pull/34283">(#34283</a>)</li>
<li>Catturato <code translate="no">ErrKeyNotFound</code> durante le operazioni CAS (Compare and Swap) nella configurazione.<a href="https://github.com/milvus-io/milvus/pull/34489">(#34489</a>)</li>
<li>Corretto un problema per cui gli aggiornamenti della configurazione fallivano a causa dell'uso errato del valore formattato in un'operazione CAS.<a href="https://github.com/milvus-io/milvus/pull/34373">(#34373</a>)</li>
</ul>
<h3 id="Miscellaneous" class="common-anchor-header">Varie</h3><ul>
<li>Aggiunto il supporto per l'esportatore HTTP OTLP, migliorando le capacità di osservazione e monitoraggio.<a href="https://github.com/milvus-io/milvus/pull/35073">[#35073</a>, <a href="https://github.com/milvus-io/milvus/pull/35299">#35299</a>]</li>
<li>Migliorata la funzionalità del database introducendo proprietà come "max collections" e "disk quota", che ora possono essere modificate dinamicamente.<a href="https://github.com/milvus-io/milvus/pull/34511">[#34511</a>, <a href="https://github.com/milvus-io/milvus/pull/34386">#34386</a>]</li>
<li>Aggiunte funzionalità di tracciamento per i processi di compattazione L0 all'interno di DataNode per migliorare la diagnostica e il monitoraggio.<a href="https://github.com/milvus-io/milvus/pull/33898">(#33898</a>)</li>
<li>Introdotta la configurazione della quota per il numero di voci di segmento L0 per raccolta, consentendo un migliore controllo dei tassi di cancellazione applicando una pressione all'indietro.<a href="https://github.com/milvus-io/milvus/pull/34837">(#34837</a>)</li>
<li>Esteso il meccanismo di limitazione della velocità per le operazioni di inserimento anche alle operazioni di upsert, garantendo prestazioni costanti in condizioni di carico elevato.<a href="https://github.com/milvus-io/milvus/pull/34616">(#34616</a>)</li>
<li>Implementato un pool CGO dinamico per le chiamate proxy CGO, ottimizzando l'uso delle risorse e le prestazioni.<a href="https://github.com/milvus-io/milvus/pull/34842">(#34842</a>)</li>
<li>Abilitata l'opzione di compilazione DiskAnn per i sistemi operativi Ubuntu, Rocky e Amazon, migliorando la compatibilità e le prestazioni su queste piattaforme.<a href="https://github.com/milvus-io/milvus/pull/34244">(#34244</a>)</li>
<li>Aggiornato Conan alla versione 1.64.1, per garantire la compatibilità con le funzioni e i miglioramenti più recenti.<a href="https://github.com/milvus-io/milvus/pull/35216">(#35216</a>)</li>
<li>Aggiornato Knowhere alla versione 2.3.7, con miglioramenti delle prestazioni e nuove funzionalità.<a href="https://github.com/milvus-io/milvus/pull/34709">(#34709</a>)</li>
<li>Corretta la revisione di specifici pacchetti di terze parti per garantire build coerenti e ridurre il rischio di modifiche inattese.<a href="https://github.com/milvus-io/milvus/pull/35316">(#35316</a>)</li>
</ul>
<h2 id="v246" class="common-anchor-header">v2.4.6<button data-href="#v246" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 16 luglio 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.6</td><td>2.4.4</td><td>2.4.2</td><td>2.4.4</td></tr>
</tbody>
</table>
<p>Milvus v2.4.6 è una release di correzione di bug che risolve problemi critici come panico, perdite di memoria e perdita di dati durante le cancellazioni. Introduce inoltre diverse ottimizzazioni, tra cui miglioramenti alle metriche di monitoraggio, l'aggiornamento della versione Go alla 1.21 e il miglioramento dell'esperienza utente per le query RESTful count(*).</p>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Migliorata la facilità d'uso delle query API RESTful<a href="https://github.com/milvus-io/milvus/pull/34444">(#34444</a>).</li>
<li>Aggiornata la versione di Go da 1.20 a 1.21<a href="https://github.com/milvus-io/milvus/pull/33940">(#33940</a>).</li>
<li>Ottimizzato il bucket della metrica dell'istogramma per una granularità più fine nel bucketing (<a href="https://github.com/milvus-io/milvus/pull/34592">#34592</a>).</li>
<li>Aggiornata la versione delle dipendenze di Pulsar da 2.8.2 a 2.9.5. Si raccomanda di aggiornare Pulsar alla versione 2.9.5 da Milvus 2.4.6.</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Corretto un problema per cui l'API GetReplicas restituiva uno stato nullo<a href="https://github.com/milvus-io/milvus/pull/34019">(#34019</a>).</li>
<li>Corretto un problema per cui le query potevano restituire record cancellati<a href="https://github.com/milvus-io/milvus/pull/34502">(#34502</a>).</li>
<li>Risolto un problema per cui IndexNode si bloccava durante l'arresto a causa di un controllo errato della durata (<a href="https://github.com/milvus-io/milvus/pull/34559">#34559</a>).</li>
<li>Corretta una perdita di memoria degli oggetti oracolo a chiave primaria quando un worker è offline (<a href="https://github.com/milvus-io/milvus/pull/34020">#34020</a>).</li>
<li>Corretto ChannelManagerImplV2 per notificare il nodo corretto, risolvendo i problemi di cattura dei parametri nella chiusura del ciclo<a href="https://github.com/milvus-io/milvus/pull/34004">(#34004</a>).</li>
<li>Corretta una corsa di dati in lettura e scrittura in ImportTask segmentsInfo implementando una copia profonda (<a href="https://github.com/milvus-io/milvus/pull/34126">#34126</a>).</li>
<li>Corrette le informazioni sulla versione per l'opzione di configurazione "legacyVersionWithoutRPCWatch", per evitare errori durante gli aggiornamenti periodici (<a href="https://github.com/milvus-io/milvus/pull/34185">#34185</a>).</li>
<li>Corretta la metrica per il numero di partizioni caricate<a href="https://github.com/milvus-io/milvus/pull/34195">(#34195</a>).</li>
<li>Passata la configurazione di <code translate="no">otlpSecure</code> quando si imposta il tracciamento di segcore<a href="https://github.com/milvus-io/milvus/pull/34210">(#34210</a>).</li>
<li>Risolto un problema per cui le proprietà di DataCoord venivano sovrascritte per errore<a href="https://github.com/milvus-io/milvus/pull/34240">(#34240</a>).</li>
<li>Risolto un problema di perdita di dati causato dall'unione errata di due flussi di messaggi appena creati<a href="https://github.com/milvus-io/milvus/pull/34563">(#34563</a>).</li>
<li>Corretto un panico causato da msgstream che cercava di consumare un pchannel non valido<a href="https://github.com/milvus-io/milvus/pull/34230">(#34230</a>).</li>
<li>Risolto un problema per cui le importazioni potevano generare file orfani (<a href="https://github.com/milvus-io/milvus/pull/34071">#34071</a>).</li>
<li>Risolti i risultati incompleti delle query a causa di chiavi primarie duplicate in un segmento<a href="https://github.com/milvus-io/milvus/pull/34302">(#34302</a>).</li>
<li>Risolto un problema di segmenti sigillati mancanti nella compattazione L0<a href="https://github.com/milvus-io/milvus/pull/34566">(#34566</a>).</li>
<li>Risolto il problema dei dati sporchi nel meta canale-cp generato dopo la garbage collection<a href="https://github.com/milvus-io/milvus/pull/34609">(#34609</a>).</li>
<li>Corretta la metrica in cui database_num era 0 dopo il riavvio di RootCoord<a href="https://github.com/milvus-io/milvus/pull/34010">(#34010</a>).</li>
<li>Corretta una perdita di memoria in SegmentManager in DataCoord rimuovendo i segmenti generati dall'importazione (<a href="https://github.com/milvus-io/milvus/pull/34652">#34652</a>).</li>
<li>Assicurato che compressBinlog riempia il logID dei binlog dopo il riavvio di DataCoord, garantendo il corretto ricarico da KV<a href="https://github.com/milvus-io/milvus/pull/34064">(#34064</a>).</li>
</ul>
<h2 id="v245" class="common-anchor-header">v2.4.5<button data-href="#v245" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 18 giugno 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.5</td><td>2.4.4</td><td>2.4.1</td><td>2.4.3</td></tr>
</tbody>
</table>
<p>Il rilascio di Milvus 2.4.5 introduce diversi miglioramenti e correzioni di bug per migliorare le prestazioni, la stabilità e la funzionalità. Milvus 2.4.5 semplifica la ricerca di vettori sparsi, float16 e bfloat16 con l'indicizzazione automatica, velocizza le ricerche, le cancellazioni e le compattazioni con le ottimizzazioni del filtro Bloom e affronta la gestione dei dati con tempi di caricamento più rapidi e il supporto dei segmenti L0 importati. Inoltre, introduce l'indice sparse HNSW per una ricerca efficiente di dati sparsi ad alta dimensione, migliora l'API RESTful con il supporto dei vettori sparse float e corregge i bug critici per una maggiore stabilità.</p>
<h3 id="New-Features" class="common-anchor-header">Nuove funzioni</h3><ul>
<li>Aggiunto il supporto rbac all'API describe/alter database<a href="https://github.com/milvus-io/milvus/pull/33804">(#33804</a>)</li>
<li>Supportata la costruzione dell'indice HNSW per i vettori sparsi<a href="https://github.com/milvus-io/milvus/pull/33653">(#33653</a>, <a href="https://github.com/milvus-io/milvus/pull/33662">#33662</a>)</li>
<li>Supportata la costruzione dell'indice Disk per i vettori binari<a href="https://github.com/milvus-io/milvus/pull/33575">(#33575</a>)</li>
<li>Supportato il tipo di vettore sparse su RESTful v2<a href="https://github.com/milvus-io/milvus/pull/33555">(#33555</a>)</li>
<li>Aggiunta l'API RESTful /management/stop per fermare un componente<a href="https://github.com/milvus-io/milvus/pull/33799">(#33799</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Impostare il valore predefinito di maxPartitionNum a 1024<a href="https://github.com/milvus-io/milvus/pull/33950">(#33950</a>)</li>
<li>Abilitato il reset forzato della connessione in caso di errore di non disponibilità (<a href="https://github.com/milvus-io/milvus/pull/33910">#33910</a>)</li>
<li>Abilitato il limitatore della velocità di lavaggio del livello di raccolta (<a href="https://github.com/milvus-io/milvus/pull/33864">#33864</a>)</li>
<li>Eseguita l'applicazione del filtro bloom in parallelo per velocizzare la previsione dei segmenti (<a href="https://github.com/milvus-io/milvus/pull/33793">#33793</a>)</li>
<li>Usato fastjson lib per unmarshal delete log per velocizzare json.Unmarshal<a href="https://github.com/milvus-io/milvus/pull/33802">(#33802</a>)</li>
<li>Usato BatchPkExist per ridurre il costo delle chiamate alle funzioni del filtro bloom (<a href="https://github.com/milvus-io/milvus/pull/33752">#33752</a>)</li>
<li>Velocizzato il caricamento di piccole raccolte<a href="https://github.com/milvus-io/milvus/pull/33746">(#33746</a>)</li>
<li>Supportata l'importazione di dati di cancellazione nel segmento L0 (<a href="https://github.com/milvus-io/milvus/pull/33712">#33712</a>)</li>
<li>Saltate le attività di compattazione dei marchi per evitare l'esecuzione ripetuta della stessa attività (<a href="https://github.com/milvus-io/milvus/pull/33833">#33833</a>).</li>
<li>Gestiti i vettori float16 e bfloat16 come BinaryVector in numpy bulk insert (<a href="https://github.com/milvus-io/milvus/pull/33788">#33788</a>)</li>
<li>Aggiunto il flag includeCurrentMsg per il metodo seek<a href="https://github.com/milvus-io/milvus/pull/33743">(#33743</a>)</li>
<li>Aggiunti mergeInterval, targetBufSize, maxTolerantLag di msgdispatcher alle configurazioni<a href="https://github.com/milvus-io/milvus/pull/33680">(#33680</a>)</li>
<li>Migliorato GetVectorByID del vettore sparse<a href="https://github.com/milvus-io/milvus/pull/33652">(#33652</a>)</li>
<li>Rimossa StringPrimarykey per ridurre le copie inutili e il costo delle chiamate di funzione (<a href="https://github.com/milvus-io/milvus/pull/33649">#33649</a>)</li>
<li>Aggiunta la mappatura dell'autoindice per i tipi di dati binari/sparsi<a href="https://github.com/milvus-io/milvus/pull/33625">(#33625</a>)</li>
<li>Ottimizzate alcune cache per ridurre l'uso della memoria<a href="https://github.com/milvus-io/milvus/pull/33560">(#33560</a>)</li>
<li>Astratta l'interfaccia di esecuzione per le operazioni di importazione/preimportazione (<a href="https://github.com/milvus-io/milvus/pull/33607">#33607</a>)</li>
<li>Usato map pk per timestamp nell'inserimento del buffer per ridurre le cause di bf (<a href="https://github.com/milvus-io/milvus/pull/33582">#33582</a>)</li>
<li>Evitate meta-operazioni ridondanti di importazione (<a href="https://github.com/milvus-io/milvus/pull/33519">#33519</a>)</li>
<li>Migliorati i log registrando meglio le informazioni sulla quota disco, aggiungendo il flag UseDefaultConsistency, rimuovendo i log non necessari<a href="https://github.com/milvus-io/milvus/pull/33597">(#33597</a>, <a href="https://github.com/milvus-io/milvus/pull/33644">#33644</a>, <a href="https://github.com/milvus-io/milvus/pull/33670">#33670</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Corretto un bug per cui queryHook non era in grado di riconoscere il tipo di vettore (<a href="https://github.com/milvus-io/milvus/pull/33911">#33911</a>)</li>
<li>Impedito l'uso della variabile di iterazione catturata partitionID (<a href="https://github.com/milvus-io/milvus/pull/33970">#33970</a>)</li>
<li>Corretto un bug che può causare l'incapacità di Milvus di creare AutoIndex su vettori binari e sparsi<a href="https://github.com/milvus-io/milvus/pull/33867">(#33867</a>)</li>
<li>Corretto un bug che può far sì che indexnode ritenti la creazione di un indice su parametri di indice non validi di tutti i vettori (<a href="https://github.com/milvus-io/milvus/pull/33878">#33878</a>)</li>
<li>Corretto il bug che quando i carichi e i rilasci avvengono in modo concomitante può mandare in crash il server<a href="https://github.com/milvus-io/milvus/pull/33699">(#33699</a>)</li>
<li>Migliorata la coerenza della cache per i valori di configurazione<a href="https://github.com/milvus-io/milvus/pull/33797">(#33797</a>)</li>
<li>Prevenuta la possibile perdita di dati durante la cancellazione<a href="https://github.com/milvus-io/milvus/pull/33821">(#33821</a>)</li>
<li>Assicurato che il campo DroppedAt (probabile timestamp di cancellazione) sia impostato dopo l'eliminazione delle raccolte (<a href="https://github.com/milvus-io/milvus/pull/33767">#33767</a>).</li>
<li>Corretto un problema che poteva causare una gestione non corretta delle dimensioni dei dati dei vettori binari da parte di Milvus<a href="https://github.com/milvus-io/milvus/pull/33751">(#33751</a>)</li>
<li>Impedito che le credenziali sensibili di Kafka vengano registrate in testo normale<a href="https://github.com/milvus-io/milvus/pull/33694">(#33694</a>, <a href="https://github.com/milvus-io/milvus/pull/33747">#33747</a>).</li>
<li>Assicurato che Milvus possa importare correttamente dati con campi vettoriali multipli.<a href="https://github.com/milvus-io/milvus/pull/33724">(#33724</a>)</li>
<li>Migliorata l'affidabilità dell'importazione controllando l'esistenza di un lavoro di importazione prima dell'avvio.<a href="https://github.com/milvus-io/milvus/pull/33673">(#33673</a>)</li>
<li>Migliorata la gestione dell'indice HNSW sparse (funzionalità interna)<a href="https://github.com/milvus-io/milvus/pull/33714">(#33714</a>)</li>
<li>Pulita la memoria vettoriale per evitare perdite di memoria<a href="https://github.com/milvus-io/milvus/pull/33708">(#33708</a>)</li>
<li>Assicurato un riscaldamento asincrono più fluido grazie alla correzione di un problema di blocco di stato.<a href="https://github.com/milvus-io/milvus/pull/33687">(#33687</a>)</li>
<li>Risolto un bug che poteva causare risultati mancanti negli iteratori delle query.<a href="https://github.com/milvus-io/milvus/pull/33506">(#33506</a>)</li>
<li>Corretto un bug che poteva causare una dimensione non uniforme dei segmenti di importazione (<a href="https://github.com/milvus-io/milvus/pull/33634">#33634</a>).</li>
<li>Corretta la gestione della dimensione dei dati per i tipi bf16, fp16 e vettori binari<a href="https://github.com/milvus-io/milvus/pull/33488">(#33488</a>).</li>
<li>Migliorata la stabilità risolvendo potenziali problemi con il compattatore L0<a href="https://github.com/milvus-io/milvus/pull/33564">(#33564</a>)</li>
<li>Assicurato che gli aggiornamenti della configurazione dinamica siano riflessi correttamente nella cache.<a href="https://github.com/milvus-io/milvus/pull/33590">(#33590</a>)</li>
<li>Migliorata l'accuratezza della metrica RootCoordQuotaStates (<a href="https://github.com/milvus-io/milvus/pull/33601">#33601</a>)</li>
<li>Assicurata la segnalazione accurata del numero di entità caricate nella metrica<a href="https://github.com/milvus-io/milvus/pull/33522">(#33522</a>).</li>
<li>Fornite informazioni più complete nei log delle eccezioni. <a href="https://github.com/milvus-io/milvus/pull/33396">(#33396</a>)</li>
<li>Ottimizzata la pipeline di query rimuovendo il controllore di gruppo non necessario<a href="https://github.com/milvus-io/milvus/pull/33485">(#33485</a>)</li>
<li>Utilizzato il percorso di archiviazione locale per un controllo più accurato della capacità del disco sul nodo indice.<a href="https://github.com/milvus-io/milvus/pull/33505">(#33505</a>)</li>
<li>Corretta la possibilità che hasMoreResult restituisca false quando il numero di hit è superiore al limite<a href="https://github.com/milvus-io/milvus/pull/33642">(#33642</a>)</li>
<li>Ritardato il caricamento dei bf nel delegatore per evitare che vengano caricati più volte quando il worker non ha più memoria<a href="https://github.com/milvus-io/milvus/pull/33650">(#33650</a>) - Corretto un bug per cui queryHook non era in grado di riconoscere il tipo di vettore<a href="https://github.com/milvus-io/milvus/pull/33911">(#33911</a>)</li>
<li>Impedito l'uso della variabile di iterazione catturata partitionID (<a href="https://github.com/milvus-io/milvus/pull/33970">#33970</a>)</li>
<li>Corretto un bug che poteva causare l'incapacità di Milvus di creare AutoIndex su vettori binari e sparsi<a href="https://github.com/milvus-io/milvus/pull/33867">(#33867</a>)</li>
<li>Corretto un bug che può far sì che indexnode ritenti la creazione di un indice su parametri di indice non validi di tutti i vettori (<a href="https://github.com/milvus-io/milvus/pull/33878">#33878</a>)</li>
<li>Corretto il bug che quando i carichi e i rilasci avvengono in modo concomitante può mandare in crash il server<a href="https://github.com/milvus-io/milvus/pull/33699">(#33699</a>)</li>
<li>Migliorata la coerenza della cache per i valori di configurazione<a href="https://github.com/milvus-io/milvus/pull/33797">(#33797</a>)</li>
<li>Prevenuta la possibile perdita di dati durante la cancellazione<a href="https://github.com/milvus-io/milvus/pull/33821">(#33821</a>)</li>
<li>Assicurato che il campo DroppedAt (probabile timestamp di cancellazione) sia impostato dopo l'eliminazione delle raccolte (<a href="https://github.com/milvus-io/milvus/pull/33767">#33767</a>).</li>
<li>Corretto un problema che poteva causare una gestione non corretta delle dimensioni dei dati dei vettori binari da parte di Milvus<a href="https://github.com/milvus-io/milvus/pull/33751">(#33751</a>)</li>
<li>Impedito che le credenziali sensibili di Kafka vengano registrate in testo normale<a href="https://github.com/milvus-io/milvus/pull/33694">(#33694</a>, <a href="https://github.com/milvus-io/milvus/pull/33747">#33747</a>).</li>
<li>Assicurato che Milvus possa importare correttamente dati con campi vettoriali multipli.<a href="https://github.com/milvus-io/milvus/pull/33724">(#33724</a>)</li>
<li>Migliorata l'affidabilità dell'importazione controllando l'esistenza di un lavoro di importazione prima dell'avvio.<a href="https://github.com/milvus-io/milvus/pull/33673">(#33673</a>)</li>
<li>Migliorata la gestione dell'indice HNSW sparse (funzionalità interna)<a href="https://github.com/milvus-io/milvus/pull/33714">(#33714</a>)</li>
<li>Pulita la memoria vettoriale per evitare perdite di memoria<a href="https://github.com/milvus-io/milvus/pull/33708">(#33708</a>)</li>
<li>Assicurato un riscaldamento asincrono più fluido grazie alla correzione di un problema di blocco di stato.<a href="https://github.com/milvus-io/milvus/pull/33687">(#33687</a>)</li>
<li>Risolto un bug che poteva causare risultati mancanti negli iteratori delle query.<a href="https://github.com/milvus-io/milvus/pull/33506">(#33506</a>)</li>
<li>Corretto un bug che poteva causare una dimensione non uniforme dei segmenti di importazione (<a href="https://github.com/milvus-io/milvus/pull/33634">#33634</a>).</li>
<li>Corretta la gestione della dimensione dei dati per i tipi bf16, fp16 e vettori binari<a href="https://github.com/milvus-io/milvus/pull/33488">(#33488</a>).</li>
<li>Migliorata la stabilità risolvendo potenziali problemi con il compattatore L0<a href="https://github.com/milvus-io/milvus/pull/33564">(#33564</a>)</li>
<li>Assicurato che gli aggiornamenti della configurazione dinamica siano riflessi correttamente nella cache.<a href="https://github.com/milvus-io/milvus/pull/33590">(#33590</a>)</li>
<li>Migliorata l'accuratezza della metrica RootCoordQuotaStates (<a href="https://github.com/milvus-io/milvus/pull/33601">#33601</a>)</li>
<li>Assicurata la segnalazione accurata del numero di entità caricate nella metrica<a href="https://github.com/milvus-io/milvus/pull/33522">(#33522</a>).</li>
<li>Fornite informazioni più complete nei log delle eccezioni. <a href="https://github.com/milvus-io/milvus/pull/33396">(#33396</a>)</li>
<li>Ottimizzata la pipeline di query rimuovendo il controllore di gruppo non necessario<a href="https://github.com/milvus-io/milvus/pull/33485">(#33485</a>)</li>
<li>Utilizzato il percorso di archiviazione locale per un controllo più accurato della capacità del disco sul nodo indice.<a href="https://github.com/milvus-io/milvus/pull/33505">(#33505</a>)</li>
<li>Corretta la possibilità che hasMoreResult restituisca false quando il numero di hit è superiore al limite<a href="https://github.com/milvus-io/milvus/pull/33642">(#33642</a>)</li>
<li>Ritardato il caricamento dei bf nel delegatore per evitare che vengano caricati più volte quando il worker non ha più memoria<a href="https://github.com/milvus-io/milvus/pull/33650">(#33650</a>).</li>
</ul>
<h2 id="v244" class="common-anchor-header">v2.4.4<button data-href="#v244" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 31 maggio 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.4</td><td>2.4.3</td><td>2.4.1</td><td>2.4.2</td></tr>
</tbody>
</table>
<p>Milvus v2.4.4 include diverse correzioni di bug critici e miglioramenti volti a migliorare le prestazioni e la stabilità. In particolare, è stato <strong>risolto un problema critico a causa del quale i registri delle statistiche degli inserti di massa non venivano raccolti in modo corretto</strong>, compromettendo potenzialmente l'integrità dei dati. <strong>Consigliamo vivamente a tutti gli utenti della versione 2.4 di effettuare l'aggiornamento a questa versione per beneficiare di queste correzioni.</strong></p>
<p><strong>Se utilizzate bulk insert, aggiornate alla v2.4.4 il prima possibile per garantire l'integrità dei dati.</strong></p>
<h3 id="Critical-bug-fixes" class="common-anchor-header">Correzioni di bug critici</h3><ul>
<li>Compilazione dell'ID del log delle statistiche e convalida della sua correttezza<a href="https://github.com/milvus-io/milvus/pull/33478">(#33478</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Aggiornato il set di bit per ARM SVE<a href="https://github.com/milvus-io/milvus/pull/33440">(#33440</a>)</li>
<li>Abilitata la compilazione di Milvus con GCC-13<a href="https://github.com/milvus-io/milvus/pull/33441">(#33441</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Visualizzazione di collezioni vuote quando tutti i privilegi sono concessi<a href="https://github.com/milvus-io/milvus/pull/33454">(#33454</a>)</li>
<li>Assicurato il download e l'installazione di CMake per la piattaforma corrente, non solo x86_64<a href="https://github.com/milvus-io/milvus/pull/33439">(#33439</a>)</li>
</ul>
<h2 id="v243" class="common-anchor-header">v2.4.3<button data-href="#v243" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 29 maggio 2024</p>
<table>
<thead>
<tr><th>Versione di Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.3</td><td>2.4.3</td><td>2.4.1</td><td>2.4.2</td></tr>
</tbody>
</table>
<p>La versione 2.4.3 di Milvus ha introdotto una serie di funzionalità, miglioramenti e correzioni di bug per aumentare le prestazioni e l'affidabilità. Tra i miglioramenti più significativi, il supporto per l'inserimento massivo di vettori float sparsi e l'accelerazione ottimizzata del filtro bloom. I miglioramenti riguardano diverse aree, dagli aggiornamenti della configurazione dinamica all'ottimizzazione dell'uso della memoria. Le correzioni di bug hanno affrontato problemi critici come gli scenari di panico e hanno garantito un funzionamento più fluido del sistema. Questa release sottolinea il costante impegno di Milvus nel migliorare le funzionalità, ottimizzare le prestazioni e offrire un'esperienza utente solida.</p>
<h3 id="Features" class="common-anchor-header">Caratteristiche</h3><ul>
<li>Supporto dell'inserimento massivo di vettori float sparsi per binlog/json/parquet<a href="https://github.com/milvus-io/milvus/pull/32649">(#32649</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Implementato il canale di sorveglianza Datacoord/nodo basato su RPC<a href="https://github.com/milvus-io/milvus/pull/32036">(#32036</a>)</li>
<li>Ottimizzato il filtro bloom per accelerare il filtraggio delle cancellazioni<a href="https://github.com/milvus-io/milvus/pull/32642">(#32642</a>, <a href="https://github.com/milvus-io/milvus/pull/33329">#33329</a>, <a href="https://github.com/milvus-io/milvus/pull/33284">#33284</a>)</li>
<li>Caricamento dei dati grezzi tramite mmap se l'indice scalare non ha dati grezzi<a href="https://github.com/milvus-io/milvus/pull/33317">(#33317</a>)</li>
<li>Sincronizzata la configurazione di milvus in milvus.yaml<a href="https://github.com/milvus-io/milvus/pull/33322">(#33322</a>, <a href="https://github.com/milvus-io/milvus/pull/32920">#32920</a>, <a href="https://github.com/milvus-io/milvus/pull/32857">#32857</a>, <a href="https://github.com/milvus-io/milvus/pull/32946">#32946</a>)</li>
<li>Aggiornata la versione di knowhere<a href="https://github.com/milvus-io/milvus/pull/33310">(#33310</a>, <a href="https://github.com/milvus-io/milvus/pull/32931">#32931</a>, <a href="https://github.com/milvus-io/milvus/pull/33043">#33043</a>)</li>
<li>Abilitato l'aggiornamento dinamico della politica del bilanciatore in QueryCoord<a href="https://github.com/milvus-io/milvus/pull/33272">(#33272</a>)</li>
<li>Utilizzato un logger precostituito nel buffer di scrittura per ridurre al minimo l'allocazione del logger (<a href="https://github.com/milvus-io/milvus/pull/33304">#33304</a>)</li>
<li>Migliorato il controllo dei parametri<a href="https://github.com/milvus-io/milvus/pull/32777">(#32777</a>, <a href="https://github.com/milvus-io/milvus/pull/33271">#33271</a>, <a href="https://github.com/milvus-io/milvus/pull/33218">#33218</a>)</li>
<li>Aggiunto un parametro per ignorare gli ID dei messaggi errati nel checkpoint<a href="https://github.com/milvus-io/milvus/pull/33249">(#33249</a>)</li>
<li>Aggiunta una configurazione per controllare la gestione dei fallimenti di inizializzazione per i plugin<a href="https://github.com/milvus-io/milvus/pull/32680">(#32680</a>)</li>
<li>Aggiunta la configurazione della coerenza del calcolo dei punteggi per knowhere<a href="https://github.com/milvus-io/milvus/pull/32997">(#32997</a>)</li>
<li>Introdotta un'opzione di configurazione per controllare l'inizializzazione dei permessi dei ruoli pubblici (<a href="https://github.com/milvus-io/milvus/pull/33174">#33174</a>)</li>
<li>Ottimizzato l'uso della memoria durante la lettura dei campi<a href="https://github.com/milvus-io/milvus/pull/33196">(#33196</a>)</li>
<li>Raffinata l'implementazione di Channel Manager v2<a href="https://github.com/milvus-io/milvus/pull/33172">(#33172</a>, <a href="https://github.com/milvus-io/milvus/pull/33121">#33121</a>, <a href="https://github.com/milvus-io/milvus/pull/33014">#33014</a>)</li>
<li>Aggiunta una funzione per tracciare la dimensione dei dati in memoria per binlog<a href="https://github.com/milvus-io/milvus/pull/33025">(#33025</a>)</li>
<li>Aggiunte metriche per le dimensioni dei file indice dei segmenti<a href="https://github.com/milvus-io/milvus/pull/32979">(#32979</a>, <a href="https://github.com/milvus-io/milvus/pull/33305">#33305</a>)</li>
<li>Sostituito Delete con DeletePartialMatch per rimuovere le metriche<a href="https://github.com/milvus-io/milvus/pull/33029">(#33029</a>)</li>
<li>Ottenuta la dimensione dei dati relativi in base al tipo di segmento<a href="https://github.com/milvus-io/milvus/pull/33017">(#33017</a>)</li>
<li>Pulite le informazioni sui nodi dei canali nel meta store<a href="https://github.com/milvus-io/milvus/pull/32988">(#32988</a>)</li>
<li>Rimosso il rootcoord dal broker dei datanodi (<a href="https://github.com/milvus-io/milvus/pull/32818">#32818</a>)</li>
<li>Abilitato il caricamento in batch (<a href="https://github.com/milvus-io/milvus/pull/32788">#32788</a>)</li>
<li>Cambiato il numero di partizione predefinito a 16 quando si usa la chiave di partizione (<a href="https://github.com/milvus-io/milvus/pull/32950">#32950</a>)</li>
<li>Migliorate le prestazioni di riduzione delle query top-k molto grandi (<a href="https://github.com/milvus-io/milvus/pull/32871">#32871</a>)</li>
<li>Utilizzata la capacità di TestLocations per accelerare la scrittura e la compattazione<a href="https://github.com/milvus-io/milvus/pull/32948">(#32948</a>)</li>
<li>Ottimizzato il pool di parser dei piani per evitare ricicli inutili (<a href="https://github.com/milvus-io/milvus/pull/32869">#32869</a>)</li>
<li>Migliorata la velocità di caricamento (<a href="https://github.com/milvus-io/milvus/pull/32898">#32898</a>)</li>
<li>Utilizzato il livello di consistenza predefinito della raccolta per restv2<a href="https://github.com/milvus-io/milvus/pull/32956">(#32956</a>)</li>
<li>Aggiunta la risposta ai costi per l'API Rest (<a href="https://github.com/milvus-io/milvus/pull/32620">#32620</a>)</li>
<li>Abilitata la politica di bilanciamento esclusivo dei canali (<a href="https://github.com/milvus-io/milvus/pull/32911">#32911</a>)</li>
<li>Esposta l'API describedatabase nel proxy (<a href="https://github.com/milvus-io/milvus/pull/32732">#32732</a>)</li>
<li>Utilizzata la mappatura coll2replica quando si ottiene RG per collezione<a href="https://github.com/milvus-io/milvus/pull/32892">(#32892</a>)</li>
<li>Aggiunto un maggiore tracciamento per la ricerca e la query<a href="https://github.com/milvus-io/milvus/pull/32734">(#32734</a>)</li>
<li>Supportata la configurazione dinamica per la traccia di opentelemetria<a href="https://github.com/milvus-io/milvus/pull/32169">(#32169</a>)</li>
<li>Evitata l'iterazione sui risultati dei canali quando si aggiorna la leaderview<a href="https://github.com/milvus-io/milvus/pull/32887">(#32887</a>)</li>
<li>Ottimizzata la gestione degli offset vettoriali per il parquet<a href="https://github.com/milvus-io/milvus/pull/32822">(#32822</a>)</li>
<li>Migliorato il filtraggio dei segmenti dei datacoord con la raccolta<a href="https://github.com/milvus-io/milvus/pull/32831">(#32831</a>)</li>
<li>Regolato il livello e la frequenza dei log (<a href="https://github.com/milvus-io/milvus/pull/33042">#33042</a>, <a href="https://github.com/milvus-io/milvus/pull/32838">#32838</a>, <a href="https://github.com/milvus-io/milvus/pull/33337">#33337</a>)</li>
<li>Abilitato l'arresto del bilanciamento dopo che questo era stato sospeso<a href="https://github.com/milvus-io/milvus/pull/32812">(#32812</a>)</li>
<li>Aggiornata la cache del leader dello shard quando la posizione del leader è cambiata<a href="https://github.com/milvus-io/milvus/pull/32470">(#32470</a>)</li>
<li>Rimossi API e campi deprecati<a href="https://github.com/milvus-io/milvus/pull/32808">(#32808</a>, <a href="https://github.com/milvus-io/milvus/pull/32704">#32704</a>)</li>
<li>Aggiunto metautil.channel per convertire i confronti tra stringhe in int<a href="https://github.com/milvus-io/milvus/pull/32749">(#32749</a>)</li>
<li>Aggiunte informazioni sul tipo per il messaggio di errore dello scrittore di payload e il log quando querynode ha trovato una nuova raccolta<a href="https://github.com/milvus-io/milvus/pull/32522">(#32522</a>)</li>
<li>Controllato il numero di partizione quando si crea una raccolta con una chiave di partizione<a href="https://github.com/milvus-io/milvus/pull/32670">(#32670</a>)</li>
<li>Rimosso il segmento legacy l0 se l'orologio fallisce<a href="https://github.com/milvus-io/milvus/pull/32725">(#32725</a>)</li>
<li>Migliorata la stampa del tipo di richiesta<a href="https://github.com/milvus-io/milvus/pull/33319">(#33319</a>)</li>
<li>Controllato che i dati del campo dell'array fossero nulli prima di ottenere il tipo<a href="https://github.com/milvus-io/milvus/pull/33311">(#33311</a>)</li>
<li>Restituito errore quando l'operazione di avvio Delete/AddNode del nodo non è riuscita<a href="https://github.com/milvus-io/milvus/pull/33258">(#33258</a>)</li>
<li>Consentito l'aggiornamento dell'ID del server del datanode (<a href="https://github.com/milvus-io/milvus/pull/31597">#31597</a>)</li>
<li>Unificata la pulizia delle metriche del querynode nella collection release<a href="https://github.com/milvus-io/milvus/pull/32805">(#32805</a>)</li>
<li>Corretta la versione errata della configurazione dell'indice automatico scalare<a href="https://github.com/milvus-io/milvus/pull/32795">(#32795</a>)</li>
<li>Raffinato il controllo dei parametri dell'indice per la creazione/alterazione dell'indice<a href="https://github.com/milvus-io/milvus/pull/32712">(#32712</a>)</li>
<li>Rimosso il recupero delle repliche ridondanti<a href="https://github.com/milvus-io/milvus/pull/32985">(#32985</a>)</li>
<li>Abilitata la meta tabella dei canali per scrivere più di 200k segmenti<a href="https://github.com/milvus-io/milvus/pull/33300">(#33300</a>)</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Corretto il panico quando il database non esisteva nell'intercettore del limite di velocità<a href="https://github.com/milvus-io/milvus/pull/33308">(#33308</a>)</li>
<li>Corretto il fallimento della raccolta delle metriche di quotacenter a causa di parametri errati<a href="https://github.com/milvus-io/milvus/pull/33399">(#33399</a>)</li>
<li>Corretto il panico se processactivestandby restituiva un errore<a href="https://github.com/milvus-io/milvus/pull/33372">(#33372</a>)</li>
<li>Corretto il troncamento dei risultati della ricerca in restful v2 quando nq &gt; 1<a href="https://github.com/milvus-io/milvus/pull/33363">(#33363</a>)</li>
<li>Aggiunto il campo del nome del database per le operazioni di ruolo in restful v2<a href="https://github.com/milvus-io/milvus/pull/33291">(#33291</a>)</li>
<li>Corretto il limite di velocità globale che non funziona<a href="https://github.com/milvus-io/milvus/pull/33336">(#33336</a>)</li>
<li>Corretto il panico causato dal fallimento della costruzione dell'indice<a href="https://github.com/milvus-io/milvus/pull/33314">(#33314</a>)</li>
<li>Aggiunta la convalida per il vettore sparse in segcore per garantire la legalità<a href="https://github.com/milvus-io/milvus/pull/33312">(#33312</a>)</li>
<li>Rimossa l'attività da syncmgr dopo il completamento dell'attività<a href="https://github.com/milvus-io/milvus/pull/33303">(#33303</a>)</li>
<li>Corretto il fallimento del filtraggio della chiave di partizione durante l'importazione dei dati (<a href="https://github.com/milvus-io/milvus/pull/33277">#33277</a>)</li>
<li>Corretta l'impossibilità di generare traceID quando si usa noop exporter<a href="https://github.com/milvus-io/milvus/pull/33208">(#33208</a>)</li>
<li>Migliorato il recupero dei risultati delle query<a href="https://github.com/milvus-io/milvus/pull/33179">(#33179</a>)</li>
<li>Segnato l'abbandono del checkpoint del canale per prevenire la perdita di metriche di ritardo del checkpoint<a href="https://github.com/milvus-io/milvus/pull/33201">(#33201</a>)</li>
<li>Corretto il nodo di query che si blocca durante l'arresto dell'avanzamento<a href="https://github.com/milvus-io/milvus/pull/33154">(#33154</a>)</li>
<li>Corretti i segmenti mancanti nella risposta di flush (<a href="https://github.com/milvus-io/milvus/pull/33061">#33061</a>)</li>
<li>Rese idempotenti le operazioni di invio (<a href="https://github.com/milvus-io/milvus/pull/33053">#33053</a>)</li>
<li>Allocata nuova slice per ogni batch nel lettore di streaming<a href="https://github.com/milvus-io/milvus/pull/33360">(#33360</a>)</li>
<li>Pulito il nodo offline dal gruppo di risorse dopo il riavvio di QueryCoord<a href="https://github.com/milvus-io/milvus/pull/33233">(#33233</a>)</li>
<li>Rimosso il compattatore l0 in completedCompactor<a href="https://github.com/milvus-io/milvus/pull/33216">(#33216</a>)</li>
<li>Ripristinato il valore della quota quando si inizializza il limitatore<a href="https://github.com/milvus-io/milvus/pull/33152">(#33152</a>)</li>
<li>Risolto il problema del superamento del limite di etcd (<a href="https://github.com/milvus-io/milvus/pull/33041">#33041</a>)</li>
<li>Risolto il superamento del limite delle transazioni etcd a causa di troppi campi<a href="https://github.com/milvus-io/milvus/pull/33040">(#33040</a>)</li>
<li>Rimosso il rientro di RLock in GetNumRowsOfPartition<a href="https://github.com/milvus-io/milvus/pull/33045">(#33045</a>)</li>
<li>Avviato LeaderCacheObserver prima di SyncAll<a href="https://github.com/milvus-io/milvus/pull/33035">(#33035</a>)</li>
<li>Abilitato il bilanciamento del canale di standby rilasciato (<a href="https://github.com/milvus-io/milvus/pull/32986">#32986</a>)</li>
<li>Inizializzato il logger degli accessi prima dell'inizializzazione del server<a href="https://github.com/milvus-io/milvus/pull/32976">(#32976</a>)</li>
<li>Il compattatore è in grado di cancellare i segmenti vuoti<a href="https://github.com/milvus-io/milvus/pull/32821">(#32821</a>)</li>
<li>Riempito il numero di voce deltalog e l'intervallo di tempo nelle compattazioni l0<a href="https://github.com/milvus-io/milvus/pull/33004">(#33004</a>)</li>
<li>Corretto l'arresto anomalo del proxy dovuto alla corsa dei dati della cache del leader dello shard<a href="https://github.com/milvus-io/milvus/pull/32971">(#32971</a>)</li>
<li>Corretta l'unità di tempo per la metrica dell'indice di carico (<a href="https://github.com/milvus-io/milvus/pull/32935">#32935</a>)</li>
<li>Corretto il problema per cui il segmento sul nodo di query in arresto non poteva essere rilasciato con successo<a href="https://github.com/milvus-io/milvus/pull/32929">(#32929</a>)</li>
<li>Corretta la stima delle risorse dell'indice<a href="https://github.com/milvus-io/milvus/pull/32842">(#32842</a>)</li>
<li>Impostazione del checkpoint del canale alla posizione delta<a href="https://github.com/milvus-io/milvus/pull/32878">(#32878</a>)</li>
<li>Fatto in modo che syncmgr blocchi la chiave prima di restituire il futuro (<a href="https://github.com/milvus-io/milvus/pull/32865">#32865</a>)</li>
<li>Assicurato che l'indice invertito avesse un solo segmento<a href="https://github.com/milvus-io/milvus/pull/32858">(#32858</a>)</li>
<li>Corretto il trigger di compattazione che sceglie due segmenti identici<a href="https://github.com/milvus-io/milvus/pull/32800">(#32800</a>)</li>
<li>Corretto il problema per cui il nome della partizione non poteva essere specificato nell'importazione di binlog<a href="https://github.com/milvus-io/milvus/pull/32730">(#32730</a>, <a href="https://github.com/milvus-io/milvus/pull/33027">#33027</a>)</li>
<li>Rese opzionali le colonne dinamiche nell'importazione di parquet<a href="https://github.com/milvus-io/milvus/pull/32738">(#32738</a>)</li>
<li>Saltato il controllo dell'ID automatico durante l'inserimento dei dati<a href="https://github.com/milvus-io/milvus/pull/32775">(#32775</a>)</li>
<li>Convalidato il numero di righe per i dati del campo di inserimento con lo schema<a href="https://github.com/milvus-io/milvus/pull/32770">(#32770</a>)</li>
<li>Aggiunti Wrapper e Keepalive per gli ID CTraceContext (<a href="https://github.com/milvus-io/milvus/pull/32746">#32746</a>)</li>
<li>Corretto il problema per cui il nome del database non veniva trovato nel meta-oggetto datacoord<a href="https://github.com/milvus-io/milvus/pull/33412">(#33412</a>)</li>
<li>Sincronizzato il segmento abbandonato per la partizione abbandonata (<a href="https://github.com/milvus-io/milvus/pull/33332">#33332</a>)</li>
<li>Corretto il fallimento della raccolta delle metriche di quotaCenter a causa di parametri errati<a href="https://github.com/milvus-io/milvus/pull/33399">(#33399</a>)</li>
</ul>
<h2 id="v241" class="common-anchor-header">v2.4.1<button data-href="#v241" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 6 maggio 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione dell'SDK Java</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.1</td><td>2.4.1</td><td>2.4.0</td><td>2.4.2</td></tr>
</tbody>
</table>
<p>La versione 2.4.1 di Milvus apporta numerosi miglioramenti e correzioni di bug che mirano a migliorare le prestazioni, l'osservabilità e la stabilità del software. Questi miglioramenti includono un'API dichiarativa per i gruppi di risorse, una funzionalità di inserimento massivo migliorata che supporta i tipi di dati vettoriali Float16/BFloat16, un meccanismo raffinato di garbage collection (GC) che riduce le operazioni di lista per la memorizzazione degli oggetti e altre modifiche relative all'ottimizzazione delle prestazioni. Inoltre, le correzioni dei bug risolvono problemi quali errori di compilazione, corrispondenze fuzzy fallite su caratteri newline, tipi di dati dei parametri errati per le interfacce RESTful e errori di BulkInsert su file numpy quando sono abilitati i campi dinamici.</p>
<h3 id="Breaking-changes" class="common-anchor-header">Modifiche di rottura</h3><ul>
<li>Interruzione del supporto per la cancellazione con un'espressione di filtro vuota.<a href="https://github.com/milvus-io/milvus/pull/32472">(#32472</a>)</li>
</ul>
<h3 id="Features" class="common-anchor-header">Caratteristiche</h3><ul>
<li>Aggiunto il supporto per i tipi di dati vettoriali Float16/BFloat16 in BulkInert<a href="https://github.com/milvus-io/milvus/pull/32157">(#32157</a>).</li>
<li>Miglioramento del vettore float sparse per supportare la ricerca iterativa a forza bruta e la ricerca per intervallo (<a href="https://github.com/milvus-io/milvus/pull/32635">#32635</a>)</li>
</ul>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Aggiunta l'API dichiarativa per i gruppi di risorse<a href="https://github.com/milvus-io/milvus/pull/31930">(#31930</a>, <a href="https://github.com/milvus-io/milvus/pull/32297">#32297</a>, <a href="https://github.com/milvus-io/milvus/pull/32536">#32536</a>, <a href="https://github.com/milvus-io/milvus/pull/32666">#32666</a>)</li>
<li>Riscritto l'osservatore delle collezioni in QueryCoord per renderlo guidato dai task (<a href="https://github.com/milvus-io/milvus/pull/32441">#32441</a>)</li>
<li>Rifatto la struttura dei dati usata nel SyncManager di DataNode per ridurre l'uso della memoria e prevenire gli errori<a href="https://github.com/milvus-io/milvus/pull/32673">(#32673</a>).</li>
<li>Rivista l'implementazione della garbage collection per minimizzare le operazioni di lista associate alla memorizzazione degli oggetti<a href="https://github.com/milvus-io/milvus/pull/31740">(#31740</a>)</li>
<li>Ridotto l'uso della cpu quando il numero di raccolte è elevato<a href="https://github.com/milvus-io/milvus/pull/32245">(#32245</a>)</li>
<li>Migliorata la gestione di milvus.yaml generando automaticamente le voci di configurazione rilevanti nel file milvus.yaml attraverso il codice<a href="https://github.com/milvus-io/milvus/pull/31832">(#31832</a>, <a href="https://github.com/milvus-io/milvus/pull/32357">#32357</a>)</li>
<li>Migliorate le prestazioni della query recuperando i dati dopo aver eseguito la riduzione locale (<a href="https://github.com/milvus-io/milvus/pull/32346">#32346</a>).</li>
<li>Aggiunta l'opzione WithBlock per la creazione del client etcd<a href="https://github.com/milvus-io/milvus/pull/32641">(#32641</a>)</li>
<li>Utilizzato client_request_id specificato dal client come TraceID se fornito dal client<a href="https://github.com/milvus-io/milvus/pull/32264">(#32264</a>)</li>
<li>Aggiunta l'etichetta db alle metriche per le operazioni di cancellazione e inserimento in blocco (<a href="https://github.com/milvus-io/milvus/pull/32611">#32611</a>)</li>
<li>Aggiunta la logica per saltare la verifica attraverso la configurazione per le colonne AutoID e PartitionKey (<a href="https://github.com/milvus-io/milvus/pull/32592">#32592</a>)</li>
<li>Raffinati gli errori relativi all'autenticazione<a href="https://github.com/milvus-io/milvus/pull/32253">(#32253</a>)</li>
<li>Affinati i log degli errori per AllocSegmentID in DataCoord<a href="https://github.com/milvus-io/milvus/pull/32351">(#32351</a>, <a href="https://github.com/milvus-io/milvus/pull/32335">#32335</a>)</li>
<li>Rimosse le metriche duplicate<a href="https://github.com/milvus-io/milvus/pull/32380">(#32380</a>, <a href="https://github.com/milvus-io/milvus/pull/32308">#32308</a>) e ripulite quelle inutilizzate<a href="https://github.com/milvus-io/milvus/pull/32404">(#32404</a>, <a href="https://github.com/milvus-io/milvus/pull/32515">#32515</a>).</li>
<li>Aggiunta opzione di configurazione per controllare se imporre l'attivazione della funzione partitionKey (<a href="https://github.com/milvus-io/milvus/pull/32433">#32433</a>)</li>
<li>Aggiunta un'opzione di configurazione per controllare la quantità massima di dati che possono essere inseriti in una singola richiesta (<a href="https://github.com/milvus-io/milvus/pull/32433">#32433</a>).</li>
<li>Parallelizzare l'operazione applyDelete a livello di segmento per accelerare l'elaborazione dei messaggi Delete da parte del delegatore<a href="https://github.com/milvus-io/milvus/pull/32291">(#32291</a>)</li>
<li>Usato l'indice<a href="https://github.com/milvus-io/milvus/pull/32232">(#32232</a>, <a href="https://github.com/milvus-io/milvus/pull/32505">#32505</a>, <a href="https://github.com/milvus-io/milvus/pull/32533">#32533</a>, <a href="https://github.com/milvus-io/milvus/pull/32595">#32595</a>) e l'add cache<a href="https://github.com/milvus-io/milvus/pull/32580">(#32580</a>) per accelerare le operazioni di filtraggio frequenti in QueryCoord.</li>
<li>Riscritta la struttura dei dati<a href="https://github.com/milvus-io/milvus/pull/32273">(#32273</a>) e rifattorizzato il codice<a href="https://github.com/milvus-io/milvus/pull/32389">(#32389</a>) per accelerare le operazioni più comuni in DataCoord.</li>
<li>Rimosso openblas da conan<a href="https://github.com/milvus-io/milvus/pull/32002">(#32002</a>).</li>
</ul>
<h3 id="Bug-fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Corretta la build milvus in rockylinux8<a href="https://github.com/milvus-io/milvus/pull/32619">(#32619</a>)</li>
<li>Corretti gli errori di compilazione per SVE su ARM<a href="https://github.com/milvus-io/milvus/pull/32463">(#32463</a>, <a href="https://github.com/milvus-io/milvus/pull/32270">#32270</a>)</li>
<li>Corretto il problema del crash su immagini GPU basate su ARM<a href="https://github.com/milvus-io/milvus/pull/31980">(#31980</a>)</li>
<li>Corretta la query regex che non può gestire il testo con newline<a href="https://github.com/milvus-io/milvus/pull/32569">(#32569</a>)</li>
<li>Corretta la ricerca che ottiene risultati vuoti quando GetShardLeaders restituisce un elenco di nodi vuoto<a href="https://github.com/milvus-io/milvus/pull/32685">(#32685</a>)</li>
<li>Corretto l'errore sollevato da BulkInsert quando incontra campi dinamici in file numpy<a href="https://github.com/milvus-io/milvus/pull/32596">(#32596</a>)</li>
<li>Corretti bug relativi all'interfaccia RESTFulV2, inclusa un'importante correzione che permette ai parametri numerici nelle richieste di accettare input numerici invece che di tipo stringa<a href="https://github.com/milvus-io/milvus/pull/32485">(#32485</a>, <a href="https://github.com/milvus-io/milvus/pull/32355">#32355</a>)</li>
<li>Corretta la perdita di memoria nel proxy rimuovendo l'evento watching config nel limitatore di velocità<a href="https://github.com/milvus-io/milvus/pull/32313">(#32313</a>)</li>
<li>Corretto il problema per cui il limitatore di velocità segnala erroneamente che la partizione non può essere trovata quando partitionName non è specificato<a href="https://github.com/milvus-io/milvus/pull/32647">(#32647</a>)</li>
<li>Aggiunto il rilevamento dei casi in cui Collection si trova nello stato di recupero e non viene caricato nel tipo di errore.<a href="https://github.com/milvus-io/milvus/pull/32447">(#32447</a>)</li>
<li>Corretta la metrica negativa del numero di entità interrogabili (<a href="https://github.com/milvus-io/milvus/pull/32361">#32361</a>).</li>
</ul>
<h2 id="v240" class="common-anchor-header">v2.4.0<button data-href="#v240" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 17 aprile 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th><th>Versione SDK Node.js</th></tr>
</thead>
<tbody>
<tr><td>2.4.0</td><td>2.4.0</td><td>2.4.0</td></tr>
</tbody>
</table>
<p>Siamo entusiasti di annunciare il lancio ufficiale di Milvus 2.4.- Basandoci sulle solide fondamenta della release 2.4.0-rc.1, ci siamo concentrati sulla risoluzione dei bug critici segnalati dai nostri utenti, preservando le funzionalità esistenti. Inoltre, Milvus 2.4.0 introduce una serie di ottimizzazioni volte a migliorare le prestazioni del sistema, a migliorare l'osservabilità attraverso l'incorporazione di varie metriche e a snellire la base di codice per una maggiore semplicità.</p>
<h3 id="Improvements" class="common-anchor-header">Miglioramenti</h3><ul>
<li>Supporto per le connessioni MinIO TLS<a href="https://github.com/milvus-io/milvus/pull/31396">(#31396</a>, <a href="https://github.com/milvus-io/milvus/pull/31618">#31618</a>)</li>
<li>Supporto dell'AutoIndex per i campi scalari<a href="https://github.com/milvus-io/milvus/pull/31593">(#31593</a>)</li>
<li>Rifattorizzazione della ricerca ibrida per percorsi di esecuzione coerenti con la ricerca regolare<a href="https://github.com/milvus-io/milvus/pull/31742">(#31742</a>, <a href="https://github.com/milvus-io/milvus/pull/32178">#32178</a>)</li>
<li>Filtraggio accelerato grazie alla rifattorizzazione di bitset e bitset_view<a href="https://github.com/milvus-io/milvus/pull/31592">(#31592</a>, <a href="https://github.com/milvus-io/milvus/pull/31754">#31754</a>, <a href="https://github.com/milvus-io/milvus/pull/32139">#32139</a>)</li>
<li>I task di importazione ora supportano l'attesa per il completamento dell'indice dei dati<a href="https://github.com/milvus-io/milvus/pull/31733">(#31733</a>)</li>
<li>Migliorata la compatibilità dell'importazione<a href="https://github.com/milvus-io/milvus/pull/32121">(#32121</a>), la pianificazione dei task<a href="https://github.com/milvus-io/milvus/pull/31475">(#31475</a>) e i limiti sulla dimensione e sul numero dei file importati<a href="https://github.com/milvus-io/milvus/pull/31542">(#31542</a>).</li>
<li>Semplificazione del codice, compresa la standardizzazione dell'interfaccia per il controllo dei tipi<a href="https://github.com/milvus-io/milvus/pull/31945">(#31945</a>, <a href="https://github.com/milvus-io/milvus/pull/31857">#31857</a>), la rimozione di codice e metriche deprecate<a href="https://github.com/milvus-io/milvus/pull/32079">(#32079</a>, <a href="https://github.com/milvus-io/milvus/pull/32134">#32134</a>, <a href="https://github.com/milvus-io/milvus/pull/31535">#31535</a>, <a href="https://github.com/milvus-io/milvus/pull/32211">#32211</a>, <a href="https://github.com/milvus-io/milvus/pull/31935">#31935</a>) e la normalizzazione dei nomi delle costanti<a href="https://github.com/milvus-io/milvus/pull/31515">(#31515</a>).</li>
<li>Nuova metrica per la latenza del punto di controllo del canale di destinazione corrente di QueryCoord<a href="https://github.com/milvus-io/milvus/pull/31420">(#31420</a>)</li>
<li>Nuova etichetta db per le metriche comuni<a href="https://github.com/milvus-io/milvus/pull/32024">(#32024</a>)</li>
<li>Nuove metriche relative al conteggio delle entità cancellate, indicizzate e caricate, con l'inclusione di etichette come collectionName e dbName<a href="https://github.com/milvus-io/milvus/pull/31861">(#31861</a>)</li>
<li>Miglioramenti nella gestione degli errori per i tipi di vettore non corrispondenti<a href="https://github.com/milvus-io/milvus/pull/31766">(#31766</a>)</li>
<li>Supporto per il lancio di errori invece che per il crash quando l'indice non può essere costruito<a href="https://github.com/milvus-io/milvus/pull/31845">(#31845</a>)</li>
<li>Supporto per l'invalidazione della meta-cache del database quando si eliminano i database<a href="https://github.com/milvus-io/milvus/pull/32092">(#32092</a>)</li>
<li>Rifattorizzazione dell'interfaccia per la distribuzione dei canali<a href="https://github.com/milvus-io/milvus/pull/31814">(#31814</a>) e la gestione delle viste leader (<a href="https://github.com/milvus-io/milvus/pull/32127">#32127</a>)</li>
<li>Rifattorizzazione dell'interfaccia del gestore della distribuzione dei canali<a href="https://github.com/milvus-io/milvus/pull/31814">(#31814</a>) e rifattorizzazione dell'interfaccia del gestore della vista leader<a href="https://github.com/milvus-io/milvus/pull/32127">(#32127</a>)</li>
<li>Elaborazione batch<a href="https://github.com/milvus-io/milvus/pull/31632">(#31632</a>), aggiunta di informazioni di mappatura<a href="https://github.com/milvus-io/milvus/pull/32234">(#32234</a>, <a href="https://github.com/milvus-io/milvus/pull/32249">#32249</a>) ed evitamento dell'uso di lock<a href="https://github.com/milvus-io/milvus/pull/31787">(#31787</a>) per accelerare le operazioni invocate di frequente.</li>
</ul>
<h3 id="Breaking-Changes" class="common-anchor-header">Modifiche di rottura</h3><ul>
<li>Interruzione della ricerca di raggruppamenti su vettori binari<a href="https://github.com/milvus-io/milvus/pull/31735">(#31735</a>)</li>
<li>Interruzione della ricerca di raggruppamento con ricerca ibrida<a href="https://github.com/milvus-io/milvus/pull/31812">(#31812</a>)</li>
<li>Interruzione dell'indice HNSW su vettori binari<a href="https://github.com/milvus-io/milvus/pull/31883">(#31883</a>)</li>
</ul>
<h3 id="Bug-Fixes" class="common-anchor-header">Correzioni di bug</h3><ul>
<li>Miglioramento dei controlli del tipo di dati e del valore per le query e gli inserimenti per prevenire gli arresti anomali<a href="https://github.com/milvus-io/milvus/pull/31478">(#31478</a>, <a href="https://github.com/milvus-io/milvus/pull/31653">#31653</a>, <a href="https://github.com/milvus-io/milvus/pull/31698">#31698</a>, <a href="https://github.com/milvus-io/milvus/pull/31842">#31842</a>, <a href="https://github.com/milvus-io/milvus/pull/32042">#32042</a>, <a href="https://github.com/milvus-io/milvus/pull/32251">#32251</a>, <a href="https://github.com/milvus-io/milvus/pull/32204">#32204</a>)</li>
<li>Correzioni di bug dell'API RESTful (<a href="https://github.com/milvus-io/milvus/pull/32160">#32160</a>)</li>
<li>Miglioramento della previsione dell'utilizzo delle risorse degli indici invertiti (<a href="https://github.com/milvus-io/milvus/pull/31641">#31641</a>)</li>
<li>Risoluzione di problemi di connessione con etcd quando l'autorizzazione è abilitata<a href="https://github.com/milvus-io/milvus/pull/31668">(#31668</a>)</li>
<li>Aggiornamento della sicurezza per il server nats (<a href="https://github.com/milvus-io/milvus/pull/32023">#32023</a>)</li>
<li>Memorizzati i file degli indici invertiti in un percorso di archiviazione locale di QueryNode invece che in /tmp<a href="https://github.com/milvus-io/milvus/pull/32210">(#32210</a>)</li>
<li>Risolte le perdite di memoria dei datacoord per collectionInfo<a href="https://github.com/milvus-io/milvus/pull/32243">(#32243</a>)</li>
<li>Risolti bug relativi a fp16/bf16 che potevano causare panico di sistema<a href="https://github.com/milvus-io/milvus/pull/31677">(#31677</a>, <a href="https://github.com/milvus-io/milvus/pull/31841">#31841</a>, <a href="https://github.com/milvus-io/milvus/pull/32196">#32196</a>)</li>
<li>Risolti problemi con la ricerca per raggruppamento che restituiva risultati insufficienti<a href="https://github.com/milvus-io/milvus/pull/32151">(#32151</a>)</li>
<li>Adattamento della ricerca con iteratori per gestire in modo più efficace gli offset nella fase di riduzione e garantire risultati adeguati con "reduceStopForBest" abilitato<a href="https://github.com/milvus-io/milvus/pull/32088">(#32088</a>)</li>
</ul>
<h2 id="v240-rc1" class="common-anchor-header">v2.4.0-rc.1<button data-href="#v240-rc1" class="anchor-icon" translate="no">
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
    </button></h2><p>Data di rilascio: 20 marzo 2024</p>
<table>
<thead>
<tr><th>Versione Milvus</th><th>Versione dell'SDK Python</th></tr>
</thead>
<tbody>
<tr><td>2.4.0-rc.1</td><td>2.4.0</td></tr>
</tbody>
</table>
<p>Questa versione introduce diverse funzionalità basate su scenari:</p>
<ul>
<li><p><strong>Nuovo indice GPU - CAGRA</strong>: grazie al contributo di NVIDIA, questo nuovo indice GPU offre un aumento delle prestazioni di 10 volte, soprattutto per le ricerche in batch. Per maggiori dettagli, consultare l'<a href="/docs/it/gpu_index.md">Indice GPU</a>.</p></li>
<li><p><strong>Ricerca</strong><strong>multivettoriale</strong> e <strong>ibrida</strong>: Questa funzione consente di memorizzare le incorporazioni vettoriali di più modelli e di effettuare ricerche ibride. Per ulteriori informazioni, consultare la sezione <a href="/docs/it/multi-vector-search.md">Ricerca ibrida</a>.</p></li>
<li><p><strong>Vettori sparsi</strong>: Ideali per l'interpretazione e l'analisi delle parole chiave, i vettori sparsi sono ora supportati per l'elaborazione nella vostra raccolta. Per ulteriori informazioni, consultare <a href="/docs/it/sparse_vector.md">Vettori sparsi</a>.</p></li>
<li><p><strong>Ricerca per raggruppamento</strong>: L'aggregazione categoriale migliora il richiamo a livello di documento per le applicazioni RAG (Retrieval-Augmented Generation). Per ulteriori informazioni, consultare la sezione <a href="https://milvus.io/docs/single-vector-search.md#Grouping-search">Ricerca per gruppi</a>.</p></li>
<li><p><strong>Indice invertito</strong> e <strong>corrispondenza fuzzy</strong>: queste funzionalità migliorano il recupero delle parole chiave per i campi scalari. Per ulteriori informazioni, consultare <a href="/docs/it/index-scalar-fields.md">Campi scalari indicizzati</a> e <a href="/docs/it/single-vector-search.md#filtered-search">ricerca filtrata</a>.</p></li>
</ul>
<h3 id="New-Features" class="common-anchor-header">Nuove funzionalità</h3><h4 id="GPU-Index---CAGRA" class="common-anchor-header">Indice GPU - CAGRA</h4><p>Desideriamo esprimere la nostra sincera gratitudine al team NVIDIA per il suo prezioso contributo a CAGRA, un indice di grafi basato su GPU allo stato dell'arte (SoTA) che può essere utilizzato online.</p>
<p>A differenza dei precedenti indici su GPU, CAGRA dimostra una superiorità schiacciante anche nelle query di piccoli lotti, un'area in cui gli indici su CPU tradizionalmente eccellono. Inoltre, le prestazioni di CAGRA nelle query batch di grandi dimensioni e la velocità di costruzione dell'indice, ambiti in cui gli indici su GPU già primeggiano, sono davvero impareggiabili.</p>
<p>Il codice di esempio è disponibile in <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/example_gpu_cagra.py">example_gpu_cagra.py</a>.</p>
<h4 id="Sparse-Vector-Beta" class="common-anchor-header">Vettore sparso (Beta)</h4><p>In questa versione è stato introdotto un nuovo tipo di campo vettoriale, chiamato sparse vector. I vettori sparsi sono diversi dalle loro controparti dense, in quanto tendono ad avere un numero di dimensioni più elevato, con solo una manciata di dimensioni non nulle. Questa caratteristica offre una migliore interpretabilità grazie alla sua natura basata sui termini e può essere più efficace in alcuni domini. I modelli sparsi appresi, come SPLADEv2/BGE-M3, si sono dimostrati molto utili per i comuni compiti di classificazione di primo livello. Il principale caso d'uso di questa nuova funzionalità di Milvus è quello di consentire un'efficiente ricerca semantica approssimata dei vicini su vettori sparsi generati da modelli neurali come SPLADEv2/BGE-M3 e da modelli statistici come l'algoritmo BM25. Milvus supporta ora la memorizzazione, l'indicizzazione e la ricerca efficace e ad alte prestazioni (MIPS, Maximum Inner Product Search) di vettori sparsi.</p>
<p>Un esempio di codice si trova in <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/hello_sparse.py">hello_sparse.py</a>.</p>
<h4 id="Multi-Embedding---Hybrid-Search" class="common-anchor-header">Incorporamento multiplo e ricerca ibrida</h4><p>Il supporto multi-vettore è la pietra miliare per le applicazioni che richiedono l'elaborazione di dati multi-modello o un mix di vettori densi e radi. Con il supporto multivettoriale, ora è possibile:</p>
<ul>
<li>Memorizzare le incorporazioni vettoriali generate per campioni di testo, immagini o audio non strutturati da più modelli.</li>
<li>Condurre ricerche RNA che includono più vettori di ogni entità.</li>
<li>Personalizzare le strategie di ricerca assegnando pesi ai diversi modelli di incorporamento.</li>
<li>Sperimentare con vari modelli di incorporamento per trovare la combinazione ottimale di modelli.</li>
</ul>
<p>Il supporto multivettoriale consente di memorizzare, indicizzare e applicare strategie di reranking a più campi vettoriali di tipo diverso, come FLOAT_VECTOR e SPARSE_FLOAT_VECTOR, in una collezione. Attualmente sono disponibili due strategie di reranking: <strong>Reciprocal Rank Fusion (RRF)</strong> e <strong>Average Weighted Scoring</strong>. Entrambe le strategie combinano i risultati della ricerca di diversi campi vettoriali in un insieme di risultati unificato. La prima strategia dà priorità alle entità che appaiono costantemente nei risultati di ricerca di diversi campi vettoriali, mentre l'altra strategia assegna dei pesi ai risultati di ricerca di ciascun campo vettoriale per determinare la loro importanza nel set di risultati finale.</p>
<p>Un esempio di codice si trova in <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/hybrid_search.py">hybrid_search.py</a>.</p>
<h4 id="Inverted-Index-and-Fuzzy-Match" class="common-anchor-header">Indice invertito e corrispondenza fuzzy</h4><p>Nelle versioni precedenti di Milvus, per l'indicizzazione dei campi scalari venivano utilizzati indici di ricerca binaria basati sulla memoria e indici Marisa Trie. Tuttavia, questi metodi richiedevano molta memoria. L'ultima versione di Milvus impiega ora l'indice inverso basato su Tantivy, che può essere applicato a tutti i tipi di dati numerici e stringhe. Questo nuovo indice migliora notevolmente le prestazioni delle query scalari, riducendo di dieci volte la ricerca di parole chiave nelle stringhe. Inoltre, l'indice invertito consuma meno memoria, grazie a ulteriori ottimizzazioni nella compressione dei dati e al meccanismo di Memory-mapped storage (MMap) della struttura di indicizzazione interna.</p>
<p>Questa versione supporta anche le corrispondenze sfumate nel filtraggio scalare utilizzando prefissi, infissi e suffissi.</p>
<p>Esempi di codice si trovano in <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/inverted_index_example.py">inverted_index_example.py</a> e <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/fuzzy_match.py">fuzzy_match.py</a>.</p>
<h4 id="Grouping-Search" class="common-anchor-header">Raggruppare la ricerca</h4><p>È ora possibile aggregare i risultati della ricerca in base ai valori di uno specifico campo scalare. Questo aiuta le applicazioni RAG a implementare il richiamo a livello di documento. Si consideri un insieme di documenti, ogni documento suddiviso in vari passaggi. Ogni passaggio è rappresentato da un'incorporazione vettoriale e appartiene a un documento. Per trovare i documenti più rilevanti invece di disperdere i passaggi, è possibile includere l'argomento group_by_field nell'operazione search() per raggruppare i risultati in base all'ID del documento.</p>
<p>Un esempio di codice si trova in <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/example_group_by.py">example_group_by.py</a>.</p>
<h4 id="Float16-and-BFloat--Vector-DataType" class="common-anchor-header">Tipo di dati vettoriali Float16 e BFloat</h4><p>L'apprendimento automatico e le reti neurali utilizzano spesso tipi di dati a mezza precisione, come Float16 e BFloat. Sebbene questi tipi di dati possano migliorare l'efficienza delle query e ridurre l'uso della memoria, hanno come contropartita una minore precisione. Con questa versione, Milvus supporta ora questi tipi di dati per i campi vettoriali.</p>
<p>Il codice di esempio si trova in <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/float16_example.py">float16_example.py</a> e <a href="https://github.com/milvus-io/pymilvus/blob/2.4/examples/bfloat16_example.py">bfloat16_example.py</a>.</p>
<h3 id="Upgraded-Architecture" class="common-anchor-header">Architettura aggiornata</h3><h4 id="L0-Segment" class="common-anchor-header">Segmento L0</h4><p>Questa versione include un nuovo segmento chiamato Segmento L0, progettato per registrare i dati cancellati. Questo segmento compatta periodicamente i record cancellati memorizzati e li divide in segmenti sigillati, riducendo il numero di flush dei dati necessari per le piccole cancellazioni e lasciando un'impronta di memoria ridotta. Con questo meccanismo, Milvus separa completamente la compattazione dei dati dal lavaggio dei dati, migliorando le prestazioni delle operazioni di cancellazione e di upsert.</p>
<h4 id="Refactored-BulkInsert" class="common-anchor-header">BulkInsert rifatto</h4><p>Questa versione introduce anche una logica di inserimento massivo migliorata. Ciò consente di importare più file in un'unica richiesta di bulk-insert. Con la versione rifattorizzata, sia le prestazioni che la stabilità del bulk insert sono migliorate in modo significativo. Anche l'esperienza dell'utente è stata migliorata, come la limitazione della velocità e i messaggi di errore più semplici. Inoltre, è possibile accedere facilmente agli endpoint di inserimento massivo tramite l'API RESTful di Milvus.</p>
<h4 id="Memory-mapped-Storage" class="common-anchor-header">Archiviazione con memoria</h4><p>Milvus utilizza lo storage memory-mapped (MMap) per ottimizzare l'uso della memoria. Invece di caricare il contenuto del file direttamente nella memoria, questo meccanismo mappa il contenuto del file nella memoria. Questo approccio ha come contropartita una riduzione delle prestazioni.  Abilitando MMap per una raccolta indicizzata HNSW su un host con 2 CPU e 8 GB di RAM, è possibile caricare 4 volte più dati con una riduzione delle prestazioni inferiore al 10%.</p>
<p>Inoltre, questa versione consente anche un controllo dinamico e a grana fine su MMap senza la necessità di riavviare Milvus.</p>
<p>Per maggiori dettagli, consultare la sezione <a href="/docs/it/mmap.md">Memorizzazione MMap</a>.</p>
<h3 id="Others" class="common-anchor-header">Altri</h3><h4 id="Milvus-CDC" class="common-anchor-header">Milvus-CDC</h4><p>Milvus-CDC è uno strumento di facile utilizzo per acquisire e sincronizzare i dati incrementali tra le istanze di Milvus, consentendo di semplificare il backup incrementale e il disaster recovery. In questa versione, Milvus-CDC ha migliorato la stabilità e la sua funzionalità Change Data Capture (CDC) è ora generalmente disponibile.</p>
<p>Per saperne di più su Milvus-CDC, consultate il <a href="https://github.com/zilliztech/milvus-cdc">repository GitHub</a> e la <a href="/docs/it/milvus-cdc-overview.md">panoramica di Milvus-CDC</a>.</p>
<h4 id="Refined-MilvusClient-Interfaces" class="common-anchor-header">Interfacce perfezionate per MilvusClient</h4><p>MilvusClient è un'alternativa facile da usare al modulo ORM. Adotta un approccio puramente funzionale per semplificare le interazioni con il server. Invece di mantenere un pool di connessioni, ogni MilvusClient stabilisce una connessione gRPC al server. Il modulo MilvusClient ha implementato la maggior parte delle funzionalità del modulo ORM. Per saperne di più sul modulo MilvusClient, visitate <a href="https://github.com/milvus-io/pymilvus">pymilvus</a> e i <a href="/api-reference/pymilvus/v2.4.x/About.md">documenti di riferimento</a>.</p>

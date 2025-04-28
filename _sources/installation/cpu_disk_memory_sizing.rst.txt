Risorse hardware consigliate
=============================

I test di funzionamento in produzione hanno evidenziato la necessità
di suddividere su almeno 3 distinti virtual machine l'architettura del sistema (SERVER-A, SERVER-B, SERVER-C).

In particolare è consigliato di mantenere separata la parte del crawler,
dalla parte del coordinamento (conductor-service), dalla parte di gestione
dei risultati e loro visualizzazione via Web.

.. _main-flow-tab:
.. list-table:: Risorse minime SERVER-A (hardware, sistema operativo, layer di virtualizzazione)
   :header-rows: 1
   * - *SW di virtualizzazione*
     - *CPU*
     - *vCPU*
     - *RAM*
     - *HDD DATA*
     - *HDD SO*
     - *SO*
     - *COMPONENTI*
   * - **page_size**
     - Dimensione della pagina per il recupero delle PA
     - 2000
     - No
   * - **parent_workflow_id**
     - Identificativo del flusso, viene valorizzato con UUID generato
     - vuoto
     - Si
   * - **codice_categoria**
     - Se valorizzato filtra le PA che fanno parte della categoria
     - vuoto
     - Si
   * - **codice_ipa**
     - Se valorizzato individua la singola PA
     - vuoto
     - Si
   * - **crawling_mode**
     - Modalità base di esecuzione del crawler può assumere i valori *httpStream* e *htmlSource*
     - httpStream
     - No
   * - **crawler_save_object**
     - Booleano indica se salvare sempre la pagina HTML
     - false
     - No
   * - **crawler_save_screenshot**
     - Booleano indica se salvare sempre lo screenshot della pagina
     - false
     - No
   * - **rule_name**
     - Nome della regola
     - amministrazione-trasparente
     - No
   * - **root_rule**
     - Nome della regola di base dell'albero
     - amministrazione-trasparente
     - No
   * - **execute_child**
     - Booleano indica se controllare le regole figlie
     - true
     - No
   * - **id_ipa_from**
     - Identificativo numerico della PA da cui partire
     - 0
     - No
   * - **connection_timeout**
     - Timeout in millisecondi della connessione
     - 60000
     - No
   * - **read_timeout**
     - Timeout in millisecondi della lettura
     - 60000
     - No
   * - **connection_timeout_max**
     - Timeout in millisecondi della connessione
     - 120000
     - No
   * - **read_timeout_max**
     - Timeout in millisecondi della lettura
     - 120000
     - No
   * - **crawler_child_type**
     - Modalità di esecuzione dei flussi figli può assumere i valori *SUB_WORKFLOW* e *START_WORKFLOW*
     - START_WORKFLOW
     - No
   * - **rule_base_url**
     - URL di base del microservizio delle Regole
     - *URL*
     - No
   * - **public_company_base_url**
     - URL di base del microservizio delle PA
     - *URL*
     - No
   * - **result_aggregator_base_url**
     - URL di base del microservizio Aggregato
     - *URL*
     - No
   * - **result_base_url**
     - URL di base del microservizio dei Risultati
     - *URL*
     - No
   * - **crawler_uri**
     - URL di base del microservizio Crawler
     - *URL*
     - No

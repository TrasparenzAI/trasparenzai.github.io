Task Scheduler Service
=======================

Task Scheduler Service è il componente che si occupa di avviare alcuni processi
eseguiti a intervalli fissi, come per esempio l'**avvio delle scansioni** dei siti 
del PA per la verifica della corrispondenza dei requisiti e la **cancellazione
dei risultati di scansione più vecchi**.

Nell'utilizzo tramite **docker-compose.yml** ricordarsi di impostare nel **.env**
la corretta variabile d'ambiente che specifica l'url del config-service da 
utilizzare e la password per l'autenticazione Basic Auth con il
*config-service*::

  environment:
    - confighost=${CONFIG_HOST}
    - spring.security.oauth2.client.registration.oidc.client-secret=${OIDC_CLIENT_SECRET}

Vedi :doc:`config-service`.

Il codice sorgente è disponibile su github:
  - https://github.com/trasparenzai/task-scheduler-service

Nel repository github è compreso anche uno script per la prima installazione
del servizio `first-setup.sh <https://github.com/trasparenzai/task-scheduler-service/blob/main/first-setup.sh>`_.

Questo servizio ha tre dipendenze per funzionare:
 - il conductor-service tramite cui avviare i flussi di verifica e la
   cancellazione dei vecchi workflow
 - il :doc:`result-service` da cui cancellare i vecchi workflow
 - il :doc:`result-aggregator-service` da cui cancellare i vecchi workflow

La configurazione del **conductor-service** per avviare i nuovi flussi e
cancellari quelli vecchi viene letta automaticamente dal :doc:`config-service`.

**Attenzione**: è invece importante impostare nel **.env** le URL dei servizi
*result-service* e *result-aggregator-service* modificando le variabili d'ambiente 
*TRANSPARENCY_RESULT_SERVICE_URL* e *TRANSPARENCY_RESULT_AGGREGATOR_SERVICE_URL*::

  # Configurazione indirizzi dei servizi dove cancellare i risutalti del workflow scaduti
  - transparency.clients.result-service.url=${TRANSPARENCY_RESULT_SERVICE_URL}
  - transparency.clients.result-aggregator-service.url=${TRANSPARENCY_RESULT_AGGREGATOR_SERVICE_URL}

Per configurare il client REST che accede a questi due servizi è necessario
configurare nel .env il parametro **OIDC_CLIENT_SECRET**, impostando il valore
generato quando si è creato il *Service Account* *task-scheduler*, vedi
:doc:`authentication`.::

  # Client Secret da generare nel Identity Provider e impostare qui
  - spring.security.oauth2.client.registration.oidc.client-secret=${OIDC_CLIENT_SECRET}

Inoltre è necessario configurare la sezione della sicurezza.

Sicurezza
---------
Gli endpoint REST di questo servizio sono protetti tramite autenticazione 
OAuth con Bearer Token.
È necessario configurare l'IDP da utilizzare per validare i token OAuth tramite
le due proprietà impostabili nel docker-compose.yml come nell'esempio seguente::

  - spring.security.oauth2.resourceserver.jwt.issuer-uri=https://dica33.ba.cnr.it/keycloak/realms/trasparenzai
  - spring.security.oauth2.resourceserver.jwt.jwk-set-uri=https://dica33.ba.cnr.it/keycloak/realms/trasparenzai/protocol/openid-connect/certs

I valori dei parametri *jwt.issuer-uri* e *jwk-set-uri* sono quelli già descritti
nella sezione :doc:`authentication`.

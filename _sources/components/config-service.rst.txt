Config Service
==============

Config Service è il componente che si occupa di archiviare e distribuire
alcune informazioni di configurazione dei servizi che compongono lo stack del
progetto TrasparenzAI.

Config Service mantiene nel proprio datastore locale le configurazioni che sono
fornite agli altri microservizi.
Le configurazioni possono essere inserite/aggiornate tramite gli appositi
endopoint REST presenti in questo servizio.

Le configurazioni disponibili sono fornite sia sotto forma di endopoint REST
con le relative CRUD, che nel formato utilizzato da *Spring Cloud Config* 
attraverso il path **/config**, inserendo il nome del servizio e il profilo
richiesto nell'url, come per esempio::

  $ http GET :8888/config/task-scheduler/default

  {
    "label": null,
    "name": "task-scheduler",
    "profiles": [
        "default"
    ],
    "propertySources": [
        {
            "name": "task-scheduler-default",
            "source": {
                "tasks.fake.cron.expression": "0 46 15 * * ?",
                "test.property1": "testme"
            }
        }
    ],
    "state": null,
    "version": null
  }

I microservizi Spring che vogliono utilizzare questo servizio di configurazione
centralizzato possono farlo specificando nella propria configurazione tre 
parametri tipo::

  spring.config.import=optional:configserver:http://@localhost:8888/config
  spring.cloud.config.username=config-service-user
  spring.cloud.config.password=PASSWORD_DA_IMPOSTARE_E_CONDIVIDERE_CON_I_CLIENT

Dove naturalmente va impostato il corretto URL a cui risponde questo servizio.

Il codice sorgente di questo componente è disponibile su GitHub:
 - https://github.com/trasparenzai/config-service

OpenAPI e Swagger UI
--------------------

Una volta avviato il servizio i servizi REST sono documentati tramite OpenAPI 
e consultabili all'indirizzo /swagger-ui/index.html.

.. figure:: images/openapi-config-service.png
  :width: 800
  :alt: Interfaccia Swagger UI all'OpenAPI del servizio

L'OpenAPI del servizio di staging è disponibile all'indirizzo 
https://dica33.ba.cnr.it/config-service/swagger-ui/index.html.


Sicurezza
---------

L'accesso in lettura alla configurazione di tipo *Spring Cloud Config* 
disponibile al path **/config** è protetto con autenticazione di tipo 
*Basic Auth*, i microservizi che vogliono utilizzare questo path per ottenere
la configurazione devono utilizzare l'utente e la password sepcificati tramite
i parametri *spring.security.user.name* e *spring.security.user.password* , i 
quali possono essere specificati nel *docker-compose.yml* come nell'esempio
seguente::

  - spring.security.user.name=config-service-user
  - spring.security.user.password=PASSWORD_DA_IMPOSTARE_E_CONDIVIDERE_CON_I_CLIENT

Invece gli endpoint REST di questo servizio disponibili al path **/properties**
sono protetti tramite autenticazione OAuth con Bearer Token.
È necessario configurare l'IDP da utilizzare per validare i token OAuth tramite
le due proprietà impostabili nel *docker-compose.yml* come nell'esempio seguente::

  - spring.security.oauth2.resourceserver.jwt.issuer-uri=https://dica33.ba.cnr.it/keycloak/realms/trasparenzai
  - spring.security.oauth2.resourceserver.jwt.jwk-set-uri=https://dica33.ba.cnr.it/keycloak/realms/trasparenzai/protocol/openid-connect/certs

Per l'accesso in HTTP GET all'API è sufficiente essere autenticati, per gli
endpoint accessibili con PUT/POST/DELETE è necessario oltre che essere
autenticati che il token OAuth contenga un role ADMIN o SUPERUSER.
Autenticazione
==============

La piattaforma necessità di un Identity Provider OAuth2 per l'autenticazione e
autorizzazione nell'accesso ai componenti dell'architettura.

Nell'ambiente di staging è stato utilizzato Keycloak come Identity Provider ma
un qualunque IDP compatibile OAuth2 può andare bene.

Per configurare i vari componenti è necessario procurarsi l'endpoint per ottenere
il token jwt e l'endpoint contenente i certificati pubblici del IDP, per esempio::

  - jwt.issuer-uri -> https://dica33.ba.cnr.it/keycloak/realms/trasparenzai 
  - jwt.jwk-set-uri -> https://dica33.ba.cnr.it/keycloak/realms/trasparenzai/protocol/openid-connect/certs

Sarà necessario impostare questi due parametri nei vari microservizi, come
spiegato nel seguito.

Ci sono due tipologie di accesso ai servizi della piattaforma, quello degli
utenti (le persone fisiche) e quello dei client (i vari componenti si 
autenticano se devono comunicare tra di loro).

Per quanto riguarda i client è necessario creare tre *Service Account* di tipo
*OpenId Connect* e autenticazione di tipo **client_credentials**, i tre
client_id devono essere:

  - crawler
  - result-aggregator
  - task-scheduler

I valori dei rispettivi *client secret* dovrà essere impostato nei microservizi 
*crawler-service*, *result-aggregator-service* e *task-scheduler-service*.

A questi tre service account deve inoltre essere assegnato un 
*Service Account Role* di tipo **ROLE_SUPERUSER**.

È inoltre necessario creare un client, sempre di tipo *OpenId Connect*, per
l'interfaccia Web Angular JS, il client si deve chiamare **angular-public** e
deve avere impostato come **valid redirect url** il valore 
**https://www.trasparenzai.it/***.
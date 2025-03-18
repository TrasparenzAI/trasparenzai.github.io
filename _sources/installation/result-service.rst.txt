Result Service
==============

Result Service è il componente che si occupa di gestire i risultati delle
verifiche sulla corrispondenza dei siti degli enti pubblici.

Result Service mantiene nel proprio datastore locale le informazioni
relative ai risultati di validazione.

Il codice sorgente è disponibile su github:
  - https://github.com/cnr-anac/result-service

Nel repository github è compreso anche un script per la prima installazione
del servizio `first-setup.sh <https://github.com/cnr-anac/result-service/blob/main/first-setup.sh>`_.

In particolare è necessario configurare la sezione della sicurezza.

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
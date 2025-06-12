Result Aggregator Service
=========================

Result Aggregator Service è il componente che si occupa di gestire i risultati
delle verifiche sulla corrispondenza, aggregando i risultati di validazione 
con altre informazioni sugli enti pubblici prelevate da altri servizi.

Result Aggregator Service mantiene nel proprio datastore locale le informazioni
relative ai risultati di validazione.

Il codice sorgente è disponibile su github:
  - https://github.com/trasparenzai/result-aggregator-service

Nel repository github è compreso anche uno script per la prima installazione
del servizio `first-setup.sh <https://github.com/trasparenzai/result-aggregator-service/blob/main/first-setup.sh>`_.

Questo servizio ha due dipendenze per funzionare:
 - il :doc:`result-service` da cui leggere le info sulle verifiche
 - il :doc:`public-sites-service` da cui prelevare le info geografiche delle PA

**Attenzione**: se il public-site-service o il result-service non sono avviati
sullo stesso server tramite docker è necessario configurare l'url a cui
rispondono, modificando nel **.env** le variabili d'ambiente 
*TRANSPARENCY_PUBLIC_SITE_URL* e *TRANSPARENCY_RESULT_SERVICE_URL*.

Per esempio nel **.env**::

  TRANSPARENCY_PUBLIC_SITE_URL=https://dica33.ba.cnr.it/public-sites-service
  TRANSPARENCY_RESULT_SERVICE_URL=https://dica33.ba.cnr.it/result-service

Per configurare il client REST che accede a questi due servizi è necessario
configurare nel .env il parametro **OIDC_CLIENT_SECRET**, impostando il valore
generato quando si è creatp il *Service Account* *result-aggregator*, vedi
:doc:`authentication`.

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

Result Aggregator Service
=========================

Result Aggregator Service è il componente che si occupa di gestire i risultati
delle verifiche sulla corrispondenza, aggregando i risultati di validazione 
con altre informazioni sugli enti pubblici prelevate da altri servizi.

Result Aggregator Service fornisce alcuni servizi REST utilizzabili in
produzione per:

 * inserire, aggiornare e cancellare all'interno del servizio le informazioni
   di una verifica effettuata su un sito web di una PA ed dei dati geografici
   degli enti pubblici
 * esportare in geoJson i risultati delle validazioni presenti arricchiti con
   la geolicazzazione degli enti

Il codice sorgente di questo componente è disponibile su GitHub:
 - https://github.com/cnr-anac/result-aggregator-service

OpenAPI e Swagger UI
--------------------

Una volta avviato il servizio i servizi REST sono documentati tramite OpenAPI 
e consultabili all'indirizzo /swagger-ui/index.html.

.. figure:: images/openapi-result-service.png
  :width: 800
  :alt: Interfaccia Swagger UI all'OpenAPI del servizio

L'OpenAPI del servizio di staging è disponibile all'indirizzo 
https://dica33.ba.cnr.it/result-aggregator-service/swagger-ui/index.html.


Dipendenze e configurazione
---------------------------

Questo servizio ha due dipendenze dagli altri componenti per funzionare:

 * il `Result Service <https://github.com/cnr-anac/result-service>`_ da cui 
   leggere le info sulle verifiche
 * il `Public Site Service <https://github.com/cnr-anac/public-sites-service>`_ 
   da cui prelevare le info geografiche delle PA

L'indirizzo di entrambi questi servizi è da configurabile nel file 
`application.properties <https://github.com/cnr-anac/result-aggregator-service/blob/main/src/main/resources/application.properties>`_
oppure tramite variabili d'ambiente se avviato tramite Docker.

Sicurezza
---------

Gli endpoint REST di questo servizio sono protetti tramite autenticazione OAuth
con Bearer Token.
E' necessario configurare l'idp da utilizzare per validare i token OAuth tramite
le due proprietà mostrare nell'esempio seguente::

  - spring.security.oauth2.resourceserver.jwt.issuer-uri=https://dica33.ba.cnr.it/keycloak/realms/trasparenzai
  - spring.security.oauth2.resourceserver.jwt.jwk-set-uri=https://dica33.ba.cnr.it/keycloak/realms/trasparenzai/protocol/openid-connect/certs

Per l'accesso in HTTP GET all'API è sufficiente essere autenticati, per gli
endpoint accessibili con PUT/POST/DELETE è necessario oltre che essere autenticati
che il token OAuth contenga un role ADMIN o SUPERUSER.

Inoltre questo servizio interagisce con il _result_service_ e il
_public_site_service_ per prelevare i risultati da aggregare.

Per configurare il client REST che accede a questi due servizi è necessario 
configurare questi parametri nel *docker-compose.yml*, in particolare
verificare *client-id*, *client-secret* e *issuer-uri*.

Esempio di configurazione dell'environment nel docker-compose.yml::

  # Generare un Service Account Oidc con questo client-id, oppure cambiare questo valore
  - spring.security.oauth2.client.registration.oidc.client-id=result-aggregator
  # Client Secret da generare nel Identity Provider e impostare qui
  - spring.security.oauth2.client.registration.oidc.client-secret=client_secret_da_generare
  # URL dell'issuer OIDC da impostare
  - spring.security.oauth2.client.provider.oidc.issuer-uri=https://dica33.ba.cnr.it/keycloak/realms/trasparenzai
  # - spring.security.oauth2.client.registration.oidc.authorization-grant-type=client_credentials #DEFAULT
  # - spring.security.oauth2.client.registration.oidc.scope=openid #DEFAULT
  # - spring.security.oauth2.client.registration.oidc.provider=oidc #DEFAULT

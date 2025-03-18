Public Sites Service
====================

Public Sites Service è il componente che si occupa di gestire le informazioni
principali relative agli enti pubblici italiani ed in particolare i siti
istituzionali.

Public Sites Service mantiene nel proprio datastore locale le informazioni
degli enti che possono essere inserite/aggiornate tramite gli OpenData di
IndicePA, oppure inserite tramite appositi servizi endopoint REST.
Il servizio utilizza Nominatim di OpenStreetMap per la geolocalizzazione degli
indirizzi degli enti pubblici.

Il codice sorgente è disponibile su github:
  - https://github.com/cnr-anac/public-sites-service

Nel repository github è compreso anche un script per la prima installazione
del servizio `first-setup.sh <https://github.com/cnr-anac/public-sites-service/blob/main/first-setup.sh>`_.

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

Integrazione API Google Maps
-----------------------------
Il servizio è già predisposto per l'integrazione con l'API di Google Maps per
la geocalizzazione degli indirizzi degli enti pubblici.
L'API Google Maps fornisce solitamente una migliore individuazione delle 
coordinate GPS degli indirizzi indicati nel IndicePA.
L'API Google Maps è però a pagamento, con un freetier per un numero iniziale di
ricerche, è necessario procurarsi una Google Maps Key per poter utilizzare questo
servizio, la quale richiede di inserire una carta di credito per gli eventuali
pagamento oltre il freetier.

L'utilizzo della API Google Maps può essere attivata nel public sites service
impostando questo parametri nell'environment del docker-compose.yml::

  - transparency.google.maps.enabled=true
  - transparency.google.maps.key=LA_CHIAVE_DA_PRELEVARE_DAI_SISTEMI_GOOGLE 

Installazione e configurazione
==============================

Prima di cominciare assicurati di avere a disposizione sufficiente risorse di
CPU, memoria RAM e spazio disco per l'utilizzo desiderato della piattaforma.
Controlla la sezione `Risorse hardware consigliate <cpu_disk_memory_sizing.html>`_ 
per verificare il dimensionamento necessario in produzione.

La modalità consigliata di installazione è tramite **Docker**, assicurati
che su ogni ogni server sui cui effettuare il deploy dei componenti
dell'architettura sia installato sia
`Docker <https://docs.docker.com/engine/install/>`_, che
`Docker Compose <https://docs.docker.com/compose/install/linux/>`_.

La piattaforma è composta da diversi servizi e microservizi, esposti solitamente
tramite interfacce REST via HTTP/HTTPS.
L'esposizione dei servizi/microservizi pubblici tramite protocollo cifrato HTTPS
è fortemente consigliata, è possibile utilizzare a questo scopo uno dei vari 
proxy http/https disponibili.
Per la piattaforma fornita in staging è stato utilizzato 
`Traefik <https://traefik.io/traefik/>`_.

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Descrizione procedure installazione e configurazione

   authentication
   authorization
   config-service
   public-sites-service
   result-service
   result-aggregator-service
   task-scheduler-service
   cpu_disk_memory_sizing
Componenti principali
=====================

Il sistema TrasparenzAI è di tipo modulare ed è composta sia da componenti sviluppati ad-hoc per il progetto che da software opensource già disponibili.

Di seguito la lista dei componenti sviluppati per il progetto:

  * https://github.com/trasparenzai/public-sites-service
  * https://github.com/trasparenzai/config-service
  * https://github.com/trasparenzai/result-service
  * https://github.com/trasparenzai/result-aggregator-service
  * https://github.com/trasparenzai/task-scheduler-service
  * https://github.com/trasparenzai/rule-service
  * https://github.com/trasparenzai/conductor
  * https://github.com/trasparenzai/workflow-definition
  * https://github.com/trasparenzai/crawler-service
  * https://github.com/trasparenzai/ui-service
 
Ogni componente è stato realizzato nell'ottica di un possibile riuso da parte della comunità opensource italiana (per esempio, progetti di crawling e analisi di siti di web similari).
I componenti sono stati sviluppati principalmente in Java (con `Spring Boot <https://spring.io/projects/spring-boot>`_) e Python (`FastAPI <https://fastapi.tiangolo.com/>`_ e `Uvicorn <https://www.uvicorn.org/>`_) per la parte backend e typescript (`Angular <https://angular.dev/>`_) per la parte frontend.

I software opensource utilizzati sono:
  * `Keycloak <https://www.keycloak.org/>`_
  * `Postgresql <https://www.postgresql.org/>`_
  * `Minio <https://min.io/>`_
  * `Selenium Grid <https://www.selenium.dev/documentation/grid/>`_
  * `Selenium Node Chrome <https://hub.docker.com/r/selenium/node-chrome>`_
  * `Conductor <https://conductor-oss.org/>`_
  * `Traefik <https://traefik.io/traefik/>`_

Del software *Conductor* è stato effettuato un fork per introdurre l'autenticazione
come client OAuth2 nei task che interagiscono con le API REST della piattaforma.

.. toctree::
   :maxdepth: 3
   :caption: Descrizione dei componenti

   public-sites-service
   config-service
   result-service
   result-aggregator-service
   task-scheduler-service
   rule-service
   conductor-service
   crawler-service
   ui-service
   

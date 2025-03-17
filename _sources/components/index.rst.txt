Componenti principali
=====================

Il sistema TrasparenzAI è di tipo modulare ed è composta sia da componenti
sviluppati ad-hoc per il progetto che da software opensource già disponibili.

I componenti sviluppati per il progetto sono:

  * https://github.com/cnr-anac/public-sites-service
  * https://github.com/cnr-anac/rule-service
  * https://github.com/cnr-anac/result-service
  * https://github.com/cnr-anac/result-aggregator-service
  * https://github.com/cnr-anac/task-scheduler-service
  * https://github.com/cnr-anac/configuration-service
  * https://github.com/cnr-anac/workflow-definition
  * https://github.com/cnr-anac/ui-service

Alcuni di questi componenti sono stati sviluppati in un ottica di possibile 
riuso da parte della comunità opensource italiana, alcuni così come sono, altri
come esempio per progetti di crawling e analisi di siti di web similari.
I componenti stati sviluppati principalmente in Java 
(con `Spring Boot <https://spring.io/projects/spring-boot>`_) e Python 
(`FastAPI <https://fastapi.tiangolo.com/>`_ e `Uvicorn <https://www.uvicorn.org/>`_) 
per la parte backend e typescript (`AngularJS <https://angularjs.org/>`_) per
la parte frontend.

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
   :maxdepth: 2
   :hidden:
   :caption: Descrizione dei componenti

   public-sites-service
   config-service
   result-service
   result-aggregator-service
   task-scheduler-service
   
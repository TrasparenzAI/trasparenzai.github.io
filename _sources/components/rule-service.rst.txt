Rule Service
====================

Rule Service è il componente che definisce ed implementa le regole relative al D.Lgs. n. 33-2013 sulla trasparenza nella PA.

Fornisce l'albero delle regole definito in `application.yaml <https://github.com/trasparenzai/rule-service/blob/main/src/main/resources/application.yaml#L66-L554>`__ oppure all'interno del :doc:`config-service` ,
che quindi può essere modificato o ampliato sia attraverso variabili di ambiente o della JVM prima di avviare il servizio,
oppure aggiornando la configurazione per poi successivamente invocare l'endpoint `dell'actuator <http://localhost:8080/actuator/refresh>`__ per recepire le modifiche. 

É possibile interagire con il servizio attraverso degli endpoint REST che permettono la consultazione dell'albero
delle regole in formato **json**, e la verifica di una o più regole su un contenuto **html**  

Docker
------
Il servizio è dotato del plugin **jib** che permette di effettuare la **build** tramite `gradle <https://gradle.org/>`__ e fornisce l'immagine per l'esecuzione tramite **docker**

.. code-block::

    ./gradlew jibDockerBuild
    docker run -p 8080:8080 -ti rule-service:{version}

La documentazione relativa ai servizi REST è consultabile `qui <http://localhost:8080/api-docs>`__ ed è possibile interagire
con i servizi attraverso **Swagger** alla seguente `URL <http://localhost:8080/swagger-ui/index.html>`__, inoltre è possibile visualizzare l'albero delle regole in formato `json <http://localhost:8080/v1/rules>`__

Oppure verificare la regola **root** ad esempio attraverso una `cURL <https://it.wikipedia.org/wiki/Curl>`__ con un html di esempio:

.. code-block::

    curl -X POST http://localhost:8080/v1/rules -H 'Content-type:application/json' --data 'PGh0bWw+CiAgICA8aGVhZD4KICAgICAgICA8dGl0bGU+R2VuZXJpY2EgQW1taW5pc3RyYXppb25lPC90aXRsZT4KICAgIDwvaGVhZD4KICAgIDxib2R5PgogICAgICAgIDxwPlBhcnNlZCBIVE1MIGludG8gYSBkb2MuPC9wPgogICAgICAgIDxhIGhyZWY9Ii9hbW1pbmlzdHJhemlvbmUiPkFtbWluaXN0cmF6aW9uZSBUcmFzcGFyZW50ZTwvYT4KICAgICAgICA8YSBocmVmPSIvcHJvZ3JhbW1hdHJhc3BhcmVuemEiPlByb2dyYW1tYSBwZXIgbGEgVHJhc3BhcmVuemE8L2E+CiAgICA8L2JvZHk+CjwvaHRtbD4='| jq .

In alternativa scaricare il contenuto del Sito istituzionale di una Pubblica Amministrazione

.. code-block::

    curl "https://www.anticorruzione.it"|base64 > base64.html
    curl -X POST http://localhost:8080/v1/rules -H 'Content-type:application/json' --data @base64.html |jq .

La risposta **json** del servizio: 

.. code-block:: JSON

    {
        "url": "https://www.anticorruzione.it/amministrazione-trasparente",
        "ruleName": "amministrazione-trasparente",
        "term": "Amministrazione Trasparente",
        "content": "Amministrazione Trasparente",
        "where": "text",
        "leaf": false,
        "status": 200,
        "score": 4.3884144
    }

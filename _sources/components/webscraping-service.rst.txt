Web Scraping service
====================

Il servizio di Web Scraping ha il compito di interfacciarsi con i siti web visitati dalla piattaforma e recuperare le 
informazioni pubblicate via web.
In particolare, riceve una richiesta di accesso al sito specificato dal Conductor e in risposta fornisce la pagina acquisita, 
codificandola in formato Base64, e interagisce con l'object store per l'archiviazione del contenuto della pagina e/o dello 
screenshot renderizzato dal browser.

I dettagli relativi agli endpoint e ai JSON da fornire sono disponibili agli url /doc e /redoc in formato Swagger/OpenAPI .

In particolare, il webscraping-service si aspetta di ricevere un JSON contenente i seguenti parametri:
  * url: contiene l'url da visitare, anche privo di schema http/https
  * crawlingMode: httpStream | htmlSource - contiene la modalità di crawling
  * saveObject: False | True - indica se l'oggetto deve essere salvato nell'object store o semplicemente restituito in risposta alla richiesta
  * saveScreenshot: False | True - indica se lo screenshot della pagina deve essere salvato nell'object store.

  .. code-block:: JSON

    {
        "url": "www.cnr.it",
        "crawlingMode": "htmlSource",
        "saveObject": True,
        "saveScreenshot": False,
    }



Relativamente alle modalità di crawling, htmlSource prevede la renderizzazione della pagina mediante un browser pilotato dal 
Selenium-hub e l'estrazione dal browser del sorgente HTML.

Nel caso invece delle richieste httpStream, il servizio di webscraping si connette alla porta TCP sulla quale ascolta il web server
analizzato e recupera lo stream HTTP riveniente dalla richiesta GET /url .

Questo metodo ha il vantaggio di essere estremamente veloce e di richiedere minori risorse computazionali ma ha lo svantaggio di 
non costruire la pagina in maniera corretta, in presenza di contenuti dinamici.

Di conseguenza il metodo htmlSource è da preferire poichè la pagina viene costruita utilizzando un browser pilotato da selenium-hub 
e richiedendo al browser di fornire il sorgente HTML della pagina costruita in fase di navigazione, simulando pertanto la stessa 
esperienza che avrebbe un navigatore accedendo al sito.



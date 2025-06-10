Homepage
========

La homepage della piattaforma TrasparenzAI è stata progettata per garantire immediatezza e semplicità nella consultazione dei risultati ottenuti. L'interfaccia mostra chiaramente i dati relativi all’ultima scansione effettuata, fornendo un quadro sintetico del numero di pubbliche amministrazioni analizzate e della conformità riscontrata. È possibile visualizzare la cronologia dettagliata dei controlli precedenti, ciascuno accompagnato da un report scaricabile in formato CSV, e una timeline interattiva che permette di consultare rapidamente l’evoluzione dei controlli nel tempo.

.. _home-img:
.. figure:: images/ui-homepage_full.png
  :width: 800
  :alt: Homepage

  Homepage - Interfaccia Web

Header (Intestazione)
---------------------

#. Presenta la barra superiore con il link al protocollo di collaborazione tra Consiglio Nazionale delle Ricerche e Autorità Nazionale Anticorruzione nell'ambito del quale è stato sviluppata la **piattaforma TrasparenzAI** (`Protocollo d’intesa tra l’Autorità Nazionale Anticorruzione e il Consiglio Nazionale delle Ricerche del 7 agosto 2023 <https://www.anticorruzione.it/-/protocollo-d-intesa-tra-l-autorit%C3%A0-nazionale-anticorruzione-e-il-consiglio-nazionale-delle-ricerche-7-agosto-2023>`__) e i link di accesso rapido a credits, documentazione, login.
#. Il menu di navigazione principale per l'accesso alle principali funzioni "Cerca amministrazioni", "Mappa delle Amministrazioni", "Regole", "Grafici e Mappe", "Esplora Sezioni". Il Menù è responsive e può essere collassato su dispositivi mobili.

.. _home-img:
.. figure:: images/ui-homepage_header.png
  :width: 800
  :alt: Homepage - Header

  Homepage - Header

Homepage - sezione ultimo controllo
-----------------------------------

Layout a griglia con card che illustrano i principali dati dell'ultimo controllo eseguito.
La prima card illustra i dati ragruppati per stato, la card centrale invece
mostra una torta con le percentuali degli stati la cui legenda è esplicitata nell'ultima card a destra.

.. _home-last_scan-img:
.. figure:: images/ui-homepage_sez-1.png
  :width: 800
  :alt: Homepage - Ultima scansione

  Homepage - Ultima scansione

Homepage - sezione cronologia dei controlli
-------------------------------------------

La piattaforma offre un riepilogo visivo delle scansioni precedenti, ciascuna con dati sintetici e la possibilità di esportare i risultati.
La sezione è composta da un carousel che permette di scorrere la cronologia dei controlli memorizzati dal sistema. Le informazioni includono data e ora del controllo, numero di amministrazioni analizzate, conformità rilevate. Qualora si abbia il ruolo necessario, è possibile l'esportazione in formato *csv* dei dati.
Il link *"LEGGI DI PIU' ->"* mostra la distribuzione geografica dei dati del singolo controllo.

.. _home-carousel-img:
.. figure:: images/ui-homepage_sez-2.png
  :width: 800
  :alt: Homepage - Carousel

  Homepage - Carousel

Homepage - sezione timeline
---------------------------

La sezione in homepage presenta una timeline verticale delle scansioni con il riepilogo dei risultati ottenuti.
Ogni nodo nella linea del tempo consente di consultare nel dettaglio i dati della relativa scansione, fornendo una visione cronologica dell’attività di monitoraggio.
Per ogni nodo è anche presente un link attivo alla distribuzione geografica dei dati del singolo controllo.

.. _home-timeline-img:
.. figure:: images/ui-homepage_sez-3.png
  :width: 800
  :alt: Homepage - Timeline

  Homepage - Timeline

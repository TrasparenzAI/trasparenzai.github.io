UI service
=================

UI Service integra e mostra i dati presenti nei vari servizi fornendo la possibilità, avendo gli
opportuni permessi, di attivare le funzionalità preposte all'inserimento e alla cancellazione degli stessi,
inoltre è possibile attivare l'autenticazione su tutte le pagine, o in alternativa di accedere senza
autenticazione per la sola consultazione dei dati, per poi richiederla successivamente.

L'interfaccia web è progettata seguendo le linee guida dell’**accessibilità**, della **responsività** e
del **design istituzionale**, secondo quanto previsto da `Designers Italia <https://designers.italia.it/>`__.
L’aspetto è professionale, ordinato e coerente con la comunicazione della Pubblica Amministrazione.

.. _home-img:
.. figure:: https://raw.githubusercontent.com/trasparenzai/ui-service/refs/heads/main/home.png
  :width: 800
  :alt: Home Page

  Home Page - Interfaccia Web

Header (Intestazione)
---------------------
#. Presenta la barra superiore istituzionale con il riferimento al `Protocollo d’intesa tra l’Autorità Nazionale Anticorruzione e il Consiglio Nazionale delle Ricerche del 7 agosto 2023 <https://www.anticorruzione.it/-/protocollo-d-intesa-tra-l-autorit%C3%A0-nazionale-anticorruzione-e-il-consiglio-nazionale-delle-ricerche-7-agosto-2023>`__, e al menu di accesso rapido (login, lingua, credits).
#. Sezione contenete il logo, con il nome e la descrizione del servizio e il link alla ricerca delle amministrazioni
#. Il menu di navigazione principale è responsive e può essere collassato su dispositivi mobili,
   presenta le seguenti voci:

.. hlist::
    :columns: 4

    * Mappa delle Amministrazioni
    * Regole
    * Grafici e Mappe
    * Esplora Sezioni

Sezione ultimo controllo / contenuti principali
-----------------------------------------------
Layout a griglia con card che illustrano i principali dati dell'ultimo controllo eseguito.

La prima card illustra i dati ragruppati per stato, la card centrale invece
mostra una torta con le percentuali degli stati la cui legenda è esplicitata nell'ultima card a destra.

Sezione cronologia dei controlli
-----------------------------------------------
La sezione è composta da un carousel che permette di scorrere la cronologia dei controlli evidenziando i dati
contentuti nel singolo controllo raggruppati per stato, permette l'estrazione *csv* dei dati
qualora si abbia il ruolo necessario, e contiene il link attivo alla distribuzione
geografica dei dati del singolo controllo.

.. _home-carousel-img:
.. figure:: images/ui-carousel.png
  :width: 800
  :alt: Home Page - Carousel

  Home Page - Carousel

Sezione timeline
-----------------------------------------------
La sezione contiene la visualizzazione cronologica dei controlli effettuati, descrive i risultati ottenuti per ogni
singolo controllo e contiene anch'essa il link attivo alla distribuzione geografica dei dati del singolo controllo.

.. _home-timeline-img:
.. figure:: images/ui-timeline.png
  :width: 800
  :alt: Home Page - Timeline

  Home Page - Timeline

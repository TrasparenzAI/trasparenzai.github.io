Risorse hardware consigliate
=============================

I test di funzionamento in produzione hanno evidenziato la necessità
di suddividere su almeno 3 distinti virtual machine l'architettura del sistema (SERVER-A, SERVER-B, SERVER-C).

In particolare è consigliato di mantenere separata la parte del crawler,
dalla parte del coordinamento (conductor-service), dalla parte di gestione
dei risultati e loro visualizzazione via Web.
.. _hwa-tab:
.. list-table:: Parametri di Input per il flusso principale
   :header-rows: 1

   * - *Nome*
     - *Descrizione*
     - *Valore consigliato/default*
     - *Può essere Vuoto?*
   * - **page_size**
     - Dimensione della pagina per il recupero delle PA
     - 2000
     - No

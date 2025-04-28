Risorse hardware consigliate
=============================

I test di funzionamento in produzione hanno evidenziato la necessità
di suddividere su almeno 3 distinti virtual machine l'architettura del sistema (SERVER-A, SERVER-B, SERVER-C).

In particolare è consigliato di mantenere separata la parte del crawler,
dalla parte del coordinamento (conductor-service), dalla parte di gestione
dei risultati e loro visualizzazione via Web.

.. _hwa-tab:
.. list-table:: **Requisiti minimi SERVER-A**

   * - **Software di virtualizzazione**
     - VMware vSphere 7.5
   * - **HW CPU**
     - Intel Xeon CPU E7-4890v2
   * - **VM Virtual CPU**
     - 32 vCPU
   * - **VM RAM**
     - 64GB
   * - **VM HDD data**
     - 1TB
   * - **VM HDD sistema operativo**
     - 500GB
   * - **Sistema operativo VM**
     - Ubuntu Server 24.04
   * - **Servizi e componenti**
     - config-service, public-site-service, result-aggregator-service, ui-service, task-scheduler-service, Traefik, Keycloak, Minio

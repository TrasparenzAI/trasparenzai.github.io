Risorse hardware consigliate
=============================

I test di funzionamento in produzione hanno evidenziato la necessità di suddividere l'architettura del sistema su almeno 3 distinte virtual machine (*VM-A*, *VM-B*, *VM-C*). In particolare, attese le risorse computazionali necessarie ai vari servizi, si consiglia l'installazione della piattaforma *TrasparenzAI* su almeno tre sistemi separati: VM-A) crawler ; VM-B) coordinamento; VM-C) gestione dei risultati e visualizzazione via Web.

Di seguito le risorse utilizzate per i test di funzionameto della piattaforma *TrasparenzAI*:


.. _hwa-tab:
.. list-table:: Risorse VM-A

   * - **Software di virtualizzazione**
     - VMware vSphere 7.5
   * - **HW CPU**
     - Intel Xeon Gold 6342
   * - **VM Virtual CPU**
     - 32 vCPU
   * - **VM RAM**
     - 64GB
   * - **VM HDD sistema operativo**
     - 500GB
   * - **Sistema operativo VM**
     - Ubuntu Server 24.04
   * - **Servizi e componenti**
     - crawler-service, `Selenium (Chrome Driver) <https://hub.docker.com/r/selenium/hub>`__

.. _hwb-tab:
.. list-table:: Risorse VM-B

   * - **Software di virtualizzazione**
     - VMware vSphere 7.5
   * - **HW CPU**
     - Intel Xeon CPU E7-4890v2
   * - **VM Virtual CPU**
     - 32 vCPU
   * - **VM RAM**
     - 32GB
   * - **VM HDD data**
     - 2TB
   * - **VM HDD sistema operativo**
     - 500GB
   * - **Sistema operativo VM**
     - Ubuntu Server 24.04
   * - **Servizi e componenti**
     - :ref:`Rule Service`, :ref:`Conductor Service`

.. _hwc-tab:
.. list-table:: Risorse VM-C
   
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
     - :ref:`Config Service`, :ref:`Public Sites Service`, :ref:`Result Aggregator Service`, :ref:`Result Service`, :ref:`UI service`, :ref:`Task Scheduler Service`, `Traefik <https://github.com/traefik>`__, `Keycloak <https://github.com/keycloak/keycloak>`__, `Minio <https://github.com/minio/>`__

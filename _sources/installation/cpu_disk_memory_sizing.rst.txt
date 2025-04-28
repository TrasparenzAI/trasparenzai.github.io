Risorse hardware consigliate
=============================

I test di funzionamento in produzione hanno evidenziato la necessità
di suddividere su almeno 3 distinti virtual machine l'architettura del sistema (`SERVER-A <https://cnr-anac.github.io/trasparenzai-doc/installation/cpu_disk_memory_sizing.html#hwa-tab>`__, `SERVER-B <https://cnr-anac.github.io/trasparenzai-doc/installation/cpu_disk_memory_sizing.html#hwB-tab>`__, `SERVER-C <https://cnr-anac.github.io/trasparenzai-doc/installation/cpu_disk_memory_sizing.html#hwc-tab>`__).

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
     - config-service, public-site-service, result-aggregator-service, result-service, ui-service, task-scheduler-service, Traefik, Keycloak, Minio

.. _hwb-tab:
.. list-table:: **Requisiti minimi SERVER-B**

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
     - rule-service, conductor-service

.. _hwc-tab:
.. list-table:: **Requisiti minimi SERVER-C**

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
     - crawler-service, Selenium + WebDriver Google Chrome

Risorse hardware consigliate
=============================

I test di funzionamento in produzione hanno evidenziato la necessità
di suddividere su almeno 3 distinti virtual machine l'architettura del sistema (`SERVER-A <#hwa-tab>`__, `SERVER-B <#hwb-tab>`__, `SERVER-C <#hwc-tab>`__).

In particolare è consigliato di mantenere separata la parte del crawler,
dalla parte del coordinamento (`conductor-service <https://cnr-anac.github.io/trasparenzai-doc/components/conductor-service.html>`__), dalla parte di gestione
dei risultati e loro visualizzazione via Web.


**Requisiti minimi SERVER-A**

.. _hwa-tab:
.. list-table:: Requisiti minimi SERVER-A

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
     - `config-service <https://cnr-anac.github.io/trasparenzai-doc/components/config-service.html>`__, `public-site-service <https://cnr-anac.github.io/trasparenzai-doc/components/public-site-service.html>`__, `result-aggregator-service <https://cnr-anac.github.io/trasparenzai-doc/components/result-aggregator-service.html>`__, `result-service <https://cnr-anac.github.io/trasparenzai-doc/components/result-service.html>`__, `ui-service <https://cnr-anac.github.io/trasparenzai-doc/components/ui-service.html>`__, `task-scheduler-service <https://cnr-anac.github.io/trasparenzai-doc/components/task-scheduler-service.html>`__, `Traefik <https://github.com/traefik>`__, `Keycloak <https://github.com/keycloak/keycloak>`__, `Minio <https://github.com/minio/>`__


**Requisiti minimi SERVER-B**

.. _hwb-tab:
.. list-table:: Requisiti minimi SERVER-B

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
     - `rule-service <https://cnr-anac.github.io/trasparenzai-doc/components/rule-service.html>`__, `conductor-service <https://cnr-anac.github.io/trasparenzai-doc/components/conductor-service.html>`__


**Requisiti minimi SERVER-C**

.. _hwc-tab:
.. list-table:: Requisiti minimi SERVER-C

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
     - crawler-service, `Selenium (Chrome Driver) <https://github.com/Selenium/selenium>`__

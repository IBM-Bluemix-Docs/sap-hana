---



copyright:
  years: 2017, 2018
lastupdated: "2018-05-30"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Pianificazione del tuo scenario di sistema
{: #planning-your-system-landscape}

Uno *scenario* SAP è un gruppo di due o più *sistemi* SAP che normalmente includono lo sviluppo, la qualità e il test e la produzione. Un sistema SAP è formato da una o più *istanze SAP*, che sono un gruppo di processi avviati e arrestati contemporaneamente. Per ulteriori informazioni sugli scenari SAP, consulta [*SAP Business Suite on IBM X6 Systems Reference Architecture*](https://lenovopress.com/redp5073.pdf). 
{: shortdesc}

Esistono molte configurazioni dello scenario possibili, come server (dimensione)/archiviazione (dimensione), per tutte le soluzioni SAP nel mercato. Queste soluzioni includono i prodotti basati su SAP NetWeaver, come [SAP Business Suite](https://open.sap.com/courses/suitehana1), SAP Business Warehouse e tutti i componenti aggiuntivi di SAP specifici, con i server nel supporto di {{site.data.keyword.cloud}} SAP-Certified Infrastructure. Ulteriori soluzioni da tenere presenti sono i software di terze parti che è possibile integrare con SAP. 

SAP HANA può essere eseguito come un database per una soluzione basata sullo stack SAP NetWeaver o come un'entità autonoma a seconda del tuo scenario di utilizzo. Per entrambi gli scenari, l'offerta {{site.data.keyword.cloud_notm}} fornisce server certificati SAP NetWeaver preconfigurati in cui lo scenario in questi server può essere creato da qualsiasi altro server.

Vuoi avere più informazioni possibili quando determini la dimensione del tuo server in base alle applicazioni che pianifichi di eseguire, la potenziale crescita e le prestazioni. In aggiunta, tieni presente i tuoi requisiti di memoria e archiviazione delle tue applicazioni. I sistemi SAP in uno scenario hanno requisiti specifici per la connettività, tra loro o con sistemi esterni. Per ulteriori informazioni, vedi [Elementi da considerare quando pianifichi il tuo scenario SAP](/docs/infrastructure/sap-hana/hana-considerations.html).

La tabella 1 contiene la procedura all'interno del processo di pianificazione. Utilizzala per creare il tuo scenario SAP di destinazione.

Tabella 1. Panoramica sul processo di pianificazione

| Passo | Dettagli |
| --- | --- |
| 1 | [Ottieni SAP e le credenziali {{site.data.keyword.cloud_notm}} e crea gli account](/docs/infrastructure/sap-hana/hana-get-credentials.html) |
| 2 | [Controlla ogni SAP rilevante e la documentazione {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana/hana-review-doc.html) |
| 3 | [Determina le tue applicazioni SAP](/docs/infrastructure/sap-hana/hana-determine-apps.html) |
| 4 | [Dimensiona il server](/docs/infrastructure/sap-hana/hana-size-server.html) |
| 5 | [Determina la tua configurazione](/docs/infrastructure/sap-hana/hana-determine-configuration.html) |

## Passi successivi

Seleziona il passo appropriato nella tabella 1 per iniziare la pianificazione del tuo scenario SAP.

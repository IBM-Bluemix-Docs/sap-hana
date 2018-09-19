---



copyright:
  years: 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 5. Configurazione della tua infrastruttura IBM Cloud per supportare SAP HANA a più nodi
{: #multi-node-storage}

{{site.data.keyword.cloud_notm}} supporta l'archiviazione SAP HANA a più nodi per i carichi di lavoro OLAP (online analytical processing), come SAP Business Warehouse (SAP BW) e SAP BW/4HANA. La soluzione {{site.data.keyword.cloud}} per SAP HANA a più nodi è costituita da un massimo di 15+1 nodi (15 nodi di lavoro, più uno standard) fino a un massimo di 30 TB di memoria utilizzata per un sistema.

Con SAP HANA a più nodi crea un solo sistema SAP HANA. I dati vengono distribuiti tra questi nodi, che formano un solo database. La configurazione a più nodi supporta la scalabilità e l'alta disponibilità tramite la configurazione standby. L'offerta {{site.data.keyword.cloud_notm}} per questa configurazione segue [SAP HANA Tailored Data Center Integration](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/) (TDI) e utilizza i server certificati SAP-HANA {{site.data.keyword.cloud_notm}} per l'archiviazione aziendale condivisa e centralizzata.

*Nota* che devi seguire le linee guida di installazione descritte in [Ordine del tuo sistema a più zone](#ordering) per soddisfare i requisiti SAP HANA TDI ed essere supportato da SAP.

Segui le linee guida in [Sizing SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) per determinare la dimensione necessaria per il tuo sistema SAP HANA di destinazione, inclusa la quantità totale di memoria e archiviazione richiesta dalla tua distribuzione. I requisiti di ridimensionamento ti aiutano a stabilire il numero di nodi SAP HANA necessari al tuo sistema SAP HANA a più nodi e l'archiviazione necessaria per ospitare i dati.

## Controllo della topologia di rete e del layout di archiviazione
{: #reviewing-topology}

La figura 1 mostra la topologia di rete necessaria per l'infrastruttura {{site.data.keyword.cloud_notm}} come una configurazione Service SAP HANA TDI.

Figura 1. Infrastruttura IBM Cloud come una topologia di rete Service SAP HANA TDI

![Figura 1. Infrastruttura IBM Cloud come una topologia di rete Service SAP HANA TDI](/images/SAP-BW.png "Infrastruttura IBM Cloud come una topologia di rete Service SAP HANA TDI")

## Configurazione dei tuoi prerequisiti
{: #prerequisites}

SAP HANA a più nodi richiede che alcune reti siano in uso per il suo funzionamento. Prima di ordinare gli altri componenti del tuo sistema, queste reti devono essere impostate correttamente, insieme ai nodi del database. È necessario
* Una rete lato client, che collega i server dell'applicazione SAP Advanced Business Application Programming (SAP ABAP), i client SAP HANA Studio e tutti gli altri client di rete al sistema a più nodi. Le opzioni di disponibilità e velocità effettiva della rete dipendono dallo scenario di utilizzo del tuo sistema SAP HANA a più nodi. Considerare la quantità di dati trasferiti da e verso il database SAP HANA e la disponibilità dei KPI (Key Performance Indicator) necessari alla tua applicazione.
* Una rete di archiviazione, obbligatoria per collegarti a {{site.data.keyword.blockstoragefull}} di backend e a {{site.data.keyword.filestorage_full_notm}}. Per ottimizzare le prestazioni e la ridondanza, è obbligatoria una rete da 10 GB con due interfacce nell'unione Linux con Link Aggregation Control Protocol (LACP). Senza le prestazioni fornite dalle linee guida sul ridimensionamento di SAP HANA, non possono essere soddisfatti i KPI SAP HANA.
* Una rete internodo per la comunicazione interna SAP HANA configurata in modo equivalente alla rete di archiviazione. La rete internodo viene utilizzata solo tra i nodi e il trasferimento dei dati che può essere necessario tra i nodi durante le operazioni. Questa configurazione di rete obbligatoria è su due adattatori da 10 GB fisici nell'unione Linux con LACP.

## Ordine del tuo sistema a più nodi
{: #ordering}

Per soddisfare i KPI di velocità effettiva e prestazioni richiesti da SAP, le tue VLAN, l'archiviazione e i nodi di calcolo devono essere ordinati nello stesso data center. Se i tuoi componenti vengono distribuiti in più data center, SAP non supporterà il tuo sistema a più nodi.

1. Ordina tre VLAN e server differenti con quattro adattatori (due privati e due pubblici). Per ulteriori informazioni sull'ordine delle VLAN, consulta [Step 1 Ordering Primary and Public VLANs](https://console.bluemix.net/docs/infrastructure/virtualization/advanced-single-site-vmware-reference-architecturesoftlayer.html#step-1-ordering-primary-public-and-private-vlans). Per ulteriori informazioni sull'ordine dei tuoi server, consulta [2. Setting up your infrastructure](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-setting-up-infrastructure.html#set_up_infrastructure).
2. Configura la VLAN privata iniziale come una "VLAN di archiviazione."
3. [Open a ticket](https://console.bluemix.net/docs/get-support/howtogetsupport.html#open-ticket) with {{site.data.keyword.cloud_notm}} Support per
   a. Spostare le interfacce pubbliche alla seconda VLAN
   b. Ordinare due ulteriori adattatori da assegnare alla terza VLAN, che è la VLAN client

Disponi ora del numero di server basato sul tuo lavoro di ridimensionamento e la tua rete è configurata in modo che
* L'archiviazione possa essere collegata a tutti i nodi
* L'installazione SAP HANA a più nodi possa essere eseguita dopo il collegamento dell'archiviazione

Le tue connessioni internodo e LAN di archiviazione vengono configurate dalla distribuzione {{site.data.keyword.cloud_notm}}. Assicurati di aver ordinato le connessioni con due adattatori da 10 GB ognuno con la configurazione del failover. Questa configurazione garantisce la configurazione LACP e l'unione Linux corretta. Contatta il team di supporto di {{site.data.keyword.cloud_notm}} se hai delle domande.

Esistono criteri di prestazioni specifici che devono essere soddisfatti da {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} (Endurance) e {{site.data.keyword.IBM_short}} {{site.data.keyword.filestorage_short}} (Performance). Per i volumi di dati, è obbligatoria l'archiviazione Endurance da 2 TB con un KPI delle prestazioni di 10 IOPS/GB per ogni nodo di lavoro. È obbligatorio un ulteriore volume della stessa dimensione dell'archiviazione condivisa SAP HANA che sarà condiviso da tutti i nodi.

Per i volumi di log, è obbligatorio un volume di 512 GB dell'archiviazione Performance per ogni nodo con un KPI delle prestazioni di 10 K IOPS.

Puoi utilizzare la procedura in [Provisioning and Managing {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) o [Provisioning and Managining {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) per ordinare la tua archiviazione Endurance e Performance.

## Configurazione di SAP HANA a più nodi
{: #configuring}

Il volume condiviso SAP HANA e ognuno dei volumi di log o di dati, deve essere accessibile da tutti i nodi. Questo approccio indica che tutti i volumi sono accessibili alla VLAN di archiviazione completa, che hai configurato in [Ordine del tuo sistema a più nodi](#ordering). Se non vuoi elencare tutti gli indirizzi IP coinvolti, rendi i volumi accessibili alla sottorete IP completa della VLAN.

Segui le istruzioni in [SAP HANA on NetApp FAS Systems with NFS](https://www.netapp.com/us/media/tr-4290.pdf) per configurare il tuo sistema SAP HANA a più nodi. Utilizza le seguenti opzioni di montaggio NFS (Network File System) per ogni volume da montare:

`rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576` in `/etc/fstab`.

Queste opzioni sono state verificate da NetApp e {{site.data.keyword.cloud_notm}}. Contatta il supporto di {{site.data.keyword.cloud_notm}} se pensi di modificare uno dei valori o delle opzioni di montaggio.

Dopo aver montato tutti i tuoi volumi su tutti i nodi, i tuoi server a più nodi sono configurati e pronti per l'installazione del database SAP HANA a più nodi. Segui le istruzioni in [SAP HANA Server Installation and Update Guide](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US) per installare un database SAP HANA della tua versione necessaria.
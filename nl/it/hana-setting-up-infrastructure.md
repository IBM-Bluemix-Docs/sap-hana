---



copyright:
  years: 2017, 2018
lastupdated: "2010-08-10"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. Configurazione della tua infrastruttura
{: #set_up_infrastructure}

Le indicazioni per configurare il {{site.data.keyword.baremetal_long}} SAP HANA, la rete, la protezione, e il sistema operativo (SO), si trovano nella seguente sezione. Contatta il [Supporto {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) per qualsiasi domanda.

## Ordine del tuo server
{: order-server}

Utilizza la seguente procedura per ordinare il tuo {{site.data.keyword.baremetal_short}}. È possibile trovare ulteriori informazioni in [Building a custom bare metal server](https://console.bluemix.net/docs/bare-metal/baremetal-provision.html#building-a-custom-bare-metal-server) utilizzando le tue credenziali univoche.

1. Accedi al [portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}}](https://control.softlayer.com) con le tue credenziali univoche.
2. Fai clic su **Account** > **Place an Order** nella pagina Account Summary.
3. Fai clic sul link **Monthly** in {{site.data.keyword.baremetal_short}} nella pagina Devices. Viene visualizzato l'elenco dei server; i server certificati SAP sono all'inizio dell'elenco. 
4. Fai clic sull'hyperlink in **STARTING PRICE PER MONTH** per selezionare il server appropriato e passare alla pagina Configure/Order. I server certificati SAP HANA sono identificati da **-H** nel modello di CPU.  
5. Immetti il numero di server che stai ordinando nel campo **Quantity** e seleziona il tuo **Data Center**.
6. **Server**, **RAM** e la tua opzione di archiviazione privata predefinita basata sulla tua selezione del server non possono essere modificati. {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} per {{site.data.keyword.cloud_notm}} o {{site.data.keyword.filestorage_full_notm}} e NAS (Network Attached Storage) vengono ordinati dopo che hai ordinato il server.
7. Seleziona il tuo **Operating System** tra Red Hat o SUSE e il sistema operativo specifico o l'hypervisor VMware per il tuo server. **Nota**: se stai utilizzando BYOL (Bring Your Own License) per il tuo sistema operativo, seleziona **Other** > **No Operating System**. Per ulteriori informazioni, consulta [BYOL (Bring your own license)](#byol).

## Selezione delle tue opzioni del server
{: #select_options}

Nel passo successivo, selezionerai il tipo e il numero di dischi che vuoi aggiungere alla tua configurazione. Puoi inoltre selezionare opzioni differenti per i gruppi di archiviazione RAID (Redundant Array of Independent Disks) e per i layout di partizionamento con i gruppi di archiviazione RAID. Per ulteriori informazioni, consulta [About RAID](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid) o [{{site.data.keyword.cloud_notm}} Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support).

1. In **SAP Certified Servers**, effettua la tua selezione in base a come pianifichi di utilizzare il tuo server. Per ulteriori informazioni, consulta [Design Decision Tool](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool) (scorri in basso nello strumento) o [{{site.data.keyword.cloud_notm}} Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) 
2. Fai clic su **Add to order** in fondo alla pagina.

## Configurazione delle impostazioni di sistema avanzate
{: #adv_config}

1. Segui le linee guida [Advanced System Configuration](https://console.bluemix.net/docs/bare-metal/baremetal-provision.html#advanced-server-configuration-options) per una guida sui valori nella finestra **Advanced System Configuration**.

I nomi host SAP devono essere formati da un massimo di 13 caratteri alfanumerici. Per ulteriori informazioni sul nome host SAP, consulta [SAP Notes 611361](https://launchpad.support.sap.com/#/611361) e [129997](https://launchpad.support.sap.com/#/129997). 

## Conferma delle tue selezioni
{: #confirm_selections}

1. Conferma le tue selezioni nella pagina Checkout e fai clic su **Cloud Service terms** e **3rd Party Software Agreement**.
2. Scorri in basso fino a Create Account: Enter Billing e immetti **Payment Type, Name, Card** e **Expiration** (data) per la carta di credito da utilizzare per la fatturazione.
3. Fai clic su **Submit Order**. Vieni reindirizzato a una schermata con il tuo numero d'ordine. Puoi stampare la schermata perché è la ricevuta del tuo ordine.

Viene inviata un'email di conferma con l'oggetto _{{site.data.keyword.cloud_notm}} Order ## has been approved_ all'indirizzo email nel tuo profilo. Questa email è l'avviso che il tuo server è stato approvato ed è in fase di distribuzione. Dopo che è stato distribuito, viene inviato un altro avviso che ti avverte che il server è disponibile e può essere gestito tramite il [portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}}](https://control.softlayer.com).

## BYOL (Bring your own license)
{: #byol}

Quando hai la tua licenza del sistema operativo, installala sul tuo {site.data.keyword.baremetal_short} in base alle istruzioni del fornitore. Per ulteriori informazioni, consulta [Opzione di nessun sistema operativo (No OS)](https://console.bluemix.net/docs/bare-metal/introduction-no-os.html#how-to-install-an-operating-system-on-a-no-os-server-).

## Passi successivi

Sei ora pronto per iniziare a gestire il tuo {{site.data.keyword.baremetal_short}}. Consulta [Gestione del tuo ambiente SAP HANA](/docs/infrastructure/sap-hana/hana-manage-environment.html).


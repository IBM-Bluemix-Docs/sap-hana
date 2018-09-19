---



copyright:
  years: 2017, 2018
lastupdated: "2018-06-28"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Panoramica di SAP HANA on IBM Cloud IaaS
{: #iaas-overview}

Un ambiente Infrastructure-as-a-server (IaaS) è formato da molti componenti: data center, calcolo, connettività, archiviazione e rete. 

## Data center

Con i data center in Nord e Sud America, Europa, Asia e Australia, puoi fornire risorse cloud dove (e quando) ti servono. Ogni data center è collegato alla rete privata globale di {{site.data.keyword.cloud_notm}}, rendendo i trasferimenti dei dati più veloci e efficienti ovunque nel mondo.

Per maggiori informazioni, consulta [Data Center](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

## Server bare metal

{{site.data.keyword.baremetal_long}} sono server fisici con funzionalità di personalizzazione limitate. I server sono dedicati al tuo utilizzo o dei tuoi clienti e non sono condivisi, neanche in parte, incluse le risorse del server, con altri clienti {{site.data.keyword.cloud_notm}} e sono forniti come un server fisico completo in esecuzione su un sistema operativo (SO) di tua scelta. I sistemi operativi per l'offerta SAP HANA sono Red Hat Enterprise Linux 7.4 per SAP HANA, SUSE Linux Enterprise Server 12 SP2 per SAP HANA e VMware Server Virtualization 6.5.

Poiché la personalizzazione è limitata sui server bare metal, sono ottenibili tempi di provisioning più veloci di 1 - 4 ore. Il provisioning rapido è utile quando stai tentando di ottenere un'applicazione dal mercato prima della concorrenza.

Ti viene offerto un array di combinazioni di RAM e CPU poiché i server certificati SAP hanno molte RAM e CPU preconfigurate. La combinazione *non può* essere modificata durante il processo d'ordine o tramite un ticket di supporto dopo la distribuzione dei server.

Per ulteriori informazioni, consulta [About bare metal servers](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers). 

## Connettività di rete

La connettività VPN (Virtual private network) alla rete cloud virtuale {{site.data.keyword.cloud_notm}} viene concessa automaticamente quando viene configurato il tuo account {{site.data.keyword.cloud_notm}}. Per impostazione predefinita, il tuo server ha un indirizzo IP privato e pubblico. Se vuoi che il tuo server sia privato, puoi disattivare l'interfaccia pubblica dopo il provisioning del tuo server o ordinarlo come privato. 

Mentre i requisiti della rete per SAP HANA (rete ridondante da 10 Gb) sono soddisfatti dall'offerta {{site.data.keyword.cloud_notm}}, potresti voler soddisfare la latenza e la velocità effettiva dei KPI (key performance indicator), a seconda del tuo scenario di applicazione. Per ulteriori informazioni sulla determinazione in quale data center posizionare il tuo server SAP HANA e sulla decisione della soluzione di connettività di rete migliore, consulta le considerazioni sulla [Connettività di rete](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity).

Per ulteriori informazioni, vedi [Getting started with Virtual Private Networking](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-) e la carta bianca [*SAP HANA Network Requirements*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html).

## Archiviazione
{: #storage}

L'archiviazione locale viene fornita con il tuo {{site.data.keyword.baremetal_short}} e utilizza la LAN virtuale di rete privata (VLAN) {{site.data.keyword.cloud_notm}} per fornire la sicurezza a livello aziendale mentre non blocca l'accesso dell'amministratore. Per i server certificati SAP HANA, è progettata e configurata per soddisfare i KPI definiti da SAP per la velocità effettiva e la latenza in conformità ai criteri di certificazione SAP HANA. L'archiviazione locale ha la dimensione rilevante di diversi file system secondari come definito dalla SAP HANA Installation Guide (`data.log` e `shared`). Nessun ulteriore adattamento deve essere fatto dall'utente.

Esistono due tipi di archiviazione per {{site.data.keyword.cloud_notm}}-blocchi e file-tra cui scegliere per eseguire i backup e i ripristini di SAP HANA. Entrambi i tipi utilizzano le operazioni di input/output al secondo (IOPS), che sono utilizzate per determinare i bisogni di archiviazione. Gli IOPS sono misurati in base alla dimensione blocco di 16 KB con un mix 50/50 di lettura/scrittra. Per raggiungere il numero massimo di IOPS su un volume, devono essere utilizzate adeguate risorse di rete. Altre considerazioni includono l'utilizzo della rete privata all'esterno dell'archiviazione lato host e le messe a punto specifiche dell'applicazione (ad esempio, gli stack IP e le profondità della coda). Per ulteriori informazioni, vedi [Getting started with Block Storage](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) e [Getting started with File Storage](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage).

{{site.data.keyword.cloud_notm}} offre inoltre NAS (Network Attached Storage) se stai cercando una soluzione di backup veloce, efficiente in termini di costo per i tuoi dispositivi. NAS può essere montato tramite NFS (Network File System) e utilizzato con FTP (File Transfer Protocol) con Parallels Plesk Panel e cPanel@WHM.

L'archiviazione NAS può essere utilizzata per qualsiasi motivo, ma, in questo caso, *non* deve essere utilizzata per i file di log o i dati SAP HANA. L'archiviazione non soddisfa i criteri relativi ai KPI I/O. Tuttavia, l'archiviazione può essere utilizzata per il backup dei dispositivi e di tutti gli altri tipi di dati. Può essere utilizzata da SAP HANA come backup dei dispositivi, per i dati e i file di log, quando montata tramite NFS.  
  
L'archiviazione NAS e FTP viene fatturata mensilmente ed è disponibile in molte dimensioni di archiviazione. Puoi principalmente interagire con la tua archiviazione NAS e FTP nella riga di comando o nel terminale con il SO o tramite le interazioni punta e fai clic nei pannelli nel portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}}. Nel portale del cliente, possono essere utilizzati i dettagli e l'utilizzo di NAS, ma il servizio non può essere manipolato al di fuori della riga di comando, il kernel o il pannello di controllo.

Per ulteriori informazioni su NAS in un ambiente {{site.data.keyword.cloud_notm}}, consulta [Getting started with NAS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas).

## Distribuzione e gestione

{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} sono distribuiti tramite l'API o il portale del cliente dell'infrastruttura {{site.data.keyword.cloud_notm}} dopo che hai creato il tuo account cliente {{site.data.keyword.cloud_notm}}. I server possono essere gestiti tramite il portale del cliente, l'API o l'interfaccia della riga di comando (CLI). Per ulteriori informazioni, consulta [About bare metal servers](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers).

## Supporto

[Il supporto clienti {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/support/index.html#getting-customer-support) gestisce tutte le domande e i problemi di supporto che si verificano tramite varie fonti, incluso il supporto basato sul ticket, chat e telefono. Il supporto clienti offerto è gratuito per tutti i clienti {{site.data.keyword.cloud_notm}} e copre la maggior parte dei ticket inseriti ogni giorno. Per ulteriori informazioni, vedi [Getting Customer Support](https://console.bluemix.net./docs/support/index.html#getting-customer-support).

Puoi anche continuare a creare i ticket tramite il supporto SAP correlato ai tuoi prodotti {{site.data.keyword.cloud_notm}} IaaS e SAP. Per ulteriori informazioni, vedi [SAP Support](https://support.sap.com/en/index.html) e [SAP Note 2414820](https://launchpad.support.sap.com/#/notes/2414820).

## Installazione di SAP HANA

Il tuo software SAP HANA deve essere installato da un programma di installazione SAP HANA certificato che ha completato il corso di certificazione di installazione SAP HANA. Per ulteriori informazioni, vedi [Who Can Install SAP HANA?](http://www.saphanacentral.com/p/who-can-install-sap-hana.html).

---



copyright:
  years: 2017, 2018
lastupdated: "2010-03-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. Infrastruktur einrichten
{: #set_up_infrastructure}

Anweisungen zur Konfiguration von {{site.data.keyword.baremetal_long}}n, Netz, Sicherheit, Speicher und Betriebssystem für SAP HANA finden sich im folgenden Abschnitt. Bei Fragen wenden Sie sich an den [{{site.data.keyword.cloud_notm}}-Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support).

## Server bestellen
{: order-server}

Gehen Sie anhand der folgenden Schritte vor, um Ihre {{site.data.keyword.baremetal_short}} zu bestellen. Weitere Informationen finden Sie unter [Bare-Metal-Server konfigurieren](https://console.bluemix.net/docs/bare-metal/configuring.html#configuring-your-bare-metal-server) mit eindeutigen Berechtigungsnachweisen.

1. Melden Sie sich mit Ihren eindeutigen Berechtigungsnachweisen beim [Kundenportal für die {{site.data.keyword.cloud_notm}}-Infrastruktur](https://control.softlayer.com) an.
2. Klicken Sie auf der Seite "Konto - Zusammenfassung" auf das Symbol **Geräte**.
3. Klicken Sie auf der Seite "Geräte" unter {{site.data.keyword.baremetal_short}} auf den Link **Monatlich**. Das Dialogfeld "Serverliste" wird angezeigt.
4. Die SAP-zertifizierten Server sind oben in der Liste angeführt. Klicken Sie auf den Hyperlink unter **AUSGANGSPREIS - MONATLICH**, um den richtigen Server auszuwählen und zur Seite für Konfiguration und Bestellung weitergeleitet zu werden. SAP HANA-zertifizierte Server sind mit einem **-H** unter dem CPU-Modell gekennzeichnet.  
5. Geben Sie im Feld **Qualität** die Anzahl zu bestellender Server ein und wählen Sie Ihr **Rechenzentrum** aus.
6. Die Standardwerte für **Server**, **RAM**, **Betriebssystem** und Ihre Option für privaten Speicher basieren auf Ihrer Serverauswahl und können nicht geändert werden. Die Speicherdimensionierung entspricht den Größen, die für SAP HANA mit einer bestimmten RAM-Größe erforderlich sind. {{site.data.keyword.IBM_notm}}-{{site.data.keyword.blockstorageshort}} für {{site.data.keyword.cloud_notm}} oder {{site.data.keyword.filestorage_full_notm}} und Network Attached Storage (NAS) werden nach der Bestellung Ihres Servers bestellt.
7. Wählen Sie Ihr **Betriebssystem** aus, entweder Red Hat oder Microsoft, und wählen Sie das spezifische Betriebssystem oder den VMware-Hypervisor für Ihren Server aus.

## Serveroptionen auswählen
{: #select_options}

Im nächsten Schritt wählen Sie den Typ und die Anzahl der Platten aus, die zu Ihrer Konfiguration hinzugefügt werden sollen. Außerdem wählen Sie verschiedene Optionen für RAID-Speichergruppen (Redundant Array of Independent Disks) und Partitionslayouts über den RAID-Speichergruppen aus. Weitere Informationen finden Sie unter [Informationen zu RAID](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid} or [{{site.data.keyword.cloud_notm}} Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support).

1. Treffen Sie unter **SAP-zertifizierte Server** Ihre Auswahl auf Grundlage des geplanten Verwendungszwecks für Ihren Server. Details zu den Optionen finden Sie unter [Bare-Metal-Server einrichten](https://console.bluemix.net/docs/bare-metal/configuring.html#setting-up-your-bare-metal-servers). Sie können auch das [Tool für die Designentscheidung](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool) (bis zum Tool hinunterblättern) oder den [{{site.data.keyword.cloud_notm}}-Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) zu Rate ziehen.
2. Klicken Sie unten auf der Seite auf **Zur Bestellung hinzufügen**.

## Erweiterte Systemkonfigurationen einrichten
{: #adv_config}

1. Folgen Sie den Anleitungen für die [erweiterte Systemkonfiguration](https://console.bluemix.net/docs/bare-metal/configuring.html#advanced-system-configuration) als Hilfestellung mit den Werten im Fenster **Erweiterte Systemkonfiguration**.

Die SAP-Hostnamen dürfen maximal 13 alphanumerische Zeichen enthalten. Weitere Informationen zu SAP-Hostnamen finden Sie in den [SAP-Hinweisen 611361](https://launchpad.support.sap.com/#/611361) und [129997](https://launchpad.support.sap.com/#/129997). 

## Auswahl bestätigen
{: #confirm_selections}

1. Bestätigen Sie Ihre Auswahl auf der Kassenseite und klicken Sie auf **Cloud-Servicebedingungen** und **Vereinbarung für Software anderer Anbieter**.
2. Blättern Sie hinunter zu "Konto erstellen": Geben Sie die Abrechnung sowie **Zahlungsart, Name, Karte** und **Ablauf** (Datum) für die Kreditkarte ein, die zur Zahlung verwendet werden soll.
3. Klicken Sie auf **Bestellung abschicken**. Sie werden zu einem Bildschirm mit Ihrer Bestellnummer weitergeleitet. Da dies auch Ihre Bestellbestätigung ist, können Sie den Bildschirm ausdrucken.

Eine Bestätigungs-E-Mail mit dem Betreff _Ihre {{site.data.keyword.cloud_notm}}-Bestellung Nr. ## wurde genehmigt_ wird an die in Ihrem Profil angegebene E-Mail-Adresse versendet. Diese E-Mail dient als Benachrichtigung, dass Ihr Server genehmigt wurde und gerade bereitgestellt wird. Nach seiner Bereitstellung wird eine weitere Benachrichtigung versendet, dass Ihr Server verfügbar ist und über das [Kundenportal der {{site.data.keyword.cloud_notm}}-Infrastruktur](https://control.softlayer.com) verwaltet werden kann.

## Nächste Schritte

Sie sind jetzt bereit, mit der Verwaltung Ihrer {{site.data.keyword.baremetal_short}} zu beginnen. Siehe [SAP HANA-Umgebung verwalten](/docs/infrastructure/sap-hana/hana-manage-environment.html).


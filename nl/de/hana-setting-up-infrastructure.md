---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-28"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, infrastructure, {{site.data.keyword.baremetal_short}}, SAP-certified infrastructure, deployment, BYOL,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 2. Infrastruktur einrichten
{: #set_up_infrastructure}

Anweisungen zur Konfiguration von {{site.data.keyword.baremetal_long}}n, Netz, Sicherheit, Speicher und Betriebssystem für SAP HANA finden sich im folgenden Abschnitt. Bei Fragen wenden Sie sich an den [{{site.data.keyword.cloud_notm}}-Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

## Server bestellen
{: order-server}

Gehen Sie anhand der folgenden Schritte vor, um Ihre {{site.data.keyword.baremetal_short}} zu bestellen. Weitere Informationen finden Sie unter [Angepassten Bare-Metal-Server erstellen](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server).

1. Melden Sie sich mit Ihren eindeutigen Berechtigungsnachweisen beim [Kundenportal für die {{site.data.keyword.cloud_notm}}-Infrastruktur ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com){: new_window} an.
2. Klicken Sie auf der Seite "Konto - Zusammenfassung" auf **Konto** > **Bestellung aufgeben**.
3. Klicken Sie auf der Seite "Geräte" unter {{site.data.keyword.baremetal_short}} auf den Link **Monatlich**. Auf der Liste der Server, die nun angezeigt wird, werden die SAP-zertifizierten ganz oben angeführt.
4. Klicken Sie auf den Hyperlink unter **AUSGANGSPREIS - MONATLICH**, um den richtigen Server auszuwählen und zur Seite für Konfiguration und Bestellung weitergeleitet zu werden. SAP HANA-zertifizierte Server sind mit einem **-H** unter dem CPU-Modell gekennzeichnet.  

Die Server "BI.S3.H2192" und "BI.S3.H238" sind auch für die **stündliche** Abrechnung verfügbar.
{: note}

5. Geben Sie im Feld **Menge** die Anzahl zu bestellender Server ein und wählen Sie Ihr **Rechenzentrum** aus.
6. Die Standardwerte für **Server** und **RAM** sowie Ihre Option für privaten Speicher basieren auf Ihrer Serverauswahl und können nicht geändert werden. {{site.data.keyword.IBM_notm}}-{{site.data.keyword.blockstorageshort}} für {{site.data.keyword.cloud_notm}} oder {{site.data.keyword.filestorage_full_notm}} und Network Attached Storage (NAS) werden nach der Bestellung Ihres Servers bestellt.
7. Wählen Sie Ihr **Betriebssystem** aus, entweder Red Hat oder SUSE, und wählen Sie das spezifische Betriebssystem oder aber den VMware-Hypervisor für Ihren Server aus.

Wenn Sie für Ihr Betriebssystem nach dem BYOL-Prinzip eine eigene Lizenz verwenden, wählen Sie die Optionen **Andere** > **Kein Betriebssystem** aus. Weitere Informationen finden Sie unter ["Bring your own license" - BYOL](#byol).
{ :note}

## Serveroptionen auswählen
{: #select_options}

Im nächsten Schritt wählen Sie den Typ und die Anzahl der Platten aus, die zu Ihrer Konfiguration hinzugefügt werden sollen. Außerdem wählen Sie verschiedene Optionen für RAID-Speichergruppen (Redundant Array of Independent Disks) und Partitionslayouts über den RAID-Speichergruppen aus. Weitere Informationen finden Sie unter [Informationen zu RAID](/docs/bare-metal?topic=bare-metal-about-raid#about-raid) oder [{{site.data.keyword.cloud_notm}}-Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

1. Treffen Sie unter **SAP-zertifizierte Server** Ihre Auswahl auf Grundlage des geplanten Verwendungszwecks für Ihren Server. Weitere Informationen finden Sie unter [Tool für Designentscheidungen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool){: new_window} (bis zum Tool hinunterblättern) oder [{{site.data.keyword.cloud_notm}}-Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).
2. Klicken Sie unten auf der Seite auf **Zur Bestellung hinzufügen**.

## Erweiterte Systemkonfigurationen einrichten
{: #adv_config}

1. Folgen Sie den Anleitungen für die [erweiterte Systemkonfiguration](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server) als Hilfestellung mit den Werten im Fenster **Erweiterte Systemkonfiguration**.

Die SAP-Hostnamen dürfen maximal 13 alphanumerische Zeichen enthalten. Weitere Informationen zu SAP-Hostnamen finden Sie in den [SAP-Hinweisen 611361 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/611361){: new_window} und [129997 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/129997){: new_window}.

## Auswahl bestätigen
{: #confirm_selections}

1. Bestätigen Sie Ihre Auswahl auf der Kassenseite und klicken Sie auf **Cloud-Servicebedingungen** und **Vereinbarung für Software anderer Anbieter**.
2. Blättern Sie hinunter zu "Konto erstellen": Geben Sie die Abrechnung sowie **Zahlungsart, Name, Karte** und **Ablauf** (Datum) für die Kreditkarte ein, die zur Zahlung verwendet werden soll.
3. Klicken Sie auf **Bestellung abschicken**. Sie werden zu einem Bildschirm mit Ihrer Bestellnummer weitergeleitet. Da dies auch Ihre Bestellbestätigung ist, können Sie den Bildschirm ausdrucken.

Eine Bestätigungs-E-Mail mit dem Betreff _Ihre {{site.data.keyword.cloud_notm}}-Bestellung Nr. ## wurde genehmigt_ wird an die in Ihrem Profil angegebene E-Mail-Adresse versendet. Diese E-Mail dient als Benachrichtigung, dass Ihr Server genehmigt wurde und gerade bereitgestellt wird. Nach seiner Bereitstellung wird eine weitere Benachrichtigung versendet, dass Ihr Server verfügbar ist und über das [Kundenportal der {{site.data.keyword.cloud_notm}}-Infrastruktur ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://control.softlayer.com){: new_window} verwaltet werden kann.

## "Bring your own license" - BYOL
{: #byol}

Wenn Sie über eine eigene Lizenz für Ihr Betriebssystem verfügen, installieren Sie sie unter Beachtung der Anweisungen des Anbieters auf Ihrer {{site.data.keyword.baremetal_short}}-Instanz. Weitere Informationen finden Sie unter [Die Option "Ohne Betriebssystem"](/docs/bare-metal?topic=bare-metal-how-to-install-an-operating-system-on-a-no-os-server-#bm-no-os).

## Nächste Schritte

Sie sind jetzt bereit, mit der Verwaltung Ihrer {{site.data.keyword.baremetal_short}} zu beginnen. Die nächsten Schritte finden Sie unter [SAP HANA-Umgebung verwalten](/docs/infrastructure/sap-hana?topic=sap-hana-manage_environment#manage_environment).

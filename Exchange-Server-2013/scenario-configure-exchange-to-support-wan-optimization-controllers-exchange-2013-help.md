---
title: 'Szenario: Konfigurieren von Exchange zur Unterstützung von WOC-Geräten (WAN Optimization Controller): Exchange 2013 Help'
TOCTitle: 'Szenario: Konfigurieren von Exchange zur Unterstützung von WOC-Geräten (WAN Optimization Controller)'
ms:assetid: 1f407698-0b71-45a3-867a-640ccf7351da
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633456(v=EXCHG.150)
ms:contentKeyID: 52062847
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Szenario: Konfigurieren von Exchange zur Unterstützung von WOC-Geräten (WAN Optimization Controller)

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-09-28_

Unter Microsoft Exchange Server 2013 ist die TLS-Verschlüsselung (Transport Layer Security) für die gesamte SMTP-Kommunikation im Transportdienst zwischen Postfachservern zwingend erforderlich. Dadurch wird die Gesamtsicherheit der Transportdienstkommunikation zwischen Postfachservern erhöht. In bestimmten Topologien, in denen WOC-Geräte (WAN Optimization Controller) eingesetzt werden, ist die TLS-Verschlüsselung des SMTP-Datenverkehrs jedoch möglicherweise nicht gewünscht. Sie können TLS für die Transportdienstkommunikation zwischen Postfachservern für diese spezifischen Szenarios deaktivieren.

Schauen Sie sich einmal die Topologie in der folgenden Abbildung an. Bei dieser aus vier Standorten bestehenden Topologie wird davon ausgegangen, dass die beiden Hauptbüros und Zweigstelle 2 über stabile Verbindungen verfügen, wohingegen die Verbindung zwischen Hauptbüro 1 und Zweigstelle 1 über eine WAN-Verbindung (Wide Area Network, Fernnetz) hergestellt wird. Das Unternehmen hat für diese Verbindung WOC-Geräte installiert, um den Datenverkehr über das WAN zu komprimieren und zu optimieren.

**Beispiel für eine Netzwerktopologie mit WOC-Geräten**

![Beispieltopologie mit WAN-Optimierungen](images/Ee633456.52876869-52f1-4c0f-85b2-7a850643e8a1(EXCHG.150).gif "Beispieltopologie mit WAN-Optimierungen")

In dieser Topologie kann der SMTP-Datenverkehr über die WAN-Verbindung nicht komprimiert werden, da Exchange 2013 für die Kommunikation zwischen Postfachservern die TLS-Verschlüsselung verwendet. Idealerweise sollte der SMTP-Datenverkehr über die WAN-Verbindung unverschlüsselt sein, die TLS-Sicherheit bei Standorten mit stabilen Verbindungen jedoch beibehalten werden. Unter Exchange 2013 können Sie die TLS-Verschlüsselung für den Datenverkehr zwischen Standorten deaktivieren, indem Sie Empfangsconnectors konfigurieren. Mit dieser Möglichkeit in Exchange 2013 können Sie eine Ausnahme für den SMTP-Datenverkehr zwischen Hauptbüro 1 und Zweigstelle 1 konfigurieren, wie in der folgenden Abbildung veranschaulicht.

**Bevorzugter logischer Meldungsfluss**

![Bevorzugter logischer Nachrichtenfluss](images/Ee633456.e0fe62fa-1bad-4d43-9eaf-205a9b8d07e1(EXCHG.150).gif "Bevorzugter logischer Nachrichtenfluss")

In der empfohlenen Konfiguration wird der nicht verschlüsselte SMTP-Datenverkehr nur auf die Nachrichten beschränkt, die über die WAN-Verbindung gesendet werden. Die gesamte standortinterne Transportdienstkommunikation zwischen Postfachservern an allen Standorten und die gesamte standortübergreifende Transportdienstkommunikation zwischen Postfachservern, an der die Zweigstelle 1 nicht beteiligt ist, sollte daher TLS-verschlüsselt werden.

Zu diesem Zweck müssen Sie die folgenden Schritte in der angegebenen Reihenfolge auf allen Postfachservern an den Standorten ausführen, an denen die WOC-Geräte (Hauptbüro 1 und Zweigstelle 1 in der bekannten Topologie) verwendet werden:

1.  Aktivieren Sie die heruntergestufte Exchange Server-Authentifizierung.

2.  Erstellen Sie einen dedizierten Empfangsconnector zur Verarbeitung des Datenverkehrs über die Verbindung, die WOC-Geräte aufweist.
    
    1.  Legen Sie die Eigenschaft für den IP-Remoteadressbereich des dedizierten Empfangsconnectors auf die IP-Adressbereiche der Postfachserver am Active Directory-Remotestandort fest.
    
    2.  Deaktivieren Sie TLS für den dedizierten Empfangsconnector.

Außerdem müssen Sie die folgenden Schritte ausführen, um sicherzustellen, dass der gesamte SMTP-Datenverkehr über die WAN-Verbindung von dem erstellten dedizierten Empfangsconnector verarbeitet wird:

  - Konfigurieren Sie die Active Directory-Standorte, die die nicht TLS-gesicherte Kommunikation verwenden, als Hubstandorte, um den gesamten Nachrichtenfluss über die dedizierten Empfangsconnectors zu erzwingen (Hauptbüro 1 und Zweigstelle 1 in der bekannten Topologie).

  - Überprüfen Sie, ob die Kosten für die Active Directory-IP-Standortverknüpfung auf eine Weise konfiguriert sind, mit der sichergestellt ist, dass der kostengünstigste Routingpfad zum Remotestandort (Zweigstelle 1 in der bekannten Topologie) über die Netzwerkverbindung mit den WOC-Geräten verläuft. Weisen Sie den Active Directory-Standortverknüpfungen nach Bedarf Exchange-spezifische Kosten zu.

Die folgenden Abschnitte enthalten einen Überblick über diese Schritte. Schrittanleitungen zur Konfiguration Ihrer Organisation für dieses Szenario finden Sie unter [Deaktivieren von TLS zwischen Active Directory-Standorten](disable-tls-between-active-directory-sites-exchange-2013-help.md).

**Inhalt**

Herunterstufen der Authentifizierung über TLS-deaktivierte Verbindungen

Erstellen und Konfigurieren dedizierter Empfangsconnectors

Konfigurieren von Hubstandorten

Konfigurieren von Exchange-spezifischen Kosten für Active Directory-Standortverknüpfungen

## Herunterstufen der Authentifizierung über TLS-deaktivierte Verbindungen

Mit der TLS-Verschlüsselung unter Exchange wird die Kerberos-Authentifizierung verwendet. Wenn Sie TLS für die Transportdienstkommunikation zwischen Postfachservern deaktivieren, müssen Sie eine andere Form der Authentifizierung ausführen. Wenn Exchange 2013 mit anderen Servern mit unter Exchange kommuniziert, die **X-ANONYMOUSTLS** nicht unterstützen, wird wieder die GSSAPI-Authentifizierung (Generic Security Services Application Programming Interface) verwendet. Für die gesamte Transportdienstkommunikation zwischen Exchange 2013-Postfachservern wird **X-ANONYMOUSTLS** verwendet. Wenn Sie den Transportdienst auf Ihrem Postfachserver für die Verwendung der heruntergestuften Exchange Server-Authentifizierung konfigurieren, aktivieren Sie eigentlich die GSSAPI-Authentifizierung für die Transportdienstkommunikation mit anderen Exchange 2013-Postfachservern.

Zurück zum Seitenanfang

## Erstellen und Konfigurieren dedizierter Empfangsconnectors

Sie müssen Empfangsconnectors erstellen, die nur für die Verarbeitung des nicht TLS-verschlüsselten Datenverkehrs zuständig sind. Durch die Verwendung separater Empfangsconnectors zu diesem Zweck wird sichergestellt, dass der gesamte Datenverkehr, der nicht über die WAN-Verbindung erfolgt, durch die TLS-Verschlüsselung gesichert bleibt.

Damit die dedizierten Empfangsconnectors nur auf den WAN-Datenverkehr beschränkt sind, müssen Sie die Eigenschaft für den IP-Remoteadressbereich konfigurieren. Exchange verwendet immer den Connector mit dem spezifischsten IP-Remoteadressbereich. Daher werden die neuen Connectors dem Standardempfangsconnector vorgezogen, der für den Empfang von Nachrichten von beliebigen Standorten konfiguriert ist.

Angenommen, in der bereits bekannten Topologie wird das Subnetz der Klasse C "10.0.1.0/24" für das Hauptbüro 1 und "10.0.2.0/24" für die Zweigstelle 1 verwendet. Sie müssen die folgenden Schritte ausführen, um die Deaktivierung von TLS für diese beiden Standorte vorzubereiten:

1.  Erstellen Sie auf jedem Postfachserver im Hauptbüro 1 und in der Zweigstelle 1 einen Empfangsconnector mit der Bezeichnung "WAN".

2.  Konfigurieren Sie den IP-Remoteadressbereich von 10.0.2.0/24 für jeden dedizierten Empfangsconnector im Hauptbüro 1.

3.  Konfigurieren Sie den IP-Remoteadressbereich von 10.0.1.0/24 für jeden dedizierten Empfangsconnector in der Zweigstelle 1.

4.  Deaktivieren Sie TLS für alle dedizierten Empfangsconnectors.

Das Ergebnis wird in der folgenden Abbildung veranschaulicht (mit der Eigenschaft für den IP-Remoteadressbereich der Empfangsconnectors namens WAN in Klammern). Aus Gründen der Übersichtlichkeit wird im Hauptbüro 1 nur ein einziger Postfachserver angezeigt, und Zweigstelle 2 wird weggelassen.

**Konfiguration des Empfangsconnectors**

![Konfiguration des Empfangsconnectors](images/Ee633456.1821b3db-1f7a-4ae7-afbc-5c99e117f976(EXCHG.150).gif "Konfiguration des Empfangsconnectors")

Zurück zum Seitenanfang

## Konfigurieren von Hubstandorten

Standardmäßig versucht ein Exchange 2013-Postfachserver, eine direkte Verbindung mit dem Postfachserver herzustellen, der dem Endziel einer bestimmten Nachricht am nächsten ist. Wenn in der bekannten Topologie ein Benutzer in Zweigstelle 2 eine Nachricht an einen Benutzer in Zweigstelle 1 sendet, stellt der Postfachserver in Zweigstelle 2 eine direkte Verbindung mit dem Postfachserver in Zweigstelle 1 her, um diese Nachricht zu übermitteln. Da diese Verbindung verschlüsselt wird, ist sie in dieser Topologie nicht von Vorteil. Damit solche Nachrichten über die Postfachserver im Hauptbüro 1 übermittelt werden und somit sichergestellt wird, dass sie während der Übertragung über die WAN-Verbindung nicht verschlüsselt werden, müssen Hauptbüro 1 und Zweigstelle 1 als Hubstandorte konfiguriert werden. Kurzum: Jeder Standort, der einen Postfachserver mit einem Empfangsconnector aufweist, bei dem TLS deaktiviert ist, muss als Hubstandort konfiguriert werden. Auf diese Weise können Sie erzwingen, dass Server an anderen Standorten den Datenverkehr über diesen Standort weiterleiten. Weitere Informationen finden Sie unter [Konfigurieren der Exchange-Einstellungen für E-Mail-Routing in Active Directory](configure-exchange-mail-routing-settings-in-active-directory-exchange-2013-help.md).

Zurück zum Seitenanfang

## Konfigurieren von Exchange-spezifischen Kosten für Active Directory-Standortverknüpfungen

Das Konfigurieren von Hubstandorten allein reicht nicht aus, um sicherzustellen, dass der gesamte Datenverkehr unverschlüsselt über die WAN-Verbindung gesendet wird. Der Grund hierfür liegt darin, dass Exchange Nachrichten nur über Hubstandorte weiterleitet, wenn sich der Hubstandort im kostengünstigsten Routingpfad befindet. Angenommen, die Kosten für die IP-Standortverknüpfung für die Beispieltopologie sind in Active Directory so konfiguriert, wie in der folgenden Abbildung dargestellt (aus Gründen der Übersichtlichkeit wird Hauptbüro 2 weggelassen).

**IP-Standortverknüpfungskosten für die Beispieltopologie**

![IP-Standortverknüpfung – Kosten für Beispieltopologie](images/Ee633456.099deb15-795a-417a-b6aa-925b3bedf8b4(EXCHG.150).gif "IP-Standortverknüpfung – Kosten für Beispieltopologie")

In diesem Fall weist der Pfad von Zweigstelle 2 zu Zweigstelle 1, der durch den Hubstandort verläuft, Gesamtkosten in Höhe von 12 (6+6) auf, die Kosten für den direkten Pfad hingegen belaufen sich auf 10. Dies ist der Grund dafür, dass keine Nachricht von Zweigstelle 2 an Zweigstelle 1 über das Hauptbüro 1 gesendet und der gesamte Datenverkehr nach wie vor TLS-verschlüsselt wird.

Zur Vermeidung dieses Problems müssen Sie Exchange-spezifische Kosten angeben, die für die IP-Standortverknüpfung zwischen Zweigstelle 2 und Zweigstelle 1 höher als 12 sind, wie in der folgenden Abbildung veranschaulicht. So wird sichergestellt, dass alle Nachrichten über den unverschlüsselten Kanal zwischen Hauptbüro 1 und Zweigstelle 1 gesendet werden.

**Mit Exchange-spezifischen IP-Standortverknüpfungskosten konfigurierte Beispieltopologie**

![Beispieltopologie mit Exchange-Kosten](images/Ee633456.cd036fe0-c37d-479e-a4c1-235e17e90ca7(EXCHG.150).gif "Beispieltopologie mit Exchange-Kosten")

Weitere Informationen finden Sie unter [Konfigurieren der Exchange-Einstellungen für E-Mail-Routing in Active Directory](configure-exchange-mail-routing-settings-in-active-directory-exchange-2013-help.md).

Zurück zum Seitenanfang


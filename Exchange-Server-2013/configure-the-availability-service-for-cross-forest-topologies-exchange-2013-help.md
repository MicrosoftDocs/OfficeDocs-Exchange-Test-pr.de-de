---
title: 'Konfig. d. Verfügbarkeitsdiensts für gesamtstrukturübergreifende Topologien'
TOCTitle: Konfigurieren des Verfügbarkeitsdiensts für gesamtstrukturübergreifende Topologien
ms:assetid: f1e7d407-f0d3-47a7-8cc3-03c5980445d5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125182(v=EXCHG.150)
ms:contentKeyID: 52062925
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren des Verfügbarkeitsdiensts für gesamtstrukturübergreifende Topologien

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-10-22_

Der Verfügbarkeitsdienst verbessert die Frei/Gebucht-Informationen für Information-Worker, indem Clients mit Microsoft Outlook sichere, konsistente und aktuelle Frei/Gebucht-Informationen zur Verfügung gestellt werden. Dieser Dienst wird standardmäßig zusammen mit Exchange Server 2013 installiert. In gesamtstrukturübergreifenden Topologien, in denen auf allen verbundenen Clients Outlook ausgeführt wird, stellt der Verfügbarkeitsdienst die einzige Methode zum Abrufen von Frei/Gebucht-Informationen dar. Der Verfügbarkeitsdienst für gesamtstrukturübergreifende Topologien kann mithilfe der Shell konfiguriert werden.


> [!NOTE]
> Die Exchange-Verwaltungskonsole eignet sich nicht zum Konfigurieren des Verfügbarkeitsdiensts für gesamtstrukturübergreifende Topologien.



## Verwenden des Verfügbarkeitsdiensts in vertrauenswürdigen und nicht vertrauenswürdigen Gesamtstrukturen

Der Verfügbarkeitsdienst kann in gesamtstrukturübergreifenden Topologien sowohl über vertrauenswürdige als auch über nicht vertrauenswürdige Gesamtstrukturen hinweg verwendet werden. Die Art der verfügbaren Frei/Gebucht-Informationen richtet sich danach, ob Sie eine vertrauenswürdige oder eine nicht vertrauenswürdige Gesamtstruktur verwenden.

**Vertrauenswürdige Gesamtstrukturen**   In vertrauenswürdigen Gesamtstrukturen können Sie den Verfügbarkeitsdienst so konfigurieren, dass Frei/Gebucht-Informationen auf Benutzerbasis abgerufen werden. Ist der Verfügbarkeitsdienst für das Abrufen von Frei/Gebucht-Informationen auf Benutzerbasis konfiguriert, kann er gesamtstrukturübergreifende Anforderungen im Auftrag eines bestimmten Benutzers stellen. Ein Benutzer in einer Remotegesamtstruktur kann somit detaillierte Frei/Gebucht-Informationen für jemanden abrufen, der nicht in derselben Gesamtstruktur enthalten ist.

**Nicht vertrauenswürdige Gesamtstrukturen**   In nicht vertrauenswürdigen Gesamtstrukturen können Sie den Verfügbarkeitsdienst nur so konfigurieren, dass Frei/Gebucht-Informationen auf organisationsweiter Basis abgerufen werden. Stellt der Verfügbarkeitsdienst gesamtstrukturübergreifende Frei/Gebucht-Anforderungen auf Organisationsebene, werden Frei/Gebucht-Informationen für jeden Benutzer innerhalb der Organisation zurückgegeben. In nicht vertrauenswürdigen Gesamtstrukturen kann die Ebene der auf Benutzerbasis zurückgegebenen Frei/Gebucht-Informationen nicht gesteuert werden.

## Konfigurieren von Windows für gesamtstrukturübergreifende Topologien

In der Standardeinstellung beinhaltet eine GAL die E-Mail-Empfänger einer einzelnen Gesamtstruktur. Wenn Sie über eine gesamtstrukturübergreifende Umgebung verfügen, wird die Verwendung von Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1) empfohlen, um sicherzustellen, dass jede Gesamtstruktur über E-Mail-Empfänger aus anderen Gesamtstrukturen verfügt. ILM 2007 FP1 erstellt E-Mail-Benutzer, die Empfängern aus anderen Gesamtstrukturen entsprechen. Dadurch können die Benutzer diese Kontakte in der GAL anzeigen und Nachrichten an diese senden. Beispielsweise werden Benutzer der Gesamtstruktur A in der Gesamtstruktur B als E-Mail-Benutzer angegeben und umgekehrt. Benutzer der Zielgesamtstruktur können zum Senden einer Nachricht das E-Mail-Benutzerobjekt auswählen, das einen Empfänger einer anderen Gesamtstruktur darstellt.

Erstellen Sie zum Aktivieren der GAL-Synchronisierung Verwaltungs-Agents, die E-Mail-aktivierte Benutzer, Kontakte und Gruppen aus den angegebenen Active Directory-Diensten in ein zentrales Metaverzeichnis importieren. Im Metaverzeichnis werden die E-Mail-aktivierten Objekte als E-Mail-Benutzer dargestellt. Gruppen werden als Kontakte ohne zugeordnete Mitgliedschaft dargestellt. Anschließend exportieren die Verwaltungs-Agents diese E-Mail-Benutzer in eine Organisationseinheit in der angegebenen Zielgesamtstruktur.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für den Verfügbarkeitsdienst" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von Frei/Gebucht-Informationen auf Benutzerebene in einer vertrauenswürdigen gesamtstrukturübergreifenden Topologie mithilfe der Shell

In diesem Beispiel wird der Verfügbarkeitsdienst für das Abrufen von Frei/Gebucht-Informationen auf Benutzerbasis auf einem Postfachserver in der Zielgesamtstruktur konfiguriert.

    Get-MailboxServer | Add-ADPermission -Accessrights Extendedright -Extendedrights "ms-Exch-
    EPI-Token-Serialization" -User "<Remote Forest Domain>\Exchange servers"

In diesem Beispiel wird die Frei/Gebucht-Zugriffsmethode definiert, die der Verfügbarkeitsdienst auf dem lokalen Postfachserver in der Quellgesamtstruktur verwendet. Der lokale Postfachserver ist für den Zugriff auf Frei/Gebucht-Informationen auf Benutzerbasis von der Gesamtstruktur "ContosoForest.com" aus konfiguriert. In diesem Beispiel wird das Dienstkonto für das Abrufen von Frei/Gebucht-Informationen verwendet.

    Add-AvailabilityAddressSpace -Forestname ContosoForest.com -AccessMethod PerUserFB -UseServiceAccount:$true


> [!NOTE]
> Um bidirektionale, gesamtstrukturübergreifende Verfügbarkeit zu konfigurieren, wiederholen Sie diese Schritte in der Zielgesamtstruktur.



Wenn Sie gesamtstrukturübergreifende Verfügbarkeit mit Vertrauensstellung konfigurieren und außerdem ein Dienstkonto verwenden möchten (statt Anmeldeinformationen auf Organisations- oder Benutzerbasis anzugeben), müssen Sie die Berechtigungen wie in dem im Abschnitt "Konfigurieren von vertrauenswürdiger gesamtstrukturübergreifender Verfügbarkeit mit einem Dienstkonto" dargestellten Beispiel erweitern. Durch die Durchführung dieses Verfahrens in der Zielgesamtstruktur wird Postfachservern in der Quellgesamtstruktur die Berechtigung zum Serialisieren des ursprünglichen Benutzerkontexts erteilt.

## Konfigurieren von vertrauenswürdiger gesamtstrukturübergreifender Verfügbarkeit mit einem Dienstkonto

In diesem Beispiel wird die vertrauenswürdige gesamtstrukturübergreifende Verfügbarkeit mit einem Dienstkonto konfiguriert.

    Get-MailboxServer | Add-ADPermission -Accessrights Extendedright -Extendedright "ms-Exch-EPI-Token-Serialization" -User "<Remote Forest Domain>\Exchange servers"

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-MailboxServer](https://technet.microsoft.com/de-de/library/bb123539\(v=exchg.150\))

  - [Add-ADPermission](https://technet.microsoft.com/de-de/library/bb124403\(v=exchg.150\))

  - [Add-AvailabilityAddressSpace](https://technet.microsoft.com/de-de/library/bb124122\(v=exchg.150\))

  - [Set-AvailabilityConfig](https://technet.microsoft.com/de-de/library/bb124103\(v=exchg.150\))

## Konfigurieren von Frei/Gebucht-Informationen auf Organisationsebene in einer nicht vertrauenswürdigen gesamtstrukturübergreifenden Topologie mithilfe der Shell

In diesem Beispiel wird das organisationsweite Konto des Verfügbarkeitskonfigurationsobjekts für das Konfigurieren der Zugriffsebene für Frei/Gebucht-Informationen in der Zielgesamtstruktur eingestellt.

    Set-AvailabilityConfig -OrgWideAccount "Contoso.com\User"

In diesem Beispiel wird das Verfügbarkeitsadressraum-Konfigurationsobjekt für die Quellgesamtstruktur hinzugefügt.

    $a = Get-Credential (Enter the credentials for organization-wide user in Contoso.com domain)
    Add-AvailabilityAddressspace -Forestname Contoso.com -Accessmethod OrgWideFB -Credential:$a


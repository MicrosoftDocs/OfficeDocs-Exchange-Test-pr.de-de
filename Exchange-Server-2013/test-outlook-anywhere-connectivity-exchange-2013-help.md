---
title: 'Testen der Outlook Anywhere-Konnektivität: Exchange 2013 Help'
TOCTitle: Testen der Outlook Anywhere-Konnektivität
ms:assetid: 0dc5b68f-2316-446a-84c9-5f1c50dc3776
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633453(v=EXCHG.150)
ms:contentKeyID: 50554811
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Testen der Outlook Anywhere-Konnektivität

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Sie können mit der Shell oder der Exchange-Remoteverbindungsuntersuchung (Exchange Remote Connectivity Analyzer, ExRCA) die komplette Outlook Anywhere-Konnektivität von Clients testen. Dies umfasst das Testen der Konnektivität über den AutoErmittlungsdienst, das Erstellen eines Benutzerprofils und das Anmelden am Postfach des Benutzers. Alle erforderlichen Werte werden vom AutoErmittlungsdienst abgerufen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Outlook Anywhere finden Sie unter [Outlook Anywhere](outlook-anywhere-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Outlook Anywhere" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Shell zum Testen der Outlook Anywhere-Konnektivität

Verwenden Sie das Cmdlet **Test-OutlookConnectivity**, wenn Sie mit der Shell die Outlook Anywhere-Konnektivität testen möchten.

Führen Sie den folgenden Befehl aus.

    Test-OutlookConnectivity -ProbeIdentity 'OutlookMailboxDeepTestProbe' -MailboxId tony@contoso.com -Hostname contoso.com


> [!NOTE]
> Der Parameterwert <EM>OutlookMailboxDeepTestProbe</EM> testet die Konnektivität des Postfachservers. Verwenden Sie <EM>OutlookMailboxCTPProbe</EM> für den Parameterwert <EM>ProbeIdentity</EM>, um die Konnektivität des Clientzugriffsservers zu testen.



## Verwenden der Exchange-Remoteverbindungsuntersuchung zum Testen der Outlook Anywhere-Konnektivität

Die Exchange-Remoteverbindungsuntersuchung (Exchange Remote Connectivity Analyzer, ExRCA) ist ein webbasiertes Tool, das zum Testen der Konnektivität mit einer Vielzahl von Exchange-Protokollen vorgesehen ist. Sie können [hier](https://go.microsoft.com/fwlink/p/?linkid=167905) auf ExRCA zugreifen.

1.  Wählen Sie auf der ExRCA-Website unter **Verbindungstests für Microsoft Office Outlook** die Option **Outlook Anywhere** aus, und wählen Sie dann unten auf der Seite "Weiter" aus.

2.  Geben Sie auf dem nächsten Bildschirm die erforderlichen Informationen ein, einschließlich E-Mail-Adresse, Domäne, Benutzername und Kennwort.

3.  Legen Sie fest, ob die Servereinstellungen mit der AutoErmittlung ermittelt werden sollen oder ob Sie sie manuell angeben möchten.

4.  Akzeptieren Sie den Haftungsausschluss, geben Sie den Überprüfungscode ein, und wählen Sie dann **Verifizieren** aus.

5.  Wählen Sie **Test durchführen** aus.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn die ExRCA-Tests abgeschlossen sind, wird die Ausgabe auf der Webseite angezeigt. Alle Fehler werden aufgelistet.


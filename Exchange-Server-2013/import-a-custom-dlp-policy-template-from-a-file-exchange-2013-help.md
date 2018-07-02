---
title: 'Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei: Exchange 2013 Help'
TOCTitle: Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei
ms:assetid: 83f49dbd-f9b1-498e-b548-1529c5e1ccdb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150531(v=EXCHG.150)
ms:contentKeyID: 50474803
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-08-09_

Sie können vertrauliche Daten mithilfe von DLP-Richtlinien verwalten, indem Sie eine Datei mit Einstellungen für die Richtlinieninformationen importieren. Richtlinien können unabhängig von Exchange als XML-Dateien entwickelt werden. Sie müssen jedoch bestimmte Formatanforderungen erfüllen, damit sie ordnungsgemäß funktionieren. Alternativ dazu können Sie auch Richtlinien in Microsoft Exchange Server 2013 importieren, die aus einer früheren Exchange-Version exportiert wurden.


> [!WARNING]
> Sie sollten Ihre DLP-Richtlinien im Testmodus aktivieren, bevor Sie sie in der Produktionsumgebung ausführen. Während dieser Tests wird empfohlen, dass Sie Beispielbenutzerpostfächer konfigurieren und Testnachrichten senden, die Ihre Testrichtlinien aufrufen, um die Ergebnisse zu bestätigen.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verhinderung von Datenverlust (Data Loss Prevention, DLP)" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei

Gehen Sie folgendermaßen vor, um eine benutzerdefinierte DLP-Richtlinienvorlage aus einer Datei zu importieren. Weisen Sie nach Möglichkeit jedem Teil der Richtlinie oder Regel einen eindeutigen Namen zu.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Klicken Sie auf den Pfeil neben dem Symbol **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und klicken Sie dann auf **Richtlinie importieren**.

3.  Füllen Sie auf der Seite **Richtlinie importieren** die folgenden Felder aus:
    
    1.  **Datei für den Import auswählen**   Fügen Sie den Namen der Richtliniendatei hinzu, die Sie installieren möchten.
    
    2.  **Name**   Fügen Sie einen Namen ein, der diese Richtlinie von anderen unterscheidet.
    
    3.  **Beschreibung** Fügen Sie optional eine Beschreibung mit einer Zusammenfassung dieser Richtlinie ein.
    
    4.  **Weitere Optionen**   Wählen Sie den Modus oder Status für diese Richtlinie. Die neue Richtlinie wird erst vollständig aktiviert, wenn Sie dies angeben. Der Standardmodus für eine Richtlinie sieht einen Test ohne Benachrichtigungen vor.
    
    5.  Klicken Sie auf **Weiter**, um die Richtlinie zu überprüfen und zu importieren.

## Verwenden der Shell zum Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei

In diesem Beispiel wird eine benutzerdefinierte DLP-Richtlinienvorlagendatei aus der Datei "C:\\My Documents\\DLP Backup.xml" importiert. Durch Importieren einer DLP-Richtliniensammlung aus einer XML-Datei werden alle vorhandenen DLP-Richtlinien entfernt oder überschrieben, die in Ihrer Organisation definiert wurden. Stellen Sie vor dem Importieren sicher, dass Sie über eine Sicherungskopie der aktuellen DLP-Richtliniensammlung verfügen, bevor Sie diese überschreiben.

    Import-DlpPolicyCollection -FileData ([Byte[]]$(Get-Content -Path " C:\My Documents\DLP Backup.xml " -Encoding Byte -ReadCount 0))

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)


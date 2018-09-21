---
title: 'Anzeigen von Informationen zu mobilen Geräten für Benutzer: Exchange 2013 Help'
TOCTitle: Anzeigen von Informationen zu mobilen Geräten für Benutzer
ms:assetid: 4fd263c0-ad61-416c-bd68-339bf66605cf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997974(v=EXCHG.150)
ms:contentKeyID: 50475631
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen von Informationen zu mobilen Geräten für Benutzer

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-29_

Benutzer können mehrere mobile Geräte für die Synchronisierung mit MicrosoftExchange Server 2013 konfigurieren. Mithilfe der Exchange-Verwaltungskonsole oder der Shell können Sie eine Liste der mobilen Geräte anzeigen, die einem bestimmten Benutzer zugeordnet sind.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf mobile Geräte finden Sie unter [Exchange ActiveSync](exchange-activesync-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachrichtlinien für mobile Geräte" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Anzeigen von Informationen zu mobilen Geräten für Benutzer mithilfe der Exchange-Verwaltungskonsole

Die Exchange-Verwaltungskonsole zeigt eine Liste der mobilen Geräte an, die derzeit für die Synchronisierung mit einem Benutzerpostfach konfiguriert sind. Sie können mobile Geräte nach Serie, Modell, Telefonnummer oder Status anzeigen.

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger** \> **Postfächer**, und wählen Sie ein Postfach aus.

2.  Führen Sie im Detailbereich einen Bildlauf bis **Telefon- und Sprachfunktionen** durch, und klicken Sie auf **Details anzeigen**, um den Bildschirm **Details des mobilen Geräts** anzuzeigen.

## Anzeigen von mobilen Geräteinformationen für Benutzer mithilfe der Shell

Mit diesem Cmdlet Get-MobileDevice können Sie eine Liste der mobilen Geräte für einen bestimmten Benutzer anzeigen.

1.  Führen Sie den folgenden Befehl aus.
    
    ```powershell
Get-MobileDevice -Mailbox useralias
```


---
title: 'Konfigurieren benutzerdef. E-Mail-Infos für Empfänger: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren benutzerdefinierter E-Mail-Infos für Empfänger
ms:assetid: df8ee7ae-2486-4890-b057-cda87b4cb1ec
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638199(v=EXCHG.150)
ms:contentKeyID: 52062784
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren benutzerdefinierter E-Mail-Infos für Empfänger

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-01_

Bei der *E-Mail-Info* handelt es sich um informative Meldungen, die auf der Infoleiste in Outlook Web App und Microsoft Outlook 2010 oder höher Benutzern angezeigt werden, wenn sie beim Verfassen einer E-Mail eine der folgenden Aktionen ausführen:

  - Empfänger hinzufügen

  - Anlage hinzufügen

  - Antworten oder allen antworten

  - Nachricht im Ordner "Entwürfe" öffnen, die bereits an Empfänger adressiert ist

Zusätzlich zu den verfügbaren vordefinierten E-Mail-Infos können Sie für alle Empfängertypen benutzerdefinierte E-Mail-Infos erstellen. Weitere Informationen zu den vordefinierten E-Mail-Infos finden Sie unter [MailTips](mailtips-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Infos" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Sie können die primäre E-Mail-Info in der Exchange-Verwaltungskonsole oder -Shell konfigurieren. Zusätzliche E-Mail-Info-Übersetzungen können Sie jedoch nur in der Shell konfigurieren.

  - Wenn Sie einem Empfänger eine E-Mail-Info hinzufügen, passieren zwei Dinge:
    
      - Dem Text werden automatisch HTML-Tags hinzugefügt. Angenommen, Sie geben den folgenden Text ein: `This mailbox is not monitored`. Dann ändert sich die E-Mail-Info automatisch in: `<html><body>This mailbox is not monitored</body></html>`. Zusätzliche HTML-Tags werden in der E-Mail-Info nicht unterstützt.
    
      - Der Text wird der Eigenschaft *MailTipTranslations* des Empfängers automatisch als Standardwert hinzugefügt. Wenn Sie den E-Mail-Infotext ändern, wird der Standardwert automatisch in der Eigenschaft *MailTipTranslations* aktualisiert.

  - Die Länge einer E-Mail-Info darf 175 angezeigte Zeichen nicht überschreiten.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren von E-Mail-Infos für Empfänger

## Verwenden der Exchange-Verwaltungskonsole zum Konfigurieren von E-Mail-Infos für Empfänger

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**.

2.  Wählen Sie basierend auf dem Empfängertyp eine der folgenden Empfängerregisterkarten aus:
    
      - **Postfächer**
    
      - **Gruppen**
    
      - **Ressourcen**
    
      - **Contacts**
    
      - **Shared**

3.  Wählen Sie auf der Empfängerregisterkarte den Empfänger aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Klicken Sie auf der angezeigten Seite mit den Empfängereigenschaften auf **E-Mail-Infos**.

5.  Geben Sie den Text der E-Mail-Info ein. Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Verwenden der Shell zum Konfigurieren von E-Mail-Infos für Empfänger

Verwenden Sie folgende Syntax, um eine E-Mail-Info für einen Empfänger zu konfigurieren.

    Set-<RecipientType> <RecipientIdentity> -MailTip "<MailTip text>"

*\<RecipientType\>* kann ein beliebiger Empfängertyp sein. Beispiele sind `Mailbox`, `MailUser`, `MailContact`, `DistributionGroup` oder `DynamicDistributionGroup`.

Angenommen, Sie haben ein Postfach mit dem Namen "Help Desk", an das Benutzer Supportanfragen senden können, und die zugesagte Antwortzeit ist zwei Stunden. Führen Sie den folgenden Befehl aus, um eine benutzerdefinierte E-Mail-Info zu konfigurieren, in der dies erläutert wird:

    Set-Mailbox "Help Desk" -MailTip "A Help Desk representative will contact you within 2 hours."

## Verwenden der Shell zum Konfigurieren zusätzlicher E-Mail-Infos in verschiedenen Sprachen

Zum Konfigurieren zusätzlicher Übersetzungen von E-Mail-Infos ohne Beeinträchtigung des vorhandenen E-Mail-Infotexts oder anderer vorhandener E-Mail-Info-Übersetzungen verwenden Sie die folgende Syntax:

    Set-<RecipientType> -MailTipTranslations @{Add="<culture1>:<localized text 1>","<culture2>:<localized text 2>"...; Remove="<culture1>:<localized text 1>","<culture2>:<localized text 2>"...}

*\<culture\>* ist ein gültiger aus zwei Buchstaben bestehender ISO 639-Kulturcode der Sprache.

Angenommen, das Postfach mit dem Namen "Benachrichtigungen" hat derzeit beispielsweise die E-Mail-Info: "Dieses Postfach wird nicht überwacht." Führen Sie den folgenden Befehl aus, um die spanische Übersetzung hinzuzufügen:

    Set-Mailbox -MailTipTranslations @{Add="ES:Esta caja no se supervisa."}

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine E-Mail-Info erfolgreich für einen Empfänger konfiguriert wurde:

1.  Verfassen Sie in Outlook Web App oder Outlook 2010 oder höher eine an den Empfänger adressierte E-Mail-Nachricht, ohne Sie zu senden.

2.  Überprüfen Sie, ob die E-Mail-Info in der Infoleiste angezeigt wird.

3.  Wenn Sie weitere E-Mail-Info-Übersetzungen konfiguriert haben, verfassen Sie die Nachricht in Outlook Web App. Zum Überprüfen der Ergebnisse muss die Spracheinstellung der Sprache der E-Mail-Info-Übersetzung entsprechen.


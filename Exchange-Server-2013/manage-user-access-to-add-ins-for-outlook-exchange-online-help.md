---
title: 'Verwalten des Benutzerzugriffs auf Apps für Outlook: Exchange 2013 Help'
TOCTitle: Verwalten des Benutzerzugriffs auf Apps für Outlook
ms:assetid: e5833dec-a23a-439e-ac03-92671817bff8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ943757(v=EXCHG.150)
ms:contentKeyID: 52062919
ms.date: 05/05/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten des Benutzerzugriffs auf Apps für Outlook

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2018-04-17_

Sie können den Benutzerzugriff auf Add-Ins für Outlook mithilfe des Exchange Admin Center (EAC) oder der Exchange PowerShell verwalten.

  - Über das EAC können Sie die grundlegenden Add-In-Zugriffseinstellungen für Ihre Benutzer auf Organisationsebene verwalten. Sie können z. B. bestimmen, ob ein Add-In für die Benutzer aktiviert oder deaktiviert ist. Sie können auch bestimmen, ob ein Add-In für die Benutzer erforderlich oder optional ist.

  - Über die Exchange-Verwaltungsshell oder die Exchange Online PowerShell können Sie alle Einstellungen, die das EAC bietet, und noch andere Einstellungen verwalten. Beispielsweise können Sie die Verfügbarkeit auf bestimmte Benutzer in Ihrer Organisation beschränken.

Informationen zu weiteren Verwaltungsaufgaben finden Sie unter [Apps für Outlook](add-ins-for-outlook-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Weitere Informationen zum EAC finden Sie unter [Exchange Admin Center in Exchange 2013](exchange-admin-center-in-exchange-2013-exchange-2013-help.md) oder [Exchange Admin Center in Exchange Online](https://technet.microsoft.com/de-de/library/jj200743\(v=exchg.150\)).

  - Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).Wie Sie mit Windows PowerShell eine Verbindung mit Exchange Online herstellen, können Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554) nachlesen.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Add-Ins für Outlook" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Angeben, ob ein Add-In verfügbar, aktiviert oder deaktiviert ist

## Angeben, ob ein Add-In verfügbar, aktiviert oder deaktiviert ist, mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Organisation** \> **Add-Ins**.

2.  Wählen Sie in der Listenansicht das Add-In aus, dessen Einstellungen Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wenn Sie nicht möchten, dass Ihre Benutzer das Add-In verwenden, deaktivieren Sie das Kontrollkästchen **Dieses Add-In Benutzern in Ihrer Organisation zur Verfügung stellen**, und klicken Sie anschließend auf **Speichern**.

4.  Wenn Sie möchten, dass Ihre Benutzer das Add-In verwenden, aktivieren Sie das Kontrollkästchen **Dieses Add-In Benutzern in Ihrer Organisation zur Verfügung stellen**, und wählen Sie anschließend die gewünschte Option aus.
    
      - **Optional, standardmäßig aktiviert**: Verwenden Sie diese Einstellung, wenn Sie den Benutzern das Deaktivieren des Add-Ins ermöglichen möchten.
    
      - **Optional, standardmäßig deaktiviert**: Verwenden Sie diese Einstellung, wenn Sie den Benutzern das Aktivieren des Add-Ins ermöglichen möchten.
    
      - **Vorgeschrieben, immer aktiviert. Benutzer können dieses Add-In nicht deaktivieren**: Wählen Sie diese Einstellung aus, wenn Sie nicht möchten, dass Ihre Benutzer das Add-In deaktivieren.

5.  Klicken Sie auf **Speichern**.

## Verwenden der Exchange PowerShell, um anzugeben, ob ein Add-In verfügbar, aktiviert oder deaktiviert ist

Führen Sie zunächst den folgenden Befehl aus, um die Anzeigenamen und Add-In-IDs aller Add-Ins für Outlook zu suchen, die für Ihre Organisation installiert sind.

    Get-App -OrganizationApp | Format-List DisplayName,AppId

Der **AppId**-Wert ist eine GUID, die das Add-In eindeutig identifiziert (z. B. `fe93bfe1-7947-460a-a5e0-7a5906b51360`). Verwenden Sie den **AppId**-Wert zum Identifizieren und Ändern der Einstellung für das Add-In.

Zum Deaktivieren und Ausblenden eines Add-Ins für alle Benutzer ersetzen Sie *\<AppId\>* mit dem tatsächlichen **AppId**-Wert und führen Sie den folgenden Befehl aus:

    Set-App -Identity <AppId> -OrganizationApp -Enabled $false

Um ein Add-In standardmäßig zu aktivieren, Ihren Benutzern aber zu gestatten, dies rückgängig zu machen, ersetzen Sie *\<AppId\>* mit dem tatsächlichen **AppId**-Wert und führen Sie den folgenden Befehl aus:

    Set-App -Identity <AppId> -OrganizationApp -Enabled $true -DefaultStateForUser Enabled

Um ein Add-In standardmäßig zu deaktivieren, Ihren Benutzern aber zu gestatten, es zu aktivieren, ersetzen Sie *\<AppId\>* mit dem tatsächlichen **AppId**-Wert und führen Sie den folgenden Befehl aus:

    Set-App -Identity <AppId> -OrganizationApp -Enabled $true -DefaultStateForUser Disabled

Wenn das Add-In für Benutzer vorgeschrieben sein soll, ersetzen Sie *\<AppId\>* mit dem tatsächlichen **AppId**-Wert und führen Sie den folgenden Befehl aus:

    Set-App -Identity <AppId> -OrganizationApp -Enabled $true -DefaultStateForUser AlwaysEnabled

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-App](https://technet.microsoft.com/de-de/library/jj218630\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Befolgen Sie einen beliebigen der folgenden Schritte, um sicherzustellen, dass das Add-In erfolgreich konfiguriert wurde:

  - Navigieren Sie im EAC zu **Organisation** \> **Add-Ins**, und überprüfen Sie die Werte in den Spalten **Benutzerstandard** und **Bereitgestellt für**.

  - Führen Sie den folgenden Befehl in der Exchange Online PowerShell aus, und überprüfen Sie die Werte der **DefaultStateForUser**- und **Enabled**-Eigenschaften:
    
        Get-App -OrganizationApp | Format-List DisplayName,AppId,Enabled,DefaultStateForUser

## Verwenden der Exchange PowerShell zum Beschränken der Add-In-Verfügbarkeit auf bestimmte Benutzer

Wenn Sie die Verfügbarkeit eines Add-Ins auf bestimmte Benutzer beschränken möchten, können Sie das EAC nicht verwenden. Sie können nur die Exchange-Verwaltungsshell oder die Exchange Online PowerShell verwenden.

Bei diesem Beispiel wird das LinkedIn-Add-In mit dem hypothetischen **AppId**-Wert `ac83a9d5-5af2-446f-956a-c583adc94d5e` auf die Mitglieder der Verteilergruppe namens Marketing beschränkt.

```
    $a = Get-DistributionGroupMember Marketing
```

```
    Set-App -Identity ac83a9d5-5af2-446f-956a-c583adc94d5e -OrganizationApp -ProvidedTo SpecificUsers -UserList $a.Identity -DefaultStateForUser Enabled
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-App](https://technet.microsoft.com/de-de/library/jj218630\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sicherzustellen, dass Sie die Verfügbarkeit von Add-Ins erfolgreich auf bestimmte Benutzer eingeschränkt haben, führen Sie den folgenden Befehl in der Exchange PowerShell aus, und überprüfen Sie den Wert der **ProvidedTo**- und **UserList**-Eigenschaften:

    Get-App -OrganizationApp | Format-List DisplayName,AppId,Enabled,DefaultStateForUser,ProvidedTo,UserList


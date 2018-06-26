---
title: 'Erstellen eines freigegebenen Postfachs: Exchange 2013 Help'
TOCTitle: Erstellen eines freigegebenen Postfachs
ms:assetid: d34bc827-1e83-4a7f-a219-8ba9c19fe24b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150570(v=EXCHG.150)
ms:contentKeyID: 50476785
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines freigegebenen Postfachs

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Office 365 Enterprise_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

**Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten**

Freigegebene Postfächer erleichtern es einer Gruppe von Personen in Ihrem Unternehmen, E-Mails von einem allgemeinen Konto wie "info@contoso.com" oder "support@contoso.com" zu überwachen und zu senden. Wenn eine Person in der Gruppe auf eine Nachricht antwortet, die an das gemeinsam genutzte Postfach gesendet wurde, sieht es so aus, als sei die E-Mail von dem gemeinsamen Postfach und nicht von dem speziellen Benutzer gesendet worden.


> [!IMPORTANT]
> Wenn Sie Office 365 for Business verwenden, sollten Sie Ihr freigegebenes Postfach im Office 365 Admin Center erstellen. 
> <UL>
> <LI>
> <P><A href="https://go.microsoft.com/fwlink/p/?linkid=834766">Erstellen von freigegebenen Postfächern in Office 365</A></P></LI></UL>



Wenn Ihre Organisation eine Exchange-Hybridumgebung verwendet, sollten Sie das lokale Exchange Admin Center (EAC) zum Erstellen und Verwalten von freigegebenen Postfächern verwenden. Weitere Informationen zu freigegebenen Postfächern finden Sie unter [Freigegebene Postfächer](shared-mailboxes-exchange-2013-help.md).

## Erstellen eines freigegebenen Postfachs mithilfe der Exchange-Verwaltungskonsole

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Benutzerpostfächer" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

1.  Navigieren Sie zu **Empfänger** \> **Freigegeben** \> **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Füllen Sie die erforderlichen Felder aus:
    
      - **Anzeigename**
    
      - **E-Mail-Adresse**

3.  Klicken Sie zum Erteilen von Vollzugriff oder "Senden als"-Berechtigungen auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie dann die Benutzer aus, denen Sie Berechtigungen erteilen möchten. Sie können die **CTRL**-TASTE verwenden, um mehrere Benutzer auszuwählen. Sie wissen nicht, welche Berechtigung Sie verwenden sollen? Siehe Welche Berechtigungen sollten Sie verwenden? weiter unten in diesem Thema.
    

    > [!NOTE]
    > Die Vollzugriff-Berechtigung ermöglicht es einem Benutzer, das Postfach zu öffnen und Elemente darin zu erstellen oder zu ändern. Die "Senden als"-Berechtigung ermöglicht es Benutzern, bei denen es sich nicht um den Postfachbesitzer handelt, E-Mails von dem freigegebenen Postfach zu senden. Beide Berechtigungen sind für erfolgreiche freigegebene Postfächer erforderlich.



4.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern und das freigegebene Postfach zu erstellen.

## Bearbeiten der freigegebenen Postfach-Stellvertretung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Freigegeben** \> **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf **Stellvertreter für Postfächer**.

3.  Klicken Sie zum Erteilen oder Entziehen von Vollzugriff oder "Senden als"-Berechtigungen auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") oder **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), und wählen Sie dann die Benutzer aus, denen Sie Berechtigungen erteilen möchten.
    

    > [!NOTE]
    > Die Vollzugriff-Berechtigung ermöglicht es einem Benutzer, das Postfach zu öffnen und Elemente darin zu erstellen oder zu ändern. Die "Senden als"-Berechtigung ermöglicht es Benutzern, bei denen es sich nicht um den Postfachbesitzer handelt, E-Mails von dem freigegebenen Postfach zu senden. Beide Berechtigungen sind für erfolgreiche freigegebene Postfächer erforderlich.



4.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Verwenden eines freigegebenen Postfachs

Um zu erfahren, wie Benutzer auf freigegebene Postfächer zugreifen und diese verwenden, lesen Sie die folgenden Informationen:

  - [Öffnen und Verwenden eines freigegebenes Postfachs in Outlook 2016 und Outlook 2013](https://go.microsoft.com/fwlink/p/?linkid=834764)

  - [Öffnen und Verwenden eines freigegebenen Postfachs in Outlook im Web für Unternehmen](https://go.microsoft.com/fwlink/p/?linkid=834766)

## Erstellen eines freigegebenen Postfachs mithilfe der Shell

In diesem Beispiel wird das freigegebene Postfach "Sales Department" erstellt, und der Sicherheitsgruppe "MarketingSG" werden Vollzugriff und "Senden im Auftrag von"-Berechtigungen erteilt. Benutzern, die Mitglied der Sicherheitsgruppe sind, werden die Berechtigungen für das Postfach erteilt.


> [!NOTE]
> In diesem Beispiel wird davon ausgegangen, dass Sie bereits die Sicherheitsgruppe MarketingSG erstellt haben und dass die Sicherheitsgruppe für E-Mail aktiviert ist. Weitere Informationen finden Sie unter <A href="manage-mail-enabled-security-groups-exchange-2013-help.md">Verwalten von E-Mail-aktivierten Sicherheitsgruppen</A>.



    New-Mailbox -Shared -Name "Sales Department" -DisplayName "Sales Department" -Alias Sales | Set-Mailbox -GrantSendOnBehalfTo MarketingSG | Add-MailboxPermission -User MarketingSG -AccessRights FullAccess -InheritanceType All

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)).

## Welche Berechtigungen sollten Sie verwenden?

Sie können die folgenden Berechtigungen mit einem freigegebenen Postfach verwenden.

  - **Vollzugriff**   Die Berechtigung "Vollzugriff" ermöglicht es einem Benutzer, das freigegebene Postfach zu öffnen und als Besitzer dieses Postfachs zu agieren. Nach dem Zugriff auf das freigegebene Postfach kann der Benutzer Kalenderelemente erstellen, E-Mails lesen, anzeigen, löschen und ändern sowie Tasks und Kalenderkontakte erstellen. Ein Benutzer mit der Berechtigung "Vollzugriff" kann jedoch keine E-Mails über das freigegebene Postfach senden, außer er hat auch die Berechtigung "Senden als" oder "Senden im Auftrag von".

  - **Senden als**   Die Berechtigung "Senden als" ermöglicht es einem Benutzer, das freigegebene Postfach beim Senden von E-Mails zu imitieren. Beispiel: Kweku meldet sich beim freigegebenen Postfach der Marketing-Abteilung an und sendet eine E-Mail. Diese wird so angezeigt, als ob die Marketing-Abteilung die E-Mail gesendet hätte.

  - **Senden im Auftrag von**   Die Berechtigung "Senden im Auftrag von" ermöglicht es einem Benutzer, E-Mails im Auftrag des freigegebenen Postfachs zu senden. Beispiel: John meldet sich beim freigegebenen Postfach des Empfangs in Gebäude 32 an und sendet eine E-Mail. Dem Empfänger wird angezeigt, dass John sie im Auftrag des Empfangs in Gebäude 32 gesendet hat. Sie können die Exchange-Verwaltungskonsole nicht verwenden, um "Senden im Auftrag von" zu ermöglichen. Sie müssen das [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))-Cmdlet mit dem *GrantSendonBehalf*-Parameter verwenden.

## Weitere Informationen

Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



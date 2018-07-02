---
title: 'Erstellen eines öffentlichen Ordners: Exchange 2013 Help'
TOCTitle: Erstellen eines öffentlichen Ordners
ms:assetid: 6d252e60-c8d0-4efd-b9d7-ba5284a6f8ab
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb691104(v=EXCHG.150)
ms:contentKeyID: 50475898
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.PublicFolders.NewPublicFolderWizardForm.NewPublicFolderWizardPage
ms.translationtype: HT
---

# Erstellen eines öffentlichen Ordners

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-02-24_

Öffentliche Ordner ermöglichen den gemeinsamen Zugriff und stellen ein einfaches und effektives Mittel zum Erfassen, Organisieren und Freigeben von Informationen für andere Personen in der Arbeitsgruppe oder Organisation dar.

Ein öffentlicher Ordner erbt standardmäßig die Einstellungen seines übergeordneten Ordners, einschließlich der Einstellungen für Berechtigungen.


> [!NOTE]
> Weitere Informationen zu den Speicherkontingenten und -grenzwerten bei öffentlichen Ordnern finden Sie unter den folgenden Themen: 
> <UL>
> <LI>
> <P>Informationen zu öffentlichen Ordnern bei Office 365 finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=391188">Exchange Online-Begrenzungen</A>.</P>
> <LI>
> <P>Informationen zu öffentlichen Ordnern beim intern verwalteten Exchange Server 2013 finden Sie unter <A href="limits-for-public-folders-exchange-2013-help.md">Grenzwerte für öffentliche Ordner</A>.</P></LI></UL>



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit öffentlichen Ordnern finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner finden Sie unter [Öffentliche Ordnerprozeduren in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj966272\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Öffentliche Ordner" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Sie können erst dann einen öffentlichen Ordner erstellen, nachdem Sie ein Postfach für öffentliche Ordner erstellt haben. Weitere Informationen zum Erstellen eines Postfachs für öffentliche Ordner finden Sie unter [Erstellen eines Postfachs für öffentliche Ordner](create-a-public-folder-mailbox-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Erstellen eines öffentlichen Ordners mithilfe der Exchange-Verwaltungskonsole

Wenn Sie einen öffentlichen Ordner mithilfe der Exchange-Verwaltungskonsole erstellen, können Sie nur den Namen und den Pfad für den Ordner festlegen. Nachdem der öffentliche Ordner erstellt wurde, müssen Sie ihn bearbeiten, um weitere Einstellungen zu konfigurieren.

1.  Navigieren Sie zu **Öffentliche Ordner** \> **Öffentliche Ordner**.

2.  Wenn Sie diesen öffentlichen Ordner als untergeordneten Ordner eines vorhandenen öffentlichen Ordners erstellen möchten, klicken Sie in der Listenansicht auf den gewünschten öffentlichen Ordner. Wenn Sie einen öffentlichen Ordner der obersten Ebene erstellen möchten, überspringen Sie diesen Schritt.

3.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Geben Sie im Feld **Öffentlicher Ordner** den Namen des öffentlichen Ordners ein.
    

    > [!IMPORTANT]
    > Verzichten Sie beim Erstellen eines öffentlichen Ordners auf einen umgekehrten Schrägstrich (\) in dessen Namen.



5.  Überprüfen Sie im Feld **Pfad** den Pfad zum öffentlichen Ordner. Wenn dies nicht der gewünschte Pfad ist, klicken Sie auf **Abbrechen**, und führen Sie Schritt 2 dieses Verfahrens durch.

6.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Erstellen eines Öffentlichen Ordners

In diesem Beispiel wird ein öffentlicher Ordner "Reports" im Pfad "Marketing\\2013" erstellt.

    New-PublicFolder -Name Reports -Path \Marketing\2013


> [!IMPORTANT]
> Verzichten Sie beim Erstellen eines öffentlichen Ordners auf einen umgekehrten Schrägstrich (\) in dessen Namen.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-PublicFolder](https://technet.microsoft.com/de-de/library/aa996405\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob der öffentliche Ordner erfolgreich erstellt wurde:

  - Klicken Sie in der Exchange-Verwaltungskonsole auf **Aktualisieren**, um die Liste der öffentlichen Ordner zu aktualisieren. Ihr neuer öffentlicher Ordner sollte in der Liste angezeigt werden.

  - Führen Sie in der Shell einen der folgenden Befehle aus:
    
        Get-PublicFolder -Identity \Marketing\2013\Reports | Format-List
    
        Get-PublicFolder -Identity \Marketing\2013 -GetChildren
    
        Get-PublicFolder -Recurse


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



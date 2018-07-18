---
title: 'E-Mail-Aktivierung oder E-Mail-Deaktivierung von öffentlichen Ordnern: Exchange 2013 Help'
TOCTitle: E-Mail-Aktivierung oder E-Mail-Deaktivierung von öffentlichen Ordnern
ms:assetid: 3d69f76d-ff3c-46c1-b962-6a1baa425d8a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997560(v=EXCHG.150)
ms:contentKeyID: 50475430
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# E-Mail-Aktivierung oder E-Mail-Deaktivierung von öffentlichen Ordnern

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-06-15_

Öffentliche Ordner ermöglichen den gemeinsamen Zugriff und stellen ein einfaches und effektives Mittel zum Erfassen, Organisieren und Freigeben von Informationen für andere Personen in der Arbeitsgruppe oder Organisation dar. Die E-Mail-Aktivierung eines öffentlichen Ordners ermöglicht es Benutzern, Nachrichten in diesem öffentlichen Ordner zu posten, indem sie eine E-Mail an den öffentlichen Ordner senden. Wenn ein öffentlicher Ordner E-Mail-aktiviert wird, stehen in der Exchange-Verwaltungskonsole zusätzliche Einstellungen für den öffentlichen Ordner zur Verfügung, beispielsweise E-Mail-Adressen und E-Mail-Kontingente. In der Shell verwenden Sie vor der E-Mail-Aktivierung eines öffentlichen Ordners das Cmdlet **Set-PublicFolder**, um sämtliche dieser Einstellungen zu verwalten. Nach der E-Mail-Aktivierung des öffentlichen Ordners verwenden Sie die Cmdlets **Set-PublicFolder** und **Set-MailPublicFolder** zum Verwalten der Einstellungen.

Wenn Sie möchten, dass die Benutzer im Internet E-Mails an einen E-Mail-aktivierten öffentlichen Ordner senden, müssen Sie zusätzliche Berechtigungen mit dem Cmdlet **Add-PublicFolderClientPermission** festlegen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit öffentlichen Ordnern finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner finden Sie unter [Öffentliche Ordnerprozeduren in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj966272\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Um sicherzustellen, dass Benutzer im Internet E-Mail-Nachrichten an E-Mail-aktivierte öffentliche Ordner senden können, muss dem anonymen Konto im öffentlichen Ordner mindestens das Zugriffsrecht *CreateItems* erteilt werden. Wenn Sie wissen möchten, wie das geht, gehen Sie zu Zulassen, dass anonyme Benutzer E-Mails an einen E-Mail-aktivierten öffentlichen Ordner senden.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Öffentliche Ordner" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## E-Mail-Aktivierung oder -Deaktivierung eines öffentlichen Ordners mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Öffentliche Ordner** \> **Öffentliche Ordner**.

2.  Wählen Sie in der Listenansicht den öffentlichen Ordner aus, den Sie für E-Mails aktivieren oder deaktivieren möchten.

3.  Klicken Sie im Detailbereich unter **E-Mail-Einstellungen** auf **Aktivieren** oder **Deaktivieren**.

4.  Sie werden in einem Warnungsfeld gefragt, ob Sie wirklich E-Mails für den öffentlichen Ordner aktivieren oder deaktivieren möchten. Klicken Sie auf **Ja**, um den Vorgang fortzusetzen.

Wenn Sie möchten, dass externe Benutzer E-Mails an diesen öffentlichen Ordner senden, führen Sie die Schritte unter Zulassen, dass anonyme Benutzer E-Mails an einen E-Mail-aktivierten öffentlichen Ordner senden aus.

## Verwenden der Shell zum E-Mail-Aktivieren eines Öffentlichen Ordners

In diesem Beispiel wird der öffentliche Ordner "Help Desk" für E-Mails aktiviert.

    Enable-MailPublicFolder -Identity "\Help Desk"

In diesem Beispiel wird der öffentliche Ordner "Reports" unterhalb des öffentlichen Ordners "Marketing" zwar E-Mail-aktiviert, in den Adresslisten jedoch ausgeblendet.

    Enable-MailPublicFolder -Identity "\Marketing\Reports" -HiddenFromAddressListsEnabled $True

Wenn Sie möchten, dass externe Benutzer E-Mails an diesen öffentlichen Ordner senden, führen Sie die Schritte unter Zulassen, dass anonyme Benutzer E-Mails an einen E-Mail-aktivierten öffentlichen Ordner senden aus.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Enable-MailPublicFolder](https://technet.microsoft.com/de-de/library/aa998824\(v=exchg.150\)).

## Verwenden der Shell zum Deaktivieren eines Öffentlichen Ordners für E-Mail

In diesem Beispiel wird der öffentliche Ordner "Marketing\\Reports" für E-Mails deaktiviert.

    Disable-MailPublicFolder -Identity "\Marketing\Reports"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Disable-MailPublicFolder](https://technet.microsoft.com/de-de/library/bb123781\(v=exchg.150\)).

## Zulassen, dass anonyme Benutzer E-Mails an einen E-Mail-aktivierten öffentlichen Ordner senden

Sie können entweder Outlook oder die Shell verwenden, um Berechtigungen für das anonyme Benutzerkonto eines öffentlichen Ordners festzulegen. Die Exchange-Verwaltungskonsole kann nicht zum Festlegen von Berechtigungen für das anonyme Konto verwendet werden.

**Verwenden von Outlook für das Festlegen von Berechtigungen für das anonyme Konto**

1.  Öffnen Sie Outlook, indem Sie ein Konto verwenden, das über Besitzerrechte für den E-Mail-aktivierten öffentlichen Ordner verfügt, der E-Mails von anonymen Benutzern akzeptieren soll.

2.  Navigieren Sie zu **Öffentliche Ordner - \<Benutzername\>**.

3.  Navigieren Sie zu dem öffentlichen Ordner, den Sie ändern möchten.

4.  Klicken Sie mit der rechten Maustaste auf den öffentlichen Ordner, dann auf **Eigenschaften**, und wählen Sie die Registerkarte **Berechtigungen** aus.

5.  Wählen Sie das Konto **Anonym** und dann **Elemente erstellen** unter **Schreiben**, und klicken Sie dann auf **OK**.

**Verwenden der Shell für das Festlegen von Berechtigungen für das anonyme Konto**

In diesem Beispiel wird die Berechtigung `CreateItems` für das anonyme Konto im E-Mail-aktivierten öffentlichen Ordner "Kundenfeedback" festgelegt.

    Add-PublicFolderClientPermission "\Customer Feedback" -AccessRights CreateItems -User Anonymous

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Add-PublicFolderClientPermission](https://technet.microsoft.com/de-de/library/bb124743\(v=exchg.150\)).


---
title: 'Entfernen einer Organisationsbeziehung: Exchange 2013 Help'
TOCTitle: Entfernen einer Organisationsbeziehung
ms:assetid: ff211394-f58b-4da7-bb3a-df6abcb5950e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657513(v=EXCHG.150)
ms:contentKeyID: 50477149
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer Organisationsbeziehung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-01-04_

Mithilfe einer Organisationsbeziehung können Benutzer in der Exchange-Organisation Kalenderinformationen, Frei-/Gebucht-Daten mit einer Office 365-Organisation oder mit anderen lokalen Exchange-Organisationen teilen. Sie können eine Organisationsbeziehung entfernen, um Kalender nicht weiter mit der anderen Organisation zu teilen.

Bevor Sie Kalender für eine andere Organisation freigeben können, müssen Sie die Authentifizierungsbeziehung mit dem Azure Active Directory-Authentifzierungssystem (auch als "Verbund" bezeichnet) einrichten und die Mindestsoftwareanforderungen erfüllen. Weitere Informationen zur Verbundfreigabe finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Kalenderberechtigungen und gemeinsame Berechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Entfernen einer Organisationsbeziehung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie auf einem Exchange 2013-Server in Ihrer lokalen Organisation zu **Organisation** \> **Freigabe**.

2.  Wählen Sie unter **Organisationsfreigabe** eine Organisationsbeziehung aus, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"), um die Organisationsbeziehung zu entfernen.

3.  Klicken Sie in der Warnung, die angezeigt wird, auf **Ja**.

## Entfernen einer Organisationsbeziehung mithilfe der Shell

In diesem Beispiel wird die Organisationsbeziehung "Contoso" aus der Exchange-Organisation entfernt

    Remove-OrganizationRelationship -Identity "Contoso"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-OrganizationRelationship](https://technet.microsoft.com/de-de/library/ee332362\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um zu überprüfen, dass Sie die Organisationsbeziehung erfolgreich entfernt haben:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Organisation** \> **Freigabe**, und stellen Sie sicher, dass die Organisationsbeziehung in der Listenansicht unter **Organisationsfreigabe** nicht angezeigt wird.

  - Führen Sie den folgenden Shell-Befehl aus, um zu überprüfen, dass die Organisationsbeziehung entfernt wurde.
    
        Get-OrganizationRelationship | Format-List


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



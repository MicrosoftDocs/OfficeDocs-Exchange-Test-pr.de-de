---
title: 'Installieren oder Entfernen von Apps für Outlook für Organisation'
TOCTitle: Installieren oder Entfernen von Apps für Outlook für Ihre Organisation
ms:assetid: 112f3ef7-9943-4a1e-8a42-e08e8e9f67f4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ943752(v=EXCHG.150)
ms:contentKeyID: 52062834
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Installieren oder Entfernen von Apps für Outlook für Ihre Organisation

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2017-02-03_

Sie können Add-Ins für Outlook für Ihre Organisation über die Exchange-Verwaltungskonsole oder über die Shell installieren und entfernen.


> [!NOTE]
> Nachdem Sie ein Add-In für Ihre Organisation installiert haben, steht dieses standardmäßig allen Benutzern in Ihrer Organisation zur Verfügung. Nach der Installation können Sie mithilfe der Verwaltungskonsole oder der Shell das Add-In als für die Benutzer optional oder erforderlich festlegen und angeben, ob das Add-In aktiviert oder deaktiviert werden soll. Weitere Informationen zum Ändern der Standardeinstellungen für ein Add-In finden Sie unter <A href="manage-user-access-to-add-ins-for-outlook-exchange-online-help.md">Verwalten des Benutzerzugriffs auf Apps für Outlook</A>. Zum Beschränken der Verfügbarkeit von Add-Ins auf bestimmte Benutzer in Ihrer Organisation müssen Sie die Shell verwenden. Weitere Informationen finden Sie unter <A href="manage-user-access-to-add-ins-for-outlook-exchange-online-help.md">Verwalten des Benutzerzugriffs auf Apps für Outlook</A>.



Informationen zu weiteren Verwaltungsaufgaben finden Sie unter [Apps für Outlook](https://review.docs.microsoft.com/de-de/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/add-ins-for-outlook).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter „Apps für Outlook“ im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Sie können Administratoren die Berechtigung zum Installieren und Verwalten von Add-Ins für Ihre Organisation zuweisen. Außerdem können Sie Benutzern die Berechtigung zum Installieren und Verwalten von Add-Ins zur eigenen Verwendung zuweisen. Weitere Informationen finden Sie unter [Festlegen der Administratoren und Benutzer, die Add-Ins für Outlook installieren und verwalten dürfen](https://review.docs.microsoft.com/de-de/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).

  - Zugriff auf Office Store wird für Postfächer oder Organisationen in bestimmten Regionen nicht unterstützt. Wenn **Aus dem Office Store hinzufügen** nicht als Option im **Exchange Admin Center** unter **Organisation** \> **Add-Ins** \> ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") angezeigt wird, können Sie ein Add-In für Outlook über eine URL oder einen Dateispeicherort installieren. Weitere Informationen erhalten Sie von Ihrem Dienstanbieter.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Installieren eines Nimble-Add-Ins für Outlook

## Hinzufügen eines Add-Ins mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Organisation** \> **Add-Ins**.

2.  Klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie dann den Speicherort aus, von dem das Add-In installiert werden soll.
    
      - **Aus dem Office Store hinzufügen**. Wählen Sie im Office Store die App aus, die Sie installieren möchten, und klicken Sie dann auf **Hinzufügen**. Apps, die mit Outlook Web App funktionieren, werden unter **Add-Ins für Office und SharePoint** \> **Outlook** aufgeführt.
        

        > [!NOTE]
        > Zugriff auf Office Store wird für Postfächer oder Organisationen in bestimmten Regionen nicht unterstützt. Wenn <STRONG>Aus dem Office Store hinzufügen</STRONG> nicht als Option im <STRONG>Exchange Admin Center</STRONG> unter <STRONG>Organisation</STRONG> &gt; <STRONG>Add-Ins</STRONG> &gt; <IMG title="Hinzufügen (Symbol)" alt="Hinzufügen (Symbol)" src="images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif"> angezeigt wird, können Sie ein Add-In für Outlook über eine URL oder einen Dateispeicherort installieren. Weitere Informationen erhalten Sie von Ihrem Dienstanbieter.

    
      - **Aus URL hinzufügen**. Geben Sie im Feld **URL** die vollständige URL für die Add-In-Manifestdatei ein, die Sie installieren möchten.
    
      - **Aus Datei hinzufügen**. Wählen Sie **Durchsuchen**, und wechseln Sie zum Speicherort der Add-In-Manifestdatei, die Sie installieren möchten.

3.  Klicken Sie auf **Speichern**.

## Hinzufügen eines Add-Ins mithilfe der Shell

Dieses Beispiel zeigt, wie Sie ein Add-In aus einer URL hinzufügen.

    New-App -OrganizationApp -Url <URL location for add-in manifest file>

Dieses Beispiel zeigt, wie Sie ein Add-In aus einer Datei hinzufügen.

    New-App -OrganizationApp -FileData <File location for add-in manifest file>


> [!TIP]
> Wenn Sie zum Installieren eines Add-Ins für Ihre Organisation die Shell verwenden, können Sie das Add-In gleichzeitig installieren und seine Einstellungen konfigurieren.



Informationen zu Syntax und Parametern finden Sie unter [New-App](https://technet.microsoft.com/de-de/library/jj218722\(v=exchg.150\)).

## Entfernen eines Add-Ins für Outlook

## Entfernen eines Add-Ins mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Organisation** \> **Add-Ins**.

2.  Wählen Sie in der Listenansicht die App aus, die Sie entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

## Entfernen eines Add-Ins mithilfe der Shell

Sie können die Shell zum Entfernen eines Add-Ins aus Ihrer Organisation verwenden.


> [!NOTE]
> Führen Sie den folgenden Befehl aus, um die Anzeigenamen und Anwendungs-IDs aller Add-Ins für Outlook nachzuschlagen, die für Ihre Organisation installiert sind.



    Get-App -OrganizationApp |FL DisplayName,AppID

Führen Sie den folgenden Befehl aus, um das benutzerdefinierte Add-In „Finance Test Add-in“ aus Ihrer Organisation zu entfernen.

    Remove-App -OrganizationApp -Identity <GUID for Finance Test Add-in>

Informationen zu Syntax und Parametern finden Sie unter [Remove-App](https://technet.microsoft.com/de-de/library/jj218709\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die in Ihrer Organisation installierten Add-Ins anzuzeigen:

  - Wechseln Sie in der Exchange-Verwaltungskonsole zu **Organisation** \> **Add-Ins**, und prüfen Sie die Liste installierter Add-Ins.

  - Führen Sie in der Shell den Befehl `Get-App` aus, und prüfen Sie die Liste installierter Add-Ins.


---
title: 'Erstellen einer UM-Postfachrichtlinie: Exchange 2013 Help'
TOCTitle: Erstellen einer UM-Postfachrichtlinie
ms:assetid: 7f20874b-c46c-4505-9a78-f63eacb578ff
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)
ms:contentKeyID: 50554851
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.CreateUMMailboxPolicyWizardForm.CreateUMMailboxPolicyWizardPage
ms.translationtype: HT
---

# Erstellen einer UM-Postfachrichtlinie

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-03-08_

Sie können eine Unified Messaging-Postfachrichtlinie (UM) erstellen, um einen allgemeinen Satz von UM-Richtlinieneinstellungen, z. B. PIN-Richtlinieneinstellungen oder Wähleinschränkungen, auf eine Sammlung von UM-aktivierten Postfächern anzuwenden. UM-Postfachrichtlinien verknüpfen einen UM-aktivierten Benutzer mit einer UM-Wähleinstellung und wenden einen allgemeinen Satz von Richtlinien oder Sicherheitseinstellungen auf eine Sammlung von UM-aktivierten Postfächern an. UM-Postfachrichtlinien sind hilfreich beim Anwenden und Standardisieren von Unified Messaging-Konfigurationseinstellungen für UM-aktivierte Benutzer.

Beim Erstellen einer UM-Wähleinstellung wird standardmäßig gleichzeitig eine UM-Postfachrichtlinie erstellt. Nachdem Sie Unified Messaging in Ihrer Organisation bereitgestellt haben, müssen Sie ggf. weitere UM-Postfachrichtlinien erstellen und konfigurieren oder vorhandene UM-Postfachrichtlinien ändern.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Erstellen einer UM-Postfachrichtlinie

1.  
    
    Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wähleinstellungen** unter **UM-Postfachrichtlinien** auf **Neu** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie auf der Seite **Neue UM-Postfachrichtlinie** im Feld **Name** den Namen der neuen UM-Postfachrichtlinie ein.
    
    Geben Sie in dieses Feld einen eindeutigen Namen für die UM-Postfachrichtlinie ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Anzeigenamen der UM-Postfachrichtlinie nach dem Erstellen ändern müssen, muss zuerst die vorhandene UM-Postfachrichtlinie gelöscht und dann eine andere UM-Postfachrichtlinie mit dem entsprechenden Namen erstellt werden. Sie können eine UM-Postfachrichtlinie nur löschen, wenn dieser keine UM-aktivierten Benutzer zugeordnet sind.
    
    Der UM-Postfachrichtlinienname ist erforderlich, wird jedoch nur zur Anzeige verwendet. Wenn in Ihrer Organisation mehrere UM-Postfachrichtlinien verwendet werden, empfiehlt sich die Verwendung sinnvoller Namen für die UM-Postfachrichtlinien. Die maximale Länge eines UM-Postfachrichtliniennamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen. Er darf jedoch keines der folgenden Zeichen enthalten: " / \\ \[ \] : ; | = , + \* ? \< \>.

4.  Klicken Sie auf **Speichern**, um die neue UM-Postfachrichtlinie zu speichern. Wenn Sie die UM-Postfachrichtlinie speichern, werden alle Standardeinstellungen einschließlich PIN-Richtlinien, Voicemailfeatures und Einstellungen für geschützte Voicemail aktiviert. Wenn Sie Standardeinstellungen anpassen oder ändern möchten, verwenden Sie das Cmdlet **Set-UMMailbox**, um die Einstellungen für die UM-Postfachrichtlinie zu ändern, die Sie gerade erstellt haben.

## Erstellen einer UM-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel wird die neue UM-Postfachrichtlinie `MyUMMailboxPolicy` erstellt, die der UM-Wähleinstellung `MyUMDialPlan` zugeordnet wird.

    New-UMMailboxPolicy -Name MyUMMailboxPolicy -UMDialPlan MyUMDialPlan


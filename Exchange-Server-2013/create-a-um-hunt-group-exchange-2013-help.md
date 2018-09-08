---
title: 'Erstellen eines UM-Sammelanschlusses: Exchange Online Help'
TOCTitle: Erstellen eines UM-Sammelanschlusses
ms:assetid: 43ecb1ec-5f82-4516-9010-de8f954d3758
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997679(v=EXCHG.150)
ms:contentKeyID: 50554805
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.CreateUMHuntGroupWizardForm.CreateUMHuntGroupWizardPage1
ms.translationtype: MT
---

# Erstellen eines UM-Sammelanschlusses

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-16_

Ein UM-Sammelanschluss ist eine logische Darstellung eines Nebenstellenanlagen- oder IP-Nebenstellenanlagen-Sammelanschlusses. UM-Sammelanschlüsse fungieren als Verbindung oder Verknüpfung zwischen einem UM-IP-Gateway und einem UM-Wählplan.


> [!NOTE]
> Wenn Sie beim Erstellen eines UM-IP-Gateways das UM-IP-Gateway einem bestimmten UM-Wählplan zuordnen, wird auch ein UM-Sammelanschluss erstellt.




> [!NOTE]
> Wenn Sie die Einstellungen für den UM-Sammelanschluss ändern möchten, müssen Sie den Sammelanschluss löschen und dann einen neuen Sammelanschluss mit den entsprechenden Einstellungen erstellen.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit UM-Sammelanschlüsse finden Sie unter [Um-Sammelanschlüsse Gruppieren von Prozeduren](https://technet.microsoft.com/de-de/library/JJ851063(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Sammelanschlüsse" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](https://technet.microsoft.com/de-de/library/Aa998045(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Erstellen eines UM-Sammelanschlusses

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** unter **UM-Sammelanschlüsse** auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie auf der Seite **Neuer UM-Sammelanschluss** die folgenden Informationen ein:
    
      - **Name**   Verwenden Sie dieses Feld, um den Anzeigenamen für den UM-Sammelanschluss zu erstellen. Ein UM-Sammelanschlussname ist erforderlich, und er muss eindeutig sein, wobei er jedoch nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell verwendet wird. Wenn Sie den Anzeigenamen des Sammelanschlusses nach dem Erstellen ändern müssen, müssen Sie zuerst den vorhandenen Sammelanschluss löschen und können dann einen anderen Sammelanschluss mit dem entsprechenden Namen erstellen.
        
        Wenn in Ihrer Organisation mehrere Sammelanschlüsse verwendet werden, empfiehlt sich die Verwendung sprechender Namen für die Sammelanschlüsse. Die maximale Länge eines UM-Sammelanschlussnamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **UM-IP-Gateway**  Geben Sie mit diesem Feld das zu verwendende UM-IP-Gateway an. Klicken Sie auf **Durchsuchen**, um das UM-IP-Gateway auszuwählen, und klicken Sie dann auf **OK**.
    
      - **Pilot-ID** Verwenden Sie dieses Feld, um eine Zeichenfolge anzugeben, die die Pilot-ID eindeutig kennzeichnet, die auf der PBX- oder der IP-PBX-Anlage konfiguriert ist.
        
        In diesem Feld können eine Durchwahlnummer oder ein SIP-URI (Session Initiation-Protokoll - Uniform Resource Identifier) verwendet werden. Alphanumerische Zeichen sind in diesem Feld zulässig. Für ältere Nebenstellenanlagen wird ein numerischer Wert als Pilot-ID verwendet. Einige IP-Nebenstellenanlagen können jedoch SIP-URIs verwenden.

4.  Klicken Sie auf **Speichern**.

## Erstellen eines UM-Sammelanschlusses mit der Shell

In diesem Beispiel wird der UM-Sammelanschluss `MyUMHuntGroup` mit der Pilot-ID 12345 erstellt.

    New-UMHuntGroup -Name MyUMHuntGroup -PilotIdentifier 12345 -UMDialplan MyUMDialPlan -UMIPGateway MyUMIPGateway

In diesem Beispiel wird der UM-Sammelanschluss `MyUMHuntGroup` mit mehreren Pilot-IDs erstellt.

    New-UMHuntGroup -Name MyUMHuntGroup -PilotIdentifier 5551234,55555 -UMDialplan MyUMDialPlan -UMIPGateway MyUMIPGateway


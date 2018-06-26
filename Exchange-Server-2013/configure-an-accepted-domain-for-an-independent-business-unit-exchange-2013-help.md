---
title: 'Konfigurieren einer akzeptierten Domäne für eine unabhängige Unternehmenseinheit: Exchange 2013 Help'
TOCTitle: Konfigurieren einer akzeptierten Domäne für eine unabhängige Unternehmenseinheit
ms:assetid: bc95dbdc-3669-4c06-ab94-90093bc0dbfd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657491(v=EXCHG.150)
ms:contentKeyID: 50476577
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren einer akzeptierten Domäne für eine unabhängige Unternehmenseinheit

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-02-17_

Es kann vorkommen, dass Sie eine akzeptierte Domäne für eine unabhängige Geschäftseinheit mit E-Mail-Servern außerhalb Ihrer Exchange-Organisation konfigurieren möchten. In solchen Szenarien können Sie die akzeptierte Domäne als externe Relaydomäne konfigurieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Akzeptierte Domänen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Besteht in Ihrem Umkreisnetzwerk ein Edge-Transport-Serverabonnement, konfigurieren Sie akzeptierte Domänen auf einem Postfachserver in Ihrer Exchange-Organisation. Während der EdgeSync-Synchronisierung wird die Konfiguration der akzeptierten Domänen auf dem Edge-Transport-Server repliziert. Weitere Informationen finden Sie unter [Edge-Abonnements](edge-subscriptions-exchange-2013-help.md).

  - Es ist nicht möglich, eine akzeptierte Domäne mit demselben Namen wie eine bereits konfigurierte Remotedomäne zu erstellen. Wenn beispielsweise fabrikam.com als Remotedomäne konfiguriert wurde, kann keine akzeptierte Domäne für fabrikam.com erstellt werden.

  - Bevor Sie eine akzeptierte Domäne konfigurieren, müssen Sie sich vergewissern, dass ein öffentlicher DNS-MX-Ressourceneintrag (Domain Name System) für diesen SMTP-Namespace vorhanden ist und der MX-Ressourceneintrag auf einen Servernamen und eine IP-Adresse verweist, die Ihrer Exchange-Organisation zugeordnet sind.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren einer akzeptierten Domäne als externe Relaydomäne mithilfe der Exchange-Verwaltungskonsole

Möglicherweise möchten Sie eine akzeptierte Domäne für eine Geschäftseinheit mit E-Mail-Servern außerhalb Ihrer Exchange-Organisation konfigurieren.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Akzeptierte Domänen**, wählen Sie die Domäne aus, die Sie konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Geben Sie im Feld **Name** den Anzeigenamen für die akzeptierte Domäne ein. Jede akzeptierte Domäne für Ihre Organisation muss über einen eindeutigen Anzeigenamen verfügen. Dieser Name kann von der akzeptierten Domäne abweichen. Beispielsweise könnte Ihre Domäne "Contoso.com" über einen Anzeigenamen "Lokale akzeptierte Contoso-Domäne" verfügen.

3.  Wählen Sie **Externe Relaydomäne** aus. Diese Option wird für E-Mails verwendet, die an einen Server außerhalb Ihrer Exchange-Organisation weitergeleitet werden.

4.  Klicken Sie auf **Speichern**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn Sie überprüfen möchten, dass Sie die akzeptierte Domäne erfolgreich als externe Relaydomäne konfiguriert haben, senden Sie eine Nachricht von der akzeptierten Domäne, die Sie als externe Relaydomäne konfiguriert haben, und vergewissern Sie sich, dass diese Nachricht empfangen wird.


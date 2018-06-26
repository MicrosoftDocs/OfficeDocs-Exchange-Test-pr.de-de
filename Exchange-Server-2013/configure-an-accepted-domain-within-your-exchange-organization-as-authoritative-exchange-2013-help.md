---
title: 'Konfigurieren einer akzeptierten Domäne in Ihrer Exchange-Organisation als autoritativ: Exchange 2013 Help'
TOCTitle: Konfigurieren einer akzeptierten Domäne in Ihrer Exchange-Organisation als autoritativ
ms:assetid: e182d54f-e58a-47ba-a5c1-28c0dfa86eed
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657734(v=EXCHG.150)
ms:contentKeyID: 50476929
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren einer akzeptierten Domäne in Ihrer Exchange-Organisation als autoritativ

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-02-17_

Wenn eine zu Ihrer Organisation gehörende Domäne Postfächer für alle Empfänger in einem SMTP-Namespace hostet, wird diese Domäne als autoritative Domäne eingestuft. Eine akzeptierte Domäne wird standardmäßig als autoritative Domäne für die Exchange-Organisation konfiguriert. Wenn Ihre Organisation mehrere SMTP-Namespaces aufweist, können Sie mehrere akzeptierte Domänen als autoritative Domänen konfigurieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Akzeptierte Domänen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Besteht in Ihrem Umkreisnetzwerk ein Edge-Transport-Serverabonnement, konfigurieren Sie akzeptierte Domänen auf einem Postfachserver in Ihrer Exchange-Organisation. Während der EdgeSync-Synchronisierung wird die Konfiguration der akzeptierten Domänen auf dem Edge-Transport-Server repliziert. Weitere Informationen finden Sie unter [Edge-Abonnements](edge-subscriptions-exchange-2013-help.md).

  - Es ist nicht möglich, eine akzeptierte Domäne mit demselben Namen wie eine bereits konfigurierte Remotedomäne zu erstellen. Wenn beispielsweise fabrikam.com als Remotedomäne konfiguriert wurde, kann keine akzeptierte Domäne für fabrikam.com erstellt werden.

  - Bevor Sie eine akzeptierte Domäne konfigurieren, müssen Sie sich vergewissern, dass ein öffentlicher DNS-MX-Ressourcendatensatz (Domain Name System) für diesen SMTP-Namespace vorhanden ist und der MX-Ressourcendatensatz auf einen Servernamen und eine IP-Adresse verweist, die der Exchange-Organisation zugeordnet sind.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren einer akzeptierten Domäne als autoritative Domäne mithilfe der Exchange-Verwaltungskonsole

Wenn eine akzeptierte Domäne für Ihre Exchange-Organisation alle Postfächer für die Empfänger im SMTP-Namespace der Domäne hostet, können Sie diese als autoritative Domäne konfigurieren.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Akzeptierte Domänen**, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im Feld **Name** den Anzeigenamen für die akzeptierte Domäne ein. Jede akzeptierte Domäne für Ihre Organisation muss einen eindeutigen Anzeigenamen aufweisen. Dieser kann anders lauten als der Name der akzeptierten Domäne. Beispielsweise könnte die Domäne "contoso.com" über den Anzeigenamen "Lokale akzeptierte Contoso-Domäne" verfügen.

3.  Geben Sie im Feld **Akzeptierte Domäne** die akzeptierte Domäne ein. Geben Sie einen SMTP-Namespace an, für den Ihre Organisation E-Mails akzeptiert. (Beispiel: Contoso.com).

4.  Wählen Sie **Autoritative Domäne** aus. Die Option gilt für E-Mails, die mittels Relay für eine akzeptierte Domäne, die Postfächer für alle Empfänger in einem SMTP-Namespace hostet, an Server in Ihrer Exchange-Organisation umgeleitet werden.

5.  Klicken Sie auf **Speichern**.


> [!TIP]
> Zum Konfigurieren einer akzeptierten Domäne, die bereits erstellt wurde, wählen Sie die Domäne in der Liste der akzeptierten Domänen aus, und klicken Sie auf <STRONG>Bearbeiten</STRONG><IMG title=Bearbeitungssymbol alt=Bearbeitungssymbol src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif">. Sie können mehrere Domänen als autoritative Domänen konfigurieren.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Die neue akzeptierte Domäne wird in der Exchange-Verwaltungskonsole in der Liste der akzeptierten Domänen angezeigt. Um sich zu vergewissern, dass Sie die akzeptierte Domäne erfolgreich als autoritative Domäne konfiguriert haben, senden Sie eine E-Mail an die Domäne, und überprüfen Sie, ob sie empfangen wird.


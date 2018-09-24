---
title: 'Konf. akz. Domäne für Unternehmen m. Postfächern außerh. Exchange-Organis.'
TOCTitle: Konfigurieren einer akzeptierten Domäne für eine Unternehmenseinheit mit Postfächern außerhalb Ihrer Exchange-Organisation
ms:assetid: ff46310b-5392-4eac-97bc-d39d397e1ce1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657737(v=EXCHG.150)
ms:contentKeyID: 50477156
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren einer akzeptierten Domäne für eine Unternehmenseinheit mit Postfächern außerhalb Ihrer Exchange-Organisation

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-08-06_

In manchen Fällen möchten Sie möglicherweise eine akzeptierte Domäne für einen Geschäftsbereich konfigurieren, in dem einige oder alle Empfänger in der Domäne keine Postfächer in Ihrer Exchange-Organisation haben. Dies kann der Fall sein, wenn eine Organisation dieselbe SMTP-Adresse für zwei oder mehr verschiedene E-Mail-Systeme verwendet. In solchen Szenarios können Sie eine akzeptierte Domäne als interne Relaydomäne konfigurieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Akzeptierte Domänen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Besteht in Ihrem Umkreisnetzwerk ein Edge-Transport-Serverabonnement, konfigurieren Sie akzeptierte Domänen auf einem Postfachserver in Ihrer Exchange-Organisation. Während der EdgeSync-Synchronisierung wird die Konfiguration der akzeptierten Domänen auf dem Edge-Transport-Server repliziert. Weitere Informationen finden Sie unter [Edge-Abonnements](edge-subscriptions-exchange-2013-help.md).

  - Bevor Sie eine akzeptierte Domäne konfigurieren, müssen Sie sich vergewissern, dass ein öffentlicher DNS-MX-Ressourceneintrag (Domain Name System) für diesen SMTP-Namespace vorhanden ist und der MX-Ressourceneintrag auf einen Servernamen und eine IP-Adresse verweist, die Ihrer Exchange-Organisation zugeordnet sind.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden Sie die Exchange-Verwaltungskonsole, um eine akzeptierte Domäne als interne Relaydomäne zu konfigurieren

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Akzeptierte Domänen**, wählen Sie die Domäne aus, die konfiguriert werden soll, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Geben Sie im Feld **Name** den Anzeigenamen für die akzeptierte Domäne ein. Jede akzeptierte Domäne für Ihre Organisation muss über einen eindeutigen Anzeigenamen verfügen. Dieser Name kann von der akzeptierten Domäne abweichen. Beispielsweise könnte Ihre Domäne "Contoso.com" über einen Anzeigenamen "Lokale akzeptierte Contoso-Domäne" verfügen.

3.  Wählen Sie **Interne Relaydomäne** aus.

4.  Klicken Sie auf **Speichern**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Stellen Sie sicher, dass Sie erfolgreich eine akzeptierte Domäne als interne Relaydomäne konfiguriert haben, indem Sie eine Nachricht von der internen Relaydomäne an ein Postfach in Ihrer Exchange-Organisation senden und überprüfen, dass sie empfangen wird.


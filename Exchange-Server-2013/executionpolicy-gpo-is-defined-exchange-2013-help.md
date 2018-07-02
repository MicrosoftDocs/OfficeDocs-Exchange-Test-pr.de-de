---
title: 'ExecutionPolicy-Gruppenrichtlinienobjekt ist definiert: Exchange 2013 Help'
TOCTitle: ExecutionPolicy-Gruppenrichtlinienobjekt ist definiert
ms:assetid: 63de83e2-9a6b-4f57-85b9-df445bea18dd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.powershellexecutionpolicycheckset(v=EXCHG.150)
ms:contentKeyID: 61201339
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# ExecutionPolicy-Gruppenrichtlinienobjekt ist definiert

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-15_

Microsoft Exchange Server 2013 Setup kann nicht fortfahren, weil erkannt wurde, dass das Gruppenrichtlinienobjekt **ExecutionPolicy** mindestens eine der beiden folgenden Richtlinien definiert:

  - **MachinePolicy**

  - **UserPolicy**

Es ist gleichgültig, wie die Richtlinien definiert wurden. Von Belang ist nur, dass sie definiert wurden.

Wenn Sie Exchange 2013 Setup ausführen, wird Exchange beendet und der Windows-Verwaltungsinstrumentationsdienst deaktiviert. Wenn eine dieser Richtlinien definiert wurde, muss der WMI-Dienst aktiviert werden, um ein Windows PowerShell-Skript auszuführen. Wenn die Richtlinien definiert sind und der WMI-Dienst angehalten wurde, schlägt Setup fehl, und der Server bleibt in einem inkonsistenten Zustand.

Damit Setup fortfahren kann, müssen Sie zeitweilig die Definition von **MachinePolicy** bzw. **UserPolicy** aus dem Gruppenrichtlinienobjekt **ExecutionPolicy** entfernen.

Informationen dazu, wie Sie Definitionen von **MachinePolicy** oder **UserPolicy** aus dem Gruppenrichtlinienobjekt **ExecutionPolicy** entfernen, finden Sie im [Knowledge Base-Artikel KB981474](https://go.microsoft.com/fwlink/?linkid=3052%26kbid=981474).


> [!NOTE]
> Dieser Knowledge Base-Artikel wurde zwar für Exchange 2010 geschrieben, er gilt aber auch für kumulative Updates und Service Packs für Exchange 2013.



Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.


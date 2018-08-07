---
title: 'Deinstallieren der Unified Messaging-Sprachpakete'
TOCTitle: Deinstallieren der Unified Messaging-Sprachpakete_AdditionalUMLangPackExists
ms:assetid: 3a7e2621-0553-44f5-8029-c72fea25af3c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.additionalumlangpackexists(v=EXCHG.150)
ms:contentKeyID: 50475335
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Deinstallieren der Unified Messaging-Sprachpakete\_AdditionalUMLangPackExists

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil beim Upgrade der Unified Messaging-Serverrolle ein Fehler aufgetreten ist.

Das Setup von Exchange erfordert, dass alle Sprachpakete für die Unified Messaging -Serverrolle mit Ausnahme des US-Englischen Sprachpakets deinstalliert werden, bevor das Upgrade der Unified Messaging-Serverrolle fortgesetzt werden kann.

In Exchange 2007 enthaltene UM-Sprachpakete (Unified Messaging) enthalten voraufgezeichnete Ansagen und TTS-Konvertierungsunterstützung (Text-to-Speech) für die jeweilige Sprache.

Die Sprachpakete von Exchange 2007 ermöglichen Anrufern und Benutzern von Outlook Voice Access die Interaktion mit dem Unified Messaging-System in mehreren Sprachen.

Die vorhandenen Nicht-US-Englischen Sprachpakete müssen deinstalliert werden, damit neue Sprachpakete installiert werden können.

Um dieses Problem zu beheben, deinstallieren Sie alle Sprachpakete für die Unified Messaging-Serverrolle mit Ausnahme des US-Englischen Sprachpakets, und führen Sie das Exchange 2007-Setup anschließend erneut aus.

Weitere Informationen zum Deinstallieren der Sprachpakete für die Unified Messaging-Serverrolle finden Sie unter [Entfernen eines Unified Messaging-Sprachpakets von einem Unified Messaging-Server](https://go.microsoft.com/fwlink/?linkid=85973) in der Exchange 2007-Produktdokumentation.


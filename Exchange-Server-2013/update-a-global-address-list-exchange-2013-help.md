---
title: 'Aktualisieren einer globalen Adressliste: Exchange 2013 Help'
TOCTitle: Aktualisieren einer globalen Adressliste
ms:assetid: 236e8530-62dd-4c43-8a5d-8465623252e6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb266966(v=EXCHG.150)
ms:contentKeyID: 50475218
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktualisieren einer globalen Adressliste

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

Sie können die Shell verwenden, um eine globale Adressliste (Global Address List, GAL) zu aktualisieren. Eine globale Adressliste ist ein Verzeichnis, das Einträge für alle Gruppen, Benutzer und Kontakte in der Microsoft Exchange-Implementierung einer Organisation enthält.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adresslisten finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adresslisten" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe“ im Thema [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Aktualisieren einer globalen Adressliste

In diesem Beispiel wird eine globale Adressliste für das Unternehmen "Fourth Coffee" aktualisiert.


> [!NOTE]
> Durch das Ausführen dieses Befehls wird der Updatevorgang nur gestartet. Es kann einige Stunden dauern, bis die GAL aktualisiert wurde.



```powershell
Update-GlobalAddressList -Identity "Fourth Coffee"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Update-GlobalAddressList](https://technet.microsoft.com/de-de/library/aa998806\(v=exchg.150\)).


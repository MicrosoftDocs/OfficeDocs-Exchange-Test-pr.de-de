---
title: 'Erstellen einer Rolle: Exchange 2013 Help'
TOCTitle: Erstellen einer Rolle
ms:assetid: e614ad8f-5946-4135-b130-89ea626afcd4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351214(v=EXCHG.150)
ms:contentKeyID: 50476959
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Rolle

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-17_

Sie können eine Verwaltungsrolle erstellen, die Verwaltungsrolleneinträge ändern, bei Bedarf einen Bereich hinzufügen und die Rolle anschließend einem Rollenempfänger zuweisen. Dieses Verfahren muss nur selten durchgeführt werden. Statt eine Verwaltungsrolle zu erstellen, empfiehlt es sich zu überprüfen, ob eine integrierte Verwaltungsrolle verwendet werden kann. Eine Liste mit integrierten Verwaltungsrollen finden Sie unter [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md).

Weitere Informationen zu Verwaltungsrollen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).


> [!NOTE]
> In diesem Thema wird die Erstellung einer Verwaltungsrolle ohne Bereich nicht behandelt. Informationen zum Erstellen einer Verwaltungsrolle ohne Bereich finden Sie unter <A href="create-an-unscoped-role-exchange-2013-help.md">Erstellen einer Rolle ohne Bereichseinschränkung</A>.



Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie hier: [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieses Verfahrens: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen der Verwaltungsrolle

Neue Verwaltungsrollen basieren auf vorhandenen Rollen. Wenn Sie eine Rolle erstellen, werden eine vorhandene Rolle und ihre Verwaltungsrolleneinträge in die neue Rolle kopiert. Die vorhandene Rolle wird zur übergeordneten Rolle der neuen untergeordneten Rolle. Sie müssen immer eine Rolle auswählen, die alle erforderlichen Cmdlets und Parameter enthält, und anschließend die nicht erforderlichen Elemente entfernen. Untergeordnete Rollen können keine Verwaltungsrolleneinträge enthalten, die in der übergeordneten Rolle nicht vorhanden sind.

Verwenden Sie die folgende Syntax, um eine neue Rolle zu erstellen.

    New-ManagementRole -Parent <existing role to copy> -Name <name of new role>

In diesem Beispiel werden die Rolle **E-Mail-Empfänger** und die zugehörigen Verwaltungsrolleneinträge in die Rolle "Seattle Mail Recipients" kopiert.

    New-ManagementRole -Parent "Mail Recipients" -Name "Seattle Mail Recipients"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRole](https://technet.microsoft.com/de-de/library/dd298073\(v=exchg.150\)).

## Schritt 2: Ändern der Verwaltungsrolleneinträge der neuen Rolle

Nachdem Sie die Rolle erstellt haben, müssen Sie die Einträge der Rolle ändern. Sie können einen ganzen Rolleneintrag löschen. Dadurch wird der Zugriff auf das zugehörige Cmdlet vollständig entfernt. Außerdem können Sie Parameter aus einem Rolleneintrag entfernen, um den Zugriff auf die jeweiligen Parameter im zugehörigen Cmdlet aufzuheben.

Sie können keine neuen Rolleneinträge oder Parameter für Rolleneinträge hinzufügen, wenn sie in der übergeordneten Rolle nicht enthalten sind. Da Sie gerade in Schritt 1 eine Rolle aus einer übergeordneten Rolle erstellt haben, können Sie keine weiteren Rolleneinträge oder Parameter für Rolleneinträge hinzufügen, da diese in der übergeordneten Rolle nicht vorhanden sind.

Wenn Sie einen Rolleneintrag für eine Rolle ändern, können Sie eine der folgenden Aktionen ausführen:

  - Einen einzelnen vollständigen Rolleneintrag entfernen.

  - Mehrere vollständige Rolleneinträge entfernen.

  - Parameter eines Rolleneintrags entfernen.

Informationen zum Entfernen von Rolleneinträgen aus der neuen Rolle finden Sie unter [Entfernen eines Rolleneintrags aus einer Rolle](remove-a-role-entry-from-a-role-exchange-2013-help.md).

## Schritt 3: Erstellen eines benutzerdefinierten Verwaltungsrollenbereichs, falls erforderlich

Durch Verwaltungsrollenbereiche werden die Objekte festgelegt, die einem Benutzer zur Ansicht oder zur Änderung mithilfe der in Schritt 2 konfigurierten Rolleneinträge zur Verfügung gestellt werden. Neue Verwaltungsrollen übernehmen die Lese- und Schreib-Verwaltungsrollenbereiche der übergeordneten Rolle. Diese werden als *implizite Bereiche* bezeichnet. Es gibt jedoch Fälle, in denen Sie den Schreibbereich der neuen Rolle auf die Anforderungen Ihres Unternehmens anpassen müssen. Wenn Sie einen benutzerdefinierten Bereich erstellen, setzen Sie den impliziten Schreibbereich der Rolle außer Kraft. Der implizite Lesebereich der Rolle ändert sich nicht. Weitere Informationen zu Verwaltungsrollenbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Sie können einen benutzerdefinierten Bereich oder einen exklusiven Bereich erstellen, einen vordefinierten Bereich verwenden oder einen Bereich für eine Zuweisung zu einer Organisationseinheit (Organizational Unit, OU) festlegen. Der neue Bereich muss innerhalb des impliziten Lesebereichs der Rolle liegen. Zum Verwenden eines vordefinierten Bereichs oder zum Angeben einer Organisationseinheit fahren Sie mit Schritt 4 fort.

Informationen zum Hinzufügen eines benutzerdefinierten Bereichs zur neuen Rolle finden Sie unter [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

## Schritt 4: Zuweisen der neuen Verwaltungsrolle

Der abschließende Schritt beim Erstellen und Konfigurieren einer Rolle ist deren Zuweisung an einen Rollenempfänger.

Beim Erstellen einer Rollenzuweisung stehen Ihnen folgende Möglichkeiten zur Auswahl:

  - Erstellen der Rollenzuweisung ohne Bereich.

  - Erstellen der Rollenzuweisung mit vordefiniertem Bereich.

  - Erstellen der Rollenzuweisung mit einer OU ohne Domäneneinschränkungsfilter.

  - Erstellen der Rollenzuweisung mit dem benutzerdefinierten oder exklusiven Bereich, den Sie in Schritt 3 erstellt haben.
    

    > [!NOTE]
    > Beim Erstellen einer Zuweisung zwischen einer Rolle und einer Verwaltungsrollen-Zuweisungsrichtlinie kann kein Bereich festgelegt werden.



Sie können die neue Rolle einer Rollengruppe, einer Rollenzuweisungsrichtlinie, einem Benutzer oder einer universellen Sicherheitsgruppe zuweisen. Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Verwalten von Rollenzuweisungsrichtlinien](manage-role-assignment-policies-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)


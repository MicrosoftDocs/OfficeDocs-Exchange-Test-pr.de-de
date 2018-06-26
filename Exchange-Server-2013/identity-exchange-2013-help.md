---
title: 'Identität: Exchange 2013 Help'
TOCTitle: Identität
ms:assetid: e90fae91-37e7-4fdc-9170-44f0dc965c66
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125042(v=EXCHG.150)
ms:contentKeyID: 50476978
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Identität

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-04_

Der Parameter *Identity* ist ein besonderer Parameter, den Sie mit den meisten Cmdlets verwenden können. Der Parameter *Identity* ermöglicht den Zugriff auf die eindeutigen Bezeichner, die auf ein bestimmtes Objekt in MicrosoftExchange Server 2013 verweisen. Auf diese Weise können Sie Aktionen für ein bestimmtes Exchange 2013-Objekt ausführen.

In den folgenden Abschnitten wird der Parameter Identity beschrieben. Ferner werden Beispiele für dessen effektive Verwendung genannt:

Characteristics of the Identity parameter

Wildcard characters in Identity

Examples of the Identity parameter

## Eigenschaften des Parameters "Identity"

Der primäre eindeutige Bezeichner eines Objekts in Exchange 2013 ist immer eine GUID. Eine GUID ist ein 128-Bit-Bezeichner, z. B. `63d64005-42c5-4f8f-b310-14f6cb125bf3`. Diese GUID wiederholt sich nie und ist daher immer eindeutig. Sie möchten jedoch solche GUIDs nicht regelmäßig eingeben. Aus diesem Grund besteht der Parameter *Identity* normalerweise außerdem aus den Werten anderer Parameter oder aus einer kombinierten Sammlung von Werten aus mehreren Parametern für ein einzelnes Objekt. Die Eindeutigkeit dieser Werte innerhalb der betreffenden Objektsammlung ist ebenfalls gewährleistet. Die Werte dieser anderen Parameter können entweder angegeben werden, z. B. *Name* und *DistriguishedName*, oder sie können vom System generiert werden. Die zusätzlichen Parameter, die ggf. verwendet werden, sowie die Art ihrer Auffüllung mit Werten hängen von dem Objekt ab, auf das Sie verweisen.

Der Parameter *Identity* ist außerdem ein Positionsparameter. Wenn keine Parameterbezeichnung eingegeben wird, wird davon ausgegangen, dass das erste Argument für ein Cmdlet der Parameter *Identity* ist. Auf diese Weise wird die Anzahl der Tastatureingaben beim Eingeben von Befehlen verringert. Weitere Informationen zu Positionsparametern finden Sie unter [Parameter](https://technet.microsoft.com/de-de/library/bb124388\(v=exchg.150\)).

Das folgende Beispiel zeigt die Verwendung des Parameters *Identity* unter Verwendung des eindeutigen Parameterwerts *Name* des Empfangsconnectors. Das Beispiel zeigt außerdem, wie der Parametername *Identity* ausgelassen werden kann, weil *Identity* ein Positionsparameter ist.

    Get-ReceiveConnector -Identity "From the Internet"
    Get-ReceiveConnector "From the Internet"

Wie auf alle Objekte in Exchange 2013 kann auf diesen Empfangsconnector auch durch seine eindeutige GUID verwiesen werden. Wenn dem Empfangsconnector namens `"From the Internet"` auch die GUID `63d64005-42c5-4f8f-b310-14f6cb125bf3` zugewiesen wurde, können Sie den Empfangsconnector z. B. auch über den folgenden Befehl abrufen:

    Get-ReceiveConnector 63d64005-42c5-4f8f-b310-14f6cb125bf3

Zurück zum Seitenanfang

## Platzhalterzeichen in "Identity"

Einige **Get**-Cmdlets akzeptieren ein Platzhalterzeichen (`*`) als Bestandteil des Werts, den Sie beim Ausführen des Cmdlets an *Identity* übergeben. Durch Verwendung eines Platzhalters mit dem Parameter *Identity* können Sie einen Teil eines Namens angeben und eine Liste von Objekten abrufen, die diesem Teilnamen entsprechen. Ein Platzhalterzeichen kann am Anfang oder am Ende des *Identity*-Werts platziert werden, jedoch nicht in der Mitte einer Zeichenfolge. Gültige Befehle sind zum Beispiel `Get-Mailbox David*` und `Get-Mailbox *anders*`. Der Befehl `Get-Mailbox Reb*ca` ist jedoch ungültig.

Einige Cmdlets vom Typ **Get** rufen Objekte in Exchange 2013 ab, die hierarchisch oder in Beziehungen aus übergeordneten und untergeordneten Objekten strukturiert sind. Das heißt, es kann eine Sammlung an übergeordneten Objekten geben, die auch ihre eigenen untergeordneten Objekte enthalten. Objekte in einer Beziehung aus über- und untergeordneten Objekten können einen Parameter *Identity* mit der Syntax `<parent>\<child>` erhalten.

Bei einem Parameter *Identity* mit der Syntax `<parent>\<child>` ermöglichen Ihnen manche Cmdlets die Verwendung eines Platzhalterzeichens (\*), um alle oder einen Teil der Namen über- oder untergeordneter Objekte zu ersetzen. Wenn Sie beispielsweise alle untergeordneten Objekte namens "Contoso" in allen übergeordneten Objekten finden möchten, könnten Sie die Syntax `"*\Contoso"` verwenden. Wenn Sie alle untergeordneten Objekte mit dem Teilnamen "Auth" finden möchten, die unter dem übergeordneten Objekt `"ServerA" ` vorhanden sind, könnten Sie entsprechend die Syntax `"ServerA\Auth*"` verwenden.

Einige, wenn auch nicht alle, Cmdlets ermöglichen Ihnen bei der Ausführung eines Befehls die Angabe nur des untergeordneten Teils des Identity-Parameters. In diesem Fall setzen die Cmdlets das derzeit verwendete übergeordnete Objekt ein. Beispielsweise gibt es sowohl auf "MBX1" als auch auf "MBX2" einen Empfangsconnector namens "Contoso Receive Connector". Wenn Sie den Befehl `Get-ReceiveConnector "Contoso Receive Connector"` auf "MBX2" ausführen, wird nur der Empfangsconnector auf dem Server "MBX2" zurückgegeben.

Das jeweilige Verhalten des Parameters Identity und der Platzhalterzeichen hängt von dem ausgeführten Cmdlet ab. Weitere Informationen über das ausgeführte Cmdlet finden Sie im featurespezifischen Inhalt für das betreffende Cmdlet.

Zurück zum Seitenanfang

## Beispiele für den Parameter "Identity"

Die in diesem Thema beschriebenen Beispiele zeigen, wie der Parameter *Identity* verschiedene eindeutige Werte annehmen kann, um auf bestimmte Objekte in der Exchange 2013-Organisation zu verweisen. Diese Beispiele zeigen auch, wie die Parameterbezeichnung *Identity* ausgelassen werden kann, um die Anzahl der Tastatureingaben beim Eingeben von Befehlen zu verringern.

## DSN-Nachrichten

Die Beispiele in diesem Abschnitt beziehen sich auf die Benachrichtigungen über den Übermittlungsstatus (Delivery Status Notification, DSN), die in einer Exchange 2013-Organisation konfiguriert werden können. Das erste Beispiel zeigt, wie DSN 5.4.1 mithilfe des Cmdlets **Get-SystemMessage** abgerufen werden kann. Im Cmdlet **Get-SystemMessage** besteht der Parameter *Identity* aus mehreren Datenelementen, die für jedes DSN-Nachrichtenobjekt konfiguriert sind. Diese Datenelemente umfassen die Sprache, in denen die Benachrichtigung geschrieben ist, ob der Bereich der Benachrichtigung intern oder extern ist, und den DSN-Nachrichtencode, wie im folgenden Beispiel gezeigt wird:

    Get-SystemMessage en\internal\5.4.1

Sie können diese DSN-Nachricht auch mithilfe ihrer GUID abrufen, wie das folgende Beispiel zeigt, weil alle Objekte in Exchange 2013 eine GUID besitzen:

    Get-SystemMessage 82ca7bde-1c2d-4aa1-97e1-f298a6f10222

Weitere Informationen zum Parameter *Identity* und seine Verwendung mit den **SystemMessage**-Cmdlets finden Sie unter [DSN-Nachrichtenidentität](dsn-message-identity-exchange-2013-help.md).

## Verwaltungsrolleneinträge

Die Beispiele in diesem Abschnitt beziehen sich auf Verwaltungsrolleneinträge, aus denen die Verwaltungsrollen in Exchange 2013 zusammengesetzt sind. Anhand von Verwaltungsrollen werden die Berechtigungen gesteuert, die Administratoren und Endbenutzern erteilt werden. Verwaltungsrolleneinträge bestehen aus zwei Teilen: der Verwaltungsrolle, der sie zugeordnet sind, und einem Cmdlet. Der Parameter Identity besteht ebenfalls sowohl aus dem Verwaltungsrollennamen als auch aus dem Namen des Cmdlets. Im Folgenden wird beispielsweise der Rolleneintrag für das Cmdlet **Set-Mailbox** für die Rolle `Mail Recipients` gezeigt:

    Mail Recipients\Set-Mailbox

Der Rolleneintrag `Mail Recipients\Set-Mailbox` ist einer von mehreren hundert Einträgen für die Rolle `Mail Recipients`. Um alle Rolleneinträge für die Rolle `Mail Recipients` anzuzeigen, verwenden Sie den folgenden Befehl:

    Get-ManagementRoleEntry "Mail Recipients\*"

Um alle Rolleneinträge für die Rolle `Mail Recipients` anzuzeigen, die die Zeichenfolge "`Mailbox`" enthalten, verwenden Sie den folgenden Befehl:

    Get-ManagementRoleEntry "Mail Recipients\*Mailbox*"

Um alle Verwaltungsrollen anzeigen, die den Rolleneintrag **Set-Mailbox** enthalten, verwenden Sie den folgenden Befehl:

    Get-ManagementRoleEntry *\Set-Mailbox

Mit Rolleneinträgen können Sie das Platzhalterzeichen vielfältig einsetzen, um die für Sie relevanten Informationen aus Exchange 2013 abzurufen.

Weitere Informationen zu Verwaltungsrollen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Zurück zum Seitenanfang


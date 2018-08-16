---
title: 'Verwaltung von Exchange-Arbeitsauslastungen: Exchange 2013 Help'
TOCTitle: Verwaltung von Exchange-Arbeitsauslastungen
ms:assetid: 276740c4-bdb7-49f1-9470-ae6f2bfd65aa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150503(v=EXCHG.150)
ms:contentKeyID: 50475374
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwaltung von Exchange-Arbeitsauslastungen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-11-16_

Bei Exchange-Arbeitsauslastungen handelt es sich um Exchange Server-Funktionen, -Protokolle oder -Dienste, die explizit zum Zweck der Exchange-Systemressourcenverwaltung definiert wurden. Jede Exchange-Arbeitsauslastung nutzt Systemressourcen (z. B. CPU, Vorgänge der Postfachdatenbank oder Active Directory-Anforderungen), um Benutzeranforderungen oder Hintergrundaufgaben auszuführen. Beispiele für Exchange-Arbeitsauslastungen sind Outlook Web App, Exchange ActiveSync, Postfachmigrationen und Postfach-Assistenten.

Sie können Exchange-Arbeitsauslastungen verwalten, indem Sie steuern, wie Ressourcen von einzelnen Benutzern genutzt werden (dies wird in Exchange 2010 manchmal Benutzereinschränkung genannt). Das Festlegen, wie Exchange-Systemressourcen von einzelnen Benutzern verwendet werden, war bereits in Exchange Server 2010 möglich. Diese Funktion wurde für Exchange Server 2013 erweitert.


> [!NOTE]
> Die Verwaltung von Arbeitsbelastungen durch Überwachung des Status von Systemressourcen auf den Exchange-Servern in Ihrer Organisation sollte nur unter der Anleitung des Microsoft-Kundendienstes und -Supports erfolgen.



## Verwalten von Arbeitsauslastungen durch Festlegen, wie Ressourcen von einzelnen Benutzern verwendet werden

Die Funktionalität für Einschränkungen wurde in Exchange 2013 erweitert. Mit diesen Erweiterungen wird sichergestellt, dass eine übermäßige Ressourcenverwendung durch einzelne Benutzer die Serverleistung oder die Benutzerfreundlichkeit nicht beeinträchtigt.

Mithilfe der Benutzereinschränkung in Exchange 2013 können Benutzer die Ressourcenverwendung für kurze Zeiträume erhöhen, ohne dass sich dabei die Bandbreite reduziert. Außerdem wird für Benutzer, die eine äußerst große Ressourcenmenge verwenden, selten oder nie eine vollständige Sperrung vorgenommen. Anstatt einen Benutzer vollständig daran zu hindern, Vorgänge auszuführen, wird eine Einschränkung vorgenommen, sodass Vorgänge für kurze Zeiträume verzögert werden (Sie können sich diese Verzögerungen als „Mikroverzögerungen“ vorstellen). Diese Maßnahmen werden ergriffen, bevor die Serverleistung in erheblichem Maße beeinträchtigt wird.

**Besondere Funktionsmerkmale**

Im Folgenden wird hervorgehoben, wie Exchange die Ressourcenverwendung durch einzelne Benutzer in Exchange 2013 steuert:

  - **Burststeigerung**   Durch Burststeigerungen können Benutzer die Ressourcenverwendung für eine kurze Zeitdauer erhöhen, ohne dass eine Einschränkung vorgenommen wird.

  - **Regenerationsrate**   Über die Regenerationsrate wird die Ressourcenverwendung Ihrer Benutzer mithilfe eines Ressourcenbudgetsystems verwaltet. Sie können die Rate festlegen, bei der die Ressourcenbudgets Ihrer Benutzer erneut gefüllt werden. Ein Wert von 600.000 Millisekunden gibt z. B. an, dass die Budgets der Benutzer bei einer Nutzungsrate von zehn Minuten pro Stunde erneut mit einem gefüllt werden.

  - **Traffic-Shaping**   Wenn die Ressourcenverwendung eines Benutzers den konfigurierten Grenzwert für eine längere Zeitdauer erreicht, treten für den Benutzer rechtzeitig für kurze Zeiträume Verzögerungen auf, um eine signifikante Leistungsbeeinträchtigung für den Server zu verhindern. Diese „Mikroverzögerungen“ sind für Benutzer üblicherweise nicht bemerkbar. Durch diesen Vorgang kann Exchange 2013 ein effizientes Traffic-Shaping durchführen, ohne die Benutzer daran zu hindern, produktiv zu sein. Traffic-Shaping hat weniger Auswirkungen auf Ihre Benutzer als eine frühzeitige Sperrung und senkt das Risiko einer Sperrung deutlich.

  - **Maximale Verwendung**   In seltenen Fällen verwendet ein Benutzer für einen kurzen Zeitraum möglicherweise eine äußerst große Menge an Ressourcen. Als Vorsichtsmaßnahme kann ein Benutzer, der einen Schwellenwert für die maximale Verwendung erreicht, vorübergehend gesperrt und an der Verwendung von Ressourcen gehindert werden. Die Sperrung von Benutzern, die vorübergehend an der Verwendung von Ressourcen gehindert werden, wird aufgehoben, sobald die Budgets der Benutzer erneut gefüllt sind.

Eine Liste der Cmdlets zum Festlegen, wie Ressourcen von einzelnen Benutzern verwendet werden, finden Sie unter "Cmdlets zum Festlegen, wie Ressourcen von einzelnen Benutzern verwendet werden" weiter unten in diesem Thema.

**Überlegungen zur Einschränkungsfunktionalität und Bereitstellung von Exchange 2013**

Unabhängig davon, ob Sie eine Neuinstallation von Exchange 2013 durchführen oder Exchange 2013 in einer Koexistenzumgebung mit Exchange 2010-Computern installieren, wird die neue Einschränkungsfunktionalität aus Exchange 2013 für alle Benutzer mit Postfächern auf Computern angewendet, auf denen Exchange 2013 ausgeführt wird. Für Exchange 2010-Postfächer werden jedoch die Einschränkungen der Exchange 2010-Einschränkungsfunktionalität angewendet, wenn die Benutzer über Exchange 2010-Clientzugriffsserver auf ihre Postfächer zugreifen.

Bei der Installation von Exchange 2013 in einer Koexistenzumgebung versucht der Exchange 2013-Installationsvorgang möglicherweise, einige Einschränkungseinstellungen aus der Exchange 2010-Konfiguration zu übernehmen. Die Exchange 2013-Einschränkungsfunktionalität unterscheidet sich jedoch so grundlegend, dass ältere Einschränkungseinstellungen im Allgemeinen keine Auswirkungen auf die Funktionsweise von Einschränkungen in Exchange 2013 haben.

**Verwalten von Einschränkungsrichtlinien mithilfe von Bereichen**

Vergleichbar mit Exchange 2010 gibt es in Exchange 2013 eine einzige Standardeinschränkungsrichtlinie. In Exchange 2013 lautet der Name der Standardeinschränkungsrichtlinie **GlobalThrottlingPolicy**. Dieser Richtlinie ist der Bereich **Global** zugewiesen. Zusätzlich sind für Benutzereinschränkungen die Bereiche **Organization** und **Regular** verfügbar. Aufgrund der Einführung von Bereichszuweisungen für Exchange 2013-Benutzereinschränkungsrichtlinien werden Einschränkungsrichtlinien nun auf andere Weise verwaltet als in Exchange 2010. Über **GlobalThrottlingPolicy** werden die grundsätzlichen Standardeinschränkungseinstellungen für alle neuen und vorhandenen Benutzer in Ihrer Organisation definiert, sofern Sie nicht über angepasste Einschränkungsrichtlinien für Ihre Organisation verfügen. In vielen typischen Exchange-Bereitstellungsszenarien ist **GlobalThrottlingPolicy** für die Verwaltung Ihrer Benutzer geeignet.

Es wird dringend davon abgeraten, **GlobalThrottlingPolicy** zu ändern, um Einschränkungseinstellungen anzupassen. Erstellen Sie stattdessen zusätzliche Einschränkungsrichtlinien. Durch das Erstellen zusätzlicher Einschränkungsrichtlinien lassen sich Ihre Arbeitsauslastungen besser verwalten. Darüber hinaus wird verhindert, dass Änderungen an den Einschränkungsrichtlinieneinstellungen durch zukünftige Exchange 2013-Updates überschrieben werden.

Wenn Sie die Einschränkungseinstellungen für alle Benutzer in Ihrer Organisation anpassen möchten, erstellen Sie eine neue Einschränkungsrichtlinie mit der Bereichszuweisung **Organization**. In neuen Richtlinien mit dem Bereich "Organization" sollten lediglich die Einschränkungseinstellungen festgelegt werden, die nicht mit **GlobalThrottlingPolicy** identisch sind. Wenn Sie die Einschränkungseinstellungen für spezifische Benutzer in Ihrer Organisation anpassen möchten, erstellen Sie eine neue Einschränkungsrichtlinie mit der Bereichszuweisung **Regular**. In neuen Richtlinien mit dem Bereich "Regular" sollten lediglich die Einschränkungseinstellungen festgelegt werden, die nicht mit **GlobalThrottlingPolicy** und anderen Organisationsrichtlinien identisch sind. So können die übrigen Richtlinieneinstellungen von **GlobalThrottlingPolicy** geerbt werden, und Sie profitieren von Aktualisierungen an den Einschränkungsrichtlinien, die in zukünftigen Exchange-Updates hinzugefügt werden.

## Verwalten von Einschränkungseinstellungen für Arbeitsauslastungen

Einschränkungseinstellungen für Arbeitsauslastungen werden mithilfe der Exchange-Verwaltungsshell verwaltet.

**Cmdlets zum Festlegen, wie Ressourcen von einzelnen Benutzern verwendet werden**

Einschränkungseinstellungen werden mit den folgenden Cmdlets verwaltet, die in Exchange 2010 eingeführt wurden:

Verwalten von Einschränkungsrichtlinien

  - [Get-ThrottlingPolicy](https://technet.microsoft.com/de-de/library/dd351264\(v=exchg.150\))

  - [New-ThrottlingPolicy](https://technet.microsoft.com/de-de/library/dd351045\(v=exchg.150\))

  - [Remove-ThrottlingPolicy](https://technet.microsoft.com/de-de/library/dd351178\(v=exchg.150\))

  - [Set-ThrottlingPolicy](https://technet.microsoft.com/de-de/library/dd298094\(v=exchg.150\))

Zuweisen von Einschränkungsrichtlinien

  - [Get-ThrottlingPolicyAssociation](https://technet.microsoft.com/de-de/library/ff459241\(v=exchg.150\))

  - [Set-ThrottlingPolicyAssociation](https://technet.microsoft.com/de-de/library/ff459231\(v=exchg.150\))


> [!NOTE]
> Die Cmdlets <STRONG>&#42;-ResourcePolicy</STRONG>, <STRONG>&#42;-WorkloadManagementPolicy</STRONG> and <STRONG>&#42;-WorkloadPolicy</STRONG> zur Verwaltung der Systemauslastung sind veraltet. Einstellungen zur Verwaltung der Systemauslastung sollten nur unter Anleitung des Microsoft-Kundendiensts und -Supports angepasst werden.



---
title: 'Optionen "WhatIf", "Confirm" und "ValidateOnly": Exchange 2013 Help'
TOCTitle: Optionen "WhatIf", "Confirm" und "ValidateOnly"
ms:assetid: a850eea7-431e-49c5-b877-1ebde2a2b48f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124088(v=EXCHG.150)
ms:contentKeyID: 50476428
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Optionen \"WhatIf\", \"Confirm\" und \"ValidateOnly\"

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-04_

Sowohl für erfahrene Administratoren und Skriptschreiber als auch für Administratoren, die sich erstmals mit Exchange und der Skripterstellung befassen, können die Optionen *WhatIf*, *Confirm* und *ValidateOnly* von Nutzen sein. Mit ihrer Hilfe können Sie die Ausführung von Befehlen steuern und exakt anzeigen, welches Ergebnis ein Befehl liefert, bevor dieser auf Daten angewendet wird. Diese Funktionalität ist besonders wichtig beim Wechsel von der Testumgebung zur Produktionsumgebung und beim Bereitstellen neuer Skripts oder Befehle.

Die Optionen *WhatIf*, *Confirm* und *ValidateOnly* sind besonders nützlich, wenn Sie sie mit Befehlen zur Änderung von Objekten verwenden, die über einen Filter oder den Befehl **Get** in einer Pipeline zurückgegeben werden. In diesem Thema werden die einzelnen Parameter beschrieben und Beispielbefehle bereitgestellt.


> [!IMPORTANT]
> Wenn Sie die Optionen <EM>WhatIf</EM>, <EM>Confirm</EM> und <EM>ValidateOnly</EM> mit Befehlen in einem Skript verwenden, müssen Sie die entsprechenden Optionen jedem einzelnen Befehl im Skript hinzufügen und nicht der Befehlszeile, die dieses Skript aufruft.




> [!NOTE]
> <EM>WhatIf</EM>, <EM>Confirm</EM> und <EM>ValidateOnly</EM> werden als Optionsparameter bezeichnet. Weitere Informationen zu Schalterparametern finden Sie unter <A href="https://technet.microsoft.com/de-de/library/bb124388(v=exchg.150)">Parameter</A>.



## Option "WhatIf"

Die Option *WhatIf* weist den jeweiligen Befehl an, die Objekte, auf die sich der Befehl bei Ausführung auswirkt, sowie die an diesen Objekten durchgeführten Änderungen nur anzuzeigen. Der Parameter ändert diese Objekte nicht wirklich. Wenn Sie die Option *WhatIf* verwenden, können Sie sehen, ob die Änderungen Ihren Erwartungen entsprechen, ohne diese Objekte wirklich zu ändern.

Wenn Sie einen Befehl mit dem Parameter *WhatIf* ausführen, fügen Sie den Parameter *WhatIf* am Ende des Befehls ein, wie in folgendem Beispiel gezeigt:

    New-AcceptedDomain -Name "Contoso Domain" -DomainName "contoso.com" -WhatIf 

Wenn Sie diesen Beispielbefehl ausführen, wird der folgende Text von der Shell zurückgegeben:

    What if: Creating Accepted Domain "Contoso Domain" with domain name "contoso.com".

## Option "Confirm"

Die Option *Confirm* weist den jeweiligen Befehl an, die Verarbeitung anzuhalten, bevor Änderungen durchgeführt werden. Danach werden Sie aufgefordert, die einzelnen Aktionen zu bestätigen, bevor die Verarbeitung fortgesetzt wird. Wenn Sie die Option *Confirm* verwenden, können Sie die Änderungen an Objekten Schritt für Schritt durchlaufen um sicherzustellen, dass nur Änderungen an den gewünschten Objekten durchgeführt werden. Diese Funktion ist hilfreich, wenn Sie viele Objekte ändern und eine präzise Kontrolle über die Operation der Shell wünschen. Es wird eine Bestätigungsaufforderung zu jedem einzelnen Objekt angezeigt, bevor dieses von der Shell geändert wird.

Standardmäßig wendet die Shell die Option *Confirm* automatisch auf Cmdlets mit folgenden Verben an:

  - **Clear**

  - **Disable**

  - **Dismount**

  - **Move**

  - **Remove**

  - **Stop**

  - **Suspend**

  - **Uninstall**

Wenn ein Cmdlet ausgeführt wird, das eines dieser Verben enthält, hält die Shell den Befehl automatisch an und wartet auf eine Bestätigung zum Fortsetzen des Prozesses.

Wenn Sie die Option *Confirm* manuell auf einen Befehl anwenden möchten, fügen Sie die Option *Confirm*, wie in folgendem Beispiel gezeigt, am Ende des Befehls ein:

    Get-JournalRule | Enable-JournalRule -Confirm

Wenn Sie diesen Beispielbefehl ausführen, wird die folgende Bestätigungsaufforderung von der Shell zurückgegeben:

    Confirm
    Are you sure you want to perform this action?
    Enabling journal rule "Litigation Journal Rule".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
    (default is "Y"):

Die Bestätigungsaufforderung bietet folgende Auswahlmöglichkeiten:

  - **\[Y\] Yes**   Geben Sie **Y** ein, um den Vorgang fortzusetzen. Der nächste Vorgang zeigt eine weitere Bestätigungsaufforderung an. `[Y] Yes` ist standardmäßig ausgewählt.

  - **\[A\] Yes to All**   Geben Sie **A** ein, wenn der Befehl diesen und alle folgenden Vorgänge fortsetzen soll. Während der Ausführung dieses Befehls werden keinen weiteren Bestätigungsaufforderungen angezeigt.

  - **\[N\] No**   Geben Sie **N** ein, wenn der Befehl diesen Vorgang auslassen und mit dem nächsten Vorgang fortfahren soll. Beim nächsten Vorgang wird eine weitere Bestätigungsaufforderung angezeigt.

  - **\[L\] No to All**   Geben Sie **L** ein, wenn der Befehl diesen und alle folgenden Vorgänge auslassen soll.

  - **\[S\] Suspend**   Geben Sie **S** ein, um die aktuelle Pipeline anzuhalten und in die Befehlszeile zurückzuwechseln. Geben Sie **Exit** ein, um die Pipeline fortzusetzen.

  - **\[?\] Help**   Geben Sie **?** ein, um Hilfeinformationen zur Bestätigungsaufforderung in der Befehlszeile anzuzeigen.

Wenn Sie das Standardverhalten der Shell außer Kraft setzen und die Bestätigungsaufforderung für Cmdlets mit diesem Verhalten unterdrücken möchten, können Sie die Option *Confirm* mit dem Wert `$False` eingeben, wie in folgendem Beispiel gezeigt:

    Get-JournalRule | Disable-JournalRule -Confirm:$False

In diesem Fall wird keine Bestätigungsaufforderung angezeigt.


> [!WARNING]
> Der Standardwert für die Option <EM>Confirm</EM> lautet <CODE>$True</CODE>. Die Shell zeigt standardmäßig automatisch eine Bestätigungsaufforderung an. Wenn Sie dieses Standardverhalten unterdrücken, weisen Sie den Befehl an, alle Bestätigungsaufforderungen für die Dauer des Befehls zu unterdrücken. Der Befehl verarbeitet alle Objekte, die den Befehlskriterien entsprechen, ohne Bestätigung.



## Option "ValidateOnly"

Die Option *ValidateOnly* weist den Befehl an, alle zur Ausführung des Befehls erforderlichen Bedingungen und Anforderungen vor einer Änderung zu überprüfen. Die Option *ValidateOnly* steht für Cmdlets zur Verfügung, deren Ausführung lange dauern kann, die mehrere Abhängigkeiten in verschiedenen Systemen beinhalten oder die sich auf wichtige Daten wie Postfächer auswirken.

Wenn Sie die Option *ValidateOnly* auf einen Befehl anwenden, führt dieser den gesamten Prozess aus. Der Befehl führt die einzelnen Aktionen auf die gleiche Weise aus, wie er sie ohne die Option *ValidateOnly* ausführen würde. Er ändert dabei jedoch keines der Objekte. Wenn der Befehl den Prozess abschließt, zeigt er eine Zusammenfassung mit dem Ergebnis der Überprüfung an. Ergibt die Überprüfung, dass der Befehl erfolgreich war, können Sie den Befehl erneut ohne die Option *ValidateOnly* ausführen.

Wenn Sie einen Befehl mit der Option *ValidateOnly* ausführen, fügen Sie die Option *ValidateOnly* am Ende des Befehls ein.


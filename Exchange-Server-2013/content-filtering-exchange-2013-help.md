---
title: 'Inhaltsfilterung: Exchange 2013 Help'
TOCTitle: Inhaltsfilterung
ms:assetid: d660ffbf-de05-46c2-940b-5200eca94e0a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124739(v=EXCHG.150)
ms:contentKeyID: 50476811
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Inhaltsfilterung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_


> [!NOTE]
> Am 1. November 2016 hat Microsoft die Generierung von Spamdefinitionsupdates für die SmartScreen-Filter in Exchange und Outlook eingestellt. Die vorhandenen SmartScreen-Spamdefinitionen bleiben bestehen, ihre Effektivität wird aber im Laufe der Zeit wahrscheinlich abnehmen. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=835894">Deprecating support for SmartScreen in Outlook and Exchange</A>.



Inhaltsfilter-Agent wertet eingehende e-Mail-Nachrichten und die Wahrscheinlichkeit, dass eine eingehende Nachricht legitime ist oder Spam bewertet. Im Gegensatz zu vielen anderen Filtern Technologien wird der Inhaltsfilter-Agent Merkmale aus einer Stichprobe Signifikanz von e-Mail-Nachrichten verwendet. Die Aufnahme der legitime Nachrichten in diesem Beispiel wird die Wahrscheinlichkeit von Fehlern verringert. Da der Inhaltsfilter-Agent Merkmale von legitimen e-Mails und Spam erkannt wird, wird seine Genauigkeit erhöht. Updates für den Inhaltsfilter-Agent sind in regelmäßigen Abständen über [Microsoft Update](https://go.microsoft.com/fwlink/p/?linkid=54836)verfügbar.

**Inhalt**

Using the Content Filter agent

Configuring the Content Filter agent

## Verwenden des Inhaltsfilter-Agents

Der Inhaltsfilter-Agent ist einer von mehreren Antispam-Agents in Exchange. Beim Konfigurieren von Antispam-Agents auf einem Exchange-Server bearbeitet der Agent Nachrichten kumulativ, um die Menge von Spam zu verringern, die in die Organisation gelangt. Weitere Informationen zum Planen und Bereitstellen von Agents zur Bekämpfung von Spam finden Sie unter [Antispamschutz](anti-spam-protection-exchange-2013-help.md).

Der Inhaltsfilter-Agent weist jeder Nachricht eine SCL-Bewertung (Spam Confidence Level zu. Die SCL-Bewertung ist eine Zahl von 0 bis 9. Eine höhere SCL-Bewertung zeigt an, dass es sich bei einer Nachricht mit größerer Wahrscheinlichkeit um Spam handelt.

Sie können den Inhaltsfilter-Agent so konfigurieren, dass abhängig von der SCL-Bewertung die folgenden Aktionen auf Nachrichten angewendet werden:

  - Nachricht löschen

  - Nachricht zurückweisen

  - Nachricht in Quarantäneverzeichnis verschieben

Sie können beispielsweise festlegen, dass Nachrichten mit der SCL-Bewertung 7 oder höher gelöscht, mit der SCL-Bewertung 6 zurückgewiesen und mit der SCL-Bewertung 5 in ein Quarantäneverzeichnis verschoben werden müssen.

Sie können den SCL-Schwellenwert anpassen, indem Sie diesen Aktionen andere SCL-Bewertungen zuweisen. Weitere Informationen zum Anpassen des SCL-Schwellenwerts an die Anforderungen Ihrer Organisation und zu empfängerbezogenen SCL-Schwellenwerten finden Sie unter [SCL-Schwellenwert](spam-confidence-level-threshold-exchange-2013-help.md).


> [!NOTE]
> Nachrichten von über 11 MB werden vom intelligenten Nachrichtenfilter nicht gescannt. Vielmehr werden sie ohne Durchsuchung durch den Inhaltsfilter übergeben.



## Zulassen und Sperren von Ausdrücken

Durch Konfigurieren von benutzerdefinierten Wörtern können Sie anpassen, wie der Inhaltsfilter-Agent SCL-Werte zuweist. Benutzerdefinierte Wörter sind einzelne Wörter oder Ausdrücke, die der Inhaltsfilter-Agent zum Anwenden der geeigneten Filterverarbeitung verwendet. Über das Zulassen von Ausdrücken können Sie erlaubte Wörter oder Ausdrücke bestimmen. Über das Blocken von Ausdrücken werden nicht zugelassene Wörter oder Ausdrücke festgelegt. Wenn der Inhaltsfilter-Agent in einer eingehenden Nachricht einen vorkonfigurierten zugelassenen Ausdruck erkennt, weist der Agent der Nachricht automatisch den SCL-Wert 0 zu. Wenn der Inhaltsfilter-Agent dagegen in einer eingehenden Nachricht einen vorkonfigurierten geblockten Ausdruck erkennt, weist der Agent der Nachricht den SCL-Wert 9 zu.

Benuzerdefinierte Wörter und Ausdrücke können in jeder beliebigen Kombination von Groß- und Kleinbuchstaben eingegeben werden. Bei der Auswertung von Nachrichteninhalten ignoriert der Inhaltsfilter-Agent die Groß-/Kleinschreibung. Es können maximal 800 benutzerdefinierte Wörter und Ausdrücke erstellt werden.

## Outlook-E-Mail-Poststempelüberprüfung

Der Inhaltsfilter-Agent umfasst außerdem die Outlook-E-Mail-Poststempelüberprüfung, ein rechnerischer Nachweis, den Outlook auf ausgehende Nachrichten anwendet, damit Empfängermessagingsysteme zulässige Nachrichten von Junk-E-Mails unterscheiden können. Diese Funktion reduziert die Wahrscheinlichkeit falsch positiver Ergebnisse. Bei der Spamfilterung liegt ein *falsch positives Ergebnis* vor, wenn ein Spamfilter eine Nachricht von einem erwünschten Absender fälschlicherweise als Spam identifiziert. Wenn die Outlook-E-Mail-Poststempelüberprüfung aktiviert ist, überprüft der Inhaltsfilter-Agent die eingehende Nachricht auf eine Kopfzeile mit einem Rechenpoststempel. Das Vorhandensein einer Kopfzeile mit einem gültigen, gelösten Rechenpoststempel in der Nachricht gibt an, dass der Clientcomputer, der die Nachricht generiert hat, den Rechenpoststempel aufgelöst hat.

Computer benötigen nicht viel Verarbeitungszeit zum Lösen einzelner Rechenpoststempel. Doch die Verarbeitung von Rechenpoststempeln in vielen Nachrichten kann sich für Spamabsender als sehr aufwendig erweisen. Absender, die Millionen von Spam-E-Mails senden, investieren voraussichtlich nicht in die Verarbeitungskapazität, die für die Lösung von Rechenpoststempeln für alle ausgehenden Spam-E-Mails benötigt wird. Wenn die E-Mail des Absenders einen gültigen, gelösten Rechenpoststempel enthält, ist es unwahrscheinlich, dass der Absender ein Spammer ist. In diesem Fall senkt der Inhaltsfilter-Agent die SCL-Bewertung. Wenn die Funktion zur Poststempelüberprüfung aktiviert ist und eine eingehende Nachricht entweder keine oder eine ungültige Kopfzeile mit einem Rechenpoststempel enthält, ändert der Inhaltsfilter-Agent die SCL-Bewertung nicht.

## Umgehen des Empfängers, Absenders und der Absenderdomäne

In einigen Organisationen müssen alle E-Mails an bestimmte Aliase akzeptiert werden. Dieses Szenario kann zu Problemen führen, wenn Ihre Organisation in einer Branche tätig ist, in der das Spamvolumen beträchtlich ist.

Angenommen, ein Unternehmen mit dem Namen Woodgrove Bank hat den Alias "customerloans@woodgrovebank.com", der externen Kreditnehmern einen E-Mail-Support bietet. Die Exchange-Administratoren konfigurieren den Inhaltsfilter-Agent für die Festlegung gesperrter Ausdrücke, mit denen Wörter oder Ausdrücke herausgefiltert werden, die typisch für Spam-E-Mails sind, die von skrupellosen Kreditvermittlungsagenturen versendet werden. Um das Zurückweisen möglicherweise erwünschter Nachrichten zu verhindern, legen die Administratoren Ausnahmen für die Inhaltsfilterung fest, indem in die Konfiguration des Inhaltsfilter-Agents eine Liste mit SMTP-E-Mail-Empfängeradressen eingegeben wird.

Sie können auch Absender und Domänen von Absendern angeben, die der Inhaltsfilter-Agent nicht blocken soll.

## Aggregation von Listen sicherer Adressen

In Exchange 2013 verwendet der Inhaltsfilter-Agent die Liste der sicheren Absender, die Liste der blockierten Absender und die Liste der sicheren Empfänger von Outlook sowie vertrauenswürdige Kontakte aus Outlook, um die Spamfilterung zu optimieren. Die *Aggregation von Listen sicherer Adressen* ist eine Zusammenstellung von Antispamfunktionen, die von Outlook und Exchange genutzt wird. Wie der Name schon sagt, erfasst diese Funktion Daten aus den Listen sicherer Adressen zur Abwehr von Spam, die von Outlook-Benutzern konfiguriert werden, und stellt diese den Antispam-Agents auf dem Exchange-Server zur Verfügung. E-Mails, die Outlook-Benutzer von Kontakten erhalten, die diese Benutzer ihrer Liste der sicheren Empfänger, ihrer Liste der sicheren Absender von Outlook oder ihrer Liste der vertrauenswürdigen Kontakte hinzugefügt haben, werden vom Inhaltsfilter-Agent als sicher eingestuft. Der Absenderfilter-Agent führt außerdem eine Filterung nach Empfängern über die von Benutzern konfigurierte Liste blockierter Empfänger durch. Weitere Informationen finden Sie unter [Aggregation von Listen sicherer Adressen](safelist-aggregation-exchange-2013-help.md).

## Konfigurieren des Inhaltsfilter-Agents

Sie konfigurieren den Inhaltsfilter-Agent mithilfe der Exchange-Verwaltungsshell.


> [!IMPORTANT]
> Konfigurationsänderungen, die Sie am Inhaltsfilter-Agent in der Exchange-Verwaltungsshell vornehmen, werden nur auf dem lokalen Computer durchgeführt. Wenn der Inhaltsfilter-Agent auf mehreren Exchange-Servern in Ihrer Organisation ausgeführt wird, müssen Sie die Änderungen an der Konfiguration des Inhaltsfilters auf jedem Computer vornehmen.



Der Inhaltsfilter-Agent benötigt Updates, um feststellen zu können, ob eine Nachricht mit der Gewissheit übermittelt werden kann, dass es sich nicht um Spam handelt. Diese Updates enthalten Daten zu Phishingwebsites, Microsoft SmartScreen-Spamheuristiken und andere Updates zum intelligenten Nachrichtenfilter. Inhaltsfilterupdates umfassen zumeist ca. 6 MB Daten, die für einen längeren Zeitraum als andere Antispamupdatesdaten von Nutzen sind.

Inhaltsfilterupdates werden über [Microsoft Update](https://go.microsoft.com/fwlink/p/?linkid=54836) bereitgestellt. Alle zwei Wochen stehen aktualisierte Inhaltsfilterdaten zum Download zur Verfügung.

Weitere Informationen zum Konfigurieren von Inhaltsfiltern finden Sie unter [Verwalten der Inhaltsfilterung](manage-content-filtering-exchange-2013-help.md).


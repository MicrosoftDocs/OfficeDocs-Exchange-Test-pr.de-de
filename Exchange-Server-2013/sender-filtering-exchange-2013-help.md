---
title: 'Absenderfilterung: Exchange 2013 Help'
TOCTitle: Absenderfilterung
ms:assetid: b833f864-ff10-46a0-a653-28fb9ba30896
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124354(v=EXCHG.150)
ms:contentKeyID: 50476530
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Absenderfilterung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-12_

Die Absenderfilterung stützt sich auf die MAIL FROM: SMTP-Kopfzeile, um die Aktion festzulegen, die ggf. auf eine eingehende E-Mail angewendet werden soll. Die Absenderfilterung wird durch den Absenderfilter-Agent bereitgestellt.

Der Absenderfilter-Agent verarbeitet Nachrichten von bestimmten Absendern von außerhalb der Organisation. Administratoren pflegen eine Liste von Absendern, denen das Senden von Nachrichten an die Organisation untersagt ist. Als Administrator können Sie einzelne Absender (beispielsweise kim@contoso.com), ganze Domänen (contoso.com) oder Domänen mit allen Unterdomänen (\*.contoso.com) blockieren. Sie können außerdem konfigurieren, welche Aktion der Absenderfilter-Agent ausführen soll, wenn eine Nachricht von einem geblockten Absender gefunden wird. Sie können folgende Aktionen konfigurieren:

  - Der Absenderfilter-Agent lehnt die SMTP-Anforderung mit dem SMTP-Sitzungsfehler `554 5.1.0 Sender Denied` ab und trennt die Verbindung.

  - Der Absenderfilter-Agent akzeptiert die Nachricht und aktualisiert sie mit der Anzeige, dass die Nachricht von einem blockierten Absender stammt. Da die Nachricht von einem blockierten Absender stammt und auch dementsprechend gekennzeichnet ist, verwendet der Inhaltsfilter-Agent diese Information bei der Berechnung der SCL-Bewertung (Spam Confidence Level).

Sie können blockierte Absender angeben und definieren, wie der Absenderfilter-Agent mit Nachrichten von blockierten Absendern umgehen soll. Weitere Informationen zum Konfigurieren des Absenderfilter-Agents finden Sie unter [Verwalten der Absenderfilterung](manage-sender-filtering-exchange-2013-help.md).


> [!IMPORTANT]
> Die MAIL FROM: SMTP-Kopfzeilen können gespooft (manipuliert) sein. Deshalb sollten Sie sich nicht alleine auf den Absenderfilter-Agent verlassen. Verwenden Sie eine Kombination aus Absenderfilter-Agent und Sender ID-Agent. Der Sender ID-Agent prüft anhand der IP-Adresse des sendenden Servers, ob die Domäne in der MAIL FROM: SMTP-Kopfzeile mit der Domäne übereinstimmt, die registriert ist. Weitere Informationen über den Sender ID-Agent finden Sie unter <A href="sender-id-exchange-2013-help.md">Absender-ID</A>.



## Blockieren von Nachrichten mit dem Absenderfilter-Agent

Wenn der Absenderfilter-Agent auf einem Exchange-Server aktiviert ist, blockiert die Absenderfilterung eingehende Nachrichten, die aus dem Internet kommen und nicht authentifiziert sind. Diese Nachrichten werden als externe Nachrichten behandelt. Sie können den Absenderfilter-Agent in einzelnen Computerkonfigurationen deaktivieren. Weitere Informationen finden Sie unter [Verwalten der Absenderfilterung](manage-sender-filtering-exchange-2013-help.md).

Wenn Sie den Absenderfilter-Agent auf einem Exchange-Server aktivieren, filtert er alle Nachrichten, die über die Empfangsconnectors auf diesem Computer eingehen. Wie weiter oben in diesem Thema erwähnt, werden nur Nachrichten aus externen Quellen gefiltert. *Externe Quellen* sind als nicht authentifizierte Quellen definiert. Diese werden als anonyme Internetquellen betrachtet.

Es hat sich als bewährte Methode erwiesen, E-Mails von vertrauenswürdigen Partnern oder aus der eigenen Organisation nicht zu filtern. Beim Ausführen von Antispamfiltern besteht immer die Gefahr, dass die Filter falsch positive Ergebnisse ermitteln. Sie sollten Antispam-Agents nur für Nachrichten aus möglicherweise nicht vertrauenswürdigen und unbekannten Quellen konfigurieren. Dadurch wird die Gefahr verringert, legitime Nachrichten durch Antispamfilter falsch zu behandeln. Sie können das Ausführen des Absenderfilter-Agents für Nachrichten aus beliebigen Quellen aktivieren bzw. deaktivieren. Weitere Informationen finden Sie unter [Verwalten der Absenderfilterung](manage-sender-filtering-exchange-2013-help.md).

Sie können den Absenderfilter-Agent so konfigurieren, dass er eingehende Nachrichten blockiert, in denen kein Absender und keine Domäne in der MAIL FROM: SMTP-Kopfzeile angegeben sind. Mithilfe dieses Features können Sie auf dem Exchange-Server Unzustellbarkeitsberichtsangriffe verhindern. Die meisten zulässigen SMTP-Nachrichten stammen von SMTP-Servern, für die für jeden Server gilt, dass er einen Absender und eine Domäne im SMTP-Befehl MAIL FROM: übermittelt.

## Angeben der Blockieraktion

Nachdem Sie blockierte Absender und Domänen angegeben haben, müssen Sie angeben, wie der Absenderfilter-Agent Nachrichten von blockierten Absendern und Domänen behandelt. Es wird empfohlen, die Nachrichten zurückzuweisen. Wenn Sie den Absenderfilter-Agent dazu verwenden, E-Mail-Adressen und Domänen zu blockieren, die von einem Exchange-Administrator angegeben wurden, ist die Wahrscheinlichkeit von falsch positiven Ergebnissen geringer als bei der Verwendung anderer Antispam-Agents. Der Inhaltsfilter-Agent ist z. B. ein Antispam-Agent, der viele verschiedene Variablen verwendet, um zu bestimmen, ob es sich bei einer Nachricht um Spam handelt.

Es sind nur zwei Szenarios denkbar, in denen erwünschte Nachrichten vom Absenderfilter-Agent abgelehnt werden könnten:

  - Wenn Sie eine E-Mail-Adresse oder einen Domänennamen falsch schreiben, wird möglicherweise der falsche Absender blockiert.

  - Wenn ein Domänenname für ein legitimes Unternehmen erneut registriert wird, nachdem Sie die Domäne zur Liste der blockierten Absender hinzugefügt haben, blockieren Sie versehentlich erwünschte Nachrichten.

In beiden Fällen kann es dennoch sinnvoll sein, die Nachrichten zurückzuweisen.


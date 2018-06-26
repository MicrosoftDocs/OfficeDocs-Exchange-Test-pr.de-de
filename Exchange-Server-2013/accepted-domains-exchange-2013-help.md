---
title: 'Akzeptierte Domänen: Exchange 2013 Help'
TOCTitle: Akzeptierte Domänen
ms:assetid: c1839a5b-49f9-4c53-b247-f4e5d78efc45
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124423(v=EXCHG.150)
ms:contentKeyID: 50476627
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Akzeptierte Domänen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-06-16_

Eine akzeptierte Domäne ist jeder SMTP-Namespace, für den eine Microsoft Exchange Server 2013-Organisation E-Mail sendet oder empfängt. Akzeptierte Domänen enthalten die Domänen, für die die Exchange-Organisation autorisierend ist. Eine Exchange-Organisation ist autorisierend, wenn sie die Nachrichtenübermittlung für Empfänger in der akzeptierten Domäne ausführt. Akzeptierte Domänen enthalten auch Domänen, für welche die Exchange-Organisation E-Mail empfängt und dann zur Zustellung an den Empfänger an einen E-Mail-Server weiterleitet, der sich außerhalb der Organisation befindet.

**Inhalt**

Konfigurieren von akzeptierten Domänen

Autoritative Domänen

Relaydomänen

Interne Relaydomäne

Externe Relaydomäne

Akzeptierte Domänen und E-Mail-Adressrichtlinien

## Konfigurieren von akzeptierten Domänen

Akzeptierte Domänen werden als globale Einstellungen für die Exchange-Organisation konfiguriert. Sie müssen jede Domäne als akzeptierte Domäne in Ihrer Organisation konfigurieren, für die Ihre Exchange-Organisation Nachrichten weiterleitet oder zustellt.

Es gibt drei Typen von akzeptierten Domänen: autoritative Domänen, interne Relaydomänen und externe Relaydomänen. Diese akzeptierten Domänentypen werden in den folgenden Abschnitten näher erläutert.


> [!NOTE]
> Besteht in Ihrem Umkreisnetzwerk ein Edge-Transport-Serverabonnement, konfigurieren Sie akzeptierte Domänen auf einem Postfachserver in Ihrer Exchange-Organisation. Während der EdgeSync-Synchronisierung wird die Konfiguration der akzeptierten Domänen auf dem Edge-Transport-Server repliziert. Weitere Informationen finden Sie unter <A href="edge-subscriptions-exchange-2013-help.md">Edge-Abonnements</A>.



## Autoritative Domänen

Eine Organisation kann mehrere SMTP-Domänen einsetzen. Bei den E-Mail-Domänen für eine Organisation handelt es sich um autoritative Domänen. In Exchange 2013 ist eine akzeptierte Domäne dann autoritativ, wenn die Exchange-Organisation als Host für Postfächer von Empfängern in dieser SMTP-Domäne dient.

Bei der Installation des ersten Exchange 2013-Postfachservers wird standardmäßig eine akzeptierte Domäne als autoritativ für die Exchange-Organisation konfiguriert. Die standardmäßig akzeptierte Domäne stellt den vollständig qualifizierten Domänennamen (FQDN) für Ihre Stammdomäne der Gesamtstruktur dar. Der interne Domänenname unterscheidet sich häufig vom Namen der externen Domäne. Der Name für Ihre interne Domäne ist beispielsweise "contoso.local", obwohl der Name Ihrer externen Domäne "contoso.com" lautet. Der DNS-Mail-Exchanger-Eintrag (MX-Eintrag) für Ihre Organisation verweist auf "contoso.com". "contoso.com" ist der SMTP-Namespace, den Sie Benutzern beim Erstellen einer Richtlinie für E-Mail-Adressen zuweisen. Sie müssen eine akzeptierte Domäne erstellen, die mit dem Namen Ihres externen Domänennamens übereinstimmt.

Weitere Informationen finden Sie unter:

  - [Konfigurieren einer akzeptierten Domäne in Ihrer Exchange-Organisation als autoritativ](configure-an-accepted-domain-within-your-exchange-organization-as-authoritative-exchange-2013-help.md)

  - [Konfigurieren von Exchange für das Annehmen von Nachrichten für mehrere autoritative Domänen](configure-exchange-to-accept-mail-for-multiple-authoritative-domains-exchange-2013-help.md)

## Relaydomänen

Normalerweise sind alle mit dem Internet verbundenen Messagingserver so konfiguriert, dass sie keine Weiterleitungen für andere Domänen zulassen. Es gibt jedoch Szenarien, in denen Sie dafür sorgen möchten, dass Partner oder Niederlassungen E-Mails über Ihre Exchange-Server weiterleiten. In Exchange 2013 können Sie akzeptierte Domänen als Relaydomänen konfigurieren. Ihre Organisation empfängt E-Mails und leitet die Nachrichten dann an einen anderen E-Mail-Server weiter.

Sie können eine Relaydomäne als interne Relaydomäne oder als externe Relaydomäne konfigurieren. Die beiden Relaydomänentypen werden in den folgenden Abschnitten näher erläutert.

## Interne Relaydomäne

Wenn Sie eine interne Relaydomäne konfigurieren, verfügen einige oder alle Empfänger in dieser Domäne nicht über Postfächer in dieser Exchange-Organisation. E-Mails aus dem Internet werden über Transportserver in der Exchange-Organisation für diese Domäne weitergeleitet. Diese Konfiguration wird in den in diesem Abschnitt beschriebenen Szenarien verwendet.

Eine Organisation muss denselben SMTP-Adressraum möglicherweise auf zwei oder mehr unterschiedliche Messagingsysteme aufteilen. Sie müssen beispielsweise den SMTP-Adressraum auf ein Exchange- und ein Messagingsystem eines Drittanbieters aufteilen oder auf Exchange-Umgebungen, die in verschiedenen Active Directory-Gesamtstrukturen konfiguriert sind. In diesen Szenarien haben die Benutzer in den einzelnen E-Mail-Systemen dasselbe Domänensuffix als Teil ihrer E-Mail-Adressen.

Sie müssen eine akzeptierte Domäne erstellen, die als interne Relaydomäne konfiguriert ist, um diese Szenarien zu unterstützen. Sie müssen außerdem einen Sendeconnector hinzufügen, der sich auf einem Postfachserver befindet und für das Senden von E-Mails an den freigegebenen Adressraum konfiguriert ist. Wenn eine akzeptierte Domäne als autoritativ konfiguriert wurde und ein Empfänger nicht in Active Directory gefunden wird, wird ein Unzustellbarkeitsbericht an den Absender zurückgegeben. Die als interne Relaydomäne konfigurierte akzeptierte Domäne versucht zunächst, die Nachricht an einen Empfänger in der Exchange-Organisation zu übermitteln. Wenn der Empfänger nicht gefunden wird, wird die Nachricht an den Sendeconnector weitergeleitet, dessen Adressraum die größte Übereinstimmung aufweist.

Wenn eine Organisation mehr als eine Gesamtstruktur aufweist und die GAL-Synchronisierung (Global Address List, globale Adressliste) konfiguriert ist, kann die SMTP-Domäne für eine Gesamtstruktur als interne Relaydomäne in einer zweiten Gesamtstruktur konfiguriert werden. Nachrichten aus dem Internet, die an Empfänger in internen Relaydomänen gerichtet sind, werden an die Postfachserver in derselben Organisation weitergeleitet. Die empfangenden Postfachserver leiten die Nachrichten daraufhin an die Postfachserver in der Empfängergesamtstruktur weiter. Konfigurieren Sie die SMTP-Domäne als interne Relaydomäne, um sicherzustellen, dass an diese Domäne adressierte E-Mails von der Exchange-Organisation akzeptiert werden. Die Connectorkonfiguration Ihrer Organisation legt die Weiterleitung von Nachrichten fest.

Weitere Informationen finden Sie unter [Konfigurieren einer akzeptierten Domäne für eine Unternehmenseinheit mit Postfächern außerhalb Ihrer Exchange-Organisation](configure-an-accepted-domain-for-a-business-unit-with-mailboxes-outside-your-exchange-organization-exchange-2013-help.md).

## Externe Relaydomäne

Beim Konfigurieren einer externen Relaydomäne werden Nachrichten an einen E-Mail-Server weitergeleitet, der sich außerhalb der Exchange-Organisation sowie außerhalb des Umkreisnetzwerks der Organisation befindet.

Weitere Informationen finden Sie unter [Konfigurieren einer akzeptierten Domäne für eine unabhängige Unternehmenseinheit](configure-an-accepted-domain-for-an-independent-business-unit-exchange-2013-help.md).

## Akzeptierte Domänen und E-Mail-Adressrichtlinien

Sie müssen eine akzeptierte Domäne konfigurieren, bevor dieser SMTP-Adressraum in einer Richtlinie für E-Mail-Adressen verwendet werden kann. Beim Erstellen einer akzeptierten Domäne können Platzhalterzeichen (\*) im Adressraum verwendet werden, um anzugeben, dass alle Unterdomänen des SMTP-Adressraums ebenfalls von der Exchange-Organisation akzeptiert werden. Geben Sie zur Konfiguration von „contoso.com“ und sämtlicher Unterdomänen als akzeptierte Domänen **\*.contoso.com** als SMTP-Adressraum an. Die Einträge für akzeptierte Domänen stehen in der E-Mail-Adressrichtlinie automatisch zur Verfügung.

Wenn Sie eine in einer E-Mail-Adressrichtlinie verwendete akzeptierte Domäne löschen, ist die Richtlinie nicht länger gültig, und Empfänger mit E-Mail-Adressen in dieser SMTP-Domäne können keine E-Mails mehr senden oder empfangen.


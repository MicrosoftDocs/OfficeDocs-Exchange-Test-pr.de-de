---
title: 'Sekundäre Wählpläne: Exchange 2013 Help'
TOCTitle: Sekundäre Wählpläne
ms:assetid: ecf474c2-042d-4aaf-9f5b-d5138c56ef39
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff629383(v=EXCHG.150)
ms:contentKeyID: 54915050
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Sekundäre Wählpläne

 

_**Gilt für:**Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Wenn Sie einen Benutzer für Unified Messaging (UM) aktivieren, müssen Sie eine Durchwahl und eine UM-Postfachrichtlinie zuweisen, die den Benutzer mit einem UM-Wählplan verknüpft. Nachdem der Benutzer für UM aktiviert wurde, können Sie für diesen Benutzer im gleichen Wählplan weitere Durchwahlnummern zuweisen. Die Durchwahlen in diesem Wählplan müssen allerdings eindeutig sein. In einigen Bereitstellungen muss einem Benutzer möglicherweise in zwei unterschiedlichen Wählplänen die gleiche Durchwahlnummer zugewiesen werden. Ist dies der Fall, können Sie den Benutzer mit einem sekundären UM-Wählplan verknüpfen. Dies kann beispielsweise dann hilfreich sein, wenn der Benutzer über zwei Telefone verfügt oder zwischen verschiedenen Standorten wechselt.

**Inhalt**

Übersicht

Use of secondary extensions

UM features that operate differently for secondary dial plans

## Übersicht

Wenn Sie einen Benutzer für Unified Messaging aktivieren, müssen Sie eine Durchwahl und eine UM-Postfachrichtlinie definieren, die den Benutzer mit einem einzelnen UM-Wählplan verknüpft. Wenn Sie den Benutzer für UM aktivieren und dieser mit einer UM-Postrichtlinie verknüpft ist, die mit einem SIP-URI- oder E.164-Wählplan verknüpft ist, müssen Sie mit der Durchwahl des Benutzers auch eine SIP-Adresse oder eine E.164-Nummer angeben. UM verwendet den Wählplan und die Durchwahlnummer sowie die SIP-Adresse oder die E.164-Nummer, um den Benutzer zu suchen, wenn an das Postfach des Benutzers eine Voicemailnachricht übermittelt wird.

Wenn Sie Telefondurchwahl-Wählpläne verwenden und für einen Benutzer die gleiche Durchwahl angeben müssen, müssen Sie einen sekundären Wählplan erstellen, den Benutzer für UM aktivieren und für den Benutzer die gleiche Durchwahl angeben. Der Grund dafür ist, dass die Durchwahlnummer in einem Wählplan nur einmal vorkommen darf.


> [!NOTE]
> Die Anzahl der sekundären Durchwahlnummern, die für einen UM-aktivierten Benutzer hinzugefügt werden können, ist unbegrenzt.



Es kann vorkommen, dass ein Benutzer zwischen verschiedenen Standorten wechselt, zwei oder mehr Telefone besitzt oder Voicemailnachrichten auf einer DID-Durchwahlnummer (Direct Inward Dial) und Faxnachrichten auf einer anderen DID-Durchwahlnummer empfangen möchte. Dazu müssen Sie dem Postfach des Benutzers eine weitere DID-Durchwahlnummer und in einigen Fällen sekundäre Wähleinstellungen hinzufügen.

In einigen Konfigurationen kann der Benutzer, wenn Sie eine zweite Durchwahl für einen primären Satz Wähleinstellungen oder eine oder mehrere Durchwahlnummer für einen sekundären Satz Wähleinstellungen hinzufügen, Sprachnachrichten oder Faxe über eine oder mehrere der Durchwahlnummern empfangen. Wenn Sie möchten, dass ein UM diese Faxanrufe entgegennimmt und an die zweite DID-Durchwahlnummer sendet, müssen Sie auch die Telefonanlage der Organisation für die Weiterleitung der Faxanrufe an die zweite DID-Durchwahlnummer konfigurieren.

Dem Postfach eines UM-aktivierten Benutzers kann Folgendes zugewiesen werden:

  - Eine einzelne Durchwahlnummer, eine SIP-Adresse (Session Initiation Protocol) oder eine E.164-Adresse in einem einzelnen Satz Wähleinstellungen

  - Mehreren Durchwahlnummern in einem einzigen Wählplan

  - Mehreren Durchwahlnummern in zwei unterschiedlichen Wählplänen

Wenn ein Benutzer für UM aktiviert ist, müssen Sie eine Durchwahlnummer und eine UM-Postfachrichtlinie angeben. UM benötigt die Durchwahlnummer, um den Benutzer zu identifizieren, wenn er sich bei Outlook Voice Access anmeldet, um Nachrichten abzurufen. Die UM-Postfachrichtlinie enthält eine Sammlung von Konfigurationseigenschaften mit Werten, die UM auf alle Benutzer anwendet, die im Rahmen dieser Richtlinie UM-aktiviert sind. Die UM-Postfachrichtlinie entspricht der "Serviceklasse", wie sie andere Systeme verwenden (wie Voicemail oder PBX), und zwar in der Hinsicht, dass die Änderung des Werts einer UM-Postfachrichtlinie für viele zugeordnete Benutzer Auswirkungen auf das Verhalten haben kann.

Eine Eigenschaft in einer UM-Postfachrichtlinie verweist auf einen Satz UM-Wähleinstellungen. Dabei handelt es sich um eine Reihe von telefoniefähigen Durchwahlnummern. Dieser Satz hat einen Nummerierungsplan, in dem doppelte Durchwahlnummern nicht zugelassen sind.

Die Durchwahlnummer eines Benutzers ist deshalb innerhalb des Satzes UM-Wähleinstellungen, in dem dieser UM-aktiviert ist, eindeutig. Tatsächlich muss der Satz UM-Wähleinstellungen in Verbindung mit der Durchwahlnummer innerhalb der Organisation eindeutig sein. Dies ist eine der Methoden, anhand derer UM einen UM-aktivierten Benutzer in einer Organisation eindeutig identifizieren kann. Die Verwendung eines sekundären Satzes Wähleinstellungen hilft zu gewährleisten, dass die Wähleinstellungen und die Durchwahlnummer in einer Organisation eindeutig sind. Stellen Sie sich beispielsweise eine Organisation vor, in der es zwei Sätze UM-Wähleinstellungen gibt: Wähleinstellungen A und Wähleinstellungen B. Die Durchwahlnummer eines Benutzers in Wähleinstellungen A lautet 55555 und in Wähleinstellungen B 66666. Bei Verwenden eines sekundären Satzes Wähleinstellungen kann die Durchwahl des Benutzers in Wähleinstellungen A 55555 und in Wähleinstellungen B ebenfalls 55555 sein. In beiden Fällen ist die Durchwahlnummer des Benutzers innerhalb des verwendeten Satzes Wähleinstellungen eindeutig.

In der folgenden Tabelle werden Begriffe im Zusammenhang mit primären und sekundären Durchwahlnummern, Outlook Voice Access-Nummern und UM-Wähleinstellungen erläutert.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Begriff</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Primäre Durchwahlnummer</p></td>
<td><p>Die Durchwahlnummer, die bei der UM-Aktivierung des Benutzers angegeben wird.</p></td>
</tr>
<tr class="even">
<td><p>Primärer Satz Wähleinstellungen</p></td>
<td><p>Die UM-Wähleinstellungen, die bei der UM-Aktivierung des Benutzers angegeben werden. Die Wähleinstellungen werden dem UM-aktivierten Benutzer zugeordnet, wenn er mit der UM-Postfachrichtlinie verknüpft wird.</p></td>
</tr>
<tr class="odd">
<td><p>primäre Outlook Voice Access-Nummer</p></td>
<td><p>Die Outlook Voice Access-Nummer für die primären Wähleinstellungen des Benutzers. Die Anrufe des Benutzers werden an diese Nummer weitergeleitet, wenn Anrufe unbeantwortet bleiben oder die Leitung besetzt ist. Diese Nummer ruft der Benutzer auch an, um sich bei Outlook Voice Access anzumelden.</p></td>
</tr>
<tr class="even">
<td><p>Sekundäre Durchwahlnummer</p></td>
<td><p>Eine oder mehrere Durchwahlnummern, die der Konfiguration des UM-aktivierten Benutzers hinzugefügt werden können.</p></td>
</tr>
<tr class="odd">
<td><p>Sekundärer Satz Wähleinstellungen</p></td>
<td><p>Ein anderer Satz UM-Wähleinstellungen als der primäre Satz Wähleinstellungen, in dem eine oder mehrere sekundäre Durchwahlnummern konfiguriert werden können.</p></td>
</tr>
<tr class="even">
<td><p>sekundäre Outlook Voice Access-Nummer</p></td>
<td><p>Die Outlook Voice Access-Nummer für die sekundären Wähleinstellungen des Benutzers. Benutzer können diese Nummer von ihrer sekundären Durchwahlnummer aus anrufen, um sich bei Outlook Voice Access anzumelden.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Verwendung sekundärer Durchwahlnummern

In den meisten Bereitstellungen ist für jeden UM-aktivierten Benutzer nur eine Durchwahlnummer konfiguriert. Es gibt jedoch fortschrittlichere Bereitstellungen, in denen Sie sekundäre Durchwahlnummern für die Benutzer hinzufügen müssen.

Wenn Microsoft Lync Server für Enterprise Voice verwendet wird, kann Unified Messaging das Voicemailsystem bereitstellen. Bei den für Enterprise-VoIP verwendeten UM-Wähleinstellungen muss es sich jedoch um spezifische SIP-URI-Wähleinstellungen für UM-Konfigurationen mit Lync Server 2010 handeln. In diesen Bereitstellungen wird die Durchwahlnummer des Benutzers durch einen Microsoft Unified Communications-Endpunkt wie MicrosoftOffice Communicator bereitgestellt, der auf dem Computer des Benutzers ausgeführt wird, oder durch Office Communicator Phone Edition, der auf einem unterstützten IP-Telefon ausgeführt wird. In den meisten Fällen müssen die primären Wähleinstellungen des Benutzers also mit den SIP-URI-Wähleinstellungen übereinstimmen, die mit Lync Server verwendet werden. Benötigt ein Benutzer jedoch mehr Durchwahlnummern, sollten Sie keine sekundäre Durchwahlnummer zu den primären Wähleinstellungen hinzufügen. Sie müssen einen sekundären Satz Wähleinstellungen hinzufügen und die sekundäre Durchwahlnummer oder EUM-Proxyadresse dann dem UM-aktivierten Benutzer hinzufügen.

Weitere Informationen zum Hinzufügen, Entfernen und Ändern von Durchwahlnummern finden Sie unter einem der folgenden Themen:

  - [Ändern einer Durchwahlnummer](change-an-extension-number-exchange-2013-help.md)

  - [Hinzufügen einer Durchwahlnummer](add-an-extension-number-exchange-2013-help.md)

  - [Entfernen einer Durchwahlnummer](remove-an-extension-number-exchange-2013-help.md)

Wenn Sie SIP-Adressen oder E.164-Nummern für UM-aktivierte Benutzer ändern müssen:

  - [Hinzufügen einer SIP-Adresse](add-a-sip-address-exchange-2013-help.md)

  - [Ändern einer SIP-Adresse](change-a-sip-address-exchange-2013-help.md)

  - [Entfernen einer SIP-Adresse](remove-a-sip-address-exchange-2013-help.md)

  - [Hinzufügen einer E.164-Nummer](add-an-e-164-number-exchange-2013-help.md)

  - [Ändern Sie eine e. 164-Nummer](change-an-e-164-number-exchange-2013-help.md)

  - [Entfernen einer e. 164-Nummer](remove-an-e-164-number-exchange-2013-help.md)

## Anrufannahme

Unified Messaging bietet folgende Optionen:

  - **Mailboxansage**   Tritt ein, wenn Benutzer Anrufe nicht beantworten und UM den Anruf entgegennimmt.

  - **Outlook Voice Access**   Wird von Benutzern verwendet, um sich in das Voicemailsystem einzuwählen und auf ihr Postfach zuzugreifen.

Zwei Konfigurationen werden häufig verwendet:

  - Ein UM-aktivierter Benutzer verfügt über zwei Durchwahlnummern (eine primäre, eine sekundäre) in den primären Wähleinstellungen. Diese Durchwahlnummern gehören zu verschiedenen Telefonen auf dem Schreibtisch des Benutzers und sind mit derselben PBX-Anlage verbunden. Die beiden Nummern stehen zwei verschiedenen Benutzergruppen zur Verfügung. In dieser Konfiguration handelt es sich bei der primären Durchwahlnummer um die "allgemeine" Arbeitsnummer und bei der zweiten Durchwahlnummer um die "aufgabenspezifische" Nummer wie eine Helpdesk-Nummer oder eine dedizierte Faxnummer.

  - Ein UM-aktivierter Benutzer verbringt einen bestimmten Zeitraum, etwa drei von vier Wochen, am Hauptsitz seines Unternehmens und den Rest der Zeit in einem anderen Büro in einer der Remoteniederlassungen des Unternehmens. Die beiden Büros haben unterschiedliche PBX-Anlagen, und die Durchwahlnummern sind für jede PBX-Anlage jeweils eindeutig. In diesem Beispiel ist für den Benutzer eine primäre Durchwahlnummer in den primären Wähleinstellungen der PBX-Anlage im Hauptbüro und eine zweite Durchwahlnummer in sekundären Wähleinstellungen der PBX-Anlage des anderen Büros konfiguriert.

In beiden Konfigurationen werden Sprachnachrichten oder Benachrichtigungen über verpasste Anrufe, die durch unbeantwortete Anrufe generiert werden, an den Posteingang des Benutzers gesendet.

## Outlook Voice Access

Unter Umständen sollen UM-aktivierte Benutzer sich von jeder Durchwahlnummer, ob primär oder sekundär, bei Outlook Voice Access anmelden können. Dies ist zwar möglich, doch gibt es einige architektonische Einschränkungen, die verhindern, dass dies von allen Durchwahlnummern aus gleich funktioniert. Um sich bei Outlook Voice Access anzumelden, müssen UM-aktivierte Benutzer die folgenden Schritte durchführen:

1.  Eine Outlook Voice Access-Nummer anrufen.

2.  Ihre Durchwahlnummer eingeben, wenn sie von einer anderen Telefonnummer aus anrufen.

3.  Ihre PIN eingeben, wenn sie nicht für Enterprise-VoIP aktiviert sind und von einem Unified Communications-Telefon, Office Communicator oder Lync Server aus anrufen.

**Verwendungsszenarien**

  - **Einzelne Durchwahlnummer mit Outlook Voice Access   **Verfügen Benutzer über eine einzelne primäre Durchwahlnummer, müssen sie stets die Outlook Voice Access-Nummer für ihren primären Satz UM-Wähleinstellungen anrufen. Wenn sie von ihrer Durchwahlnummer aus anrufen, werden sie nicht aufgefordert, die Durchwahlnummer einzugeben, und Schritt 2 der vorhergehenden Schritte wird übersprungen.

  - **Zwei Durchwahlnummern im primären Satz Wähleinstellungen mit Outlook Voice Access   **Verfügen Benutzer nur über zwei Durchwahlnummern, eine primäre und eine sekundäre, und sowohl primäre als auch sekundäre Durchwahlnummer stammen aus demselben Satz UM-Wähleinstellungen, müssen sie stets die Outlook Voice Access-Nummer des Satzes Wähleinstellungen anrufen. Wenn sie von ihrer primären oder sekundären Durchwahlnummer aus anrufen, werden sie nicht aufgefordert, die Durchwahlnummer einzugeben, und Schritt 2 der vorhergehenden Schritte wird übersprungen. Outlook Voice Access-Funktionen funktionieren je nach Durchwahlnummer, die zur Anmeldung verwendet wird, auf dieselbe Weise.

  - **Durchwahlnummern im primären und in einem sekundären Satz Wähleinstellungen mit Outlook Voice Access   **Verfügt der Benutzer nur über zwei Durchwahlnummern, eine primäre und eine sekundäre, und primäre und sekundäre Durchwahlnummer stammen jeweils aus verschiedenen Sätzen Wähleinstellungen (primär und sekundär), sollten sie die entsprechende Outlook Voice Access-Nummer für den jeweiligen Satz Wähleinstellungen anrufen. Von ihrer primären Durchwahlnummer sollten sie die Outlook Voice Access-Nummer des primären Satzes Wähleinstellungen und von der sekundären Durchwahlnummer aus die Outlook Voice Access-Nummer des sekundären Satzes Wähleinstellungen anrufen. Wenn sie dies tun, werden sie nicht aufgefordert, die Durchwahlnummer einzugeben, und Schritt 2 der vorhergehenden Schritte wird übersprungen.
    
    Outlook Voice Access-Funktionen, die keine ausgehenden Wählvorgänge (wie "Den Absender anrufen" oder "Im Büro anrufen") beinhalten, funktionieren je nach Durchwahlnummer, die zur Anmeldung verwendet wird, auf dieselbe Weise. Allerdings arbeiten Outlook Voice Access-Funktionen, die ausgehende Wahlvorgänge erfordern, nicht erwartungsgemäß, wenn Benutzer sich bei einem sekundären Satz Wähleinstellungen anmelden, es sei denn, die Regeln für ausgehende Wahlvorgänge sind in beiden Sätzen Wähleinstellungen identisch. Damit das Verhalten ausgehender Wahlvorgänge absolut identisch ist, müssen Sie sicherstellen, dass die folgenden Eigenschaften im primären und im sekundären Satz Wähleinstellungen gleich konfiguriert sind:
    
      - Kurzwahlnummern (Amtsvorwahl, national und international)
    
      - Nationale oder regionale Vorwahlnummern
    
      - Wählregeln
    
      - Wählregelgruppen-Namen

Ein UM-aktivierten Benutzer ist einer UM-Postfachrichtlinie zugeordnet, und diese UM-Postfachrichtlinie ist dem primären Satz Wähleinstellungen des Benutzers zugeordnet. Die dem primären Satz Wähleinstellungen des UM-aktivierten Benutzers zugeordneten UM-Postfachrichtlinieneinstellungen werden auf den Benutzer angewendet. Ist ein Benutzer einem sekundären Satz Wähleinstellungen mit einer sekundären Durchwahlnummer im sekundären Satz Wähleinstellungen zugeordnet, werden weiterhin die dem primären Satz Wähleinstellungen zugeordneten UM-Postfachrichtlinieneinstellungen angewendet. In Outlook Voice Access werden die UM-Postfachrichtlinieneinstellungen verwendet, die dem primären Satz Wähleinstellungen zugeordnet sind, unabhängig davon, ob der Benutzer den primären Satz oder den sekundären Satz Wähleinstellungen anruft.

Die Eigenschaften **AllowedInCountryOrRegionGroups** und **AllowedInternationalGroups** in der UM-Postfachrichtlinie enthalten die Namen von Wählregelgruppen, die in den Eigenschaften **ConfiguredInCountryOrRegionGroups** und **ConfiguredInternationalGroups** eines Satzes UM-Wähleinstellungen konfiguriert sind. Ruft ein UM-aktivierter Benutzer bei Outlook Voice Access an, werden die Regeln für ausgehende Anrufe der UM-Postfachrichtlinie, die dem primären oder sekundären Satz Wähleinstellungen zugeordnet ist, auf die Anrufe angewendet, die der Benutzer tätigt, je nachdem, ob der UM-aktivierte Benutzer die Outlook Voice Access-Nummer des primären oder des sekundären Satzes Wähleinstellungen angerufen hat.

Wenn beispielsweise ein primärer Satz Wähleinstellungen namens "Contoso Dial Plan 1" die Wählregel "US and Canada" in der Eigenschaft **ConfiguredInCountryOrRegionGroups** besitzt, kann die UM-Postfachrichtlinie "Contoso UM Policy 1" ebenfalls "US and Canada" in der Eigenschaft **AllowedInCountryOrRegionGroups** haben. Wenn Sie für einen Benutzer in "Contoso UM Policy 2" eine sekundäre Durchwahlnummer in "Contoso Dial Plan 2" hinzufügen wollen, müssen Sie sicherstellen, dass die Eigenschaft **ConfiguredInCountryOrRegionGroups** von "Contoso Dial Plan 2" ebenfalls eine Regeln namens "US and Canada" enthält. Ansonsten kann UM keine Regel namens "US and Canada" im sekundären Satz Wähleinstellungen finden, wenn sich der Benutzer von der sekundären Durchwahlnummer aus bei Outlook Voice Access anmeldet. Ist dies der Fall, lässt UM nur Anrufe des Benutzers zu, die für alle Anrufer des sekundären Satzes Wähleinstellungen zugelassen sind, was unter Umständen restriktiver ist.

Zurück zum Seitenanfang

## UM-Funktionen, die für sekundäre Wähleinstellungen anders funktionieren

Es gibt eine Reihe von UM-Funktionen, die sekundäre Wähleinstellungen verwenden können, in gewissen Situationen möglicherweise aber nicht richtig funktionieren. Sie sollten wissen, wie die einzelnen Funktionen betroffen sind, wenn Sie UM-konfigurierte Benutzer für die Verwendung eines sekundären Satzes Wähleinstellungen konfigurieren.

## Wiedergabe über Telefon

In Outlook Web App verwendet die Wiedergabe über Telefon für den ausgehenden Anruf das VoIP-Gateway, das dem primären Satz Wähleinstellungen des Benutzers zugeordnet ist. Die Funktion wendet Wählregeln aus den primären Wähleinstellungen und die UM-Postfachrichtlinie an, die dem Postfach des Benutzers zugeordnet ist.

## Verzeichnissuche (Outlook Voice Access)

Eine Suche im Verzeichnis nach einem Benutzer, der authentifiziert wurde, erfolgt nach diese Regeln:

  - Die Möglichkeit, nach einem Benutzer zu suchen und dann eine Sprachnachricht zu hinterlassen oder einen Benutzer anzurufen, ist nur dann verfügbar, wenn der Benutzer, der die Suche durchführt, UM-aktiviert ist und über eine primäre Durchwahlnummer im selben Satz Wähleinstellungen verfügt wie der Benutzer, der angerufen wird. Ist dies der Fall, wird der Benutzer bei der Suche nach Name, Alias und primärer Durchwahlnummer gefunden. Bei einer Suche mithilfe der sekundären Durchwahlnummer wird der Benutzer jedoch nicht gefunden.

  - Wenn der gesuchte Benutzer UM-aktiviert ist und über eine sekundäre Durchwahlnummer im angerufenen Satz Wähleinstellungen verfügt, wird der Benutzer durch eine Suche nach Name, Alias und sekundärer Durchwahlnummer gefunden. Doch auch wenn die Option angeboten wird, eine Sprachnachricht zu hinterlassen und den Kontakt anzurufen, ist die Anrufkontaktoption nicht erfolgreich. In diesem Fall wird der Benutzer bei einer Suche nach der primären Durchwahlnummer nicht gefunden.

  - Um den gesuchten Benutzer zu finden und ihn entweder anzurufen oder ihm eine Sprachnachricht zu hinterlassen, sollte der UM-aktivierte Benutzer Outlook Voice Access über seine Outlook Voice Access-Nummer im primären Satz Wähleinstellungen verwenden und nach Name, Alias oder primärer Durchwahlnummer suchen. Wenn der gesuchte Benutzer über die Outlook Voice Access-Nummer des sekundären Satzes Wähleinstellungen angerufen wird, wird der Benutzer nur gefunden, wenn die Suche nach Name, Alias oder sekundärer Durchwahlnummer erfolgt. Wird die primäre Durchwahlnummer verwendet, besteht für den Benutzer nur die Option, eine Voicemail zu hinterlassen.

## Verzeichnissuche (Outlook Voice Access)

Eine Suche im Verzeichnis nach einem Benutzer, der nicht authentifiziert wurde, erfolgt nach diesen Regeln:

  - Der gesuchte Benutzer wird gefunden, und die Option, eine Sprachnachricht zu hinterlassen oder den Benutzer anzurufen, wird nur dann angeboten, wenn der Benutzer UM-aktiviert ist und eine primäre Durchwahlnummer in den angerufenen Wähleinstellungen hat. Ist dies der Fall, wird der Benutzer bei der Suche nach Name, Alias und primärer Durchwahlnummer gefunden. Bei einer Suche mithilfe der sekundären Durchwahlnummer wird der Benutzer jedoch nicht gefunden.

  - Wenn der gesuchte Benutzer UM-aktiviert ist, über eine sekundäre Durchwahlnummer in den angerufenen Wähleinstellungen verfügt und die Option **Weiterleitung und Suche** \> **Ermöglicht Anrufern Folgendes** \> **Sprachnachrichten ohne Klingeln des Telefons des Benutzers hinterlassen in den angerufenen Wähleinstellungen** ausgewählt ist, wird der Benutzer bei der Suche nach Name, Alias und sekundärer Durchwahlnummer gefunden. Der Anrufer erhält jedoch die Option, eine Sprachnachricht zu hinterlassen, und es gibt keine Option, den Benutzer anzurufen.

  - Um die Möglichkeit zu haben, einen Benutzer zu suchen und anzurufen oder eine Sprachnachricht zu hinterlassen, muss der Anrufer die Outlook Voice Access-Nummer der primären Wähleinstellungen des Benutzers anrufen und nach Name, Alias oder sekundärer Durchwahlnummer des Benutzers suchen. Wenn die sekundäre Outlook Voice Access-Nummer des Benutzers angerufen wird, wird der Benutzer nur gefunden, wenn die Option **Anrufer dürfen Benutzer nach Name oder Alias suchen** auf **In der gesamten Organisation** festgelegt ist. Ist dies der Fall, wird nur die Option zum Hinterlassen einer Sprachnachricht bereitgestellt.

## Anrufen des Absenders (Outlook Voice Access)

Wenn ein Benutzer bei Outlook Voice Access anruft und die Option "Den Absender anrufen" auswählt, kann er entweder eine E-Mail-Nachricht oder eine Voicemailnachricht an einen UM-aktivierten Benutzer senden. Welche Optionen verfügbar sind, hängt davon ab, ob der Anrufer denselben Wähleinstellungen zugeordnet ist wie der Absender, den er anruft. Wenn der Anrufer eine Teilnehmerzugriffsnummer wählt und der Anrufer authentifiziert wird, folgen Anrufe an einen UM-aktivierten Benutzer diesen Regeln:

  - **E-Mail-Nachrichten   **Handelt es sich bei dem Absender der E-Mail-Nachricht um einen UM-aktivierten Benutzer, führt die Auswahl der Option zum Anrufen des Absenders zu einem Anruf an die primäre Durchwahlnummer des Absenders in den primären Wähleinstellungen des Benutzers. In dem Fall, dass die primäre Durchwahlnummer des Absenders sich in einem anderen Satz Wähleinstellungen befindet als die des Anrufers, wird die Option "Den Absender anrufen" nur bereitgestellt, wenn ein Geschäfts-, Privat- oder Mobiltelefon für den Absender konfiguriert ist und der Anruf gemäß der Wählregeln zugelassen ist.

  - **Voicemailnachrichten   **Handelt es sich bei dem Anrufer um einen UM-aktivierten Benutzer, führt die Option zum Anrufen des Absenders stets zu einem Anruf an die Durchwahlnummer, die vom Absender zum Hinterlassen seiner Sprachnachricht verwendet wird. Besitzt diese Durchwahlnummer eine andere Anzahl Ziffern als im angerufenen Satz Wähleinstellungen, wird die Aufforderung zum Anrufen des Absenders nur dann bereitgestellt, wenn Wählregeln konfiguriert sind, die den Anruf zulassen. Beispiel:
    
      - Die Option "Den Absender anrufen" wird nur angeboten, wenn der Absender eine Durchwahlnummer in den Wähleinstellungen verwendet, die zum Senden der Sprachnachricht verwendet wurden.
    
      - Die Option "Den Absender anrufen" wird bereitgestellt, wenn der Absender eine Durchwahlnummer aus einem anderen Satz Wähleinstellungen verwendet als in Outlook Voice Access zum Senden der Sprachnachricht verwendet wurde und beide Sätze dieselbe Anzahl von Ziffern aufweisen. Ob der Anruf erfolgreich ist, hängt davon ob, ob das VoIP-Gateway und die PBX-Infrastruktur die Anrufübertragung zulassen.
    
      - Die Option "Den Absender anrufen" wird nicht bereitgestellt, wenn der Absender eine Durchwahlnummer aus einem anderen Satz Wähleinstellungen verwendet als in Outlook Voice Access zum Senden der Sprachnachricht verwendet wurde, beide Sätze eine andere Anzahl von Ziffern aufweisen und es keine Amtswahlregeln gibt, die mit der Durchwahlnummer des Absenders übereinstimmen.

Zurück zum Seitenanfang


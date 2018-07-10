---
title: 'Empfängerauflösung: Exchange 2013 Help'
TOCTitle: Empfängerauflösung
ms:assetid: 09deda5a-d405-45b1-a3ff-fefd3d76cdea
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb430743(v=EXCHG.150)
ms:contentKeyID: 52062829
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Empfängerauflösung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-03-17_

*Empfängerauflösung* ist der Vorgang des Aufgliederns und Auflösens aller Empfänger in einer Nachricht. Beim Auflösen von Empfängern wird ein Empfänger dem entsprechenden Active Directory-Objekt in der Microsoft Exchange-Organisation zugeordnet. Beim Aufgliedern von Empfängern werden alle Verteilergruppen in eine Liste einzelner Empfänger aufgegliedert. Mithilfe der Empfängerauflösung können Nachrichtenbeschränkungen und alternative Empfänger ordnungsgemäß auf die einzelnen Empfänger angewendet werden.

In einer Microsoft Exchange Server 2013-Organisation wird die Empfängerauflösung durch das Kategorisierungsmodul im Transportdienst auf Postfachservern durchgeführt. Die Kategorisierung erfolgt für jede Nachricht, nachdem eine neu eingegangene Nachricht in die Übermittlungswarteschlange eingestellt wurde. Über die Inhaltskonvertierung und das Routing hinaus wird die Empfängerauflösung auf die Nachricht angewendet, bevor die Nachricht in eine Zustellungswarteschlange eingestellt wird. Das Kategorisierungsmodul führt die Empfängerauflösung vor dem Routing aus. Die Komponente des Kategorisierungsmoduls, die für die Empfängerauflösung zuständig ist, wird häufig als *Konfliktlöser* bezeichnet.

**Inhalt**

Auflösung auf oberster Ebene

Aufgliederung

Verzweigung und Steuerung der Empfängeraufgliederung

Empfängerauflösungsdiagnose

## Auflösung auf oberster Ebene

*Auflösung auf oberster Ebene* ist die erste Phase der Empfängerauflösung. Die Auflösung auf oberster Ebene ordnet jeden Empfänger in einer eingehenden Nachricht einem entsprechenden Empfängerobjekt in Active Directory zu. Während der Auflösung auf oberster Ebene erstellt das Kategorisierungsmodul eine Liste, die den in der Nachricht enthaltenen Absender und die ursprünglichen, nicht aufgegliederten Empfänger-E-Mail-Adressen enthält. Anschließend verwendet das Kategorisierungsmodul diese Liste von E-Mail-Adressen, um Active Directory abzufragen und alle E-Mail-aktivierten Objekte zu suchen, für die entsprechende E-Mail-Adressattribute vorhanden sind. Wenn eine Übereinstimmung gefunden wird, werden die Eigenschaften passender Active Directory-Objekte für die spätere Verwendung zwischengespeichert. Ebenfalls werden alle Nachrichteneinschränkungen für Absender durchgesetzt.

## Empfänger-E-Mail-Adressen

Die Auflösung auf oberster Ebene beginnt mit einer Nachricht und der ursprünglichen, nicht aufgegliederten Liste der Empfänger aus dem *Nachrichtenumschlag*. Der Nachrichtenumschlag enthält die Befehle, die zum Übertragen von Nachrichten zwischen SMTP-Messagingservern verwendet werden. Die E-Mail-Adresse des Absenders ist im Befehl **MAIL FROM:**  enthalten. Die E-Mail-Adressen der einzelnen Empfänger befinden sich in einem getrennten Befehl **RCPT TO:**  . Der Umschlagabsender und der Umschlagempfänger werden normalerweise aus dem Absender und dem Empfänger in den Kopfzeilenfeldern `To:`, `From:`, `Cc:` und `Bcc:` im Nachrichtenkopf erstellt. Dies trifft jedoch nicht immer zu. Die Kopfzeilenfelder `To:`, `From:`, `Cc:` und `Bcc:` in einer Nachricht sind leicht zu fälschen und stimmen möglicherweise nicht mit den tatsächlichen Absender- oder Empfänger-E-Mail-Adressen überein, die zum Übertragen der Nachricht verwendet wurden.

## Gekapselte E-Mail-Adressen

Standardmäßige SMTP-E-Mail-Adressen entsprechen den Spezifikationen von RFC 2821 und RFC 2822, z. B. chris@contoso.com. Eine E-Mail-Adresse kann jedoch auch eine Nicht-SMTP-E-Mail-Adresse sein, die in einer gültigen SMTP-Adresse gekapselt ist. Exchange unterstützt gekapselte Adressen, die die IMCEA-Kapselungsmethode (Internet Mail Connector Encapsulated Address) verwenden.

Für diese Kapselungsmethode ist die Codierung von Zeichen erforderlich, die in SMTP-E-Mail-Adressen ungültig sind. Alphanumerische Zeichen, das Gleichheitszeichen (=) und der Bindestrich (-) erfordern keine Codierung. Für andere Zeichen wird die folgende Codierungssyntax verwendet:

  - Ein Schrägstrich (/) wird durch einen Unterstrich (\_) ersetzt.

  - Andere US-ASCII-Zeichen werden durch ein Pluszeichen (+) ersetzt, und die zwei Stellen ihres ASCII-Werts werden in hexadezimaler Schreibweise geschrieben. Beispielsweise hat das Leerzeichen den codierten Wert `+20`.

Die IMCEA-Kapselungsmethode verwendet die folgende Syntax: `IMCEA<Type>-<address>@<domain>`

Der Platzhalter \<*Type*\> identifiziert den Typ von Nicht-SMTP-Adresse, z. B. `EX`, `X400` oder `FAX`.


> [!NOTE]
> Obwohl <CODE>SMTP</CODE> und <CODE>X500</CODE> theoretisch gültige Werte für &lt;<EM>Type</EM>&gt; sind, lehnt die Exchange-Empfängerauflösung alle mit IMCEA codierten Adressen ab, die einen dieser Typen verwenden.



Der Platzhalter \<*address*\> ist die codierte Originaladresse. Der Platzhalter \<*domain*\> stellt die zum Kapseln der Nicht-SMTP-Adresse verwendete SMTP-Domäne dar, z. B. "contoso.com"

Bei der IMCEA-Kapselungsmethode sind Adressen nur dann nicht verschlüsselt, wenn die Domäne mit der autorisierenden Standarddomäne in der Exchange-Organisation übereinstimmt. Weitere Informationen zu akzeptierten Domänen finden Sie unter [Akzeptierte Domänen](accepted-domains-exchange-2013-help.md).

Die maximale Länge für eine SMTP-E-Mail-Adresse in Exchange beträgt 571 Zeichen. Dieser Grenzwert setzt sich wie folgt zusammen:

  - 315 Zeichen für den Namensanteil der Adresse

  - 255 Zeichen für den Domänennamen

  - Das @-Zeichen, das den Namensanteil der Adresse vom Domänennamen trennt

Beachten Sie, dass Exchange keine mit der IMCEA-Kapselungsmethode codierten Nachrichten unterstützt, wenn der Namensteil der Adresse 315 Zeichen überschreitet. Dies gilt auch dann, wenn die gesamte E-Mail-Adresse weniger als 571 Zeichen umfasst.

## Adressauflösung

Für jede Nachricht werden die Absender-E-Mail-Adresse und alle Empfänger-E-Mail-Adressen einer Liste hinzugefügt, die zum Abfragen von Active Directory verwendet wird. Alle gekapselten Adressen werden aus der Kapselung befreit, bevor sie der Liste der E-Mail-Adressen hinzugefügt werden. Die Active Directory-Abfrage wird für jeweils bis zu 20 E-Mail-Adressen durchgeführt. Wenn die Active Directory-Abfrage vorübergehende Fehler feststellt, wird die Nachricht an die Übermittlungswarteschlange zurückgegeben und für den Zeitraum verzögert, der durch den Schlüssel *ResolverRetryInterval* in der XML-Anwendungskonfigurationsdatei `%ExchangeInstallPath%Bin\EdgeTransport.exe.config` angegeben wird, die dem Microsoft Exchange-Transportdienst zugeordnet ist. Der Standardwert beträgt 30 Minuten.

In der folgenden Tabelle sind die Empfängerobjekte beschrieben, die in Active Directory verwendet werden. Weitere Informationen über die Exchange-Empfängertypen finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

### Empfängerobjekte in Active Directory

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Active Directory-Empfängertyp</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DistributionGroup</p></td>
<td><p>Jedes E-Mail-aktivierte Gruppenobjekt. Diese Typen von Verteilergruppenobjekten stehen zur Verfügung:</p>
<ul>
<li><p><strong>MailUniversalDistributionGroup</strong>   Ein universelles Verteilergruppenobjekt</p></li>
<li><p><strong>MailUniversalSecurityGroup</strong>   Ein universelles Sicherheitsgruppenobjekt (USG), das über eine E-Mail-Adresse verfügt</p></li>
<li><p><strong>MailNonUniversalGroup</strong>   Ein lokales Sicherheitsgruppenobjekt oder globales Sicherheitsgruppenobjekt, das über eine E-Mail-Adresse verfügt</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>DynamicDistributionGroup</p></td>
<td><p>Ein Objekt, das die Active Directory-Klasse <strong>msExchDynamicDistributionList</strong> aufweist. Weitere Informationen finden Sie unter <a href="manage-dynamic-distribution-groups-exchange-2013-help.md">Verwalten dynamischer Verteilergruppen</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Mailbox</p></td>
<td><p>Ein Benutzerobjekt, das eine E-Mail-Adresse und einen definierten <em>Database</em>-Parameter aufweist</p></td>
</tr>
<tr class="even">
<td><p>MailUser</p></td>
<td><p>Ein Benutzerobjekt, das eine E-Mail-Adresse ohne einen definierten <em>Database</em>-Parameter aufweist. Weitere Informationen finden Sie unter <a href="manage-mail-users-exchange-2013-help.md">Verwalten von E-Mail-Benutzern</a>.</p></td>
</tr>
<tr class="odd">
<td><p>MailContact</p></td>
<td><p>Ein Kontaktobjekt, das eine E-Mail-Adresse aufweist. Normalerweise wird ein E-Mail-Kontakt für Empfänger außerhalb der Exchange-Organisation verwendet. Ein E-Mail-Kontakt wird außerdem in gesamtstrukturübergreifenden Exchange-Umgebungen verwendet. Weitere Informationen finden Sie unter <a href="manage-mail-contacts-exchange-2013-help.md">Verwalten von E-Mail-Kontakten</a>.</p></td>
</tr>
<tr class="even">
<td><p>MailPublicFolder</p></td>
<td><p>Ein öffentliches Ordnerobjekt, das eine E-Mail-Adresse aufweist.</p></td>
</tr>
<tr class="odd">
<td><p>MicrosoftExchangeRecipient</p></td>
<td><p>Ein Objekt, das die Active Directory-Klasse <strong>msExchExchangeServerRecipient</strong> aufweist. Weitere Informationen zum Microsoft Exchange-Empfängerobjekt finden Sie unter <a href="recipients-exchange-2013-help.md">Empfänger</a>.</p></td>
</tr>
<tr class="even">
<td><p>SystemAttendantMailbox</p></td>
<td><p>Ein Objekt, das die Active Directory-Klasse <strong>exchangeAdminService</strong> aufweist. Es sollte nur ein Postfach der Systemaufsicht in der Exchange-Organisation vorhanden sein.</p></td>
</tr>
<tr class="odd">
<td><p>SystemMailbox</p></td>
<td><p>Ein Benutzerobjekt, das über eine E-Mail-Adresse verfügt und sich im Container &quot;Microsoft Exchange-Systemobjekte&quot; befindet. Es sollte nur ein Systempostfach für jede Postfachdatenbank in der Exchange-Organisation vorhanden sein.</p></td>
</tr>
</tbody>
</table>


Ein Objekt, das fehlende oder falsch formatierte kritische Eigenschaften enthält, wird von der Active Directory-Abfrage als ungültiges Objekt klassifiziert. Beispielsweise wird ein dynamisches Verteilergruppenobjekt ohne E-Mail-Adresse als ungültig angesehen. Für Nachrichten, die an Empfänger gesendet werden, die als ungültige Objekte klassifiziert wurden, wird ein Unzustellbarkeitsbericht (Non-Delivery Report, NDR) erstellt.

Für jede E-Mail-Adresse wird eine einzelne anfängliche Abfrage für alle möglichen Empfängereigenschaften ausgeführt, wie etwa für die Empfänger-ID, den Empfängertyp, Nachrichtengrenzwerte, E-Mail-Adressen und alternative Empfänger. Die anwendbaren Eigenschaften für den Empfänger werden für die spätere Verwendung zwischengespeichert. Die Empfängerauflösung klassifiziert die Empfänger auf der Grundlage von Ähnlichkeiten in der Weise der Auflösung der Empfänger und der Ähnlichkeit der anwendbaren Empfängereigenschaften.

Der für die Adressauflösung verwendete LDAP-Filter wird wie folgt beschrieben:

  - Für den E-Mail-Adresstyp **EX** basiert der LDAP-Filter auf dem Active Directory-Empfängerattribut **legacyExchangeDN** oder dem Active Directory-Empfängerattribut **proxyAddresses**. Das Active Directory-Attribut **legacyExchangeDN** besitzt Vorrang.

  - Für alle anderen E-Mail-Adresstypen wird das Active Directory-Empfängerattribut **proxyAddresses** als LDAP-Filter verwendet.

Wenn die in der Nachricht verwendete E-Mail-Adresse nicht mit der primären SMTP-Adresse des entsprechenden Active Directory-Objekts übereinstimmt, schreibt das Kategorisierungsmodul die E-Mail-Adresse in der Nachricht so um, dass sie der primären SMTP-Adresse entspricht. Die ursprüngliche E-Mail-Adresse wird im `ORCPT=`-Eintrag im Befehl **RCPT TO:**  im Nachrichtenumschlag gespeichert.

## Nachrichtenbeschränkungen für Absender

Der Wert, der für die Beschränkung der Nachrichtengröße für Absender verwendet wird, entspricht dem Wert des Kopfzeilenfelds **X-MS-Exchange-Organization-OriginalSize:**  im Nachrichtenkopf. Exchange verwendet dieses Kopfzeilenfeld zum Aufzeichnen der ursprünglichen Größe der Nachricht zu dem Zeitpunkt, zu dem sie in der Exchange-Organisation eingegangen ist. Bei jeder Überprüfung der Nachricht im Vergleich zu den angegebenen Beschränkungen der Nachrichtengröße wird der niedrigere Wert der aktuellen Nachrichtengröße oder die ursprüngliche Größe der Nachrichtenkopfzeile verwendet. Die Größe der Nachricht kann sich aufgrund von Inhaltskonvertierung, Codierung sowie Agent-Verarbeitung ändern. Wenn dieses Kopfzeilenfeld nicht vorhanden ist, wird es anhand des aktuellen Werts für die Nachrichtengröße erstellt. Wenn die Nachricht zu umfangreich ist, wird ein NDR erstellt, und die weitere Nachrichtenverarbeitung wird eingestellt.

Der Empfängergrenzwert für Absender wird nur im Transportdienst auf dem ersten Postfachserver durchgesetzt, der die Nachricht verarbeitet. Die ursprüngliche, nicht aufgegliederte Empfängeranzahl des Nachrichtenumschlags wird mit dem Empfängergrenzwert für gesendete Nachrichten verglichen. Die ursprüngliche, nicht aufgegliederte Empfängeranzahl des Nachrichtenumschlags wird verwendet, um die in Microsoft Exchange Server 2003 teilweise bestehenden Übermittlungsprobleme für Nachrichten zu vermeiden, deren geschachtelte Verteilerlisten Remoteserver für die Aufgliederung verwendeten.

Der Nachrichtenabsender und alle Empfänger werden als aufgelöst gekennzeichnet, indem eine erweiterte Eigenschaft in der Nachricht gestempelt wird. Aufgrund dieser erweiterten Eigenschaft kann die Nachricht die Auflösung auf oberster Ebene umgehen, wenn die Nachricht die Empfängerauflösung erneut durchlaufen muss. Eine Nachricht muss die Empfängerauflösung möglicherweise erneut durchlaufen, weil der Microsoft Exchange-Transportdienst erneut gestartet wurde.

Zurück zum Seitenanfang

## Aufgliederung

Die Aufgliederung erfolgt nach der Auflösung auf oberster Ebene. Die Aufgliederung gliedert verschachtelte Empfängerebenen vollständig in einzelne Empfänger auf. Die Aufgliederung erfordert gegebenenfalls mehrere Durchläufe im Aufgliederungsprozess, um alle Empfänger aufzugliedern. Es müssen nicht alle Empfänger aufgegliedert werden. Jedoch müssen alle Empfänger den Aufgliederungsprozess durchlaufen. Der Aufgliederungsprozess setzt darüber hinaus Einschränkungen für empfangene Nachrichten für alle Arten von Empfängern durch.

In der folgenden Liste sind die Arten von Empfängern beschrieben, für die Aufgliederung erforderlich ist:

  - **Verteilergruppen und dynamische Verteilergruppen**   Verteilergruppen werden auf der Grundlage der Active Directory-Eigenschaft **memberOf** aufgegliedert. Dynamische Verteilergruppen werden mithilfe der Active Directory-Abfragedefinition aufgegliedert. Wenn der Parameter *ExpansionServer* für die Gruppe festgelegt ist, wird die Gruppe nicht vom aktuellen Server aufgegliedert. Die Verteilergruppe wird für die Aufgliederung an den angegebenen Server geroutet.
    

    > [!NOTE]
    > Wenn Sie einen bestimmten Transportserver in der Organisation als Server für die Aufgliederung der Verteilerlisten auswählen, hängt die Verwendung der Verteilergruppe von der Verfügbarkeit dieses Servers ab. Wenn der Server für die Aufgliederung der Verteilerlisten nicht erreichbar ist, können die an die Verteilergruppe gesendeten Nachrichten nicht zugestellt werden. Wenn Sie beabsichtigen, bestimmte Server für die Aufgliederung von Verteilerlisten für Ihre Verteilergruppen zu verwenden, sollten Sie das Implementieren von Lösungen für hohe Verfügbarkeit für diese Server in Erwägung ziehen, um die Gefahr von Dienstunterbrechungen zu verringern.



  - **Alternative Empfänger**   Der Parameter *ForwardingAddress* kann für Postfächer und E-Mail-aktivierte Öffentliche Ordner festgelegt werden. Mit dem Parameter *ForwardingAddress* werden alle Nachrichten an den angegebenen alternativen Empfänger umgeleitet. Die Bezeichnung hierfür lautet *weitergeleiteter Empfänger*. Wenn eine alternative Zustelladresse im Parameter *ForwardingAddress* angegeben ist und der Parameter *DeliverToMailboxAndForward* auf `$true` festgelegt ist, wird die Nachricht dem ursprünglichen und dem alternativen Empfänger zugestellt. Dies wird als ein *zugestellter und weitergeleiteter Empfänger* bezeichnet.

  - **Kontaktketten**   Eine *Kontaktkette* ist ein E-Mail-Benutzer oder E-Mail-Kontakt, dessen Parameter *ExternalEmailAddress* auf die E-Mail-Adresse eines anderen Empfängers in der Exchange-Organisation festgelegt ist.

## Erkennung von Empfängerschleifen

Wenn die Verteilergruppen, alternativen Empfänger und Kontaktketten aufgegliedert werden, prüft das Kategorisierungsmodul auf *Empfängerschleifen*. Eine Empfängerschleife ist ein Problem bei der Empfängerkonfiguration, das die Zustellung einer Nachricht an die gleichen Empfänger in einer Endlosschleife bewirkt. In der folgenden Liste werden die verschiedenen Arten von Empfängerschleifen beschrieben:

  - **Harmlose Empfängerschleifen**   Eine harmlose Empfängerschleife führt zu einer erfolgreichen Nachrichtenzustellung. In der folgenden Liste sind zwei Szenarien beschrieben, in denen harmlose Empfängerschleifen auftreten:
    
      - Wenn zwei Verteilergruppen einander als Mitglieder enthalten.
    
      - Wenn Postfächer oder E-Mail-aktivierte Öffentliche Ordner so eingerichtet sind, dass sie aneinander zustellen und weiterleiten. Dieser Fall tritt ein, wenn der Parameter *DeliverToMailboxAndForward* beider Empfänger auf `$true` und der Parameter *ForwardingAddress* auf einen anderen Empfänger festgelegt ist.
    
    Wenn eine harmlose Empfängerschleife erkannt wird, wird die Nachricht an den Empfänger übermittelt, jedoch werden keine weiteren Versuche unternommen, die Nachricht an den gleichen Empfänger zuzustellen.

  - **Unterbrochene Empfängerschleife**   Eine unterbrochene Empfängerschleife kann nicht zu einer erfolgreichen Nachrichtenzustellung führen. Ein Beispiel für eine unterbrochene Empfängerschleife ergibt sich, wenn der Parameter *ForwardingAddress* von Postfächern oder E-Mail-aktivierten Öffentlichen Ordnern jeweils aufeinander festgelegt ist. Wenn das Kategorisierungsmodul eine unterbrochene Empfängerschleife erkennt, werden die Aufgliederungsaktivitäten für den aktuellen Empfänger eingestellt, und es wird ein NDR für den Empfänger erstellt.

Die Erkennung von Empfängerschleifen verhindert nicht die doppelte Zustellung von Nachrichten. Beispielsweise tritt in Verteilergruppe C eine doppelte Zustellung von Nachrichten auf, wenn die folgenden Bedingungen erfüllt sind:

  - Verteilergruppe B und Verteilergruppe C sind Mitglieder von Verteilergruppe A.

  - Verteilergruppe C ist außerdem Mitglied von Verteilergruppe B.

## Umleitung von Übermittlungsberichten für Verteilergruppen

Beim Aufgliedern einer Verteilergruppe wird der Nachrichtentyp überprüft, um zu ermitteln, ob es sich bei der Nachricht um einen Zustellungsbericht handelt. Wenn die Nachricht ein Zustellungsbericht ist, werden die Umleitungseinstellungen der Verteilergruppe überprüft, um zu bestimmen, ob eine Umleitung des Zustellungsberichts erforderlich ist. Es kann sinnvoll sein, die Zustellungsberichte zu unterdrücken, weil die Zustellungsberichte unerwünschte Informationen über die Verteilergruppe und ihre Mitglieder offen legen können.

In der folgenden Liste sind die Umleitungseinstellungen beschrieben, die für Verteilergruppen und dynamische Verteilergruppen verfügbar sind:

  - **ReportToManagerEnabled**   Dieser Parameter ermöglicht das Senden von Zustellungsberichten an den Verteilergruppenleiter. Gültige Werte sind `$true` oder `$false`. Der Standardwert ist `$false`. Bei Verteilergruppen wird der Leiter mithilfe des Parameters *ManagedBy* im Cmdlet **Set-Group** gesteuert. Bei dynamischen Verteilergruppen wird der Leiter mithilfe des Parameters *ManagedBy* im Cmdlet **Set-DynamicDistributionGroup** gesteuert.

  - **ReportToOriginatorEnabled**   Dieser Parameter ermöglicht das Senden von Übermittlungsberichten an die Absender der an diese Verteilergruppe gesendeten E-Mail-Nachrichten. Gültige Werte sind `$true` oder `$false`. Der Standardwert ist `$true`.
    

    > [!NOTE]
    > Die Werte der Parameter <EM>ReportToManagerEnabled</EM> und <EM>ReportToOriginatorEnabled</EM> dürfen nicht beide auf <CODE>$true</CODE> festgelegt sein. Wenn ein Parameter auf <CODE>$true</CODE> festgelegt ist, muss der andere auf <CODE>$false</CODE> festgelegt sein. Die Werte beider Parameter können <CODE>$false</CODE> sein. Dadurch wird die Umleitung aller Zustellungsberichtnachrichten unterdrückt.



In der folgenden Liste werden die verfügbaren Zustellungsberichtnachrichten beschrieben:

  - **Zustellungsbestätigung (Delivery Receipt, DR)**   Dieser Bericht bestätigt, dass eine Nachricht an den beabsichtigten Empfänger zugestellt wurde.

  - **Benachrichtigung über den Zustellungsstatus (Delivery Status Notification, DSN)**   Dieser Bericht beschreibt das Ergebnis eines Versuchs, eine Nachricht zuzustellen. Weitere Informationen zu DSN-Nachrichten finden Sie unter [DSNs und NDRs in Exchange 2013](dsns-and-ndrs-in-exchange-2013-exchange-2013-help.md).

  - **Benachrichtigung über den Nachrichtenstatus (Message Disposition Notification, MDN)**   In diesem Bericht wird der Status einer Nachricht beschrieben, nachdem sie einem Empfänger erfolgreich zugestellt wurde. Eine Lesebenachrichtigung (Read Notification, RN) und eine Nichtlesebenachrichtigung (Non-Read Notification, NRN) sind beide Beispiele für eine MDN-Nachricht. MDN-Nachrichten werden in RFC 2298 definiert und durch das Kopfzeilenfeld **Disposition-Notification-To:**  im Nachrichtenkopf gesteuert. MDN-Einstellungen, die das Kopfzeilenfeld `Disposition-Notification-To:` verwenden, sind mit vielen verschiedenen Nachrichtenservern kompatibel. MDN-Einstellungen können auch mithilfe von MAPI-Eigenschaften in Microsoft Outlook und Exchange definiert werden.

  - **Unzustellbarkeitsbericht (Non-Delivery Report, NDR)**   Dieser Bericht zeigt dem Absender der Nachricht an, dass die Nachricht nicht an die angegebenen Empfänger zugestellt werden konnte.

  - **Nichtlesebenachrichtigung (NRN)**   Dieser Bericht zeigt an, dass eine Nachricht gelöscht wurde, bevor sie gelesen wurde.

  - **Abwesenheit (Out Of Office, OOF)**   Dieser Bericht zeigt an, dass der Empfänger nicht auf E-Mail-Nachrichten antwortet. Das Akronym OOF wird auf das ursprüngliche Microsoft-Messagingsystem zurückgeführt, in dem die entsprechende Benachrichtigung den Namen "Out Of Facility" trug.

  - **Lesebenachrichtigung (RN)**   Dieser Bericht zeigt an, dass eine Nachricht gelesen wurde.

  - **Rückrufbericht**   Dieser Bericht zeigt den Status einer Rückrufanforderung für einen bestimmten Empfänger an. Eine Rückrufanforderung liegt vor, wenn ein Absender versucht, eine gesendete Nachricht mithilfe von Outlook zurückzurufen.

Wenn eine Zustellungsberichtnachricht an eine Verteilergruppe gesendet wird, bewirken die folgenden Einstellungen das Löschen der Berichtsnachricht:

  - Es ist keine Berichtsumleitung festgelegt. Alternativ kann die Berichtsumleitung auf den Absender der Nachricht festgelegt sein.

  - Die Berichtsumleitung ist auf den Verteilergruppenleiter festgelegt, und bei der Zustellungsberichtnachricht handelt es sich nicht um einen Unzustellbarkeitsbericht.

Wenn eine Übermittlungsberichtnachricht an eine Verteilergruppe gesendet wird, wird die Übermittlungsberichtnachricht möglicherweise dem Leiter der Verteilergruppe zugestellt. Dies geschieht, wenn die Berichtsumleitung auf den Leiter der Verteilergruppe festgelegt ist und es sich bei der Berichtsnachricht um einen Unzustellbarkeitsbericht handelt.

Wenn eine Nachricht, die keine Zustellungsberichtnachricht ist, an eine Verteilergruppe gesendet wird, erfolgt die Nachrichtenzustellung an die Mitglieder der Verteilergruppe. Die Einstellungen für die Berichtsanforderung sind in der folgenden Liste zusammengefasst:

  - Wenn die Berichtsumleitung auf den Absender der Nachricht festgelegt ist, werden die Einstellungen für die Berichtsanforderung nicht geändert.

  - Wenn keine Berichtsumleitung festgelegt ist, werden alle Einstellungen für die Berichtsanforderung unterdrückt. Der Eintrag `NOTIFY=NEVER` wird dem Befehl **RCPT TO:**  für jeden Empfänger im Nachrichtenumschlag hinzugefügt.

  - Wenn die Berichtsumleitung auf den Verteilergruppenleiter festgelegt ist, werden alle Einstellungen zur Berichtsanforderung unterdrückt, mit Ausnahme von NDR-Nachrichten, die an den Leiter der Verteilergruppe gesendet werden.

## Nachrichteneinschränkungen für Empfänger

Der Aufgliederungsprozess setzt auch alle Nachrichteneinschränkungen durch, die für Empfänger konfiguriert sind. Diese Einschränkungen können einzeln für jeden Empfänger oder organisationsweit für alle Hub-Transport-Server in der Exchange-Organisation konfiguriert werden. Die folgende Tabelle beschreibt die Nachrichteneinschränkungen, die für Empfänger konfiguriert werden.

### Nachrichteneinschränkungen für Empfänger

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Quelle</th>
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-DistributionGroup</strong></p>
<p><strong>Set-DynamicDistributionGroup</strong></p>
<p><strong>Set-Mailbox</strong></p>
<p><strong>Set-MailContact</strong></p>
<p><strong>Set-MailPublicFolder</strong></p>
<p><strong>Set-MailUser</strong></p>
<p><strong>Set-TransportConfig</strong></p></td>
<td><p><em>MaxReceiveSize</em></p></td>
<td><p>Der Parameter <em>MaxReceiveSize</em> legt als Größe für Nachrichteneinschränkungen, die für Empfänger konfiguriert werden, den Wert des Kopfzeilenfelds <strong>X-MS-Exchange-Organization-OriginalSize:</strong> im Nachrichtenkopf fest. Exchange verwendet dieses Kopfzeilenfeld zum Aufzeichnen der ursprünglichen Größe der Nachricht zu dem Zeitpunkt, zu dem sie in der Exchange-Organisation eingegangen ist. Bei jeder Überprüfung der Nachricht hinsichtlich der angegebenen Beschränkungen der Nachrichtengröße wird der niedrigere Wert der aktuellen Nachrichtengröße oder der ursprünglichen Größe des Nachrichtenkopfs verwendet. Die Größe der Nachricht kann sich aufgrund von Inhaltskonvertierung, Codierung sowie Agent-Verarbeitung ändern. Wenn dieses Kopfzeilenfeld nicht vorhanden ist, wird es aus dem aktuellen Wert für die Nachrichtengröße erstellt. Wenn die Nachricht zu umfangreich ist, wird ein NDR erstellt, und die weitere Nachrichtenverarbeitung wird eingestellt.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-DistributionGroup</strong></p>
<p><strong>Set-DynamicDistributionGroup</strong></p>
<p><strong>Set-Mailbox</strong></p>
<p><strong>Set-MailContact</strong></p>
<p><strong>Set-MailPublicFolder</strong></p>
<p><strong>Set-MailUser</strong></p></td>
<td><p><em>RequireSenderAuthenticationEnabled</em></p></td>
<td><p>Der Parameter <em>RequireSenderAuthenticationEnabled</em> setzt voraus, dass alle Nachrichten, die an den Empfänger gesendet werden, von authentifizierten Absendern stammen. Wenn der Wert dieses Parameters auf <code>$true</code> festgelegt ist, werden Nachrichten von nicht authentifizierten Absendern abgelehnt. Alle Absender, die Nachrichten an das Systempostfach und das Postfach der Systemaufsicht senden, müssen authentifiziert sein.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-DistributionGroup</strong></p>
<p><strong>Set-DynamicDistributionGroup</strong></p>
<p><strong>Set-Mailbox</strong></p>
<p><strong>Set-MailContact</strong></p>
<p><strong>Set-MailPublicFolder</strong></p>
<p><strong>Set-MailUser</strong></p></td>
<td><p><em>AcceptMessagesOnlyFromSendersOrMembers</em></p>
<p><em>RejectMessagesFromSendersOrMembers</em></p></td>
<td><p>Der Parameter <em>AcceptMessagesOnlyFromSendersOrMembers</em> gibt die Absender oder Verteilergruppen an, deren Mitglieder Nachrichten an den Empfänger senden dürfen. Beachten Sie, dass dieser Parameter die Funktionalität der älteren Parameter <em>AcceptMessagesOnlyFrom</em> und <em>AcceptMessagesOnlyFromDLMembers</em> miteinander verbindet.</p>
<p>Der Parameter <em>RejectMessagesFromSendersOrMembers</em> gibt die Absender oder Verteilergruppen an, deren Mitglieder keine Nachrichten an den Empfänger senden dürfen. Beachten Sie, dass dieser Parameter die Funktionalität der älteren Parameter <em>RejectMessagesFrom</em> und <em>RejectMessagesFromDLMembers</em> miteinander verbindet.</p>
<p>Das Kategorisierungsmodul überprüft die Empfängerberechtigungen in zwei Phasen. In der ersten Phase wird bestimmt, ob der Absender im Parameter <em>AcceptOnlyMessagesFromSendersOrMembers</em> oder <em>RejectMessagesFromSendersOrMembers</em> vorhanden ist. Wenn der Absender in keinem der Parameter zu finden ist, werden die Verteilergruppen in diesen Parametern vollständig aufgegliedert. Die vollständige Aufgliederung der Verteilergruppen kann einige Zeit in Anspruch nehmen. Es empfiehlt sich, die Tiefe verschachtelter Verteilergruppen in diesen Parametern auf ein Mindestmaß zu beschränken.</p></td>
</tr>
</tbody>
</table>


Bestimmte Arten von Nachrichten, die von authentifizierten Absender gesendet werden, sind von Einschränkungen ausgenommen. In der folgenden Liste sind die Nachrichten beschrieben, die von Empfängereinschränkungen ausgenommen sind:

  - **Alle Nachrichten, die vom Empfänger "Microsoft Exchange" gesendet werden   **Diese Nachrichten schließen DSN-Meldungen, Journalberichte, Kontingentmeldungen und andere vom System generierte Nachrichten ein, die an interne Absender von Nachrichten gesendet werden. Weitere Informationen über den Microsoft-Empfänger finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

  - **Alle Nachrichten, die von der externen Postmasteradresse gesendet werden**   Diese Nachrichten schließen DSN-Meldungen und andere vom System generierte Nachrichten ein, die an externe Absender von Nachrichten gesendet werden. Weitere Informationen zu externen Postmasteradressen finden Sie unter [Konfigurieren der externen Postmasteradresse](configure-the-external-postmaster-address-exchange-2013-help.md).

Bestimmte Typen von Nachrichten werden blockiert, wenn sie von der Exchange-Organisation an externe Domänen gesendet werden. Die Einstellungen werden von den folgenden Parametern im Cmdlet **Set-RemoteDomain** gesteuert:

  - *AllowedOOFType*

  - *AutoForwardEnabled*

  - *AutoReplyEnabled*

  - *DeliveryReportEnabled*

  - *NDREnabled*

Weitere Informationen finden Sie unter [Remotedomänen](remote-domains-exchange-2013-help.md).

Zurück zum Seitenanfang

## Verzweigung und Steuerung der Empfängeraufgliederung

Da die gesamte Liste der Nachrichtenempfänger von der Empfängerauflösung aufgegliedert und aufgelöst wird, entstehen Situationen, in denen verschiedene Kopien derselben Nachricht erstellt werden müssen. Diese Situationen werden durch die folgenden Szenarien beschrieben:

  - **Wenn für die Nachrichtenempfänger unterschiedliche Nachrichteneinstellungen erforderlich sind**   Nachrichteneigenschaften, wie etwa Lesebestätigungen, müssen für einige Empfänger aktiviert und für andere blockiert werden. Das Erstellen einer neuen Version der Nachricht mit geringfügig von der Originalnachricht abweichenden Eigenschaften wird als *Verzweigung* bezeichnet.

  - **Zum Einschränken der Anzahl der Umschlagsempfänger in einer einzelnen Nachricht**   Der Empfängeraufgliederungsprozess kann Tausende Einzelempfänger generieren, wenn große Verteilergruppen aufgegliedert werden. Anstelle eines einzelnen Exemplars der Nachricht mit Tausenden von Umschlagsempfängern werden in Exchange mehrere Exemplare derselben Nachricht mit einer eingeschränkten Anzahl von Umschlagsempfängern erstellt.

## Verzweigung

Die Empfängerauflösung verzweigt eine Nachricht, wenn die folgenden Bedingungen erfüllt sind:

  - Wenn der Nachrichtenabsender in **MAIL FROM:**  im Nachrichtenumschlag aktualisiert wird. Dies ist beispielsweise der Fall, wenn der Parameter *ReportToManagerEnabled* für eine Verteilergruppe den Wert `$true` aufweist.

  - Wenn Nachrichten für die automatische Antwort, wie etwa DSNs, OOF-Nachrichten und Rückrufberichte, unterdrückt werden müssen.

  - Wenn alternative Empfänger aufgegliedert werden.

  - Wenn dem Nachrichtenkopf ein Kopfzeilenfeld **Resent-From:**  hinzugefügt werden muss. "Resent"-Kopfzeilenfelder sind Informationskopfzeilenfelder, die zum Bestimmen verwendet werden können, ob eine Nachricht von einem Benutzer weitergeleitet wurde. Resent-Kopfzeilenfelder werden verwendet, damit die Nachricht dem Empfänger so erscheint, als wäre sie direkt vom ursprünglichen Absender gesendet worden. Der Empfänger kann den Nachrichtenkopf anzeigen und ermitteln, wer die Nachricht weitergeleitet hat. Resent-Kopfzeilenfelder sind im Abschnitt 3.6.6 von RFC 2822 definiert.

  - Wenn der Verlauf der Aufgliederung der Verteilergruppe übermittelt werden muss.

## Steuern der Empfängeraufgliederung

Wenn die Anzahl der aufgegliederten Empfänger zu groß ist, teilt das Kategorisierungsmodul die Nachricht in mehrere Exemplare auf. Dieser Vorgang wird ausgeführt, um den Ressourcenbedarf des Systems während der Aufgliederung von Nachrichten zu verringern. Die maximale Anzahl von Umschlagsempfängern in einer Nachricht wird mithilfe des Schlüssels *ExpansionSizeLimit* in der Anwendungskonfigurationsdatei `%ExchangeInstallPath%Bin\EdgeTransport.exe.config` festgelegt. Der Standardwert ist 1000.


> [!WARNING]
> Es wird empfohlen, den Wert des Schlüssels <EM>ExpansionSizeLimit</EM> für einen Exchange-Transportserver in einer Produktionsumgebung nicht zu ändern.



Zurück zum Seitenanfang

## Empfängerauflösungsdiagnose

Berichts- und Diagnoseínformationen für die Empfängerauflösung werden über Leistungsindikatoren und Protokolleinträge der Nachrichtenverfolgung bereitgestellt. Diese Quellen können Sie beim Identifizieren und Diagnostizieren von Problemen bei der Empfängerauflösung unterstützen.

## Leistungsindikatoren der Empfängerauflösung

In der folgenden Tabelle werden die für Empfängerauflösung verfügbaren Leistungsindikatoren beschrieben.

### Leistungsindikatoren der Empfängerauflösung

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Indikatorname</th>
<th>Anzeigename</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AmbiguousRecipientsTotal</p></td>
<td><p>Nicht eindeutige Empfänger</p></td>
<td><p>Dies ist die Gesamtanzahl von nicht eindeutigen Empfängern, die während der Empfängerauflösung erkannt wurden. Nicht eindeutige Empfänger sind verschiedene Empfänger, die übereinstimmende Active Directory-Attribute <strong>legacyExchangeDN</strong> oder <strong>proxyAddresses</strong> aufweisen.</p></td>
</tr>
<tr class="even">
<td><p>AmbiguousSendersTotal</p></td>
<td><p>Nicht eindeutige Absender</p></td>
<td><p>Dies ist die Anzahl der nicht eindeutigen Absender, die während der Empfängerauflösung erkannt wurden. Nicht eindeutige Absender sind verschiedene Absender, die übereinstimmende Active Directory-Attribute <strong>legacyExchangeDN</strong> oder <strong>proxyAddresses</strong> aufweisen.</p></td>
</tr>
<tr class="odd">
<td><p>FailedRecipientsTotal</p></td>
<td><p>Empfängerfehler</p></td>
<td><p>Dies ist die Anzahl der Empfängerfehler, die während der Empfängerauflösung erkannt wurden.</p></td>
</tr>
<tr class="even">
<td><p>LoopRecipientsTotal</p></td>
<td><p>Schleifenempfänger</p></td>
<td><p>Dies ist die Anzahl der Empfänger, bei deren Empfängerauflösung ein Fehler aufgrund von Empfängerschleifen aufgetreten ist.</p></td>
</tr>
<tr class="odd">
<td><p>MessagesChippedTotal</p></td>
<td><p>Abgetrennte Nachrichten</p></td>
<td><p>Dies ist die Gesamtanzahl von Exemplaren der gleichen Nachricht, die während der Empfängerauflösung erstellt wurden, um die Anzahl der Umschlagsempfänger in einer einzelnen Nachricht zu steuern. In Exchange wird dieser Vorgang als <em>Abtrennen</em> bezeichnet.</p></td>
</tr>
<tr class="even">
<td><p>MessagesCreatedTotal</p></td>
<td><p>Erstellte Nachrichten</p></td>
<td><p>Dies ist die Anzahl der Nachrichten, die während der Empfängerauflösung erstellt wurden.</p></td>
</tr>
<tr class="odd">
<td><p>MessagesRetriedTotal</p></td>
<td><p>Nachrichten mit Wiederholungsversuchen</p></td>
<td><p>Dies ist die Anzahl der Nachrichten, für die während der Empfängerauflösung ein Wiederholungsversuch geplant wurde.</p></td>
</tr>
<tr class="even">
<td><p>UnresolvedOrgRecipientsTotal</p></td>
<td><p>Nicht aufgelöste Organisationsempfänger</p></td>
<td><p>Dies ist die Anzahl der nicht aufgelösten Empfänger von einer autoritativen Domäne, die während der Empfängerauflösung erkannt wurden.</p></td>
</tr>
<tr class="odd">
<td><p>UnresolvedOrgSendersTotal</p></td>
<td><p>Nicht aufgelöste Organisationsabsender</p></td>
<td><p>Dies ist die Anzahl der nicht aufgelösten Absender von einer autoritativen Domäne, die während der Empfängerauflösung erkannt wurden.</p></td>
</tr>
</tbody>
</table>


## Ereignisse der Empfängerauflösung im Protokoll der Nachrichtenverfolgung

In der folgenden Tabelle werden die Ereignisse der Empfängerauflösung beschrieben, die im Protokoll der Nachrichtenverfolgung erfasst werden.

### Ereignisse der Empfängerauflösung im Protokoll der Nachrichtenverfolgung

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Ereignis der Nachrichtenverfolgung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EXPAND</p></td>
<td><p>Dieses Ereignis zeigt an, dass eine Verteilergruppe aufgegliedert wurde.</p></td>
</tr>
<tr class="even">
<td><p>REDIRECT</p></td>
<td><p>Mit diesem Ereignis wird angegeben, dass eine an einen Postfachempfänger oder einen Empfänger eines E-Mail-aktivierten Öffentlichen Ordners gesendete Nachricht entsprechend der Angabe im Parameter <em>ForwardingAddress</em> an einen alternativen Empfänger umgeleitet wurde.</p></td>
</tr>
<tr class="odd">
<td><p>RESOLVE</p></td>
<td><p>Dieses Ereignis zeigt an, dass die E-Mail-Adresse eines Empfängers in die primäre SMTP-E-Mail-Adresse des entsprechenden Active Directory-Empfängerobjekts geändert wurde.</p></td>
</tr>
<tr class="even">
<td><p>TRANSFER</p></td>
<td><p>Dieses Ereignis zeigt an, dass eine Verzweigung oder Abtrennung einer Nachricht aufgetreten ist.</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zur Nachrichtenverfolgung finden Sie unter [Nachrichtenverfolgung](message-tracking-exchange-2013-help.md).


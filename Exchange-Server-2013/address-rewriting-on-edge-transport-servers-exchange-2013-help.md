---
title: 'Adressumschreibung auf Edge-Transport-Servern: Exchange 2013 Help'
TOCTitle: Adressumschreibung auf Edge-Transport-Servern
ms:assetid: 23f1eaf6-247a-4671-ad72-aae19d9b511d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996806(v=EXCHG.150)
ms:contentKeyID: 61061218
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Adressumschreibung auf Edge-Transport-Servern

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Durch Adressumschreibungen werden E-Mail-Adressen von Senden und Empfängern in Nachrichten geändert, die über einen Edge-Transport-Server in Ihrer Organisation ankommen oder diese verlassen. Zwei Transport-Agents auf dem Edge-Transport-Server stellen die Umschreibungsfunktion bereit: der Adressumschreibungs-Agent für eingehende Nachrichten und der Adressumschreibungs-Agent für ausgehende Nachrichten. Der Hauptgrund für die Adressumschreibung in ausgehenden Nachrichten ist, dass externen Empfängern eine einzelne konsistente E-Mail-Domäne präsentiert werden soll. Der Hauptgrund für die Adressumschreibung in eingehenden Nachrichten ist, dass die Nachrichten an den korrekten Empfänger geleitet werden sollen.

Über den *Adressumschreibungseintrag*, den Sie erstellen, werden die internen (die E-Mail-Adressen, die Sie ändern möchten) und die externen Adressen (die gewünschten endgültigen E-Mail-Adressen) festgelegt. Sie können angeben, ob E-Mail-Adressen in eingehenden und ausgehenden Nachrichten oder nur in ausgehenden Nachrichten umgeschrieben werden sollen. Sie können Adressumschreibungseinträge für einen einzelnen Benutzer (chris@contoso.com in support@contoso.com), für alle Benujtzer in einer einzelnen Domäne (contoso.com in fabrikam.com) oder für Benutzer in mehreren Unterdomänen mit Ausnahmen ändern (\*fabrikam.com in contoso.com, außer legal.fabrikam.com).


> [!IMPORTANT]
> Unabhängig davon, wie Sie die Adressumschreibung verwenden möchten, müssen Sie prüfen, ob die resultierenden E-Mail-Adressen in Ihrem Unternehmen eindeutig sind, sodass Sie keine Duplikate erzeugen. Der Grund dafür ist, dass die Eindeutigkeit einer umgeschriebenen E-Mail-Adresse bei der Adressumschreibung selbst nicht geprüft wird.



**Inhalt**

Szenarien für das Umschreiben von Adressen

Eigenschaften der Nachricht durch Adressumschreibung geändert

Was durch die Adressumschreibung nicht geändert wird

Überlegungen zur Adressumschreibung in ausgehenden Nachrichten

Überlegungen zur Adressumschreibung in eingehenden und ausgehenden Nachrichten

Überlegungen zur Adressumschreibung in mehreren Domänen

Priorität der Adressumschreibungseinträge

Digital signierte, verschlüsselte und durch Rechte geschützte Nachrichten

## Szenarien für das Umschreiben von Adressen

Die folgenden Szenarien sind Beispiele dafür, wie Sie die Adressumschreibung verwenden können:

  - **Gruppenkonsolidierung**   Einige Organisationen segmentieren ihre internen Geschäftssparten in separate Domänen, die auf Geschäfts- oder technischen Anforderungen basieren. Diese Konfiguration kann jedoch dazu führen, dass E-Mail-Nachrichten von separaten Gruppen oder sogar separaten Organisationen zu stammen scheinen.
    
    Das folgende Beispiel zeigt, wie eine Organisation (Contoso, Ltd.) ihre Unterdomänen vor externen Empfängern verbergen könnte:
    
      - Ausgehende Nachrichten von den Domänen Northamerica.contoso.com, Europe.contoso.com und Asia.contoso.com werden so umgeschrieben, als würden sie alle von der Domäne Contoso.com stammen. Alle Nachrichten werden umgeschrieben, während sie Edge-Transport-Servercomputer durchlaufen, die SMTP-Verbindungen zwischen der gesamten Organisation und dem Internet bereitstellen.
    
      - Eingehende Nachrichten an contoso.com-Empfänger werden über den Edge-Transport-Server an einen Postfachserver umgeleitet. Die Nachricht wird auf Grundlage der Proxyadresse, die im Postfach des Empfängers konfiguriert ist, an den korrekten Empfänger gesendet.

  - **Fusionen und Übernahmen**   Ein übernommenes Unternehmen kann auch weiterhin als separate Geschäftseinheit geführt werden, Sie können jedoch die Adressumschreibung verwenden, damit sich die beiden Organisationen so darstellen, als handele es sich um eine integrierte Organisation.
    
    Das folgende Beispiel zeigt, wie Contoso, Ltd. die E-Mail-Domäne des neu übernommenen Unternehmens Fourth Coffee verbergen kann:
    
      - Contoso, Ltd. wünscht, dass alle ausgehenden Nachrichten aus der Exchange-Organisation von Fourth Coffee so aussehen, als stammten sie von Contoso.com. Alle Nachrichten aus beiden Organisationen werden über die Edge-Transport-Server bei Contoso, Ltd. gesendet, wo die E-Mail-Nachrichten von *jemand*@fourthcoffee.com in *jemand@contoso.com* umgeschrieben werden.
    
      - Eingehende Nachrichten an *jemand*@contoso.com werden umgeschrieben und an die Postfächer von *jemand*@fourthcoffee.com geleitet. Eingehende Nachrichten, die an *jemand*@fourthcoffee.com gesendet werden, werden direkt an die E-Mail-Server von Fourth Coffee weitergeleitet.

  - **Partner**   Viele Organisationen arbeiten mit externen Partnern zusammen, um Dienste für ihre Kunden, andere Organisationen oder die eigene Organisation bereitzustellen. Um Verwirrung zu vermeiden, kann die Organisation die E-Mail-Domäne der Partnerorganisation durch ihre eigene E-Mail-Domäne ersetzen.
    
    Das folgende Beispiel zeigt, wie Contoso, Ltd. die E-Mail-Domäne eines Partners verbergen kann:
    
      - Contoso, Ltd. stellt Support für die größere Organisation Wingtip Toys zur Verfügung. Wingtip Toys möchte seinen Kunden ein einheitliches E-Mail-Erscheinungsbild bieten und verlangt, dass alle Nachrichten, die vom Supportpersonal bei Contoso, Ltd. stammen, so aussehen, als wären sie von Wingtip Toys gesendet worden. Alle ausgehenden Nachrichten, die sich auf Wingtip Toys beziehen, werden über deren Edge-Transport-Server gesendet, und alle Contoso.com-Adressen werden in Wingtiptoys.com-Adressen umgeschrieben.
    
      - Eingehende Nachrichten für support@wingtiptoys.com werden von den Edge-Transport-Servern von Wingtip Toys akzeptiert, umgeschrieben und dann an die E-Mail-Adresse support@contoso.com weitergeleitet.

Zurück zum Seitenanfang

## Eigenschaften der Nachricht durch Adressumschreibung geändert

Eine standardmäßige SMTP-E-Mail besteht aus einem *Nachrichtenumschlag* und dem Nachrichteninhalt. Der Nachrichtenumschlag enthält Informationen, die für die Übermittlung und Zustellung der Nachricht zwischen SMTP-Mailservern erforderlich sind. Der Nachrichteninhalt enthält Nachrichtenkopffelder (zusammenfassend als *Nachrichtenkopf* bezeichnet) sowie den Nachrichtentext. Der Nachrichtenumschlag wird in RFC 2821 und der Nachrichtenkopf in RFC 2822 beschrieben.

Wenn ein Absender eine E-Mail verfasst und zur Zustellung übermittelt, enthält die Nachricht die grundlegenden Informationen, die erforderlich sind, um die SMTP-Standards zu erfüllen. Hierzu gehören beispielsweise ein Absender, ein Empfänger, Datum und Uhrzeit der Erstellung der Nachricht sowie optional eine Betreffzeile und ein Nachrichtentext. Diese Informationen sind in der Nachricht selbst und laut Definition im Nachrichtenkopf enthalten.

Der Mailserver des Absenders erzeugt einen Nachrichtenumschlag für die Nachricht, indem er die im Nachrichtenkopf gefundenen Sender- und Empfänger-Informationen verwendet. Anschließend wird die Nachricht zur Übermittlung an den Mailserver des Empfängers ins Internet gesendet. Empfänger bekommen den Nachrichtenumschlag nicht angezeigt, da er vom Nachrichtenübermittlungsprozess generiert wird und nicht tatsächlicher Bestandteil der Nachricht ist.

Durch Adressumschreibung wird eine E-Mail-Adresse geändert, indem bestimmte Felder im Nachrichtenkopf oder im Nachrichtenumschlag umgeschrieben werden. Durch Adressumschreibung werden einige Felder in ausgehenden Nachrichten, aber nur ein Feld in eingehenden Nachrichten geändert. Die folgende Tabelle zeigt, welche SMTP-Kopfzeilenfelder für ausgehende und eingehende Nachrichten umgeschrieben werden.

### In ausgehenden und eingehenden Nachrichten umgeschriebene Nachrichtenfelder

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Feld</th>
<th>Ort</th>
<th>Ausgehende Nachrichten</th>
<th>Eingehende Nachrichten</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>MAIL FROM</strong></p></td>
<td><p>Nachrichtenumschlag</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="even">
<td><p><strong>RCPT TO</strong></p></td>
<td><p>Nachrichtenumschlag</p></td>
<td><p>Nicht umgeschrieben</p></td>
<td><p>Umgeschrieben</p></td>
</tr>
<tr class="odd">
<td><p><strong>An</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="even">
<td><p><strong>Cc</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="odd">
<td><p><strong>Von</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="even">
<td><p><strong>Sender</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="odd">
<td><p><strong>Reply-To</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="even">
<td><p><strong>Return-Receipt-To</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="odd">
<td><p><strong>Disposition-Notification-To</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="even">
<td><p><strong>Resent-From</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
<tr class="odd">
<td><p><strong>Resent-Sender</strong></p></td>
<td><p>Nachrichtenkopf</p></td>
<td><p>Umgeschrieben</p></td>
<td><p>Nicht umgeschrieben</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Was durch die Adressumschreibung nicht geändert wird

Durch die Adressumschreibung werden keine Felder im Nachrichtenkopf geändert, die die SMTP-Funktion beeinträchtigen könnten. Die Veränderujng bestimmter Felder im Nachrichtenkopf könnte sich z. B. auf die Nachrichtenschleifenerkennung auswirken, die Signatur ungültig machen oder dazu führen, dass eine durch Rechte geschützte Nachricht unlesbar wird. Deshalb werden die folgenden Kopffelder durch die Adressumschreibung nicht verändert.

  - **Return-Path**

  - **Received**

  - **Message-ID**

  - **X-MS-TNEF-Correlator**

  - **Content-Type Boundary=string**

  - Kopffelder, die sich in MIME-Nachrichtentext befinden

Bei der Adressumschreibung werden Domänen ignoriert, die nicht von der Exchange-Organisation kontrolliert werden. Mit anderen Worten: Es werden keine Kopffelder umgeschrieben, die Domänen enthalten, für die die Exchange-Organisation nicht autorisierend ist. Das Umschreiben solcher Domänen würde eine unkontrollierbare Form der Nachrichtenweiterleitung bewirken.

Bei der Adressumschreibung werden außerdem nicht die Kopfzeilenfelder von Nachrichten geändert, die in andere Nachrichten eingebettet sind. Absender und Empfänger erwarten, dass eingebettete Nachrichten unter der Voraussetzung unversehrt bleiben und ohne Änderungen zugestellt werden, dass die Nachricht keine Transportregeln auslöst, die zwischen dem Absender und dem Empfänger implementiert sind.

Zurück zum Seitenanfang

## Überlegungen zur Adressumschreibung in ausgehenden Nachrichten

Durch die Beschränkung der Adressumschreibung auf ausgehende Nachrichten auf einem Edge-Transport-Server wird die E-Mail-Adresse des Absenders geändert, sobald die Nachricht die Exchange-Organisation verlässt. Sie können die Adressumschreibung in ausgehenden Nachrichten für einen einzelnen Benutzer (chris@contoso.com in support@contoso.com) oder für alle Benutzer in einer einzelnen Domäne (contoso.com in fabrikam.com) konfigurieren. Es ist erforderlich, die Adressumschreibung nur in ausgehenden Nachrichten für Benutzer in mehreren Unterdomänen (\*.fabrikam.com in .contoso.com) zu konfigurieren.

Die umgeschriebene E-Mail-Adresse muss für die betreffenden Empfänger als Proxyadresse konfiguriert werden. Beispiel: Wenn "laura@sales.contoso.com" in "laura@contoso.com" umgeschrieben wird, muss die Proxyadresse "laura@contoso.com" in Lauras Postfach konfiguriert werden. Dadurch können Antworten und eingehende Nachrichten richtig zugestellt werden.

Zurück zum Seitenanfang

## Überlegungen zur Adressumschreibung in eingehenden und ausgehenden Nachrichten

Durch Adressumschreibung in eingehenden und ausgehenden Nachrichten, auch als *bidirektionale* Adressumschreibung bezeichnet, auf einem Edge-Transport-Server werden die E-Mail-Adresse des Absenders in Nachrichten, die die Exchange-Organisation verlassen, uind die E-Mail-Adresse des Empfängers in Nachrichten, die in der Exchange-Organisation ankommen, geändert.

Sie können die Adressumschreibung in ausgehenden Nachrichten für einen einzelnen Benutzer (chris@contoso.com in support@contoso.com) und für alle Benutzer in einer einzelnen Domäne (contoso.com in fabrikam.com) konfigurieren. Sie können die bidirektionale Adressumschreibung für Benutzer in mehreren Unterdomänen (\*.fabrikam.com in contoso.com) umschreiben.

Zurück zum Seitenanfang

## Überlegungen zur Adressumschreibung in mehreren Domänen

Wenn Sie mehrere interne Domänen oder Unterdomänen zu einer einzelnen externen Domäne zusammenfassen, müssen Sie die folgenden Faktoren bedenken:

  - **Überprüfung auf eindeutige Aliase**   Alle E-Mail-Aliase (der Teil der E-Mail-Adresse, der links vom Symbol @ steht) müssen in allen Unterdomänen eindeutig sein. Wenn z. B. eine Adresse joe@sales.contoso.com vorhanden ist, darf die Adresse joe@marketing.contoso.com nicht vorhanden sein, da die umgeschriebene Adresse für beide Benutzer joe@contoso.com lauten würde.

  - **Hinzufügen von Proxyadressen**   Die umgeschriebene E-Mail-Adresse muss als Proxyadresse für alle betroffenen Absender in den betreffenden Domänen konfiguriert werden. Wenn z. B. die Adresse joe@sales.contoso.com in joe@contoso.com umgeschrieben wird, muss die Proxyadresse joe@contoso.com zu Joes Postfach hinzugefügt werden. Dadurch können Antworten und eingehende Nachrichten richtig zugestellt werden.

  - **Mail-Kontakte für Nicht-Exchange-Organisationen**   Wenn Sie E-Mail-Adressen aus einem Nicht-Exchange-System umschreiben, müssen Sie E-Mail-Kontakte in Exchange erzeugen, um die Benutzer im Nicht-Exchange-E-Mail-System darzustellen. Diese E-Mail-Kontakte müssen die ursprünglichen E-Mail-Adressen und die umgeschriebenen E-Mail-Adressen enthalten. Wenn z. B. die Adresse joe@unix.contoso.com in joe@contoso.com umgeschrieben wird, müssen Sie einen neuen E-Mail-Kontakt mit joe@unix.contoso.com als externer E-Mail-Adresse und joe@contoso.com als Proxyadresse erstellen.

## Überprüfung auf eindeutige Aliase

Wenn Sie E-Mail-Adressen in mehreren Unterdomänen umschreiben, müssen Sie sicherstellen, dass alle E-Mail-Aliase in allen Unterdomänen eindeutig sind. Sehen Sie sich z. B. die folgende Konfiguration an:

Die folgenden Benutzer befinden sich in den Unterdomänen sales.contoso.com, marketing.contoso.com und research.contoso.com:

  - maria@sales.contoso.com

  - chris@sales.contoso.com

  - david@marketing.contoso.com

  - brian@marketing.contoso.com

  - chris@research.contoso.com

  - adam@research.contoso.com

Angenommen, Sie möchten die Unterdomänen sales.contoso.com, marketing.contoso.com und research.contoso.com in die Einzeldomäne contoso.com umschreiben.

Wenn die E-Mail-Adressen in allen Unterdomänen umgeschrieben werden, kommt es zu einem Konflikt zwischen chris@sales.contoso.com und chris@research.contoso.com, da beide E-Mail-Adressen in chris@contoso.com umgeschrieben werden. Um diese Situation aufzulösen, müssen Sie die E-Mail-Adresse eines der betreffenden Empfänger ändern. Sie können z. B. chris@research.contoso.com in christopher@research.contoso.com ändern, sodass die E-Mail-Adresse in christopher@contoso.com umgeschrieben wird.

Zurück zum Seitenanfang

## Priorität der Adressumschreibungseinträge

Wenn die E-Mail-Adresse mit mehreren Adressumschreibungseinträgen übereinstimmt, wird die E-Mail-Adresse nur einmal umgeschrieben und dafür die beste Übereinstimmung verwendet. In der folgenden Liste wird die Reihenfolge der Einträge zum Umschreiben von Adressen von der höchsten Priorität bis zur niedrigsten Priorität dargestellt:

1.  **Einzelne E-Mail-Adressen**   Ein Adressumschreibungseintrag wird für die Umschreibung der E-Mail-Adresse john@contoso.com in support@contoso.com konfiguriert.

2.  **Zuordnung von Domänen oder Unterdomänen**   Ein Adressumschreibungseintrag wird für die Umschreibung aller E-Mail-Adressen mit contoso.com in northwindtraders.com oder aller E-Mail-Adressen mit sales.contoso.com in contoso.com konfiguriert.

3.  **Domänenzusammenfassung**   Ein Adressumschreibungseintrag wird für die Umschreibung aller E-Mail-Adressen mit \*.contoso.com in contoso.com konfiguriert.

Betrachten wir z. B. einen Edge-Transport-Server, für den die folgenden Adressumschreibungseinträge für ausgehende Nachrichten konfiguriert sind:

  - \*.contoso.com-E-Mail-Adressen werden in contoso.com umgeschrieben

  - japan.sales.contoso.com-E--Mail-Adressen werden in contoso.jp umgeschrieben

Wenn masato@japan.sales.contoso.com eine E-Mail-Nachricht sendet, wird die Adresse in masato@contoso.jp umgeschrieben, da dieser Eintrag am meisten mit dem Absender der E-Mail-Adresse übereinstimmt.

Zurück zum Seitenanfang

## Digital signierte, verschlüsselte und durch Rechte geschützte Nachrichten

Das Umschreiben von Adressen sollte sich auf die meisten signierten, verschlüsselten oder durch Rechte geschützten Nachrichten nicht auswirken. Wenn die Adressumschreibung den Sicherheitsstatus dieser Arten von Nachrichten in irgendeiner Weise ändern oder beeinträchtigen würde, findet die Adressumschreibung nicht statt.

Die folgenden Werte können umgeschrieben werden, da die Informationen nicht Teil der Nachrichtensignierung, der Verschlüsselung oder des Schutzes durch Rechte sind:

  - Felder im Nachrichtenumschlag

  - Nachrichtentext-Kopfzeilen der obersten Stufe

Die folgenden Werte werden nicht umgeschrieben, da die Informationen Teil der Nachrichtensignierung, der Verschlüsselung oder des Schutzes durch Rechte sind:

  - Kopffelder, die sich in MIME-Nachrichtentext befinden und möglicherweise signiert sind

  - Der Begrenzungszeichenfolge-Parameter des MIME-Inhaltstyps

Zurück zum Seitenanfang


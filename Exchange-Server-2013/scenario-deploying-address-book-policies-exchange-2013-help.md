---
title: 'Szenario: Bereitstellen von Adressbuchrichtlinien: Exchange 2013 Help'
TOCTitle: 'Szenario: Bereitstellen von Adressbuchrichtlinien'
ms:assetid: 6ac3c87d-161f-447b-afb2-149ae7e3f1dc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657455(v=EXCHG.150)
ms:contentKeyID: 50475906
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Szenario: Bereitstellen von Adressbuchrichtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

## Bereitstellungsszenarien

Die folgenden drei Szenarien beschreiben mögliche Bereitstellungslösungen für drei verschiedene Organisationsarten. Zwar gibt es wesentlich mehr Szenarien, hier werden jedoch nur die gängigsten erläutert. Die Adresslisten und globalen Adresslisten (GALs) in diesen Szenarien wurden anhand von Filtern wie beispielsweise benutzerdefinierten Attributen erstellt, welche die Objekte logisch gruppieren.

## Szenario 1: Zwei separate Unternehmen – eine Exchange-Organisation

Dieses Szenario kann für Regierungsbehörden, Unternehmensbereiche oder Abteilungen angewendet werden, in denen eine Infrastruktur gemeinsam genutzt wird, die jedoch nicht über eine Mitarbeiterkette und gemeinsame Mitarbeiter verfügen. Darüber hinaus stellen die Bereiche keine besonderen Anforderungen an Sicherheit oder Datenschutz. In diesem Szenario werden zwei Adressbuchrichtlinien erstellt, mit denen Mitarbeiter nur Mitglieder der gleichen Organisation sehen können, wenn sie die globale Adressbuchrichtlinie oder die Mitgliedschaft in anderen Bereichsgruppen anzeigen. Darüber hinaus ist kein Benutzer Mitglied in einer Verteilergruppe, die sich über die gesamte Organisation erstreckt.

![Adressbuchrichtlinien von zwei separaten Unternehmen](images/JJ657455.b4fc82da-a659-4ade-ba33-d55d90dcf204(EXCHG.150).gif "Adressbuchrichtlinien von zwei separaten Unternehmen")

Die Adressbuchrichtlinien für Contoso und Humungous Insurance wurden unter Verwendung der folgenden Adresslisten, globalen Adresslisten, Raumlisten und Offlineadressbücher erstellt. Die Offlineadressbücher wurden unter Verwendung eines Empfängerfilters erstellt, der die Objekte mithilfe eines Filters wie beispielsweise eines benutzerdefinierten Attributs gruppiert. Da die beiden Unternehmen getrennt sind und nicht interagieren, sind keine gemeinsamen Adresslisten vorhanden.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Contoso</p></td>
<td><p>Humungous Insurance</p></td>
</tr>
<tr class="even">
<td><p>Adresslisten</p></td>
<td><p>AL_CON_Gruppen</p>
<p>AL_CON_Benutzer</p>
<p>AL_CON_Kontakte</p></td>
<td><p>AL_HI_Gruppen</p>
<p>AL_HI_Benutzer</p>
<p>AL_HI_Kontakte</p></td>
</tr>
<tr class="odd">
<td><p>Globale Adressliste</p></td>
<td><p>GAL_CON</p></td>
<td><p>GAL_HI</p></td>
</tr>
<tr class="even">
<td><p>Raumadressliste</p></td>
<td><p>AL_CON_Raeume</p></td>
<td><p>AL_HI_Raeume</p></td>
</tr>
<tr class="odd">
<td><p>Offlineadressbuch (OAB)</p></td>
<td><p>OAB_CON</p></td>
<td><p>OAB_HI</p></td>
</tr>
</tbody>
</table>


## Szenario 2: Zwei Unternehmen mit einem gemeinsamen CEO

In diesem Szenario nutzen Fabrikam und Tailspin Toys die gleiche Exchange-Organisation und haben einen gemeinsamen CEO. Der CEO ist die einzige gemeinsame Person in beiden Unternehmen. Dieses Szenario erfordert drei Adressbuchrichtlinien, die folgende Merkmale aufweisen:

  - Die Benutzer in Tailspin Toys können beim Durchsuchen der globalen Adressliste nur Tailspin Toys-Benutzer anzeigen.

  - Die Benutzer in Fabrikam können beim Durchsuchen der globalen Adressliste nur Fabrikam-Benutzer anzeigen.

  - In jedem Unternehmen befindet sich eine Verteilergruppe für die Geschäftsleitung, die die leitenden Mitarbeiter des jeweiligen Unternehmens sowie den CEO enthält.

  - Benutzer, die die Gruppenmitgliedschaft des CEOs anzeigen, sehen nur diejenigen Gruppen, die zu ihrem eigenen Unternehmen gehören. Benutzer sehen keine Gruppen außerhalb des eigenen Unternehmens.

  - Es werden drei Adressbuchrichtlinien erstellt: **Fab**, **Tail** und **CEO**.

![Zwei Unternehmen, ein CEO](images/JJ657455.c87a5654-d456-4688-acb2-0be15ba1cda6(EXCHG.150).gif "Zwei Unternehmen, ein CEO")


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Fabrikam</p></td>
<td><p>Tailspin Toys</p></td>
<td><p>CEO</p></td>
</tr>
<tr class="even">
<td><p>Adresslisten</p></td>
<td><p>AL_FAB_Benutzer_DGs</p>
<p>AL_FAB_Kontakte</p></td>
<td><p>AL_TAIL_Benutzer_DGs</p>
<p>AL_TAIL_Kontakte</p></td>
<td><p>AL_FAB_Benutzer_DGs</p>
<p>AL_FAB_Kontakte</p>
<p>AL_TAIL_Benutzer_DGs</p>
<p>AL_TAIL_Kontakte</p></td>
</tr>
<tr class="odd">
<td><p>Globale Adressliste</p></td>
<td><p>GAL_FAB</p></td>
<td><p>GAL_TAIL</p></td>
<td><p>Standard-GAL</p></td>
</tr>
<tr class="even">
<td><p>Raumadressliste</p></td>
<td><p>AL_FAB_Raeume</p></td>
<td><p>AL_TAIL_Raeume</p></td>
<td><p>Standard_alle_Raeume</p></td>
</tr>
<tr class="odd">
<td><p>Offlineadressbuch (OAB)</p></td>
<td><p>OAB_FAB</p></td>
<td><p>OAB_TAIL</p></td>
<td><p>Standard-OAB</p></td>
</tr>
</tbody>
</table>


Wenn der CEO in jeder Organisation zu den Verteilergruppen hinzugefügt wurde und sich im Geltungsbereich der Adressbuchrichtlinien jedes Unternehmens befindet, kann der CEO in jedem Unternehmen angezeigt werden. Der CEO kann Verteilergruppen erstellen, die sich über beide Unternehmen erstrecken und in der globalen Adressliste jedes Unternehmens angezeigt werden. Mitglieder der Verteilergruppe können jedoch nur Gruppenmitglieder anzeigen, die sich innerhalb ihrer eigenen Organisation befinden.

## Szenario 3: Schulung und Weiterbildung

Dieses Szenario kann für Schulen oder Universitäten angewendet werden, in denen nach Unterrichtsräumen getrennt werden muss, um den Datenschutz der Schüler und Studenten zu gewährleisten. Das Szenario für Schulung und Weiterbildung weist folgende Merkmale auf:

  - Schüler/Studenten können nur andere Schüler/Studenten in ihrer Klasse, ihren Lehrer und den Direktor anzeigen.

  - Lehrer können nur Schüler/Studenten in ihren eigenen Unterrichtsräumen anzeigen.

  - Lehrer können alle Lehrer und den Direktor anzeigen.

  - Verteilergruppen werden für die Eltern der Schüler/Studenten einer Klasse und für den Fachbereich erstellt.

![Schulungsszenario für Adressbuchrichtlinien](images/JJ657455.435f3b1a-9752-4c61-ab8a-80115c643d12(EXCHG.150).gif "Schulungsszenario für Adressbuchrichtlinien")


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Studenten_RaumA</p></td>
<td><p>Lehrer_RaumA</p></td>
<td><p>Direktor</p></td>
</tr>
<tr class="even">
<td><p>Adresslisten</p></td>
<td><p>AL_RaumAAL_Direktor</p></td>
<td><p>AL_RaumAAL_AlleLehrerAL_AlleGruppenAL_Direktor</p></td>
<td><p>AL_RaumA</p>
<p>AL_RaumB</p>
<p>AL_AlleLehrer</p>
<p>AL_AlleStudenten</p>
<p>AL_AlleGruppen</p></td>
</tr>
<tr class="odd">
<td><p>Globale Adressliste</p></td>
<td><p>GAL_StudentenRaumA</p></td>
<td><p>GAL_LehrerRaumA</p></td>
<td><p>GAL_Jeder</p></td>
</tr>
<tr class="even">
<td><p>Raumadressliste</p></td>
<td><p>AL_RaumLeer</p></td>
<td><p>AL_RaumLeer</p></td>
<td><p>Standard_alle_Raeume</p></td>
</tr>
<tr class="odd">
<td><p>Offlineadressbuch (OAB)</p></td>
<td><p>OAB_StudentenRaumA</p></td>
<td><p>OAB_LehrerRaumA</p></td>
<td><p>Standard-OAB</p></td>
</tr>
</tbody>
</table>


## Überlegungen und bewährte Methoden

Beachten Sie Folgendes, wenn Sie Adressbuchrichtlinien in Ihrer Organisation verwenden:

  - Damit Adressbuchrichtlinien ordnungsgemäß funktionieren, muss sich das Benutzerpostfach, auf das Sie die Adressbuchrichtlinie anwenden möchten, auf einem Server mit Exchange 2010 SP3 oder Exchange 2013 befinden.

  - Führen Sie die Clientzugriffs-Serverrolle von Exchange 2010 nicht auf dem globalen Katalogserver aus. Dies würde dazu führen, dass für NSPI (Name Service Provider Interface) Active Directory anstelle des Microsoft Exchange-Adressbuchdiensts verwendet wird. Sie können Exchange 2013-Serverrollen auf einem globalen Katalogserver ausführen, und die Adressbuchrichtlinien funktionieren ordnungsgemäß. Es empfiehlt sich jedoch nicht, Exchange auf einem Domänencontroller zu installieren.

  - Sie können hierarchische Adressbücher (Hierarchical Address Books, HABs) und Adressbuchrichtlinien nicht gleichzeitig einsetzen. Weitere Informationen finden Sie unter [Hierarchische Adressbücher](https://review.docs.microsoft.com/de-de/exchange/address-books/hierarchical-address-books/hierarchical-address-books).

  - Jeder Benutzer, dem eine Adressbuchrichtlinie zugewiesen wurde, sollte in der eigenen GAL vorhanden sein.

  - Wenn Sie den Zugriff von Clientanwendungen auf Active Directory direkt über LDAP zulassen, umgehen diese Anwendungen die in die Adressbuchrichtlinien integrierte Logik. Da Outlook für Mac 2011 und Entourage 2008 direkte LDAP-Abfragen für den Zugriff auf Active Directory nutzen, funktionieren diese Clientanwendungen nicht ordnungsgemäß mit Adressbuchrichtlinien, wenn ein Domänencontroller oder ein globaler Katalogserver angegeben oder durch den AutoErmittlungsdienst bereitgestellt wird. Outlook für Mac 2011 kann Exchange-Webdienste oder ein lokales OAB verwenden, um auf Verzeichnisinformationen zuzugreifen. Wenn Outlook für Mac 2011 jedoch direkt auf einen LDAP-Dienst zugreifen kann, nutzt das Programm diese Möglichkeit.

  - Die in einer Adressbuchrichtlinie verwendete GAL muss mindestens alle in der Adressbuchrichtlinie definierten und angegebenen Adresslisten enthalten, einschließlich der Raumadressliste. Erstellen Sie keine GAL, die weniger Objekte enthält als eine der Adresslisten in der gleichen Adressbuchrichtlinie.

  - Es wird empfohlen, Verteilergruppen zu erstellen, die nicht über die Grenzen der virtuellen Organisation hinausgehen. Wenn Sie Verteilergruppen erstellen, die Mitglieder verschiedener virtueller Organisationen enthalten, treten folgende Probleme auf:
    
      - Wenn Gruppenmitglieder beim Senden von E-Mails an die Verteilergruppe eine Zustellungs- oder Lesebestätigung anfordern, können sie die E-Mail-Adressen der Gruppenmitglieder in anderen virtuellen Organisationen anzeigen
    
      - Wenn eine verschlüsselte Nachricht an die Verteilergruppe gesendet wird und einige der Gruppenmitglieder nicht über gültige digitale IDs verfügen, erhält der Absender eine Warnmeldung, die die Gesamtanzahl von Mitgliedern ohne gültige ID sowie eine Liste der zugehörigen E-Mail-Adressen enthält. Befinden sich allerdings einige dieser Mitglieder ohne gültige ID in einer anderen Organisation als der Absender, enthält die Warnmeldung zwar die richtige Anzahl von Mitgliedern, zeigt jedoch nicht die E-Mail-Adressen der Mitglieder in der anderen Organisation an. Dies führt dazu, dass die Gesamtzahl nicht mit der Liste der Adressen der Mitglieder übereinstimmt.
        
        Ein Beispiel: Eine Verteilergruppe umfasst fünf Mitglieder aus zwei Organisationen, Filiale A und Filiale B. Drei Mitglieder gehören zu Filiale A, und die digitale ID eines dieser Mitglieder ist ungültig. Die anderen beiden Mitglieder gehören zu Filiale B und besitzen beide keine gültigen digitalen IDs. Wenn ein Mitglied aus Filiale A eine verschlüsselte Nachricht an die Verteilergruppe sendet, erhält dieses Mitglied eine Warnmeldung mit dem Inhalt, dass drei Empfänger nicht über gültige digitale IDs verfügen. Es wird jedoch nur die E-Mail-Adresse des Empfängers aus Filiale A in der Warnmeldung aufgeführt.
    
      - Adressbuchrichtlinien gelten nicht für die **Get-Group**-Cmdlets. Benutzer oder Prozesse, die **Get-Group** ausführen können, können daher alle Mitglieder aller Gruppen anzeigen, auf die sie Zugriff haben.
        
        Es wird empfohlen, die Gruppenverwaltungseinstellungen der OWA-Optionen zu bearbeiten, sodass Benutzer Outlook Web App nicht zur Verwaltung von Gruppen verwenden können. Um zu verhindern, dass Benutzer die OWA-Optionen zur Verwaltung von Gruppen einsetzen, schließen Sie die Benutzer aus der RBAC-Rolle "MyDistributionGroupMembership" aus. Weitere Informationen finden Sie unter [Rolle „MyDistributionGroupMembership“](mydistributiongroupmembership-role-exchange-2013-help.md).
    
      - Wenn Sie Benutzern die Verwendung von Outlook oder Outlook Web App zur Verwaltung von Gruppen gestatten, müssen die Gruppenbesitzer die Liste der Gruppenmitglieder vollständig anzeigen können.

  - Alle Adressbuchrichtlinien müssen eine Raumadressliste enthalten. Wenn Ihre Organisation jedoch keine Raumadresslisten verwendet, können Sie eine standardmäßige leere Raumadressliste erstellen.

  - Durch die Bereitstellung von Adressbuchrichtlinien wird nicht verhindert, dass Benutzer aus einer virtuellen Organisation E-Mails an Benutzer in einer anderen virtuellen Organisation senden. Wenn Sie das organisationsübergreifende Senden von E-Mails unterbinden möchten, empfiehlt sich die Erstellung einer Transportregel. Zur Erstellung einer Transportregel, die verhindert, dass Contoso-Benutzer E-Mails von Fabrikam-Benutzern erhalten, jedoch zulässt, dass die Geschäftsleitung von Fabrikam Nachrichten an Contoso-Benutzer sendet, führen Sie folgenden Shellbefehl aus:
    
        New-TransportRule -Name "StopFabrikamtoContosoMail" -FromMemberOf "AllFabrikamEmployees" -SentToMemberOf "AllContosoEmployees" -DeleteMessage -ExceptIfFrom seniorleadership@fabrikam.com

  - Wenn Sie ein Feature wie Adressbuchrichtlinie im Lync-Client erzwingen möchten, können Sie das Attribut `msRTCSIP-GroupingID` für bestimmte Benutzerobjekte festlegen. Weitere Informationen finden Sie im Thema ["PartitionByOU" ersetzt durch "msRTCSIP-GroupingID"](https://go.microsoft.com/fwlink/p/?linkid=232306).

## Allgemeine Bereitstellungsschritte

## Migrieren von der Adresslistensegmentierung zu Adressbuchrichtlinien

Wenn in Ihrer Organisation die Exchange 2007-Adresslistensegmentierung anhand der Anweisungen im Whitepaper [Konfigurieren von virtuellen Organisationen und Segmentierung von Adresslisten in Exchange 2007](https://go.microsoft.com/fwlink/p/?linkid=109601) konfiguriert wurde, sollten Sie zuerst zu Exchange Server 2010 migrieren. Befolgen Sie dazu die in [Migration von der Exchange 2007-Adresslistensegmentierung zu Exchange 2010-Adresslistenrichtlinien](https://go.microsoft.com/fwlink/p/?linkid=235967) beschriebenen Schritte. Dieses Verfahren verursacht einige Ausfallzeiten für Ihre Organisation und muss daher entsprechend geplant werden.

## Neue Bereitstellung von Adressbuchrichtlinien

Wenn in Ihrer Organisation Exchange 2013-Adressbuchrichtlinien bereitgestellt werden sollen und die Exchange 2007-Adresslistensegmentierung nicht verwendet wurde, können Sie die Adressbuchrichtlinien mithilfe dieser Anweisungen in Ihrer Organisation bereitstellen.

Die Schritte in diesem Abschnitt begleiten Sie durch Szenario 2: Szenario 2: Zwei Unternehmen mit einem gemeinsamen CEO. In diesem Szenario sind Fabrikam und Tailspin Toys getrennte Unternehmen mit einem gemeinsamen CEO und gemeinsamer Geschäftsleitung.

## Schritt 1: Installieren und Konfigurieren des Agents für das Routing von Adressbuchrichtlinien

Wenn Sie Adressbuchrichtlinien verwenden und nicht möchten, dass Benutzer in getrennten virtuellen Organisationen sich gegenseitig ihre möglicherweise vertraulichen Informationen anzeigen, können Sie den Agent für das Routing von Adressbuchrichtlinien aktivieren. Der Agent für das Routing von Adressbuchrichtlinien ist ein auf dem Postfachserver ausgeführte Transport-Agent, der steuert, wie Empfänger in der Organisation aufgelöst werden. Nachdem der Agent für das Routing von Adressbuchrichtlinien installiert und konfiguriert wurde, werden Benutzer, die verschiedenen globalen Adresslisten zugewiesen sind, insofern als externe Empfänger angezeigt, da sie die Kontaktkarten externer Empfänger nicht anzeigen können.

Ausführliche Anweisungen finden Sie unter [Installieren und Konfigurieren des Agents für das Routing von Adressbuchrichtlinien](install-and-configure-the-address-book-policy-routing-agent-exchange-2013-help.md).

## Schritt 2: Unterteilen Sie Ihre virtuellen Organisationen

Sie müssen eine Methode erarbeiten, um Ihre Organisation zu unterteilen. Es empfiehlt sich die Verwendung der Eigenschaften von "CustomAttribute1-15" in den Postfächern, Kontakten und Gruppen, nicht der Einsatz vordefinierter Bedingungsattribute (wie etwa Unternehmen, Abteilung oder Bundesland/Kanton). Der Einsatz von benutzerdefinierten Attributen anstelle von vordefinierten Attributen bietet folgende Vorteile:

  - In Active Directory sind nicht für alle Empfängerobjekttypen Bedingungsattribute vordefiniert. Verteilergruppen und dynamische Verteilergruppen beispielsweise unterstützen keine Attribute für Unternehmen, Abteilung oder Bundesland/Kanton.

  - Für einige Empfänger sind nicht alle vordefinierten Bedingungsattribute in Cmdlets verfügbar. Beispielsweise stehen die Parameter *Company*, *department* und *StateOrProvince* in den Cmdlets für E-Mail-Benutzer, Kontakte, Verteilergruppen und E-Mail-aktivierte öffentliche Ordner nicht zur Verfügung.

  - Zum Segmentieren von Empfängern sind mehrere Cmdlets erforderlich, wenn Sie ein vordefiniertes Bedingungsattribut verwenden. Wenn Sie z. B. die Cmdlets **New-Mailbox** oder **Set-Mailbox** verwendet haben, müssen Sie anschließend "Set-User" ausführen, um *Company*, *Department* oder *StateOrProvince* für ein Benutzerpostfach zu kennzeichnen.

  - Alle *CustomAttributeX*-Parameter stehen im Set-\*-Cmdlet für jeden Empfängertyp zur Verfügung, sodass die Segmentierung für diesen Typ vollständig über ein einziges Set-Cmdlet ausgeführt werden kann

  - CustomAttributeX-Attribute sind explizit für die Anpassung einer Organisation reserviert und werden ausschließlich von den Administratoren der Organisation verwendet.

Eine weitere bewährte Methode zur Segmentierung einer Organisation ist die Verwendung von Unternehmens-IDs in den Namen von Verteilergruppen und dynamischen Verteilergruppen. Exchange verfügt über eine Funktion für Gruppenbenennungsrichtlinien, die dem Namen einer Verteilergruppe automatisch basierend auf verschiedenen Attributen des Benutzers, der die Verteilergruppe erstellt, ein Suffix oder ein Präfix hinzufügt. Zu diesen Attributen gehören u. a. Unternehmen, Bundesland/Kanton, Titel und "CustomAttribute1" bis "CustomAttribute15". Die Gruppenbenennungsrichtlinie ist insbesondere dann wichtig, wenn Sie Benutzern gestatten, selbst Verteilergruppen zu erstellen. Weitere Informationen finden Sie unter [Erstellen einer Benennungsrichtlinie für Verteilergruppen](https://review.docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy).

Gruppenbenennungsrichtlinien gelten nicht für dynamische Verteilergruppen. Sie müssen diese manuell segmentieren und eine Benennungsrichtlinie darauf anwenden.

## Schritt 3: Erstellen von Adresslisten, GALs und OABs

Wenn Sie Adresslisten und globale Adresslisten erstellen, verwenden Sie keine IncludedRecipient- und ConditionalX-Parameter wie zum Beispiel "ConditionalCompany" und "ConditionalCustomAttribute5". Sie sollten stattdessen einen Empfängerfilter verwenden. Zum Erstellen von Empfängerfiltern müssen Sie die Shell verwenden. Weitere Informationen zu Empfängerfiltern finden Sie unter [Empfängerfilter auf Edge-Transport-Servern](recipient-filtering-on-edge-transport-servers-exchange-2013-help.md)

Beim Erstellen der Adressbuchrichtlinie erstellen Sie mehrere Adresslisten, je nachdem, wie Ihre Benutzer die Listen in Outlook oder Outlook Web App anzeigen sollen. Diese Organisation verfügt über vier Adresslisten:

  - AL\_FAB\_Benutzer\_DGs

  - AL\_FAB\_Kontakte

  - AL\_TAIL\_Benutzer\_DGs

  - AL\_TAIL\_Kontakte

In diesem Beispiel wird die Adressliste AL\_TAIL\_Benutzer\_DGs erstellt. Die Adressliste enthält alle Benutzer und Verteilergruppen, für die gilt: "CustomAttribute15" ist gleich "TAIL".

    New-AddressList -Name "AL_TAIL_Users_DGs" -RecipientFilter {((RecipientType -eq 'UserMailbox') -or (RecipientType -eq "MailUniversalDistributionGroup") -or (RecipientType -eq "DynamicDistributionGroup")) -and (CustomAttribute15 -eq "TAIL")}

Weitere Informationen zum Erstellen von Adresslisten unter Verwendung von Empfängerfiltern finden Sie unter [Erstellen einer Adressliste mithilfe von Empfängerfiltern](https://review.docs.microsoft.com/de-de/exchange/address-books/address-lists/use-recipient-filters-to-create-an-address-list).

Zum Erstellen einer Adressbuchrichtlinie müssen Sie eine Raumadressliste bereitstellen. Wenn Ihre Organisation nicht über Ressourcenpostfächer (wie zum Beispiel Raum- oder Gerätepostfächer) verfügt, empfiehlt es sich, eine leere Raumadressliste zu erstellen. Im folgenden Beispiel wird eine leere Raumadressliste erstellt, da in der Organisation keine Raumpostfächer vorhanden sind.

    New-AddressList -Name AL_BlankRoom -RecipientFilter {(Alias -ne $null) -and ((RecipientDisplayType -eq 'ConferenceRoomMailbox') -or (RecipientDisplayType -eq 'SyncedConferenceRoomMailbox'))}

In diesem Szenario verfügen jedoch sowohl Fabrikam als auch Contoso über Raumpostfächer. In diesem Beispiel wird eine Raumliste für Fabrikam erstellt. Dabei wird ein Empfängerfilter verwendet, für den gilt: "CustomAttribute15" ist gleich "FAB".

    New-AddressList -Name AL_FAB_Room -RecipientFilter {(Alias -ne $null) -and (CustomAttribute15 -eq "FAB")-and (RecipientDisplayType -eq 'ConferenceRoomMailbox') -or (RecipientDisplayType -eq 'SyncedConferenceRoomMailbox')}

Bei der in einer Adressbuchrichtlinie verwendeten globalen Adressliste muss es sich um die Obermenge aller Adresslisten handeln. Erstellen Sie keine globale Adressliste mit weniger Objekten als in einer oder allen Adresslisten in der Adressbuchrichtlinie. In diesem Beispiel wird die globale Adressliste für Tailspin Toys erstellt. Diese umfasst alle Empfänger, die in den Adresslisten und der Raumadressliste vorhanden sind.

    New-GlobalAddressList -Name "GAL_TAIL" -RecipientFilter {(CustomAttribute15 -eq "TAIL")}

Weitere Informationen finden Sie unter [Erstellen einer globalen Adressliste](https://review.docs.microsoft.com/de-de/exchange/address-books/address-lists/create-global-address-list).

Beim Erstellen des Offlineadressbuchs sollten Sie die geeignete globale Adressliste verwenden, wenn Sie den Parameter *AddressLists* für "New-OfflineAddressBook" oder "Set-OfflineAddressBook" bereitstellen, um sicherzustellen, dass kein Eintrag fehlt. Grundsätzlich können Sie die Anzahl von Einträgen, die ein Benutzer anzeigen kann, oder die Downloadgröße des Offlineadressbuchs reduzieren, indem Sie eine Liste mit Adresslisten im Parameter "AddressLists" der New/Set-OfflineAddressBook-Cmdlets angeben. Wenn Sie jedoch möchten, dass Benutzer sämtliche Einträge der globalen Adressliste im Offlineadressbuch anzeigen können, sollten Sie sicherstellen, dass die globale Adressliste in diesem Parameter enthalten ist.

In diesem Beispiel wird das Offlineadressbuch "OAB\_FAB" für Fabrikam erstellt.

    New-OfflineAddressBook -Name "OAB_FAB" -AddressLists "GAL_FAB"

Weitere Informationen finden Sie unter [Erstellen eines Offlineadressbuchs](create-an-offline-address-book-exchange-2013-help.md).

## Schritt 4: Erstellen der Adressbuchrichtlinien

Nachdem Sie alle erforderlichen Objekte erstellt haben, können Sie die Adressbuchrichtlinie erstellen. In diesem Beispiel wird die Adressbuchrichtlinie "ABP\_TAIL" erstellt.

    New-AddressBookPolicy -Name "ABP_TAIL" -AddressLists "AL_TAIL_Users_DGs"," AL_TAIL_Contacts" -OfflineAddressBook "\OAB_TAIL" -GlobalAddressList "\GAL_TAIL" -RoomList "\AL_TAIL_Rooms"

Weitere Informationen finden Sie unter [Erstellen einer Adressbuchrichtlinie](https://review.docs.microsoft.com/de-de/exchange/address-books/address-book-policies/create-an-address-book-policy).

## Schritt 5: Zuweisen der Adressbuchrichtlinien zu Postfächern

Das Zuweisen der Adressbuchrichtlinien zu Benutzern ist der letzte Schritt in diesem Prozess. Adressbuchrichtlinien werden angewendet, wenn die Anwendung eines Benutzers eine Verbindung zum Microsoft Exchange-Adressbuchdienst auf dem Clientzugriffsserver herstellt. Wenn der Benutzer beim Anwenden der Adressbuchrichtlinie auf sein Konto bereits mit Outlook oder Outlook Web App verbunden ist, muss der Benutzer die Clientanwendung schließen und erneut öffnen, um die neuen Adresslisten und die globale Adressliste anzuzeigen.

In diesem Beispiel wird "ABP\_FAB" allen Postfächern zugewiesen, bei denen gilt: "CustomAttribute15" ist gleich "FAB".

    Get-Mailbox -resultsize unlimited | where {$_.CustomAttribute15 -eq "TAIL"} | Set-Mailbox -AddressBookPolicy "ABP_TAIL"

Weitere Informationen finden Sie unter [Zuweisen einer Adressbuchrichtlinie zu E-Mail-Benutzern](https://review.docs.microsoft.com/de-de/exchange/address-books/address-book-policies/assign-an-address-book-policy-to-mail-users).


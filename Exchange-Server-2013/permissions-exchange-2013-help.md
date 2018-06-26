---
title: 'Berechtigungen: Exchange 2013 Help'
TOCTitle: Berechtigungen
ms:assetid: d8dd605e-0af1-4e18-9ce6-e51d04e161ba
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351175(v=EXCHG.150)
ms:contentKeyID: 50476840
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Berechtigungen

 

_**Gilt für:**Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Microsoft Exchange Server 2013 umfasst diverse vordefinierte Berechtigungen, die auf dem RBAC-Berechtigungsmodell (Role Based Access Control, rollenbasierte Zugriffssteuerung) basieren und zur problemlosen Zuweisung von Berechtigungen zu Administratoren und Benutzern umgehend verwendet werden können. Mithilfe der Berechtigungsfunktionen in Exchange 2013 können Sie die Einrichtungs- und Bereitstellungsschritte einer neuen Organisation schnell ausführen.


> [!NOTE]
> Verschiedene Funktionen und Konzepte der rollenbasierten Zugriffssteuerung werden in diesem Thema nicht behandelt, da es sich um erweiterte Funktionen handelt. Wenn Sie Ihre Anforderungen mit den in diesem Thema erläuterten Funktionen nicht erfüllen können und Ihr Berechtigungsmodell zusätzlich anpassen möchten, finden Sie unter <A href="understanding-role-based-access-control-exchange-2013-help.md">Grundlegendes zur rollenbasierten Zugriffssteuerung</A> weitere Informationen.



Sie suchen nach einer umfassenden Liste mit Artikeln zum Thema Berechtigungen? Weitere Informationen finden Sie unter Dokumentation zu Berechtigungen.

**Inhalt**

Rollenbasierte Berechtigungen

Rollengruppen und Rollenzuweisungsrichtlinien

Arbeiten mit Rollengruppen

Arbeiten mit Rollenzuweisungsrichtlinien

## Rollenbasierte Berechtigungen

In Exchange 2013 basieren die Berechtigungen, die Administratoren und Benutzern zugewiesen werden können, auf Verwaltungsrollen. Eine Rolle definiert die Aufgaben, die ein Administrator oder Benutzer ausführen kann. Die Verwaltungsrolle `Mail Recipients` definiert z. B. die Aufgaben, die ein Benutzer für Postfächer, Kontakte und Verteilergruppen ausführen kann. Wenn einem Administrator oder Benutzer eine Rolle zugewiesen wird, erhält dieser die von der Rolle bereitgestellten Berechtigungen.

Es gibt zwei Typen von Rollen, Administratorrollen und Endbenutzerrollen:

  - **Administratorrollen**   Diese Rollen umfassen Berechtigungen, die Administratoren oder spezialisierten Benutzern mithilfe von Rollengruppen zur Verwaltung eines bestimmten Bereichs der Exchange-Organisation (z. B. Empfänger, Server oder Datenbanken) zugewiesen werden können.

  - **Endbenutzerrollen**   Diese Rollen werden über Richtlinien zur Rollenzuweisung zugewiesen und ermöglichen Benutzern die Verwaltung bestimmter Aspekte eigener Postfächer und Verteilergruppen. Endbenutzerrollen beginnen mit dem Präfix `My`.

Die Berechtigungen einer Rolle zum Ausführen von Aufgaben werden Administratoren und Benutzern erteilt, indem ihnen die entsprechenden Cmdlets zur Verfügung gestellt werden. Da die Exchange-Verwaltungskonsole und die Exchange-Verwaltungsshell zur Verwaltung von Exchange Cmdlets verwenden, können Administratoren oder Benutzer mit Zugriff auf ein Cmdlet die entsprechende Aufgabe über jede der Exchange-Verwaltungsschnittstellen ausführen.

Exchange 2013 umfasst ca. 86 Rollen, die Sie zum Erteilen von Berechtigungen verwenden können. Eine Liste der in Exchange 2013 enthaltenen Rollen finden Sie unter [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md).

Rollenbasierte Berechtigungen

## Rollengruppen und Rollenzuweisungsrichtlinien

Über Rollen werden Berechtigungen zum Ausführen von Aufgaben in Exchange 2013 erteilt. Sie benötigen jedoch eine einfache Möglichkeit, um diese Rollen Administratoren und Benutzern zuzuweisen. Exchange 2013 bietet zu diesem Zweck die folgenden Methoden:

  - **Rollengruppen**   Mithilfe von Rollengruppen können Sie Administratoren und spezialisierten Benutzern Berechtigungen erteilen.

  - **Rollenzuweisungsrichtlinien**   Über Richtlinien zur Rollenzuweisung können Sie Endbenutzern die Berechtigung zum Ändern der Einstellungen ihrer eigenen Postfächer oder Verteilergruppen erteilen.

Weitere Informationen zu Rollengruppen und Rollenzuweisungsrichtlinien finden Sie in den folgenden Abschnitten.

## Rollengruppen

Jedem Administrator, der Exchange 2013 verwaltet, muss mindestens eine Rolle zugewiesen werden. Da Administratoren möglicherweise Funktionen in mehreren Bereichen von Exchange ausführen, können sie über mehrere Rollen verfügen. Ein Administrator kann z. B. sowohl Empfänger als auch Exchange-Server verwalten. In diesem Fall kann dem Administrator sowohl die Rolle `Mail Recipients` als auch die Rolle `Exchange Servers` zugewiesen werden.

Um die Zuweisung mehrerer Rollen zu einem Administrator zu vereinfachen, umfasst Exchange 2013 Rollengruppen. Bei Rollengruppen handelt es sich um spezielle universelle Sicherheitsgruppen (USGs), die von Exchange 2013 verwendet werden und Active Directory-Benutzer, USGs und andere Rollengruppen enthalten. Beim Zuweisen einer Rolle zu einer Rollengruppe werden die Berechtigungen der Rolle allen Mitgliedern der Rollengruppe erteilt. So können Sie mehreren Rollengruppenmitgliedern gleichzeitig eine Vielzahl von Rollen zuweisen. Rollengruppen gelten typischerweise für umfassendere Verwaltungsbereiche, z. B. die Empfängerverwaltung. Sie werden ausschließlich mit Administratorrollen und nicht mit Endbenutzerrollen verwendet.


> [!NOTE]
> Eine Rolle kann einem Benutzer oder einer universellen Sicherheitsgruppe direkt und ohne Verwendung einer Rollengruppe zugewiesen werden. Diese Methode zur Rollenzuweisung ist jedoch ein erweitertes Verfahren, das in diesem Thema nicht behandelt wird. Es wird empfohlen, zur Verwaltung von Berechtigungen Rollengruppen einzusetzen.



Die folgende Abbildung zeigt die Beziehung zwischen Benutzern, Rollengruppen und Rollen.

**Rollen, Rollengruppen und Rollengruppenmitglieder**

![Rolle, Rollengruppe und Mitglied – Beziehung](images/Dd351175.3fb0b47d-333a-4953-ae38-d710d327bde0(EXCHG.150).gif "Rolle, Rollengruppe und Mitglied – Beziehung")

Exchange 2013 umfasst eine Vielzahl von integrierten Rollengruppen, die jeweils Berechtigungen zum Verwalten bestimmter Bereiche in Exchange 2013 bieten. Bei einigen Rollengruppen gibt es möglicherweise Überschneidungen. In der folgenden Tabelle sind die einzelnen Rollengruppen sowie eine Beschreibung ihrer Verwendung aufgeführt. Zum Anzeigen der Rollen, die den einzelnen Rollengruppen zugewiesen sind, klicken Sie in der Spalte "Rollengruppe" auf den Namen der Rollengruppe, und öffnen Sie den Abschnitt "Dieser Rollengruppe zugewiesene Verwaltungsrollen".

### Integrierte Rollengruppen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Rollengruppe</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="organization-management-exchange-2013-help.md">Organisationsverwaltung</a></p></td>
<td><p>Administratoren, die Mitglieder der Rollengruppe Organisationsverwaltung sind, verfügen über Administratorzugriff auf die gesamte Exchange 2013-Organisation und können praktisch sämtliche Aufgaben für ein beliebiges Exchange 2013-Objekt ausführen. Es gelten jedoch einige Ausnahmen (z. B. die Rolle <code>Discovery Management</code>).</p>

> [!IMPORTANT]
> Da die Rollengruppe Organisationsverwaltung sehr viele Berechtigungen umfasst, sollten nur Benutzer oder universelle Sicherheitsgruppen, die Administratoraufgaben auf Organisationsebene mit potenziellen Auswirkungen auf die gesamte Exchange-Organisation ausführen, Mitglieder dieser Rollengruppe sein.


</td>
</tr>
<tr class="even">
<td><p><a href="view-only-organization-management-exchange-2013-help.md">Organisationsverwaltung mit Leserechten</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe Organisationsverwaltung – nur Leserechte sind, können die Eigenschaften aller Objekte in der Exchange-Organisation anzeigen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="recipient-management-exchange-2013-help.md">Empfängerverwaltung</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe Empfängerverwaltung sind, haben Administratorzugriff zum Erstellen oder Ändern von Exchange 2013-Empfängern innerhalb der Exchange 2013-Organisation.</p></td>
</tr>
<tr class="even">
<td><p><a href="um-management-exchange-2013-help.md">UM-Verwaltung</a></p></td>
<td><p>Administratoren, die Mitglied der UM-Verwaltungsrollengruppe sind, können in der Exchange-Organisation Einstellungen wie die UM-Dienstkonfiguration (Unified Messaging), UM-Eigenschaften für Postfächer, UM-Telefonansagen und die Konfiguration automatischer UM-Telefonzentralen verwalten.</p></td>
</tr>
<tr class="odd">
<td><p><a href="help-desk-exchange-2013-help.md">Helpdesk</a></p></td>
<td><p>Die Helpdesk-Rollengruppe ermöglicht ihren Mitgliedern standardmäßig das Anzeigen und Ändern der Microsoft OfficeOutlook Web App-Optionen aller Benutzer in der Organisation. Zu diesen Optionen gehört mitunter das Ändern des Anzeigenamens, der Adresse und der Telefonnummer des Benutzers. Optionen, die in den Outlook Web App-Optionen nicht verfügbar sind, beispielsweise die Änderung der Postfachgröße oder die Konfiguration der Postfachdatenbank, in der sich ein Postfach befindet, gehören nicht dazu.</p></td>
</tr>
<tr class="even">
<td><p><a href="hygiene-management-exchange-2013-help.md">Verwaltung von Nachrichtenschutz</a></p></td>
<td><p>Administratoren, die Mitglieder der Rollengruppe &quot;Verwaltung von aktivem Nachrichtenschutz&quot; sind, können die Antiviren- und Antispamfunktionen von Exchange 2013 konfigurieren. Drittanbieterprogramme, die in Exchange 2013 integriert werden können, können dieser Rollengruppe Dienstkonten hinzufügen, damit Programme Zugriff auf die Cmdlets haben, die zum Abrufen und Konfigurieren der Exchange-Konfiguration erforderlich sind.</p></td>
</tr>
<tr class="odd">
<td><p><a href="records-management-exchange-2013-help.md">Datensatzverwaltung</a></p></td>
<td><p>Benutzer, die Mitglieder der Rollengruppe Datensatzverwaltung sind, können Funktionen zur Einhaltung von Vorschriften konfigurieren, z. B. Aufbewahrungsrichtlinientags, Nachrichtenklassifikationen und Transportregeln.</p></td>
</tr>
<tr class="even">
<td><p><a href="discovery-management-exchange-2013-help.md">Erkennungsverwaltung</a></p></td>
<td><p>Administratoren oder Benutzer, die Mitglied der Rollengruppe Discoveryverwaltung sind, können Postfächer in der Exchange-Organisation nach Daten durchsuchen, die mit bestimmten Kriterien übereinstimmen. Zudem können diese Mitglieder eine rechtliche Aufbewahrungspflicht für Postfächer konfigurieren.</p></td>
</tr>
<tr class="odd">
<td><p><a href="public-folder-management-exchange-2013-help.md">Verwaltung Öffentlicher Ordner</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe zur Verwaltung öffentlicher Ordner sind, können öffentliche Ordner auf Servern mit Exchange 2013 verwalten.</p></td>
</tr>
<tr class="even">
<td><p><a href="server-management-exchange-2013-help.md">Serververwaltung</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe zur Serververwaltung sind, können die serverspezifische Konfiguration von Transport-, Unified Messaging-, Clientzugriffs- und Postfachfunktionen wie Datenbankkopien, Zertifikate, Transportwarteschlangen und Sendeconnectors, virtuelle Verzeichnisse und Clientzugriffsprotokolle konfigurieren.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delegated-setup-exchange-2013-help.md">Delegiertes Setup</a></p></td>
<td><p>Administratoren, die Mitglied der Rollengruppe Delegiertes Setup sind, können exExchange2k13-Server bereitstellen, die zuvor durch ein Mitglied der Rollengruppe exOnPremOrgMgmt bereitgestellt wurden.</p></td>
</tr>
<tr class="even">
<td><p><a href="compliance-management-exchange-2013-help.md">Verwaltung der Richtlinientreue</a></p></td>
<td><p>Benutzer, die Mitglied der Rollengruppe &quot;Verwaltung der Richtlinientreue&quot; sind, können Exchange-Einstellungen zur Richtlinientreue in Übereinstimmung mit der Richtlinie ihrer Organisation konfigurieren und verwalten.</p></td>
</tr>
</tbody>
</table>


Wenn Sie in einer kleinen Organisation tätig sind, die nur über einige wenige Administratoren verfügt, ist es möglicherweise ausreichend, diese Administratoren lediglich zur Rollengruppe exOnPremOrgMgmt hinzuzufügen. Die Verwendung der anderen Rollengruppen ist gegebenenfalls nicht erforderlich. In einer größeren Organisation verfügen Sie möglicherweise über Administratoren, die bestimmte exExchangeNoVersion-Verwaltungsaufgaben ausführen, z. B die Empfänger- oder die Serververwaltung. In diesem Fall fügen Sie z. B. einen Administrator zur Rollengruppe exOnPremRecipMgmt und einen anderen Administrator zur Rollengruppe Serververwaltung hinzu. Diese Administratoren können so die ihnen zugewiesenen Bereiche von exExchange2k13 verwalten, sind jedoch nicht zum Verwalten von Bereichen berechtigt, für die sie nicht verantwortlich sind.

Wenn die integrierten Rollengruppen in Exchange 2013 nicht für die Aufgabenbereiche Ihrer Administratoren geeignet sind, können Sie Rollengruppen erstellen und Rollen zu diesen Gruppen hinzufügen. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt Arbeiten mit Rollengruppen.

Rollenbasierte Berechtigungen

## Rollenzuweisungsrichtlinien

Exchange 2013 bietet Richtlinien zur Rollenzuweisung, mit denen Sie steuern können, welche Einstellungen Benutzer für eigene Postfächer und Verteilergruppen konfigurieren können. Diese Einstellungen umfassen den Anzeigenamen, Kontaktinformationen, Voicemaileinstellungen und die Mitgliedschaft in Verteilergruppen.

Um für die verschiedenen Typen von Benutzern innerhalb der Organisation unterschiedliche Berechtigungsebenen zu implementieren, kann eine Exchange 2013-Organisation über mehrere Rollenzuweisungsrichtlinien verfügen. Einige Benutzer können abhängig von der ihrem Postfach zugeordneten Rollenzuweisungsrichtlinie z. B. zum Ändern ihrer Adresse oder Erstellen von Verteilergruppen berechtigt sein, während andere Benutzer diese Aufgaben nicht ausführen dürfen. Rollenzuweisungsrichtlinien werden direkt zu Postfächern hinzugefügt, und jedem Postfach kann nur jeweils eine Rollenzuweisungsrichtlinie zugeordnet sein.

Eine Rollenzuweisungsrichtlinie in Ihrer Organisation ist als Standardrichtlinie gekennzeichnet. Die Standardrichtlinie für die Rollenzuweisung wird neuen Postfächern zugeordnet, denen bei der Erstellung nicht explizit eine Rollenzuweisungsrichtlinie zugeordnet wird. Die Standardrichtlinie für die Rollenzuweisung sollte die Berechtigungen umfassen, die dem Großteil Ihrer Postfächer erteilt werden sollen.

Berechtigungen werden über Endbenutzerrollen zu Rollenzuweisungsrichtlinien hinzugefügt. Der Name von Endbenutzerrollen beginnt mit dem Präfix `My`. Über diese Rollen werden Benutzern Berechtigungen zum Verwalten ihrer eigenen Postfächer oder Verteilergruppen erteilt. Sie können nicht zum Verwalten anderer Postfächer verwendet werden. Einer Rollenzuweisungsrichtlinie können nur Endbenutzerrollen zugewiesen werden.

Beim Zuweisen einer Endbenutzerrolle zu einer Rollenzuweisungsrichtlinie erhalten alle Postfächer, die dieser Rollenzuweisungsrichtlinie zugeordnet sind, die über die Rolle erteilten Berechtigungen. So können Sie Berechtigungen zu einer Gruppe von Benutzern hinzufügen oder von dieser Gruppe entfernen, ohne einzelne Postfächer konfigurieren zu müssen. Die Abbildung unten zeigt Folgendes:

  - Endbenutzerrollen werden Rollenzuweisungsrichtlinien zugewiesen. Rollenzuweisungsrichtlinien können dieselben Endbenutzerrollen gemeinsam verwenden.

  - Rollenzuweisungsrichtlinien werden Postfächern zugeordnet. Jedem Postfach kann nur eine Rollenzuweisungsrichtlinie zugeordnet werden.

  - Nachdem einem Postfach eine Rollenzuweisungsrichtlinie zugeordnet wurde, werden die Endbenutzerrollen auf das Postfach angewendet. Die über die Rollen erteilten Berechtigungen werden dem Benutzer des Postfachs zugewiesen.

**Rollen, Rollenzuweisungsrichtlinien und Postfächer**

![Rolle, Rollenzuweisungsrichtlinie, Postfachbeziehung](images/Dd351175.82e07b3d-da59-465b-b349-e0bfde369ace(EXCHG.150).gif "Rolle, Rollenzuweisungsrichtlinie, Postfachbeziehung")

Die Rollenzuweisungsrichtline "Standardrichtlinie für Rollenzuweisung" ist in Exchange 2013 enthalten. Wie der Name schon sagt, handelt es sich um die Standardrichtlinie für Rollenzuweisung. Informationen zum Ändern der mit dieser Rollenzuweisungsrichtlinie bereitgestellten Berechtigungen oder zum Erstellen von Rollenzuweisungsrichtlinien finden Sie unter Arbeiten mit Rollenzuweisungsrichtlinien weiter unten in diesem Thema.

## Arbeiten mit Rollengruppen

Am besten verwenden Sie zum Verwalten der Berechtigungen mithilfe von Rollengruppen in Exchange 2013 die Exchange-Verwaltungskonsole. Wenn Sie zum Verwalten von Rollengruppen die Exchange-Verwaltungskonsole verwenden, können Sie mit ein paar Mausklicks Rollen und Mitglieder hinzufügen und entfernen, Rollengruppen erstellen oder Rollengruppen kopieren. Um diese Aufgaben auszuführen, bietet die Exchange-Verwaltungskonsole einfache Dialogfelder wie das in der folgenden Abbildung gezeigte Dialogfeld **Neue Rollengruppe**.

**Dialogfeld "Neue Rollengruppe" in der Exchange-Verwaltungskonsole**

![Dialogfeld "Neue Rollengruppe" in der Exchange-Verwaltungskonsole](images/Dd351175.e0577090-73e6-4671-ae98-78a8064fde87(EXCHG.150).jpg "Dialogfeld \"Neue Rollengruppe\" in der Exchange-Verwaltungskonsole")

Exchange 2013 enthält mehrere Rollengruppen, die Berechtigungen in spezielle Verwaltungsbereiche einteilen. Wenn diese vorhandenen Rollengruppen die Berechtigungen bieten, die Ihre Administratoren zum Verwalten der Exchange 2013-Organisation benötigen, müssen Sie die Administratoren lediglich als Mitglieder der entsprechenden Rollengruppen hinzufügen. Nachdem Sie Administratoren zu einer Rollengruppe hinzugefügt haben, können diese die Funktionen im Zusammenhang mit dieser Rollengruppe verwalten. Um Mitglieder einer Rollengruppe hinzuzufügen oder aus dieser zu entfernen, öffnen Sie die Rollengruppe in der Exchange-Verwaltungskonsole, und fügen Sie der Mitgliedschaftsliste Mitglieder hinzu bzw. entfernen Sie Mitglieder daraus. Eine Liste mit integrierten Rollengruppen finden Sie unter [Integrierte Rollengruppen](built-in-role-groups-exchange-2013-help.md).


> [!IMPORTANT]
> Wenn ein Administrator Mitglied mehrerer Rollengruppen ist, erteilt Exchange 2013 dem Administrator die Berechtigungen aller Rollengruppen, in denen er Mitglied ist.



Wenn keine der in Exchange 2013 enthaltenen Rollengruppen die erforderlichen Berechtigungen bietet, können Sie über die Exchange-Verwaltungskonsole eine Rollengruppe erstellen und dieser die Rollen mit den erforderlichen Berechtigungen hinzufügen. Für eine neue Rollengruppe führen Sie die folgenden Aufgaben aus:

1.  Auswählen eines Namens für die Rollengruppe.

2.  Auswählen der Rollen, die zur Rollengruppe hinzugefügt werden sollen.

3.  Hinzufügen von Mitgliedern zur Rollengruppe.

4.  Speichern der Rollengruppe.

Nach dem Erstellen der Rollengruppe wird diese wie alle anderen Rollengruppen verwaltet.

Wenn eine vorhandene Rollengruppe einige, jedoch nicht alle erforderlichen Berechtigungen bietet, können Sie die Rollengruppe kopieren und anschließend Änderungen vornehmen, um eine neue Rollengruppe zu erstellen. Sie können eine vorhandene Rollengruppe kopieren und ändern, ohne dass sich dies auf die ursprüngliche Rollengruppe auswirkt. Wenn Sie die Rollengruppe kopieren, können Sie einen neuen Namen und eine Beschreibung angeben, Rollen zur neuen Rollengruppe hinzufügen oder aus dieser entfernen und neue Mitglieder hinzufügen. Beim Erstellen oder Kopieren einer Rollengruppe verwenden Sie erneut das in der Abbildung oben gezeigte Dialogfeld.

Vorhandene Rollengruppen können ebenfalls geändert werden. Über ein Dialogfeld in der Exchange-Verwaltungskonsole, das dem oben gezeigten Dialogfeld ähnelt, können Sie Rollen vorhandenen Rollengruppen hinzufügen bzw. aus diesen Gruppen entfernen und gleichzeitig Mitglieder hinzufügen oder entfernen. Durch das Hinzufügen und Entfernen von Rollen zu bzw. aus Rollengruppen aktivieren und deaktivieren Sie Verwaltungsfunktionen für Mitglieder dieser Rollengruppe. Eine Liste der Rollen, die zu einer Rollengruppe hinzugefügt werden können, finden Sie unter [Integrierte Verwaltungsrollen](built-in-management-roles-exchange-2013-help.md).


> [!NOTE]
> Wenngleich Sie ändern können, welche Rollen integrierten Rollengruppen zugewiesen sind, sollten Sie die integrierten Rollengruppen stattdessen kopieren, die Kopie der Rollengruppe ändern und anschließend Mitglieder zur Kopie der Rollengruppe hinzufügen.



Rollenbasierte Berechtigungen

## Arbeiten mit Rollenzuweisungsrichtlinien

Am besten verwenden Sie die Exchange-Verwaltungskonsole, um die Berechtigungen zu verwalten, die Sie Endbenutzern zum Verwalten ihrer eigenen Postfächer in Exchange 2013 zuweisen. Wenn Sie zum Verwalten von Endbenutzerberechtigungen die Exchange-Verwaltungskonsole verwenden, können Sie mit ein paar Mausklicks Rollen hinzufügen und entfernen oder Rollenzuweisungsrichtlinien erstellen. Um diese Aufgaben auszuführen, bietet die Exchange-Verwaltungskonsole einfache Dialogfelder wie das in der folgenden Abbildung gezeigte Dialogfeld **Rollenzuweisungsrichtlinie**.

**Dialogfeld "Rollenzuweisungsrichtlinie" in der Exchange-Verwaltungskonsole**

![Dialogfeld "Rollenzuweisungsrichtlinie" in der Exchange-Verwaltungskonsole](images/Dd351175.ecdf3cd4-d50e-4014-95f8-1bd5dafacaff(EXCHG.150).jpg "Dialogfeld \"Rollenzuweisungsrichtlinie\" in der Exchange-Verwaltungskonsole")

Exchange 2013 umfasst eine Standard-Rollenzuweisungsrichtlinie. Benutzer, deren Postfächer dieser Rollenzuweisungsrichtlinie zugeordnet sind, können folgende Aufgaben ausführen:

  - Beitreten zu oder Verlassen von Verteilergruppen, die Mitgliedern das Verwalten der eigenen Mitgliedschaft gestatten.

  - Anzeigen und Ändern grundlegender Postfacheinstellungen ihrer eigenen Postfächer. Dazu zählen z. B. Einstellungen für Posteingangsregeln, Rechtschreibprüfung, Junk-E-Mail und Microsoft ActiveSync-Geräte.

  - Ändern ihrer Kontaktinformationen, z. B. geschäftliche Adresse und Telefonnummer, Mobiltelefonnummer und Pagernummer.

  - Erstellen, Ändern oder Anzeigen von Einstellungen für Textnachrichten.

  - Anzeigen oder Ändern von Voicemaileinstellungen.

  - Anzeigen und Ändern ihrer Marketplace-Apps.

  - Erstellen von Teampostfächern und Verbinden dieser Postfächer mit Microsoft SharePoint-Listen.

Um der Standardrichtlinie für Rollenzuweisung oder einer anderen Rollenzuweisungsrichtlinie Berechtigungen hinzuzufügen oder Berechtigungen aus diesen zu entfernen, können Sie die Exchange-Verwaltungskonsole verwenden. Diese Aufgaben werden in einem Dialogfeld ausgeführt, das dem oben gezeigten ähnelt. Wenn Sie die Rollenzuweisungsrichtlinie in der Exchange-Verwaltungskonsole öffnen, aktivieren Sie die Kontrollkästchen neben den Rollen, die der Richtlinie zugewiesen werden sollen, bzw. deaktivieren Sie die Kontrollkästchen neben den Rollen, die entfernt werden sollen. Die an der Rollenzuweisungsrichtlinie vorgenommenen Änderungen werden auf alle Postfächer angewendet, die der Richtlinie zugeordnet sind.

Wenn Sie den verschiedenen Typen von Benutzern in Ihrer Organisation unterschiedliche Endbenutzerberechtigungen zuweisen möchten, können Sie Rollenzuweisungsrichtlinien erstellen. Beim Erstellen einer Rollenzuweisungsrichtlinie wird ein Dialogfeld angezeigt, das dem oben gezeigten ähnelt. Sie können einen neuen Namen für die Rollenzuweisungsrichtlinie angeben und anschließend die Rollen auswählen, die der Rollenzuweisungsrichtlinie zugewiesen werden sollen. Nach dem Erstellen einer Rollenzuweisungsrichtlinie können Sie die Richtlinie über die Exchange-Verwaltungskonsole Postfächern zuordnen.

Um die Einstellung zu ändern, welche Rollenzuweisungsrichtlinie als Standardrichtlinie verwendet wird, muss die Shell verwendet werden. Wenn Sie die Standard-Rollenzuweisungsrichtlinie ändern, werden alle neu erstellten Postfächer der neuen Standard-Rollenzuweisungsrichtlinie zugeordnet, sofern nicht explizit eine andere Richtlinie angegeben wurde. Die Rollenzuweisungsrichtlinie, die vorhandenen Postfächern zugeordnet ist, wird beim Auswählen einer neuen Standard-Rollenzuweisungsrichtlinie nicht geändert.


> [!NOTE]
> Wenn Sie ein Kontrollkästchen für eine Rolle mit untergeordneten Rollen aktivieren, werden auch die Kontrollkästchen der untergeordneten Rollen aktiviert. Wenn Sie das Kontrollkästchen für eine Rolle mit untergeordneten Rollen deaktivieren, werden auch die Kontrollkästchen der untergeordneten Rollen deaktiviert.<BR>Die Schritte zum Erstellen von Rollenzuweisungsrichtlinien bzw. zum Ändern von vorhandenen Rollenzuweisungsrichtlinien sind in den folgenden Themen näher beschrieben: 
> <UL>
> <LI>
> <P><A href="manage-role-assignment-policies-exchange-2013-help.md">Verwalten von Rollenzuweisungsrichtlinien</A></P>
> <LI>
> <P><A href="change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md">Ändern der Zuweisungsrichtlinie für ein Postfach</A></P></LI></UL>



Rollenbasierte Berechtigungen

## Dokumentation zu Berechtigungen

Die folgende Tabelle enthält Links zu Themen mit Informationen zu Berechtigungen und deren Verwaltung in Exchange 2013.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="understanding-role-based-access-control-exchange-2013-help.md">Grundlegendes zur rollenbasierten Zugriffssteuerung</a></p></td>
<td><p>Informieren Sie sich über die einzelnen RBAC-Komponenten, und erfahren Sie, wie Sie erweiterte Berechtigungsmodelle erstellen können, wenn Rollengruppen und Verwaltungsrollen nicht ausreichen.</p></td>
</tr>
<tr class="even">
<td><p><a href="understanding-multiple-forest-permissions-exchange-2013-help.md">Grundlegendes zu Berechtigungen für mehrere Gesamtstrukturen</a></p></td>
<td><p>Informieren Sie sich über das Implementieren von RBAC-Berechtigungen in Organisationen mit Konten- und Ressourcengesamtstrukturen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="understanding-split-permissions-exchange-2013-help.md">Grundlegendes zu geteilten Berechtigungen</a></p></td>
<td><p>Informieren Sie sich über das Teilen von Exchange- und Sicherheitsprinzipalverwaltung mithilfe von geteilten RBAC- und Active Directory-Berechtigungen.</p></td>
</tr>
<tr class="even">
<td><p><a href="understanding-permissions-coexistence-with-exchange-2007-and-exchange-2010-exchange-2013-help.md">Grundlegendes zur Koexistenz von Berechtigungen in Exchange 2007 und Exchange 2010</a></p></td>
<td><p>Konfigurieren Sie Berechtigungen, um die Verwaltung von Exchange 2013 in vorhandenen Exchange 2007- und Exchange 2010-Organisationen zu ermöglichen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="manage-role-groups-exchange-2013-help.md">Verwalten von Rollengruppen</a></p></td>
<td><p>Konfigurieren Sie mithilfe von Rollengruppen Berechtigungen für Exchange-Administratoren und spezielle Benutzer.</p></td>
</tr>
<tr class="even">
<td><p><a href="manage-role-group-members-exchange-2013-help.md">Verwalten von Rollengruppenmitgliedern</a></p></td>
<td><p>Fügen Sie Rollengruppen Mitglieder hinzu, und entfernen Sie Mitglieder aus Rollengruppen. Durch das Hinzufügen und Entfernen von Mitgliedern in Rollengruppen, legen Sie die Benutzer fest, die Exchange-Features verwalten können.</p></td>
</tr>
<tr class="odd">
<td><p><a href="manage-linked-role-groups-exchange-2013-help.md">Verwalten von verknüpften Rollengruppen</a></p></td>
<td><p>Konfigurieren Sie Berechtigungen für Exchange-Administratoren und spezielle Benutzer in Exchange-Bereitstellungen mit mehreren Gesamtstrukturen.</p></td>
</tr>
<tr class="even">
<td><p><a href="manage-role-assignment-policies-exchange-2013-help.md">Verwalten von Rollenzuweisungsrichtlinien</a></p></td>
<td><p>Konfigurieren Sie die Features, auf die Endbenutzer mithilfe von Rollenzuweisungsrichtlinien in ihrem Postfach zugreifen können.</p></td>
</tr>
<tr class="odd">
<td><p><a href="change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md">Ändern der Zuweisungsrichtlinie für ein Postfach</a></p></td>
<td><p>Konfigurieren Sie die Rollenzuweisungsrichtlinie, die auf mindestens ein Postfach angewendet wird.</p></td>
</tr>
<tr class="even">
<td><p><a href="create-linked-role-groups-that-mirror-built-in-role-groups-exchange-2013-help.md">Erstellen verknüpfter Rollengruppen, die integrierte Rollengruppen spiegeln</a></p></td>
<td><p>Erstellen Sie die integrierten Rollengruppen erneut als verknüpfte Rollengruppen in Exchange-Bereitstellungen mit mehreren Gesamtstrukturen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="view-effective-permissions-exchange-2013-help.md">Anzeigen geltender Berechtigungen</a></p></td>
<td><p>Zeigen Sie die Benutzer an, die über Berechtigungen zum Verwalten von Exchange-Features verfügen.</p></td>
</tr>
<tr class="even">
<td><p><a href="feature-permissions-exchange-2013-help.md">Funktionsberechtigungen</a></p></td>
<td><p>Erfahren Sie mehr über die zum Verwalten von Exchange-Features und -Diensten erforderlichen Berechtigungen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="advanced-permissions-exchange-2013-help.md">Erweiterte Berechtigungen</a></p></td>
<td><p>Verwenden Sie erweiterte RBAC-Features, um stark angepasste Berechtigungsmodelle zu erstellen, die die Anforderungen jeder beliebigen Organisation erfüllen.</p></td>
</tr>
</tbody>
</table>


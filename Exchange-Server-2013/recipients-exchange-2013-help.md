---
title: 'Empfänger: Exchange 2013 Help'
TOCTitle: Empfänger
ms:assetid: 40300ed4-85a5-463d-bb3a-cf787bd44e9d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201680(v=EXCHG.150)
ms:contentKeyID: 50475536
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Empfänger

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Die Personen und Ressource, die Nachrichten senden und empfangen, bilden den Kern jedes Systems für Messaging und Collaboration. In einer Exchange-Organisation werden diese Personen und Ressourcen als *Empfänger* bezeichnet. Ein Empfänger ist ein beliebiges E-Mail-aktiviertes Objekt in Active Directory, an das Microsoft Exchange Nachrichten übermitteln oder weiterleiten kann.

## Exchange-Empfängertypen

Microsoft umfasst verschiedene explizite Empfängertypen. Jeder Empfängertyp wird in der Exchange-Verwaltungskonsole identifiziert und verfügt in der Eigenschaft *RecipientTypeDetails* in der Exchange-Verwaltungsshell über einen eindeutigen Wert. Die Verwendung expliziter Empfängertypen besitzt die folgenden Vorteile:

  - Sie können auf einen Blick zwischen verschiedenen Empfängertypen unterscheiden.

  - Sie können nach Empfängertyp suchen und sortieren.

  - Sie können Massenverwaltungsvorgänge für ausgewählte Empfängertypen einfacher ausführen.

  - Die Anzeige von Empfängereigenschaften wird vereinfacht, da die Empfängertypen in der Exchange-Verwaltungskonsole zur Darstellung unterschiedlicher Eigenschaftenseiten verwendet werden. Die Ressourcenkapazität wird beispielsweise für ein Raumpostfach angezeigt, nicht jedoch für ein Benutzerpostfach.

In der folgenden Tabelle werden die verfügbaren Empfängertypen aufgeführt. Alle diese Empfängertypen werden weiter unten in diesem Thema ausführlicher erläutert.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Empfängertyp</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dynamische Verteilergruppe</p></td>
<td><p>Eine Verteilergruppe, die Empfängerfilter und Bedingungen zum Ableiten ihrer Mitgliedschaft beim Senden der Nachricht verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Gerätepostfach</p></td>
<td><p>Ein Ressourcenpostfach, das einer ortsunabhängigen Ressource zugewiesen wird, z. B. einem tragbaren Computer, einem Laptop, einem Mikrofon oder Firmenwagen. Gerätepostfächer können als Ressourcen in Besprechungsanfragen eingebunden und so einfach und effizient zur Nutzung von Ressourcen für Benutzer verwendet werden.</p></td>
</tr>
<tr class="odd">
<td><p>Verknüpftes Postfach</p></td>
<td><p>Ein Postfach, das einem einzelnen Benutzer in einer separaten, vertrauenswürdigen Gesamtstruktur zugewiesen wurde.</p></td>
</tr>
<tr class="even">
<td><p>E-Mail-Kontakt</p></td>
<td><p>Ein E-Mail-aktivierter Active Directory-Kontakt, der Informationen zu Personen oder Organisationen außerhalb der Exchange-Organisation enthält. Jeder E-Mail-Kontakt verfügt über eine externe E-Mail-Adresse. Alle E-Mail-Nachrichten, die an den E-Mail-Kontakt gesendet werden, werden an diese externe Adresse weitergeleitet.</p></td>
</tr>
<tr class="odd">
<td><p>Kontakt einer E-Mail-Gesamtstruktur</p></td>
<td><p>Ein E-Mail-Kontakt, der ein Empfängerobjekt aus einer anderen Gesamtstruktur darstellt. Kontakte einer E-Mail-Gesamtstruktur werden normalerweise durch die Microsoft Identity Integration Server-Synchronisierung (MIIS) erstellt.</p>

> [!IMPORTANT]
> Kontakte einer E-Mail-Gesamtstruktur sind schreibgeschützte Empfängerobjekte, die nur mithilfe von MIIS (Microsoft Identity Integration Server) oder einem ähnlichen benutzerdefinierten Synchronisierungsverfahren aktualisiert werden. Die Exchange-Verwaltungskonsole oder -Shell kann nicht zum Entfernen oder Ändern eines Kontakts einer E-Mail-Gesamtstruktur verwendet werden.


</td>
</tr>
<tr class="even">
<td><p>E-Mail-Benutzer</p></td>
<td><p>Ein E-Mail-aktivierter Active Directory-Benutzer, der einen Benutzer außerhalb der Exchange-Organisation darstellt. Jeder E-Mail-Benutzer verfügt über eine externe E-Mail-Adresse. Alle E-Mail-Nachrichten, die an den E-Mail-Benutzer gesendet werden, werden an diese externe Adresse weitergeleitet.</p>
<p>Ein E-Mail-Benutzer ist einem E-Mail-Kontakt ähnlich, mit der Ausnahme, dass ein E-Mail-Benutzer über Active Directory-Anmeldeinformationen verfügt und auf Ressourcen zugreifen kann.</p></td>
</tr>
<tr class="odd">
<td><p>E-Mail-aktivierte nicht universelle Gruppe</p></td>
<td><p>Ein E-Mail-aktiviertes globales oder lokales Gruppenobjekt von Active Directory. E-Mail-aktivierte nicht universelle Gruppen wurden in Exchange Server 2007 eingestellt und können nur vorhanden sein, wenn sie von Exchange 2003 oder früheren Exchange-Versionen migriert wurden. Sie können Exchange Server 2013 nicht verwenden, um neue nicht-universelle Verteilergruppen zu erstellen.</p></td>
</tr>
<tr class="even">
<td><p>E-Mail-aktivierter Öffentlicher Ordner</p></td>
<td><p>Ein Öffentlicher Ordner von Exchange, der für den Empfang von Nachrichten konfiguriert ist.</p></td>
</tr>
<tr class="odd">
<td><p>Verteilergruppen</p></td>
<td><p>Eine Verteilergruppe ist ein E-Mail-aktiviertes Active Directory-Verteilergruppenobjekt, das ausschließlich zum Verteilen von Nachrichten an eine Gruppe von Empfängern verwendet werden kann.</p></td>
</tr>
<tr class="even">
<td><p>E-Mail-aktivierte Sicherheitsgruppe</p></td>
<td><p>Eine E-Mail-aktivierte Sicherheitsgruppe ist ein universelles Active Directory-Sicherheitsgruppenobjekt, das zum Erteilen von Zugriffsberechtigungen auf Ressourcen in Active Directory sowie zum Verteilen von Nachrichten verwendet werden kann.</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Exchange-Empfänger</p></td>
<td><p>Ein besonderes Empfängerobjekt, das einen vereinheitlichten und bekannten Nachrichtenabsender zur Verfügung stellt, um vom System generierte Nachrichten von anderen Nachrichten zu unterscheiden. Er ersetzt den Absender &quot;Systemadministrator&quot;, der in früheren Versionen von Exchange für vom System erstellte Nachrichten verwendet wurde.</p></td>
</tr>
<tr class="even">
<td><p>Raumpostfach</p></td>
<td><p>Ein Ressourcenpostfach, das einem Besprechungsort zugewiesen wird, z. B. einem Konferenzraum, einem Hörsaal oder einem Schulungsraum. Raumpostfächer können als Ressourcen in Besprechungsanfragen eingebunden und auf diese Weise einfach und effizient zum Organisieren von Besprechungen für Benutzer verwendet werden.</p></td>
</tr>
<tr class="odd">
<td><p>Freigegebenes Postfach</p></td>
<td><p>Ein Postfach, das nicht hauptsächlich einem einzelnen Benutzer zugeordnet und im Allgemeinen so konfiguriert ist, dass der Zugriff durch mehrere Benutzer zulässig ist.</p></td>
</tr>
<tr class="even">
<td><p>Websitepostfach</p></td>
<td><p>Ein Postfach, das aus einem Exchange-Postfach zum Speichern von E-Mail-Nachrichten und einer SharePoint-Website zum Speichern von Dokumenten besteht. Benutzer können mithilfe einer einzigen Clientschnittstelle sowohl auf E-Mail-Nachrichten als auch auf Dokumente zugreifen. Weitere Informationen finden Sie unter <a href="site-mailboxes-exchange-2013-help.md">Websitepostfächer</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Benutzerpostfach</p></td>
<td><p>Ein Postfach, das einem einzelnen Benutzer in Ihrer Exchange-Organisation zugeordnet ist. Es enthält normalerweise Nachrichten, Kalenderelemente, Kontakte, Aufgaben, Dokumente und andere wichtige Geschäftsdaten.</p></td>
</tr>
<tr class="even">
<td><p>Office 365-Postfach</p></td>
<td><p>In hybriden Bereitstellungen besteht ein Office 365-Postfach aus einem E-Mail-Benutzer, der in Active Directory lokal vorhanden ist und einem zugeordneten Cloudpostfach, das in Exchange Online vorliegt.</p></td>
</tr>
<tr class="odd">
<td><p>Verknüpfter Benutzer</p></td>
<td><p>Ein verknüpfter Benutzer ist ein Benutzer, dessen Postfach in einer anderen Gesamtstruktur vorliegt als der, in welcher der Benutzer vorhanden ist.</p></td>
</tr>
</tbody>
</table>


## Postfächer

Postfächer sind der häufigste Empfängertyp, der von Information-Workern in einer Exchange-Organisation verwendet wird. Jedem Postfach ist ein Active Directory-Benutzerkonto zugeordnet. Der Benutzer kann das Postfach zum Senden und Empfangen von Nachrichten sowie zum Speichern von Nachrichten, Terminen, Aufgaben, Notizen und Dokumenten verwenden. Postfächer stellen die wichtigsten Tools für Messaging und Zusammenarbeit für die Benutzer in Ihrer Exchange-Organisation dar.

## Postfachkomponenten

Jedes Postfach besteht aus einem Active Directory-Benutzer und den Postfachdaten, die in der Exchange-Postfachdatenbank gespeichert sind (wie in der folgenden Abbildung gezeigt). Sämtliche Konfigurationsdaten für das Postfach werden in den Exchange-Attributen des Active Directory-Benutzerobjekts gespeichert. Die Postfachdatenbank enthält die tatsächlichen Daten, die sich in dem Benutzerkonto zugeordneten Postfach befinden.


> [!IMPORTANT]
> Wenn Sie ein Postfach für einen neuen oder vorhandenen Benutzer erstellen, werden die Exchange-Attribute, die für ein Postfach erforderlich sind, dem Benutzerobjekt in Active Directory hinzugefügt. Die zugehörigen Postfachdaten werden erst erstellt, wenn das Postfach eine Nachricht empfängt oder sich der Benutzer beim Postfach anmeldet.



**Postfachkomponenten**

![Bestandteile eines Postfachs](images/Bb201680.5fcb5e6d-656e-42ae-871f-0eef8aea456b(EXCHG.150).gif "Bestandteile eines Postfachs")


> [!WARNING]
> Wenn Sie ein Postfach entfernen, wird die Exchange-Postfachdatenbank zum Löschen markiert, und auch das zugehörige Benutzerkonto wird aus Active Directory gelöscht. Um das Benutzerkonto beizubehalten und nur die Postfachdaten zu löschen, müssen Sie das Postfach deaktivieren.



## Postfachtypen

Exchange unterstützt die folgenden Postfachtypen:

  - **Benutzerpostfächer   **Benutzerpostfächer werden einzelnen Benutzern in Ihrer Exchange-Organisation zugeordnet. Benutzerpostfächer stellen Ihren Benutzern eine reichhaltige Plattform für Collaboration zur Verfügung. Benutzer können Nachrichten senden und empfangen, ihre Kontakte verwalten, Besprechungen planen und eine Aufgabenliste verwalten. Sie können auch Voicemailnachrichten an ihre Postfächer übermitteln lassen. Benutzerpostfächer sind der am häufigsten verwendete Postfachtyp, und es ist normalerweise dieser Postfachtyp, der Benutzern in einer Organisation zugewiesen wird.

  - **Verknüpfte Postfächer**   Verknüpfte Postfächer sind Postfächer, auf die Benutzer in einer getrennten, vertrauenswürdigen Gesamtstruktur zugreifen. Verknüpfte Postfächer sind ggf. für Organisationen erforderlich, die Exchange in einer Ressourcengesamtstruktur bereitstellen. Mit dem Ressourcengesamtstruktur-Szenario kann eine Organisation Exchange in einer Einzelgesamtstruktur zentralisieren und dabei den Zugriff auf die Exchange-Organisation mit Benutzerkonten in mindestens einer vertrauenswürdigen Gesamtstruktur zur Verfügung stellen.
    
    Wie bereits erwähnt, muss jedem Postfach ein Benutzerkonto zugeordnet sein. Das Benutzerpostfach, das auf das verknüpfte Postfach zugreift, ist jedoch nicht in der Gesamtstruktur vorhanden, in der Exchange bereitgestellt wird. Aus diesem Grund ist ein deaktiviertes Benutzerkonto, das in der gleichen Gesamtstruktur wie Exchange vorhanden ist, jedem verknüpften Postfach zugeordnet. Die folgende Abbildung zeigt die Beziehung zwischen dem verknüpften Benutzerkonto, das für den Zugriff auf das verknüpfte Postfach verwendet wird, und dem deaktivierten Benutzerkonto in der Exchange-Ressourcengesamtstruktur, das dem verknüpften Postfach zugeordnet ist.
    
    **Verknüpftes Postfach**
    
    ![Komplexe Exchange-Organisation mit Ressourcengesamtstruktur](images/Aa998031.706725cf-e520-4b89-a275-acd8fb58943a(EXCHG.150).gif "Komplexe Exchange-Organisation mit Ressourcengesamtstruktur")  

  - **Office 365-Postfächer**   Wenn Sie ein Office 365-Postfach in Exchange Online in einer hybriden Bereitstellung erstellen, wird der E-Mail-Benutzer lokal in Active Directory erstellt. Die Verzeichnissynchronisierung, sofern konfiguriert, synchronisiert dieses neue Objekt automatisch mit Office 365, wo es in Exchange Online in ein Cloudpostfach konvertiert wird. Sie können Office 365-Postfächer als reguläre Benutzerpostfächer, Ressourcenpostfächer für Besprechungsräume und Geräte sowie als freigegebene Postfächer erstellen.

  - **Freigegebene Postfächer**   Freigegebene Postfächer sind nicht primär einzelnen Benutzern zugeordnet und sind im Allgemeinen so konfiguriert, dass der Zugriff durch mehrere Benutzer zulässig ist.
    
    Es ist zwar möglich, weiteren Benutzern Zugriffsberechtigungen für beliebige Postfachtypen zuzuweisen, die freigegebenen Postfächer erfüllen jedoch genau diesen Zweck. Der Active Directory-Benutzer, der einem freigegebenen Postfach zugeordnet wird, muss ein deaktiviertes Benutzerkonto sein. Nachdem ein freigegebenes Postfach erstellt wurde, müssen Sie allen Benutzern Berechtigungen zuweisen, die Zugriff auf das freigegebene Postfach benötigen.

  - **Ressourcenpostfächer**   Ressourcenpostfächer sind besondere Postfächer, die zum Planen von Ressourcen konzipiert wurden. Ebenso wie alle anderen Postfachtypen besitzt ein Ressourcenpostfach ein zugehöriges Active Directory-Benutzerkonto. Es muss sich jedoch um ein deaktiviertes Konto handeln. Es gibt die folgenden Typen von Ressourcenpostfächern:
    
      - **Raumpostfächer:**    Diese Postfächer sind Besprechungsorten zugewiesen, z. B. Konferenzräumen, Hörsälen und Schulungsräumen.
    
      - **Gerätepostfächer**   Hierbei handelt es sich um Postfächer, die ortsunabhängigen Ressourcen zugewiesen sind, wie z. B. tragbaren Computern, Projektoren, Mikrofonen oder Firmenwagen.
    
    Beide Typen von Ressourcenpostfächern können in Besprechungsanfragen eingebunden und auf diese Weise einfach und effizient zur Nutzung von Ressourcen für Benutzer verwendet werden. Sie können Ressourcenpostfächer so konfigurieren, dass eingehende Besprechungsanfragen basierend auf den Ressourcenbuchungsrichtlinien, die durch die Ressourcenbesitzer definiert wurden, automatisch verarbeitet werden. Ein Konferenzraum kann z. B. so konfiguriert werden, dass er automatisch eingehende Besprechungsanfragen mit Ausnahme von Besprechungsserien zusagt, die durch den Ressourcenbesitzer genehmigt werden müssen.

## Systempostfächer

Systempostfächer werden während der Installation von Exchange in der Stammdomäne der Active Directory-Gesamtstruktur erstellt. Benutzer oder Administratoren können sich nicht bei diesen Postfächern anmelden. Systempostfächer werden für Exchange-Funktionen wie beispielsweise Unified Messaging (UM), Migration, Nachrichtengenehmigung und Compliance-eDiscovery erstellt. Diese Tabelle enthält Informationen zu Systempostfächern, die in Active Directory angezeigt werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Postfach</th>
<th>Name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organization</p></td>
<td><p>SystemMailbox {bb558c35-97f1-4cb9-8ff7-d53741dc928c}</p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenbestätigung</p></td>
<td><p>SystemMailbox {1f05a927-<em>xxxx</em>- <em>xxxx</em> - <em>xxxx</em> -<em>xxxxxxxxxxxx</em>}</p>
<p>Hierbei steht <em>x</em> für eine zufällig zugewiesene und eindeutige Zahl für jede Exchange-Gesamtstruktur</p></td>
</tr>
<tr class="odd">
<td><p>UM-Datenspeicher</p></td>
<td><p>SystemMailbox {e0dc1c29-89c3-4034-b678-e6c29d823ed9}</p></td>
</tr>
<tr class="even">
<td><p>Ermittlung</p></td>
<td><p>DiscoverySearchMailbox {D919BA05-46A6-415f-80AD-7E09334BB852}</p></td>
</tr>
<tr class="odd">
<td><p>Verbund-E-Mail</p></td>
<td><p>FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042</p></td>
</tr>
<tr class="even">
<td><p>Migration</p></td>
<td><p>Migration.8f3e7716-2011-43e4-96b1-aba62d229136</p></td>
</tr>
</tbody>
</table>


Wenn Sie den letzten Postfachserver in der Exchange-Organisation außer Betrieb nehmen möchten, sollten Sie zuerst diese Systempostfächer mithilfe des Cmdlets [Disable-Mailbox](https://technet.microsoft.com/de-de/library/aa997210\(v=exchg.150\)) deaktivieren. Wenn Sie einen Postfachserver außer Betrieb nehmen, der diese Systempostfächer enthält, sollten Sie die Systempostfächer auf einen anderen Postfachserver verschieben, um sicherzustellen, dass keine Funktionalität verloren geht.

## Planen von Postfächern

Postfächer werden in Postfachdatenbanken auf Servercomputern mit Exchange erstellt, auf denen die Postfachserverrolle installiert ist. Damit eine zuverlässige und effektive Plattform für Ihre Postfachbenutzer zur Verfügung gestellt werden kann, ist eine ausführliche Planung der Bereitstellung von Postfachservern und Datenbanken wesentlich. Weitere Informationen zur Planung von Postfachservern und Datenbanken finden Sie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md).

## Verteilergruppen

Verteilergruppen sind E-Mail-aktivierte Active Directory-Gruppenobjekte, die hauptsächlich für das Verteilen von Nachrichten an mehrere Empfänger verwendet werden. Jeder beliebige Empfängertyp kann Mitglied einer Verteilergruppe sein.


> [!IMPORTANT]
> Beachten Sie die Terminologieunterschiede zwischen Active Directory und Exchange. In Active Directory wird eine beliebige Gruppe ohne Sicherheitskontext als Verteilergruppe bezeichnet, unabhängig davon, ob sie E-Mail-aktiviert ist oder nicht. In Exchange werden alle E-Mail-aktivierten Gruppen als Verteilergruppen bezeichnet – unabhängig davon, ob sie in einen Sicherheitskontext eingebunden sind oder nicht.



Exchange unterstützt die folgenden Typen von Verteilergruppen:

  - **Verteilergruppen**   Hierbei handelt es sich um universelle Active Directory-Verteilergruppenobjekte, die E-Mail-aktiviert sind. Sie können ausschließlich zum Verteilen von Nachrichten an eine Gruppe von Empfängern verwendet werden.

  - **E-Mail-aktivierte Sicherheitsgruppen**   Hierbei handelt es sich um universelle Active Directory-Sicherheitsgruppenobjekte, die E-Mail-aktiviert sind. Sie können zur Zuweisung von Zugriffsberechtigungen auf Ressourcen in Active Directory sowie zum Verteilen von Nachrichten verwendet werden.

  - **E-Mail-aktivierte nicht universelle Gruppen**   Dabei handelt es sich um globale oder lokale Active Directory-Gruppenobjekte, die E-Mail-aktiviert sind. Sie können nur universelle Verteilergruppen erstellen bzw. für E-Mail aktivieren. Möglicherweise verfügen Sie über E-Mail-aktivierte Gruppen, die aus früheren Versionen von Exchange migriert wurden und bei denen es sich nicht um universelle Gruppen handelt. Diese Gruppen können weiterhin über die Exchange-Verwaltungskonsole oder die Shell verwaltet werden.
    

    > [!NOTE]
    > Zum Konvertieren einer globalen oder lokalen Gruppe der Domäne in eine universelle Gruppe können Sie das Cmdlet <A href="https://technet.microsoft.com/de-de/library/bb123770(v=exchg.150)">Set-Group</A> in der Shell verwenden.



## Dynamische Verteilergruppen

Dynamische Verteilergruppen sind Verteilergruppen, deren Mitgliedschaft auf bestimmten Empfängerfiltern und nicht auf einer definierten Empfängergruppe basiert.

Im Gegensatz zu normalen Verteilergruppen wird die Mitgliederliste für dynamische Verteilergruppen basierend auf den von Ihnen angegebenen Filtern und Bedingungen jedes Mal berechnet, wenn eine Nachricht an die Gruppe übermittelt wird. Wenn eine E-Mail-Nachricht an eine dynamische Verteilergruppe gesendet wird, wird sie an alle Empfänger in der Organisation zugestellt, die den für die dynamische Verteilergruppe definierten Kriterien entsprechen.


> [!IMPORTANT]
> Eine dynamische Verteilergruppe umfasst alle Empfänger in Active Directory, die Attribute besitzen, die dem Filter der Gruppe zum Zeitpunkt des Sendens der Nachricht entsprechen. Werden die Eigenschaften eines Empfängers geändert, damit sie dem Filter der Gruppe entsprechen, kann dieser Empfänger ggf. versehentlich ein Gruppenmitglied werden und Nachrichten erhalten, die an die dynamische Verteilergruppe gesendet werden. Eindeutige und konsistente Kontobereitstellungsverfahren verringern dieses Risiko.



Zur Unterstützung beim Erstellen von Empfängerfiltern für dynamische Verteilergruppen können Sie Musterfilter verwenden. Bei einem *Musterfilter* handelt es sich um einen gängigen Filter, mit dem verschiedene Kriterien der Empfängerfilterung erfüllt werden. Sie können mit diesen Filtern die Empfängertypen angeben, die in die dynamische Verteilergruppe aufgenommen werden sollen. Außerdem können Sie eine Liste mit Bedingungen angeben, die die Empfänger erfüllen müssen. Sie können Musterbedingungen basierend auf den folgenden Eigenschaften erstellen:

  - Benutzerdefinierte Attribute 1–15

  - Bundesland oder Kanton

  - Firma

  - Abteilung

  - Empfängercontainer

Sie können Bedingungen auch basierend auf anderen Empfängereigenschaften als den oben genannten angeben. Zu diesem Zweck müssen Sie mithilfe der Shell eine benutzerdefinierte Abfrage für die dynamische Verteilergruppe erstellen. Denken Sie daran, dass die Filter- und Bedingungseinstellungen für dynamische Verteilergruppen mit benutzerdefinierten Empfängerfiltern nur über die Shell verwaltet werden können. Ein Beispiel dafür, wie eine dynamische Verteilergruppe mithilfe einer benutzerdefinierten Abfrage erstellt wird, finden Sie unter [Verwalten dynamischer Verteilergruppen](https://technet.microsoft.com/de-de/library/Bb123722(v=EXCHG.150)).

## E-Mail-Kontakte

E-Mail-Kontakte enthalten normalerweise Informationen über Personen oder Organisationen außerhalb Ihrer Exchange-Organisation. E-Mail-Kontakte können in der globalen Adressliste (GAL) Ihrer Organisation und anderen Adresslisten enthalten sein und können Verteilergruppen als Mitglieder hinzugefügt werden. Jeder Kontakt besitzt eine externe E-Mail-Adresse, und alle an einen Kontakt gesendeten E-Mail-Nachrichten werden automatisch an diese Adresse weitergeleitet. Kontakte eignen sich ideal zur Darstellung von Personen außerhalb Ihrer Exchange-Organisation (im freigegebenen Adressbuch), die keinen Zugriff auf interne Ressourcen benötigen. Die folgenden E-Mail-Kontakttypen stehen zur Verfügung:

  - **E-Mail-Kontakte**   Dabei handelt es sich um E-Mail-aktivierte Active Directory-Kontakte, die Informationen über Personen oder Organisationen außerhalb der Exchange-Organisation enthalten.

  - **Kontakte einer E-Mail-Gesamtstruktur**   Dabei handelt es sich um Empfängerobjekte aus einer anderen Gesamtstruktur. Diese Kontakte werden normalerweise durch die Verzeichnissynchronisierung erstellt. Kontakte einer E-Mail-Gesamtstruktur sind schreibgeschützte Empfängerobjekte, die nur mithilfe der Synchronisierung entfernt werden können. Es ist nicht möglich, Exchange-Verwaltungsschnittstellen zum Ändern oder Entfernen eines E-Mail-Gesamtstrukturkontakts zu verwenden.

## E-Mail-Benutzer

E-Mail-Benutzer ähneln den E-Mail-Kontakten. Beide verfügen über externe E-Mail-Adressen und können Informationen zu Personen außerhalb Ihrer Exchange-Organisation enthalten, und beide können im freigegebenen Adressbuch und in anderen Adresslisten angezeigt werden. Im Gegensatz zu E-Mail-Kontakten verfügen E-Mail-Benutzer jedoch über Anmeldeinformationen für Active Directory und können auf die Ressourcen zugreifen, für die ihnen Berechtigungen zugewiesen wurden.

Wenn eine Person außerhalb Ihrer Organisation Zugriff auf Ressourcen im Netzwerk benötigt, sollten Sie einen E-Mail-Benutzer und keinen E-Mail-Kontakt erstellen. Sie können z. B. E-Mail-Benutzer für kurzzeitig tätige Berater erstellen, die Zugriff auf Ihre Serverinfrastruktur benötigen, jedoch ihre eigene externe E-Mail-Adresse verwenden.

Ein anderes Szenario ist, wenn Sie E-Mail-Benutzer für Benutzer in Ihrer Organisation erstellen, für die Sie kein Exchange-Postfach verwalten möchten. Nach einer Übernahme verwaltet das übernommene Unternehmen z. B. seine eigene separate Messaginginfrastruktur, benötigt aber ggf. Zugriff auf Ressourcen in Ihrem Netzwerk. Für diese Benutzer können Sie z. B. E-Mail-Benutzer anstatt Postfachbenutzer erstellen.


> [!NOTE]
> Verwenden Sie in der Exchange-Verwaltungskonsole die Seite <STRONG>Empfänger</STRONG> &gt; <STRONG>Kontakte</STRONG>, um E-Mail-Benutzer zu erstellen und zu verwalten. Für E-Mail-Benutzer ist keine separate Seite vorhanden.



## E-Mail-aktivierte Öffentliche Ordner

Öffentliche Ordner dienen als Repository für Informationen, die von zahlreichen Benutzern gemeinsam verwendet werden. Durch die E-Mail-Aktivierung für einen Öffentlichen Ordner erhalten Benutzer eine zusätzliche Funktionsebene. Benutzer können nicht nur Nachrichten im Ordner bereitstellen, sondern auch E-Mail-Nachrichten an den öffentlichen Ordner senden und in einigen Fällen auch E-Mail-Nachrichten vom öffentlichen Ordner empfangen. Für jeden E-Mail-aktivierten Ordner ist in Active Directory ein Objekt vorhanden, in dem die E-Mail-Adresse, der Adressbuchname und weitere E-Mail-Attribute des Ordners gespeichert sind.

Legacypostfächer können über die Exchange-Verwaltungskonsole oder die Shell verwaltet werden. Weitere Informationen zum Verwalten von Öffentlichen Ordnern finden Sie unter [Öffentliche Ordner](public-folders-exchange-2013-help.md).

## Microsoft Exchange-Empfänger

Der Microsoft Exchange-Empfänger ist ein besonderes Empfängerobjekt, das einen vereinheitlichten und bekannten Nachrichtenabsender zur Verfügung stellt, um vom System generierte Nachrichten von anderen Nachrichten zu unterscheiden. Er ersetzt den Absender "System Administrator", der in früheren Versionen von Microsoft Exchange für vom System erstellte Nachrichten verwendet wurde.

Der Microsoft Exchange-Empfänger ist kein typisches Empfängerobjekt, wie etwa ein Postfach, ein E-Mail-Benutzer oder ein E-Mail-Kontakt, und wird nicht mithilfe der üblichen Empfängertools verwaltet. Sie können jedoch das Cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)) in der Shell verwenden, um den Microsoft Exchange-Empfänger zu konfigurieren.


> [!NOTE]
> Wenn vom System generierte Nachrichten an einen externen Absender gesendet werden, wird der Microsoft Exchange-Empfänger nicht als Absender der Nachricht verwendet. Stattdessen wird die im Cmdlet <A href="https://technet.microsoft.com/de-de/library/bb124151(v=exchg.150)">Set-TransportConfig</A> durch den Parameter <EM>ExternalPostmasterAddress</EM> angegebene E-Mail-Adresse verwendet.



## Empfängerdokumentation

In der folgenden Tabelle sind Links zu Themen aufgeführt, in denen Sie weitere Informationen zu Exchange-Empfängern sowie zur Verwaltung dieser Empfänger finden.


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
<td><p><a href="create-user-mailboxes-exchange-2013-help.md">Erstellen von Benutzerpostfächern</a></p></td>
<td><p>Hier erfahren Sie, wie Benutzerpostfächer mithilfe der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell erstellt werden.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes">Verwalten von Benutzerpostfächern</a></p></td>
<td><p>Hier erfahren Sie, wie Sie Benutzerpostfächer erstellen, Postfacheigenschaften ändern und ausgewählte Eigenschaften für mehrere Postfächer per Massenvorgang bearbeiten.</p></td>
</tr>
<tr class="odd">
<td><p><a href="manage-linked-mailboxes-exchange-2013-help.md">Verwalten verknüpfter Postfächer</a></p></td>
<td><p>Hier erfahren Sie, welche Anforderungen für verknüpfte Postfächer gelten, wie Sie verknüpfte Postfächer erstellen und mit einem Hauptkonto verknüpfen und wie Sie die Eigenschaften verknüpfter Postfächer ändern.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups">Erstellen und Verwalten von Verteilergruppen</a></p></td>
<td><p>Hier erfahren Sie, wie Sie Verteilergruppen erstellen und verwalten und eine Gruppenbenennungsrichtlinie für Ihre Organisation erstellen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups">Verwalten von E-Mail-aktivierten Sicherheitsgruppen</a></p></td>
<td><p>Hier erfahren Sie, wie Sie E-Mail-aktivierte Sicherheitsgruppen erstellen und verwalten.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups">Verwalten dynamischer Verteilergruppen</a></p></td>
<td><p>Hier erfahren Sie, wie Sie dynamische Verteilergruppen erstellen und deren Eigenschaften verwalten, beispielsweise benutzerdefinierte Attribute und weitere Eigenschaften zum Ermitteln der Gruppenmitgliedschaft.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-mail-contacts">Verwalten von E-Mail-Kontakten</a></p></td>
<td><p>Hier erfahren Sie, wie Sie E-Mail-Kontakte erstellen und verwalten.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-mail-users">Verwalten von E-Mail-Benutzern</a></p></td>
<td><p>Hier erfahren Sie, wie Sie E-Mail-Benutzer erstellen und verwalten.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-room-mailboxes">Erstellen und Verwalten von Raumpostfächern</a></p></td>
<td><p>Hier erfahren Sie, wie Sie Raumpostfächer erstellen und deren Eigenschaften verwalten, beispielsweise die Aktivierung von Besprechungsserien sowie das Konfigurieren von Buchungs- und Planungsoptionen.</p></td>
</tr>
<tr class="even">
<td><p><a href="manage-equipment-mailboxes-exchange-2013-help.md">Verwalten von Gerätepostfächern</a></p></td>
<td><p>Hier erfahren Sie, wie Sie Gerätepostfächer erstellen, Buchungs- und Planungsoptionen konfigurieren und weitere Postfacheigenschaften verwalten.</p></td>
</tr>
<tr class="odd">
<td><p><a href="disconnected-mailboxes-exchange-2013-help.md">Getrennte Postfächer</a></p></td>
<td><p>Hier erhalten Sie Informationen zu den beiden Typen getrennter Postfächer und zur Arbeit mit diesen Postfächern.</p></td>
</tr>
<tr class="even">
<td><p><a href="custom-attributes-exchange-2013-help.md">Benutzerdefinierte Attribute</a></p></td>
<td><p>Hier erfahren Sie, wie Informationen über einen Empfänger mithilfe von benutzerdefinierten Attributen hinzugefügt werden.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/bb124268(v=exchg.150)">Filter in Shell-Empfängerbefehlen</a></p></td>
<td><p>Hier erfahren Sie, wie muster- oder benutzerdefinierte Filter mit Befehlen zum Filtern einer Menge von Empfängern verwendet werden.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Verwalten von Berechtigungen für Empfänger</a></p></td>
<td><p>Hier erfahren Sie, wie Benutzern und Gruppen mithilfe der Exchange-Verwaltungskonsole oder der Shell Berechtigungen zugewiesen werden.</p></td>
</tr>
<tr class="odd">
<td><p><a href="automatic-mailbox-distribution-exchange-2013-help.md">Automatische Postfachverteilung</a></p></td>
<td><p>Erfahren Sie mehr über die Funktionsweise der automatischen Postfachverteilung und die Steuerung, welche Postfachdatenbanken für neue und verschobene Postfächer ausgewählt werden.</p></td>
</tr>
</tbody>
</table>


---
title: 'Freigabe: Exchange 2013 Help'
TOCTitle: Freigabe
ms:assetid: 09e6732a-4e99-44d0-801d-9463fdc57a9b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638083(v=EXCHG.150)
ms:contentKeyID: 50475041
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Freigabe

 

_**Gilt für:** Exchange Server 2013, Outlook 2013_

_**Letztes Änderungsdatum des Themas:** 2015-02-27_

Es kann vorkommen, dass Sie Terminpläne mit Mitarbeitern verschiedener Organisationen oder mit Freunden oder Familienmitgliedern koordinieren müssen, um zusammen an Projekten arbeiten oder Unternehmungen planen zu können. Mit Exchange 2013 können Administratoren verschiedene Stufen von Kalenderzugriffen einrichten, über die Unternehmen mit anderen Unternehmen zusammenarbeiten oder Anwender ihre Terminpläne mit anderen teilen können. Die unternehmensübergreifende Kalenderfreigabe wird durch Anlegen von *Organisationsbeziehungen* eingerichtet. Kalenderfreigaben zwischen Benutzern werden durch Anwendung von *Freigaberichtlinien* eingerichtet.


> [!IMPORTANT]
> Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



**Inhalt**

Freigabeszenarios in Exchange 2013

Einschränkungen bei der Freigabe von Frei/Gebucht-Informationen

Überlegungen zur Firewall bei der Verbundfreigabe

Koexistenz mit Exchange 2010

Koexistenz mit Exchange 2007

Dokumentation zur Freigabe

## Freigabeszenarios in Exchange 2013

Die folgenden Freigabeszenarios werden in Exchange 2013 unterstützt:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Freigabeziel</th>
<th>Zu verwendende Einstellung</th>
<th>Anforderungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Freigeben von Kalendern mit einer Office 365-Organisation</p></td>
<td><p>Organisationsbeziehungen</p></td>
<td><p>Die Office 365-Organisation kann konfiguriert werden. Der lokale Exchange-Administrator muss eine Administrationsbeziehung mit der Cloud (auch als &quot;Verbund&quot; bezeichnet') einrichten, die die minimalen Software-Anforderungen erfüllt. Weitere Informationen zur Verbundeinrichtung finden Sie unter <a href="federation-exchange-2013-help.md">Verbund</a>.</p></td>
</tr>
<tr class="even">
<td><p>Freigeben von Kalendern mit einer anderen lokalen Exchange-Organisation</p></td>
<td><p>Organisationsbeziehungen</p></td>
<td><p>Beide lokalen Exchange-Organisationen müssen einen Verbund einrichten und die minimalen Software-Anforderungen erfüllen</p></td>
</tr>
<tr class="odd">
<td><p>Freigabe eines Exchange-Benutzer-Kalenders für einen Internet-Benutzer</p></td>
<td><p>Freigaberichtlinien</p></td>
<td><p>Keine, bereit zur Konfiguration</p></td>
</tr>
<tr class="even">
<td><p>Freigabe eines Exchange-Benutzer-Kalenders für einen anderen lokalen Exchange-Benutzer</p></td>
<td><p>Freigaberichtlinien</p></td>
<td><p>Beide lokalen Exchange-Organisationen müssen einen Verbund einrichten und die minimalen Software-Anforderungen erfüllen</p></td>
</tr>
</tbody>
</table>


In der folgenden Tabelle sind die Unterschiede zwischen Organisationsbeziehungen und Freigaberichtlinien aufgeführt.

### Organisationsbeziehungen und Freigaberichtlinien im Vergleich

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktionalität</th>
<th>Organisationsbeziehung</th>
<th>Freigaberichtlinie</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Erfordert eine Verbundvertrauensstellung für Ihre Organisation</p></td>
<td><p>Ja</p></td>
<td><p>Ja, bei der Freigabe für andere Verbunddomänenorganisationen. Nicht erforderlich für Internetfreigaberichtlinien.</p></td>
</tr>
<tr class="even">
<td><p>Empfiehlt das Hinzufügen der externen Domäne zum Verbund</p></td>
<td><p>Ja</p></td>
<td><p>Ja, bei der Freigabe für andere Verbunddomänenorganisationen. Nicht erforderlich für Internetfreigaberichtlinien.</p></td>
</tr>
<tr class="odd">
<td><p>Erlaubt einer großen Benutzergruppe die Freigabe von Frei/Gebucht-Informationen (einschließlich Betreff und Ort) für externe Organisationen.</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>Erlaubt die Freigabe von Kalenderordnern mit Frei/Gebucht-Informationen</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Erlaubt die Freigabe von Kalenderordnern mit Frei/Gebucht-Informationen plus Betreff und Nachrichtentext</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Erfordert, dass Benutzer eine Einladung zur Freigabe an externe Empfänger senden</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Stellt eine Zugriffsmethode bereit</p></td>
<td><p>Ihr Clientzugriffsserver greift bei Bedarf auf den Clientzugriffsserver der externen Organisation zu und ruft Frei/Gebucht-Informationen für den externen Benutzer ab.</p></td>
<td><p>Ihr Clientzugriffsserver greift auf den Clientzugriffsserver der externen Organisation zu und abonniert den Kalenderordner des externen Benutzers. Bei Internetfreigaberichtlinien greifen externe Benutzer entweder auf eine eingeschränkte oder eine öffentliche URL auf dem Clientzugriffsserver zu.</p></td>
</tr>
<tr class="even">
<td><p>Kann auf alle externen Domänen angewendet werden</p></td>
<td><p>Nein (eine 1:1-Beziehung zwischen zwei Exchange 2013-Organisationen)</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Bietet Benutzern in Bezug auf die Freigabe für externe Empfänger eine andere Erfahrung</p></td>
<td><p>Nein</p></td>
<td><p>Ja, basierend auf der angewendeten Freigaberichtlinie</p></td>
</tr>
<tr class="even">
<td><p>Deaktiviert die Freigabe für einige Benutzer</p></td>
<td><p>Ja, durch Angeben einer Sicherheitsverteilergruppe für die Organisationsbeziehung</p></td>
<td><p>Ja, durch Deaktivieren der angewendeten Freigaberichtlinie</p></td>
</tr>
<tr class="odd">
<td><p>Erfordert, dass sich das Postfach auf einem Exchange 2013-Postfachserver befindet</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Einschränkungen bei der Freigabe von Frei/Gebucht-Informationen

Für die gemeinsame Nutzung von Frei/Gebucht-Informationen zwischen Exchange-Organisationen gelten die folgenden Einschränkungen:

1.  **Outlook Web Access 2003**   Wenn ein Benutzer in einer Exchange 2003-Organisation Outlook Web Access für den Zugriff auf Frei/Gebucht-Informationen für Benutzer in einer Exchange 2013-Remoteorganisation verwendet, treten bei der Anforderung Fehler auf. Von Exchange 2003 ausgehende Outlook Web Access-Verbindungen können keine WebDAV-Verbindungen (Web-based Distributed Authoring and Versioning) mit einem Frei/Gebucht-Systemordner herstellen, um Frei/Gebucht-Informationen für Remotebenutzer abzurufen. Da Exchange 2013 keine Unterstützung für WebDAV-Verbindungen bietet, kann der Exchange 2003-Server für Outlook Web Access-Anforderungen keine Verbindung mit "External (FYDIBOHF25SPDLT)" auf dem Exchange 2013-Clientzugriffsserver herstellen. Für Outlook-Clients gilt diese Einschränkung nicht, da diese Clients nicht WebDAV, sondern MAPI zur Herstellung einer Verbindung mit "External (FYDIBOHF25SPDLT)" verwenden.

2.  **WAN-Latenz**   In Exchange 2003-Organisationen müssen sich die Replikate für alle Frei/Gebucht-Ordner auf Exchange 2010 SP2-Postfachservern oder höher befinden. In Umgebungen, in denen Öffentliche Ordner-Datenbanken aus Exchange 2003 an verschiedenen physischen Standorten vorhanden sind, kann es zu übermäßigen Wartezeiten und Leistungsproblemen kommen, wenn interne Frei/Gebucht-Anforderungen über WAN-Leitungen geleitet werden, um auf Öffentliche Ordner-Datenbanken in Exchange 2010 zuzugreifen, die sich nicht am selben physischen Standort befinden.

3.  **Zeitraum für Frei/Gebucht-Informationen**   Bei Anforderungen von Frei/Gebucht-Informationen, die von einer Exchange 2013-Organisation an eine Exchange 2007-Organisation gesendet werden, treten aufgrund eines ungleichen Zeitraums für Frei/Gebucht-Informationen möglicherweise Fehler auf. Standardmäßig akzeptiert Exchange 2007 Verfügbarkeitsanforderungen für Frei/Gebucht-Informationen für 42 Tage, wohingegen Exchange 2013 Frei/Gebucht-Informationen für einen Zeitraum von 62 Tagen anfordern kann. Wenn die Anforderung das Standardlimit von 42 Tagen für Exchange 2007 überschreitet, treten bei der Anforderung Fehler auf.
    
    Führen Sie die folgenden Schritte aus, um Ihren Exchange 2007-Clientzugriffsserver so zu konfigurieren, dass bei Anforderungen von Frei/Gebucht-Informationen längere Zeiträume akzeptiert werden:
    
    1.  Öffnen Sie auf allen Exchange 2007-Clientzugriffsservern die folgende Datei in einem Text-Editor: \<Exchange-Installationspfad\>\\V14\\ClientAccess\\ExchWeb\\EWS\\web.config
        

        > [!WARNING]
        > Bevor Sie Änderungen an der Datei "web.config" vornehmen, erstellen Sie eine Kopie der Datei, und speichern Sie diese an einem sicheren Ort.

    
    2.  Suchen Sie in der Datei web.config nach dem Abschnitt **appSettings**.
    
    3.  Fügen Sie einen neuen Schlüssel namens "\<add key="maximumQueryIntervalDays" value="62" /\>" hinzu, und speichern Sie die Datei web.config.
        

        > [!NOTE]
        > Der Wert maximumQueryIntervalDays ist standardmäßig nicht vorhanden. Wenn dieser Wert nicht vorhanden ist, verwendet Exchange&nbsp;2007 das Standardintervall von 42&nbsp;Tagen.

    
    4.  Beenden Sie die Microsoft-Internetinformationsdienste (IIS) auf allen Exchange 2007-Clientzugriffsservern, und starten Sie IIS anschließend neu.

4.  **Exchange-Organisationen, die sowohl lokale als auch Cloudbenutzer umfassen**   Wenn Sie die Kalenderfreigabe mit einer anderen Exchange-Organisation konfigurieren, die in einer Hybridbereitstellung mit Microsoft Office 365 konfiguriert ist, treten bei Frei/Gebucht-Verfügbarkeitsanforderungen für Office 365-basierte Benutzer oder Remotebenutzer, die in die Cloud verschoben wurden, Fehler auf. Da die Organisationsbeziehung für Ihre Exchange-Organisation nicht mit der Office 365-basierten Exchange Online-Organisation, sondern mit der lokalen Exchange-Remoteorganisation eingerichtet wurde, können keine Frei/Gebucht-Anforderungen für die Office 365-basierten Benutzer ausgeführt werden. Exchange 2013 bietet keine Unterstützung für Funktionen, mit der diese Verfügbarkeitsanforderungen über die lokale Organisation an den Office 365-Dienst weitergeleitet werden.

Einzelheiten zum Konfigurieren der Freigabe von Frei/Gebucht-Informationen zwischen Exchange-Bereitstellungen finden Sie unter [Konfigurieren von Verbundfreigaben zwischen Exchange-Organisationen](configuring-federated-sharing-between-exchange-organizations-exchange-2013-help.md).

## Überlegungen zur Firewall bei der Verbundfreigabe

Für die Funktionen der Verbundfreigabe müssen die Clientzugriffsserver in Ihrer Organisation über ausgehenden HTTPS-Zugriff auf das Internet verfügen. Sie müssen für alle Exchange 2013-Postfachserver in der Organisation ausgehenden HTTPS-Zugriff einrichten (Port 443 für TCP).

Damit eine externe Organisation auf die Frei/Gebucht-Informationen Ihrer Organisation zugreifen kann, müssen Sie mindestens einen Clientzugriffsserver im Internet veröffentlichen. Hierzu ist eingehender HTTPS-Zugriff aus dem Internet auf den Clientzugriffsserver erforderlich. Clientzugriffsserver an Active Directory-Standorten, die nicht über einen im Internet veröffentlichten Clientzugriffsserver verfügen, können Clientzugriffsserver an anderen Active Directory-Standorten verwenden, auf die über das Internet zugegriffen werden kann. Für nicht im Internet veröffentlichte Clientzugriffsserver muss die externe URL des virtuellen Verzeichnisses der Webdienste auf die URL festgelegt sein, die für externe Organisationen sichtbar ist.

Zurück zum Seitenanfang

## Koexistenz mit Exchange 2010

In Organisationen, die sowohl Exchange 2010- als auch Exchange 2013-Server enthalten, können Benutzer mit Postfächern auf einem Exchange 2010-Postfachserver mithilfe von Organisationsbeziehungen Frei/Gebucht-Informationen für Empfänger in externen Exchange 2013-Verbunddomänenorganisationen freigeben. Auf den Exchange 2010-Clientzugriffsservern und -Postfachservern muss SP2 oder höher ausgeführt werden, und in der Exchange 2010-Organisation muss mindestens ein Exchange 2013-Clientzugriffsserver vorhanden sein.

## Koexistenz mit Exchange 2007

In Organisationen, die sowohl Exchange 2013- als auch Exchange 2007-Server enthalten, können die Benutzer, die ein Postfach auf einem Exchange 2007-Postfachserver haben, mithilfe von Organisationsbeziehungen Frei/Gebucht-Informationen für Empfänger in externen Verbunddomänenorganisationen freigeben. Auf dem Postfachserver muss Exchange 2007 SP2 oder höher ausgeführt werden, und es muss in der Exchange-Organisation mindestens einen Exchange 2013-Clientzugriffsserver geben. Durch die Einführung eines einzigen Exchange 2013-Clientzugriffsservers in der Organisation können Sie Organisationsbeziehungen nutzen, die viel robuster sind als Lösungen, bei denen Frei/Gebucht-Informationen und die globale Adressliste (GAL) synchronisiert werden müssen.

Zur Planung einer Besprechung mit Outlook 2010 oder Outlook Web App auf einem Exchange 2007-Server kann ein Benutzer, der ein Postfach auf einem Exchange 2007-Server hat, die Frei/Gebucht-Informationen eines Benutzers in der externen Organisation anzeigen. Frei/Gebucht-Informationen für Exchange 2007-Postfächer werden Empfängern in der externen Organisation angezeigt.

Freigaberichtlinien sind Exchange 2013-Postfachbenutzern zugewiesen. Zur Verwendung von Freigaberichtlinien muss sich ein Postfach auf einem Exchange 2013-Postfachserver befinden. Zum Generieren von oder zum Antworten auf Einladungen zur Freigabe können nur Outlook 2010- und Outlook Web App-Clients verwendet werden.

Zurück zum Seitenanfang

## Dokumentation zur Freigabe

In der folgenden Tabelle sind Links zu Themen aufgeführt, in denen Sie weitere Informationen zur Freigabe in Exchange 2013 sowie zur Verwaltung dieser Funktionen finden.


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
<td><p><a href="federation-exchange-2013-help.md">Verbund</a></p></td>
<td><p>Erfahren Sie mehr über die zugrunde liegende Vertrauensstellungsinfrastruktur, die Freigaben unterstützt, eine einfache Methode zur gemeinsamen Kalendernutzung mit externen Empfängern.</p></td>
</tr>
<tr class="even">
<td><p><a href="organization-relationships-exchange-2013-help.md">Organisationsbeziehungen</a></p></td>
<td><p>Erfahren Sie mehr über 1:1-Beziehungen zwischen Exchange-Organisationen, die eine Freigabe von Frei/Gebucht-Informationen ermöglichen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="sharing-policies-exchange-2013-help.md">Freigaberichtlinien</a></p></td>
<td><p>Erfahren Sie mehr über Richtlinien zur Freigabe zwischen Personen.</p>
<p></p></td>
</tr>
</tbody>
</table>


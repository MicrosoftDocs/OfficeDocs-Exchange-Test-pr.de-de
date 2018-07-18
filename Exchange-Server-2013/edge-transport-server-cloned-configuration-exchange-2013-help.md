---
title: 'Geklonte Edge-Transport-Server-Konfiguration: Exchange 2013 Help'
TOCTitle: Geklonte Edge-Transport-Server-Konfiguration
ms:assetid: 683a6b8a-59bf-43ed-96c8-504945c2f665
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998622(v=EXCHG.150)
ms:contentKeyID: 61180469
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Geklonte Edge-Transport-Server-Konfiguration

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Edge-Transport-Servers speichern ihre Konfigurationsinformationen in Active Directory Lightweight Directory Services (AD LDS). Sie können mehrere Edge-Transport-Server im Umkreisnetzwerk installieren und Roundrobin-DNS verwenden, um einen Lastenausgleich des Netzwerkverkehrs unter allen Edge-Transport-Servern durchzuführen. Roundrobin ist ein einfacher Mechanismus, der von DNS-Servern verwendet wird, um Lasten für Netzwerkressourcen freizugeben und zu verteilen.

Um sicherzustellen, dass alle bereitgestellten Edge-Transport-Server dieselben Konfigurationsinformationen verwenden, verwenden Sie die bereitgestellten Skripts zum Klonen der Konfiguration, um die Konfiguration eines Quellservers auf einen Zielserver zu duplizieren.

Die *geklonte Konfiguration* wird verwendet, um neue Edge-Transport-Server basierend auf einem konfigurierten Quellserver bereitzustellen. Die Konfigurationsinformationen des Quellservers werden dupliziert und dann in eine XML-Datei exportiert. Die XML-Datei wird anschließend auf den Zielserver importiert.

Dieses Thema bietet eine Übersicht des geklonten Konfigurationsprozesses. Genaue Anweisungen zum Konfigurieren Ihrer Edge-Transport-Server mithilfe der geklonten Konfiguration finden Sie unter [Konfigurieren der Edge-Transport-Server mithilfe geklonter Konfiguration](configure-edge-transport-server-using-cloned-configuration-exchange-2013-help.md).

**Inhalt**

Geklonte Konfiguration und EdgeSync

Geklonter Konfigurationsprozess

Transportkonfigurationsinformationen

## Geklonte Konfiguration und EdgeSync

Führen Sie den EdgeSync-Prozess aus, nachdem Sie die geklonte Konfiguration importiert haben. Zum Ausführen von Empfänger-Lookup- und Nachrichtensicherheitsaufgaben benötigt der Edge-Transport-Server Daten, die in Active Directory gespeichert sind. *EdgeSync* ist eine Sammlung von Prozessen, die auf einem Exchange 2013-Postfachserver ausgeführt werden, um eine unidirektionale Replikation von Empfänger- und Konfigurationsinformationen aus Active Directory in die AD LDS-Instanz auf einem Edge-Transport-Server einzurichten. EdgeSync kopiert nur die Informationen, die der Edge-Transport-Server zum Durchführen von Antispam-Aufgaben benötigt, sowie die Informationen zur Connectorkonfiguration, die zum Aktivieren der End-to-End-Nachrichtenübermittlung erforderlich sind. EdgeSync führt geplante Updates aus, damit die Informationen in AD LDS aktuell bleiben.

Bei der geklonten Konfiguration werden die Edge-Abonnementeinstellungen eines Servers nicht dupliziert. Die von EdgeSync verwendeten Zertifikate werden nicht geklont. Sie müssen den EdgeSync-Vorgang separat für jeden Edge-Transport-Server durchführen. EdgeSync überschreibt alle Einstellungen, die sowohl in den geklonten Konfigurationsinformationen als auch in den EdgeSync-Replikationsinformationen enthalten sind. Zu diesen Einstellungen zählen Sendeconnectors, Empfangsconnectors, akzeptierte Domänen und Remotedomänen.

## Geklonter Konfigurationsprozess

Das Verfahren zum Klonen der Konfiguration untergliedert sich in drei Schritte:

1.  Exportieren der Konfiguration vom Quellserver.
    
    Ausführen des Skripts "ExportEdgeConfig.ps1" (aus dem Verzeichnis "%ExchangeInstallPath%Scripts"), um die Konfigurationsinformationen des Quellservers in eine XML-Zwischendatei zu exportieren.

2.  Überprüfen der Konfiguration des Zielservers.
    
    Ausführen des Skripts "ImportEdgeConfig.ps1" (aus dem Verzeichnis "%ExchangeInstallPath%Scripts"). Dieses Skript überprüft die in der XML-Datei vorhandenen Informationen, um sicherzustellen, dass die exportierten Einstellungen für den Zielserver gültig sind, und erstellt dann eine Antwortdatei. Die Antwortdatei enthält serverspezifische Informationen, die beim Importieren der Konfiguration auf den Zielserver verwendet werden. Die Antwortdatei enthält Einträge für jede Quellservereinstellung, die für den Zielserver nicht gültig ist. Sie können diese Einstellungen so ändern, dass sie für den Zielserver gültig sind. Wenn alle Einstellungen gültig sind, enthält die Antwortdatei keine Einträge.

3.  Importieren der Konfiguration auf den Zielserver.
    
    Im Skript "ImportEdgeConfig.ps1" werden die XML-Zwischendatei und die Antwortdatei verwendet, um eine vorhandene Konfiguration zu klonen oder eine bestimmte Konfiguration des Servers wiederherzustellen.

## Schritt 1: Exportieren der Konfiguration vom Quellserver

Führen Sie nach dem Installieren und Konfigurieren der Edge-Transport-Serverrolle das Skript "ExportEdgeConfig.ps1" (aus dem Verzeichnis "%ExchangeInsallPath%Scripts") aus. Dieses Skript ruft die Konfigurationsinformationen des Quellservers ab und speichert sie in einer XML-Zwischendatei.

Die folgenden Informationen werden vom Quellserver exportiert und in der XML-Zwischendatei gespeichert:

  - Transportserverbezogene Informationen und Informationen zum Protokolldateipfad:
    
      - *ReceiveProtocolLogPath*
    
      - *SendProtocolLogPath*
    
      - *MessageTrackingLogPath*
    
      - *PickupDirectoryPath*
    
      - *RoutingTableLogPath*

  - Transport-Agent-bezogene Informationen, zu denen Status- und Prioritätseinstellungen jedes Transport-Agents gehören.

  - Alle sendeconnectorbezogenen Informationen. Wenn Sendeconnectors für die Verwendung von Anmeldeinformationen konfiguriert sind, wird das Kennwort als verschlüsselte Zeichenfolge in die XML-Zwischendatei geschrieben. Sie können den Parameter *-key* zusammen mit den Skripts "ImportEdgeConfig.ps1" und "ExportEdgeConfig.ps1" zum Angeben der 32 Byte langen Zeichenfolge verwenden, die zur Kennwortverschlüsselung und -entschlüsselung verwendet werden soll. Wenn der Parameter *-key* nicht verwendet wird, wird ein Standardverschlüsselungsschlüssel verwendet.

  - Alle empfangsconnectorbezogenen Informationen. Zum Ändern der lokalen Netzwerkbindung und der Porteigenschaften müssen Sie die Konfigurationsinformationen in der Antwortdatei ändern, die während der Konfigurationsüberprüfung erstellt wird.

  - Konfiguration der akzeptierten Domänen

  - Remotedomänenkonfiguration

  - Konfigurationseinstellungen der Antispamfunktionen:
    
      - Informationen der IP-Zulassungsliste Nur die vom Administrator manuell konfigurierten Einträge der IP-Zulassungsliste werden exportiert.
    
      - Informationen der IP-Sperrliste
    
      - Inhaltsfilterkonfiguration
    
      - Empfängerfilterkonfiguration
    
      - Einträge zum Umschreiben von Adressen
    
      - Anlagenfiltereinträge

Zurück zum Seitenanfang

## Schritt 2: Überprüfen der Konfiguration des Zielservers

Der Zielserver ist ein Exchange 2013-Server mit einer Neuinstallation der Edge-Transport-Serverrolle. Führen Sie zuerst das Skript "ImportEdgeConfig.ps1" (aus dem Verzeichnis "%ExchangeInsallPath%Scripts") auf dem Zielserver aus, um die in der XML-Zwischendatei vorhandenen Informationen zu überprüfen und die Antwortdatei zu erstellen. Die Antwortdatei enthält serverspezifische Informationen, die beim Importieren der Konfiguration auf den Zielserver verwendet werden. Die Antwortdatei enthält Einträge für jede Quellservereinstellung, die für den Zielserver nicht gültig ist. Sie müssen diese Einstellungen so ändern, dass sie für den Zielserver gültig sind. Wenn alle Einstellungen gültig sind, enthält die Antwortdatei keine Einträge. Die XML-Zwischendatei kann für unterschiedliche Zielserver verwendet werden. Die Antwortdatei gilt speziell für einen bestimmten Zielserver.

Das Skript "ImportEdgeConfig.ps1" (aus dem Verzeichnis "%ExchangeInsallPath%Scripts") führt die folgenden Aufgaben aus:

  - Überprüfen, ob die Daten- und Protokollpfade auf dem Server erstellt werden können. Wenn die Pfade nicht erstellt werden können, wird ein leerer Pfad in die Antwortdatei eingefügt.

  - Für jeden Sendeconnector in der XML-Datei fügt das Skript einen leeren Eintrag für die IP-Quelladresse in die Antwortdatei ein.

  - Für jeden Empfangsconnector in der XML-Datei fügt das Skript einen leeren Eintrag für die lokalen Netzwerkbindungen in die Antwortdatei ein.

Sie müssen die Antwortdatei manuell bearbeiten und die folgenden Informationen für serverspezifische Einstellungen angeben:

  - Füllen Sie die Daten- und Protokollpfade aus. Werden diese Pfade in der Antwortdatei leer gelassen, werden im nächsten Schritt beim Importieren der Konfiguration auf den Zielserver die in der XML-Zwischendatei konfigurierten Pfade verwendet.

  - Geben Sie für jeden Sendeconnectoreintrag die IP-Quelladresse an. Wenn Sie dieses Feld leer lassen, tritt beim Import der Konfiguration ein Fehler auf.

  - Geben Sie für jeden Empfangsconnectoreintrag die lokalen Netzwerkbindungen an. Wenn Sie keine lokalen Netzwerkbindungen angeben, tritt beim Import der Konfiguration auf dem Zielserver ein Fehler auf.

Zurück zum Seitenanfang

## Schritt 3: Importieren der Konfiguration auf dem Zielserver

Sie können diesen Schritt auf jedem Zielserver ausführen, um die Konfiguration eines vorhandenen Edge-Transport-Servers zu klonen oder eine bestimmte Konfiguration für den Server wiederherzustellen. Führen Sie das Skript "ImportEdgeConfig.ps1" (aus dem Verzeichnis "%ExchangeInsallPath%Scripts) aus, um die neue Konfiguration zu überprüfen und zu importieren. Nachdem Sie das Skript ausgeführt haben, entspricht die Konfiguration des Zielservers den Einstellungen in der XML-Zwischendatei und der Antwortdatei.


> [!IMPORTANT]
> Es wird empfohlen, die vorhandene Serverkonfiguration zu sichern, bevor Sie die Konfiguration importieren. Auf diese Weise können Sie bei einem Scheitern des Klonvorgangs den bisherigen stabilen Zustand des Servers wiederherstellen.



In diesem Schritt werden die in der Antwortdatei enthaltenen serverspezifischen Informationen verwendet. Wenn in der Antwortdatei keine Einstellung angegeben wird, werden die Daten aus der XML-Zwischendatei verwendet. Bevor das Skript die Konfiguration ändert, werden die Daten in der XML-Zwischendatei und der Antwortdatei überprüft.

Die folgenden Konfigurationseinstellungen des Zielservers werden durch den Konfigurationsimport geändert:

  - Die Transport-Agent-Konfiguration wird geändert.

  - Die auf dem Zielserver vorhandenen Connectors werden entfernt, und die Connectors aus der XML-Zwischendatei werden hinzugefügt.

  - Die vorhandenen akzeptierten Domänen werden entfernt, und die Einträge der akzeptierten Domänen aus der XML-Zwischendatei werden hinzugefügt.

  - Die vorhandenen Remotedomänen werden entfernt, und die Remotedomäneneinträge aus der XML-Zwischendatei werden hinzugefügt.

  - Die vorhandenen Einträge der IP-Zulassungsliste werden entfernt, und die Einträge der IP-Zulassungsliste aus der Remotedomänen-Zwischendatei werden hinzugefügt.

  - Die vorhandenen Einträge der IP-Sperrliste werden entfernt, und die Einträge der IP-Sperrliste aus der Remotedomänen-Zwischendatei werden hinzugefügt.

  - Die folgende Antispamkonfiguration wird auf den Zielserver geklont:
    
      - Inhaltsfilterkonfiguration
    
      - Empfängerfilterkonfiguration
    
      - Einträge zum Umschreiben von Adressen
    
      - Anlagenfiltereinträge

Zurück zum Seitenanfang

## Transportkonfigurationsinformationen

Die Einstellungen des Transportkonfigurationsobjekts definieren die serverweiten E-Mail-Transporteinstellungen für einen Edge-Transport-Server. Wenn Sie die XML-Zwischendatei auf den Zielserver importieren, werden alle Einstellungen des Transportkonfigurationsobjekts importiert außer den Folgenden:

  - Allgemeine Namen und Erstellungsdatumsangaben aus der exportierten XML-Datei

  - Sendeconnectorinformationen

  - Empfangsconnectorinformationen

  - Anlagenfiltereinträge

  - Der Attributeintrag **MaxDumpsterSizePerStorageGroup**

Nach Abschluss des Importvorgangs können Sie die Einstellungen auch mithilfe des Cmdlets **Set-TransportConfig** konfigurieren. Weitere Informationen finden Sie unter [Set-TransportConfig](https://technet.microsoft.com/de-de/library/bb124151\(v=exchg.150\)).

Die folgende Tabelle enthält die Attribute, die dem Transportkonfigurationsobjekt zugeordnet sind, sowie deren Standardwerte. Sie können dieses Objekt sowohl auf Postfachservern als auch auf Edge-Transport-Servern konfigurieren. Viele Attribute gelten allerdings nur für den Transportdienst auf Exchange 2013-Postfachservern. Das Konfigurieren dieser Attribute auf einem Edge-Transport-Server hat keinerlei Auswirkungen.

### Transportkonfigurationsattribute und Standardwerte

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Beschreibung</th>
<th>Standardwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ClearCategories</strong></p></td>
<td><p>Dieses Attribut gibt an, ob Microsoft Outlook-Kategorien während der Inhaltskonvertierung gelöscht werden sollen.</p></td>
<td><p>True</p></td>
</tr>
<tr class="even">
<td><p><strong>GenerateCopyOfDSNFor</strong></p></td>
<td><p>Dieses Attribut gibt die DSN-Codes (Delivery Status Notification, Benachrichtigung über den Zustellungsstatus) an, die bewirken, dass die DSN-Nachricht kopiert und an die E-Mail-Adresse des Postmasters gesendet wird. DSN-Codes werden im Format <em>x.y.z</em> eingegeben und durch Kommas getrennt.</p></td>
<td><p>5.4.8, 5.4.6, 5.4.4, 5.2.4, 5.2.0, 5.1.4</p></td>
</tr>
<tr class="odd">
<td><p><strong>InternalSMTPServers</strong></p></td>
<td><p>Dieses Attribut gibt eine Liste von internen SMTP-Server-IP-Adressen oder -IP-Adressbereichen an, die von der Sender ID- und der Verbindungsfilterung ignoriert werden sollen.</p></td>
<td><p>Null</p></td>
</tr>
<tr class="even">
<td><p><strong>JournalingReportNdrTo</strong></p></td>
<td><p>Dieses Attribut gibt die E-Mail-Adresse an, an die Journalberichte gesendet werden, wenn das Journalpostfach nicht verfügbar ist. Dieses Attribut gilt nicht für die Konfiguration eines Edge-Transport-Servers.</p></td>
<td><p>Null</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxDumpsterSizePerStorageGroup</strong></p></td>
<td><p>Dieses Attribut gibt die maximale Größe des Transportdumpsters auf einem Postfachserver an. Dieses Attribut gilt nicht für die Konfiguration eines Edge-Transport-Servers.</p></td>
<td><p>18 MB</p></td>
</tr>
<tr class="even">
<td><p><strong>MaxDumpsterTime</strong></p></td>
<td><p>Dieses Attribut gibt an, wie lange eine E-Mail-Nachricht im Transportdumpster auf einem Postfachserver bleiben soll. Dieses Attribut gilt nicht für die Konfiguration eines Edge-Transport-Servers.</p></td>
<td><p>7.00:00:00</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxReceiveSize</strong></p></td>
<td><p>Dieses Attribut gibt die maximale Größe von Nachrichten an, die von Empfängern in der Organisation empfangen werden dürfen. Dieses Attribut gilt nicht für die Konfiguration eines Edge-Transport-Servers.</p></td>
<td><p>10 MB</p></td>
</tr>
<tr class="even">
<td><p><strong>MaxRecipientEnvelopeLimit</strong></p></td>
<td><p>Dieses Attribut gibt die maximale Anzahl von Empfängern an, die in eine E-Mail-Nachricht aufgenommen werden dürfen. Dieses Attribut gilt nicht für die Konfiguration eines Edge-Transport-Servers.</p></td>
<td><p>5,000</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxSendSize</strong></p></td>
<td><p>Dieses Attribut gibt die maximale Größe von Nachrichten an, die von Empfängern in der Organisation gesendet werden dürfen. Dieses Attribut gilt nicht für die Konfiguration eines Edge-Transport-Servers.</p></td>
<td><p>10 MB</p></td>
</tr>
<tr class="even">
<td><p><strong>TLSReceiveDomainSecureList</strong></p></td>
<td><p>Dieses Attribut gibt die Remotedomänen an, die MTLS-Authentifizierung (Mutual Transport Layer Security) durch Empfangsconnectors verwenden, die für die Unterstützung von Domänensicherheit konfiguriert wurden. Mehrere Domänen können durch Komma getrennt werden. Das Platzhalterzeichen (*) wird in den Domänen, die in diesem Attribut aufgelistet werden, nicht unterstützt.</p></td>
<td><p>Null</p></td>
</tr>
<tr class="odd">
<td><p><strong>TLSSendDomainSecureList</strong></p></td>
<td><p>Dieses Attribut gibt die Remotedomänen an, die MTLS-Authentifizierung (Mutual Transport Layer Security) verwenden, wenn E-Mail-Nachrichten durch einen Sendeconnector gesendet werden, der für die Unterstützung von Domänensicherheit und den Adressraum der Zieldomäne konfiguriert wurde. Mehrere Domänen können durch Komma getrennt werden. Das Platzhalterzeichen (*) wird in den Domänen, die in diesem Attribut aufgelistet werden, nicht unterstützt.</p></td>
<td><p>Null</p></td>
</tr>
<tr class="even">
<td><p><strong>VerifySecureSubmitEnabled</strong></p></td>
<td><p>Dieses Attribut überprüft, ob E-Mail-Clients, die Nachrichten von Postfächern auf Postfachservern übermitteln, die verschlüsselte MAPI-Übermittlung verwenden. Dieses Attribut gilt nicht für die Konfiguration eines Edge-Transport-Servers. Gültige Werte für dieses Attribut sind <code>$true</code> und <code>$false</code>.</p></td>
<td><p>False</p></td>
</tr>
<tr class="odd">
<td><p><strong>VoicemailJournalingEnabled</strong></p></td>
<td><p>Dieses Attribut gibt an, ob UM-Voicemailnachrichten (Unified Messaging) vom Journal-Agent erfasst werden. Dieses Attribut gilt nicht für die Konfiguration eines Edge-Transport-Servers.</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Wenn der Edge-Transport-Server später für die Exchange-Organisation abonniert wird, wird der Wert des Attributs <STRONG>InternalSMTPServers</STRONG> während des EdgeSync-Prozesses überschrieben. Weitere Informationen finden Sie unter <A href="edge-subscriptions-exchange-2013-help.md">Edge-Abonnements</A>.



Zurück zum Seitenanfang


---
title: 'Planen von Edge-Transport-Servern: Exchange 2013 Help'
TOCTitle: Planen von Edge-Transport-Servern
ms:assetid: 3d34de82-58a5-4b30-9978-7d330102eb92
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn641596(v=EXCHG.150)
ms:contentKeyID: 61543914
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Planen von Edge-Transport-Servern

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Die Edge-Transport-Serverrolle wurde in Exchange Service Pack 1 wieder eingeführt. Der Edge-Transport-Server bietet für die Exchange-Organisation einen verbesserten Schutz gegen Spam. Der Edge-Transport-Server wendet außerdem Richtlinien auf Nachrichten an, die sich im Transport zwischen Organisationen befinden. Diese Serverrolle wird im Umkreisnetzwerk und außerhalb der Active Directory-Gesamtstruktur bereitgestellt. Im Gegensatz zu Clientzugriffs- oder Postfachservern können Edge-Transport-Server nicht direkt auf Konfigurations- und Empfängerinformationen in Active Directory zugreifen. Der Edge-Transport-Server verwendet AD LDS (Active Directory Lightweight Directory Service) zum lokalen Speichern von Konfigurations- und Empfängerinformationen.

Sie können einen Edge-Transport-Server einer vorhandenen Exchange 2013-Organisation hinzufügen. Sie müssen keine weiteren Schritte zur Vorbereitung von Active Directory ausführen, wenn der Edge-Transport-Server installiert wird.


> [!NOTE]
> Wenn Sie den Edge-Transport-Server einer vorhandenen Exchange 2010- oder Exchange 2007-Organisation hinzufügen, müssen Sie vor der Installation des Exchange 2013-Edge-Transport-Servers auf Ihren Legacyservern bestimmte Rollupupdates installieren. Weitere Informationen finden Sie unter <A href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange&nbsp;2013 – Systemanforderungen</A>.



Wenn Sie die Bereitstellung von Edge-Transport-Servern planen, sollten Sie folgende Aspekte beachten:

  - **Serverkapazität**   Zur Planung der Serverkapazität gehört die Planung der Leistungsüberwachung des Edge-Transport-Servers. Der Leistungsüberwachung können Sie entnehmen, wie intensiv der Server beansprucht wird. Diese Informationen ermöglichen Rückschlüsse auf die Kapazität der aktuellen Hardwarekonfiguration.

  - **Transportfunktionen**   Der Edge-Transport-Server kann Antispamschutz für die Peripherie des Netzwerks bereitstellen. Als Teil des Planungsprozesses sollten Sie die Antispamfunktionen festlegen, die auf dem Edge-Transport-Server aktiviert werden sollen, und planen, wie diese Funktionen konfiguriert werden sollen.

  - **Sicherheit**   Die Edge-Transport-Serverrolle wurde so entwickelt, dass sie nur eine minimale Angriffsfläche bietet. Daher ist es wichtig, sowohl den physischen Zugriff als auch den Netzwerkzugriff auf den Server ordnungsgemäß zu sichern und zu verwalten. Die Planung der Sicherheit trägt zur Gewährleistung bei, dass IP-Verbindungen nur von autorisierten Servern und autorisierten Benutzern aktiviert werden können. Weitere Informationen finden Sie unter [Prüfliste für Bereitstellungssicherheit](deployment-security-checklist-exchange-2013-help.md).
    
    Die empfohlene Methode besteht darin, den Edge-Transport-Server in ein Umkreisnetzwerk einzubinden. Sie müssen die Kommunikation über die in der folgenden Tabelle aufgeführten Ports zulassen, um sicherzustellen, dass der Server E-Mails senden und empfangen kann sowie Updates von Empfänger- und Konfigurationsdaten vom MicrosoftExchange-EdgeSync-Dienst empfangen kann.
    
    ### Konfigurationsporteinstellungen für Edge-Transport-Server
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Netzwerkschnittstelle</th>
    <th>Offener Port</th>
    <th>Protokoll</th>
    <th>Hinweis</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Eingehend aus dem Internet und ausgehend in das Internet</p></td>
    <td><p>25/TCP</p></td>
    <td><p>SMTP</p></td>
    <td><p>Dieser Port muss für die Nachrichtenübermittlung in das und aus dem Internet geöffnet sein.</p></td>
    </tr>
    <tr class="even">
    <td><p>Eingehend aus dem internen Netzwerk und ausgehend in das interne Netzwerk</p></td>
    <td><p>25/TCP</p></td>
    <td><p>SMTP</p></td>
    <td><p>Dieser Port muss für die Nachrichtenübermittlung in die und aus der Exchange-Organisation geöffnet sein.</p></td>
    </tr>
    <tr class="odd">
    <td><p>Nur lokal</p></td>
    <td><p>50389/TCP</p></td>
    <td><p>LDAP</p></td>
    <td><p>Mit diesem Port wird eine lokale Verbindung zu AD LDS hergestellt.</p></td>
    </tr>
    <tr class="even">
    <td><p>Eingehend aus dem internen Netzwerk</p></td>
    <td><p>50636/TCP</p></td>
    <td><p>Sicheres LDAP</p></td>
    <td><p>Dieser Port ist für die EdgeSync-Synchronisierung erforderlich.</p></td>
    </tr>
    <tr class="odd">
    <td><p>Eingehend aus dem internen Netzwerk</p></td>
    <td><p>3389/TCP</p></td>
    <td><p>RDP</p></td>
    <td><p>Das Öffnen dieses Ports ist optional. Er gestaltet die Verwaltung der Edge-Transport-Server von innerhalb des internen Netzwerks aus flexibler, indem er zu diesem Zweck die Verwendung einer Remotedesktopverbindung ermöglicht.</p></td>
    </tr>
    </tbody>
    </table>
    

    > [!NOTE]
    > Die Edge-Transport-Serverrolle verwendet nicht standardmäßige LDAP-Ports. Die in diesem Thema angegebenen Ports sind die LDAP-Kommunikationsports, die beim Installieren der Edge-Transport-Serverrolle konfiguriert werden.



  - **EdgeSync**   Der empfohlene Bereitstellungsprozess sieht das Erstellen eines Edge-Abonnements vor, um den Edge-Transport-Server für die Exchange-Organisation zu abonnieren. Beim Erstellen eines Edge-Abonnements werden Empfänger- und Konfigurationsdaten von Active Directory in AD LDS repliziert. Sie abonnieren einen Edge-Transport-Server für einen Active Directory-Standort. Anschließend aktualisiert der MicrosoftExchange-Dienst EdgeSync, der auf den Postfachservern an diesem Standort ausgeführt wird, regelmäßig AD LDS, indem Daten von Active Directory synchronisiert werden. Beim Edge-Abonnementprozess werden automatisch die Sendeconnectors bereitgestellt, die erforderlich sind, um die Nachrichtenübermittlung von der Exchange-Organisation über einen Edge-Transport-Server in das Internet zu ermöglichen. Wenn Sie auf dem Edge-Transport-Server die Funktionen der Empfängersuche oder der Aggregation von Listen sicherer Adressen verwenden, muss der Edge-Transport-Server für die Organisation abonniert werden.

## Konfigurieren von DNS-Einstellungen für die Edge-Transport-Serverrolle

Der Edge-Transport-Server wird außerhalb der Exchange-Organisation als ein eigenständiger Server im Umkreisnetzwerk oder als Mitglied einer Active Directory-Domäne im Umkreisnetzwerk bereitgestellt. Sie müssen das korrekte DNS-Suffix für die Edge-Transport-Serverrolle manuell konfigurieren, bevor Sie Exchange 2013 installieren. Wenn das DNS-Suffix nicht konfiguriert wurde, kann das Setup nicht durchgeführt werden.

Da der Edge-Transport-Server im Umkreisnetzwerk bereitgestellt wird, sind die zugehörigen Netzwerkschnittstellen mit mehreren Netzwerksegmenten verbunden. Jedes dieser Netzwerksegmente verfügt über eine eindeutige IP-Konfiguration. Die Netzwerkschnittstelle, die mit dem externen oder öffentlichen Netzwerksegment verbunden ist, sollte so konfiguriert sein, dass sie einen öffentlichen DNS-Server für die Namensauflösung verwendet. Auf diese Weise kann der Server SMTP-Domänennamen in MX-Ressourceneinträge auflösen und Nachrichten an das Internet routen.

Die mit dem internen, oder privaten, Netzwerksegment verbundene Netzwerkschnittstelle sollte so konfiguriert sein, dass sie einen DNS-Server verwendet, der die Namen der Postfachserver in Ihrer Organisation auflösen kann. Alternativ dazu sollte sie über eine Hosts-Datei verfügen. Die Edge-Transport- und Postfachserver müssen in der Lage sein, sich gegenseitig mithilfe der DNS-Hostauflösung zu finden.

Zum Aktivieren der Namensauflösung von Postfachservern durch Edge-Transport-Server verwenden Sie eine der folgenden Methoden:

  - Erstellen Sie manuell Ressourceneinträge für Postfachserver in einer Forward-Lookupzone auf dem DNS-Server, der auf der internen Netzwerkkarte des Edge-Transport-Servers konfiguriert ist.

  - Bearbeiten Sie die Hosts-Datei auf dem Edge-Transport-Server so, dass sie die Hosteinträge für die Postfachserver enthält. Die Hosts-Datei ist eine lokale Textdatei im selben Format wie die 4.3 BSD UNIX-Datei **/etc/hosts** (Berkeley Software Distribution). In dieser Datei werden Hostnamen IP-Adressen zugeordnet, und sie wird im Ordner **\\%Systemroot%\\System32\\Drivers\\Etc** gespeichert.

Zum Aktivieren der Namensauflösung von Edge-Transport-Servern durch Postfachserver verwenden Sie eine der folgenden Methoden:

  - Erstellen Sie manuell Ressourceneinträge für Edge-Transport-Server in einer Forward-Lookupzone auf dem DNS-Server, der auf dem Postfachserver konfiguriert ist.

  - Zum Hinzufügen der Hosteinträge für die Edge-Transport-Server bearbeiten Sie die Hosts-Datei auf den Postfachservern, die sich an den abonnierten Active Directory-Standorten befinden.

Führen Sie die folgenden Schritte aus, um die DNS-Einstellungen für den Edge-Transport-Server zu konfigurieren:

1.  Stellen Sie sicher, dass die DNS-Servereinstellungen der einzelnen Netzwerkschnittstellen für das Netzwerksegment korrekt sind.

2.  Gehen Sie folgendermaßen vor, um das DNS-Suffix für den Edge-Transport-Servernamen zu konfigurieren:
    
    1.  Öffnen Sie die Systemsteuerung, und wählen Sie **Systemeigenschaften**.
    
    2.  Klicken Sie auf die Registerkarte **Computername**.
    
    3.  Klicken Sie auf **Ändern**.
    
    4.  Klicken Sie auf der Seite **Computernamen ändern** auf **Weitere**.
    
    5.  Geben Sie im Feld **Primäres DNS-Suffix des Computers:** einen DNS-Domänennamen und ein -Suffix für den Edge-Transport-Server ein.
    
    Dieser Name kann nach der Installation der Edge-Transport-Serverrolle nicht mehr geändert werden.

## Außerkraftsetzen von DNS-Einstellungen

Sie müssen ggf. die standardmäßigen DNS-Einstellungen auf dem Exchange-Server so außer Kraft setzen, dass E-Mail ordnungsgemäß weitergeleitet und zugestellt werden kann. Dazu ändern Sie die Einstellungen **Interne DNS-Lookups** und **Externe DNS-Lookups** in den Eigenschaften des Transportservers. Diese Einstellungen setzen die Einstellungen der Netzwerkkarte zum Weiterleiten von E-Mail-Nachrichten außer Kraft.


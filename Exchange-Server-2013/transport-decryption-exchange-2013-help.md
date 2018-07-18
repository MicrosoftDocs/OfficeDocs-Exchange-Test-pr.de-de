---
title: 'Transportentschlüsselung: Exchange 2013 Help'
TOCTitle: Transportentschlüsselung
ms:assetid: 4267c46d-f488-404d-a5cb-51f9127461c0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638122(v=EXCHG.150)
ms:contentKeyID: 50475544
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Transportentschlüsselung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

In Microsoft Exchange Server 2013, Microsoft Outlook 2010 (und höheren Versionen) sowie in Microsoft OfficeOutlook Web App können Benutzer ihre Nachrichten über die Verwaltung von Informationsrechten (Information Rights Management, IRM) schützen. Sie können Outlook-Schutzregeln erstellen, um automatisch den IRM-Schutz auf Nachrichten anzuwenden, bevor sie von einem Outlook 2010-Client gesendet werden. Sie können außerdem Transportschutzregeln erstellen, um IRM-Schutz auf im Transport befindliche Nachrichten anzuwenden, auf die die Regelbedingungen zutreffen. Die Transportentschlüsselung ermöglicht Zugriff auf IRM-geschützte Nachrichten und Inhalte, um Messagingrichtlinien zu erzwingen.

Verwaltungsaufgaben im Zusammenhang mit der Verwaltung von IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Einschränkungen für andere Verschlüsselungslösungen

Wenn Ihre Organisation vertrauliche Informationen schützen muss, einschließlich unternehmenskritischer Informationen (High Business Impact, HBI) und personenbezogener Informationen (Personally Identifiable Information, PII), sollten Sie E-Mail-Nachrichten und Anlagen möglicherweise verschlüsseln. E-Mail-Verschlüsselungslösungen wie S/MIME stehen schon seit langem zur Verfügung. Diese Verschlüsselungslösungen sind in unterschiedlichen Arten von Organisationen unterschiedlich stark im Einsatz. Solche Lösungen bringen jedoch die folgenden Herausforderungen mit sich:

  - **Keine Anwendung von Messagingrichtlinien**   Zu den Anforderungen für die Einhaltung von Vorschriften, die von Organisationen erfüllt werden müssen, zählt u. a. das Einhalten von Messagingrichtlinien in Messaginginhalten. Die Inhalte von Nachrichten, die mit clientbasierten Verschlüsselungslösungen, einschließlich S/MIME, verschlüsselt sind, können jedoch meist nicht auf dem Server untersucht werden. Ohne Inhaltsuntersuchung kann eine Organisation nicht überprüfen, ob alle von den Benutzern gesendeten oder empfangenen Nachrichten die Messagingrichtlinien einhalten. Beispielsweise haben Sie zur Einhaltung einer gesetzlichen Vorschrift eine Transportregel für die Erkennung von personenbezogenen Informationen (z. B. Sozialversicherungsnummern) konfiguriert, die automatisch einen Haftungsausschluss an die Nachricht anhängt. Wenn die Nachricht verschlüsselt ist, kann der Transportregel-Agent im Transportdienst nicht auf den Nachrichteninhalt zugreifen und deshalb den Haftungsausschluss nicht anwenden. Dies führt zu einer Verletzung der Richtlinie.

  - **Geringere Sicherheit**   Antivirensoftware kann verschlüsselte Nachrichteninhalte nicht überprüfen. Dies erhöht für die Organisation das Risiko nicht sicherer Inhalte wie Viren und Würmer. Verschlüsselte Nachrichten werden von den meisten Benutzern als vertrauenswürdig angesehen, sodass die Wahrscheinlichkeit einer Ausbreitung des Virus in der gesamten Organisation deutlich höher ist. Beispielsweise haben Sie eine Outlook-Schutzregel so konfiguriert, dass automatisch der IRM-Schutz auf alle Nachrichten angewendet wird, die mit der RMS-Vorlage (Rights Management Services, Rechteverwaltungsdienste) "Firma (vertraulich)" an die Verteilerliste "Alle Mitarbeiter" gesendet wird. Die Arbeitsstation eines Benutzers ist mit einem Virus infiziert, der sich ausbreitet, indem er automatisch die Option "Allen antworten" verwendet. Wenn die Nachricht, die den Virus enthält, verschlüsselt ist, kann der Antivirusscanner die Nachricht nicht überprüfen.

  - **Auswirkungen auf benutzerdefinierte Transport-Agents**   Viele Organisationen entwickeln benutzerdefinierte Transport-Agents für unterschiedliche Zwecke, z. B. die Einhaltung zusätzlicher Verarbeitungsanforderungen für die Kompatibilität, die Sicherheit oder das benutzerdefinierte Nachrichtenrouting. Benutzerdefinierte Transport-Agents, die von einer Organisation entwickelt wurden, um Nachrichten zu untersuchen oder zu ändern, können keine verschlüsselten Nachrichten verarbeiten. Wenn die von Ihrer Organisation entwickelten benutzerdefinierten Transport-Agents nicht auf Nachrichteninhalte zugreifen können, hindert die Nachrichtenverschlüsselung Ihre Organisation möglicherweise am Erreichen der Ziele, für die die benutzerdefinierten Transport-Agents entwickelt wurden.

## Verwenden der Transportentschlüsselung für verschlüsselte Inhalte

In Exchange 2013 kann diesen Herausforderungen mit IRM-Funktionen begegnet werden. Wenn Nachrichten IRM-geschützt sind, können diese während der Übermittlung über die Transportentschlüsselung entschlüsselt werden. IRM-geschützte Nachrichten werden vom Entschlüsselungs-Agent entschlüsselt, einem auf Richtlinientreue ausgelegten Transport-Agent.


> [!NOTE]
> In Exchange 2013 ist der Entschlüsselungs-Agent ein integrierter Agent. Integrierte Agents sind nicht in der Liste von Agents enthalten, die vom Cmdlet <STRONG>Get-TransportAgent</STRONG> zurückgegeben wird. Weitere Informationen finden Sie unter <A href="transport-agents-exchange-2013-help.md">Transport-Agents</A>.



Der Entschlüsselungs-Agent entschlüsselt die folgenden Arten IRM-geschützter Nachrichten:

  - Vom Benutzer in Outlook Web App IRM-geschützte Nachrichten.

  - Vom Benutzer in Outlook 2010 IRM-geschützte Nachrichten.

  - Automatisch über Outlook-Schutzregeln in Exchange 2013 und Outlook 2010 IRM-geschützte Nachrichten.


> [!IMPORTANT]
> Nur Nachrichten, die durch den AD&nbsp;RMS-Server in Ihrer Organisation IRM-geschützt werden, werden vom Entschlüsselungs-Agent entschlüsselt.




> [!NOTE]
> Nachrichten, die während der Übertragung mit Transportschutzregeln geschützt werden, müssen nicht vom Entschlüsselungs-Agent entschlüsselt werden. Der Entschlüsselungs-Agent wird durch die Transportereignisse <STRONG>OnEndOfData</STRONG> und <STRONG>OnSubmit</STRONG> ausgelöst. Transportschutzregeln werden vom Agent für Transportregeln angewendet, der durch das Ereignis <STRONG>OnRoutedMessage</STRONG> ausgelöst wird, und der IRM-Schutz wird bei Eintreten des Ereignisses <STRONG>OnRoutedMessage</STRONG> vom Entschlüsselungs-Agent angewendet. Weitere Informationen zu Transport-Agents und eine Liste der SMTP-Ereignisse, für die sie registriert werden können, finden Sie unter <A href="transport-agents-exchange-2013-help.md">Transport-Agents</A>.



Die Transportentschlüsselung erfolgt im ersten Exchange 2013-Transportdienst, der eine Nachricht in einer Active Directory-Gesamtstruktur verarbeitet. Wenn eine Nachricht an einen Transportdienst in einer anderen Active Directory-Gesamtstruktur übertragen wird, wird sie erneut entschlüsselt. Nach der Entschlüsselung stehen nicht verschlüsselte Inhalte für andere Transport-Agents auf dem betreffenden Server zur Verfügung. Beispielsweise kann der Transportregel-Agent in einem Transportdienst Nachrichteninhalte untersuchen und Transportregeln anwenden. Alle in der Regel angegebenen Aktionen, z. B. das Anhängen eines Haftungsausschlusses oder jegliche sonstige Veränderung der Nachricht, können für die nicht verschlüsselte Nachricht durchgeführt werden. Transport-Agents von Drittanbietern, z. B. Antivirusscanner, können die Nachricht auf Viren und Schadsoftware überprüfen. Nachdem andere Transport-Agents die Nachricht untersucht und möglicherweise geändert haben, wird sie wieder mit denselben Benutzerrechten verschlüsselt, die sie vor der Entschlüsselung durch den Entschlüsselungs-Agent aufwies. Dieselbe Nachricht wird von einem anderen Transportdienst auf anderen Postfachservern in der Organisation nicht erneut entschlüsselt.

Vom Entschlüsselungs-Agent entschlüsselte Nachrichten verlassen den Transportdienst nicht, ohne erneut verschlüsselt zu werden. Wenn beim Entschlüsseln oder Verschlüsseln der Nachricht ein vorübergehender Fehler auftritt, versucht der Transportdienst zweimal, den Vorgang zu wiederholen. Nach dem dritten Fehlschlagen wird der Fehler als dauerhafter Fehler behandelt. Wenn ein dauerhafter Fehler auftritt – wobei auch vorübergehende Fehler nach zwei Wiederholungsversuchen als dauerhaft betrachtet werden –, geht der Transportdienst so vor:

  - Wenn der dauerhafte Fehler während der Entschlüsselung auftritt, wird ein Unzustellbarkeitsbericht (Non-Delivery Report, NDR) nur dann gesendet, wenn die Transportentschlüsselung auf `Mandatory` festgelegt ist, und die verschlüsselte Nachricht wird zusammen mit dem Unzustellbarkeitsbericht gesendet. Weitere Informationen zu den verfügbaren Konfigurationsoptionen für die Transportentschlüsselung finden Sie unter Konfigurieren der Transportentschlüsselung weiter unten in diesem Thema.

  - Wenn der dauerhafte Fehler während der erneuten Verschlüsselung auftritt, wird immer ein Unzustellbarkeitsbericht ohne die entschlüsselte Nachricht gesendet.


> [!IMPORTANT]
> Alle benutzerdefinierten Agents oder Drittanbieter-Agents, die im Transportdienst installiert sind, haben Zugriff auf die entschlüsselte Nachricht. Sie müssen das Verhalten solcher Transport-Agents berücksichtigen. Wir empfehlen, alle benutzerdefinierten Agents und Drittanbieter-Agents gründlich zu testen, bevor Sie sie in einer Produktionsumgebung bereitstellen.<BR>Wenn nach der Entschlüsselung einer Nachricht durch den Entschlüsselungs-Agent ein Transport-Agent eine neue Nachricht erstellt und die ursprüngliche Nachricht in die neue einbettet (an diese anhängt), wird nur die neue Nachricht geschützt. Die ursprüngliche Nachricht, die zu einer Anlage der neuen Nachricht wird, wird nicht erneut verschlüsselt. Ein Empfänger, der solch eine Nachricht erhält, kann die angehängte Nachricht öffnen und Aktionen ausführen, beispielsweise eine Weiterleitung oder eine Antwort auf die Nachricht, wodurch die Rechteerzwingung umgangen würde.



## Konfigurieren der Transportentschlüsselung

Die Transportentschlüsselung wird in der Exchange-Verwaltungsshell mit dem Cmdlet [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)) konfiguriert. Bevor Sie jedoch die Transportentschlüsselung konfigurieren, müssen Sie Exchange 2013-Servern die Rechte zum Entschlüsseln von Inhalten erteilen, die über Ihren AD RMS-Server geschützt werden. Dies erreichen Sie, indem Sie das Verbundpostfach zu der im AD RMS-Cluster Ihrer Organisation konfigurierten Benutzergruppe mit Administratorrechten hinzufügen.


> [!IMPORTANT]
> In gesamtstrukturübergreifenden AD&nbsp;RMS-Bereitstellungen, in denen in jeder Gesamtstruktur ein AD&nbsp;RMS-Cluster vorhanden ist, müssen Sie das Verbundpostfach der Benutzergruppe mit Administratorrechten auf dem AD&nbsp;RMS-Cluster in jeder Gesamtstruktur hinzufügen, um dem Transportdienst auf einem Exchange 2013-Postfachserver oder einem Exchange 2010-Hub-Transport-Server das Entschlüsseln der geschützten Nachrichten für jeden AD&nbsp;RMS-Cluster zu ermöglichen.



Weitere Informationen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).

Exchange 2013 bietet bei Aktivierung der Transportentschlüsselung zwei unterschiedliche Einstellungen an:

  - **Verbindlich** (Verbindlich)   Wenn die Transportentschlüsselung auf `Mandatory` festgelegt ist, lehnt der Entschlüsselungs-Agent die Nachricht ab und gibt einen Unzustellbarkeitsbericht an den Absender zurück, wenn bei der Entschlüsselung einer Nachricht ein dauerhafter Fehler zurückgegeben wird. Wenn in Ihrer Organisation die Zustellung einer Nachricht nicht gewünscht ist, wenn sie nicht erfolgreich entschlüsselt werden kann und Aktionen wie Antivirusscans und Transportregeln nicht angewendet werden können, müssen Sie diese Einstellung auswählen.

  - **Optional**   Wenn für die Transportverschlüsselung "Optional" festgelegt ist, verwendet der Entschlüsselungs-Agent den "Best-Effort-Ansatz". Nachrichten, die entschlüsselt werden können, werden entschlüsselt; Nachrichten mit einem dauerhaften Fehler bei der Entschlüsselung werden jedoch ebenfalls zugestellt. Wenn in Ihrer Organisation die Nachrichtenzustellung eine höhere Priorität hat als die Einhaltung von Messagingrichtlinien, müssen Sie diese Einstellung verwenden.

Weitere Informationen zum Konfigurieren der Transportentschlüsselung finden Sie unter [Aktivieren oder Deaktivieren der Transportentschlüsselung](enable-or-disable-transport-decryption-exchange-2013-help.md).


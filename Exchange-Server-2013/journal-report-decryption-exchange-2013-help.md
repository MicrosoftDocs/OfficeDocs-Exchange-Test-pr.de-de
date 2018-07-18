---
title: 'Journalberichtentschlüsselung: Exchange 2013 Help'
TOCTitle: Journalberichtentschlüsselung
ms:assetid: c063e2bd-2444-480d-8b35-73f31064a31b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876936(v=EXCHG.150)
ms:contentKeyID: 50476615
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Journalberichtentschlüsselung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-16_

In Microsoft Exchange Server 2013 können Benutzer von Microsoft Outlook 2010 und höher und von Microsoft OfficeOutlook Web App ihre Nachrichten mit der Verwaltung von Informationsrechten (Information Rights Management, IRM) schützen. Sie können Outlook-Schutzregeln erstellen, um Nachrichten automatisch mit IRM-Schutz zu versehen, bevor sie von einem Outlook 2010-Client gesendet werden. Sie können auch Transportschutzregeln erstellen, um Nachrichten, die den Regelbedingungen entsprechen, während der Übertragung mit IRM-Schutz zu versehen.

Informationen zu Outlook-Schutzregeln finden Sie unter [Outlook-Schutzregeln](outlook-protection-rules-exchange-2013-help.md).

## Einschränkungen der Standardverschlüsselungslösungen

Wenn Ihre Organisation Nachrichten mithilfe herkömmlicher Lösungen wie S/MIME verschlüsselt, können Datensatzverwalter verschlüsselte Inhalte weder überprüfen noch durchsuchen. Die Archivierung verschlüsselter Nachrichten mit Inhalten, auf die nicht zugegriffen werden kann bzw. die nicht durchsucht werden können, entspricht ggf. nicht geschäftlichen oder gesetzlichen Vorschriften. Wenn elektronische Beweismittel erforderlich sein sollten, kann die Unfähigkeit, Inhalte in verschlüsselten Nachrichten zu entschlüsseln, zu durchsuchen und vorzulegen, Probleme verursachen, die sich zu rechtlichen und finanziellen Risiken für Ihre Organisation ausweiten können.

Darüber hinaus können die Messagingrichtlinien Ihrer Organisation ggf. anfordern, dass im Journal erfasste Nachrichten so entschlüsselt werden müssen, dass der Zugriff durch Tools für die elektronische Beweissicherung, automatisierte Prozesse oder Datensatzverwalter mit Zugriff auf ein Journalpostfach ermöglicht wird. Die Journalberichtentschlüsselung in Exchange 2010 hilft Ihnen, diese Anforderungen erfüllen.

Weitere Informationen zu Journalen finden Sie unter [Journale](journaling-exchange-2013-help.md).

## Journalberichtentschlüsselung

Mithilfe der Journalberichtentschlüsselung können Sie eine unverschlüsselte Kopie einer mit IRM geschützten Nachricht gemeinsam mit der ursprünglichen mit IRM geschützten Nachricht in Journalberichten speichern. Sofern die mit IRM geschützte Nachricht unterstützte Anlagen enthält, die vom Active Directory-Rechteverwaltungsdienste-Cluster (AD RMS) in Ihrer Organisation geschützt wurden, werden die Anlagen ebenfalls entschlüsselt.


> [!IMPORTANT]
> Zur Verwendung der Journalberichtentschlüsselung müssen Sie über eine Exchange Enterprise-Clientzugriffslizenz (Client Access License, CAL) verfügen. Die Journalberichtentschlüsselung unterstützt nur Premium-Journale.



Die Entschlüsselung erfolgt durch den Journalberichtentschlüsselungs-Agent, einen Transport-Agent mit Schwerpunkt auf Vorschrifteneinhaltung. Der Journalberichtentschlüsselungs-Agent wird beim **OnCategorizedMessage**-Ereignis ausgelöst. Nachrichten, die während der Übertragung durch Transportschutzregeln geschützt werden, wurden bereits vom Verschlüsselungs-Agent verschlüsselt, der beim **OnRoutedMessage**-Ereignis ausgelöst wird, bevor sie den Journalberichtentschlüsselung-Agent erreichen. Der Journalberichtentschlüsselungs-Agent entschlüsselt diese Nachrichten.


> [!NOTE]
> In Exchange 2013 ist der Journalberichtentschlüsselungs-Agent ein integrierter Agent. Integrierte Agents sind nicht in der Liste der Agents enthalten, die vom Cmdlet <STRONG>Get-TransportAgent</STRONG> zurückgegeben wird. Weitere Informationen finden Sie unter <A href="transport-agents-exchange-2013-help.md">Transport-Agents</A>.



Der Agent entschlüsselt die folgenden Arten mit IRM geschützter Nachrichten:

  - Nachrichten, die vom Benutzer in Outlook Web App mit IRM-Schutz versehen wurden.

  - Nachrichten, die vom Benutzer in Outlook 2010 mit IRM-Schutz versehen wurden.

  - Nachrichten, die in Outlook 2010 mithilfe von Outlook-Schutzregeln mit IRM-Schutz versehen wurden.

  - Nachrichten, die während der Übertragung mithilfe von Transportschutzregeln mit IRM-Schutz versehen wurden.


> [!IMPORTANT]
> Nur Nachrichten, die vom Server mit Active Directory-Rechteverwaltungsdienste (AD&nbsp;RMS) in Ihrer Organisation mit IRM-Schutz versehen wurden, werden vom Journalberichtentschlüsselungs-Agent entschlüsselt. Der Agent entschlüsselt eine Anlage nicht, wenn sie nicht zur gleichen Zeit wie die Nachricht geschützt wurde (und demzufolge nicht dieselbe Nutzungslizenz hat) oder wenn eine mit IRM geschützte Datei an eine nicht geschützte Nachricht angehängt ist.



## Konfigurieren der Journalberichtentschlüsselung

Die Journalberichtentschlüsselung wird mithilfe des Cmdlets [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)) in der Exchange-Verwaltungsshell konfiguriert. Bevor Sie die Journalberichtentschlüsselung konfigurieren können, müssen Sie Exchange 2013-Servern die Berechtigungen zum Entschlüsseln von Inhalten gewähren, die von Ihrem AD RMS-Server IRM-geschützt werden. Hierzu fügen Sie das Verbundpostfach der Administratorengruppe hinzu, die im AD RMS-Cluster Ihrer Organisation konfiguriert wurde. Weitere Informationen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).


> [!IMPORTANT]
> In gesamtstrukturübergreifenden AD&nbsp;RMS-Bereitstellungen, bei denen in jeder Gesamtstruktur ein AD&nbsp;RMS-Cluster bereitgestellt wurde, müssen Sie das Verbundpostfach in jeder Gesamtstruktur im AD&nbsp;RMS-Cluster der Gruppe "Administratoren" hinzufügen, damit der Exchange 2013-Transportdienst die Nachrichten entschlüsseln kann, die von jedem AD&nbsp;RMS-Cluster geschützt werden.



Weitere Informationen zum Konfigurieren der Journalberichtentschlüsselung finden Sie unter [Aktivieren oder Deaktivieren von Journalberichtentschlüsselung](enable-or-disable-journal-report-decryption-exchange-2013-help.md).

Nachdem Sie die Journalberichtentschlüsselung aktiviert haben, kann das Journalpostfach unverschlüsselte Journalberichte mit vertraulichen Informationen enthalten. Es wird ausdrücklich empfohlen, den Zugriff auf das Journalpostfach streng zu überwachen und auf autorisierte Personen zu beschränken. Dies ist auch eine empfohlene Vorgehensweise, wenn Sie nicht mit dem IRM-Schutz für E-Mail arbeiten.


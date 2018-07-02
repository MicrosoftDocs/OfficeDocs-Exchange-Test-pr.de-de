---
title: 'Remotedomänen: Exchange 2013 Help'
TOCTitle: Remotedomänen
ms:assetid: 10fb7d62-4d78-40a3-82db-d62bcd27ba42
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996309(v=EXCHG.150)
ms:contentKeyID: 50475110
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Remotedomänen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Sie können Remotedomäneneinträge erstellen, um die Einstellungen für die Nachrichtenübermittlung zwischen der Microsoft Exchange Server 2013-Organisation und Domänen außerhalb Ihrer Exchange-Organisation zu definieren. Durch das Erstellen eines Remotedomäneneintrags steuern Sie die Nachrichtentypen, die an diese Domäne gesendet werden. Sie können zudem auch Nachrichtenformatrichtlinien anwenden und zulässige Zeichensätze für Nachrichten angeben, die von Benutzer Ihrer Organisation an die Remotedomäne gesendet werden. Bei den Einstellungen für Remotedomänen handelt es sich um globale Konfigurationseinstellungen für die Exchange-Organisation.

Die Remotedomäneneinstellungen werden während der Kategorisierung im Transportdienst auf Postfachservern auf die Nachrichten angewendet. Bei der Empfängerauflösung wird die Empfängerdomäne mit den konfigurierten Remotedomänen verglichen. Wenn durch die Konfiguration einer Remotedomäne verhindert wird, dass ein bestimmter Nachrichtentyp an Empfänger in dieser Domäne gesendet werden kann, wird die Nachricht gelöscht. Wenn Sie für die Remotedomäne ein bestimmtes Nachrichtenformat festlegen, werden Nachrichtenkopfzeile und -inhalt geändert. Die Einstellungen gelten für alle Nachrichten, die von der Exchange-Organisation verarbeitet werden.


> [!NOTE]
> Wenn Sie Nachrichteneinstellungen auf Benutzerbasis konfigurieren, wird die Organisationskonfiguration durch diese Einstellungen außer Kraft gesetzt.



Standardmäßig gibt es nur einen einzigen Remotedomäneneintrag. Der Adressraum der Domäne wird als Sternchen (\*) konfiguriert. Das Sternchen steht für alle Remotedomänen. Wenn Sie keine weiteren Remotedomäneneinträge erstellen, gelten für alle Nachrichten, die an alle Empfänger in allen Remotedomänen gesendet werden, die gleichen Einstellungen.

Beim Konfigurieren von Remotedomänen können Sie verhindern, dass bestimmte Nachrichtentypen an diese Domäne übermittelt werden. Zu diesen Nachrichtentypen gehören Abwesenheitsnachrichten, automatische Antwortnachrichten, Unzustellbarkeitsberichte (Non-Delivery Reports, NDRs) und Weiterleitungsbenachrichtigungen für Besprechungen. In einer Umgebung mit mehreren Gesamtstrukturen möchten Sie die Übermittlung dieser Nachrichtentypen an solche Domänen ggf. zulassen. Wenn Sie allerdings eine Domäne identifiziert haben, aus der Spam gesendet wird, empfiehlt es sich in der Regel, die Übermittlung solcher Nachrichtentypen an die Remotedomänen zu sperren.

**Inhalt**

Nachrichtenformat

Einstellungen für automatische Antworten

Steuern von Unzustellbarkeitsinformationen

## Nachrichtenformat

Sie können das Nachrichtenformat und den Zeichensatz angeben, das bzw. der für E-Mails verwendet werden soll, die an Remotedomänen gesendet werden. Diese Einstellungen können hilfreich sein, um sicherzustellen, dass die aus Ihrer Domäne an die Remotedomäne gesendeten E-Mails mit dem empfangenden E-Mail-System kompatibel sind. Wenn Sie beispielsweise wissen, dass das Messagingsystem der Remotedomäne Exchange ist, können Sie angeben, dass immer das Exchange-RTF-Format verwendet werden soll. Weitere Informationen finden Sie unter [Inhaltskonvertierung](content-conversion-exchange-2013-help.md).

## Einstellungen für automatische Antworten

In Exchange 2013 können Benutzer unterschiedliche automatische Antworten für interne und externe Empfänger angeben. Darüber hinaus sind die in der Organisation verfügbaren Typen von automatischen Antworten auch von der verwendeten Microsoft Outlook-Version abhängig.

In Exchange 2013 stehen zwei Typen von automatischen Antworten zur Verfügung:

  - **Extern**   Wird von Exchange 2013 und Exchange 2010 unterstützt. Kann nur von Outlook 2010 oder Office Outlook 2007 oder mithilfe von Microsoft OfficeOutlook Web App festgelegt werden.

  - **Intern**   Wird von Exchange 2013 und Exchange 2010 unterstützt. Kann nur von Outlook 2010 oder Outlook 2007 oder mithilfe von Outlook Web App festgelegt werden.

In der folgenden Tabelle werden die verschiedenen Kombinationen aus Clients und Servern sowie die Typen von automatischen Antworten aufgeführt, die in den einzelnen Szenarien verwendet werden können.

**Client- und Serverunterstützung für automatische Antworten**


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Clientversion</th>
<th>Exchange-Version</th>
<th>Unterstützte automatische Antworten</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2010 oder Outlook 2007</p></td>
<td><p>Exchange 2013Exchange 2010Exchange 2007</p></td>
<td><p>Intern, Extern</p></td>
</tr>
<tr class="even">
<td><p>Outlook Web App</p></td>
<td><p>Exchange 2013Exchange 2010Exchange 2007</p></td>
<td><p>Intern, Extern</p></td>
</tr>
</tbody>
</table>


## Steuern von Unzustellbarkeitsinformationen

Wie schon zu Beginn dieses Themas erwähnt, können Sie verhindern, dass Unzustellbarkeitsberichte an eine Remotedomäne gesendet werden. Durch das Blockieren von Unzustellbarkeitsberichten für eine Remotedomäne verhindern Sie, dass die im Unzustellbarkeitsbericht enthaltenen Daten Ihre Organisation verlassen, und schränken dadurch die Informationen ein, die ein böswilliger Benutzer über Ihre Organisation erhalten kann. Dadurch erhalten aber auch berechtigte Absender keine Unzustellbarkeitsberichte, was zu Verwirrung und Produktivitätseinbußen führen kann.

Mit Exchange 2013 können Sie im Detail steuern, welche Inhalte eines Unzustellbarkeitsberichts für eine Remotedomäne bestimmt sind. Mit Exchange 2013 können Sie Unzustellbarkeitsberichte für eine Remotedomäne zulassen und gleichzeitig alle Diagnoseinformationen entfernen. Auf diese Weise verhindern Sie, dass Informationen zur Exchange-Bereitstellung Ihre Organisation verlassen, und stellen gleichzeitig externen Absendern Unzustellbarkeitsbenachrichtigungen zur Verfügung.

Diese Funktion wird über den Parameter *NDRDiagnosticInfoEnabled* des Cmdlets **Set-RemoteDomain** gesteuert. Diese Einstellung kann für jede Remotedomäne konfiguriert werden. Daher können Sie je nach Bedarf unterschiedliche Einstellungen vornehmen. Sie können beispielsweise die Diagnoseinformationen im Unzustellbarkeitsbericht für die Standardremotedomäne entfernen, sie jedoch für die Remotedomänen Ihrer Partner zulassen.

Weitere Informationen zu dieser neuen Einstellung finden Sie unter [Set-RemoteDomain](https://technet.microsoft.com/de-de/library/aa997857\(v=exchg.150\)).


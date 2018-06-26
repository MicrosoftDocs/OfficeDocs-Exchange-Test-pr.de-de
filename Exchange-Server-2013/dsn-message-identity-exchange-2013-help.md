---
title: 'DSN-Nachrichtenidentität: Exchange 2013 Help'
TOCTitle: DSN-Nachrichtenidentität
ms:assetid: 70ffba22-e4fd-4cd3-98f5-8bfca2df89e4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998835(v=EXCHG.150)
ms:contentKeyID: 50475930
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# DSN-Nachrichtenidentität

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Sie können eine benutzerdefinierte DSN-Nachricht (Delivery Status Notification, Benachrichtigung über den Zustellungsstatus) anhand ihrer Syntax identifizieren. Die Identität ist die GUID der angepassten DSN-Nachricht für eine Zeichenfolge, die aus den folgenden Werten besteht:

  - **Locale**   In dieser Variable werden die Länderinformationen der Sprache angegeben, in der die DSN-Nachricht angezeigt wird. Eine Liste der Länderinformationscodes, die in Kombination mit dem **New-SystemMessage**-Befehl verwendet werden können, finden Sie unter [Unterstützte Sprachen für Systemmeldungen](supported-languages-for-system-messages-exchange-2013-help.md).

  - **Internal oder External**   Diese Variable gibt an, ob die DSN-Nachricht nur an Absender gesendet wird, die Teil der internen Microsoft Exchange Server 2013-Organisation sind, oder auch an Absender außerhalb der Exchange-Organisation. Sie können die Option "Internal" verwenden, wenn Sie einen bestimmten E-Mail-Kontakt oder eine Auflösung in DSN-Nachrichten einschließen möchten, die an interne Absender gesendet werden, diese Informationen für Absender außerhalb der Organisation jedoch nicht offenlegen möchten.

  - **DSN-Code**   Diese Variable gibt den DSN-Code der angepassten DSN-Nachricht an.

Die Syntax der DSN-Nachrichtenkennung ist `<Locale>\<Internal or External>\<DSN code>`.

Für jeden DSN-Code kann mehr als eine angepasste DSN-Nachricht erstellt werden, die auf interne Absender oder externe Absender zielt und verschiedene Länderinformationen enthalten kann. Die folgende Tabelle zeigt beispielsweise einige der möglichen Konfigurationen für den DSN-Code 5.1.2 und die entsprechenden DSN-Nachrichtenidentitäten.

### DSN-Beispielkonfigurationen und -Identitäten

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>DSN-Konfiguration</th>
<th>DSN-Identität</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DSN-Nachrichten mit englischen (en) Länderinformationen für interne Absender anzeigen</p></td>
<td><p>En\Internal\5.1.2</p></td>
</tr>
<tr class="even">
<td><p>DSN-Nachrichten mit englischen (en) Länderinformationen für externe Absender anzeigen</p></td>
<td><p>En\External\5.1.2</p></td>
</tr>
<tr class="odd">
<td><p>DSN-Nachrichten mit japanischen (ja) Länderinformationen für interne Absender anzeigen</p></td>
<td><p>Ja\Internal\5.1.2</p></td>
</tr>
<tr class="even">
<td><p>DSN-Nachrichten mit japanischen (ja) Länderinformationen für externe Absender anzeigen</p></td>
<td><p>Ja\External\5.1.2</p></td>
</tr>
</tbody>
</table>


---
title: 'Konfigurieren der Blockierung von Outlook-Clients: Exchange 2013 Help'
TOCTitle: Konfigurieren der Blockierung von Outlook-Clients
ms:assetid: 3a579c83-8bc7-4adc-a25c-8eb6eed7220c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335207(v=EXCHG.150)
ms:contentKeyID: 51409289
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Blockierung von Outlook-Clients

 

_**Gilt für:**Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

In Exchange Server 2013 können Sie Aufbewahrungsrichtlinien oder verwaltete Ordner für die Messaging-Datensatzverwaltung (Messaging Records Management, MRM) verwenden. Nur Benutzer, die Microsoft Outlook 2010 und höher ausführen, haben Zugriff auf alle Clientfunktionen für Aufbewahrungsrichtlinien und verwaltete Ordner. Aufbewahrungsrichtlinien werden jedoch unabhängig von der vom Benutzer verwendeten Outlook-Clientversion vom Assistenten für verwaltete Ordner auf dem Postfachserver angewendet. Ältere Outlook-Clients stellen die MRM-Funktionalität dieser Funktionen nicht bereit. Da Outlook 2007 z. B. keine Aufbewahrungsrichtlinien unterstützt, können Benutzer keine persönlichen Tags auf Elemente oder Ordner anwenden.

Sie können den Zugriff auf Exchange-Postfächer für Benutzer mit älteren Versionen von Outlook blockieren. Sie können den Zugriff auch für einzelne Postfächer oder Clientzugriffsserver blockieren.

Weitere Verwaltungsaufgaben im Zusammenhang mit MRM finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## Verfügbarkeit von MRM-Funktionen nach Clientanwendung und -version

In der folgenden Tabelle sind die MRM-Funktionen aufgelistet, die in verschiedenen Clientanwendungen und -versionen verfügbar sind.

### MRM-Funktionen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Clientanwendung</th>
<th>Verfügbare MRM-Clientfunktionen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2013 und Outlook 2010</p></td>
<td><p>Alle</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2007</p></td>
<td><p>Verwaltete Ordner</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 2003 und früher</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
<tr class="even">
<td><p>Andere E-Mail-Clientsoftware</p></td>
<td><p>Keine</p></td>
</tr>
</tbody>
</table>


In der folgenden Tabelle werden die Versionsnummern für Outlook angezeigt.

### Outlook-Versionen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Outlook-Version</th>
<th>Versionsnummer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2013</p></td>
<td><p>15</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2010</p></td>
<td><p>14</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 2007</p></td>
<td><p>12</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2003</p></td>
<td><p>11</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 2002</p></td>
<td><p>10</p></td>
</tr>
<tr class="even">
<td><p>Outlook 2000</p></td>
<td><p>9</p></td>
</tr>
<tr class="odd">
<td><p>Outlook 98</p></td>
<td><p>8.5</p></td>
</tr>
<tr class="even">
<td><p>Outlook 97</p></td>
<td><p>8</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Bevor Sie Änderungen vornehmen, beachten Sie, dass sich Hotfixes und Service Pack-Releases auf die Versionszeichenfolge des Clients auswirken können. Gehen Sie mit Umsicht vor, wenn Sie den Clientzugriff einschränken, weil serverseitige Exchange-Komponenten ebenfalls MAPI für die Anmeldung verwenden müssen. Einige Komponenten melden ihre Clientversion als Komponentennamen (wie etwa SMTP oder OLE&nbsp;DB), während andere die Exchange-Buildnummer (wie etwa 6.0.4712.0) melden. Vermeiden Sie daher das Einschränken von Clients, die mit 6.&lt;<EM>x</EM>.<EM>x</EM>.&gt; beginnende Versionsnummern aufweisen. Geben Sie beispielsweise, um den MAPI-Zugriff vollständig zu verhindern, statt <STRONG>0.0.0-6.5535.65535.65535</STRONG> zwei Bereiche an, sodass sich die Serverkomponenten anmelden können. Geben Sie z.&nbsp;B. Folgendes an: <STRONG>0.0.0-5.9.9; 7.0.0-</STRONG>.



Seien Sie sich nach dem Ausführen dieser Verfahren bewusst, dass für Benutzer, deren Zugriff auf ihr Postfach blockiert ist, die folgende Warnmeldung angezeigt wird:


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Ihr Exchange Server-Administrator hat die Outlook-Version, die Sie verwenden, blockiert. Weitere Informationen erhalten Sie von Ihrem Administrator.</p></td>
</tr>
</tbody>
</table>


Um die Warnmeldung zu umgehen, dass MRM-Funktionen für E-Mail-Clients, die frühere Outlook-Versionen als Outlook 2010 ausführen, nicht unterstützt werden, können Sie den Parameter *ManagedFolderMailboxPolicyAllowed* der Cmdlets **New-Mailbox**, **Enable-Mailbox** und **Set-Mailbox** in der Shell verwenden. Wenn eine Postfachrichtlinie für verwalteten Ordner mithilfe des Parameters *ManagedFolderMailboxPolicy* einem Postfach zugewiesen wurde, wird die Warnung standardmäßig angezeigt, sofern nicht der Parameter *ManagedFolderMailboxPolicyAllowed* verwendet wird.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Diese Verfahren können nicht mit der Exchange-Verwaltungskonsole durchgeführt werden. Sie müssen die Shell verwenden.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Was möchten Sie machen?

## Blockieren von Outlook-Versionen nach Postfächern

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Benutzerpostfächer" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

In diesem Beispiel werden alle Versionen von Outlook blockiert, die älter sind als 11.8010.8036.

    Set-CASMailbox -Identity adam@contoso.com -MAPIBlockOutlookVersions "-11.8010.8036"

In diesem Beispiel wird der von einer Outlook-Version blockierte Zugriff auf das Postfach wiederhergestellt.

    Set-CASMailbox -Identity adam@contoso.com -MAPIBlockOutlookVersions $null

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\)).

## Blockieren von Outlook-Versionen auf einem Clientzugriffsserver

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Einstellungen für den RPC-Clientzugriff" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

In diesem Beispiel wird der Zugriff auf Postfächer auf einem Clientzugriffsserver unter Exchange 2010 oder höher für Outlook-Clients mit einer niedrigeren Version als Version 12.0.0 blockiert.


> [!IMPORTANT]
> Die für den Parameter <EM>BlockedClientVersions</EM> verwendeten Werte sind Beispiele. Sie können die richtigen Versionen der Clientsoftware ermitteln, indem Sie die Protokolldateien für den RPC-Clientzugriff unter <CODE>%ExchangeInstallPath%Logging\RPC Client Access</CODE> analysieren.



    Set-RpcClientAccess -Server CAS01 -BlockedClientVersions "0.0.0-5.65535.65535;7.0.0;8.02.4-11.65535.65535"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-RpcClientAccess](https://technet.microsoft.com/de-de/library/dd351072\(v=exchg.150\)).


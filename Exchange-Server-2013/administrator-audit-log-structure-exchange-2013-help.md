---
title: 'Administrator-Überwachungsprotokollstruktur: Exchange 2013 Help'
TOCTitle: Administrator-Überwachungsprotokollstruktur
ms:assetid: 87e259c9-c884-4d53-bd78-d13f2300d73e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff459251(v=EXCHG.150)
ms:contentKeyID: 50554865
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Administrator-Überwachungsprotokollstruktur

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Administratorüberwachungsprotokolle enthalten eine Aufzeichnung aller Cmdlets und Parameter, die in der Exchange-Verwaltungsshell und von der Exchange-Verwaltungskonsole ausgeführt wurden. Sie werden bei Bedarf beim Ausführen des Berichts "Administratorüberwachungsprotokoll" in der Exchange-Verwaltungskonsole oder des Cmdlets **New-AdminAuditLogSearch** in der Shell erstellt. Weitere Informationen zu Überwachungsprotokollen finden Sie unter [Administratorüberwachungsprotokollierung](administrator-audit-logging-exchange-2013-help.md).

Überwachungsprotokolle sind XML-Dateien und können mehrere Überwachungsprotokolleinträge enthalten. Die folgende Tabelle beschreibt die einzelnen XML-Tags und die zugeordneten Attribute.

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit Administratorüberwachungsprotokollen gibt? Weitere Informationen finden Sie unter [Verwalten der Administratorüberwachungsprotokollierung](manage-administrator-audit-logging-exchange-2013-help.md).

### Überwachungsprotokoll-XML-Tags und Attribute

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Attribut</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;</code></p>
<p></p></td>
<td><p><code>N/A</code></p></td>
<td><p>Dies ist das XML-Dokumentdeklarations-Tag. Es ist in jeder Überwachungsprotokoll-XML-Datei enthalten und enthält die XML-Versionsnummer und den Zeichencodierungswert.</p></td>
</tr>
<tr class="even">
<td><p><code>SearchResults</code></p></td>
<td><p><code>N/A</code></p></td>
<td><p>Dieses Tag enthält alle Überwachungsprotokolleinträge in der XML-Datei. Das Tag <code>Event</code> ist ein untergeordnetes Element dieses Tags.</p>
<p>Es gibt nur ein <code>SearchResults</code>-Tag pro XML-Datei.</p></td>
</tr>
<tr class="odd">
<td><p><code>Event</code></p></td>
<td><p></p></td>
<td><p>Dieses Tag enthält den Überwachungsprotokolleintrag für ein einzelnes Cmdlet. Dieses Tag enthält die Attribute <code>Caller</code>, <code>Cmdlet</code>, <code>ObjectModified</code>, <code>RunDate</code>, <code>Succeeded</code>, <code>Error</code> und <code>OriginatingServer</code>. Die Tags <code>CmdletParameters</code> und <code>ModifiedProperties</code> sind untergeordnete Elemente dieses Tags.</p>
<p>Es gibt ein <code>Event</code>-Tag pro Überwachungsprotokolleintrag.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><code>Caller</code></p></td>
<td><p>Dieses Attribut enthält das Benutzerkonto des Benutzers, der das Cmdlet im Attribut <code>Cmdlet</code> ausgeführt hat.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><code>Cmdlet</code></p></td>
<td><p>Das Attribut enthält den Namen des Cmdlets, das vom Benutzer im Attribut <code>Caller</code> ausgeführt wurde.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><code>ObjectModified</code></p></td>
<td><p>Dieses Attribut enthält das Objekt, das von dem im Attribut <code>Cmdlet</code> angegebenen Cmdlet geändert wurde. Das Tag <code>ModifiedProperties</code> zeigt an, welche Eigenschaften auf diesem Objekt geändert wurden.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><code>RunDate</code></p></td>
<td><p>Dieses Attribut enthält das Datum und die Uhrzeit, zu dem/der das Cmdlet im Attribut <code>Cmdlet</code> ausgeführt wurde.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><code>Succeeded</code></p></td>
<td><p>Dieses Attribut gibt an, ob das Cmdlet im Attribut <code>Cmdlet</code> erfolgreich ausgeführt wurde. Mögliche Werte sind <code>True</code> und <code>False</code>.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><code>Error</code></p></td>
<td><p>Dieses Attribut enthält die generierte Fehlermeldung, wenn das Cmdlet im Attribut <code>Cmdlet</code> nicht erfolgreich ausgeführt wurde. Wenn kein Fehler aufgetreten ist, wird der Wert auf <code>None</code> festgelegt.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><code>OriginatingServer</code></p></td>
<td><p>Dieses Attribut enthält den Server, auf dem das im Attribut <code>Cmdlet</code> angegebene Cmdlet ausgeführt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>CmdletParameters</code></p></td>
<td><p><code>N/A</code></p></td>
<td><p>Dieses Tag enthält alle Parameter, die beim Ausführen des Cmdlets angegeben wurden. Das Tag <code>Parameter</code> ist ein untergeordnetes Element dieses Tags.</p>
<p>Es gibt ein <code>CmdletParameters</code>-Tag pro <code>Event</code>-Tag.</p></td>
</tr>
<tr class="even">
<td><p><code>Parameter</code></p></td>
<td><p></p></td>
<td><p>Dieses Tag enthält jeden einzelnen Parameter, der beim Ausführen des Cmdlets angegeben wurde. Dieses Tag enthält die Attribute <code>Name</code> und <code>Value</code>.</p>
<p>Es kann mehrere <code>Parameter</code>-Tags pro <code>CmdletParameters</code>-Tag geben.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><code>Name</code></p></td>
<td><p>Dieses Attribut enthält den Namen des Parameters, der im ausgeführten Cmdlet angegeben wurde.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><code>Value</code></p></td>
<td><p>Dieses Attribut enthält den Wert, der von dem im Attribut <code>Name</code> angegebenen Parameter bereitgestellt wurde.</p></td>
</tr>
<tr class="odd">
<td><p><code>ModifiedProperties</code></p></td>
<td><p><code>N/A</code></p></td>
<td><p>Dieses Tag enthält alle Eigenschaften, die vom ausgeführten Cmdlet geändert wurden. Das <code>Property</code>-Tag ist ein untergeordnetes Element dieses Tags.</p>
<p>Es gibt ein <code>ModifiedProperties</code>-Tag pro <code>Event</code>-Tag.</p>

> [!IMPORTANT]
> Dieses Tag wird nur aufgefüllt, wenn der Parameter <EM>LogLevel</EM> für das Cmdlet <STRONG>Set-AdminAuditLogConfig</STRONG> auf <CODE>Verbose</CODE> festgelegt ist.


</td>
</tr>
<tr class="even">
<td><p><code>Property</code></p></td>
<td><p></p></td>
<td><p>Dieses Tag enthält eine einzelne Eigenschaft, die beim Ausführen des Cmdlets angegeben wurde. Dieses Tag enthält die Attribute <code>Name</code>, <code>OldValue</code> und <code>NewValue</code>.</p>
<p>Es kann mehrere <code>Property</code>-Tags pro <code>ModifiedProperties</code>-Tag geben.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><code>Name</code></p></td>
<td><p>Dieses Attribut enthält den Namen der Eigenschaft, die beim Ausführen des Cmdlets geändert wurde.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><code>OldValue</code></p></td>
<td><p>Dieses Attribut enthält den Wert, der in der im Attribut <code>Name</code> angegebenen Eigenschaft vor der Änderung enthalten war.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><code>NewValue</code></p></td>
<td><p>Dieses Attribut enthält den Wert, in den die Eigenschaft im Attribut <code>Name</code> geändert wurde.</p></td>
</tr>
</tbody>
</table>


## Beispiel eines Überwachungsprotokolleintrags

Das folgende Beispiel zeigt einen typischen Überwachungsprotokolleintrag. Basierend auf dem Protokolleintrag sind folgende Informationen bekannt:

  - Am 18.10.2012 um 15:48:00 Uhr (UTC-7) hat der Benutzer `Administrator` das Cmdlet **Set-Mailbox** ausgeführt.

  - Beim Ausführen der Cmdlets **Set-Mailbox** wurden die beiden folgenden Parameter bereitgestellt:
    
      - *Identity* mit dem Wert `david`
    
      - *ProhibitSendReceiveQuota* mit dem Wert `10GB`

  - Die folgenden zwei Eigenschaften auf dem Objekt `david` wurden geändert:
    

    > [!NOTE]
    > Die geänderten Eigenschaften werden im Überwachungsprotokoll gespeichert, da der Parameter <EM>LogLevel</EM> für das Cmdlet <CODE>Set-AdminAuditLogConfig</CODE> in diesem Beispiel auf <CODE>Verbose</CODE> festgelegt war.

    
      - *ProhibitSendReceiveQuota* mit dem neuen Wert `10GB`, der den alten Wert `35GB` ersetzte

  - Der Vorgang wurde erfolgreich ohne Fehler abgeschlossen.

<!-- end list -->

    <?xml version="1.0" encoding="utf-8"?>
    <SearchResults>
    
      <Event Caller="corp.e15a.contoso.com/Users/Administrator" Cmdlet="Set-Mailbox" ObjectModified="corp.e15a.contoso.com/Users/david" RunDate="2012-10-18T15:48:15-07:00" Succeeded="true" Error="None" OriginatingServer="WIN8MBX (15.00.0516.032)">
        <CmdletParameters>
          <Parameter Name="Identity" Value="david" />
          <Parameter Name="ProhibitSendReceiveQuota" Value="10 GB (10,737,418,240 bytes)" />
        </CmdletParameters>
        <ModifiedProperties>
          <Property Name="ProhibitSendReceiveQuota" OldValue="35 GB (37,580,963,840 bytes)" NewValue="10 GB (10,737,418,240 bytes)" />
        </ModifiedProperties>
      </Event>
    </SearchResults>


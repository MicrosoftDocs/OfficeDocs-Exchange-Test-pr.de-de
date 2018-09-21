---
title: 'Ändern von mehrwertigen Eigenschaften: Exchange 2013 Help'
TOCTitle: Ändern von mehrwertigen Eigenschaften
ms:assetid: dc2c1062-ad79-404b-8da3-5b5798dbb73b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb684908(v=EXCHG.150)
ms:contentKeyID: 50476860
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ändern von mehrwertigen Eigenschaften

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Eine mehrwertige Eigenschaft ist eine Eigenschaft, die mehr als einen Wert enthalten kann. Die Eigenschaft **BlockedRecipients** des Objekts **RecipientFilterConfig** kann beispielsweise mehrere Empfängeradressen enthalten, wie nachfolgend dargestellt:

  - john@contoso.com

  - kim@northwindtraders.com

  - david@adatum.com

Da die Eigenschaft **BlockedRecipients** mehrere Werte akzeptiert, wird sie als mehrwertige Eigenschaft bezeichnet. In diesem Thema wird erläutert, wie Sie mithilfe der Exchange-Verwaltungsshell Werte zu einer mehrwertigen Eigenschaft eines Objekts hinzufügen bzw. Werte aus einer mehrwertigen Eigenschaft entfernen.

Weitere Informationen zu Objekten finden Sie unter [Strukturierte Daten](https://technet.microsoft.com/de-de/library/aa996386\(v=exchg.150\)). Weitere Informationen zur Shell finden Sie unter [Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\)).

## Ändern mehrwertiger Eigenschaften im Vergleich zum Ändern einwertiger Eigenschaften

Das Ändern einer mehrwertigen Eigenschaft unterscheidet sich geringfügig vom Ändern einer Eigenschaft, die nur einen Wert akzeptiert. Wenn Sie eine Eigenschaft ändern, die nur einen einzigen Wert akzeptiert, können Sie dieser Eigenschaft einen Wert direkt zuweisen, wie im folgenden Befehl dargestellt.

```powershell
Set-TransportConfig -MaxSendSize 12MB
```

Wenn Sie der Eigenschaft **MaxSendSize** mit diesem Befehl einen neuen Wert zuweisen, wird der gespeicherte Wert überschrieben. Bei einwertigen Eigenschaften ist dies unproblematisch. Bei mehrwertigen Eigenschaften stellt dies jedoch ein Problem dar. Angenommen, die Eigenschaft **BlockedRecipients** des Objekts **RecipientFilterConfig** ist mit den drei Werten konfiguriert, die im vorherigen Abschnitt aufgeführt sind. Wenn Sie den Befehl `Get-RecipientFilterConfig | Format-List BlockedRecipients` ausführen, wird Folgendes angezeigt.

```powershell
BlockedRecipients : {david@adatum.com, kim@northwindtraders.com, john@contoso.com}
```

Angenommen, Sie werden nun gebeten, eine neue SMTP-Adresse zur Liste der blockierten Empfänger hinzuzufügen. Um die neue SMTP-Adresse hinzuzufügen, führen Sie den folgenden Befehl aus.

```powershell
Set-RecipientFilterConfig -BlockedRecipients chris@contoso.com
```

Wenn Sie den Befehl `Get-RecipientFilterConfig | Format-List BlockedRecipients` erneut ausführen, wird Folgendes angezeigt.

```powershell
BlockedRecipients : {chris@contoso.com}
```

Dies ist nicht, was Sie erwartet haben. Sie wollten die neue SMTP-Adresse zur vorhandenen Liste der blockierten Empfänger hinzufügen, stattdessen wurde die vorhandene Liste der blockierten Empfänger jedoch durch die neue SMTP-Adresse ersetzt. Dieses unbeabsichtigte Ergebnis zeigt den Unterschied beim Ändern mehrwertiger und einwertiger Eigenschaften. Wenn Sie eine mehrwertige Eigenschaft ändern, müssen Sie sicherstellen, dass Werte hinzugefügt bzw. einzelne Werte entfernt werden und nicht die gesamte Werteliste überschrieben wird. In den folgenden Abschnitten wird veranschaulicht, die Sie genau dies tun.

## Ändern von mehrwertigen Eigenschaften

Das Ändern mehrwertiger Eigenschaften ähnelt der Änderung einwertiger Eigenschaften. Sie müssen nur zusätzliche Syntax hinzufügen und der Shell damit mitteilen, dass Sie der mehrwertigen Eigenschaft Werte hinzufügen bzw. daraus entfernen möchten, statt alle in der Eigenschaft gespeicherten Informationen zu ersetzen. Die Syntax wird zusammen mit dem Wert bzw. den Werten, die Sie der Eigenschaft hinzufügen bzw. daraus entfernen möchten, beim Ausführen eines Cmdlets als Wert für einen Parameter angegeben. Die folgende Tabelle zeigt die Syntax, die Sie einem Parameter bei einem Cmdlet hinzufügen müssen, um mehrwertige Eigenschaften zu ändern.

### Syntax mehrwertiger Eigenschaften

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Action</th>
<th>Syntax</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Hinzufügen eines oder mehrerer Werte zu einer mehrwertigen Eigenschaft</p></td>
<td><pre><code>@{Add=&quot;&lt;value1&gt;&quot;, &quot;&lt;value2&gt;&quot;, &quot;&lt;value3&gt;&quot;}</code></pre></td>
</tr>
<tr class="even">
<td><p>Entfernen eines oder mehrerer Werte aus einer mehrwertigen Eigenschaft</p></td>
<td><pre><code>@{Remove=&quot;&lt;value1&gt;&quot;, &quot;&lt;value2&gt;&quot;, &quot;&lt;value3&gt;&quot;}</code></pre></td>
</tr>
</tbody>
</table>


Die Syntax, die Sie in der Syntaxtabelle für mehrwertige Eigenschaften auswählen, wird als Parameterwert für ein Cmdlet angegeben. Der folgende Befehl fügt einer mehrwertigen Eigenschaft beispielsweise mehrere Werte hinzu:

```powershell
Set-ExampleCmdlet -Parameter @{Add="Red", "Blue", "Green"}
```

Wenn Sie diese Syntax verwenden, werden die von Ihnen angegebenen Werte der Liste von Werten hinzugefügt bzw. daraus entfernt, die für die Eigenschaft bereits vorhanden sind. Um das **BlockedRecipients**-Beispiel weiter oben in diesem Thema aufzugreifen, können Sie jetzt "chris@contoso.com" hinzufügen, ohne die übrigen Werte dieser Eigenschaft zu überschreiben. Dazu verwenden Sie folgenden Befehl:

```powershell
Set-RecipientFilterConfig -BlockedRecipients @{Add="chris@contoso.com"}
```

Wenn Sie "david@adatum.com" aus der Werteliste entfernen möchten, verwenden Sie folgenden Befehl:

```powershell
Set-RecipientFilterConfig -BlockedRecipients @{Remove="david@adatum.com"}
```

Komplexere Kombinationen sind möglich, beispielsweise das gleichzeitige Hinzufügen und Entfernen von Werten zu bzw. aus einer Eigenschaft. Hierzu fügen Sie ein Semikolon (`;`) zwischen `Add` und `Remove`-Aktionen ein. Beispiel:

    Set-RecipientFilterConfig -BlockedRecipients @{Add="carter@contoso.com", "sam@northwindtraders.com", "brian@adatum.com"; Remove="john@contoso.com"}

Wenn Sie den Befehl `Get-RecipientFilterConfig | Format-List BlockedRecipients` erneut ausführen, stellen Sie fest, dass die E-Mail-Adressen für Carter, Sam und Brian hinzugefügt wurden und dass die Adresse für John entfernt wurde.

    BlockedRecipients : {brian@adatum.com, sam@northwindtraders.com, carter@contoso.com, chris@contoso.com, kim@northwindtraders.com}


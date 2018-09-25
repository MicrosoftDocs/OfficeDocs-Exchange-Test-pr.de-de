---
title: 'Verwalten der Anlagenfilterung auf Edge-Transport-Servern: Exchange 2013 Help'
TOCTitle: Verwalten der Anlagenfilterung auf Edge-Transport-Servern
ms:assetid: 2ec91cc6-6ade-48ee-88bb-66153874393d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997139(v=EXCHG.150)
ms:contentKeyID: 60828897
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten der Anlagenfilterung auf Edge-Transport-Servern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Anlagenfilterung wird vom Anlagenfilter-Agent bereitgestellt, der nur auf Edge-Transport-Servern verfügbar ist. Mit der Anlagenfilterung wird verhindert, dass an E-Mail-Nachrichten angehängte Dateien in Ihre Organisation gelangen. Sie können einen oder mehrere Anlagenfiltereinträge konfigurieren, um Anlagen nach Inhaltstyp oder Dateiname zu filtern.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfunktionen" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md) und "Transport-Agents" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Konfigurationsänderungen, die Sie an Anlagenfiltern auf einem Edge-Transport-Server vornehmen, gelten nur für den lokalen Computer. Wenn Sie mehrere Edge-Transport-Server im Umkreisnetzwerk installiert haben, müssen Sie die Anlagenfilterung auf jedem Edge-Transport-Server separat konfigurieren.

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Wenn Sie die Anlagenfilterung deaktivieren und den Microsoft Exchange-Transportdienst neu starten, funktionieren die Anlagenfilterfunktionen nicht mehr.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Anlagenfilterung mithilfe der Shell

Wenn Sie den Anlagenfilter-Agent aktivieren oder deaktivieren, wird die Änderung wirksam, nachdem Sie den Microsoft Exchange-Transportdienst neu starten. Während Sie den Microsoft Exchange-Transportdienst auf einem Edge-Transport-Server neu starten, wird der E-Mail-Fluss auf dem Server zeitweise unterbrochen.

Führen Sie zum Deaktivieren der Anlagenfilterung folgenden Befehl aus:

```powershell
Disable-TransportAgent "Attachment Filtering Agent"
```

Führen Sie zum Aktivieren der Anlagenfilterung folgenden Befehl aus:

```powershell
Enable-TransportAgent "Attachment Filtering Agent"
```

Nachdem Sie die Anlagenfilterung aktiviert oder deaktiviert haben, starten Sie den Microsoft Exchange-Transportdienst neu, indem Sie folgenden Befehl ausführen:

```powershell
Restart-Service MSExchangeTransport
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob die Anlagenfilterung erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-TransportAgent "Attachment Filtering Agent"
    ```

2.  Wenn der Wert für **Enabled**`True` ist, dann ist die Anlagenfilterung aktiviert. Ist der Wert `False`, dann ist die Anlagenfilterung deaktiviert.

## Verwenden der Shell zum Anzeigen von Anlagenfiltereinträgen

Anlagenfiltereinträge definieren die Nachrichtenanhänge, die Sie aus Ihrer Organisation heraushalten möchten. Zum Anzeigen der Anlagenfiltereinträge, die vom Anlagenfilter-Agent verwendet werden, führen Sie den folgenden Befehl aus:

```powershell
Get-AttachmentFilterEntry | Format-Table
```

Verwenden Sie die folgende Syntax, um einen bestimmten MIME-Inhaltstyp anzuzeigen:

```powershell
Get-AttachmentFilteringEntry ContentType:<MIMEContentType>
```

Führen Sie z. B. den folgenden Befehl aus, um den Inhaltstypeintrag für JPEG-Bilder anzuzeigen:

```powershell
Get-AttachmentFilteringEntry ContentType:image/jpeg
```

Verwenden Sie die folgende Syntax, um den Eintrag für einen bestimmten Dateinamen oder eine Dateinamenerweiterung anzuzeigen:

```powershell
Get-AttachmentFilteringEntry FileName:<FileName or FileNameExtension>
```

Führen Sie z. B. den folgenden Befehl aus, um den Dateinamenerweiterungseintrag für JPEG-Anlagen anzuzeigen:

```powershell
    Get-AttachmentFilteringEntry FileName:*.jpg
```

## Verwenden der Shell zum Hinzufügen von Anlagenfiltereinträgen

Wenn Sie einen Anlagenfiltereintrag hinzufügen möchten, der Anlagen mit einem bestimmten MIME-Inhaltstyp filtert, verwenden Sie die folgende Syntax:

```powershell
Add-AttachmentFilterEntry -Name <MIMEContentType> -Type ContentType
```

Im folgenden Beispiel wird ein MIME-Inhaltstypeintrag hinzugefügt, der JPEG-Bilder filtert.

```powershell
Add-AttachmentFilterEntry -Name image/jpeg -Type ContentType
```

Wenn Sie einen Anlagenfiltereintrag hinzufügen möchten, der Anlagen nach Dateiname oder Dateinamenerweiterung filtert, verwenden Sie die folgende Syntax:

```powershell
Add-AttachmentFilterEntry -Name <FileName or FileNameExtension> -Type FileName
```

Im folgenden Beispiel werden Anlagen mit der JPG-Erweiterung gefiltert.

```powershell
    Add-AttachmentFilterEntry -Name *.jpg -Type FileName
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob der Anlagenfiltereintrag erfolgreich hinzugefügt wurde:

1.  Führen Sie den folgenden Befehl aus, um sicherzustellen, dass der Filtereintrag vorhanden ist:
    
    ```powershell
    Get-AttachmentFilterEntry | Format-Table
    ```

2.  Senden Sie eine Testnachricht, die eine verbotene Anlage enthält, von einem externen Postfach an einen internen Empfänger, und vergewissern Sie sich, dass die Nachricht abgelehnt, gelöscht oder die Anlage entfernt wird.

## Verwenden der Shell zum Entfernen von Anlagenfiltereinträgen

Wenn Sie einen Anlagenfiltereintrag entfernen möchten, der Anlagen mit einem bestimmten MIME-Inhaltstyp filtert, verwenden Sie die folgende Syntax:

```powershell
Remove-AttachmentFilterEntry ContentType:<ContentType>
```

Im folgenden Beispiel wird ein MIME-Inhaltstypeintrag entfernt, der JPEG-Bilder filtert.

```powershell
Remove-AttachmentFilterEntry ContentType:image/jpeg
```

Wenn Sie einen Anlagenfiltereintrag entfernen möchten, der Anlagen nach Dateiname oder Dateinamenerweiterung filtert, verwenden Sie die folgende Syntax:

```powershell
Remove-AttachmentFilterEntry FileName:<FileName or FileNameExtension>
```

Im folgenden Beispiel wird der Dateinameneintrag für die JPG-Erweiterung entfernt.

```powershell
    Remove-AttachmentFilterEntry FileName:*.jpg
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob der Anlagenfiltereintrag erfolgreich entfernt wurde:

1.  Führen Sie den folgenden Befehl aus, um sicherzustellen, dass der Filtereintrag entfernt wurde:
    
    ```powershell
    Get-AttachmentFilterEntry | Format-Table
    ```

2.  Senden Sie eine Testnachricht, die eine zulässige Anlage enthält, von einem externen Postfach an einen internen Empfänger, und vergewissern Sie sich, dass die Nachricht mit der Anlage erfolgreich zugestellt wird.

## Verwenden der Shell zum Anzeigen der Anlagenfilteraktion

Zum Anzeigen der Anlagenfilteraktion, die verwendet wird, wenn eine verbotene Anlage in einer Nachricht erkannt wird, führen Sie den folgenden Befehl aus:

```powershell
Get-AttachmentFilterListConfig
```

## Verwenden der Shell zum Konfigurieren der Anlagenfilteraktion

Zum Konfigurieren der Anlagenfilteraktion, die verwendet wird, wenn eine verbotene Anlage in einer Nachricht erkannt wird, verwenden Sie die folgende Syntax:

```powershell
    Set-AttachmentFilterListConfig [-Action <Reject | Strip | SilentDelete>] [-RejectResponse "<Message text>"] [-AdminMessage "<Replacement file text>"] [-ExceptionConnectors <ConnectorGUID>]
```

In diesem Beispiel werden folgende Änderungen an der Anlagenfilterkonfiguration vorgenommen:

  - Ablehnen (Blockieren) von Nachrichten mit verbotenen Anlagen

  - Verwenden einer benutzerdefinierten Antwort für abgelehnte Nachrichten

<!-- end list -->

```powershell
    Set-AttachmentFilterListConfig -Action Reject -RejectResponse "This message contains a prohibited attachment. Your message can't be delivered. Please resend the message without the attachment."
```

Weitere Informationen finden Sie unter [Set-AttachmentFilterListConfig](https://technet.microsoft.com/de-de/library/bb123483\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sicherzustellen, dass Sie die Anlagenfilteraktion erfolgreich konfiguriert haben, senden Sie eine Testnachricht, die eine verbotene Anlage enthält, von einem externen Postfach an einen internen Empfänger, und vergewissern Sie sich, dass die Anlage wie erwartet behandelt wird.


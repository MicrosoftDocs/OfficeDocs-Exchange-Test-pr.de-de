---
title: 'Anlagenfilterung auf Edge-Transport-Servern: Exchange 2013 Help'
TOCTitle: Anlagenfilterung auf Edge-Transport-Servern
ms:assetid: be39a181-c82e-41f5-8846-085bf1f84164
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124399(v=EXCHG.150)
ms:contentKeyID: 60828923
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anlagenfilterung auf Edge-Transport-Servern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-02-10_

In Microsoft Exchange Server 2013 können Sie mit der Anlagenfilterung auf Edge-Transport-Servern die Anlagen kontrollieren, die Benutzer mit ihren E-Mail-Nachrichten erhalten. Die Anlagenfilterung wird vom Anlagenfilter-Agent durchgeführt, der nur auf Edge-Transport-Servern zur Verfügung steht.

## Arten der Anlagenfilterung

Folgende Arten der Anlagenfilterung können zur Steuerung der Anlagen, die in Ihrer Organisation über einen Edge-Transport-Server ein- oder ausgehen, verwendet werden:

  - **Filterung anhand von Dateinamen oder Dateinamenerweiterungen**   Sie können den genauen Dateinamen oder die Dateinamenerweiterung der zu filternden Anlagen angeben. Ein Beispiel für einen Dateinamenfilter ist `BadFileName.exe`. Ein Beispiel für einen Dateinamenerweiterungsfilter ist `*.exe`.

  - **Filterung anhand von MIME-Inhaltstypen von Dateien**   Sie geben den MIME-Inhaltstypenwert an, den Sie filtern möchten. Der Wert für den MIME-Inhaltstyp gibt an, um was es sich bei der Anlage handelt, z. B. ein JPEG-Bild, eine ausführbare Datei oder eine Microsoft Excel-Datei. Inhaltstypen werden als `type/subtype` ausgedrückt. So wird eine JPEG-Bilddatei beispielsweise durch `image/jpeg` angegeben.
    
    Führen Sie den auf dem Edge-Transport-Server folgenden Befehl aus, um eine vollständige Liste aller Dateinamenerweiterungen und Inhaltstypen anzuzeigen, auf die die Anlagenfilterung angewendet werden kann:
    
    ```powershell
    Get-AttachmentFilterEntry | Format-List
    ```

Nachdem Sie die zu suchenden Dateien definiert haben, können Sie die Aktion festlegen, die für Nachrichten mit diesen Anlagen durchgeführt werden soll. Sie können keine unterschiedlichen Aktionen für unterschiedliche Arten von Anlagen angeben. Sie können eine der folgenden Aktionen für alle Nachrichten konfigurieren, die den Anlagenfiltern entsprechen:

  - **Nachricht ablehnen (blockieren)**   Die Nachricht wird blockiert. Der Absender erhält einen Unzustellbarkeitsbericht (NDR), in dem erläutert wird, dass die Nachricht aufgrund einer unzulässigen Anlage nicht zugestellt wurde. Sie können den Text im Unzustellbarkeitsbericht anpassen. Der Standardtext lautet: `Message rejected due to unacceptable attachments`.

  - **Anlage entfernen, aber Nachricht passieren lassen**   Die Anlage wird aus der Nachricht gelöscht. Die Nachricht selbst sowie andere Anlagen, die dem Filter nicht entsprechen, werden weitergeleitet. Wenn eine Anlage entfernt wird, wird sie durch eine Textdatei ersetzt, in der erläutert wird, weshalb die Anlage entfernt wurde. Hierbei handelt es sich um die Standardaktion.

  - **Nachricht ohne Benachrichtigung löschen**   Die Nachricht wird gelöscht. Weder der Absender noch der Empfänger erhält eine Benachrichtigung.

Weitere Informationen finden Sie unter [Verwalten der Anlagenfilterung auf Edge-Transport-Servern](manage-attachment-filtering-on-edge-transport-servers-exchange-2013-help.md).


> [!NOTE]
> Sie können Nachrichten, die blockiert wurden, oder Anlagen, die entfernt wurden, nicht mehr abrufen. Untersuchen Sie beim Konfigurieren von Anlagenfiltern alle möglichen Dateinamenentsprechungen sorgfältig. Stellen Sie außerdem sicher, dass rechtmäßige Anlagen von dem Filter unberührt bleiben.<BR>Entfernen Sie außerdem keine Anlagen von digital signierten, verschlüsselten oder durch Rechte geschützten E-Mail-Nachrichten. Wenn Sie Anlagen von solchen Nachrichten entfernen, wird die digital signierte Nachricht ungültig und verschlüsselte bzw. durch Rechte geschützte Nachrichten werden unlesbar.



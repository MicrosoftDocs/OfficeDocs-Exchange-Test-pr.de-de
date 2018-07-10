---
title: Importieren des Exchange Server 2013-Management Packs
TOCTitle: Importieren des Exchange Server 2013-Management Packs
ms:assetid: dc929928-61b8-448b-9ae5-d3fa73a18ee9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn195914(v=EXCHG.150)
ms:contentKeyID: 53181889
ms.date: 04/03/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Importieren des Exchange Server 2013-Management Packs

 

_**Letztes Änderungsdatum des Themas:**  2013-03-30_

Beginnen wir mit dem Importieren des Management Pack in die SCOM-Bereitstellung.

## Voraussetzungen

Bevor Sie das Management Pack importieren können, stellen Sie sicher, dass die folgenden Bedingungen erfüllt sind:

  - Sie haben eine der folgenden Versionen von System Center Operations Manager in Ihrer Organisation bereitgestellt:
    
      - System Center Operations Manager 2012 RTM oder höher
    
      - System Center Operations Manager 2007 R2 oder höher

  - Sie haben auf Ihren Exchange-Servern bereits SCOM-Agenten bereitgestellt. [Überprüfen des Agent-Bereitstellungsstatus](procedures-related-to-deployment.md).

  - Die SCOM-Agenten auf Ihren Exchange-Servern werden unter dem lokalen Systemkonto ausgeführt. [Überprüfen der Agent-Sicherheitskonfiguration](procedures-related-to-deployment.md).

  - Die SCOM-Agenten auf Ihren Exchange-Servern sind so konfiguriert, dass sie als Proxy dienen und verwaltete Objekte auf anderen Computern erkennen. [Überprüfen der Agent-Proxykonfiguration](procedures-related-to-deployment.md).

  - Ihr Benutzerkonto ist ein Mitglied der Operations Manager-Administratorrolle.

## Importieren des Exchange Server 2013-Management Packs

Führen Sie die folgenden Schritte aus, um das Exchange Server 2013-Management Pack zu importieren. Bei diesem Verfahren wird vorausgesetzt, dass Sie die Management Pack-Inhalte auf ein lokales Laufwerk auf Ihrem System Center Operations Manager-Server (SCOM) extrahiert haben. Sie können das Exchange Server 2013-Management Pack herunterladen im

1.  Melden Sie sich bei Ihrem SCOM-Server an, und laden Sie das Exchange Server 2013-Management Paket im [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?linkid=268587) herunter.

2.  Extrahieren Sie den Inhalt des Management Pack in einen Ordner auf Ihrem System, indem Sie die Datei `ExchangeServerManagementPack.msi` ausführen.

3.  Starten Sie die SCOM-Konsole. Klicken Sie in der SCOM-Konsole auf **Verwaltung**.

4.  Klicken Sie mit der rechten Maustaste auf **Management Packs**, und klicken Sie dann auf **Management Pack importieren**.

5.  Der Assistent zum Importieren von Management Packs wird geöffnet. Klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Von Datenträger hinzufügen**.

6.  Das Dialogfeld **Zu importierende Management Packs auswählen** wird angezeigt. Navigieren Sie zum Verzeichnis mit dem extrahierten Management Pack. Klicken Sie auf die Datei `Microsoft.Exchange.15.mp`, und klicken Sie anschließend auf **Öffnen**.

7.  Auf der Seite**Management Packs auswählen** wird das Exchange Server 2013-Management Pack aufgeführt. Klicken Sie auf **Installieren**.

8.  Auf der Seite **Management Packs importieren** wird der Fortschritt des Vorgangs angezeigt. Wenn in einer beliebigen Phase des Importvorgangs ein Problem auftritt, wählen Sie das Management Pack in der Liste aus, um die Statusdetails anzuzeigen.

9.  Klicken Sie nach Abschluss des Importvorgangs auf **Schließen**.

10. Klicken Sie auf **Ansicht** und dann **Aktualisieren**, oder drücken Sie die Taste F5, damit das Microsoft Exchange Server 2013-Management Pack in der Liste der Management Packs angezeigt wird.

Nachdem Sie das Management Pack nun importiert haben, lesen Sie [Erste Schritte mit Exchange Server 2013 Management Pack](getting-started-with-exchange-server-2013-management-pack.md) für weitere Informationen zum neuen Dashboard.


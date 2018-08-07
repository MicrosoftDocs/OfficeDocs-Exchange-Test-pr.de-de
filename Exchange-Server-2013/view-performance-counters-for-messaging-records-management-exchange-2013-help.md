---
title: 'Anz. v. Leistungsindikat. für Messaging-Datensatzverw.: Exchange 2013-Hilfe'
TOCTitle: Anzeigen von Leistungsindikatoren für die Messaging-Datensatzverwaltung
ms:assetid: ec374d31-2797-4f8b-8c96-3839d01a662c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb397227(v=EXCHG.150)
ms:contentKeyID: 51409363
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen von Leistungsindikatoren für die Messaging-Datensatzverwaltung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2009-12-09_

Mithilfe der Windows-Zuverlässigkeits- und Leistungsüberwachung (**Perfmon.exe**) können Leistungsindikatoren für die Messaging-Datensatzverwaltung (Messaging Records Management, MRM) ausgewählt und angezeigt werden. Anhand von Leistungsindikatoren können Sie den Assistenten für verwaltete Ordner während der Ausführung ressourcenintensiver MRM-Prozesse überwachen.

Eine Liste der Leistungsindikatoren für MRM finden Sie unter [Leistungsindikatoren für die Verwaltung von Nachrichtendatensätzen](performance-counters-for-messaging-records-management-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Aufgaben es im Zusammenhang mit der MRM-Überwachung gibt? Weitere Informationen finden Sie hier: [Überwachen von messaging-datensatzverwaltung](monitoring-messaging-records-management-exchange-2013-help.md).

## Verwenden der Windows-Zuverlässigkeits- und Leistungsüberwachung zum Anzeigen von Leistungsindikatoren für MRM

Damit Sie dieses Verfahren ausführen können, muss die Mitgliedschaft in der lokalen Gruppe **Administratoren** an das verwendete Konto delegiert worden sein.

1.  Klicken Sie zum Starten der Windows-Zuverlässigkeits- und Leistungsüberwachung auf **Start**, dann auf **Ausführen**, und geben Sie anschließend **perfmon** ein.

2.  Navigieren Sie in der Konsolenstruktur zu **Überwachungstools** \> **Systemmonitor**.

3.  Klicken Sie auf der Symbolleiste auf das Pluszeichen (+). Das Dialogfeld **Leistungsindikatoren hinzufügen** wird angezeigt.

4.  Wählen Sie in der Liste **Leistungsindikatorobjekte auswählen von** eine der folgenden Optionen aus:
    
      - Wenn Sie dieses Verfahren auf dem lokalen Computer ausführen, wählen Sie **\<Lokaler Computer\>** aus. Dies ist die Standardauswahl.
    
      - Wenn Sie dieses Verfahren remote durchführen, wählen Sie den Server aus, den Sie überwachen möchten.

5.  Erweitern Sie in der Liste der Leistungsindikatoren den Eintrag **MSExchange-Assistenten - Pro Datenbank** oder **MSExchange-Assistent für verwaltete Ordner**.

6.  Wählen Sie die zu überwachenden Leistungsindikatoren aus.

7.  Um die Leistungsindikatoren unter **MSExchange-Assistenten - Pro Datenbank** für alle Postfachdatenbanken anzuzeigen, klicken Sie unter **Instanzen des ausgewählten Objekts** auf **Alle Instanzen**. Um eine oder mehrere Postfachdatenbanken anzugeben, wählen Sie die entsprechenden Instanzen aus der Liste aus.

8.  Um die ausgewählten Leistungsindikatoren zur Anzeige in der Windows-Zuverlässigkeits- und Leistungsüberwachung hinzuzufügen und mit dem Erfassen von Leistungsdaten zu beginnen, klicken Sie auf **Hinzufügen**.


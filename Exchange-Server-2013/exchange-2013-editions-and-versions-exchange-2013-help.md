---
title: 'Exchange 2013: Editionen und Versionen: Exchange 2013 Help'
TOCTitle: 'Exchange 2013: Editionen und Versionen'
ms:assetid: b563b543-fb3f-4465-9a54-cbfd680aee1f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232170(v=EXCHG.150)
ms:contentKeyID: 50554910
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange 2013: Editionen und Versionen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Microsoft Exchange Server 2013 ist in zwei Servereditionen verfügbar: Standard Edition und Enterprise Edition. Enterprise Edition kann bis auf 50 Datenbanken pro Server in der RTM-Version und den kumulativen Update 1 (CU1) Versionen sowie bis auf 100 Datenbanken pro Server in den kumulativen Update 2 (CU2) und höheren Versionen erweitert werden; die Standard Edition ist auf 5 Datenbanken pro Server beschränkt. Bei einer bereitgestellten Datenbank handelt es sich um eine Datenbank, die bereits in Betrieb ist. Eine bereitgestellte Datenbank kann eine aktive Postfachdatenbank sein, die für die Verwendung durch Clients bereitgestellt wird oder eine passive Postfachdatenbank, die zur Wiederherstellung von Replikations- und Wiedergabeprotokollen bereitgestellt wird. Obwohl Sie mehrere Datenbanken als oben angegeben erstellen können, können Sie nur die oben angegebene maximale Anzahl an Datenbanken bereitstellen. Für die Datenbankwiederherstellung gilt diese Einschränkung nicht.

Diese Lizenzierungseditionen sind durch einen Product Key definiert. Wenn Sie einen gültigen, lizenzierten Product Key eingeben, wird die für den Server unterstützte Edition eingerichtet. Product Keys können nur für Schlüsselwechsel bei derselben Edition und für Upgrades verwendet werden, nicht für Herabstufungen. Sie können einen gültigen Product Key verwenden, um von einer Evaluierungsversion (Testversion) von Exchange 2013 zur Standard Edition oder zur Enterprise Edition zu wechseln. Sie können einen gültigen Product Key auch verwenden, um von der Standard Edition zur Enterprise Edition zu wechseln.

Sie können auch den Server mithilfe eines Product Keys derselben Edition erneut lizenzieren. Wenn Sie z. B. über zwei Standard Edition-Server mit zwei Product Keys verfügen, aber aus Versehen denselben Product Key für beide Server verwendet haben, dann können Sie den Product Key für einen Server ändern, sodass dieser den anderen für Sie ausgestellten Product Key verwendet. Sie können diese Maßnahmen ohne erneute Installation oder Konfiguration durchführen. Nachdem Sie den Product Key eingegeben und den Microsoft Exchange-Informationsspeicherdienst neu gestartet haben, wird die dem Product Key entsprechende Edition angezeigt.

Wenn die Testversion abläuft, wird die Funktionalität nicht eingeschränkt. Daher können Sie Labor-, Demo-, Schulungs- und andere Testumgebungen länger als 120 Tage beibehalten, ohne die Testversion von Exchange 2013 erneut installieren zu müssen.

Wie bereits erwähnt, können Sie mit den Product Keys keine Herabstufung von der Enterprise Edition auf die Standard Edition durchführen, und Sie können die Product Keys nicht dazu verwenden, um zur Testversion zurückzukehren. Für diese Arten von Herabstufung müssen Sie Exchange 2013 deinstallieren, Exchange 2013 erneut installieren und anschließend den richtigen Produkt Key eingeben.

## Exchange 2013-Versionen

Eine Liste der Exchange 2013-Versionen und Informationen zum Herunterladen und zum Upgrade auf die neueste Version von Exchange 2013 finden Sie in den folgenden Themen:

  - [Exchange Server-Updates: Buildnummern und Veröffentlichungstermine](https://technet.microsoft.com/de-de/library/hh135098\(v=exchg.150\))

  - [Aktualisieren von Exchange 2013 auf das neueste kumulative Update oder Service Pack](upgrade-exchange-2013-to-the-latest-cumulative-update-or-service-pack-exchange-2013-help.md)

Um die Buildnummer für die Exchange 2013-Version anzuzeigen, die Sie ausführen, verwenden Sie in der Exchange-Verwaltungsshell den folgenden Befehl:

    Get-ExchangeServer | fl name,edition,admindisplayversion

## Exchange 2013-Lizenztypen

Exchange 2013 wird ähnlich wie Exchange 2010 als Server-/Clientzugriffslizenz-Modell lizenziert. Es gibt die folgenden Arten von Lizenzen:

  - **Serverlizenzen**   Für jede ausgeführte Instanz der Serversoftware muss eine Lizenz zugewiesen werden. Die Serverlizenz wird über zwei Servereditionen vertrieben: Standard Edition und Enterprise Edition.

  - **Clientzugriffslizenzen (Client Access Licenses, CALs)**   Exchange 2013 ist zudem in zwei CAL-Editionen verfügbar, die als Standard-CAL und Enterprise-CAL bezeichnet werden. Sie können die Servereditionen und die CAL-Typen beliebig kombinieren. Sie können z. B. Enterprise-CALs mit der Exchange 2013 Standard Edition verwenden. Ebenso können Sie Standard-CALs mit der Exchange 2013 Enterprise Edition verwenden.

Weitere Informationen über die Lizenztypen von Exchange finden Sie unter [Lizenzierung](https://go.microsoft.com/fwlink/p/?linkid=392675).


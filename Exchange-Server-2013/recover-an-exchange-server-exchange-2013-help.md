---
title: 'Wiederherstellen eines Exchange-Servers: Exchange 2013 Help'
TOCTitle: Wiederherstellen eines Exchange-Servers
ms:assetid: 46e9a1cf-b64c-43c3-a898-6171176da761
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876880(v=EXCHG.150)
ms:contentKeyID: 50475589
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Wiederherstellen eines Exchange-Servers

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mithilfe der Option **Setup /m:RecoverServer** von Microsoft Exchange Server 2013 können Sie einen ausgefallenen Server wiederherstellen. Die meisten der Einstellungen für einen Computer mit Exchange 2013 sind in Active Directory gespeichert. Mit der Option */m:RecoverServer* wird anhand der Informationen und Einstellungen in Exchange ein neuer Active Directory-Server mit dem gleichen Namen erstellt.

Die Wiederherstellung eines ausgefallenen Servers mit Exchange erfolgt häufig unter Verwendung neuer Hardware. Sie können jedoch auch einen vorhandenen Server verwenden.

In diesem Thema wird erläutert, wie Sie einen ausgefallenen Server mit Exchange 2013 wiederherstellen, der kein Mitglied einer Database Availability Group (DAG) ist. Eine ausführliche Beschreibung der Schritte zum Wiederherstellen eines Servers, der Mitglied einer DAG war, finden Sie unter [Wiederherstellen von Mitgliedsservern einer Datenbankverfügbarkeitsgruppe](recover-a-database-availability-group-member-server-exchange-2013-help.md).


> [!NOTE]
> Wenn Exchange nicht im Standardverzeichnis installiert wird, müssen Sie den Speicherort der Exchange-Binärdateien über die Option <EM>/TargetDir</EM> angeben. Wenn Sie die Option <EM>/TargetDir</EM> nicht verwenden, werden die Exchange-Dateien im Standardverzeichnis ("%Programme%\Microsoft\Exchange Server\V15") installiert.<BR>Führen Sie zum Ermitteln des Installationsverzeichnisses die folgenden Schritte aus: 
> <OL>
> <LI>
> <P>Öffnen Sie ADSIEDIT.MSC oder LDP.EXE.</P>
> <LI>
> <P>Navigieren Sie zu folgendem Verzeichnis: <STRONG>CN=ExServerName,CN=Servers,CN=First Administrative Group,CN=Administrative Groups,CN=ExOrg Name,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=DomainName,CN=Com</STRONG></P>
> <LI>
> <P>Klicken Sie mit der rechten Maustaste auf das Exchange-Serverobjekt, und klicken Sie dann auf <STRONG>Eigenschaften</STRONG>.</P>
> <LI>
> <P>Suchen Sie nach dem Attribut <STRONG>msExchInstallPath</STRONG>. Dieses Attribut speichert den aktuellen Installationspfad.</P></LI></OL>



Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit dem Sichern und Wiederherstellen von Daten gibt? Weitere Informationen finden Sie hier: [Sicherung, Wiederherstellung und Notfallwiederherstellung](backup-restore-and-disaster-recovery-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 20 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Exchange-Infrastrukturberechtigungen" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Auf dem Server, auf dem die Wiederherstellung erfolgt, muss das gleiche Betriebssystem wie auf dem ausgefallenen Server ausgeführt werden. Es ist beispielsweise nicht möglich, einen Server, auf dem Exchange 2013 und Windows Server 2008 R2 ausgeführt wurden, auf einem Server unter Windows Server 2012 wiederherzustellen oder umgekehrt. Es ist gleichermaßen nicht möglich, einen Server, auf dem Exchange 2013 und Windows Server 2012 ausgeführt wurden, auf einem Server unter Windows Server 2012 R2 wiederherzustellen oder umgekehrt.

  - Die auf dem ausgefallenen Server für eingebundene Datenbanken vorhandenen Laufwerkbuchstaben müssen auch auf dem Server vorhanden sein, auf dem Sie die Wiederherstellung durchführen.

  - Der Server, auf dem die Wiederherstellung erfolgt, muss die gleichen Leistungsmerkmale und die gleiche Hardwarekonfiguration wie der ausgefallene Server aufweisen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Wiederherstellen eines ausgefallenen Exchange-Servers

1.  Setzen Sie das Computerkonto für den ausgefallenen Server zurück. Eine detaillierte Anleitung finden Sie unter [Zurücksetzen eines Computerkontos](https://go.microsoft.com/fwlink/p/?linkid=165388).

2.  Installieren Sie das geeignete Betriebssystem, und weisen Sie dem neuen Server den gleichen Namen wie dem ausgefallenen Server zu. Eine erfolgreiche Wiederherstellung ist nicht möglich, wenn der Server, auf dem die Wiederherstellung erfolgt, nicht den gleichen Namen wie der ausgefallenen Server aufweist.

3.  Fügen Sie den Server derselben Domäne hinzu, der der ausgefallene Server angehörte.

4.  Installieren Sie die erforderlichen Voraussetzungen und Betriebssystemkomponenten. Ausführliche Informationen finden Sie unter [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md) und [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

5.  Melden Sie sich am Server an, der wiederhergestellt wird, und öffnen Sie eine Eingabeaufforderung.

6.  Navigieren Sie zu den Installationsdateien von Exchange 2013, und führen Sie den folgenden Befehl aus:
    
    ```powershell
    Setup /m:RecoverServer /IAcceptExchangeServerLicenseTerms
    ```

7.  Nach Abschluss des Setupprogramms, jedoch bevor der wiederhergestellte Server in der Produktionsumgebung in Betrieb genommen wird, müssen Sie erneut alle benutzerdefinierten Einstellungen konfigurieren, die zuvor auf dem Server konfiguriert waren. Starten Sie anschließend den Server neu.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Der erfolgreiche Abschluss des Setups ist der Hauptindikator für eine erfolgreiche Wiederherstellung. Gehen Sie wie folgt vor, um darüber hinaus zu überprüfen, ob Sie einen verlorenen Server erfolgreich wiederhergestellt haben:

  - Öffnen Sie das Windows-Dienste-Tool ("services.msc"), und überprüfen Sie, ob die Microsoft Exchange-Dienste installiert sind und ausgeführt werden.


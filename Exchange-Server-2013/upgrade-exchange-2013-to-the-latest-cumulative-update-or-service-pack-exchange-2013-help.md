---
title: 'Aktualisieren von Exchange 2013 auf neuestes kumulatives Update oder SP'
TOCTitle: Aktualisieren von Exchange 2013 auf das neueste kumulative Update oder Service Pack
ms:assetid: 928a4a0b-0082-4d50-a696-bfaf2782f42d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ983803(v=EXCHG.150)
ms:contentKeyID: 52062895
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktualisieren von Exchange 2013 auf das neueste kumulative Update oder Service Pack

 

_**Gilt für:** Exchange Online, Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-09-04_

Wenn Sie Microsoft Exchange Server 2013 installiert haben, können Sie auf das aktuellste kumulative Update oder Service Pack von Exchange 2013 aktualisieren. Sie können den Exchange 2013-Setup-Assistenten verwenden, um ihre gegenwärtige Version von Exchange 2013 zu aktualisieren. Weitere Informationen zum neuesten kumulativen Update oder Service Pack für Exchange 2013 finden Sie unter [Updates für Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md). Weitere Informationen zu Exchange 2013 finden Sie unter [Neuerungen in Exchange 2013](what-s-new-in-exchange-2013-exchange-2013-help.md).


> [!WARNING]
> Nach dem Aktualisieren von Exchange 2013 auf ein neueres kumulatives Update oder Service Pack können Sie die neue Version nicht mehr deinstallieren, um das System auf die vorherige Version zurückzusetzen. Mit einer Deinstallation der neuen Version entfernen Sie Exchange vom Server.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 60 Minuten

  - Lesen Sie auf jeden Fall die Anmerkungen zu dieser Version, bevor Sie mit der Installation von Exchange 2013 beginnen. Weitere Informationen finden Sie unter [Versionshinweise zu Exchange 2013](release-notes-for-exchange-2013-exchange-2013-help.md).

  - Stellen Sie sicher, dass alle Server, auf denen das kumulative Update oder Service Pack installiert werden soll, die Systemanforderungen und Voraussetzungen erfüllen. Weitere Informationen finden Sie unter [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md) und [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).
    

    > [!WARNING]
    > Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z.&nbsp;B. an „web.config“-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config“ auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.



  - Nach der Installation eines kumulativen Updates oder Service Packs müssen Sie den Computer neu starten, damit Änderungen an der Registrierung und am Betriebssystem vorgenommen werden können.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Installieren des kumulativen Updates oder Service Pack für Exchange 2013

Sie können das kumulative Update oder Service Pack für Exchange 2013 mit dem Setup-Assistenten oder im unbeaufsichtigten Modus installieren. Besondere Anweisungen finden Sie in den folgenden Themen:

  - [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md)

  - [Installieren von Exchange 2013 im unbeaufsichtigten Modus](install-exchange-2013-using-unattended-mode-exchange-2013-help.md)

Wenn der Computer, auf dem Sie ein Service Pack oder ein kumulatives Update installiert haben, Mitglied einer Datenbankverfügbarkeitsgruppe (DAG) ist, befolgen Sie die Schritte im Abschnitt [Durchführen der Wartung bei DAG-Mitgliedern](managing-database-availability-groups-exchange-2013-help.md) des Themas [Verwalten von Datenbankverfügbarkeitsgruppen](managing-database-availability-groups-exchange-2013-help.md).


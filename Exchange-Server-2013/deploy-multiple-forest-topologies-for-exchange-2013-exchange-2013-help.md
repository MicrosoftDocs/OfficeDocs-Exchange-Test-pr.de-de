---
title: 'Bereit. v. Topol. m. mehr. Gesamtstr. für Exchange 2013: Exchange 2013-Hilfe'
TOCTitle: Bereitstellen von Topologien mit mehreren Gesamtstrukturen für Exchange 2013
ms:assetid: d51f2b7d-9045-40cf-8b9f-43787a6fff6d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124734(v=EXCHG.150)
ms:contentKeyID: 51409351
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Bereitstellen von Topologien mit mehreren Gesamtstrukturen für Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In diesem Thema wird eine Übersicht über die Bereitstellung von Microsoft Exchange Server 2013 in Topologien mit mehreren Gesamtstrukturen bereitgestellt. Es enthält Informationen zu den folgenden Themen:

  - **Unterstützte Topologien mit mehreren Gesamtstrukturen**   Exchange 2013 unterstützt zwei Arten von Topologien mit mehreren Gesamtstrukturen: Gesamtstrukturübergreifende und Ressourcengesamtstrukturen.

  - **GAL-Synchronisierung**   Wenn Sie über eine gesamtstrukturübergreifende Umgebung verfügen, müssen Sie sicherstellen, dass die globale Adressliste in jeder Gesamtstruktur E-Mail-Empfänger aus anderen Gesamtstrukturen umfasst.

  - **Verschieben von Postfächern zwischen Gesamtstrukturen**    Die Cmdlets **New-MoveRequest** und **New-MigrationBatch** in der Exchange-Verwaltungsshell können zum Verschieben von Postfächern zwischen Gesamtstrukturen verwendet werden.

  - **Grundlegendes zur Verwaltung mehrerer Gesamtstrukturen**   Eine Beschreibung des Berechtigungsmodells, um die Berechtigungen innerhalb Ihrer Gesamtstrukturen konfigurieren und verwalten zu können.

## Unterstützte Topologien mit mehreren Gesamtstrukturen

Exchange 2013 unterstützt die folgenden Typen von Topologien mit mehreren Gesamtstrukturen:

  - **Gesamtstrukturübergreifend**   Eine gesamtstrukturübergreifende Topologie besteht aus mehreren Exchange-Gesamtstrukturen. Es folgt eine Übersicht der Aufgaben zum Bereitstellen von Exchange 2013 in einer Topologie mit mehreren Gesamtstrukturen:
    
    1.  Zunächst muss in jeder Gesamtstruktur Exchange 2013 installiert werden. Weitere Informationen finden Sie unter [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md).
    
    2.  Als nächstes müssen die Empfänger in jeder der Gesamtstrukturen so synchronisiert werden, dass die globale Adressliste (GAL) in jeder Gesamtstruktur Benutzer aus allen synchronisierten Gesamtstrukturen enthält. Ausführliche Informationen finden Sie im Abschnitt "GAL-Synchronisierung" weiter unten.
    
    3.  Schließlich muss der Verfügbarkeitsdienst so konfiguriert werden, dass Benutzer in einer Gesamtstruktur Verfügbarkeitsdaten von Benutzern in einer anderen Gesamtstruktur anzeigen können. Weitere Informationen finden Sie unter [Konfigurieren des Verfügbarkeitsdiensts für gesamtstrukturübergreifende Topologien](configure-the-availability-service-for-cross-forest-topologies-exchange-2013-help.md).
    
    Weitere Informationen zum Bereitstellen von Exchange 2013 in einer gesamtstrukturübergreifenden Topologie finden Sie unter [Bereitstellen von Exchange 2013 in einer gesamtstrukturübergreifenden Topologie](deploy-exchange-2013-in-a-cross-forest-topology-exchange-2013-help.md).

  - **Ressourcengesamtstruktur**   Eine Ressourcengesamtstruktur besteht aus einer Exchange-Gesamtstruktur und mindestens einer Benutzerkontengesamtstruktur. Es folgt eine Übersicht der Aufgaben zum Bereitstellen von Exchange 2013 in einer Topologie mit einer Ressourcengesamtstruktur:
    
    1.  Es muss eine Gesamtstruktur vorhanden sein, in der Exchange installiert ist. In der Exchange-Gesamtstruktur müssen die Benutzerkonten mit Exchange-Postfächern deaktiviert sein.
    
    2.  Sie müssen über mindestens eine Gesamtstruktur mit Benutzerkonten verfügen. In dieser Gesamtstruktur sollte Exchange*nicht* installiert sein.
    
    3.  Danach müssen die deaktivierten Benutzerkonten in der Exchange-Gesamtstruktur den Benutzerkonten in der Kontengesamtstruktur zugeordnet werden.
    
    Weitere Informationen zum Bereitstellen von Exchange 2013 in einer Topologie mit Ressourcengesamtstruktur finden Sie unter [Bereitstellen von Exchange 5.113,02 cm einer Exchange-Ressourcengesamtstruktur-Topologie](deploy-exchange-2013-in-an-exchange-resource-forest-topology-exchange-2013-help.md).

## GAL-Synchronisierung

Standardmäßig enthält eine GAL die E-Mail-Empfänger aus einer einzelnen Gesamtstruktur. Wenn Sie über eine gesamtstrukturübergreifende Umgebung verfügen, wird die Verwendung von Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1) empfohlen, um sicherzustellen, dass jede Gesamtstruktur über E-Mail-Empfänger aus anderen Gesamtstrukturen verfügt. ILM 2007 FP1 erstellt E-Mail-Benutzer, die Empfängern aus anderen Gesamtstrukturen entsprechen. Dadurch können die Benutzer diese Kontakte in der GAL anzeigen und Nachrichten an diese senden. Beispielsweise werden Benutzer der Gesamtstruktur A in der Gesamtstruktur B als E-Mail-Benutzer angegeben und umgekehrt. Benutzer der Zielgesamtstruktur können zum Senden einer Nachricht das E-Mail-Benutzerobjekt auswählen, das einen Empfänger einer anderen Gesamtstruktur darstellt.

Erstellen Sie zum Aktivieren der GAL-Synchronisierung Verwaltungs-Agents, die E-Mail-aktivierte Benutzer, Kontakte und Gruppen aus den angegebenen Active Directory-Diensten in ein zentrales Metaverzeichnis importieren. Im Metaverzeichnis werden die E-Mail-aktivierten Objekte als E-Mail-Benutzer dargestellt. Gruppen werden als Kontakte ohne zugeordnete Mitgliedschaft dargestellt. Anschließend exportieren die Verwaltungs-Agents diese E-Mail-Benutzer in eine Organisationseinheit in der angegebenen Zielgesamtstruktur.

Weitere Informationen zu Forefront Identity Manager (FIM) finden Sie unter [Forefront Identity Manager 2010](https://go.microsoft.com/fwlink/p/?linkid=279864).

## Verschieben von Postfächern zwischen Gesamtstrukturen

In einer gesamtstrukturübergreifenden Topologie möchten Sie möglicherweise Postfächer von einer Gesamtstruktur in die andere verschieben. Hierzu müssen Sie das Cmdlet **New-MoveRequest** oder **New-MigrationBatch** in der Exchange-Verwaltungsshell verwenden. Weitere Informationen zum Verschieben von Postfächern zwischen Gesamtstrukturen finden Sie unter den folgenden Themen:

  - [Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungsanforderungen](prepare-mailboxes-for-cross-forest-move-requests-exchange-2013-help.md)

  - [Vorbereiten von Postfächern für eine standortübergreifende Verschiebung mit dem Skript „Prepare-MoveRequest.ps1“ in der Shell](prepare-mailboxes-for-cross-forest-moves-using-the-prepare-moverequest-ps1-script-in-the-shell-exchange-2013-help.md)

  - [Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungen unter Verwendung von Beispielcode](prepare-mailboxes-for-cross-forest-moves-using-sample-code-exchange-2013-help.md)

## Grundlegendes zur Verwaltung mehrerer Gesamtstrukturen

Exchange 2013 verwendet zum Verwalten Ihrer Umgebungen mit mehreren Gesamtstrukturen neue Berechtigungsfunktionen.

Exchange 2013 verwendet ein Berechtigungsmodell für die rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC). Die Verwaltungsrollengruppen, denen Administratoren angehören, sowie die Zuweisungsrichtlinien für Verwaltungsrollen, denen Endbenutzer zugeordnet sind, bestimmen, welche Aufgaben Administratoren und Endbenutzer ausführen können. Um Berechtigungen für mehrere Gesamtstrukturen verstehen zu können, müssen Sie mit dem RBAC-Modell vertraut sein. Weitere Informationen zu RBAC, Rollengruppen und Rollenzuweisungsrichtlinien finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

Das Berechtigungsmodell für die rollenbasierte Zugriffssteuerung kann zum Konfigurieren und Verwalten der Berechtigungen innerhalb Ihrer Gesamtstrukturen verwendet werden. Weitere Informationen zu Berechtigungen innerhalb mehrerer Gesamtstrukturen finden Sie unter den folgenden Themen:

  - [Grundlegendes zu Berechtigungen für mehrere Gesamtstrukturen](understanding-multiple-forest-permissions-exchange-2013-help.md)

  - [Verwalten von verknüpften Rollengruppen](manage-linked-role-groups-exchange-2013-help.md)

  - [Erstellen verknüpfter Rollengruppen, die integrierte Rollengruppen spiegeln](create-linked-role-groups-that-mirror-built-in-role-groups-exchange-2013-help.md)


---
title: 'Dial Tone-Portabilität: Exchange 2013 Help'
TOCTitle: Dial Tone-Portabilität
ms:assetid: ea62fae0-5e0a-460c-beb6-52532c8c8dbc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876950(v=EXCHG.150)
ms:contentKeyID: 51409359
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Dial Tone-Portabilität

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-01-28_

Die Microsoft Exchange Server 2013-Funktion der Dial Tone-Portabilität bietet eine eingeschränkte Geschäftskontinuitätslösung für Ausfälle, die sich auf eine Postfachdatenbank, einen Server oder einen ganzen Standort auswirken. Durch die Dial Tone-Portabilität erhalten Benutzer die Möglichkeit, ein temporäres Postfach zum Senden und Empfangen von E-Mails zu nutzen, während ihr ursprüngliches Postfach wiederhergestellt oder repariert wird. Das temporäre Postfach kann sich auf demselben Exchange 2013-Postfachserver oder auf einem beliebigen anderen Exchange 2013-Postfachserver innerhalb der Organisation befinden, auf dem Datenbanken mit derselben Datenbankschemaversion verwendet werden. Somit kann ein alternativer Server die Postfächer von Benutzern hosten, die sich zuvor auf einem anderen Server befunden haben, der jetzt nicht mehr verfügbar ist. Clients mit Unterstützung für AutoErmittlung werden automatisch auf den neuen Server umgeleitet, ohne dass das Desktopprofil des Benutzers manuell aktualisiert werden muss. Nach der Wiederherstellung der eigentlichen Postfachdaten des Benutzers kann ein Administrator das wiederhergestellte Postfach und das Dial Tone-Postfach des Benutzers in ein einziges, aktuelles Postfach zusammenführen.

Das Verfahren zur Verwendung der Dial Tone-Portabilität wird als *Dial Tone-Wiederherstellung* bezeichnet. Eine Dial Tone-Wiederherstellung umfasst das Erstellen einer leeren Datenbank auf einem Postfachserver, um eine fehlerhafte Datenbank zu ersetzen. Mithilfe dieser leeren Datenbank, die auch als *Dial Tone-Datenbank* bezeichnet wird, können Benutzer E-Mails senden und empfangen, während die fehlerhafte Datenbank wiederhergestellt wird.

Zur Durchführung einer Dial Tone-Wiederherstellung gibt es drei Optionen:

  - **Dial Tone-Wiederherstellung auf dem Server mit der ausgefallenen Datenbank**   Wenn der Server, der die ausgefallene Datenbank hostet, noch funktioniert, empfiehlt es sich, eine Dial Tone-Wiederherstellung auf diesem Server durchzuführen. Das bedeutet weniger Ausfallzeit, weil Sie keine Datenbankdateien zwischen Servern verschieben müssen. Zusätzlich müssen Sie keine Messagingprofile für Clients neu konfigurieren, die die AutoErmittlung nicht unterstützen.

  - **Dial Tone-Wiederherstellung mithilfe eines anderen Servers für die Dial Tone-Datenbank**   Wenn ein Server ausfällt und neu eingerichtet werden muss, besteht die effizienteste Methode zum Bereitstellen einer grundlegenden E-Mail-Funktionalität für Benutzer darin, eine Dial Tone-Datenbank auf einem anderen Server zu erstellen und die Postfachkonfiguration der Benutzer anhand der Datenbankportabilität auf diesen neuen Server zu verschieben. Da dieser Prozess das Verschieben der Dial Tone-Datenbank zurück auf den ursprünglichen (wiederhergestellten) Server umfasst, dauert der Wiederherstellungsprozess bei dieser Option insgesamt länger. Dieser Vorgang ist zudem komplexer als eine Dial Tone-Wiederherstellung auf dem ursprünglichen Server. Wenn dieser Vorgang ausgeführt wird, muss der Server mit der Datenbank für Freizeichen über ausreichend Ressourcen verfügen, um die Last der zusätzlichen Benutzer zu unterstützen. Wenn AutoErmittlung vom Client des Benutzers nicht unterstützt wird, muss das entsprechende Messagingprofil zudem so neu konfiguriert werden, dass auf den Server für Freizeichen verwiesen wird.

  - **Dial Tone-Wiederherstellung mithilfe eines anderen Servers für die Dial Tone-Datenbank, auf dem diese anschließend verbleibt**   Diese Option ähnelt der vorherigen Option, außer dass sie die Datenbank nicht auf den ursprünglichen Server zurück verschieben. Diese Option empfiehlt sich in Situationen, in denen der ausgefallene Server nicht wiederhergestellt werden kann. In diesem Szenario verbleiben Benutzer nach Abschluss der Wiederherstellung normalerweise auf einem anderen Server. Wenn dieser Vorgang ausgeführt wird, muss der Server mit der Datenbank für Freizeichen über ausreichend Ressourcen verfügen, um die Last der zusätzlichen Benutzer zu unterstützen. Wenn AutoErmittlung vom Client des Benutzers nicht unterstützt wird, muss das entsprechende Messagingprofil zudem so neu konfiguriert werden, dass auf den Server für Freizeichen verwiesen wird.

Alle drei Optionen basieren auf denselben grundlegenden Schritten:

1.  **Erstellen Sie eine leere Dial Tone-Datenbank, um die fehlerhafte Datenbank zu ersetzen.**
    
    Diese neue Datenbank ermöglicht Benutzern mit Postfächern auf der fehlerhaften Datenbank das Senden und Empfangen neuer Nachrichten. Die Dial Tone-Portabilität ermöglicht Ihnen das Umleiten eines Benutzers an eine andere Datenbank, ohne das Postfach zu verschieben. Wenn Sie die Dial Tone-Datenbank auf einem anderen Server als dem Server erstellt haben, auf dem die fehlerhafte Datenbank gespeichert war, müssen Sie die Postfachkonfiguration auf diesen neuen Server verschieben.

2.  **Stellen Sie die alte Datenbank wieder her.**
    
    Verwenden Sie Ihre übliche Software zur Sicherung und Wiederherstellung, um die ausgefallene Datenbank wiederherzustellen. Wenn keine Sicherung der fehlerhaften Datenbank vorhanden ist, stellen Sie die fehlerhafte Datenbank nach Möglichkeit auf andere Weise wieder her. Wenn Sie denselben Server für die Dial Tone-Wiederherstellung verwenden, müssen Sie die Datenbank in einer Wiederherstellungsdatenbank wiederherstellen.

3.  **Tauschen Sie die Dial Tone-Datenbank gegen die wiederhergestellte Datenbank aus.**
    
    Nach der Wiederherstellung der ausgefallenen Datenbank tauschen Sie diese mit der Dial Tone-Datenbank aus. Auf diese Weise erhalten Benutzer die Möglichkeit, E-Mail zu senden und zu empfangen und auf alle Daten in der wiederhergestellten Datenbank zuzugreifen. Wenn Benutzer in eine Dial Tone-Datenbank auf einem anderen Server verschoben wurden, müssen Sie die Postfachkonfiguration zurück auf den ursprünglichen Server verschieben.

4.  **Führen Sie die Datenbanken zusammen.**
    
    Um die Daten aus der Dial Tone-Datenbank in die wiederhergestellte Datenbank zu integrieren, führen Sie die Daten über das [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\))-Cmdlet zusammen.

Genaue Anweisungen zum Durchführen einer Dial Tone-Wiederherstellung finden Sie unter [Durchführen einer "Dial Tone"-Wiederherstellung](perform-a-dial-tone-recovery-exchange-2013-help.md).


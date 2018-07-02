---
title: 'Installieren von Exchange 2013 mithilfe des Setup-Assistenten: Exchange 2013 Help'
TOCTitle: Installieren von Exchange 2013 mithilfe des Setup-Assistenten
ms:assetid: da690d47-3384-4430-a69e-0cd4d3bf80a7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124778(v=EXCHG.150)
ms:contentKeyID: 50476875
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.ExSetupUI.SetupWizardForm.IntroductionPage
ms.translationtype: HT
---

# Installieren von Exchange 2013 mithilfe des Setup-Assistenten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-19_

In diesem Thema wird erläutert, wie die Exchange 2013-Postfachrolle und -Clientzugriffsrolle mithilfe des Microsoft Exchange Server 2013-Setup-Assistenten auf einem Computer installiert werden. Weitere Informationen zur Planung und Bereitstellung von Exchange 2013 finden Sie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md).

Wenn Sie die Exchange 2013-Edge-Transportrolle auf einem Computer installieren möchten, lesen Sie [Installieren der Exchange 2013-Edge-Transportrolle mithilfe des Setup-Assistenten](install-the-exchange-2013-edge-transport-role-using-the-setup-wizard-exchange-2013-help.md). Die Edge-Transportrolle kann nicht auf dem gleichen Computer wie die Postfach- oder Clientzugriffs-Serverrollen installiert werden.


> [!TIP]
> Kennen Sie schon den Bereitstellungs-Assistent für Exchange&nbsp;Server? Es handelt sich dabei um ein kostenloses Onlinetool, mit dem Sie Exchange 2013 schnell und einfach in Ihrem Unternehmen bereitstellen können, indem Sie einige Fragen beantworten und es eine Checklist für die Bereitstellung für Sie erstellt. Weitere Informationen finden Sie unter <A href="exchange-server-deployment-assistant-exchange-2013-help.md">Exchange Server-Bereitstellungs-Assistent</A>.




> [!NOTE]
> Nachdem Sie Serverrollen auf einem Computer mit exExchange2k13 installiert haben, können Sie nicht den exExchange2k13-Installationsassistenten verwenden, um dem gleichen Computer weitere Serverrollen hinzuzufügen. Wenn Sie einem Computer weitere Serverrollen hinzufügen möchten, müssen Sie entweder die Funktion Software in der Systemsteuerung verwenden oder "Setup.exe" in einem Eingabeaufforderungsfenster ausführen.



Weitere Informationen zu Aufgaben, die nach der Installation auszuführen sind, finden Sie unter [Aufgaben nach der Installation von Exchange 2013](exchange-2013-post-installation-tasks-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 60 Minuten

  - Lesen Sie vor der Installation von Exchange 2013 in jedem Fall die Versionshinweise. Weitere Informationen finden Sie unter [Versionshinweise zu Exchange 2013](release-notes-for-exchange-2013-exchange-2013-help.md).

  - Jede Organisation erfordert mindestens einen Clientzugriffsserver und einen Postfachserver in der Active Directory-Gesamtstruktur. Jeder Active Directory-Standort, der einen Postfachserver umfasst, muss zudem auch mindestens einen Clientzugriffsserver aufweisen. Wenn Sie die Serverrollen trennen, empfiehlt es sich, zuerst die Postfachserverrolle zu installieren.

  - Der Computer, auf dem Sie Exchange 2013 installieren, muss über ein unterstütztes Betriebssystem verfügen (beispielsweise Windows Server 2008 R2 mit Service Pack 1 (SP1) oder Windows Server 2012), genügend freien Festplattenspeicher aufweisen, ein Mitglied einer Active Directory-Domäne sein und weitere Anforderungen erfüllen. Weitere Informationen zu den Systemanforderungen finden Sie unter [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md).

  - Um Exchange 2013-Setup auszuführen, müssen Sie Microsoft .NET Framework 4.5, Windows Management Framework 3.0 und sonstige erforderliche Software installieren. Informationen zu den Voraussetzungen für alle Serverrollen finden Sie unter [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

  - Sie müssen sicherstellen, dass die Mitgliedschaft in der Gruppe Schema-Admins dem verwendeten Konto zugewiesen wurde, wenn Sie das exADNoMk-Schema nicht zuvor vorbereitet haben. Wenn Sie den ersten exExchange2k13-Server in der Organisation installieren, muss das verwendete Konto Mitglied der Gruppe Organisations-Admins sein. Wenn Sie das Schema bereits vorbereitet haben und nicht den ersten Server mit exExchange2k13 in der Organisation installieren, muss das verwendete Konto Mitglied der exExchange2k13-Rollengruppe "Organisationsverwaltung" sein.
    
    Administratoren, die Mitglied der Rollengruppe "Delegiertes Setup" sind, können Exchange 2013-Server bereitstellen, die zuvor durch ein Mitglied der Verwaltungsrollengruppe "Organisationsverwaltung" bereitgestellt wurden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Nach der Installation von Exchange auf einem Server muss der Servername nicht geändert werden. Das Umbenennen eines Servers nach der Installation einer Exchange-Serverrolle wird nicht unterstützt.



## Installieren von Exchange Server 2013

Wenn Sie den ersten Exchange 2013-Server in der Organisation installieren und die Active Directory-Vorbereitungsschritte nicht durchgeführt wurden, muss das verwendete Konto Mitglied der Gruppe "Organisationsadministratoren" sein. Wenn Sie das Active Directory-Schema noch nicht vorbereitet haben, muss das Konto außerdem Mitglied der Gruppe "Schema-Admins" sein. Informationen zum Vorbereiten von Active Directory für Exchange 2013 finden Sie unter [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md). Wenn Sie die Schritte zur Vorbereitung von Schema und Active Directory bereits durchgeführt haben, muss das verwendete Konto Mitglied der Verwaltungsrolle "Delegiertes Setup" oder der Rollengruppe "Organisationsverwaltung" sein.


> [!NOTE]
> Die aktuelle Version von Exchange 2013 zum Herunterladen finden Sie unter <A href="updates-for-exchange-2013-exchange-2013-help.md">Updates für Exchange 2013</A>.



1.  Melden Sie sich an dem Computer an, auf dem Exchange 2013 installiert werden soll.

2.  Navigieren Sie zum Netzwerkspeicherort der Exchange 2013-Installationsdateien.

3.  Starten von Exchange 2013-Setup durch Doppelklicken auf `Setup.exe`
    

    > [!IMPORTANT]
    > Wenn die Benutzerzugriffssteuerung aktiviert ist, klicken Sie mit der rechten Maustaste auf <CODE>Setup.exe</CODE>, und wählen Sie <STRONG>Als Administrator ausführen</STRONG> aus.



4.  Legen Sie auf der Seite **Soll nach Updates gesucht werden?** fest, ob eine Verbindung mit dem Internet hergestellt werden soll und Produkt- und Sicherheitsupdates für Exchange 2013 heruntergeladen werden sollen. Wenn Sie **Verbindung mit dem Internet herstellen und nach Updates suchen** auswählen, werden Updates heruntergeladen und angewendet, bevor der Vorgang fortgesetzt wird. Wenn Sie die Option **Jetzt nicht nach Updates suchen** auswählen, können Sie die Updates später manuell herunterladen und installieren. Wir empfehlen, die Updates jetzt herunterzuladen und zu installieren. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

5.  
    
    Die Installation von Exchange in Ihrer Organisation beginnt mit der Seite **Einführung**. Sie werden durch die Installation geleitet. Es werden mehrere Links zu hilfreichem Inhalt zu Bereitstellungen aufgelistet. Es wird empfohlen, dass Sie diese Links aufrufen, bevor Sie Setup fortsetzen. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

6.  
    
    Lesen Sie die auf der Seite **Lizenzvertrag** angezeigten Lizenzbedingungen für die Software. Wenn Sie den Bedingungen zustimmen, wählen Sie **Ich stimme den Bedingungen des Lizenzvertrags zu**, und klicken Sie auf **Weiter**.

7.  
    
    Legen Sie auf der Seite **Empfohlene Einstellungen** fest, ob die empfohlenen Einstellungen verwendet werden sollen. Wenn Sie **Empfohlene Einstellungen verwenden** auswählen, sendet Exchange an Microsoft automatisch Fehlerberichte und Informationen zu Ihrer Computerhardware sowie zur Verwendung von Exchange. Wenn Sie **Empfohlene Einstellungen nicht verwenden** auswählen, bleiben diese Einstellungen deaktiviert; Sie können sie jedoch jederzeit nach Abschluss von Setup aktivieren. Weitere Informationen zu diesen Einstellungen und dazu, wie an Microsoft gesendete Informationen verwendet werden, erhalten Sie durch Klicken auf **?**.

8.  
    
    Wählen Sie auf der Seite **Serverrollenauswahl** aus, ob die **Postfachrolle**, die **Clientzugriffsrolle**, beide Rollen oder nur die **Verwaltungstools** auf diesem Computer installiert werden sollen. Sie können später weitere Serverrollen hinzufügen, wenn Sie diese jetzt nicht installieren. Für eine Organisation muss mindestens eine Postfachrolle und mindestens eine Clientzugriffs-Serverrolle installiert sein. Sie können auf demselben Computer oder auf getrennten Computern installiert werden. Die Verwaltungstools werden bei der Installation jeder anderen Serverrolle automatisch installiert.
    
    Wählen Sie **Für die Installation von Exchange Server erforderliche Windows Server-Rollen und -Funktionen automatisch installieren** aus, damit alle erforderlichen Windows-Voraussetzungen installiert werden. Möglicherweise müssen Sie den Computer neu starten, um die Installation einiger Windows-Funktionen abzuschließen. Wenn Sie diese Option nicht aktivieren, müssen Sie die Windows-Funktionen manuell installieren.
    

    > [!NOTE]
    > Diese Option installiert nur die Windows-Funktionen, die für Exchange erforderlich sind. Weitere Komponenten zur Erfüllung der Voraussetzungen müssen Sie manuell installieren. Weitere Informationen finden Sie unter <A href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</A>.

    
    Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

9.  Übernehmen Sie auf der Seite **Speicherplatz und Speicherort der Installation** den vorgegebenen Installationspfad, oder klicken Sie auf **Durchsuchen**, um einen anderen Installationspfad auszuwählen. Vergewissern Sie sich, dass der Pfad, unter dem Sie Exchange installieren möchten, ausreichend Speicherplatz aufweist. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

10. 
    
    Wenn es sich um den ersten Exchange-Server in Ihrer Organisation handelt, geben Sie auf der Seite **Exchange-Organisation** einen Namen für Ihre Exchange-Organisation ein. Der Name der Exchange-Organisation darf nur die folgenden Zeichen enthalten:
    
      - A bis Z
    
      - a bis z
    
      - 0 bis 9
    
      - Leerzeichen (weder führend noch nachgestellt)
    
      - Bindestrich/Gedankenstrich
        

        > [!NOTE]
        > Der Name der Organisation darf maximal 64 Zeichen enthalten. und er darf nicht leer sein.

    
    Wenn Sie das Modell mit geteilten Berechtigungen von Active Directory verwenden möchten, wählen Sie **Sicherheitsmodell mit geteilten Berechtigungen von Active Directory auf die Exchange-Organisation anwenden** aus.
    

    > [!WARNING]
    > Für die meisten Organisationen ist es nicht erforderlich, das Modell mit geteilten Berechtigungen von Active Directory anzuwenden. Wenn Sie die Verwaltung von Active Directory-Sicherheitsprinzipalen und Exchange-Konfiguration voneinander trennen möchten, können Sie ggf. die geteilten Berechtigungen für die rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC) verwenden. Weitere Informationen erhalten Sie durch Klicken auf <STRONG>?</STRONG>.

    
    Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

11. Wenn Sie die Postfachrolle installieren, legen Sie auf der Seite **Einstellungen zum Schutz vor Schadsoftware** fest, ob die Prüfung auf Schadsoftware aktiviert oder deaktiviert werden soll. Wenn Sie die Prüfung auf Schadsoftware jetzt deaktivieren, können Sie sie später jederzeit wieder aktivieren. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

12. 
    
    Überprüfen Sie auf der Seite **Abschließende Überprüfung** den Status, um zu ermitteln, ob die Überprüfung der Voraussetzungen für die Organisation und die Serverrollen erfolgreich abgeschlossen wurde. Wenn sie nicht erfolgreich abgeschlossen wurden, müssen Sie gemeldete Fehler beheben, bevor Sie Exchange 2013 installieren können. Es ist nicht erforderlich, das Setup zu beenden, um Fehler im Zusammenhang mit Voraussetzungen zu beseitigen. Klicken Sie nach dem Beheben eines gemeldeten Fehlers auf **Zurück**, und klicken Sie dann auf **Weiter**, um die Überprüfung der Voraussetzungen erneut auszuführen. Überprüfen Sie auch alle gemeldeten Warnungen. Wenn alle Überprüfungen der Bereitschaft erfolgreich abgeschlossen wurden, klicken Sie auf **Weiter**, um die Installation von Exchange 2013 zu starten.

13. 
    
    Klicken Sie auf der Seite **Fertigstellung** auf **Fertig stellen**.

14. Starten Sie den Computer nach Abschluss der Exchange 2013-Installation neu.

15. Schließen Sie Ihre Bereitstellung ab, indem Sie die unter [Aufgaben nach der Installation von Exchange 2013](exchange-2013-post-installation-tasks-exchange-2013-help.md) beschriebenen Aufgaben durchführen.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Informationen dazu, wie Sie überprüfen, ob die Installation von Exchange 2013 erfolgreich abgeschlossen wurde, finden Sie unter [Überprüfen einer Exchange 2013-Installation](verify-an-exchange-2013-installation-exchange-2013-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.


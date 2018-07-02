---
title: 'Installieren der Exchange 2013-Edge-Transportrolle mithilfe des Setup-Assistenten: Exchange 2013 Help'
TOCTitle: Installieren der Exchange 2013-Edge-Transportrolle mithilfe des Setup-Assistenten
ms:assetid: b8e51b0b-201e-4c64-92c8-3ac0db04b6e2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn635117(v=EXCHG.150)
ms:contentKeyID: 61201343
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Installieren der Exchange 2013-Edge-Transportrolle mithilfe des Setup-Assistenten

 

_**Gilt für:** Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-19_

In diesem Thema wird erläutert, wie die Exchange 2013-Edge-Transport-Serverrolle mithilfe des Microsoft Exchange Server 2013-Setup-Assistenten auf einem Computer installiert wird. Die Edge-Transportrolle ist mit Exchange 2013 Service Pack 1 (SP1) oder höher verfügbar. Weitere Informationen zur Planung und Bereitstellung von Exchange 2013 finden Sie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md).

Wir empfehlen, die Edge-Transportrolle in einem Umkreisnetzwerk außerhalb der internen Active Directory-Gesamtstruktur Ihrer Organisation zu installieren. Sie können die Edge-Transport-Serverrolle zwar auf einem der Domäne beigetretenen Computer installieren. Allerdings wird dadurch aber nur die Domänenverwaltung von Windows-Funktionen und -Einstellungen aktiviert. Die Edge-Transportrolle selbst verwendet Active Directory nicht. Sie verwendet stattdessen das Active Directory Lightweight Directory Services (AD LDS) Windows-Feature, um Konfiguration- und Empfängerinformationen zu speichern. Weitere Informationen zur Edge-Transportrolle finden Sie unter [Edge-Transport-Server](edge-transport-servers-exchange-2013-help.md).

Wenn Sie die Exchange 2013-Postfachrolle oder -Clientzugriffsrolle auf einem Computer installieren möchten, lesen Sie [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md). Die Edge-Transportrolle kann nicht auf dem gleichen Computer wie die Postfach- oder Clientzugriffs-Serverrollen installiert werden.


> [!TIP]
> Kennen Sie schon den Bereitstellungs-Assistent für Exchange&nbsp;Server? Es handelt sich dabei um ein kostenloses Onlinetool, mit dem Sie Exchange 2013 schnell und einfach in Ihrem Unternehmen bereitstellen können, indem Sie einige Fragen beantworten und es eine Checklist für die Bereitstellung für Sie erstellt. Weitere Informationen finden Sie unter <A href="exchange-server-deployment-assistant-exchange-2013-help.md">Exchange Server-Bereitstellungs-Assistent</A>.



Weitere Informationen zu Aufgaben, die nach der Installation auszuführen sind, finden Sie unter [Aufgaben nach der Installation von Exchange 2013](exchange-2013-post-installation-tasks-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 40 Minuten

  - Lesen Sie vor der Installation von Exchange 2013 in jedem Fall die Versionshinweise. Weitere Informationen finden Sie unter [Versionshinweise zu Exchange 2013](release-notes-for-exchange-2013-exchange-2013-help.md).

  - Der Computer, auf dem Sie Exchange 2013 installieren, muss über ein unterstütztes Betriebssystem (wie Windows Server 2008 R2 mit SP1, Windows Server 2012 R2 oder Windows Server 2012) und ausreichend Speicherplatz verfügen und andere Anforderungen erfüllen. Weitere Informationen zu den Systemanforderungen finden Sie unter [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md).

  - Um Exchange 2013-Setup auszuführen, müssen Sie Microsoft .NET Framework 4.5, Windows Management Framework und sonstige erforderliche Software installieren. Informationen zu den Voraussetzungen für alle Serverrollen finden Sie unter [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

  - Sie müssen das primäre DNS-Suffix auf dem Computer konfigurieren. Wenn der vollständig qualifizierte Domänenname Ihres Computers z. B. "edge.contoso.com" lautet, lautet das DNS-Suffix für den Computer "contoso.com". Weitere Informationen finden Sie unter [Primäres DNS-Suffix fehlt](primary-dns-suffix-is-missing-exchange-2013-help.md).

  - Exchange 2007- und Exchange 2010-Hub-Transport-Server müssen aktualisiert werden, bevor Sie ein EdgeSync-Abonnement zwischen diesen und einem Exchange 2013-Edge-Transport-Server erstellen können. Wenn Sie dieses Update nicht installieren, funktioniert das EdgeSync-Abonnement nicht ordnungsgemäß. Weitere Informationen finden Sie im Abschnitt "Unterstützte Koexistenzszenarien" in [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md).

  - Stellen Sie sicher, dass das von Ihnen verwendete Konto Mitglied der lokalen Administratorengruppe auf dem Computer ist, auf dem Sie die Edge-Transportrolle installieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Nach der Installation von Exchange auf einem Server muss der Servername nicht geändert werden. Das Umbenennen eines Servers nach der Installation einer Exchange-Serverrolle wird nicht unterstützt.



## Installieren von Exchange Server 2013


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
    
    Wählen Sie auf der Seite **Auswahl von Serverrollen** die Option **Edge-Transport** aus. Beachten Sie hierbei, dass Sie einem Computer, auf dem die Edge-Transport-Rolle installiert ist, keine Postfach- oder Clientzugriffsserver-Rollen hinzufügen können. Die Verwaltungstools werden bei der Installation jeder anderen Serverrolle automatisch installiert.
    
    Wählen Sie **Für die Installation von Exchange Server erforderliche Windows Server-Rollen und -Funktionen automatisch installieren** aus, damit alle erforderlichen Windows-Voraussetzungen installiert werden. Möglicherweise müssen Sie den Computer neu starten, um die Installation einiger Windows-Funktionen abzuschließen. Wenn Sie diese Option nicht aktivieren, müssen Sie die Windows-Funktionen manuell installieren.
    

    > [!NOTE]
    > Diese Option installiert nur die Windows-Funktionen, die für Exchange erforderlich sind. Weitere Komponenten zur Erfüllung der Voraussetzungen müssen Sie manuell installieren. Weitere Informationen finden Sie unter <A href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</A>.

    
    Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

9.  Übernehmen Sie auf der Seite **Speicherplatz und Speicherort der Installation** den vorgegebenen Installationspfad, oder klicken Sie auf **Durchsuchen**, um einen anderen Installationspfad auszuwählen. Vergewissern Sie sich, dass der Pfad, unter dem Sie Exchange installieren möchten, ausreichend Speicherplatz aufweist. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

10. 
    
    Überprüfen Sie auf der Seite **Abschließende Überprüfung** den Status, um zu ermitteln, ob die Überprüfung der Voraussetzungen für die Organisation und die Serverrollen erfolgreich abgeschlossen wurde. Wenn sie nicht erfolgreich abgeschlossen wurden, müssen Sie gemeldete Fehler beheben, bevor Sie Exchange 2013 installieren können. Es ist nicht erforderlich, das Setup zu beenden, um Fehler im Zusammenhang mit Voraussetzungen zu beseitigen. Klicken Sie nach dem Beheben eines gemeldeten Fehlers auf **Zurück**, und klicken Sie dann auf **Weiter**, um die Überprüfung der Voraussetzungen erneut auszuführen. Überprüfen Sie auch alle gemeldeten Warnungen. Wenn alle Überprüfungen der Bereitschaft erfolgreich abgeschlossen wurden, klicken Sie auf **Weiter**, um die Installation von Exchange 2013 zu starten.

11. 
    
    Klicken Sie auf der Seite **Fertigstellung** auf **Fertig stellen**.

12. Starten Sie den Computer nach Abschluss der Exchange 2013-Installation neu.

13. Schließen Sie Ihre Bereitstellung ab, indem Sie die unter [Aufgaben nach der Installation von Exchange 2013](exchange-2013-post-installation-tasks-exchange-2013-help.md) beschriebenen Aufgaben durchführen.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Informationen dazu, wie Sie überprüfen, ob die Installation von Exchange 2013 erfolgreich abgeschlossen wurde, finden Sie unter [Überprüfen einer Exchange 2013-Installation](verify-an-exchange-2013-installation-exchange-2013-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.


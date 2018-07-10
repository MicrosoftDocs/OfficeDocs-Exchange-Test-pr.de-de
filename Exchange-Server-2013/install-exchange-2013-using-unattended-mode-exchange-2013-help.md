---
title: 'Installieren von Exchange 2013 im unbeaufsichtigten Modus: Exchange 2013 Help'
TOCTitle: Installieren von Exchange 2013 im unbeaufsichtigten Modus
ms:assetid: 386465e9-41da-4e26-9816-b3b69be1f8bf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997281(v=EXCHG.150)
ms:contentKeyID: 50475482
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Installieren von Exchange 2013 im unbeaufsichtigten Modus

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-19_

Zur Durchführung einer unbeaufsichtigten Installation müssen Sie Exchange Server 2013 über eine Eingabeaufforderung installieren. Weitere Informationen zur Planung und Bereitstellung von Exchange 2013 finden Sie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md).

Wir empfehlen, die Edge-Transport-Rolle in einem Umkreisnetzwerk außerhalb der internen Active Directory-Gesamtstruktur Ihrer Organisation zu installieren. Sie können die Edge-Transport-Serverrolle zwar auf einem der Domäne beigetretenen Computer installieren. Allerdings wird dadurch aber nur die Domänenverwaltung von Windows-Funktionen und -Einstellungen aktiviert. Die Edge-Transport-Rolle selbst verwendet Active Directory nicht. Sie verwendet stattdessen das Active Directory Lightweight Directory Services (AD LDS) Windows-Feature, um Konfigurations- und Empfängerinformationen zu speichern. Weitere Informationen zur Edge-Transportrolle finden Sie unter [Edge-Transport-Server](edge-transport-servers-exchange-2013-help.md).


> [!TIP]
> Kennen Sie schon den Bereitstellungs-Assistent für Exchange&nbsp;Server? Es handelt sich dabei um ein kostenloses Onlinetool, mit dem Sie Exchange 2013 schnell und einfach in Ihrem Unternehmen bereitstellen können, indem Sie einige Fragen beantworten und es eine Checklist für die Bereitstellung für Sie erstellt. Weitere Informationen finden Sie unter <A href="exchange-server-deployment-assistant-exchange-2013-help.md">Exchange Server-Bereitstellungs-Assistent</A>.




> [!NOTE]
> Nachdem Sie Serverrollen auf einem Computer mit Exchange 2013 installiert haben, können Sie nicht den Exchange 2013-Installationsassistenten verwenden, um dem gleichen Computer weitere Serverrollen hinzuzufügen. Wenn Sie einem Computer weitere Serverrollen hinzufügen möchten, müssen Sie entweder die Funktion <STRONG>Software</STRONG> in der Systemsteuerung verwenden oder "Setup.exe" in einem Eingabeaufforderungsfenster ausführen.<BR>Die Edge-Transportrolle kann nicht auf dem gleichen Computer wie die Postfach- oder Clientzugriffs-Serverrollen installiert werden.



Weitere Informationen zu Aufgaben, die nach der Installation auszuführen sind, finden Sie unter [Aufgaben nach der Installation von Exchange 2013](exchange-2013-post-installation-tasks-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

Die folgenden Informationen gelten für alle Exchange 2013 -Serverrollen.

  - Lesen Sie vor der Installation von Exchange 2013 in jedem Fall die Versionshinweise. Weitere Informationen finden Sie unter [Versionshinweise zu Exchange 2013](release-notes-for-exchange-2013-exchange-2013-help.md).

  - Der Computer, auf dem Sie Exchange 2013 installieren, muss über ein unterstütztes Betriebssystem (wie Windows Server 2008 R2 mit Service Pack 1 (SP1), Windows Server 2012 R2 oder Windows Server 2012) und ausreichend Speicherplatz verfügen und andere Anforderungen erfüllen. Weitere Informationen zu den Systemanforderungen finden Sie unter [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md).

  - Um Exchange 2013-Setup auszuführen, müssen Sie Microsoft .NET Framework 4.5, Windows Management Framework und sonstige erforderliche Software installieren. Informationen zu den Voraussetzungen für alle Serverrollen finden Sie unter [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Nach der Installation von Exchange auf einem Server muss der Servername nicht geändert werden. Das Umbenennen eines Servers nach der Installation einer Exchange-Serverrolle wird nicht unterstützt.



Die folgenden Informationen gelten für die Exchange 2013-Postfach- und Clientzugriffs-Serverrollen.

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 60 Minuten

  - Jede Organisation erfordert mindestens einen Clientzugriffsserver und einen Postfachserver in der Active Directory-Gesamtstruktur. Jeder Active Directory-Standort, der einen Postfachserver umfasst, muss zudem auch mindestens einen Clientzugriffsserver aufweisen. Wenn Sie die Serverrollen trennen, empfiehlt es sich, zuerst die Postfachserverrolle zu installieren.

  - Der Computer, auf dem Sie Exchange 2013 installieren, muss ein Mitglied einer Active Directory-Domäne sein.

  - Sie müssen sicherstellen, dass die Mitgliedschaft in der Gruppe **Schema-Admins** dem verwendeten Konto zugewiesen wurde, wenn Sie das Active Directory-Schema nicht zuvor vorbereitet haben. Wenn Sie den ersten Exchange 2013-Server in der Organisation installieren, muss das verwendete Konto Mitglied der Gruppe **Organisations-Admins** sein. Wenn Sie das Schema bereits vorbereitet haben und nicht den ersten Server mit Exchange 2013 in der Organisation installieren, muss das verwendete Konto Mitglied der Exchange 2013-Rollengruppe "Organisationsverwaltung" sein.
    
    Administratoren, die Mitglied der Rollengruppe "Delegiertes Setup" sind, können Exchange 2013-Server bereitstellen, die zuvor durch ein Mitglied der Rollengruppe "Organisationsverwaltung" bereitgestellt wurden.

Die folgenden Informationen gelten für die Exchange 2013-Edge-Transport-Serverrolle.

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 40 Minuten

  - Die Edge-Transport-Rolle ist mit Exchange 2013 SP1 oder höher verfügbar.

  - Sie müssen das primäre DNS-Suffix auf dem Computer konfigurieren. Wenn der vollständig qualifizierte Domänenname Ihres Computers z. B. "edge.contoso.com" lautet, lautet das DNS-Suffix für den Computer "contoso.com". Weitere Informationen finden Sie unter [Primäres DNS-Suffix fehlt](primary-dns-suffix-is-missing-exchange-2013-help.md).

  - Exchange 2007- und Exchange 2010-Hub-Transport-Server müssen aktualisiert werden, bevor Sie ein EdgeSync-Abonnement zwischen diesen und einem Exchange 2013-Edge-Transport-Server erstellen können. Wenn Sie dieses Update nicht installieren, funktioniert das EdgeSync-Abonnement nicht ordnungsgemäß. Weitere Informationen finden Sie im Abschnitt "Unterstützte Koexistenzszenarien" in [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md).

  - Stellen Sie sicher, dass das von Ihnen verwendete Konto Mitglied der lokalen Administratorengruppe auf dem Computer ist, auf dem Sie die Edge-Transport-Rolle installieren.

## Verwenden von "Setup.exe" zum Installieren von Exchange 2013 im unbeaufsichtigten Modus


> [!NOTE]
> Die aktuelle Version von Exchange 2013 zum Herunterladen finden Sie unter <A href="updates-for-exchange-2013-exchange-2013-help.md">Updates für Exchange 2013</A>.



1.  Melden Sie sich an dem Computer an, auf dem Exchange 2013 installiert werden soll.

2.  Navigieren Sie zum Netzwerkspeicherort der Exchange 2013-Installationsdateien.

3.  Führen Sie an der Eingabeaufforderung den entsprechenden Befehl für Ihre Organisation aus.
    

    > [!IMPORTANT]
    > Wenn die Benutzerkontensteuerung aktiviert ist, müssen Sie <CODE>Setup.exe</CODE> über eine Eingabeaufforderung mit erhöhten Rechten ausführen.

    
        Setup.exe [/Mode:<setup mode>] [/IAcceptExchangeServerLicenseTerms]
        [/Roles:<server roles to install>] [/InstallWindowsComponents] 
        [/OrganizationName:<name for the new Exchange organization>] 
        [/TargetDir:<target directory>] [/SourceDir:<source directory>]
        [/UpdatesDir:<directory from which to install updates>] 
        [/DomainController:<FQDN of domain controller>] [/DisableAMFiltering]
        [/AnswerFile:<filename>] [/DoNotStartTransport] 
        [/EnableErrorReporting] [/CustomerFeedbackEnabled:<True | False>] 
        [/AddUmLanguagePack:<UM language pack name>] 
        [/RemoveUmLanguagePack:<UM language pack name>] 
        [/NewProvisionedServer:<server>] [/RemoveProvisionedServer:<server>] 
        [/MdbName:<mailbox database name>] [/DbFilePath:<Edb file path>] 
        [/LogFolderPath:<log folder path>] [/ActiveDirectorySplitPermissions:<True | False>]
        [/TenantOrganizationConfig:<path>]

4.  Die Installationsdateien werden lokal auf den Computer kopiert, auf dem Exchange 2013 installiert wird.

5.  Setup überprüft die Voraussetzungen einschließlich aller Voraussetzungen, die für die Serverrollen spezifisch sind, die Sie installieren. Wenn nicht alle Voraussetzungen erfüllt sind, tritt bei der Installation ein Fehler auf, und eine Fehlermeldung wird zurückgegeben, in der die Ursache des Fehlers erläutert wird. Wenn alle Voraussetzungen erfüllt sind, wird Exchange 2013 installiert.

6.  Starten Sie den Computer nach Abschluss der Exchange 2013-Installation neu.

7.  Schließen Sie Ihre Bereitstellung ab, indem Sie die unter [Aufgaben nach der Installation von Exchange 2013](exchange-2013-post-installation-tasks-exchange-2013-help.md) beschriebenen Aufgaben durchführen.

## Beispiele

Die folgenden Beispiele zeigen die Verwendung von "Setup.exe":

  - **Setup.exe /mode:Install /role:ClientAccess,Mailbox /OrganizationName:MyOrg /IAcceptExchangeServerLicenseTerms**
    
    Mit diesem Befehl wird in Active Directory eine Exchange 2013-Organisation namens "MyOrg" erstellt. Außerdem werden die Clientzugriffs-, die Postfachrolle und die Verwaltungstools installiert, und es werden die Lizenzbedingungen für Exchange 2013 akzeptiert.

  - **Setup.exe /mode:Install /role:ClientAccess,Mailbox /TargetDir:"C:\\Exchange Server" /IAcceptExchangeServerLicenseTerms**
    
    Mit diesem Befehl werden die Clientzugriffs-Serverrolle, die Postfachserverrolle und die Verwaltungstools im "C:\\Exchange Server" installiert. Bei diesem Befehl wird davon ausgegangen, dass bereits eine Exchange 2013-Organisation vorbereitet wurde.

  - **Setup.exe /mode:Install /r:CA,MB /IAcceptExchangeServerLicenseTerms**
    
    Mit diesem Befehl werden die Clientzugriffs-Serverrolle, die Postfachserverrolle und die Verwaltungstools am standardmäßigen Installationsspeicherort installiert.

  - **Setup.exe /mode:Install /r:EdgeTransport /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl installiert die Edge-Transport-Serverrolle sowie die Verwaltungstools am Standardinstallationsort.

  - **Setup.exe /mode:Install /r:ET /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl installiert die Edge-Transport-Serverrolle sowie die Verwaltungstools am Standardinstallationsort.

  - **Setup.exe /mode:Uninstall /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl entfernt Exchange 2013 vollständig vom Server und entfernt die Exchange-Konfiguration dieses Servers aus Active Directory.

  - **Setup.exe /PrepareAD /on:"My Org" /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl erstellt die Exchange-Organisation **My Org** und bereitet Active Directory auf Exchange 2013 vor.

  - **C:\\ExchangeServer\\bin\\Setup.exe /m:Install /r:ClientAccess /SourceDir:d:\\amd64 /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl fügt einem vorhandenen Exchange 2013-Server die Clientzugriffs-Serverrolle unter Verwendung von **D:\\amd64** als Quellverzeichnis hinzu.

  - **Setup.exe /role:ClientAccess,Mailbox /UpdatesDir:"C:\\ExchangeServer\\New Patches" /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl aktualisiert "ExchangeServer.msi" mit Patches aus dem angegebenen Verzeichnis und installiert dann die Clientzugriffs- und die Postfachserverrolle sowie die Verwaltungstools. Wenn ein Sprachpaket im Verzeichnis vorhanden ist, wird das Sprachpaket ebenfalls installiert.

  - **Setup.exe /mode:Install /role:ClientAccess,Mailbox /DomainController:DC01 /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl verwendet den Domänencontroller "DC01", um während der Installation der Clientzugriffs- und Postfachserverrolle sowie der Verwaltungstools Abfragen an Active Directory zu senden und Änderungen vorzunehmen.

  - **Setup.exe /mode:Install /role:ClientAccess /AnswerFile:c:\\ExchangeConfig.txt /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl installiert die Clientzugriffs-Serverrolle mithilfe der Einstellungen in der Datei "ExchangeConfig.txt".

  - **Setup.exe /rprs:Exchange03 /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl entfernt das Objekt **Exchange03** aus Active Directory.

  - **Setup.exe /AddUmLanguagePack:ko-KR /IAcceptExchangeServerLicenseTerms**
    
    Dieser Befehl installiert das koreanische Unified Messaging-Sprachpaket aus dem Verzeichnis "%ExchangeSourceDir%\\ServerRoles\\UnifiedMessaging".

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Informationen dazu, wie Sie überprüfen, ob die Installation von Exchange 2013 erfolgreich abgeschlossen wurde, finden Sie unter [Überprüfen einer Exchange 2013-Installation](verify-an-exchange-2013-installation-exchange-2013-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.


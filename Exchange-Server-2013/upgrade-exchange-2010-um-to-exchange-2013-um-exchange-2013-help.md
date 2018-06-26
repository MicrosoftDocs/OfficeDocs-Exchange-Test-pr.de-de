---
title: 'Aktualisierung von Exchange 2010 Unified Messaging auf Exchange 2013 Unified Messaging: Exchange 2013 Help'
TOCTitle: Aktualisierung von Exchange 2010 Unified Messaging auf Exchange 2013 Unified Messaging
ms:assetid: 01aa5dab-689b-4738-afab-0d2f11a60b39
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn169226(v=EXCHG.150)
ms:contentKeyID: 54652679
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktualisierung von Exchange 2010 Unified Messaging auf Exchange 2013 Unified Messaging

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Bei der Aktualisierung einer Microsoft Exchange 2010-Organisation mit Unified Messaging (UM) auf Exchange 2013 Unified Messaging gibt es notwendige Schritte und Schritte, die bereits im Rahmen Ihrer Exchange 2010 UM-Bereitstellung durchgeführt wurden. Abhängig von Ihrer Telefonieumgebung und den für die Unterstützung von Unified Messaging in Exchange 2010 erstellten und konfigurierten UM-Komponenten müssen Sie möglicherweise zusätzliche Telefoniegeräte wie VoIP-Gateways (Voice over IP), IP Private Branch eXchanges (PBXs) oder herkömmliche beziehungsweise SIP-fähige PBXs bereitstellen und anschließend alle zusätzlichen UM-Komponenten erstellen und konfigurieren, die für Exchange 2013 UM benötigt werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 45-90 Minuten.

  - Überprüfen Sie, dass Sie in der Exchange 2010- und der Exchange 2013-Organisation über die entsprechenden Berechtigungen zur Erstellung und Konfiguration aller notwendigen Komponenten verfügen.

  - Vergewissern Sie sich, dass Sie Ihre Telefoniekomponenten einschließlich VoIP-Gateways und Nebenstellenanlagen, IP-Nebenstellenanlagen oder SIP-aktivierte (Session Initiation Protocol) Nebenstellenanlagen bereitgestellt und richtig konfiguriert haben.

  - Vergewissern Sie sich, dass der Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Dienst für die Anrufweiterleitung ausgeführt wird, und der Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, korrekt installiert und konfiguriert wurden. Weitere Informationen über UM-Dienste finden Sie unter [UM-Dienste](um-services-exchange-2013-help.md).
    

    > [!WARNING]
    > Sie müssen in Ihrer Organisation mindestens einen Exchange 2013-Postfachserver bereitstellen, bevor Sie die VoIP-Gateways oder IP-PBXs so konfigurieren können, dass diese UM SIP- und RTP-Datenverkehr zum Exchange 2013-Clientzugriffsserver senden.



  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Wie gehen Sie dazu vor?

## Schritt 1: Herunterladen und Installieren der erforderlichen UM-Sprachpakete

UM-Sprachpakete ermöglichen Anrufern und Outlook Voice Access-Benutzern die Interaktion mit dem Voicemailsystem in mehreren Sprachen. Nachdem Sie eine zusätzliche Sprache auf einem Exchange 2013-Postfachserver installiert haben, können Anrufer und Outlook Voice Access-Benutzer E-Mail-Nachrichten in dieser Sprache wiedergeben und mit dem Voicemailsystem in dieser Sprache interagieren. Zur Bereitstellung der Sprache für eingehende Anrufe müssen Sie jedoch die erforderlichen UM-Sprachpakete auf allen Exchange 2013-Postfachservern installieren. Der Grund hierfür besteht darin, dass jeder Exchange 2013-Postfachserver eingehende Anrufe für Unified Messaging beantworten kann.

Bei der Installation eines Exchange 2013-Postfachservers wird standardmäßig das Sprachpaket für US-amerikanisches Englisch (en-US) installiert. Dabei handelt es sich um die einzige verfügbare Sprachoption für Ihre Wähleinstellungen, es sei denn, Sie installieren ein anderes UM-Sprachpaket. (Die US-englische Version kann nur entfernt werden, wenn Sie den Postfachserver vom Computer entfernen.) Nachdem Sie ein UM-Sprachpaket auf einem Exchange 2013-Postfachserver installiert haben, wird die dem Sprachpaket zugeordnete Sprache als verfügbare Option aufgelistet, wenn Sie die Standardsprache für die Wähleinstellungen konfigurieren. Standardmäßig wird aufgrund der Verknüpfung einer automatischen Telefonzentrale mit einem UM-Wählplan während der Erstellung der automatischen Telefonzentrale die Standardspracheinstellung des verknüpften UM-Wählplans verwendet. Diese Einstellung kann jedoch geändert werden, nachdem die automatische UM-Telefonzentrale erstellt wurde.


> [!NOTE]
> Wenn US-Englisch die einzige Sprache ist, die Sie für Ihre Wähleinstellungen bereitstellen möchten, können Sie diesen Schritt überspringen und mit Schritt&nbsp;2 fortfahren.



Nach dem Herunterladen eines UM-Sprachpakets von [Exchange Server 2013 UM Language Packs – Deutsch](https://go.microsoft.com/fwlink/p/?linkid=266542) kann dieses über den Befehl "Setup.exe" oder über das Installationsprogramm "*\<UMLanguagePack\>*.exe" installiert werden. Weitere Informationen finden Sie unter [Installieren eines Sprachpakets](install-a-um-language-pack-exchange-2013-help.md).

In diesem Beispiel wird mit "Setup.exe" das UM-Sprachpaket für Japanisch (ja-JP) installiert.

    setup.exe /AddUmLanguagePack:ja-JP /s:d:\Exchange\UMLanguagePacks /IAcceptExchangeServerLicenseTerms

## Schritt 2: Verschieben des Exchange 2010-Systempostfachs für benutzerdefinierte UM-Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen in Exchange 2013

Benutzerdefinierte Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen werden von UM-Wählplänen und automatischen Telefonzentralen verwendet. Das Systempostfach {e0dc1c29-89c3-4034-b678-e6c29d823ed9} wird erstellt, wenn Sie Exchange 2010 oder Exchange 2013 installieren. Es dient der Unterstützung von Funktionen wie Nachrichtengenehmigung und Suche in mehreren Postfächern. Mit dem Systempostfach werden zusätzlich benutzerdefinierte Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen für Wählpläne und automatische Telefonzentralen gespeichert. Wenn das Systempostfach nicht vorhanden ist, können Sie es mit **Setup /PrepareAD** erstellen.

Systempostfächer werden standardmäßig nicht im Exchange Admin Center angezeigt. Eine Liste der Systempostfächer können Sie mit einer der nachstehenden Methoden abrufen:

Mit diesem Befehl wird eine Liste aller Systempostfächer angezeigt.

    Get-Mailbox -Arbitration

Mit diesem Befehl wird eine Liste der Systempostfächer und den dazugehörigen individuellen Eigenschaften und Einstellungen angezeigt.

    Get-Mailbox -Arbitration |fl

Mithilfe dieses Systempostfachs können benutzerdefinierte Begrüßungen, Ansagen Menüs und Eingabeaufforderungen zusammen mit anderen Postfächern in einer Datenbank gesichert und wiederhergestellt werden. Dadurch werden die benötigten Ressourcen verringert. Mit dem Speichern von benutzerdefinierten Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen in einem Systempostfach werden möglicherweise aufgetretene Inkonsistenzen beseitigt. Weitere Informationen zu Postfachverschiebungen finden Sie unter [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

## Optional: Manuelles Exportieren und Importieren von benutzerdefinierten Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen für Wählpläne und automatische Telefonzentralen

Es kann vorkommen, dass das Exchange 2010-Systempostfach verschoben wurde und Sie weiterhin die benutzerdefinierten Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen für UM-Wählpläne und automatische Telefonzentralen aus dem Exchange 2010-Systempostfach exportieren und in das Exchange 2013-Systempostfach importieren müssen. Der Name des Systempostfachs lautet in beiden Versionen {e0dc1c29-89c3-4034-b678-e6c29d823ed9}.

Benutzerdefinierte Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen sind Audiodateien (im WAV- oder WMA-Format), die von UM zu folgenden Zwecken eingesetzt werden:

  - In UM-Wählplänen werden die Audiodateien für angepasste Begrüßungen und Informationsansagen verwendet. Sie werden wiedergegeben, wenn Benutzer von Outlook Voice Access eine Outlook Voice Access-Nummer anrufen.

  - Mit automatischen Telefonzentralen werden die Audiodateien für benutzerdefinierte Begrüßungen während und außerhalb der Geschäftszeiten, Informationsansagen, Menüansagen und Navigationsmenüs verwendet. Sie werden wiedergegeben, wenn Anrufer eine automatische Telefonzentrale anrufen.

Exportieren und importieren Sie benutzerdefinierte Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen aus Exchange 2010 in Exchange 2013, müssen Sie die Cmdlets**Export-UMPrompt** und **Import-UMPrompt** verwenden. Benutzerdefinierte Eingabeaufforderungen können Sie mit der Exchange-Verwaltungskonsole nicht exportieren oder importieren. Exportieren Sie auf einem Exchange 2010-Server den Exchange 2010-Wählplan und die Eingabeaufforderungen der automatischen Telefonzentrale mit dem Cmdlet **Export-UMPrompt**. Nach dem Export der Eingabeaufforderungen können Sie sie in den Exchange 2013-Postfachserver importieren. Bei der Ausführung des Cmdlet **Export-UMPrompt** auf dem Exchange 2010-Server wird mit dem Befehl im Active Directory eine GUID- oder eine Objekt-ID-Suche für den Wählplan oder die automatische Telefonzentrale durchgeführt und eine Abfrage ausgeführt, um festzustellen, ob benutzerdefinierte Begrüßungen, Ansagen, Menüs oder Eingabeaufforderungen vorhanden sind. Ist dies der Fall, werden benutzerdefinierte Begrüßungen, Ansagen, Menüs oder Eingabeaufforderungen im angegebenen Verzeichnis gespeichert. Importieren Sie nach dem Export aller benutzerdefinierter Begrüßungen, Ansagen, Menüs oder Eingabeaufforderungen mit dem Cmdlet **Import-UMPrompt** die Eingabeaufforderungen in Ihr Exchange 2013-Systempostfach.

In diesem Beispiel wird die Begrüßung für den UM-Wählplan `MyUMDialPlan` exportiert, und die Datei wird unter dem Namen `welcomegreeting.wav` gespeichert.

    $prompt = Export-UMPrompt -PromptFileName "customgreeting.wav" -UMDialPlan MyUMDialPlan
    set-content -Path "d:\DialPlanPrompts\welcomegreeting.wav" -Value $prompt.AudioData -Encoding Byte

In diesem Beispiel wird die Begrüßungsdatei `welcomegreeting.wav` aus "D:\\UMPrompts" in den UM-Wählplan `MyUMDialPlan` importiert.

    [byte[]]$c = Get-content -Path "d:\UMPrompts\welcomegreeting.wav" -Encoding Byte -ReadCount 0
    Import-UMPrompt -UMDialPlan MyUMDialPlan -PromptFileName "welcomegreeting.wav" -PromptFileData $c

In diesem Beispiel wird eine benutzerdefinierte Begrüßung für die automatische Telefonzentrale `MyUMAutoAttendant` exportiert, und die Datei wird unter dem Namen `welcomegreetingbackup.wav` gespeichert.

    Export-UMPrompt -PromptFileName "welcomegreeting.wav" -UMAutoAttendant MyUMAutoAttendant
    set-content -Path "e:\UMPromptsBackup\welcomegreeting.wav" -Value $prompt.AudioData -Encoding Byte

In diesem Beispiel wird die Begrüßungsdatei `welcomegreeting.wav` aus "D:\\UMPrompts" in die automatische Telefonzentrale `MyUMAutoAttendant` importiert.

    [byte[]]$c = Get-content -Path "d:\UMPrompts\welcomegreeting.wav" -Encoding Byte -ReadCount 0
    Import-UMPrompt -UMAutoAttendant MyUMAutoAttendant -PromptFileName "welcomegreeting.wav" -PromptFileData $c

Weitere Informationen zu benutzerdefinierten Eingabeaufforderungen für UM finden Sie hier:

  - [Importieren und Exportieren angepasster Begrüßungen, Informationsansagen, Menüs und Menüansagen](import-and-export-custom-greetings-announcements-menus-and-prompts-exchange-2013-help.md)

  - [Import-UMPrompt](https://technet.microsoft.com/de-de/library/dd876899\(v=exchg.150\))

  - [Export-UMPrompt](https://technet.microsoft.com/de-de/library/dd876882\(v=exchg.150\))

  - [UM-Sprachen, -Telefonansagen und -Begrüßungen](um-languages-prompts-and-greetings-exchange-2013-help.md)

## Schritt 4: Exportieren und Importieren von Zertifikaten

Wenn Sie in Ihrer Exchange 2010-Organisation SIP-gesicherte oder gesicherte Wählpläne verwenden, müssen Sie die verwendeten Zertifikate exportieren und in Ihre Exchange 2013-Clientzugriffs- und Postfachserver importieren. Für die Verschlüsselung der zwischen Ihren Exchange 2013-Servern und den VoIP-Gateways, IP-PBX-Anlagen und SIP-fähigen PBX-Anlagen gesendeten Daten wird MTLS (Mutual Transport Layer Security) eingesetzt. Zertifikate dienen zum Binden der Identität des Zertifikatbesitzers an ein Paar elektronischer Schlüssel (öffentlich und privat), die zum Verschlüsseln und digitalen Signieren von Informationen verwendet werden. Sie können eines der folgenden Zertifikate für die UM- und UM-Anrufweiterleitungsdienste verwenden:

  - Ein selbstsigniertes (Exchange-)Zertifikat

  - Ein internes PKI-Zertifikat (Public Key-Infrastruktur)

  - Ein kommerzielles Zertifikat eines Drittanbieters

Standardmäßig werden bei der Installation von Exchange 2013 zwei selbstsignierte Zertifikate erstellt: **Microsoft Exchange Server Auth Certificate** und **Microsoft Exchange**. Das selbstsignierte **Microsoft Exchange**-Zertifikat kann für UM zur Datenverschlüsselung verwendet werden. Sie müssen das Zertifikat jedoch den UM- und UM-Anrufweiterleitungsdiensten zuweisen. Dieses selbstsignierte Zertifikat kann kopiert und anschließend in die VoIP-Gateways, IP-PBX-Anlagen und SIP-fähigen PBX-Anlagen importiert werden. Es kann jedoch nicht für die Integration von UM mit Microsoft Lync Server eingesetzt werden.

Führen Sie die folgenden Schritte aus, um UM das Verschlüsseln von Daten zu ermöglichen, die zwischen Ihren Exchange 2013-Servern und VoIP-Gateways, IP-PBX-Anlagen und SIP-fähigen PBX-Anlagen gesendet werden:

  - Verwenden Sie ein bereits vorhandenes selbstsigniertes UM-Zertifikat, erstellen Sie ein neues selbstsigniertes Exchange-Zertifikat, leiten Sie eine Zertifikatanforderung an einer interne Zertifizierungsstelle für ein PKI-Zertifikat weiter, oder erwerben Sie ein kommerzielles Zertifikat eines Drittanbieters, das Sie für MTLS zwischen Ihren Exchange 2013-Postfachservern und Clientzugriffsservern sowie VoIP-Gateways, IP-PBX-Anlagen und SIP-fähigen PBX-Anlagen verwenden können.
    
    Erstellen Sie wie folgt ein selbstsigniertes Exchange-Zertifikat mit der Exchange-Verwaltungskonsole:
    
    1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Zertifikate**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").
    
    2.  Wählen Sie auf der Seite **Neues Exchange-Zertifikat** die Option **Selbstsigniertes Zertifikat erstellen** aus, und klicken Sie dann auf **Weiter**.
    
    3.  Geben Sie einen Anzeigenamen für das Zertifikat ein, und klicken Sie dann auf **Weiter**.
    
    4.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Exchange-Server auszuwählen, denen dieses Zertifikat zugewiesen werden soll, und klicken Sie dann auf **Weiter**.
    
    5.  Geben Sie die Domänen an, die Sie in das Zertifikat aufnehmen möchten, und klicken Sie dann auf **Weiter**. Wenn Sie eine Domäne für einen Dienst hinzufügen möchten, klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    6.  Vergewissern Sie sich, dass die richtigen Domänen angegeben sind, und klicken Sie dann auf **Fertig stellen**.
    

    > [!IMPORTANT]
    > Wenn Sie ein Zertifikat mit der Exchange-Verwaltungskonsole erstellen, werden Sie nicht zur Aktivierung der Dienste für das Zertifikat aufgefordert. Nach der Erstellung des Zertifikats können Sie die Dienste mit der Exchange-Verwaltungskonsole aktivieren. Weitere Informationen zur Aktivierung eines Zertifikats für Dienste finden Sie unter <A href="assign-a-certificate-to-the-um-and-um-call-router-services-exchange-2013-help.md">Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst</A>.

    
    Erstellen Sie ein selbstsigniertes Exchange-Zertifikat, indem Sie in der Shell den folgenden Befehl ausführen.
    
        New-ExchangeCertificate -Services 'UM, UMCallRouter' -DomainName '*.northwindtraders.com' -FriendlyName 'UMSelfSigned' -SubjectName 'C=US,S=WA,L=Redmond,O=Northwindtraders,OU=Servers,CN= Northwindtraders.com' -PrivateKeyExportable $true
    

    > [!NOTE]
    > Wenn Sie die zu aktivierenden Dienste mit dem Parameter <EM>Services</EM> angeben, werden Sie zur Aktivierung der Dienste für das erstellte Zertifikat aufgefordert. In diesem Beispiel werden Sie zur Aktivierung des Zertifikats für die UM- und UM-Anrufweiterleitungsdienste aufgefordert. Weitere Informationen zur Aktivierung eines Zertifikats für Dienste finden Sie unter <A href="assign-a-certificate-to-the-um-and-um-call-router-services-exchange-2013-help.md">Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst</A>.



  - Importieren Sie das Zertifikat, das auf allen Exchange 2013-Clientzugriffs- und Postfachservern in Ihrer Organisation verwendet wird. Bei Verwendung des selbstsignierten Exchange 2013-Zertifikats müssen Sie das Zertifikat kopieren und anschließend in die VoIP-Gateways, IP-PBX-Anlagen oder SIP-fähigen PBX-Anlagen importieren. Verwenden Sie das selbstsignierte Zertifikat aus Exchange 2010, muss der alternative Antragstellername die Computernamen aller Exchange 2013-Server enthalten. Befinden sich in Ihrer Organisation Exchange 2010 UM-Server, können Sie das selbstsignierte Exchange 2013-Zertifikat verwenden, Sie müssen jedoch die Computernamen der Exchange 2010 UM-Server zum alternativen Antragstellernamen im Exchange 2013-Zertifikat hinzufügen.

  - Aktivieren Sie das Zertifikat, das für die UM- und UM-Anrufweiterleitungsdienste auf den Clientzugriffs- und Postfachservern in Ihrer Organisation verwendet werden soll, oder weisen Sie es zu.
    
    Aktivieren Sie den UM-Dienst und den UM-Anrufweiterleitungsdienst auf allen Exchange 2013-Servern für die Verwendung des selbstsignierten Exchange-Zertifikats mit der Exchange-Verwaltungskonsole wie folgt:
    
    1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Zertifikate**, wählen Sie das Zertifikat aus, für das Dienste aktiviert werden sollen, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    2.  Wählen Sie auf der Seite **Verfahren** die Option **Dienste** aus, wählen Sie **Unified Messaging** und dann **Unified Messaging-Anrufweiterleitung**.
    
    Aktivieren Sie ein selbstsigniertes Exchange-Zertifikat, indem Sie in der Shell den folgenden Befehl ausführen.
    
        Enable-ExchangeCertificate -Thumbprint 5113ae0233a72fccb75b1d0198628675333d010e -Services 'UM, UMCallRouter'

  - Konfigurieren Sie alle neuen oder bestehenden UM-Wählpläne als "SIP-gesichert" oder "Gesichert".

  - Konfigurieren Sie den UM-Startmodus auf den Clientzugriffs- und Postfachservern in Ihrer Organisation als "TLS" oder "Dual"

  - Erstellen und konfigurieren Sie neue oder bestehende UM-IP-Gateways mit einem vollständig qualifizierten Domänennamen (FQDN).

  - Konfigurieren Sie den Überwachungsport für die UM-IP-Gateways für die Verwendung von TCP-Port 5061.

  - Starten Sie den UM-Anrufweiterleitungsdienst auf allen Exchange 2013-Clientzugriffsservern neu, und starten Sie den UM-Dienst auf allen Exchange 2013-Postfachservern neu. Weitere Informationen über UM-Dienste finden Sie unter [UM-Dienste](um-services-exchange-2013-help.md).

## Schritt 5: Konfigurieren des UM-Startmodus auf allen Exchange 2013-Clientzugriffsservern

Wenn Sie SIP-gesicherte oder gesicherte Wählpläne verwenden, müssen Sie den UM-Startmodus auf Ihren Exchange 2013-Clientzugriffsservern konfigurieren. Sie können den UM-Startmodus für den UM-Anrufweiterleitungsdienst auf einem Exchange 2013-Clientzugriffsserver festlegen, indem Sie die Exchange-Verwaltungskonsole oder die Exchange-Verwaltungsshell verwenden. Standardmäßig wird der Clientzugriffsserver im TCP-Modus gestartet. Wenn Sie jedoch TLS (Transport Layer Security) zum Verschlüsseln von VoIP-Datenverkehr (Voice over IP) verwenden, müssen Sie den Exchange 2013-Clientzugriffsserver so konfigurieren, dass der TLS- oder der Dualmodus verwendet wird. Es wird empfohlen, alle Exchange 2013-Clientzugriffsserver für den UM-Startmodus "Dual" zu konfigurieren. Der Grund hierfür besteht darin, dass alle Exchange 2013-Clientzugriffserver eingehende Anrufe für alle UM-Wählpläne beantworten können, diese Wählpläne jedoch unterschiedliche Sicherheitseinstellungen aufweisen können. Wenn Sie den UM-Startmodus ändern, müssen Sie den UM-Anrufweiterleitungsdienst erneut starten, damit die Änderung wirksam wird. Weitere Informationen über UM-Dienste finden Sie unter [UM-Dienste](um-services-exchange-2013-help.md).

Konfigurieren Sie den UM-Startmodus auf einem Exchange 2013-Clientzugriffsserver mit der Exchange-Verwaltungskonsole wie folgt:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Wählen Sie unter **UM-Anrufroutereinstellungen** \> **UM-Startmodus** in der Dropdownliste eine der folgenden Optionen aus:
    
      - **TCP**   Verwenden Sie diese Option, wenn Sie kein mTLS verwenden und nur ungesicherte Wählpläne einsetzen.
    
      - **TLS**   Verwenden Sie diese Option, wenn Sie mTLS verwenden und nur SIP-gesicherte oder gesicherte Wählpläne einsetzen.
    
      - **DUAL**   Verwenden Sie diese Option, wenn Sie mTLS und außerdem ungesicherte, SIP-gesicherte und gesicherte Wählpläne einsetzen.

5.  Nachdem Sie den UM-Startmodus ausgewählt haben, klicken Sie auf **Speichern**.

Konfigurieren Sie den UM-Startmodus auf einem Exchange 2013-Clientzugriffsserver durch die Ausführung des folgenden Befehls in der Shell.

    Set-UMCallRouterSettings -Server MyUMCallRouter.northwindtraders.com -UMStartupMode Dual

## Schritt 6: Konfigurieren des UM-Startmodus auf allen Exchange 2013-Postfachservern

Wenn Sie SIP-gesicherte oder gesicherte Wählpläne verwenden, müssen Sie den UM-Startmodus auf Ihren Exchange 2013-Postfachservern konfigurieren. Sie können den UM-Startmodus für den UM-Dienst auf einem Exchange 2013-Postfachserver angeben, indem Sie die Exchange-Verwaltungskonsole oder die Shell verwenden. Standardmäßig wird der Exchange 2013-Postfachserver im TCP-Modus gestartet. Wenn Sie jedoch TLS (Transport Layer Security) zum Verschlüsseln von VoIP-Datenverkehr (Voice over IP) verwenden, müssen Sie den Exchange 2013-Postfachserver so konfigurieren, dass der TLS- oder der Dualmodus verwendet wird. Es wird empfohlen, alle Exchange 2013-Postfachserver für den UM-Startmodus "Dual" zu konfigurieren. Der Grund hierfür besteht darin, dass alle Exchange 2013-Postfachserver eingehende Anrufe für alle UM-Wählpläne beantworten können, diese Wählpläne jedoch unterschiedliche Sicherheitseinstellungen aufweisen können. Wenn Sie den UM-Startmodus ändern, müssen Sie den UM-Dienst erneut starten, damit die Änderung wirksam wird. Weitere Informationen über UM-Dienste finden Sie unter [UM-Dienste](um-services-exchange-2013-help.md).

Konfigurieren Sie den UM-Startmodus auf einem Exchange 2013-Postfachserver mit der Exchange-Verwaltungskonsole wie folgt:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Wählen Sie unter **UM-Diensteinstellungen** \> **UM-Startmodus** eine der folgenden Optionen aus der Dropdownliste aus:
    
      - **TCP**   Verwenden Sie diese Option, wenn Sie kein mTLS verwenden und nur ungesicherte Wählpläne einsetzen.
    
      - **TLS**   Verwenden Sie diese Option, wenn Sie mTLS verwenden und nur SIP-gesicherte oder gesicherte Wählpläne einsetzen.
    
      - **DUAL**   Verwenden Sie diese Option, wenn Sie mTLS und außerdem ungesicherte, SIP-gesicherte und gesicherte Wählpläne einsetzen.

5.  Nachdem Sie den UM-Startmodus ausgewählt haben, klicken Sie auf **Speichern**.

Konfigurieren Sie den UM-Startmodus auf einem Exchange 2013-Postfachserver durch die Ausführung des folgenden Befehls in der Shell.

    Set-UMService -Identity MyUMServer -ExternalHostFqdn host.external.contoso.com -IPAddressFamily Any -UMStartupMode Dual

## Schritt 7: Erstellen oder Konfigurieren von vorhandenen UM-Wählplänen

Je nach Ihrer vorhandenen Exchange 2010-Bereitstellung müssen Sie möglicherweise neue UM-Wählpläne erstellen oder vorhandene Wählpläne konfigurieren. Ein UM-Wählplan stellt eine Gruppe von herkömmlichen oder SIP-fähigen Nebenstellenanlagen (Private Branch eXchange, PBX) oder IP-PBX-Anlagen dar, die bestimmte Benutzerdurchwahlnummern gemeinsam nutzen. Alle Benutzer-Durchwahlnummern, die auf herkömmlichen oder SIP-fähigen PBX-Anlagen oder IP-PBX-Anlagen in einem Wählplan gehostet werden, enthalten dieselbe Anzahl Stellen. Die Benutzer können die Durchwahlen der anderen Benutzer wählen, ohne eine Sondernummer an die Durchwahl anfügen oder eine vollständige Telefonnummer wählen zu müssen.

UM-Wählpläne werden in Unified Messaging verwendet, um sicherzustellen, dass die Telefondurchwahlen der Benutzer eindeutig sind. In einigen Telefonnetzen sind mehrere Nebenstellenanlagen oder IP-Nebenstellenanlagen vorhanden. In solchen Telefonnetzen können theoretisch zwei Benutzer mit identischer Telefondurchwahlnummer vorhanden sein. Mithilfe von UM-Wählplänen kann dies vermieden werden. Indem Sie die beiden Benutzer zwei getrennten UM-Wählplänen zuordnen, werden ihre Durchwahlen eindeutig. Weitere Informationen finden Sie unter [UM-Wählpläne](um-dial-plans-exchange-2013-help.md).

Sie können gegebenenfalls einen UM-Wählplan mit der Exchange-Verwaltungskonsole erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, und klicken Sie dann auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Füllen Sie auf der Seite **Neue UM-Wähleinstellungen** folgende Felder aus:
    
      - **Name**   Geben Sie den Namen für die Wähleinstellungen ein. Ein Name für die UM-Wähleinstellungen ist erforderlich und muss eindeutig sein. Der eingegebene Name dient jedoch nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell. Der Name der UM-Wähleinstellungen kann eine Länge von maximal 64 Zeichen haben und Leerzeichen enthalten. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
        
        Das Feld für den Namen der Wähleinstellungen kann zwar 64 Zeichen aufnehmen, der Name der Wähleinstellungen darf jedoch höchstens 49 Zeichen umfassen. Wenn Sie versuchen, einen Namen von Wähleinstellungen mit mehr als 49 Zeichen zu erstellen, wird eine Fehlermeldung angezeigt. Die Meldung gibt an, dass die UM-Postfachrichtlinie nicht generiert werden konnte, da der UM-Wählplanname zu lang ist. Das liegt daran, dass bei der Erstellung eines Wählplans auch eine UM-Postfachrichtlinie mit dem Namen *\<DialPlanName\>* auch eine **Standardrichtlinie** erstellt wird. Werden die 15 Zeichen in der Standardrichtlinie dem Wählplannamen hinzugefügt, wird die maximal zulässige Zeichenanzahl überschritten. Der Parameter *name* für den UM-Wählplan und die UM-Postfachrichtlinie kann insgesamt eine Länge von 64 Zeichen haben. Wenn der Name der Wähleinstellungen allerdings aus mehr als 49 Zeichen besteht, hat der Name der standardmäßigen UM-Postfachrichtlinie eine Länge von mehr als 64 Zeichen. Dies wird vom System nicht unterstützt.
    
      - **Durchwahllänge (Ziffern)**   Geben Sie die Anzahl von Ziffern für Durchwahlnummern in den Wähleinstellungen ein. Die Anzahl der Stellen für Durchwahlnummern basiert auf den Telefoniewähleinstellungen, die auf einer PBX (Nebenstellenanlage) eingerichtet werden. Wenn beispielsweise ein Benutzer, der bestimmten Telefoniewähleinstellungen zugeordnet ist, eine 4-stellige Durchwahl wählt, um einen anderen Benutzer mit den gleichen Telefoniewähleinstellungen anzurufen, dann wählen Sie 4 als die Anzahl der Stellen in der Durchwahl aus.
        
        Dies ist ein erforderliches Feld mit Werten von 1 bis 20. Die typische Durchwahllänge beträgt 3 bis 7 Ziffern. Wenn die vorhandene Telefonieumgebung Durchwahlnummern verwendet, müssen Sie eine Anzahl für die Stellen festlegen, die mit der Anzahl der Stellen in diesen Durchwahlnummern übereinstimmt.
        
        Wenn Sie einen Wählplan für die Telefondurchwahl erstellen, müssen Sie eine Durchwahlnummer für den Benutzer eingeben, wenn dieser mit dem Wählplan für die Telefondurchwahl verknüpft ist. Eine Durchwahlnummer ist auch bei SIP-Wähleinstellungen (Session Initiation Protocol) oder E.164-Wähleinstellungen erforderlich, wenn ein UM-aktivierter Benutzer mit SIP-URI- oder E.164-Wähleinstellungen verknüpft ist. Die Durchwahlnummer wird von Outlook Voice Access-Benutzern verwendet, wenn sie auf ihr Exchange-Postfach zugreifen.
    
      - UNRESOLVED\_TOKENBLOCK\_VAL(UI\_URI-Typ)
    
      - UNRESOLVED\_TOKENBLOCK\_VAL(UI\_VoIP-Sicherheit)
    
      - **Länder-/Regionscode**   Verwenden Sie dieses Feld zur Eingabe des Länder-/Regionscodes für ausgehende Anrufe. Diese Nummer wird automatisch vor der zu wählenden Telefonnummer eingefügt. In diesem Feld werden nur 1 bis 4 Ziffern akzeptiert. In den USA wird beispielsweise als Landes-/Regionscode 1, in Großbritannien 44 verwendet.

3.  Klicken Sie auf **Speichern**.

Sie können gegebenenfalls einen UM-Wählplan durch Ausführen des folgenden Befehls in der Shell erstellen.

    New-UMDialplan -Name MyUMDialPlan -URIType E164 -NumberOfDigitsInExtension 5 -VoIPSecurity Secured

Sie können gegebenenfalls einen vorhandenen UM-Wählplan mit der Exchange-Verwaltungskonsole erstellen wie folgt:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie anzeigen oder ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**. Nutzen Sie die Konfigurationsoptionen zur Anzeige bestimmter Wählplaneinstellungen und zur Aktivierung beziehungsweise Deaktivierung von Funktionen.

Sie können gegebenenfalls einen vorhandenen UM-Wählplan mit der Shell konfigurieren:

    Set-UMDialplan -Identity MyDialPlan -AccessTelephoneNumbers 4255551234 -AudioCodec Wma -CallAnsweringRulesEnabled $false -OutsideLineAccessCode 9 -VoIPSecurity SIPSecured

Im Rahmen der Bereitstellung von Exchange 2010 Unified Messaging wurden Sie aufgefordert, einem UM-Wählplan einen Unified Messaging-Server hinzuzufügen, damit dieser eingehende Anrufe beantwortet. Dies ist nicht mehr erforderlich. In Exchange 2013 können Clientzugriffsserver und Postfachserver nicht mit einer Telefondurchwahl oder einem E.164-Wählplan verknüpft werden, sie müssen jedoch mit SIP URI-Wählplänen verknüpft werden. Clientzugriffs- und Postfachserver beantworten alle eingehenden Anrufe für alle Typen von Wähleinstellungen.

## Schritt 8: Erstellen oder Konfigurieren bestehender UM-IP-Gateways

Je nach Ihrer vorhandenen Exchange 2010-Bereitstellung müssen Sie möglicherweise neue UM-IP-Gateways erstellen oder bereits vorhandene konfigurieren. Bei Verwendung von SIP-gesicherten oder gesicherten Wählplänen müssen Sie ein UM-IP-Gateway mit einem FQDN erstellen und mithilfe der Shell für das Abhören von Port 5061 konfigurieren. Vergewissern Sie sich, dass bestehende UM-IP-Gateways mit einem FQDN konfiguriert sind und Port 5061 abhören. Verwendet das UM-IP-Gateway keinen FQDN, ändern Sie die Adresse mit der Exchange-Verwaltungskonsole oder der Shell. Verwendet das UM-IP-Gateway nicht Port 5061, ändern Sie den Port mit der Shell. Die Einstellungen eines UM-IP-Gateways können Sie mit dem Cmdlet **Get-UMIPGateway** anzeigen lassen.

Ein UM-IP-Gateway stellt ein physisches VoIP-Gateway (Voice over IP), eine IP-PBX-Anlage oder eine SIP-fähige PBX-Anlage dar. Ehe ein VoIP-Gateway, eine IP-PBX-Anlage oder eine SIP-fähige PBX-Anlage zum Annehmen eingehender Anrufe und zum Senden ausgehender Anrufe für Voicemailbenutzer genutzt werden kann, muss im Verzeichnisdienst ein UM-IP-Gateway erstellt werden.

Durch die Kombination des UM-IP-Gateways mit einem UM-Sammelanschluss wird eine Verknüpfung zwischen einem VoIP-Gateway, einer IP-PBX-Anlage oder einer SIP-fähigen PBX-Anlage und einem UM-Wählplan eingerichtet. Durch Erstellen mehrerer UM-Sammelanschlüsse kann ein einzelnes UM-IP-Gateway mehreren UM-Wähleinstellungen zugeordnet werden. Weitere Informationen finden Sie unter [UM-IP-Gateways](um-ip-gateways-exchange-2013-help.md).

Sie können gegebenenfalls ein UM-IP-Gateway mit der Exchange-Verwaltungskonsole erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie auf der Seite **Neues UM-IP-Gateway** die folgenden Informationen ein:
    
      - **Name**   Geben Sie in diesem Feld einen eindeutigen Namen für das UM-IP-Gateway ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Namen des UM-IP-Gateways nach dem Erstellen ändern müssen, muss zuerst das vorhandene UM-IP-Gateway gelöscht und dann ein anderes UM-IP-Gateway mit dem entsprechenden Namen erstellt werden. Der UM-IP-Gatewayname ist erforderlich, wird aber nur zur Anzeige verwendet. Da in Ihrer Organisation unter Umständen mehrere UM-IP-Gateways verwendet werden, sollten Sie aussagekräftige Namen für Ihre UM-IP-Gateways verwenden. Die maximale Länge eines UM-IP-Gatewaynamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **Adresse**   Sie können ein UM-IP-Gateway mit einer IPv4- oder IPv6-Adresse oder mit einem FQDN konfigurieren. Verwenden Sie dieses Feld, um die auf VoIP-Gateway, IP-PBX-Anlage oder SIP-fähiger PBX-Anlage konfigurierte IP-Adresse oder einen vollqualifizierten Domänennamen (FQDN) anzugeben. In dieses Textfeld können nur gültige FQDNs eingegeben werden, die ordnungsgemäß formatiert sind.
        
        Sie können Buchstaben und Zahlen eingeben. Es werden IPv4-Adressen, IPv6-Adressen und FQDNs unterstützt. Um MTLS zwischen einem UM-IP-Gateway und Wähleinstellungen zu verwenden, die im SIP-gesicherten oder gesicherten Modus betrieben werden, müssen Sie das UM-IP-Gateway mit einem FQDN konfigurieren. Außerdem müssen Sie das Gateway für die Überwachung von Port 5061 konfigurieren und sicherstellen, dass VoIP-Gateways oder IP-PBX-Anlagen ebenfalls für die Überwachung von Port 5061 auf Mutual TLS-Anforderungen konfiguriert wurden. Führen Sie zum Konfigurieren eines UM-IP-Gateways den folgenden Befehl in der Shell aus: `Set-UMIPGateway -identity MyUMIPGateway -Port 5061`
        
        Wenn Sie einen FQDN verwenden, müssen Sie außerdem sicherstellen, dass Sie für das VoIP-Gateway, die IP-PBX-Anlage oder die SIP-fähige PBX-Anlage einen gültigen DNS-Hosteintrag konfiguriert haben, sodass der Hostname fehlerfrei in eine IP-Adresse aufgelöst werden kann. Auch wenn Sie anstelle einer IP-Adresse einen vollqualifizierten Domänennamen (FQDN) verwenden und die DNS-Konfiguration für das UM-IP-Gateway ändern, müssen Sie das UM-IP-Gateway deaktivieren und erneut aktivieren, um sicherzustellen, dass die Konfigurationsinformationen für das UM-IP-Gateway ordnungsgemäß aktualisiert werden.
    
      - **UM-Wählplan**   Klicken Sie auf **Durchsuchen**, um den UM-Wählplan auszuwählen, den Sie dem UM-IP-Gateway zuordnen möchten. Wenn Sie einen UM-Wählplan für die Zuordnung zu einem UM-IP-Gateway auswählen, wird außerdem ein UM-Sammelanschluss erstellt und diesem UM-Wählplan zugeordnet. Wenn Sie keinen UM-Wählplan auswählen, müssen Sie manuell einen UM-Sammelanschluss erstellen und diesen dann einem erstellten UM-IP-Gateway zuordnen.

3.  Klicken Sie auf **Speichern**.

Sie können gegebenenfalls mit dem folgenden Befehl ein UM-IP-Gateway erstellen.

    New-UMIPGateway -Identity MyUMIPGateway -Address "MyUMIPGateway.contoso.com"

So konfigurieren Sie ein bestehendes UM-IP-Gateway mit der Exchange-Verwaltungskonsole:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-IP-Gateway** auf **Konfigurieren**. Nutzen Sie die Konfigurationsoptionen zur Anzeige bestimmter UM-IP-Gatewayeinstellungen und zur Aktivierung beziehungsweise Deaktivierung von Funktionen.

Führen Sie zur Konfiguration eines bestehenden UM-IP-Gateways in der Shell den folgenden Befehl in der Shell aus.

    Set-UMIPGateway -Identity MyUMIPGateway -Address fe80::39bd:88f7:6969:d223%11 -IPAddressFamily Any -Status Disabled -OutcallsAllowed $false

## Schritt 9: Erstellen eines UM-Sammelanschlusses

Je nach Ihrer bestehenden Exchange 2010-Bereitstellung müssen Sie möglicherweise neue UM-Sammelanschlüsse erstellen. Ein telefonischer Sammelanschluss bietet eine Möglichkeit, Telefonanrufe einer einzelnen Nummer an mehrere Durchwahlen oder Telefonnummern zu verteilen. In Unified Messaging (UM) ist ein UM-Sammelanschluss die logische Abbildung eines telefonischen Sammelanschlusses und dient zum Verbinden eines UM-IP-Gateways mit einem UM-Wählplan.

Sie benötigen mindestens einen UM-Sammelanschluss für jeden IP-PBX- oder PBX-Sammelanschluss. Wenn Sie das folgende Verfahren abschließen, wird ein UM-Sammelanschluss standardmäßig erstellt. Wenn Sie über mehrere IP-PBX- oder PBX-Sammelanschlüsse verfügen, müssen Sie zusätzliche UM-Sammelanschlüsse erstellen. Weitere Informationen zu UM-Sammelanschlüssen finden Sie unter [UM-Sammelanschlüsse](um-hunt-groups-exchange-2013-help.md).

Sie können gegebenenfalls einen UM-Sammelanschluss mit der Exchange-Verwaltungskonsole erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** unter **UM-Sammelanschlüsse** auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie auf der Seite **Neuer UM-Sammelanschluss** die folgenden Informationen ein:
    
      - **Name**   Verwenden Sie dieses Feld, um den Anzeigenamen für den UM-Sammelanschluss zu erstellen. Ein UM-Sammelanschlussname ist erforderlich, und er muss eindeutig sein, wobei er jedoch nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell verwendet wird. Wenn Sie den Anzeigenamen des Sammelanschlusses nach dem Erstellen ändern müssen, müssen Sie zuerst den vorhandenen Sammelanschluss löschen und können dann einen anderen Sammelanschluss mit dem entsprechenden Namen erstellen. Wenn in Ihrer Organisation mehrere Sammelanschlüsse verwendet werden, empfiehlt sich die Verwendung aussagekräftiger Namen für die Sammelanschlüsse. Der Name eines UM-Sammelanschlusses kann eine Länge von maximal 64 Zeichen haben und Leerzeichen enthalten. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **UM-IP-Gateway**   Verwenden Sie dieses Feld für die Auswahl eines UM-IP-Gateways. Dieses enthält den Namen des UM-IP-Gateways, das dem UM-Sammelanschluss zugeordnet wird. Klicken Sie zur Verknüpfung eines UM-IP-Gateways mit dem UM-Sammelanschluss auf **Durchsuchen**.
    
      - **Pilot-ID**   Verwenden Sie dieses Feld, um eine Zeichenfolge anzugeben, die die Pilot-ID eindeutig kennzeichnet, die auf der PBX- oder der IP-PBX-Anlage konfiguriert ist. In diesem Feld können eine Durchwahlnummer oder ein SIP-URI (Session Initiation-Protokoll - Uniform Resource Identifier) verwendet werden. Alphanumerische Zeichen sind in diesem Feld zulässig. Für ältere Nebenstellenanlagen wird ein numerischer Wert als Pilot-ID verwendet. Einige IP-PBX-Anlagen und SIP-fähige PBX-Anlagen können jedoch SIP-URIs verwenden.

4.  Klicken Sie auf **Speichern**.

Sie können gegebenenfalls einen UM-Sammelanschluss durch Ausführen des folgenden Befehls in der Shell erstellen.

    New-UMHuntGroup -Name MyUMHuntGroup -PilotIdentifier 5551234,55555 -UMDialPlan MyUMDialPlan -UMIPGateway MyUMIPGateway


> [!TIP]
> Sie können für UM-Sammelanschlüsse keine Einstellungen konfigurieren oder ändern. Möchten Sie die Konfigurationseinstellungen für einen UM-Sammelanschluss ändern, müssen Sie diesen löschen und einen neuen UM-Sammelanschluss mit den richtigen Einstellungen hinzufügen.



## Schritt 10: Erstellen oder Konfigurieren von automatischen UM-Telefonzentralen

In Abhängigkeit von Ihrer bestehenden Exchange 2010-Bereitstellung müssen Sie möglicherweise neue automatische UM-Telefonzentralen erstellen. Sie können automatische UM-Telefonzentralen verwenden, um ein sprachgesteuertes Menüsystem zu erstellen, mit dessen Hilfe interne und externe Anrufer das Menüsystem der automatischen UM-Telefonzentrale verwenden können, um Benutzer und Abteilungen in einer Organisation suchen und Anrufe an diese durchstellen oder umleiten zu können. Weitere Informationen finden Sie unter [Automatisches Beantworten und Weiterleiten eingehender Anrufe](automatically-answer-and-route-incoming-calls-exchange-2013-help.md).

In kleineren Bereitstellungen können Sie UM nur bereitstellen, um Voicemailnachrichten für Benutzer zu hinterlassen. In diesen Bereitstellungen ist das Erstellen einer automatischen Telefonzentrale nicht erforderlich. In den meisten Fällen sind automatische Telefonzentralen jedoch für externe Anrufer sehr hilfreich, wenn diese einen Anruf in Ihre Organisation tätigen.

Sie können gegebenenfalls eine automatische UM-Telefonzentrale mit der Exchange-Verwaltungskonsole erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie den UM-Wählplan aus, für den eine automatische Telefonzentrale hinzugefügt werden soll, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Füllen Sie auf der Seite **Neue automatische UM-Telefonzentrale** die folgenden Felder aus:
    
      - **Name**   Geben Sie in dieses Feld den Anzeigenamen für die automatische UM-Telefonzentrale ein. Ein Name für die automatische UM-Telefonzentrale ist erforderlich und muss eindeutig sein. Er dient jedoch nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell. Falls Sie den Namen für die automatische Telefonzentrale nach ihrer Erstellung ändern möchten, müssen Sie zunächst die vorhandene automatische UM-Telefonzentrale löschen und anschließend eine andere automatische Telefonzentrale mit dem gewünschten Namen erstellen. Wenn in Ihrer Organisation mehrere automatische UM-Telefonzentralen eingesetzt werden, sollten Sie aussagekräftige Namen für Ihre automatischen UM-Telefonzentralen verwenden. Die maximale Länge für den Namen einer automatischen UM-Telefonzentrale beträgt 64 Zeichen inklusive Leerzeichen.
        
        Wenngleich der Name einer neuen automatischen UM-Telefonzentrale Leerzeichen enthalten darf, ist bei der Integration von Unified Messaging in Lync Server die Verwendung von Leerzeichen im Namen von automatischen Telefonzentralen nicht zulässig. Wenn Sie daher eine automatische Telefonzentrale mit Leerzeichen im Anzeigenamen erstellt haben und Sie eine Integration in Lync Server durchführen, müssen Sie diese automatische Telefonzentrale zunächst löschen und dann eine andere automatische Telefonzentrale erstellen, die keine Leerzeichen im Anzeigenamen enthält.
    
      - **Diese automatische Telefonzentrale als aktiviert erstellen**   Aktivieren Sie dieses Kontrollkästchen, wenn nach Abschluss der Erstellung der automatischen UM-Telefonzentrale die automatische Telefonzentrale eingehende Anrufe beantworten soll. Standardmäßig wird eine neue automatische Telefonzentrale als deaktiviert erstellt. Wenn Sie die automatische UM-Telefonzentrale als deaktiviert erstellen, können Sie sie nach der Erstellung in der Exchange-Verwaltungskonsole oder in der Shell aktivieren.
    
      - **Automatische Telefonzentrale zur Antwort auf Sprachbefehle einrichten**   Aktivieren Sie dieses Kontrollkästchen, um die automatische Telefonzentrale für die Spracherkennung zu aktivieren. Bei Sprachaktivierung der automatischen Telefonzentrale können Anrufer auf Systemansagen oder benutzerdefinierte Ansagen der automatischen UM-Telefonzentrale mit Tonwahl- oder Spracheingaben antworten. Standardmäßig wird die automatische Telefonzentrale bei ihrer Erstellung nicht sprachaktiviert. Damit Anrufern eine sprachaktivierte automatische Telefonzentrale in einer anderen Sprache als US-Englisch (en-US) zur Verfügung steht, müssen Sie das entsprechende UM-Sprachpaket installieren und die Eigenschaften der automatischen Telefonzentrale für die Verwendung dieser Sprache konfigurieren. Bei der Installation eines Exchange 2013-Postfachservers wird standardmäßig die US-englische Version (en-US) des UM-Sprachpakets installiert.
    
      - **Zugriffsnummern**   Geben Sie die Durchwahl- bzw. Telefonnummern ein, die Anrufer zum Erreichen der automatischen Telefonzentrale verwenden. Geben Sie eine Durchwahlnummer oder eine Telefonnummer in das Feld ein, und klicken Sie auf **Hinzufügen**, um die Nummer der Liste hinzuzufügen. Die Anzahl von Ziffern der eingegebenen Durchwahl- oder Telefonnummer muss nicht mit der Anzahl von Ziffern einer Durchwahlnummer übereinstimmen, die im zugeordneten Satz UM-Wähleinstellungen konfiguriert ist. Der Grund dafür ist, dass direkte Anrufe bei automatischen UM-Telefonzentralen zulässig sind.
        
        Sie können unbegrenzt viele Durchwahlnummern oder Zugriffsnummern eingeben. Sie können die neue automatische Telefonzentrale jedoch auch ohne Durchwahl- oder Telefonnummer erstellen. Eine Durchwahl- oder Telefonnummer ist nicht erforderlich. Sie können eine vorhandene Durchwahlnummer oder Pilot-ID bearbeiten und löschen. Klicken Sie zum Bearbeiten einer vorhandenen Durchwahl- oder Telefonnummer auf **Bearbeiten**. Klicken Sie zum Entfernen einer vorhandenen Durchwahl- oder Telefonnummer aus der Liste auf **Entfernen**.

4.  Klicken Sie auf **Speichern**.

Sie können gegebenenfalls einen UM-Sammelanschluss durch Ausführen des folgenden Befehls in der Shell erstellen.

    New-UMAutoAttendant -Name MyUMAutoAttendant -UMDialPlan MyUMDialPlan -PilotIdentifierList 56000,56100 -SpeechEnabled $true -Status Enabled

Sie können gegebenenfalls eine vorhandene automatische UM-Telefonzentrale mit der Exchange-Verwaltungskonsole konfigurieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie anzeigen oder konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Nutzen Sie die Konfigurationsoptionen zur Anzeige bestimmter Einstellungen für automatische Telefonzentralen und zur Aktivierung beziehungsweise Deaktivierung von Funktionen.

Sie können gegebenenfalls eine vorhandene automatische Telefonzentrale durch Ausführen des folgenden Befehls in der Shell konfigurieren.

    Set-UMAutoAttendant -Identity MySpeechEnabledAA -DTMFFallbackAutoAttendant MyDTMFAA -OperatorExtension 50100 -AfterHoursTransferToOperatorEnabled $true -StaroutToDialPlanEnabled $true

## Schritt 11: Erstellen oder Konfigurieren von UM-Postfachrichtlinien

Je nach Ihrer vorhandenen Exchange 2010-Bereitstellung müssen Sie möglicherweise neue UM-Postfachrichtlinien erstellen oder bereits vorhandene UM-Postfachrichtlinien konfigurieren. UM-Postfachrichtlinien sind erforderlich, wenn Sie Benutzer für Unified Messaging aktivieren. Das Postfach jedes UM-aktivierten Benutzers muss mit einer einzelnen UM-Postfachrichtlinie verknüpft sein. Nachdem Sie eine UM-Postfachrichtlinie erstellt haben, ordnen Sie ihr ein oder mehrere UM-aktivierte Postfächer zu. Dadurch können Sie PIN-Sicherheitseinstellungen festlegen, wie z. B. die Mindestanzahl von Stellen einer PIN oder die Höchstanzahl von Anmeldeversuchen für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind. Weitere Informationen finden Sie unter [UM-Postfachrichtlinien](um-mailbox-policies-exchange-2013-help.md).

Sie können gegebenenfalls eine UM-Postfachrichtlinie mit der Exchange-Verwaltungskonsole erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wähleinstellungen** unter **UM-Postfachrichtlinien** auf **Hinzufügen** ![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **Neue UM-Postfachrichtlinie** im Textfeld **Name** den Namen der neuen UM-Postfachrichtlinie ein.
    

    > [!NOTE]
    > Geben Sie in dieses Feld einen eindeutigen Namen für die UM-Postfachrichtlinie ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Anzeigenamen der UM-Postfachrichtlinie nach dem Erstellen ändern müssen, muss zuerst die vorhandene UM-Postfachrichtlinie gelöscht und dann eine andere UM-Postfachrichtlinie mit dem entsprechenden Namen erstellt werden. Sie können keine UM-Postfachrichtlinie löschen, solange UM-aktivierte Benutzer damit verknüpft sind. Es muss ein UM-Postfachrichtlinienname angegeben werden, er wird jedoch nur zu Anzeigezwecken verwendet. Wenn in Ihrer Organisation mehrere UM-Postfachrichtlinien verwendet werden, empfiehlt sich die Verwendung sinnvoller Namen für die UM-Postfachrichtlinien. Die maximale Länge eines UM-Postfachrichtliniennamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \ [ ] : ; | = , + * ? &lt; &gt;.



4.  Klicken Sie auf **Speichern**.
    

    > [!NOTE]
    > Wenn Sie die UM-Postfachrichtlinie speichern, werden alle Standardeinstellungen einschließlich PIN-Richtlinien, Voicemailfunktionen und Einstellungen für geschützte Voicemail aktiviert. Wenn Sie Standardeinstellungen für die soeben erstellte UM-Postfachrichtlinie anpassen oder ändern möchten, verwenden Sie das Cmdlet <STRONG>Set-UMMailbox</STRONG> oder die Exchange-Verwaltungskonsole.



Sie können gegebenenfalls eine UM-Postfachrichtlinie durch Ausführen des folgenden Befehls in der Shell erstellen.

    New-UMMailboxPolicy -Name MyUMMailboxPolicy -UMDialPlan MyUMDialPlan

Sie können gegebenenfalls eine vorhandenen UM-Postfachrichtlinie mit der Exchange-Verwaltungskonsole konfigurieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie anzeigen oder konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Nutzen Sie die Konfigurationsoptionen zur Anzeige bestimmter UM-Postfachrichtlinieneinstellungen und zur Aktivierung beziehungsweise Deaktivierung von Funktionen.

Sie können gegebenenfalls eine vorhandene UM-Postfachrichtlinie durch Ausführen des folgenden Befehls in der Shell konfigurieren.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 8 -MaxLogonAttempts 12 -MinPINLength 8 -PINHistoryCount 10 -PINLifetime 60 -ResetPINText "The PIN used to allow you access to your mailbox using Outlook Voice Access has been reset."

## Schritt 12: Verschieben von UM-aktivierten Postfächern in Exchange 2013

In Exchange 2010 Unified Messaging wird nach der Aktivierung von Benutzern in der Organisation für die Verwendung von Voicemail den Benutzern ein Standardsatz UM-Eigenschaften zugewiesen, damit diese UM-Funktionen verwenden können. Weitere Informationen finden Sie unter [Voicemail für Benutzer](voice-mail-for-users-exchange-2013-help.md).

Während der Aktualisierung wird es eine Zeitspanne geben, in der Sie über auf Exchange 2010-Postfachservern und auf Exchange 2013-Postfachservern UM-aktivierte Postfächer verfügen. Verschieben Sie jedoch alle UM-aktivierte Benutzer auf Exchange 2013-Postfachserver, müssen Sie die Exchange-Verwaltungskonsole oder das Cmdlet **New-MoveRequest** in der Shell von einem Exchange 2013-Server aus verwenden, um alle Eigenschaften und Einstellungen, einschließlich der Benutzer-PIN, beizubehalten.

Als Verschiebungsanforderung wird das Verschieben eines Postfachs von einer Postfachdatenbank in eine andere bezeichnet. Eine lokale Verschiebungsanforderung ist eine Postfachverschiebung, die in einer einzelnen Gesamtstruktur erfolgt. Weitere Informationen zum Verschieben von Postfächern finden Sie unter:

  - [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md)

  - [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\))

  - [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\))

  - [Verwalten von Verschiebungsanforderungen](https://go.microsoft.com/fwlink/p/?linkid=296352)

So verschieben Sie ein Exchange 2010-Postfach mit der Exchange-Verwaltungskonsole auf einen Exchange 2013-Postfachserver:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger** \> **Migration** und dann auf **Hinzufügen**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie im Assistenten für neue lokale Postfachverschiebungendie zu verschiebenden Benutzer aus, und klicken Sie auf **OK** und anschließend auf **Weiter**.

3.  Geben Sie auf der Seite **Konfiguration verschieben** einen Namen für den neuen Batch ein. Wählen Sie die gewünschten Optionen für das Archivpostfach sowie den Speicherort der Postfachdatenbank aus, und klicken Sie auf **Neu**.

Führen Sie zum Verschieben eines Exchange 2010-Postfachs auf einen Exchange 2013-Postfachserver mit der Shell den folgenden Befehl aus.

    New-MoveRequest -Identity 'tony@alpineskihouse.com' -TargetDatabase "DB01"

## Schritt 13: Aktivieren neuer Benutzer für UM oder Konfigurieren von Einstellungen für einen vorhandenen UM-aktivierten Benutzer

Ein Benutzer muss über ein Postfach verfügen, bevor eine Aktivierung für Unified Messaging durchgeführt werden kann. Standardmäßig ist ein Benutzer, der über ein Postfach verfügt, nicht für Unified Messaging aktiviert. Nach der UM-Aktivierung können Sie die UM-Eigenschaften und Voicemailfunktionen für den Benutzer verwalten, ändern und konfigurieren. Sie können Benutzer mit der Exchange-Verwaltungskonsole oder der Shell für UM aktivieren. Weitere Informationen finden Sie unter [Voicemail für Benutzer](voice-mail-for-users-exchange-2013-help.md).

Wenn Sie einen Benutzer für UM aktivieren, müssen Sie mindestens eine Durchwahlnummer definieren, die UM bei der Übermittlung einer Voicemail an das Postfach des Benutzers verwendet und die dem Benutzer die Nutzung von Outlook Voice Access ermöglicht. Nachdem Sie den Benutzer für UM aktiviert haben, können Sie dem Benutzerpostfach sekundäre Durchwahlnummern hinzufügen, diese ändern oder entfernen, indem Sie die Exchange Unified Messaging-Proxyadresse (EUM-Proxyadresse) für das Benutzerpostfach konfigurieren oder zusätzliche oder sekundäre Durchwahlnummern für die Benutzer in der Exchange-Verwaltungskonsole hinzufügen oder entfernen. Informationen zum Hinzufügen, Ändern oder Entfernen von Durchwahlnummern, E.164-Nummern oder SIP-Adressen finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

So aktivieren Sie einen Benutzer mit der der Exchange-Verwaltungskonsole für UM:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger**.

2.  Wählen Sie in der Listenansicht den Benutzer aus, dessen Postfach Sie für Unified Messaging aktivieren möchten.

3.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** auf **Aktivieren**.

4.  Klicken Sie auf der Seite **UM-Postfach aktivieren** neben **UM-Postfachrichtlinie** auf die Schaltfläche **Durchsuchen**, navigieren Sie zu der UM-Postfachrichtlinie, der Sie den Benutzer aus der Liste zuweisen möchten, und klicken Sie dann auf **OK**.

5.  Füllen Sie auf der Seite **UM-Postfach aktivieren** die folgenden Felder aus:
    
      - **SIP-Adresse oder E.164-Nummer**   Geben Sie die SIP-Adresse oder E.164-Nummer für den Benutzer ein. Diese Optionen sind nur verfügbar, wenn der Benutzer, den Sie für Unified Messaging aktivieren, einer UM-Postfachrichtlinie zugewiesen ist, die mit SIP-URI- oder E.164-Wähleinstellungen verknüpft ist. Das Hinzufügen einer SIP-Adresse oder E.164-Nummer für einen Benutzer ist nicht verfügbar, wenn der Benutzer Telefondurchwahl-Wähleinstellungen zugewiesen ist. Wenn Sie den Benutzer einer UM-Postfachrichtlinie zuweisen, die mit SIP-URI- oder E.164-Wähleinstellungen verknüpft ist, müssen Sie auch eine Durchwahlnummer für den Benutzer eingeben. Diese Durchwahlnummer wird verwendet, wenn Benutzer mit Outlook Voice Access auf ihr Postfach zugreifen. Die Anzahl der in diesem Feld konfigurierten Ziffern muss der Anzahl von Ziffern entsprechen, die für die SIP-URI- oder E.164-Wähleinstellungen konfiguriert ist.
    
      - **Durchwahlnummer**   Geben Sie die Durchwahlnummer für den Benutzer, den Sie für UM aktivieren, manuell ein.
        
        Sie müssen für den Benutzer eine gültige Durchwahlnummer angeben, die mit der im Wählplan angegebenen Anzahl von Ziffern übereinstimmt. Sie können nur numerische Zeichen oder Ziffern von 1 bis 20 eingeben. Eine typische Durchwahlnummer hat 3 bis 7 Ziffern. Die Anzahl von Ziffern der Durchwahl ist für den Wählplan festgelegt, der mit dem einem Benutzer zugewiesenen UM-Postfach verknüpft ist.
    
      - Führen Sie unter **PIN-Einstellungen** folgende Schritte aus:
        
          - **PIN automatisch generieren**   Klicken Sie auf diese Schaltfläche, um automatisch eine PIN für den UM-aktivierten Benutzer zu generieren, mit der der Benutzer über Outlook Voice Access auf das Voicemailsystem zugreifen kann. Dies ist die Standardeinstellung. Wenn Sie auf diese Schaltfläche klicken wird automatisch eine PIN basierend auf den PIN-Richtlinien erstellt, die in der dem Empfänger zugeordneten UM-Postfachrichtlinie konfiguriert sind. Es wird empfohlen, diese Einstellung zum Schutz der Benutzer-PIN zu verwenden. Die PIN wird in der Begrüßungsnachricht an den Benutzer gesendet, die er nach der Aktivierung für UM erhält. Standardmäßig muss diese PIN bei der ersten Anmeldung beim Postfach zum Abrufen der Voicemail geändert werden.
        
          - **PIN eingeben**   Klicken Sie auf diese Schaltfläche, wenn Sie manuell die PIN eingeben möchten, mit der der Benutzer auf das Voicemailsystem zugreifen kann. Die PIN muss mit den PIN-Richtlinieneinstellungen übereinstimmen, die in der UM-Postfachrichtlinie konfiguriert sind, die diesem UM-aktivierten Benutzer zugewiesen ist. Wenn die UM-Postfachrichtlinie beispielsweise so konfiguriert wurde, dass ausschließlich PINs mit sieben oder mehr Ziffern akzeptiert werden, muss die in diesem Feld eingegebene PIN mindestens sieben Ziffern umfassen.
        
          - **Benutzer muss PIN bei der ersten Anmeldung zurücksetzen**   Aktivieren Sie dieses Kontrollkästchen, um festzulegen, dass der Benutzer seine Voicemail-PIN ändern muss, wenn er das erste Mal mit einem Telefon über Outlook Voice Access auf das Voicemailsystem zugreift. Sie werden dazu aufgefordert, eine ihnen vertrautere PIN einzugeben. Dabei handelt es sich um eine bewährte Sicherheitsmethode, mit der UM-aktivierte Benutzer gezwungen werden, ihre PIN bei der ersten Anmeldung zu ändern. Auf diese Weise werden die Daten und Posteingänge besser vor unbefugtem Zugriff geschützt. Dieses Kontrollkästchen ist standardmäßig aktiviert.

6.  Überprüfen Sie auf der Seite **UM-Postfach aktivieren** Ihre Einstellungen. Klicken Sie auf **Fertig stellen**, um den Benutzer für Unified Messaging zu aktivieren. Klicken Sie auf **Zurück**, um Konfigurationsänderungen vorzunehmen.

Führen Sie zur Aktivierung eines Benutzers für UM mithilfe der Shell den folgenden Befehl aus.

    Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -NotifyEmail administrator@contoso.com -PINExpired $true

Sie können gegebenenfalls einen Benutzer konfigurieren, der mit der Exchange-Verwaltungskonsole für UM aktiviert wurde:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, dessen UM-Postfachrichtlinie Sie ändern möchten.

3.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** \> **Unified Messaging** auf **Details anzeigen**.

4.  Klicken Sie auf der Seite **UM-Postfach** auf **UM-Postfacheinstellungen**, um folgende UM-Eigenschaften für einen vorhandenen UM-aktivierten Benutzer anzuzeigen oder zu ändern:
    
      - **PIN-Status**   In diesem schreibgeschützten Feld wird der Status des Benutzerpostfachs angezeigt. Bei UM-aktivierten Benutzern wird der PIN-Status standardmäßig als **Nicht gesperrt** aufgelistet. Wenn der Benutzer jedoch mehrmals eine falsche Outlook Voice Access-PIN eingegeben hat, wird der Status als **Gesperrt** angezeigt.
    
      - **UM-Postfachrichtlinie**   Dieses Feld zeigt den Namen der UM-Postfachrichtlinie, die dem UM-aktivierten Benutzer zugeordnet ist. Sie können auf **Durchsuchen** klicken, um die UM-Postfachrichtlinie zu finden und anzugeben, die diesem UM-Postfach zugeordnet werden soll.
    
      - **Durchwahl für persönliche Vermittlungsstelle**   Verwenden Sie dieses Feld, um die Durchwahlnummer der Vermittlungsstelle für den Benutzer anzugeben. Standardmäßig ist keine Durchwahlnummer konfiguriert. Die Durchwahlnummer darf 1 bis 20 Zeichen lang sein. Eingehende Anrufe für den UM-aktivierten Benutzer können damit an die in diesem Feld angegebene Durchwahlnummer weitergeleitet werden.
        
        Für Wähleinstellungen und automatische Telefonzentralen können weitere Typen von Durchwahlnummern für Vermittlungsstellen angegeben werden. Diese Durchwahlnummern gelten jedoch in der Regel für unternehmensweite Telefonvermittlungen. Die Einstellung für die Durchwahl der persönlichen Vermittlungsstelle kann verwendet werden, wenn ein administrativer oder persönlicher Assistent eingehende Anrufe für einen bestimmten Benutzer beantwortet.

5.  Auf der Seite **UM-Postfach** können Sie unter **Andere Durchwahlen** Durchwahlnummern für den Benutzer anzeigen, hinzufügen und ändern.
    
      - Zum Hinzufügen einer Durchwahlnummer klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Verwenden Sie auf der Seite **Weitere Durchwahl hinzufügen** das Feld **Durchsuchen**, um den UM-Wählplan auszuwählen, und geben Sie dann die Durchwahlnummer im Feld **Durchwahlnummer** ein.
    
      - Zum Entfernen einer Durchwahlnummer wählen Sie die entsprechende Durchwahlnummer aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

6.  Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.

Sie können gegebenenfalls in der Shell mit dem folgenden Befehl einen Benutzer konfigurieren, der für UM aktiviert ist.

    Set-UMMailbox -Identity tony@contoso.com -CallAnsweringAudioCodec Wma -CallAnsweringRulesEnabled $false -FaxEnabled $false -UMSMSNotificationOption VoiceMail

## Schritt 14: Konfigurieren Ihrer VoIP-Gateways, IP-PBX-Anlagen und SIP-fähigen PBX-Anlagen zum Senden aller eingehenden Anrufe an die Exchange 2013-Clientzugriffsserver

Werden Exchange 2013-Clientzugriffs- und Postfachserver installiert, werden sie automatisch aktiviert, damit sie ein- und ausgehende Anrufe tätigen und Voicemailnachrichten an die vorgesehenen Empfänger weiterleiten können. Nachdem Sie Ihre Exchange 2013-Clientzugriffs- und Postfachserver installiert und Unified Messaging bereitgestellt haben, müssen Sie UM-Wählplänen keine Exchange 2013-Clientzugriffs- oder Postfachserver zuordnen. Exchange 2013-Clientzugriffs- und Postfachserver beantworten alle eingehenden Anrufe und bestimmen anschließend Benutzer mithilfe von UM-Wählplänen.

Der Exchange 2013-Clientzugriffsserver ist der Einstiegspunkt für alle eingehenden Anrufe oder SIP-Anforderungen (Session Initiation Protocol) für Unified Messaging (UM). Die SIP-Anforderungen auf einem Exchange 2013-Clientzugriffsserver werden vom UM-Anrufweiterleitungsdienst verarbeitet. Dieser läuft auf allen Exchange 2013-Clientzugriffsservern in Ihrer Organisation.

Wenn Sie auf Exchange 2013-UM aktualisieren, müssen Sie bereits mindestens ein VoIP-Gateway installiert und konfiguriert haben, um eine Verbindung mit den PBX-Anlagen in Ihrem Telefonienetzwerk herzustellen, oder SIP-fähige (Session Initiation Protocol) PBX-Anlagen oder IP-PBX-Anlagen installiert und konfiguriert haben.

Der letzte Schritt in der Aktualisierung auf Exchange 2013-UM ist die Konfiguration Ihrer VoIP-Gateways, IP-PBX-Anlagen oder SIP-fähigen PBX-Anlagen für das Senden eingehender Anrufe, einschließlich Anrufer, die Voicemail für einen Benutzer hinterlassen möchten, Anrufe von UM-aktivierten Benutzern, die Outlook Voice Access anrufen, und Anrufe von Anrufern, die sich in eine automatische UM-Telefonzentrale einwählen, an Ihre Exchange 2013-Clientzugriffsserver. Diese Anrufe gehen zunächst an einem VoIP-Gateway, einer IP-PBX-Anlage oder einer SIP-fähigen PBX-Anlage ein und werden dann an die Exchange 2013-Clientzugriffsserver in Ihrer Exchange 2013-Organisation weitergeleitet. Weitere Informationen hierzu finden Sie in den folgenden Ressourcen:

  -  
    [UM-Dienste](um-services-exchange-2013-help.md)

  -  
    [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md)

  -  
    [Telefonieratgeber für Exchange 2013](telephony-advisor-for-exchange-2013-exchange-2013-help.md)

## Schritt 15: Deaktivieren der Anrufbeantwortung auf einem Exchange 2010-UM-Server

Sie können die Anrufbeantwortung durch die Deaktivierung von UM auf einem Exchange 2010-UM-Server oder durch Entfernen des UM-Servers aus einem Wählplan deaktivieren. Deaktivieren Sie UM, beantwortet der UM-Server keine eingehenden Anrufe. Sie können angeben, dass alle Anrufe sofort getrennt werden oder dass die Verarbeitung der aktuellen Anrufe abgewartet werden soll, bevor der UM-Server deaktiviert wird. Es empfiehlt sich, die Anrufbeantwortung vor dem Entfernen des Servers aus einem Wählplan zu deaktivieren, damit die Verarbeitung aller eingehenden Anrufe abgeschlossen werden kann.

So deaktivieren Sie UM auf einem Exchange 2010-UM-Server mit der Exchange-Verwaltungskonsole:

1.  Navigieren Sie in der Konsolenstruktur zu **Serverkonfiguration** \> **Unified Messaging**.

2.  Wählen Sie im Ergebnisbereich den zu deaktivierenden Unified Messaging-Server aus.

3.  Klicken Sie im Aktionsbereich auf eine der folgenden Optionen:
    
      - **Sofort deaktivieren**: Bei Auswahl dieser Option trennt der Unified Messaging-Server alle Anrufe, die mit dem Unified Messaging-Server verbunden sind.
    
      - **Nach Beenden der Anrufe deaktivieren**: Bei Auswahl dieser Option nimmt der Unified Messaging-Server keine neuen Anrufe an, wird jedoch erst deaktiviert, nachdem alle Anrufe verarbeitet wurden.

4.  Klicken Sie im Bestätigungsdialogfeld auf **Ja**, um den Vorgang fortzusetzen.

So deaktivieren Sie UM auf einem Exchange 2010-UM-Server mit der Shell durch Ausführen des folgenden Befehls:

    Disable-UMServer -Identity MyUMServer -Immediate $true


> [!TIP]
> Sie können das Cmdlet <STRONG>Disable-UMServer</STRONG> von einem Exchange 2010-UM-Server oder das Cdmlet <STRONG>Disable-UMService</STRONG> von einem Exchange 2013-Postfachserver aus verwenden, um die Anrufbeantwortung zu deaktivieren.



## Schritt 16: Entfernen eines Exchange 2010-UM-Servers aus einem Wählplan

Damit Anrufe verarbeitet werden können, muss mindestens einem UM-Wählplan ein Exchange 2010-UM-Server hinzugefügt werden. Ein UM-Server kann mehreren UM-Wählplänen hinzugefügt werden. Sie können einen Exchange 2010-UM-Server aus einem UM-Wählplan entfernen. Wenn Sie einen UM-Server aus einem Wählplan entfernen, beantwortet der UM-Server keine weiteren Anrufe und verarbeitet keine UM-Anrufe für UM-aktivierte Benutzer.

So entfernen Sie einen Exchange 2010-UM-Server mit der Exchange-Verwaltungskonsole aus einem Wählplan:

1.  Navigieren Sie in der Konsolenstruktur zu **Serverkonfiguration** \> **Unified Messaging**.

2.  Wählen Sie im Ergebnisbereich den Unified Messaging-Server aus.

3.  Klicken Sie im Aktionsbereich auf **Eigenschaften**.

4.  Klicken Sie auf der Registerkarte **UM-Einstellungen** im Abschnitt **Zugeordnete Wählpläne** auf **Entfernen**.

5.  Klicken Sie im Bestätigungsdialogfeld auf **Ja**, um den Löschvorgang des Exchange 2010-Servers aus den UM-Wähleinstellungen zu bestätigen.

6.  Klicken Sie auf **OK**, um das Eigenschaftenfenster zu schließen.

Führen Sie zur Entfernung eines Exchange 2010-UM-Servers aus einem Wählplan mithilfe der Shell folgenden Befehl aus.

    $dp= Get-UMDialPlan "MySIPDialPlan"
    $s=Get-UMServer -id MyUMServer
    $s.dialplans-=$dp.identity
    Set-UMServer -id MyUMServer -dialplans:$s.dialplans

In diesem Beispiel sind drei SIP-UIR-Wählpläne vorhanden: SipDP1, SipDP2 und SipDP3. In diesem Beispiel wird ein UM-Server mit dem Namen `MyUMServer` aus dem Wählplan "SipDP3" entfernt.

    Set-UMServer -id MyUMServer -DialPlans SipDP1,SipDP2

In diesem Beispiel sind zwei SIP-UIR-Wählpläne vorhanden: SipDP1 und SipDP2. In diesem Beispiel wird ein UM-Server mit dem Namen `MyUMServer` aus dem Wählplan "SipDP2" entfernt.

    Set-UMServer -id MyUMServer -DialPlans SipDP1


> [!TIP]
> Mit dem Cmdlet <STRONG>Set-UMServer</STRONG> in der Shell auf einem Exchange 2010-UM-Server oder dem Cmdlet <STRONG>Set-UMService</STRONG> auf einem Exchange 2013-Postfachserver können Sie einen Exchange 2010 UM-Server aus einem oder mehreren Wählplänen entfernen. Führen Sie beispielsweise zum Entfernen eines UM-Servers aus allen Wählplänen den folgenden Befehl aus: <CODE>Set-UMServer -identity MyUMServer -DialPlans $null</CODE>



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Überprüfen Sie nach der Einrichtung von UM Folgendes, um die einwandfreie Funktion sicherzustellen:

  - Ein Benutzer, den Sie für Voicemail aktiviert haben, kann sich bei Outlook Web App oder Outlook anmelden und sieht eine Willkommensmeldung für Unified Messaging (UM).

  - UM-Benutzer können Sprachnachrichten empfangen.

  - UM-Benutzer können eine Outlook Voice Access-Nummer anrufen, um E-Mails, Kalendereinträge und Voicemail anzuhören.

  - UM leitet Anrufe von außerhalb der Organisation weiter, und Sie können einen Anruf vornehmen.


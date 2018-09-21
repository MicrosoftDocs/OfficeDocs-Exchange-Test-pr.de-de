---
title: 'Aktualisieren von Exchange 2007 UM auf Exchange 2013 UM: Exchange 2013-Hilfe'
TOCTitle: Aktualisieren von Exchange 2007 Unified MESSAGING auf Exchange 2013 UM
ms:assetid: 642c922d-7e85-40f0-bb9b-0f20da692be3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn169227(v=EXCHG.150)
ms:contentKeyID: 54652694
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktualisieren von Exchange 2007 Unified MESSAGING auf Exchange 2013 UM

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Beim Aktualisieren von einer Microsoft Exchange 2007-Organisation mit Unified Messaging (UM) auf Exchange 2013 Unified Messaging sind erforderlichen Schritte und weitere Schritte aus, die bereits im Rahmen Ihrer Exchange 2007 Unified MESSAGING-Bereitstellung abgeschlossen wurden. Je nach Ihrer Umgebung Telefonie und die UM-Komponenten, die erstellt und die Unterstützung in Exchange 2007 Unified Messaging konfiguriert wurden, ist möglicherweise müssen Sie zusätzliche telephonieausrüstung Voice over IP (VoIP)-Gateways, Nebenstellenanlagen IP Private Branch Exchange (Exchange, PBX), einschließlich bereitstellen oder traditionellen oder SIP-aktivierte Nebenstellenanlagen, erstellen und konfigurieren Sie zusätzlichen UM Komponenten, die für Exchange 2013 UM benötigt werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 45-90 Minuten.

  - Stellen Sie sicher, dass Sie die entsprechenden Berechtigungen in der Exchange 2007 und Exchange 2013-Organisation erstellen und Konfigurieren aller notwendigen Komponenten verfügen.

  - Vergewissern Sie sich, dass Sie Ihre Telefoniekomponenten einschließlich VoIP-Gateways und Nebenstellenanlagen, IP-Nebenstellenanlagen oder SIP-aktivierte (Session Initiation Protocol) Nebenstellenanlagen bereitgestellt und richtig konfiguriert haben.

  - Vergewissern Sie sich, dass der Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Dienst für die Anrufweiterleitung ausgeführt wird, und der Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, korrekt installiert und konfiguriert wurden. Weitere Informationen über UM-Dienste finden Sie unter [UM-Dienste](um-services-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Wie gehen Sie dazu vor?

## Schritt 1: Herunterladen und Installieren der erforderlichen UM-Sprachpakete

UM-Sprachpakete ermöglichen Anrufern und Outlook Voice Access-Benutzern die Interaktion mit dem Voicemailsystem in mehreren Sprachen. Nachdem Sie eine zusätzliche Sprache auf einem Exchange 2013-Postfachserver installiert haben, können Anrufer und Outlook Voice Access-Benutzer E-Mail-Nachrichten in dieser Sprache wiedergeben und mit dem Voicemailsystem in dieser Sprache interagieren. Zur Bereitstellung der Sprache für eingehende Anrufe müssen Sie jedoch die erforderlichen UM-Sprachpakete auf allen Exchange 2013-Postfachservern installieren. Der Grund hierfür besteht darin, dass jeder Exchange 2013-Postfachserver eingehende Anrufe für Unified Messaging beantworten kann.

Bei der Installation eines Exchange 2013-Postfachservers wird standardmäßig das Sprachpaket für US-amerikanisches Englisch (en-US) installiert. Dabei handelt es sich um die einzige verfügbare Sprachoption für Ihre Wähleinstellungen, es sei denn, Sie installieren ein anderes UM-Sprachpaket. (Die US-englische Version kann nur entfernt werden, wenn Sie den Postfachserver vom Computer entfernen.) Nachdem Sie ein UM-Sprachpaket auf einem Exchange 2013-Postfachserver installiert haben, wird die dem Sprachpaket zugeordnete Sprache als verfügbare Option aufgelistet, wenn Sie die Standardsprache für die Wähleinstellungen konfigurieren. Standardmäßig wird aufgrund der Verknüpfung einer automatischen Telefonzentrale mit einem UM-Wählplan während der Erstellung der automatischen Telefonzentrale die Standardspracheinstellung des verknüpften UM-Wählplans verwendet. Diese Einstellung kann jedoch geändert werden, nachdem die automatische UM-Telefonzentrale erstellt wurde.


> [!NOTE]
> Wenn US-Englisch die einzige Sprache ist, die Sie für Ihre Wähleinstellungen bereitstellen möchten, können Sie diesen Schritt überspringen und mit Schritt&nbsp;2 fortfahren.



Mithilfe des Befehls setup.exe oder durch das *\<UMLanguagePack\>*.exe-Installationsprogramm ausführen, nachdem Sie das UM-Sprachpaket aus [Exchange Server 2013 UM Language Packs](https://go.microsoft.com/fwlink/p/?linkid=266542)heruntergeladen haben, können Sie UM-Sprachpakete hinzufügen. Weitere Informationen finden Sie unter [Installieren eines Sprachpakets](install-a-um-language-pack-exchange-2013-help.md).

In diesem Beispiel wird mit "Setup.exe" das UM-Sprachpaket für Japanisch (ja-JP) installiert.

    setup.exe /AddUmLanguagePack:ja-JP /s:d:\Exchange\UMLanguagePacks /IAcceptExchangeServerLicenseTerms

## Schritt 2: Verschieben der Exchange 2007-begrüßungen, ansagen, Menüs und fordert das Systempostfach Exchange 2013

Benutzerdefinierte begrüßungen, ansagen, Menüs und eingabeaufforderungen sind von Unified Messaging-Wählpläne und automatische Telefonzentralen verwendet. Das Systempostfach namens {e0dc1c29-89c3-4034-b678-e6c29d823ed9} wird erstellt, bei der Installation von Exchange 2007 oder Exchange 2013 und zur Unterstützung von Features wie beispielsweise Nachrichtengenehmigung und Suche in mehreren Postfächern verwendet wird. Dieses Systempostfach wird auch zum Speichern von Dial Plan und automatische Telefonzentrale begrüßungen, ansagen, Menüs und eingabeaufforderungen verwendet. Wenn das Systempostfach nicht vorhanden ist, können Sie den Befehl **Setup/PrepareAD** , um zu erstellen.

Systempostfächer werden standardmäßig nicht im Exchange Admin Center angezeigt. Eine Liste der Systempostfächer können Sie mit einer der nachstehenden Methoden abrufen:

Mit diesem Befehl wird eine Liste aller Systempostfächer angezeigt.

```powershell
Get-Mailbox -Arbitration
```

Mit diesem Befehl wird eine Liste der Systempostfächer und den dazugehörigen individuellen Eigenschaften und Einstellungen angezeigt.

```powershell
Get-Mailbox -Arbitration |fl
```

Wenn Sie benutzerdefinierte begrüßungen, ansagen, Menüs und eingabeaufforderungen von Exchange 2007 auf Exchange 2013 importieren, müssen Sie das Skript MigrateUMCustomPrompts.ps1 verwenden. Sie können keine der Exchange-Verwaltungskonsole verwenden, um benutzerdefinierte begrüßungen, ansagen, Menüs und eingabeaufforderungen importieren. Das MigrateUMCustomPrompts.ps1-Skript migriert eine Kopie des Exchange Server 2007 UM benutzerdefinierte begrüßungen, ansagen, Menüs und eingabeaufforderungen in Exchange 2013 UM. Standardmäßig wird das Skript MigrateUMCustomPrompts.ps1 befindet sich im Ordner \\Microsoft\\Exchange Server\\V15\\Scripts *\<Program Files\>*auf einem Exchange 2013-Postfachserver und muss von einem Exchange 2013-Postfachserver ausgeführt werden. Ausführen des Skripts:

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange Server 2013** \> **Exchange-Verwaltungsshell**.

2.  Geben Sie in der Exchange-Verwaltungsshell Sie an der Eingabeaufforderung den Pfad des Skripts ein. Beispielsweise geben Sie **cd "d:\\Programme\\Microsoft zum Verzeichnis c:\\Programme\\Microsoft\\Exchange Server\\V15\\Scripts"**, und drücken Sie die EINGABETASTE.

3.  Geben Sie an der Eingabeaufforderung Shell **". \\MigrateUMCustomPrompts"**, und drücken Sie dann die EINGABETASTE.


> [!NOTE]
> Benutzerdefinierte Ansagen können auch mithilfe des Cmdlets <STRONG>Import-UMPrompt</STRONG> einzeln importiert werden. Mit dem Exchange 2007 Unified MESSAGING- <STRONG>Copy-UMCustomPrompt</STRONG> -Cmdlet wird nicht unterstützt, zum Kopieren von benutzerdefinierter Ansagen in Exchange 2013 UM.



Beim Ausführen des Skripts MigrateUMCustomPrompts.ps1 aus Ihrem Exchange 2013-Server führt eine GUID oder -Objekt-ID-Suche für den Wählplan durch das Skript oder automatische Telefonzentrale in Active Directory und Abfragen, um zu ermitteln, ob eine beliebige benutzerdefinierte begrüßungen, ansagen, Menüs oder Anweisungen. Wenn gefunden, die benutzerdefinierte begrüßungen, ansagen, Menüs und eingabeaufforderungen in das Postfach mit dem Namen {e0dc1c29-89c3-4034-b678-e6c29d823ed9} importiert werden sollen.

Mithilfe dieses Systempostfachs können benutzerdefinierte Begrüßungen, Ansagen Menüs und Eingabeaufforderungen zusammen mit anderen Postfächern in einer Datenbank gesichert und wiederhergestellt werden. Dadurch werden die benötigten Ressourcen verringert. Mit dem Speichern von benutzerdefinierten Begrüßungen, Ansagen, Menüs und Eingabeaufforderungen in einem Systempostfach werden möglicherweise aufgetretene Inkonsistenzen beseitigt. Weitere Informationen zu Postfachverschiebungen finden Sie unter [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md).

## Schritt 3: Exportieren und Importieren von Zertifikaten

Falls Sie SIP-gesicherte oder gesicherte in Ihrer Organisation Exchange 2007 Wähleinstellungen, müssen Sie exportieren und Importieren von Zertifikaten, die verwendet wurden auf Ihren Exchange 2013-Clientzugriffsserver und Postfachserver Servern. Mutual Transport Layer Security (MTLS) wird zum Verschlüsseln von Daten, die zwischen Ihren Exchange 2013-Servern und VoIP-Gateways, IP-PBX-Anlagen gesendet und SIP-aktivierte Nebenstellenanlagen. Zertifikate binden die Identität des Zertifikatbesitzers auf ein Paar von elektronischen Schlüsseln (öffentliche und private), die zum Verschlüsseln und digitales Signieren von Informationen verwendet werden. Sie können eine der folgenden Zertifikate für die UM- und UM-Anrufrouter Dienste verwenden:

  - Ein selbstsigniertes (Exchange-)Zertifikat

  - Ein internes PKI-Zertifikat (Public Key Infrastructure)

  - Ein kommerzielles Zertifikat eines Drittanbieters

Standardmäßig werden bei der Installation von Exchange 2013 zwei selbstsignierte Zertifikate erstellt: **Microsoft Exchange Server Auth Certificate** und **Microsoft Exchange**. Das selbstsignierte **Microsoft Exchange**-Zertifikat kann für UM zur Datenverschlüsselung verwendet werden. Sie müssen das Zertifikat jedoch den UM- und UM-Anrufweiterleitungsdiensten zuweisen. Dieses selbstsignierte Zertifikat kann kopiert und anschließend in die VoIP-Gateways, IP-PBX-Anlagen und SIP-fähigen PBX-Anlagen importiert werden. Es kann jedoch nicht für die Integration von UM mit Microsoft Lync Server eingesetzt werden.

Führen Sie die folgenden Schritte aus, um UM das Verschlüsseln von Daten zu ermöglichen, die zwischen Ihren Exchange 2013-Servern und VoIP-Gateways, IP-PBX-Anlagen und SIP-fähigen PBX-Anlagen gesendet werden:

  - Verwenden Sie ein vorhandenes selbstsigniertes Zertifikat UM, Erstellen eines neuen selbstsignierten Exchange-Zertifikats, Anfordern eines Zertifikats auf einer internen Zertifizierungsstelle für ein PKI-Zertifikat, oder erwerben Sie ein kommerzielles Zertifikat von Drittanbietern, das Sie für mutual TLS zwischen Ihrer Exchange 2013 Postfach- und Clientzugriffs-Servern und VoIP-Gateways, IP-PBX-Anlagen und SIP-aktivierte Nebenstellenanlagen verwenden können.
    
    Erstellen Sie wie folgt ein selbstsigniertes Exchange-Zertifikat mit der Exchange-Verwaltungskonsole:
    
    1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Zertifikate**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").
    
    2.  Wählen Sie auf der Seite **Neues Exchange-Zertifikat** die Option **Selbstsigniertes Zertifikat erstellen** aus, und klicken Sie dann auf **Weiter**.
    
    3.  Geben Sie einen Anzeigenamen für das Zertifikat ein, und klicken Sie dann auf **Weiter**.
    
    4.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Exchange-Server auszuwählen, denen dieses Zertifikat zugewiesen werden soll, und klicken Sie dann auf **Weiter**.
    
    5.  Geben Sie die Domänen an, die Sie in das Zertifikat aufnehmen möchten, und klicken Sie dann auf **Weiter**. Möchten Sie eine Domäne für einen Dienst hinzufügen, klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    6.  Vergewissern Sie sich, dass die richtigen Domänen angegeben sind, und klicken Sie dann auf **Fertig stellen**.
    

    > [!IMPORTANT]
    > Wenn Sie ein Zertifikat mit der Exchange-Verwaltungskonsole erstellen, werden Sie nicht zur Aktivierung der Dienste für das Zertifikat aufgefordert. Nach der Erstellung des Zertifikats können Sie die Dienste mit der Exchange-Verwaltungskonsole aktivieren. Weitere Informationen zur Aktivierung eines Zertifikats für Dienste finden Sie unter <A href="assign-a-certificate-to-the-um-and-um-call-router-services-exchange-2013-help.md">Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst</A>.

    
    Erstellen Sie ein selbstsigniertes Exchange-Zertifikat, indem Sie in der Shell den folgenden Befehl ausführen.
    
        New-ExchangeCertificate -Services 'UM, UMCallRouter' -DomainName '*.northwindtraders.com' -FriendlyName 'UMSelfSigned' -SubjectName 'C=US,S=WA,L=Redmond,O=Northwindtraders,OU=Servers,CN= Northwindtraders.com' -PrivateKeyExportable $true
    

    > [!TIP]
    > Wenn Sie die zu aktivierenden Dienste mit dem Parameter <EM>Services</EM> angeben, werden Sie zur Aktivierung der Dienste für das erstellte Zertifikat aufgefordert. In diesem Beispiel werden Sie zur Aktivierung des Zertifikats für die UM- und UM-Anrufweiterleitungsdienste aufgefordert. Weitere Informationen zur Aktivierung eines Zertifikats für Dienste finden Sie unter <A href="assign-a-certificate-to-the-um-and-um-call-router-services-exchange-2013-help.md">Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst</A>.



  - Importieren Sie das Zertifikat, das auf allen Servern mit Exchange 2013-Clientzugriffsserver und Postfachserver in Ihrer Organisation verwendet werden soll. Wenn Sie das selbstsignierte Zertifikat von Exchange 2013 verwenden, müssen Sie kopieren Sie das Zertifikat, und klicken Sie dann auf die VoIP-Gateways, IP-Nebenstellenanlagen oder SIP-aktivierte Nebenstellenanlagen importieren. Wenn Sie das selbstsignierte Zertifikat von Exchange 2007 verwenden, muss das Subject Alternative Name (SAN) den Namen des Computers, der alle Exchange 2013-Server enthalten. Wenn Sie Exchange 2007 Unified Messaging-Server in Ihrer Organisation verfügen, können Sie das selbstsignierte Zertifikat von Exchange 2013, jedoch müssen Sie den Namen des Computers, der Exchange 2007 Unified MESSAGING-Server mit dem SAN des Zertifikats Exchange 2013 hinzufügen.

  - Aktivieren Sie das Zertifikat, das für die UM- und UM-Anrufweiterleitungsdienste auf den Clientzugriffs- und Postfachservern in Ihrer Organisation verwendet werden soll, oder weisen Sie es zu.
    
    Aktivieren Sie den UM-Dienst und den UM-Anrufrouter-Dienst auf allen Exchange 2013-Servern das selbstsignierte Zertifikat von Exchange mithilfe der Exchange-Verwaltungskonsole wie folgt:
    
    1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Zertifikate**, wählen Sie das Zertifikat aus, für das Dienste aktiviert werden sollen, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    2.  Wählen Sie auf der Seite **Verfahren** die Option **Dienste** aus, wählen Sie **Unified Messaging** und dann **Unified Messaging-Anrufweiterleitung**.
    
    Aktivieren Sie ein selbstsigniertes Exchange-Zertifikat, indem Sie in der Shell den folgenden Befehl ausführen.
    
        Enable-ExchangeCertificate -Thumbprint 5113ae0233a72fccb75b1d0198628675333d010e -Services 'UM, UMCallRouter'

  - Konfigurieren Sie alle neuen oder bestehenden UM-Wählpläne als "SIP-gesichert" oder "Gesichert".

  - Konfigurieren Sie den UM-Startmodus auf den Clientzugriffs- und Postfachservern in Ihrer Organisation als "TLS" oder "Dual"

  - Erstellen und konfigurieren Sie neue oder bestehende UM-IP-Gateways mit einem vollständig qualifizierten Domänennamen (FQDN).

  - Konfigurieren Sie den Überwachungsport für die UM-IP-Gateways für die Verwendung von TCP-Port 5061.

  - Starten Sie den UM-Anrufweiterleitungsdienst auf allen Exchange 2013-Clientzugriffsservern neu, und starten Sie den UM-Dienst auf allen Exchange 2013-Postfachservern neu. Weitere Informationen über UM-Dienste finden Sie unter [UM-Dienste](um-services-exchange-2013-help.md).

## Schritt 4: Konfigurieren des UM-Startmodus auf allen Exchange 2013-Clientzugriffsservern

Falls Sie SIP-gesicherte oder gesicherte Wähleinstellungen, müssen Sie den UM-Startmodus auf Ihren Exchange 2013-Clientzugriffs-Servern konfigurieren. Sie können den UM-Startmodus für den UM-Anrufrouter-Dienst auf einem Exchange 2013-Clientzugriffs-Server mithilfe der Exchange-Verwaltungskonsole oder der Shell angeben. Standardmäßig wird der Exchange 2013-Clientzugriffsserver im TCP-Modus gestartet, aber wenn Sie zum Verschlüsseln von Voice over IP (VoIP) Datenverkehr Transport Layer Security (TLS) verwenden, müssen Sie den Exchange 2013-Clientzugriffsserver Verwendung von TLS oder Dual-Modus konfigurieren. Es wird empfohlen, dass allen Exchange 2013-Clientzugriffsservern konfiguriert werden, um als der UM-Startmodus Dual verwenden. Dies ist, da alle Exchange 2013-Clientzugriffsservern Beantworten eingehender Anrufe für alle UM-Wählpläne und diejenigen Wählpläne können verschiedene Sicherheitseinstellungen haben können. Wenn Sie den UM-Startmodus ändern, müssen Sie den UM-Anrufrouter Dienst für die Änderung wirksam wird neu starten. Weitere Informationen zu UM-Dienste finden Sie unter [UM-Dienste](um-services-exchange-2013-help.md).

Konfigurieren Sie den UM-Startmodus auf einem Exchange 2013-Clientzugriffsserver mit der Exchange-Verwaltungskonsole wie folgt:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Wählen Sie unter **UM-Anrufroutereinstellungen** \> **UM-Startmodus** in der Dropdownliste eine der folgenden Optionen aus:
    
      - **TCP**   Verwenden Sie diese Option, wenn Sie kein mTLS verwenden und nur ungesicherte Wählpläne einsetzen.
    
      - **TLS**    Verwenden Sie diese Option, wenn Sie mTLS verwenden und nur SIP-gesicherte oder gesicherte Wähleinstellungen.
    
      - **DUALE**    Verwenden Sie diese Option, wenn Sie mTLS verwenden und Unsecured, SIP-gesicherte, verwenden und Secured Wähleinstellungen.

5.  Nachdem Sie den UM-Startmodus ausgewählt haben, klicken Sie auf **Speichern**.

Konfigurieren Sie den UM-Startmodus auf einem Exchange 2013-Clientzugriffsserver durch die Ausführung des folgenden Befehls in der Shell.

```powershell
Set-UMCallRouterSettings -Server MyUMCallRouter.northwindtraders.com -UMStartupMode Dual
```

## Schritt 5: Konfigurieren des UM-Startmodus auf allen Exchange 2013-Postfachservern

Wenn Sie SIP-gesicherte oder gesicherte Wählpläne verwenden, müssen Sie den UM-Startmodus auf Ihren Exchange 2013-Postfachservern konfigurieren. Sie können den UM-Startmodus für den UM-Dienst auf einem Exchange 2013-Postfachserver angeben, indem Sie die Exchange-Verwaltungskonsole oder die Shell verwenden. Standardmäßig wird der Exchange 2013-Postfachserver im TCP-Modus gestartet. Wenn Sie jedoch TLS (Transport Layer Security) zum Verschlüsseln von VoIP-Datenverkehr (Voice over IP) verwenden, müssen Sie den Exchange 2013-Postfachserver so konfigurieren, dass der TLS- oder der Dualmodus verwendet wird. Es wird empfohlen, alle Exchange 2013-Postfachserver für den UM-Startmodus "Dual" zu konfigurieren. Der Grund hierfür besteht darin, dass alle Exchange 2013-Postfachserver eingehende Anrufe für alle UM-Wählpläne beantworten können, diese Wählpläne jedoch unterschiedliche Sicherheitseinstellungen aufweisen können. Wenn Sie den UM-Startmodus ändern, müssen Sie den UM-Dienst erneut starten, damit die Änderung wirksam wird. Weitere Informationen über UM-Dienste finden Sie unter [UM-Dienste](um-services-exchange-2013-help.md).

Konfigurieren Sie den UM-Startmodus auf einem Exchange 2013-Postfachserver mit der Exchange-Verwaltungskonsole wie folgt:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Wählen Sie unter **UM-Diensteinstellungen** \> **UM-Startmodus** eine der folgenden Optionen aus der Dropdownliste aus:
    
      - **TCP**   Verwenden Sie diese Option, wenn Sie kein mTLS verwenden und nur ungesicherte Wählpläne einsetzen.
    
      - **TLS**    Verwenden Sie diese Option, wenn Sie mTLS verwenden und nur SIP-gesicherte oder gesicherte Wähleinstellungen.
    
      - **DUALE**    Verwenden Sie diese Option, wenn Sie mTLS verwenden und Unsecured, SIP-gesicherte, verwenden und Secured Wähleinstellungen.

5.  Nachdem Sie den UM-Startmodus ausgewählt haben, klicken Sie auf **Speichern**.

Konfigurieren Sie den UM-Startmodus auf einem Exchange 2013-Postfachserver durch die Ausführung des folgenden Befehls in der Shell.

    Set-UMService -Identity MyUMServer -ExternalHostFqdn host.external.contoso.com -IPAddressFamily Any -UMStartupMode Dual

## Schritt 6: Erstellen Sie oder konfigurieren Sie vorhandener um-Wählpläne

Abhängig von Ihrer vorhandenen Exchange 2007-Bereitstellung müssen Sie auf neue um-Wählpläne erstellen oder vorhandene Wählplänen konfigurieren. Ein Wählplan stellt eine Reihe von traditionellen oder SIP-aktivierte Private Nebenstellenanlagen (PBX), IP-Nebenstellenanlagen oder SIP-aktivierte Nebenstellenanlagen, die häufige Durchwahlnummern für Benutzer freigeben. Allen Benutzern Extensions auf traditionellen oder SIP-aktivierte Nebenstellenanlagen oder IP-Nebenstellenanlagen innerhalb eines Wählplans gehostet enthalten die gleiche Anzahl von Ziffern. Benutzer können jeweils anderen Person per Telefon Extensions einwählen, ohne die Erweiterung wie eine besondere Nummer angefügt oder eine vollständige Telefonnummer gewählt.

Um-Wählpläne werden in Unified Messaging verwendet, um sicherzustellen, dass Benutzer Telefon Extensions eindeutig sind. In einigen Telefonienetzwerken vorhanden mehrere IP-Nebenstellenanlagen, herkömmliche Nebenstellenanlagen oder SIP-fähigen PBX-Anlagen. In dieser Netzwerke Telefonie könnten zwei Benutzer mit demselben Telefondurchwahl vorhanden sein. Um-Wählplänen auflösen diese situation Zwei separate Wählplänen die beiden Benutzer Inbetriebnahme macht ihren Erweiterungen eindeutig. Weitere Informationen finden Sie unter [UM-Wählpläne](https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/um-dial-plans).

Sie können gegebenenfalls einen UM-Wählplan mit der Exchange-Verwaltungskonsole erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, und klicken Sie dann auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Führen Sie auf der Seite **Neue UM-Wählplan** die folgenden Schritte aus:
    
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

```powershell
New-UMDialplan -Name MyUMDialPlan -URIType E164 -NumberOfDigitsInExtension 5 -VoIPSecurity Secured
```

Falls erforderlich, können Sie einen vorhandenen UM-Wählplan mithilfe der Exchange-Verwaltungskonsole konfigurieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie anzeigen oder ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**. Nutzen Sie die Konfigurationsoptionen zur Anzeige bestimmter Wählplaneinstellungen und zur Aktivierung beziehungsweise Deaktivierung von Funktionen.

Falls erforderlich, können Sie einen vorhandenen UM-Wählplan mithilfe des folgenden Befehls in der Shell konfigurieren.

    Set-UMDialplan -Identity MyDialPlan -AccessTelephoneNumbers 4255551234 -AudioCodec Wma -CallAnsweringRulesEnabled $false -OutsideLineAccessCode 9 -VoIPSecurity SIPSecured

Wenn Sie Exchange 2007 Unified Messaging bereitgestellt haben, mussten Sie Hinzufügens von Unified Messaging-Servers zu einem um-Wählplan für die eingehende Anrufe entgegennehmen. Dies ist nicht mehr erforderlich. In Exchange 2013 Clientzugriffs-und Postfachservern können nicht verknüpft werden mit Durchwahl oder e. 164-Wählplan, aber mit SIP-URI-Wählpläne verknüpft sein. Clientzugriffs-und Postfachserver werden für alle Typen von Wählplänen alle eingehenden Anrufe beantworten.

## Schritt 7: Erstellen Sie oder konfigurieren Sie vorhandener UM-IP-gateways

Abhängig von Ihrer vorhandenen Exchange 2007-Bereitstellung müssen Sie zum Erstellen neuer UM-IP-Gateways oder Ihre vorhandene Datenbanken konfiguriert. Wenn Sie SIP-gesicherte oder gesicherte Wähleinstellungen, müssen Sie erstellen ein UM-IP-Gateway mit dem FQDN und mithilfe der Shell konfigurieren anhören Port 5061. Vorhandene UM-IP-Gateways stellen Sie sicher, dass sie mit einem FQDN konfiguriert sind, und Port 5061 überwacht werden. Bei das UM-IP-Gateway einen vollqualifizierten Domänennamen nicht verwendet werden, die Adresse ändern der Exchange-Verwaltungskonsole oder der Shell. Falls der UM-IP-Gateways nicht Port 5061 verwendet, mithilfe der Shell um den Port zu ändern. Sie können die Einstellungen des UM-IP-Gateways mithilfe des **Get-UMIPGateway** Cmdlets anzeigen.

Ein UM-IP-Gateway stellt ein physisches VoIP-Gateway (Voice over IP), eine IP-PBX-Anlage oder eine SIP-fähige PBX-Anlage dar. Ehe ein VoIP-Gateway, eine IP-PBX-Anlage oder eine SIP-fähige PBX-Anlage zum Annehmen eingehender Anrufe und zum Senden ausgehender Anrufe für Voicemailbenutzer genutzt werden kann, muss im Verzeichnisdienst ein UM-IP-Gateway erstellt werden.

Durch die Kombination des UM-IP-Gateways mit einem UM-Sammelanschluss wird eine Verknüpfung zwischen einem VoIP-Gateway, einer IP-PBX-Anlage oder einer SIP-fähigen PBX-Anlage und einem UM-Wählplan eingerichtet. Durch Erstellen mehrerer UM-Sammelanschlüsse kann ein einzelnes UM-IP-Gateway mehreren UM-Wähleinstellungen zugeordnet werden. Weitere Informationen finden Sie unter [UM-IP-Gateways](https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/um-ip-gateways).

Sie können gegebenenfalls ein UM-IP-Gateway mit der Exchange-Verwaltungskonsole erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie auf der Seite **Neues UM-IP-Gateway** die folgenden Informationen ein:
    
      - **Name**   Geben Sie in diesem Feld einen eindeutigen Namen für das UM-IP-Gateway ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Namen des UM-IP-Gateways nach dem Erstellen ändern müssen, muss zuerst das vorhandene UM-IP-Gateway gelöscht und dann ein anderes UM-IP-Gateway mit dem entsprechenden Namen erstellt werden. Der UM-IP-Gatewayname ist erforderlich, wird aber nur zur Anzeige verwendet. Da in Ihrer Organisation unter Umständen mehrere UM-IP-Gateways verwendet werden, sollten Sie aussagekräftige Namen für Ihre UM-IP-Gateways verwenden. Die maximale Länge eines UM-IP-Gatewaynamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **Adresse**   Sie können ein UM-IP-Gateway mit einer IPv4- oder IPv6-Adresse oder mit einem FQDN konfigurieren. Verwenden Sie dieses Feld, um die auf VoIP-Gateway, IP-PBX-Anlage oder SIP-fähiger PBX-Anlage konfigurierte IP-Adresse oder einen vollqualifizierten Domänennamen (FQDN) anzugeben. In dieses Textfeld können nur gültige FQDNs eingegeben werden, die ordnungsgemäß formatiert sind.
        
        Sie können alphabetische und numerische Zeichen eingeben. IPv4-Adressen, IPv6-Adressen und FQDNs werden unterstützt. Wenn Sie mutual TLS zwischen einer UM-IP-Gateways verwenden möchten, und einem Wählplan Betrieb SIP-gesichert oder Modus gesichert, müssen Sie die UM-IP-Gateways mit einem vollqualifizierten Domänennamen konfigurieren. Sie müssen auch konfigurieren, um zu Lauschen Port 5061, und stellen Sie sicher, dass alle VoIP-Gateways oder IP-PBX-Anlagen auch Port 5061 mutual TLS-Anforderungen abzuhören konfiguriert wurde. Führen Sie den folgenden Befehl in der Shell, um ein UM-IP-Gateway zu konfigurieren: `Set-UMIPGateway -identity MyUMIPGateway -Port 5061`
        
        Wenn Sie einen FQDN verwenden, müssen Sie außerdem sicherstellen, dass Sie für das VoIP-Gateway, die IP-PBX-Anlage oder die SIP-fähige PBX-Anlage einen gültigen DNS-Hosteintrag konfiguriert haben, sodass der Hostname fehlerfrei in eine IP-Adresse aufgelöst werden kann. Auch wenn Sie anstelle einer IP-Adresse einen vollqualifizierten Domänennamen (FQDN) verwenden und die DNS-Konfiguration für das UM-IP-Gateway ändern, müssen Sie das UM-IP-Gateway deaktivieren und erneut aktivieren, um sicherzustellen, dass die Konfigurationsinformationen für das UM-IP-Gateway ordnungsgemäß aktualisiert werden.
    
      - **UM-Wählplan**   Klicken Sie auf **Durchsuchen**, um den UM-Wählplan auszuwählen, den Sie dem UM-IP-Gateway zuordnen möchten. Wenn Sie einen UM-Wählplan für die Zuordnung zu einem UM-IP-Gateway auswählen, wird außerdem ein UM-Sammelanschluss erstellt und diesem UM-Wählplan zugeordnet. Wenn Sie keinen UM-Wählplan auswählen, müssen Sie manuell einen UM-Sammelanschluss erstellen und diesen dann einem erstellten UM-IP-Gateway zuordnen.

3.  Klicken Sie auf **Speichern**.

Falls erforderlich, können Sie eine UM-IP-Gateways mithilfe des folgenden Befehls in der Shell erstellen.

```powershell
New-UMIPGateway -Identity MyUMIPGateway -Address "MyUMIPGateway.contoso.com"
```

Falls erforderlich, können Sie einer vorhandenen UM-IP-Gateways mithilfe der Exchange-Verwaltungskonsole konfigurieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-IP-Gateway** auf **Konfigurieren**. Nutzen Sie die Konfigurationsoptionen zur Anzeige bestimmter UM-IP-Gatewayeinstellungen und zur Aktivierung beziehungsweise Deaktivierung von Funktionen.

Gegebenenfalls können Sie einen vorhandenen UM-IP-Gateways mithilfe des folgenden Befehls in der Shell konfigurieren.

    Set-UMIPGateway -Identity MyUMIPGateway -Address fe80::39bd:88f7:6969:d223%11 -IPAddressFamily Any -Status Disabled -OutcallsAllowed $false

## Schritt 8: Erstellen eines um-Sammelanschlusses

Abhängig von Ihrer vorhandenen Exchange 2007-Bereitstellung möglicherweise Sie zum Erstellen neuer UM-Sammelanschlüsse erforderlich. Ein Sammelanschluss Telefonie bietet eine Möglichkeit zum Verteilen Telefonanrufe über eine einzelne Zahl auf mehrere Erweiterungen oder Telefonnummern. In Unified Messaging ein um-Sammelanschlusses ist eine logische Darstellung eines Sammelanschlusses Telefonie, und es einen UM-IP-Zugang zu einem um-Wählplan verknüpft.

Sie benötigen mindestens einen UM-Sammelanschluss für jeden IP-PBX- oder PBX-Sammelanschluss. Wenn Sie das folgende Verfahren abschließen, wird ein UM-Sammelanschluss standardmäßig erstellt. Wenn Sie über mehrere IP-PBX- oder PBX-Sammelanschlüsse verfügen, müssen Sie zusätzliche UM-Sammelanschlüsse erstellen. Weitere Informationen zu UM-Sammelanschlüssen finden Sie unter [UM-Sammelanschlüsse](https://technet.microsoft.com/de-de/library/Aa995918(v=EXCHG.150)).

Falls erforderlich, können Sie einen um-Sammelanschluss mithilfe der Exchange-Verwaltungskonsole erstellen:

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



## Schritt 9: Erstellen Sie oder konfigurieren Sie der automatischen UM-Telefonzentralen

Abhängig von Ihrer vorhandenen Exchange 2007-Bereitstellung müssen Sie neue automatische um-Telefonzentralen erstellen. Automatische um-Telefonzentralen kann zum Erstellen einer VoIP-Menüsystem, mit der, externen und internen Aufrufer verwenden das Menüsystem UM Auto attendant zum Auffinden der Ansprechpartner und tätigen oder durchstellen von Anrufen an Unternehmen Benutzer oder Abteilungen in einer Organisation. Weitere Informationen finden Sie unter [Automatisches Beantworten und Weiterleiten eingehender Anrufe](https://technet.microsoft.com/de-de/library/Bb124724(v=EXCHG.150)).

In kleinere Bereitstellungen können Sie nur UM bereitstellen möchten, damit Anrufer Voicemail für Benutzer lassen können. Erstellen eine automatische Telefonzentrale nicht in dieser Bereitstellung erforderlich. In den meisten Fällen die Verwendung ist jedoch automatischen Telefonzentralen sehr nützlich für externe Anrufer beim Aufruf Ihrer Organisation.

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

Gegebenenfalls können Sie eine vorhandene automatische Telefonzentrale mithilfe der Exchange-Verwaltungskonsole konfigurieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie anzeigen oder konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Nutzen Sie die Konfigurationsoptionen zur Anzeige bestimmter Einstellungen für automatische Telefonzentralen und zur Aktivierung beziehungsweise Deaktivierung von Funktionen.

Sie können gegebenenfalls eine vorhandene automatische Telefonzentrale durch Ausführen des folgenden Befehls in der Shell konfigurieren.

    Set-UMAutoAttendant -Identity MySpeechEnabledAA -DTMFFallbackAutoAttendant MyDTMFAA -OperatorExtension 50100 -AfterHoursTransferToOperatorEnabled $true -StaroutToDialPlanEnabled $true

## Schritt 10: Erstellen oder Konfigurieren von UM-Postfachrichtlinien

Abhängig von Ihrer vorhandenen Exchange 2007-Bereitstellung müssen Sie auf neue UM-Postfachrichtlinien erstellen oder vorhandene UM-Postfachrichtlinien zu konfigurieren. UM-Postfachrichtlinien sind erforderlich, wenn Sie Benutzer für Unified Messaging aktivieren. Das Postfach von einzelnen UM-aktivierten Benutzer muss mit einem einzelnen UM-Postfachrichtlinie verknüpft werden. Nachdem Sie eine um-Postfachrichtlinie erstellen, verknüpfen Sie mindestens einen UM-aktivierten Postfächer mit UM-Postfachrichtlinie. Hiermit können Sie steuern, PIN-Sicherheitseinstellungen wie die minimale Anzahl von Ziffern in eine PIN-NUMMER oder der maximale Anzahl der Anmeldeversuche für UM-aktivierten Benutzer, die mit der UM-Postfachrichtlinie verknüpft sind. Weitere Informationen finden Sie unter [UM-Postfachrichtlinien](https://technet.microsoft.com/de-de/library/Bb124909(v=EXCHG.150)).

Sie können gegebenenfalls eine UM-Postfachrichtlinie mit der Exchange-Verwaltungskonsole erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wähleinstellungen** unter **UM-Postfachrichtlinien** auf **Hinzufügen** ![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **Neue UM-Postfachrichtlinie** im Textfeld **Name** den Namen der neuen UM-Postfachrichtlinie ein.
    

    > [!NOTE]
    > Geben Sie in dieses Feld einen eindeutigen Namen für die UM-Postfachrichtlinie ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Anzeigenamen der UM-Postfachrichtlinie nach dem Erstellen ändern müssen, muss zuerst die vorhandene UM-Postfachrichtlinie gelöscht und dann eine andere UM-Postfachrichtlinie mit dem entsprechenden Namen erstellt werden. Sie können keine UM-Postfachrichtlinie löschen, solange UM-aktivierte Benutzer damit verknüpft sind. Es muss ein UM-Postfachrichtlinienname angegeben werden, er wird jedoch nur zu Anzeigezwecken verwendet. Wenn in Ihrer Organisation mehrere UM-Postfachrichtlinien verwendet werden, empfiehlt sich die Verwendung sinnvoller Namen für die UM-Postfachrichtlinien. Die maximale Länge eines UM-Postfachrichtliniennamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \ [ ] : ; | = , + * ? &lt; &gt;.



4.  Klicken Sie auf **Speichern**.
    

    > [!NOTE]
    > Beim Speichern der UM-Postfachrichtlinie sind alle die Standardeinstellungen, einschließlich PIN-Richtlinien, Voicemail-Features und Einstellungen für geschützte Voicemail aktiviert. Wenn Sie anpassen oder alle Standardeinstellungen für die um-Postfachrichtlinie gerade erstellten ändern möchten, verwenden Sie das Cmdlet <STRONG>Set-UMMailbox</STRONG> oder der Exchange-Verwaltungskonsole.



Falls erforderlich, können Sie eine um-Postfachrichtlinie in der Shell erstellen, indem Sie den folgenden Befehl ausführen.

```powershell
New-UMMailboxPolicy -Name MyUMMailboxPolicy -UMDialPlan MyUMDialPlan
```

Sie können gegebenenfalls eine vorhandenen UM-Postfachrichtlinie mit der Exchange-Verwaltungskonsole konfigurieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie anzeigen oder konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Nutzen Sie die Konfigurationsoptionen zur Anzeige bestimmter UM-Postfachrichtlinieneinstellungen und zur Aktivierung beziehungsweise Deaktivierung von Funktionen.

Sie können gegebenenfalls eine vorhandene UM-Postfachrichtlinie durch Ausführen des folgenden Befehls in der Shell konfigurieren.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 8 -MaxLogonAttempts 12 -MinPINLength 8 -PINHistoryCount 10 -PINLifetime 60 -ResetPINText "The PIN used to allow you access to your mailbox using Outlook Voice Access has been reset."

## Schritt 11: Verschieben Sie vorhandene UM-aktivierte Postfächer nach Exchange 2013

In Exchange wird 2007 Unified Messaging, nachdem Sie Benutzer innerhalb der Organisation verwenden von Voicemail, einen Standardsatz Eigenschaften für UM aktiviert haben, die dem Benutzer angewendet, sodass diese UM-Features verwenden können. Weitere Informationen finden Sie unter [Voicemail für Benutzer](https://technet.microsoft.com/de-de/library/Aa997885(v=EXCHG.150)).

Während des Aktivierungsvorgangs upgraden werden eine bestimmten Zeitspanne während der Sie Postfächer verfügen werden, DIE UM auf Exchange 2007-Postfachservern sowohl auf Exchange 2013-Postfachservern aktiviert sind. Wenn Sie alle UM-aktivierten Benutzer auf Exchange 2013-Postfachservern über verschieben möchten, müssen Sie jedoch der Exchange-Verwaltungskonsole oder **New-MoveRequest** -Cmdlet in der Shell aus einem Exchange 2013-Server verwenden, die alle Eigenschaften und Einstellungen, einschließlich der PIN des Benutzers beibehalten werden.

Als Verschiebungsanforderung wird das Verschieben eines Postfachs von einer Postfachdatenbank in eine andere bezeichnet. Eine lokale Verschiebungsanforderung ist eine Postfachverschiebung, die in einer einzelnen Gesamtstruktur erfolgt. Weitere Informationen zum Verschieben von Postfächern finden Sie unter:

  - [Postfachverschiebungen in Exchange 2013](mailbox-moves-in-exchange-2013-exchange-2013-help.md)

  - [New-MoveRequest](https://technet.microsoft.com/de-de/library/dd351123\(v=exchg.150\))

  - [New-MigrationBatch](https://technet.microsoft.com/de-de/library/jj219166\(v=exchg.150\))

  - [Verschieben von Postfächern](https://go.microsoft.com/fwlink/p/?linkid=296351)

So verschieben Sie ein Exchange 2007-Postfach mit einem Exchange 2013 Mailbox-Server mithilfe der Exchange-Verwaltungskonsole:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger** \> **Migration** und dann auf **Hinzufügen**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie im Assistenten für neue lokale Postfachverschiebungendie zu verschiebenden Benutzer aus, und klicken Sie auf **OK** und anschließend auf **Weiter**.

3.  Geben Sie auf der Seite **Konfiguration verschieben** einen Namen für den neuen Batch ein. Wählen Sie die gewünschten Optionen für das Archivpostfach sowie den Speicherort der Postfachdatenbank aus, und klicken Sie auf **Neu**.

Führen Sie den folgenden Befehl, um ein Exchange 2007-Postfach mithilfe der Shell auf einen Exchange 2013-Postfachserver zu verschieben.

```powershell
New-MoveRequest -Identity 'tony@alpineskihouse.com' -TargetDatabase "DB01"
```

## Schritt 12: Aktivieren neuer Benutzer für UM oder Konfigurieren von Einstellungen für einen vorhandenen UM-aktivierten Benutzer

Ein Benutzer muss über ein Postfach verfügen, bevor eine Aktivierung für Unified Messaging durchgeführt werden kann. Standardmäßig ist ein Benutzer, der über ein Postfach verfügt, nicht für Unified Messaging aktiviert. Nach der UM-Aktivierung können Sie die UM-Eigenschaften und Voicemailfunktionen für den Benutzer verwalten, ändern und konfigurieren. Sie können Benutzer mit der Exchange-Verwaltungskonsole oder der Shell für UM aktivieren. Weitere Informationen finden Sie unter [Voicemail für Benutzer](https://technet.microsoft.com/de-de/library/Aa997885(v=EXCHG.150)).

Wenn Sie einen Benutzer für UM aktivieren, müssen Sie mindestens eine Durchwahlnummer definieren, die UM bei der Übermittlung einer Voicemail an das Postfach des Benutzers verwendet und die dem Benutzer die Nutzung von Outlook Voice Access ermöglicht. Nachdem Sie den Benutzer für UM aktiviert haben, können Sie dem Benutzerpostfach sekundäre Durchwahlnummern hinzufügen, diese ändern oder entfernen, indem Sie die Exchange Unified Messaging-Proxyadresse (EUM-Proxyadresse) für das Benutzerpostfach konfigurieren oder zusätzliche oder sekundäre Durchwahlnummern für die Benutzer in der Exchange-Verwaltungskonsole hinzufügen oder entfernen. Informationen zum Hinzufügen, Ändern oder Entfernen von Durchwahlnummern, E.164-Nummern oder SIP-Adressen finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://technet.microsoft.com/de-de/library/JJ835776(v=EXCHG.150)).

So aktivieren Sie einen Benutzer mit der der Exchange-Verwaltungskonsole für UM:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger**.

2.  Wählen Sie in der Listenansicht den Benutzer aus, dessen Postfach Sie für Unified Messaging aktivieren möchten.

3.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** auf **Aktivieren**.

4.  Klicken Sie auf der Seite **UM-Postfach aktivieren** neben **UM-Postfachrichtlinie** auf die Schaltfläche **Durchsuchen**, navigieren Sie zu der UM-Postfachrichtlinie, der Sie den Benutzer aus der Liste zuweisen möchten, und klicken Sie dann auf **OK**.

5.  Füllen Sie auf der Seite **UM-Postfach aktivieren** die folgenden Felder aus:
    
      - **SIP-Adresse oder die e. 164-Nummer**    Geben Sie der SIP-Adresse oder die e. 164-Nummer für den Benutzer ein. Diese Optionen sind verfügbar, wenn der Benutzer, den Sie für Unified Messaging aktivieren einer um-Postfachrichtlinie zugewiesen ist, die mit einer SIP-URI oder eine e. 164-Wählplan verknüpft ist. Hinzufügen einer SIP-Adresse oder die e. 164-Nummer für einen Benutzer ist nicht verfügbar, wenn der Benutzer eine Telefondurchwahl-Wähleinstellungen zugeordnet ist. Wenn Sie den Benutzer zuweisen einer um-Postfachrichtlinie, die mit einer SIP-URI verknüpft ist, oder e. 164-Wählplan, müssen Sie auch eine Durchwahlnummer für den Benutzer eingeben. Diese Erweiterung Zahl wird verwendet, wenn Benutzer auf ihr Postfach mithilfe von Outlook Voice Access zugreifen. Die Anzahl der Ziffern, die Sie in dieses Feld konfigurieren, muss die Anzahl der Nachkommastellen für den SIP-URI konfiguriert entsprechen oder e. 164-Wählplan.
    
      - **Durchwahlnummer**   Geben Sie die Durchwahlnummer für den Benutzer, den Sie für UM aktivieren, manuell ein.
        
        Sie müssen für den Benutzer eine gültige Durchwahlnummer angeben, die mit der im Wählplan angegebenen Anzahl von Ziffern übereinstimmt. Sie können nur numerische Zeichen oder Ziffern von 1 bis 20 eingeben. Eine typische Durchwahlnummer hat 3 bis 7 Ziffern. Die Anzahl von Ziffern der Durchwahl ist für den Wählplan festgelegt, der mit dem einem Benutzer zugewiesenen UM-Postfach verknüpft ist.
    
      - Führen Sie unter **PIN-Einstellungen** folgende Schritte aus:
        
          - **PIN automatisch generieren**   Klicken Sie auf diese Schaltfläche, um automatisch eine PIN für den UM-aktivierten Benutzer zu generieren, mit der der Benutzer über Outlook Voice Access auf das Voicemailsystem zugreifen kann. Dies ist die Standardeinstellung. Wenn Sie auf diese Schaltfläche klicken wird automatisch eine PIN basierend auf den PIN-Richtlinien erstellt, die in der dem Empfänger zugeordneten UM-Postfachrichtlinie konfiguriert sind. Es wird empfohlen, diese Einstellung zum Schutz der Benutzer-PIN zu verwenden. Die PIN wird in der Begrüßungsnachricht an den Benutzer gesendet, die er nach der Aktivierung für UM erhält. Standardmäßig muss diese PIN bei der ersten Anmeldung beim Postfach zum Abrufen der Voicemail geändert werden.
        
          - **PIN eingeben**   Klicken Sie auf diese Schaltfläche, wenn Sie manuell die PIN eingeben möchten, mit der der Benutzer auf das Voicemailsystem zugreifen kann. Die PIN muss mit den PIN-Richtlinieneinstellungen übereinstimmen, die in der UM-Postfachrichtlinie konfiguriert sind, die diesem UM-aktivierten Benutzer zugewiesen ist. Wenn die UM-Postfachrichtlinie beispielsweise so konfiguriert wurde, dass ausschließlich PINs mit sieben oder mehr Ziffern akzeptiert werden, muss die in diesem Feld eingegebene PIN mindestens sieben Ziffern umfassen.
        
          - **Benutzer muss PIN bei der ersten Anmeldung zurücksetzen**   Aktivieren Sie dieses Kontrollkästchen, um festzulegen, dass der Benutzer seine Voicemail-PIN ändern muss, wenn er das erste Mal mit einem Telefon über Outlook Voice Access auf das Voicemailsystem zugreift. Sie werden dazu aufgefordert, eine ihnen vertrautere PIN einzugeben. Dabei handelt es sich um eine bewährte Sicherheitsmethode, mit der UM-aktivierte Benutzer gezwungen werden, ihre PIN bei der ersten Anmeldung zu ändern. Auf diese Weise werden die Daten und Posteingänge besser vor unbefugtem Zugriff geschützt. Dieses Kontrollkästchen ist standardmäßig aktiviert.

6.  Überprüfen Sie auf der Seite **UM-Postfach aktivieren** Ihre Einstellungen. Klicken Sie auf **Fertig stellen**, um den Benutzer für Unified Messaging zu aktivieren. Klicken Sie auf **Zurück**, um Konfigurationsänderungen vorzunehmen.

Aktivieren Sie einen Benutzer für Unified Messaging in der Shell den folgenden Befehl ausführen.

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

## Schritt 13: Konfigurieren der VoIP-Gateways, IP-PBX-Anlagen und SIP-aktivierten Nebenstellenanlagen für das Senden aller eingehenden Anrufe an die Exchange 2013-Clientzugriffsserver

Werden Exchange 2013-Clientzugriffs- und Postfachserver installiert, werden sie automatisch aktiviert, damit sie ein- und ausgehende Anrufe tätigen und Voicemailnachrichten an die vorgesehenen Empfänger weiterleiten können. Nachdem Sie Ihre Exchange 2013-Clientzugriffs- und Postfachserver installiert und Unified Messaging bereitgestellt haben, müssen Sie UM-Wählplänen keine Exchange 2013-Clientzugriffs- oder Postfachserver zuordnen. Exchange 2013-Clientzugriffs- und Postfachserver beantworten alle eingehenden Anrufe und bestimmen anschließend Benutzer mithilfe von UM-Wählplänen.

Der Exchange 2013-Clientzugriffsserver ist der Einstiegspunkt für alle eingehenden Anrufe oder SIP-Anforderungen (Session Initiation Protocol) für Unified Messaging (UM). Die SIP-Anforderungen auf einem Exchange 2013-Clientzugriffsserver werden vom UM-Anrufweiterleitungsdienst verarbeitet. Dieser läuft auf allen Exchange 2013-Clientzugriffsservern in Ihrer Organisation.

Wenn Sie auf Exchange 2013-UM aktualisieren, müssen Sie bereits mindestens ein VoIP-Gateway installiert und konfiguriert haben, um eine Verbindung mit den PBX-Anlagen in Ihrem Telefonienetzwerk herzustellen, oder SIP-fähige (Session Initiation Protocol) PBX-Anlagen oder IP-PBX-Anlagen installiert und konfiguriert haben.

Der letzte Schritt in der Aktualisierung auf Exchange 2013-UM ist die Konfiguration Ihrer VoIP-Gateways, IP-PBX-Anlagen oder SIP-fähigen PBX-Anlagen für das Senden eingehender Anrufe, einschließlich Anrufer, die Voicemail für einen Benutzer hinterlassen möchten, Anrufe von UM-aktivierten Benutzern, die Outlook Voice Access anrufen, und Anrufe von Anrufern, die sich in eine automatische UM-Telefonzentrale einwählen, an Ihre Exchange 2013-Clientzugriffsserver. Diese Anrufe gehen zunächst an einem VoIP-Gateway, einer IP-PBX-Anlage oder einer SIP-fähigen PBX-Anlage ein und werden dann an die Exchange 2013-Clientzugriffsserver in Ihrer Exchange 2013-Organisation weitergeleitet. Weitere Informationen hierzu finden Sie in den folgenden Ressourcen:

  -  [UM-Dienste](um-services-exchange-2013-help.md)

  -  [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](https://technet.microsoft.com/de-de/library/JJ938013(v=EXCHG.150))

  -  [Telefonieratgeber für Exchange 2013](https://technet.microsoft.com/de-de/library/Ee364753(v=EXCHG.150))

## Schritt 14: Deaktivieren der Anrufbeantwortung auf einem Exchange 2007 Unified Messaging-server

Sie können die Anrufbeantwortung, indem UM auf einem Exchange 2007 Unified Messaging-Server deaktivieren oder Entfernen des UM-Servers aus einem Wählplan deaktivieren. Beim Deaktivieren UM, zu verhindern, dass Sie den Server Unified Messaging von antwortenden eingehende Anrufe. Sie können auch alle Anrufe sofort getrennt oder warten Sie auf vorhandene Anrufe verarbeitet werden, bevor Sie Unified Messaging-Server deaktivieren. Sie sollten vor dem Entfernen des Servers aus einem Wählplan, damit es die Verarbeitung eingehender Anrufe beendet wird Anrufbeantwortung zu deaktivieren.

Unified Messaging auf einem Exchange 2007 Unified MESSAGING-Server deaktivieren, indem Sie mit der Exchange-Verwaltungskonsole:

1.  Navigieren Sie in der Konsolenstruktur zu **Serverkonfiguration** \> **Unified Messaging**.

2.  Wählen Sie im Ergebnisbereich den zu deaktivierenden Unified Messaging-Server aus.

3.  Klicken Sie im Aktionsbereich auf eine der folgenden Optionen:
    
    1.  **Sofort deaktivieren**: Bei Auswahl dieser Option trennt der Unified Messaging-Server alle Anrufe, die mit dem Unified Messaging-Server verbunden sind.
    
    2.  **Nach Beenden der Anrufe deaktivieren**: Bei Auswahl dieser Option nimmt der Unified Messaging-Server keine neuen Anrufe an, wird jedoch erst deaktiviert, nachdem alle Anrufe verarbeitet wurden.

4.  Klicken Sie im Bestätigungsdialogfeld auf **Ja**, um den Vorgang fortzusetzen.

Führen Sie den folgenden Befehl, um Unified Messaging auf einem Exchange 2007 Unified MESSAGING-Server deaktivieren, indem Sie mit der Shell.

```powershell
Disable-UMServer -Identity MyUMServer -Immediate $true
```


> [!TIP]
> Das Cmdlet <STRONG>Disable-UMServer</STRONG> aus einer Exchange 2007 UM-Server oder <STRONG>Disable-UMService</STRONG> Cmdlet von einem Exchange 2013 Mailbox-Server können Sie um die Anrufbeantwortung zu deaktivieren.



## Schritt 15: Entfernen eines Exchange 2007 Unified Messaging-Servers aus einem Wählplan

Damit Anrufe verarbeitet werden, muss mindestens ein UM-Wählplan ein Exchange 2007 Unified MESSAGING-Server hinzugefügt werden. Ein UM-Server kann mehrere um-Wählpläne hinzugefügt werden. Sie können einen Exchange 2007 Unified MESSAGING-Server aus einem um-Wählplan entfernen. Beim Entfernen eines UM-Servers aus einem Wählplan der UM-Server nicht mehr Anrufe entgegennimmt oder UM Anrufe für UM-aktivierte Benutzer verarbeiten.

So entfernen Sie einen Exchange 2007 UM-Server aus einem Wählplan mithilfe der Exchange-Verwaltungskonsole:

1.  Navigieren Sie in der Konsolenstruktur zu **Serverkonfiguration** \> **Unified Messaging**.

2.  Wählen Sie im Ergebnisbereich den Unified Messaging-Server aus.

3.  Klicken Sie im Aktionsbereich auf **Eigenschaften**.

4.  Klicken Sie auf der Registerkarte **UM-Einstellungen** im Abschnitt **Zugeordnete Wählpläne** auf **Entfernen**.

5.  Klicken Sie im Bestätigungsdialogfeld auf **Ja**, um den Löschvorgang des Exchange 2007 Unified Messaging Servers aus der um-Wählplan zu bestätigen.

6.  Klicken Sie auf **OK**, um das Eigenschaftenfenster zu schließen.

Führen Sie den folgenden Befehl, um eine Exchange 2007 Unified MESSAGING-Server mithilfe der Shell aus einem Wählplan zu entfernen.

    $dp= Get-UMDialPlan "MySIPDialPlan"
    $s=Get-UMServer -id MyUMServer
    $s.dialplans-=$dp.identity
    Set-UMServer -id MyUMServer -dialplans:$s.dialplans

In diesem Beispiel sind drei SIP-UIR-Wählpläne vorhanden: SipDP1, SipDP2 und SipDP3. In diesem Beispiel wird ein UM-Server mit dem Namen `MyUMServer` aus dem Wählplan "SipDP3" entfernt.

```powershell
Set-UMServer -id MyUMServer -DialPlans SipDP1,SipDP2
```

In diesem Beispiel sind zwei SIP-UIR-Wählpläne vorhanden: SipDP1 und SipDP2. In diesem Beispiel wird ein UM-Server mit dem Namen `MyUMServer` aus dem Wählplan "SipDP2" entfernt.

```powershell
Set-UMServer -id MyUMServer -DialPlans SipDP1
```


> [!TIP]
> Das Cmdlet <STRONG>Set-UMServer</STRONG> können in der Shell auf einem Exchange 2007 Unified Messaging-Server oder auf einem Exchange 2013 Mailbox-Server-Cmdlet <STRONG>Set-UMService</STRONG> zum Entfernen eines Exchange 2007 Unified MESSAGING-Servers aus einer einzelnen oder mehreren Wählplänen. Führen Sie beispielsweise den folgenden Befehl zum Entfernen eines UM-Servers aus allen Wählplänen: <CODE>Set-UMServer -identity MyUMServer -DialPlan $null</CODE>



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Überprüfen Sie nach der Einrichtung von UM Folgendes, um die einwandfreie Funktion sicherzustellen:

  - Ein Benutzer, den Sie für Voicemail aktiviert haben, kann sich bei Outlook Web App oder Outlook anmelden und sieht eine Willkommensmeldung für Unified Messaging (UM).

  - UM-Benutzer können Sprachnachrichten empfangen.

  - UM-Benutzer können eine Outlook Voice Access-Nummer anrufen, um E-Mails, Kalendereinträge und Voicemail anzuhören.

  - UM leitet Anrufe von außerhalb der Organisation weiter, und Sie können einen Anruf vornehmen.


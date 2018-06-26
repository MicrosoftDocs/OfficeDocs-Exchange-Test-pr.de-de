---
title: 'Verwenden der anspruchsbasierten AD FS-Authentifizierung mit Outlook Web App und Exchange-Verwaltungskonsole: Exchange 2013 Help'
TOCTitle: Verwenden der anspruchsbasierten AD FS-Authentifizierung mit Outlook Web App und Exchange-Verwaltungskonsole
ms:assetid: 919a9bfb-c6df-490a-b2c4-51796b0f0596
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn635116(v=EXCHG.150)
ms:contentKeyID: 61201342
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwenden der anspruchsbasierten AD FS-Authentifizierung mit Outlook Web App und Exchange-Verwaltungskonsole

 

_**Gilt für:**Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:**2017-04-14_

**Zusammenfassung:**

Bei lokalen Bereitstellungen von Exchange 2013 Service Pack 1 (SP1) bedeutet die Installation und Konfiguration von Active Directory-Verbunddiensten (AD FS), dass Sie nun die anspruchsbasierte AD FS-Authentifizierung zum Herstellen einer Verbindung mit Outlook Web App und EAC verwenden können. Sie können AD FS und anspruchsbasierte Authentifizierung mit Exchange 2013 SP1 integrieren. Die anspruchsbasierte Authentifizierung ersetzt die herkömmlichen Authentifizierungsmethoden, einschließlich der folgenden:

  - Windows-Authentifizierung

  - Formularbasierte Authentifizierung

  - Digestauthentifizierung

  - Standardauthentifizierung

  - Active Directory-Authentifizierung mit Clientzertifikaten

Die Authentifizierung ist der Vorgang, bei dem die Identität eines Benutzers überprüft wird. Die Authentifizierung prüft, ob die tatsächliche Identität des Benutzers seinen Angaben entspricht. Anspruchsbasierte Identität ist eine andere Möglichkeit zur Authentifizierung. Die anspruchsbasierte Authentifizierung ersetzt die Verwaltung der Authentifizierung in der Anwendung – in diesem Fall Outlook Web App und Exchange-Verwaltungskonsole – damit Konten einfacher über eine zentralisierte Authentifizierung verwaltet werden können. Outlook Web App und Exchange-Verwaltungskonsole sind nicht für die Authentifizierung der Benutzer, das Speichern von Benutzerkonten und Kennwörtern, das Suchen von Benutzeridentitätsdaten oder die Integration mit anderen Identitätssystemen zuständig. Die zentralisierte Authentifizierung vereinfacht die Aktualisierung auf zukünftige Authentifizierungsmethoden.


> [!NOTE]
> OWA für Geräte bietet keine Unterstützung für anspruchsbasierte AD&nbsp;FS-Authentifizierung.



Es gibt mehrere Versionen von AD FS, die verwendet werden können. Diese sind in der folgenden Tabelle zusammengefasst.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Windows Server-Version</th>
<th>Installation</th>
<th>Version von AD FS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Windows Server 2008 R2</p></td>
<td><p><strong>Herunterladen und installieren</strong> von AD FS 2.0, einer Zusatzkomponente für Windows.</p></td>
<td><p>AD FS 2.0</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2012</p></td>
<td><p>Installieren Sie die <strong>integrierte</strong> AD FS-Serverrolle.</p></td>
<td><p>AD FS 2.1</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2012 R2</p></td>
<td><p>Installieren Sie die <strong>integrierte</strong> AD FS-Serverrolle.</p></td>
<td><p>AD FS 3.0</p></td>
</tr>
</tbody>
</table>


Die Aufgaben, die Sie hier ausführen werden, basieren auf Windows Server 2012 R2, das den AD FS-Rollendienst enthält.

**Übersicht der erforderlichen Schritte**

Step 1 - Review the certificate requirements for AD FS

Step 2 - Install and configure Active Directory Federation Services (AD FS)

Schritt 3: Erstellen einer Vertrauensstellung und benutzerdefinierte Anspruchsregeln für Outlook Web App und Exchange-Verwaltungskonsole

Schritt 4: Installieren des Webanwendungsproxy-Rollendiensts (optional)

Schritt 5: Konfigurieren des Webanwendungsproxy-Rollendiensts (optional)

Schritt 6: Veröffentlichen von Outlook Web App und EAC mithilfe des Webanwendungsproxy (optional)

Schritt 7: Konfigurieren von Exchange 2013 für die Verwendung der AD FS-Authentifizierung

Schritt 8: Aktivieren der AD FS-Authentifizierung für die virtuellen Verzeichnisse „OWA" und „ECP"

Schritt 9: Neustart oder Wiederverwendung von Internetinformationsdiensten (Internet Information Services, IIS)

Schritt 10: Testen der AD FS-Ansprüche für Outlook Web App und Exchange-Verwaltungskonsole

Additional information you might want to know

## Was muss ich wissen, bevor ich beginne?

  - Sie müssen mindestens getrennte Server mit Windows Server 2012 R2 installieren: einen als Domänencontroller, der Active Directory-Domänendienste (AD DS) verwendet, einen Exchange 2013-Server, einen Webanwendungsproxy-Server und einen Active Directory-Verbunddienste (AD FS)-Server. Stellen Sie sicher, dass alle Updates installiert wurden.

  - Installieren Sie AD DS auf der entsprechenden Anzahl von Windows Server 2012 R2-Servern in Ihrer Organisation. Sie können auch **Benachrichtigungen** in **Server-Manager** \> **Dashboard** verwenden und den **Server zu einem Domänencontroller heraufstufen**.

  - Installieren Sie entsprechende Anzahl von Clientzugriffs- und Postfachservern für Ihre Organisation. Stellen Sie sicher, dass alle Updates einschließlich SP1 auf allen Exchange 2013-Servern in Ihrer Organisation installiert wurden. SP1 können Sie unter [Updates für Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md) herunterladen.

  - Das Bereitstellen des Webanwendungsproxy auf einem Server erfordert lokale Administratorberechtigungen. Sie müssen AD FS auf einem Server mit Windows Server 2012 R2 in Ihrer Organisation bereitstellen, bevor Sie den Webanwendungsproxy bereitstellen können.

  - Installieren und konfigurieren Sie die AD FS-Rolle und erstellen Sie Vertrauensstellungen und Anspruchsregeln unter Windows Server 2012 R2. Gehen Sie zu diese Zweck wie folgt vor: Melden Sie sich mit einem Benutzerkonto an, das Mitglied der Gruppe "Domänen-Admins", "Organisations-Admins" oder der lokalen Administratorengruppe ist.

  - Bestimmen Sie die erforderlichen Berechtigungen für Exchange 2013. Informationen dazu finden Sie unter [Funktionsberechtigungen](feature-permissions-exchange-2013-help.md).

  - Sie müssen über Berechtigungen zum Verwalten von Outlook Web App verfügen. Informationen zu den erforderlichen Berechtigungen finden Sie unter "Berechtigungen für Outlook Web App" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Sie müssen über Berechtigungen zum Verwalten von EAC verfügen. Welche Berechtigungen Sie benötigen, können Sie dem Eintrag "Konnektivität der Exchange-Verwaltungskonsole" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md) entnehmen.

  - Möglicherweise können Sie lediglich mit der Shell einige Verfahren durchführen. Wie eine Shell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Schritt 1: Überprüfen Sie die Zertifikatanforderungen für AD FS

Zertifikate spielen eine entscheidende Rolle beim Absichern der Kommunikation zwischen Exchange 2013 SP1-Servern, Webclients wie Outlook Web App, der Exchange-Verwaltungskonsole und Windows Server 2012 R2-Servern, einschließlich Active Directory-Verbunddienst (AD FS)-Servern und Webanwendungsproxy-Servern. Die Anforderungen für Zertifikate unterscheiden sich je nachdem, ob Sie einen AD FS-Server, AD FS-Proxy oder einen Webanwendungsproxy-Server einrichten. Die Zertifikate, die für AD FS-Dienste verwendet werden, einschließlich der SSL- und Tokensignaturzertifikate, müssen in den Speicher für vertrauenswürdige Stammzertifizierungsstellen auf allen Exchange-, AD FS- und Webanwendungsproxy-Servern importiert werden. Der Fingerabdruck für das importierte Zertifikat wird auch auf den Exchange 2013 SP1-Servern verwendet, wenn Sie das Cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)) benutzen.

Bei jedem AD FS-Design müssen verschiedene Zertifikate verwendet werden, um die Kommunikation zwischen Benutzern im Internet und AD FS-Servern abzusichern. Jeder Verbundserver muss über ein Dienstkommunikationszertifikat oder ein SSL (Secure Socket Layer)-Zertifikat und ein Tokensignaturzertifikat verfügen, bevor AD FS-Server, Active Directory-Domänencontroller und Exchange 2013-Server kommunizieren und sich authentifizieren können. Erwägen Sie sorgfältig, welche Zertifikate Sie entsprechend Ihren Sicherheits- und Kostenanforderungen von einer öffentlichen Zertifizierungsstelle oder einer Organisationszertifizierungsstelle beschaffen. Wenn Sie eine Stamm- oder untergeordnete Zertifizierungsstelle der Organisation installieren und konfigurieren wollen, können Sie Active Directory-Zertifikatdienste (AD CS) verwenden. Weitere Informationen zu AD CS finden Sie unter [Active Directory-Zertifikatdienste: Übersicht](https://go.microsoft.com/fwlink/?linkid=392697).

AD FS erfordert zwar keine Zertifikate, die von einer ZS ausgestellt wurden, allerdings muss das SSL-Zertifikat (das auch standardmäßig als Dienstkommunikationszertifikat verwendet wird) von den AD FS-Clients als vertrauenswürdig eingestuft werden. Es wird empfohlen, dass Sie nicht selbst-signierte Zertifikate verwenden. Verbundserver verwenden ein SSL-Zertifikat, um den Datenverkehr von Webdiensten für SSL-Kommunikation mit Webclients und Verbundserver-Proxys abzusichern. Da das SSL-Zertifikat von Clientcomputern als vertrauenswürdig eingestuft werden muss, empfehlen wir Ihnen, ein Zertifikat zu verwenden, das von einer vertrauenswürdigen ZS signiert wurde. Alle von Ihnen ausgewählten Zertifikate müssen über einen entsprechenden privaten Schlüssel verfügen. Nachdem Sie ein Zertifikat von einer ZS (Organisation oder öffentlich) empfangen haben, stellen Sie sicher, dass alle Zertifikate in den Speicher für vertrauenswürdige Stammzertifizierungsstellen auf allen Servern importiert werden. Sie können Zertifikate mit dem MMC-Snap-In **Zertifikate** importieren oder die Zertifikate mithilfe der Active Directory-Zertifikatdienste verteilen. Es ist wichtig, dass Sie bei Ablauf eines importierten Zertifikats manuell ein anderes, gültiges Zertifikat importieren.


> [!IMPORTANT]
> Wenn Sie das selbstsignierte Tokensignaturzertifikat von AD&nbsp;FS verwenden, müssen Sie dieses Zertifikat in den Speicher für vertrauenswürdige Stammzertifizierungsstellen auf allen Ihren Exchange 2013-Servern importieren. Wenn das selbstsignierte Tokensignaturzertifikat nicht verwendet und der Webanwendungsproxy bereitgestellt wird, müssen Sie den öffentlichen Schlüssel in der Webanwendungsproxy-Konfiguration und allen AD&nbsp;FS-Vertrauensstellungen aktualisieren.



Befolgen Sie diese Zertifikatempfehlungen, wenn Sie Exchange 2013 SP1, AD FS und Webanwendungsproxy einrichten:

  - **Postfachserver**   Die Zertifikate, die auf den Postfachservern verwendet werden, sind selbstsignierte Zertifikate. Sie werden bei der Installation von Exchange 2013 erstellt. Da sich alle Clients über einen Exchange 2013-Clientzugriffsserver mit einem Exchange 2013-Postfachserver verbinden, müssen Sie lediglich die Zertifikate auf den Clientzugriffsservern verwalten.

  - **Clientzugriffsserver**   Ein SSL-Zertifikat für Dienstkommunikation ist erforderlich. Wenn Ihr vorhandenes SSL-Zertifikat bereits den FQDN enthält, den Sie zum Einrichten des Vertrauensstellungsendpunkts verwenden, sind keine zusätzlichen Zertifikate erforderlich.

  - **AD FS**   Zwei Zertifikattypen werden von AD FS benötigt:
    
      - SSL-Zertifikat für Dienstkommunikation
        
          - Antragstellername: **adfs.contoso.com** (AD FS-Bereitstellungsname)
        
          - Alternativer Antragstellername (SAN): Keine
    
      - Tokensignaturzertifikat
        
          - Antragstellername: **tokensigning.contoso.com**
        
          - Alternativer Antragstellername (SAN): Keine
        

        > [!NOTE]
        > Wenn Sie das Tokensignaturzertifikat in AD&nbsp;FS ersetzen, müssen alle vorhandenen Vertrauensstellungen aktualisiert werden, sodass Sie das neue Tokensignaturzertifikat verwenden.



  - **Webanwendungsproxy**
    
      - SSL-Zertifikat für Dienstkommunikation
        
          - Antragstellername: **owa.contoso.com**
        
          - Alternativer Antragstellername (SAN): Keine
        

        > [!NOTE]
        > Wenn die externe URL Ihres Webanwendungsproxys mit Ihrer internen URL übereinstimmt, können Sie das SSL-Zertifikat von Exchange hier wiederverwenden.

    
      - AD FS-Proxy-SSL-Zertifikat
        
          - Antragstellername: **adfs.contoso.com** (AD FS-Bereitstellungsname)
        
          - Alternativer Antragstellername (SAN): Keine
    
      - Tokensignaturzertifikat – Dies wird im Rahmen der folgenden Schritte automatisch aus AD FS kopiert. Wird dieses Zertifikat verwendet, muss es von den Exchange 2013-Servern in Ihrer Organisation als vertrauenswürdig eingestuft werden.

Weitere Informationen zu Zertifikaten finden Sie im Abschnitt "Zertifikatanforderungen" unter [Prüfen der Anforderungen für die Bereitstellung von AD FS](https://go.microsoft.com/fwlink/?linkid=392699).


> [!NOTE]
> Sie benötigen ein SSL-Verschlüsselungszertifikat für Outlook Web App und EAC, auch wenn Sie über ein SSL-Zertifikat für AD&nbsp;FS verfügen. Das SSL-Zertifikat wird für die virtuellen Verzeichnisse "OWA" und "ECP" verwendet.



## Schritt 2: Installation und Konfiguration der Active Directory-Verbunddienste (AD FS)

AD FS bietet unter Windows Server 2012 R2 vereinfachte, sichere Identitätsverbund- und Web-Einmalanmeldungsfunktionen (Single Sign-On, SSO). AD FS umfasst einen Verbunddienst, der browserbasiertes Web-SSO sowie mehrstufige und anspruchsbasierte Authentifizierung ermöglicht. AD FS vereinfacht den Zugriff auf Systeme und Anwendungen mithilfe einer anspruchsbasierten Authentifizierung und eines Autorisierungsmechanismus, um die Anwendungssicherheit zu gewährleisten.

Installieren von AD FS auf Windows Server 2012 R2:

1.  Öffnen Sie den **Server-Manager** auf dem **Startbildschirm** oder wählen Sie **Server-Manager** auf der Taskleiste auf dem Desktop. Klicken Sie im Menü **Verwalten** auf **Rollen und Funktionen hinzufügen**.

2.  Klicken Sie auf der Seite **Vorbereitung** auf **Weiter**.

3.  Klicken Sie auf der Seite **Installationsart auswählen** auf **Rollenbasierter oder funktionsbasierte Installation** und dann auf **Weiter**.

4.  Klicken Sie auf der Seite **Zielserver auswählen** auf **Server aus dem Serverpool auswählen**, stellen Sie sicher, dass der lokale Computer ausgewählt wird, und klicken Sie anschließend auf **Weiter**.

5.  Klicken Sie auf der Seite **Serverrollen auswählen** auf **Active Directory-Verbunddienste** und dann auf **Weiter**.
    
    Klicken Sie auf der Seite **Funktionen auswählen** auf **Weiter**. Die erforderlichen Voraussetzungen und Funktionen sind bereits für Sie ausgewählt. Sie müssen keine weiteren Funktionen auswählen.

6.  Klicken Sie auf der Seite **Active Directory-Verbunddienst (AD FS)** auf **Weiter**.

7.  Markieren Sie auf der Seite **Installationsauswahl bestätigenZielserver wenn nötig automatisch neu starten** und klicken Sie anschließend auf **Installieren**.
    

    > [!NOTE]
    > Schließen Sie den Assistenten nicht während der Installation.



Nachdem Sie die benötigten AD FS-Server installiert und die erforderlichen Zertifikate erstellt haben, müssen Sie AD FS konfigurieren und dann die ordnungsgemäße Funktion prüfen. Sie können auch die folgende Prüfliste als Hilfe bei der Einrichtung und Konfiguration von AD FS verwenden: [Prüfliste: Einrichten eines Verbundservers](https://go.microsoft.com/fwlink/?linkid=392700).

So konfigurieren Sie Active Directory-Verbunddienste:

1.  Klicken Sie auf der Seite **Installationsstatus** im Fenster unter **Active Directory-Verbunddienste** auf **Verbunddienst auf diesem Server konfigurieren**. Der Assistent zum Konfigurieren von Active Directory-Verbunddiensten wird geöffnet.

2.  Klicken Sie auf der **Begrüßungsseite** auf **Ersten Verbundserver in einer Verbundserverfarm erstellen** und anschließend auf **Weiter**.

3.  Geben Sie auf der Seite **Mit AD DS verbinden** ein Konto mit Domänenadministratorrechten für die entsprechende Active Directory-Domäne an, der dieser Computer angehört, und klicken Sie dann auf **Weiter**. Wenn Sie einen anderen Benutzer auswählen wollen, klicken Sie auf **Ändern**.

4.  Führen Sie anschließend auf der Seite **Diensteigenschaften angeben** die folgenden Schritte aus und klicken Sie dann auf **Weiter**:
    
      - Importieren Sie das SSL-Zertifikat, das Sie zuvor von AD CS oder einer öffentlichen ZS erhalten haben. Dieses Zertifikat ist das benötigte Dienstauthentifizierungszertifikat. Navigieren Sie zum Speicherort des SSL-Zertifikats. Weitere Informationen zum Erstellen und Importieren von SSL-Zertifikaten finden Sie unter [Serverzertifikate](https://go.microsoft.com/fwlink/?linkid=392703).
    
      - Geben Sie einen Namen für Ihren Verbunddienst ein, z. B. **adfs.contoso.com**.
    
      - Geben Sie als Anzeigenamen für Ihren Verbunddienst den Namen Ihrer Organisation ein, z. B. **Contoso, Ltd.**.

5.  Wählen Sie auf der Seite **Dienstkonto angeben** die Option **Ein Domänenbenutzerkonto oder ein gruppenverwaltetes Dienstkonto verwenden** aus und geben Sie dann das GMSA-Konto (FsGmsa) an, das Sie bei der Erstellung des Domänencontrollers erstellt haben. Geben Sie das Kennwort für das Konto ein und klicken Sie dann auf **Weiter**.
    

    > [!NOTE]
    > Ein global verwaltetes Dienstkonto (Globally Managed Service Account, GMSA) ist ein Konto, das erstellt werden muss, wenn Sie einen Domänencontroller konfigurieren. Das GMSA-Konto ist für die AD&nbsp;FS-Installation und -Konfiguration erforderlich. Wenn Sie dieses Konto noch nicht erstellt haben, führen Sie den folgenden Windows PowerShell-Befehl aus. Dieser erstellt das Konto für die Domäne "contoso.com" und den AD&nbsp;FS-Server:



6.  Führen Sie den folgenden Befehl aus.
    
        Add-KdsRootKey -EffectiveTime (Get-Date).AddHours(-10)

7.  Dieses Beispiel erstellt ein neues GMSA-Konto, mit dem Namen FsGmsa für den Verbunddienst mit dem Namen adfs.contoso.com. Der Verbunddienst-Name ist der Wert, der für Clients sichtbar ist.
    
        New-ADServiceAccount FsGmsa -DNSHostName adfs.contoso.com -ServicePrincipalNames http/adfs.contoso.com

8.  Wählen Sie auf der Seite **Konfigurationsdatenbank angeben** die Option **Auf diesem Server eine Datenbank mit der internen Windows-Datenbank erstellen** und klicken Sie dann auf **Weiter**.

9.  Auf der Seite **Optionen überprüfen** bestätigen Sie Ihre Konfigurationsauswahl. Optional können Sie die Schaltfläche **Skript anzeigen** verwenden, um weitere AD FS-Installationen zu automatisieren. Klicken Sie auf **Weiter**.

10. Auf der Seite **Überprüfung von Voraussetzungen** prüfen Sie, ob alle Überprüfungen erfolgreich abgeschlossen wurden, und klicken Sie anschließend auf **Konfigurieren**.

11. Überprüfen Sie auf der Seite **Installationsstatus**, ob alles richtig installiert wurde, und klicken Sie anschließend auf **Schließen**.

12. Auf der Seite **Ergebnisse** prüfen Sie die Ergebnisse, überprüfen, ob die Konfiguration erfolgreich abgeschlossen wurde, und klicken anschließend auf **Weitere Schritte, die zum Abschluss der Bereitstellung des Verbunddiensts erforderlich sind**.

Die folgenden Windows PowerShell-Befehle führen Sie dieselben Schritte wie die vorangegangenen Schritte.

    Import-Module ADFS

    Install-AdfsFarm -CertificateThumbprint 0E0C205D252002D535F6D32026B6AB074FB840E7 -FederationServiceDisplayName "Contoso Corporation" -FederationServiceName adfs.contoso.com -GroupServiceAccountIdentifier "contoso\FSgmsa`$"

Weitere Informationen und die Syntax finden Sie unter [Install-AdfsFarm](https://go.microsoft.com/fwlink/?linkid=392704).

So überprüfen Sie die Installation: Öffnen Sie auf dem AD FS-Server Ihren Webbrowser und rufen Sie dann die URL der Verbundmetadaten, z. B. **https://adfs.contoso.com/federationmetadata/2007-06/federationmetadata.xml**.

## Schritt 3: Erstellen einer Vertrauensstellung und benutzerdefinierte Anspruchsregeln für Outlook Web App und Exchange-Verwaltungskonsole

Für alle Anwendungen und Dienste, die Sie über den Webanwendungsproxy veröffentlichen wollen, müssen Sie eine Vertrauensstellung auf dem AD FS-Server erstellen. Bei Bereitstellungen mit mehreren Active Directory-Websites, die separate Namespaces verwenden, muss für jeden Namespace eine Vertrauensstellung für Outlook Web App und Exchange-Verwaltungskonsole hinzugefügt werden.

Die Exchange-Verwaltungskonsole verwendet das virtuelle Verzeichnis "ECP". Sie können Einstellungen für die Exchange-Verwaltungskonsole mithilfe der Cmdlets [Get-EcpVirtualDirectory](https://technet.microsoft.com/de-de/library/dd351058\(v=exchg.150\)) und [Set-EcpVirtualDirectory](https://technet.microsoft.com/de-de/library/dd297991\(v=exchg.150\)) anzeigen und konfigurieren. Um auf die Exchange-Verwaltungskonsole zuzugreifen, müssen Sie einen Webbrowser benutzen und **http://server1.contoso.com/ecp** aufrufen.


> [!NOTE]
> Die Einbeziehung des abschließenden Schrägstrichs <STRONG>/</STRONG> in den unten gezeigten URL-Beispielen ist beabsichtigt. Dies dient zur Sicherstellung, dass die AD FS-Vertrauensstellungen und die Exchange Audience-URIs <STRONG>identisch sind</STRONG>. Das bedeutet, die AD FS-Vertrauensstellungen und die Exchange Audience-URIs sollten <STRONG>beide</STRONG> die abschließenden Schrägstrichen in den URLs <STRONG>enthalten oder ausgeben</STRONG>. In den Beispielen in diesem Abschnitt sind abschließende Schrägstriche (<STRONG>/</STRONG>) am Ende der URL mit „owa&amp;quot; (/owa) oder „ecp&amp;quot; (/ecp/) enthalten.



So erstellen Sie Vertrauensstellungen für Outlook Web App mithilfe des AD FS-Verwaltungs-Snap-Ins in Windows Server 2012 R2:

1.  Klicken Sie in **Server-Manager** auf **Tools** und wählen Sie anschließend **AD FS-Verwaltung** aus.

2.  Klicken Sie im **AD FS-Snap-In** unter **AD FS\\Vertrauensstellungen** mit der rechten Maustaste auf **Vertrauensstellungen**. Klicken Sie dann auf **Vertrauensstellung hinzufügen**, um den Assistenten **Vertrauensstellung hinzufügen** zu öffnen.

3.  Klicken Sie auf der **Begrüßungsseite** auf **Start**.

4.  Klicken Sie auf der Seite **Datenquelle auswählen** auf **Daten der vertrauenden Seite manuell eingeben** und anschließend auf **Weiter**.

5.  Auf der Seite **Anzeigename angeben** geben Sie in das Feld **Anzeigename** Folgendes ein: **Outlook Web App**. Geben Sie dann unter **Notizen** eine Beschreibung der vertrauenden Seite ein (z. B. **This is a trust for https://mail.contoso.com/owa**) und klicken Sie anschließend auf **Weiter**.

6.  Klicken Sie auf der Seite **Profil auswählen** auf **AD FS-Profil** und anschließend auf **Weiter**.

7.  Klicken Sie auf der Seite **Zertifikat konfigurieren** auf **Weiter**.

8.  Klicken Sie auf der Seite **URL konfigurieren** auf **Unterstützung für den passiven Verbund mit WS-Protokoll aktivieren**. Geben Sie dann unter **URL der vertrauenden Seite für den passiven Verbund mit dem WS-Protokoll** Folgendes ein: **type https://mail.contoso.com/owa**. Klicken Sie anschließend auf **Weiter**.

9.  Geben Sie auf der Seite **IDs konfigurieren** eine oder mehrere IDs für die vertrauende Seite ein. Klicken Sie auf **Hinzufügen**, um sie zur Liste hinzuzufügen, und klicken Sie anschließend auf **Weiter**.

10. Auf der Seite **Mehrstufige Authentifizierung jetzt konfigurieren?** wählen Sie **Mehrstufige Authentifizierungseinstellungen für diese Vertrauensstellung konfigurieren**.

11. Auf der Seite **Mehrstufige Authentifizierung konfigurieren** prüfen Sie, ob **Ich möchte jetzt keine mehrstufigen Authentifizierungseinstellungen für diese Vertrauensstellung konfigurieren** ausgewählt ist, und klicken Sie dann auf **Weiter**.

12. Auf der Seite **Regeln für Ausstellungsautorisierung wählen** wählen Sie **Allen Benutzern Zugriff auf diese vertrauende Seite gewähren** aus. Klicken Sie dann auf **Weiter**.

13. Auf der Seite **Vertrauensstellung kann hinzugefügt werden** prüfen Sie die Einstellungen und klicken dann auf **Weiter**, um die Daten der Vertrauensstellung zu speichern.

14. Auf der Seite **Fertig stellen** stellen Sie sicher, dass die Option **Dialog zum Bearbeiten der Anspruchsregeln für diese Vertrauensstellung öffnen, wenn der Assistent geschlossen wird** nicht aktiviert ist. Klicken Sie dann auf **Schließen**.

Um eine Vertrauensstellung für die Exchange-Verwaltungskonsole zu erstellen, müssen Sie diese Schritte erneut ausführen und eine zweite Vertrauensstellung erstellen. Allerdings geben Sie statt **Outlook Web App** als Anzeigenamen **EAC** ein. Als Beschreibung geben Sie **This is a trust for the Exchange Admin Center** ein, die **URL der vertrauenden Seite für den passiven Verbund mit dem WS-Protokoll** lautet **https://mail.contoso.com/ecp**.

Bei einem anspruchsbasierten Identitätsmodell ist die Funktion von Active Directory-Verbunddiensten (AD FS) als Verbunddienst, ein Token auszustellen, das eine Reihe von Ansprüchen enthält. Anspruchsregeln bestimmen die Entscheidungen in Bezug auf Ansprüche, die AD FS stellt. Anspruchsregeln und alle Serverkonfigurationsdaten werden in der AD FS-Konfigurationsdatenbank gespeichert.

Es ist erforderlich, dass Sie zwei Anspruchsregeln erstellen:

  - Active Directory-Benutzer-SID

  - Active Directory UPN

So fügen Sie die erforderlichen Anspruchsregeln hinzu:

1.  Klicken Sie in **Server-Manager** auf **Tools** und anschließend auf **AD FS-Verwaltung**.

2.  Klicken Sie in der Konsolenstruktur unter **AD FS\\Vertrauensstellungen** entweder auf **Vertrauensstellungen von Anspruchsanbietern** oder **Vertrauensstellungen von vertrauenden Seiten** und anschließend auf die Vertrauensstellung für Outlook Web App.

3.  Klicken Sie im Fenster **Vertrauensstellungen von vertrauenden Seiten** mit der rechten Maustaste auf die Vertrauensstellung Outlook Web App und klicken Sie anschließend auf **Anspruchsregeln bearbeiten**.

4.  Im Fenster **Anspruchsregeln bearbeiten** klicken Sie auf der Registerkarte **Ausstellungstransformationsregeln** auf **Regel hinzufügen**, um den Assistenten zum Hinzufügen einer Regel zur Anspruchstransformation zu starten.

5.  Wählen Sie auf der Seite **Regelvorlage auswählen** unter **Anspruchsregelvorlage** den Eintrag **Ansprüche mit einer benutzerdefinierten Regel senden** aus der Liste aus und klicken Sie auf **Weiter**.

6.  Auf der Seite **Regel konfigurieren** geben Sie beim Schritt **Regeltyp wählen** unter **Name der Anspruchsregel** den Namen der Anspruchsregel ein. Verwenden Sie einen beschreibenden Namen, beispielsweise **ActiveDirectoryUserSID**. Geben Sie unter **Benutzerdefinierte Regel** die folgende Anspruchsregel-Sprachsyntax für die Regel ein:
    
        c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"] => issue(store = "Active Directory", types = ("http://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid"), query = ";objectSID;{0}", param = c.Value);

7.  Klicken Sie auf der Seite **Regel konfigurieren** auf **Fertig stellen**.

8.  Im Fenster **Anspruchsregeln bearbeiten** klicken Sie auf der Registerkarte **Ausstellungstransformationsregeln** auf **Regel hinzufügen**, um den Assistenten zum Hinzufügen einer Regel zur Anspruchstransformation zu starten.

9.  Wählen Sie auf der Seite **Regelvorlage auswählen** unter **Anspruchsregelvorlage** den Eintrag **Ansprüche mit einer benutzerdefinierten Regel senden** aus der Liste aus und klicken Sie auf **Weiter**.

10. Auf der Seite **Regel konfigurieren** geben Sie beim Schritt **Regeltyp wählen** unter **Name der Anspruchsregel** den Namen der Anspruchsregel ein. Verwenden Sie einen beschreibenden Namen, beispielsweise **ActiveDirectoryUPN**. Geben Sie unter **Benutzerdefinierte Regel** die folgende Anspruchsregel-Sprachsyntax für die Regel ein:
    
        c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"] => issue(store = "Active Directory", types = ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"), query = ";userPrincipalName;{0}", param = c.Value);

11. Klicken Sie auf **Fertig stellen**.

12. Klicken Sie im Fenster **Anspruchsregeln bearbeiten** auf **Übernehmen** und dann auf **OK**.

13. Wiederholen Sie die Schritte 3 bis 12 dieses Verfahrens für die Vertrauensstellung der Exchange-Verwaltungskonsole.

Alternativ können Sie Vertrauensstellungen und Anspruchsregeln mithilfe von Windows PowerShell erstellen:

1.  Erstellen Sie die beiden TXT-Dateien "IssuanceAuthorizationRules.txt" und "IssuanceTransformRules.txt".

2.  Importieren Sie ihre Inhalte in zwei Variablen.

3.  Führen Sie zum Erstellen der Vertrauensstellungen die folgenden zwei Cmdlets aus. In diesem Beispiel werden dadurch auch die Anspruchsregeln konfiguriert.

**IssuanceAuthorizationRules.txt enthält:**

    @RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit", Value = "true");

**IssuanceTransformRules.txt enthält:**

    @RuleName = "ActiveDirectoryUserSID" c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"] => issue(store = "Active Directory", types = ("http://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid"), query = ";objectSID;{0}", param = c.Value); 
    
    @RuleName = "ActiveDirectoryUPN" c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"] => issue(store = "Active Directory", types = ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"), query = ";userPrincipalName;{0}", param = c.Value);

**Führen Sie die folgenden Befehle aus:**

    [string]$IssuanceAuthorizationRules=Get-Content -Path C:\IssuanceAuthorizationRules.txt
    
    [string]$IssuanceTransformRules=Get-Content -Path c:\IssuanceTransformRules.txt
    
    Add-ADFSRelyingPartyTrust -Name "Outlook Web App" -Enabled $true -Notes "This is a trust for https://mail.contoso.com/owa/" -WSFedEndpoint https://mail.contoso.com/owa/ -Identifier https://mail.contoso.com/owa/ -IssuanceTransformRules $IssuanceTransformRules -IssuanceAuthorizationRules $IssuanceAuthorizationRules
    
    Add-ADFSRelyingPartyTrust -Name "Exchange Admin Center (EAC)" -Enabled $true -Notes "This is a trust for https://mail.contoso.com/ecp/" -WSFedEndpoint https://mail.contoso.com/ecp/ -Identifier https://mail.contoso.com/ecp/ -IssuanceTransformRules $IssuanceTransformRules -IssuanceAuthorizationRules $IssuanceAuthorizationRules

## Schritt 4: Installieren des Webanwendungsproxy-Rollendiensts (optional)


> [!NOTE]
> Die Schritte 4, 5 und 6 sind für Benutzer bestimmt, die Exchange OWA und die Exchange-Systemsteuerung (ECP) mit dem Webanwendungsproxy veröffentlichen möchten und die die AD&nbsp;FS-Authentifizierung mithilfe des Webanwendungsproxy durchführen möchten. Das Veröffentlichen von Exchange über den Webanwendungsproxy ist jedoch nicht erforderlich. Sie können also mit Schritt 7 fortfahren, wenn Sie den Webanwendungsproxy nicht verwenden und die AD&nbsp;FS-Authentifizierung von Exchange durchgeführt werden soll.



Webanwendungsproxy ist ein neuer Remotezugriff-Rollendienst in Windows Server 2012 R2. Webanwendungsproxy bietet Reverseproxy-Funktionalität für Webanwendungen in Ihrem Unternehmensnetzwerk, sodass Benutzer von vielen Geräten von außerhalb des Unternehmensnetzwerks auf diese Anwendungen zugreifen können. Webanwendungsproxy nimmt mithilfe von Active Directory-Verbunddiensten (AD FS) eine Vorauthentifizierung des Zugriffs auf Webanwendungen vor und fungiert außerdem auch als AD FS-Proxy. Webanwendungsproxy ist zwar nicht erforderlich, wird aber empfohlen, wenn AD FS für externe Clients zugänglich ist. Allerdings wird der Offlinezugriff in Outlook Web App nicht unterstützt, wenn die AD FS-Authentifizierung über Webanwendungsproxy verwendet wird. Weitere Informationen zur Integration mit Webanwendungsproxy finden Sie unter [Installieren und Konfigurieren von Webanwendungsproxy für das Veröffentlichen interner Anwendungen](https://go.microsoft.com/fwlink/?linkid=392705).


> [!WARNING]
> Sie können Webanwendungsproxy nicht auf demselben Server installieren wie AD&nbsp;FS.



Um Webanwendungsproxy bereitzustellen, müssen Sie die Serverrolle "Remotezugriff" mit dem Webanwendungsproxy-Rollendienst auf einem Server installieren, der als Webanwendungsproxy-Server fungieren wird. So installieren Sie den Webanwendungsproxy-Dienst:

1.  Klicken Sie auf dem Webanwendungsproxy-Server unter **Server-Manager** auf **Verwalten** und anschließend auf **Rollen und Funktionen**.

2.  Klicken Sie im Assistenten "Rollen und Funktionen hinzufügen" dreimal auf **Weiter**, um zur Seite **Serverrollen** zu gelangen.

3.  Wählen Sie auf der Seite **ServerrollenRemotezugriff** aus der Liste aus und klicken Sie anschließend auf **Weiter**.

4.  Klicken Sie auf der Seite **Funktionen** auf **Weiter**.

5.  Lesen Sie auf der Seite **Remotezugriff** die Informationen und klicken Sie dann auf **Weiter**.

6.  Wählen Sie auf der Seite **RollendiensteWebanwendungsproxy** aus. Klicken Sie im Fenster **Assistent zum Hinzufügen von Rollen und Funktionen** auf **Funktionen hinzufügen** und dann auf **Weiter**.

7.  Klicken Sie im Fenster **Bestätigung** auf **Installieren**. Falls erforderlich, können Sie auch **Zielserver wenn nötig automatisch neu starten** aktivieren.

8.  Bestätigen Sie im Dialogfeld **Installationsstatus**, dass die Installation erfolgreich war, und klicken Sie dann auf **Schließen**.

Das folgende Windows PowerShell-Cmdlet erfüllt dieselbe Funktion wie die vorangegangenen Schritte.

    Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools

## Schritt 5: Konfigurieren des Webanwendungsproxy-Rollendiensts (optional)

Sie müssen Webanwendungsproxy konfigurieren, um eine Verbindung mit dem AD FS-Server herzustellen. Wiederholen Sie dieses Verfahren für alle Server, die Sie als Webanwendungsproxy-Server bereitstellen möchten.

So konfigurieren Sie den Rollendienst für die Webanwendung:

1.  Klicken Sie auf dem Webanwendungsproxy-Server unter **Server-Manager** auf **Tools** und anschließend auf **Remotezugriffsverwaltung**.

2.  Klicken Sie im Bereich **Konfiguration** auf **Webanwendungsproxy**.

3.  In der Konsole **Remotezugriffsverwaltung** klicken Sie im mittleren Bereich auf **Konfigurationsassistenten für Webanwendungsproxy ausführen**.

4.  Klicken Sie im Dialogfeld **Willkommen** des Konfigurationsassistenten für Webanwendungsproxy auf **Weiter**.

5.  Führen Sie anschließend auf der Seite **Verbundserver** die folgenden Schritte aus und klicken Sie dann auf **Weiter**:
    
      - Geben Sie im Feld **Verbunddienstname** den vollqualifizierten Domänennamen (FQDN) des AD FS-Servers ein, z. B. **adfs.contoso.com**.
    
      - Geben Sie im Feld **Benutzername** und **Kennwort** die Anmeldeinformationen eines lokalen Administratorkontos auf den AD FS-Servern ein.

6.  Wählen Sie im Dialogfeld **AD FS-Proxyzertifikat** aus der Liste der aktuell auf dem Webanwendungsproxy-Server installierten Zertifikate das Zertifikat aus, das von Webanwendungsproxy für die AD FS-Proxyfunktion verwendet werden soll. Klicken Sie dann auf **Weiter**. Das Zertifikat, das Sie hier auswählen, sollte dasjenige sein, dessen Antragstellername der Verbunddienstname ist, z. B. **adfs.contoso.com**.

7.  Prüfen Sie im Dialogfeld **Bestätigung** die Einstellungen. Falls erforderlich, können Sie das Windows PowerShell-Cmdlet kopieren, um weitere Installationen zu automatisieren. Klicken Sie auf **Konfigurieren**.

8.  Prüfen Sie im Dialogfeld **Ergebnisse**, ob die Installation erfolgreich war, und klicken Sie dann auf **Schließen**.

Das folgende Windows PowerShell-Cmdlet erfüllt dieselbe Funktion wie die vorangegangenen Schritte.

    Install-WebApplicationProxy -CertificateThumprint 1a2b3c4d5e6f1a2b3c4d5e6f1a2b3c4d5e6f1a2b -FederationServiceName adfs.contoso.com

## Schritt 6: Veröffentlichen von Outlook Web App und EAC mithilfe des Webanwendungsproxy (optional)

In Schritt 3 haben Sie Anspruchsvertrauensstellungen für Outlook Web App und Exchange-Verwaltungskonsole erstellt. Nun müssen Sie beide Anwendungen veröffentlichen. Bevor Sie das jedoch tun, prüfen Sie, ob eine Vertrauensstellung für sie erstellt wurde und sich auf dem Webanwendungsproxy-Server ein Zertifikat befindet, das für Outlook Web App und Exchange-Verwaltungskonsole geeignet ist. Für alle AD FS-Endpunkte, die vom Webanwendungsproxy veröffentlicht werden sollen, müssen Sie in der AD FS-Verwaltungskonsole den Endpunkt auf **Proxy aktiviert** festlegen.

Befolgen Sie die Schritte, um Outlook Web App mithilfe von Webanwendungsproxy zu veröffentlichen. Für die Exchange-Verwaltungskonsole wiederholen Sie diese Schritte. Wenn Sie die Exchange-Verwaltungskonsole veröffentlichen, müssen Sie den Namen, die externe URL, das externe Zertifikat und die Back-End-URL ändern.

So veröffentlichen Sie Outlook Web App und Exchange-Verwaltungskonsole mithilfe von Webanwendungsproxy:

1.  Auf dem Webanwendungsproxy-Server klicken Sie in der Konsole **Remotezugriffsverwaltung** im Bereich **Navigation** auf **Webanwendungsproxy**. Klicken Sie dann im Bereich **Aufgaben** auf **Veröffentlichen**.

2.  Klicken Sie im Assistenten zum Veröffentlichen neuer Anwendungen auf der Seite **Willkommen** auf **Weiter**.

3.  Klicken Sie auf der Seite **Vorauthentifizierung** auf **Active Directory-Verbunddienst (AD FS)** und anschließend auf **Weiter**.

4.  Auf der Seite **Vertrauende Seite** wählen Sie aus der Liste der vertrauenden Seiten die vertrauende Seite für die Anwendung aus, die Sie veröffentlichen wollen, und klicken Sie anschließend auf **Weiter**.

5.  Führen Sie anschließend auf der Seite **Veröffentlichungseinstellungen** die folgenden Schritte aus und klicken Sie dann auf **Weiter**:
    
    1.  Geben Sie einen Anzeigenamen für die Anwendung in das Feld **Name** ein. Dieser Name wird nur in der Liste der veröffentlichten Anwendungen in der **Remotezugriff-Verwaltungskonsole** verwendet. Sie können **OWA** und **EAC** für die Namen verwenden.
    
    2.  Geben Sie im Feld **Externe URL** die externe URL für diese Anwendung ein, z. B. **https://external.contoso.com/owa** für Outlook Web App und **https://external.contoso.com/ecp** für die Exchange-Verwaltungskonsole.
    
    3.  Wählen Sie aus der Liste **Externes Zertifikat** ein Zertifikat aus, dessen Antragstellername mit dem Hostnamen der externen URL übereinstimmt.
    
    4.  Geben Sie im Feld **Back-End-Server-URL** die URL des Back-End-Servers ein. Beachten Sie, dass dieser Wert automatisch eingegeben wird, wenn Sie die externe URL eingeben, und dass Sie ihn nur ändern sollten, wenn die Back-End-Server-URL davon abweicht, z. B. **https://mail.contoso.com/owa** für Outlook Web App und **https://mail.contoso.com/ecp** für die Exchange-Verwaltungskonsole.
    

    > [!NOTE]
    > Webanwendungsproxy kann Hostnamen in URLs übersetzen, für Pfade gilt dies jedoch nicht. Daher können Sie verschiedenen Hostnamen eingeben, müssen jedoch denselben Pfad eingeben. Sie können beispielsweise die externe URL <EM>https://external.contoso.com/app1/</EM> und die Back-End-Server-URL <EM>https://mail.contoso.com/app1/</EM> eingeben. Allerdings können Sie nicht die externe URL <EM>https://external.contoso.com/app1/</EM> und als Back-End-Server-URL <EM>https://mail.contoso.com/internal-app1/</EM> eingeben.



6.  Überprüfen Sie auf der Seite **Bestätigung** die Einstellungen und klicken Sie dann auf **Veröffentlichen**. Sie können den Windows PowerShell-Befehl kopieren, um weitere veröffentlichte Anwendungen einzurichten.

7.  Stellen Sie auf der Seite **Ergebnisse** sicher, dass die Anwendung erfolgreich veröffentlicht wurde, und klicken Sie anschließend auf **Schließen**.

Das folgende Windows PowerShell-Cmdlet erfüllt dieselben Aufgaben wie das vorangegangene Verfahren für Outlook Web App.

    Add-WebApplicationProxyApplication -BackendServerUrl 'https://mail.contoso.com/owa/' -ExternalCertificateThumbprint 'E9D5F6CDEA243E6E62090B96EC6DE873AF821983' -ExternalUrl 'https://external.contoso.com/owa/' -Name 'OWA' -ExternalPreAuthentication ADFS -ADFSRelyingPartyName 'Outlook Web App'

Das folgende Windows PowerShell-Cmdlet erfüllt dieselben Aufgaben wie das vorangegangene Verfahren für die Exchange-Verwaltungskonsole.

    Add-WebApplicationProxyApplication -BackendServerUrl 'https://mail.contoso.com/ecp/' -ExternalCertificateThumbprint 'E9D5F6CDEA243E6E62090B96EC6DE873AF821983' -ExternalUrl 'https://external.contoso.com/ecp/' -Name 'EAC' -ExternalPreAuthentication ADFS -ADFSRelyingPartyName 'Exchange Admin Center'

Nachdem Sie diese Schritte ausgeführt haben, führt das Webanwendungsproxy die AD FS-Authentifizierung für Outlook Web App und EAC-Clients durch und leitet auch die Verbindungen als Proxy an Exchange in ihrem Auftrag weiter. Sie müssen Exchange an sich nicht für die AD FS-Authentifizierung konfigurieren. Fahren Sie also mit Schritt 10 fort, um die Konfiguration zu testen.

## Schritt 7: Konfigurieren von Exchange 2013 für die Verwendung der AD FS-Authentifizierung

Wenn Sie AD FS für die anspruchsbasierte Authentifizierung mit Outlook Web App und Exchange-Verwaltungskonsole in Exchange 2013 konfigurieren, müssen Sie AD FS für Ihre Exchange-Organisation aktivieren. Zum Konfigurieren der AD FS-Einstellungen für Ihre Organisation müssen Sie das Cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)) verwenden:

  - Legen Sie als AD FS-Aussteller **https://adfs.contoso.com/adfs/ls** fest.

  - Legen Sie als AD FS-URIs **https://mail.contoso.com/owa** und **https://mail.contoso.com/ecp** fest.

  - Hier finden Sie das AD FS-Token Signierung Zertifikatfingerabdruck durch Verwendung Windows PowerShell auf dem AD FS-Server und `Get-ADFSCertificate -CertificateType "Token-signing"`eingeben. Klicken Sie dann, weisen Sie Tokensignatur Fingerabdruck des Zertifikats, den Sie gefunden. Wenn die AD FS Tokensignaturzertifikat abgelaufen ist, muss der Fingerabdruck aus der neuen AD FS Tokensignaturzertifikat mithilfe des Cmdlets [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)) aktualisiert werden.

Führen Sie die folgenden Befehle in der Exchange-Verwaltungsshell.

    $uris = @(" https://mail.contoso.com/owa/","https://mail.contoso.com/ecp/")
    Set-OrganizationConfig -AdfsIssuer "https://adfs.contoso.com/adfs/ls/" -AdfsAudienceUris $uris -AdfsSignCertificateThumbprint "88970C64278A15D642934DC2961D9CCA5E28DA6B"


> [!NOTE]
> Der Parameter <EM>-AdfsEncryptCertificateThumbprint</EM> wird für diese Szenarien nicht unterstützt.



Weitere Informationen und die Syntax finden Sie unter [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)) und [Get-ADFSCertificate](https://go.microsoft.com/fwlink/?linkid=392706).

## Schritt 8: Aktivieren der AD FS-Authentifizierung für die virtuellen Verzeichnisse „OWA\&quot; und „ECP\&quot;

Aktivieren Sie für die virtuellen Verzeichnisse "OWA" und "ECP" die AD FS-Authentifizierung als einzige Authentifizierungsmethode und deaktivieren Sie alle anderen Authentifizierungsmethoden.


> [!WARNING]
> Sie müssen das virtuelle Verzeichnis "ECP" vor dem virtuellen Verzeichnis "OWA" konfigurieren.



Konfigurieren Sie das virtuelle Verzeichnis ECP mithilfe der Exchange-Verwaltungsshell. Führen Sie in der Shell den folgenden Befehl ein.

    Get-EcpVirtualDirectory | Set-EcpVirtualDirectory -AdfsAuthentication $true -BasicAuthentication $false -DigestAuthentication $false -FormsAuthentication $false -WindowsAuthentication $false

Konfigurieren Sie das virtuelle Verzeichnis OWA mithilfe der Exchange-Verwaltungsshell. Führen Sie in der Shell den folgenden Befehl ein.

    Get-OwaVirtualDirectory | Set-OwaVirtualDirectory -AdfsAuthentication $true -BasicAuthentication $false -DigestAuthentication $false -FormsAuthentication $false -WindowsAuthentication $false -OAuthAuthentication $false


> [!NOTE]
> Exchange-Verwaltungsshell den vorstehenden Befehlen konfigurieren Sie die virtuellen Verzeichnisse "OWA" und "ECP" auf jedem Clientzugriffsserver in Ihrer Organisation. Wenn Sie diese Einstellungen gelten für alle Clientzugriffsserver möchten, verwenden Sie den Parameter <EM>-Identity</EM> , und geben Sie den Client Access Server. Es ist wahrscheinlich möchten diese Einstellungen nur für die Clientzugriffsserver in Ihrer Organisation angewendet Internet werden facing.



Weitere Informationen und die Syntax finden Sie unter [Get-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/aa998588\(v=exchg.150\)) und [Set-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/bb123515\(v=exchg.150\)) oder [Get-EcpVirtualDirectory](https://technet.microsoft.com/de-de/library/dd351058\(v=exchg.150\)) und [Set-EcpVirtualDirectory](https://technet.microsoft.com/de-de/library/dd297991\(v=exchg.150\)).

## Schritt 9: Neustart oder Wiederverwendung von Internetinformationsdiensten (Internet Information Services, IIS)

Nachdem Sie alle erforderlichen Schritte, einschließlich der Änderungen an virtuellen Exchange-Verzeichnissen, abgeschlossen haben, müssen Sie die Internetinformationsdienste neu starten. Verwenden Sie dazu eine der folgenden Methoden:

  - Mit Windows PowerShell:
    
        Restart-Service W3SVC,WAS -noforce

  - Mit einer Befehlszeile: Klicken Sie auf **Start**, klicken Sie auf **Ausführen** und geben Sie dann `IISReset /noforce` ein. Klicken Sie anschließend auf **OK**.

  - Mit dem Internetinformationsdienste-Manager: Klicken Sie in **Server-Manager** \> **IIS** auf **Tools** und anschließend auf **Internetinformationsdienste-Manager**. Klicken Sie im Fenster **Internetinformationsdienste** im Aktionsbereich unter **Server verwalten** auf **Neu starten**.

## Schritt 10: Testen der AD FS-Ansprüche für Outlook Web App und Exchange-Verwaltungskonsole

So testen Sie die AD FS-Ansprüche für Outlook Web App:

  - Melden Sie sich in Ihrem Webbrowser bei Outlook Web App an, z. B. **https://mail.contoso.com/owa**.

  - Wenn Sie im Browserfenster einen Zertifikatfehler erhalten, fahren Sie einfach fort, und rufen Sie die Outlook Web App-Website auf. Sie werden zur AD FS-Anmeldeseite weitergeleitet oder zur Eingabe der AD FS-Anmeldeinformationen aufgefordert.

  - Geben Sie Ihren Benutzernamen (Domäne\\Benutzer) und das Kennwort ein, und klicken Sie auf **Anmelden**.

Outlook Web App wird im Fenster geladen.

So testen Sie die AD FS-Ansprüche für die Exchange-Verwaltungskonsole:

1.  Rufen Sie im Webbrowser **https://mail.contoso.com/ecp** auf.

2.  Wenn Sie im Browserfenster einen Zertifikatfehler erhalten, fahren Sie einfach fort, und rufen Sie die ECP-Website auf. Sie werden zur AD FS-Anmeldeseite weitergeleitet oder zur Eingabe der AD FS-Anmeldeinformationen aufgefordert.

3.  Geben Sie Ihren Benutzernamen (Domäne\\Benutzer) und das Kennwort ein, und klicken Sie auf **Anmelden**.

4.  Die Exchange-Verwaltungskonsole sollte im Fenster geladen werden.

## Weitere hilfreiche Informationen

**Mehrstufige Authentifizierung**

Wenn bei lokalen Exchange 2013 SP1-Bereitstellungen Active Directory-Verbunddienste (AD FS) 2.0 mithilfe von Ansprüchen bereitgestellt und konfiguriert werden, können Outlook Web App und Exchange-Verwaltungskonsole in Exchange 2013 SP1 mehrstufige Authentifizierungsmethoden unterstützen. Dazu gehören zertifikatbasierte Authentifizierung, Authentifizierung oder Sicherheitstoken sowie Fingerabdruckauthentifizierung. Die zweistufige Authentifizierung wird häufig mit anderen Formen der Authentifizierung verwechselt. Für die mehrstufige Authentifizierung müssen zwei der drei Authentifizierungsfaktoren verwendet werden. Es handelt sich um die folgenden Faktoren:

  - Etwas, das nur der Benutzer weiß (z. B. Kennwort, PIN oder Muster)

  - Etwas, das nur der Benutzer besitzt (z. B. Geldkarte, Sicherheitstoken, Smartcard oder Mobiltelefon)

  - Ein Merkmal, das nur der Benutzer besitzt (z. B. eine biometrische Eigenschaft wie ein Fingerabdruck)

Weitere Informationen zur mehrstufigen Authentifizierung in Windows Server 2012 R2 finden Sie unter [Übersicht: Verwalten von Risiken mit zusätzlicher mehrstufiger Authentifizierung für sensible Anwendungen](https://go.microsoft.com/fwlink/?linkid=392707) und [Handbuch mit exemplarischer Vorgehensweise: Verwalten von Risiken mit zusätzlicher mehrstufiger Authentifizierung für sensible Anwendungen](https://go.microsoft.com/fwlink/?linkid=392708).

Beim AD FS-Rollendienst von Windows Server 2012 R2 fungiert der Verbunddienst als Sicherheitstokendienst, stellt Sicherheitstoken bereit, die mit Ansprüchen verwendet werden, und gibt Ihnen die Möglichkeit, mehrstufige Authentifizierung einzusetzen. Der Verbunddienst stellt Token auf Grundlage der angegebenen Anmeldeinformationen aus. Nachdem der Kontospeicher die Anmeldeinformationen eines Benutzers überprüft hat, werden die Ansprüche für den Benutzer entsprechend den Regeln der Vertrauensrichtlinie erstellt und anschließend einem Sicherheitstoken hinzugefügt, das an den Client ausgegeben wird. Weitere Informationen zu Ansprüchen finden Sie unter [Grundlegendes zu Ansprüchen](https://go.microsoft.com/fwlink/?linkid=392709).

**Gleichzeitige Installation mit anderen Exchange-Versionen**

Es ist möglich, die AD FS-Authentifizierung für Outlook Web App und Exchange-Verwaltungskonsole zu verwenden, wenn Sie mehrere Exchange-Versionen in Ihrer Organisation bereitgestellt haben. Dieses Szenario wird nur für die Bereitstellung von Exchange 2010 und Exchange 2013 unterstützt, und nur dann, wenn alle Clients eine Verbindung über die Exchange 2013-Server herstellen **und** diese Exchange 2013-Server für die AD FS-Authentifizierung konfiguriert wurden.

Benutzer mit einem Postfach auf einem Exchange 2010-Server können über einen Exchange 2013-Server, der für die AD FS-Authentifizierung konfiguriert wurde, auf ihre Postfächer zugreifen. Die erste Clientverbindung mit dem Exchange 2013-Server verwendet die AD FS-Authentifizierung. Die weitergeleitete Verbindung mit dem Exchange 2010-Server verwendet jedoch Kerberos. Es gibt keine Möglichkeit, Exchange Server 2010 für die direkte AD FS-Authentifizierung zu konfigurieren.


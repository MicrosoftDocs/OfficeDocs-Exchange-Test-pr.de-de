---
title: 'Erstellen einer Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration: Exchange 2013 Help'
TOCTitle: Erstellen einer Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration
ms:assetid: 997a25d3-7fb3-4d4e-bb28-defcbf542c99
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ200787(v=EXCHG.150)
ms:contentKeyID: 50477185
ms.date: 03/16/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration

Dieses Thema ist in Bearbeitung.  

_<strong>Gilt für:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-09_

Durch Einrichten einer Hybridbereitstellung können Sie die Funktionsvielfalt und die administrativen Möglichkeiten, die Ihre vorhandene lokale Exchange Server-Organisation bietet, auf die Cloud ausdehnen. Eine Hybridbereitstellung bietet außerdem Unterstützung für eine cloudbasierte Archivierungslösung für Ihre lokalen Postfächer mit Exchange Online-Archivierung und kann als Zwischenschritt in Richtung einer vollständigen Migration Ihrer lokalen Postfächer zu Exchange Online fungieren.

In diesem Thema wird beschrieben, wie Sie mit dem Assistenten für die Hybridkonfiguration eine Hybridbereitstellung für Ihre lokale Exchange-Organisation und Ihre Exchange Online-Organisation in Office 365 für Unternehmen konfigurieren können. Dazu wird eine Hybridbereitstellung für die folgende Organisationskonfiguration erstellt:

  - Die lokale Organisation ist eine lokale Exchange-Organisation mit einer einzelnen Gesamtstruktur.

  - In der lokalen Organisation wird für den lokalen Schutz kein vorhandener Microsoft-EOP-Dienst (Exchange Online Protection) verwendet.

  - In der lokalen Organisation werden keine Edge-Transport-Server bereitgestellt. Im Assistenten für die Hybridkonfiguration wird das Konfigurieren von Edge-Transport-Servern als Teil einer Hybridbereitstellung unterstützt, das Konfigurieren von Edge-Transport-Servern mit dem Assistenten wird in diesem Thema aber nicht beschrieben.


> [!IMPORTANT]
> Das Konfigurieren einer Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration erfordert mehrere wichtige Voraussetzungen, damit der Assistent erfolgreich ausgeführt werden kann und die Features der Hybridbereitstellung ordnungsgemäß funktionieren. Bevor Sie mit dem Assistenten für die Hybridkonfiguration Ihre Hybridbereitstellung erstellen und konfigurieren können, müssen alle Voraussetzungen erfüllt sein, die unter <A href="hybrid-deployment-prerequisites-exchange-2013-help.md">Voraussetzungen für die Hybridbereitstellung</A> aufgeführt sind.<BR>Des Weiteren ist der <A href="http://technet.microsoft.com/exdeploy2013">Bereitstellungs-Assistent für Exchange Server</A> ein kostenloses webbasiertes Tool, mit dem Sie eine Hybridbereitstellung zwischen Ihrer lokalen Organisation und Office&nbsp;365 konfigurieren oder vollständig zu Office&nbsp;365 migrieren können. Der Assistent stellt Ihnen einige einfache Fragen und erstellt dann anhand Ihrer Antworten eine angepasste Checkliste mit Anweisungen zum Konfigurieren der Hybridbereitstellung. Wir empfehlen dringend, zum Generieren einer angepassten Checkliste für die Hybridbereitstellung für die speziellen Anforderungen Ihrer Organisation den Bereitstellungs-Assistenten zu verwenden.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Hybridbereitstellungen finden Sie unter [Hybrid-Bereitstellungsverfahren](hybrid-deployment-procedures-exchange-2013-help.md).

Weitere Informationen zu Hybridbereitstellungen finden Sie unter [Hybridbereitstellungen in Exchange Server](exchange-server-hybrid-deployments-exchange-2013-help.md). Weitere Informationen zu Office 365 finden Sie unter [Was ist Office 365?](http://go.microsoft.com/fwlink/?linkid=266712).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 30 Minuten
    

    > [!IMPORTANT]
    > Das Konfigurieren der Anforderungen für eine Hybridbereitstellung wird deutlich länger dauern als die geschätzte Zeit für ein Ausführen der Schritte des Assistenten für die Hybridkonfiguration, die in diesem Thema aufgeführt sind. Beispielsweise erfordern das Anmelden bei Office 365 für Unternehmen, das Konfigurieren der Active Directory-Synchronisierung und das Zuweisen von Exchange Online-Lizenzen einige Zeit sowie möglicherweise Änderungen an der Netzwerktopologie. Für das Abschließen der gesamten Konfiguration der Hybridbereitstellung sollten Sie mehr Zeit einplanen als die Zeit, die zum Ausführen dieses Verfahrens angegeben ist.



  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Hybridbereitstellungen" im Thema [Exchange- und Shellinfrastrukturberechtigungen](https://technet.microsoft.com/de-de/library/dd638114\(v=exchg.150\)).

  - Sie müssen den Hybridkonfigurations-Assistenten von einem Computer mit der neuesten Version einer unterstützten Version von Exchange ausführen. Die abschließenden Schritte im Assistenten für die Hybridkonfiguration, mit denen die Exchange-OAuth-Authentifizierung konfiguriert wird, müssen auf einem lokalen Exchange-Server oder einem Server oder Computer in der Domäne ausgeführt werden. Außerdem funktioniert der OAuth-Authentifizierungsprozess am besten, wenn die Desktopversion von Internet Explorer 11 oder höher verwendet wird.

  - Lesen Sie [Hybridbereitstellungen in Exchange Server](exchange-server-hybrid-deployments-exchange-2013-help.md), und machen Sie sich klar, welche Bereiche vom Konfigurieren einer Hybridbereitstellung betroffen sind.

  - Sorgen Sie dafür, dass alle Anforderungen für eine Hybridbereitstellung erfüllt werden, die unter [Voraussetzungen für die Hybridbereitstellung](hybrid-deployment-prerequisites-exchange-2013-help.md) beschrieben sind.

  - Die Microsoft-Remoteverbindungsuntersuchung überprüft die externen Verbindungen Ihrer lokalen Exchange-Organisation und stellt sicher, dass die Voraussetzungen für die Konfiguration Ihrer Hybridbereitstellung erfüllt sind. Es wird dringend empfohlen, Ihre lokale Organisation mit der Remoteverbindungsuntersuchung zu überprüfen, bevor Sie Ihre Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration konfigurieren. Weitere Informationen finden Sie unter [Remote Connectivity Analyzer](http://go.microsoft.com/fwlink/p/?linkid=167905).

  - Wir empfehlen dringend das Konfigurieren des einmaligen Anmeldens mit Azure Active Directory-Connect-Kennwortsynchronisierung. Mit der einmaligen Anmeldung können Benutzer mit denselben Anmeldeinformationen (Benutzername und Kennwort) auf die lokale und auf die Exchange Online-Organisation zugreifen. Das einmalige Anmelden stellt außerdem sicher, dass Benutzer nicht zur Eingabe ihrer Anmeldeinformationen aufgefordert werden, wenn sie in der Exchange Online-Organisation auf archivierte Inhalte zugreifen (sofern die Exchange Online-Archivierung verwendet wird). Weitere Informationen zur Kennwortsynchronisierung finden Sie unter [Azure AD Connect-Synchronisierung: Implementieren der Kennwortsynchronisierung](http://go.microsoft.com/fwlink/p/?linkid=723513).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](https://technet.microsoft.com/de-de/library/jj150484\(v=exchg.150\)).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen einer Hybridbereitstellung mit der Exchange-Verwaltungskonsole und dem Assistenten für die Hybridkonfiguration

Gehen Sie wie folgt vor, um eine Hybridbereitstellung zu erstellen und zu konfigurieren:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole auf einem Exchange-Server in Ihrer lokalen Organisation zum Knoten **Hybrid**.

2.  Klicken Sie im Knoten **Hybrid** auf **Konfigurieren**, um Ihre Office 365-Anmeldeinformationen einzugeben.
    

    > [!IMPORTANT]
    > Wenn sich Ihre lokale Organisation in China befindet und Ihr Office&nbsp;365-Mandant von 21Vianet gehostet wird, müssen Sie das Kontrollkästchen aktivieren, das besagt, dass Ihre Office&nbsp;365-Organisation von 21Vianet gehostet wird. Wenn Ihr Office&nbsp;365-Mandant von 21Vianet gehostet wird und dieses Kontrollkästchen nicht aktiviert ist, stellt der Assistent für die Hybridkonfiguration keine Verbindung zum 21Vianet-Dienst her, Ihre Anmeldeinformationen für das Office&nbsp;365-Konto werden nicht erkannt, und der Assistent wird nicht ordnungsgemäß abgeschlossen.



3.  Wählen Sie an der Eingabeaufforderung zum Anmelden bei Office 365 **Bei Office 365 anmelden** aus, und geben Sie die Kontoanmeldeinformationen ein. Das Konto, an dem Sie sich anmelden, muss ein globaler Administrator in Office 365 sein.

4.  Klicken Sie erneut auf **Konfigurieren**, um den Assistenten für die Hybridkonfiguration zu starten.

5.  Klicken Sie auf der Seite **Microsoft Office 365-Assistenten für die Hybridkonfiguration herunterladen** auf **Hier klicken**, um den Assistenten herunterzuladen. Klicken Sie, wenn Sie dazu aufgefordert werden, auf **Installieren** im Dialogfeld **Anwendung installieren**.

6.  Klicken Sie auf **Weiter**, und wählen Sie dann im Abschnitt **Lokale Exchange Server-Organisation** die Option **Server erkennen, auf dem Exchange 2013 CAS oder Exchange 2016 ausgeführt wird** aus. Der Assistent versucht, einen lokalen Exchange-Server zu erkennen. Wenn der Assistent keinen Exchange-Server erkennt, oder wenn Sie einen anderen Server verwenden möchten, wählen Sie **Einen Server mit Exchange 2013 CAS oder Exchange 2016 angeben** aus, und geben Sie dann den internen FQDN eines Exchange-Postfachservers ein.

7.  Wählen Sie im Abschnitt **Office 365 Exchange Online** die Option **Microsoft Office 365** und dann **Weiter** aus.

8.  Wählen Sie auf der Seite **Anmeldeinformationen** im Abschnitt **Geben Sie Ihre lokalen Kontoanmeldeinformationen ein** die Option **Aktuelle Windows-Anmeldeinformationen verwenden** aus, damit der Assistent das Konto verwendet, mit dem Sie sich angemeldet haben, um auf Ihr lokales Active Directory und Ihre lokalen Exchange-Server zuzugreifen. Wenn Sie einen anderen Satz von Anmeldeinformationen angeben möchten, deaktivieren Sie **Aktuelle Windows-Anmeldeinformationen verwenden**, und geben Sie den Benutzernamen und das Kennwort eines Active Directory-Kontos ein, das Sie verwenden möchten. Unabhängig von Ihrer Auswahl muss das von Ihnen verwendete Konto ein Mitglied der Sicherheitsgruppe Organisations-Admins sein.

9.  Geben Sie im Abschnitt **Office 365-Anmeldeinformationen eingeben** den Benutzernamen und das Kennwort für ein Office 365-Konto ein, das über globale Administratorberechtigungen verfügt. Klicken Sie auf **Weiter**.

10. Auf der Seite **Überprüfen der Verbindungen und Anmeldeinformationen** stellt der Assistent eine Verbindung mit Ihrer lokalen Organisation und Ihrer Office 365-Organisation her, um Anmeldeinformationen und die aktuelle Konfiguration beider Organisationen zu überprüfen. Klicken Sie dann auf **Weiter**.

11. Wählen Sie unter **Hybriddomänen** die Domänen aus, die Sie in Ihre Hybridumgebung einschließen möchten. In den meisten Bereitstellungen können Sie die Spalte **Automatische Erkennung** für alle Domänen auf **False** festlegen. Wählen Sie neben einer Domäne nur **True** aus, wenn Sie den Assistenten zwingen möchten, die Autoerkennungsinformationen aus einer bestimmten Domäne zu verwenden. Klicken Sie auf **Weiter**.
    

    > [!IMPORTANT]
    > Es kann sein, dass der Schritt zur Auswahl der Domänen im Assistenten für die Hybridkonfiguration nicht angezeigt wird.<BR>Dieser Schritt wird übersprungen, wenn Folgendes zutrifft: 
    > <UL>
    > <LI>
    > <P>Sie haben Ihrem Office&nbsp;365-Mandanten nur eine lokale akzeptierte Domäne hinzugefügt. Da diese Domäne die einzige für die Konfiguration der Hybridbereitstellung verfügbare Domäne ist, wird sie automatisch ausgewählt, und der Schritt wird im Assistenten übersprungen.</P>
    > <LI>
    > <P>Es gibt keine lokalen akzeptierten Domänen, die Ihrem Office&nbsp;365-Mandanten hinzugefügt wurden. In diesem Fall wird ein Fehler angezeigt, und Sie müssen Ihrem Office&nbsp;365-Mandanten mindestens eine Domäne hinzufügen, bevor Sie zum nächsten Schritt wechseln können. Das Hinzufügen erfolgt über das Office&nbsp;365-Verwaltungsportal oder durch das optionale Konfigurieren von Active Directory-Verbunddiensten (AD&nbsp;FS) in Ihrer lokalen Organisation.</P></LI></UL>Dieser Schritt wird angezeigt, wenn Sie Ihrem Office&nbsp;365-Mandanten mehrere lokale akzeptierte Domänen hinzugefügt haben.



12. Klicken Sie auf der Seite **Verbundvertrauensstellung** auf **Aktivieren**, und klicken Sie dann auf **Weiter**.

13. Klicken Sie auf der Seite **Domänenbesitz** auf **Klicken Sie, um in die Zwischenablage zu kopieren**, um die Domänen-Prüftokeninformationen der Domänen, die Sie für die Aufnahme in die Hybridbereitstellung ausgewählt haben, zu kopieren. Öffnen Sie einen Texteditor (beispielsweise Editor), und fügen Sie die Tokeninformationen für diese Domänen ein. Bevor Sie im Assistenten für die Hybridkonfiguration zum nächsten Schritt wechseln, müssen Sie mit diesen Informationen einen TXT-Eintrag für jede Domäne in Ihrem öffentlichen DNS erstellen. Informationen zum Hinzufügen eines TXT-Eintrags zur DNS-Zone finden Sie in der Hilfe zu Ihrem DNS-Host. Klicken Sie auf **Weiter**, nachdem Sie die TXT-Einträge erstellt haben und die DNS-Einträge repliziert wurden.

14. Wählen Sie auf der Seite **Transportzertifikat** im Feld **Referenzserver auswählen** den Exchange-Server aus, der das Zertifikat enthält, das Sie weiter oben in der Checkliste konfiguriert haben.

15. Wählen Sie im Feld **Zertifikat auswählen** das Zertifikat aus, das für den sicheren E-Mail-Transport verwendet werden soll. In der Liste werden die digitalen Zertifikate angezeigt, die von einer externen Zertifizierungsstelle ausgegeben wurde, die auf den Postfachservern installiert ist, die Sie im vorherigen Schritt ausgewählt haben. Klicken Sie dann auf **Weiter**.

16. Geben Sie auf der Seite **FQDN der Organisation** den extern zugänglichen FQDN für den Internet-Exchange-Server ein. Office 365 verwendet diesen FQDN, um die Dienstconnectors für den sicheren E-Mail-Transport zwischen Ihren Exchange-Organisationen zu konfigurieren. Geben Sie beispielsweise „mail.contoso.com“ ein. Klicken Sie dann auf **Weiter**.

17. Die ausgewählten Optionen für die Konfiguration der Hybridbereitstellung wurden aktualisiert, Sie können nun die Änderungen der Exchange-Dienste und die Konfiguration der Hybridbereitstellung starten. Klicken Sie auf **Aktualisieren**, um die Konfiguration zu starten. Im Verlauf des Hybridkonfigurationsprozesses zeigt der Assistent die Feature- und Dienstbereiche an, die während ihrer Aktualisierung für die Hybridbereitstellung konfiguriert werden.

18. Der Assistent zeigt eine Meldung über die Fertigstellung und die Schaltfläche **Schließen** an. Klicken Sie auf **Schließen**, um den Konfigurationsprozess für die Hybridbereitstellung abzuschließen und den Assistenten zu beenden.

## Konfigurieren von OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen

Bei kombinierten Exchange 2013/2010- und Exchange 2013/2007-Hybridbereitstellungen wird die OAuth-basierte Authentifizierungsverbindung der neuen Hybridbereitstellung zwischen Office 365 und lokalen Exchange-Organisationen nicht im Assistenten für die Hybridkonfiguration konfiguriert. Für diese Bereitstellungen wird weiterhin standardmäßig der Prozess der Verbundvertrauensstellung verwendet. Bestimmte Exchange 2013-Features, wie die Messaging-Datensatzverwaltung (Message Records Management, MRM), die Compliance-Archivierung in Exchange 2013 und Compliance-eDiscovery sind in Ihrer gesamten Organisation nur dann vollständig verfügbar, wenn das neue Exchange-OAuth-Authentifizierungsprotokoll verwendet wird. Wir empfehlen, dass alle kombinierten Exchange 2013/2010- und Exchange 2013/2007-Organisationen, die diese Features als Teil einer neuen Hybridbereitstellung mit Exchange Online implementieren möchten, die Exchange-OAuth-Authentifizierung konfigurieren, nachdem sie ihre Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration konfiguriert haben.

Weitere Informationen zur Konfiguration finden Sie unter [Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen](https://technet.microsoft.com/de-de/library/dn594521\(v=exchg.150\)).

Weitere Informationen zu den Exchange-Sicherheits- und Kompatibilitätsfeatures, die die OAuth-Authentifizierung nutzen, finden Sie unter:

  - [Verwenden der OAuth-Authentifizierung zur Unterstützung der Archivierung in einer Exchange-Hybridbereitstellung](https://technet.microsoft.com/de-de/library/dn689104\(v=exchg.150\))

  - [Verwenden der OAuth-Authentifizierung zur Unterstützung von eDiscovery in einer Exchange-Hybridbereitstellung](https://technet.microsoft.com/de-de/library/dn497703\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Der erfolgreiche Abschluss des Assistenten für die Hybridkonfiguration ist der erste Hinweis darauf, dass das Konfigurieren der Hybridbereitstellung erwartungsgemäß verlaufen ist.

Gehen Sie wie folgt vor, um sich weiter zu vergewissern, dass die Hybridbereitstellung erfolgreich erstellt und konfiguriert wurde:

  - Führen Sie in der Exchange-Verwaltungsshell folgenden Befehl für die lokale Organisation aus. Dieser Befehl zeigt die Konfigurationswerte und -einstellungen der Hybridbereitstellung, Hybridfeatures und Transportendpunkte an. Vergewissern Sie sich, dass diese Werte korrekt sind.
    
        Get-HybridConfiguration

  - Überprüfen Sie, ob der Assistent für die Hybridkonfiguration alle Konfigurationsschritte ausgeführt hat, indem Sie das Hybridkonfigurationsprotokoll auswerten. Standardmäßig befindet sich das Protokoll auf dem lokalen Postfachserver im Verzeichnis "C:\\Programme\\Microsoft\\Exchange Server\\V15\\Logging\\Update-HybridConfiguration".

  - Verschieben Sie ein lokales Postfach in die Exchange Online-Organisation, um zu testen, ob Postfachverschiebungen unterstützt werden. Oder erstellen Sie ein neues Benutzerpostfach in der Exchange Online-Organisation, um die Freigabe von Frei/Gebucht-Kalenderinformationen zwischen den beiden Organisationen zu testen. Mit jeder der beiden Postfachaktionen können Sie außerdem feststellen, ob die Nachrichtenzustellung zwischen der lokalen und der Exchange Online-Organisation mit vorhandenen Postfächern ordnungsgemäß funktioniert und ob die Nachrichtenzustellung sicher ist und die Nachrichten als für die Exchange-Organisation interne Nachrichten verarbeitet werden.
    
      - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unternehmen** \> **Empfänger** \> **Postfächer**, um ein neues Remotepostfach in Exchange Online zu erstellen.
    
      - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Office 365** \> **Empfänger** \> **Migration**, um ein vorhandenes Postfach nach Exchange Online zu verschieben.


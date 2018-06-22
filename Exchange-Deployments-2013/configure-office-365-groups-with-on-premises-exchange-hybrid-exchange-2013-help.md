---
title: 'Konfigurieren von Office 365-Gruppen mit lokalen Exchange-Hybridlösungen: Exchange 2013 Help'
TOCTitle: Konfigurieren von Office 365-Gruppen mit lokalen Exchange-Hybridlösungen
ms:assetid: 184dfcfe-4b8e-450a-adc6-e647213b9501
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt668829(v=EXCHG.150)
ms:contentKeyID: 72513029
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Office 365-Gruppen mit lokalen Exchange-Hybridlösungen

 

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-06_

Erfahren Sie, wie Sie lokalen Exchange-Benutzern die Verwendung von Office 365-Gruppen in einer Hybridbereitstellung ermöglichen.

Gruppen sind ein Office 365-Dienst, mit dessen Hilfe Teams einfacher kommunizieren, Besprechungen planen und an Dokumenten zusammenarbeiten können. Alle mit einer Gruppe geteilten Informationen, von an die Gruppe gesendeten E-Mail-Nachrichten bis hin zu in den OneDrive for Business- oder SharePoint-Bibliotheken der Gruppe gespeicherten Dateien, stehen jedem Mitglied einer Gruppe zur Verfügung. Wenn Sie eine Hybridbereitstellung zwischen Ihrer lokalen Exchange-Organisation und Office 365 konfiguriert haben, können Sie mit den Schritten in diesem Thema in Office 365 erstellte Gruppen Ihren lokalen Benutzern zur Verfügung stellen.


> [!IMPORTANT]
> Die Verwendung von Office 365-Gruppen für lokale Benutzer in einer Exchange-Hybridbereitstellung ist ein neues Feature. Da es so neu ist, können beim Einrichten möglicherweise einige Probleme auftreten. Im Abschnitt Bekannte Probleme am Ende dieses Themas finden Sie ggf. Lösungen für Probleme, die möglicherweise auftreten können.



## Voraussetzungen

Bevor Sie beginnen, sollten Sie unbedingt die folgenden Schritte ausgeführt haben:

  - Sie haben Azure Active Directory Premium-Lizenzen für Ihren Mandanten erworben. Dies ist erforderlich, um das Rückschreiben von Gruppen in Azure Active Directory Connect zu aktivieren.

  - Sie haben eine Hybridbereitstellung zwischen Ihrer lokalen Exchange-Organisation und Office 365 konfiguriert und ihre Funktion überprüft. Weitere Informationen zu Exchange-Hybridbereitstellungen finden Sie hier:
    
      - [Hybridbereitstellungen in Exchange Server](exchange-server-hybrid-deployments-exchange-2013-help.md)
    
      - [Voraussetzungen für die Hybridbereitstellung](hybrid-deployment-prerequisites-exchange-2013-help.md)

  - Eine unterstützte Version von lokalem Exchange wurde installiert. Die Integration von lokalem Exchange mit Office 365-Gruppen ist verfügbar in KU1 und höheren Versionen von Exchange 2016 sowie in KU11 und neueren Versionen von Exchange 2013. Für die Exchange-Hybridbereitstellung muss jedoch das neueste kumulative Update (KU) von Exchange 2013 oder Exchange 2016 auf Ihren lokalen Exchange-Servern installiert sein. Wenn Sie das neueste KU nicht installieren können, kann das unmittelbar vor dem aktuellen KU veröffentlichte KU verwendet werden.

  - Single Sign-On wurde für die Verwendung von Azure Active Directory Connect (Azure AD Connect) konfiguriert. Dies ist erforderlich, um Benutzern zu erlauben, auf **Gruppendateien anzeigen** oder Links von Cloud-Anlagen in Gruppen-E-Mail-Nachrichten zu klicken.
    
    Wenn Sie Azure AD Connect für Single Sign-On in einer Exchange-Hybridbereitstellung konfigurieren, empfehlen wir Ihnen, die Synchronisierung von Kennwörtern zu verwenden. Active Directory Federation Services (AD FS) sollte nur in großen Organisationen verwendet werden oder wenn Sie über eine komplexe lokale Active Directory-Bereitstellung verfügen (z. B. mehrere AD-Gesamtstrukturen) oder wenn ein anderes Microsoft-Produkt AD FS zur Verwendung von Office 365 erfordert oder wenn Sie aus Compliance-Gründen Kennwörter nicht außerhalb des lokalen Netzwerks synchronisieren dürfen. Weitere Informationen zu Single Sign-On finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](http://go.microsoft.com/fwlink/p/?linkid=723513).

## Aktivieren des Gruppenrückschreibens in Azure AD Connect

1.  Wählen Sie im Azure AD Connect-Assistent **Synchronisierungsoptionen anpassen** aus, und klicken Sie dann auf **Weiter**.

2.  Geben Sie auf der Seite **Mit Azure AD verbinden** Ihre Office 365- und lokalen Anmeldedaten an. Klicken Sie auf **Weiter**.

3.  Überprüfen Sie auf der Seite **Optionale Features**, ob die Optionen, die Sie zuvor konfiguriert haben, weiterhin ausgewählt sind. Die am häufigsten ausgewählten Optionen sind **Exchange hybrid** und **Kennworthashsynchronisierung**.

4.  Wählen Sie **Gruppenrückschreiben** aus, und klicken Sie dann auf **Weiter**.

5.  Wählen Sie auf der Seite **Rückschreiben** eine Active Directory-Organisationseinheit (OU) zum Speichern von Objekten aus, die aus Office 365 in Ihre lokale Organisation synchronisiert werden, und klicken Sie dann auf **Weiter**.

6.  Klicken Sie auf der Seite **Bereit zur Konfiguration** auf **Konfigurieren**.

7.  Wenn der Assistent abgeschlossen ist, klicken Sie auf der Seite **Die Konfiguration ist abgeschlossen** auf **Beenden**.

8.  Öffnen Sie Active Directory-Benutzer und -Computers auf einem Active Directory-Domänencontroller, und suchen Sie das Benutzerkonto, das mit **AAD\_** beginnt. Notieren Sie den Namen dieses Kontos.

9.  Öffnen Sie die Exchange-Verwaltungsshell auf einem lokalen Exchange-Server, und führen Sie die folgenden Befehle aus.
    
        $AzureADConnectSWritebackAccount = <AAD_ account name from step 8>
        
        $GroupsOU = <writeback Active Directory OU selected in step 5>
        
        Import-Module "C:\Program Files\Microsoft Azure Active Directory Connect\AdPrep\AdSyncPrep.psm1"
        
        Initialize-ADSyncGroupWriteBack -ADConnectorAccount $AzureADConnectSWritebackAccount -GroupWriteBackContainerDN $GroupsOU

## Konfigurieren einer Gruppendomäne

Die primäre SMTP-Domäne einer Office 365-Gruppe wird als *Gruppendomäne* bezeichnet. Standardmäßig wird die in Ihrer Organisation als Standard verwendete Domäne als Gruppendomäne ausgewählt. Wenn Sie eine dedizierte Gruppendomäne hinzufügen möchten, können Sie anhand der folgenden Schritte eine Domäne hinzufügen. Weitere Informationen über die Unterstützung mehrerer Domänen für Office 365-Gruppen finden Sie unter [Unterstützung mehrerer Domänen für Office 365-Gruppen](https://support.office.com/de-de/article/multi-domain-support-for-office-365-groups-admin-help-7cf5655d-e523-4bc3-a93b-3ccebf44a01a)

1.  Fügen Sie Ihre neue Domäne der Office 365-Organisation hinzu. Wenn Sie beim Hinzufügen einer Domäne zu Office 365 Hilfe benötigen, finden Sie weitere Informationen unter [Hinzufügen von Benutzern und Domänen zu Office 365](https://support.office.com/de-de/article/add-users-and-domain-to-office-365-6383f56d-3d09-4dcb-9b41-b5f5a5efd611?ui=en-us%26rs=en-us%26ad=us)

2.  Fügen Sie die Gruppendomäne mit dem folgenden Befehl als akzeptierte Domäne in der lokalen Exchange-Organisation hinzu. Dies ist erforderlich, damit der hybride Sendeconnector zur Zustellung ausgehender Mail an die Gruppendomäne in Office 365 verwendet werden kann.
    
        New-AcceptedDomain -Name groups.contoso.com -DomainName groups.contoso.com -DomainType InternalRelay

3.  Erstellen Sie die folgenden öffentlichen DNS-Einträge bei Ihrem DNS-Anbieter.
    
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>DNS-Eintragsname</p></th>
    <th><p>DNS-Eintragstyp</p></th>
    <th><p>DNS-Eintragswert</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>groups.contoso.com</p></td>
    <td><p>MX</p></td>
    <td><p>groups-contoso-com.mail.protection.outlook.com</p>

    > [!NOTE]  
    > Das Format dieses DNS-Datensatzwerts lautet <EM>&lt;domain key&gt;</EM>.mail.protection.outlook.com. Informationen zum Ermitteln des Domänenschlüssels finden Sie unter <A href="https://support.office.com/de-de/article/gather-the-information-you-need-to-create-office-365-dns-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67?ui=en-us%26rs=en-us%26ad=us">Sammeln der zum Erstellen von Office 365-DNS-Einträgen erforderlichen Informationen</A>.


</td>
    </tr>
    <tr class="even">
    <td><p>autodiscover.groups.contoso.com</p></td>
    <td><p>CNAME</p></td>
    <td><p>autodiscover.outlook.com</p></td>
    </tr>
    </tbody>
    </table>
    

   > [!WARNING]  
   > Wenn der MX-DNS-Eintrag für die Gruppendomäne auf den lokalen Exchange-Server festgelegt ist, funktioniert der E-Mail-Fluss zwischen Benutzern in der lokalen Exchange-Organisation und der Office 365-Gruppe nicht ordnungsgemäß.



4.  Fügen Sie die Gruppendomäne mit dem folgenden Befehl dem hybriden Sendeconnector hinzu, der vom Assistenten für die Hybridkonfiguration in der lokalen Exchange-Organisation erstellt wurde.
    
        Set-SendConnector -Identity "Outbound to Office 365" -AddressSpaces "contoso.mail.onmicrosoft.com","groups.contoso.com"
    

    > [!NOTE]  
    > Wenn der Sendeconnector nicht aktualisiert oder die Gruppendomäne nicht als akzeptierte Domäne in der lokalen Exchange-Organisation hinzugefügt wird, wird aus einem lokalen Postfach gesendete Mail nicht an die Gruppe übermittelt, sofern die Gruppe nicht für den Empfang von Mail von externen Absendern konfiguriert ist.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sicherzustellen, dass Gruppen mit Ihrer Exchange-Hybridbereitstellung funktionieren, sollten Sie diese mithilfe eines lokalen Postfachs sowie eines Postfachs, das aus der lokalen Organisation zu Office 365 verschoben wurde, testen. Führen Sie die Schritte in den folgenden Abschnitten aus, um die einzelnen Test durchzuführen.

## Test mit einem lokalen Postfach

1.  Fügen Sie ein lokales Postfach zu einer Office 365-Gruppe hinzu.

2.  Fügen Sie ein Office 365-Postfach zu derselben Office 365-Gruppe hinzu.

3.  Melden Sie sich bei dem Office 365-Postfach mithilfe von Outlook im Web an.

4.  Posten Sie mit dem Office 365-Postfach eine Nachricht an die Gruppe.

5.  Öffnen Sie das lokale Postfach mithilfe von Outlook 2016 oder Outlook im Web.

6.  Überprüfen Sie, ob in dem Postfach eine E-Mail-Nachricht mit dem Post eingegangen ist, den Sie an die Office 365-Gruppe gesendet haben.

7.  Verfassen Sie im selben Postfach eine Antwort auf die Nachricht, und senden Sie sie an die Gruppe.

8.  Überprüfen Sie, ob die Nachricht von allen Mitgliedern der Gruppe angezeigt werden kann.

## Test mit einem zu Office 365 verschobenen Postfach

1.  Verschieben Sie ein Postfach aus der lokalen Exchange-Organisation nach Office 365.

2.  Fügen Sie das Postfach zu einer Office 365-Gruppe hinzu.

3.  Melden Sie sich in einer neuen Browsersitzung an dem Postfach an, das zu Office 365 verschoben wurde.

4.  Überprüfen Sie in Outlook im Web, ob die Gruppe in der linken Navigationsleiste angezeigt wird.

5.  Posten Sie eine Nachricht an die Gruppe.

6.  Überprüfen Sie, ob die Nachricht von allen Mitgliedern der Gruppe angezeigt werden kann.

## Bekannte Probleme

  - **Gruppen werden für zu Office 365 verschobene Postfächer nicht angezeigt** Wenn ein Benutzer aus Ihrer lokalen Exchange-Organisation zu Office 365 verschoben wird, werden Gruppen nicht im linken Navigationsbereich in Outlook oder Outlook im Web angezeigt. Um das Problem zu beheben, entfernen Sie das Postfach aus allen Gruppen, denen es angehört, und fügen Sie es wieder zu jeder einzelnen Gruppe hinzu.

  - **Neue Gruppen werden in der globalen Adressliste (GAL) der lokalen Exchange-Bereitstellung nicht angezeigt** Wenn eine neue Gruppe in Office 365 erstellt wird, wird sie nicht automatisch in der lokalen GAL angezeigt. Zur Behebung des Problems öffnen Sie die Exchange-Verwaltungsshell auf einem lokalen Exchange-Server, und führen Sie den folgenden Befehl aus.
    
        Update-Recipient "<group name>"

  - **Gruppen empfangen keine Nachrichten von lokalen Benutzern** Ein lokaler Benutzer kann keine Mail an eine Office 365-Gruppe senden, wenn Folgendes zutrifft:
    
      - Die Gruppendomäne ist als autoritative Domäne in Ihrer lokalen Exchange-Organisation konfiguriert.
    
      - Die Gruppe wurde vor kurzem erstellt, und die zugehörigen Informationen wurden noch nicht in Ihr lokales Active Directory zurückgeschrieben.
    
    Dieses Problem behebt sich von selbst, wenn Azure AD Connect die nächste Synchronisierung zwischen Office 365 und Ihrer lokalen Organisation ausführt. Die Azure AD Connect-Synchronisierung erfolgt alle dreißig Minuten.

  - **Lokale Benutzer können keine Links in Gruppennachrichtenfußzeilen verwenden**Lokale Benutzer können die Links **Gruppenunterhaltungen anzeigen** oder **Abonnement kündigen**, die in der Fußzeile jeder an sie gesendeten Gruppennachricht enthalten sind, nicht verwenden. Um das Abonnement einer Gruppe zu kündigen, müssen sich lokale Benutzer an einen Gruppenadministrator wenden.

  - **An die sekundäre SMTP-Adresse einer Gruppe gesendete Mail kann nicht übermittelt werden** Wenn mehrere E-Mail-Adressen zu einer Gruppe hinzugefügt werden, wird nur die primäre SMTP-Adresse in Ihr lokales Active Directory zurückgeschrieben. Wenn ein lokaler Benutzer versucht, eine Nachricht an die sekundäre SMTP-Adresse einer Gruppe zu senden, wird die Nachricht nicht übermittelt. Um dieses Problem zu vermeiden, konfigurieren Sie nur eine SMTP-Adresse für jede Gruppe.

  - **Lokale Benutzer können kein Administrator einer Gruppe werden** Lokale Benutzer können nicht direkt auf den Gruppenbereich zugreifen. Aus diesem Grund können sie nicht als Administrator einer Gruppe hinzugefügt werden.

  - **Die Zustellung externer E-Mails an eine Gruppe kann zu Fehlern führen, wenn Sie den zentralen Nachrichtenfluss aktiviert haben** Wenn der zentrale Nachrichtenfluss aktiviert ist, kann eine von einem externen Benutzer an eine Gruppe gesendete E-Mail-Nachricht nicht zugestellt werden, obwohl die Gruppe Nachrichten von externen Absendern zulässt.

  - **Lokale Benutzer können keine E-Mail-Nachricht als Gruppe senden** Ein lokaler Benutzer, der eine Nachricht als Office 365-Gruppe sendet, erhält auch dann eine Fehlermeldung, dass die Berechtigung verweigert wurde, wenn er für die Gruppe über die Berechtigung „Senden als“ verfügt. Die Berechtigung „Senden als“ in einer Gruppe funktioniert nur für Exchange Online-Postfachbenutzer.

  - **Beim Auswählen einer Gruppe über den linken Navigationsbereich von Outlook wird nicht das Gruppenpostfach geöffnet** Outlook verwendet die AutoErmittlungs-URL zum Öffnen eines Gruppenpostfachs. Wenn sich die primäre E-Mail-Adresse einer Gruppe in einer Domäne befindet, die nicht auf die AutoErmittlungs-URL von Office 365 (autodiscover.outlook.com) verweist, kann Outlook das Gruppenpostfach nicht öffnen. Um das Problem zu beheben, können Gruppen mit einer primären Adresse in einer Domäne bereitgestellt werden, die auf die AutoErmittlungs-URL von Office 365 verweist. Sie können eine E-Mail-Adressenrichtlinie konfigurieren, um jedem Gruppenpostfach eine primäre E-Mail-Adresse hinzuzufügen, die auf die AutoErmittlungs-URL von Office 365 verweist. Weitere Informationen finden Sie unter [Unterstützung mehrerer Domänen für Office 365-Gruppen](https://support.office.com/de-de/article/multi-domain-support-for-office-365-groups-admin-help-7cf5655d-e523-4bc3-a93b-3ccebf44a01a)


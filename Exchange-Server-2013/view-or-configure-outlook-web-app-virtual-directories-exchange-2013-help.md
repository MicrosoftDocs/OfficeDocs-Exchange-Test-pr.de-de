---
title: 'Anz. o. Konfig. d. virt. Outlook Web App-Verzeichnisse: Exchange 2013-Hilfe'
TOCTitle: Anzeigen oder Konfigurieren der virtuellen Outlook Web App-Verzeichnisse
ms:assetid: 90babcf6-4486-4e01-9819-6d3ca4ed756c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298140(v=EXCHG.150)
ms:contentKeyID: 50476240
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anzeigen oder Konfigurieren der virtuellen Outlook Web App-Verzeichnisse

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-08-12_

Sie können die Exchange-Verwaltungskonsole oder die Shell verwenden, um die Eigenschaften eines virtuellen Outlook Web App-Verzeichnisses anzuzeigen oder zu konfigurieren.


> [!WARNING]
> In Exchange Online haben Administratoren nicht die Möglichkeit, virtuelle Outlook Web App-Verzeichnisse anzuzeigen oder zu konfigurieren.



Wenn Sie die Shell zum Anzeigen der Eigenschaften eines virtuellen Outlook Web App-Verzeichnisses verwenden, wird eine Untermenge der verfügbaren Informationen zurückgegeben. Wenn Sie beispielsweise das Cmdlet **Get-OWAVirtualDirectory** verwenden, um Eigenschaften anzuzeigen, gibt Exchange die folgenden Informationen zurück:

  - Name des virtuellen Verzeichnisses

  - Servername

  - Version des Exchange-Servers

Sie können unter Verwendung der verfügbaren Parameter auch Informationen für ein bestimmtes virtuelles Verzeichnis auf einem bestimmten Server abrufen. Weitere Informationen zu den Parametern für das Cmdlet **Get-OWAVirtualDirectory** finden Sie unter [Get-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/aa998588\(v=exchg.150\)).

Wenn Sie die Exchange-Verwaltungskonsole zum Anzeigen der Eigenschaften eines virtuellen Outlook Web App-Verzeichnisses verwenden, können Sie die meisten Eigenschaften des angezeigten virtuellen Verzeichnisses anzeigen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Virtuelle Outlook Web App-Verzeichnisse" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anzeigen oder Konfigurieren der Eigenschaften des virtuellen Outlook Web App-Verzeichnisses mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Server** \> **Virtuelle Verzeichnisse**.
    
    Sie können die Dropdownlisten verwenden, um den Typ des Servers und des virtuellen Verzeichnisses auszuwählen. Standardmäßig werden alle Server und virtuellen Verzeichnisse angezeigt.

2.  Wählen Sie im Ergebnisbereich das virtuelle Verzeichnis aus, das Sie anzeigen oder bearbeiten möchten, und klicken Sie dann auf **Bearbeiten**.

3.  Auf der Registerkarte **Allgemein** können Sie die Eigenschaften der Standardwebsite von Outlook Web App anzeigen und eine externe sowie eine interne URL angeben. Zeigen Sie die folgenden Optionen an, oder wählen Sie sie aus:
    
      - **Server**   (schreibgeschützt) **Server** zeigt den Namen des Servers an, der als Host für das virtuelle Outlook Web App-Verzeichnis dient.
    
      - **Version**   (schreibgeschützt) **Version** zeigt die Version des Exchange-Servers an, auf dem sich das virtuelle Verzeichnis befindet.
    
      - **Website**   (schreibgeschützt) **Website** zeigt den Namen der Website an.
    
      - **Outlook Web App-Version**    (schreibgeschützt.) **Outlook Web App-Version** zeigt die ExchangeServerversion an.
    
      - **Geändert**   (schreibgeschützt) **Geändert** zeigt Datum und Uhrzeit der letzten Änderung des virtuellen Verzeichnisses an.
    
      - **Interne URL**   Geben Sie in diesem Textfeld die URL an, über die von einem internen Netzwerk aus auf diese Website zugegriffen werden kann. Eine interne URL wird bei der Einrichtung von Exchange 2013 automatisch konfiguriert. Die interne URL-Standardeinstellung für einen mit dem Internet verbundenen bzw. nicht mit dem Internet verbundenen Server lautet "https://\<Computer Name\>/owa".
    
      - **Externe URL**   Geben Sie in diesem Textfeld die URL an, über die vom Internet aus auf diese Website zugegriffen werden kann. Standardmäßig ist das Feld **Externe URL** leer. Für Clientzugriffsserver mit Internetverbindung sollte die **Externe URL** auf den im DNS für diesen Active Directory-Standort veröffentlichten Wert festgelegt werden. Bei Exchange 2013-Servern, die nicht über eine Internetverbindung verfügen, sollte die Einstellung **Externe URL** leer bleiben.

4.  Geben Sie auf der Registerkarte **Authentifizierung** die Authentifizierungsverfahren, das Anmeldeformat und die Anmeldedomäne an.
    
      - **Mindestens ein Standardauthentifizierungsverfahren verwenden**   Wählen Sie diese Option aus, wenn mindestens eines der folgenden Standardauthentifizierungsverfahren verwendet werden soll:
        
        **Integrierte Windows-Authentifizierung**   Dieses Verfahren erfordert für den Zugriff auf Informationen, dass Benutzer über einen gültigen Windows Server 2008- oder Windows Server 2012-Benutzerkontonamen und ein zugehöriges Kennwort verfügen. Benutzer werden nicht zur Eingabe von Kontonamen und Kennwörtern aufgefordert. sondern der Server kommuniziert mit den Windows-Sicherheitspaketen, die auf den Clientcomputern installiert sind. Die integrierte Windows-Authentifizierung ermöglicht dem Server die Authentifizierung von Benutzern, ohne sie zur Eingabe von Informationen aufzufordern und ohne unverschlüsselte Informationen über das Netzwerk zu übertragen. Damit dieses Verfahren funktioniert, muss der Clientcomputer zu derselben Domäne gehören wie die Server, auf denen Exchange ausgeführt wird, bzw. zu einer Domäne, die für die Domäne, in der sich der Server mit Exchange befindet, vertrauenswürdig ist.
        
        **Digestauthentifizierung für Windows-Domänenserver**   Bei diesem Verfahren werden für zusätzliche Sicherheit Kennwörter als Hashwert über das Netzwerk übermittelt. Die Digestauthentifizierung kann nur in Windows Server 2008- und Windows Server 2012-Domänen für Benutzer verwendet werden, die über ein Konto verfügen, das in Active Directory gespeichert ist. Weitere Informationen zur Digestauthentifizierung finden Sie in der Windows Server-Dokumentation.
        
        **Standardauthentifizierung (Kennwort wird unverschlüsselt gesendet)**   Dieses Verfahren ist ein einfacher, durch die HTTP-Spezifikation definierter Authentifizierungsmechanismus, bei dem der Anmeldename und das Kennwort eines Benutzers codiert werden, bevor die Anmeldeinformationen des Benutzers an den Server gesendet werden. Um sicherzustellen, dass das Kennwort möglichst sicher ist, müssen Sie zwischen den Clientcomputern und dem Server, auf dem die Clientzugriffs-Serverrolle installiert ist, die SSL-Verschlüsselung (Secure Sockets Layer) verwenden.
    
      - **Formularbasierte Authentifizierung verwenden**   Die formularbasierte Authentifizierung bietet höhere Sicherheit für virtuelle Outlook Web App-Verzeichnisse. Bei der formularbasierten Authentifizierung wird eine Anmeldeseite für Outlook Web App erstellt. Den Typ der Anmeldeaufforderung, der von der formularbasierten Authentifizierung verwendet wird, können Sie konfigurieren. Sie können die formularbasierte Authentifizierung beispielsweise so konfigurieren, dass Benutzer auf der Outlook Web App-Anmeldeseite ihre Domäne und den Benutzernamen im Format "Domäne\\Benutzer" angeben müssen.
        

        > [!IMPORTANT]
        > Ein sicherer Kanal wird bei der formularbasierten Authentifizierung nur bei Aktivierung von SSL verwendet.

        
        Wählen Sie eine der folgenden Optionen aus:
        
        **Domäne\\Benutzername**   Erfordert die Eingabe der Domäne und des Benutzernamens im Format "Domäne\\Benutzername". Die Anmeldung für den Benutzer "Kweku" in der Contoso-Domäne würde beispielsweise wie folgt lauten: contoso\\kweku.
        
        **Benutzerprinzipalname (User Principal Name, UPN)** Bei Angabe des UPN-Anmeldeformats (User Principal Name, Benutzerprinzipalname) werden die Benutzer auf der Outlook Web App-Anmeldeseite aufgefordert, im Feld **Benutzername** ihre E-Mail-Adresse einzugeben (Beispiel: kweku@contoso.com). Ist der Benutzerprinzipalname nicht mit der E-Mail-Adresse identisch, erhält der Benutzer bei Verwendung der **PrincipalName**-Anmeldeaufforderung keinen Zugriff auf Outlook Web App. Eine bewährte Methode ist, die **PrincipalName**-Anmeldeaufforderung nur zu verwenden, wenn der Benutzerprinzipalname der Benutzer mit ihrer E-Mail-Adresse übereinstimmt.
        
        **Nur Benutzername** Der Benutzer gibt nur seinen Benutzernamen ein, den Domänennamen jedoch nicht. Beispiel: Kweku. Bei Verwendung der Anmeldeaufforderung **Nur Benutzername** bei der formularbasierten Authentifizierung müssen Sie auch die Eigenschaft **Anmeldedomäne** angeben. Die Eigenschaft **Anmeldedomäne** legt die Standarddomäne fest, die verwendet wird, wenn ein Benutzer versucht, auf Outlook Web App zuzugreifen. Wenn beispielsweise die Standarddomäne "Contoso" ist und sich der Domänenbenutzer Kweku bei Outlook Web App anmeldet, muss nur "Kweku" als Benutzername eingegeben werden. Der Server verwendet dann die Standarddomäne "Contoso". Wenn der Benutzer kein Mitglied der Contoso-Domäne ist, müssen Domäne und Benutzername eingegeben werden.

5.  Auf der Registerkarte **Funktionen** können Sie die Funktionen angeben, die für Outlook Web App-Benutzer in einem virtuellen Verzeichnis aktiviert bzw. deaktiviert werden sollen.
    

    > [!NOTE]
    > Funktionseinstellungen für einzelne Benutzer setzen Einstellungen für das virtuelle Verzeichnis außer Kraft. Sie können die Segmentierungseinstellungen für einzelne Benutzer mithilfe des Cmdlets <STRONG>Set-CASMailbox</STRONG> oder über Outlook Web App-Postfachrichtlinien ändern. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/outlook-web-app-mailbox-policies">Outlook Web App-Postfachrichtlinien</A>.

    
    Verwenden Sie die Kontrollkästchen, um Funktionen zu aktivieren oder zu deaktivieren. Standardmäßig werden die gängigsten Funktionen angezeigt. Klicken Sie auf **Weitere Optionen**, um alle Funktionen anzuzeigen, die aktiviert oder deaktiviert werden können.
    

    > [!NOTE]
    > Die Möglichkeit zum Aktivieren oder Deaktivieren der Standardversion von Outlook Web App über das Kontrollkästchen <STRONG>Premium-Client</STRONG> ist veraltet und wird aus den Einstellungen entfernt. Die Standardversion von Outlook Web App ist immer aktiviert.



6.  Verwenden Sie die Kontrollkästchen auf der Registerkarte **Dateizugriff**, um die Dateizugriffs- und Anzeigeoptionen für Benutzer zu konfigurieren. Mit der Dateizugriffsoption kann ein Benutzer alle an eine E-Mail-Nachricht angehängten Dateien öffnen oder anzeigen.
    
    Der Dateizugriff kann basierend darauf gesteuert werden, ob sich ein Benutzer bei einem öffentlichen oder privaten Computer angemeldet hat. Die Option, mit der Benutzer zwischen Zugriff über einen öffentlichen oder privaten Computer auswählen können, stehen nur bei Verwendung der formularbasierten Authentifizierung zur Verfügung. Bei allen weiteren Formen der Authentifizierung wird von einem Zugriff auf einen privaten Computer ausgegangen.
    
      - **Direkter Dateizugriff**   Aktivieren Sie dieses Kontrollkästchen, um den direkten Dateizugriff zu aktivieren. Über den direkten Dateizugriff können Benutzer Dateien öffnen, die an eine E-Mail-Nachricht angehängt wurden.
    
      - **WebReady Document Viewing**   Aktivieren Sie dieses Kontrollkästchen, um die Konvertierung unterstützter Dokumente in HTML und deren Anzeige in einem Webbrowser zu aktivieren.
    
      - **Bei vorhandenem Konverter WebReady Document Viewing erzwingen**   Aktivieren Sie dieses Kontrollkästchen, wenn die Konvertierung von Dokumenten in HTML und ihre Anzeige in einem Webbrowser erzwungen werden soll, bevor Benutzer sie in der anzeigenden Anwendung öffnen können. Dokumente können in der anzeigenden Anwendung nur geöffnet werden, wenn der direkte Dateizugriff aktiviert wurde.

7.  Klicken Sie auf **Speichern**, um die Richtlinie zu aktualisieren.

## Anzeigen oder Konfigurieren der Eigenschaften des virtuellen Outlook Web App-Verzeichnisses mithilfe der Shell

In diesem Beispiel wird die formularbasierte Authentifizierung im virtuellen Outlook Web App-Standardverzeichnis auf dem Server "Contoso" aktiviert.

    set-OwaVirtualDirectory -Identity "Contoso\owa (default web site)" -FormsAuthentication $true

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/bb123515\(v=exchg.150\)).

## Anzeigen der Eigenschaften des virtuellen Outlook Web App-Verzeichnisses mithilfe der Shell

In diesem Beispiel können Sie die Eigenschaften aller virtuellen Outlook Web App-Verzeichnisse auf allen IIS-Websites (Internet Information Services) auf allen Computern anzeigen, auf denen die Clientzugriffs-Serverrolle in einer Exchange-Organisation installiert ist.

```powershell
Get-OWAVirtualDirectory
```

In diesem Beispiel können Sie die Eigenschaften für ein virtuelles Outlook Web App-Verzeichnis auf der IIS-Standardwebsite auf einem lokalen Exchange-Server anzeigen.

    Get-OWAVirtualDirectory -identity "<Exchange Server Name>\owa (default web site)"

In diesem Beispiel können Sie die Eigenschaften für alle virtuellen Outlook Web App-Verzeichnisse auf einer IIS-Website auf einem bestimmten Exchange-Server anzeigen.

```powershell
Get-OWAVirtualDirectory -server <Exchange Server Name>
```

In diesem Beispiel können Sie die Werte der Eigenschaften aller virtuellen Outlook Web App-Verzeichnisse auf allen IIS-Websites auf allen Clientzugriffsservern in einer Exchange-Organisation anzeigen.

```powershell
Get-OWAVirtualDirectory | format-list
```

Weitere Informationen zu Syntax und Parametern finden Sie unter [Get-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/aa998588\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

So überprüfen Sie, ob Sie ein virtuelles Outlook Web App-Verzeichnis erfolgreich bearbeitet haben:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Server** \> **Virtuelle Verzeichnisse**, und wählen Sie ein spezifische virtuelles Outlook Web App-Verzeichnis aus.

2.  Klicken Sie auf die Schaltfläche **Bearbeiten**, um die Eigenschaften des virtuellen Verzeichnisses anzuzeigen.

3.  Klicken Sie auf **Speichern** oder **Abbrechen**, um die Eigenschaftenseite zu schließen.


---
title: 'Erstellen einer Organisationsbeziehung: Exchange 2013 Help'
TOCTitle: Erstellen einer Organisationsbeziehung
ms:assetid: 5ea61b96-c8ca-44fc-b8b5-ca4341af36a6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657451(v=EXCHG.150)
ms:contentKeyID: 50475787
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Organisationsbeziehung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Richten Sie eine Organisationsbeziehung ein, um Kalenderinformationen für externe Geschäftspartner freizugeben. Sie können eine Organisationsbeziehung zwischen zwei Exchange 2013-Verbundorganisationen oder zwischen einer Exchange 2013-Verbundorganisation und Exchange 2010-Verbundorganisationen einrichten. Außerdem können Sie eine Organisationsbeziehung zwischen der lokalen Exchange-Organisation und einer Office 365-Organisation einrichten.


> [!IMPORTANT]
> Das Erstellen von Organisationsbeziehungen ist einer von mehreren Schritten beim Einrichten einer Verbundfreigabe in Ihrer Exchange-Organisation und erfordert die Konfiguration einer Verbundvertrauensstellung für Ihre lokale Exchange-Organisation.



Weitere Informationen zu Verbundfreigaben finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Kalenderberechtigungen und gemeinsame Berechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Es muss eine aktive Verbundvertrauensstellung für die lokale Exchange-Organisation konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren einer Verbundvertrauensstellung](configure-a-federation-trust-exchange-2013-help.md).

  - Für die externe Organisation, die Sie in der Organisationsbeziehung konfigurieren möchten, muss auch eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem erstellt worden sein. Sie verwenden die primäre Verbunddomäne für die externe Exchange-Organisation, wenn Sie die Organisationsbeziehung konfigurieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Erstellen einer Organisationsbeziehung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie auf einem Exchange 2013-Server in der lokalen Organisation zu **Organisation** \> **Freigabe**.

2.  Klicken Sie unter **Organisationsfreigabe** auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie in **Neue Organisationsbeziehung** in das Feld **Beziehungsname** einen Anzeigenamen für die Organisationsbeziehung ein.

4.  Geben Sie in das Feld **Domänen für Freigabe** die Verbunddomäne oder Verbundunterdomäne für die Office 365-Organisation oder die lokale Exchange-Organisation ein, welche die Kalender Ihrer Organisation sehen können soll. Wenn Sie mehrere Domänen für die externe Organisation eingeben müssen, trennen Sie die Domänen jeweils durch ein Komma voneinander. Beispiel: **contoso.com, service.contoso.com**.

5.  Aktivieren Sie das Kontrollkästchen **Freigabe von Frei/Gebucht-Kalenderinformationen aktivieren**, um die Freigabe von Kalenderinformationen für die aufgelisteten Domänen in Kraft zu setzen. Definieren Sie Freigabeebene für Frei/Gebucht-Kalenderinformationen, und legen Sie fest, welche Benutzer die Frei/Gebucht-Kalenderinformationen freigeben können.
    
    Wählen Sie eine der folgenden Optionen zur Festlegung der Frei/Gebucht-Zugriffsebene:
    
      - **Frei/Gebucht-Kalenderinformationen nur mit Zeit**
    
      - **Frei/Gebucht-Kalenderinformationen mit Zeit, Betreff und Ort**
    
    Um festzulegen, welche Benutzer die Frei/Gebucht-Kalenderinformationen freigeben können, wählen Sie eine der folgenden Optionen aus:
    
      - **Jeder in Ihrem Unternehmen**
    
      - **Eine bestimmte Sicherheitsgruppe**
        
        Um eine Sicherheitsgruppe anzugeben, klicken Sie auf **Durchsuchen**.

6.  Klicken Sie auf **Speichern**, um die Organisationsbeziehung zu erstellen.

## Erstellen einer Organisationsbeziehung mithilfe der Shell

In diesem Beispiel wird eine Organisationsbeziehung mit Contoso, Ltd. erstellt, die folgende Bedingungen erfüllt:

  - Die Organisationsbeziehung wird für "contoso.com", "northamerica.contoso.com" und "europe.contoso.com" aktiviert.

  - Frei/Gebucht-Zugriff ist aktiviert.

  - Die anfordernde Organisation empfängt Informationen zu Frei/Gebucht-Zeit, Betreff und Ort von der Zielorganisation.

<!-- end list -->

```powershell
    New-OrganizationRelationship -Name "Contoso" -DomainNames "contoso.com","northamerica.contoso.com","europe.contoso.com" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel LimitedDetails
```

In diesem Beispiel wird versucht, unter Verwendung der im Cmdlet **Get-FederationInformation** bereitgestellten Domänennamen automatisch Konfigurationsinformationen von der externen Exchange-Organisation "Contoso.com" zu ermitteln. Wenn Sie diese Methode zum Erstellen Ihrer Organisationsbeziehung einsetzen, müssen Sie zunächst sicherstellen, dass mit dem Cmdlet **Set-FederatedOrganizationIdentifier** eine Organisations-ID erstellt wurde.

```powershell
    Get-FederationInformation -DomainName Contoso.com | New-OrganizationRelationship -Name "Contoso" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel -LimitedDetails
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-FederationInformation](https://technet.microsoft.com/de-de/library/dd351221\(v=exchg.150\)) und [New-OrganizationRelationship](https://technet.microsoft.com/de-de/library/ee332357\(v=exchg.150\)).

In diesem Beispiel wird eine Organisationsbeziehung mit "Fourth Coffee" erstellt. In diesem Beispiel werden die Einstellungen für die Verbindung mit der externen Exchange-Organisation bereitgestellt. Dabei gelten folgenden Bedingungen:

  - Die Organisationsbeziehung wird eingerichtet mit der Domäne "fourthcoffee.com", einer Verbunddomäne von Fourth Coffee.

  - Die Anwendungs-URL für die Exchange-Webdienste lautet "mail.fourthcoffee.com".

  - Die AutoErmittlungs-URL ist "https://mail.fourthcoffee.com/autodiscover/autodiscover.svc/wssecurity".

  - Frei/Gebucht-Zugriff ist aktiviert.

  - Die anfordernde Organisation empfängt Frei/Gebucht-Informationen nur mit der Zeit.

<!-- end list -->

```powershell
    New-OrganizationRelationship -Name "Fourth Coffee" -DomainNames "fourthcoffee.com" -FreeBusyAccessEnabled $true -FreeBusyAccessLevel -AvailabilityOnly -TargetAutodiscoverEpr "https://mail.fourthcoffee.com/autodiscover/autodiscover.svc/wssecurity" -TargetApplicationUri "mail.fourthcoffee.com"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-OrganizationRelationship](https://technet.microsoft.com/de-de/library/ee332357\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Der erfolgreiche Abschluss des Assistenten für neue Organisationsbeziehungen ist ein erster Hinweis darauf, dass die Organisationsbeziehung erwartungsgemäß erstellt wurde.

Führen Sie den folgenden Shell-Befehl aus, um die Informationen zur Organisationsbeziehung zu überprüfen und die erfolgreiche Erstellung der Organisationsbeziehung sicherzustellen:

```powershell
Get-OrganizationRelationship | format-list
```


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



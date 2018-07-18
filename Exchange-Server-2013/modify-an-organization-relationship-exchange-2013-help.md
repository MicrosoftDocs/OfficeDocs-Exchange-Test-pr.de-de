---
title: 'Ändern einer Organisationsbeziehung: Exchange 2013 Help'
TOCTitle: Ändern einer Organisationsbeziehung
ms:assetid: 3713ef83-f01a-41bb-b127-62ca242dd7a4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673055(v=EXCHG.150)
ms:contentKeyID: 50475313
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern einer Organisationsbeziehung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-01-01_

Mithilfe der Organisationsbeziehung können Benutzer in der Exchange-Organisation Frei/Gebucht-Kalenderinformationen mit anderen Office 365- oder lokalen Exchange-Organisationen gemeinsam nutzen. Sie können verschiedene Eigenschaften einer Organisationsbeziehung ändern, beispielsweise den Namen, die temporäre Deaktivierung der Kalenderfreigabe, die Zugriffsebene oder welche Sicherheitsgruppen Kalender gemeinsam nutzen.

Bevor Sie Kalender für eine andere Organisation freigeben können, müssen Sie die Authentifizierungsbeziehung mit der Cloud (auch als "Verbund" bezeichnet) einrichten und die Mindestsoftwareanforderungen erfüllen. Weitere Informationen zu Verbundfreigaben finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf den Partnerverbund finden Sie unter [Verbundverfahren](federation-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "*Calendar and Sharing Permissions*" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Eine aktive Verbundvertrauensstellung für die lokale Exchange-Organisation muss konfiguriert werden.

  - Für die externe Organisation, die Sie in der Organisationsbeziehung konfigurieren möchten, muss auch eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem erstellt worden sein.

  - Die Verfahren in diesem Thema nehmen Änderungen an einer Organisationsbeziehung namens "Contoso" vor. Die Beispiele zeigen folgende Vorgehensweisen:
    
      - Hinzufügen einer Domäne namens "service.contoso.com" zur externen Organisation.
    
      - Deaktivieren der Freigabe von Frei/Gebucht-Informationen für die Organisationsbeziehung.
    
      - Ändern der Frei/Gebucht-Zugriffsebene von *Calendar free/busy information with time, subject, and location* in *Calendar free/busy information with time only*.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Hinzufügen einer Domäne zu einer Organisation mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie auf einem Exchange 2013-Server in Ihrer lokalen Organisation zu **Organisation** \> **Freigabe**.

2.  Wählen Sie in der Listenansicht unter **Organisationsfreigabe** die Organisationsbeziehung "Contoso" aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Ändern Sie unter **Organisationsbeziehung**, **Allgemein** nicht den **Namen** der Organisationsbeziehung.

4.  Geben Sie im Feld **Domänen für Freigabe** die Domäne **service.contoso.com** ein und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Klicken Sie auf **Speichern**, um die Organisationsbeziehung zu aktualisieren.

## Deaktivieren des Zugriffs auf Frei/Gebucht-Informationen für die Organisationsbeziehung mithilfe der Exchange-Verwaltungskonsole

1.  Wechseln Sie zu **Organisation**\> **Freigabe**.

2.  Wählen Sie in der Listenansicht unter **Organisationsfreigabe** die Organisationsbeziehung "Contoso" aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie unter **Organisationsbeziehung** auf **Freigabe**.

4.  Wählen Sie **Frei/Gebucht-Kalenderinformationen nur mit Zeit** aus.

5.  Klicken Sie auf **Speichern**, um die Organisationsbeziehung zu aktualisieren.

## Ändern der Zugriffsebene für Frei/Gebucht-Informationen für die Organisationsbeziehung mithilfe der Exchange-Verwaltungskonsole

1.  Wechseln Sie zu **Organisation**\> **Freigabe**.

2.  Wählen Sie in der Listenansicht unter **Organisationsfreigabe** die Organisationsbeziehung "Contoso" aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie unter **Organisationsbeziehung** auf **Freigabe**.

4.  Wählen Sie **Frei/Gebucht-Kalenderinformationen nur mit Zeit** aus.

5.  Klicken Sie auf **Speichern**, um die Organisationsbeziehung zu aktualisieren.

## Ändern der Organisationsbeziehung mithilfe der Shell

  - In diesem Beispiel wird der Organisationsbeziehung "Contoso" der Domänenname "service.contoso.com" hinzugefügt.
    
        $domains = (Get-OrganizationRelationship Contoso).DomainNames
        $domains += 'service.contoso.com'
        Set-OrganizationRelationship -Identity Contoso -DomainNames $domains

  - In diesem Beispiel wird die Organisationsbeziehung "Contoso" deaktiviert.
    
        Set-OrganizationRelationship -Identity Contoso -Enabled $false

  - In diesem Beispiel wird der Zugriff auf Verfügbarkeitsinformationen aus Kalendern für die Organisationsbeziehung "WoodgroveBank" ermöglicht, und die Zugriffsebene wird auf `AvailabilityOnly` (Frei/Gebucht-Kalenderinformationen nur mit Zeit) festgelegt.
    
        Set-OrganizationRelationship -Identity Contoso -FreeBusyAccessEnabled $true -FreeBusyAccessLevel AvailabilityOnly

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-OrganizationRelationship](https://technet.microsoft.com/de-de/library/ee332343\(v=exchg.150\)) und [Set-OrganizationRelationship](https://technet.microsoft.com/de-de/library/ee332326\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Shell-Befehl aus, und überprüfen Sie die Informationen zur Organisationsbeziehung, um die erfolgreiche Aktualisierung der Organisationsbeziehung sicherzustellen.

    Get-OrganizationRelationship | format-list


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



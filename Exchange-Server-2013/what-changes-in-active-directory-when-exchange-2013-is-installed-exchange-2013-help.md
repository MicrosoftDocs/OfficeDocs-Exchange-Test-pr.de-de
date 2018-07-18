---
title: 'Welche Änderungen werden in Active Directory vorgenommen, wenn Exchange 2013 installiert wird?: Exchange 2013 Help'
TOCTitle: Welche Änderungen werden in Active Directory vorgenommen, wenn Exchange 2013 installiert wird?
ms:assetid: 07386078-6103-49a2-8698-2d41db9cec95
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn750898(v=EXCHG.150)
ms:contentKeyID: 62371378
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Welche Änderungen werden in Active Directory vorgenommen, wenn Exchange 2013 installiert wird?

 

_**Gilt für:** Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-05-26_

Wenn Sie Exchange 2013 installieren, werden Änderungen an Ihrer Active Directory-Gesamtstruktur und den zugehörigen Domänen vorgenommen. Exchange führt diese Änderungen durch, damit Informationen über die Exchange-Server, -Postfächer und weitere Objekte im Zusammenhang mit Exchange in Ihrer Organisation gespeichert werden können. Diese Änderungen werden für Sie vorgenommen, wenn Sie den Setup-Assistenten für Exchange 2013 ausführen oder wenn Sie die Befehle *PrepareSchema*, *PrepareAD* und *PrepareDomains* (Informationen zur Verwendung dieser Befehle finden Sie unter [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md)) während der Ausführung der Befehlszeilenversion des Exchange 2013-Setups ausführen. Wenn Sie sich für die Änderungen interessieren, die Exchange an Active Directory durchführt, ist dies das richtige Thema für Sie. Hierin wird erläutert, wie Exchange bei jedem Schritt der Active Directory-Vorbereitung verfährt.

Für die Vorbereitung von Active Directory für Exchange müssen drei Schritte durchgeführt werden:

  - Erweitern des Active Directory-Schemas

  - Vorbereiten von Active Directory-Containern, -Objekten und anderen Elementen

  - Vorbereiten der Active Directory-Domänen

Nachdem die drei Schritte durchgeführt wurden, ist Ihre Active Directory-Gesamtstruktur bereit für Exchange 2013. Weitere Informationen zum Installieren von Exchange 2013 finden Sie unter [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md).

## Erweitern des Active Directory-Schemas

Beim Erweitern des Active Directory-Schemas werden Klassen, Attribute und andere Elemente hinzugefügt und aktualisiert. Diese Änderungen sind notwendig, damit Exchange Container und Objekte erstellen kann, um Informationen über die Exchange-Organisation zu speichern. Da Exchange eine Vielzahl von Änderungen am Active Directory-Schema vornimmt, ist diesem Schritt ein eigenes Thema gewidmet. Informationen zu allen am Schema vorgenommenen Änderungen finden Sie unter [Änderungen des Active Directory-Schemas in Exchange 2013](exchange-2013-active-directory-schema-changes-exchange-2013-help.md).

Dieser Schritt wird automatisch durchgeführt, wenn Sie den Setup-Assistenten für Exchange 2013 auf dem ersten Exchange 2013-Server in der Active Directory-Gesamtstruktur ausführen. Er wird ebenfalls durchgeführt, wenn Sie die Befehlszeilenversion des Exchange 2013-Setups mit dem Befehl *PrepareSchema* (oder optional mit dem Befehl *PrepareAD*) auf dem ersten Exchange 2013-Server in der Gesamtstruktur ausführen. Weitere Informationen zum Erweitern des Schemas finden Sie unter [Extend the Active Directory schema](prepare-active-directory-and-domains-exchange-2013-help.md) im Thema [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md).

Nachdem Exchange die Schemaerweiterung abgeschlossen hat, wird die Schemaversion festgelegt, die im Attribut **ms-Exch-Schema-Version-Pt** gespeichert wird. Durch Überprüfung des in diesem Attribut gespeicherten Werts können Sie sich vergewissern, ob das Active Directory-Schema erfolgreich erweitert wurde. Wenn der Wert in dem Attribut der Schemaversion entspricht, die für die installierte Version von Exchange 2013 aufgeführt ist, war die Erweiterung des Schemas erfolgreich. Eine Liste der Exchange-Versionen und Informationen dazu, wie Sie den Wert dieses Attributs überprüfen, finden Sie im Abschnitt [How do you know this worked?](prepare-active-directory-and-domains-exchange-2013-help.md) unter [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md).

## Vorbereiten von Active Directory-Containern, -Objekten und anderen Elementen

Nachdem das Schema erweitert wurde, besteht der nächste Schritt darin, alle Container, Objekte, Attribute und sonstigen Elemente, die Exchange zum Speichern von Informationen in Active Directory verwendet, hinzuzufügen. Die meisten in diesem Schritt durchgeführten Änderungen werden auf die ganze Active Directory-Gesamtstruktur angewendet. Eine geringere Anzahl Änderungen wird an der lokalen Active Directory-Domäne vorgenommen, wenn der Befehl *PrepareAD* während des Setup ausgeführt wurde.

Die folgenden Änderungen werden an der Active Directory-Gesamtstruktur vorgenommen:

  - Der Microsoft Exchange-Container wird unter "CN=Services,CN=Configuration,DC=\<*root domain*\>" erstellt, sofern er noch nicht vorhanden ist.

  - Die folgenden Container und Objekte werden unter "CN=\<*organization name*\>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<*root domain*\>" erstellt, sofern sie noch nicht vorhanden sind:
    
      - CN=Address Lists Container
    
      - CN=AddressBook Mailbox Policies
    
      - CN=Addressing
    
      - CN=Administrative Groups
    
      - CN=Approval Applications
    
      - CN=Auth Configuration
    
      - CN=Availability Configuration
    
      - CN=Client Access
    
      - CN=Connections
    
      - CN=ELC Folders Container
    
      - CN=ELC Mailbox Policies
    
      - CN=ExchangeAssistance
    
      - CN=Federation
    
      - CN=Federation Trusts
    
      - CN=Global Settings
    
      - CN=Hybrid Configuration
    
      - CN=Mobile Mailbox Policies
    
      - CN=Mobile Mailbox Settings
    
      - CN=Monitoring Settings
    
      - CN=OWA Mailbox Policies
    
      - CN=Provisioning Policy Container
    
      - CN=Push Notification Settings
    
      - CN=RBAC
    
      - CN=Recipient Policies
    
      - CN=Remote Accounts Policies Container
    
      - CN=Retention Policies Container
    
      - CN=Retention Policy Tag Container
    
      - CN=ServiceEndpoints
    
      - CN=System Policies
    
      - CN=Team Mailbox Provisioning Policies
    
      - CN=Transport Settings
    
      - CN=UM AutoAttendant Container
    
      - CN=UM DialPlan Container
    
      - CN=UM IPGateway Container
    
      - CN=UM Mailbox Policies
    
      - CN=Workload Management Settings

  - Die folgenden Container und Objekte werden unter "CN=Transport Settings,CN=\<*Organization Name*\>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<*root domain*\> erstellt, sofern sie noch nicht vorhanden sind.
    
      - CN=Accepted Domains
    
      - CN=ControlPoint Config
    
      - CN=DNS Customization
    
      - CN=Interceptor Rules
    
      - CN=Malware Filter
    
      - CN=Message Classifications
    
      - CN=Message Hygiene
    
      - CN=Rules
    
      - CN=MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e

  - Berechtigungen werden in der gesamten Konfigurationspartition in Active Directory festgelegt.

  - Die Datei "Rights.ldf" wird importiert. Diese Datei fügt Berechtigungen hinzu, die zum Installieren von Exchange und Konfigurieren von Active Directory verwendet werden.

  - Die Organisationseinheit für MicrosoftExchange-Sicherheitsgruppen wird in der Stammdomäne der Gesamtstruktur erstellt, und Berechtigungen werden zugewiesen.

  - Die folgenden Verwaltungsrollengruppen werden in der Organisationseinheit für Microsoft Exchange-Sicherheitsgruppen erstellt, sofern sie noch nicht vorhanden sind:
    
      - Verwaltung der Richtlinientreue
    
      - Delegiertes Setup
    
      - Discoveryverwaltung
    
      - Helpdesk
    
      - Nachrichtenschutz
    
      - Organisationsverwaltung
    
      - Verwaltung Öffentlicher Ordner
    
      - Empfängerverwaltung
    
      - Datensatzverwaltung
    
      - Serververwaltung
    
      - UM-Verwaltung
    
      - Organisationsverwaltung mit Leserechten

  - Die neuen Verwaltungsrollengruppen (werden in Active Directory als universelle Sicherheitsgruppen angezeigt), die in der Organisationseinheit für MicrosoftExchange-Sicherheitsgruppen erstellt wurden, werden dem Attribut **otherWellKnownObjects** hinzugefügt, das im Container "CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<*root domain*\>" gespeichert ist.

  - Der Kontakt "Unified Messaging-Sprachnachrichtenabsender" wird im Container "Microsoft Exchange-Systemobjekte" der Stammdomäne erstellt.

  - Die Domäne, in der der Befehl *PrepareAD* ausgeführt wurde, wird für Exchange 2013 vorbereitet. Informationen zu den Schritten, die zum Vorbereiten der Active Directory-Domäne für Exchange durchgeführt werden, finden Sie unter Vorbereiten der Active Directory-Domänen.

  - Die Eigenschaft **msExchProductId** für das Exchange-Organisationsobjekt wird festgelegt. Durch Überprüfung des in dieser Eigenschaft gespeicherten Werts können Sie sich vergewissern, ob das Active Directory-Schema erfolgreich erweitert wurde. Wenn der Wert in der Eigenschaft der Schemaversion entspricht, die für die installierte Version von Exchange 2013 aufgeführt ist, war die Erweiterung des Schemas erfolgreich. Eine Liste der Exchange-Versionen und Informationen dazu, wie Sie den Wert dieser Eigenschaft überprüfen, finden Sie im Abschnitt [How do you know this worked?](prepare-active-directory-and-domains-exchange-2013-help.md) unter [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md).

## Vorbereiten der Active Directory-Domänen

Beim letzten Schritt der Vorbereitung von Active Directory für Exchange werden alle Active Directory-Domänen vorbereitet, in denen Exchange-Server installiert werden oder in denen sich postfachaktivierter Benutzer befinden. Dieser Schritt wird automatisch in der Domäne durchgeführt, in der der Befehl *PrepareAD* ausgeführt wurde.

Die folgenden Änderungen werden an den Active Directory-Domänen vorgenommen:

  - Der Container "Microsoft Exchange-Systemobjekte" wird in der Stammdomänenpartition in Active Directory erstellt, sofern er noch nicht vorhanden ist.

  - Berechtigungen für den Container "Microsoft Exchange-Systemobjekte" werden für die Sicherheitsgruppen "Exchange-Server", "Organisationsverwaltung" und "Authentifizierte Benutzer" festgelegt.

  - Die globale Domänengruppe "Exchange Install Domain Servers" wird in der aktuellen Domäne erstellt und in den Container "Microsoft Exchange-Systemobjekte" eingefügt.

  - Die Gruppe "Exchange Install Domain Servers" wird der universellen Sicherheitsgruppe "Exchange-Server" in der Stammdomäne hinzugefügt.

  - Berechtigungen werden auf Domänenebene für die universellen Sicherheitsgruppen "Exchange-Server" und "Organisationsverwaltung" zugewiesen.

  - Die Eigenschaft **objectVersion** im Container "Microsoft Exchange-Systemobjekte" unter "DC=\<*root domain*\>" wird festgelegt. Durch Überprüfung des in dieser Eigenschaft gespeicherten Werts können Sie sich vergewissern, ob das Active Directory-Schema erfolgreich erweitert wurde. Wenn der Wert in der Eigenschaft der Schemaversion entspricht, die für die installierte Version von Exchange 2013 aufgeführt ist, war die Erweiterung des Schemas erfolgreich. Eine Liste der Exchange-Versionen und Informationen dazu, wie Sie den Wert dieser Eigenschaft überprüfen, finden Sie im Abschnitt [How do you know this worked?](prepare-active-directory-and-domains-exchange-2013-help.md) unter [Vorbereitung von Active Directory und Domänen](prepare-active-directory-and-domains-exchange-2013-help.md).


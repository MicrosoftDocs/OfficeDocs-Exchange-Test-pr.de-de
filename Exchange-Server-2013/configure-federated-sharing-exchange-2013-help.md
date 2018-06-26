---
title: 'Konfigurieren der Verbundfreigabe: Exchange 2013 Help'
TOCTitle: Konfigurieren der Verbundfreigabe
ms:assetid: b25ae450-def3-4797-a5fc-6e9bcee71a5d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657483(v=EXCHG.150)
ms:contentKeyID: 50476467
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Verbundfreigabe

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Mit der Verbundfreigabe in Exchange Server 2013 können Benutzer Informationen für Empfänger in externen Verbundorganisationen freigeben. Dazu gehört das Freigeben ihrer Frei/Gebucht-Informationen (die sogenannte "Kalenderverfügbarkeit") für die Terminplanung oder, je nach Art der Geschäftsbeziehung, das Freigeben von ausführlicheren Kalenderinformationen. Weitere Informationen zur Verbundfreigabe finden Sie unter [Freigabe](sharing-exchange-2013-help.md).


> [!IMPORTANT]
> Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 1 Stunde.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen und Konfigurieren einer Verbundvertrauensstellung

Eine Verbundvertrauensstellung richtet eine Vertrauensstellung zwischen einer Exchange 2013-Organisation und dem Azure Active Directory-Authentifizierungssystem ein und ist für Verbundfreigaben erforderlich.

Ausführliche Anweisungen finden Sie unter [Konfigurieren einer Verbundvertrauensstellung](configure-a-federation-trust-exchange-2013-help.md).

## Schritt 2: Erstellen einer Organisationsbeziehung

Mithilfe einer Organisationsbeziehung können Benutzer in Ihrer Exchange-Organisation Frei/Gebucht-Kalenderinformationen im Rahmen der Verbundfreigabe für andere Exchange-Verbundorganisationen freigeben. Die Verbundfreigabe kann zwischen zwei Exchange 2013-Verbundorganisationen oder zwischen einer Exchange 2013-Verbundorganisation und Exchange 2010-Verbundorganisationen konfiguriert werden.

Ausführliche Anweisungen finden Sie unter [Erstellen einer Organisationsbeziehung](create-an-organization-relationship-exchange-2013-help.md).

## Schritt 3: Erstellen einer Freigaberichtlinie

Freigaberichtlinien ermöglichen die durch den Benutzer eingerichtete personenbezogene Freigabe von Kalenderinformationen für verschiedene Typen von externen Benutzern. Sie unterstützen die Freigabe von Kalender- und Kontaktinformationen für externe Verbundorganisationen, externe Nicht-Verbundorganisationen und einzelne Benutzer mit Internetzugang. Wenn Sie keine Freigaben zwischen Personen oder Kontakten (Freigabe nur auf Organisationsebene) konfigurieren müssen, müssen Sie keine Freigaberichtlinie konfigurieren.

Ausführliche Anweisungen finden Sie unter [Erstellen einer Freigaberichtlinie](create-a-sharing-policy-exchange-2013-help.md).

## Schritt 4: Konfigurieren eines öffentlichen DNS-Eintrags für die AutoErmittlung

Sie müssen einen Alias-CNAME-Ressourceneintrag (kanonischer Name) zum DNS mit öffentlichem Zugriff hinzufügen. Der neue CNAME-Eintrag sollte auf einen mit dem Internet verbundenen Exchange 2013-Clientzugriffsserver verweisen, auf dem der AutoErmittlungsdienst ausgeführt wird.

Ausführliche Anweisungen zum Hinzufügen von CNAME-Einträgen erhalten Sie von dem Anbieter, der Ihre öffentlichen DNS-Einträge hostet. Häufig ist dies der Internetdienstanbieter, der auch Ihre Domänenwebsite hostet.


---
title: 'Hinzufügen einer autom. Telefonzentralen-Durchwahlnummer: Exchange 2013-Hilfe'
TOCTitle: Fügen Sie eine automatische Telefonzentrale Durchwahlnummer ein hinzu
ms:assetid: f2bd62ba-1e01-4cb7-862c-c750752e20e0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232200(v=EXCHG.150)
ms:contentKeyID: 50477053
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Fügen Sie eine automatische Telefonzentrale Durchwahlnummer ein hinzu

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Sie können in einer automatischen UM-Telefonzentrale (Unified Messaging) eine oder mehrere Durchwahlnummern konfigurieren. Wenn Sie einer automatischen UM-Telefonzentrale eine Durchwahlnummer hinzufügen, kann diese Nummer von Anrufern zum Anrufen der automatischen Telefonzentrale verwendet werden. Außerdem müssen Sie mitunter Durchwahlnummern hinzufügen, weil Anrufer mehr als eine Durchwahlnummer für den Zugriff auf eine automatische Telefonzentrale verwenden können. Standardmäßig werden bei der Erstellung einer automatischen Telefonzentrale keine Durchwahlnummern konfiguriert.

Sie können eine neue automatische Telefonzentrale erstellen, ohne dass Sie hierfür eine Durchwahlnummer einrichten. Sie können einer einzigen automatischen Telefonzentrale auch mehrere Telefon- oder Durchwahlnummern zuordnen. Sie können die Durchwahlnummern entweder beim Erstellen der automatischen UM-Telefonzentrale oder nach der Konfiguration der automatischen Telefonzentrale hinzufügen. Die Anzahl der Ziffern der Durchwahlnummer, die Sie für die automatische UM-Telefonzentrale konfigurieren, muss der Anzahl der Ziffern einer Durchwahlnummer entsprechen, die in dem der automatischen UM-Telefonzentrale zugeordneten UM-Wählplan konfiguriert ist.


> [!NOTE]
> Sie können auch eine SIP-Adresse (Session Initiation Protocol) anstelle einer Durchwahlnummer hinzufügen. Eine SIP-Adresse wird von einigen IP-Nebenstellenanlagen und von Office Communications Server 2007 R2 oder Microsoft Lync Server verwendet.



Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/um-auto-attendant-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Hinzufügen von Durchwahl- oder Telefonnummern für eine automatische UM-Telefonzentrale mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie bearbeiten möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, zu der Sie Durchwahl- oder Telefonnummern hinzufügen möchten.

3.  Klicken Sie auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Geben Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Allgemein** unter **Zugriffsnummern** die zu verwendenden Durchwahl- oder Telefonnummern ein, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Klicken Sie auf **Speichern**, um die Nummer hinzuzufügen.

## Konfigurieren einer Durchwahlnummer für eine automatische UM-Telefonzentrale mithilfe der Shell

In diesem Beispiel wird eine automatische UM-Telefonzentrale namens `MyUMAutoAttendant` mit mehreren Durchwahlnummern konfiguriert.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -PilotIdentifierList "12345, 72000, 75000"


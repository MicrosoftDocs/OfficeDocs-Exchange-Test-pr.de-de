---
title: 'Zulassen von MWI für UM-IP-Gateway: Exchange 2013-Hilfe'
TOCTitle: MWI (Message Waiting Indicator) für ein UM-IP-Gateway unterstützen
ms:assetid: 5667e37c-48c6-4659-9dc9-94b1dd8ba232
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd297995(v=EXCHG.150)
ms:contentKeyID: 50475686
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# MWI (Message Waiting Indicator) für ein UM-IP-Gateway unterstützen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-23_

Sie können Voicemailbenachrichtigungen an Benutzer für Anrufe zulassen oder verhindern, die von einem UM-IP-Gateway (Unified Messaging) empfangen werden. Wenn Sie diese Einstellung aktivieren, kann das UM-IP-Gateway SIP-NOTIFY-Nachrichten für Benutzer empfangen und senden. Der MWI (Message Waiting Indicator) ist standardmäßig aktiviert und ermöglicht es, dass Benachrichtigungen über wartende Nachrichten an Benutzer gesendet werden. Diese Einstellung kann jedoch gemäß Ihren Anforderungen deaktiviert werden.

Ein MWI (Message Waiting Indicator) benachrichtigt Benutzer über eine neue oder nicht abgehörte Sprachnachricht. Sie wird im Posteingang von Clients wie z. B. Outlook und Outlook Web App angezeigt. Es kann sich dabei auch um Folgendes handeln: Eine SMS, die an ein registriertes Mobiltelefon gesendet wird, ein ausgehender Anruf von einem Exchange-Server an eine Nummer, die für die Wiedergabe neuer Nachrichten konfiguriert ist, oder ein leuchtendes Lämpchen am Telefon auf dem Schreibtisch des Benutzers.


> [!TIP]
> MWI-Benachrichtigungen können auch für eine UM-Postfachrichtlinie für eine Gruppe von Benutzern aktiviert oder deaktiviert werden.



Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](https://technet.microsoft.com/de-de/library/JJ822153(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Weitere Informationen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt wurde. Weitere Informationen finden Sie unter [Erstellen eines UM-IP-Gateways](https://technet.microsoft.com/de-de/library/Aa998045(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Zulassen des Message Waiting Indicator (MWI) mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, wählen Sie das UM-IP-Gateway aus, das Sie ändern möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-IP-Gateway** das Kontrollkästchen neben **WMI (Waiting Message Indicator) zulassen**.

3.  Klicken Sie auf **Speichern**.

## Zulassen des Message Waiting Indicator (MWI) mithilfe der Shell

In diesem Beispiel wird die WMI-Anzeige für Benutzer zugelassen, die dem UM-IP-Gateway `MyUMIPGateway` mit der IP-Adresse 10.10.10.1 zugeordnet sind.

    Set-UMIPGateway -Identity MyUMIPGateway -Address 10.10.10.1 -MessageWaitingIndicatorAllowed $true


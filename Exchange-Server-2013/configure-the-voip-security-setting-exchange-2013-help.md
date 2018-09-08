---
title: 'Konfigurieren der VoIP-Sicherheitseinstellung: Exchange Online Help'
TOCTitle: Konfigurieren der VoIP-Sicherheitseinstellung
ms:assetid: b5335654-c766-4f3f-883c-f31263e1d9c1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201721(v=EXCHG.150)
ms:contentKeyID: 50476499
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren der VoIP-Sicherheitseinstellung

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2014-10-16_

Sie können VoIP-Sicherheit (Voice over IP) für einen UM-Wählplan (Unified Messaging) aktivieren. Beim Erstellen von UM-Wählplänen verwenden diese standardmäßig den ungesicherten Modus und keine Verschlüsselung. Exchange-Server können Anrufe für einzelne oder mehrere UM-Wählpläne sowie für Wählpläne annehmen, die andere VoIP-Sicherheitseinstellungen haben. In Office 365 und Exchange Online ist der abgesicherte Modus erforderlich und kann nicht deaktiviert werden.

Wenn Sie einen UM-Wählplan so konfigurieren, dass der SIP-gesicherte (Session Initiation Protocol) oder der sichere Modus verwendet wird, verschlüsseln die Exchange-Server, die Anrufe für den UM-Wählplan annehmen, den SIP-Signalverkehr (für den SIP-gesicherten Modus) oder sowohl die RTP-Medienkanäle (Realtime Transport Protocol) als auch den SIP-Signalverkehr (für den sicheren Modus).


> [!IMPORTANT]
> Wenn Sie bei lokalen und Hybridbereitstellungen den SipTCPListeningPort, SipTLSListeningPort oder UMStartUpMode auf einem Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Anrufrouterdienst ausgeführt wird, oder einem Postfachserver konfigurieren, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, müssen Sie die Regeln der Windows-Firewall so konfigurieren, dass SIP- und RTP-Netzwerkdatenverkehr ordnungsgemäß zugelassen wird.



Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wählpläne" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von VoIP-Sicherheit für einen UM-Wählplan mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, wählen Sie den UM-Wählplan aus, für den Sie die VoIP-Sicherheit ändern möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

3.  Wählen Sie in **Allgemein** unter **VoIP-Sicherheitsmodus** eine der folgenden Optionen aus:
    
      - **SIP-gesichert**
    
      - **Ungesichert** (Standard)
    
      - **Gesichert**

4.  Klicken Sie auf **Speichern**.

## Konfigurieren von VoIP-Sicherheit für einen UM-Wählplan mithilfe der Shell

In diesem Beispiel wird ein UM-Wählplan namens `MySecureDialPlan` für das Verschlüsseln von SIP- und RTP-Datenverkehr konfiguriert.

    Set-UMDialPlan -identity MySecureDialPlan -VoIPSecurity Secured

In diesem Beispiel wird ein UM-Wählplan namens `MySecureDialPlan` für das Verschlüsseln von SIP-, nicht jedoch von RTP-Datenverkehr konfiguriert.

    Set-UMDialPlan -identity MySecureDialPlan -VoIPSecurity SIPsecured

In diesem Beispiel wird ein UM-Wählplan namens `MySecureDialPlan` für den nicht gesicherten SIP- und RTP-Datenverkehr konfiguriert.

    Set-UMDialPlan -identity MySecureDialPlan -VoIPSecurity Unsecured


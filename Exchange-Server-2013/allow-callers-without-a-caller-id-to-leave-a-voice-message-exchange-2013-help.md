---
title: 'Zulassen einer Sprachnachricht bei Anrufern ohne Anrufer-ID: Exchange 2013 Help'
TOCTitle: Zulassen einer Sprachnachricht bei Anrufern ohne Anrufer-ID
ms:assetid: 51367d98-e17c-4bcf-8b14-208bd1ac3af0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232040(v=EXCHG.150)
ms:contentKeyID: 50475640
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zulassen einer Sprachnachricht bei Anrufern ohne Anrufer-ID

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können es zulassen oder unterbinden, dass UM-aktivierte Benutzer Voicemailnachrichten von anonymen Anrufern empfangen. Wenn Benutzer für Unified Messaging (UM) und Voicemail aktiviert sind, können sie standardmäßig Anrufe empfangen, die anonym sind und keine Anrufer-ID-Informationen enthalten.

In den meisten Fällen enthalten Anrufe, die von Unified Messaging empfangen werden, eine Anrufer-ID, anhand der die Quelle des eingehenden Anrufs bestimmt werden kann. Aus folgenden Gründen ist es jedoch möglich, dass eingehende Anrufe keine Anrufer-ID-Informationen enthalten:

  - Die Telefonieausrüstung Ihrer Organisation ist so konfiguriert, dass Anrufer-ID-Informationen nicht eingeschlossen werden.

  - Der eingehende Anruf stammt von einem mobilen oder externen Telefon.

  - Der Anrufer hat die Anrufer-ID auf seinem Telefon deaktiviert.

Da der Parameter *AnonymousCallersCanLeaveMessages* standardmäßig aktiviert ist, kann ein UM-aktivierter Benutzer eine Sprachnachricht empfangen, auch wenn die Anrufer-ID-Informationen nicht enthalten sind. Wenn die Option *AnonymousCallersCanLeaveMessages* deaktiviert ist und der UM-aktivierte Benutzer einen Anruf erhält, der keine Anrufer-ID einschließt, wird der Anruf als anonym erkannt, und der UM-aktivierte Benutzer erhält keine Sprachnachricht.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass das Postfach des Benutzers UM-aktiviert wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Zulassen des Empfangs von Sprachnachrichten von anonymen Anrufern mithilfe der Shell

In diesem Beispiel wird es dem UM-aktivierten Benutzer "tonysmith@contoso.com" ermöglicht, Sprachnachrichten von eingehenden Anrufen zu empfangen, die keine Anrufer-ID-Informationen einschließen.

    Set-UMMailbox -Identity tonysmith@contoso.com -AnonymousCallersCanLeaveMessages $true


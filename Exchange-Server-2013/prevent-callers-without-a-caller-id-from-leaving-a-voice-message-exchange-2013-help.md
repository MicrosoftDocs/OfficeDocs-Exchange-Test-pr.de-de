---
title: 'Verhindern, dass Anrufer ohne Anrufer-ID Sprachnachricht hinterlassen'
TOCTitle: Verhindern Sie, dass Anrufer ohne eine Anrufer-ID eine Sprachnachricht hinterlassen
ms:assetid: dd5dad32-2f69-4bf4-8ff0-545c413d395a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673571(v=EXCHG.150)
ms:contentKeyID: 50476884
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verhindern Sie, dass Anrufer ohne eine Anrufer-ID eine Sprachnachricht hinterlassen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können es zulassen oder unterbinden, dass UM-aktivierte Benutzer Sprachnachrichten von anonymen Anrufern empfangen. Wenn Benutzer für Unified Messaging (UM) und Voicemail aktiviert sind, können sie standardmäßig Anrufe empfangen, die anonym sind und keine Anrufer-ID-Informationen enthalten.

In den meisten Fällen enthalten Anrufe, die von Exchange-Servern empfangen werden, eine Anrufer-ID, anhand der die Quelle des eingehenden Anrufs bestimmt werden kann. Aus folgenden Gründen ist es jedoch möglich, dass eingehende Anrufe keine Anrufer-ID-Informationen enthalten:

  - Die Telefonieausrüstung Ihrer Organisation ist so konfiguriert, dass Anrufer-ID-Informationen nicht eingeschlossen werden.

  - Der eingehende Anruf stammt von einem mobilen oder externen Telefon.

  - Der Anrufer hat die Anrufer-ID auf seinem Telefon deaktiviert.

Da der Parameter *AnonymousCallersCanLeaveMessages* standardmäßig aktiviert ist, kann ein UM-aktivierter Benutzer eine Sprachnachricht empfangen, auch wenn die Anrufer-ID-Informationen nicht enthalten sind. Wenn die Option *AnonymousCallersCanLeaveMessages* deaktiviert ist und der UM-aktivierte Benutzer einen Anruf erhält, der keine Anrufer-ID einschließt, wird der Anruf als anonym erkannt, und der UM-aktivierte Benutzer erhält keine Sprachnachricht.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://technet.microsoft.com/de-de/library/JJ835776(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass das Postfach des Benutzers UM-aktiviert wurde. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Unterbinden des Empfangs von Sprachnachrichten von anonymen Anrufern mithilfe der Shell

In diesem Beispiel wird unterbunden, dass der UM-aktivierte Benutzer "tonysmith@contoso.com" Sprachnachrichten von Anrufen empfängt, die keine Anrufer-ID-Informationen einschließen.

    Set-UMMailbox -Identity tonysmith@contoso.com -AnonymousCallersCanLeaveMessages $false


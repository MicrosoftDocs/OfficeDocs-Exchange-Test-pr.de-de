---
title: 'Verhindert, dass Benutzer empfangen von Faxnachrichten: Exchange Online Help'
TOCTitle: Verhindert, dass Benutzer empfangen von Faxnachrichten
ms:assetid: b5d022b9-043a-4324-87fb-074d5e2c2ca3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201722(v=EXCHG.150)
ms:contentKeyID: 52062809
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verhindert, dass Benutzer empfangen von Faxnachrichten

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Verhindern Sie, dass einen Benutzer für Unified Messaging (UM) empfangen von Faxnachrichten. Erfahren Sie, wie Sie für neue und vorhandene UM-Benutzer Fax modifizieren.

In der Standardeinstellung Wenn Sie einen Benutzer für Unified Messaging aktivieren werden sie Faxe empfangen, wenn Sie Faxen aktivieren und konfigurieren einen faxpartner URI auf die um-Postfachrichtlinie, die dem Benutzer verknüpft ist. Faxen kann aktiviert oder deaktiviert auf UM einwählen, Pläne, UM-Postfachrichtlinien oder das UM-aktivierten Postfach des Benutzers.

Standardmäßig lassen das Postfach des Benutzers und der Wählplan, der dem Benutzer zugeordnet ist, den Faxeingang zu. Damit ein Benutzer jedoch Faxnachrichten empfangen kann, müssen Sie zunächst den Faxeingang in der mit dem UM-aktivierten Benutzer verknüpften UM-Postfachrichtlinie aktivieren und den URI des Faxpartners eingeben.


> [!NOTE]
> Der Exchange-Verwaltungskonsole können Sie für einen Unified Messaging-Postfachrichtlinie Fax Einstellungen konfigurieren. Allerdings müssen Sie die Shell verwenden, Fax-Einstellungen für Wählpläne oder für einzelne Benutzer konfiguriert.



Weitere Informationen zu Fax Partner finden Sie unter [Microsoft Hindernissen bei für Fax Partner](https://go.microsoft.com/fwlink/?linkid=190238).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Faxnachrichten finden Sie unter [Faxfunktion – Verfahren](faxing-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass der Benutzer für Unified Messaging aktiviert ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum verhindern, dass eines UM-aktivierten Benutzers empfangen von Faxnachrichten

In diesem Beispiel wird verhindert, dass der UM-aktivierte Benutzer Tony über sein Postfach Faxnachrichten empfangen kann.

    Set-UMMailbox -Identity tony@contoso.com -FaxEnabled $false


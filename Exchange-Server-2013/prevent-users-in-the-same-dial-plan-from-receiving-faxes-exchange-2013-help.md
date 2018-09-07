---
title: 'Verh. d. Empf. v. Faxnach. f. Benutzer im gl. Wählplan: Exchange 2013-Hilfe'
TOCTitle: Verhindern, dass Benutzer in den gleichen Wähleinstellungen empfangen von Faxnachrichten
ms:assetid: 4fc66414-c950-4bca-ac20-4e489f288d06
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201688(v=EXCHG.150)
ms:contentKeyID: 52062705
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verhindern, dass Benutzer in den gleichen Wähleinstellungen empfangen von Faxnachrichten

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können verhindern, dass UM-aktivierte Benutzer, die mit einem Unified Messaging-Wählplan (UM) verknüpft sind, Faxnachrichten empfangen. Standardmäßig können Benutzer, die für Unified Messaging aktiviert und mit einem UM-Wählplan verknüpft sind, Faxnachrichten empfangen. Unter gewissen Umständen kann es jedoch notwendig sein, den Empfang von Faxnachrichten für Benutzer, die bestimmten UM-Wähleinstellungen zugeordneten sind, zu unterbinden.

Sie können den Faxempfang für UM-aktivierte Benutzer unterbinden, indem Sie den UM-Wählplan, die UM-Postfachrichtlinie oder das Postfach des UM-aktivierten Benutzers konfigurieren. Wenn Sie die Zustellung eingehender Faxnachrichten in UM-Wähleinstellungen deaktivieren, wird der Empfang von Faxnachrichten für alle Benutzer unterbunden, die den Wähleinstellungen zugeordnet sind. Das Aktivieren bzw. Deaktivieren von Faxnachrichten in Wähleinstellungen hat Vorrang vor den Einstellungen für einen einzelnen UM-aktivierten Benutzer.


> [!NOTE]
> Faxeinstellungen für eine UM-Postfachrichtlinie können Sie über die Exchange-Verwaltungskonsole konfigurieren. Sie müssen allerdings die Shell verwenden, um Faxeinstellungen für Wählpläne oder einzelne Benutzer zu konfigurieren.



Weitere Informationen zu Fax Partner finden Sie unter [Microsoft Hindernissen bei für Fax Partner](https://go.microsoft.com/fwlink/?linkid=190238).

Weitere Verwaltungsaufgaben im Zusammenhang mit Faxnachrichten finden Sie unter [Faxfunktion – Verfahren](faxing-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verhindern des Empfangs von Faxnachrichten für Benutzer, die einem Wählplan zugeordnet sind, mithilfe der Shell

In diesem Beispiel wird verhindert, dass UM-aktivierte Benutzer, die dem Satz UM-Wähleinstellungen `MyUMDialPlan` zugeordnet sind, Faxnachrichten empfangen.

    Set-UMDialPlan -Identity MyUMDialPlan -FaxEnabled $false


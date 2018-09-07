---
title: 'Zul. d. Empf. v. Faxnach. für Ben. m. demselben Wählplan: Exchange 2013-Hilfe'
TOCTitle: Zulassen des Empfangs von Faxnachrichten für Benutzer mit demselben Wählplan
ms:assetid: cb245028-0b86-4171-879e-934dd35fa626
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124557(v=EXCHG.150)
ms:contentKeyID: 52062779
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zulassen des Empfangs von Faxnachrichten für Benutzer mit demselben Wählplan

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können allen Benutzern, die einem Unified Messaging-Wählplan (UM) zugeordnet sind, das Empfangen von Faxnachrichten in ihren Postfächern erlauben. Standardmäßig können Benutzer, die für Unified Messaging aktiviert und einem UM-Wählplan zugeordnet sind, Faxnachrichten empfangen. Damit UM-aktivierte Benutzer Faxnachrichten in ihren Postfächern empfangen können, muss der Wählplan für das Akzeptieren eingehender Faxanrufe konfiguriert werden. Sie müssen den Faxbetrieb auch in der UM-Postfachrichtlinie und für den Benutzer aktivieren. Standardmäßig ist der Faxbetrieb für Wählpläne, UM-Postfachrichtlinien und Benutzer aktiviert. Es kann jedoch vorkommen, dass diese Standardeinstellungen geändert wurden und UM-aktivierte Benutzer keine Faxnachrichten empfangen können.

Wenn Sie das Empfangen von Faxnachrichten für einen Satz mit Wähleinstellungen deaktivieren, können alle Benutzer, die den Wähleinstellungen zugeordnet sind, keine Faxnachrichten empfangen. Dies gilt selbst dann, wenn Sie die Eigenschaften eines einzelnen Benutzers für den Empfang von Faxnachrichten konfigurieren. Das Aktivieren bzw. Deaktivieren von Faxnachrichten für einen Wählplan hat Vorrang vor den Einstellungen für den Faxbetrieb für eine UM-Postfachrichtlinie oder einen einzelnen UM-aktivierten Benutzer.


> [!NOTE]
> Faxeinstellungen für eine UM-Postfachrichtlinie können Sie über die Exchange-Verwaltungskonsole konfigurieren. Sie müssen allerdings die Shell verwenden, um Faxeinstellungen für Wählpläne oder einzelne Benutzer zu konfigurieren.



Weitere Informationen zu Faxpartnern finden Sie unter [Microsoft PinPoint für Faxpartner](https://go.microsoft.com/fwlink/?linkid=190238).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Faxnachrichten finden Sie unter [Faxfunktion – Verfahren](faxing-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell, um den Empfang von Faxnachrichten für Benutzer, die einem Wählplan zugeordnet sind, zu erlauben

In diesem Beispiel wird für UM-aktivierte Benutzer, die dem Wählplan `MyUMDialPlan` zugeordnet sind, der Empfang von Faxnachrichten aktiviert.

    Set-UMDialPlan -Identity MyUMDialPlan -FaxEnabled $true


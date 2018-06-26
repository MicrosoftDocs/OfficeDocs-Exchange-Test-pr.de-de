---
title: 'Aktivieren eines Benutzers für den Faxempfang: Exchange 2013 Help'
TOCTitle: Aktivieren eines Benutzers für den Faxempfang
ms:assetid: a0505001-aac0-41ef-824f-76e5e56d7675
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201712(v=EXCHG.150)
ms:contentKeyID: 52062768
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren eines Benutzers für den Faxempfang

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Sie können einen Benutzer für Unified Messaging (UM) aktivieren, damit dieser Faxnachrichten empfangen kann. Wenn Sie einen Benutzer für Unified Messaging aktivieren, kann dieser standardmäßig Faxnachrichten empfangen, wenn Sie den Faxbetrieb aktivieren und einen Faxpartner-URI für die UM-Postfachrichtlinie konfigurieren, die mit dem Benutzer verknüpft ist. Die Faxfunktion kann in den UM-Wähleinstellungen, in den UM-Postfachrichtlinien oder im UM-aktivierten Benutzerpostfach aktiviert oder deaktiviert werden.

Standardmäßig lassen das Postfach des Benutzers und der Wählplan, der dem Benutzer zugeordnet ist, den Faxeingang zu. Damit ein Benutzer jedoch Faxnachrichten empfangen kann, müssen Sie zunächst den Faxeingang in der mit dem UM-aktivierten Benutzer verknüpften UM-Postfachrichtlinie aktivieren und den URI des Faxpartners eingeben.


> [!NOTE]
> Faxeinstellungen für eine UM-Postfachrichtlinie können Sie über die Exchange-Verwaltungskonsole konfigurieren. Sie müssen allerdings die Shell verwenden, um Faxeinstellungen für Wählpläne oder einzelne Benutzer zu konfigurieren.



Weitere Informationen zu Faxpartnern finden Sie unter [Microsoft PinPoint für Faxpartner](https://go.microsoft.com/fwlink/?linkid=190238).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Faxnachrichten finden Sie unter [Faxfunktion – Verfahren](faxing-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Bevor Sie dieses Verfahren ausführen, vergewissern Sie sich, dass in der dem Benutzer zugewiesenen UM-Postfachrichtlinie der Faxbetrieb aktiviert und die URI des Faxpartners ordnungsgemäß konfiguriert ist.

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass der Benutzer für Unified Messaging aktiviert ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Aktivieren des Faxempfangs für einen UM-Benutzer mithilfe der Shell

In diesem Beispiel wird der Empfang eingehender Faxnachrichten für Tony Smith aktiviert.

    Set-UMMailbox -Identity tonysmith@contoso.com -FaxEnabled $true


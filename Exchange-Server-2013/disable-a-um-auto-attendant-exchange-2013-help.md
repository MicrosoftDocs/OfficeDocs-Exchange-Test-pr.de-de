---
title: 'Deaktivieren einer automatischen UM-Telefonzentrale: Exchange Online Help'
TOCTitle: Deaktivieren einer automatischen UM-Telefonzentrale
ms:assetid: ad79f374-f68f-430b-8b9c-2c841e1c55ae
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124228(v=EXCHG.150)
ms:contentKeyID: 50476422
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren einer automatischen UM-Telefonzentrale

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Beim Erstellen einer automatischen UM-Telefonzentrale wird deren Status standardmäßig auf "Deaktiviert" festgelegt. Nachdem Sie die automatische UM-Telefonzentrale erstellt haben, können Sie deren Status ändern, um zu steuern, ob sie eingehende Anrufe annehmen kann. Sie können beispielsweise die automatische UM-Telefonzentrale deaktivieren, um benutzerdefinierte Ansagen und Mitteilungen zum ersten Mal oder erneut aufzuzeichnen.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://technet.microsoft.com/de-de/library/JJ822155(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://technet.microsoft.com/de-de/library/Aa998875(v=EXCHG.150)). Vergewissern Sie sich außerdem, dass der Status der automatischen UM-Telefonzentrale auf "Aktiviert" festgelegt ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren einer automatischen UM-Telefonzentrale mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den Wählplan aus, den Sie ändern möchten, und klicken Sie auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie deaktivieren möchten. Klicken Sie auf der Symbolleiste auf den **Pfeil nach unten**![NACH-UNTEN-TASTE (Symbol)](images/JJ150576.ef5ca57d-a033-457b-bd92-6361877c33d0(EXCHG.150).gif "NACH-UNTEN-TASTE (Symbol)")

3.  Klicken Sie auf der Seite **Warnung** auf **Ja**.

## Deaktivieren einer automatischen UM-Telefonzentrale mithilfe der Shell

In diesem Beispiel wird die automatische UM-Telefonzentrale `MyUMAutoAttendant` deaktiviert.

    Disable-UMAutoAttendant -Identity MyUMAutoAttendant


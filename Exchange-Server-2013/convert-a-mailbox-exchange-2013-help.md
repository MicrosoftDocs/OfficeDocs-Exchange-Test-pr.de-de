---
title: 'Konvertieren eines Postfachs: Exchange 2013 Help'
TOCTitle: Konvertieren eines Postfachs
ms:assetid: dfed045e-a740-4a90-aff9-c58d53592f79
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ710164(v=EXCHG.150)
ms:contentKeyID: 50476902
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konvertieren eines Postfachs

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-04-26_

Das Konvertieren eines Postfachs in einen anderen Postfachtyp ist dem Vorgang in Exchange 2010 sehr ähnlich. Sie müssen weiterhin das Cmdlet „Set-Mailbox“ in der Shell verwenden, um die Konvertierung durchzuführen.

Sie können die folgenden Postfächer von einem Typ in einen anderen konvertieren:

  - Benutzerpostfach in Ressourcenpostfach (Raum/Arbeitsgerät)

  - Freigegebenes Postfach in Benutzerpostfach

  - Freigegebenes Postfach in Ressourcenpostfach

  - Ressourcenpostfach in Benutzerpostfach

  - Ressourcenpostfach in freigegebenes Postfach

Wenn Ihre Organisation eine Exchange-Hybridumgebung verwendet, müssen Sie Ihre Postfächer mithilfe der lokalen Exchange-Verwaltungstools verwalten. Um ein Postfach in einer Hybridumgebung zu konvertieren, müssen Sie das Postfach möglicherweise zurück auf den lokalen Exchange-Computer verschieben, den Postfachtyp konvertieren und das Postfach dann zurück nach Office 365 verschieben.


> [!IMPORTANT]
> Wenn Sie ein Benutzerpostfach in ein freigegebenes Postfach konvertieren, sollten Sie entweder vor der Konvertierung alle mobilen Geräte aus dem Postfach entfernen oder nach der Konvertierung den mobilen Zugriff auf das Postfach blockieren. Der Grund hierfür ist, dass die mobilen Funktionen eines Postfachs nach dessen Konvertierung in ein freigegebenes Postfach nicht mehr ordnungsgemäß arbeiten. Weitere Informationen zum Sperren des Zugriffs finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=847873">Entfernen eines ehemaligen Mitarbeiters aus Office 365</A>.



## Konvertieren eines Postfachs mithilfe der Shell

Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

In diesem Beispiel wird das freigegebene Postfach „MarketingDept1“ in ein Benutzerpostfach konvertiert.

    Set-Mailbox MarketingDept1 -Type Regular

Für den Parameter *Type* können folgende Werte verwendet werden:

  - Regular

  - Room

  - Equipment

  - Shared

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Shell-Befehl aus, um sich zu vergewissern, dass Sie das Postfach erfolgreich konvertiert haben:

    Get-Mailbox -Identity MarketingDept1 | Format-List RecipientTypeDetails

Der Wert für *RecipientTypeDetails* sollte *UserMailbox* lauten.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



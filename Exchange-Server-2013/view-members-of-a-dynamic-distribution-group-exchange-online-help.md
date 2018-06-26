---
title: 'View members of a dynamic distribution group: Exchange Online Help'
TOCTitle: View members of a dynamic distribution group
ms:assetid: 40b100c6-864e-4c82-9f98-08dd5c83e378
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232019(v=EXCHG.150)
ms:contentKeyID: 50474760
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# View members of a dynamic distribution group

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2018-03-02_

Dynamische Verteilergruppen sind Verteilergruppen, deren Mitgliedschaft auf bestimmten Empfängerfiltern und nicht auf einer definierten Empfängergruppe basiert. MicrosoftExchange stellt Musterfilter zur Verfügung, um das Erstellen von Empfängerfiltern für dynamische Verteilergruppen zu vereinfachen. Bei einem *Musterfilter* handelt es sich um einen häufig verwendeten Filter, mit dem verschiedene Kriterien der Empfängerfilterung erfüllt werden. Sie können die Empfängertypen angeben, die in die dynamische Verteilergruppe aufgenommen werden sollen. Außerdem können Sie eine Liste mit Bedingungen angeben, die die Empfänger erfüllen müssen. Sie können mit der Shell eine Vorschau der Empfängerliste für eine dynamische Verteilergruppe anzeigen, die Musterfilter verwendet.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Dynamische Verteilergruppen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Shell zum Anzeigen einer Vorschau der Mitgliederliste für eine dynamische Verteilergruppe

In diesem Beispiel wird die Mitgliederliste für die dynamische Verteilergruppe mit dem Namen "Full Time Employees" zurückgegeben. Mit dem ersten Befehl wird das dynamische Verteilergruppenobjekt in der Variablen `$FTE` gespeichert. Beim zweiten Befehl wird das Cmdlet **Get-Recipient** zum Auflisten der Empfänger verwendet, die die für die dynamische Verteilergruppe definierten Kriterien erfüllen.

    $FTE = Get-DynamicDistributionGroup "Full Time Employees"

    Get-Recipient -RecipientPreviewFilter $FTE.RecipientFilter -OrganizationalUnit $FTE.RecipientContainer

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-DynamicDistributionGroup](https://technet.microsoft.com/de-de/library/bb124762\(v=exchg.150\)) und [Get-Recipient](https://technet.microsoft.com/de-de/library/aa996921\(v=exchg.150\)).


> [!NOTE]
> Sie können keine Mitglieder einer Gruppe dynamische Verteilergruppe mithilfe der Exchange-Verwaltungskonsole anzeigen.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sicherzustellen, dass Sie die Mitglieder einer dynamischen Verteilergruppe erfolgreich angezeigt haben, führen Sie folgende Schritte aus:

  - In der Shell wird eine Liste der Mitglieder zurückgegeben, wenn Sie den vorherigen Befehl ausführen, um eine Vorschau der Liste der Mitglieder für eine dynamische Verteilergruppe anzuzeigen. Wenn Sie beispielsweise ein neues Benutzerpostfach mit Eigenschaften erstellen, die dem Empfängerfilter für die dynamische Verteilergruppe entsprechen, sollte dieser neue Benutzer in der Liste der Gruppenmitglieder angezeigt werden.


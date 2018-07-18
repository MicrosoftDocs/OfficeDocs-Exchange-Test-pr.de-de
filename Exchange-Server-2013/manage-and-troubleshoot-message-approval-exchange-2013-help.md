---
title: 'Verwalten und Problembehandlung der Nachrichtengenehmigung: Exchange 2013 Help'
TOCTitle: Verwalten und Problembehandlung der Nachrichtengenehmigung
ms:assetid: 860df43f-a05b-4da3-83f1-68d3123a923d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298110(v=EXCHG.150)
ms:contentKeyID: 52062871
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten und Problembehandlung der Nachrichtengenehmigung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Unter Umständen erhalten Sie bei dem Versuch, ein Vermittlungspostfach zu entfernen, die folgende Fehlermeldung:


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Vermittlungspostfach &lt;<em>Postfach</em>&gt; kann nicht entfernt werden, da es für den Genehmigungsworkflow für vorhandene Empfänger verwendet wird, für die Mitgliedschaftsbeschränkungen oder die Moderation aktiviert sind. Sie sollten entweder die Genehmigungsfunktionen für diese Empfänger deaktivieren oder ein anderes Vermittlungspostfach für diese Empfänger angeben, bevor Sie dieses Vermittlungspostfach entfernen.</p></td>
</tr>
</tbody>
</table>


Ein Vermittlungspostfach kann für die Handhabung des Genehmigungsworkflows für moderierte Empfänger und Genehmigungen über die Mitgliedschaft in Verteilergruppen verwendet werden. Mithilfe von PowerShell finden Sie alle Empfänger, die für die Verwendung dieses Vermittlungspostfachs konfiguriert sind. Nach dem Bestimmen der Empfänger können Sie sie entweder für die Nutzung eines anderen Vermittlungspostfachs konfigurieren oder die Vermittlung für sie deaktivieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Vermittlung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Schritt 1: Verwenden der Shell, um alle Empfänger zu finden, die das Vermittlungspostfach verwenden, das Sie zu löschen versuchen

Führen Sie die folgenden Befehle aus:

    $AM = Get-Mailbox "<arbitration mailbox>" -Arbitration
    $AMDN = $AM.DistinguishedName
    Get-Recipient -RecipientPreviewFilter {ArbitrationMailbox -eq $AMDN}

Um beispielsweise alle Empfänger zu finden, die das Vermittlungspostfach "Arbitration Mailbox01" verwenden, führen Sie die folgenden Befehle aus:

    $AM = Get-Mailbox "Arbitration Mailbox01" -Arbitration
    $AMDN = $AM.DistinguishedName
    Get-Recipient -RecipientPreviewFilter {ArbitrationMailbox -eq $AMDN}


> [!NOTE]
> Das Vermittlungspostfach wird mit dem Distinguished Name (DN) angegeben. Wenn Sie den DN des Vermittlungspostfachs kennen, können Sie den folgenden Befehl ausführen: <CODE>Get-Recipient -RecipientPreviewFilter {ArbitrationMailbox -eq &lt;DN&gt;}</CODE>.



## Schritt 2: Verwenden der Shell, um ein anderes Vermittlungspostfach anzugeben oder die Moderation für die Empfänger zu deaktivieren

Damit moderierte Empfänger nicht mehr das Vermittlungspostfach verwenden, das Sie zu löschen versuchen, können Sie entweder ein anderes Vermittlungspostfach angeben oder die Moderation für die Empfänger deaktivieren.

Führen Sie den folgenden Befehl aus, wenn Sie ein anderes Vermittlungspostfach für die Empfänger angeben möchten:

    Set-<RecipientType> <Identity> -ArbitrationMailbox <different arbitration mailbox>

Um beispielsweise die Verteilergruppe "All Employees" für die Verwendung des Vermittlungspostfachs "Arbitration Mailbox02" neu zu konfigurieren, führen Sie den folgenden Befehl aus:

    Set-DistributionGroup "All Employees" -ArbitrationMailbox "Arbitration Mailbox02"

Führen Sie den folgenden Befehl aus, wenn Sie die Moderation für die Empfänger deaktivieren möchten:

    Set-<RecipientType> <Identity> -ModerationEanbled $false

Um beispielsweise die Moderation für das Postfach "Human Resources" zu deaktivieren, führen Sie den folgenden Befehl aus:

    Set-Mailbox "Human Resources" -ModerationEanbled $false

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Das Verfahren war erfolgreich, wenn Sie das Vermittlungspostfach löschen können, ohne die Fehlermeldung zu erhalten, dass es verwendet wird.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).


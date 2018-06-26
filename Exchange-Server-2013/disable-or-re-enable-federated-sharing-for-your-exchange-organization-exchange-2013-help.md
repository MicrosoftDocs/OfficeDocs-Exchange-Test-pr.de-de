---
title: 'Deaktivieren oder erneutes Aktivieren der Verbundfreigabe für Ihre Exchange-Organisation: Exchange 2013 Help'
TOCTitle: Deaktivieren oder erneutes Aktivieren der Verbundfreigabe für Ihre Exchange-Organisation
ms:assetid: d36490d8-0268-47b9-a6d4-e56427f1b02e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657497(v=EXCHG.150)
ms:contentKeyID: 50476790
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Deaktivieren oder erneutes Aktivieren der Verbundfreigabe für Ihre Exchange-Organisation

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-02-17_

In bestimmten Situationen müssen Sie möglicherweise vorübergehend die Verbundfreigabe für Ihre Organisation deaktivieren. Statt die vorhandene Verbundvertrauensstellung bzw. Organisationsbeziehungen und Freigaberichtlinien zu löschen, die Sie in Zukunft vielleicht noch benötigen, können Sie einfach die Organisations-ID (OrgID) für die Verbundvertrauensstellung deaktivieren.


> [!WARNING]
> In Hybridbereitstellungen mit Office&nbsp;365 werden durch das Deaktivieren der Verbundvertrauensstellung für die lokalen Server auch Hybridfeatures wie die Freigabe von Frei/Gebucht-Informationen im Kalender, E-Mail-Info und Nachrichtenverfolgung deaktiviert. Der sichere E-Mail-Transport wird in der Hybridbereitstellung jedoch nicht deaktiviert, wenn die Verbundvertrauensstellung für die lokale Organisation deaktiviert wird.



Weitere Informationen zu Verbundvertrauensstellungen finden Sie unter [Verbund](federation-exchange-2013-help.md). Weitere Informationen zur Verbundfreigabe finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Verbundfreigabe finden Sie unter [Verbundverfahren](federation-procedures-exchange-2013-help.md).


> [!IMPORTANT]
> Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "*Federation and certificates*-Berechtigungen" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Vorhandene Organisationsbeziehungen und Freigaberichtlinien für andere Exchange-Verbundorganisationen werden nicht geändert, funktionieren aber auch nicht. Freigaberichtlinien, über die Empfängern im Internet Zugriff auf Kalenderinformationen bereitgestellt wird, sind davon nicht betroffen.

  - Die Organisations-ID für eine Verbundvertrauensstellung kann nicht in der Exchange-Verwaltungskonsole deaktiviert bzw. aktiviert werden. Sie müssen die Shell verwenden.

## Deaktivieren bzw. erneutes Aktivieren der Verbundfreigabe mithilfe der Shell

In diesem Beispiel wird die Organisations-ID deaktiviert, und es werden der Verbund und die Verbundfreigabe für die Exchange-Organisation deaktiviert.

    Set-FederatedOrganizationIdentifier -Enabled $false

In diesem Beispiel wird die Organisations-ID wieder aktiviert, und es werden der Verbund und die Verbundfreigabe für die Exchange-Organisation wieder aktiviert.

    Set-FederatedOrganizationIdentifier -Enabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-FederatedOrganizationIdentifier](https://technet.microsoft.com/de-de/library/dd351037\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Die erfolgreiche Ausführung des Cmdlets **Set-OrganizationIdentifier** ist ein erster Zeichen dafür, dass die Organisations-ID deaktiviert bzw. aktiviert wurde.

Für eine weitere Prüfung können Sie den folgenden Shell-Befehl ausführen und den für den Parameter *Enabled* zurückgegebenen Wert überprüfen

    Get-FederatedOrganizationIdentifier


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



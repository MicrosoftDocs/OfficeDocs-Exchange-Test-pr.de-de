---
title: 'Erstellen einer Outlook-Schutzregel: Exchange 2013 Help'
TOCTitle: Erstellen einer Outlook-Schutzregel
ms:assetid: da64750d-faaf-44de-ad8c-888eba7fbdbf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638196(v=EXCHG.150)
ms:contentKeyID: 50476846
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Outlook-Schutzregel

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Unter Verwendung von Microsoft Outlook-Schutzregeln können Sie Nachrichten durch IRM (Information Rights Management, Verwaltung von Informationsrechten) schützen, indem Sie vor dem Senden der Nachrichten eine Active Directory RMS-Vorlage (Rights Management Services, Rechteverwaltungsdienste) in Outlook 2010 anwenden.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rechteschutz" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Sie müssen einen [AD RMS](https://technet.microsoft.com/de-de/library/hh831364.aspx)-Server in derselben Active Directory-Gesamtstruktur bereitstellen, in der sich auch der Server mit Microsoft Exchange Server 2013 befindet.

  - Wenn Sie Outlook-Schutzregeln für durch IRM geschützte Nachrichten konfigurieren, sollten Sie die Transportentschlüsselung in Betracht ziehen, sodass Transport-Agents (einschließlich des Agents für Transportregeln) die Nachricht entschlüsseln und auf diese zugreifen können. Bei Verwendung der Journalfunktion sollten Sie auch die Aktivierung der Journalberichtentschlüsselung erwägen, sodass der Journal-Agent eine nicht verschlüsselte Kopie der Nachricht im Journalbericht speichern kann. Weitere Informationen finden Sie unter [Journalberichtentschlüsselung](journal-report-decryption-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht zum Erstellen von Outlook-Schutzregeln verwendet werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen einer Outlook-Schutzregel mithilfe der Shell

In diesem Beispiel wird die Outlook-Schutzregel "Project Contoso" erstellt. Mithilfe dieser Regel werden Nachrichten, die an die Verteilergruppe "ContosoPMs" gesendet werden, mit der AD RMS-Vorlage "Business Critical" geschützt.

    New-OutlookProtectionRule -Name "Project Contoso" -SentTo "DL-ContosoPMs@contoso.com" -ApplyRightsProtectionTemplate "Business Critical"


> [!NOTE]
> Wenn Sie das Prädikat <CODE>SentTo</CODE> für eine Outlook-Schutzregel verwenden und eine Verteilergruppe angeben, werden nur Nachrichten durch IRM geschützt, die über die Felder <STRONG>An</STRONG>, <STRONG>Cc</STRONG> oder <STRONG>Bcc</STRONG> an die Verteilergruppe gesendet werden. Auf Nachrichten, die an einzelne Mitglieder der Verteilergruppe gesendet werden, wird der IRM-Schutz nicht angewendet.



Sie können auch die Prädikate `FromDepartment` und `SentToScope` einsetzen, um Nachrichten von Benutzern in der angegebenen Abteilung oder Nachrichten an den angegebenen Bereich (`InOrganization` für interne Nachrichten, `All` für alle Empfänger) durch IRM zu schützen.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-OutlookProtectionRule](https://technet.microsoft.com/de-de/library/dd298182\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie erfolgreich eine Outlook-Schutzregel erstellt haben:

  - Führen Sie das Cmdlet [Get-OutlookProtectionRule](https://technet.microsoft.com/de-de/library/dd298004\(v=exchg.150\)) aus, um zu überprüfen, ob die Regel erstellt wurde, und um die Eigenschaften der Regel anzuzeigen. Ein Beispiel, wie eine Outlook-Schutzregel abgerufen wird, finden Sie unter [Examples](https://technet.microsoft.com/de-de/dd298004\(exchg.150\)#examples) in **Get-OutlookProtectionRule**.

  - Erstellen Sie in Outlook 2010 eine Testnachricht, die die Regelbedingungen erfüllt, und stellen Sie sicher, dass die Regel auf dem Client ausgelöst wird.
    

    > [!NOTE]
    > Es kann einige Zeit dauern, bis eine Outlook-Schutzregel in Outlook verfügbar ist.



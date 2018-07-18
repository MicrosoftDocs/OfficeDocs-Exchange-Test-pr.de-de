---
title: 'Anzeigen von Antispamstempeln in Outlook: Exchange 2013 Help'
TOCTitle: Anzeigen von Antispamstempeln in Outlook
ms:assetid: cddb5dbf-ad1e-471c-9fc8-28ddcf7ec1d0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124595(v=EXCHG.150)
ms:contentKeyID: 50476744
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Anzeigen von Antispamstempeln in Outlook

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Sie können Microsoft Outlook zum Anzeigen von Antispamstempeln verwenden, die von Microsoft Exchange einer E-Mail zugewiesen wurden. Antispamstempel helfen Ihnen bei der Diagnose spambezogener Probleme, indem Diagnosemetadaten oder Stempel (z. B. absenderspezifische Informationen, Ergebnisse der Poststempelüberprüfung und Ergebnisse der Inhaltsfilterung) auf Nachrichten angewendet werden, während die Nachrichten die Antispam-Agents passieren, die aus dem Internet eingehende Nachrichten filtern.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachzugriff" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden von Outlook 2010 oder Outlook 2013 zum Anzeigen von Antispamstempeln

1.  Doppelklicken Sie zum Öffnen einer Nachricht in Outlook 2010 oder Outlook 2013 auf einem Clientcomputer in der E-Mail-Ansicht auf eine Nachricht.

2.  Klicken Sie im Abschnitt **Tags** des Menübands auf das Symbol **Optionen**, um das Dialogfeld **Eigenschaften** der Nachricht anzuzeigen.

3.  Verwenden Sie im Dialogfeld **Eigenschaften** im Abschnitt **Internetkopfzeilen** die Bildlaufleiste, um Antispamstempel anzuzeigen. Beispiel.
    
        X-MS-Exchange-Organization-PCL:7
        X-MS-Exchange-Organization-SCL:6
        X-MS-Exchange-Organization-Antispam-Report: DV:3.1.3924.1409;SID:SenderIDStatus Fail;PCL:PhishingLevel SUSPICIOUS;CW:CustomList;PP:Presolved;TIME:TimeBasedFeatures

## Verwenden von Outlook 2007 zum Anzeigen von Antispamstempeln

1.  Klicken Sie zum Öffnen einer Nachricht in Outlook 2007 auf einem Clientcomputer in der E-Mail-Ansicht auf eine Nachricht.

2.  Kicken Sie auf der Registerkarte **Nachricht** unter **Optionen** auf **Nachrichtenoptionen**.

3.  Verwenden Sie im Dialogfeld **Nachrichtenoptionen** im Abschnitt **Internetkopfzeilen** die Bildlaufleiste, um Antispamstempel anzuzeigen. Beispiel.
    
        X-MS-Exchange-Organization-PCL:7
        X-MS-Exchange-Organization-SCL:6
        X-MS-Exchange-Organization-Antispam-Report: DV:3.1.3924.1409;SID:SenderIDStatus Fail;PCL:PhishingLevel SUSPICIOUS;CW:CustomList;PP:Presolved;TIME:TimeBasedFeatures


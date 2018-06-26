---
title: 'Konfigurieren der Gruppenmetrik: Exchange 2013 Help'
TOCTitle: Konfigurieren der Gruppenmetrik
ms:assetid: 76ccd6a7-e2ec-42f4-9ab3-e8cc257ac896
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ649327(v=EXCHG.150)
ms:contentKeyID: 50476033
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren der Gruppenmetrik

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

E-Mail-Infos, die Angaben zur Größe von Verteilergruppen und dynamischen Verteilergruppen bereitstellen, stützen sich auf Gruppenmetrikdaten. Gruppenmetrikdaten werden auf designierten Postfachservern generiert. Weitere Informationen zu Gruppenmetrikdaten finden Sie unter [Gruppe Metriken und e-Mail-Infos](group-metrics-and-mailtips-exchange-2013-help.md).

Sie können das Generieren von Gruppenmetrikdaten auf einem Postfachserver aktivieren oder deaktivieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Gruppenmetrik" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Gruppenmetrikdaten werden nur für E-Mail-Infos verwendet. Stellen Sie sicher, dass auf Gruppenmetrikdaten basierende E-Mail-Infos in Ihrer Organisation aktiviert sind. Ausführliche Anleitungen finden Sie unter [Verwalten von E-Mail-Infos für Organisationsbeziehungen](manage-mailtips-for-organization-relationships-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Aktivieren oder Deaktivieren der Generierung von Gruppenmetrikdaten


> [!NOTE]
> Gruppenmetrikdaten werden standardmäßig auf einem beliebigen Server generiert, der auch das Offlineadressbuch (OAB) generiert. Diese Beispiele sind nur für Organisationen erforderlich, die keine Offlineadressbücher verwenden.



Führen Sie folgenden Befehl aus, um die Generierung von Gruppenmetrikdaten auf einem Postfachserver zu aktivieren oder zu deaktivieren:

    Set-MailboxServer <ServerIdentity> -ForceGroupMetricsGeneration <$true | $false>

Im folgenden Beispiel wird die Generierung von Gruppenmetrikdaten auf dem Postfachserver "MBX1" aktiviert.

    Set-MailboxServer MBX1 -ForceGroupMetricsGeneration $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Generierung von Gruppenmetrikdaten in einer Organisation, in der keine Offlineadressbücher verwendet werden, erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-MailboxServer <ServerIdentity> | Format-List ForceGroupMetricsGeneration

2.  Überprüfen Sie, ob die angezeigte Einstellung der Einstellung entspricht, die Sie konfiguriert haben.


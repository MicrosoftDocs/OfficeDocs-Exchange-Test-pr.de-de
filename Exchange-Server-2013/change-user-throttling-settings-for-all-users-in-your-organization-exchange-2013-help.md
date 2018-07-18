---
title: 'Ändern von Benutzereinschränkungseinstellungen für alle Benutzer in Ihrer Organisation: Exchange 2013 Help'
TOCTitle: Ändern von Benutzereinschränkungseinstellungen für alle Benutzer in Ihrer Organisation
ms:assetid: c45cacfc-768d-4605-9bb0-53e30273fe4d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ863578(v=EXCHG.150)
ms:contentKeyID: 50554901
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern von Benutzereinschränkungseinstellungen für alle Benutzer in Ihrer Organisation

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-08-05_

Sie können steuern, wie Ressourcen von einzelnen Benutzern in Ihrer Exchange-Organisation genutzt werden, indem Sie die standardmäßigen Einschränkungseinstellungen ändern.

Das Festlegen, wie Ressourcen von einzelnen Benutzern verwendet werden, war bereits in Exchange Server 2010 möglich. Diese Funktion wurde für Exchange Server 2013 erweitert. Die Richtlinie mit dem Namen "GlobalThrottlingPolicy" definiert die standardmäßigen Einschränkungseinstellungen für alle neuen und vorhandenen Benutzer in Ihrer Organisation, es sei denn, Sie haben die Einschränkungsrichtlinien angepasst. In vielen typischen Exchange-Bereitstellungsszenarien ist die Richtlinie "GlobalThrottlingPolicy" für die Verwaltung von Benutzern geeignet.

Wenn Sie die Einschränkungseinstellungen für alle Benutzer in Ihrer Organisation anpassen möchten, erstellen Sie eine neue Einschränkungsrichtlinie mit der Bereichszuweisung "Organization". Sie können über die Shell nur die standardmäßigen Einschränkungseinstellungen ändern.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Benutzereinschränkungen" im Thema [Berechtigungen für Serverstatus und Leistung](server-health-and-performance-permissions-exchange-2013-help.md).

  - In neuen Richtlinien mit dem Bereich "Organization" sollten lediglich die Einschränkungseinstellungen festgelegt werden, die nicht mit "GlobalThrottlingPolicy" und anderen Organisationsrichtlinien identisch sind. Auf diese Weise werden die restlichen Richtlinieneinstellungen der Richtlinie "GlobalThrottlingPolicy" sowie alle Aktualisierungen an Einschränkungsrichtlinien vererbt, die bei künftigen Updates von Exchange hinzugefügt werden. Bevor Sie dieses Verfahren ausführen, sollten Sie den Abschnitt "Verwalten von Einschränkungsrichtlinien mithilfe von Bereichen" im Thema [Verwaltung von Exchange-Arbeitsauslastungen](exchange-workload-management-exchange-2013-help.md) lesen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Ändern der Weise, in der Ressourcen von allen Benutzern in der gesamten Organisation verwendet werden können, mithilfe der Shell

In diesem Beispiel wird eine Einschränkungsrichtlinie erstellt, die für alle Benutzer in Ihrer Organisation gilt. Alle von Ihnen ausgelassenen Parameter erben die Werte der Standardeinschränkungsrichtlinie "GlobalThrottlingPolicy".

    New-ThrottlingPolicy -Name AllUsersEWSPolicy EwsMaxConcurrency 4 -ThrottlingPolicyScope Organization

Weitere Informationen zu Syntax und Parametern finden Sie unter [New-ThrottlingPolicy](https://technet.microsoft.com/de-de/library/dd351045\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Einschränkungsrichtlinie "Organization" erfolgreich erstellt wurde:

1.  Führen Sie den folgenden Befehl aus.
    
        Get-ThrottlingPolicy | Format-List

2.  Überprüfen Sie, ob die Einschränkungsrichtlinie "Organization", die Sie zuvor erstellt haben, in der Spalte enthalten ist, die das Objekt "GlobalThrottlingPolicy" enthält.

3.  Führen Sie den folgenden Befehl aus.
    
        Get-ThrottlingPolicy | Format-List

4.  Prüfen Sie, ob die Eigenschaften der neuen Richtlinie "Organization" Ihren konfigurierten Werten entspricht.


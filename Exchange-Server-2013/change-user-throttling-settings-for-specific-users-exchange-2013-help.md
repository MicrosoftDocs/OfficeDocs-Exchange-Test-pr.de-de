---
title: 'Ändern v. Benutzereinschränkungseinst. f. best. Benutzer: Exchange 2013-Hilfe'
TOCTitle: Ändern von Benutzereinschränkungseinstellungen für bestimmte Benutzer
ms:assetid: c5f834d6-189d-485e-9800-5e0066815ecf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ863577(v=EXCHG.150)
ms:contentKeyID: 50554904
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern von Benutzereinschränkungseinstellungen für bestimmte Benutzer

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-08-05_

Sie können steuern, wie Ressourcen von einzelnen Benutzern in Ihrer Exchange-Organisation genutzt werden, indem Sie die standardmäßigen Einschränkungseinstellungen ändern.

Das Festlegen, wie Ressourcen von einzelnen Benutzern verwendet werden, war bereits in Exchange Server 2010 möglich. Diese Funktion wurde für Exchange Server 2013 erweitert. Die Richtlinie mit dem Namen "GlobalThrottlingPolicy" definiert die standardmäßigen Einschränkungseinstellungen für alle neuen und vorhandenen Benutzer in Ihrer Organisation, es sei denn, Sie haben die Einschränkungsrichtlinien angepasst. In vielen typischen Exchange-Bereitstellungsszenarien ist die Richtlinie "GlobalThrottlingPolicy" für die Verwaltung von Benutzern geeignet.

Wenn Sie die Einschränkungseinstellungen für spezifische Benutzer in Ihrer Organisation anpassen möchten, erstellen Sie eine neue Einschränkungsrichtlinie mit der Bereichszuweisung "Regular". Sie können über die Shell nur die standardmäßigen Einschränkungseinstellungen ändern.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Benutzereinschränkungen" im Thema [Berechtigungen für Serverstatus und Leistung](server-health-and-performance-permissions-exchange-2013-help.md).

  - In neuen Richtlinien mit dem Bereich "Regular" sollten lediglich die Einschränkungseinstellungen festgelegt werden, die nicht mit "GlobalThrottlingPolicy" und anderen Organisationsrichtlinien identisch sind. Auf diese Weise werden die restlichen Richtlinieneinstellungen der Richtlinie "GlobalThrottlingPolicy" sowie alle Aktualisierungen an Einschränkungsrichtlinien vererbt, die bei künftigen Updates von Exchange hinzugefügt werden. Bevor Sie dieses Verfahren ausführen, sollten Sie den Abschnitt "Verwalten von Einschränkungsrichtlinien mithilfe von Bereichen" im Thema [Verwaltung von Exchange-Arbeitsauslastungen](exchange-workload-management-exchange-2013-help.md) lesen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Ändern der Weise, in der Ressourcen von bestimmten Benutzern in der gesamten Organisation verwendet werden können, mithilfe der Shell

In diesem Beispiel wird die nicht standardmäßige Benutzereinschränkungsrichtlinie "ITStaffPolicy" erstellt, die bestimmten Benutzern zugewiesen werden kann. Alle von Ihnen ausgelassenen Parameter erben die Werte der Standardeinschränkungsrichtlinie "GlobalThrottlingPolicy". Nachdem Sie diese Richtlinie erstellt haben, müssen Sie sie bestimmten Benutzern zuordnen.

```powershell
New-ThrottlingPolicy -Name ITStaffPolicy -EwsMaxConcurrency 4 -ThrottlingPolicyScope Regular
```

In diesem Beispiel wird dem Benutzer "tonysmith" die Einschränkungsrichtlinie "ITStaffPolicy" (mit höheren Grenzwerten) zugeordnet.

```powershell
Set-ThrottlingPolicyAssociation -Identity tonysmith -ThrottlingPolicy ITStaffPolicy
```

Das Cmdlet **Set-ThrottlingPolicyAssociation** muss nicht verwendet werden, um einem Benutzer eine Richtlinie zuzuordnen. Alternativ können die folgenden Befehle ausgeführt werden, um dem Benutzer "tonysmith" die Einschränkungsrichtlinie "ITStaffPolicy" zuzuordnen.

```
```powershell
$b = Get-ThrottlingPolicy ITStaffPolicy
```
```

```
```powershell
Set-Mailbox -Identity tonysmith -ThrottlingPolicy $b
```
```

Weitere Informationen zu Syntax und Parametern finden Sie unter [New-ThrottlingPolicy](https://technet.microsoft.com/de-de/library/dd351045\(v=exchg.150\)) und [Set-ThrottlingPolicyAssociation](https://technet.microsoft.com/de-de/library/ff459231\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Einschränkungsrichtlinie "Regular" erfolgreich erstellt wurde:

1.  Führen Sie den folgenden Befehl aus.
    
    ```powershell
Get-ThrottlingPolicy | Format-List
```

2.  Überprüfen Sie, ob die Einschränkungsrichtlinie "Regular", die Sie zuvor erstellt haben, in der Spalte enthalten ist, die das Objekt "GlobalThrottlingPolicy" enthält.

3.  Führen Sie den folgenden Befehl aus.
    
    ```powershell
Get-ThrottlingPolicy | Format-List
```

4.  Prüfen Sie, ob die Eigenschaften der neuen Richtlinie "Regular" Ihren konfigurierten Werten entspricht.

5.  Führen Sie den folgenden Befehl aus.
    
    ```powershell
Get-ThrottlingPolicyAssociation
```

6.  Überprüfen Sie, ob die neue Richtlinie "Regular" den Benutzern zugeordnet ist, denen Sie sie zugeordnet haben.


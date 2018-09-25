---
title: 'Verwalten von Remotedomänen: Exchange 2013 Help'
TOCTitle: Verwalten von Remotedomänen
ms:assetid: 41a86907-bd9e-40d0-94d3-6deb95a0bffa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997639(v=EXCHG.150)
ms:contentKeyID: 52062694
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.NewRemoteDomainWizardForm.NewRemoteDomainWizardPage
ms.translationtype: HT
---

# Verwalten von Remotedomänen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-13_

Bei Remotedomänen handelt es sich um SMTP-Domänen, die sich außerhalb Ihrer Microsoft Exchange-Organisation befinden. Sie können Remotedomäneneinträge erstellen, um die Einstellungen für die Nachrichtenübergabe zwischen Ihrer Exchange-Organisation und bestimmten externen Domänen festzulegen. Die Einstellungen im Remotedomäneneintrag für eine bestimmte externe Domäne setzen die Einstellungen in der Standardremotedomäne außer Kraft, die normalerweise für alle externen Empfänger gelten. Die Remotedomäneneinstellungen gelten global für die Exchange-Organisation.

Wenn Sie einen Remotedomäneneintrag entfernen, gelten die Einstellungen für die Nachrichtenübermittlung nicht mehr für Nachrichten, die an die Remotedomäne gesendet werden. Durch das Entfernen eines Remotedomäneneintrags wird der E-Mail-Fluss zur Remotedomäne nicht deaktiviert. Nach dem Entfernen eines Remotedomäneneintrags gelten die Konfigurationseinstellungen der Standardremotedomäne für neue Nachrichten, die an diese Domäne gesendet werden. Die Standardremotedomäne kann nicht entfernt werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Remotedomänen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Sie können keine Remotedomäne für einen Adressraum erstellen, der in Ihrer Organisation als akzeptierte Domäne konfiguriert ist. Wenn Ihre Organisation beispielsweise E-Mail für "fabrikam.com" akzeptiert, können Sie keine Remotedomäne für "fabrikam.com" erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie tun?

## Erstellen einer Remotedomäne mithilfe der Shell

Verwenden Sie folgende Syntax, um einen neuen Remotedomäneneintrag zu erstellen.

```powershell
New-RemoteDomain -Name <Descriptive Name> -DomainName <SMTP address space>
```

In diesem Beispiel wird ein Remotedomäneneintrag für Nachrichten erstellt, die an die Domäne "contoso.com" gesendet werden.

```powershell
New-RemoteDomain -Name Contoso -DomainName contoso.com
```

In diesem Beispiel wird ein Remotedomäneneintrag für Nachrichten erstellt, die an die Domäne "fabrikam.com" und alle Unterdomänen gesendet werden.

```powershell
    New-RemoteDomain -Name Fabrikam -DomainName *.fabrikam.com
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine Remotedomäne erfolgreich erstellt wurde:

1.  Führen Sie den Befehl **Get-RemoteDomain** aus, und prüfen Sie, ob die Remotedomäne aufgeführt wird.

2.  Führen Sie den Befehl `Get-RemoteDomain <Remote Domain Name> | Format-List` aus, um die Einstellungen für die neue Remotedomäne zu überprüfen. Senden Sie eine Testnachricht an einen Empfänger in dem Adressraum, der im neuen Remotedomäneneintrag angegeben wurde, und stellen Sie sicher, dass die Nachrichteneinstellungen denjenigen im neuen Remotedomäneneintrag entsprechen.

## Konfigurieren einer Remotedomäne mithilfe der Shell

Die Einstellungen im Remotedomäneneintrag werden mit dem Cmdlet **Set-RemoteDomain** konfiguriert. Es gibt viele verschiedene Einstellungen, die sich auf automatische Antworten, das Nachrichtenformat und die Verschlüsselung sowie auf andere Nachrichteneinstellungen beziehen. Weitere Informationen finden Sie unter [Set-RemoteDomain](https://technet.microsoft.com/de-de/library/aa997857\(v=exchg.150\)).

Informationen zum Konfigurieren von Remotedomänen für bestimmte Szenarios finden Sie in den folgenden Themen:

  - [Konfigurieren von Abwesenheitsbenachrichtigungen für die Remotedomäne](configure-remote-domain-out-of-office-replies-exchange-2013-help.md)

  - [Konfigurieren von automatischen Antworten für die Remotedomäne](configure-remote-domain-automatic-replies-exchange-2013-help.md)

  - [Konfigurieren von Nachrichtenberichten für Remotedomänen](configure-remote-domain-message-reporting-exchange-2013-help.md)

## Entfernen einer Remotedomäne mithilfe der Shell

Verwenden Sie folgende Syntax, um einen Remotedomäneneintrag zu entfernen.

```powershell
Remove-RemoteDomain <RemoteDomainName>
```

In diesem Beispiel wird der Remotedomäneneintrag namens "Contoso" entfernt

```powershell
Remove-RemoteDomain Contoso
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass die Remotedomäne erfolgreich entfernt wurde:

1.  Führen Sie den Befehl **Get-RemoteDomain** aus, und stellen Sie sicher, dass die Remotedomäne nicht aufgeführt wird.

2.  Führen Sie den Befehl `Get-RemoteDomain Default | Format-List` aus, um die Einstellungen für die Standardremotedomäne zu überprüfen. Senden Sie eine Testnachricht an einen Empfänger in dem Adressraum, der im entfernten Remotedomäneneintrag angegeben wurde, und stellen Sie sicher, dass die Nachrichteneinstellungen denjenigen entsprechen, die in der Standardremotedomäne festgelegt sind.


---
title: 'Festl. d. Admins u. Benutzer, die Add-Ins für Outlook inst. und verw. dürfen'
TOCTitle: Festlegen der Administratoren und Benutzer, die Add-Ins für Outlook installieren und verwalten dürfen
ms:assetid: 7ee4302d-b8bb-40a0-9810-10d3a0271bcb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ943754(v=EXCHG.150)
ms:contentKeyID: 52062868
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen der Administratoren und Benutzer, die Add-Ins für Outlook installieren und verwalten dürfen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2017-02-08_

Sie können angeben, welche Administratoren in Ihrer Organisation Berechtigungen zum Installieren und Verwalten von Add-Ins für Outlook haben. Außerdem können Sie angeben, welche Benutzer in Ihrer Organisation die Berechtigung zum Installieren und Verwalten von Add-Ins zur eigenen Verwendung besitzen.

Dies geschieht durch Zuweisen oder Entfernen von Verwaltungsrollen zu bestimmten Add-Ins. Es gibt fünf integrierte Rollen, die Sie verwenden können.

Administratorrollen

  - **Marketplace-Apps einer Organisation**   Ermöglicht einem Administrator das Installieren und Verwalten von Add-Ins, die im Office Store für die Organisation verfügbar sind.

  - **Benutzerdefinierte Apps einer Organisation**   Ermöglicht einem Administrator das Installieren und Verwalten benutzerdefinierter Add-Ins in der Organisation.

Benutzerrollen

  - **Eigene Marketplace-Apps**   Ermöglicht einem Benutzer das Installieren und Verwalten von Office Store-Add-Ins für die eigene Verwendung.

  - **Eigene benutzerdefinierte Apps**   Ermöglicht einem Benutzer das Installieren und Verwalten benutzerdefinierter Add-Ins für die eigene Verwendung.

  - **Eigene ReadWriteMailbox Apps**   Ermöglicht einem Benutzer das Installieren und Verwalten von Add-Ins, für die die ReadWriteMailbox-Berechtigungsstufe im Manifest erforderlich ist.

Standardmäßig sind für alle Administratoren mit der Rollengruppe **Organisationsverwaltung** beide oben genannten administrativen Rollen aktiviert. Standardmäßig sind auch beide genannten Benutzerrollen für Endbenutzer aktiviert.

Informationen zu jeder dieser Rollen finden Sie unter [Rolle „Marketplace-Apps einer Organisation\&quot;](org-marketplace-apps-role-exchange-2013-help.md), [Rolle „Benutzerdefinierte Apps einer Organisation\&quot;](org-custom-apps-role-exchange-2013-help.md), [Rolle „Eigene Marketplace-Apps\&quot;](my-marketplace-apps-role-exchange-2013-help.md), [Rolle „Eigene benutzerdefinierte Apps\&quot;](my-custom-apps-role-exchange-2013-help.md)und [Rolle „My ReadWriteMailbox Apps\&quot;](my-readwritemailbox-apps-role-exchange-2013-help.md).

Informationen zu Add-Ins finden Sie unter [Apps für Outlook](https://technet.microsoft.com/de-de/library/JJ943753(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie dieses Cmdlet ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. In diesem Thema sind zwar alle Parameter für das Cmdlet aufgeführt, aber Sie verfügen möglicherweise nicht über Zugriff auf einige Parameter, falls diese nicht in den Ihnen zugewiesenen Berechtigungen enthalten sind. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter „Rollenzuweisungen\&quot; im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Zugriff auf Office Store wird für Postfächer oder Organisationen in bestimmten Regionen nicht unterstützt. Wenn **Aus dem Office Store hinzufügen** nicht als Option im **Exchange Admin Center** unter **Organisation** \> **Add-Ins** \> ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") angezeigt wird, können Sie ein Add-In für Outlook über eine URL oder einen Dateispeicherort installieren. Weitere Informationen erhalten Sie von Ihrem Dienstanbieter.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Zuweisen von Berechtigungen zu Administratoren, die für das Installieren und Verwalten von Add-Ins in Ihrer Organisation benötigt werden

## Zuweisen von Berechtigungen zu Administratoren über die Exchange-Verwaltungskonsole

Über das EAC können Sie Administratoren die Berechtigungen zuweisen, die für das Installieren und Verwalten von Add-Ins aus dem Office Store für Ihre Organisation benötigt werden. Weitere Informationen hierzu finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

## Zuweisen von Berechtigungen zu Benutzern, die für das Installieren und Verwalten von Add-Ins zur eigenen Verwendung benötigt werden

## Zuweisen von Berechtigungen zu Benutzern über die Exchange-Verwaltungskonsole

Über das EAC können Sie Benutzern die Berechtigungen zuweisen, die für das Anzeigen und Ändern benutzerdefinierter Add-Ins zur eigenen Verwendung benötigt werden. Weitere Informationen hierzu finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Überprüfen, ob Sie einem Benutzer Berechtigungen erfolgreich zugewiesen haben, führen Sie einem Shell-Befehl im Format `Get-ManagementRoleAssignment -Role <Role Name> -GetEffectiveUsers` aus, bei dem `Role Name` der Rolle ist, deren zugewiesene Berechtigungen Sie überprüfen möchten.

Dieses Beispiel veranschaulicht, wie Sie überprüfen können, wem Sie Berechtigungen zum Installieren von Add-Ins aus dem Office Store für die Organisation zugewiesen haben.

1.  Führen Sie `Get-ManagementRoleAssignment -Role "Org Marketplace Apps" -GetEffectiveUsers` aus.

2.  Überprüfen Sie in den Ergebnissen die Einträge in der Spalte **Gültige Benutzer**.

Weitere Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).


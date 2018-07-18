---
title: 'Grundlegendes zu Verwaltungsrollenzuweisungen: Exchange 2013 Help'
TOCTitle: Grundlegendes zu Verwaltungsrollenzuweisungen
ms:assetid: 1dc33dd6-52fb-4852-a5ce-027bc73e1d8f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335131(v=EXCHG.150)
ms:contentKeyID: 50475161
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu Verwaltungsrollenzuweisungen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-04_

Eine *Verwaltungsrollenzuweisung* gehört zum Berechtigungsmodell der rollenbasierten Zugriffssteuerung (Role Based Access Control, RBAC) in Microsoft Exchange Server 2013. Sie stellt die Verknüpfung zwischen einer Verwaltungsrolle und einem Rollenempfänger her. Ein *Rollenempfänger* ist eine Rollengruppe, eine Rollenzuweisungsrichtlinie, ein Benutzer oder eine universelle Sicherheitsgruppe (Universal Security Group, USG). Eine Rolle muss einem Rollenempfänger zugewiesen werden, um wirksam zu werden. Weitere Informationen zu RBAC finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).


> [!NOTE]
> Inhalt dieses Themas ist die erweiterte RBAC-Funktionalität. Informationen zum Verwalten grundlegender Exchange 2013-Berechtigungen finden Sie unter <A href="permissions-exchange-2013-help.md">Berechtigungen</A>. In diesem Thema wird z.&nbsp;B. beschrieben, wie Sie das Exchange Admin Center (EAC) verwenden, um Mitglieder zu Rollengruppen hinzuzufügen oder aus diesen zu entfernen oder um Rollengruppen und Rollenzuweisungsrichtlinien zu erstellen oder zu ändern.



In diesem Thema werden die Zuweisung von Rollen zu Rollengruppen und Rollenzuweisungsrichtlinien sowie die direkte Rollenzuweisung zu Benutzern und USGs erörtert. Die Zuweisung von Rollengruppen oder Rollenzuweisungsrichtlinien zu Benutzern werden hier nicht berücksichtigt. Weitere Informationen zu Rollengruppen und Rollenzuweisungsrichtlinien, die für die Zuweisung von Berechtigungen zu Benutzern empfohlenen Methoden, finden Sie in den folgenden Themen:

  - [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien](understanding-management-role-assignment-policies-exchange-2013-help.md)

Sie können die folgenden Typen von Rollenzuweisungen erstellen, die weiter unten in diesem Thema detailliert erläutert werden:

  - Reguläre und delegierende Rollenzuweisungen

  - Exklusive Rollenzuweisungen

## Verwalten von Rollenzuweisungen

Beim Ändern von Rollenzuweisungen führen Sie im Allgemeinen Änderungen zwischen Rollengruppen und Rollenzuweisungsrichtlinien durch. Indem Sie Rollenzuweisungen für diese Rollenempfänger hinzufügen, entfernen oder ändern, können Sie steuern, welche Berechtigungen den Administratoren und Benutzern erteilt werden. Damit aktivieren oder deaktivieren Sie im Endeffekt die Verwaltung zugehöriger Funktionen.

Sie können Rollen auch Benutzern oder universellen Sicherheitsgruppen direkt zuweisen. Dies ist eine fortgeschrittenere Aufgabe, mit der Sie genau definieren können, welche Berechtigungen den Benutzern erteilt werden sollen. Diese Möglichkeit bietet Flexibilität, erhöht jedoch auch die Komplexität Ihres Berechtigungsmodells. Wenn ein Benutzer beispielsweise die berufliche Position wechselt, sollten Sie möglicherweise die bisher diesem Benutzer zugewisenen Rollen manuell einem anderen Benutzer zuweisen. Daher sollten Sie Rollengruppen und Rollenzuweisungsrichtlinien verwenden, um Benutzern Berechtigungen zu erteilen. Sie können die Rollen einer Rollengruppe oder Rollenzuweisungsrichtlinie zuweisen und dann einfach Mitglieder der Rollengruppe hinzufügen oder aus ihr entfernen bzw. Rollenzuweisungsrichtlinien nach Bedarf ändern.

Sie können Rollenzuweisungen hinzufügen, entfernen und aktivieren, den Verwaltungsbereich einer vorhandenen Rollenzuweisung ändern sowie Rollenzuweisungen zu anderen Rollenempfängern verschieben. Das Verfahren für das Zuweisen von Rollen zu Rollengruppen, Rollenzuweisungrichtlinien, Benutzern und USGs ist im Wesentlichen für alle Rollenempfänger gleich. Die einzigen Ausnahmen sind:

  - Rollenzuweisungsrichtlinien können nur Endbenutzer-Verwaltungsrollen zugewiesen werden.

  - Rollenzuweisungsrichtlinien können delegierten Rollenzuweisungen nicht zugewiesen werden.

  - Sie können bei der Erstellung einer Rollenzuweisung für Rollenzuweisungsrichtlinien keinen Verwaltungsbereich angeben.

Weitere Informationen zum Verwalten von Rollenzuweisungen finden Sie unter den folgenden Themen:

  - Rollengruppen:
    
      - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - Rollenzuweisungsrichtlinien:
    
      - [Verwalten von Rollenzuweisungsrichtlinien](manage-role-assignment-policies-exchange-2013-help.md)
    
      - [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md)

  - Benutzer und universelle Sicherheitsgruppen:
    
      - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)
    
      - [Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe](remove-a-role-from-a-user-or-usg-exchange-2013-help.md)
    
      - [Ändern einer Rollenzuweisung](change-a-role-assignment-exchange-2013-help.md)
    
      - [Ändern eines Rollenbereichs](change-a-role-scope-exchange-2013-help.md)
    
      - [Delegieren von Rollenzuweisungen](delegate-role-assignments-exchange-2013-help.md)

## Reguläre und delegierende Rollenzuweisungen

Reguläre Rollenzuweisungen ermöglichen es dem Rollenempfänger, auf die Verwaltungsrolleneinträge zuzugreifen, die von der zugeordneten Verwaltungsrolle zur Verfügung gestellt werden. Wenn einem Rollenempfänger mehrere Verwaltungsrollen zugewiesen sind, werden die Verwaltungsrolleneinträge aus den einzelnen Verwaltungsrollen aggregiert und angewendet. Dies bedeutet beispielsweise, dass bei einem Rollenempfänger, dem die Rollen "Transportregeln" und "Journale" zugeordnet wurden, diese Rollen kombiniert werden und dann alle zugehörigen Verwaltungrolleneinträge dem Rollenempfänger zugeordnet werden. Wenn es sich bei dem Rollenempfänger um eine Rollengruppe oder eine Rollenzuweisungsrichtlinie handelt, werden die von den Rollen bereitgestellten Berechtigungen den Benutzern erteilt, die der Rollengruppe oder Rollenzuweisungsrichtlinie zugewiesen sind. Weitere Informationen zu Verwaltungsrollen und Rolleneinträgen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Durch das Delegieren von Rollenzuweisungen wird kein Zugriff auf die Verwaltung von Funktionen erteilt. Das Delegieren von Rollenzuweisungen ermöglicht dem Rollenempfänger, die angegebene Rolle anderen Rollenempfängern zuzuweisen. Wenn es sich bei dem Rollenempfänger um eine Rollengruppe handelt, kann jedes Mitglied der Rollengruppe die Rolle einem anderen Rollenempfänger zuweisen. Standardmäßig kann nur die Rollengruppe "Organisationsverwaltung" anderen Rollenempfängern Rollen zuweisen. Standardmäßig ist ausschließlich der Benutzer, der Exchange 2013 installiert hat, Mitglied der Rollengruppe "Organisationsverwaltung". Sie können jedoch dieser Rollengruppe bei Bedarf andere Benutzer hinzufügen oder andere Rollengruppen erstellen und ihnen delegierende Rollenzuweisungen zuweisen.


> [!NOTE]
> Durch das Delegieren von Rollenzuweisungen können Rollenempfänger Verwaltungsrollen an andere Rollenempfänger delegieren. Dies ermöglicht den Benutzern nicht, Rollengruppen zu delegieren. Weitere Informationen zum Delegieren von Rollengruppen finden Sie unter <A href="understanding-management-role-groups-exchange-2013-help.md">Grundlegendes zu Verwaltungsrollengruppen</A>.



Wenn ein Benutzer in der Lage sein soll, eine Funktion zu verwalten und die Rolle, mit der die Berechtigung zum Verwenden der Funktionen erteilt wird, anderen Benutzern zuzuweisen, weisen Sie Folgendes zu:

1.  Eine reguläre Rollenzuweisung für jede Verwaltungsrolle, mit der der Zugriff auf die zu verwaltenden Funktionen erteilt wird.

2.  Eine delegierende Rollenzuweisung für jede Verwaltungsrolle, für die Sie die Zuweisung zu anderen Rollenempfängern zulassen.

Die regulären Rollenzuweisungen und die delegierenden Rollenzuweisungen, die einem Rollenempfänger zugewiesen sind, müssen nicht identisch sein. Beispielsweise ist ein Benutzer Mitglied einer Rollengruppe, der die Rolle "Transportregeln" mithilfe einer regulären Rollenzuweisung zugewiesen wurde. Dies ermöglicht es dem Benutzer, die Funktion "Transportregeln" zu verwalten. Dem Benutzer wird jedoch keine delegierende Rollenzuweisung für die Rolle "Transportregeln" zugewiesen. Daher kann der Benutzer diese Rolle nicht anderen Benutzern zuweisen. Der Benutzer ist allerdings Mitglied einer Rollengruppe, der die Verwaltungsrolle "Journale" mithilfe einer delegierenden Rollenzuweisung zugewiesen wurde. Die Rollengruppe, in der der Benutzer Mitglied ist, verfügt nicht über eine reguläre Rollenzuweisung für die Rolle "Journale". Da sie aber über eine delegierende Rollenzuweisung verfügt, kann der Benutzer die Rolle anderen Rollenempfängern zuweisen.

## Verwaltungsbereiche

Wenn Sie eine reguläre oder delegierende Verwaltungsrollenzuweisung erstellen, können Sie die Zuweisung mit einem Verwaltungsbereich erstellen, um einzuschränken, welche Objekte der Benutzer bearbeiten kann. Sie können Empfängerbereiche oder Konfigurationsbereiche erstellen. Mit Empfängerbereichen können Sie steuern, wer Postfächer, E-Mail-Benutzer, Verteilergruppen usw. bearbeiten kann. Mit Konfigurationsbereichen können Sie steuern, wer Server und Datenbanken bearbeiten kann.

Mit Empfänger- und Konfigurationsbereichen können Sie die Verwaltung von Server-, Datenbank- oder Empfängerobjekten in Ihrer Organisation aufteilen. Beispielsweise kann ein Empfängerbereich einer Rollenzuweisung hinzugefügt werden, sodass Administratoren in Vancouver nur Empfänger im selben Büro verwalten können. Ein Serverkonfigurationsbereich könnte einer anderen Rollenzuweisung hinzugefügt werden, sodass Administratoren in Sydney nur Server an ihrem Active Directory-Standort verwalten können.

Mithilfe von Bereichen können Sie Benutzergruppen Berechtigungen zuweisen sowie steuern, wo diese Administratoren ihre Verwaltungsaufgaben ausführen dürfen. So können Sie ein Berechtigungsmodell erstellen, das den geografischen oder organisatorischen Grenzen Ihrer Organisation entspricht.

Sie können eine Zuweisung mit einem vordefinierten Bereich erstellen oder der Zuweisung einen benutzerdefinierten Bereich hinzufügen. Vordefinierte Bereiche, die z. B. einen Benutzer auf das eigene Postfach oder die eigenen Verteilergruppen einschränken, können mithilfe von Optionen angewendet werden, die für die Zuweisung zur Verfügung stehen. Alternativ können Sie einen benutzerdefinierten Empfänger- oder Konfigurationsbereich erstellen und der Rollenzuweisung hinzufügen. Mit benutzerdefinierten Bereichen können Sie genauer bestimmen, welche Objekte in den jeweiligen Bereich aufgenommen werden.

Sie können vordefinierte und benutzerdefinierte Bereiche nicht in derselben Zuweisung angeben. Sie können außerdem exklusive und reguläre Bereiche nicht in derselben Zuweisung kombinieren.

Jede Rollenzuweisung kann nur einen Empfängerbereich und einen Konfigurationsbereich aufweisen. Wenn Sie einem Rollenempfänger mehrere Empfängerbereiche oder Konfigurationsbereiche für dieselbe Verwaltungsrolle zuordnen möchten, müssen Sie mehrere Rollenzuweisungen erstellen.

Wenn weder ein benutzerdefinierter noch ein vordefinierter Bereich vorhanden ist, sind Rollenzuweisungen auf die Empfänger- und Konfigurationsbereiche beschränkt, die für die Rolle selbst definiert sind. Diese Bereiche werden als implizite Bereiche bezeichnet. Jede Rollenzuweisung, die keinen vordefinierten oder benutzerdefinierten Bereich aufweist, erbt die impliziten Bereiche von der Rolle, der sie zugeordnet ist.

Weitere Informationen zu Bereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

## Exklusive Rollenzuweisungen

Exklusive Rollenzuweisungen werden erstellt, wenn Sie einen exklusiven Bereich einer Rollenzuweisung zuordnen. Exklusive Bereiche werden wie reguläre Bereiche verwendet und ermöglichen es Rollenempfängern, Empfänger zu verwalten, die dem exklusiven Bereich entsprechen. Anders als bei regulären Bereichen können jedoch alle anderen Rollenempfänger den Empfänger nicht verwalten, auch wenn der Empfänger Bereichen entspricht, die auf ihre Rollenzuweisungen angewendet werden. Dies kann hilfreich sein, wenn Sie die Verwaltung eines Empfängers auf wenige Administratoren einschränken möchten. Nur diese Administratoren können den Empfänger verwalten, und allen anderen Administratoren wird der Zugriff verweigert.

Beachten Sie folgende Beispiele:

  - John ist Führungskraft bei Contoso. Sein Postfach entspricht dem exklusiven Bereich "VIP Users", der der exklusiven Zuweisung "VIP Restricted" zugeordnet ist.

  - Außedem ist Johns Postfach in den regulären Bereich "Redmond Users", eingeschlossen, der der regulären Zuweisung "Redmond Administration" zugeordnet ist.

  - Bill ist Administrator und ist der exklusiven Zuweisung "VIP Restricted" zugeordnet.

  - Chris ist Administrator und ist der regulären Zuweisung "Redmond Administration" zugeordnet.

Da Johns Postfach dem exklusiven Bereich "VIP Users" entspricht, kann nur Bill sein Postfach verwalten. Zwar entspricht Johns Postfach auch dem regulären Bereich "Redmond Users", aber Chris ist nicht der exklusiven Zuweisung "VIP Restricted" zugeordnet. Daher verweigert Exchange Chris die Berechtigung zum Verwalten von Johns Postfach. Damit Chris Johns Postfach verwalten kann, muss Chris eine exklusive Zuweisung zugewiesen werden, die einen exklusiven Bereich umfasst, der Johns Postfach entspricht.

Weitere Informationen finden Sie unter [Grundlegendes zu exklusiven Bereichen](understanding-exclusive-scopes-exchange-2013-help.md).


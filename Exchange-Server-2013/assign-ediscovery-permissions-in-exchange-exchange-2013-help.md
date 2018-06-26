---
title: 'Zuweisen von eDiscovery-Berechtigungen in Exchange: Exchange 2013 Help'
TOCTitle: Zuweisen von eDiscovery-Berechtigungen in Exchange
ms:assetid: 729e09d8-614b-431f-ae04-ae41fb4c628e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298059(v=EXCHG.150)
ms:contentKeyID: 50475996
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zuweisen von eDiscovery-Berechtigungen in Exchange

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-10-02_

Wenn Sie Benutzern die Verwendung der Microsoft Exchange Server 2013 Compliance-eDiscovery ermöglichen möchten, müssen Sie die Benutzer erst dazu autorisieren, indem Sie sie zur Rollengruppe "Discoveryverwaltung" hinzufügen. Mitglieder der Rollengruppe Discoveryverwaltung verfügen über vollständige Postfachzugriffsberechtigungen für das von Exchange-Setup erstellte Discoverypostfach.


> [!WARNING]
> Mitglieder der Rollengruppe "Discoveryverwaltung" können auf vertrauliche Nachrichteninhalte zugreifen. Insbesondere können die Mitglieder die <A href="in-place-ediscovery-exchange-2013-help.md">Compliance-eDiscovery</A> verwenden, um alle Postfächer in Ihrer Exchange-Organisation zu durchsuchen, eine Vorschau für Nachrichten (und andere Postfachelemente) anzuzeigen, Nachrichten in ein Discoverypostfach zu kopieren und die kopierten Nachrichten in eine PST-Datei zu exportieren. In den meisten Organisationen wird diese Berechtigung Mitarbeitern in der Rechts- oder Personalabteilung bzw. für die Einhaltung von Richtlinien zuständigen Mitarbeitern gewährt.<BR>



Weitere Informationen zur Rollengruppe "Discoveryverwaltung" finden Sie unter [Erkennungsverwaltung](discovery-management-exchange-2013-help.md). Informationen zur rollenbasierten Zugriffssteuerung (Role Based Access Control, RBAC) finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Erstellen einer Compliance-eDiscovery-Suche](create-an-in-place-ediscovery-search-exchange-2013-help.md)

  - [Erstellen oder Entfernen eines Compliance-Archivs](create-or-remove-an-in-place-hold-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollengruppen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Standardmäßig weist die Rollengruppe Discoveryverwaltung keine Mitglieder auf. Administratoren mit der Rolle Organisationsverwaltung können ebenfalls keine Discoverysuchen erstellen oder verwalten, ohne zur Rollengruppe Discoveryverwaltung hinzugefügt worden zu sein.

  - In Exchange 2013 können Mitglieder der Rollengruppe Organisationsverwaltung eine [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md) erstellen, um den gesamten Postfachinhalt in ein Archiv zu platzieren. Damit Benutzer jedoch ein abfragebasiertes Compliance-Archiv erstellen können, müssen sie Mitglied der Rollengruppe "Discoveryverwaltung" sein oder es muss ihnen die Rolle "Postfachsuche" zugewiesen sein.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Hinzufügen eines Benutzers zur Rollengruppe "Discoveryverwaltung" mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie in der Listenansicht den Eintrag **Discoveryverwaltung**, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol")

3.  Klicken Sie in **Rollengruppe** unter **Mitglieder** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie in **Mitglieder auswählen** mindestens einen Benutzer aus, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.

5.  Klicken Sie in **Rollengruppe** auf **Speichern**.

## Verwenden der Shell zum Hinzufügen eines Benutzers zur Rollengruppe "Discoveryverwaltung"

In diesem Beispiel wird der Benutzer "Bsuneja" zur Rollengruppe "Discoveryverwaltung" hinzugefügt.

    Add-RoleGroupMember -Identity "Discovery Management" -Member Bsuneja

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Add-RoleGroupMember](https://technet.microsoft.com/de-de/library/dd638207\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob der Benutzer der Rollengruppe "Discoveryverwaltung" hinzugefügt wurde:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Berechtigungen** \> **Administratorrollen**.

2.  Wählen Sie in der Listenansicht den Eintrag **Discoveryverwaltung** aus.

3.  Überprüfen Sie im Detailbereich, ob der Benutzer unter **Mitglieder** aufgeführt wird.

Sie können auch diesen Befehl ausführen, um die Mitglieder der Rollengruppe "Discoveryverwaltung" zu listen.

    Get-RoleGroupMember -Identity "Discovery Management"


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



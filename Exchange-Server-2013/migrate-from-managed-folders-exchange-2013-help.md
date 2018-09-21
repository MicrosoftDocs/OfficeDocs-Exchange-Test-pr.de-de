---
title: 'Migrieren von verwalteten Ordnern: Exchange 2013 Help'
TOCTitle: Migrieren von verwalteten Ordnern
ms:assetid: 6796a79d-501e-4216-9370-77965bc5835d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298032(v=EXCHG.150)
ms:contentKeyID: 52062862
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Migrieren von verwalteten Ordnern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

In Microsoft Exchange Server 2013 erfolgt die Messaging-Datensatzverwaltung (Messaging Records Management, MRM) über die Verwendung von Aufbewahrungstags und Aufbewahrungsrichtlinien. Eine Aufbewahrungsrichtlinie ist eine Gruppe von Aufbewahrungstags, die auf ein Postfach angewendet werden können. Weitere Informationen finden Sie unter [Aufbewahrungstags und Aufbewahrungsrichtlinien](https://technet.microsoft.com/de-de/library/Dd297955(v=EXCHG.150)). Verwaltete Ordner, die in Exchange Server 2007 eingeführte Technologie für die Messaging-Datensatzverwaltung, werden nicht unterstützt.

Ein Postfach, auf das eine Postfachrichtlinie für verwalteten Ordner angewendet wird, kann für die Verwendung einer Aufbewahrungsrichtlinie migriert werden. Dazu müssen Sie Aufbewahrungstags erstellen, die den verwalteten Ordnern entsprechen, die mit der Postfachrichtlinie für verwalteten Ordner des Benutzers verknüpft sind.


> [!IMPORTANT]
> Bevor Sie verwaltete Ordner in Ihrer Produktionsumgebung in Aufbewahrungsrichtlinien migrieren, sollten Sie den Prozess in einer Testumgebung testen.




> [!TIP]
> Sie können für Postfächer eine Aufbewahrungszeit aktivieren, um die Verarbeitung von Aufbewahrungsrichtlinien und Postfachrichtlinien für verwaltete Ordner zu unterbrechen. Das Aktivieren einer Aufbewahrungszeit für Postfächer kann in Migrationsszenarien hilfreich sein, um das Löschen von Nachrichten oder deren Verschiebung in ein Archiv zu vermeiden, bis neue Richtlinieneinstellungen für Testpostfächer oder eine kleine Anzahl von Produktionspostfächern getestet wurden. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold">Anhalten der Aufbewahrungszeit für ein Postfach</A>.



Weitere Verwaltungsaufgaben im Zusammenhang mit MRM finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## Vergleichen von Aufbewahrungstags und verwalteten Ordnern

Anders als verwaltete Ordner, bei denen Benutzer Elemente auf der Grundlage von Aufbewahrungseinstellungen in einen verwalteten Ordner verschieben müssen, können Aufbewahrungstags auf einen Ordner oder ein einzelnes Element im Postfach angewendet werden. Dieser Prozess hat minimale Auswirkungen auf den Workflow und die E-Mail-Organisationsmethoden des Benutzers. Wenn auf einen Ordner Aufbewahrungstags angewendet werden, werden die Aufbewahrungseinstellungen an alle Elemente in diesem Ordner vererbt. Benutzer können weitere Aufbewahrungseinstellungen angeben, indem sie verschiedene Aufbewahrungstags auf einzelne Elemente im Ordner anwenden.

Verwaltete Ordner unterstützen unterschiedliche Einstellungen für verwaltete Inhalte für einen Ordner, die alle eine andere Nachrichtenklasse besitzen (z. B. E-Mail-Elemente oder Kalendereinträge). Aufbewahrungstags erfordern kein separates Einstellungsobjekt für verwaltete Inhalte, da die Aufbewahrungseinstellungen in den Eigenschaften des Tags angegeben sind. Nicht unterstützt wird das Erstellen von Aufbewahrungstags für bestimmte Nachrichtenklassen mit Ausnahme eines Standardrichtlinientags für Voicemailnachrichten. Außerdem steht für Aufbewahrungstags die Journalfunktion nicht zur Verfügung, die vom Assistenten für verwaltete Ordner übernommen wird.


> [!NOTE]
> Journalregeln, die zum Senden von Kopien von Nachrichten mit einem Journalbericht an ein Journalpostfach dienen, werden in der Transportpipeline durch den Journal-Agent erzwungen und sind von der Messaging-Datensatzverwaltung unabhängig. Weitere Informationen finden Sie unter <A href="journaling-exchange-2013-help.md">Journale</A>.



Die folgende Tabelle zeigt einen Vergleich der verfügbaren MRM-Funktionalität bei Verwenden von Aufbewahrungstags bzw. verwalteten Ordnern.

### Aufbewahrungstags und verwaltete Ordner

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Funktionalität</th>
<th>Aufbewahrungstags</th>
<th>Verwaltete Ordner</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Angeben von Aufbewahrungseinstellungen für Standardordner (z. B. Posteingang)</p></td>
<td><p>Verwenden von Aufbewahrungsrichtlinientags</p></td>
<td><p>Verwenden von verwalteten Standardordnern</p></td>
</tr>
<tr class="even">
<td><p>Angeben der Aufbewahrungseinstellungen für das gesamte Postfach</p></td>
<td><p>Verwenden eines Standardrichtlinientags</p></td>
<td><p>Verwenden von verwalteten Standardordnern</p></td>
</tr>
<tr class="odd">
<td><p>Verwenden von Aufbewahrungseinstellungen für benutzerdefinierte Ordner</p></td>
<td><p>Verwenden von persönlichen Tags</p></td>
<td><p>Verwenden von verwalteten benutzerdefinierten Ordnern</p></td>
</tr>
<tr class="even">
<td><p>Einstellungen für verwaltete Inhalte erforderlich</p></td>
<td><p>Nein (Aufbewahrungseinstellungen sind in einem Aufbewahrungstag enthalten)</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Verwenden von Aufbewahrungseinstellungen für unterschiedliche Nachrichtenklassen (z. B. E-Mail-Nachrichten, Voicemail oder Kalendereinträge)</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Unterstützung für das Verschieben ins Archiv, um Elemente in das Archivpostfach des Benutzers zu verschieben</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Unterstützung für das Verschieben in einen verwalteten Ordner</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Zulassen der Journalerstellung mithilfe des Assistenten für verwalteten Ordner</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Auf Benutzer angewendete Richtlinie</p></td>
<td><p>Aufbewahrungsrichtlinie</p></td>
<td><p>Postfachrichtlinie für verwalteten Ordner</p></td>
</tr>
<tr class="even">
<td><p>Maximale Anzahl von Richtlinien, die auf einen Postfachbenutzer angewendet werden können</p></td>
<td><p>1</p></td>
<td><p>1</p></td>
</tr>
<tr class="odd">
<td><p>Verarbeitet vom Assistenten für verwalteten Ordner</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Clientunterstützung</p></td>
<td><p>Microsoft Outlook 2010 und Office Outlook Web App</p></td>
<td><p>Outlook 2010, Office Outlook 2007 und Outlook Web App</p></td>
</tr>
</tbody>
</table>


## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 20 Minuten.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Die Exchange-Verwaltungskonsole kann nicht zum Erstellen von Aufbewahrungstags basierend auf Aufbewahrungsrichtlinien verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Migrieren von Postfachbenutzern aus verwalteten Ordnern

Im Folgenden handelt es sich um allgemeine Schritte zum Migrieren von Benutzern aus dieser Postfachrichtlinie für verwalteten Ordner in eine Aufbewahrungsrichtlinie. Jeder Schritt wird später in diesem Thema ausführlich erläutert:

1.  Erfassen Sie Informationen zu Postfachrichtlinien für verwaltete Ordner, die für alle Exchange 2010- und Exchange 2007-Postfächer gelten, zu verwalteten Ordnern in jeder Richtlinie und Einstellungen für verwaltete Inhalte für jeden verwalteten Ordner. Zum Sammeln dieser Informationen können Sie die Exchange-Verwaltungskonsole oder Shell auf einem Server mit Exchange 2010 oder Exchange 2007 verwenden.

2.  Erstellen Sie Aufbewahrungstags für die Migration.

3.  Erstellen Sie eine Aufbewahrungsrichtlinie, und verknüpfen Sie die neu erstellten Aufbewahrungstags mit der Richtlinie.

4.  Entfernen Sie die Postfachrichtlinie für verwaltete Ordner, und wenden Sie anschließend die Aufbewahrungsrichtlinie auf die Benutzerpostfächer an.
    

    > [!IMPORTANT]
    > Wenn Sie die Aufbewahrungsrichtlinie auf einen Benutzer angewendet haben und der Assistent für verwaltete Ordner ausgeführt wurde, können die verwalteten Ordner im Postfach des Benutzers nicht mehr verwaltet werden.



In den folgenden Verfahren wird auf Contoso-Postfächer eine Postfachrichtlinie für verwalteten Ordner angewendet, die folgende verwaltete Ordner enthält.

### Verwaltete Ordner für Contoso

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwalteter Ordner</th>
<th>Einstellungen für verwaltete Inhalte</th>
<th>Aufbewahrung aktiviert</th>
<th>Aufbewahrungszeitraum</th>
<th>Aufbewahrungsaktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Corp-DeletedItems</p></td>
<td><p>CS-Corp-DeletedItems</p></td>
<td><p>Ja</p></td>
<td><p>30 Tage</p></td>
<td><p>Löschen und Wiederherstellung zulassen</p></td>
</tr>
<tr class="even">
<td><p>Corp-SentItems</p></td>
<td><p>CS-Corp-SentItems</p></td>
<td><p>Ja</p></td>
<td><p>1.825 Tage</p></td>
<td><p>In Ordner &quot;Gelöschte Objekte&quot; verschieben</p></td>
</tr>
<tr class="odd">
<td><p>Corp-JunkMail</p></td>
<td><p>CS-Corp-JunkMail</p></td>
<td><p>Ja</p></td>
<td><p>30 Tage</p></td>
<td><p>Endgültig löschen</p></td>
</tr>
<tr class="even">
<td><p>Corp-EntireMailbox</p></td>
<td><p>CS-Corp-EntireMailbox</p></td>
<td><p>Ja</p></td>
<td><p>365 Tage</p></td>
<td><p>In Ordner &quot;Gelöschte Objekte&quot; verschieben</p></td>
</tr>
<tr class="odd">
<td><p>30 Tage</p></td>
<td><p>CS-30Days</p></td>
<td><p>Ja</p></td>
<td><p>30 Tage</p></td>
<td><p>In Ordner &quot;Gelöschte Objekte&quot; verschieben</p></td>
</tr>
<tr class="even">
<td><p>5 Jahre</p></td>
<td><p>CS-5Years</p></td>
<td><p>Ja</p></td>
<td><p>1.825 Tage</p></td>
<td><p>In Ordner &quot;Gelöschte Objekte&quot; verschieben</p></td>
</tr>
<tr class="odd">
<td><p>Läuft nie ab</p></td>
<td><p>CS-NeverExpire</p></td>
<td><p>Nein</p></td>
<td><p>365 Tage</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen Sie Aufbewahrungstags für die Migration

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

Es gibt zwei Methoden, die Sie für diesen Schritt verwenden können:

  - **Erstellen von Aufbewahrungstags basierend auf den verwalteten Ordnern und ihren dazugehörigen Einstellungen für verwaltete Inhalte**   Bei dieser Methode verwenden Sie das Cmdlet **New-RetentionPolicyTag** mit dem Parameter *ManagedFolderToUpgrade*. Wenn Sie diesen Parameter angeben, wird das entsprechende Aufbewahrungstag automatisch auf den verwalteten Ordner angewendet.
    

    > [!IMPORTANT]
    > Wenn der zu portierende verwaltete Ordner über mehrere Einstellungen für verwaltete Inhalte für die verschiedenen Nachrichtenklassen verfügt, wird nur ein Aufbewahrungstag erstellt. Dabei wird als Aufbewahrungszeitraum für das portierte Tag unabhängig von der Nachrichtenklasse der Einstellungen für verwaltete Inhalte der längste Aufbewahrungszeitraum aller Einstellungen für verwaltete Inhalte verwendet.<BR>Im Folgenden sind beispielsweise die Einstellungen für verwaltete Inhalte für den verwalteten Ordner "Corp-DeletedItems" aufgeführt.



  - **Erstellen von Aufbewahrungstags durch manuelles Angeben der Aufbewahrungseinstellungen**   Bei dieser Methode verwenden Sie das Cmdlet **New-RetentionPolicyTag** ohne den Parameter *ManagedFolderToUpgrade*. Wenn Sie diesen Parameter nicht angeben, werden alle Aufbewahrungsrichtlinientags, die Sie der Richtlinie hinzufügen, auf die Standardordner und das Standardrichtlinientag auf das gesamte Postfach angewendet. Persönliche Tags, die Sie der Richtlinie hinzufügen, werden jedoch nicht automatisch auf die verwalteten Ordner angewendet.


> [!NOTE]
> Bei einer heterogenen Umgebung mit Exchange 2013- und Exchange 2010-Servern können Sie den <STRONG>Assistenten zum Portieren verwalteter Ordner</STRONG> in der Exchange-Verwaltungskonsole auf einem Exchange 2010-Server ausführen, um verwaltete Ordner und die dazugehörigen Einstellungen für verwaltete Inhalte einfach in Aufbewahrungstags zu portieren.



**Erstellen von Aufbewahrungstags auf der Grundlage verwalteter Ordner**

In diesem Beispiel werden Aufbewahrungstags auf der Grundlage der entsprechenden Einstellungen für verwaltete Inhalte in der Contoso-Postfachrichtlinie für verwalteten Ordner erstellt.

    New-RetentionPolicyTag Corp-DeletedItems -ManagedFolderToUpgrade Corp-DeletedItems
    New-RetentionPolicyTag Corp-SentItems -ManagedFolderToUpgrade Corp-SentItems
    New-RetentionPolicyTag Corp-JunkMail -ManagedFolderToUpgrade Corp-JunkMail
    New-RetentionPolicyTag Corp-EntireMailbox -ManagedFolderToUpgrade Corp-EntireMailbox
    New-RetentionPolicyTag 30Days -ManagedFolderToUpgrade 30Days
    New-RetentionPolicyTag 5Years -ManagedFolderToUpgrade 5Years
    New-RetentionPolicyTag NeverExpire -ManagedFolderToUpgrade NeverExpire

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd335226\(v=exchg.150\)).

**Manuelles Erstellen von Aufbewahrungstags**


> [!NOTE]
> Über die Exchange-Verwaltungskonsole können Sie Aufbewahrungstags auch (nicht auf Einstellungen in verwalteten Ordnern basierend) manuell erstellen. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy">Erstellen einer Aufbewahrungsrichtlinie</A>.



In diesem Beispiel werden Aufbewahrungstags auf der Grundlage der verwalteten Ordner und entsprechenden Einstellungen für verwaltete Inhalte in der Contoso-Postfachrichtlinie für verwalteten Ordner erstellt. Die Aufbewahrungseinstellungen werden manuell ohne Verwendung des Parameters *ManagedFolderToUpgrade* angegeben.

    New-RetentionPolicyTag Corp-DeletedItems -Type DeletedItems -RetentionEnabled $true -AgeLimitForRetention 30 -RetentionAction DeleteAndAllowRecovery
    New-RetentionPolicyTag Corp-SentItems -Type SentItems -RetentionEnabled $true -AgeLimitforRetention 1825 -RetentionAction MoveToDeletedItems
    New-RetentionPolicyTag Corp-JunkMail -Type JunkMail -RetentionEnabled $true -AgeLimitforRetention 30 -RetentionAction PermanentlyDelete
    New-RetentionPolicyTag Corp-EntireMailbox -Type All -RetentionEnabled $true -AgeLimitForRetention 365 -RetentionAction MoveToDeletedItems
    New-RetentionPolicyTag 30Days -Type Personal -RetentionEnabled $true -AgeLimitForRetention 30 -RetentionAction MoveToDeletedItems
    New-RetentionPolicyTag 5Years -Type Personal -RetentionEnabled $true -AgeLimitForRetention 1825 -RetentionAction MoveToDeletedItems
    New-RetentionPolicyTag NeverExpire -Type Personal -RetentionEnabled $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd335226\(v=exchg.150\)).

## Schritt 2: Erstellen Sie eine Aufbewahrungsrichtlinie

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).


> [!NOTE]
> In der Exchange-Verwaltungskonsole können Sie auch eine Aufbewahrungsrichtlinie erstellen und Aufbewahrungstags der Richtlinie hinzufügen. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/messaging-records-management/create-a-retention-policy">Erstellen einer Aufbewahrungsrichtlinie</A>.



In diesem Beispiel wird die Aufbewahrungsrichtlinie "RC-Corp" erstellt, und die neu erstellten Aufbewahrungstags werden mit der Richtlinie verknüpft.

    New-RetentionPolicy RP-Corp -RetentionPolicyTagLinks Corp-DeletedItems,Corp-SentItems,Corp-JunkMail,Corp-EntireMailbox,30Days,NeverExpire

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd297970\(v=exchg.150\)).

## Schritt 3: Entfernen der Postfachrichtlinie für verwaltete Ordner aus Benutzerpostfächern

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Anwenden von Aufbewahrungsrichtlinien" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

In diesem Beispiel werden die Postfachrichtlinie für verwaltete Ordner sowie alle verwalteten Ordner aus dem Postfach von Ken Kwok entfernt. Verwaltete Ordner, die Nachrichten enthalten, werden nicht entfernt.

```powershell
Set-Mailbox -Identity Kwok -RemoveManagedFolderAndPolicy RP-Corp
```

## Schritt 4: Wenden Sie die Aufbewahrungsrichtlinie auf Benutzerpostfächer an

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Anwenden von Aufbewahrungsrichtlinien" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).


> [!NOTE]
> Über die Exchange-Verwaltungskonsole können Sie Benutzern eine Aufbewahrungsrichtlinie zuordnen. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/security-and-compliance/messaging-records-management/apply-retention-policy">Anwenden einer Aufbewahrungsrichtlinie auf Postfächer</A>.



In diesem Beispiel wird die neu erstellte Aufbewahrungsrichtlinie "RP-Corp" auf den Postfachbenutzer "Ken Kwok" angewendet.

```powershell
Set-Mailbox -Identity Kwok -RetentionPolicy RP-Corp
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass diese Aufgabe erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration von verwalteten Ordnern zu Aufbewahrungsrichtlinien erfolgt ist:

  - Erstellen Sie einen Bericht aller Benutzerpostfächer und der ihnen zugeordneten Aufbewahrungsrichtlinie.
    
    Dieser Befehl ruft die für alle Postfächer in einer Organisation geltende Aufbewahrungsrichtlinie und den Aufbewahrungsstatus ab.
    
        Get-Mailbox -ResultSize unlimited -Filter {Name -NotLike "DiscoverySearch*�?} | Format-Table Name,RetentionPolicy,RetentionHoldEnabled -Auto

  - Nachdem der Assistenten für verwaltete Ordner ein Postfach mit einer Aufbewahrungsrichtlinie verarbeitet hat, rufen Sie mit dem Cmdlet [Get-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd298009\(v=exchg.150\)) die im Benutzerpostfach bereitgestellten Aufbewahrungstags ab.
    
    Dieser Befehl ruft die Aufbewahrungstags ab, die dem Postfach von April Stewart zugeordnet sind.
    
    ```powershell
Get-RetentionPolicyTag -Mailbox astewart
```


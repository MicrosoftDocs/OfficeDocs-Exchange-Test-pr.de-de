---
title: 'Hinzufügen und Entfernen von Aufbewahrungstags in Aufbewahrungsrichtlinie'
TOCTitle: Hinzufügen von Aufbewahrungstags zu oder Entfernen von Aufbewahrungstags aus einer Aufbewahrungsrichtlinie
ms:assetid: 3a5196ce-2764-453d-9bc1-5ec22d06b40d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd362328(v=EXCHG.150)
ms:contentKeyID: 50475499
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinzufügen von Aufbewahrungstags zu oder Entfernen von Aufbewahrungstags aus einer Aufbewahrungsrichtlinie

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-02_

Sie können Aufbewahrungstags zu einer Aufbewahrungsrichtlinie hinzufügen, wenn die Richtlinie erstellt wird, oder zu einem beliebigen späteren Zeitpunkt. Genaue Anweisungen zum Erstellen einer Aufbewahrungsrichtlinie, einschließlich des gleichzeitigen Hinzufügens von Aufbewahrungstags, finden Sie unter [Erstellen einer Aufbewahrungsrichtlinie](create-a-retention-policy-exchange-2013-help.md).

Eine Aufbewahrungsrichtlinie kann die folgenden Aufbewahrungstags enthalten:

  - Ein oder mehrere Aufbewahrungsrichtlinientags (Retention Policy Tag, RPT) für unterstützte Standardordner

  - Ein Standardrichtlinientag (Default Policy Tag, DPT) mit der Aktion **In Archiv verschieben**

  - Ein Standardrichtlinientag mit der Aktion **Löschen und Wiederherstellung zulassen** oder mit der Aktion **Endgültig löschen**

  - Ein Standardrichtlinientag für Voicemail

  - Eine beliebige Anzahl von persönlichen Tags

Weitere Informationen zu Aufbewahrungstags finden Sie unter [Aufbewahrungstags und Aufbewahrungsrichtlinien](retention-tags-and-retention-policies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Aufbewahrungstags werden nicht auf ein Postfach angewendet, bis sie mit einer Aufbewahrungsrichtlinie verknüpft werden und der Assistent für verwaltete Ordner das Postfach verarbeitet. Informationen zum Starten des Assistenten für verwaltete Ordner, damit er ein Postfach verarbeitet, finden Sie unter [Konfigurieren des Assistenten für verwaltete Ordner](configure-the-managed-folder-assistant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden von EAC zum Hinzufügen oder Entfernen von Aufbewahrungstags

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Aufbewahrungsrichtlinien**.

2.  Wählen Sie in der Listenansicht die Aufbewahrungsrichtlinie aus, der Sie Aufbewahrungstags hinzufügen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Verwenden Sie im Abschnitt **Aufbewahrungsrichtlinie** die folgenden Einstellungen:
    
      - **Hinzufügen** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)")   Klicken Sie auf diese Schaltfläche, um der Richtlinie ein Aufbewahrungstag hinzuzufügen.
    
      - **Entfernen** ![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)")   Wählen Sie ein Tag aus der Liste aus, und klicken Sie auf diese Schaltfläche, um das Tag aus der Richtlinie zu entfernen.

## Verwenden der Shell zum Hinzufügen oder Entfernen von Aufbewahrungstags

In diesem Beispiel werden die Aufbewahrungstags "VPs-Default", "VPs-Inbox" und "VPs-DeletedItems" der Aufbewahrungsrichtlinie "RetPolicy-VPs" hinzugefügt, mit der noch keine Aufbewahrungstags verknüpft sind.


> [!WARNING]
> Wenn mit der Richtlinie bereits Aufbewahrungstags verknüpft sind, werden die vorhandenen Tags durch diesen Befehl ersetzt.



    Set-RetentionPolicy -Identity "RetPolicy-VPs" -RetentionPolicyTagLinks "VPs-Default","VPs-Inbox","VPs-DeletedItems"

In diesem Beispiel wird das Aufbewahrungstag "VPs-DeletedItems" mit der Aufbewahrungsrichtlinie "RetPolicy-VPs" verknüpft, mit der bereits andere Aufbewahrungstags verknüpft sind.

    $TagList = (Get-RetentionPolicy "RetPolicy-VPs").RetentionPolicyTagLinks
    $TagList.Add((Get-RetentionPolicyTag 'VPs-DeletedItems').DistinguishedName)
    Set-RetentionPolicy "RetPolicy-VPs" -RetentionPolicyTagLinks $TagList

In diesem Beispiel wird das Aufbewahrungstag "VPs-Inbox" aus der Aufbewahrungsrichtlinie "RetPolicy-VPs" entfernt.

    $TagList = (Get-RetentionPolicy "RetPolicy-VPs").RetentionPolicyTagLinks
    $TagList.Remove((Get-RetentionPolicyTag 'VPs-Inbox').DistinguishedName)
    Set-RetentionPolicy "RetPolicy-VPs" -RetentionPolicyTagLinks $TagList

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd335196\(v=exchg.150\)) und [Get-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd298086\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Überprüfen Sie mit dem Cmdlet [Get-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd298086\(v=exchg.150\)) die Eigenschaft *RetentionPolicyTagLinks*, um sicherzustellen, dass das Aufbewahrungstag der Aufbewahrungsrichtlinie ordnungsgemäß hinzugefügt oder aus dieser entfernt wurde.

In diesem Beispiel wird das Cmdlet **Get-RetentionPolicy** dazu verwendet, Aufbewahrungstags abzurufen, die der Richtlinie "Default MRM" hinzugefügt wurden. Die Ausgabe wird dann mittels Pipe an das Cmdlet **Format-Table** umgeleitet, um nur die Namenseigenschaft für jedes Tag auszugeben.

    (Get-RetentionPolicy "Default MRM Policy").RetentionPolicyTagLinks | Format-Table name


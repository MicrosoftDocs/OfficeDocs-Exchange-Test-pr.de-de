---
title: 'Erstellen einer Aufbewahrungsrichtlinie: Exchange 2013 Help'
TOCTitle: Erstellen einer Aufbewahrungsrichtlinie
ms:assetid: d8806c98-fea5-492f-906d-f514e25361b2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150573(v=EXCHG.150)
ms:contentKeyID: 50476835
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Aufbewahrungsrichtlinie

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In Exchange Online und Exchange Server 2013 können Sie den E-Mail-Lebenszyklus mithilfe von Aufbewahrungsrichtlinien verwalten. Aufbewahrungsrichtlinien werden angewendet, indem Aufbewahrungstags erstellt und zu einer Aufbewahrungsrichtlinie hinzugefügt werden, die auf Postfachbenutzer angewendet wird.

Sehen Sie sich das [Video](https://go.microsoft.com/fwlink/?linkid=825854) an, in dem gezeigt wird, wie eine Aufbewahrungsrichtlinie erstellt und auf ein Postfach in Exchange Online angewendet wird.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Aufbewahrungsrichtlinien finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 30 Minuten.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Postfächer, auf die Sie Aufbewahrungsrichtlinien anwenden möchten, müssen sich auf Servern mit Exchange Server 2010 oder höher befinden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen eines Aufbewahrungstags

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

**Erstellen eines Aufbewahrungstags mithilfe der Exchange-Verwaltungskonsole**

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Aufbewahrungstags**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)")

2.  Wählen Sie eine der folgenden Optionen aus:
    
      - **Automatisch auf gesamtes Postfach angewendet (Standard)**   Wählen Sie diese Option, wenn Sie ein Standardrichtlinientag erstellen möchten. Mithilfe von Standardrichtlinientags können Sie eine Standardlöschrichtlinie und Standardarchivrichtlinie erstellen, die für alle Elemente im Postfach gilt.
        

        > [!NOTE]
        > Ein Standardrichtlinientag zum Löschen von Voicemailelementen kann nicht in der Exchange-Verwaltungskonsole erstellt werden. Einzelheiten zum Erstellen eines Standardrichtlinientags zum Löschen von Voicemailelementen finden Sie im folgenden Shell-Beispiel.

    
      - **Automatisch auf bestimmten Ordner angewendet**   Wählen Sie diese Option, wenn Sie ein Aufbewahrungsrichtlinientag für einen Standardordner wie **Posteingang** oder **Gelöschte Elemente** erstellen möchten.
        

        > [!NOTE]
        > Aufbewahrungsrichtlinientags können nur mit der Aktion <STRONG>Löschen und Wiederherstellung zulassen</STRONG> oder <STRONG>Endgültig löschen</STRONG> erstellt werden.

    
      - **Von Benutzern auf Elemente und Ordner angewendet (Persönlich)**   Wählen Sie diese Option, um persönliche Tags zu erstellen. Diese Tags ermöglichten Benutzern von Outlook und Outlook Web App das Anwenden von Archivierungs- oder Löscheinstellungen auf eine Nachricht oder Ordner, die sich von den Einstellungen unterscheiden, die für den übergeordneten Ordner oder das gesamte Postfach gelten.

3.  Titel und Optionen auf der Seite **Neues Aufbewahrungstag** sind je nach gewähltem Tagtyp unterschiedlich. Füllen Sie folgende Felder aus:
    
      - **Name** Geben Sie einen Namen für das Aufbewahrungstag ein. Der Tagname dient nur zu Anzeigezwecken und hat keine Auswirkungen auf den Ordner oder das Element, auf den bzw. das ein Tag angewendet wird. Berücksichtigen Sie, dass persönliche Tags, die Sie für Benutzer bereitstellen, in Outlook und Outlook Web App verfügbar sind.
    
      - **Dieses Tag auf folgenden Standardordner anwenden**   Diese Option ist nur verfügbar, wenn Sie **Automatisch auf bestimmten Ordner angewendet** ausgewählt haben.
    
      - **Aufbewahrungsaktion**   Wählen Sie eine der folgenden Aktionen aus, die ausgeführt werden soll, wenn der Aufbewahrungszeitraum des Elements abläuft.
        
          - **Löschen und Wiederherstellung zulassen**   Wählen Sie diese Aktion aus, um Elemente zu löschen, Benutzern aber die Möglichkeit zu bieten, diese Elemente mithilfe der Option **Gelöschte Elemente wiederherstellen** in Outlook oder Outlook Web App wiederherzustellen. Elemente werden aufbewahrt, bis die Aufbewahrungszeit für gelöschte Elemente, die für die Postfachdatenbank oder den Postfachbenutzer konfiguriert ist, erreicht ist.
        
          - **Endgültig löschen** Wählen Sie diese Option aus, um das Element endgültig aus der Postfachdatenbank zu löschen.
            

            > [!IMPORTANT]
            > Postfächer oder Elemente, die der Compliance-Archivierung bzw. dem Beweissicherungsverfahren unterliegen, werden aufbewahrt und bei Compliance-eDiscovery-Suchvorgängen zurückgegeben. Weitere Informationen finden Sie unter <A href="in-place-hold-and-litigation-hold-exchange-2013-help.md">In-Place Hold and Litigation Hold</A>.

        
          - **In Archiv verschieben**   Diese Aktion ist nur verfügbar, wenn Sie ein Standardrichtlinientag oder persönliches Tag erstellen. Wählen Sie diese Aktion zum Verschieben von Elementen in das Compliance-Archiv des Benutzers.
    
      - **Aufbewahrungszeitraum** Wählen Sie eine der folgenden Optionen aus:
        
          - **Nie**   Wählen Sie diese Option, damit Elemente nie gelöscht oder in das Archiv verschoben werden.
        
          - **Wenn das Element das folgende Alter (in Tagen) erreicht**   Wählen Sie diese Option aus, und geben Sie die Anzahl von Tagen ein, die Elemente aufbewahrt werden sollen, bevor sie verschoben oder gelöscht werden. Der Aufbewahrungszeitraum für alle unterstützten Elemente – ausgenommen Kalender- und Aufgabenelemente – wird ab dem Datum berechnet, an dem ein Element empfangen oder erstellt wird. Der Aufbewahrungszeitraum für Kalender- und Aufgabenelemente wird ab dem Enddatum berechnet.
    
      - **Kommentar**   Geben Sie in dieses optionale Feld administrative Hinweise oder Kommentare ein. Das Feld wird Benutzern nicht angezeigt.

**Erstellen eines Aufbewahrungstags mithilfe der Shell**

Verwenden Sie das Cmdlet **New-RetentionPolicyTag**, um ein Aufbewahrungstag zu erstellen. Unterschiedliche im Cmdlet verfügbare Optionen ermöglichen Ihnen das Erstellen verschiedener Typen von Aufbewahrungstags. Geben Sie den Parameter *Type* an, um ein Standardrichtlinientag (`All`), ein Aufbewahrungsrichtlinientag (geben Sie einen Standardordnertyp wie `Inbox` an) oder ein persönliches Tag (`Personal`) zu erstellen.

Dieser Befehl erstellt ein Standardrichtlinientag zum Löschen aller Nachrichten im Postfach nach 7 Jahren (2556 Tagen).

    New-RetentionPolicyTag -Name "DPT-Corp-Delete" -Type All -AgeLimitForRetention 2556 -RetentionAction DeleteAndAllowRecovery

Dieser Befehl erstellt ein Standardrichtlinientag zum Verschieben aller Nachrichten in das Compliance-Archiv in 2 Jahren (730 Tagen).

    New-RetentionPolicyTag -Name "DPT-Corp-Move" -Type All -AgeLimitForRetention 730 -RetentionAction MoveToArchive

Dieser Befehl erstellt ein Standardrichtlinientag zum Löschen von Voicemailnachrichten nach 20 Tagen.

    New-RetentionPolicyTag -Name "DPT-Corp-Voicemail" -Type All -MessageClass Voicemail -AgeLimitForRetention 20 -RetentionAction DeleteAndAllowRecovery

Dieser Befehl erstellt ein Aufbewahrungsrichtlinientag zum endgültigen Löschen der Nachrichten im Junk-E-Mail-Ordner nach 30 Tagen.

    New-RetentionPolicyTag -Name "RPT-Corp-JunkMail" -Type JunkEmail -AgeLimitForRetention 30 -RetentionAction PermanentlyDelete

Dieser Befehl erstellt ein persönliches Tag, bei dessen Anwendung Nachrichten nie gelöscht werden.

    New-RetentionPolicyTag -Name "Never Delete" -Type Personal -RetentionAction DeleteAndAllowRecovery -RetentionEnabled $false

## Schritt 2: Erstellen Sie eine Aufbewahrungsrichtlinie

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

**Erstellen einer Aufbewahrungsrichtlinie mithilfe der Exchange-Verwaltungskonsole**

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Aufbewahrungsrichtlinien**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)")

2.  Füllen Sie unter **Neue Aufbewahrungsrichtlinie** die folgenden Felder aus:
    
      - **Name**   Geben Sie einen Namen für die Aufbewahrungsrichtlinie ein.
    
      - **Aufbewahrungstags**   Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Tags auszuwählen, die Sie dieser Aufbewahrungsrichtlinie hinzufügen möchten.
        
        Eine Aufbewahrungsrichtlinie kann die folgenden Tags enthalten:
        
          - Ein Standardrichtlinientag mit der Aktion **In Archiv verschieben**
        
          - Ein Standardrichtlinientag mit der Aktion **Löschen und Wiederherstellung zulassen** oder **Endgültig löschen**
        
          - Ein Standardrichtlinientag für Voicemailnachrichten mit der Aktion **Löschen und Wiederherstellung zulassen** oder **Endgültig löschen**
        
          - Ein Aufbewahrungsrichtlinientag pro Standardordner, z. B. **Posteingang**, zum Löschen von Elementen
        
          - Eine beliebige Anzahl von persönlichen Tags
            

            > [!NOTE]
            > Sie können einer Aufbewahrungsrichtlinie zwar beliebig viele persönliche Tags hinzufügen; viele persönliche Tags mit unterschiedlichen Aufbewahrungseinstellungen können Benutzer aber zusätzlich verwirren. Es wird empfohlen, mit einer Aufbewahrungsrichtlinie nicht mehr als 10&nbsp;persönliche Tags zu verknüpfen.

        
        Sie können eine Aufbewahrungsrichtlinie erstellen, ohne dieser Aufbewahrungstags hinzuzufügen, doch Elemente im Postfach, für das die Richtlinie gilt, werden nicht verschoben oder gelöscht. Sie können einer Aufbewahrungsrichtlinie auch nach ihrer Erstellung Aufbewahrungstags hinzufügen bzw. aus dieser entfernen.

**Erstellen einer Aufbewahrungsrichtlinie mithilfe der Shell**

In diesem Beispiel wird die Aufbewahrungsrichtlinie "RetentionPolicy-Corp" erstellt und der Parameter *RetentionPolicyTagLinks* verwendet, um der Richtlinie fünf Tags zuzuordnen.

    New-RetentionPolicy "RetentionPolicy-Corp"  -RetentionPolicyTagLinks "DPT-Corp-Delete","DPT-Corp-Move","DPT-Corp-Voicemail","RPT-Corp-JunkMail","Never Delete"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd297970\(v=exchg.150\)).

## Schritt 3: Anwenden einer Aufbewahrungsrichtlinie auf Postfachbenutzer

Nachdem Sie eine Aufbewahrungsrichtlinie erstellt haben, wenden Sie sie auf Postfachbenutzer an. Sie können auf mehrere Benutzer unterschiedliche Aufbewahrungsrichtlinien anwenden. Ausführliche Anweisungen finden Sie unter [Anwenden einer Aufbewahrungsrichtlinie auf Postfächer](apply-a-retention-policy-to-mailboxes-exchange-2013-help.md).

## Woher wissen Sie, dass diese Aufgabe erfolgreich war?

Nachdem Sie Aufbewahrungstags erstellt, diese einer Aufbewahrungsrichtlinie hinzugefügt und die Richtlinie auf einen Postfachbenutzer angewendet haben, werden Nachrichten bei der nächsten Verarbeitung des Postfachs basierend auf den in den Aufbewahrungstags konfigurierten Einstellungen verschoben oder gelöscht.

Gehen Sie wie folgt vor, um sich zu vergewissern, dass die Aufbewahrungsrichtlinie angewendet wurde:

1.  Führen Sie folgenden Shell-Befehl aus, um den MRM-Assistenten manuell für ein einzelnes Postfach auszuführen.
    
        Start-ManagedFolderAssistant -Identity <mailbox identity>

2.  Melden Sie sich mit Outlook oder Outlook Web App bei dem Postfach an, und überprüfen Sie, ob Nachrichten entsprechend der Richtlinienkonfiguration gelöscht bzw. in ein Archiv verschoben wurden.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



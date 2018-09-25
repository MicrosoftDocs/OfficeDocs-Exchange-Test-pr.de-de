---
title: 'Konf. d. Aufbewahrung f. gelösch. Elem. u. Kontingente für wiederherst. Elem.'
TOCTitle: Konfigurieren der Aufbewahrungszeit für gelöschte Elemente und Kontingente für wiederherstellbare Elemente
ms:assetid: de7d667a-1c93-4364-a4f9-2aa5e3678b12
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee364752(v=EXCHG.150)
ms:contentKeyID: 50554928
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Aufbewahrungszeit für gelöschte Elemente und Kontingente für wiederherstellbare Elemente

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Wenn ein Benutzer zum Löschen von Elementen aus dem Ordner **Gelöschte Elemente** die ENTF-Taste oder die Umschalttaste und die ENTF-Taste drückt bzw. die Option **Ordner "Gelöschte Elemente" leeren** wählt, werden die Elemente in den Ordner **Wiederherstellbare Elemente\\Löschvorgänge** verschoben. Die Zeitdauer, während der gelöschte Elemente in diesem Ordner beibehalten werden, basiert auf den Einstellungen für die Aufbewahrungszeit gelöschter Elemente, die für die Postfachdatenbank oder das Postfach konfiguriert sind. Für Postfachdatenbanken ist standardmäßig eine Aufbewahrungszeit für gelöschte Elemente von 14 Tagen konfiguriert. Für die Anzeige einer Warnung zum Kontingent für wiederherstellbare Elemente und für das Kontingent für wiederherstellbare Elemente sind 20 GB bzw. 30 GB festgelegt.


> [!NOTE]
> Vor dem Ablauf der Aufbewahrungszeit für gelöschte Elemente können Benutzer von Microsoft Outlook und Microsoft OfficeOutlook Web App gelöschte Elemente über die Funktion „Gelöschte Elemente wiederherstellen“ wiederherstellen. Weitere Informationen zu diesen Funktionen finden Sie im Thema „Wiederherstellen gelöschter Elemente“ für <A href="https://go.microsoft.com/fwlink/p/?linkid=198206">Outlook</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=198207">Outlook Web App</A>.



Zum Konfigurieren der Aufbewahrungszeit gelöschter Elemente und Kontingente für wiederherstellbare Elemente für ein Postfach oder eine Postfachdatenbank kann die Shell verwendet werden. Aufbewahrungseinstellungen für gelöschte Elemente werden ignoriert, wenn ein Postfach in einem Compliance-Archiv platziert ist bzw. einem Beweissicherungsverfahren unterliegt.

Weitere Informationen zur Aufbewahrung von gelöschten Elementen, zum Ordner **Wiederherstellbare Elemente**, Compliance-Archiv und Beweissicherungsverfahren finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren der Aufbewahrungsdauer für gelöschte Objekte für ein Postfach

**Konfigurieren der Aufbewahrungszeit von gelöschten Elementen für ein Postfach mithilfe der Exchange-Verwaltungskonsole**

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht ein Postfach aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Postfachnutzung** auf **Weitere Optionen**, und wählen Sie anschließend eine der folgenden Optionen
    
      - **Standard-Aufbewahrungseinstellungen der Postfachdatenbank verwenden**   Wählen Sie diese Einstellung zum Verwenden der Aufbewahrungseinstellung für gelöschte Elemente, die für die Postfachdatenbank konfiguriert ist.
    
      - **Die Einstellungen für dieses Postfach anpassen**   Wählen Sie diese Einstellung zum Konfigurieren von Aufbewahrungseinstellungen für gelöschte Elemente für das Postfach.
        
        **Gelöschte Elemente aufbewahren für (Tage)**   In diesem Feld wird der Zeitraum angezeigt, den gelöschte Elemente aufbewahrt werden, bevor sie endgültig gelöscht werden und vom Benutzer nicht mehr wiederhergestellt werden können. Beim Erstellen des Postfachs basiert dieser Wert auf den Aufbewahrungseinstellungen für gelöschte Elemente, die für die Postfachdatenbank konfiguriert wurden. Standardmäßig ist eine Postfachdatenbank für eine Aufbewahrung gelöschter Elemente für 14 Tage konfiguriert. Der Wertebereich für diese Einstellung liegt zwischen 0 und 24.855 Tagen.
    
      - **Elemente nicht endgültig löschen, bevor die Datenbank gesichert ist**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass Postfächer und E-Mails gelöscht werden, bevor die Postfachdatenbank, in der sich das Postfach befindet, gesichert wurde.

**Konfigurieren der Aufbewahrungszeit von gelöschten Elementen für ein Postfach**

In diesem Beispiel wird für das Postfach von April Stewart eine Aufbewahrungszeit von gelöschten Elementen von 30 Tagen konfiguriert.

```powershell
Set-Mailbox -Identity - "April Stewart" -RetainDeletedItemsFor 30
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Konfigurieren von Kontingenten für wiederherstellbare Elemente für ein Postfach mithilfe der Shell


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Konfigurieren wiederherstellbarer Elemente für ein Postfach verwendet werden.



In diesem Beispiel wird für das Postfach von April Stewart ein Kontingent für wiederherstellbare Elemente von 15 GB konfiguriert. Zudem wird festgelegt, dass bei einer Größe von 12 GB eine Warnung zu diesem Kontingent für wiederherstellbare Elemente angezeigt wird.

```powershell
    Set-Mailbox -Identity "April Stewart" -RecoverableItemsWarningQuota 12GB -RecoverableItemsQuota 15GB -UseDatabaseQuotaDefaults $false
```


> [!NOTE]
> Um für ein Postfach ein anderes Kontingent für wiederherstellbare Elemente zu konfigurieren als das Kontingent der Postfachdatenbank, muss der Parameter <EM>UseDatabaseQuotaDefaults</EM> auf <CODE>$false</CODE> festgelegt werden.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Konfigurieren der Aufbewahrungszeit von gelöschten Elementen für eine Postfachdatenbank


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Konfigurieren der Aufbewahrung gelöschter Elemente für eine Postfachdatenbank verwendet werden.



In diesem Beispiel wird eine Aufbewahrungszeit von gelöschten Elementen von 10 Tagen für die Postfachdatenbank "MDB2" konfiguriert.

```powershell
Set-MailboxDatabase -Identity MDB2 -DeletedItemRetention 10
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)).

## Konfigurieren von Kontingenten für wiederherstellbare Elemente für eine Postfachdatenbank mithilfe der Shell


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Konfigurieren wiederherstellbarer Elemente für eine Postfachdatenbank verwendet werden



In diesem Beispiel wird für die Postfachdatenbank "MDB2" ein Kontingent für wiederherstellbare Elemente von 20 GB konfiguriert. Zudem wird festgelegt, dass bei einer Größe von 15 GB eine Warnung zu diesem Kontingent für wiederherstellbare Elemente angezeigt wird.

```powershell
Set-MailboxDatabase -Identity MDB2 -RecoverableItemsWarningQuota 15GB -RecoverableItemsQuota 20GB
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)).


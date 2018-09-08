---
title: 'Deaktivieren der Kalenderveröffentlichung im Internet: Exchange 2013 Help'
TOCTitle: Deaktivieren der Kalenderveröffentlichung im Internet
ms:assetid: f26dbf04-9dae-460f-a987-2ad3dfbc7b7e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ853047(v=EXCHG.150)
ms:contentKeyID: 50554942
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Deaktivieren der Kalenderveröffentlichung im Internet

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-02-15_

Das Deaktivieren der Veröffentlichung von Kalenderinformationen, hängt davon ab, wie die Aktivierung erfolgt ist. Wenn Sie für das Veröffentlichung von Kalenderinformationen dediziert eine Freigaberichtlinie erstellt haben, können Sie die Richtlinie entweder deaktivieren oder ganz löschen. Wenn Sie die Veröffentlichung von Kalenderinformationen als Freigaberegel in der standardmäßigen Freigaberichtlinie konfiguriert haben, können Sie die Freigaberegel für die Domäne **Anonym** entfernen.

Wenn Sie eine Freigaberichtlinie zum Definieren der Kalenderveröffentlichung im Internet deaktivieren, können Benutzer, die der Freigaberegel unterliegen, Kalenderinformationen nicht länger für die in der Richtlinie angegebene Internetdomäne **Anonym** freigeben. Sie können allerdings eine für die Veröffentlichung von Kalenderinformationen im Internet vorgesehene Freigaberichtlinie erst löschen oder deaktivieren, nachdem bei Benutzern, die dieser Richtlinie unterliegen, die Richtlinieneinstellung für ihre Postfächer entfernt wurde. Weitere Informationen zum Ändern der Einstellung der Freigaberichtlinie finden Sie unter [Verwalten von Benutzerpostfächern](https://technet.microsoft.com/de-de/library/Bb123809(v=EXCHG.150)).


> [!NOTE]
> Wenn Sie die Freigaberichtlinie deaktivieren oder löschen, können Benutzer, die dieser Richtlinie unterliegen, so lange Informationen weiter gemeinsam verwenden, bis der Freigaberichtlinien-Assistent ausgeführt wird. Um anzugeben, wie häufig der Freigaberichtlinien-Assistent ausgeführt wird, verwenden Sie das Cmdlet <A href="https://technet.microsoft.com/de-de/library/aa998651(v=exchg.150)">Set-MailboxServer</A> mit dem Parameter <EM>SharingPolicySchedule</EM>.



Zur vollständigen Deaktivierung der Kalenderveröffentlichung im Internet sollten Sie das virtuelle Outlook Web App-Verzeichnis, das für die Kalenderveröffentlichung verwendet wird, ebenfalls deaktivieren. Dadurch wird der Zugriff auf die veröffentlichten Kalenderlinks, die zuvor von Benutzern der Exchange-Organisation an externe Internetbenutzer freigegeben wurden, verhindert. Dieser Schritt wird später in diesem Thema ausführlich erläutert.

Weitere Informationen zur Veröffentlichung von Kalenderinformationen im Internet und zu Freigaberichtlinien finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 15 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Kalender- und Freigabeberechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Verwenden der Exchange-Verwaltungskonsole oder Shell zum Deaktivieren der Freigaberichtlinien für die Kalenderveröffentlichung im Internet

## Verwenden der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Führen Sie in der Listenansicht **Individuelle Freigabe** einen der folgenden Schritte durch:
    
      - Wenn Sie speziell für die Veröffentlichung von Kalenderinformationen im Internet eine Freigaberichtlinie erstellt haben, wählen Sie diese Richtlinie aus, und deaktivieren Sie anschließend das Kontrollkästchen in der Spalte **EIN**, um die Freigaberichtlinie zu deaktivieren, oder klicken Sie auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"), um sie zu löschen.
    
      - Wenn Sie die Veröffentlichung von Kalenderinformationen im Internet als Freigaberegel in der standardmäßigen Freigaberichtlinie konfiguriert haben, führen Sie die folgenden Schritte aus:
        
        1.  Wählen Sie die Standardfreigaberegel aus, und klicken Sie dann auf **Bearbeiten**.![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol")
        
        2.  Wählen Sie in **Freigaberegel** die Freigaberegel **Anonym** aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um die Freigaberegel zu entfernen.
        
        3.  Klicken Sie auf **Speichern**.

## Verwenden der Shell

In diesem Beispiel wird die dedizierte Freigaberichtlinie zur Kalenderveröffentlichung im Internet mit dem Namen **Internet** deaktiviert.

    Set-SharingPolicy -Identity "Internet" -Enabled $false

In diesem Beispiel wird die dedizierte Freigaberichtlinie zur Kalenderveröffentlichung im Internet mit dem Namen **Internet** gelöscht.

    Remove-SharingPolicy -Identity "Internet"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-SharingPolicy](https://technet.microsoft.com/de-de/library/dd297931\(v=exchg.150\)).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können untersuchen, ob Sie die Freigaberichtlinie entfernt oder aktualisiert haben, indem Sie den folgenden Shell-Befehl ausführen, um die Informationen zur Freigaberichtlinie zu überprüfen.

    Get-SharingPolicy <policy name> | format-list

Wenn Sie die dedizierte Freigaberichtlinie zur Kalenderveröffentlichung im Internet entfernt haben, ist die Richtlinie nicht in den Ergebnissen des Cmdlets enthalten.

Wenn Sie die Standardfreigaberichtlinie aktualisiert haben, prüfen Sie, ob die Domäne `Anonymous` aus dem Parameter *Domains* entfernt wurde.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-SharingPolicy](https://technet.microsoft.com/de-de/library/dd335081\(v=exchg.150\)).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Schritt 2: Deaktivieren der anonymen Funktionen des virtuellen Outlook Web App-Verzeichnisses mithilfe der Shell


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Deaktivieren der anonymen Funktionen des virtuellen Outlook Web App-Verzeichnisses verwendet werden.



In diesem Beispiel werden anonymen Funktionen für das virtuelle Outlook Web App-Verzeichnis für den Clientzugriffsserver CAS01 deaktiviert.

    Set-OwaVirtualDirectory -Identity "CAS01" - AnonymousFeaturesEnabled -$false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/bb123515\(v=exchg.150\)).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können genauer untersuchen, ob Sie die anonymen Funktionen für das virtuelle Outlook Web App-Verzeichnis auf dem Clientzugriffsserver erfolgreich deaktiviert haben, indem Sie den folgenden Shell-Befehl ausführen und prüfen, ob der Parameter *AnonymousFeaturesEnabled* auf `$false` festgelegt ist.

    Get-OwaVirtualDirectory | format-list

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/aa998588\(v=exchg.150\)).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



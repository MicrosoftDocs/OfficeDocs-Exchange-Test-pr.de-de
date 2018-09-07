---
title: 'Ändern von Archivrichtlinien: Exchange 2013 Help'
TOCTitle: Ändern von Archivrichtlinien
ms:assetid: 1e3002c2-801a-43ea-ae00-52ab34d76b9c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529919(v=EXCHG.150)
ms:contentKeyID: 50475182
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern von Archivrichtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-02-01_

In Exchange Server 2013 und Exchange Online können Sie Archivrichtlinien zum automatischen Verschieben von Postfachelementen in persönliche (lokale) oder cloudbasierte Archive verwenden. Archivrichtlinien sind Aufbewahrungstags, die die Aufbewahrungsaktion **In Archiv verschieben** verwenden.

Exchange-Setup erstellt die Aufbewahrungsrichtlinie **MRM-Standardrichtlinie**. Dieser Richtlinie ist ein Standardrichtlinientag (DPT) zugewiesen, mit dem Elemente nach zwei Jahren in das Archivpostfach verschoben werden. Diese Richtlinie enthält auch eine Reihe von persönlichen Tags, die Benutzer auf Ordner oder Postfachelemente anwenden können, um Nachrichten automatisch zu verschieben oder zu löschen. Wenn einem Postfach bei der Aktivierung des Archivs keine Aufbewahrungsrichtlinie zugewiesen wird, wird in Exchange automatisch die MRM-Standardrichtlinie angewendet. Sie können auch eigene Archiv- und Aufbewahrungsrichtlinien erstellen und auf Postfachbenutzer anwenden. Weitere Informationen finden Sie unter [Aufbewahrungstags und Aufbewahrungsrichtlinien](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

Sie können die in der Standardrichtlinie enthaltenen Aufbewahrungstags an Ihre Geschäftsanforderungen anpassen. Sie können beispielsweise die Archiv-DPT so ändern, dass Elemente nach drei statt zwei Jahren in das Archiv verschoben werden. Sie können auch zusätzliche persönliche Tags erstellen und entweder zu einer Aufbewahrungsrichtlinie hinzufügen, z. B. zur MRM-Standardrichtlinie, oder es Benutzern ermöglichen, über die Outlook Web App-Optionen persönliche Tags zu ihren Postfächern hinzuzufügen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Archive finden Sie unter:

  - **Exchange Server 2013:**  [Verwalten von In-Situ-Archiven in Exchange 2013](manage-in-place-archives-in-exchange-2013-exchange-2013-help.md)

  - **Exchange Online:**  [Aktivieren oder Deaktivieren eines Archivpostfachs in Exchange Online](https://technet.microsoft.com/de-de/library/jj984357\(v=exchg.150\))


> [!NOTE]
> In einer Exchange-Hybridbereitstellung können Sie ein cloudbasiertes Archivpostfach für ein lokales primäres Postfach aktiveren. Beim Zuweisen einer Archivrichtlinie zu einem lokalen Postfach werden die Elemente zum cloudbasierten Archiv verschoben. Wenn ein Element in das Archivpostfach verschoben wird, wird im lokalen Postfach keine Kopie davon beibehalten. Wenn das lokale Postfach ausgesetzt wird, werden Elemente anhand einer Archivrichtlinie weiterhin in das cloudbasierte Archivpostfach verschoben, in dem sie so lange aufbewahrt werden, wie dies durch die In-Situ-Speicherung festgelegt wurde.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Ändern der Standardarchivrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Aufbewahrungstags**.

2.  Wählen Sie in der Listenansicht das Tag **Standard, 2 Jahre, in Archiv verschieben** aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    

    > [!TIP]
    > Klicken Sie auf die Spalte <STRONG>TYP</STRONG>, um die Aufbewahrungstags nach Typ zu sortieren. Die Standardarchivrichtlinie wird mit dem Typ <STRONG>Standard</STRONG> und der Aufbewahrungsaktion <STRONG>Archiv</STRONG> angezeigt. Alternativ können Sie auf <STRONG>NAME</STRONG> klicken, um die Aufbewahrungstags nach Name zu sortieren.



3.  Bearbeiten Sie in **Aufbewahrungstag** gegebenenfalls die folgenden Einstellungen, und klicken Sie auf **Speichern**:
    
      - **Name**   Verwenden Sie dieses Feld am oberen Rand der Seite, um den Tagnamen anzuzeigen oder zu ändern.
    
      - **Aufbewahrungstagtyp**   Dieses schreibgeschützte Feld zeigt den Tagtyp an.
    
      - **Aufbewahrungsaktion**   Ändern Sie dieses Feld nicht für Archivrichtlinien.
    
      - **Aufbewahrungszeitraum** Wählen Sie eine der folgenden Optionen:
        
          - **Nie**   Klicken Sie auf diese Schaltfläche, um das Tag zu deaktivieren. Wenn das Standardrichtlinientag deaktiviert ist, wird es nicht länger auf das Postfach angewendet.
            

            > [!IMPORTANT]
            > Elemente, auf die ein deaktiviertes Aufbewahrungstag angewendet wird, werden nicht vom Postfach-Assistenten verarbeitet. Wenn Sie verhindern möchten, dass ein Tag auf Elemente angewendet wird, sollten Sie das Tag nicht löschen, sondern deaktivieren. Beim Löschen eines Tags wird die Tagkonfiguration aus Active Directory gelöscht, und der Postfach-Assistent verarbeitet alle Nachrichten, um das gelöschte Tag zu entfernen.

            

            > [!NOTE]
            > Wenn ein Benutzer ein Tag auf ein Element anwendet und davon ausgeht, dass das Element nie verschoben wird, kann das spätere Aktivieren des Tags zum Verschieben von Elementen führen, die der Benutzer im primären Postfach aufbewahren wollte.

        
          - **Wenn das Element das folgende Alter (in Tagen) erreicht**   Klicken Sie auf diese Schaltfläche, um festzulegen, dass Elemente nach einem bestimmten Zeitraum in ein Archiv verschoben werden. Standardmäßig werden Elemente nach zwei Jahren (730 Tagen) in das Archiv verschoben. Zum Ändern dieser Einstellung geben Sie im entsprechenden Textfeld den Aufbewahrungszeitraum in Tagen ein. Der Wertebereich liegt zwischen 1 und 24.855 Tagen.
    
      - **Kommentar**   In diesem Feld können Sie einen Kommentar eingeben, der Outlook- und Outlook Web App-Benutzern angezeigt wird.

## Ändern von Archivierungsrichtlinien mithilfe der Shell

In diesem Beispiel wird das Tag `Default 2 year move to archive` geändert, um Elemente nach 1095 Tagen (3 Jahren) zu verschieben.

    Set-RetentionPolicyTag "Default 2 year move to archive" -Name "Default 3 year move to archive" -AgeLimitForRetention 1095

In diesem Beispiel wird das Tag `Default 2 year move to archive` deaktiviert.

    Set-RetentionPolicyTag "Default 2 year move to archive" -RetentionEnabled $false

In diesem Beispiel werden alle Archiv-DPTs und persönlichen Tags abgerufen und deaktiviert.

    Get-RetentionPolicyTag | ? {$_.RetentionAction -eq "MoveToArchive"} | Set-RetentionPolicyTag -RetentionEnabled $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd298042\(v=exchg.150\)) und [Get-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd298009\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Verwenden Sie das Cmdlet [Get-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd298009\(v=exchg.150\)), um die Einstellungen des Aufbewahrungstags abzurufen.

Mit diesem Befehl werden Eigenschaften des Aufbewahrungstags `Default 2 year move to archive` abgerufen, und die Ausgabe wird mittels Pipe an das Cmdlet **Format-List** weitergeleitet, um sämtliche Eigenschaften in einem Listenformat anzuzeigen.

    Get-RetentionPolicyTag "Default 2 year move to archive" | Format-List


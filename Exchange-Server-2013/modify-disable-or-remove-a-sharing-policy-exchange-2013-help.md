---
title: 'Ändern, Deaktivieren oder Entfernen einer Freigaberichtlinie: Exchange 2013 Help'
TOCTitle: Ändern, Deaktivieren oder Entfernen einer Freigaberichtlinie
ms:assetid: 714af42d-ca29-4bb4-ac48-f0b3d4fd1c15
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657460(v=EXCHG.150)
ms:contentKeyID: 50475935
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern, Deaktivieren oder Entfernen einer Freigaberichtlinie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-02-15_

Freigaberichtlinien ermöglichen es Benutzern in Ihrer Exchange-Organisation, Frei/Gebucht-Informationen für Benutzer in anderen Exchange-Verbundorganisationen, in Exchange-Organisationen außerhalb des Verbunds sowie für einzelne Internetbenutzer freizugeben. Während des normalen Betriebs ist es möglicherweise erforderlich, Eigenschaften von Freigaberichtlinien zu ändern, um z. B. Freigaberegeln zu bearbeiten, die Zugriffsebene für Frei/Gebucht-Informationen zu ändern, eine Freigaberichtlinie temporär zu deaktivieren oder eine Freigaberichtlinie ganz zu entfernen.

Weitere Informationen zu Verbundfreigaben finden Sie unter [Freigabe](sharing-exchange-2013-help.md)

Informationen zum Erstellen einer Freigaberichtlinie finden Sie unter [Erstellen einer Freigaberichtlinie](create-a-sharing-policy-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Kalender- und Freigabeberechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Entfernen einer Freigaberichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Wählen Sie unterhalb von **Einzelne Freigabe** eine Freigaberichtlinie, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie in **Freigaberichtlinie** auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Ändern Sie in **Freigaberegel** die Freigaberegeln wie gewünscht. Sie können verschiedene Einstellungen ändern, z. B. die Domäne, für die Informationen freigegeben werden sollen, die Freigabeebene für Kalendertermine. Wenn Sie die Einstellungen wunschgemäß geändert haben, klicken Sie auf **Speichern**, um das Dialogfeld **Freigaberegeln** zu schließen.

5.  Klicken Sie in **Freigaberichtlinie** auf **Speichern**, um die Freigaberichtlinie zu aktualisieren.

## Festlegen einer Freigaberichtlinie als Standardfreigaberichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Wählen Sie unterhalb von **Einzelne Freigabe** eine Freigaberichtlinie aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie in **Freigaberichtlinie** das Kontrollkästchen **Diese Richtlinie als meine Standardfreigaberichtlinie verwenden**.

4.  Klicken Sie auf **Speichern**, um die Freigaberichtlinie zu aktualisieren.

## Deaktivieren einer Freigaberichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Wählen Sie unter **Individuelle Freigabe** eine Freigaberichtlinie.

3.  Deaktivieren Sie in der Spalte **Ein** das Kontrollkästchen für die Freigaberichtlinie, die Sie deaktivieren möchten.

## Entfernen einer Freigaberichtlinie mithilfe der Exchange-Verwaltungskonsole


> [!IMPORTANT]
> Bevor Sie eine Freigaberichtlinie entfernen, muss sie aus allen Benutzerpostfächern entfernt werden.



1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Wählen Sie unter **Einzelne Freigabe** eine Freigaberichtlinie, und klicken Sie auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

3.  Klicken Sie im Warnungsdialogfeld auf **Ja**, um die Freigaberichtlinie zu löschen.

## Entfernen einer Freigaberichtlinie mithilfe der Shell

  - In diesem Beispiel wird die Freigaberichtlinie "Contoso" für die Domäne "contoso.com" geändert, die sich außerhalb der Organisation befindet. Mithilfe dieser Richtlinie können Benutzer in der Domäne "Contoso" nur Frei/Gebucht-Informationen anzeigen.
    
        Set-SharingPolicy -Identity Contoso -Domains 'sales.contoso.com: CalendarSharingFreeBusySimple'

  - In diesem Beispiel wird der Freigaberichtlinie "Contoso" eine zweite Domäne hinzugefügt. Wenn Sie einer vorhandenen Richtlinie eine Domäne hinzufügen, müssen Sie sämtliche zuvor eingeschlossenen Domänen auch einschließen.
    
        Set-SharingPolicy -Identity Contoso -Domains 'contoso.com: CalendarSharingFreeBusySimple', 'atlanta.contoso.com: CalendarSharingFreeBusyReviewer', 'beijing.contoso.com: CalendarSharingFreeBusyReviewer'

  - In diesem Beispiel wird die Freigaberichtlinie "Contoso" als Standardfreigaberichtlinie festgelegt.
    
        Set-SharingPolicy -Identity Contoso -Default $True

  - In diesem Beispiel wird die Freigaberichtlinie "Contoso" deaktiviert.
    
        Set-SharingPolicy -Identity "Contoso" -Enabled $False

  - Im ersten Beispiel wird die Freigaberichtlinie "Contoso" entfernt. Im zweiten Beispiel wird die Freigaberichtlinie "Contoso" entfernt und die Bestätigung unterdrückt, dass die Richtlinie wirklich entfernt werden soll.
    
        Remove-SharingPolicy -Identity Contoso
    
        Remove-SharingPolicy -Identity Contoso -Confirm

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-SharingPolicy](https://technet.microsoft.com/de-de/library/dd297931\(v=exchg.150\)) und [Remove-SharingPolicy](https://technet.microsoft.com/de-de/library/dd351071\(v=exchg.150\)).


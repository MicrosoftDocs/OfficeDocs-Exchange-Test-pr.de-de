---
title: 'Anwenden von Freigaberichtlinien für Postfächer: Exchange 2013 Help'
TOCTitle: Anwenden von Freigaberichtlinien für Postfächer
ms:assetid: dd4cc765-8469-4176-bb6e-d5b0f5235927
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657501(v=EXCHG.150)
ms:contentKeyID: 50476895
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anwenden von Freigaberichtlinien für Postfächer

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-02-15_

Freigaberichtlinien sind Bestandteil der Verbundfreigabe und ermöglichen die durch den Benutzer eingerichtete personenbezogene Freigabe von Kalenderinformationen für verschiedene Typen von externen Benutzern. Die Freigaberichtlinie, die ein Administrator auf das Postfach des Benutzers anwendet, legt die Zugriffsebene fest, auf der Daten für bestimmte Personen freigegeben werden können. Wenn Sie hier keine Änderungen vornehmen, gilt die vorgegebene Freigaberichtlinie für sämtliche Benutzer. Wenn Sie eine neue Freigaberichtlinie erstellen, müssen Sie diese zunächst auf die betreffenden Postfächer anwenden, bevor sie wirksam werden kann. Eine Freigaberichtlinie kann auf ein einzelnes Benutzerpostfach oder gleichzeitig auf mehrere Benutzerpostfächer angewendet werden. Ein Administrator kann die Freigaberichtlinie eines Benutzers auch deaktivieren, um einen Zugriff auf Kalenderdaten von außen zu unterbinden.

Weitere Informationen zur Verbundfreigabe finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "*Recipient Provisioning Permissions*" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Es muss eine Freigaberichtlinie vorhanden sein. Weitere Informationen finden Sie unter [Erstellen einer Freigaberichtlinie](create-a-sharing-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Anwenden einer Freigaberichtlinie auf ein einzelnes Postfach mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das gewünschte Postfach aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie in **Benutzerpostfach** auf **Postfachfunktionen**.

4.  Wählen Sie in der Liste **Freigaberichtlinie** die Freigaberichtlinie aus, die Sie auf dieses Postfach anwenden möchten.

5.  Klicken Sie auf **Speichern**, um die Freigaberichtlinie anzuwenden.

## Anwenden einer Freigaberichtlinie auf mehrere Postfächer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Halten Sie in der Listenansicht die STRG-TASTE gedrückt, während Sie mehrere Postfächer auswählen.

3.  Im Detailbereich werden die Postfacheigenschaften für die Massenbearbeitung konfiguriert. Klicken Sie auf **Weitere Optionen**.

4.  Klicken Sie unter **Freigaberichtlinie** auf **Aktualisieren**.

5.  Verwenden Sie unter **Massenzuweisung von Freigaberichtlinie** die Liste **Freigaberichtlinie auswählen**, um eine Freigaberichtlinie für die Zuweisung zu den Postfächern auszuwählen.

6.  Klicken Sie auf **Speichern**, um die Freigaberichtlinie auf die ausgewählten Postfächer anzuwenden.

## Anwenden einer Freigaberichtlinie auf mindestens ein Postfach mithilfe der Shell

In diesem Beispiel wird die Freigaberichtlinie "Contoso" auf das Postfach der Benutzerin Barbara angewendet.

    Set-Mailbox -Identity Barbara -SharingPolicy "Contoso"

In diesem Beispiel wird angegeben, dass für alle Benutzerpostfächer in der Marketing-Abteilung die Freigaberichtlinie "Contoso Marketing" verwendet wird.

    Get-Mailbox -Filter {Department -eq "Marketing"} | Set-Mailbox -SharingPolicy "Contoso Marketing"

In diesem Beispiel werden alle Postfächer zurückgegeben, auf die die Freigaberichtlinie "Contoso" angewendet wird. Außerdem werden die Benutzer nur mit Alias und E-Mail-Adressen in einer Tabelle aufgelistet.

    Get-Mailbox -ResultSize unlimited | Where {$_.SharingPolicy -eq "Contoso" } | format-table Alias, EmailAddresses

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) und [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sich zu vergewissern, dass Sie die Freigaberichtlinie erfolgreich auf ein Benutzerpostfach angewendet haben:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**, und wählen Sie dann das Postfach aus, auf das Sie die Freigaberichtlinie angewendet haben. Klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), klicken Sie auf **Postfachfeatures**, und überprüfen Sie dann, ob in der Liste **Freigaberichtlinie** die richtige Freigaberichtlinie angezeigt wird.

  - Führen Sie folgenden Shell-Befehl aus, um zu überprüfen, ob die Freigaberichtlinie einem Benutzerpostfach zugewiesen wurde. Überprüfen Sie, ob die richtige Freigaberichtlinie im Parameter *SharingPolicy* aufgeführt wird.
    
        Get-Mailbox <user name> | format-list


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



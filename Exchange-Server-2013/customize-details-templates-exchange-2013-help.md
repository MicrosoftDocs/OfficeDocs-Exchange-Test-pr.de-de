---
title: 'Anpassen von Detailvorlagen: Exchange 2013 Help'
TOCTitle: Anpassen von Detailvorlagen
ms:assetid: b4beeedd-e46f-442e-844a-e8575f95dca0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.toolbox.detailstemplate(v=EXCHG.150)
ms:contentKeyID: 50476490
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anpassen von Detailvorlagen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-09-25_

Mit dem Detailvorlagen-Editor können Sie die clientseitige Darstellung von Objekteigenschaften, auf die mithilfe von Adresslisten in MicrosoftOutlook zugegriffen wird, in der grafischen Benutzeroberfläche (Graphical User Interface, GUI) anpassen. Wenn ein Benutzer beispielsweise in Outlook eine Adressliste öffnet, werden die Eigenschaften eines bestimmten Objekts entsprechend der Definition in der Detailvorlage der Exchange-Organisation dargestellt. Die Objekte können durch Ändern der Feldgröße, Hinzufügen oder Entfernen von Feldern, Hinzufügen oder Entfernen von Registerkarten oder durch Neuanordnen von Feldern angepasst werden. Das Layout dieser Vorlagen richtet sich nach der jeweiligen Sprache.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Im Detailvorlagen-Editor gibt es keine Option zum Rückgängigmachen. Falls Ihnen ein Fehler unterläuft, müssen Sie zur vorherigen Version zurückkehren. Weitere Informationen finden Sie unter [Stellen Sie eine Detailvorlage die Standardkonfiguration wieder her](restore-a-details-template-to-the-default-configuration-exchange-2013-help.md).

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Detailvorlagen" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Anpassen der Detailvorlage

1.  Klicken Sie in der **Exchange-Toolbox** auf **Detailvorlagen-Editor** und dann im Aktionsbereich auf **Tool öffnen**.

2.  Klicken Sie in der Konsolenstruktur im Detailvorlagen-Editor auf **Detailvorlagen**.
    
    Im Detailbereich werden die folgenden Spalten angezeigt:
    
      - **Sprache**   In dieser Spalte wird die Sprache angezeigt, in der die Vorlage erstellt wurde.
    
      - **Vorlagentyp**   In dieser Spalte wird der Vorlagentyp angezeigt, den Sie anpassen können.
    
      - **Identität**   In dieser Spalte wird die eindeutige Identität der Vorlage angezeigt.
    
      - **Erstellt**   In dieser Spalte wird das Datum samt Uhrzeit angezeigt, an dem die Vorlage erstellt wurde.
    
      - **Geändert**   In dieser Spalte wird das Datum samt Uhrzeit angezeigt, an dem die Vorlage zuletzt geändert wurde.

3.  Klicken Sie zum Bearbeiten einer Vorlage auf die Vorlage und dann im Aktionsbereich auf **Bearbeiten**. Die Kontaktdetailvorlage für **Englisch (USA)** wird z. B. in der folgenden Abbildung angezeigt.
    
    **In Outlook 2013 angezeigte Standarddetailvorlage**
    
    ![Standarddetailvorlage in Outlook 2007](images/JJ556601.a0af8aca-663d-4702-ab2f-9a342f481cdf(EXCHG.150).gif "Standarddetailvorlage in Outlook 2007")  

4.  Nachdem Sie auf **Bearbeiten** geklickt haben, können Sie verschiedene Aufgaben durchführen, um eine Detailvorlage anzupassen:
    
      - Wenn Sie ein Objekt im Designer-Bereich verschieben möchten, wählen Sie das Objekt aus und ziehen es dann an seine neue Position in der Vorlage. Beim Verschieben des Objekts werden Ausrichtungslinien angezeigt.
    
      - Wenn Sie den Text einer Beschriftung ändern möchten, wählen Sie die Beschriftung im Designer-Bereich aus. Geben Sie im Eigenschaftenbereich den neuen Text in das Feld **Text** ein. Zum Erstellen von Tastenkombinationen können Sie das Symbol für das kaufmännische Und (&) verwenden. Positionieren Sie das kaufmännische Und (&) vor dem Buchstaben, den Sie als Tastenkombination verwenden möchten.
    
      - Wenn Sie die Größe eines Objekts ändern möchten, wählen Sie das Objekt aus und ziehen die Ziehpunkte, bis das Objekt die gewünschte Form und Größe hat.
    
      - Wenn Sie ein Objekt löschen möchten, markieren Sie das Objekt und drücken dann die ENTF-TASTE.
        

        > [!NOTE]
        > Der Detailvorlagen-Editor verfügt nicht über die Schaltfläche <STRONG>Rückgängig</STRONG>, und es gibt auch keine Tastenkombination, mit der eine Aktion rückgängig gemacht werden kann. Wenn Sie einer Vorlage ein Objekt hinzugefügt haben, können Sie es nur mit der ENTF-TASTE wieder löschen. Zum Rückgängigmachen eines Löschvorgangs müssen Sie die Einstellung erneut zuweisen. Sie können die ursprünglichen Einstellungen auch wiederherstellen, indem Sie den Detailvorlagen-Editor beenden, ohne die Änderungen zu speichern. Sollen nach dem Speichern Änderungen rückgängig gemacht werden, können Sie die Vorlage wiederherstellen. Beim Wiederherstellen einer Vorlage gehen sämtliche Anpassungen verloren, und die Vorlage verfügt wieder über die ursprüngliche Konfiguration. Weitere Informationen zum Wiederherstellen der Detailvorlage finden Sie unter <A href="restore-a-details-template-to-the-default-configuration-exchange-2013-help.md">Stellen Sie eine Detailvorlage die Standardkonfiguration wieder her</A>.

    
      - Wenn Sie Textfelder vom Typ "Bearbeiten", ein Listenfeld, ein mehrwertiges Dropdownfeld oder ein mehrwertiges Listenfeld hinzufügen möchten, ziehen Sie das Objekt im Toolboxbereich in den Designer-Bereich. Legen Sie das Attribut des Objekts fest, indem Sie auf das Dropdownfeld mit den Attributen im Eigenschaftenbereich klicken und dann das von Exchange zu verwendende Attribut auswählen.
        

        > [!NOTE]
        > Sie müssen das Objekt mit einem Attribut verknüpfen, damit es von Exchange verwendet werden kann. Zusätzlich bestimmt das Attribut den Inhalt, der dem Benutzer in Outlook angezeigt wird. Wenn Sie kein Attribut auswählen, wird automatisch ein zufälliges Attribut ausgewählt.

    
      - Um ein Gruppenfeld hinzuzufügen, ziehen Sie das Objekt in den Designer-Bereich. Geben Sie dann im Eigenschaftenbereich einen Namen in das Feld **Text** ein. Verwenden Sie Gruppenfelder zum Gruppieren ähnlicher Objekte.
    
      - Um eine Registerkarte zu einer Vorlage hinzuzufügen, klicken Sie mit der rechten Maustaste auf eine vorhandene Registerkarte und klicken dann auf **Registerkarte hinzufügen**. Eine leere Registerkarte wird angezeigt. Geben Sie einen Namen in das Feld **Text** im Eigenschaftenbereich ein, um die Registerkarte zu benennen.
    
      - Um eine Registerkarte aus einer Vorlage zu entfernen, klicken Sie mit der rechten Maustaste auf die Registerkarte und klicken dann auf **Registerkarte entfernen**. Eine Warnung wird angezeigt. Klicken Sie auf **OK**, um das Entfernen der Registerkarte zu bestätigen.
    
      - Wenn Sie die Aktivierungsreihenfolge der Objekte auf der Registerkarte ändern möchten, damit die Benutzer mithilfe der TAB-TASTE zu den einzelnen Objekten in der gewünschten Reihenfolge navigieren können, wählen Sie das Objekt im Designer-Bereich aus. und ändern Sie im Eigenschaftenbereich über das Feld **TabIndex** die Reihenfolge.
        

        > [!NOTE]
        > Um sicherzustellen, dass die Benutzer mithilfe der TAB-TASTE nicht auf die Beschriftungen von Objekten zugreifen können (z.&nbsp;B. <STRONG>Name</STRONG> oder <STRONG>Aliasname</STRONG>), ändern Sie die Reihenfolge der Beschriftungen, damit diese sich in der Aktivierungsreihenfolge an letzter Position befinden.



5.  Klicken Sie im Menü **Datei** auf **Speichern**, um die Änderungen an der Detailvorlage zu speichern.

6.  Klicken Sie zum Schließen der Vorlage im Menü **Datei** auf **Schließen**.


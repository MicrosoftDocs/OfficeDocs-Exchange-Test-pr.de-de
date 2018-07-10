---
title: 'Exchange-Überwachungsberichte: Exchange 2013 Help'
TOCTitle: Exchange-Überwachungsberichte
ms:assetid: 2b3e1529-1677-4564-be0b-ce22757ddc0d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150497(v=EXCHG.150)
ms:contentKeyID: 50474743
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange-Überwachungsberichte

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Verwenden Sie die Überwachungsprotokollierung zum Beheben von Konfigurationsproblemen, indem Sie bestimmte Änderungen von Administratoren nachverfolgen, sowie zum Einhalten gesetzlicher Bestimmungen und zum Aufbewahren von Daten, die für Rechtsstreitigkeiten erforderlich sind. Von Microsoft Exchange werden zwei Arten der Überwachungsprotokollierung bereitgestellt:

  - Bei der *Administratorüberwachungsprotokollierung* werden (auf der Grundlage eines Exchange Verwaltungsshell-Cmdlets) alle Aktionen aufgezeichnet, die von einem Administrator ausgeführt wurden. Diese Informationen können Sie zur Behandlung von Konfigurationsproblemen bzw. zum Ermitteln der Ursache von Sicherheits- oder Kompatibilitätsproblemen heranziehen. In Exchange Online werden Aktionen, die von Microsoft-Administratoren und delegierten Administratoren durchgeführt werden, außerdem protokolliert.

  - Bei der *Postfachüberwachungsprotokollierung* werden alle Postfachzugriffe durch Administratoren, delegierte Benutzer oder den Postfachbesitzer aufgezeichnet. Dadurch können Sie feststellen, wer auf ein Postfach zugegriffen hat und welche Aktionen ausgeführt wurden.

In diesem Thema werden die folgenden Punkte erläutert:

  - Exportieren von Überwachungsprotokollen

  - Ausführen von Überwachungsberichten

  - Konfigurieren der Überwachungsprotokollierung
    
      - Aktivieren der Postfachüberwachungsprotokollierung
    
      - Gewähren des Benutzerzugriffs auf Überwachungsberichte
    
      - Konfigurieren von Outlook Web App, um XML-Anlagen zuzulassen

## Exportieren von Überwachungsprotokollen

In der Exchange-Verwaltungskonsole (EAC) können Sie auf der Seite **Verwaltung der Richtlinientreue** \> **Überwachung** nach Einträgen aus dem Administratorüberwachungsprotokoll und aus dem Postfachüberwachungsprotokoll suchen und diese exportieren.

  - **Administratorüberwachungsprotokoll exportieren**   Jede von einem Administrator ausgeführte Aktion, die auf einem Shell-Cmdlet basiert und nicht mit den Verben **Get**, **Search** oder **Test** beginnt, wird im Administratorüberwachungsprotokoll protokolliert. Überwachungsprotokolleinträge enthalten das ausgeführte Cmdlet, den Parameter und die Werte, die zusammen mit dem Cmdlet verwendet wurden, sowie den Status des Vorgangs. Sie können nach den Einträgen aus dem Administratorüberwachungsprotokoll suchen und diese exportieren. Wenn Sie die Suchergebnisse exportieren, werden diese in einer XML-Datei gespeichert, und die Datei wird an eine E-Mail angefügt. Weitere Informationen finden Sie unter:
    
      - [Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle](search-the-role-group-changes-or-administrator-audit-logs-exchange-2013-help.md)
    
      - [Anzeige und Export des externen Administratorüberwachungsprotokolls](https://technet.microsoft.com/de-de/library/dn505728\(v=exchg.150\))
    

    > [!NOTE]
    > Standardmäßig werden die Einträge im Administrator-Überwachungsprotokoll 90&nbsp;Tage lang aufbewahrt. Einträge, die älter als 90&nbsp;Tage sind, werden gelöscht. In cloudbasierten Organisationen lässt sich diese Einstellung nicht ändern. In lokalen Exchange-Organisationen jedoch kann sie mithilfe des Cmdlets <STRONG>Set-AdminAuditLog</STRONG> geändert werden.



  - **Postfachüberwachungsprotokolle exportieren**   Ist die Postfachüberwachungsprotokollierung für ein Postfach aktiviert, speichert Microsoft Exchange alle Aktionen, die von anderen Benutzern als dem Postfachbesitzer auf die Postfachdaten angewendet wurden, im Postfachüberwachungsprotokoll. Dieses Protokoll liegt in einem ausgeblendeten Ordner im überwachten Postfach. Die Postfachüberwachungsprotokollierung kann so konfiguriert werden, dass auch die Aktionen des Postfachbenutzers protokolliert werden. Die Einträge in diesem Protokoll geben Aufschluss darüber, wer auf das Postfach zugegriffen hat, wann der Zugriff erfolgte, welche Aktionen durchgeführt wurden und ob die Aktionen erfolgreich waren. Wenn Sie die Einträge im Postfachüberwachungsprotokoll durchsuchen und exportieren, speichert Microsoft Exchange die Suchergebnisse in einer XML-Datei und fügt diese Datei an eine E-Mail an. Weitere Informationen finden Sie unter [Exportieren von Postfachüberwachungsprotokollen](export-mailbox-audit-logs-exchange-2013-help.md).

## Ausführen von Überwachungsberichten

Wenn Sie in der Exchange-Verwaltungskonsole auf der Seite **Überwachung** einen der folgenden Berichte ausführen, werden die Ergebnisse im Detailbereich des Berichts angezeigt.

  - **Bericht für Nicht-Besitzer-Postfachzugriff ausführen**   Verwenden Sie diesen Bericht, um nach Postfächern zu suchen, auf die von einer Person zugegriffen wurde, bei der es sich nicht um den Besitzer des Postfachs handelt. Weitere Informationen finden Sie unter [Ausführen eines Berichts zum Postfachzugriff durch Nicht-Besitzer](run-a-non-owner-mailbox-access-report-exchange-online-help.md).

  - **Administrator-Rollengruppenbericht ausführen**   Verwenden Sie diesen Bericht, um nach Änderungen an Administratorrollengruppen zu suchen. Weitere Informationen finden Sie unter [Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle](search-the-role-group-changes-or-administrator-audit-logs-exchange-2013-help.md).

  - **Compliance-Discovery- und -Archivbericht ausführen**   Mit diesem Bericht können Sie Postfächer finden, die im Compliance-Archiv gespeichert oder daraus entfernt wurden. Weitere Informationen finden Sie unter:
    
      - [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md)
    
      - [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md)

  - **Bericht zu Beweissicherungsverfahren pro Postfach ausführen**   Mit diesem Bericht können Sie Postfächer finden, für die das Beweissicherungsverfahren aktiviert oder deaktiviert wurde. Weitere Informationen finden Sie unter.
    
      - [Ausführen eines Berichts zu Beweissicherungsverfahren pro Postfach](run-a-per-mailbox-litigation-hold-report-exchange-2013-help.md)
    
      - [Aktivieren des Beweissicherungsverfahrens für ein Postfach](place-a-mailbox-on-litigation-hold-exchange-2013-help.md)

  - **Administratorüberwachungsprotokoll ausführen**   Verwenden Sie diesen Bericht, um die Einträge im Administratorüberwachungsprotokoll anzuzeigen. Anstatt das Administratorüberwachungsprotokoll zu exportieren, dessen Empfang in einer E-Mail-Nachricht bis zu 24 Stunden dauern kann, können Sie diesen Bericht in der Exchange-Verwaltungskonsole ausführen. Dieser Bericht protokolliert die Konfigurationsänderungen, die von Administratoren in Ihrer Organisation vorgenommen werden. Es können bis zu 5000 Einträge auf mehreren Seiten angezeigt werden. Um die Suche einzuschränken, können Sie einen Datumsbereich angeben. Weitere Informationen finden Sie unter:
    
      - [Anzeigen des Administratorüberwachungsprotokolls](view-the-administrator-audit-log-exchange-2013-help.md)
    
      - [Administratorüberwachungsprotokollierung](administrator-audit-logging-exchange-2013-help.md)

  - **Externes Administratorüberwachungsprotokoll ausführen**   Dieser Bericht ist nur in Exchange Online und Exchange Online Protection verfügbar. Von Microsoft-Administratoren oder delegierten Administratoren ausgeführte Aktionen werden im Administratorüberwachungsprotokoll protokolliert. Verwenden Sie das externe Administratorüberwachungsprotokoll, um Aktionen zu suchen und anzuzeigen, die Administratoren außerhalb Ihrer Organisation an der Konfiguration Ihrer Exchange Online-Organisation durchgeführt haben. Weitere Informationen finden Sie unter [Anzeige und Export des externen Administratorüberwachungsprotokolls](https://technet.microsoft.com/de-de/library/dn505728\(v=exchg.150\)).

## Konfigurieren der Überwachungsprotokollierung

Sie müssen zunächst die Überwachungsprotokollierung für die Organisation konfigurieren, um Überwachungsberichte ausführen und Überwachungsprotokolle exportieren zu können.

## Aktivieren der Postfachüberwachungsprotokollierung

Die Postfachüberwachungsprotokollierung muss für jedes Postfach aktiviert werden, für das ein Bericht zum Postfachzugriff durch Nicht-Besitzer ausgeführt werden soll. Wenn die Postfachüberwachungsprotokollierung für ein Postfach nicht aktiviert ist, erhalten Sie beim Ausführen eines Berichts sowie beim Exportieren des Postfachüberwachungsprotokolls keine Ergebnisse für das Postfach.

Führen Sie den folgenden Befehl in der Shell aus, um die Postfachüberwachungsprotokollierung für ein einzelnes Postfach zu aktivieren.

    Set-Mailbox <Identity> -AuditEnabled $true

Führen Sie folgende Befehle aus, um die Postfachüberwachung für alle Benutzerpostfächer in Ihrer Organisation zu aktivieren.

    $UserMailboxes = Get-mailbox -Filter {(RecipientTypeDetails -eq 'UserMailbox')}
    $UserMailboxes | ForEach {Set-Mailbox $_.Identity -AuditEnabled $true}

Weitere Informationen dazu, wie Sie konfigurieren, welche Aktionen protokolliert werden sollen, finden Sie in den folgenden Artikeln:

  - **Exchange 2013**   [Aktivieren oder Deaktivieren der Überwachungsprotokollierung für ein Postfach](enable-or-disable-mailbox-audit-logging-for-a-mailbox-exchange-2013-help.md)

  - **Exchange Online**   [Aktivieren der Postfachüberwachung in Office 365](https://go.microsoft.com/fwlink/p/?linkid=626109)

## Gewähren des Benutzerzugriffs auf Überwachungsberichte

Standardmäßig können Administratoren in der Exchange-Verwaltungskonsole auf alle Berichte der Seite **Überwachung** zugreifen und diese ausführen. Anderen Benutzern (beispielsweise aus der Datensatzverwaltung oder aus der Rechtsabteilung) müssen die notwendigen Berechtigungen jedoch erst zugewiesen werden.

Die einfachste Art, den Benutzern Zugriff zu gewähren, ist das Hinzufügen der Benutzer zur Rollengruppe "Datensatzverwaltung". Sie können einem Benutzer auch mithilfe der Shell Zugriff auf die Seite **Überwachung** in der Exchange-Verwaltungskonsole gewähren, indem Sie ihm die Rolle für Überwachungsprotokolle zuweisen.

## Hinzufügen eines Benutzers zur Rollengruppe "Datensatzverwaltung"

1.  Navigieren Sie zu **Berechtigungen** \> **Administratorrollen**.

2.  Klicken Sie in der Liste mit den Rollengruppen auf **Datensatzverwaltung** und dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie unter **Mitglieder** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie im Dialogfeld **Mitglieder auswählen** den Benutzer aus. Sie können auch nach einem Benutzer suchen, indem Sie seinen Anzeigenamen ganz oder teilweise eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken. Sie können die Liste auch sortieren, indem Sie auf die Spaltenüberschriften **Name** oder **Anzeigename** klicken.

5.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") und dann auf **OK**, um zur Rollengruppenseite zurückzukehren.

6.  Klicken Sie auf **Speichern**, um die Änderungen an der Rollengruppe zu speichern.

Im Detailbereich wird der Benutzer unter **Mitglieder** aufgeführt, und er kann in der Exchange-Verwaltungskonsole auf die Seite **Überwachung** zugreifen, Überwachungsberichte ausführen und Überwachungsprotokolle exportieren.

## Zuweisen der Rolle für Überwachungsprotokolle zu einem Benutzer

Führen Sie den folgenden Befehl aus, um einem Benutzer die Rolle für Überwachungsprotokolle zuzuweisen.

    New-ManagementRoleAssignment -Role "Audit Logs" -User <Identity>

Auf diese Weise kann der Benutzer in der Exchange-Verwaltungskonsole die Optionen **Verwaltung der Richtlinientreue** \> **Überwachung** auswählen, um einen Bericht auszuführen. Zudem kann der Benutzer auch das Postfachüberwachungsprotokoll exportieren und das Administratorüberwachungsprotokoll exportieren und anzeigen.


> [!NOTE]
> Wenn Sie einem Benutzer zwar das Ausführen von Überwachungsberichten, aber nicht das Exportieren von Überwachungsprotokollen ermöglichen möchten, weisen Sie mithilfe des vorherigen Befehls die Rolle mit Leserechten für Überwachungsprotokolle zu.



## Konfigurieren von Outlook Web App, um XML-Anlagen zuzulassen

Wenn Sie das Postfachüberwachungsprotokoll oder das Administratorüberwachungsprotokoll exportieren, wird das Überwachungsprotokoll (XML-Datei) an eine E-Mail angefügt. Jedoch blockiert Outlook Web App standardmäßig XML-Anlagen. Wenn Sie mit Outlook Web App auf exportierte Überwachungsprotokolle zugreifen möchten, muss Outlook Web App für das Zulassen von XML-Anlagen konfiguriert werden.

Führen Sie den folgenden Befehl aus, um XML-Anlagen in Outlook Web App zuzulassen.

    Set-OwaMailboxPolicy -Identity Default -AllowedFileTypes '.rpmsg','.xlsx','.xlsm','.xlsb','.tiff','.pptx','.pptm','.ppsx','.ppsm','.docx','.docm','.zip','.xls','.wmv','.wma','.wav','.vsd','.txt','.tif','.rtf','.pub','.ppt','.png','.pdf','.one','.mp3','.jpg','.gif','.doc','.bmp','.avi','.xml'


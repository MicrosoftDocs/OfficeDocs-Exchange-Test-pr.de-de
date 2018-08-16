---
title: 'Nachverfolgen von Nachrichten mit Zustellungsberichten: Exchange 2013 Help'
TOCTitle: Nachverfolgen von Nachrichten mit Zustellungsberichten
ms:assetid: a14e4e62-08ca-4a7b-92e1-d39fe3e0a9e5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150554(v=EXCHG.150)
ms:contentKeyID: 50474818
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nachverfolgen von Nachrichten mit Zustellungsberichten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-13_

Zustellungsberichte sind ein Nachrichtenverfolgungstool in der Exchange-Verwaltungskonsole, mit dem Sie anhand des Übermittlungsstatus nach E-Mails suchen können, die mit einem bestimmten Betreff von Benutzern oder an Benutzer im Adressbuch der Organisation gesendet wurden. Sie können Zustellungsinformationen zu Nachrichten nachverfolgen, die von einem bestimmten Postfach in der Organisation gesendet oder empfangen wurden. Der Inhalt des Nachrichtentexts wird im Übermittlungsbericht nicht zurückgegeben, die Betreffzeile wird in den Ergebnissen jedoch angezeigt. Sie können Nachrichten bis zu 14 Tage nach ihrem Sende- oder Empfangsdatum nachverfolgen.


> [!NOTE]
> Zustellungsberichte verfolgen Nachrichten, die von Benutzern über Microsoft Outlook oder Outlook Web App-E-Mail-Clients gesendet wurden. Sie erfassen keine über POP- oder IMAP-E-Mail-Clients gesendete Nachrichten, wie z.&nbsp;B. Windows Mail, Outlook Express oder Mozilla Thunderbird.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: Der Zeitraum variiert je nach Umfang Ihrer Suche.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Nachrichtenverfolgung" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

  - Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351)..

## Was möchten Sie machen?

Nachverfolgen von Nachrichten mithilfe der Exchange-Verwaltungskonsole

Überprüfen eines Zustellungsberichts mithilfe der Exchange-Verwaltungskonsole

## Nachverfolgen von Nachrichten mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Zustellungsberichte**.

2.  Geben Sie die folgenden Informationen ein:
    
      - **\* Zu durchsuchendes Postfach:**  Klicken Sie auf **Durchsuchen**, um das Postfach aus dem Adressbuch auszuwählen, und klicken Sie dann auf **OK**. Das zu durchsuchende Postfach muss ausgewählt werden.
    
      - Wählen Sie eine der folgenden Optionen aus:
        
          - **Nachrichten suchen an Empfänger:**    Verwenden Sie diese Option, um nach Nachrichten zu suchen, die an bestimmte Benutzer gesendet wurden. Klicken Sie auf **Benutzer auswählen**, und wählen Sie Benutzer im Adressbuch aus, indem Sie einen Benutzer in der Liste auswählen und auf **Hinzufügen** klicken. Sie können mehrere Benutzer auswählen. Wenn Sie alle gewünschten Benutzer ausgewählt haben, klicken Sie auf **OK**, um zur Seite **Zustellungsberichte** zurückzukehren. Wenn Sie diese Option auswählen, können Sie das Feld auch leer lassen, um nach Nachrichten zu suchen, die an beliebige Benutzer gesendet wurden.
        
          - **Nachrichten suchen von Absender:**    Verwenden Sie diese Option, um nach Nachrichten zu suchen, die von einem bestimmten Benutzer empfangen wurden. Wählen Sie den Benutzer im Adressbuch aus, und klicken Sie auf **OK**, um zur Seite **Zustellungsberichte** zurückzukehren. Wenn Sie diese Option auswählen, müssen Sie einen Absender angeben.
    
      - **Diese Wörter in der Betreffzeile suchen:**    Geben Sie hier Betreffzeileninformationen ein, oder lassen Sie das Feld leer, um die Suche zu erweitern.

3.  Klicken Sie nach Abschluss des Vorgangs auf **Suchen**. Wenn Sie noch einmal von vorne beginnen möchten, klicken Sie auf **Löschen**.

## Überprüfen eines Zustellungsberichts mithilfe der Exchange-Verwaltungskonsole

Zum Anzeigen von Zustellungsinformationen wählen Sie im Bereich **Suchergebnisse** eine Nachricht aus, und klicken Sie auf **Details**.

Im Zustellungsbericht werden der Zustellungsstatus und ausführliche Zustellungsinformationen für die Nachricht angezeigt, die Sie im Bereich **Suchergebnisse** ausgewählt haben. Oben im Bericht werden die folgenden Felder angezeigt:

  - **Betreff**   Die Betreffzeile der Nachricht wird als Überschrift des Berichts angezeigt.

  - **Von**   Der Alias, der Anzeigename oder die E-Mail-Adresse der Person, die die Nachricht gesendet hat.

  - **An**   Der Alias, der Anzeigename oder die E-Mail-Adresse für jeden Empfänger der Nachricht.

  - **Gesendet**   Das Datum und die Uhrzeit, zu der die Nachricht gesendet wurde.

## Zusammenfassung bis Datum (Abschnitt)

Dieser Abschnitt wird im Übermittlungsbericht angezeigt, wenn eine Nachricht an mehr als eine Person (Empfänger) gesendet wurde. Oben in diesem Abschnitt ist die Gesamtanzahl der Empfänger angegeben, an die die Nachricht gesendet wurde, und es werden kurze Übermittlungsinformationen für jeden Empfänger bereitgestellt.

  - **Zusammenfassung bis Datum**   Zeigt die Gesamtanzahl von Empfängern sowie die Information an, ob ausstehende, übermittelte oder fehlgeschlagene Nachrichten vorhanden sind. Klicken Sie auf die Links, um die Nachrichten nach Status zu sortieren.

  - **Suchfeld**   Das Suchfeld ist nützlich, wenn Sie die Nachricht an eine Gruppe von mehr als 30 Empfängern gesendet haben. Geben Sie im Suchfeld eine E-Mail-Adresse ein, zu der Sie Zustellungsinformationen erhalten möchten, und klicken Sie auf die Lupe.

  - **An**   Zeigt die E-Mail-Adresse des Empfängers.

  - **Status**   In dieser Spalte wird der Status der Nachricht für jeden Empfänger angezeigt.

## Ausführliche Berichtinformationen

Dieser Abschnitt enthält ausführliche Übermittlungsinformationen für eine Nachricht, die an den Empfänger gesendet wurde, den Sie im Abschnitt Zusammenfassung bis Datum ausgewählt haben.

  - **Zustellungsbericht für**   Hier wird die E-Mail-Adresse des ausgewählten Empfängers angezeigt.

  - **Übermittelt**   Datum und Uhrzeit der Übermittlung der Nachricht durch das System.

Je nach Zustellungsstatus der Nachricht werden möglicherweise unterschiedliche Statusnachrichten angezeigt, einschließlich der folgenden:

  - **Übermittelt**   Zeigt die erfolgreiche Übermittlung an.

  - **Zurückgestellt**   Gibt an, dass eine Nachricht verzögert wird.

  - **Ausstehend**   Wenn die Zustellung einer Nachrichten ausstehend ist, da eine Nachricht die Kriterien für eine organisationsweite Regel oder Richtlinie erfüllt oder da sie der Nachrichtengenehmigung unterliegt, wird im Status angegeben, welche Aktion einer Regel ausgeführt wird oder dass die Nachricht vor der Zustellung von einem Moderator bestätigt werden muss.

  - **Moderator**   Der Status gibt an, ob die Nachricht vom Moderator genehmigt oder abgelehnt wurde.

  - **Gruppe erweitert**   Wenn eine Nachricht an eine Gruppe gesendet wurde, werden die einzelnen Benutzer (Empfänger) im Abschnitt **Zusammenfassung bis Datum** zusammen mit dem jeweiligen Zustellungsstatus angezeigt. Wenn Sie beim Untersuchen eines Zustellungsberichts einen Benutzer aus einer Gruppe entfernen oder ihr hinzufügen möchten, können Sie die Gruppe ändern, indem Sie auf **Gruppen bearbeiten** klicken.

  - **Fehler**   Zeigt das Datum, die Uhrzeit und die Ursache für einen Nachrichtenzustellungsfehler an. Möglicherweise blockt beispielsweise eine organisationsweite Regel die Übermittlung der Nachricht, oder die Nachricht konnte nicht übermittelt werden.

Wenn Sie die Überprüfung des Berichts abgeschlossen haben, klicken Sie auf **Schließen**. Übermittlungsberichte werden nicht gespeichert, aber Sie können einen Bericht jederzeit erneut ausführen. Beachten Sie das zweiwöchige Suchfenster.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn Ihre Suche erfolgreich war, werden Nachrichten, die den Suchkriterien entsprechen, im Bereich **Suchergebnisse** angezeigt. Zum Anzeigen der Zustellungsinformationen für die ausgewählte Nachricht wählen Sie die Nachricht aus, und klicken Sie auf **Details**. Wenn im Bereich **Suchergebnisse** keine Nachrichten angezeigt werden, ändern Sie die Suchkriterien, und führen Sie die Suche erneut aus.


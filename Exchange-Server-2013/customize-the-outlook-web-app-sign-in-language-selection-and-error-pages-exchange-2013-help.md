---
title: 'Anpassen der Outlook Web App-Seiten für Anmeldung, Sprachauswahl und Fehler: Exchange 2013 Help'
TOCTitle: Anpassen der Outlook Web App-Seiten für Anmeldung, Sprachauswahl und Fehler
ms:assetid: d8d9f735-7181-428f-9049-b9886dce5159
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633483(v=EXCHG.150)
ms:contentKeyID: 54652706
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anpassen der Outlook Web App-Seiten für Anmeldung, Sprachauswahl und Fehler

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In diesem Thema wird erläutert, wie Sie die Farbe und die Grafiken der Seiten für Anmeldung, Sprachauswahl und Fehler für Outlook Web App anpassen können.

Die Seiten für Anmeldung, Sprachauswahl und Fehler in Outlook Web App werden basierend auf Grafiken und CSS-Dateien im Designressourcenordner erstellt. Outlook Web App verwendet für alle Designs nur einen Satz von Seiten für Anmeldung, Sprachauswahl und Fehler. Alle Änderungen an diesen Seiten werden allen Benutzern angezeigt. Sie finden den Designressourcenordner im Installationsverzeichnis von Exchange unter V15\\FrontEnd\\HttpProxy\\owa\\auth\\version\\themes\\resources. Sie benötigen einen Texteditor, um die Standardfarben zu ändern, sowie einen Grafikeditor, um die Grafiken zu ändern. Wenn Sie eine bestimmte Farbe benötigen und diese unter [Color Table](https://go.microsoft.com/fwlink/p/?linkid=280679) (Farbtabelle) nicht finden, erstellen Sie ein Beispiel der Farbe in einem Bildbearbeitungstool, und ermitteln Sie so den entsprechenden HTML RGB-Wert.

Wenn Sie mehrere Server besitzen, die Outlook Web App unterstützen, und alle die gleichen Seiten für Anmeldung, Sprache und Fehler verwenden sollen, müssen Sie die geänderten Dateien auf jeden Server kopieren. Sie sollten zudem eine Sicherungskopie Ihrer angepassten Dateien erstellen. Bei der erneuten Installation oder beim Upgrade von Exchange werden sämtliche Dateien im Designordner überschrieben. Nach Abschluss der Installation oder des Upgrades müssen Sie Ihre angepassten Dateien in den entsprechenden Designordner kopieren.


> [!IMPORTANT]
> Erstellen Sie Sicherungskopien aller Dateien, die Sie ändern, bevor Sie mit der Erstellung Ihrer benutzerdefinierten Anmelde- und Abmeldeseiten beginnen.



Weitere Informationen zum Erstellen eines benutzerdefinierten Designs finden Sie unter [Erstellen eines Designs für Outlook Web App](create-a-theme-for-outlook-web-app-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 45 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter Eintrag "Grafikeditor" unter "Berechtigungen für Outlook Web App" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anpassen der Farbe der Anmeldeseite

1.  Melden Sie sich beim Exchange-Server an, wechseln Sie mithilfe von Windows Explorer zum Exchange-Server-Installationsverzeichnis, und suchen Sie \\V15\\FrontEnd\\HttpProxy\\owa\\auth\\\<version\>\\themes\\resources.

2.  Verwenden Sie einen Texteditor, wie z. B. Notepad, um die Datei logon.css zu öffnen.

3.  Suchen Sie nach dem Standardfarbwert \#0072c6, und ersetzen Sie ihn durch den HTML RGB-Wert für die Farbe, die Sie verwenden möchten. Sie können HTML RGB-Werte hier finden: [Color Table](https://go.microsoft.com/fwlink/p/?linkid=280679) (Farbtabelle).

4.  Speichern und schließen Sie die Datei.

## Anpassen der Farbe der Fehlerseite

1.  Melden Sie sich beim Exchange-Server an, wechseln Sie mithilfe von Windows Explorer zum Exchange-Server-Installationsverzeichnis, und suchen Sie \\V15\\FrontEnd\\HttpProxy\\owa\\auth\\\<version\>\\themes\\resources.

2.  Verwenden Sie einen Texteditor, wie z. B. Notepad, um die Datei errorFE.css zu öffnen.

3.  Suchen Sie nach dem Standardfarbwert \#0072c6, und ersetzen Sie ihn durch den HTML RGB-Wert für die Farbe, die Sie verwenden möchten. Sie können HTML RGB-Werte hier finden: [Color Table](https://go.microsoft.com/fwlink/p/?linkid=280679) (Farbtabelle).

4.  Speichern und schließen Sie die Datei.

## Anpassen der Farbe der Sprachauswahlseite

1.  Melden Sie sich beim Exchange-Server an, wechseln Sie mithilfe von Windows Explorer zum Exchange-Server-Installationsverzeichnis, und suchen Sie \\V15\\Client Access\\OWA\\version\\Owa2\\resources\\styles.

2.  Verwenden Sie einen Texteditor wie z. B. Editor, um die Datei LanguageSelection.css zu öffnen.

3.  Suchen Sie nach dem Standardfarbwert \#0072c6, und ersetzen Sie ihn durch den HTML RGB-Wert für die Farbe, die Sie verwenden möchten. Sie können HTML RGB-Werte hier finden: [Color Table](https://go.microsoft.com/fwlink/p/?linkid=280679) (Farbtabelle).

4.  Speichern und schließen Sie die Datei.

## Anpassen der Grafiken auf der Anmelde- und der Fehlerseite

Verwenden Sie ein Grafikbearbeitungstool, um die Grafiken zu öffnen und zu bearbeiten, die zur Erstellung der Anmelde- und der Fehlerseite verwendet werden.

1.  Melden Sie sich beim Exchange-Server an, wechseln Sie mithilfe von Windows Explorer zum Exchange-Server-Installationsverzeichnis, und suchen Sie \\V15\\FrontEnd\\HttpProxy\\owa\\auth\\\<version\>\\themes\\resources.

2.  Verwenden Sie einen Grafikeditor, um die folgenden Dateien zu öffnen und zu ändern:
    
      - owa\_text\_blue.png, um das Textlogo "Outlook Web App" zu ändern.
    
      - olk\_logo\_white.png, um das Anwendungslogo in der linken Leiste zu ändern.
    
      - olk\_logo\_white\_cropped.png, um die Grafik im Teilfenster links auf der Fehlerseite zu ändern.
    
      - sign\_in\_arrow.png, um das Symbol links neben der Anmeldeschaltfläche zu ändern.
    
      - olk\_exchange\_text\_blue.png, um das Logo "Outlook Mobile" im tnarrow-Layout zu ändern.
    
      - olk\_logo\_white\_small.png wird in tnarrow verwendet.
    
      - olk\_exchange\_text\_stacked\_white\_small.png wird in tnarrow verwendet.

3.  Suchen Sie nach dem Standardfarbwert \#0072c6, und ersetzen Sie ihn durch den HTML RGB-Wert für die Farbe, die Sie verwenden möchten. Sie können HTML RGB-Werte hier finden: [Color Table](https://go.microsoft.com/fwlink/p/?linkid=280679) (Farbtabelle).

4.  Speichern und schließen Sie die Datei.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Öffnen Sie die Anmeldeseite von Outlook Web App in Internet Explorer. Zum Testen der Änderungen an der Standardwebsite auf dem Server, auf dem sich das virtuelle Outlook Web App-Verzeichnis befindet, öffnen Sie Internet Explorer, und geben Sie die URL https://localhost/owa ein.

Wenn die Änderungen nicht angezeigt werden, gehen Sie folgendermaßen vor:

1.  Wählen Sie in der Symbolleiste **Einstellungen** \> **Internetoptionen** \> **Allgemein** aus.

2.  Wählen Sie unter **Browserverlauf** die Option **Löschen** aus.

3.  Wählen Sie **Temporäre Internet- und Websitedateien** und dann **Löschen** aus.

4.  Wenn Internet Explorer den Löschvorgang abgeschlossen hat, wählen Sie zum Schließen des Fensters **Internetoptionen** die Option **OK** aus.

5.  Aktualisieren Sie das Browserfenster.


> [!TIP]
> Um die Effekte Ihre Änderungen anzuzeigen, können Sie die CSS-Datei, die Sie bearbeiten, geöffnet lassen und das Browserfenster nach der Speicherung jeder Änderung aktualisieren.



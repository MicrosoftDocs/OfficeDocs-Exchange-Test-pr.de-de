---
title: 'Erstellen eines Designs für Outlook Web App: Exchange 2013 Help'
TOCTitle: Erstellen eines Designs für Outlook Web App
ms:assetid: 7e1fa13c-3de3-45c2-b1fa-e74fc8487bda
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201700(v=EXCHG.150)
ms:contentKeyID: 54652696
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen eines Designs für Outlook Web App

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Ein *Design* definiert die Hintergrundfarbe, die Schriftarten, die Farben für Hervorhebungen sowie die Symbole und Kopfzeilen, die von MicrosoftOutlook Web App verwendet werden. Jedes Design ist eine Sammlung von Mediendateien und CSS-Dateien (Cascading Style Sheets), die auf dem MicrosoftExchange-Server im Installationsverzeichnis unter „\\Client Access\\OWA\\prem\\*version*\\resources\\themes\&quot; gespeichert werden. Jedes Design wird in einem eigenen Unterverzeichnis von „\\themes\&quot; gespeichert.

Das Standarddesign befindet sich in „\\Client Access\\OWA\\prem\\*version*\\resources\\themes\\base\&quot;. Jeder Designordner enthält alle Dateien, die zum Definieren eines Designs erforderlich sind. Bei diesen Dateien handelt es sich z. B. um CSS-Dateien, Grafiken und eine XML-Datei, die den Namen des Designs definiert. Weitere Designs können durch Kopieren aller Dateien eines Designs in einen neuen Ordner und Ändern dieser Dateien nach Bedarf erstellt werden.

Standardmäßig werden bei der Installation von Exchange Server 2013 folgende Designs installiert:

  - CSS-Dateien definieren Farben, Verläufe und Schriftarten.

  - Bild-Dateien (PNG) stellen die Symbole und andere grafische Elemente bereit. Wenn Sie eines der Symbole bearbeiten, dürfen Sie seine Größe nicht ändern. Wenn Sie die Größe beliebiger grafischer Elemente ändern, testen Sie Ihre Änderungen, damit sichergestellt ist, dass die Elemente weiterhin richtig zusammenpassen.

Diese Dateien werden auf dem Clientzugriffsserver im Installationsverzeichnis unter „\\Client Access\\OWA\\prem\\*\<version\>*\\resources\\themes\&quot; gespeichert. Jedes Design wird in einem Unterverzeichnis für das betreffende Design gespeichert. Sie können zusätzliche Designs erstellen, indem Sie ein vorhandenes Design kopieren und die Kopie ändern.

Nachdem Sie ein Design erstellt haben, können Sie die folgenden Aufgaben ausführen: [Anpassen der Outlook Web App-Seiten für Anmeldung, Sprachauswahl und Fehler](customize-the-outlook-web-app-sign-in-language-selection-and-error-pages-exchange-2013-help.md).


> [!NOTE]
> Die Light-Version von Outlook Web App unterstützt keine Designs.




> [!WARNING]
> Wenn Outlook Web App auf mehreren Servern unterstützt wird, müssen Sie das benutzerdefinierte Design auf jeden Server kopieren. Sie sollten zudem eine Sicherungskopie des benutzerdefinierten Designs erstellen. Bei der erneuten Installation oder beim Upgrade von Exchange werden sämtliche Dateien im Ordner themes überschrieben. Nach Abschluss der Installation oder des Upgrades müssen Sie das Design in den entsprechenden Ordner kopieren.<BR>Fertigen Sie vor der Erstellung des benutzerdefinierten Designs Sicherungskopien von allen Dateien an, die Sie ändern möchten.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 60 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Virtuelle Outlook Web App-Verzeichnisse" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Für diese Verfahren benötigen Sie Zugriffsrechte des lokalen Serveradministrators.

  - Sie benötigen einen Text-Editor auf die Standardfarben ändern und einem Graphics-Editor die Bilder zu ändern. Wenn müssen Sie eine bestimmte Farbe übereinstimmen, und es eine Übereinstimmung bei [Farbe Tabelle](https://go.microsoft.com/fwlink/p/?linkid=280679)nicht finden, können Sie ein Bild Bearbeitungstool Stichprobe einer Farbe, und bestimmen Sie den HTML-RGB-Wert.

  - Als bewährte Methode wird empfohlen, die folgenden Richtlinien zu befolgen, wenn Sie ein Outlook Web App-Design ändern oder erstellen:
    
      - Wenn Sie ein vorhandenes Design bearbeiten möchten, erstellen Sie Sicherungskopien der ursprünglichen Dateien, bevor Sie sie bearbeiten.
    
      - Löschen Sie weder den Ordner „\\Client Access\\OWA\\prem\\*version*\\resources\\themes\\base\&quot; noch darin enthaltene Dateien.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen eines neuen Outlook Web App-Designs

Beginnen Sie, indem Sie einen Ordner für ein neues Design erstellen, und kopieren Sie dann die Dateien aus dem vorhandenen Design in den neuen Ordner.

1.  Melden Sie sich an dem Exchange-Server an, der das virtuelle Verzeichnis für Outlook Web App hostet, indem Sie ein Konto verwenden, an das die Mitgliedschaft in der lokalen Gruppe Administratoren delegiert wurde.

2.  Öffnen Sie Windows Explorer, und suchen Sie das Installationsverzeichnis von Exchange Server.

3.  Erstellen Sie unter „\\Client Access\\OWA\\prem\\*version*\\resources\\themes\&quot; einen neuen Ordner, und nennen Sie diesen beispielsweise „Fourth Coffee\&quot;.

4.  Kopieren Sie alle Dateien aus einem anderen Design in den neuen Ordner.

## Schritt 2: Benennen des neuen Designs

Gehen Sie folgendermaßen vor, um den Anzeigenamen für das neue Design festzulegen:

1.  Öffnen Sie die Kopie der Datei themeinfo.xml im soeben erstellten Ordner des benutzerdefinierten Designs.

2.  Suchen Sie den Wert `displayname` des Designs, und ändern Sie ihn in den Namen, den Sie verwenden möchten. Beispiel: `displayname = "Fourth Coffee Theme"`.

3.  Speichern und schließen Sie themeinfo.xml.

## Schritt 3: Ändern der Sortierreihenfolge des neuen Designs (optional)

Auf Wunsch können Sie die Sortierreihenfolge des neuen Designs ändern, indem Sie die Datei themeinfo.xml bearbeiten. Die Sortierreihenfolge bestimmt die Position des Designs im Bereich **Design** im Menü Einstellungen.

Gehen Sie folgendermaßen vor, um die Sortierreihenfolge für das neue Design mithilfe der Datei themeinfo.xml zu ändern:

1.  Öffnen Sie die Kopie der Datei themeinfo.xml im Ordner des benutzerdefinierten Designs.

2.  Suchen Sie den Wert `sortorder` des Designs, und ändern Sie ihn in die Position, an der das neue Design in der Liste aufgeführt werden soll. Die Designs werden nach dem numerischen Wert in aufsteigender Reihenfolge angeordnet. In der Standardeinstellung wird das Basisdesign an erster Stelle angezeigt und hat den `sortorder`-Wert "0". Beispiel: `sortorder="<number>"`.

3.  Speichern und schließen Sie themeinfo.xml.

## Schritt 4: Ändern des neuen Designs

Nachdem Sie die Dateien kopiert und Ihr Design benannt haben, können Sie es anpassen. Die folgenden Elemente in einem Outlook Web App-Design können angepasst werden:

  - Bilddateien, in denen der Kopfzeilenbereich und Symbole definiert werden.

  - CSS-Dateien, die Schriftarten und Farben definieren.

## Bilddateien

Designbilder werden in zwei Ordnern unter "\\themes*\\\<Designname\>*\\images\\" gespeichert. Der Ordner \\images\\0 enthält Bilder, die in von links nach rechts gelesenen Sprachen (wie Deutsch) verwendet werden. Für Sprachen, die von rechts nach links gelesen werden, werden die Bilder im Ordner \\images\\rtl verwendet.


> [!NOTE]
> Einige Bilder im Ordner \images\rtl stimmen mit denen im Ordner \images\0 überein, sind jedoch gespiegelt.



Zur Anpassung des Designs können Sie die folgenden Bilder in einem Bildbearbeitungstool öffnen und ändern:

  - Headerbgmain.png
    
      - Dies ist das Hauptbild für die Kopfzeile. Es sollte die Kopfzeilenhöhe von 30 Pixel nicht überschreiten. Im Standarddesign wird kein Hintergrundbild verwendet. Daher ist das Bild transparent. Ein Beispiel für ein Design mit einem benutzerdefinierten Hintergrundbild stellt das Bild im Ordner des Designs **Blaupause** dar.

  - Headerbgright.png
    
      - Dieses Bild wird mehrfach hinter der Kopfzeile angezeigt. Im Standarddesign wird kein mehrfach angezeigtes Hintergrundbild verwendet. Daher ist das Bild transparent. Ein Beispiel für ein Design mit einem benutzerdefinierten mehrfach angezeigten Hintergrundbild stellt das Bild im Ordner des Designs **Blaupause** dar.

  - sprite1.mouse.png
    
      - Dies enthält die Mehrzahl der in einem Design verwendeten Bilder. Sie können die Farbe der Bilder an das Design anpassen und das standardmäßige Outlook Web App-Textlogo ändern.
    
      - Zur Vermeidung von Problemen sollten Sie die Größe einzelner Symbole im Sprite nicht ändern und sicherstellen, dass es als transparente PNG-Datei gespeichert wird.

  - themepreview.png
    
      - Dieses Bild stellt das Design im Bereich **Design** im Menü Einstellungen von Outlook Web App dar.

## Farben und Schriftarten

CSS-Dateien (Cascading Style Sheet) definieren die in einem Design verwendeten Farben und Schriftarten. Sie werden in mehreren Ordnern unter "\\themes\\*\<Designname\>*" gespeichert. Der Ordner "\\*\<Designname\>*\\0" enthält CSS-Dateien, die in von links nach rechts gelesenen Sprachen (wie Deutsch) verwendet werden. Für Sprachen, die von rechts nach links gelesen werden, werden die CSS-Dateien im Ordner "\\*\<Designname\>*\\rtl" verwendet. Daneben sind sprachspezifische Ordner (wie \\ja, \\ko, \\zhs und \\zht) mit CSS-Dateien für diese Sprachen vorhanden.

Ändern Sie zunächst den Ordner „\\*\<theme name\>*\\images\\0\&quot;. In jedem Design können vier Farben angepasst werden.

  - BrandColor: \#0072C6

  - NavBarHoverColor: \#4C9CD7

  - UnreadColor: \#2A8DD4

  - FocusColor: \#DFEDFA

Sie können in einem Text-Editor wie Editor alle Instanzen dieser Werte in den folgenden beiden Dateien suchen und durch die Farben Ihres Designs ersetzen: owa2styles.mouseCSS und owa2styles2.mouseCSS. Dies muss in jedem Ordner des neuen Designs erfolgen, der diese CSS-Dateien enthält.

## Schritt 5: Festlegen des Standarddesigns für Outlook Web App

Die Festlegung eines neuen Standarddesigns betrifft nur Benutzer, die ihr Design nicht über das Menü Einstellungen in Outlook Web App geändert haben.

Wenn alle Benutzer das Standarddesign verwenden sollen, müssen Sie ein Standarddesign festlegen und gleichzeitig die Designauswahl deaktivieren.

## Festlegen des Standarddesigns für Outlook Web App mithilfe der Shell

In diesem Beispiel wird das Standarddesign für Outlook Web App festgelegt. Dabei lautet der Servername `fourthcoffee`, der Name des virtuellen Verzeichnisses `owa`, der Websitename `default web site`, und das Design befindet sich im Ordner `Custom`.

    set-owavirtualdirectory -identity "fourthcoffee\owa (default web site)" -defaulttheme Custom 

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/bb123515\(v=exchg.150\)).

## Deaktivieren der Designauswahl für Outlook Web App mithilfe der Shell

In diesem Beispiel wird die Designauswahl in Outlook Web App deaktiviert, wobei der Servername `fourthcoffee`, der Name des virtuellen Verzeichnisses `owa` und der Websitename `default web site` lautet.

    set-owavirtualdirectory -identity "fourthcoffee\owa (default web site)" -themeselectionenabled $false 

Sie können auch beide Befehle gleichzeitig ausführen, wie im folgenden Beispiel gezeigt:

    set-owavirtualdirectory -identity "fourthcoffee\owa (default web site)" -defaulttheme Custom -themeselectionenabled $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/bb123515\(v=exchg.150\)).

## Schritt 6: Ausführen von "iisreset/noforce" zum Speichern der Änderungen

Wenn Sie ein Design hinzufügen oder ändern bzw. den Namen oder die Sortierreihenfolge eines Designs ändern, werden diese Änderungen erst nach dem Beenden und erneuten Starten von Internetinformationsdienste (IIS) wirksam. Öffnen Sie hierzu ein Eingabeaufforderungsfenster auf dem Server, auf dem Sie das neue Design erstellt haben, und führen Sie den Befehl **iisresest /nforce** aus.

## Woher wissen Sie, dass diese Aufgabe erfolgreich war?

1.  Melden Sie sich mit dem virtuellen Verzeichnis auf dem Server, auf dem Sie das neue Design erstellt haben, bei Outlook Web App an. Zum Testen der Änderungen an der Standardwebsite auf dem Exchange-Server, auf dem sich das virtuelle Outlook Web App-Verzeichnis befindet, öffnen Sie Internet Explorer, und geben Sie die URL https://localhost/owa ein.

2.  Wechseln Sie zum benutzerdefinierten Design, indem Sie das Menü Einstellungen \> **Design** und dann das benutzerdefinierte Design auswählen.

## Ausführen von "iisreset/noforce", wenn die letzten Änderungen nicht wirksam wurden

1.  Wählen Sie auf der Symbolleiste von Internet Explorer das Menü Einstellungen \> **Internetoptionen** aus.

2.  Wählen Sie auf der Registerkarte **Allgemein** unter **Browserverlauf** die Option **Löschen** aus, und überprüfen Sie, ob **Temporäre Internet- und Websitedateien** aktiviert ist. Wählen Sie dann **Löschen** aus, um diese Dateien zu entfernen.

3.  Wählen Sie **OK** aus, um **Internetoptionen** zu schließen.

4.  Wählen Sie **Aktualisieren** aus, um die Änderungen anzuzeigen.

Möglicherweise müssen Sie diese Schritte immer dann wiederholen, wenn Sie Änderungen an den Designdateien vorgenommen haben. Wenn Sie mehrere Änderungen vornehmen, können Sie Outlook Web App geöffnet lassen und nach Bedarf **iisreset/noforce** auf dem Server ausführen sowie temporäre Dateien von Internet Explorer löschen.


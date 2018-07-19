---
title: 'Konfigurieren von Outlook zum Anzeigen des ursprünglichen Absenders im Quarantänepostfach: Exchange 2013 Help'
TOCTitle: Konfigurieren von Outlook zum Anzeigen des ursprünglichen Absenders im Quarantänepostfach
ms:assetid: 9249425d-1b06-48a0-ad95-c4eefb641ff4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee861109(v=EXCHG.150)
ms:contentKeyID: 50476245
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren von Outlook zum Anzeigen des ursprünglichen Absenders im Quarantänepostfach

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Die Spamquarantäne ist eine Funktion des Inhaltsfilter-Agents, durch die das Risiko reduziert wird, dass legitime Nachrichten verloren gehen. Die Spamquarantäne stellt einen temporären Speicherort für Nachrichten bereit, die als Spam erkannt wurden und nicht an ein Benutzerpostfach in der Organisation gesendet werden sollen.

Wenn eine Nachricht den Schwellenwert für Quarantäne erreicht, wird sie in einen Unzustellbarkeitsbericht (NDR, Non-Delivery Report) aufgenommen und an das Quarantänepostfach für Spam übergeben. Da die isolierten Nachrichten im Quarantänepostfach als Unzustellbarkeitsberichte gespeichert sind, wird die Postmasteradresse der Organisation als: Absenderadresse für alle Nachrichten angegeben. Wenn die Feldliste jedoch die Adresse des ursprünglichen Absenders, die Adresse des ursprünglichen Empfängers und die ursprüngliche SCL-Bewertung (Spam Confidence Level) enthielte, wäre die wiederherzustellende Nachricht leichter zu finden.

Standardmäßig können Sie diese Felder in Microsoft Outlook nicht auswählen. Bevor Sie diese Felder in der Nachrichtenansicht hinzufügen können, müssen Sie zuerst ein Outlook-Formular erstellen, mit dem der ursprüngliche Absender, der ursprüngliche Empfänger und die ursprüngliche SCL-Bewertung als optionale, auswählbare Felder hinzugefügt werden. Nach der Erstellung dieses benutzerdefinierten Formulars können Sie Outlook so konfigurieren, dass diese Felder in der Nachrichtenansicht angezeigt werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieses Verfahrens: 15 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachzugriff" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Für dieses Verfahren muss das Antispam-Quarantänepostfach konfiguriert sein. Weitere Informationen finden Sie unter [Konfigurieren eines Spamquarantänepostfachs](configure-a-spam-quarantine-mailbox-exchange-2013-help.md).

  - Um das Quarantänepostfach zuzugreifen, müssen Sie ein Outlook-Profil für dieses Postfach zu konfigurieren, und öffnen Sie das Postfach mithilfe von Outlook. Weitere Informationen zum Konfigurieren und verwenden mehrere Outlook-Profilen finden Sie unter [Übersicht über die in Outlook](https://go.microsoft.com/fwlink/p/?linkid=178975).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Schritt 1: Erstellen eines benutzerdefinierten Outlook-Formulars mit Editor

1.  Öffnen Sie Editor, und kopieren Sie den folgenden Code in das Dokument.
    
        [Description]
        MessageClass=IPM.Note
        CLSID={00020D31-0000-0000-C000-000000000046}
        DisplayName=Quarantine Extension Form
        Category=Standard
        Subcategory=Form
        Comment=This form allows the Original Sender (ReceivedRepresentingEmailAddress), Original Recipient (To), and Original SCL (OriginalScl) values to be viewed as columns.
        LargeIcon=IPML.ico
        SmallIcon=IPMS.ico
        Version=3.0
        Locale=enu
        Hidden=1
        Owner=Microsoft Corporation
        Contact=Your Name
        
        [Platforms]
        Platform1=Win16
        Platform2=NTx86
        Platform9=Win95
        
        [Platform.Win16]
        CPU=ix86
        OSVersion=Win3.1
        
        [Platform.NTx86]
        CPU=ix86
        OSVersion=WinNT3.5
        
        [Platform.Win95]
        CPU=ix86
        OSVersion=Win95
        
        [Properties]
        Property01=ReceivedRepresentingEmailAddress
        Property02=DisplayTo
        Property03=OriginalScl
        
        [Property.ReceivedRepresentingEmailAddress]
        Type=31
        NmidInteger=0x0078
        DisplayName=ReceivedRepresentingEmailAddress
        
        [Property.DisplayTo]
        Type=31
        NmidInteger=0x0E04
        DisplayName=DisplayTo
        
        [Property.OriginalScl]
        Type=3
        NmidPropset={41F28F13-83F4-4114-A584-EEDB5A6B0BFF}
        NmidString=OriginalScl
        DisplayName=OriginalScl
        
        [Verbs]
        Verb1=1
        
        [Verb.1]
        DisplayName=&Open
        Code=0
        Flags=0
        Attribs=2
        
        [Extensions]
        Extensions1=1
        
        [Extension.1]
        Type=31
        NmidPropset={00020D0C-0000-0000-C000-000000000046}
        NmidInteger=1
        Value=1000000000000000

2.  Speichern Sie die Datei im Ordner "Office Forms" mit den folgenden Werten:
    
      - **Pfad** *\<Office-Installationspfad\>*\\\<*OfficeVersion\>*\\Forms\\*\<LCID\>*
        
          - *\<Office-Installationspfad\>*   Für 32-Bit-Versionen von Office unter 32-Bit-Versionen von Microsoft Windows oder 64-Bit-Versionen von Office unter 64-Bit-Versionen von Windows lautet der Standardpfad `C:\Program Files\Microsoft Office`. Für 32-Bit-Versionen von Office unter 64-Bit-Versionen von Windows lautet der Standardpfad `C:\Program Files (x86)\Microsoft Office`.
        
          - *\<OfficeVersion\>*   Für Outlook 2007 lautet der Wert `Office12`. Für Outlook 2010 lautet der Wert `Office14`. Für Outlook 2013 lautet der Wert `Office15`.
        
          - *\<LCID\>*   Dies ist der Wert für Ihre Gebietsschema-ID (LCID). Beispielsweise ist die LCID für US-Englisch 1033. Weitere Informationen finden Sie unter [KB221435: Liste der unterstützten Gebietsschemabezeichner in Word](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=221435).
    
      - **Name**   Nehmen Sie für den Rest dieses Verfahrens an, dass der Dateiname `QTNE.cfg` lautet. Der Name der Datei ist nicht von Bedeutung; schließen Sie den Wert jedoch unbedingt in Anführungszeichen ein, damit die Datei als QTNE.cfg und nicht als QTNE.cfg.txt gespeichert wird.
    
    Wenn Sie beispielsweise über eine 32-Bit-Version von Outlook 2013 auf US-Englisch verfügen, die unter einer 64-Bit-Version von Windows installiert ist, speichern Sie die Datei als:
    
        "C:\Program Files (x86)\Microsoft Office\Office15\Forms\1033\QTNE.cfg"
    

    > [!NOTE]
    > Wenn die Windows-Benutzerzugriffssteuerung (User Access Control, UAC) verhindert, dass Sie die Datei am richtigen Speicherort speichern können, speichern Sie sie zuerst an einem temporären Speicherort, und kopieren Sie die Datei dann.



## Schritt 2: Konfigurieren von Outlook für die Verwendung des benutzerdefinierten Outlook-Formulars

Verwenden Sie eines der folgenden Verfahren, abhängig davon, welche Version von Outlook auf Ihrem Computer installiert ist.

## Konfigurieren von Outlook 2010 oder Outlook 2013

1.  Klicken Sie in Outlook 2010 oder Outlook 2013 auf **Datei** \> **Optionen** \> **Erweitert**.

2.  Klicken Sie im Abschnitt **Entwickler** auf **Benutzerdefinierte Formulare**.

3.  Klicken Sie im Dialogfeld **Optionen** auf **Formulare verwalten**.

4.  Klicken Sie im Dialogfeld **Formular-Manager** auf **Installieren**. Navigieren Sie zum Speicherort der Datei `QTNE.cfg`, wählen Sie die Datei aus, und klicken Sie auf **Öffnen**. Überprüfen Sie die Informationen im Dialogfeld **Formulareigenschaften**, und klicken Sie dann auf **OK**, um das Quarantäneerweiterungsformular in Ihrer Bibliothek für persönliche Formulare zu installieren.

5.  Klicken Sie im Dialogfeld **Formular-Manager** auf **Schließen**. Klicken Sie zweimal auf **OK**, um die verbleibenden Dialogfelder zu schließen und zur Hauptbenutzeroberfläche von Outlook zurückzukehren.

6.  Klicken Sie auf der Registerkarte **Start** in der Ansicht **E-Mail** des Posteingangs mit der rechten Maustaste auf die Spaltenüberschriftenzeile (Sie müssen die Breite der Nachrichtenliste möglicherweise vergrößern, um die Spalten zu sehen), und wählen Sie dann **Ansichtseinstellungen** aus.

7.  Klicken Sie im Dialogfeld **Erweiterte Ansichtseinstellungen** auf **Spalten**.

8.  Führen Sie im Dialogfeld **Spalten anzeigen** in der Dropdownliste **Verfügbare Spalten auswählen aus** einen Bildlauf zum Ende der Liste durch, und wählen Sie **Formulare** aus.

9.  Wählen Sie im Dialogfeld **Wählen Sie Unternehmensformulare für diesen Ordner aus** im Feld **Ausgewählte Formulare** den Eintrag **Nachricht** aus, und klicken Sie auf **Entfernen**. Wählen Sie im Feld **Persönliche Formulare** den Eintrag **Quarantäneerweiterungsformular** aus, und klicken Sie dann auf **Hinzufügen**. Klicken Sie nach Abschluss des Vorgangs auf **Schließen**.

10. Wählen Sie im Dialogfeld **Spalten anzeigen** im Abschnitt **Verfügbare Spalten** mindestens eines der folgenden Felder aus, und klicken Sie nach jedem ausgewählten Feld auf **Hinzufügen**.
    
      - **ReceivedRepresentingEmailAddress**   Ursprünglicher Absender
    
      - **DisplayTo**   Ursprünglicher Empfänger (beachten Sie, dass dies nach dem Hinzufügen als **An** angezeigt wird)
    
      - **OriginalScl**   Ursprüngliche SCL-Bewertung
    
    Verwenden Sie die Schaltflächen **Nach oben** und **Nach unten**, um die Spalten in der Ansicht zu positionieren. Für beste Ergebnisse positionieren Sie die drei neuen Felder nach dem Feld **Anlage** und vor dem Feld **Von**. Klicken Sie nach Abschluss des Vorgangs zweimal auf **OK**, um zur Hauptbenutzeroberfläche Outlook zurückzukehren.

## Konfigurieren von Outlook 2007

1.  Klicken Sie in Outlook 2007 auf **Extras** \> **Optionen**.

2.  Klicken Sie im Dialogfeld **Optionen** auf die Registerkarte **Weitere**, und klicken Sie dann unter **Allgemein** auf **Erweiterte Optionen**.

3.  Klicken Sie im Dialogfeld **Erweiterte Optionen** auf **Benutzerdefinierte Formulare**, und klicken Sie dann im Dialogfeld **Benutzerdefinierte Formulare** auf **Formulare verwalten**.

4.  Klicken Sie im Dialogfeld **Formular-Manager** auf **Installieren**. Navigieren Sie zum Speicherort der Datei `QTNE.cfg`, wählen Sie die Datei aus, und klicken Sie auf **Öffnen**. Überprüfen Sie die Informationen im Dialogfeld **Formulareigenschaften**, und klicken Sie dann auf **OK**, um das Quarantäneerweiterungsformular in Ihrer Bibliothek für persönliche Formulare zu installieren.

5.  Schließen Sie das Dialogfeld **Formular-Manager**, und klicken Sie dann dreimal auf **OK**, um die verbleibenden Dialogfelder zu schließen und zur Hauptbenutzeroberfläche von Outlook 2007 zurückzukehren.

6.  Klicken Sie in der Ansicht **E-Mail** des Posteingangs mit der rechten Maustaste auf die Spaltenüberschriftenzeile (Sie müssen die Breite der Nachrichtenliste möglicherweise vergrößern, um die Spalten zu sehen), und wählen Sie dann **Aktuelle Ansicht anpassen** aus.

7.  Klicken Sie im Dialogfeld **Ansicht anpassen: Nachrichten** auf **Felder anzeigen**.

8.  Führen Sie im Dialogfeld **Felder anzeigen** in der Dropdownliste **Verfügbare Felder auswählen aus** einen Bildlauf zum Ende der Liste durch, und wählen Sie **Formulare** aus.

9.  Wählen Sie im Dialogfeld **Wählen Sie Unternehmensformulare für diesen Ordner aus** im Feld **Ausgewählte Formulare** den Eintrag **Nachricht** aus, und klicken Sie auf **Entfernen**. Wählen Sie im Feld **Persönliche Formulare** den Eintrag **Quarantäneerweiterungsformular** aus, und klicken Sie dann auf **Hinzufügen**. Klicken Sie nach Abschluss des Vorgangs auf **Schließen**.

10. Wählen Sie im Dialogfeld **Felder anzeigen** im Abschnitt **Verfügbare Felder** mindestens eines der folgenden Felder aus, und klicken Sie nach jedem ausgewählten Feld auf **Hinzufügen**.
    
      - **ReceivedRepresentingEmailAddress**   Ursprünglicher Absender
    
      - **DisplayTo**   Ursprünglicher Empfänger (beachten Sie, dass dies nach dem Hinzufügen als **An** angezeigt wird)
    
      - **OriginalScl**   Ursprüngliche SCL-Bewertung
    
    Verwenden Sie die Schaltflächen **Nach oben** und **Nach unten**, um die Spalten in der Ansicht zu positionieren. Für beste Ergebnisse positionieren Sie die drei neuen Felder nach dem Feld **Anlage** und vor dem Feld **Von**. Klicken Sie nach Abschluss des Vorgangs zweimal auf **OK**, um zur Hauptbenutzeroberfläche Outlook 2007 zurückzukehren.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn das Verfahren erfolgreich war, sehen Sie in Outlook die Werte für den ursprünglichen Absender, ursprünglichen Empfänger und ursprünglichen SCL-Wert für isolierte Nachrichten im Spam-Quarantänepostfach.


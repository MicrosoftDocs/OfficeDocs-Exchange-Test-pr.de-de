---
title: 'Erstellen der Menünavigation: Exchange Online Help'
TOCTitle: Erstellen der Menünavigation
ms:assetid: 3cfc9a01-0a61-4d15-9561-621568dc30d9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997471(v=EXCHG.150)
ms:contentKeyID: 50475422
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.UnifiedMessaging.AutoAttendantKeyMappingControl
ms.translationtype: MT
---

# Erstellen der Menünavigation

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Können Sie der Seite **neue menünavigationseintrags** zum Erstellen von einzelnen oder mehreren tastenzuordnungen Business oder Hauptmenü außerhalb der Geschäftszeiten für automatische Telefonzentralen aufgefordert wird. Sie können die Aktion definieren, die ausgeführt wird, wenn eine Taste auf der Telefontastatur den Aufruf von einer Durchwahlnummer oder eine andere automatische Telefonzentrale übertragen gedrückt wird, beispielsweise.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/um-auto-attendant-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## UM automatische Telefonzentrale Navigationsmenüs konfigurieren mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** UM-Telefonzentrale für die Sie Menünavigation erstellen möchten. Klicken Sie auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Auf der Seite **UM-Telefonzentrale** auf **Menünavigation**, wählen Sie **aktivieren die Menünavigation Geschäftszeiten** oder **Aktivieren der Menünavigation außerhalb der Geschäftszeiten** aus und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Konfigurieren Sie auf der Seite **neue menünavigationseintrags** Folgendes ein:
    
      - **Telefonansage**   Geben Sie in dieses Feld den Namen des neuen Navigationsmenüs ein. Der Navigationsmenüname wird nur für Anzeigezwecke verwendet. Dieses Feld ist erforderlich.
        
        Da Sie möglicherweise mehrere neue Navigationsmenüs festlegen möchten, sollten Sie für die Tastenzuordnungen aussagekräftige Namen verwenden. Die maximale Länge des Namens für eine Tastenzuordnung beträgt 64 Zeichen inklusive Leerzeichen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **Wenn diese Taste gedrückt wird**   Mithilfe dieser Liste können Sie die Tastenzuordnungen aktivieren. Die Tastenzuordnung ist die Zahlentaste, die ein Anrufer drückt, um die automatische Telefonzentrale einen bestimmten Vorgang ausführen zu lassen, wie zum Beispiel die Weiterleitung des Anrufers an eine andere automatische Telefonzentrale oder an eine Vermittlungsstelle. Standardmäßig sind keine Einträge festgelegt.
        
        Verwenden Sie die Dropdown-Liste, um den numerischen Schlüssel (von 1 bis 9) auswählen, den der Anrufer drücken muss. Null (0) ist für die automatische Telefonzentrale-Operator reserviert.
        
        Wenn Sie in der Dropdownliste die Option **Timeout** auswählen, können Anrufer an eine Durchwahlnummer oder eine automatische Telefonzentrale weitergeleitet werden, wenn sie innerhalb einer bestimmten Zeit keine Taste auf der Telefontastatur drücken. Zum Beispiel "Bitte legen Sie nicht auf. Ihr Anruf wird vom nächsten freien Mitarbeiter entgegengenommen." Die Standardeinstellung ist 5 Sekunden. Wenn Sie diese Option aktivieren, wird eine leere Tastenzuordnung erstellt.
    
      - **Die folgende Audiodatei wiedergeben**    Verwenden Sie diese Option, um eine zuvor aufgezeichnete Audiodatei für Anrufer auszuwählen. Klicken Sie auf **Ändern**, und klicken Sie dann auf **Durchsuchen**, um die Audiodatei zu suchen.
    
      - **Folgende zusätzliche Aktion ausführen**   Wählen Sie eine der folgenden Optionen aus, um die Aktion festzulegen, die von der automatischen Telefonzentrale für den Anrufer ausgeführt werden soll:
        
          - **None**    Wenn Sie nicht an die automatische Telefonzentrale Weiterleiten des Anrufs an eine Erweiterung oder an eine andere automatische Telefonzentrale oder für einen Benutzer eine Nachricht hinterlassen möchten, verwenden Sie diese Option aus.
        
          - **Weiterleiten an diese Durchwahl**   Wählen Sie diese Option aus, damit Anrufe an eine Durchwahlnummer weitergeleitet werden können. Wenn Sie diese Option aktivieren, geben Sie die Durchwahlnummer, an die der Anruf weitergeleitet wird, in das Feld ein. In diesem Feld werden nur numerische Zeichen akzeptiert. Die folgenden Zeichen dürfen nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
        
          - **Weiterleiten an diese automatische UM-Telefonzentrale**   Wählen Sie diese Option, um den Anruf an eine automatische Telefonzentrale weiterzuleiten. Klicken Sie auf **Durchsuchen**, um die automatische Telefonzentrale zu suchen, die Sie verwenden möchten. Vor dem Aktivieren dieser Option müssen Sie zunächst eine automatische Telefonzentrale erstellen und konfigurieren. Diese Option wird verwendet, wenn Sie eine über- und untergeordnete Struktur von automatischen UM-Telefonzentralen erstellen.
        
          - **Sprachnachricht für diesen Benutzer hinterlassen**   Wählen Sie diese Option aus, damit ein Anrufer eine Voicemailnachricht für einen Benutzer hinterlassen kann, der sich im selben Wählplan wie die automatische UM-Telefonzentrale befindet, die Sie konfigurieren. Wenn ein Anrufer diese Option aus dem Menü einer automatischen Telefonzentrale auswählt, wird er zum Hinterlassen einer Sprachnachricht für den ausgewählten Benutzer aufgefordert. Klicken Sie auf **Durchsuchen**, um den UM-aktivierten Benutzer ausfindig zu machen.
        
          - **Unternehmensstandort ansagen**   Wählen Sie diese Option aus, damit ein Anrufer eine Menüoption einer automatischen Telefonzentrale auswählen und den Standort des Unternehmens angesagt bekommen kann, das für die automatische UM-Telefonzentrale konfiguriert ist. Damit dies ordnungsgemäß funktioniert, müssen Sie zuerst den Unternehmensstandort in das Feld **Unternehmensstandort** auf der Registerkarte **Allgemein** der automatischen UM-Telefonzentrale eingeben.
        
          - **Geschäftszeiten ansagen**   Wählen Sie diese Option aus, damit ein Anrufer eine Menüoption einer automatischen Telefonzentrale auswählen und die Geschäftszeiten für das Unternehmen angesagt bekommen kann, das für die automatische UM-Telefonzentrale konfiguriert ist. Damit dies ordnungsgemäß funktioniert, müssen Sie zuerst die Geschäftszeiten auf der Seite **Geschäftszeiten** der automatischen UM-Telefonzentrale eingeben.

5.  Klicken Sie auf **OK**, um die neue Menünavigation zu erstellen.

6.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** auf **Speichern**, um Ihre Änderungen zu speichern.

## Verwenden der Shell zum Konfigurieren von UM Auto attendant tastenzuordnungen

Dieses Beispiel aktiviert die Geschäftszeiten den tastenzuordnungen, damit:

  - Wenn Anrufer 1 drücken, werden sie zu einer anderen UM-Telefonzentrale mit dem Namen `SalesAutoAttendant`weitergeleitet werden.

  - Wenn sie 2 drücken, werden diese Durchwahlnummer 12345 für den Support weitergeleitet werden.

  - Wenn sie 3 drücken, werden sie an eine andere automatische Telefonzentrale gesendet werden, die eine Audiodatei wiedergegeben werden.

<!-- end list -->

    Set-UMAutoAttendant -id MyAutoAttendant -BusinessHoursKeyMappingEnabled $true -BusinessHoursKeyMapping "1,Sales,,SalesAutoAttendant","2,Support,12345","3,Directions,,,directions.wav"

Dieses Beispiel legt den tastenzuordnungen, die in einer durch Trennzeichen getrennten Werten (CSV)-Datei definiert. Sie müssen zuerst die CSV-Datei mit den folgenden Überschriften und der AutoKorrektur-Eintrag erstellen: \< Schlüssel \>, \< Beschreibung \>, \[\< Erweiterung \>\] \[\< Autoattendant Name \>\], \[\< Promptfilenamepath \>\], \[\< asrphrase1; asrphrase2 \>\], \[\< Leavevoicemailfor \>\], \[\< Transfertomailbox \>\]. Die Werte in Klammern sind optional. Importieren Sie nach dem Erstellen der CSV-Datei, die CSV-Datei mit dem Cmdlet **Import-csv** .

    $o = Import-csv -path "C:\UMFiles\AutoAttendants\keymappings.csv"
    Set-UMAutoAttendant MyAutoAttendant -BusinessHoursKeyMapping $o

In diesem Beispiel wird den tastenzuordnungen aus einer vorhandenen UM-Telefonzentrale in eine CSV-Datei exportiert und importiert dann die gleichen tastenzuordnungen in eine andere UM-Telefonzentrale. Sie konnte den tastenzuordnungen auch in eine CSV-Datei exportieren, bearbeiten oder ändern die Zuordnung für den Schlüssel in der CSV-Datei und dann diese tastenzuordnungen in einer anderen UM-Telefonzentrale zu importieren.

    $aa = Get-UMAutoAttendant -id MyAutoAttendant
    $aa1 = Get-UMAutoAttendant -id MyAutoAttendant2
    $aa.BusinessHoursKeyMapping | Export-csv -path "C:\UMFiles\AutoAttendants\keymappings.csv"
    $aa1.BusinessHoursKeyMapping = (Import-csv -path "C:\UMFiles\AutoAttendants\keymappings.csv")


---
title: 'Erstellen Sie außerhalb der Geschäftszeiten Navigationsmenüs: Exchange Online Help'
TOCTitle: Erstellen Sie außerhalb der Geschäftszeiten Navigationsmenüs
ms:assetid: bfe81ed6-9648-4882-8baf-ac93ea30a8ca
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232175(v=EXCHG.150)
ms:contentKeyID: 50476614
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen Sie außerhalb der Geschäftszeiten Navigationsmenüs

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Für eine automatische UM-Telefonzentrale (Unified Messaging) können Sie Tastenzuordnungen für Nicht-Geschäftszeiten aktivieren. Nachdem Sie eine automatische UM-Telefonzentrale erstellt haben, hören Anrufer eine Standardsystemansage als Begrüßungsansage für das Hauptmenü außerhalb der Geschäftszeiten, nachdem die Begrüßung außerhalb der Geschäftszeiten wiedergegeben wurde. Die standardmäßige Hauptmenüansage außerhalb der Geschäftszeiten lautet "Willkommen bei der automatischen Telefonzentrale von Microsoft Exchange außerhalb der Geschäftszeiten." Da standardmäßig keine Tastenzuordnungen definiert sind, stehen dem Anrufer keine Menüoptionen zur Verfügung und er hört nur die standardmäßige Hauptmenüansage außerhalb der Geschäftszeiten.

Beim Konfigurieren von Tastenzuordnungen definieren Sie die Optionen und Vorgänge, die durchgeführt werden, wenn ein Anrufer bei Verwendung einer sprachaktivierten automatischen Telefonzentrale ein bestimmtes Wort sagt oder bei Verwendung einer nicht sprachaktivierten automatischen Telefonzentrale eine Taste auf der Telefontastatur drückt.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren von Tastenzuordnungen für Nicht-Geschäftszeiten für eine automatische UM-Telefonzentrale mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** eine automatische UM-Telefonzentrale aus, für die Sie ein Navigationsmenü für Nicht-Geschäftszeiten erstellen möchten. Klicken Sie auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** unter **Menünavigation außerhalb der Geschäftszeit** auf **Menünavigation**, wählen Sie **Menünavigation außerhalb der Geschäftszeit aktivieren** aus, und klicken Sie die dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Verwenden Sie auf der Seite **Neuer Menünavigationseintrag** folgende Optionen, um einen neuen Menünavigationseintrag zu erstellen:
    
      - **Telefonansage**   Geben Sie in dieses Feld den Namen des neuen Navigationsmenüs ein. Der Navigationsmenüname wird nur für Anzeigezwecke verwendet. Dieses Feld ist erforderlich.
        
        Da Sie möglicherweise mehrere neue Navigationsmenüs festlegen möchten, sollten Sie für die Tastenzuordnungen aussagekräftige Namen verwenden. Die maximale Länge des Namens für eine Tastenzuordnung beträgt 64 Zeichen inklusive Leerzeichen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **Wenn diese Taste gedrückt wird**   Mithilfe dieser Liste können Sie die Tastenzuordnungen aktivieren. Die Tastenzuordnung ist die Zahlentaste, die ein Anrufer drückt, um die automatische Telefonzentrale einen bestimmten Vorgang ausführen zu lassen, wie zum Beispiel die Weiterleitung des Anrufers an eine andere automatische Telefonzentrale oder an eine Vermittlungsstelle. Standardmäßig sind keine Einträge festgelegt.
        
        Verwenden Sie die Dropdownliste, um die Zifferntaste (1 bis 9) auszuwählen, die der Anrufer drücken muss. Null (0) ist für die Vermittlungsstelle der automatischen Telefonzentrale reserviert.
        
        Wenn Sie in der Dropdownliste die Option **Timeout** auswählen, können Anrufer an eine Durchwahlnummer oder eine automatische Telefonzentrale weitergeleitet werden, wenn sie innerhalb einer bestimmten Zeit keine Taste auf der Telefontastatur drücken. Zum Beispiel "Bitte legen Sie nicht auf. Ihr Anruf wird vom nächsten freien Mitarbeiter entgegengenommen." Die Standardeinstellung ist 5 Sekunden. Wenn Sie diese Option aktivieren, wird eine leere Tastenzuordnung erstellt.
    
      - **Folgende Audiodatei wiedergeben**   Über diese Option können Sie eine zuvor aufgezeichnete Audiodatei für Anrufer auswählen. Klicken Sie auf **Ändern** und dann auf **Durchsuchen**, um die Audiodatei ausfindig zu machen. Wenn Sie für die Audiodatei die Standardeinstellung \<Keine\> übernehmen, erzeugt das UM-Text-Sprache-Modul (TTS) eine Hauptmenüansage außerhalb der Geschäftszeiten. Alternativ dazu können Sie auch für eine sprachaktivierte Telefonzentrale eine benutzerdefinierte Audiodatei für die Hauptmenüansage außerhalb der Geschäftszeiten erstellen, die beispielsweise so lauten könnte: "Sie rufen außerhalb der Geschäftszeiten bei Contoso an. Wenn Sie eine Sprachnachricht für den Vertrieb hinterlassen möchten, sagen Sie 1. Wenn Sie eine Sprachnachricht für den technischen Support hinterlassen möchten, sagen Sie 2. Wenn Sie eine Sprachnachricht für die Verwaltung hinterlassen möchten, sagen Sie 3. Wenn Sie mit der Vermittlung sprechen möchten, drücken Sie die 0."
    
      - **Folgende zusätzliche Aktion ausführen**   Wählen Sie eine der folgenden Optionen aus, um die Aktion festzulegen, die von der automatischen Telefonzentrale für den Anrufer ausgeführt werden soll:
        
          - **Keine**   Verwenden Sie diese Option, wenn Sie nicht möchten, dass die automatische Telefonzentrale einen Anruf an eine Durchwahl oder eine andere automatische Telefonzentrale weiterleitet, oder wenn Sie nicht möchten, dass Anrufer eine Nachricht hinterlassen können.
        
          - **Weiterleiten an diese Durchwahl**   Wählen Sie diese Option aus, damit Anrufe an eine Durchwahlnummer weitergeleitet werden können. Wenn Sie diese Option aktivieren, verwenden Sie das Feld, um die Durchwahlnummer einzugeben, an die der Anruf weitergeleitet wird. In diesem Feld werden nur numerische Zeichen akzeptiert. Die folgenden Zeichen dürfen nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
        
          - **Weiterleiten an diese automatische UM-Telefonzentrale**   Wählen Sie diese Option, um den Anruf an eine vorhandene automatische Telefonzentrale weiterzuleiten. Klicken Sie auf **Durchsuchen**, um die automatische Telefonzentrale zu suchen, die Sie verwenden möchten. Vor dem Aktivieren dieser Option müssen Sie zunächst eine automatische Telefonzentrale erstellen und konfigurieren. Diese Option wird verwendet, wenn Sie eine über- und untergeordnete Struktur von automatischen UM-Telefonzentralen erstellen.
        
          - **Sprachnachricht für diesen Benutzer hinterlassen**   Wählen Sie diese Option aus, damit ein Anrufer eine Voicemailnachricht für einen Benutzer hinterlassen kann, der sich im selben Wählplan wie die automatische UM-Telefonzentrale befindet, die Sie konfigurieren. Wenn ein Anrufer diese Option aus dem Menü einer automatischen Telefonzentrale auswählt, wird er zum Hinterlassen einer Sprachnachricht für den ausgewählten Benutzer aufgefordert. Klicken Sie auf **Durchsuchen**, um den UM-aktivierten Benutzer ausfindig zu machen.
        
          - **Unternehmensstandort ansagen**   Wählen Sie diese Option aus, damit ein Anrufer eine Menüoption einer automatischen Telefonzentrale auswählen und den Standort des Unternehmens angesagt bekommen kann, das für die automatische UM-Telefonzentrale konfiguriert ist. Damit dies ordnungsgemäß funktioniert, müssen Sie zuerst den Unternehmensstandort in das Feld **Unternehmensstandort** auf der Registerkarte **Allgemein** der automatischen UM-Telefonzentrale eingeben.
        
          - **Geschäftszeiten ansagen**   Wählen Sie diese Option aus, damit ein Anrufer eine Menüoption einer automatischen Telefonzentrale auswählen und die Geschäftszeiten für das Unternehmen angesagt bekommen kann, das für die automatische UM-Telefonzentrale konfiguriert ist. Damit dies ordnungsgemäß funktioniert, müssen Sie zuerst die Geschäftszeiten auf der Seite **Geschäftszeiten** der automatischen UM-Telefonzentrale eingeben.

5.  Klicken Sie auf **OK**, um die neue Menünavigation zu erstellen.

6.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** auf **Speichern**, um Ihre Änderungen zu speichern.

## Aktivieren von Tastenzuordnungen außerhalb der Geschäftszeiten für eine automatische UM-Telefonzentrale mithilfe der Shell

In diesem Beispiel wird eine automatische UM-Telefonzentrale `MyAutoAttendant` konfiguriert, und die Tastenzuordnungen außerhalb der Geschäftszeiten werden so aktiviert, dass Anrufer, wenn Sie "After Hours" sagen, an die Durchwahl 12345 weitergeleitet werden. Wenn die Anrufer "Directions" sagen, werden sie an die Durchwahl 23456 weitergeleitet.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -AfterHoursKeyMappingEnabled $true -AfterHoursKeyMapping "AfterhoursOperator,12345","Directions,23456"


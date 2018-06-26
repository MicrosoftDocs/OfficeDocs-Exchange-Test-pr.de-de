---
title: 'Verwalten einer automatischen UM-Telefonzentrale: Exchange 2013 Help'
TOCTitle: Verwalten einer automatischen UM-Telefonzentrale
ms:assetid: 4809ff56-ae34-4ce6-8e39-9193311c3f83
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997867(v=EXCHG.150)
ms:contentKeyID: 50475593
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.UnifiedMessaging.AutoAttendantGeneralPropertyPage
ms.translationtype: HT
---

# Verwalten einer automatischen UM-Telefonzentrale

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-04-30_

Nach der Erstellung einer automatischen Unified Messaging-Telefonzentrale (UM) können Sie eine Reihe von Einstellungen anzeigen oder konfigurieren. Sie können beispielsweise der automatischen Telefonzentrale zugeordnete Durchwahlnummern hinzufügen, entfernen und ändern. Sie können außerdem die automatische Spracherkennung (Automatic Speech Recognition, ASR) für die automatische Telefonzentrale aktivieren oder deaktivieren und die Begrüßungen ändern, die innerhalb und außerhalb der Geschäftszeiten verwendet werden.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anzeigen oder Konfigurieren von Eigenschaften einer automatischen UM-Telefonzentrale mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie anzeigen oder konfigurieren möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  
    
    Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** auf **Allgemein**, um schreibgeschützte Informationen zur automatischen UM-Telefonzentrale anzuzeigen und Verwaltungsaufgaben für eine automatische UM-Telefonzentrale auszuführen:
    
      - **UM-Wählplan**   In diesem Feld wird der UM-Wählplan angezeigt, dem die automatische Telefonzentrale zugeordnet ist. Nach dem Erstellen einer automatischen Telefonzentrale können die der automatischen Telefonzentrale zugeordneten Wähleinstellungen nicht geändert werden. Wenn einer automatischen Telefonzentrale andere Wähleinstellungen zugeordnet werden sollen, müssen Sie die Wähleinstellungen löschen und der automatischen Telefonzentrale die gewünschten Wähleinstellungen zuordnen, nachdem Sie diese neu erstellt haben.
    
      - **Name**   In diesem Feld wird der Name angezeigt, der der automatischen Telefonzentrale bei deren Erstellung zugewiesen wurde. Dies ist der Name, der in der Exchange-Verwaltungskonsole angezeigt wird.
    
      - **Status**   In diesem Feld wird angezeigt, ob die automatische UM-Telefonzentrale aktiviert oder deaktiviert ist. Schließen Sie die Seite **Automatische UM-Telefonzentrale** und verwenden Sie die Symbolleiste unterhalb von **Automatische UM-Telefonzentralen** auf der Seite **UM-Wählplan**, um die automatische Telefonzentrale zu aktivieren oder zu deaktivieren.
    
      - **Zugriffsnummern**   Verwenden Sie dieses Feld zur Eingabe einer Durchwahl- oder Zugriffsnummer, mit der Anrufer an die automatische Telefonzentrale weitergeleitet werden. Standardmäßig werden bei der Erstellung einer automatischen Telefonzentrale keine Durchwahl- oder Zugriffsnummern konfiguriert.
        
        Die Anzahl von Ziffern der angegebenen Durchwahl- oder Zugriffsnummer muss mit der Anzahl von Ziffern für eine Durchwahlnummer übereinstimmen, die in den UM-Wähleinstellungen konfiguriert ist, die der automatischen UM-Telefonzentrale zugeordnet sind. Darüber hinaus können Sie diesem Feld eine SIP-Adresse (Session Initiation Protocol) hinzufügen. Eine SIP-Adresse wird von einigen IP-Nebenstellenanlagen, SIP-aktivierten Nebenstellenanlagen und Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server verwendet.
        
        Sie können die neue automatische Telefonzentrale auch ohne Durchwahl- oder Zugriffsnummer erstellen. Geben Sie zum Hinzufügen einer Durchwahl die Nummer in diesem Feld ein, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Sie können einer automatischen Telefonzentrale mehrere Nummern zuordnen. Sie können eine vorhandene Zugriffsnummer auch bearbeiten oder entfernen. Klicken Sie zum Bearbeiten einer vorhandenen Nummer auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Markieren Sie zum Entfernen einer Durchwahlnummer diese in der Liste, und klicken Sie auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").
    
      - **Automatische Telefonzentrale zum Beantworten von Sprachbefehlen festlegen**   Aktivieren Sie dieses Kontrollkästchen, damit Anrufer per Spracheingabe auf Ansagen der automatischen Telefonzentrale reagieren können, um im Menüsystem zu navigieren. Standardmäßig wird eine automatische Telefonzentrale nicht als sprachaktiviert erstellt.
        
        Wenn Sie die automatische UM-Telefonzentrale ohne Sprachaktivierung erstellen, können Sie nach Erstellung der automatischen UM-Telefonzentrale die Exchange-Verwaltungskonsole oder die Shell verwenden, um die Sprachaktivierung für die Telefonzentrale vorzunehmen.
    
      - **Verwenden Sie diese automatische Telefonzentrale, wenn die Sprachbefehle nicht ordnungsgemäß funktionieren**   Klicken Sie auf **Durchsuchen**, um die automatische Telefonzentrale auszuwählen, die verwendet werden soll, wenn Sprachbefehle nicht funktionieren. Diese wird auch als automatische DTMF-Fallback-Telefonzentrale bezeichnet. Eine automatische DTMF-Fallback-Telefonzentrale kann nur verwendet werden, wenn Sie die Option **Verwenden Sie diese automatische Telefonzentrale, wenn die Sprachbefehle nicht ordnungsgemäß funktionieren** aktiviert haben. Sie müssen zunächst eine automatische DTMF-Fallback-Telefonzentrale erstellen und dann auf die Schaltfläche **Durchsuchen** klicken, um nach der geeigneten automatischen DTMF-Telefonzentrale zu suchen.
        
        Eine automatische DTMF-Fallback-Telefonzentrale wird verwendet, wenn die sprachaktivierte automatische UM-Telefonzentrale die Spracheingaben des Anrufers nicht erkennen kann. Bei Einsatz der automatischen DTMF-Telefonzentrale muss der Anrufer DTMF-Eingaben verwenden, um durch das Menüsystem zu navigieren, den Namen eines Benutzers zu buchstabieren oder eine benutzerdefinierte Menüansage zu verwenden. Ein Anrufer kann nicht mithilfe von Sprachbefehlen durch diese automatische Telefonzentrale navigieren.
        
        Wenn Sie keine automatische DTMF-Fallback-Telefonzentrale konfigurieren, empfehlen wir die Angabe einer Durchwahlnummer für die Vermittlungsstelle in der automatischen Telefonzentrale. Wenn keine Durchwahlnummer für die Vermittlungsstelle konfiguriert wird und Benutzer eine sprachaktivierte automatische Telefonzentrale verwenden, das System die Spracheingaben aber nicht erkennt, können die Benutzer nicht durch das System navigieren und nicht an eine Vermittlungsstelle weitergeleitet werden.
        
        Obwohl es nicht erforderlich ist, empfehlen wir, für die automatische DTMF-Fallback-Telefonzentrale dieselbe Konfiguration wie für die sprachaktivierte automatische Telefonzentrale zu verwenden. Die automatische DTMF-Fallback-Telefonzentrale darf nicht sprachaktiviert sein.
    
      - **Sprache für automatisierte Sprachschnittstelle**   Verwenden Sie diese Liste zur Auswahl der Sprache, die für Ansagen der automatischen Telefonzentrale verwendet wird. Die Standardsprache wird bei der Installation von Microsoft Exchange festgelegt. Bei lokalen und Hybridbereitstellungen wird als Standardsprache "U.S. English" verwendet, da die automatische Telefonzentrale die Spracheinstellung im UM-Wählplan verwendet. Um weitere Sprachen zur Verfügung zu stellen, müssen Sie die UM-Sprachpakete der gewünschten Sprachen installieren. Weitere Informationen zum Installieren eines UM-Sprachpakets finden Sie unter [Installieren eines Sprachpakets](install-a-um-language-pack-exchange-2013-help.md). Für UM in Office 365 müssen keine zusätzlichen UM-Sprachpakete installiert werden.
        
        Obwohl eine andere Sprache ausgewählt werden kann als die, die in den der automatischen Telefonzentrale zugeordneten UM-Wähleinstellungen ausgewählt ist, empfehlen wir, dass die Spracheinstellungen in den Wähleinstellungen und in der automatischen Telefonzentrale übereinstimmen. Wenn die Spracheinstellungen nicht übereinstimmen und Anrufer eine in den Wähleinstellungen angegebene Durchwahlnummer anrufen, erhalten Sie Ansagen in einer Sprache. Wenn die Anrufer eine der automatischen Telefonzentrale zugeordnete Durchwahlnummer anrufen, werden Sie mit Ansagen in einer anderen Sprache begrüßt.
    
      - **Firmenname   **Verwenden Sie dieses Feld, um den Namen des Unternehmens einzugeben. Standardmäßig ist kein Firmenname eingegeben. Wenn Sie in dieses Feld einen Firmennamen eingeben, wird Anrufern statt der Standardbegrüßung eine Ansage mit dem Firmennamen abgespielt.
    
      - **Unternehmensstandort   **Verwenden Sie dieses Feld, um den Standort des Unternehmens einzugeben. Standardmäßig ist kein Unternehmensstandort eingegeben. Wenn Sie den Standort des Unternehmens in dieses Feld eingeben, wird er Anrufern wiedergegeben.

4.  
    
    Verwenden Sie die Einstellung **Begrüßungen** in der automatischen Telefonzentrale, um aufgezeichnete Begrüßungen zu verwalten. Sie können Standardbegrüßungen oder zuvor aufgezeichnete benutzerdefinierte Begrüßungen für Zeiten während und außerhalb der Geschäftszeit auswählen. Sie können Folgendes konfigurieren:
    
      - **Begrüßung während der Geschäftszeit**   Dies ist die Eingangsbegrüßung, die ein Anrufer hört, wenn der Anruf während der Geschäftszeiten Ihrer Organisation mit der automatischen Telefonzentrale verbunden wird. Die Geschäftszeit ist standardmäßig auf einen Zeitraum von 00:00 Uhr bis 24:00 Uhr festgelegt, und es sind keine Zeiten außerhalb der Geschäftszeit konfiguriert. Wenn Sie keine benutzerdefinierte Begrüßung festlegen, hören Anrufer die Systemansage "Willkommen bei der automatischen Exchange-Telefonzentrale". Die Zeiten während und außerhalb der Geschäftszeit werden im Abschnitt **Geschäftszeiten** der automatischen Telefonzentrale konfiguriert.
        
        Sie können die Begrüßung anpassen und auf Ihre Organisation abstimmen, wie zum Beispiel "Danke für Ihren Anruf bei der Woodgrove Bank." Sie können eine für die Geschäftszeiten spezifische Begrüßung konfigurieren, indem Sie auf **Ändern** klicken und eine zuvor aufgezeichnete Begrüßungsdatei auswählen. Die benutzerdefinierte Begrüßung muss bereits als WAV- oder WMA-Datei aufgezeichnet worden sein.
    
      - **Begrüßung außerhalb der Geschäftszeit**   Dies ist die Eingangsbegrüßung, die ein Anrufer hört, wenn der Anruf außerhalb der Geschäftszeiten Ihrer Organisation mit der automatischen Telefonzentrale verbunden wird. Standardmäßig sind keine Zeiten außerhalb der Geschäftszeit konfiguriert. Eine Standardbegrüßung außerhalb der Geschäftszeit ist daher nicht vorhanden. Im Abschnitt **Geschäftszeiten** der automatischen Telefonzentrale können die Zeiten während und außerhalb der Geschäftszeit konfiguriert werden.
        
        Sie können diese Begrüßung anpassen und auf Ihre Organisation abstimmen, wie zum Beispiel "Danke für Ihren Anruf bei der Woodgrove Bank. Leider rufen Sie außerhalb der Geschäftszeit an.", oder "Dies ist der Anschluss von Contoso, Ltd. Unser Büro ist momentan leider nicht besetzt." Unsere Geschäftszeiten sind Montag und Freitag zwischen 8:00 Uhr und 17:00 Uhr." Sie können eine spezifische Begrüßung außerhalb der Geschäftszeiten konfigurieren, indem Sie auf **Ändern** klicken und eine zuvor aufgezeichnete Begrüßungsdatei auswählen. Die benutzerdefinierte Begrüßung muss bereits als WAV- oder WMA-Datei aufgezeichnet worden sein.
    
      - **Informationsansage** Ist diese Option aktiviert, wird diese Aufzeichnung unmittelbar nach der Begrüßung während oder außerhalb der Geschäftszeit abgespielt. Informationsansagen können die Geschäftszeiten der Organisation wiedergeben, z. B. "Unsere Geschäftszeit ist Montag bis Freitag von 8:30 Uhr bis 17:30 Uhr und Samstag von 8:30 Uhr bis 13:00 Uhr." Eine Informationsansage kann ebenfalls Informationen enthalten, die für die Einhaltung von Organisationsrichtlinien erforderlich sind, wie zum Beispiel "Anrufe können zu Schulungszwecken überwacht werden." Falls es wichtig ist, dass Anrufer die Informationsansage in voller Länge hören, kann sie so konfiguriert werden, dass keine Unterbrechung möglich ist. Der Anrufer muss die Ansage in diesem Fall vollständig abhören.
        
        Standardmäßig ist für UM-Wähleinstellungen oder automatische Telefonzentralen keine Informationsansage konfiguriert. Wenn Sie eine Informationsansage aktivieren und eine benutzerdefinierte Audiodatei speziell für Ihre Organisation verwenden, steht die Option **Unterbrechen der Ansage zulassen** zur Verfügung. Die Aufzeichnungen müssen bereits als aufgezeichnete WAV- oder WMA-Dateien vorliegen. Klicken Sie auf **Ändern**, um eine zuvor aufgezeichnete benutzerdefinierte Informationsansagedatei zu suchen.
        
        **Unterbrechen der Ansage zulassen**   Aktivieren Sie dieses Kontrollkästchen, um es dem Anrufer zu ermöglichen, die Informationsansage zu unterbrechen. Bei langen Informationsansagen sollte diese Option aktiviert werden. Anrufer ärgern sich möglicherweise, wenn die Informationsansage zu lang ist und nicht unterbrochen werden kann, um auf die über die automatische Telefonzentrale verfügbaren Optionen zuzugreifen.

5.  Verwenden Sie die Option **Geschäftszeiten**, um die Öffnungszeiten der Organisation festzulegen. Während der Geschäftszeiten hören Anrufer die für die Geschäftszeiten festgelegte Standardbegrüßung bzw. eine benutzerdefinierte Begrüßung und die Ansage des Hauptmenüs, wenn die entsprechenden Tastenzuordnungen für Zeiten innerhalb der Geschäftszeit im Bereich **Menünavigation** konfiguriert sind. Sie können Folgendes konfigurieren:
    
      - **Zeitzonen**   Verwenden Sie diese Liste, um Ihre Zeitzone auszuwählen. Berücksichtigen Sie beim Festlegen des Zeitplans, ob die der automatischen Telefonzentrale zugeordneten Wähleinstellungen mehrere Zeitzonen abdecken.
        
        Bei lokalen und Hybridbereitstellungen wird bei der Installation des Postfachservers, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, die Zeitzone standardmäßig unter Verwendung der Systemzeit des lokalen Servers konfiguriert.
    
      - **Geschäftszeiten**   Klicken Sie auf **Geschäftszeiten konfigurieren**, und verwenden Sie anschließend auf der Seite **Geschäftszeiten konfigurieren** die Tabelle zum Konfigurieren der Geschäftszeiten für Ihre Organisation.
    
      - **Feiertagszeitplan**   Verwenden Sie diesen Bereich, um die Tage (von 00:00 Uhr bis 23:59 Uhr) festzulegen, an denen Ihre Organisation aufgrund von Feiertagen geschlossen ist. Anrufer, die die automatische Telefonzentrale während der auf der Seite **Neuer Feiertag** angegebenen Zeiten erreichen, hören eine von Ihnen festgelegte Audiodatei mit der benutzerdefinierten Begrüßung für Feiertage. Wenn Sie den Feiertagszeitplan konfigurieren, müssen Sie den Namen des Feiertags, die Audiodatei für die aufgezeichnete Begrüßung für Feiertage sowie das **Startdatum** und das **Enddatum** definieren. Die Begrüßungen müssen bereits als aufgezeichnete WAV- oder WMA-Dateien vorliegen.

6.  Verwenden Sie den Abschnitt **Menünavigation**, um die Menüoptionen anzugeben, die den Anrufern während und außerhalb der Geschäftszeiten zur Verfügung stehen sollen. Wenn Sie die Menünavigation aktivieren möchten, müssen Sie die Menünavigation während der Geschäftszeit und die Menünavigation außerhalb der Geschäftszeit separat aktivieren. Wenn Sie beispielsweise die Menünavigation während der Geschäftszeit aktivieren möchten, müssen Sie eine Aufzeichnung einer benutzerdefinierten Menüansage hinzufügen, das Kontrollkästchen **Menünavigation während der Geschäftszeit** aktivieren, auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") klicken und die Optionen auf der Seite **Neuer Menünavigationseintrag** festlegen.
    
      - **Menünavigation während der Geschäftszeit**   Dies ist die Liste der Optionen, die Anrufer während der Geschäftszeiten hören, die auf der Seite **Geschäftszeiten** definiert wurde. Zum Beispiel "Wenn Sie technischen Support benötigen, drücken oder sagen Sie 1. Wenn Sie mit Unternehmensstandorten oder der Unternehmensverwaltung verbunden werden möchten, drücken oder sagen Sie 2. Wenn Sie mit dem Vertrieb verbunden werden möchten, drücken oder sagen Sie 3."
        
        Sie müssen die folgenden Schritte ausführen, um eine Menünavigation während der Geschäftszeit zu aktivieren:
        
        1.  **Menüansage**   Verwenden Sie diese Option, um eine Audiodatei für die benutzerdefinierte Menüansage anzugeben. Klicken Sie auf **Ändern** und anschließend auf **Durchsuchen**, um die Aufzeichnung der Menüansage zu suchen, wenn Sie eine benutzerdefinierte oder eine zuvor aufgezeichnete Menüansage während der Geschäftszeiten verwenden möchten.
        
        2.  **Menünavigation während der Geschäftszeit aktivieren**   Aktivieren Sie dieses Kontrollkästchen, um Optionen für die Menünavigation zu aktivieren, die während der Geschäftszeit verwendet werden. Wenn Sie die Menünavigation während der Geschäftszeit aktivieren, können Sie neue Menünavigationseinträge hinzufügen, die während der Geschäftszeit verwendet werden.
        
        3.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um einen neuen Menünavigationseintrag zu erstellen. Verwenden Sie auf der Seite **Neuer Menünavigationseintrag** folgende Optionen, um einen neuen Menünavigationseintrag zu erstellen:
            
              - **Ansage**   Geben Sie in dieses Feld den Namen des neuen Navigationsmenüs ein. Der Navigationsmenüname wird nur für Anzeigezwecke verwendet. Dieses Feld ist erforderlich.
                
                Da Sie möglicherweise mehrere neue Navigationsmenüs festlegen möchten, sollten Sie für die Tastenzuordnungen aussagekräftige Namen verwenden. Die maximale Länge des Namens für eine Tastenzuordnung beträgt 64 Zeichen inklusive Leerzeichen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
            
              - **Wenn diese Taste gedrückt wird**   Verwenden Sie diese Liste, um die Tastenzuordnung zu aktivieren. Die Tastenzuordnung ist die Zahlentaste, die ein Anrufer drückt, um die automatische Telefonzentrale einen bestimmten Vorgang ausführen zu lassen, wie zum Beispiel die Weiterleitung des Anrufers an eine andere automatische Telefonzentrale oder an eine Vermittlungsstelle. Standardmäßig sind keine Einträge festgelegt.
                
                Verwenden Sie die Dropdownliste, um die Zifferntaste (1 bis 9) auszuwählen, die der Anrufer drücken muss. Null (0) ist für die Vermittlungsstelle der automatischen Telefonzentrale reserviert.
                
                Wenn Sie in der Dropdownliste die Option **Timeout** auswählen, können Anrufer an eine Durchwahlnummer oder eine andere automatische Telefonzentrale weitergeleitet werden, vorausgesetzt, sie drücken keine Taste auf der Wähltastatur des Telefons. Zum Beispiel "Bitte legen Sie nicht auf. Ihr Anruf wird vom nächsten freien Mitarbeiter entgegengenommen." Die Standardeinstellung ist 5 Sekunden. Wenn Sie diese Option aktivieren, wird eine leere Tastenzuordnung erstellt.
            
              - **Folgende Audiodatei wiedergeben**   Verwenden Sie diese Option, um für Anrufer eine zuvor aufgezeichnete Audiodatei auszuwählen. Klicken Sie auf **Ändern** und anschließend auf **Durchsuchen**, um nach der Audiodatei zu suchen. Wenn Sie für die Audiodatei die Standardeinstellung \<Keine\> übernehmen, erzeugt das UM-Text-Sprache-Modul (TTS) eine Hauptmenüansage während der Geschäftszeiten. Alternativ dazu können Sie eine benutzerdefinierte Audiodatei erstellen, die in einer sprachaktivierten automatischen Telefonzentrale für die Hauptmenüansage während der Geschäftszeiten verwendet wird. Die Ansage könnte beispielsweise lauten: "Wenn Sie eine Sprachnachricht für den Vertrieb hinterlassen möchten, sagen Sie 1. Wenn Sie eine Sprachnachricht für den technischen Support hinterlassen möchten, sagen Sie 2. Wenn Sie eine Sprachnachricht für die Verwaltung hinterlassen möchten, sagen Sie 3."
            
              - **Diese zusätzliche Aktion ausführen**   Verwenden Sie eine der folgenden Optionen, um die Aktion festzulegen, die von der automatischen Telefonzentrale für den Anrufer ausgeführt werden soll:
                
                  - **Keine**   Verwenden Sie diese Option, wenn Sie nicht möchten, dass die automatische Telefonzentrale einen Anruf an eine Durchwahl oder eine andere automatische Telefonzentrale weiterleitet, oder wenn Sie nicht möchten, dass Anrufer eine Nachricht hinterlassen können.
                
                  - **Weiterleiten an diese Durchwahl**   Wählen Sie diese Option aus, damit Anrufe an eine Durchwahlnummer weitergeleitet werden können. Wenn Sie diese Option aktivieren, geben Sie die Durchwahlnummer, an die der Anruf weitergeleitet wird, in das Feld ein. In diesem Feld werden nur numerische Zeichen akzeptiert. Die folgenden Zeichen dürfen nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
                
                  - **Weiterleiten an diese automatische UM-Telefonzentrale**   Wählen Sie diese Option, um den Anruf an eine automatische Telefonzentrale weiterzuleiten. Klicken Sie auf **Durchsuchen**, um die automatische Telefonzentrale zu suchen, die Sie verwenden möchten. Vor dem Aktivieren dieser Option müssen Sie zunächst eine automatische Telefonzentrale erstellen und konfigurieren. Diese Option wird verwendet, wenn Sie eine über- und untergeordnete Struktur von automatischen UM-Telefonzentralen erstellen.
                
                  - **Sprachnachricht für diesen Benutzer hinterlassen**   Wählen Sie diese Option aus, damit ein Anrufer eine Sprachnachricht für einen Benutzer hinterlassen kann, der sich in dem gleichen Wählplan wie die automatische UM-Telefonzentrale befindet, die Sie konfigurieren. Wenn ein Anrufer diese Option aus dem Menü einer automatischen Telefonzentrale auswählt, wird er zum Hinterlassen einer Sprachnachricht für den ausgewählten Benutzer aufgefordert. Klicken Sie auf **Durchsuchen**, um nach dem UM-aktivierten Benutzer zu suchen.
                
                  - **Unternehmensstandort ansagen**   Aktivieren Sie diese Option, damit ein Anrufer eine Menüoption einer automatischen Telefonzentrale auswählen und den Standort des Unternehmens angesagt bekommen kann, das für die automatische UM-Telefonzentrale konfiguriert ist. Damit dies ordnungsgemäß funktioniert, müssen Sie zuerst den Unternehmensstandort in das Feld **Unternehmensstandort** auf der Registerkarte **Allgemein** der automatischen UM-Telefonzentrale eingeben.
                
                  - **Geschäftszeiten ansagen**   Aktivieren Sie diese Option, damit ein Anrufer eine Menüoption einer automatischen Telefonzentrale auswählen und die Geschäftszeiten für das Unternehmen angesagt bekommen kann, das für die automatische UM-Telefonzentrale konfiguriert ist. Damit dies ordnungsgemäß funktioniert, müssen Sie zuerst die Geschäftszeiten auf der Seite **Geschäftszeiten** für die automatische UM-Telefonzentrale eingeben.
    
      - **Menünavigation während der Geschäftszeit**   Dies ist die Liste der Optionen, die Anrufer außerhalb der Geschäftszeiten hören, die auf der Seite **Geschäftszeiten** definiert wurde. Zum Beispiel "Wir freuen uns sehr über Ihren Anruf. Sie rufen Woodgrove Bank jedoch außerhalb der normalen Geschäftszeit an. Wenn Sie eine Nachricht hinterlassen möchten, drücken oder sagen Sie 1. Wir rufen Sie so schnell wie möglich zurück."
        
        Sie müssen die folgenden Schritte ausführen, um eine Menünavigation außerhalb der Geschäftszeit zu aktivieren:
        
        1.  **Menüansage**   Verwenden Sie diese Option, um eine Audiodatei für die benutzerdefinierte Menüansage anzugeben. Klicken Sie auf **Durchsuchen**, um eine benutzerdefinierte oder zuvor aufgezeichnete Menüansage zu suchen, die außerhalb der Geschäftszeiten verwendet werden soll.
        
        2.  **Menünavigation außerhalb der Geschäftszeit aktivieren**   Aktivieren Sie dieses Kontrollkästchen, um Optionen für die Menünavigation zu aktivieren, die außerhalb der Geschäftszeit verwendet werden. Wenn Sie die Menünavigation außerhalb der Geschäftszeit aktivieren, können Sie neue Menünavigationseinträge hinzufügen, die außerhalb der Geschäftszeit verwendet werden.
        
        3.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um einen neuen Menünavigationseintrag zu erstellen. Verwenden Sie auf der Seite **Neuer Menünavigationseintrag** folgende Optionen, um einen neuen Menünavigationseintrag zu erstellen:
            
              - **Ansage**   Geben Sie in dieses Feld den Namen des neuen Navigationsmenüs ein. Der Navigationsmenüname wird nur für Anzeigezwecke verwendet. Dieses Feld ist erforderlich.
                
                Da Sie möglicherweise mehrere neue Navigationsmenüs festlegen möchten, sollten Sie für die Tastenzuordnungen aussagekräftige Namen verwenden. Die maximale Länge des Namens für eine Tastenzuordnung beträgt 64 Zeichen inklusive Leerzeichen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
            
              - **Wenn diese Taste gedrückt wird**   Verwenden Sie diese Liste, um die Tastenzuordnung zu aktivieren. Die Tastenzuordnung ist die Zahlentaste, die ein Anrufer drückt, um die automatische Telefonzentrale einen bestimmten Vorgang ausführen zu lassen, wie zum Beispiel die Weiterleitung des Anrufers an eine andere automatische Telefonzentrale oder an eine Vermittlungsstelle. Standardmäßig sind keine Einträge festgelegt.
                
                Verwenden Sie die Dropdownliste, um die Zifferntaste (1 bis 9) auszuwählen, die der Anrufer drücken muss. Null (0) ist für die Vermittlungsstelle der automatischen Telefonzentrale reserviert.
                
                Wenn Sie in der Dropdownliste die Option **Timeout** auswählen, können Anrufer an eine Durchwahlnummer oder eine andere automatische Telefonzentrale weitergeleitet werden, vorausgesetzt, sie drücken keine Taste auf der Wähltastatur des Telefons. Zum Beispiel "Bitte legen Sie nicht auf. Ihr Anruf wird vom nächsten freien Mitarbeiter entgegengenommen." Die Standardeinstellung ist 5 Sekunden. Wenn Sie diese Option aktivieren, wird eine leere Tastenzuordnung erstellt.
            
              - **Folgende Audiodatei wiedergeben**   Verwenden Sie diese Option, um für Anrufer eine zuvor aufgezeichnete Audiodatei auszuwählen. Klicken Sie auf **Ändern** und anschließend auf **Durchsuchen**, um nach der Audiodatei zu suchen. Wenn Sie für die Audiodatei die Standardeinstellung \<Keine\> übernehmen, erzeugt das UM-Text-Sprache-Modul (TTS) eine Hauptmenüansage außerhalb der Geschäftszeiten. Alternativ dazu können Sie auch für eine sprachaktivierte Telefonzentrale eine benutzerdefinierte Audiodatei für die Hauptmenüansage außerhalb der Geschäftszeiten erstellen, die beispielsweise so lauten könnte: "Sie rufen außerhalb der Geschäftszeiten bei Contoso an. Wenn Sie eine Sprachnachricht für den Vertrieb hinterlassen möchten, sagen Sie 1. Wenn Sie eine Sprachnachricht für den technischen Support hinterlassen möchten, sagen Sie 2. Wenn Sie eine Sprachnachricht für die Verwaltung hinterlassen möchten, sagen Sie 3. Wenn Sie mit der Vermittlung sprechen möchten, drücken Sie die 0."
            
              - **Diese zusätzliche Aktion ausführen**   Verwenden Sie eine der folgenden Optionen, um die Aktion festzulegen, die von der automatischen Telefonzentrale für den Anrufer ausgeführt werden soll:
                
                  - **Keine**   Verwenden Sie diese Option, wenn Sie nicht möchten, dass die automatische Telefonzentrale einen Anruf an eine Durchwahl oder eine andere automatische Telefonzentrale weiterleitet, oder wenn Sie nicht möchten, dass Anrufer eine Nachricht hinterlassen können.
                
                  - **Weiterleiten an diese Durchwahl**   Wählen Sie diese Option aus, damit Anrufe an eine Durchwahlnummer weitergeleitet werden können. Wenn Sie diese Option aktivieren, verwenden Sie das Feld, um die Durchwahlnummer einzugeben, an die der Anruf weitergeleitet wird. In diesem Feld werden nur numerische Zeichen akzeptiert. Die folgenden Zeichen dürfen nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
                
                  - **Weiterleiten an diese automatische UM-Telefonzentrale**   Wählen Sie diese Option, um den Anruf an eine vorhandene automatische Telefonzentrale weiterzuleiten. Klicken Sie auf **Durchsuchen**, um die automatische Telefonzentrale zu suchen, die Sie verwenden möchten. Vor dem Aktivieren dieser Option müssen Sie zunächst eine automatische Telefonzentrale erstellen und konfigurieren. Diese Option wird verwendet, wenn Sie eine über- und untergeordnete Struktur von automatischen UM-Telefonzentralen erstellen.
                
                  - **Sprachnachricht für diesen Benutzer hinterlassen**   Wählen Sie diese Option aus, damit ein Anrufer eine Sprachnachricht für einen Benutzer hinterlassen kann, der sich in dem gleichen Wählplan wie die automatische UM-Telefonzentrale befindet, die Sie konfigurieren. Wenn ein Anrufer diese Option aus dem Menü einer automatischen Telefonzentrale auswählt, wird er zum Hinterlassen einer Sprachnachricht für den ausgewählten Benutzer aufgefordert. Klicken Sie auf **Durchsuchen**, um nach dem UM-aktivierten Benutzer zu suchen.
                
                  - **Unternehmensstandort ansagen**   Aktivieren Sie diese Option, damit ein Anrufer eine Menüoption einer automatischen Telefonzentrale auswählen und den Standort des Unternehmens angesagt bekommen kann, das für die automatische UM-Telefonzentrale konfiguriert ist. Damit dies ordnungsgemäß funktioniert, müssen Sie zuerst den Unternehmensstandort in das Feld **Unternehmensstandort** auf der Seite **Allgemein** der automatischen UM-Telefonzentrale eingeben.
                
                  - **Geschäftszeiten ansagen**   Aktivieren Sie diese Option, damit ein Anrufer eine Menüoption einer automatischen Telefonzentrale auswählen und die Geschäftszeiten für das Unternehmen angesagt bekommen kann, das für die automatische UM-Telefonzentrale konfiguriert ist. Damit dies ordnungsgemäß funktioniert, müssen Sie zuerst die Geschäftszeiten auf der Seite **Geschäftszeiten** für die automatische UM-Telefonzentrale eingeben.

7.  Verwenden Sie die Einstellung **Zugriff auf Adressbuch und Vermittlungsstelle**, um die Funktionen zu definieren, die Anrufern bei einem Anruf bei der automatischen Telefonzentrale zur Verfügung stehen. Sie können folgende Funktionen konfigurieren: die bei der Anwahl der automatischen Telefonzentrale zu verwendende Sprache sowie die Umleitung von Anrufern an die Durchwahlnummer der Vermittlungsstelle. Sie können Folgendes konfigurieren:
    
      - **Optionen für das Kontaktieren von Benutzern**   Verwenden Sie diese Optionen, um festzulegen, wie Anrufer Benutzer per Voicemail kontaktieren können, wenn sie bei einer automatischen Telefonzentrale anrufen
        
          - **Anrufer dürfen Benutzer wählen**   Aktivieren Sie dieses Kontrollkästchen, um Anrufern die Übergabe von Anrufen an Benutzer zu gestatten. Diese Option ist standardmäßig aktiviert und erlaubt Benutzern, die den Wähleinstellungen zugeordnet sind, die Übergabe von Anrufen an Benutzer in denselben UM-Wähleinstellungen. Im Anschluss an das Aktivieren des Kontrollkästchens können Sie die Gruppe von Benutzern festlegen, an die Anrufer übergeben werden können, indem Sie auf dieser Seite die geeignete Option unter **Optionen zum Durchsuchen des Adressbuchs** auswählen.
            
            Wenn Sie diese Option und die Option **Anrufer dürfen Sprachnachrichten für Benutzer hinterlassen** deaktivieren, stehen die Optionen unter **Optionen zum Durchsuchen des Adressbuchs** nicht zur Verfügung.
        
          - **Anrufer dürfen Sprachnachrichten für Benutzer hinterlassen**   Aktivieren Sie dieses Kontrollkästchen, um Anrufern das Hinterlassen von Sprachnachrichten für Benutzer zu gestatten. Diese Option ist standardmäßig aktiviert und ermöglicht Benutzern, die den Wähleinstellungen zugeordnet sind, Sprachnachrichten an Benutzer in denselben UM-Wähleinstellungen zu senden. Im Anschluss an das Aktivieren des Kontrollkästchens können Sie die Gruppe von Benutzern festlegen, denen Anrufer Sprachnachrichten senden dürfen, indem Sie auf dieser Seite die geeignete Option unter **Optionen zum Durchsuchen des Adressbuchs** auswählen.
            
            Wenn Sie diese Option und die Option **Anrufer dürfen Benutzer wählen** deaktivieren, stehen die Optionen unter **Optionen zum Durchsuchen des Adressbuchs** nicht zur Verfügung.
            
            Wenn Sie diese Option deaktivieren, stellt die automatische Telefonzentrale Anrufern während einer Systemansage nicht das Senden einer Sprachnachricht zur Wahl.
    
      - **Optionen zum Durchsuchen des Adressbuchs**   Verwenden Sie diese Optionen, um eine Gruppierung von Benutzern festzulegen. Standardmäßig ist die Option **Anrufer dürfen Benutzer nach Name oder Alias suchen** aktiviert, zusammen mit der Option **Nur in diesem Wählplan**. Sie können die Gruppierung von Benutzern jedoch ändern, um Anrufern die Übergabe von Anrufen oder das Senden von Sprachnachrichten an Benutzer zu ermöglichen, die in der globalen Adressliste (Global Address List, GAL) für eine Organisation enthalten sind. Es stehen folgende Optionen zur Auswahl:
        
          - **Anrufer dürfen Benutzer nach Name oder Alias suchen**   Diese Option ist standardmäßig aktiviert. Sie ermöglicht es Anrufern, die bei dieser automatischen Telefonzentrale anrufen, Benutzer im Verzeichnis nach Name oder Alias zu suchen. Beim Erstellen eines Postfachs für einen Benutzer wird diesem ein Alias zugewiesen. Der Alias ist der erste Teil einer SMTP-Adresse, beispielsweise "tonysmith@contoso.com". Die SMTP-Adresse lautet "tonysmith@contoso.com", der Alias lautet "tonysmith". Die Aktivierung dieser Option betrifft nur Anrufer, die diese automatische Telefonzentrale verwenden. Auf Anrufer, die Outlook Voice Access verwenden, wird die Option nicht angewendet.
            
              - **Nur in diesem Wählplan**   Mithilfe dieser Option können Sie Anrufern, die eine Verbindung mit der automatischen UM-Telefonzentrale herstellen, erlauben, Benutzer zu ermitteln und zu kontaktieren, die in dem Wählplan enthalten sind, der der automatischen UM-Telefonzentrale zugeordnet ist. Standardmäßig ist diese Option im Wählplan und in der automatischen Telefonzentrale aktiviert. Dies bedeutet, dass sowohl Outlook Voice Access-Benutzer als auch Anrufer, die eine Verbindung mit der automatischen Telefonzentrale herstellen, nach Benutzern im selben Wählplan suchen können.
            
              - **In der gesamten Organisation**   Aktivieren Sie diese Option, um Anrufern, die eine Verbindung mit dieser automatischen UM-Telefonzentrale herstellen, das Auffinden und Kontaktieren beliebiger Benutzer zu ermöglichen, die in der GAL für die Organisation enthalten sind. Dazu gehören nicht nur UM-aktivierte Benutzer, sondern alle Benutzer, die Postfach-aktiviert sind. Mit dieser Option können Anrufer Benutzer in mehreren Wählplänen kontaktieren. Diese Funktion ist nicht standardmäßig aktiviert. Diese Einstellungen steht auch in einem Wählplan für Outlook Voice Access-Benutzer zur Verfügung.
        
          - **Informationen, die für Benutzer mit ähnlichen Namen eingeschlossen werden**   Verwenden Sie diese Dropdownliste zur Auswahl der Option, die für die automatische UM-Telefonzentrale verwendet wird, wenn Benutzer denselben oder ähnliche Namen aufweisen. Diese Einstellung wird verwendet, wenn mindestens zwei Benutzer mit demselben Namen im Verzeichnis vorhanden sind. Dies wird auch als Auswahlmethode für übereinstimmende Namen oder als Mehrdeutigkeitsvermeidungsfeld bezeichnet. Sie können diese Einstellung konfigurieren oder die Standardeinstellung in der automatischen Telefonzentrale beibehalten. Standardmäßig erbt die automatische Telefonzentrale diese Einstellung vom Wählplan, der dieser automatischen Telefonzentrale zugeordnet ist. Nachfolgend ein Beispiel für eine sprachaktivierte automatische Telefonzentrale:
            
            1.  System: "Herzlich willkommen bei Contoso. Wenn Sie den Namen der Person kennen, die Sie erreichen möchten, sagen Sie bitte deren Namen."
            
            2.  Anrufer sagt "Tony Smith."
            
            3.  Es gibt mehrere Personen mit diesem Namen. Wählen Sie eine der folgenden Optionen: Für Tony Smith, Forschung, drücken Sie bitte die 1. Für Tony Smith, Verwaltung, drücken Sie bitte die 2. Für Tony Smith, technischer Support, drücken Sie bitte die 3."
            
            4.  Der Anrufer drückt die entsprechende Taste auf der Tastatur, und der Anruf wird an den gewünschten Benutzer übergeben.
                

                > [!NOTE]
                > Bei Verwendung einer automatischen Telefonzentrale ohne Sprachaktivierung weist das System den Anrufer an, den Namen des Benutzers (Nachname zuerst) über die Tastatur einzugeben und nach dem Benutzer zu suchen. Wenn mehrere Personen mit demselben Namen im Verzeichnis enthalten sind, wird der Anrufer angewiesen, die geeignete Taste zu drücken, um mit dem gewünschten Benutzer verbunden zu werden. Sie können optional eine automatische DTMF-Fallback-Telefonzentrale erstellen, die ausschließlich die Tastatur zur Eingabe eines Namen oder Alias verwendet.

            
            Zur Verwendung dieser Einstellungen müssen Sie dem Benutzer die richtigen Informationen hinzufügen. Wenn Sie beispielsweise möchten, dass die automatische Telefonzentrale einen Titel zur Unterscheidung von zwei Benutzern mit demselben Namen verwendet, müssen Sie diese Informationen dem Benutzerkonto hinzufügen. Wählen Sie eine der folgenden Methoden aus, um dem Anrufer weitere Informationen bereitzustellen, die diesen bei der Auswahl des gewünschten Benutzers in der Organisation unterstützen:
            
              - **Vererbung von Wählplan**   Wählen Sie diese Option aus, damit die automatische Telefonzentrale die Standardeinstellung aus dem Wählplan verwendet, der der automatischen Telefonzentrale zugeordnet ist.
            
              - **Titel**   Wählen Sie diese Option aus, damit in der automatischen Telefonzentrale beim Auflisten der Treffer die Titel sämtlicher Benutzer angezeigt werden.
            
              - **Abteilung**   Wählen Sie diese Option aus, damit in der automatischen Telefonzentrale beim Auflisten der Treffer die Abteilungen sämtlicher Benutzer angezeigt werden.
            
              - **Ort**   Wählen Sie diese Option aus, damit in der automatischen Telefonzentrale beim Auflisten der Treffer die Orte sämtlicher Benutzer angezeigt werden.
            
              - **Keine**   Wählen Sie diese Option aus, damit beim Auflisten der Treffer keine weiteren Informationen angezeigt werden.
            
              - **Ansage für Alias**   Wählen Sie diese Option aus, damit die automatische Telefonzentrale den Anrufer zur Angabe des Benutzeralias auffordert.

8.  Unterhalb von **Vermittlungsstellenzugriff** können Sie folgende Vermittlungsstelleneinstellungen für die automatische Telefonzentrale festlegen:
    
      - **Durchwahl für Vermittlungsstelle**   Verwenden Sie dieses Feld, um die Durchwahlnummer für eine Vermittlungsstelle einzugeben. Über diese Durchwahlnummer kann der Anrufer mit einem Telefonist oder einem UM-aktivierten Postfach verbunden werden. Die Nummer kann auch so konfiguriert werden, dass eine externe Telefonnummer angerufen wird. Standardmäßig ist in diesem Feld keine Durchwahlnummer für eine Vermittlungsstelle angegeben.
    
      - **Übergabe an Vermittlungsstelle während der Geschäftszeit zulassen**   Aktivieren Sie dieses Kontrollkästchen, damit Anrufer während der Geschäftszeit an einen Telefonisten weitergeleitet werden, wenn sie die Durchwahlnummer verwenden, die im Feld **Durchwahl für Vermittlungsstelle** konfiguriert wurde. Diese Option ist standardmäßig deaktiviert.
        
        Diese Option sollte aktiviert werden, damit Anrufer eine Sprachnachricht hinterlassen bzw. bei der Vermittlungsstelle anrufen können, falls Sie den gewünschten Teilnehmer während der Geschäftszeit weder über Menüansagen noch über die Verzeichnissuche erreichen können. Nach dem Aktivieren dieser Option können Sie die Durchwahlnummer für die Vermittlungsstelle festlegen, die in einem überwachten UM-fähigen Postfach konfiguriert ist. Der Anrufer kann eine Sprachnachricht hinterlassen oder die Hilfe eines Telefonisten in Anspruch nehmen, der die Durchwahlnummer kennt.
    
      - **Übergabe an Vermittlungsstelle außerhalb der Geschäftszeit zulassen**   Aktivieren Sie dieses Kontrollkästchen, damit Anrufer außerhalb der Geschäftszeit an einen Telefonisten weitergeleitet werden, wenn sie die Durchwahlnummer verwenden, die im Feld **Durchwahl für Vermittlungsstelle** konfiguriert wurde. Diese Option ist standardmäßig deaktiviert.
        
        Diese Option sollte aktiviert werden, damit Anrufer eine Sprachnachricht hinterlassen bzw. bei der Vermittlung anrufen können, falls Sie den gewünschten Teilnehmer außerhalb der Geschäftszeit weder über Menüansagen noch über die Verzeichnissuche erreichen können. Nach dem Aktivieren dieser Option können Sie die Durchwahlnummer für die Vermittlungsstelle festlegen, die in einem überwachten UM-fähigen Postfach konfiguriert ist. Der Anrufer kann eine Sprachnachricht hinterlassen oder die Hilfe eines Telefonisten in Anspruch nehmen, der die Durchwahlnummer kennt.

9.  
    
    Verwenden Sie die Einstellung **Wählautorisierung**, um Wählregeln für Anrufer zu konfigurieren, die bei einer automatischen UM-Telefonzentrale anrufen. Mithilfe dieser Einstellungen können Sie die Durchwahlnummern steuern, die über eine automatische Telefonzentrale erreichbar sind, oder die Rufnummern, die von Anrufern gewählt werden können, die eine automatische Telefonzentrale angewählt haben. Sie können Folgendes konfigurieren:
    
      - **Anrufe in denselben Wähleinstellungen**   Aktivieren Sie dieses Kontrollkästchen, damit Benutzer, die eine Verbindung mit einer automatischen Telefonzentrale herstellen, eine Durchwahlnummer anrufen oder einen Anruf an diese Durchwahlnummer weiterleiten können. Die Durchwahlnummer muss hierbei einem UM-aktivierten Benutzer zugeordnet sein, dem dieselben Wähleinstellungen zugeordnet sind wie die der automatischen Telefonzentrale. Diese Einstellung ist standardmäßig aktiviert.
        
        Wenn Sie diese Einstellung deaktivieren, können Benutzer beim Anwählen einer automatischen Telefonzentrale Benutzer ohne UM-Aktivierung oder andere Durchwahlnummern anrufen, die keinem UM-aktivierten Benutzer zugeordnet sind, sowie Anrufe an diese weiterleiten. Benutzer können keine Anrufe an UM-aktivierte Benutzer weiterleiten, die denselben Wähleinstellungen wie die automatische Telefonzentrale zugeordnet sind. Der Grund dafür ist, dass die Einstellung **Anrufe an jede Durchwahl zulassen** standardmäßig aktiviert ist.
    
      - **Anrufe an jede Durchwahl zulassen**   Wenn diese Einstellung deaktiviert ist, können Benutzer beim Anwählen einer automatischen Telefonzentrale Benutzer ohne UM-Aktivierung oder andere Durchwahlnummern nicht anrufen, die keinem UM-aktivierten Benutzer zugeordnet sind. Sie sind jedoch in der Lage, Anrufe zu tätigen oder Anrufe an Durchwahlnummern, die UM-aktivierten Benutzern zugewiesen sind, weiterzuleiten. Der Grund dafür ist, dass die Einstellung **Anrufe im gleichen UM-Wählplan** standardmäßig aktiviert ist. Die Einstellung **Anrufe an jede Durchwahl zulassen** ist standardmäßig aktiviert.
        
        Wenn diese Einstellung aktiviert ist, können Benutzer beim Anwählen einer automatischen Telefonzentrale Benutzer ohne UM-Aktivierung, andere Durchwahlnummern, die keinem UM-aktiviertem Benutzer zugeordnet sind, und UM-aktivierte Benutzer anrufen. Der Grund dafür ist, dass die Einstellung **Anrufe in denselben UM-Wähleinstellungen** standardmäßig aktiviert ist.
        
        Diese Einstellung kann in einer Umgebung aktiviert werden, in der nicht alle Benutzer UM-aktiviert sind. Sie ist außerdem hilfreich, wenn Sie zulassen möchten, dass Benutzer, die bei einer in einer Telefonzentrale konfigurierten Rufnummer anrufen, Durchwahlnummern anrufen können, die keinem UM-aktivierten Benutzer zugeordnet sind.
    
      - **Autorisierte nationale Wählregelgruppen**   Verwenden Sie diesen Abschnitt, um zulässige nationale Wählregelgruppen hinzuzufügen oder zu entfernen. Standardmäßig sind keine nationalen/regionalen Wählregelgruppen in UM-Telefonzentralen konfiguriert.
        
        Mit nationalen/regionalen Wählregelgruppen können Sie den Zugriff auf Rufnummern in einem Land oder einer Region zulassen oder beschränken, die von Benutzern beim Anrufen der UM-Telefonzentrale gewählt werden können. Diese Maßnahme hilft dabei, unnötige bzw. nicht autorisierte Telefonate und Gebühren zu vermeiden.
        
        Sie müssen zuerst die entsprechenden nationalen/regionalen Wählregelgruppen für die Wähleinstellungen erstellen, die der UM-Telefonzentrale zugeordnet sind, um nationale/regionale Wählregelgruppen hinzufügen zu können. Anschließend müssen Sie die entsprechende Wählregelgruppe hinzufügen.
        
        Nationale/regionsinterne Wählregelgruppen können von Unified Messaging verwendet werden, um den Zugriff auf Rufnummern in einem Land oder einer Region zuzulassen oder einzuschränken. Dies wird bei jedem Benutzer angewendet, der bei einer Telefonzentrale anruft. Weitere Informationen zum Wählen externer Nummern finden Sie unter [Autorisieren von Benutzern für Anrufe](allow-users-to-make-calls-exchange-2013-help.md).
    
      - **Autorisierte internationale Wählregelgruppen**   Verwenden Sie diesen Abschnitt, um zulässige internationale Wählregelgruppen hinzuzufügen oder zu entfernen. Standardmäßig sind keine internationalen Wählregelgruppen in UM-Telefonzentralen konfiguriert.
        
        Mit internationalen Wählregelgruppen können Sie den Zugriff auf Rufnummern außerhalb eines Landes oder einer Region zulassen oder beschränken, die von Benutzern beim Anrufen der UM-Telefonzentrale gewählt werden können. Diese Maßnahme hilft dabei, unnötige bzw. nicht autorisierte Telefonate und Gebühren zu vermeiden.
        
        Zum Hinzufügen von internationalen Wählregelgruppen müssen Sie zunächst geeignete internationale Wählregelgruppen in dem Wählplan erstellen, der der automatischen UM-Telefonzentrale zugeordnet ist. Nachdem Sie die erforderlichen Wählregelgruppen im Wählplan erstellt haben, müssen Sie sie der Liste der autorisierten Wählregelgruppen in der automatischen UM-Telefonzentrale hinzufügen.
        
        Mithilfe von internationalen Wählregelgruppen kann Unified Messaging den Zugriff auf Rufnummern außerhalb eines Lands oder einer Region zulassen oder einschränken. Dies wird bei jedem Benutzer angewendet, der bei einer Telefonzentrale anruft. Weitere Informationen zum Wählen externer Nummern finden Sie unter [Autorisieren von Benutzern für Anrufe](allow-users-to-make-calls-exchange-2013-help.md).

10. Klicken Sie auf **OK**, um die neue Menünavigation zu erstellen.

11. Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** auf **Speichern**, um die Änderungen zu speichern.

## Konfigurieren von Eigenschaften der automatischen UM-Telefonzentralen mithilfe der Shell

In diesem Beispiel wird eine automatische UM-Telefonzentrale mit dem Namen `MySpeechEnabledAA` so konfiguriert, dass die automatische Telefonzentrale `MyDTMFAA` als Fallback-Telefonzentrale verwendet wird, die Durchwahl zur Vermittlungsstelle auf 50100 festgelegt und die Übergabe an diese Durchwahlnummer außerhalb der Geschäftszeit aktiviert wird.

    Set-UMAutoAttendant -Identity MySpeechEnabledAA -DTMFFallbackAutoAttendant MyDTMFAA -OperatorExtension 50100 -AfterHoursTransferToOperatorEnabled $true

In diesem Beispiel wird die automatische UM-Telefonzentrale `MyUMAutoAttendant` gelöscht: Die Geschäftszeiten sind als 10:45 Uhr bis 13:15 Uhr (Sonntag), 09:00 Uhr bis 17:00 Uhr (Montag) und 09:00 Uhr bis 16:30 Uhr (Samstag) konfiguriert. Feiertage sind mit den entsprechenden Begrüßungen "New Year" am 2. Januar 2013 und "Building closed for construction" vom 24. bis 28. April 2013 konfiguriert.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessHoursSchedule 0.10:45-0.13:15,1.09:00-1.17:00,6.09:00-6.16:30 -HolidaySchedule "New Year,newyrgrt.wav,1/2/2013","Building Closed for Construction,construction.wav,4/24/2013,4/28/2013"

## Anzeigen von Eigenschaften der automatischen UM-Telefonzentralen mithilfe der Shell

In diesem Beispiel wird eine formatierte Liste aller automatischen UM-Telefonzentralen zurückgegeben.

    Get-UMAutoAttendant | Format-List

In diesem Beispiel werden die Eigenschaften einer automatischen UM-Telefonzentrale mit dem Namen "MyUMAutoAttendant" angezeigt.

    Get-UMAutoAttendant -Identity MyUMAutoAttendant


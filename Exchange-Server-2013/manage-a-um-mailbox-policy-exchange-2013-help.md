---
title: 'Verwalten einer UM-Postfachrichtlinie: Exchange 2013 Help'
TOCTitle: Verwalten einer UM-Postfachrichtlinie
ms:assetid: 704b001c-3e6f-4ed5-bbe5-42a778f6ac0d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998829(v=EXCHG.150)
ms:contentKeyID: 50554847
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.UMMailboxPolicyGeneralTab
ms.translationtype: HT
---

# Verwalten einer UM-Postfachrichtlinie

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Nachdem Sie eine Unified Messaging-Postfachrichtlinie (UM) erstellt haben, können Sie verschiedene Einstellungen anzeigen und konfigurieren. Beispielsweise können Sie UM-Funktionen wie "Voicemailvorschau" oder "Wiedergabe über Telefon" sowie andere, sicherheitsbezogene Optionen wie Einstellungen für geschützte Voicemail und PIN-Richtlinien konfigurieren.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](https://technet.microsoft.com/de-de/library/JJ851061(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwalten einer UM-Postfachrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** unterhalb von **UM-Postfachrichtlinien** auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
      - Unter **Allgemein** können Sie die Einstellungen für eine UM-Postfachrichtlinie anzeigen und konfigurieren. Beispielsweise können Sie die der UM-Postfachrichtlinie zugeordneten Wähleinstellungen anzeigen oder Benachrichtigungen über verpasste Anrufe für Benutzer, die einer bestimmten UM-Postfachrichtlinie zugeordnet sind, deaktivieren. Wenn Sie die Einstellungen für eine UM-Postfachrichtlinie ändern, gelten die geänderten Einstellungen für alle Benutzer, die der UM-Postfachrichtlinie zugeordnet sind. Sie können folgende Informationen anzeigen oder konfigurieren:
        
          - **UM-Wählplan**   Zeigt den Namen des Wählplans an, der der UM-Postfachrichtlinie zugeordnet ist. Der Name der Wähleinstellung wird in der Shell angezeigt.
            
            Wenn eine neue UM-Postfachrichtlinie erstellt wird, muss sie einer Wähleinstellung zugeordnet werden. Nachdem die UM-Postfachrichtlinie erstellt und einer Wähleinstellung zugeordnet wurde, werden die für die Postfachrichtlinie definierten Einstellungen auf die der Wähleinstellung zugeordneten Benutzer angewendet. Beim Erstellen einer Wähleinstellung mithilfe der Shell wird standardmäßig auch eine UM-Postfachrichtlinie erstellt.
        
          - **Name**   Geben Sie den Namen für die Wähleinstellungen ein. Ein Name für die UM-Wähleinstellungen ist erforderlich und muss eindeutig sein. Er wird allerdings nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell verwendet. Wenn Sie den Anzeigenamen der Wähleinstellungen nach dem Erstellen ändern müssen, müssen zuerst die vorhandenen UM-Wähleinstellungen gelöscht und dann andere Wähleinstellungen mit dem entsprechenden Namen erstellt werden. Wenn in Ihrer Organisation verschiedene UM-Wähleinstellungen verwendet werden, empfiehlt sich die Verwendung aussagekräftiger Namen für die UM-Wähleinstellungen. Der Name der UM-Wähleinstellungen kann eine Länge von maximal 64 Zeichen haben und Leerzeichen enthalten. (Bei Anbindung an Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server wird von der Verwendung von Leerzeichen abgeraten.) Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
        
          - **Beschränkung der persönlichen Begrüßungstexte (Minuten)**   Verwenden Sie dieses Textfeld, um die maximale Anzahl an Minuten anzugeben, die Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, zum Aufzeichnen von Voicemail-Begrüßungen verwenden können. Diese Einstellung kann nach dem Erstellen der UM-Postfachrichtlinie geändert werden. Es sind nur numerische Zeichen zulässig. Der gültige Bereich für die Begrüßung liegt zwischen 1 und 10 Minuten. Die Standardeinstellung ist 5 Minuten.
        
          - **Voicemailvorschau zulassen**   Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die Funktion "Voicemailvorschau zulassen" für Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, zu aktivieren oder zu deaktivieren. Bei Aktivierung dieser Einstellung können Benutzer den Text einer Voicemailnachricht im Nachrichtentext einer E-Mail- oder Textnachricht empfangen. Die Standardeinstellung ist "Aktiviert".
        
          - **Konfigurieren von Mailboxansageregeln durch Benutzer zulassen**   Aktivieren Sie dieses Kontrollkästchen, um Benutzern, die der UM-Postfachrichtlinie zugeordnet sind, das Erstellen von Mailboxansageregeln zu gestatten. Wenn diese Option in den UM-Wähleinstellungen deaktiviert ist, ist diese Funktion für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, nicht verfügbar. Die Standardeinstellung ist "Aktiviert".
        
          - **Anzeige für wartende Nachrichten zulassen**   Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die MWI-Funktion (Message Waiting Indicator, Anzeige für wartende Nachrichten) für Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, zu aktivieren oder zu deaktivieren. Die meisten Legacy-Voicemailsysteme umfassen eine MWI-Funktion (Message Waiting Indicator). Üblicherweise wird dem Voicemailbenutzer der Eingang einer neuen Sprachnachricht über eine Signal-LED am Telefon angezeigt. MWI kann auch eine Textnachricht an das Mobiltelefon des UM-aktivierten Benutzers senden. Die Standardeinstellung ist "Aktiviert".
        
          - **Outlook Voice Access zulassen**   Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um den Zugriff auf Outlook Voice Access für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, zu aktivieren oder zu deaktivieren. Mit Outlook Voice Access können UM-aktivierte Benutzer über ein Telefon auf ihr Postfach zugreifen. Diese Einstellung ist standardmäßig aktiviert.
        
          - **Benachrichtigungen über verpasste Anrufe zulassen**   Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um Benachrichtigungen über verpasste Anrufe für Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, zu aktivieren oder zu deaktivieren. Eine Benachrichtigung über einen verpassten Anruf ist eine E-Mail-Nachricht, die an das Postfach eines Benutzers gesendet wird, wenn der Benutzer einen eingehenden Anruf nicht annimmt. Dies ist jedoch nicht die E-Mail-Nachricht, die die für einen Benutzer hinterlassene Sprachnachricht enthält.
            

            > [!NOTE]
            > Wenn Sie Unified Messaging und Lync Server lokal integrieren, stehen Benachrichtigungen über verpasste Anrufe nicht für Benutzer zur Verfügung, die über ein Postfach auf einem Exchange&nbsp;2007- oder Exchange&nbsp;2010-Postfachserver verfügen. Es wird eine Benachrichtigung über einen verpassten Anruf generiert, wenn ein Benutzer sich abmeldet, bevor der Anruf an Unified Messaging gesendet wurde.

            
            Normalerweise bekommt ein Benutzer zwei E-Mail-Nachrichten, wenn er einen eingehenden Anruf verpasst: eine Nachricht, die die Sprachnachricht enthält, und eine Nachricht, die den Benutzer über den verpassten Anruf informiert. Standardmäßig wird beim Erstellen einer UM-Postfachrichtlinie die Benachrichtigung über verpasste Anrufe aktiviert.
        
          - **Voicemail-Wiedergabe über Telefon zulassen**   Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die Funktion "Wiedergabe über Telefon" für Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, zu aktivieren oder zu deaktivieren. Diese Option ist standardmäßig aktiviert und ermöglicht es den Benutzern, ihre Sprachnachrichten über ein beliebiges Telefon wiederzugeben, einschließlich eines Telefons am Arbeitsplatz oder eines Mobiltelefons.
        
          - **Eingehende Faxe zulassen**   Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um den Empfang eingehender Faxnachrichten für Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, zu aktivieren oder zu deaktivieren. Wenn Sie Benutzer für UM aktivieren, ist das Postfach dieser Benutzer standardmäßig in der Lage, Faxnachrichten zu empfangen. Falls diese Option im UM-Wählplan deaktiviert ist, können UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, jedoch keine Faxnachrichten empfangen. In der Standardeinstellung für die UM-Postfachrichtlinie ist diese Option deaktiviert.
            
            Nachdem Sie die Einstellung **Eingehende Faxe zulassen** aktiviert haben, müssen Sie den URI des Partnerfaxservers angeben. Falls die UM-Postfachrichtlinie mit einem Wählplan verknüpft ist, der TCP und TLS verwenden kann, müssen Sie URIs sowohl für TCP als auch für TLS eingeben.
        
          - **Unterstützen Sie Microsoft bei der Verbesserung der Voicemailvorschau**   Mit diesen Optionen ermöglichen Sie es Microsoft, die Qualität der Voicemailvorschau zu verbessern. Sie können folgende Einstellungen aktivieren:
            
              - **Analyse der von Anrufern hinterlassenen Sprachnachrichten zulassen**   Verwenden Sie diese Option, um zur Verbesserung der Qualität der Voicemailvorschau in zukünftigen Versionen von Microsoft Exchange beizutragen, indem Kopien der Sprachnachrichten zur Analyse an Microsoft weitergeleitet werden. Sie können diese Option nicht festlegen, wenn alle Sprachnachrichten geschützt sind.
            
              - **Anrufer mitteilen, dass Sprachnachrichten ggf. analysiert werden**   Verwenden Sie diese Option, um Anrufern mitzuteilen, dass die von ihnen zurückgelassenen Nachrichten eventuell von Microsoft analysiert werden, um die Qualität der Voicemailvorschau zu verbessern, und um den Anrufern auf diese Weise die Möglichkeit zu bieten, ihre Zustimmung zur Nachrichtenweitergabe zu verweigern.
    
      - 
        
        Unter **Nachrichtentext** können Sie die Nachrichtentexteinstellungen für Benutzer konfigurieren, die einer UM-Postfachrichtlinie zugeordnet sind. Sie können beispielsweise den Text der E-Mail-Nachricht festlegen, die an Benutzer gesendet wird, nachdem sie ihre UM-PIN zurückgesetzt haben. Sie können Folgendes konfigurieren:
        
          - **Wenn ein Benutzer für Unified Messaging aktiviert ist**   Der in dieses Textfeld eingegebene Text wird in der E-Mail-Nachricht angezeigt, die an Benutzer gesendet wird, wenn sie für UM aktiviert sind. Wenn das Postfach eines Empfängers für UM aktiviert wird und die Voicemailfunktion für den Benutzer aktiviert ist, wird eine E-Mail-Nachricht mit einer Unified Messaging-Begrüßung an den Benutzer gesendet. Der Text in diesem Textfeld darf nicht mehr als 512 Zeichen lang sein und kann einfache HTML-Formatierung enthalten. In der Standardeinstellung ist in diesem Textfeld kein Text vorhanden.
            
            Diese Nachricht enthält Begrüßungstext und die PIN-Informationen, die der Benutzer für den Zugriff auf das Unified Messaging- oder Voicemailsystem verwendet. Der in dieses Textfeld eingegebene Text wird unten in dieser Begrüßungsnachricht angezeigt. Sie können dieses Textfeld für Informationen wie z. B. die Rufnummern des technischen Supports für Voicemail oder Outlook Voice Access-Nummern verwenden.
            
            Wenn in dieses Textfeld kein Text eingegeben wird, enthält die E-Mail-Nachricht den vom UM- oder Voicemailsystem generierten Standardtext.
            
            In dieses Textfeld eingegebener Text darf unformatiert sein. Er darf auch einfache HTML-Formatierungstags enthalten, wenn Sie Text hervorheben oder Hyperlinks hinzufügen möchten.
            
            **Beispiel 1** Wenn Sie Fragen oder Vorschläge zum Voicemaildienst haben, wenden Sie sich an den Helpdesk unter der Durchwahl 4200.
            
            **Beispiel 2** Wenn Sie Fragen oder Vorschläge zum \<b\>Voicemaildienst\</b\> haben, wenden Sie sich an den Helpdesk unter der Durchwahl 4200, oder besuchen Sie unsere Website unter \<href="http://emp.contoso.com/itinfo/vmail"\>\</a\>.
        
          - **Wenn die Outlook Voice Access-PIN eines Benutzers zurückgesetzt wird**   Der in dieses Textfeld eingegebene Text wird in der E-Mail-Nachricht angezeigt, die an UM-aktivierte Benutzer gesendet wird, nachdem ihre UM-PIN zurückgesetzt wurde.
            
            Eine PIN wird vom UM- oder Voicemailsystem zurückgesetzt, falls mehr als 10 (Standardeinstellung) gescheiterte Anmeldeversuche unternommen wurden oder Benutzer ihre PIN mithilfe der UM-Funktionen von Microsoft Outlook, Outlook Web App oder Outlook Voice Access per Telefon selbst zurücksetzen. Sie können dieses Textfeld verwenden, um Informationen wie z. B. Sicherheitshinweise oder andere sicherheitsbezogene Informationen in die E-Mail-Nachricht aufzunehmen.
            
            Wenn in dieses Textfeld kein Text eingegeben wird, enthält die E-Mail-Nachricht den vom UM-System generierten Standardtext.
            
            Die Länge dieses Textfelds ist auf 512 Zeichen begrenzt. In der Standardeinstellung ist in diesem Textfeld kein Text vorhanden.
            
            In dieses Textfeld eingegebener Text darf unformatiert sein. Er darf auch einfache HTML-Formatierungstags enthalten, wenn Sie Text hervorheben oder Hyperlinks hinzufügen möchten.
        
          - **Wenn ein Benutzer eine Sprachnachricht empfängt**   Der in dieses Textfeld eingegebene Text wird in der E-Mail-Nachricht angezeigt, die an Benutzer gesendet wird, wenn sie eine Sprachnachricht eines Anrufers erhalten. Dieser Text kann z. B. Haftungsausschlüsse mit Informationen zum Weiterleiten von Sprachnachrichten oder Systemsicherheitsrichtlinien enthalten, die das ordnungsgemäße Verfahren für den Umgang mit Sprachnachrichten in Ihrer Organisation beschreiben.
            
            Wenn in dieses Textfeld kein Text eingegeben wird, enthält die E-Mail-Nachricht den vom System generierten Standardtext. Die Länge dieses Textfelds ist auf 512 Zeichen begrenzt. In der Standardeinstellung ist in diesem Textfeld kein Text vorhanden.
            
            In dieses Textfeld eingegebener Text darf unformatiert sein. Er darf auch einfache HTML-Formatierungstags enthalten, wenn Sie Text hervorheben oder Hyperlinks hinzufügen möchten.
        
          - **Wenn ein Benutzer eine Faxnachricht empfängt**   Der in dieses Textfeld eingegebene Text wird in der E-Mail-Nachricht angezeigt, die an Benutzer gesendet wird, wenn in ihrem Postfach eine Faxnachricht eingegangen ist. Sie können in dieses Textfeld z. B. Verzichtserklärungen eingeben, die Informationen zum Weiterleiten von Voicemailnachrichten bereitstellen, oder Systemsicherheitsrichtlinien, die das ordnungsgemäße Verfahren für den Umgang mit Faxnachrichten in Ihrer Organisation beschreiben.
            
            Wenn in dieses Textfeld kein Text eingegeben wird, enthält die E-Mail-Nachricht den vom System generierten Standardtext. Die Länge dieses Textfelds ist auf 512 Zeichen begrenzt. In der Standardeinstellung ist in diesem Textfeld kein Text vorhanden.
    
      - 
        
        Unter **PIN-Richtlinien** können Sie die PIN-Einstellungen für Benutzer konfigurieren, die einer UM-Postfachrichtlinie zugeordnet sind. UM-PINs ermöglichen es Benutzern, per Telefon auf ihren Posteingang zuzugreifen. Beim Konfigurieren der Einstellungen auf dieser Seite können Sie die Mindestanzahl von Ziffern für eine UM-PIN festlegen und angeben, wie viele Anmeldeversuche scheitern dürfen, bevor das Postfach eines Benutzers gesperrt wird.
        
        Planen Sie die UM-PIN-Richtlinien, die Sie in Ihrer Umgebung implementieren, sehr sorgfältig. Falls Sie keine geeigneten UM-PIN-Richtlinien planen und implementieren, kann dies Sicherheitsbedrohungen zur Folge haben und versehentlich nicht autorisierten Zugriff auf Ihr Netzwerk ermöglichen. Sie können Folgendes konfigurieren:
        
          - **Minimale PIN-Länge (Ziffern)**   Verwenden Sie dieses Textfeld, um die Mindestanzahl an Ziffern anzugeben, die die PIN eines UM-Benutzers enthalten muss. Die Standardeinstellung ist sechs Ziffern. Der Bereich der möglichen Werte reicht von 4 bis 24 numerischen Stellen. Diese Einstellung kann nicht deaktiviert werden.
            
            Wenn Sie die Anzahl der Ziffern erhöhen, die für eine PIN erforderlich ist, steigt auch der Sicherheitsgrad für Ihr UM-System. Wenn Sie die Anzahl der Ziffern verringern, die für eine PIN erforderlich ist, wird der Sicherheitsgrad für Ihr Netzwerk gesenkt. Je weniger Ziffern für eine PIN erforderlich sind, desto einfacher ist es für einen möglichen Angreifer, die PIN eines Benutzers zu erraten.
            
            Wenn die Einstellung zu hoch gewählt wird, können die Benutzer Probleme haben, sich ihre PIN zu merken. Wenn die Einstellung jedoch zu niedrig ist, riskieren Sie nicht autorisierte Zugriffe auf das UM-System.
        
          - **Anzahl der PIN-Wiederverwendungen**   Verwenden Sie diese Einstellung, um die Anzahl an unterschiedlichen PINs festzulegen, die ein Benutzer verwenden muss, bevor eine alte PIN erneut verwendet werden darf. Bei den meisten Organisationen sollte dieser Wert bei der Standardeinstellung von 5 PINs, die sich das System merkt, belassen werden. Der PIN-Verlauf kann nicht deaktiviert werden.
            
            Sie können für diese Einstellung einen Wert zwischen 1 und 20 festlegen. Wenn Sie diesen Wert zu niedrig festlegen, kann dies die Benutzer verärgern, weil es schwierig ist, sich so viele PINs zu merken. Wird er zu niedrig festgelegt, kann dies eine Sicherheitsbedrohung für Ihr Netzwerk bedeuten.
        
          - **Gängige PIN-Muster zulassen**   Verwenden Sie diese Einstellung, um die PIN-Komplexitätsanforderungen für UM festzulegen. Diese Komplexitätsanforderungen werden für PIN-Änderungen oder beim Erstellen neuer PINs erzwungen.
            
            Wenn diese Option deaktiviert ist, werden Zahlenfolgen, wiederholte Zahlen und das Suffix der Postfachdurchwahl zurückgewiesen. Wenn diese Option aktiviert ist, wird nur das Suffix der Postfachdurchwahl zurückgewiesen.
            
            Als bewährte Sicherheitsmethode wird empfohlen, diese Einstellung zu deaktivieren. Bei Aktivierung dieser Einstellung dürfen Benutzer-PINs Folgendes nicht enthalten:
            
            Zahlenfolgen wie 123456 oder 456789.
            
            Wiederholte Zahlen wie z. B. 111111 oder 8888888.
            
            Suffix der Postfachdurchwahl.
        
          - **PIN-Gültigkeitsdauer (Tage) erzwingen**   Mithilfe dieses Textfelds können Sie die Anzahl der Tage konfigurieren, nach denen die PIN des UM-aktivierten Benutzers abläuft. Nachdem die PIN abgelaufen ist, muss der Benutzer eine neue UM-PIN erstellen. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung von 60 Tagen festgelegt werden.
            
            Der Wert dieser Einstellung kann zwischen 0 und 999 liegen. Bei der Einstellung 0 sind PINs unbegrenzt gültig. Wenn Sie diesen Wert zu niedrig festlegen, kann dies die Benutzer verärgern, weil sie zu häufig neue PINs erstellen und sich merken müssen.
        
          - **Anzahl der Anmeldefehler vor dem Zurücksetzen der PIN**   Verwenden Sie dieses Textfeld, um festzulegen, wie viele erfolglose oder gescheiterte Anmeldeversuche nacheinander unternommen werden können, bevor das UM-System die PIN eines Benutzers automatisch zurücksetzt. Bei den meisten Organisationen sollte dieser Wert auf die Standardeinstellung von 5 Versuchen festgelegt werden.
            
            Der Wert dieser Einstellung kann zwischen 0 und 999 liegen. Beim Wert 0 ist die Einstellung deaktiviert, und das System setzt die PINs von Benutzern nicht automatisch zurück. Wird der Wert zu niedrig gewählt, kann dies Verärgerung bei den Benutzern auslösen. Bei einem zu hohen Wert erhalten böswillige Benutzer größere Chancen, die PIN zu ermitteln.
            
            Der Wert dieser Einstellung muss niedriger sein als der Wert der Einstellung **Anzahl der Anmeldefehler vor dem Sperren**. Diese Einstellung kann dazu beitragen, Brute-Force-Angriffe auf Benutzer-PINs abzuwehren.
        
          - **Anzahl der Anmeldefehler vor dem Sperren**   Geben Sie in dieses Textfeld die maximale Anzahl an erfolglosen oder gescheiterten Anmeldeversuchen ein, die nacheinander erfolgen dürfen, bevor das Postfach eines Benutzers gesperrt wird.
            
            Wenn ein Benutzer z. B. fünfmal erfolglos versucht, sich bei seinem Postfach anzumelden, setzt das System die PIN des Benutzers basierend auf der Einstellung **Anzahl der Anmeldefehler vor dem Zurücksetzen der PIN** zurück. Versucht der Benutzer wiederum mehr als fünfmal erfolglos, seine neue PIN zu verwenden, setzt das System die PIN erneut zurück. Wenn der Benutzer anschließend nochmals fünfmal erfolglos versucht, seinen neue PIN zu verwenden, wird das Postfach des Benutzers gesperrt. Nachdem das Postfach des Benutzers gesperrt wurde, muss ein Administrator das Postfach für den Benutzer manuell zurücksetzen oder die Sperre aufheben.
            
            Die Einstellung kann auf einen Wert zwischen 1 und 999 festgelegt werden. Wird der Wert zu niedrig gewählt, kann dies Verärgerung bei den Benutzern auslösen. Bei einem zu hohen Wert erhalten böswillige Benutzer größere Chancen, die PIN zu ermitteln. Bei den meisten Organisationen sollte dieser Wert auf die Standardeinstellung von 15 Versuchen festgelegt werden.
            
            Der angegebene Wert muss größer sein als der Wert der Einstellung **Anzahl der Anmeldefehler vor dem Zurücksetzen der PIN**. Diese Einstellung kann dazu beitragen, Brute-Force-Angriffe auf Benutzer-PINs abzuwehren.
    
      - 
        
        Unter **Wählautorisierung** können Sie die Wählregeln für UM-aktivierte Benutzer konfigurieren, die dieser UM-Postfachrichtlinie zugeordnet sind.
        
        Mit diesen Einstellungen können Sie die Durchwahlnummern, die erreichbar sind, oder die Telefonnummern steuern, die von UM-aktivierten Benutzern, die der UM-Postfachrichtlinie zugeordnet sind, gewählt werden können. Sie können Folgendes konfigurieren:
        
          - **Anrufe an Benutzer im selben UM-Wählplan**   Aktivieren Sie dieses Kontrollkästchen, um zuzulassen, dass UM-aktivierte Benutzer, die eine im Wählplan konfigurierte Abonnentenzugriffsnummer anrufen und sich erfolgreich bei ihrem Postfach anmelden, Anrufe an UM-aktivierte Benutzer tätigen oder weiterleiten können, die über Durchwahlnummern innerhalb desselben Wählplans verfügen. Diese Einstellung ist standardmäßig aktiviert.
            
            Wenn Sie diese Einstellung deaktivieren, können UM-aktivierte Benutzer, die eine in einem Wählplan konfigurierte Abonnentenzugriffsnummer anrufen und sich erfolgreich bei ihrem Postfach anmelden, nicht-UM-aktivierte Benutzer oder andere Durchwahlnummern, die keinem UM-aktivierten Benutzer zugeordnet sind, anrufen oder Anrufe an diese weiterleiten. Sie können jedoch keine Anrufe an UM-aktivierte Benutzer weiterleiten, die in der gleichen Wähleinstellung aufgeführt sind. Der Grund dafür ist, dass die Einstellung **Anrufe an jede Durchwahl** standardmäßig aktiviert ist.
        
          - **Anrufe an jede Durchwahl**   Wenn diese Einstellung aktiviert ist, können Benutzer, die eine in einem Wählplan konfigurierte Abonnentenzugriffsnummer anrufen und sich erfolgreich bei ihrem Postfach anmelden, Anrufe bei nicht-UM-aktivierten Benutzern, bei anderen Durchwahlnummern, die keinem UM-aktivierten Benutzer zugeordnet sind, sowie bei UM-aktivierten Benutzern innerhalb des gleichen Wählplans tätigen. Der Grund dafür ist, dass die Einstellung **Anrufe im gleichen UM-Wählplan** standardmäßig aktiviert ist.
            
            Wenn diese Einstellung deaktiviert ist, können Benutzer, die eine in einem Wählplan konfigurierte Outlook Voice Access-Nummer anrufen und sich erfolgreich bei ihrem Postfach anmelden, weder nicht-UM-aktivierte Benutzer noch andere Durchwahlnummern anrufen, die keinem UM-aktivierten Benutzer zugeordnet sind. Sie sind jedoch in der Lage, Anrufe zu tätigen oder Anrufe an Durchwahlnummern, die UM-aktivierten Benutzern zugewiesen sind, weiterzuleiten. Der Grund dafür ist, dass die Einstellung **Anrufe im gleichen UM-Wählplan** standardmäßig aktiviert ist. Die Einstellung **Anrufe an jede Durchwahl** ist standardmäßig aktiviert.
            
            Diese Einstellung kann in einer Umgebung aktiviert werden, in der nicht alle Benutzer UM-aktiviert sind. Sie ist außerdem hilfreich, wenn Sie zulassen möchten, dass Benutzer, die eine in einer Wähleinstellung konfigurierte Outlook Voice Access-Nummer anrufen, Durchwahlnummern anrufen können, die keinem UM-aktivierten Benutzer zugeordnet sind.
        
          - **Autorisierte nationale Wählregelgruppen**   Verwenden Sie diesen Abschnitt, um zulässige nationale Wählregelgruppen hinzuzufügen oder zu entfernen. Standardmäßig sind keine nationalen/regionale Wählregelgruppen für UM-Postfachrichtlinien konfiguriert.
            
            Nationale/regionale Wählregelgruppen werden verwendet, um die Rufnummern innerhalb eines Landes oder einer Region, die Benutzer von Outlook Voice Access anrufen können, zuzulassen oder einzuschränken. Diese Maßnahme hilft dabei, unnötige bzw. nicht autorisierte Telefonate und Gebühren zu vermeiden.
            
            Zum Hinzufügen von nationalen/regionalen Wählregelgruppen müssen Sie zunächst die entsprechenden nationalen/regionalen Wählregelgruppen in der Wähleinstellung erstellen, die der UM-Postfachrichtlinie zugeordnet ist, und anschließend der Wählregelgruppe die entsprechenden Wählregeleinträge hinzufügen. Wenn Sie die erforderlichen Wählregelgruppen für den Wählplan erstellt haben, müssen Sie die Wählregelgruppen zur Liste der Wähleinschränkungen unter **Wählautorisierung** für die UM-Postfachrichtlinie hinzufügen.
            
            Mithilfe von nationalen Wählregelgruppen können Sie Unified Messaging in die Lage versetzen, den Zugriff auf Rufnummern in einem Land zuzulassen oder einzuschränken. Dies gilt für Outlook Voice Access-Benutzer, die eine Outlook Voice Access-Nummer angerufen haben.
        
          - **Autorisierte internationale Wählregelgruppen**   Verwenden Sie diesen Abschnitt, um zulässige internationale Wählregelgruppen hinzuzufügen oder zu entfernen. Standardmäßig sind keine internationalen Wählregelgruppen für UM-Postfachrichtlinien konfiguriert.
            
            Zum Hinzufügen von internationalen Wählregelgruppen müssen Sie zunächst die entsprechenden internationalen Wählregelgruppen in der Wähleinstellung erstellen, die der UM-Postfachrichtlinie zugeordnet ist, und anschließend der Wählregelgruppe die entsprechenden Wählregeleinträge hinzufügen. Wenn Sie die erforderlichen Wählregelgruppen erstellt haben, müssen Sie diese den Wähleinschränkungen für die UM-Postfachrichtlinie hinzufügen.
            
            Mithilfe von internationalen Wählregelgruppen können Sie Unified Messaging in die Lage versetzen, den Zugriff auf Rufnummern außerhalb eines Lands oder einer Region zuzulassen oder einzuschränken. Dies findet Anwendung bei Outlook Voice Access-Benutzern, die eine Outlook Voice Access-Nummer angerufen haben.
            
            Internationale Wählregelgruppen werden verwendet, um die Rufnummern außerhalb eines Landes oder einer Region, die Benutzer von Outlook Voice Access anrufen können, zuzulassen oder einzuschränken. Diese Maßnahme hilft dabei, unnötige bzw. nicht autorisierte Telefonate und Gebühren zu vermeiden.
    
      - 
        
        Unter **Geschützte Voicemail** können Sie die folgenden Einstellungen konfigurieren:
        
          - **Sprachnachrichten von nicht authentifizierten Anrufern schützen**   Wählen Sie aus der Dropdownliste eine der folgenden Optionen aus, um festzulegen, ob bei einem eingehenden Anruf, der von Unified Messaging beantwortet wird, Sprachnachrichten geschützt werden. Diese Einstellung gilt für Sprachnachrichten, die an UM-aktivierte Benutzer gesendet werden, wenn diese ein Gespräch nicht entgegennehmen. Diese Einstellung gilt auch für direkt an UM-aktivierte Benutzer gesendete Sprachnachrichten, wenn der Anrufer eine automatische UM-Telefonzentrale verwendet. Sie können Folgendes konfigurieren:
            
            **Keine**   Verwenden Sie diese Einstellung, wenn an UM-aktivierte Benutzer gesendete Sprachnachrichten nicht geschützt werden sollen.
            
            **Privat**   Verwenden Sie diese Einstellung, wenn Sie nur Sprachnachrichten schützen möchten, die vom Anrufer als privat gekennzeichnet wurden.
            
            **Alle**   Verwenden Sie diese Einstellung, wenn Sie alle Sprachnachrichten einschließlich der nicht als privat gekennzeichneten Nachrichten schützen möchten.
        
          - **Sprachnachrichten von authentifizierten Anrufern schützen**   Wählen Sie aus der Dropdownliste eine der folgenden Optionen aus, um festzulegen, ob bei einem eingehenden Anruf, der von Unified Messaging beantwortet wird, Sprachnachrichten geschützt werden. Diese Einstellung gilt für Sprachnachrichten, die an UM-aktivierte Benutzer gesendet werden, wenn diese ein Gespräch nicht entgegennehmen. Diese Einstellung gilt auch, wenn Anrufer sich über Outlook Voice Access bei ihrem Postfach anmelden und anschließend eine Sprachnachricht erstellen und senden. Sie können Folgendes konfigurieren:
            
            **Keine**   Verwenden Sie diese Einstellung, wenn an UM-aktivierte Benutzer gesendete Sprachnachrichten nicht geschützt werden sollen.
            
            **Privat**   Verwenden Sie diese Einstellung, wenn Sie nur Sprachnachrichten schützen möchten, die vom Anrufer als privat gekennzeichnet wurden.
            
            **Alle**   Verwenden Sie diese Einstellung, wenn Sie alle Sprachnachrichten einschließlich der nicht als privat gekennzeichneten Nachrichten schützen möchten.
        
          - **"Wiedergabe über Telefon" für geschützte Sprachnachrichten anfordern**   Aktivieren Sie dieses Kontrollkästchen, wenn Sie erzwingen möchten, dass Benutzer, die geschützte Sprachnachrichten erhalten, die Funktion "Wiedergabe über Telefon" verwenden. Falls die Clientsoftware keine Rechteverwaltung unterstützt, müssen die Benutzer Outlook Voice Access verwenden. Die Funktion "Wiedergabe über Telefon" ist nur bei Clients anwendbar, die eine Version von Outlook mit Unterstützung der Rechteverwaltung verwenden. Bei Outlook 2007 und früheren Versionen ohne Unterstützung der Rechteverwaltung sowie bei Outlook Web App-Clients können Benutzer geschützte Sprachnachrichten nur über Outlook Voice Access abhören.
            
            In der Standardeinstellung müssen alle Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, zum Abhören von geschützten Sprachnachrichten die Funktion "Wiedergabe über Telefon" verwenden. Damit wird verhindert, dass die Sprachnachricht mit einem Media Players über Computerlautsprecher oder auf einem Mobiltelefon wiedergegeben wird und dabei von anderen Personen gehört werden kann. Auch wenn diese Option aktiviert ist, können UM-aktivierte Benutzer weiterhin Outlook Voice Access zum Abhören der geschützten Sprachnachricht verwenden.
            
            Dies ist insbesondere dann sinnvoll, wenn UM-aktivierte Benutzer öffentliche Computer, Laptops an öffentlich zugänglichen Orten oder die Medienwiedergabe ihres Mobiltelefons zum Abhören von Sprachnachrichten verwenden, die private Informationen enthalten können.
        
          - **Sprachantworten auf E-Mail- und Kalenderelemente zulassen**   Verwenden Sie diese Option, um UM-aktivierten Benutzern das Senden von Sprachantworten auf geschützte Voicemailnachrichten zu erlauben. Standardmäßig ist diese aktiviert. Wenn Sie diese Option deaktivieren, ist es UM-aktivierten Benutzern, die eine geschützte Voicemailnachricht erhalten, nicht möglich, mit Outlook Voice Access auf E-Mail- und Kalenderelemente zu antworten.
        
          - **Nachricht, die an Benutzer gesendet werden soll, die keine Unterstützung durch Windows-Rechteverwaltung haben**   Der Zugriff auf geschützte Voicemail ist nur mit E-Mail-Clients möglich, die die Verwaltung von Informationsrechten (Information Rights Management, IRM) unterstützen, oder wenn ein UM-aktivierter Benutzer Outlook Voice Access verwendet, um auf die geschützte Voicemailnachricht zuzugreifen.
            
            Wird eine geschützte Voicemailnachricht an einen E-Mail-Client ohne IRM-Unterstützung gesendet, erhält der Benutzer eine E-Mail-Nachricht mit dem Text, den Sie in dieses Feld eingeben. Dieser Text sollte erläutern, was der Benutzer tun muss, um die geschützte Voicemailnachricht empfangen zu können.

## Verwalten einer UM-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel werden die PIN-Einstellungen für Benutzer festgelegt, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 8 -MaxLogonAttempts 12 -MinPINLength 8 -PINHistoryCount 10 -PINLifetime 60 -ResetPINText "The PIN that is used to allow you access to your mailbox using Outlook Voice Access has been reset."

In diesem Beispiel werden die nationalen/regionalen und internationalen Gruppen aus den Gruppen ausgewählt, die für die UM-Wähleinstellungen der UM-Postfachrichtlinie konfiguriert sind. UM-aktivierte Benutzer, die dieser UM-Postfachrichtlinie zugeordnet sind, können ausgehende Anrufe entsprechend den für diese Gruppen definierten Regeln ausführen.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowDialPlanSubscribers $true -AllowedInCountryOrRegionGroups InCountry/RegionGroup1,InCountry/RegionGroup2 -AllowedInternationalGroups InternationalGroup1,InternationalGroup2 -AllowExtensions $true 

In diesem Beispiel wird der Text von Sprachnachrichten, die an UM-aktivierte Benutzer gesendet werden, sowie der Text der E-Mail-Nachricht konfiguriert, die ein Benutzer nach der UM-Aktivierung erhält.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -UMEnabledText "You have been enabled for Unified Messaging." -VoiceMailText "You have received a voice message from Microsoft Exchange 2013 Unified Messaging." 

## Anzeigen der Eigenschaften von UM-Postfachrichtlinien mithilfe der Shell

In diesem Beispiel wird eine formatierte Liste aller UM-Postfachrichtlinien in der Active Directory-Gesamtstruktur zurückgegeben.

    Get-UMMailboxPolicy | Format-List

In diesem Beispiel werden die Eigenschaften und Werte für die UM-Postfachrichtlinie `MyUMMailboxPolicy` zurückgegeben.

    Get-UMMailboxPolicy -Identity MyUMMailboxPolicy


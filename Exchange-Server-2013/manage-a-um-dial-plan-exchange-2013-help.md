---
title: 'Verwalten eines UM-Wählplans: Exchange 2013 Help'
TOCTitle: Verwalten eines UM-Wählplans
ms:assetid: a89735e4-36ec-49fb-ad0f-192fad37e801
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124090(v=EXCHG.150)
ms:contentKeyID: 50476403
ms.date: 04/27/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.DialPlanGeneralPropertyPage
ms.translationtype: HT
---

# Verwalten eines UM-Wählplans

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2018-04-26_

Nach Erstellen von Unified Messaging-Wähleinstellungen (UM) können Sie verschiedene Einstellungen anzeigen und konfigurieren. Sie können beispielsweise den Grad der VoIP-Sicherheit (Unified Messaging), den Audiocodec und Wähleinschränkungen konfigurieren. Die von Ihnen konfigurierten UM-Wählplaneinstellungen wirken sich auf alle Benutzer aus, die diesen Einstellungen über eine UM-Postfachrichtlinie zugeordnet sind.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anzeigen oder Konfigurieren von UM-Wählplaneinstellungen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie anzeigen oder ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**. Über die Konfigurationsoptionen können Sie so, wie dies in den folgenden Schritten beschrieben ist, bestimmte Wählplaneinstellungen anzeigen sowie Features aktivieren oder deaktivieren.

4.  **Allgemein**   Auf dieser Seite können Sie bestimmte Wählplaneinstellungen anzeigen sowie Features für UM-aktivierte Benutzer aktivieren oder deaktivieren:
    
      - **Name**   Dies ist der Name des Wählplans, der erstellt wurde. Der Name der UM-Wähleinstellungen kann eine Länge von maximal 64 Zeichen haben und Leerzeichen enthalten. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - Wenngleich der Name eines UM-Wählplans Leerzeichen enthalten darf, ist bei der Integration von Unified Messaging in Office Communications Server 2007 R2 oder Microsoft Lync Server die Verwendung von Leerzeichen im Namen von Wählplänen nicht zulässig. Wenn Sie daher einen Wählplan mit Leerzeichen im Anzeigenamen erstellt haben und Sie eine Integration in Office Communications Server 2007 R2 oder Lync Server durchführen, müssen Sie diesen Wählplan zunächst löschen und einen anderen Wählplan erstellen, der keine Leerzeichen im Anzeigenamen aufweist.
        

        > [!IMPORTANT]
        > Das Feld für den Namen der Wähleinstellungen kann zwar 64&nbsp;Zeichen aufnehmen, der Name der Wähleinstellungen darf jedoch höchstens 49&nbsp;Zeichen umfassen. Wenn Sie versuchen, einen Namen von Wähleinstellungen mit mehr als 49 Zeichen zu erstellen, wird eine Fehlermeldung angezeigt. Die Nachricht gibt an, dass die UM-Postfachrichtlinie nicht erstellt werden konnte, da der Name des UM-Wählplans zu lang ist. Wie bereits weiter oben erwähnt, liegt das daran, dass bei der Erstellung eines Wählplans auch eine UM-Standardpostfachrichtlinie mit dem Namen "Standardrichtlinie für <EM>&lt;Name_der_Wähleinstellungen&gt;</EM>" erstellt wird. Wenn die 15 Zeichen in der Standardrichtlinie zum Namen des Wählplans addiert werden, überschreitet die Gesamtzahl der Zeichen die Beschränkung. Der Parameter <EM>name</EM> für den UM-Wählplan und die UM-Postfachrichtlinie kann insgesamt eine Länge von 64&nbsp;Zeichen haben. Wenn der Name der Wähleinstellungen allerdings aus mehr als 49 Zeichen besteht, hat der Name der standardmäßigen UM-Postfachrichtlinie eine Länge von mehr als 64 Zeichen. Dies wird nicht unterstützt.

    
      - **Durchwahllänge (Ziffern)**   Dies ist die Anzahl von Ziffern in der Durchwahl für Benutzer, die diesem Wählplan zugeordnet sind. Wenn beispielsweise ein Benutzer, der bestimmten Wähleinstellungen zugeordnet ist, eine vierstellige Durchwahl wählt, um einen anderen Benutzer in den gleichen Wähleinstellungen anzurufen, wählen Sie 4 als die Anzahl der Stellen in der Durchwahl aus.
        
        Die Anzahl von Ziffern für Durchwahlnummern basiert auf dem Telefoniewählplan, der auf einer IP-Nebenstellenanlage oder Nebenstellenanlage eingerichtet wurde. Dies ist ein erforderliches Feld mit Werten von 1 bis 20. Die typische Durchwahllänge ist 3 bis 7 Stellen. Wenn in der vorhandenen Telefonieumgebung Durchwahlnummern verwendet werden, müssen Sie beim Erstellen der UM-Wähleinstellungen eine Anzahl für die Stellen festlegen, die mit der Anzahl der Stellen in diesen Durchwahlen übereinstimmt.
    
      - **Wählplantyp**   Ein Uniform Resource Identifier (URI) ist eine Zeichenfolge, die eine Ressource identifiziert bzw. benennt. Der Hauptzweck dieser Identifizierung ist es, die VoIP-Geräte und PBX-Anlagen für die Kommunikation mit anderen Geräten über ein Netzwerk mithilfe bestimmter Protokolle zu aktivieren. URIs sind in Schemas definiert, die eine bestimmte Syntax und ein Format sowie die Protokolle für den Aufruf definieren. Einfach ausgedrückt: Dieses Format wird von der IP-PBX oder PBX übergeben, und der Typ des von Ihnen erstellten Wählplans muss dieses Format aufweisen. Wenn Sie einen UM-Wählplan erstellt haben, können Sie den Typ des Wählplans nur ändern, wenn Sie den Wählplan löschen und anschließend mit dem richtigen Wählplantyp neu erstellen. Sie können eine der folgenden Wählplantypen auswählen:
        
          - **Telefondurchwahl**   Dies ist der häufigste Wählplantyp. Die Teilnehmerinformationen des Anrufenden und des Angerufenen vom VoIP-Gateway oder von der IP-Nebenstellenanlage werden in einem der folgenden Formate aufgeführt: Tel:512345 oder 512345@\<*IP-Adresse*\>. Dies ist der Standardtyp für Wählpläne.
        
          - **SIP-URI**   Verwenden Sie diesen Wählplantyp, wenn Sie einen SIP-URI-Wählplan (Session Initiation Protocol) verwenden müssen, z. B. bei einer IP-Nebenstellenanlage, die das SIP-Routing unterstützt, einer SIP-aktivierten PBX-Anlage, oder wenn Sie Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server und Unified Messaging integrieren. Die Teilnehmerinformationen des Anrufenden und des Angerufenen vom VoIP-Gateway. Eine IP-Nebenstellenanlage, eine SIP-aktivierte PBX-Anlage oder Communications Server 2007 R2 oder Lync Server wird als SIP-Adresse im folgenden Format aufgelistet: sip:\<*Benutzername*\>@\<*Domäne* oder *IP-Adresse*\>:Port.
        
          - **E.164**   E.164 ist ein internationaler Nummerierungsplan für Telefonsysteme, in dem jede zugeordnete Nummer einen Ländercode (Country Code, CC), einen nationalen Zielcode (National Destination Code, NDC) und eine Teilnehmernummer (Subscriber Number, SN) enthält. Die vom VoIP-Gateway und der PBX-Anlage oder der IP-Nebenstellenanlage übermittelten Teilnehmerinformationen des Anrufenden und des Angerufenen werden im folgenden Format aufgeführt: Tel:+14255550123.
        

        > [!NOTE]
        > Wenn Sie einen Wählplan erstellt haben, können Sie den Typ des Wählplans nur ändern, wenn Sie den Wählplan löschen und anschließend mit dem richtigen Wählplantyp neu erstellen.

    
      - **VoIP-Sicherheitsmodus**   Verwenden Sie diese Dropdownliste, um die VoIP-Sicherheitseinstellung für den UM-Wählplan auszuwählen. Sie können eine der folgenden Sicherheitseinstellungen für die Wähleinstellungen auswählen:
        
          - **Ungesichert**   Wenn Sie einen UM-Wählplan erstellen, wird dieser standardmäßig so eingestellt, dass weder SIP-Signalisierungs- noch RTP-Datenverkehr verschlüsselt wird. Im ungesicherten Modus senden und empfangen die dem UM-Wählplan zugeordneten Exchange-Server Daten von VoIP-Gateways, IP-Nebenstellenanlagen, SBCs und anderen Exchange-Servern unverschlüsselt. Im ungesicherten Modus werden weder der RTP-Medienkanal (Realtime Transport Protocol) noch die SIP-Signalinformationen verschlüsselt.
        
          - **SIP-gesichert**   Wenn Sie **SIP-gesichert** auswählen, wird nur der SIP-Signalverkehr verschlüsselt, und die RTP-Medienkanäle verwenden weiterhin das unverschlüsselte TCP. Im gesicherten Modus werden der SIP-Signalverkehr und die VoIP-Daten mithilfe von MTLS (Mutual Transport Layer Security) verschlüsselt.
        
          - **Gesichert**   Bei Auswahl von **Gesichert** werden sowohl die SIP-Signale als auch die RTP-Medienkanäle verschlüsselt. Sowohl der sichere Signalmedienkanal, der SRTP (Secure Realtime Transport Protocol) verwendet, als auch der SIP-Signaldatenverkehr nutzen MTLS zum Verschlüsseln der VoIP-Daten.

5.  **Kurzwahlnummern**   Auf dieser Seite können Sie die Kurzwahlnummern für einen UM-Wählplan konfigurieren. Einige Einstellungen für Kurzwahlnummern können in den Wähleinstellungen konfiguriert werden. Dazu gehören Optionen für eingehende und ausgehende Anrufe. Sie können Folgendes konfigurieren:
    
      - **Kurzwahlnummern für ausgehende Anrufe**   Mit diesen Einstellungen können Sie die Kurzwahlnummern für ausgehende Anrufe angeben, die von UM-aktivierten Benutzern geführt werden können. Diese ausgehenden Anrufe sind Anrufe, die mit Outlook Voice Access oder aus einer Voicemailnachricht getätigt werden.
        
          - **Amtskennziffer**   In diesem Feld können Sie die Nummer bzw. Nummern eingeben, die für den Zugriff auf eine Amtsleitung für ausgehende externe Anrufe verwendet wird/werden. Diese Nummer wird vor der eigentlichen Telefonnummer gewählt. Sie wird auch als Amtsvorwahl bezeichnet. In diesem Feld werden nur 1 bis 16 Ziffern akzeptiert. Die meisten Organisationen verwenden die Nummer 9. Das Feld enthält standardmäßig keinen Eintrag.
            
            Diese Einstellung wird häufig in Telefonieumgebungen verwendet, in denen eine Nebenstellenanlage oder IP-Nebenstellenanlage am Standort genutzt wird (am Standort oder durch eine Organisation gewartet). Eine Konfiguration ist möglicherweise nicht erforderlich, wenn die Telefonieumgebung der Organisation von einem externen Unternehmen oder Dienstleister verwaltet wird.
        
          - **Internationale VAZ**   Geben Sie in dieses Feld die Nummer ein, die für internationale Telefonnummern bei ausgehenden Anrufen verwendet wird. Diese Nummer wird vor der eigentlichen Telefonnummer gewählt. Dieses Feld ist standardmäßig nicht ausgefüllt. In diesem Feld werden nur 1 bis 4 Ziffern akzeptiert. Die internationale VAZ lautet für die USA 011 und für Europa 00.
        
          - **Rufnummernpräfix, national**   In dieses Feld geben Sie die Nummer ein, die zum Wählen von Telefonnummern außerhalb des Ortsnetzes, aber innerhalb des Lands/der Region verwendet wird. Diese Nummer wird vor der eigentlichen Telefonnummer gewählt. Dieses Feld ist standardmäßig nicht ausgefüllt. In diesem Feld werden nur 1 bis 4 Ziffern akzeptiert. In Europa wird beispielsweise 0, in Nordamerika hingegen 1 verwendet.
        
          - **Länder-/Regionscode** Verwenden Sie dieses Feld zur Eingabe der Landes-/Regionskennzahl für ausgehende Anrufe. Diese Nummer wird vor der eigentlichen Telefonnummer gewählt. Dieses Feld ist standardmäßig nicht ausgefüllt. In diesem Feld werden nur 1 bis 4 Ziffern akzeptiert. In den USA wird beispielsweise als Landes-/Regionskennzahl 1, in Großbritannien 44 verwendet.
    
      - **Nummernformate zum Wählen in UM-Wählplänen**   Mit diesen Einstellungen können Sie Anrufe zwischen Benutzern in getrennten Wählplänen konfigurieren, wenn die Benutzer Anrufe zwischen den Wählplänen tätigen.
        
          - **Nationales Nummernformat**   Geben Sie in diesem Feld an, wie die Telefonnummer eines Benutzers von den Exchange-Servern gewählt werden soll, wenn sich Benutzer in einem anderen Wählplan befinden, der dieselbe Landeskennzahl hat. Diese Information wird von automatischen Telefonzentralen sowie dann verwendet, wenn ein Outlook Voice Access-Benutzer den Benutzer im Verzeichnis sucht und anzurufen versucht.
            
            Dieser Eintrag besteht aus einem Nummernpräfix und einer variablen Anzahl von Zeichen (beispielsweise 020*xxxxxxx*). Zur Bestimmung der Telefonnummer fügt Unified Messaging die letzten *x* Ziffern aus der Telefonnummer, die im Verzeichnis angegeben ist, an das angegebene Präfix an.
        
          - **Internationales Nummernformat**   Geben Sie in diesem Feld an, wie die Telefonnummer eines Benutzers von Unified Messaging gewählt werden soll, wenn sich Benutzer in unterschiedlichen Wählplänen befinden, die unterschiedliche Landeskennzahlen haben. Diese Information wird von einer automatischen Telefonzentrale sowie dann verwendet, wenn ein Outlook Voice Access-Benutzer den Benutzer im Verzeichnis sucht und anzurufen versucht.
            
            Dieser Eintrag besteht aus einem Nummernpräfix und einer variablen Anzahl von Zeichen, z. B. 4420*xxxxxxx*. Zur Ermittlung der Telefonnummer fügt Unified Messaging die letzten *x* Ziffern zu dem angegebenen Präfix der Telefonnummer hinzu, die im Verzeichnis angegeben ist.
        
          - **Nummernformate für eingehende Anrufe im gleichen Wählplan**   Über dieses Feld können Sie Nummernformate für eingehende Anrufe hinzufügen oder entfernen, die zwischen Benutzern im gleichen Wählplan getätigt werden. In dieses Feld können Sie sowohl Zahlen als auch den Buchstaben "x" als Platzhalterzeichen eingeben. In diesem Feld können keine anderen Buchstaben verwendet werden.
            
            Fügen Sie für eingehende Anrufe im gleichen Wählplan ein Zahlenformat hinzu. Wenn Sie beispielsweise ein Zahlenformat für Durchwahlen mit 5 Ziffern hinzufügen möchten, geben Sie "142570xxxxx" ein, und klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Klicken Sie auf ![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um ein Nummernformat zu entfernen.

6.  **Outlook Voice Access**   Auf dieser Seite können Sie die Outlook Voice Access-Einstellungen für den UM-Wählplan konfigurieren. Mit Outlook Voice Access können Benutzer auf ihre einzelnen Postfächer zugreifen, um E-Mails, Sprachnachrichten, Kontakte und Kalenderinformationen über ein Telefon abzurufen. Sie können folgende Informationen anzeigen oder konfigurieren:
    
      - **Begrüßung**   In diesem schreibgeschützten Feld wird der Name der Audiodatei angezeigt, die für die Begrüßung verwendet wird.
        
          - **Standardbegrüßung**   Der Willkommensgruß wird verwendet, wenn ein Outlook Voice Access-Benutzer oder ein anderer Anrufer die Outlook Voice Access-Nummer anruft und eine Verzeichnissuche ausführt. Diese Audiodatei wird als Standardbegrüßung für einen Satz mit UM-Wähleinstellungen verwendet. Sie können diese Begrüßung jedoch ändern und stattdessen eine unternehmensspezifische Ansage bereitstellen. Beispiel: "Willkommen bei Outlook Voice Access von Contoso, Ltd."
            
            Wenn Sie diese Begrüßung anpassen möchten, müssen Sie zuerst eine entsprechende Ansage aufzeichnen, diese als WAV-Datei speichern und dann den Wählplan so konfigurieren, dass diese Begrüßung verwendet wird. Die Länge des Dateinamens und Pfads darf 255 Zeichen nicht überschreiten.
            
            Sie können eine angepasste Begrüßung hinzufügen, indem Sie auf **Ändern** und dann auf **Durchsuchen** klicken, um eine zuvor aufgezeichnete angepasste Ansage auszuwählen und die Audiodatei (WAV) anzugeben, die für den Willkommensgruß verwendet werden soll. Wenn Sie keine Audiodatei angeben, wird für Outlook Voice Access-Anrufer eine Standardbegrüßung mit folgendem Text abgespielt: "Willkommen. Sie sind mit Microsoft Exchange verbunden."
    
      - **Informationsansage**   Ist diese Option aktiviert, wird diese optionale Aufzeichnung unmittelbar nach der Begrüßung abgespielt, die während oder außerhalb der Geschäftszeiten verwendet wird. In einer Informationsansage können die Sicherheitsrichtlinien einer Organisation mitgeteilt werden, die für ein Zugreifen auf das System gelten. Beispiel: "Wenn Sie über Outlook Voice Access auf unser System zugreifen, stimmen Sie den Bedingungen unserer Geschäftsvereinbarung zu, und es gelten alle Sicherheitsrichtlinien für unsere Organisation. Der Zugriff auf unser System wird überwacht, und ein Verschaffen von unzulässigem Zugriff wird strafrechtlich verfolgt." Eine Informationsansage kann ebenfalls Informationen enthalten, die für die Einhaltung von Organisationsrichtlinien erforderlich sind, wie zum Beispiel "Anrufe können zu Schulungszwecken überwacht werden." Falls es wichtig ist, dass Anrufer die Informationsansage in voller Länge hören, kann sie so konfiguriert werden, dass keine Unterbrechung möglich ist.
        
        Standardmäßig ist für UM-Wählpläne keine Informationsansage konfiguriert. Wenn Sie eine Informationsansage aktivieren und eine auf Ihre Organisation abgestimmte benutzerdefinierte Audiodatei verwenden möchten, klicken Sie auf **Ändern** und dann auf **Durchsuchen**.
    
      - **Unterbrechen der Ansage zulassen**   Aktivieren Sie dieses Kontrollkästchen, um dem Outlook Voice Access-Anrufer ein Unterbrechen der Informationsansage zu ermöglichen. Wenn Sie lange Informationsansagen haben, sollten Sie dies tun. Outlook Voice Access-Benutzer ärgern sich möglicherweise, wenn die Informationsansage zu lang ist und nicht unterbrochen werden kann, um auf die Optionen zuzugreifen, die vom UM-Wählplan bereitgestellt werden.
    
      - **Outlook Voice Access-Nummern**   Fügen Sie in diesem Feld eine Telefonnummer oder Durchwahl oder einen SIP-URI hinzu, die oder den Outlook Voice Access-Benutzer anrufen, um über Outlook Voice Access auf das Voicemailsystem zuzugreifen. In den meisten Fällen wird eine Durchwahl oder eine externe Telefonnummer eingegeben. Da in diesem Feld jedoch alle alphanumerische Zeichen zulässig sind, kann ein SIP-URI angegeben werden, wenn eine IP-Nebenstellenanlage, Office Communications Server 2007 R2 oder Microsoft Lync Server verwendet wird.
        
        Beim Erstellen eines Wählplans werden standardmäßig keine Outlook Voice Access-Nummern definiert. Sollen Outlook Voice Access-Benutzer in der Lage sein, sich in Outlook Voice Access einzuwählen, müssen Sie mindestens eine Telefonnummer konfigurieren. Die Nummer darf nicht mehr als 20 alphanumerische Zeichen enthalten.
        
        Wenn Sie diese Nummer im Wählplan konfigurieren, wird sie in Microsoft OfficeOutlook 2007 oder höheren Versionen und Outlook Web App für Voicemailoptionen angezeigt.
        
        Geben Sie die Nummer in das Feld ein, und klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue Outlook Voice Access-Nummer hinzuzufügen. Klicken Sie auf ![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um eine Outlook Voice Access-Nummer zu entfernen.

7.  **Einstellungen**   Auf dieser Seite können Sie die Wählplaneinstellungen für Unified Messaging konfigurieren. Wenn Sie Einstellungen auf dieser Seite konfigurieren, können Sie steuern, wie Outlook Voice Access-Benutzer und externe Anrufer, die bei einer mit dem Wählplan verknüpften Telefonzentrale anrufen, Benutzer in Ihrer Organisation finden, und Sie können den Audiocodec, der für Voicemailnachrichten verwendet wird, die Anzahl von Anmeldefehlern sowie Timeoutwerte festlegen. Sie können Folgendes konfigurieren:
    
      - **Primäre Methode für Namenssuche**   Wählen Sie in dieser Liste aus, welche primäre Methode Anrufer bei der Einwahl in das System zur Benutzersuche verwenden sollen.
        
        Standardmäßig ist **Nachname Vorname** ausgewählt. Bei dieser Einstellung geben Benutzer bei der Suche nach Benutzern im Verzeichnis zuerst den Nachnamen und dann den Vornamen ein.
        
        Wenn ein Outlook Voice Access-Benutzer eine Outlook Voice Access-Nummer für den Zugriff auf sein Postfach anruft, ein Anrufer eine Outlook Voice Access-Nummer zum Durchführen einer Verzeichnissuche anruft oder ein Anrufer eine mit einem UM-Wählplan verknüpfte automatische Telefonzentrale anruft, können diese Benutzer nach einem Benutzer im Verzeichnis suchen, indem sie den Namen oder den Alias dieses Benutzers buchstabieren.
        
        Sie müssen eine der unterstützten Methoden auswählen, um die primäre Methode für Wahl nach Namen verwenden zu können. Die folgenden Methoden werden unterstützt:
        
          - **Nachn., Vorn. (Standardeinstellung)**
        
          - **Vorname Nachname**
        
          - **SMTP-Adresse**
    
      - **Sekundäre Methode für Namenssuche**   Wählen Sie in dieser Liste aus, welche sekundäre Methode Anrufer bei der Einwahl in das System zur Benutzersuche verwenden sollen.
        
        Standardmäßig ist **SMTP-Adresse** ausgewählt. Wenn ein Benutzer nach einem Benutzer im Verzeichnis sucht, gibt er bei dieser Einstellung den E-Mail-Alias oder die SMTP-Adresse des Benutzers ein.
        
        Wenn ein Outlook Voice Access-Benutzer eine Outlook Voice Access-Nummer für den Zugriff auf sein Postfach anruft, ein Anrufer eine Outlook Voice Access-Nummer zum Durchführen einer Verzeichnissuche anruft oder ein Anrufer eine mit einem UM-Wählplan verknüpfte automatische Telefonzentrale anruft, können diese Benutzer nach einem Benutzer im Verzeichnis suchen, indem sie den Namen oder den Alias dieses Benutzers buchstabieren. Wenn Sie eine dieser Optionen auswählen, können Anrufer die primäre oder die sekundäre Methode für die Namenssuche verwenden, um nach Benutzern im Verzeichnis zu suchen.
        
        Sie müssen keine der vier unterstützten Methoden auswählen. Wenn Sie keine sekundäre Methode für die Suche nach Benutzern auswählen, können Anrufer nur eine Methode für diese Suche nutzen. Die folgenden Optionen sind verfügbar:
        
          - **Nachname Vorname**
        
          - **Vorname Nachname**
        
          - **SMTP-Adresse** (Standard)
        
          - **Keine**
    
      - **Audiocodec**   Wählen Sie in dieser Liste den von den Wähleinstellungen zu verwendenden Audiocodec aus. Wenn ein Anrufer einen Benutzer anruft, der einem bestimmten Wählplan zugeordnet ist, und eine Sprachnachricht hinterlässt, verwendet Unified Messaging den in dieser Liste ausgewählten Audiocodec, um Sprachnachrichten aufzuzeichnen, die an voicemailaktivierte Benutzer gesendet werden. Folgende drei Audiocodecs werden unterstützt:
        
          - **MP3** (Standardeinstellung)
        
          - **WMA** (Windows Media Audio)
        
          - **G711** (Pulse Code Modulation (PCM) Linear)
        
          - **GSM** (Group System Mobile 06.10)
        
        Standardmäßig ist das MP3-Format ausgewählt. Das MP3-Format ist ein gängiges Audiodateiformat, das zum weitreichenden Verkleinern der Audiodatei dient und auf MP3-Playern und anderen Audiogeräten weite Verbreitung gefunden hat. MP3 ist ein plattformübergreifender Audiocodectyp, der mit vielen Mobiltelefonen und -geräten sowie verschiedenen Computerbetriebssystemen kompatibel ist.
        
        WMA wird wegen seiner besonders starken Komprimierung verwendet und hat qualitativ hochwertige Formateigenschaften. G.711 PCM Linear ist ein Audiocodecformat mit Telefonqualität, das den niedrigsten Komprimierungsgrad und die geringste Formatqualität hat. GSM 06.10 ist ein Audiocodecformat, das von Mobiltelefonherstellern verwendet wird. Dieses Format wird als Standard bei digitalen Mobiltelefondiensten benutzt.
        
        Wenn Sie Bedenken bezüglich der Datenträgerkapazität von Benutzern haben, wählen Sie WMA als Audiocodec aus. Die Größe von Sprachnachrichten reduziert sich auf ungefähr die Hälfte, wenn diese im WMA-Format statt mit einem der anderen Audiocodecs gespeichert werden.
    
      - **Durchwahl für Vermittlungsstelle**   Geben Sie in diesem Textfeld die Telefonnummer oder eine Durchwahl für die Vermittlungsstelle der Wähleinstellungen ein. Diese unterscheidet sich von einer Vermittlungsstellendurchwahl, die für eine automatische UM-Telefonzentrale konfiguriert ist. Sie können aber für beide Typen von Vermittlungsstellen dieselbe Telefon- oder Durchwahlnummer angeben.
        
        Sie können diese Einstellung so konfigurieren, dass die Anrufe ggf. an eine automatische Telefonzentrale, eine Vermittlungskraft, externe Rufnummern oder Durchwahlnummern umgeleitet werden.
        
        Wenn ein Anrufer bei Verwendung der Telefontastatur die Null (0) drückt oder "Empfang" oder "Vermittlungsstelle" sagt, oder wenn der Schwellenwert **Anzahl der Eingabefehler vor dem Trennen der Verbindung** überschritten wird, wird der Anrufer an die in diesem Textfeld angegebene Telefon- oder Durchwahlnummer weitergeleitet.
        
        Bei der Telefonnummer kann es sich um eine externe Telefonnummer oder eine interne Durchwahl handeln. Wenn die Durchwahl zum Empfang oder zur Vermittlungsstelle 81964 lautet und Ihre Organisation nur einen Satz mit Wähleinstellungen verwendet, geben Sie 81964 ein.
        
        Diese Einstellung enthält standardmäßig keinen Wert. Wenn Sie in dieses Feld keine Nummer eingeben, können keine Anrufe an die Vermittlungsstelle umgeleitet werden, und der Anruf wird auf höfliche Weise beendet, da niemand den Anruf entgegennehmen kann.
        
        Es wird empfohlen, in diesem Feld eine Telefonnummer einzugeben, die Anrufer an eine Vermittlung weiterleitet, wenn der entsprechende Benutzer im Verzeichnis nicht erreichbar ist.
    
      - **Anzahl der Anmeldefehler vor dem Trennen der Verbindung**   Geben Sie in dieses Textfeld die zulässige Anzahl von nacheinander erfolglosen Anmeldeversuchen ein, bevor die Verbindung beendet wird.
        
        Der Wertbereich dieser Einstellung ist 1 bis 20. Bei einem zu niedrigen Wert reagieren Benutzer unter Umständen verärgert. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung von drei Versuchen festgelegt werden.
    
      - **Timeouts und Wiederholungsversuche**   Diese Einstellungen gelten nur für Outlook Voice Access-Benutzer und externe Anrufer, die über eine automatische UM-Telefonzentrale anrufen.
        
          - **Maximale Anrufdauer (Minuten)**   Geben Sie in dieses Textfeld die Anzahl von Minuten ein, für die bei einem eingehenden Anruf die Verbindung mit dem System ohne Umleitung auf eine zulässige Durchwahl erhalten bleibt, bevor der Anruf abgebrochen wird. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung von 30 Minuten festgelegt werden.
            
            Diese Einstellung gilt für alle Arten von Anrufen. Dazu zählen eingehende Outlook Voice Access-Anrufe, interne Sprachanrufe innerhalb der Organisation sowie Sprachanrufe und eingehende Faxanrufe von außerhalb der Organisation.
            
            Der Wertebereich dieser Einstellung ist 10 bis 120. Wenn Sie diesen Wert zu niedrig ansetzen, werden eingehende Anrufe möglicherweise vor ihrem Abschluss unterbrochen. Wenn Ihre Organisation beispielsweise lange Faxnachrichten erhält, sollten Sie diesen Wert höher als den Standardwert festlegen, damit alle Seiten der Faxnachricht empfangen werden.
        
          - **Maximale Aufzeichnungsdauer (Minuten)**   Geben Sie in dieses Textfeld die maximale Anzahl von Minuten ein, die pro Sprachaufzeichnung zulässig sind, wenn ein Anrufer eine Sprachnachricht hinterlässt. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung von 20 Minuten festgelegt werden.
            
            Der Wertebereich dieser Einstellung ist 1 bis 100. Wenn Sie diesen Wert zu niedrig ansetzen, werden lange Sprachnachrichten möglicherweise vor ihrem Abschluss unterbrochen. Wird dieser Wert zu hoch eingestellt, können Benutzer übermäßig lange Sprachnachrichten im Posteingang speichern.
            
            Diese Einstellung ist wichtig, wenn Sie strikte Datenträgerkontingente für Benutzer eingerichtet haben. Dieser Wert muss unter dem der Einstellung **Maximale Anrufdauer (Minuten)** liegen.
        
          - **Aufzeichnungsleerlauf-Zeitüberschreitung (Sekunden)**   Geben Sie in dieses Textfeld die Anzahl von Sekunden ein, in denen beim Aufzeichnen einer Sprachnachricht geschwiegen werden darf, bevor das Telefonat beendet wird. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung von 5 Sekunden festgelegt werden.
            
            Der Wertebereich dieser Einstellung ist 2 bis 10. Wenn Sie diesen Wert zu niedrig ansetzen, trennt das System möglicherweise die Verbindung, bevor die Sprachnachricht vollständig ist. Bei einer zu hohen Einstellung dieses Werts können Sprachnachrichten zu lange Pausen enthalten.
        
          - **Anzahl der Eingabefehler vor dem Trennen der Verbindung**   Geben Sie in dieses Textfeld ein, wie oft ein Anrufer eine falsche Menüoption eingeben darf, bevor die Verbindung getrennt wird. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung von drei Versuchen festgelegt werden. Dies ist eine wichtige Einstellung für sprachaktivierte UM-Wähleinstellungen.
            
            Ein Eingabefehler entsteht beispielsweise, wenn ein Anrufer eine nicht im System gefundenen Durchwahl anfordert, das System die Durchwahl des Benutzers zum Weiterleiten des Anrufs nicht erreichen kann oder der Anrufer eine nicht zulässige Menüoption drückt.
            
            Der Wertebereich dieser Einstellung ist 1 bis 20. Bei einem zu niedrigen Wert wird die Verbindung des Anrufers möglicherweise vorzeitig getrennt.
    
      - **Audiosprache**   Mithilfe dieser Liste können Sie die von Outlook Voice Access-Benutzern zu verwendende Standardsprache festlegen. Diese Einstellung gilt nicht für die Spracheinstellung einer automatischen UM-Telefonzentrale. Sie können für Outlook Voice Access dieselbe oder eine andere Sprache wie für eine automatisch UM-Zentrale festlegen. Wenn ein Benutzer einen Benutzer anruft, der einem bestimmten Wählplan zugeordnet ist, ist die Audiosprache die Standardsprache, die bei Sprachaufzeichnungen der Vermittlungsstelle verwendet wird. Die Systemansagen, die ein Anrufer hört, werden in der gleichen Sprache wiedergegeben. Die in dem UM-Wählplan gewählte Sprache dient zum Vorlesen von E-Mails, Voicemails und Kalenderelementen, Sagen des Namens des Benutzers, wenn eine persönliche Begrüßungsnachricht nicht aufgezeichnet wurde, Transkribieren einer Sprachnachricht mithilfe des Voicemailvorschau-Features und Aktivieren des ordnungsgemäßen Betriebs der automatischen Spracherkennung.
        
        Wenn bei lokalen Bereitstellungen weitere Sprachen hinzugefügt werden, kann Outlook Voice Access eine andere Sprache anstelle von Englisch (USA) verwenden. Wenn ein Outlook Voice Access-Benutzer beispielsweise über eine Outlook Voice Access-Nummer von einem Tischtelefon aus anruft, wird eine vorab aufgezeichnete Ansage der Vermittlungsstelle in englischer Sprache abgespielt. Selbst wenn derselbe Benutzer eine andere Sprache (z. B. Französisch) in Outlook Web App auswählt, erfolgen die Menüansagen weiterhin auf Englisch (USA). Damit der Benutzer die aufgezeichneten Menüs in französischer Sprache abrufen kann, müssen Sie das entsprechende Sprachpaket installieren.
        

        > [!NOTE]
        > Für Exchange Online sind alle Sprachen verfügbar.



8.  **Wählregeln**   Geben Sie auf dieser Seite Wählregeln für nationale und internationale Anrufe an, die von UM-aktivierten Benutzern getätigt werden. Jeder Eintrag, der in den Wählregeln definiert ist, bestimmt den Typ der Anrufe, die Benutzer innerhalb einer bestimmten Wählregelgruppe tätigen können. Nachdem Sie Wählregeln auf der Seite **Wählregeln** konfiguriert haben, müssen Sie den UM-Wählplan, eine UM-Postfachrichtlinie oder eine automatische UM-Telefonzentrale so konfigurieren, dass die entsprechende Wählregel verwendet wird. Nachdem Sie die UM-Postfachrichtlinie für die Verwendung einer Wählregelgruppe konfiguriert haben, gelten die konfigurierten Wähleinschränkungen für alle UM-aktivierten Benutzer, die der UM-Postfachrichtlinie zugeordnet sind. Sie können z. B. eine Wählregelgruppe konfigurieren, bei der den Wähleinstellungen zugeordnete Benutzer keinen Zugangscode für die Amtsleitung wählen müssen, wenn sie eine nationale Telefonnummer anrufen möchten. Sie können Folgendes konfigurieren:
    
      - **Nationale Wählregeln**   In diesem Feld können Sie die in den UM-Postfachrichtlinien verwendeten nationalen Wählregelgruppen hinzufügen, löschen oder bearbeiten. Klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Wählregel zu erstellen. Klicken Sie auf ![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um eine vorhandene Wählregel zu bearbeiten. Klicken Sie auf ![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um eine Wählregel zu entfernen. Wenn Sie eine Wählregel erstellen, müssen Sie auf der Seite **Neue Wählregel** die folgenden Informationen angeben:
        
          - **Name der Wählregel**   Verwenden Sie dieses Textfeld, um den Namen der Wählregel einzugeben, die Sie gerade erstellen. Sie können den gleichen Namen verwenden, um mehrere Regeln in einer Gruppe zusammenzufassen, und diese dann unter **Wählautorisierung** aktivieren oder deaktivieren. Der Name darf bis zu 32 Zeichen umfassen.
        
          - **Nummernmuster für Transformation (Nummernmaske)**   Verwenden Sie dieses Textfeld, um das Nummernmuster einzugeben, das vor dem Wählvorgang transformiert werden soll, z. B. 91425xxxxxxx. Wenn ein Benutzer eine Nummer eingibt, die diesem Muster entspricht, transformiert UM die gewählte Nummer in eine gewählte Nummer, bevor der Anruf durchgeführt wird. Sie können nur Zahlen und das Platzhalterzeichen "x" eingeben.
        
          - **Gewählte Nummer**   Geben Sie in dieses Textfeld die Nummer ein, die gewählt werden soll und dem Nummernmuster entspricht, das Sie in **Nummernmuster für Transformation (Nummernmaske)** festgelegt haben. Mithilfe der gewählten Nummer kann die tatsächliche Wählzeichenfolge bestimmt werden, die an das VoIP-Gateway oder die IP-Nebenstelle gesendet wird. Diese Nummer kann sich von der Nummer unterscheiden, die durch Unified Messaging für den ausgehenden Anruf ermittelt wurde. Die Nebenstellenanlage oder IP-Nebenstellenanlage kann jedoch auch für das Auslassen der Vorwahl für Ortsgespräche und für private Sprachnummernpläne konfiguriert werden. Platzhalterzeichen (*x*) in der Wählzeichenfolge werden durch die Ziffern der ursprünglichen Nummer ersetzt, die der Nummernmaske der Wählregel entsprachen. Ein Beispiel für eine gültige gewählte Nummer ist 9*xxxxxxx*. Dieses Feld kann nur Zahlen und das Zeichen *x* enthalten.
        
          - **Kommentar**   Verwenden Sie dieses Textfeld, um einen Kommentar oder eine Beschreibung für die Wählregel einzugeben, die Sie hinzufügen oder ändern. Dieses Textfeld enthält standardmäßig keinen Wert.
            

            > [!NOTE]
            > Wenn Sie eine Integration mit Office Communications Server&nbsp;2007&nbsp;R2 oder Microsoft Lync Server durchführen, ist es möglicherweise nicht notwendig, Wählregeln oder Wählregelgruppen in Unified Messaging zu konfigurieren. Office Communications Server 2007 R2 und Lync Server sind so konzipiert, dass sie Anrufweiterleitung und Nummernübersetzung für Benutzer in Ihrer Organisation ausführen, und übernehmen diese Aufgaben auch, wenn Anrufe im Namen von Benutzern getätigt werden.

    
      - **Internationale Regeln**   In diesem Textfeld können Sie die von den UM-Postfachrichtlinien verwendeten internationalen Wählregelgruppen hinzufügen, löschen oder bearbeiten.
        
          - **Name der Wählregel**   Verwenden Sie dieses Textfeld, um den Namen der Wählregel einzugeben, die Sie gerade erstellen. Sie können den gleichen Namen verwenden, um mehrere Regeln in einer Gruppe zusammenzufassen, und diese dann unter **Wählautorisierung** aktivieren oder deaktivieren. Der Name darf bis zu 32 Zeichen umfassen.
        
          - **Nummernmuster für Transformation (Nummernmaske)**   Verwenden Sie dieses Textfeld, um das Nummernmuster einzugeben, das vor dem Wählvorgang transformiert werden soll, z. B. 91425xxxxxxx. Wenn ein Benutzer eine Nummer eingibt, die diesem Muster entspricht, transformiert UM die gewählte Nummer in eine gewählte Nummer, bevor der Anruf durchgeführt wird. Sie können nur Zahlen und das Platzhalterzeichen "x" eingeben.
        
          - **Gewählte Nummer**   Geben Sie in dieses Textfeld die Nummer ein, die gewählt werden soll und dem Nummernmuster entspricht, das Sie in **Nummernmuster für Transformation (Nummernmaske)** festgelegt haben. Mithilfe der gewählten Nummer kann die tatsächliche Wählzeichenfolge bestimmt werden, die an das VoIP-Gateway oder die IP-Nebenstelle gesendet wird. Diese Nummer kann sich von der Nummer unterscheiden, die durch Unified Messaging für den ausgehenden Anruf ermittelt wurde. Die Nebenstellenanlage oder IP-Nebenstellenanlage kann jedoch auch für das Auslassen der Vorwahl für Ortsgespräche und für private Sprachnummernpläne konfiguriert werden. Platzhalterzeichen (*x*) in der Wählzeichenfolge werden durch die Ziffern der ursprünglichen Nummer ersetzt, die der Nummernmaske der Wählregel entsprachen. Ein Beispiel für eine gültige gewählte Nummer ist 9*xxxxxxx*. Dieses Feld kann nur Zahlen und das Zeichen *x* enthalten.
        
          - **Kommentar**   Verwenden Sie dieses Textfeld, um einen Kommentar oder eine Beschreibung für die Wählregel einzugeben, die Sie hinzufügen oder ändern. Dieses Textfeld enthält standardmäßig keinen Wert.
            

            > [!NOTE]
            > Wenn Sie bei lokalen Bereitstellungen eine Integration mit Office Communications Server&nbsp;2007&nbsp;R2 oder Microsoft Lync Server durchführen, ist es möglicherweise nicht notwendig, Wählregeln oder Wählregelgruppen in Unified Messaging zu konfigurieren. Office Communications Server 2007 R2 und Lync Server sind so konzipiert, dass sie Anrufweiterleitung und Nummernübersetzung für Benutzer in Ihrer Organisation ausführen, und übernehmen diese Aufgaben auch, wenn Anrufe im Namen von Benutzern getätigt werden.



9.  **Wählautorisierung**   Wählen Sie auf dieser Seite die Wählregeln für Anrufer aus, die über eine Outlook Voice Access-Nummer anrufen, die in einem UM-Wählplan konfiguriert ist. Durch Konfigurieren von Wählregelgruppen und Wähleinschränkungen können Sie den Typ von Anrufen einschränken, die von Anrufern getätigt werden, wenn ein nicht authentifizierter Benutzer oder ein Outlook Voice Access-Benutzer über eine Outlook Voice Access-Nummer anruft, die in einem Wählplan konfiguriert ist. Sie können Folgendes konfigurieren:
    
      - **Anrufe im gleichen UM-Wählplan zulassen**   Aktivieren Sie dieses Kontrollkästchen, damit Benutzer, die über eine Outlook Voice Access-Nummer anrufen, die in einem Wählplan konfiguriert ist, Anrufe an eine Durchwahlnummer senden oder weiterleiten können, die einem UM-aktivierten Benutzer im gleichen Wählplan zugeordnet ist. Diese Einstellung ist standardmäßig aktiviert.
        
        Wenn Sie diese Einstellung deaktivieren, sind Benutzer, die über die Outlook Voice Access-Nummer anrufen, nicht in der Lage, Anrufe an Benutzer ohne UM-Aktivierung, an andere Durchwahlnummern oder an UM-aktivierte Benutzer zu senden oder weiterzuleiten, die demselben Wählplan zugeordnet sind. Der Grund dafür ist, dass die Einstellung **Anrufe an jede Durchwahl zulassen** standardmäßig deaktiviert ist.
    
      - **Anrufe an jede Durchwahl zulassen**   Wenn diese Einstellung deaktiviert ist, können Benutzer, die über eine im Wählplan definierte Outlook Voice Access-Nummer anrufen, keine Anrufe mit Benutzern ohne UM-Aktivierung oder mit anderen Durchwahlnummern führen, die keinem UM-aktivierten Benutzer zugeordnet sind. Sie können jedoch Durchwahlnummern anrufen, die UM-aktivierten Benutzern zugeordnet sind, bzw. Gespräche an diese weiterleiten. Der Grund dafür ist, dass die Einstellung **Anrufe im gleichen UM-Wählplan** standardmäßig aktiviert ist. Die Einstellung **Anrufe an jede Durchwahl zulassen** ist standardmäßig deaktiviert.
        
        Wenn diese Einstellung aktiviert ist, können Benutzer, die über eine im Wählplan konfigurierte Outlook Voice Access-Nummer anrufen, Anrufe mit Benutzern ohne UM-Aktivierung, mit anderen Durchwahlnummern, die keinem UM-aktivierten Benutzer zugeordnet sind, und mit UM-aktivierten Benutzern führen. Der Grund dafür ist, dass die Einstellung **Anrufe im gleichen UM-Wählplan** standardmäßig aktiviert ist.
        
        Diese Einstellung kann in einer Umgebung aktiviert werden, in der nicht alle Benutzer UM-aktiviert sind. Sie ist außerdem nützlich, wenn Sie zulassen möchten, dass Benutzer, die über eine Outlook Voice Access-Nummer anrufen, die in einem Wählplan konfiguriert ist, Durchwahlnummern anrufen können, die nicht zugeordnet sind.
    
      - **Autorisierte nationale Wählregelgruppen**   Verwenden Sie diesen Abschnitt, um zulässige nationale Wählregeln hinzuzufügen oder zu entfernen. Standardmäßig sind keine nationalen Wählregeln in UM-Wählplänen konfiguriert.
        
        Mithilfe von nationalen/regionsinternen Wählregelgruppen kann der Zugriff auf Telefonnummern in einem Land oder einer Region zugelassen oder eingeschränkt werden, die ein Benutzer, der die Teilnehmerzugriffsnummer gewählt hat, wählen kann. Diese Maßnahme hilft, unnötige bzw. nicht autorisierte Telefonate und Gebühren zu vermeiden.
        
        Damit Sie nationale Wählregeln hinzufügen können, müssen Sie zuerst die entsprechende nationale Wählregel im Wählplan erstellen und dann der Wählregel die entsprechenden Wählregeleinträge hinzufügen. Nachdem Sie die erforderlichen Wählregeln im Wählplan erstellt haben, müssen Sie die Wählregeln im Wählplan auf der Registerkarte **Wählautorisierungen** der Liste der Wählautorisierungen hinzufügen.
        
        Nationale/regionsinterne Wählregelgruppen können verwendet werden, um den Zugriff auf Rufnummern in einem Land oder einer Region zuzulassen oder einzuschränken. Dies gilt für alle Benutzer, die bei einer Outlook Voice Access-Nummer angerufen haben.
    
      - **Autorisierte internationale Wählregelgruppen**   Verwenden Sie diesen Abschnitt, um zulässige internationale Wählregeln hinzuzufügen oder zu entfernen. Standardmäßig sind keine internationalen Wählregeln in UM-Wählplänen konfiguriert.
        
        Mithilfe von internationalen Wählregeln können die internationalen Telefonnummern zugelassen oder eingeschränkt werden, die ein Benutzer wählen kann, der sich über die Outlook Voice Access-Nummer eingewählt hat. Diese Maßnahme hilft, unnötige bzw. nicht autorisierte Telefonate und Gebühren zu vermeiden.
        
        Damit Sie internationale Wählregelgruppen hinzufügen können, müssen Sie zuerst die entsprechenden internationalen Wählregeln im Wählplan erstellen und dann die entsprechenden Wählregeleinträge hinzufügen. Nachdem Sie die erforderlichen Wählregeln im Wählplan erstellt haben, müssen Sie die Wählregeln im Wählplan auf der Registerkarte **Wählautorisierungen** der Liste der Wählautorisierungen hinzufügen.
        
        Internationale Wählregelgruppen können verwendet werden, um den Zugriff auf Rufnummern außerhalb eines Lands oder einer Region zuzulassen oder einzuschränken. Dies gilt für alle Benutzer, die bei einer Outlook Voice Access-Nummer angerufen haben.

10. **Weiterleitung und Suche**   Auf dieser Seite können Sie die Features des UM-Wählplans konfigurieren. Für UM-Wähleinstellungen können zahlreiche Funktionen konfiguriert werden. Dazu gehören Weiterleiten von Anrufen, Senden von Sprachnachrichten und Suchen nach Benutzern. Sie können Folgendes konfigurieren:
    
      - **Ermöglicht Anrufern Folgendes**   Mit diesen Einstellungen können Sie festlegen, wie Benutzer, die sich über eine Outlook Voice Access-Nummer einwählen, Kontakt mit anderen Benutzern herstellen können. Sie können Folgendes konfigurieren:
        
          - **Weiterleiten an Benutzer**   Aktivieren Sie dieses Kontrollkästchen, um Outlook Voice Access-Benutzern die Weiterleitung von Anrufen an Benutzer zu gestatten. Diese Option ist standardmäßig aktiviert. Dadurch können den Wähleinstellungen zugeordnete Benutzer Anrufe an Benutzer derselben UM-Wähleinstellungen vermitteln. Nachdem Sie dieses Kontrollkästchen aktiviert haben, können Sie die Gruppe von Benutzern festlegen, nach denen Anrufer suchen können, indem Sie auf dieser Seite die geeignete Option unter **Anrufern die Benutzersuche nach Name oder Alias erlauben** auswählen.
            
            Wenn Sie diese Option deaktivieren, lässt Outlook Voice Access für keinen Benutzer zu, dass er an einen anderen Benutzer im Wählplan weitergeleitet wird.
        
          - **Sprachnachrichten ohne Klingeln des Telefons des Benutzers hinterlassen**   Aktivieren Sie dieses Kontrollkästchen, um Anrufern das Senden von Sprachnachrichten an Benutzer zu gestatten. Diese Option ist standardmäßig aktiviert. Dadurch können dem Wählplan zugeordnete Outlook Voice Access-Benutzer Sprachnachrichten an Benutzer im gleichen UM-Wählplan senden. Nachdem Sie dieses Kontrollkästchen aktiviert haben, können Sie die Gruppe von Benutzern festlegen, nach denen Anrufer suchen können, indem Sie auf dieser Seite die geeignete Option unter **Anrufern die Benutzersuche nach Name oder Alias erlauben** auswählen.
            
            Wenn Sie diese Option deaktivieren, gibt Outlook Voice Access Anrufern in einer Systemansage nicht die Möglichkeit, eine Sprachnachricht zu senden.
    
      - **Anrufer dürfen Benutzer nach Name oder Alias suchen**   Mit dieser Option können Sie eine Gruppierung von Benutzern festlegen, nach denen gesucht werden kann. Standardmäßig ist die Option **Nur in diesem Wählplan** aktiviert. Sie können jedoch die Gruppierung der Benutzer ändern. Wählen Sie aus den folgenden Optionen aus:
        
          - **Nur in diesem Wählplan**   Mithilfe dieser Option können Sie Anrufern, die sich über Outlook Voice Access einwählen, die Suche nach und die Kontaktaufnahme mit Benutzern gestatten, die sich im gleichen Wählplan befinden.
        
          - **In der gesamten Organisation**   Mithilfe dieser Option können Sie Anrufern, die sich über Outlook Voice Access einwählen, die Suche nach und die Kontaktaufnahme mit jeder Person gestatten, die in der gesamten Organisation aufgelistet wird. Hierzu gehören alle Benutzer, die in allen Wählplänen postfach- oder UM-aktivierte Benutzer sind.
        
          - **Nur in dieser automatischen Telefonzentrale**   Mithilfe dieser Liste können Sie Outlook Voice Access-Benutzern gestatten, eine Verbindung mit einer automatischen UM-Telefonzentrale und dann möglicherweise eine Verbindung mit einer anderen automatischen Telefonzentrale herzustellen, die Sie konfiguriert haben. Sie müssen diese automatische Telefonzentrale erstellen, damit Anrufer an eine andere automatische Telefonzentrale, die angegeben ist, vermittelt werden können.
        
          - **Nur für diese Durchwahl**   Mithilfe dieser Option können Sie Outlook Voice Access-Benutzern gestatten, eine Verbindung mit einer Durchwahlnummer herzustellen, die Sie im Feld dieser Option angegeben haben. Dieses Feld akzeptiert nur numerische Eingaben. Die Anzahl der in diesem Feld definierten Ziffern muss der Anzahl von Ziffern entsprechen, die für die Wähleinstellungen konfiguriert sind, die der automatischen Telefonzentrale zugeordnet sind.
    
      - **Informationen, die für Benutzer mit demselben Namen eingeschlossen werden**   Geben Sie in diesem Feld an, wie im Wählplan zwischen Benutzern unterschieden werden soll, die denselben oder ähnliche Namen haben. Wenn ein Anrufer aufgefordert wird, Buchstaben einzugeben oder den Namen einer Person zu sagen, um einen bestimmten Benutzer in der Organisation zu finden, entsprechen mitunter mehrere Namen der Eingabe des Anrufers. Wenn es zwei Benutzer mit demselben Namen gibt, verwendet UM eine der folgenden Methoden, um dem Namen des Benutzers weitere Informationen hinzuzufügen. Wenn Sie beispielsweise **Abteilung** auswählen, hört ein Anrufer, wenn er sich als Outlook Voice Access-Benutzer in Outlook Voice Access einwählt und nach einem Benutzer sucht, für den es doppelte oder ähnliche Namen im Verzeichnis gibt, den Namen und die Abteilung des Benutzers. Beispiel:
        
        1.  System: "Willkommen bei Outlook Web Access. Geben Sie bitte Ihre PIN ein, und drücken Sie die Rautetaste."
        
        2.  Der Anrufer gibt seine PIN ein, und drückt die Rautetaste (\#).
        
        3.  System: "Bitte sagen Sie Sprachnachricht, E-Mail, Kalender, persönliche Kontakte, Verzeichnis oder persönliche Optionen."
        
        4.  Anrufer: "Verzeichnis"
        
        5.  System: "Verzeichnissuche. Für die folgenden Aufgaben müssen Sie die Tastatur Ihres Telefons benutzen, eine Spracheingabe ist nicht möglich. Buchstabieren Sie über die Tastatur entweder den Namen der Person, nach der Sie suchen möchten, dabei zuerst den Nachnamen, oder den ersten Teil der E-Mail-Adresse der Person, und drücken Sie zweimal die Rautetaste. Wenn Sie die Durchwahl kennen, drücken Sie die Rautetaste."
        
        6.  Der Aufrufer gibt über die Telefontastatur "smithtony" ein und drückt die \#-Taste.
        
        7.  System: "Für Tony Smith, Forschung, drücken Sie die 1. Für Tony Smith, Verwaltung, drücken Sie die 2. Für Tony Smith, Technischer Support, drücken Sie die 3."
        
        8.  Der Anrufer drückt die entsprechende Taste auf der Tastatur, und der Anruf wird an den Benutzer weitergeleitet.
        
        Standardmäßig übernehmen alle diesen UM-Wähleinstellungen zugeordneten automatischen UM-Telefonzentralen diese Einstellung. Sie können diese Einstellung für jede automatische UM-Telefonzentrale ändern, die Sie erstellen.
        
        Wählen Sie eine der folgenden Methoden aus, mit deren Hilfe dem Anrufer weitere Informationen bereitgestellt werden, um ihm beim Auffinden des gewünschten Benutzers in der Organisation behilflich zu sein:
        
          - **Keine**   Bei der Auflistung der Entsprechungen werden keine zusätzlichen Information gegeben. Diese Methode ist standardmäßig aktiviert.
        
          - **Titel**   Das Voicemailsystem fügt bei der Auflistung der Entsprechungen den Titel jedes Benutzers hinzu.
        
          - **Abteilung**   Das Voicemailsystem fügt bei der Auflistung der Entsprechungen die Abteilung jedes Benutzers hinzu.
        
          - **Ort**   Das Voicemailsystem fügt bei der Auflistung der Entsprechungen den Standort jedes Benutzers hinzu.
        
          - **Ansage für Alias**   Der Anrufer wird vom Voicemailsystem zur Angabe des Alias des Benutzers aufgefordert.

11. Nachdem Sie die erforderlichen Einstellungen konfiguriert haben, klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Konfigurieren von UM-Wählplaneinstellungen mithilfe der Shell

In diesem Beispiel werden die UM-Wähleinstellungen namens `MyDialPlan` für die Verwendung der Amtskennziffer 9 konfiguriert.

    Set-UMDialplan -Identity MyDialPlan -OutsideLineAccessCode 9

In diesem Beispiel werden die UM-Wähleinstellungen namens `MyDialPlan` für die Verwendung einer Begrüßung konfiguriert.

    Set-UMDialplan -Identity MyDialPlan -WelcomeGreetingEnabled $true -WelcomeGreetingFilename welcome.wav

In diesem Beispiel werden die UM-Wähleinstellungen namens `MyDialPlan` mit Wählregeln konfiguriert.

    $csv=import-csv "C:\MyInCountryGroups.csv"
    Set-UMDialPlan -Identity MyDialPlan -ConfiguredInCountryGroups $csv
    Set-UMDialPlan -Identity MyDialPlan -AllowedInCountryGroups "local, long distance"

## Anzeigen von UM-Wählplaneinstellungen mithilfe der Shell

In diesem Beispiel wird eine Liste aller UM-Wählpläne angezeigt.

    Get-UMDialplan

In diesem Beispiel wird eine formatierte Liste mit allen Einstellungen eines UM-Wählplans namens `MyUMDialPlan` angezeigt.

    Get-UMDialplan -Identity MyUMDialPlan | Format-List


---
title: 'Installieren eines Sprachpakets: Exchange 2013 Help'
TOCTitle: Installieren eines Sprachpakets
ms:assetid: ed14ffa5-c9b0-4367-b5da-564024b360ff
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876951(v=EXCHG.150)
ms:contentKeyID: 50477024
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Installieren eines Sprachpakets

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Wenn Sie eine Sprache in der Liste der verfügbaren Unified Messaging-Sprachen für einen UM-Wählplan oder eine UM-Telefonzentrale verfügbar machen möchten, müssen Sie zunächst das geeignete UM-Sprachpaket installieren. Sie installieren das Sprachpaket mithilfe der sprachspezifischen, selbstextrahierenden Datei oder über den Befehl **setup.exe /AddUmLanguagePack** auf einem Postfachserver mit aktivem Microsoft Exchange Unified Messaging-Dienst. Bevor Sie ein UM-Sprachpaket installieren können, müssen Sie es zunächst in einen lokalen Ordner auf dem Postfachserver herunterladen. Sie können UM-Sprachpakete auf der Seite [Exchange Server 2013 UM Language Packs – Deutsch](https://go.microsoft.com/fwlink/p/?linkid=266542) herunterladen. Es gibt für jede Sprache eine eigene ausführbare Datei.

Nachdem Sie das geeignete UM-Sprachpaket installiert haben, können Sie die Liste der installierten UM-Sprachpakete anzeigen, indem Sie die Dropdownliste auf der Seite **Einstellungen** eines UM-Wählplans oder die Dropdownliste **Sprache für automatisierte Sprachschnittstelle** auf der Seite **Allgemein** einer UM-Telefonzentrale anzeigen. Sie können außerdem die Standardsprache für UM-Wählpläne und automatische Telefonzentralen auf eine andere Sprache als Englisch (en-US) festlegen.


> [!WARNING]
> Die UM-Sprachpakete für Microsoft Exchange Server&nbsp;2007 oder Exchange 2007 Service Pack&nbsp;1&nbsp;(SP1), SP2 oder SP3 oder Exchange 2010 Service Pack&nbsp;1&nbsp;SP1, SP2 oder SP3 können nicht auf einem Exchange 2013-Postfachserver verwendet werden.



Weitere Informationen zu Aufgaben im Zusammenhang mit UM-Sprachen finden Sie unter [UM-Sprachen, -Telefonansagen und -Begrüßungen – Verfahren](um-languages-prompts-and-greetings-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachserver (UM-Dienst)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Überprüfen Sie, ob der Postfachserver auf einem anderen Computer als der Clientzugriffsserver installiert ist oder sich die Clientzugriffs- und Postfachserver auf derselben Hardware befinden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Installieren eines UM-Sprachpakets mithilfe der Installationsdatei (.exe) für das UM-Sprachpaket

1.  Laden Sie die sprachspezifische UM-Sprachpaketdatei (.exe) aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=266542) in einen lokalen Ordner auf dem Postfachserver herunter.

2.  Doppelklicken Sie auf die Datei "UMLanguagePack.*\<CultureCode\>.exe*". Um beispielsweise das deutsche UM-Sprachpaket herunterzuladen, laden Sie die Datei "UMLanguagePack.de-DE.exe" herunter.

3.  
    
    Lesen Sie im Exchange 2013 Setup-Assistenten auf der Seite **Lizenzvertrag** die Bedingungen des Lizenzvertrags, aktivieren Sie das Kontrollkästchen **Ich stimme den Bedingungen des Lizenzvertrags zu**, und klicken Sie auf **Weiter**.

4.  
    
    Stellen Sie auf der Seite **Unified Messaging-Sprachpaket** sicher, dass im Fenster **Die folgenden Unified Messaging-Sprachpakete werden installiert** die richtige Sprache aufgelistet ist, und klicken Sie anschließend auf **Installieren**.

5.  Klicken Sie auf **Fertig stellen**, um die Installation des UM-Sprachpakets abzuschließen.

## Installieren eines UM-Sprachpakets mithilfe von "Setup.exe"

In diesem Beispiel wird das japanische (ja-JP) UM-Sprachpaket installiert, das in den Ordner "D:\\Exchange\\UMLanguagePacks" auf einem Postfachserver heruntergeladen wurde.

    setup.exe /AddUmLanguagePack:ja-JP /s:d:\Exchange\UMLanguagePacks /IAcceptExchangeServerLicenseTerms

In diesem Beispiel werden die UM-Sprachpakete für Spanisch (Mexiko) (es-MX) und Deutsch (de-DE) installiert, die in den Ordner "D:\\Exchange\\UMLanguagePacks" auf einem Postfachserver heruntergeladen wurden.

    setup.exe /AddUmLanguagePack:es-MX,de-DE /s:d:\Exchange\UMLanguagePacks /IAcceptExchangeServerLicenseTerms


> [!WARNING]
> Wenn Sie nicht den Parameter "/IAcceptExchangeServerLicenseTerms" verwenden, wird folgende Fehlermeldung angezeigt: Willkommen bei der unbeaufsichtigten Installation von Microsoft Exchange Server 2013. Für die Installation von Microsoft Exchange Server 2013 müssen Sie dem Lizenzvertrag zustimmen. Den Lizenzvertrag finden Sie unter http://go.microsoft.com/fwlink/p/?LinkId=150127. Fügen Sie den Parameter "/IAcceptExchangeServerLicenseTerms" zum ausgeführten Befehl hinzu, um den Lizenzvertrag zu akzeptieren. Führen Sie für weitere Informationen "setup /?" aus.



Weitere Informationen zu verfügbaren UM-Sprachen und den Kulturcodes finden Sie unter [UM-Sprachen, -Telefonansagen und -Begrüßungen](um-languages-prompts-and-greetings-exchange-2013-help.md).


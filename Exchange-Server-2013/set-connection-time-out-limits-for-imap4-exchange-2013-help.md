---
title: 'Festlegen von Verbindungstimeout-Einschränkungen für IMAP4: Exchange 2013 Help'
TOCTitle: Festlegen von Verbindungstimeout-Einschränkungen für IMAP4
ms:assetid: 6b6a5bd1-a878-4a70-8e21-14d5042a58f1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998665(v=EXCHG.150)
ms:contentKeyID: 50554842
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Festlegen von Verbindungstimeout-Einschränkungen für IMAP4

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-11-28_

Mithilfe der Exchange-Verwaltungskonsole oder der Shell können Sie Grenzwerte für Verbindungstimeouts für inaktive authentifizierte oder nicht authentifizierte IMAP4-Verbindungen konfigurieren.

Weitere Informationen zu IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "IMAP4-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Festlegen von Grenzwerten für Verbindungstimeouts für IMAP4 mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** **\>** **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie anschließend auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **IMAP4**.

4.  Führen Sie einen Bildlauf nach unten durch, und klicken Sie auf **Weitere Optionen**.

5.  Verwenden Sie unter **Timeouteinstellungen** die folgenden Einstellungen:
    
      - **Authentifizierter Timeout (Sekunden)**   Gibt die Wartezeit an, nach der eine im Leerlauf befindliche authentifizierte Verbindung geschlossen wird. Der Standardwert ist 1.800. Der Bereich möglicher Werte ist 30 bis 86.400.
    
      - **Nicht authentifizierter Timeout (Sekunden)**   Gibt die Wartezeit an, nach der eine im Leerlauf befindliche nicht authentifizierte Verbindung geschlossen wird. Der Standardwert ist 60. Der Bereich möglicher Werte ist 30 bis 3.600.

6.  Klicken Sie auf **Übernehmen** und dann auf **OK**, um die Änderung zu speichern.

Nachdem Sie die Grenzwerte für Verbindungstimeouts für IMAP4 eingerichtet haben, müssen Sie die IMAP4-Dienste neu starten, damit die Einstellungen wirksam werden. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

## Verwenden der Shell zum Festlegen der Grenzwerte für Verbindungstimeouts für IMAP4

In diesem Beispiel wird der Grenzwert für Verbindungstimeouts für inaktive authentifizierte Verbindungen festgelegt.

    Set -ImapSettings -Identity CAS01 -AuthenticatedConnectionTimeout TimeValue

In diesem Beispiel wird der Grenzwert für Verbindungstimeouts für inaktive nicht authentifizierte Verbindungen festgelegt.

    Set -ImapSettings -Identity CAS01 -PreAuthenticatedConnectionTimeout TimeValue

Nachdem Sie die Grenzwerte für Verbindungstimeouts für IMAP4 eingerichtet haben, müssen Sie die IMAP4-Dienste neu starten, damit die Einstellungen wirksam werden. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um das erfolgreiche Einstellen der Grenzwerte für Verbindungstimeouts zu überprüfen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** **\>** **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie anschließend auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **IMAP4**.

4.  Führen Sie einen Bildlauf nach unten durch, und klicken Sie auf **Weitere Optionen**.

5.  Überprüfen Sie unter **Timeouteinstellungen**, ob die Verbindungseinstellungen richtig sind.

– oder –

1.  Führen Sie folgenden Befehl in der Shell aus.
    
        Get-ImapSettings | format-list

2.  Überprüfen Sie, ob die Verbindungseinstellungen richtig sind.

## Weitere Informationen

Nachdem Sie die Grenzwerte für Verbindungstimeouts für IMAP4 festgelegt haben, können Sie die folgenden Aufgaben ausführen:

[Aktivieren von IMAP4 in Exchange 2016](enable-imap4-in-exchange-2013-exchange-2013-help.md)

[Festlegen von Verbindungslimits für IMAP4](set-connection-limits-for-imap4-exchange-2013-help.md)


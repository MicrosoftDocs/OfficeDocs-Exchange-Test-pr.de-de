---
title: 'Festlegen von Verbindungslimits für IMAP4: Exchange 2013 Help'
TOCTitle: Festlegen von Verbindungslimits für IMAP4
ms:assetid: 8e3aa366-e77c-4c70-b78d-ddbb178cb521
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123712(v=EXCHG.150)
ms:contentKeyID: 50554856
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Festlegen von Verbindungslimits für IMAP4

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-28_

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell für ein Benutzerpostfach IMAP4-Verbindungslimits für Ihre Organisation festlegen.

Beim Angeben von Verbindungslimits für IMAP4 können Sie Verbindungslimits für den Server, eine IP-Adresse oder einen bestimmten Benutzer auswählen.

Weitere Informationen zu IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "IMAP4-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Festlegen von IMAP4-Verbindungslimits für einen Server, eine IP-Adresse oder einen Benutzer

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** **\>** **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **IMAP4**.

4.  Klicken Sie nach einem Bildlauf nach unten auf **Weitere Optionen**.

5.  Geben Sie unter **Verbindungslimits** Folgendes an:
    
      - **Maximale Anzahl von Verbindungen**   Gibt die Gesamtanzahl an Verbindungen an, die der angegebene Server akzeptiert. Dazu gehören authentifizierte und nicht authentifizierte Verbindungen. Der Standardwert ist 2.147.483.647. Der Bereich möglicher Werte ist 1 bis 2.147.483.647.
    
      - **Maximale Anzahl von Verbindungen von einer einzelnen IP-Adresse**   Dient zum Angeben der Anzahl von Verbindungen, die der Server von einer einzelnen IP-Adresse akzeptiert. Der Standardwert ist 2.147.483.647. Der Bereich möglicher Werte ist 1 bis 2.147.483.647.
    
      - **Maximale Anzahl von Verbindungen von einem einzelnen Benutzer**   Dient zum Angeben der maximalen Anzahl von Verbindungen, die der Server von einem bestimmten Benutzer akzeptiert. Der Standardwert ist 16. Der Bereich möglicher Werte ist 1 bis 2.147.483.647.
    
      - **Maximale Befehlsgröße (Bytes)**   Dient zum Angeben der maximalen Größe eines einzelnen Befehls. Die Standardgröße ist 10.240. Der Bereich möglicher Werte ist 1.024 bis 16.384.

6.  Klicken Sie auf **Übernehmen** und dann auf **OK**, um die Änderung zu speichern.

Nachdem Sie Verbindungslimits festgelegt haben, müssen Sie die IMAP4-Dienste neu starten. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

## Verwenden der Shell zum Festlegen von IMAP4-Verbindungslimits für einen Server, eine IP-Adresse oder einen Benutzer

In diesem Beispiel wird das Verbindungslimit für einen Server festgelegt.

    Set-ImapSettings -Identity CAS01 -MaxConnections Value

In diesem Beispiel wird das Verbindungslimit für eine IP-Adresse festgelegt.

    Set-ImapSettings -Identity CAS01 -MaxConnectionsFromSingleIP Value

In diesem Beispiel wird das Verbindungslimit für einen Benutzer festgelegt.

    Set-ImapSettings -MaxConnectionsPerUser Value

In diesem Beispiel wird die maximale Befehlsgröße festgelegt.

    Set-ImapSettings -MaxCommandSize Value

Nachdem Sie Verbindungslimits festgelegt haben, müssen Sie die IMAP4-Dienste neu starten. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Festlegung von Verbindungslimits zu überprüfen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** **\>** **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **IMAP4**.

4.  Klicken Sie nach einem Bildlauf nach unten auf **Weitere Optionen**.

5.  Überprüfen Sie unter **Verbindungslimits**, ob die Verbindungseinstellungen ordnungsgemäß sind.

– oder –

1.  Führen Sie folgenden Befehl in der Shell aus.
    
        Get-ImapSettings | format-list

2.  Prüfen Sie, ob die Verbindungslimits ordnungsgemäß sind.

## Weitere Informationen

Nachdem Sie die IMAP4-Verbindungslimits für einen Server, eine IP-Adresse oder einen Benutzer festgelegt haben, können Sie die folgenden Aufgaben ausführen:

[Aktivieren von IMAP4 in Exchange 2016](enable-imap4-in-exchange-2013-exchange-2013-help.md)

[Festlegen von Verbindungstimeout-Einschränkungen für IMAP4](set-connection-time-out-limits-for-imap4-exchange-2013-help.md)


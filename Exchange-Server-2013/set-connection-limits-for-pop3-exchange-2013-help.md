---
title: 'Festlegen von Verbindungslimits für POP3: Exchange 2013 Help'
TOCTitle: Festlegen von Verbindungslimits für POP3
ms:assetid: 512d61c2-2a34-4813-92a9-875339d3388b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997988(v=EXCHG.150)
ms:contentKeyID: 50554818
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Festlegen von Verbindungslimits für POP3

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-28_

Sie können die Exchange-Verwaltungskonsole oder die Shell zum Verwalten von POP3-Verbindungslimits für Ihre Organisation verwenden.

Beim Angeben von Verbindungslimits für POP3 können Sie Verbindungslimits für den Server, für eine IP-Adresse oder für einen bestimmten Benutzer auswählen.

Weitere Informationen zu POP3 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "POP3-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Festlegen von POP3-Verbindungslimits für einen Server, eine IP-Adresse oder einen Benutzer

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** **\>** **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **POP3**.

4.  Führen Sie einen Bildlauf nach unten durch, und klicken Sie auf **Weitere Optionen**.

5.  Legen Sie unter **Verbindungslimits** die folgenden Einstellungen fest:
    
      - **Maximale Anzahl von Verbindungen**   Gibt die Gesamtanzahl von Verbindungen an, die der angegebene Server akzeptiert. Dies umfasst authentifizierte und nicht authentifizierte Verbindungen. Der Standardwert ist 2.147.483.647. Der Bereich möglicher Werte ist 1 bis 2.147.483.647.
    
      - **Maximale Anzahl Verbindungen von einer einzelnen IP-Adresse**   Gibt die Anzahl von Verbindungen an, die der Server von einer einzelnen IP-Adresse akzeptiert. Der Standardwert ist 2.147.483.647. Der Bereich möglicher Werte ist 1 bis 2.147.483.647.
    
      - **Maximale Anzahl Verbindungen von einem einzelnen Benutzer**   Gibt die maximale Anzahl von Verbindungen an, die der Server von einem bestimmten Benutzer akzeptiert. Der Standardwert ist 16. Der Bereich möglicher Werte ist 1 bis 2.147.483.647.
    
      - **Max. Befehlsgröße (Bytes)**   Gibt die maximale Größe eines einzelnen Befehls an. Die Standardgröße ist 512. Der Bereich möglicher Werte ist 40 bis 1.024.

6.  Klicken Sie auf **Übernehmen** und dann auf **OK**, um die Änderungen zu speichern.

Nachdem Sie Verbindungslimits festgelegt haben, müssen Sie die POP3-Dienste neu starten. Informationen zum Neustarten der POP3-Dienste finden Sie unter [Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md).

## Verwenden der Shell zum Festlegen von POP3-Verbindungslimits für einen Server, eine IP-Adresse oder einen Benutzer

In diesem Beispiel wird das Verbindungslimit für einen Server festgelegt.

```powershell
Set-PopSettings -Identity CAS01 -MaxConnections Value
```

In diesem Beispiel wird das Verbindungslimit für eine IP-Adresse festgelegt.

```powershell
Set-PopSettings -Identity CAS01 -MaxConnectionsFromSingleIP Value
```

In diesem Beispiel wird das Verbindungslimit für einen Benutzer festgelegt.

```powershell
    Set-PopSettings -MaxConnectionsPerUser Value 
```

In diesem Beispiel wird die maximale Größe eines Befehls festgelegt.

```powershell
Set-PopSettings -MaxCommandSize Value
```

Nachdem Sie Verbindungslimits festgelegt haben, müssen Sie die POP3-Dienste neu starten. Informationen zum Neustarten der POP3-Dienste finden Sie unter [Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-PopSettings](https://technet.microsoft.com/de-de/library/aa997154\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass die Verbindungslimits richtig festgelegt sind:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** **\>** **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **POP3**.

4.  Führen Sie einen Bildlauf nach unten durch, und klicken Sie auf **Weitere Optionen**.\

5.  Überprüfen Sie unter **Verbindungslimits**, ob die Verbindungseinstellungen korrekt sind.

– oder –

1.  Führen Sie folgenden Befehl in der Shell aus.
    
    ```powershell
    Get-PopSettings | format-list
    ```

2.  Stellen Sie sicher, dass die Verbindungseinstellungen korrekt sind.

## Weitere Informationen

Nachdem Sie die POP3-Verbindungslimits für einen Server, eine IP-Adresse oder einen Benutzer festgelegt haben, können Sie die folgenden Aufgaben ausführen:

[Aktivieren von POP3 in Exchange 2013](enable-pop3-in-exchange-2013-exchange-2013-help.md)

[Festlegen von Grenzwerten für Verbindungstimeouts für POP3](set-connection-time-out-limits-for-pop3-exchange-2013-help.md)


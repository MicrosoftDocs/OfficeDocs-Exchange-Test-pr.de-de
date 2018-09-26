---
title: 'Konfig. v. Intervallen für Wiederh., erneute Übermittl. u. Ablauf von Nachr.'
TOCTitle: Konfigurieren von Wiederholungsintervallen, Intervallen für die erneute Übermittlung und Ablaufintervallen für Nachrichten
ms:assetid: 5420124f-aa4c-4702-b493-40a9a7edb786
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998043(v=EXCHG.150)
ms:contentKeyID: 51409295
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Wiederholungsintervallen, Intervallen für die erneute Übermittlung und Ablaufintervallen für Nachrichten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

In Microsoft Exchange Server 2013 können Sie die Intervalle für das Wiederholen, das erneute Übermitteln und den Ablauf von Nachrichten im Transportdienst auf Postfachservern und auf Edge-Transport-Servern konfigurieren. Beschreibungen dieser Einstellungen finden Sie unter [Wiederholungsintervalle, Intervalle für die erneute Übermittlung und Ablaufintervalle für Nachrichten](message-retry-resubmit-and-expiration-intervals-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportdienst" und "Edge-Transport-Server" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - UNRESOLVED\_TOKENBLOCK\_VAL(GENL\_Upgrade\_WebConfigFiles)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden Sie "EdgeTransport.exe.config" zum Konfigurieren des Zählers für Wiederholungsversuche für Warteschlangen, des Wiederholungsintervalls für Warteschlangen, des Wiederholungsintervalls für eine Postfachzustellungswarteschlange und der maximalen Leerlaufzeit vor dem Intervall für die erneute Übermittlung.

Zum Konfigurieren des Zählers für Wiederholungsversuche für Warteschlangen, des Wiederholungsintervalls für Warteschlangen, des Wiederholungsintervalls für eine Postfachzustellungswarteschlange und der maximalen Leerlaufzeit vor dem Intervall für die erneute Übermittlung werden Schlüssel in der XML-Anwendungskonfigurationsdatei "%ExchangeInstallPath%Bin\\EdgeTransport.exe.config" auf dem Postfachserver oder dem Edge-Transport-Server geändert. Änderungen, die Sie in dieser Datei speichern, werden nach einem Neustart des Microsoft Exchange-Transportdiensts angewendet. Wenn Sie diesen Dienst neu starten, wird die Nachrichtenübermittlung auf dem Server zeitweise unterbrochen.

1.  Öffnen Sie die Datei "EdgeTransport.exe.config" im Editor, indem Sie in einem Eingabeaufforderungsfenster auf dem Postfachserver oder Edge-Transport-Server den folgenden Befehl eingeben:
    
    ```powershell
        Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config
    ```

2.  Suchen Sie im Abschnitt `<appSettings>` die folgenden Schlüssel.
    
    ```powershell
        <add key="QueueGlitchRetryCount" value="<Integer>" />
        <add key="QueueGlitchRetryInterval" value="<hh:mm:ss>" />
        <add key="MailboxDeliveryQueueRetryInterval" value="<hh:mm:ss>" />
        <add key="MaxIdleTimeBeforeResubmit" value="<hh:mm:ss>" />
    ```
    
    In diesem Beispiel wird der Zähler für Wiederholungsversuche für Warteschlangen auf 6, das Wiederholungsintervall für Warteschlangen auf 30 Sekunden, das Wiederholungsintervall für eine Postfachzustellungswarteschlange auf 3 Minuten und die maximale Leerlaufzeit vor dem Intervall für die erneute Übermittlung auf 6 Stunden gesetzt.
    
    ```powershell
        <add key="QueueGlitchRetryCount" value="6" />
        <add key="QueueGlitchRetryInterval" value="00:00:30" />
        <add key="MailboxDeliveryQueueRetryInterval" value="00:03:00" />
        <add key="MaxIdleTimeBeforeResubmit" value="6:00:00" />
    ```
    
3.  Speichern und schließen Sie die Datei "EdgeTransport.exe.config" nach Abschluss des Vorgangs.

4.  Starten Sie den Microsoft Exchange-Transportdienst neu, indem Sie folgenden Befehl ausführen:
    
    ```powershell
        net stop MSExchangeTransport && net start MSExchangeTransport
    ```
    
## Konfigurieren der Wiederholungsversuche bei vorübergehenden Fehlern, des Intervalls für Wiederholungsversuche bei vorübergehenden Fehlern und des Wiederholungsintervalls bei Fehlern ausgehender Verbindungen

Die Wiederholungsversuche bei vorübergehenden Fehlern geben die Anzahl der Verbindungsversuche an, die nach dem Scheitern von Verbindungsversuchen durchgeführt werden, die durch die Schlüssel `QueueGlitchRetryCount` und `QueueGlitchRetryInterval` gesteuert werden. Der Standardwert für die Anzahl der Wiederholungsversuche bei vorübergehenden Fehlern beträgt 6. Der gültige Eingabebereich für diesen Parameter reicht von 0 bis 15. Wenn Sie die Anzahl der Wiederholungsversuche bei vorübergehenden Fehlern auf 0 setzen, wird der nächste Verbindungsversuch vom *Wiederholungsintervall bei Fehlern ausgehender Verbindungen* gesteuert.

Das Intervall für Wiederholungsversuche bei vorübergehenden Fehlern gibt das Intervall zwischen den einzelnen Verbindungsversuchen an, das über die Anzahl der Wiederholungsversuche bei vorübergehenden Fehlern angegeben wird. Im Transportdienst auf einem Postfachserver beträgt das Standardintervall für Wiederholungsversuche bei vorübergehenden Fehlern 5 Minuten. Auf einem Edge-Transport-Server beträgt das Standardintervall für Wiederholungsversuche bei vorübergehenden Fehlern 10 Minuten.

Das Wiederholungsintervall bei Fehlern ausgehender Verbindungen gibt das Wiederholungsintervall für ausgehende Verbindungsversuche an, die zuvor fehlgeschlagen sind. Die Anzahl der fehlgeschlagenen Verbindungsversuche wird über die Einstellungen für die Anzahl der Wiederholungsversuche bei vorübergehenden Fehlern und das Intervall für Wiederholungsversuche bei vorübergehenden Fehlern gesteuert. Der Standardwert für das Wiederholungsintervall bei ausgehenden Verbindungsfehlern im Transportdienst auf einem Postfachserver beträgt 10 Minuten. Der Standardwert für einen Edge-Transport-Server beträgt 30 Minuten.

## Konfigurieren der Wiederholungsversuche bei vorübergehenden Fehlern, des Intervalls für Wiederholungsversuche bei vorübergehenden Fehlern oder des Wiederholungsintervalls bei Fehlern ausgehender Verbindungen mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Server** \> **Server**, wählen Sie den Server aus, klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), und klicken Sie anschließend auf **Transportgrenzwerte**.

2.  Geben Sie im Abschnitt **Wiederholungsversuche** einen Wert für **Wiederholungsintervall bei Fehlern ausgehender Verbindungen (Sekunden)**, **Intervall für Wiederholungsversuche bei vorübergehenden Fehlern (Minuten)** oder **Wiederholungsversuche bei vorübergehenden Fehlern** ein.

3.  Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Konfigurieren der Wiederholungsversuche bei vorübergehenden Fehlern, des Intervalls für Wiederholungsversuche bei vorübergehenden Fehlern und des Wiederholungsintervalls bei Fehlern ausgehender Verbindungen mithilfe der Shell

Verwenden Sie die folgende Syntax zum Konfigurieren der Anzahl der Wiederholungsversuche bei vorübergehenden Fehlern, des Intervalls für Wiederholungsversuche bei vorübergehenden Fehlern und des Wiederholungsintervalls bei Fehlern ausgehender Verbindungen im Transportdienst auf einem Postfachserver oder einem Edge-Transport-Server.

```powershell
Set-TransportService <ServerIdentity> -TransientFailureRetryCount <Integer> -TransientFailureRetryInterval <hh:mm:ss> -OutboundConnectionFailureRetryInterval <dd.hh:mm:ss>
```

In diesem Beispiel werden die folgenden Werte auf dem Postfachserver "Mailbox01" geändert: auf dem Edge-Transport-Server "Exchange01".

  - Die Anzahl der Wiederholungsversuche bei vorübergehenden Fehlern wird auf 8 festgelegt.

  - Das Intervall für Wiederholungsversuche bei vorübergehenden Fehlern wird auf 1 Minute festgelegt.

  - Das Wiederholungsintervall bei Fehlern ausgehender Verbindungen wird auf 45 Minuten festgelegt.

<!-- end list -->

```powershell
    Set-TransportService Mailbox01 -TransientFailureRetryCount 8 -TransientFailureRetryInterval 00:01:00 -OutboundConnectionFailureRetryInterval 00:45:00
```

> [!NOTE]
> Die Parameter <EM>TransientFailureRetryCount</EM> und <EM>TransientFailureRetryInterval</EM> stehen auch im Cmdlet <STRONG>Set-FrontEndTransportService</STRONG> für den Front-End-Transport-Dienst auf Clientzugriffsservern zur Verfügung.



## Konfigurieren der Wiederholungsversuche bei vorübergehenden Fehlern, des Intervalls für Wiederholungsversuche bei vorübergehenden Fehlern und des Wiederholungsintervalls bei Fehlern ausgehender Verbindungen

## Konfigurieren der Wiederholungsversuche bei vorübergehenden Fehlern, des Intervalls für Wiederholungsversuche bei vorübergehenden Fehlern und des Wiederholungsintervalls bei Fehlern ausgehender Verbindungen mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Server** \> **Server**, wählen Sie den Server aus, klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), und klicken Sie anschließend auf **Transportgrenzwerte**.

2.  Geben Sie im Abschnitt **Wiederholungsversuche** einen Wert für **Wiederholungsintervall bei Fehlern ausgehender Verbindungen (Sekunden)**, **Intervall für Wiederholungsversuche bei vorübergehenden Fehlern (Minuten)** oder **Wiederholungsversuche bei vorübergehenden Fehlern** ein.

3.  Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Konfigurieren der Wiederholungsversuche bei vorübergehenden Fehlern, des Intervalls für Wiederholungsversuche bei vorübergehenden Fehlern und des Wiederholungsintervalls bei Fehlern ausgehender Verbindungen mithilfe der Shell

Verwenden Sie die folgende Syntax zum Konfigurieren der Anzahl der Wiederholungsversuche bei vorübergehenden Fehlern, des Intervalls für Wiederholungsversuche bei vorübergehenden Fehlern und des Wiederholungsintervalls bei Fehlern ausgehender Verbindungen im Transportdienst auf einem Postfachserver oder einem Edge-Transport-Server.

```powershell
    Set-TransportService <ServerIdentity> -TransientFailureRetryCount <Integer> -TransientFailureRetryInterval <hh:mm:ss> -OutboundConnectionFailureRetryInterval <dd.hh:mm:ss>
```

In diesem Beispiel werden die folgenden Werte auf dem Postfachserver "Mailbox01" geändert: auf dem Edge-Transport-Server "Exchange01".

  - Die Anzahl der Wiederholungsversuche bei vorübergehenden Fehlern wird auf 8 festgelegt.

  - Das Intervall für Wiederholungsversuche bei vorübergehenden Fehlern wird auf 1 Minute festgelegt.

  - Das Wiederholungsintervall bei Fehlern ausgehender Verbindungen wird auf 45 Minuten festgelegt.

<!-- end list -->

```powershell
    Set-TransportService Mailbox01 -TransientFailureRetryCount 8 -TransientFailureRetryInterval 00:01:00 -OutboundConnectionFailureRetryInterval 00:45:00
```

> [!NOTE]
> Die Parameter <EM>TransientFailureRetryCount</EM> und <EM>TransientFailureRetryInterval</EM> stehen auch im Cmdlet <STRONG>Set-FrontEndTransportService</STRONG> für den Front-End-Transport-Dienst auf Clientzugriffsservern zur Verfügung.



## Konfigurieren des Wiederholungsintervalls für Nachrichten mithilfe der Shell

Für das Wiederholungsintervall für Nachrichten ist standardmäßig `00:15:00` oder 15 Minuten festgelegt. Es wird empfohlen, den Standardwert nur zu ändern, wenn Sie vom Microsoft Customer Service and Support dazu aufgefordert werden.

Verwenden Sie folgende Syntax, um das Wiederholungsintervall für Nachrichten festzulegen.

```powershell
Set-TransportService <ServerIdentity> -MessageRetryInterval <dd.hh:mm:ss>
```

In diesem Beispiel wird das Nachrichtenwiederholungsintervall auf dem Postfachserver "Mailbox01" auf 20 Minuten festgelegt.

```powershell
Set-TransportService Mailbox01 -MessageRetryInterval 00:20:00
```

## Konfigurieren der Timeouteinstellungen für DNS-Verzögerungen

Das Timeoutintervall für DSN-Verzögerungsbenachrichtigungen kann mithilfe der Exchange-Verwaltungskonsole oder mithilfe der Shell konfiguriert werden. Diese Einstellung wird nur auf den lokalen Transportserver angewendet. Das Senden von DSN-Verzögerungsbenachrichtigungen an interne und externe Absender kann nur über die Shell aktiviert oder deaktiviert werden. Diese Einstellung gilt für alle Transportserver in Ihrer Organisation.


> [!NOTE]
> Auf Exchange 2007-Hub-Transport-Servern stehen alle <EM>ExternalDSN*</EM>- und <EM>InternalDSN*</EM>-Parameter im Cmdlet <STRONG>Set-TransportServer</STRONG>, nicht im Cmdlet <STRONG>Set-TransportConfig</STRONG> zur Verfügung. Wenn Sie in Ihrer Organisation Exchange 2007-Hub-Transport-Server verwenden, müssen Sie Änderungen an diesen Werten über das Cmdlet <STRONG>Set-TransportServer</STRONG> auf jedem Exchange 2007-Hub-Transport-Server vornehmen.



## Konfigurieren des Timeoutintervalls für DSN-Verzögerungsbenachrichtigungen mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Server** \> **Server**, wählen Sie den Server aus, klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), und klicken Sie anschließend auf **Transportgrenzwerte**.

2.  Geben Sie im Abschnitt **Benachrichtigungen** einen Wert für **Absender bei Verzögerung der Nachricht benachrichtigen nach (Stunden)** ein.

3.  Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Konfigurieren des Timeoutintervalls für DSN-Verzögerungsbenachrichtigungen mithilfe der Shell

Verwenden Sie folgende Syntax, um das Wiederholungsintervall für Nachrichten festzulegen.

```powershell
Set-TransportService <ServerIdentity> -DelayNotificationTimeout <dd.hh:mm:ss>
```

In diesem Beispiel wird das Timeoutintervall für DSN-Verzögerungsbenachrichtigungen auf dem Postfachserver "Mailbox01" auf 6 Stunden geändert.

```powershell
Set-TransportService Mailbox01 -DelayNotificationTimeout 06:00:00
```

## Aktivieren oder Deaktivieren des Versands von DSN-Verzögerungsbenachrichtigungen an externe oder interne Nachrichtenabsender mithilfe der Shell

Verwenden Sie folgende Syntax, um die Einstellungen von DSN-Verzögerungsbenachrichtigungen zu konfigurieren.

```powershell
    Set-TransportConfig -ExternalDelayDSNEnabled <$true | $false> -InternalDelayDSNEnabled <$true |$false>
```

In diesem Beispiel wird das Senden von DNS-Verzögerungsbenachrichtigungen an externe Absender deaktiviert.

```powershell
Set-TransportConfig -ExternalDelayDSNEnabled $false
```

In diesem Beispiel wird das Senden von DNS-Verzögerungsbenachrichtigungen an interne Absender deaktiviert.

```powershell
Set-TransportConfig -InternalDelayDSNEnabled $false
```

## Konfigurieren des Timeoutintervalls für den Nachrichtenablauf

## Konfigurieren des Timeoutintervalls für den Nachrichtenablauf mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Server** \> **Server**, wählen Sie den Server aus, klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), und klicken Sie anschließend auf **Transportgrenzwerte**.

2.  Geben Sie im Abschnitt **Nachrichtenablauf** einen Wert für **Maximale Dauer seit Übermittlung (Tage)** ein.

3.  Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Konfigurieren des Timeoutintervalls für den Nachrichtenablauf mithilfe der Shell

Verwenden Sie die folgende Syntax, um das Timeoutintervall für den Nachrichtenablauf zu konfigurieren.

```powershell
Set-TransportService <ServerIdentity> -MessageExpirationTimeout <dd.hh:mm:ss>
```

In diesem Beispiel wird das Timeoutintervall für den Nachrichtenablauf auf dem Exchange-Server "Mailbox01" in 4 Tage geändert.

```powershell
Set-TransportService Mailbox01 -MessageExpirationTimeout 4.00:00:00
```


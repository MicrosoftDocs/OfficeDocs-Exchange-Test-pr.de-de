---
title: 'Konfig. v. Nach.abrufformat-Opt. für POP3 und IMAP4: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren von Nachrichtenabrufformat-Optionen für POP3 und IMAP4
ms:assetid: 481096e0-4492-46c2-8ca8-bdf84a84531e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997869(v=EXCHG.150)
ms:contentKeyID: 50554792
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Nachrichtenabrufformat-Optionen für POP3 und IMAP4

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Sie können das Nachrichtenabrufformat für Benutzer konfigurieren, die mithilfe von POP3 und IMAP4 eine Verbindung mit ihrem E-Mail-Konto herstellen möchten. Nachrichtenabrufoptionen können auf Serverebene mithilfe der Exchange-Verwaltungskonsole oder der Shell konfiguriert werden. Auf Benutzerebene können sie mithilfe der Shell konfiguriert werden.

Weitere Informationen zu POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "POP3-Einstellungen" und "IMAP4-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Festlegen des POP3-Nachrichtenabrufformats auf Serverebene

## Festlegen des POP3-Nachrichtenabrufformats auf Serverebene mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **POP3**.

4.  Unter **MIME-Nachrichtenformat** stehen die folgenden Einstellungen zur Auswahl:
    
      - Text
    
      - HTML
    
      - HTML und Alternativtext
    
      - RTF
    
      - RTF und alternativer Text
    
      - Bestes Nachrichtentextformat
    
      - TNEF

5.  Klicken Sie auf **Speichern**.

Nachdem Sie die Einstellungen für das Nachrichtenabrufformat für POP3 festgelegt haben, müssen Sie die POP3-Dienste neu starten, damit die Einstellungen wirksam werden. Informationen zum Neustarten der POP3-Dienste finden Sie unter [Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md).

## Festlegen des POP3-Nachrichtenabrufformats auf Serverebene mithilfe der Shell

In diesem Beispiel wird die Option für das Nachrichtenabrufformat für alle POP3-Benutzer auf dem Server "CAS01" auf "Nur Text" festgelegt.

    Set-PopSettings -Identity CAS01 -MessageRetrievalMimeFormat TextOnly

Es stehen folgende Einstellungen zur Auswahl. Sie können den Wert für den Parameter *MessageRetrievalMimeFormat* festlegen, indem Sie einen numerischen Wert oder eine Textzeichenfolge verwenden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Nachrichtenformat</strong></p></td>
<td><p><strong>Wert</strong></p></td>
</tr>
<tr class="even">
<td><p>Text</p></td>
<td><p><code>0</code> oder <code>TextOnly</code></p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p><code>1</code> oder <code>HtmlOnly</code></p></td>
</tr>
<tr class="even">
<td><p>HTML und Alternativtext</p></td>
<td><p><code>2</code> oder <code>HtmlAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>RTF</p></td>
<td><p><code>3</code> oder <code>TextEnriched</code></p></td>
</tr>
<tr class="even">
<td><p>RTF und alternativer Text</p></td>
<td><p><code>4</code> oder <code>TextEnrichedAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Bestes Nachrichtentextformat</p></td>
<td><p><code>5</code> oder <code>BestBodyFormat</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF</p></td>
<td><p><code>6</code> oder <code>Tnef</code></p></td>
</tr>
</tbody>
</table>


Nachdem Sie die Einstellungen für das Nachrichtenabrufformat für POP3 festgelegt haben, müssen Sie die POP3-Dienste neu starten, damit die Einstellungen wirksam werden. Informationen zum Neustarten der POP3-Dienste finden Sie unter [Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-PopSettings](https://technet.microsoft.com/de-de/library/aa997154\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Konfiguration der Einstellungen für den POP3-Nachrichtenabruf auf einem Server zu überprüfen.

1.  Führen Sie folgenden Befehl in der Shell aus.
    
        Get-PopSettings | format-list

2.  Vergewissern Sie sich, dass die *MessageRetrievalMimeFormat*-Einstellungen korrekt sind.

## Festlegen des IMAP4-Nachrichtenabrufformats auf Serverebene

## Festlegen des IMAP4-Nachrichtenabrufformats auf Serverebene mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **IMAP4**.

4.  Unter **MIME-Nachrichtenformat** stehen die folgenden Einstellungen zur Auswahl:
    
      - Text
    
      - HTML
    
      - HTML und Alternativtext
    
      - RTF
    
      - RTF und alternativer Text
    
      - Bestes Nachrichtentextformat
    
      - TNEF

5.  Klicken Sie auf **Speichern**.

Nachdem Sie die Einstellungen für das Nachrichtenabrufformat für IMAP4 festgelegt haben, müssen Sie die IMAP4-Dienste neu starten, damit die Einstellungen wirksam werden. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

## Festlegen des IMAP4-Nachrichtenabrufformats auf Serverebene mithilfe der Shell

In diesem Beispiel wird die Option für das Nachrichtenabrufformat für alle IMAP4-Benutzer auf dem Server "CAS01" auf "Nur Text" festgelegt.

    Set-ImapSettings -Identity CAS01 -MessageRetrievalMimeFormat TextOnly

Es stehen folgende Einstellungen zur Auswahl. Sie können den Wert für den Parameter *MessageRetrievalMimeFormat* festlegen, indem Sie einen numerischen Wert oder eine Textzeichenfolge verwenden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Nachrichtenformat</strong></p></td>
<td><p><strong>Wert</strong></p></td>
</tr>
<tr class="even">
<td><p>Text</p></td>
<td><p><code>0</code> oder <code>TextOnly</code></p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p><code>1</code> oder <code>HtmlOnly</code></p></td>
</tr>
<tr class="even">
<td><p>HTML und Alternativtext</p></td>
<td><p><code>2</code> oder <code>HtmlAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>RTF</p></td>
<td><p><code>3</code> oder <code>TextEnriched</code></p></td>
</tr>
<tr class="even">
<td><p>RTF und alternativer Text</p></td>
<td><p><code>4</code> oder <code>TextEnrichedAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Bestes Nachrichtentextformat</p></td>
<td><p><code>5</code> oder <code>BestBodyFormat</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF</p></td>
<td><p><code>6</code> oder <code>Tnef</code></p></td>
</tr>
</tbody>
</table>


Nachdem Sie die Einstellungen für das Nachrichtenabrufformat für IMAP4 festgelegt haben, müssen Sie die IMAP4-Dienste neu starten, damit die Einstellungen wirksam werden. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Konfiguration der Einstellungen für den IMAP4-Nachrichtenabruf auf einem Server zu überprüfen.

1.  Führen Sie folgenden Befehl in der Shell aus.
    
        Get-ImapSettings | format-list

2.  Vergewissern Sie sich, dass die *MessageRetrievalMimeFormat*-Einstellungen korrekt sind.

## Festlegen des POP3-Nachrichtenabrufformats für einen Benutzer

## Festlegen des POP3-Nachrichtenabrufformats für einen Benutzer mithilfe der Shell

In diesem Beispiel wird das Nachrichtenabrufformat für den POP3-Zugriff für `USER01` auf "Nur Text" festgelegt.

    Set-CASMailbox -Identity USER01 -PopMessagesRetrievalMimeFormat TextOnly

Es stehen folgende Einstellungen zur Auswahl. Sie können den Wert für den Parameter *PopMessagesRetrievalMimeFormat* festlegen, indem Sie einen numerischen Wert oder eine Textzeichenfolge verwenden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Nachrichtenformat</strong></p></td>
<td><p><strong>Wert</strong></p></td>
</tr>
<tr class="even">
<td><p>Text</p></td>
<td><p><code>0</code> oder <code>TextOnly</code></p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p><code>1</code> oder <code>HtmlOnly</code></p></td>
</tr>
<tr class="even">
<td><p>HTML und Alternativtext</p></td>
<td><p><code>2</code> oder <code>HtmlAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>RTF</p></td>
<td><p><code>3</code> oder <code>TextEnriched</code></p></td>
</tr>
<tr class="even">
<td><p>RTF und alternativer Text</p></td>
<td><p><code>4</code> oder <code>TextEnrichedAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Bestes Nachrichtentextformat</p></td>
<td><p><code>5</code> oder <code>BestBodyFormat</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF</p></td>
<td><p><code>6</code> oder <code>Tnef</code></p></td>
</tr>
</tbody>
</table>


Nachdem Sie die Einstellungen für das Nachrichtenabrufformat für POP3 festgelegt haben, müssen Sie die POP3-Dienste neu starten, damit die Einstellungen wirksam werden. Informationen zum Neustarten der POP3-Dienste finden Sie unter [Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Konfiguration der Optionen für den POP3-Nachrichtenabruf für einen Benutzer zu überprüfen.

1.  Führen Sie folgenden Befehl in der Shell aus.
    
        Get-CAS Mailbox <identity> | format-list

2.  Überprüfen Sie, ob der Wert für *PopMessagesRetrievalMimeFormat* richtig ist.

## Festlegen des IMAP4-Nachrichtenabrufformats für einen Benutzer

## Festlegen des IMAP4-Nachrichtenabrufformats für einen Benutzer mithilfe der Shell

In diesem Beispiel wird das Nachrichtenabrufformat für den IMAP4-Zugriff für `USER01` auf "Nur Text" festgelegt.

    Set-CASMailbox -Identity USER01 -ImapMessagesRetrievalMimeFormat TextOnly

Sie können den Wert für den Parameter *ImapMessagesRetrievalMimeFormat* festlegen, indem Sie einen numerischen Wert oder eine Textzeichenfolge verwenden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Nachrichtenformat</strong></p></td>
<td><p><strong>Wert</strong></p></td>
</tr>
<tr class="even">
<td><p>Text</p></td>
<td><p><code>0</code> oder <code>TextOnly</code></p></td>
</tr>
<tr class="odd">
<td><p>HTML</p></td>
<td><p><code>1</code> oder <code>HtmlOnly</code></p></td>
</tr>
<tr class="even">
<td><p>HTML und Alternativtext</p></td>
<td><p><code>2</code> oder <code>HtmlAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>RTF</p></td>
<td><p><code>3</code> oder <code>TextEnriched</code></p></td>
</tr>
<tr class="even">
<td><p>RTF und alternativer Text</p></td>
<td><p><code>4</code> oder <code>TextEnrichedAndTextAlternative</code></p></td>
</tr>
<tr class="odd">
<td><p>Bestes Nachrichtentextformat</p></td>
<td><p><code>5</code> oder <code>BestBodyFormat</code></p></td>
</tr>
<tr class="even">
<td><p>TNEF</p></td>
<td><p><code>6</code> oder <code>Tnef</code></p></td>
</tr>
</tbody>
</table>


Nachdem Sie die Einstellungen für das Nachrichtenabrufformat für IMAP4 festgelegt haben, müssen Sie die IMAP4-Dienste neu starten, damit die Einstellungen wirksam werden. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Konfiguration der Optionen für den IMAP4-Nachrichtenabruf für einen Benutzer zu überprüfen.

1.  Führen Sie folgenden Befehl in der Shell aus.
    
        Get-CAS Mailbox <identity> | format-list

2.  Überprüfen Sie, ob der Wert für *ImapMessagesRetrievalMimeFormat* richtig ist.

## Weitere Informationen

Nachdem Sie das Nachrichtenabrufformat für IMAP4- und POP3-Benutzer festgelegt haben, können Sie die folgenden Aufgaben ausführen:

[Aktivieren oder Deaktivieren des POP3-Zugriffs für einen Benutzer](enable-or-disable-pop3-access-for-a-user-exchange-2013-help.md)

[Aktivieren oder Deaktivieren des IMAP4-Zugriffs für einen Benutzer](enable-or-disable-imap4-access-for-a-user-exchange-2013-help.md)

[Konfigurieren von Kalenderoptionen für IMAP4](configure-calendar-options-for-imap4-exchange-2013-help.md)

[Konfigurieren von Kalenderoptionen für POP3](configure-calendar-options-for-pop3-exchange-2013-help.md)


---
title: 'Konfig. d. Inhaltsfilt. für Verw. sicherer Domänendaten: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren der Inhaltsfilterung für eine Verwendung sicherer Domänendaten
ms:assetid: 1ee2b663-b4f3-4fef-8954-986f2d820924
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn467930(v=EXCHG.150)
ms:contentKeyID: 59634163
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren der Inhaltsfilterung für eine Verwendung sicherer Domänendaten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-16_

Sichere Domänendaten sind eine komplette Domäne (z. B. @contoso.com), die in der Liste sicherer Absender eines Benutzers gespeichert ist. Standardmäßig verwendet der Inhaltsfilter-Agent sichere Domänendaten nicht, um Absender zu identifizieren, die die Inhaltsfilterung von Nachrichten umgehen dürfen.

Diese Standardeinstellung trägt dazu bei, die Menge von Spam-Nachrichten, die Ihr Unternehmen erhält, zu reduzieren. Ein Benutzer kann z. B. die Domäne eines großen E-Mail-Anbieters zu seiner Liste sicherer Absender hinzufügen. Wenn diese Domäne häufig verwendet oder von Spammern gefälscht wird und wenn die Inhaltsfilterung so konfiguriert ist, dass sichere Domänendaten verwendet werden, um die Nachrichten als sicher zu markieren, werden Nachrichten von allen Absendern in dieser Domäne an alle Empfänger in Ihrem Unternehmen gesendet.

Wir empfehlen, die Standardeinstellungen in den meisten Fällen nicht zu ändern. Sie können allerdings die sicheren Domänendaten eines Benutzers so konfigurieren, dass Sie in Active Directory gespeichert und von der Inhaltsfilterung verwendet werden, um Nachrichten als sicher zu markieren. Dafür müssen Sie die XML-Anwendungskonfigurationsdatei MSExchangeMailboxAssistants.exe.config, die mit dem Microsoft Exchange-Postfach-Assistentendienst verknüpft ist, verändern. Dieses Verfahren wird später in diesem Thema ausführlich erläutert. Wenn Sie diese Konfigurationsänderung durchführen, werden die sicheren Domänendaten einem Hashvorgang unterzogen und im Benutzerobjektattribut **msExchSafeSenderHash** eines jeden Benutzers in Active Directory als Teil der Aggregation von Listen sicherer Empfänger gespeichert. Anschließend kann der Inhaltsfilter-Agent die sicheren Domänendaten verwenden, um Nachrichten von Absendern in diesen Domänen als sicher zu markieren. Weitere Informationen zur Aggregation von Listen sicherer Empfänger finden Sie unter [Aggregation von Listen sicherer Adressen](safelist-aggregation-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten

  - Exchange-Berechtigungen gelten nicht für die Verfahren in diesem Thema. Diese Verfahren werden im Betriebssystem des Exchange Server-Computers ausgeführt.

  - Änderungen, die Sie in der Datei MSExchangeMailboxAssistants.exe.config speichern, werden übernommen, wenn Sie den Microsoft Exchange-Postfach-Assistentendienst neu starten.

  - Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z. B. an „web.config\&quot;-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config\&quot; auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden Sie eine Eingabeaufforderung, um die Inhaltsfilterung für eine Verwendung sicherer Domänendaten zu konfigurieren.

1.  Geben Sie in einem Eingabeaufforderungsfenster den folgenden Befehl ein, um die Datei "MSExchangeMailboxAssistants.exe.config" in Notepad zu öffnen:
    
    ```powershell
        Notepad %ExchangeInstallPath%Bin\MSExchangeMailboxAssistants.exe.config
    ```
2.  Navigieren Sie zum Schlüssel *\</appsettings\>* am Ende der Datei, und fügen Sie vor dem Schlüssel *\</appsettings\>* den folgenden Schlüssel ein:
    
    ```command line
    <add key="IncludeSafeDomains" value="true" />
    ```

3.  Speichern und schließen Sie die Datei "MSExchangeMailboxAssistants.exe.config" nach Abschluss des Vorgangs.

4.  Starten Sie den Microsoft Exchange-Postfach-Assistentendienst neu, indem Sie folgenden Befehl ausführen:
    
    ```powershell
        net stop MSExchangeMailboxAssistants && net start MSExchangeMailboxAssistants
    ```
    
## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob Sie die Inhaltsfilterung erfolgreich für eine Verwendung sicherer Domänendaten konfiguriert haben:

1.  Überprüfen Sie, ob durch Hinzufügung einer Domäne zur Liste sicherer Absender in Outlook das Attribut **msExchSafeSenderHash** eines Benutzers in Active Directory aktualisiert wird. Zeigen Sie dafür das Attribut in ADSIEdit.exe oder LDP.exe an, öffnen Sie das Postfach des Benutzers in Outlook, fügen Sie eine Domäne zur Liste sicherer Absender hinzu, führen Sie den Befehl `Update-Safelist <username>` aus, und prüfen Sie, ob die ursprünglichen und die aktuellen Werte von **msExchSafeSenderHash** unterschiedlich sind.

2.  Wenn Sie überprüft haben, ob die sicheren Domänendaten in Active Directory gespeichert werden, senden Sie eine Testnachricht von einem externen Sender in dieser Domäne an einen Benutzer in Ihrem Unternehmen. Überprüfen Sie, ob die Nachricht als sicher markiert wird, indem Sie die Antispam-Kopfzeilenfelder in der Nachrichtenkopfzeile untersuchen.


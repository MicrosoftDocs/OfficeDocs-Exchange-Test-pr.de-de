---
title: 'Konfigurieren von IP-Adressen und Ports für POP3- und IMAP4-Zugriff: Exchange 2013 Help'
TOCTitle: Konfigurieren von IP-Adressen und Ports für POP3- und IMAP4-Zugriff
ms:assetid: 8292747b-6626-4d7f-ba73-1e17f5d99fa4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123530(v=EXCHG.150)
ms:contentKeyID: 50554852
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von IP-Adressen und Ports für POP3- und IMAP4-Zugriff

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-11-28_

Sie können über die Exchange-Verwaltungskonsole und Shell die Microsoft Exchange POP3- und IMAP4-Dienste für die Verwendung von IP-Adressen und Ports konfigurieren, die sich von den Standardeinstellungen unterscheiden.


> [!NOTE]
> Geben Sie die IP-Adressen und IP-Adressbereiche im IPv4-Format (Internet Protocol Version 4), im IPv6-Format (Internet Protocol Version 6) oder in beiden Formaten ein. In einer Standardinstallation von Windows Server 2008 ist die Unterstützung für IPv4 und IPv6 aktiviert.



Weitere Informationen zu POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "POP3-Einstellungen" und "IMAP4-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der zu verwendenden IP-Adressen und Ports für POP3

## Konfigurieren der IP-Adressen und Ports für POP3 mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** **\>** **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **POP3**.

4.  Klicken Sie unter **TLS- oder unverschlüsselte Verbindungen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Wählen Sie auf der Seite **IP-Adresse hinzufügen** unter **IP-Adresse** eine der folgenden Optionen:
    
      - **Alle verfügbaren IPv4-Adressen**   Verwenden Sie alle für einen Server verfügbaren IPv4-Adressen.
    
      - **Alle verfügbaren IPv6-Adressen**   Verwenden Sie alle für einen Server verfügbaren IPv6-Adressen.
    
      - **IP-Adresse angeben**   Verwenden Sie eine bestimmte IP-Adresse.

6.  Geben Sie unter **Port** eine Portnummer ein, oder übernehmen Sie den Standardport.

7.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

Nachdem Sie die IP-Adressen und Porteinstellungen für POP3 eingerichtet haben, müssen Sie den POP3-Dienst neu starten, damit die Einstellungen in Kraft treten. Informationen zum Neustarten des POP3-Diensts finden Sie unter [Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md).

## Konfigurieren der IP-Adressen und Ports für POP3 mithilfe der Shell

In diesem Beispiel werden die IP-Adresse und der Port für die Kommunikation mit Exchange mithilfe von POP3 mit SSL (Secure Sockets Layer) festgelegt.

    Set-PopSettings -SSLBindings: IPaddress:Port

In diesem Beispiel werden die IP-Adresse und der Port für die Kommunikation mit Exchange mithilfe von POP3 ohne Verschlüsselung oder mit TLS-Verschlüsselung (Transport Layer Security) festgelegt.

    Set-PopSettings -UnencryptedOrTLSBindings IPaddress:Port

Nachdem Sie die IP-Adressen und Porteinstellungen für POP3 eingerichtet haben, müssen Sie den POP3-Dienst neu starten, damit die Einstellungen in Kraft treten. Informationen zum Neustarten des POP3-Diensts finden Sie unter [Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-PopSettings](https://technet.microsoft.com/de-de/library/aa997154\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Schritte aus, um zu bestätigen, dass Sie die IP-Adress- und Porteinstellungen für POP3 auf einem Server geändert haben.

1.  Führen Sie folgenden Befehl in der Shell aus.
    
        Get-PopSettings | format-list

2.  Vergewissern Sie sich, dass die Einstellungen *UnencryptedOrTLSBindings* und *SSLBindings* ordnungsgemäß sind.

## Konfigurieren der zu verwendenden IP-Adressen und Ports für IMAP4

## Konfigurieren der IP-Adressen und Ports für IMAP4 mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** **\>** **Server**.

2.  Wählen Sie in der Liste der Server den Clientzugriffsserver aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Servereigenschaften auf **IMAP4**.

4.  Wenn Sie TLS- oder unverschlüsselte Verbindungseinstellungen festlegen möchten, klicken Sie unter **TLS- oder unverschlüsselte Verbindungen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wenn Sie SSL-Verbindungseinstellungen (Secure Sockets Layer) festlegen möchten, klicken Sie unter **SSL-Verbindungen (Secure Sockets Layer)** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Wählen Sie auf der Seite **IP-Adresse hinzufügen** unter **IP-Adresse** eine der folgenden Optionen:
    
      - **Alle verfügbaren IPv4-Adressen**   Verwenden Sie alle für einen Server verfügbaren IPv4-Adressen.
    
      - **Alle verfügbaren IPv6-Adressen**   Verwenden Sie alle für einen Server verfügbaren IPv6-Adressen.
    
      - **IP-Adresse angeben**   Verwenden Sie eine bestimmte IP-Adresse.

6.  Geben Sie unter **Port** eine Portnummer ein, oder übernehmen Sie den Standardport.

7.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

Nachdem Sie die IP-Adressen und Porteinstellungen für IMAP4 eingerichtet haben, müssen Sie die IMAP4-Dienste neu starten, damit die Einstellungen in Kraft treten. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

## Konfigurieren der IP-Adressen und Ports für IMAP4 mithilfe der Shell

In diesem Beispiel werden die IP-Adresse und der Port für die Kommunikation mit Exchange mit IMAP4 festgelegt.

    Set-ImapSettings -SSLBindings: IPaddress:Port

In diesem Beispiel werden die IP-Adresse und der Port für die Kommunikation mit Exchange mithilfe von IMAP4 ohne Verschlüsselung oder mit TLS-Verschlüsselung (Transport Layer Security) festgelegt.

    Set-ImapSettings -UnencryptedOrTLSBindings IPaddress:Port 

Nachdem Sie die IP-Adressen und Porteinstellungen für IMAP4 eingerichtet haben, müssen Sie den IMAP4-Dienst neu starten, damit die Einstellungen in Kraft treten. Informationen zum Neustarten des IMAP4-Diensts finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Schritte aus, um zu bestätigen, dass Sie die IP-Adress- und Porteinstellungen für IMAP4 auf einem Server geändert haben.

1.  Führen Sie folgenden Befehl in der Shell aus.
    
        Get-ImapSettings | format-list

2.  Vergewissern Sie sich, dass die Einstellungen *UnencryptedOrTLSBindings* und *SSLBindings* ordnungsgemäß sind.

## Weitere Informationen

Nachdem Sie die IP-Adressen und Ports für POP3 und IMAP4 konfiguriert haben, können Sie die folgenden Aufgaben ausführen:

[Aktivieren von IMAP4 in Exchange 2016](enable-imap4-in-exchange-2013-exchange-2013-help.md)

[Aktivieren von POP3 in Exchange 2013](enable-pop3-in-exchange-2013-exchange-2013-help.md)


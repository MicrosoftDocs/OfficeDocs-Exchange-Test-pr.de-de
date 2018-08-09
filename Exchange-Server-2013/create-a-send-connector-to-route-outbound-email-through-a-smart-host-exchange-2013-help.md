---
title: 'Erstellen v. Sendeconnectors f. Weiterleit. v. ausgeh. E-Mails über Smarthost'
TOCTitle: Erstellen eines Sendeconnectors, um ausgehende E-Mails über einen Smarthost weiterzuleiten
ms:assetid: 4a9ef08e-bd62-4c6b-8790-d24fb0f8f24b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673059(v=EXCHG.150)
ms:contentKeyID: 50475622
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines Sendeconnectors, um ausgehende E-Mails über einen Smarthost weiterzuleiten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-07_

In einigen Situationen ist es vielleicht erforderlich, E-Mails über einen Smarthost eines Drittanbieters zu routen. Dies kann beispielsweise der Fall sein, wenn Sie ein Netzwerkgerät verwenden, mit dem Sie Richtlinienprüfungen für ausgehende Nachrichten durchführen.


> [!NOTE]
> Der Smarthost des Drittanbieters muss SMTP für den Transport verwenden. Andernfalls sollten Sie einen fremden Connector oder einen Zustellungs-Agent-Connector verwenden.



Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Konfigurieren von Nachrichtenfluss und Clientzugriff](configure-mail-flow-and-client-access-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Sendeconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Lesen Sie [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md), wenn Sie gerade mit der Installation beginnen. Nach der Installation können Sie die Schritte in diesem Thema ausführen, um den ausgehenden Connector zu erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen eines Sendeconnectors zum Routen ausgehender E-Mails über einen Smarthost mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Sendconnectors**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im Assistenten für neue Sendeconnectors einen Namen für den Sendeconnector an, und wählen Sie für **Typ** die Option **Benutzerdefiniert**. Üblicherweise wählen Sie diese Option, wenn Sie Nachrichten an Computer ohne Microsoft Exchange Server 2013 routen möchten. Klicken Sie dann auf **Weiter**.

3.  Wählen Sie **E-Mail über Smarthosts weiterleiten** aus, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Geben Sie im Fenster **Smarthost hinzufügen** die IP-Adresse, z. B. 192.168.100.1, oder den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN), z. B. "contoso.com" an. Klicken Sie auf **Speichern**.
    
    Wählen Sie unter **Smarthostauthentifizierung** die Art der Authentifizierung, die für den Smarthost erforderlich ist. Wenn Sie **Standardauthentifizierung** auswählen, müssen Sie einen Benutzernamen und ein Kennwort eingeben.
    

    > [!NOTE]
    > Bei Verwendung der Standardauthentifizierung wird empfohlen, eine verschlüsselte Verbindung zu nutzen, da Benutzername und Kennwort als Klartext gesendet werden.



4.  Klicken Sie unter **Adressraum** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Stellen Sie sicher, dass im Fenster **Domäne hinzufügen** als **Typ** SMTP aufgeführt ist. Geben Sie als **Vollqualifizierter Domänenname (FQDN)** ein Sternchen (\*) ein. Dies bedeutet, dass der Sendeconnector auf Nachrichten angewendet wird, die an eine beliebige Domäne gesendet werden. Klicken Sie auf **Speichern**.

5.  Klicken Sie bei **Quellserver** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wählen Sie im Fenster **Server auswählen** einen Postfachserver aus, der zum Senden von E-Mails an das Internet über den Clientzugriffsserver verwendet werden soll, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Nachdem Sie den Server ausgewählt haben, klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Klicken Sie auf **OK**.

6.  Klicken Sie auf **Fertig stellen**.

Nachdem Sie den Sendeconnector erstellt haben, wird dieser in der Liste der Sendeconnectors angezeigt.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Senden Sie eine Nachricht von einem Benutzer in Ihrer Organisation (Sie können Outlook Web App verwenden) an die Domäne, die Sie unter **Adressraum** eingegeben haben, um die erfolgreiche Erstellung eines Sendeconnectors zum Routen ausgehender E-Mails über einen Smarthost zu überprüfen. Wenn der Empfänger die Nachricht erhält, haben Sie den Sendeconnector erfolgreich erstellt.

## Weitere Informationen

[Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden](create-a-send-connector-for-email-sent-to-the-internet-exchange-2013-help.md)

[Sendeconnectors](send-connectors-exchange-2013-help.md)


---
title: 'Erstellen eines Empfangsconnectors zum Empfangen von Nachrichten von einem internen Exchange-Server: Exchange 2013 Help'
TOCTitle: Erstellen eines Empfangsconnectors zum Empfangen von Nachrichten von einem internen Exchange-Server
ms:assetid: 546cead9-7a2d-4332-a5f6-35343d56c619
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657448(v=EXCHG.150)
ms:contentKeyID: 50475705
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines Empfangsconnectors zum Empfangen von Nachrichten von einem internen Exchange-Server

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-03_

Sie erstellen einen Empfangsconnector vom Typ **Intern**, wenn Sie E-Mails von einem Exchange-Server empfangen möchten. Verwenden Sie diese Art von Connector, um das E-Mail-Routing innerhalb Ihrer Organisation zu steuern: beispielsweise, wenn Sie E-Mails vom Transportdienst auf einem Postfachserver an einen bestimmten Edge-Transport-Server oder von einem Postfachserver an einen anderen weiterleiten möchten.

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Konfigurieren von Nachrichtenfluss und Clientzugriff](configure-mail-flow-and-client-access-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Empfangsconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Lesen Sie [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md), wenn Sie gerade mit der Installation beginnen. Nach der Installation können Sie die Schritte in diesem Thema verwenden, um den Empfangsconnector zu erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen eines Empfangsconnectors zum Empfangen von Nachrichten von einem internen Exchange-Server

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Empfangsconnectors**. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um einen neuen Empfangsconnector zu erstellen.

2.  Geben Sie auf der Seite **Neuer Empfangsconnector** einen Namen für den Empfangsconnector an, und wählen Sie für **Rolle** die Option **Hub-Transport**. In diesem Fall wird davon ausgegangen, dass Sie E-Mails innerhalb Ihres Netzwerks weiterleiten und nicht in die und aus der Organisation senden möchten.

3.  Wählen Sie als Typ **Intern** aus. Der Connector wird mit der Exchange-Serverauthentifizierung konfiguriert.

4.  Wenn auf der Seite mit den Remotenetzwerkeinstellungen 0.0.0.0-255.255.255.255 aufgeführt ist, der Empfangsconnector also Verbindungen von allen IP-Adressen empfängt, klicken Sie zum Entfernen auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"). Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), fügen Sie die IP-Adresse für den Server hinzu, vom dem Sie E-Mails empfangen möchten – beispielsweise 192.168.1.1 –, und klicken Sie auf **Speichern**.

5.  Klicken Sie auf **Fertig stellen**, um den Connector zu erstellen.

Nachdem Sie den Empfangsconnector erstellt haben, wird er in der Liste der Empfangsconnectors angezeigt. Ein Beispiel für das Erstellen eines Empfangsconnectors mit einem Cmdlet finden Sie unter [New-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125139\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Testen Sie, ob Nachrichten vom sendenden Server erfolgreich an den Empfangsserver gesendet werden, um sicherzustellen, dass Sie der Empfangsconnector zum Empfang von Nachrichten von einem internen Server erfolgreich erstellt wurde. Eine Möglichkeit hierzu ist die Verwendung der Exchange-Verwaltungsshell. Legen Sie den Parameter *ProtocolLoggingLevel* des Cmdlets [Set-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125140\(v=exchg.150\)) für den erstellten Empfangsconnector auf `Verbose` fest, und überprüfen Sie die Protokolle auf eine erfolgreiche Nachrichtenzustellung.

## Weitere Informationen

[Erstellen eines Empfangsconnectors zum Empfang von E-Mails aus dem Internet](create-a-receive-connector-to-receive-email-from-the-internet-exchange-2013-help.md)

[Erstellen eines sicheren Empfangsconnectors, um E-Mails von einem Partner zu empfangen](create-a-secure-receive-connector-to-receive-email-from-a-partner-exchange-2013-help.md)


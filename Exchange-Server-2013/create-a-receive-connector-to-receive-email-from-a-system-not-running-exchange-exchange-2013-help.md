---
title: 'Erstellen eines Empfangsconnectors zum Empfang von E-Mails von einem System ohne Exchange: Exchange 2013 Help'
TOCTitle: Erstellen eines Empfangsconnectors zum Empfang von E-Mails von einem System ohne Exchange
ms:assetid: 85f0864a-6502-49db-8804-16755a7292b4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657467(v=EXCHG.150)
ms:contentKeyID: 50476087
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines Empfangsconnectors zum Empfang von E-Mails von einem System ohne Exchange

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Es kann vorkommen, dass Sie Nachrichten von einem System empfangen möchten, auf dem kein Exchange ausgeführt wird. Beispielsweise könnten Sie ein Netzwerkgerät verwenden, das Richtlinienprüfungen durchführt und anschließend Nachrichten an Ihren Exchange-Server sendet. In diesem Fall wird davon ausgegangen, dass das Gerät SMTP verwendet. Andernfalls sollten Sie einen fremden Connector oder einen Zustellungs-Agent-Connector einsetzen.

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Konfigurieren von Nachrichtenfluss und Clientzugriff](configure-mail-flow-and-client-access-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Empfangsconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Lesen Sie [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md), wenn Sie gerade mit der Installation beginnen. Nach der Installation können Sie die Schritte in diesem Thema verwenden, um den Empfangsconnector zu erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen eines Empfangsconnectors zum Empfangen von Nachrichten von einer Messaging-Appliance mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Empfangsconnectors**. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um einen Empfangsconnector zu erstellen.

2.  Geben Sie auf der Seite **Neuer Empfangsconnector** einen Namen für den Empfangsconnector ein, und wählen Sie dann als **Rolle** die Option **Hub-Transport** aus. In diesem Fall soll der Postfachserver, auf dem der Transportdienst ausgeführt wird, Nachrichten von der Appliance erhalten.

3.  Wählen Sie als Typ **Benutzerdefiniert**, da der Empfangsconnector E-Mails von einer Appliance erhalten soll, auf der kein Microsoft Exchange Server 2013 ausgeführt wird.

4.  Beachten Sie unter **Netzwerkadapterbindungen**, dass **Alle verfügbaren IPV4** in der Liste **IP-Adressen** aufgeführt ist. Klicken Sie dann auf **Weiter**.

5.  Klicken Sie unter **Remote-Netzwerkeinstellungen** auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um **0.0.0.0-255.255.255.255** aus der Liste **IP-Adressen** zu entfernen, da Sie festlegen möchten, dass der Connector E-Mails von einer bestimmten Appliance akzeptiert. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue IP-Adresse hinzuzufügen, und fügen Sie im Fenster **IP-Adresse hinzufügen** die IP-Adresse Ihrer Appliance hinzu. Klicken Sie auf **Speichern**.

6.  Klicken Sie auf die Schaltfläche **Fertig stellen**, um den Connector zu erstellen.

Nachdem Sie den Empfangsconnector erstellt haben, wird er in der Liste der Empfangsconnectors angezeigt. Ein Beispiel für die Erstellung eines Empfangsconnectors mithilfe eines Cmdlets finden Sie unter [New-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125139\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Testen Sie, ob Sie E-Mails von der Appliance empfangen können, um sicherzustellen, dass Sie den Empfangsconnector zum Empfangen von Nachrichten von einer Messaging-Appliance erfolgreich erstellt haben. Wenn Sie E-Mails empfangen können, funktioniert die Konfiguration fehlerfrei.

## Weitere Informationen

[Erstellen eines Empfangsconnectors zum Empfang von E-Mails aus dem Internet](create-a-receive-connector-to-receive-email-from-the-internet-exchange-2013-help.md)


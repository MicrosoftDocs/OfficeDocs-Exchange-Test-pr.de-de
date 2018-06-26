---
title: 'Erstellen eines Empfangsconnectors zum Empfang von E-Mails aus dem Internet: Exchange 2013 Help'
TOCTitle: Erstellen eines Empfangsconnectors zum Empfang von E-Mails aus dem Internet
ms:assetid: 534bbd32-a0db-4d50-9579-4933b156d7b3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657447(v=EXCHG.150)
ms:contentKeyID: 50475673
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines Empfangsconnectors zum Empfang von E-Mails aus dem Internet

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-15_

In diesem Thema wird gezeigt, wie Sie einen Empfangsconnector für den Empfang von E-Mails aus dem Internet konfigurieren.


> [!NOTE]
> In den meisten Fällen ist es nicht erforderlich, eine explizite Einrichtung eines Empfangsconnectors zum Empfang von E-Mails aus dem Internet durchzuführen, da bei der Installation von Exchange implizit ein Empfangsconnector zum Akzeptieren von E-Mails aus dem Internet erstellt wird. Weitere Informationen finden Sie unter <A href="receive-connectors-exchange-2013-help.md">Empfangsconnectors</A>.



Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Konfigurieren von Nachrichtenfluss und Clientzugriff](configure-mail-flow-and-client-access-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Empfangsconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Lesen Sie [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md), wenn Sie gerade mit der Installation beginnen. Nach der Installation können Sie die Schritte in diesem Thema verwenden, um den Empfangsconnector zu erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen eines Empfangsconnectors für den Empfang von Nachrichten aus dem Internet mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Empfangsconnectors**. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um einen Empfangsconnector zu erstellen.

2.  Geben Sie auf der Seite **Neuer Empfangsconnector** einen Namen für den Empfangsconnector an, und wählen Sie für **Rolle** die Option **Front-End-Transport**. Da Sie in diesem Fall E-Mails aus dem Internet empfangen, sollten Sie E-Mails zunächst an Ihren Front-End-Server weiterleiten, um die Nachrichtenübermittlung zu vereinfachen und zu konsolidieren.

3.  Wählen Sie als Typ **Internet** aus. Der Empfangsconnector empfängt E-Mails von Internetabsendern.

4.  Beachten Sie, dass für **Netzwerkadapterbindungen** der Eintrag **Alle verfügbaren IPv4** in der Liste **IP-Adressen** aufgeführt und im Feld **Port** der Port 25 festgelegt ist. (Simple Mail Transfer Protocol \[SMTP\] verwendet Port 25.) Damit wird angegeben, dass der Connector Verbindungen für alle IP-Adressen abhört, die Netzwerkkarten des lokalen Servers zugewiesen sind.
    

    > [!NOTE]
    > Wenn Sie über mehrere Netzwerkadapter verfügen, können Sie auf dieser Seite eine IP-Adresse hinzufügen, die einem bestimmten Netzwerkadapter auf dem lokalen Server zugewiesen wird. Diese Eingabe ist jedoch nicht erforderlich.



5.  Klicken Sie auf die Schaltfläche **Fertig stellen**, um den Connector zu erstellen.

Nachdem Sie den Empfangsconnector erstellt haben, wird er in der Liste der Empfangsconnectors angezeigt. Ein Beispiel für das Erstellen eines Empfangsconnectors mit einem Cmdlet finden Sie unter [New-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125139\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Testen Sie, ob Sie E-Mails von einer externen Quelle senden können, und überprüfen Sie den erfolgreichen Empfang dieser E-Mails durch interne Benutzer, um die erfolgreiche Erstellung eines Empfangsconnectors zum Empfang von Nachrichten aus dem Internet sicherzustellen. Wenn Sie E-Mails empfangen können, funktioniert die Konfiguration fehlerfrei.

## Weitere Informationen

[Erstellen eines sicheren Empfangsconnectors, um E-Mails von einem Partner zu empfangen](create-a-secure-receive-connector-to-receive-email-from-a-partner-exchange-2013-help.md)

[Erstellen eines Empfangsconnectors zum Empfang von E-Mails von einem System ohne Exchange](create-a-receive-connector-to-receive-email-from-a-system-not-running-exchange-exchange-2013-help.md)


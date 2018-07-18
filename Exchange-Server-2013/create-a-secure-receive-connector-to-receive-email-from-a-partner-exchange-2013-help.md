---
title: 'Erstellen eines sicheren Empfangsconnectors, um E-Mails von einem Partner zu empfangen: Exchange 2013 Help'
TOCTitle: Erstellen eines sicheren Empfangsconnectors, um E-Mails von einem Partner zu empfangen
ms:assetid: 06aa692c-7940-4a14-a722-058c47440f85
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673037(v=EXCHG.150)
ms:contentKeyID: 50474976
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines sicheren Empfangsconnectors, um E-Mails von einem Partner zu empfangen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

In diesem Thema wird gezeigt, wie Sie einen Empfangsconnector für den Empfang sicherer E-Mails von einem Partner konfigurieren. Führen Sie diese Schritte aus, wenn Sie die Kommunikation zwischen Ihrer eigenen Organisation und einem vertrauenswürdigen Partner verschlüsseln müssen. Der Connector wird so konfiguriert, dass ausschließlich Verbindungen von Servern akzeptiert werden, die sich über Transport Layer Security (TLS) authentifizieren.

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Konfigurieren von Nachrichtenfluss und Clientzugriff](configure-mail-flow-and-client-access-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Empfangsconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Lesen Sie [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md), wenn Sie gerade mit der Installation beginnen. Nach der Installation können Sie die Schritte in diesem Thema verwenden, um den Empfangsconnector zu erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen eines Empfangsconnectors für den Empfang sicherer Nachrichten von einem Partner mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Empfangsconnectors**. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um einen neuen Empfangsconnector zu erstellen.

2.  Geben Sie auf der Seite **Neuer Empfangsconnector** einen Namen für den Empfangsconnector an, und wählen Sie für **Rolle** die Option **Front-End-Transport**. Da Sie in diesem Fall E-Mails von einem Partner empfangen, sollten Sie E-Mails zunächst an Ihren Front-End-Server weiterleiten, um die Nachrichtenübermittlung zu vereinfachen und zu konsolidieren.

3.  Wählen Sie als Typ **Partner** aus. Der Empfangsconnector empfängt E-Mails von einem vertrauenswürdigen Drittanbieter.

4.  Beachten Sie, dass für **Netzwerkadapterbindungen** der Eintrag **Alle verfügbaren IPv4** in der Liste **IP-Adressen** aufgeführt und im Feld **Port** der Port 25 festgelegt ist. (Simple Mail Transfer Protocol verwendet Port 25.) Damit wird angegeben, dass der Connector Verbindungen für alle IP-Adressen abhört, die Netzwerkkarten des lokalen Servers zugewiesen sind. Klicken Sie dann auf **Weiter**.

5.  Wenn auf der Seite mit den Remotenetzwerkeinstellungen 0.0.0.0-255.255.255.255 aufgeführt ist, der Empfangsconnector also Verbindungen von allen IP-Adressen empfängt, klicken Sie zum Entfernen auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"). Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), fügen Sie die IP-Adressen für den Server des Partners hinzu, und klicken Sie auf **Speichern**.
    

    > [!NOTE]
    > Sie können auch eine IP-Adresse mit CIDR-Schreibweise angeben (z.&nbsp;B. 64.4.6.100/24).



6.  Klicken Sie auf **Fertig stellen**, um den Connector zu erstellen.

Nachdem Sie den Empfangsconnector erstellt haben, wird er in der Liste der Empfangsconnectors angezeigt. Ein Beispiel für das Erstellen eines Empfangsconnectors mit einem Cmdlet finden Sie unter [New-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125139\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um die erfolgreiche Erstellung eines Empfangsconnectors für den Empfang der Nachrichten eines Partners zu überprüfen, testen Sie, ob der Partner E-Mails an einen Ihrer Benutzer senden kann und der Benutzer diese E-Mails erfolgreich empfängt. Die Konfiguration war erfolgreich, wenn Sie verschlüsselte E-Mails empfangen können (Sie können anhand des Nachrichtenkopfs überprüfen, ob TLS verwendet wird).

## Weitere Informationen

[Empfangsconnectors](receive-connectors-exchange-2013-help.md)


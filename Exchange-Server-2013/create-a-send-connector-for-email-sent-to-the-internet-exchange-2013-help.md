---
title: 'Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden: Exchange 2013 Help'
TOCTitle: Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden
ms:assetid: 6deaefa8-1152-40d9-b1ba-9c19bdf8a928
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657457(v=EXCHG.150)
ms:contentKeyID: 50475910
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-01-23_

Standardmäßig lässt Microsoft Exchange Server 2013 kein Senden von E-Mails außerhalb Ihrer Domäne zu. Sie müssen einen Sendeconnector erstellen, damit E-Mails an Empfänger außerhalb Ihrer Domäne gesendet werden zu können. Die folgende Grafik veranschaulicht den Nachrichtenfluss, wenn Sie einen Sendeconnector erstellen, um Nachrichten an das Internet zu senden.

![connector\_send\_onprem\_internet](images/JJ657457.e8963e4f-7dce-461f-bbcf-660278cefa35(EXCHG.150).gif "connector_send_onprem_internet")

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Konfigurieren von Nachrichtenfluss und Clientzugriff](configure-mail-flow-and-client-access-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Sendeconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Lesen Sie [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md), wenn Sie gerade mit der Installation beginnen. Nach der Installation können Sie die Schritte in diesem Thema ausführen, um den ausgehenden Connector zu erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole, um einen Sendeconnector zum Senden von E-Mails über das Internet zu erstellen

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Sendconnectors**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im Assistenten für neue Sendeconnectors einen Namen für den Sendeconnector an, und wählen Sie für **Typ** die Option **Internet**. Klicken Sie dann auf **Weiter**.

3.  Überprüfen Sie, ob **Mit der Empfängerdomäne verbundener MX-Eintrag** aktiviert ist. Diese Option gibt an, dass der Connector DNS (Domain Name System) zum Weiterleiten von E-Mails verwendet. Klicken Sie dann auf **Weiter**.

4.  Klicken Sie unter **Adressraum** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Stellen Sie sicher, dass im Fenster **Domäne hinzufügen** als **Typ** SMTP aufgeführt ist. Geben Sie als **Vollqualifizierter Domänenname (FQDN)** ein Sternchen (\*) ein. Dies bedeutet, dass der Sendeconnector auf Nachrichten angewendet wird, die an eine beliebige Domäne gesendet werden. Klicken Sie auf **Speichern**.

5.  Stellen Sie sicher, dass das Kontrollkästchen **Sendeconnector mit Bereich** deaktiviert ist, und klicken Sie auf **Weiter**.

6.  Klicken Sie bei **Quellserver** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wählen Sie im Fenster **Server auswählen** einen Postfachserver aus, der zum Senden von E-Mails an das Internet über den Clientzugriffsserver verwendet werden soll, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Nachdem Sie den Server ausgewählt haben, klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Klicken Sie auf **OK**.

7.  Klicken Sie auf **Fertig stellen**.

Nachdem Sie den Sendeconnector erstellt haben, wird dieser in der Liste der Sendeconnectors angezeigt.

## Weiterleiten von Nachrichten über den Clientzugriffsserver mithilfe der Shell

In Exchange 2013 können Sie den Parameter *FrontendProxyEnabled* des Cmdlets **Set-SendConnector** verwenden, um ausgehende Nachrichten über den Clientzugriffsserver weiterzuleiten. Der Parameter ist nicht standardmäßig auf `$true` festgelegt. In vielen Fällen jedoch kann dieser Parameter die Nachrichtenübermittlung konsolidieren und vereinfachen, insbesondere in Umgebungen mit einer Vielzahl von Messagingservern.

In diesem Beispiel wird der Parameter *FrontendProxyEnabled* auf einem Sendeconnector auf `$true` festgelegt.

    Set-SendConnector "Contoso.com Send Connector" -FrontendProxyEnabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Überprüfen, ob der Sendeconnector zum Senden von E-Mails über das Internet erfolgreich erstellt wurde, senden Sie eine E-Mail von einem Ihrer Benutzer an einen Empfänger außerhalb Ihrer Domäne, und vergewissern Sie sich, dass die E-Mail empfangen wurde.

## Weitere Informationen

[Sendeconnectors](send-connectors-exchange-2013-help.md)

[Erstellen eines Sendeconnectors, um ausgehende E-Mails über einen Smarthost weiterzuleiten](create-a-send-connector-to-route-outbound-email-through-a-smart-host-exchange-2013-help.md)


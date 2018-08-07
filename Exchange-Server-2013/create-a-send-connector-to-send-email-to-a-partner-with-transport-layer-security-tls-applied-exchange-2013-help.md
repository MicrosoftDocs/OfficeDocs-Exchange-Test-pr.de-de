---
title: 'Erst. v. Sendeconnectors n. Aktiv. v. TLS zum Send. v. E-Mails an Partner'
TOCTitle: Erstellen eines Sendeconnectors nach Aktivierung von Transport Layer Security (TLS), um E-Mails an Partner zu senden
ms:assetid: ff2abefc-dd3e-4431-b947-df942fbf82d9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657514(v=EXCHG.150)
ms:contentKeyID: 50477154
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines Sendeconnectors nach Aktivierung von Transport Layer Security (TLS), um E-Mails an Partner zu senden

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-15_

Wenn Sie die sichere, verschlüsselte Kommunikation mit einem Partner sicherstellen möchten, können Sie einen Sendeconnector erstellen, der für die Durchsetzung der Transport Layer Security (TLS) für Nachrichten konfiguriert wird, die an eine Partnerdomäne gesendet werden. TLS stellt sichere Kommunikation über das Internet bereit.

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Konfigurieren von Nachrichtenfluss und Clientzugriff](configure-mail-flow-and-client-access-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Sendeconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Weitere Informationen finden Sie unter [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md), wenn Sie Ihre Installation starten. Nach der Installation können Sie die Schritte in diesem Thema ausführen, um den ausgehenden Connector zu erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen von Sendeconnectors mithilfe der Exchange-Verwaltungskonsole, um E-Mails an einen Partner zu senden, wobei TLS angewendet wurde

Melden Sie sich an der Exchange-Verwaltungskonsole an, und führen Sie die folgenden Schritte aus, um einen Sendeconnector für dieses Szenario zu erstellen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Sendeconnectors**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im Assistenten **Neuer Sendeconnector** einen Namen für den Sendeconnector an, und wählen Sie dann unter **Typ** die Option **Partner** aus. Wenn Sie **Partner** auswählen, wird der Connector so konfiguriert, dass nur Verbindungen mit Servern zugelassen werden, die sich mit TLS authentifizieren. Klicken Sie dann auf **Weiter**.

3.  Überprüfen Sie, dass die Option **Mit der Empfängerdomäne verbundener MX-Eintrag** ausgewählt ist, die angibt, dass der Connector das Domain Name System (DNS) verwendet, um E-Mail weiterzuleiten. Klicken Sie dann auf **Weiter**.

4.  Klicken Sie unter **Adressbereich** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Stellen Sie im Fenster **Domäne hinzufügen** sicher, dass SMTP als **Typ** aufgelistet ist. Geben Sie für **Vollqualifizierter Domänenname (FQDN)** den Namen Ihrer Partnerdomäne ein. Klicken Sie auf **Speichern**.

5.  Klicken Sie für **Quellserver** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wählen Sie im Fenster **Server auswählen** einen Postfachserver aus, der zum Senden von E-Mail an das Internet über den Clientzugriffsserver verwendet wird, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Nachdem Sie den Server ausgewählt haben, klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Klicken Sie auf **OK**.

6.  Klicken Sie auf **Fertig stellen**.

Nachdem Sie den Sendeconnector erstellt haben, wird dieser in der Liste der Sendeconnectors angezeigt.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Stellen Sie sicher, dass Sie erfolgreich einen Sendeconnector erstellt haben, um E-Mail an einen Partner zu senden, wobei TLS angewendet wurde, indem Sie eine Nachricht von einem Benutzer in Ihrer Organisation an einen Empfänger in der Partnerorganisation senden. Wenn der Empfänger die Nachricht erhält, wurde der Connector erfolgreich erstellt.

## Weitere Informationen

[Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden](create-a-send-connector-for-email-sent-to-the-internet-exchange-2013-help.md)

[Erstellen eines Sendeconnectors, um ausgehende E-Mails über einen Smarthost weiterzuleiten](create-a-send-connector-to-route-outbound-email-through-a-smart-host-exchange-2013-help.md)


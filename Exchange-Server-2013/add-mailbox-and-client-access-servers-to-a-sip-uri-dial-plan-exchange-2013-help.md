---
title: 'Hinzufügen von Postfach- und Clientzugriffsservern zu einem SIP-URI-Wählplan'
TOCTitle: Hinzufügen von Postfach- und Clientzugriffsservern zu einem SIP-URI-Wählplan
ms:assetid: 17fed308-ff0d-4e61-b9f9-e6680b6eccaa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996399(v=EXCHG.150)
ms:contentKeyID: 52062835
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinzufügen von Postfach- und Clientzugriffsservern zu einem SIP-URI-Wählplan

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-16_

Sie können Clientzugriffs- und Postfachserver zu SIP-URI-Wählplänen hinzufügen. Clientzugriffs- und Postfachserver können keinen Telefondurchwahlnummern oder E.164-Wählplänen zugewiesen werden, der Server wird jedoch alle eingehenden Anrufe beantworten.

Wenn Sie Microsoft Lync Server bereitstellen, müssen Sie den für Lync Server erstellten SIP-URI-Wählplänen alle Clientzugriffs- und Postfachserver manuell hinzufügen, damit ausgehende Anrufe einwandfrei funktionieren.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein SIP-URI-UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Mit der Exchange-Verwaltungskonsole einen Postfachserver zu einem SIP-URI-Wählplan hinzufügen.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Postfachserver aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Klicken Sie unter **UM-Diensteinstellungen** \> **Zugeordnete Wählpläne** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Wählen Sie im Fenster **UM-Wählplan auswählen** den SIP-URI-Wählplan aus, und klicken Sie auf **Hinzufügen**, dann auf **OK** und schließlich auf **Speichern**.

## Mit der Shell einen Postfachserver zu einem SIP-URI-Wählplan hinzufügen

In diesem Beispiel wird der Postfachserver `MyMailboxServer` einem SIP-URI-Wählplan namens `MySIPDialPlan` hinzugefügt und für die Annahme neuer Anrufe gesperrt. Außerdem wird der Startmodus auf den Dualmodus festgelegt. Dies ermöglicht dem Postfachserver das Akzeptieren von TCP- und TLS-Anforderungen.

    Set-UMService -Identity MyMailboxServer -DialPlans MySIPDialPlan -Status Disabled -UMStartupMode Dual

In diesem Beispiel wird der Postfachserver `MyMailboxServer` zwei SIP-Wählplänen namens `MySIPDialPlan` und `MySIPDialPlan2` hinzugefügt. Ferner werden folgende Einstellungen festgelegt:

  - Zulassen sowohl von IPv4- als auch von IPv6-Adressen.

  - Legt die maximale Anzahl eingehender Anrufe auf 50 fest.

  - Konfiguriert den SIP-Zugriffsdiensts für Lync Server.

<!-- end list -->

    Set-UMService -Identity MyMailboxServer -DialPlans MySIPDialPlan, MySIPDialPlan2 -IPAddressFamily Any -MaxCallsAllowed 50 -SipAccessService northamerica.lyncpoolna.contoso.com

## Mit der Exchange-Verwaltungskonsole einen Clientzugriffsserver zu einem SIP-URI-Wählplan hinzufügen

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Cientzugriffsserver aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Klicken Sie unter **UM-Anrufroutereinstellungen** \> **Zugeordnete Wählpläne** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Wählen Sie im Fenster **UM-Wählplan auswählen** den SIP-URI-Wählplan aus, und klicken Sie auf **Hinzufügen**, dann auf **OK** und schließlich auf **Speichern**.

## Mit der Shell einen Clientzugriffsserver zu einem SIP-URI-Wählplan hinzufügen

In diesem Beispiel wird der Clientzugriffsserver `MyClientAccessServer` einem SIP-URI-Wählplan mit der Bezeichnung `MySIPDialPlan` hinzugefügt. Außerdem wird der Startmodus auf den Dualmodus festgelegt. Dies ermöglicht dem Clientzugriffsserver das Akzeptieren von TCP- und TLS-Anforderungen.

    Set-UMCallRouterSettings -DialPlans MySIPDialPlan -Server MyClientAccessServer -UMStartupMode Dual

In diesem Beispiel wird der Clientzugriffsserver `MyClientAccessServer` zu zwei SIP-Wählplänen mit der Bezeichnung `MySIPDialPlan` und `MySIPDialPlan2` hinzugefügt, und der Server kann IPv4- und IPv6-Addressen verwenden.

    Set-UMCallRouterSettings -DialPlans MySIPDialPlan, MySIPDialPlan2 -IPAddressFamily Any -Server MyClientAccessServer


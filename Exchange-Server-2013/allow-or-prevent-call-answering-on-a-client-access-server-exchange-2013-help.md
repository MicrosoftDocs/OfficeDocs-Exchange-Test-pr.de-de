---
title: 'Ermöglichen oder verhindern, dass die Anrufbeantwortung auf einem Clientzugriffsserver: Exchange 2013 Help'
TOCTitle: Ermöglichen oder verhindern, dass die Anrufbeantwortung auf einem Clientzugriffsserver
ms:assetid: 8287bb78-2621-4b80-a128-8f2ccd67923a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123529(v=EXCHG.150)
ms:contentKeyID: 50554862
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ermöglichen oder verhindern, dass die Anrufbeantwortung auf einem Clientzugriffsserver

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-18_

Sie können dem Microsoft Exchange Unified Messaging-Anrufrouterdienst auf einem Clientzugriffsserver erlauben, neue Anruf entgegenzunehmen, oder ihn daran hindern. Standardmäßig nimmt ein Clientzugriffsserver nach seiner Installation Anrufe an. Mit dem Cmdlet **Set-ServerComponentState** können Sie den Clientzugriffsserver für das Annehmen von Sprach-, Fax- und Outlook Voice Access-Anrufen sowie von Anrufen der automatischen Telefonzentrale einrichten.

Durch Konfigurieren des Wartungsmodus für einen Clientzugriffsserver können Sie den Server außer Dienst nehmen. Ein außer Dienst genommener Clientzugriffsserver kann keine eingehenden Anrufe von VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen oder Session Border Controller (SBCs) annehmen.

In Exchange 2007 und Exchange 2010 gab es einen Statusparameter, mit dem der Betriebsstatus eines Unified Messaging-Servers gesteuert werden konnte. In Exchange 2013 steht zu diesem Zweck für das Cmdlet **Set-UMCallRouterSettings** für einen Clientzugriffsserver kein Statusparameter zur Verfügung.


> [!IMPORTANT]
> Sie müssen Clientzugriffsserver und Postfachserver nur dann zum Verarbeiten von UM-Anrufen einem UM-Wählplan hinzufügen, wenn Sie UM mit Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server integrieren. Standardmäßig stehen alle Clientzugriffs- und Postfachserver zum Beantworten eingehender Anrufe zur Verfügung.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Clientzugriffsserver finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Exchange Server-Konfigurationseinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Stellen Sie sicher, dass der Clientzugriffsserver installiert ist, entweder auf demselben Computer wie der Postfachserver oder auf einem anderen Computer.

  - Wenn Sie einen Clientzugriffsserver in den Wartungsmodus versetzen, vergewissern Sie sich, dass im Clientzugriffsarray genügend stabile Kapazität vorhanden ist, damit der Server außer Dienst gehen kann.

  - Überprüfen Sie, bevor Sie einen Server wieder in den Betriebsmodus versetzen, den Status des Servers, und vergewissern Sie sich, dass er in Dienst gehen kann.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Konfigurieren des Zulassens oder Verhindern von Mailboxansagen mithilfe der Shell

Dieses Beispiel ermöglicht dem Clientzugriffsserver `UMCallRouter-05x.contoso.com` das Beantworten von Sprach-, Fax- und Outlook Voice Access-Anrufen sowie von Anrufen der automatischen Telefonzentrale von VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen und SBCs und schreibt die Änderung in die Registrierung auf dem Server "UMCallRouter-05x".

    Set-ServerComponentState -Component UnifiedMessaging -Identity UMCallRouter-05x.contoso.com -Requester Maintenance -State Active -LocalOnly

Dieses Beispiel hindert den Clientzugriffsserver `UMCallRouter-05x.contoso.com` am Beantworten von Sprach-, Fax- und Outlook Voice Access-Anrufen sowie von Anrufen der automatischen Telefonzentrale von VoIP-Gateways, IP-Nebenstellenanlagen, SIP-fähigen Nebenstellenanlagen und SBCs und schreibt die Änderung nur in Active Directory.

    Set-ServerComponentState -Component UnifiedMessaging -Identity UMCallRouter-05x.contoso.com -Requester Maintenance -State Inactive -RemoteOnly


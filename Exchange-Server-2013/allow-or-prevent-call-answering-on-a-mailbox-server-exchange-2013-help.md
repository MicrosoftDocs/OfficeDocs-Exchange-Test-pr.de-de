---
title: 'Ermöglichen oder verhindern, dass die Anrufbeantwortung auf einem Postfachserver: Exchange 2013 Help'
TOCTitle: Ermöglichen oder verhindern, dass die Anrufbeantwortung auf einem Postfachserver
ms:assetid: 4b860c09-6669-4e3d-b3dc-17b8018b3860
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997908(v=EXCHG.150)
ms:contentKeyID: 50554816
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ermöglichen oder verhindern, dass die Anrufbeantwortung auf einem Postfachserver

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-18_

Sie können den Microsoft Exchange Unified Messaging-Dienst auf einem Postfachserver zu neuen Anrufe entgegennehmen oder verhindern, dass Sie auf diese Weise erlauben. Standardmäßig wird ein Postfachserver in einem aktivierten Status nach der Installation. Beim Festlegen von des Postfachserver eingehende Sprach-, Fax-, automatische Telefonzentrale und Outlook Voice Access-Anrufe annehmen kann, verwenden Sie das Cmdlet **Set-ServerComponentState** .

Für einen Postfachserver Wartungsmodus konfigurieren, können Sie den Server außer Betrieb nehmen. Für einen Postfachserver bedeutet Out-of-Service an, dass der Server werden keine aktiven Datenbanken hosten, alle transportwarteschlangen leer sind und der Server werden kein eingehende Anrufe von Client Access Server, VoIP-Gateways, IP-PBX-Anlagen, SIP-aktivierte Nebenstellenanlagen oder Session Border Controller (SBCs akzeptiert).

In Exchange 2007 und Exchange 2010 gab es ein Statusparameter, der zum Steuern der Betriebsstatus des Unified Messaging-Servers verwendet werden konnte. In Exchange 2013 ist kein Statusparameter für diesen Zweck im **Set-UMService** -Cmdlet für einen Postfachserver verfügbar.


> [!IMPORTANT]
> Sie müssen Clientzugriffsserver und Postfachserver nur dann zum Verarbeiten von UM-Anrufen einem UM-Wählplan hinzufügen, wenn Sie UM mit Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server integrieren. Standardmäßig stehen alle Clientzugriffs- und Postfachserver zum Beantworten eingehender Anrufe zur Verfügung.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Postfachserver finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Exchange Server-Konfigurationseinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Stellen Sie sicher, dass der Postfachserver installiert ist, entweder auf demselben Computer wie der Clientzugriffsserver oder auf einem anderen Computer.

  - Wenn Sie einen Postfachserver in den Wartungsmodus bereitstellen, stellen Sie sicher, dass genügend Redundanz alle Datenbankkopien, damit den Server außer Betrieb wechseln kann vorhanden ist.

  - Überprüfen Sie, bevor Sie einen Server wieder in den Betriebsmodus versetzen, den Status des Servers, und vergewissern Sie sich, dass er in Dienst gehen kann.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Zulassen oder Sperren von Anrufbeantwortung auf einem Postfachserver

In diesem Beispiel wird ein Postfach Server `UMMBXr-05x.contoso.com` Beantworten eingehender Sprach-, Fax-, automatische Telefonzentrale aktiviert, und Outlook Voice Access Aufrufe von VoIP-Gateways, IP-PBX-Anlagen, SIP-aktivierte Nebenstellenanlagen und SBCs, und schreibt die Änderung der Registrierung auf die UMMBX-05 x Server.

    Set-ServerComponentState -Component UnifiedMessaging -Identity UMMBX-05x.contoso.com -Requester Maintenance -State Active -LocalOnly

In diesem Beispiel wird verhindert, dass ein Postfach Server `UMMBX-05x.contoso.com` aus antwortenden eingehende Sprach-, Fax-, automatische Telefonzentrale und Outlook Voice Access-Anrufe von VoIP-Gateways, IP-PBX-Anlagen, SIP-aktivierte Nebenstellenanlagen und SBCs, und schreibt die Änderung nur in Active Directory.

    Set-ServerComponentState -Component UnifiedMessaging -Identity UMMBX-05x.contoso.com -Requester Maintenance -State Inactive -RemoteOnly


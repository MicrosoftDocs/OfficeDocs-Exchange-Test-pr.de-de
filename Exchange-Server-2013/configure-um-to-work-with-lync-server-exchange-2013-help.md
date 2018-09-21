---
title: 'Konfigurieren der Zusammenarbeit von UM mit Lync Server: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren der Zusammenarbeit von Unified Messaging mit Lync Server
ms:assetid: 29bdddbf-75d5-4c92-988e-c8506ecc7a1c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ966276(v=EXCHG.150)
ms:contentKeyID: 52062849
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Zusammenarbeit von Unified Messaging mit Lync Server

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-06-11_

Wenn Sie Microsoft Lync Server in Exchange Unified Messaging (UM) integrieren, müssen Sie das Skript "ExchUcUtil.ps1" in der Shell ausführen. Das Skript "ExchUcUtil.ps1" führt Folgendes aus:

  - Es erstellt ein UM-IP-Gateway für jeden Lync Server-Pool.
    

    > [!IMPORTANT]
    > Das Skript "ExchUcUtil.ps1" erstellt ein oder mehrere UM-IP-Gateways. Sie müssen ausgehende Anrufe für alle UM-IP-Gateways deaktivieren, außer dem einen Gateway, das durch das Skript erstellt wurde. Dazu gehört auch das Deaktivieren von ausgehenden Anrufen auf UM-IP-Gateways, die vor dem Ausführen des Skripts erstellt wurden. Informationen zum Deaktivieren von ausgehenden Anrufen auf UM-IP-Gateways finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/disable-outgoing-calls-on-um-ip-gateways">Deaktivieren Sie ausgehende Anrufe für UM-IP-gateways</A>.



  - Es erstellt einen UM-Sammelanschluss für jedes UM-IP-Gateway. Die Pilot-ID der einzelnen Sammelanschlüsse gibt den UM-SIP-URI-Wählplan an, der von dem Lync Server-Front-End-Pool oder von dem Standard Edition-Server verwendet wird, der dem UM-IP-Gateway zugeordnet ist.

  - Es erteilt Lync Server die Berechtigung zum Lesen von Active Directory-UM-Containerobjekten wie UM-Wählplänen, automatischen Telefonzentralen, UM-IP-Gateways und UM-Sammelanschlüssen.


> [!IMPORTANT]
> Jede UM-Gesamtstruktur muss so konfiguriert werden, dass sie der Gesamtstruktur vertraut, in der Lync Server 2013 bereitgestellt wird. Die Gesamtstruktur, in der Lync Server 2013 bereitgestellt wird, muss wiederum so konfiguriert sein, dass sie jeder UM-Gesamtstruktur vertraut. Falls Exchange UM in mehreren Gesamtstrukturen installiert ist, müssen die Schritte zur Exchange Server-Integration für jede UM-Gesamtstruktur durchgeführt werden. Ansonsten müssen Sie die Lync Server-Domäne angeben. Beispiel: <EM>ExchUcUtil.ps1 –Forest:&lt;lync-domain-controller-fqdn&gt;</EM>.



Weitere Verwaltungsaufgaben im Zusammenhang mit der Integration von Lync Server und Unified Messaging finden Sie unter [Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)](deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungs-Cmdlets" im Thema [Exchange 2013-Cmdlets](https://technet.microsoft.com/de-de/library/bb124413\(v=exchg.150\)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Ausführen des Skripts "ExchUcUtil.ps1" mithilfe der Shell

Führen Sie das Skript "ExchUcUtil.ps1" auf einem Exchange-Server in Ihrer Organisation aus, der sich in derselben Topologie wie Microsoft Lync Server befindet. Sie können das Skript in der Shell auf einem Postfachserver oder über die Windows Remote-PowerShell auf einem Clientzugriffsserver ausführen. Wenn Sie das Skript auf einem Clientzugriffsserver in Ihrer Organisation ausführen, leitet der Clientzugriffsserver die Windows Remote-PowerShell-Sitzung über einen Proxy an einen Postfachserver in der Organisation weiter.


> [!IMPORTANT]
> Das ExchUCUtil.ps1-Skript erstellt ein oder mehrere UM-IP-Gateways. Sie müssen ausgehende Anrufe für alle UM-IP-Gateways deaktivieren, außer dem einen Gateway, das durch das Skript erstellt wurde. Dazu gehört auch das Deaktivieren von ausgehenden Anrufen auf UM-IP-Gateways, die vor dem Ausführen des Skripts erstellt wurden. Informationen zum Deaktivieren von ausgehenden Anrufen auf UM-IP-Gateways finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/disable-outgoing-calls-on-um-ip-gateways">Deaktivieren Sie ausgehende Anrufe für UM-IP-gateways</A>.




> [!IMPORTANT]
> Sie benötigen die Berechtigungen der Rolle "Exchange-Organisationsverwaltung" oder müssen ein Mitglied der Sicherheitsgruppe "Exchange-Organisationsadministratoren" sein, um das Skript auszuführen.



1.  Öffnen Sie die Exchange-Verwaltungsshell.

2.  Geben Sie an der `C:\Windows\System32`-Eingabeaufforderung **cd “\<Laufwerkbuchstabe\>\\Programme\\Microsoft\\Exchange Server\\V15\\Scripts\>.ExchUcUtil.ps1”** ein, und drücken Sie dann die EINGABETASTE.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob das Skript "ExchUcUtul.ps1" erfolgreich abgeschlossen wurde:

  - Verwenden Sie das Cmdlet **Get-UMIPGateway** oder die Exchange-Verwaltungskonsole, um die neu erstellten UM-IP-Gateways anzuzeigen.

  - Verwenden Sie das Cmdlet **Get-UMHuntGroup** oder die Exchange-Verwaltungskonsole, um die neu erstellten UM-Sammelanschlüsse anzuzeigen.


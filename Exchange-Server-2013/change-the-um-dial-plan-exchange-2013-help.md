---
title: 'Ändern des um-Wählplans: Exchange Online Help'
TOCTitle: Ändern des um-Wählplans
ms:assetid: 4a6b6b6f-c61c-44e8-91dd-c5d28835f441
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633465(v=EXCHG.150)
ms:contentKeyID: 50475579
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ändern des um-Wählplans

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-05_

Es kann notwendig sein, einen Benutzer, der für Unified Messaging (UM) aktiviert wurde, in einen anderen UM-Wählplan zu verschieben oder die Wähleinstellungen zu ändern, die dem zugeordnet sind. Beispielsweise könnten Sie einen UM-aktivierten Benutzer aus einem Wählplan mit Telefondurchwahlen in einen SIP-URI-Wählplan verschieben.

Zum Ändern des UM-Wählplans müssen Sie den Benutzer für UM deaktivieren und den Benutzer anschließend im neuen UM-Wählplan wieder für UM aktivieren. Dies ist erforderlich, da für verschiedene Wähleinstellungen verschiedene Einstellungen und Anforderungen gelten können, z. B. unterschiedliche Durchwahllängen oder verschiedene URI-Typen. Bei SIP-URI-Wähplänen ist es beispielsweise erforderlich, dass jedem UM-aktivierten Postfach eine SIP-Ressourcen-ID zugewiesen ist, bei Telefondurchwahl-Wähleinstellungen jedoch nicht. Darüber hinaus enthält jedes UM-Postfach Verweise sowohl auf die UM-Wähleinstellungen als auch auf die UM-Postfachrichtlinie. Die UM-Postfachrichtlinie enthält wiederum Verweise auf den UM-Wählplan. Wenn Sie die primäre Proxyadresse für einen UM-aktivierten Benutzer ändern, sodass sie auf andere Wähleinstellungen zeigt, weist das UM-Postfach anschließend einen inkonsistenten Zustand auf.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass der vorhandene Exchange-Empfänger für Unified Messaging aktiviert ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen des neuen UM-Wählplans


> [!IMPORTANT]
> Wenn Sie UM-aktivierte Benutzer zu Microsoft Office Communications Server 2007&nbsp;R2 oder Microsoft Lync Server migrieren, müssen Sie zunächst einen SIP-URI-Wählplan erstellen.



Ausführliche Anweisungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

## Schritt 2: Deaktivieren des Benutzers für Unified Messaging

Ausführliche Anweisungen finden Sie unter [Deaktivieren von Voicemail für einen Benutzer](disable-voice-mail-for-a-user-exchange-2013-help.md).

## Schritt 3: Aktivieren des Benutzers für Unified Messaging im neuen UM-Wählplan


> [!IMPORTANT]
> Wenn Sie Benutzer in eine Umgebung mit Office Communications Server 2007&nbsp;R2 oder Lync Server verschieben, müssen Sie außerdem eine SIP-Ressourcen-ID für den Benutzer angeben, wenn Sie ihn für UM aktivieren. Darüber hinaus müssen Sie die UM-Postfachrichtlinie auswählen, die den SIP-Wähleinstellungen zugeordnet ist.



Ausführliche Anweisungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).


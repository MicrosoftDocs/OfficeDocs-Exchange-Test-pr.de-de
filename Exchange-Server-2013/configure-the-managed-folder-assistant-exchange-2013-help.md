---
title: 'Konfigurieren des Assistenten für verwaltete Ordner: Exchange 2013 Help'
TOCTitle: Konfigurieren des Assistenten für verwaltete Ordner
ms:assetid: 9fcfb9b6-bd24-4218-a163-bc599cd5476a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123958(v=EXCHG.150)
ms:contentKeyID: 50476319
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren des Assistenten für verwaltete Ordner

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-10-01_

Der *Assistent für verwaltete Ordner* ist ein MicrosoftExchange-Postfach-Assistent, mit dem Einstellungen für die Aufbewahrung von Nachrichten angewendet werden, die in Aufbewahrungsrichtlinien konfiguriert sind.

Weitere Verwaltungsaufgaben im Zusammenhang mit der Messaging-Datensatzverwaltung (MRM) finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Konfiguration des Assistenten für verwaltete Ordner kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden

  - In Exchange 2013 ist der Assistent für verwaltete Ordner ein einschränkungsbasierter Assistent. Einschränkungsbasierte Assistenten werden immer ausgeführt und müssen nicht geplant werden. Die Systemressourcen, die von ihnen beansprucht werden können, sind eingeschränkt. Sie können den Assistenten für verwaltete Ordner so konfigurieren, dass er alle Postfächer auf einem Postfachserver innerhalb eines bestimmten Zeitraums (bezeichnet als ein *Arbeitszyklus*) verarbeitet. Der Arbeitszyklus ist standardmäßig auf einen Tag festgelegt.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren des Assistenten für verwaltete Ordner mithilfe der Shell

In diesem Beispiel wird der Assistent für verwaltete Ordner so konfiguriert, dass alle Postfächer innerhalb eines Tags verarbeitet werden.

    Set-MailboxServer MyMailboxServer -ManagedFolderWorkCycle 1

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-MailboxServer](https://technet.microsoft.com/de-de/library/aa998651\(v=exchg.150\)).

## Woher weiß ich, dass der Vorgang erfolgreich war?

Zum Überprüfen, ob der Assistent für verwaltete Ordner erfolgreich konfiguriert wurde, verwenden Sie das Cmdlet [Get-MailboxServer](https://technet.microsoft.com/de-de/library/bb123539\(v=exchg.150\)), um den Parameter *ManagedFolderWorkCycle* zu prüfen.

Dieser Befehl ruft alle Postfachserver in der Organisation ab und gibt die Arbeitszykluseigenschaften des Assistenten für verwaltete Ordner von jedem Server in Tabellenformat zurück. Die Option *Auto* wird verwendet, um die Spaltenbreite automatisch anzupassen.

    Get-MailboxServer | Format-Table Name,ManagedFolderWorkCycle* -Auto

## Verwenden der Shell zum Starten des Assistenten für verwaltete Ordner

In diesem Beispiel wird eine sofortige Verarbeitung des Postfachs von Morris Cornejo durch den Assistenten für verwaltete Ordner ausgelöst.

    Start-ManagedFolderAssistant -Identity morris.cornejo@contoso.com

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Start-ManagedFolderAssistant](https://technet.microsoft.com/de-de/library/aa998864\(v=exchg.150\)).


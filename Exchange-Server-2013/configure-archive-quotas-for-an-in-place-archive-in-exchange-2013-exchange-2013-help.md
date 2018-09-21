---
title: 'Konfigurieren von Kontingenten für In-Situ-Archiv in Exchange 2013'
TOCTitle: Konfigurieren von Kontingenten für ein Compliance-Archiv (lokal)
ms:assetid: f10e77c7-e1d4-415a-bef9-cb3f00e74c34
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633489(v=EXCHG.150)
ms:contentKeyID: 50554938
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Kontingenten für ein Compliance-Archiv (lokal)

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-12-04_

Bei lokalen Bereitstellungen werden Compliance-Archive standardmäßig mit unbegrenzten Speicherkontingenten erstellt. Demzufolge müssen Sie die Eigenschaften eines Postfachs bearbeiten, um für das Archiv Speicherkontingente festzulegen. Sie können die folgenden Kontingente für ein Archiv festlegen:

  - **Archiv: Kontingent, ab dem eine Warnung ausgegeben wird**   Wenn ein Compliance-Archiv das angegebene Archivierungskontingent, ab dem eine Warnung ausgegeben wird, überschreitet, wird für den Exchange-Administrator ein Ereignis protokolliert, woraufhin der Postfachbenutzer eine Warnmeldung erhält.

  - **Archivierungskontingent**   Wenn ein Compliance-Archiv das angegebene Archivierungskontingent überschreitet, werden Nachrichten nicht mehr in das Archiv verschoben, woraufhin der Postfachbenutzer eine Warnmeldung erhält.

Weitere Informationen zu Compliance-Archiven finden Sie unter [In-Situ-Archivierung in Exchange 2013](in-place-archiving-in-exchange-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Über eine Dropdownliste mit festen Werten in der Exchange-Verwaltungskonsole können Sie das Archivierungskontingent und das Archivierungskontingent, ab dem eine Warnung ausgegeben wird, konfigurieren. Wenn Sie die Kontingente auf einen Wert festlegen möchten, der nicht in der Exchange-Verwaltungskonsole aufgeführt ist, verwenden Sie die Shell.

  - Legen Sie für das Archivierungskontingent, ab dem eine Warnung ausgegeben wird, einen niedrigeren Wert als für das Archivierungskontingent fest. Je nachdem, wie schnell das Archiv eines Benutzers anwächst, muss die Differenz zwischen dem Archivierungskontingent, ab dem eine Warnung ausgegeben wird, und dem Archivierungskontingent dem Benutzer genügend Zeit lassen, die entsprechenden Maßnahmen zu ergreifen. Dazu können beispielsweise das Löschen von Elementen aus dem Archiv oder das Auffordern des Administrators oder IT-Helpdesk zählen, das Archivierungskontingent zu erhöhen.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren des Archivierungskontingents und des Archivierungskontingents, ab dem eine Warnung ausgegeben wird, für ein Postfach mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**

2.  Wählen Sie in der Listenansicht ein Postfach aus,

3.  Klicken Sie im Detailbereich unter **Compliance-Archive** auf **Details anzeigen**.

4.  Wählen Sie in **Archivpostfach** in den Listen **Kontingentwert (GB)** und **Warnmeldung senden ab (GB)** die gewünschten Werte aus.

5.  Klicken Sie auf **OK**.

## Konfigurieren des Archivierungskontingents und des Archivierungskontingents, ab dem eine Warnung ausgegeben wird, für ein Postfach mithilfe der Shell

In diesem Beispiel wird das Archivierungskontingent des Postfachs von "Chris Ashton" auf 10 GB festgelegt. Danach erhält der Benutzer eine Warnmeldung, dass das Compliance-Archiv voll ist und er keine weiteren Elemente in das Archiv verschieben kann. Außerdem wird in diesem Beispiel das Archivierungskontingent, ab dem eine Warnung ausgegeben wird, auf 9,5 GB festgelegt. Danach erhält der Benutzer eine Warnmeldung, dass das Compliance-Kontingent beinahe voll ausgeschöpft ist.

```powershell
Set-Mailbox -Identity "Chris Ashton" -ArchiveQuota 10GB -ArchiveWarningQuota 9.5GB
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Aktivierung eines lokalen Archivs für ein vorhandenes Postfach zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**, und wählen Sie das gewünschte Postfach aus. Klicken Sie im Detailbereich unter **Compliance-Archive** auf **Details anzeigen**, und überprüfen Sie die Kontingenteinstellungen des Archivs.

  - Führen Sie in der Shell den folgenden Befehl aus, um Kontingentinformationen zum neuen Archiv anzuzeigen.
    
        Get-Mailbox <Name> | FL Name,Archive*Quota


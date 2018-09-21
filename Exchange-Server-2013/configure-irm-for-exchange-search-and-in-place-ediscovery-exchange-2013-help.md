---
title: 'Konfig. v. IRM für Exchange-Suche und In-Situ-eDiscovery: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren von IRM für Exchange-Suche und Compliance-eDiscovery
ms:assetid: d96790e9-93ad-4a56-b90f-2dbfa2f2073c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg588319(v=EXCHG.150)
ms:contentKeyID: 50476869
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren von IRM für Exchange-Suche und Compliance-eDiscovery

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-16_

In Microsoft Exchange Server 2013 können Sie die Verwaltung von Informationsrechten (Information Rights Management, IRM) so konfigurieren, dass Exchange-Suche IRM-geschützte Nachrichten indizieren kann.

Wenn Mitglieder der Rollengruppe "Discoveryverwaltung" eine [Compliance-eDiscovery](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)-Suche ausführen, werden IRM-geschützte Nachrichten in den Suchergebnissen zurückgegeben und in das Discoverypostfach kopiert, das in der Suche angegeben ist. Mitglieder der Rollengruppe "Discoveryverwaltung" können außerdem mit Outlook Web App auf die IRM-geschützten Nachrichten zugreifen, die als Ergebnis der Discoverysuche in das Discoverypostfach kopiert wurden.


> [!NOTE]
> Mitglieder der Rollengruppe "Discoveryverwaltung" können nicht auf IRM-geschützte Nachrichten zugreifen, die aus einem Discoverypostfach in ein anders Postfach oder in eine PST-Datei kopiert wurden. Auf IRM-geschützte Nachrichten in einem Discoverypostfach kann nur über Outlook Web App zugegriffen werden.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rechteschutz" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - IRM muss in Ihrer Exchange 2013-Organisation konfiguriert sein. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren von IRM für interne Nachrichten](enable-or-disable-irm-for-internal-messages-exchange-2013-help.md).

  - Das Verbundpostfach muss der Administratorengruppe für die Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS) hinzugefügt worden sein. Weitere Informationen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).

  - IRM kann nicht in der Exchange-Verwaltungskonsole für die Exchange-Suche und die Compliance-eDiscovery konfiguriert werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren von IRM für Exchange-Suche mithilfe der Shell

In diesem Beispiel wird IRM so konfiguriert, dass Exchange-Suche IRM-geschützte Nachrichten indizieren kann.


> [!NOTE]
> Standardmäßig ist der Parameter <EM>SearchEnabled</EM> auf <CODE>$true</CODE> festgelegt. Soll die Indizierung von IRM-geschützten Nachrichten deaktiviert werden, legen Sie ihn auf <CODE>$false</CODE> fest. Wenn die Indizierung von IRM-geschützten Nachrichten deaktiviert ist, werden diese nicht in Suchergebnissen zurückgegeben, wenn Benutzer ihre Postfächer durchsuchen oder Discovery-Manager die Compliance-eDiscovery verwenden.



```powershell
Set-IRMConfiguration -SearchEnabled $true
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Konfigurieren von IRM für die Compliance-eDiscovery mithilfe der Shell

In diesem Beispiel wird angegeben, dass Mitglieder der Rollengruppe "Discoveryverwaltung" auf IRM-geschützte Nachrichten zugreifen können, die sich im Discoverypostfach befinden.


> [!NOTE]
> Standardmäßig ist der Parameter <EM>EDiscoverySuperUserEnabled</EM> auf <CODE>$true</CODE> festgelegt. Soll der Zugriff auf IRM-geschützte Nachrichten für Mitglieder der Rollengruppe "Discoveryverwaltung" deaktiviert werden, legen Sie den Parameter auf <CODE>$false</CODE> fest.



```powershell
Set-IRMConfiguration -EDiscoverySuperUserEnabled $true
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Rufen Sie mithilfe des Cmdlets **Get-IRMConfigurtaion** die Informationen zur IRM-Konfiguration ab, um sich zu vergewissern, dass Sie IRM erfolgreich für die Exchange-Suche und die Compliance-eDiscovery konfiguriert haben. Ein Beispiel für das Abrufen der IRM-Konfiguration finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/e1821219-fe18-4642-a9c2-58eb0aadd61a\(exchg.150\)#examples) zu **Get-IRMConfiguration**.


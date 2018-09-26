---
title: 'Verwalten der Administratorüberwachungsprotokollierung: Exchange 2013 Help'
TOCTitle: Verwalten der Administratorüberwachungsprotokollierung
ms:assetid: 15c284c0-b8e6-42ca-9913-7c59fdb6885d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335109(v=EXCHG.150)
ms:contentKeyID: 50554800
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten der Administratorüberwachungsprotokollierung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-05-17_

Die Administrator-Überwachungsprotokollierung in Microsoft Exchange Server 2013 ermöglicht es Ihnen, bei jeder Ausführung eines angegebenen Cmdlets einen Protokolleintrag zu erstellen. In Protokolleinträgen finden Sie Informationen darüber, welches Cmdlet ausgeführt wurde, welche Parameter verwendet wurden, wer das Cmdlet ausgeführt hat und welche Objekte betroffen sind. Weitere Informationen zur Administrator-Überwachungsprotokollierung finden Sie unter [Administratorüberwachungsprotokollierung](administrator-audit-logging-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: Weniger als 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Administrator-Überwachungsprotokollierung" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Die Administrator-Überwachungsprotokollierung verwendet die Active Directory-Replikation für die Replikation von Konfigurationseinstellungen, die Sie für die Domänencontroller in Ihrer Organisation festlegen. Je nach den Replikationseinstellungen werden von Ihnen vorgenommene Änderungen möglicherweise nicht sofort auf alle Exchange 2013-Server in Ihrer Organisation angewendet.

  - Änderungen an der Überwachungsprotokollkonfiguration werden alle 60 Minuten auf Computern aktualisiert, deren Shell zum Zeitpunkt einer Konfigurationsänderung geöffnet ist. Wenn Sie die Änderungen sofort anwenden möchten, schließen Sie die Shell auf den einzelnen Computern, und öffnen Sie sie wieder.

  - Es dauert bis zu 15 Minuten nach dem Ausführen eines Befehls, bis dieser in den Suchergebnissen in des Überwachungsprotokolls angezeigt wird. Der Grund hierfür liegt darin, dass Überwachungsprotokolleinträge indiziert werden müssen, bevor sie durchsucht werden können. Wenn ein Befehl nicht im Administratorüberwachungsprotokoll aufgeführt wird, warten Sie einige Minuten, und führen Sie dann die Suche erneut aus.

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Angeben der zu überwachenden Cmdlets

Standardmäßig wird bei der Überwachungsprotokollierung für jedes ausgeführt Cmdlet ein Protokolleintrag erstellt. Wenn Sie die Überwachungsprotokollierung zum ersten Mal aktivieren und dieses Verhalten wünschen, müssen Sie die Überwachungsliste für Cmdlets nicht ändern. Wenn Sie zuvor zu überwachende Cmdlets angegeben haben und jetzt alle Cmdlets überwachen möchten, können Sie das Platzhalterzeichen (\*) im Parameter *AdminAuditLogCmdlets* für das Cmdlet **Set-AdminAuditLogConfig** wie im folgenden Befehl gezeigt verwenden.

```powershell
    Set-AdminAuditLogConfig -AdminAuditLogCmdlets *
```

Sie können angeben, welche Cmdlets überwacht werden sollen, indem Sie mit dem Parameter *AdminAuditLogCmdlets* eine Liste von Cmdlets bereitstellen. In der Liste der zu überwachenden Cmdlets können Sie einzelne Cmdlets, Cmdlets mit Sternchen (\*) oder eine Kombination bereitstellen. Die Einträge in der Liste sind durch Kommas getrennt. Folgende Werte sind gültig:

  - `New-Mailbox`

  - `*TransportRule`

  - `*Management*`

  - `Set-Transport*`

In diesem Beispiel werden die Cmdlets in der obigen Liste überwacht.

```powershell
    Set-AdminAuditLogConfig -AdminAuditLogCmdlets New-Mailbox, *TransportRule, *Management*, Set-Transport*
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-AdminAuditLogConfig](https://technet.microsoft.com/de-de/library/dd298169\(v=exchg.150\)).

## Angeben der zu überwachenden Parameter

Standardmäßig wird bei der Überwachungsprotokollierung für jedes ausgeführte Cmdlet ein Protokolleintrag erstellt, unabhängig von den angegebenen Parametern. Wenn Sie die Überwachungsprotokollierung zum ersten Mal aktivieren und dieses Verhalten wünschen, müssen Sie die Überwachungsliste für Parameter nicht ändern. Wenn Sie zuvor zu überwachende Parameter angegeben haben und jetzt alle Parameter überwachen möchten, können Sie das Platzhalterzeichen (\*) im Parameter *AdminAuditLogParameters* für das Cmdlet **Set-AdminAuditLogConfig** wie im folgenden Befehl gezeigt verwenden.

```powershell
    Set-AdminAuditLogConfig -AdminAuditLogParameters *
```

Mit dem Parameter *AdminAuditLogParameters* kann festgelegt werden, welche Parameter überwacht werden. In der Liste der zu überwachenden Parameter können Sie einzelne Parameter, Parameter mit Sternchen (\*) oder eine Kombination bereitstellen. Die Einträge in der Liste sind durch Kommas getrennt. Folgende Werte sind gültig:

  - `Database`

  - `*Address*`

  - `Custom*`

  - `*Region`


> [!NOTE]
> Damit bei der Ausführung eines Befehls ein Überwachungsprotokolleintrag erstellt wird, muss der Befehl vorhandene Parameter oder mit dem Parameter <EM>AdminAuditLogCmdlets</EM> angegebene Cmdlets enthalten.



In diesem Beispiel werden die Parameter in der obigen Liste überwacht.

```powershell
    Set-AdminAuditLogConfig -AdminAuditLogParameters Database, *Address*, Custom*, *Region
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-AdminAuditLogConfig](https://technet.microsoft.com/de-de/library/dd298169\(v=exchg.150\)).

## Angeben der Verfallszeit für Überwachungsprotokolle

Die Verfallszeit für Überwachungsprotokolle bestimmt, wie lange Überwachungsprotokolleinträge gespeichert werden. Überschreitet ein Protokolleintrag die Verfallszeit, wird er gelöscht. Der Standardwert beträgt 90 Tage.

Sie können die Anzahl der Tage, Stunden, Minuten und Sekunden angeben, die Überwachungsprotokolleinträge gespeichert werden. Verwenden Sie zum Angeben eines Werts das Format "dd.hh.mm:ss", wobei Folgendes gilt:

  - **dd**   Die Anzahl der Tage, die der Überwachungsprotokolleintrag gespeichert werden soll

  - **hh**   Die Anzahl der Stunden, die der Überwachungsprotokolleintrag gespeichert werden soll

  - **mm**   Die Anzahl der Minuten, die der Überwachungsprotokolleintrag gespeichert werden soll

  - **ss**   Die Anzahl der Sekunden, die der Überwachungsprotokolleintrag gespeichert werden soll


> [!WARNING]
> Sie können die Verfallszeit für Überwachungsprotokolle auch auf einen Wert unter der derzeitigen Verfallszeit festlegen. In diesem Fall wird jeder Überwachungsprotokolleintrag, der die neue Verfallszeit überschreitet, gelöscht.<BR>Wenn Sie die Verfallszeit auf 0 festlegen, löscht Exchange alle Einträge im Überwachungsprotokoll.<BR>Es wird empfohlen, nur äußerst vertrauenswürdigen Benutzern die Berechtigung zur Konfiguration der Verfallszeit für Überwachungsprotokolle zu erteilen.



In diesem Beispiel wird eine Verfallszeit von zwei Jahren und sechs Monaten angegeben.

```powershell
Set-AdminAuditLogConfig -AdminAuditLogAgeLimit 913.00:00:00
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-AdminAuditLogConfig](https://technet.microsoft.com/de-de/library/dd298169\(v=exchg.150\)).

## Aktivieren oder Deaktivieren der Protokollierung von Test-Cmdlets

Cmdlets, die mit dem Verb **Test** beginnen, werden nicht standardmäßig protokolliert. Der Grund dafür ist, dass **Test**-Cmdlets eine erhebliche Datenmenge in kurzer Zeit generieren. Aktivieren Sie die Protokollierung von **Test**-Cmdlets nur für kurze Zeit.

Mit diesem Befehl können Sie die Protokollierung von **Test**-Cmdlets aktivieren.

```powershell
Set-AdminAuditLogConfig -TestCmdletLoggingEnabled $True
```

Mit diesem Befehl können Sie die Protokollierung von **Test**-Cmdlets deaktivieren.

```powershell
Set-AdminAuditLogConfig -TestCmdletLoggingEnabled $False
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-AdminAuditLogConfig](https://technet.microsoft.com/de-de/library/dd298169\(v=exchg.150\)).

## Deaktivieren der Administrator-Überwachungsprotokollierung

Verwenden Sie den folgenden Befehl, um die Administrator-Überwachungsprotokollierung zu deaktivieren.

```powershell
Set-AdminAuditLogConfig -AdminAuditLogEnabled $False
```

## Aktivieren der Administratorüberwachungsprotokollierung

Verwenden Sie den folgenden Befehl, um die Administrator-Überwachungsprotokollierung zu aktivieren.

```powershell
Set-AdminAuditLogConfig -AdminAuditLogEnabled $True
```

## Anzeigen der Einstellungen für die Administrator-Überwachungsprotokollierung

Verwenden Sie den folgenden Befehl, um die für Ihre Organisation konfigurierten Einstellungen für die Administrator-Überwachungsprotokollierung anzuzeigen.

```powershell
Get-AdminAuditLogConfig
```


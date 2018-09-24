---
title: 'Entfernen von Postfach- und Clientzugriffs-Servern aus einem SIP-URI-Wählplan'
TOCTitle: Entfernen von Postfach- und Clientzugriffs-Servern aus einem SIP-URI-Wählplan
ms:assetid: 367441e1-1a0f-42c8-9fa8-8abe80b3d015
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997238(v=EXCHG.150)
ms:contentKeyID: 54652683
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Entfernen von Postfach- und Clientzugriffs-Servern aus einem SIP-URI-Wählplan

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-16_

Sie können Clientzugriffs- und Postfachserver aus SIP-URI-Wählplänen entfernen. Wenn Sie Microsoft Lync Server bereitstellen, müssen Sie den für Lync Server erstellten SIP-URI-Wählplänen alle Clientzugriffs- und Postfachserver manuell hinzufügen, damit ausgehende Anrufe einwandfrei funktionieren. Sie müssen jedoch möglicherweise einen Clientzugriffs- oder Postfachserver aus Ihrer Lync -Bereitstellung entfernen, beispielsweise dann, wenn Sie Wartungsarbeiten vornehmen oder den Server in den Offline-Betrieb wechseln.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein SIP-URI-UM-Wählplan erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Mit der Exchange-Verwaltungskonsole einen Postfachserver aus einem SIP-URI-Wählplan entfernen.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Postfachserver aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Suchen Sie unter **UM-Diensteinstellungen** \> **Verbundene Wählpläne** den zu entfernenden SIP-URI-Wählplan, klicken Sie auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), und klicken Sie dann auf **Speichern**. Möchten Sie mehrere SIP-URI-Wählpläne entfernen, halten Sie die STRG-Taste gedrückt, wählen Sie die zu entfernenden Wählpläne aus, und klicken Sie auf **Speichern**.

## Verwenden Sie die Shell zum Entfernen eines Postfachservers aus einem SIP-URI-Wählplan.

In diesem Beispiel wird der Postfachserver `MyMailboxServer` aus einem SIP-URI-Wählplan mit der Bezeichnung `MySIPDialPlan` entfernt.

```powershell
$dp= Get-UMDialPlan "MySIPDialPlan"
$s=Get-UMService MyMailboxServer
$s.dialplans-=$dp.identity
Set-UMService -id MyMailboxServer -dialplans:$s.dialplans
```

In diesem Beispiel sind drei SIP-UIR-Wählpläne vorhanden: SipDP1, SipDP2 und SipDP3. In diesem Beispiel wird der Postfachserver mit dem Namen `MyMailboxServer` aus dem Wählplan "SipDP3" entfernt.

```powershell
Set-UMService -id MyMailboxServer -DialPlans SipDP1,SipDP2
```

In diesem Beispiel sind zwei SIP-UIR-Wählpläne vorhanden: SipDP1 und SipDP2. In diesem Beispiel wird der Postfachserver mit dem Namen `MyMailboxServer` aus dem Wählplan "SipDP2" entfernt.

```powershell
Set-UMService -id MyMailboxServer -DialPlans SipDP1
```

In diesem Beispiel wird der Postfachserver mit dem Namen `MyMailboxServer` aus allen SIP-Wählplänen entfernt.

```powershell
Set-UMService -id MyUMServer -DialPlans $null
```

## Entfernen Sie mit der Exchange-Verwaltungskonsole einen Clientzugriffsserver aus einem SIP-URI-Wählplan.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Clientzugriffsserver aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Suchen Sie unter **UM-Anrufroutereinstellungen** \> **Verbundene Wählpläne** den zu entfernenden SIP-URI-Wählplan, klicken Sie auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), und klicken Sie dann auf **Speichern**. Möchten Sie mehrere SIP-URI-Wählpläne entfernen, halten Sie die STRG-Taste gedrückt, wählen Sie die zu entfernenden Wählpläne aus, und klicken Sie auf **Speichern**.

## Entfernen Sie mit der Shell einen Clientzugriffsserver aus einem SIP-URI-Wählplan.

In diesem Beispiel wird der Clientzugriffsserver `MyClientAccessServer` aus einem SIP-URI-Wählplan mit der Bezeichnung `MySIPDialPlan` entfernt.

```powershell
$dp= Get-UMDialPlan "MySIPDialPlan"
$s=Get-UMCallRouterSettings MyClientAccessServer
$s.dialplans-=$dp.identity
Set-UMCallRouterSettings -id MyClientAccessServer -dialplans:$s.dialplans
```

In diesem Beispiel sind drei SIP-UIR-Wählpläne vorhanden: SipDP1, SipDP2 und SipDP3. In diesem Beispiel wird der Clientzugriffsserver mit dem Namen `MyClientAccessServer` aus dem Wählplan "SipDP3" entfernt.

```powershell
Set-UMCallRouterSettings -id MyClientAccessServer -DialPlans SipDP1,SipDP2
```

In diesem Beispiel sind zwei SIP-UIR-Wählpläne vorhanden: SipDP1 und SipDP2. In diesem Beispiel wird der Clientzugriffsserver mit dem Namen `MyClientAccessServer` aus dem Wählplan "SipDP2" entfernt.

```powershell
Set-UMCallRouterSettings -id MyClientAccessServer -DialPlans SipDP1
```

In diesem Beispiel wird der Clientzugriffsserver mit dem Namen `MyClientAccessServer` aus allen SIP-Wählplänen entfernt.

```powershell
Set-UMCallRouterSettings -id MyClientAccessServer -DialPlans $null
```
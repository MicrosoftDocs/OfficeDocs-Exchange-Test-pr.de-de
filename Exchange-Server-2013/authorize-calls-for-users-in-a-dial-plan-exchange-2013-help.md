---
title: 'Autorisieren von Anrufen für Benutzer in einem Wählplan: Exchange Online Help'
TOCTitle: Autorisieren von Anrufen für Benutzer in einem Wählplan
ms:assetid: 7c7fd0c4-4001-408e-b352-c49bac9f78cc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb691175(v=EXCHG.150)
ms:contentKeyID: 51409316
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Autorisieren von Anrufen für Benutzer in einem Wählplan

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-21_

Sie können Wählautorisierungen für einen UM-Wählplan (Unified Messaging) aktivieren. Wählautorisierungen für einen Wählplan dienen zum Unterbinden, dass nicht authentifizierte Outlook Voice Access-Benutzer Fern- oder Auslandsgespräche bzw. *Outdialing*-Telefonate führen. Outdialing erfolgt, wenn Unified Messaging einen ausgehenden Anruf für einen Benutzer einleitet, nachdem dieser sich bei einer Outlook Voice Access-Telefonnummer eingewählt hat, die für einen UM-Wählplan konfiguriert ist. Wenn Sie eine Einstellung für einen UM-Wählplan konfigurieren, gilt diese für alle nicht authentifizierten Benutzer, die sich bei einer Outlook Voice Access-Nummer einwählen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Outdialing finden Sie unter [Ermöglichen, dass Benutzer Anrufe Verfahren stellen](allowing-users-to-make-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Bestätigen Sie, bevor Sie dieses Verfahren durchführen, dass nationale und internationale Wählregeln für einen UM-Wählplan erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen von Wählregeln für Benutzer](create-dialing-rules-for-users-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Aktivieren von Wählautorisierungen für nationale Regelgruppen in einem UM-Wählplan

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

3.  Klicken Sie auf der Seite **UM-Wählplan** \> **Wählautorisierung** unter **Autorisierte nationale Wählregelgruppen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie auf der Seite **Wählregelgruppen für Zulassen auswählen** die Wählregelgruppe aus, klicken Sie auf **OK** und dann auf **Speichern**.

## Verwenden der Exchange-Verwaltungskonsole zum Aktivieren von Wählautorisierungen für internationale Wählregelgruppen in einem UM-Wählplan

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

3.  Klicken Sie auf der Seite **UM-Wählplan** \> **Wählautorisierung** unter **Autorisierte internationale Wählregelgruppen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie auf der Seite **Wählregelgruppen für Zulassen auswählen** die Wählregelgruppe aus, klicken Sie auf **OK** und dann auf **Speichern**.

## Verwenden der Shell zum Aktivieren von regionalen/nationalen und internationalen Wählautorisierungen in einem UM-Wählplan

In diesem Beispiel werden die Wählautorisierungen "InCountry/RegionGroup1", "InCountry/RegionGroup2", "InternationalGroup1" und "InternationalGroup2" für den UM-Wählplan `MyUMDialPlan` aktiviert.

    Set-UMDialPlan -Identity MyUMDialPlan -AllowedInCountryOrRegionGroups InCountry/RegionGroup1,InCountry/RegionGroup2 -AllowedInternationalGroups InternationalGroup1,InternationalGroup2


---
title: 'Autorisieren von Aufrufen für automatische Telefonzentralen Anrufer: Exchange Online Help'
TOCTitle: Autorisieren von Aufrufen für automatische Telefonzentralen Anrufer
ms:assetid: c6c94fad-64df-44aa-a198-980f017ef716
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb691238(v=EXCHG.150)
ms:contentKeyID: 51409340
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Autorisieren von Aufrufen für automatische Telefonzentralen Anrufer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Sie können Wählautorisierungen für eine automatische Unified Messaging-Telefonzentrale (UM) aktivieren. Wählautorisierungen für eine automatische Telefonzentrale dienen zum Unterbinden, dass Benutzer, die sich in die automatische Telefonzentrale einwählen, Fern- oder Auslandsgespräche bzw. *Outdialing*-Telefonate führen. Outdialing erfolgt, wenn Unified Messaging einen ausgehenden Anruf für einen Benutzer tätigt, nachdem dieser sich bei einer Telefonnummer eingewählt hat, die für eine automatische UM-Telefonzentrale konfiguriert ist.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Outdialing finden Sie unter [Ermöglichen, dass Benutzer Anrufe Verfahren stellen](allowing-users-to-make-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Bestätigen Sie, bevor Sie diese Verfahren durchführen, dass regionale/nationale und internationale Wählregeln für einen UM-Wählplan erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen von Wählregeln für Benutzer](create-dialing-rules-for-users-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren von Wählautorisierungen für eine automatische UM-Telefonzentrale für nationale/regionsinterne Regelgruppen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie eine Wählautorisierung erstellen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Wählautorisierung** unter **Autorisierte nationale Wählregelgruppen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie auf der Seite **Wählregelgruppen für Zulassen auswählen** die Wählregelgruppe aus, klicken Sie auf **OK** und dann auf **Speichern**.

## Aktivieren von Wählautorisierungen für eine automatische UM-Telefonzentrale für internationale Regelgruppen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie eine Wählautorisierung erstellen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Wählautorisierung** unter **Autorisierte internationale Wählregelgruppen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie auf der Seite **Wählregelgruppen für Zulassen auswählen** die Wählregelgruppe aus, klicken Sie auf **OK** und dann auf **Speichern**.

## Aktivieren von nationalen/regionsinternen und internationalen Wählautorisierungen für eine automatische UM-Telefonzentrale mithilfe der Shell

In diesem Beispiel werden die Wählautorisierungen "InCountry/RegionGroup1", "InCountry/RegionGroup2", "InternationalGroup1" und "InternationalGroup2" für die automatische UM-Telefonzentrale `MyUMAutoAttendant` aktiviert.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -AllowedInCountryOrRegionGroups InCountry/RegionGroup1,InCountry/RegionGroup2 -AllowedInternationalGroups InternationalGroup1,InternationalGroup2


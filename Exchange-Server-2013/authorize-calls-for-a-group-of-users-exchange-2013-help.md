---
title: 'Autorisieren von Anrufen für eine Gruppe von Benutzern: Exchange Online Help'
TOCTitle: Autorisieren von Anrufen für eine Gruppe von Benutzern
ms:assetid: 7fc36757-868c-4bde-b793-6ae630da155c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232099(v=EXCHG.150)
ms:contentKeyID: 51409307
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Autorisieren von Anrufen für eine Gruppe von Benutzern

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Sie können Wählautorisierungen für eine UM-Postfachrichtlinie (Unified Messaging) aktivieren. Wählautorisierungen für eine Postfachrichtlinie dienen zum Unterbinden, dass authentifizierte Outlook Voice Access-Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, nationale bzw. internationale oder *Outdialing*-Telefonate führen. Outdialing erfolgt, wenn Unified Messaging einen ausgehenden Anruf für einen Benutzer einleitet, nachdem dieser sich bei einer Outlook Voice Access-Telefonnummer eingewählt hat, die für einen UM-Wählplan konfiguriert ist. Die in einer UM-Postfachrichtlinie konfigurierten Einstellungen gelten für alle UM-aktivierten Benutzer, die der UM-Postfachrichtlinie zugeordnet sind.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Outdialing finden Sie unter [Ermöglichen, dass Benutzer Anrufe Verfahren stellen](allowing-users-to-make-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Bestätigen Sie, bevor Sie diese Verfahren durchführen, dass regionale/nationale und internationale Wählregeln für einen UM-Wählplan erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen von Wählregeln für Benutzer](https://technet.microsoft.com/de-de/library/JJ898502(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Aktivieren von Wählautorisierungen für regionale/nationale Wählregelgruppen in einer UM-Postfachrichtlinie

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** eine UM-Postfachrichtlinie aus, für die Sie eine Wählautorisierung erstellen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Postfachrichtlinie** \> **Wählautorisierung** unter **Autorisierte nationale Wählregelgruppen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie auf der Seite **Wählregelgruppen für Zulassen auswählen** die Wählregelgruppe aus, klicken Sie auf **OK** und dann auf **Speichern**.

## Verwenden der Exchange-Verwaltungskonsole zum Aktivieren von Wählautorisierungen für internationale Wählregelgruppen in einer UM-Postfachrichtlinie

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** eine UM-Postfachrichtlinie aus, für die Sie eine Wählautorisierung erstellen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Postfachrichtlinie** \> **Wählautorisierung** unter **Autorisierte internationale Wählregelgruppen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Wählen Sie auf der Seite **Wählregelgruppen für Zulassen auswählen** die Wählregelgruppe aus, klicken Sie auf **OK** und dann auf **Speichern**.

## Verwenden der Shell zum Aktivieren von regionalen/nationalen oder internationalen Wählautorisierungen in einer UM-Postfachrichtlinie

In diesem Beispiel werden die Wählautorisierungen "InCountry/RegionGroup1", "InCountry/RegionGroup2", "InternationalGroup1" und "InternationalGroup2" in der UM-Postfachrichtlinie `MyUMMailboxPolicy` aktiviert.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -AllowedInCountryOrRegionGroups InCountry/RegionGroup1,InCountry/RegionGroup2 -AllowedInternationalGroups InternationalGroup1,InternationalGroup2


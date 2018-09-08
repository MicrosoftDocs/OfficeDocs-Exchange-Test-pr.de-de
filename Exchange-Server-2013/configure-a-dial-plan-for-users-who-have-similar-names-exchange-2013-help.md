---
title: 'Konfig. eines Wählplans für Benutzer mit ähnl. Namen: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren eines Wählplans für Benutzer mit ähnliche Namen
ms:assetid: 14783f45-95f5-49de-8215-0a3aef7dc034
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb266943(v=EXCHG.150)
ms:contentKeyID: 51409267
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren eines Wählplans für Benutzer mit ähnliche Namen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Sie können einen UM-Wählplan (Unified Messaging) zum Angeben von Informationen konfigurieren, die für Anrufer bereitgestellt werden, wenn Benutzer denselben oder ähnliche Namen besitzen. Anhand dieser Einstellung unterscheidet UM zwischen Benutzern mit demselben oder ähnlichen Namen und stellt diese Information den Anrufern bereit. Wenn ein Anrufer oder ein Benutzer von Outlook Voice Access aufgefordert wird, Buchstaben einzugeben, um einen bestimmten Benutzer zu suchen, entsprechen manchmal mehrere Namen der Eingabe des Anrufers. Anhand einer der verfügbaren Optionen können Sie dem Anrufer weitere Informationen bereitstellen und ihm beim Auffinden des gewünschten Benutzers behilflich sein.

Diese Einstellung kann sowohl in UM-Wählplänen als auch in automatischen UM-Telefonzentralen festgelegt werden. Wenn eine automatische UM-Telefonzentrale erstellt wird, übernimmt diese die Einstellung von dem Wählplan der zugehörigen automatischen Telefonzentrale. Standardmäßig ist diese Einstellung nicht für Wählpläne konfiguriert, sodass Anrufern keine weiteren Informationen zum Auffinden des richtigen Benutzers bereitgestellt werden.


> [!NOTE]
> Damit die Informationen für Benutzer mit ähnlichen Namen ordnungsgemäß verwendet werden können, müssen Sie den Titel, die Abteilung und Standortinformationen für die Empfänger in Ihrer Microsoft Exchange-Organisation bereitstellen.



Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren eines UM-Wählplans für Benutzer mit ähnlichen Namen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren** \> **Weiterleitung und Suche**, und wählen Sie unter **Informationen, die für Benutzer mit demselben Namen eingeschlossen werden** eine der folgenden Optionen aus:
    
      - **Titel**   Der Wählplan enthält die Titel der einzelnen Benutzer, wenn zwei oder mehr Benutzer mit ähnlichen Namen gefunden werden.
    
      - **Abteilung**   Der Wählplan enthält die Abteilungen der einzelnen Benutzer, wenn zwei oder mehr Benutzer mit ähnlichen Namen gefunden werden.
    
      - **Ort**   Der Wählplan enthält die Standorte der einzelnen Benutzer, wenn zwei oder mehr Benutzer mit ähnlichen Namen gefunden werden.
    
      - **Keine**   Der Wählplan umfasst keine weiteren Informationen zu Benutzern mit ähnlichen Namen. Auch wenn dies der Standardeinstellung entspricht, empfiehlt es sich, eine der verfügbaren Optionen für Anrufer einzubeziehen. Andernfalls können Anrufer nicht zwischen mehreren Benutzern mit ähnlichen Namen unterscheiden.
    
      - **Ansage für Alias**   Der Anrufer wird vom Wählplan zur Angabe des Alias des Benutzers aufgefordert. Ein Alias ist der Teil der E-Mail- oder SMTP-Adresse des Benutzers, der sich vor dem (@)-Symbol befindet.

3.  Klicken Sie auf **Speichern**.

## Konfigurieren eines UM-Wählplans für Benutzer mit ähnlichen Namen mithilfe der Shell

In diesem Beispiel werden die Informationen zu Benutzern mit ähnlichen Namen in einem UM-Wählplan namens `MyDialPlan` so festgelegt, dass zur Eingabe des Benutzeralias aufgefordert wird.

    Set-UMDialplan -Identity MyDialPlan -MatchedNameSelectionMethod PromptForAlias

In diesem Beispiel werden die Informationen zu Benutzern mit ähnlichen Namen in einem UM-Wählplan namens `MyDialPlan` auf die Abteilung festgelegt.

    Set-UMDialplan -Identity MyDialPlan -MatchedNameSelectionMethod Department

In diesem Beispiel werden die Informationen zu Benutzern mit ähnlichen Namen in einem UM-Wählplan namens `MyDialPlan` auf den Standort festgelegt.

    Set-UMDialplan -Identity MyDialPlan -MatchedNameSelectionMethod Location


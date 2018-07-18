---
title: 'Konfigurieren einer automatischen Telefonzentrale für Benutzer mit ähnlichen Namen: Exchange Online Help'
TOCTitle: Konfigurieren einer automatischen Telefonzentrale für Benutzer mit ähnlichen Namen
ms:assetid: 2e7318a0-67f9-4d7b-8300-5f0ef77656a8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997135(v=EXCHG.150)
ms:contentKeyID: 52062682
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren einer automatischen Telefonzentrale für Benutzer mit ähnlichen Namen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-12-16_

In den Optionen **Zugriff auf Adressbuch und Vermittlungsstelle** der automatischen Telefonzentrale können Sie die Methode konfigurieren, die für Benutzer mit ähnlichen Namen verwendet wird, oder Sie können die Standardeinstellung der automatischen Telefonzentrale beibehalten und diese Einstellung in dem Wählplan konfigurieren, der der automatischen Telefonzentrale zugeordnet ist. Standardmäßig kann eine automatische Telefonzentrale zwischen mehreren Benutzern mit demselben oder ähnlichen Namen unterscheiden, weil die Standardeinstellung der automatischen Telefonzentrale **Vererbung von Wählplan** lautet.


> [!NOTE]
> Damit die Informationen für Benutzer mit ähnlichen Namen ordnungsgemäß verwendet werden können, müssen Sie den Titel, die Abteilung und Standortinformationen für die Empfänger in Ihrer Microsoft Exchange-Organisation bereitstellen.



Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren einer automatischen UM-Telefonzentrale für Benutzer mit ähnlichen Namen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** auf **Zugriff auf Adressbuch und Vermittlungsstelle**, und wählen Sie unter **Informationen, die für Benutzer mit demselben Namen eingeschlossen werden** eine der folgenden Optionen aus:
    
      - **Titel**   Die automatische Telefonzentrale fügt bei der Auflistung der Übereinstimmungen den Titel des Benutzers hinzu.
    
      - **Abteilung**   Die automatische Telefonzentrale fügt bei der Auflistung der Übereinstimmungen die Abteilung des Benutzers hinzu.
    
      - **Ort**   Die automatische Telefonzentrale fügt bei der Auflistung der Übereinstimmungen den Ort jedes Benutzers hinzu.
    
      - **Keine**   Die automatische Telefonzentrale stellt bei der Auflistung der Übereinstimmungen keine zusätzlichen Informationen bereit.
    
      - **Ansage für Alias**   Der Anrufer wird von der automatischen Telefonzentrale zur Angabe des Alias des Benutzers aufgefordert.
    
      - **Vererbung von Wähleinstellungen**   Die automatische Telefonzentrale verwendet die Standardeinstellung aus den Wähleinstellungen, die der automatischen Telefonzentrale zugeordnet sind.

4.  Klicken Sie auf **Speichern**.

## Konfigurieren einer automatischen UM-Telefonzentrale für Benutzer mit ähnlichen Namen mithilfe der Shell

In diesem Beispiel werden die Informationen, die bei Benutzern mit ähnlichen Namen bereitgestellt werden, für eine automatische UM-Telefonzentrale namens `MyUMAutoAttendant` so eingestellt, dass nach einem Alias gefragt wird.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -MatchedNameSelectionMethod PromptForAlias

In diesem Beispiel werden die Informationen, die bei Benutzern mit ähnlichen Namen bereitgestellt werden, für die automatische UM-Telefonzentrale `MyUMAutoAttendant` auf den Titel der Benutzer festgelegt. Es werden Namenssuchen ermöglicht, und Anrufer, die sich in die automatische Telefonzentrale einwählen, können die Sternchen-Taste (\*) drücken, um die Outlook Voice Access-Begrüßung zu hören.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -MatchedNameSelectionMethod Title -NameLookupEnabled $true -StarOutToDialPlanEnabled $true


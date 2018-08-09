---
title: 'Auswählen der Sprache für automatische Telefonzentrale: Exchange 2013-Hilfe'
TOCTitle: Auswählen der Sprache für eine automatische Telefonzentrale
ms:assetid: 3a1c1ec0-c726-41fb-a294-59faab205609
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997306(v=EXCHG.150)
ms:contentKeyID: 50554773
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Auswählen der Sprache für eine automatische Telefonzentrale

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können die Einstellung der Standardansagesprache für eine automatische Unified Messaging-Telefonzentrale (UM) konfigurieren. Mit der für eine automatische UM-Telefonzentrale verfügbaren Spracheinstellung können Sie die Standardansagesprache für die automatische Telefonzentrale konfigurieren. Wenn Sie die Standardsystemansagen für die automatische Telefonzentrale verwenden, ist dies die Sprache, die ein Anrufer hört, wenn die automatische Telefonzentrale den eingehenden Anruf beantwortet. Diese Spracheinstellung hat nur Auswirkungen auf die Standardsystemansagen, die verfügbar sind, nachdem Sie den Postfachserver mit dem Microsoft Exchange Unified Messaging-Dienst installiert haben. Diese Einstellung wirkt sich nicht auf benutzerdefinierte Ansagen aus, die für eine automatische Telefonzentrale konfiguriert wurden. Die verfügbaren Sprachen beruhen auf den Unified Messaging-Sprachpaketen, die auf dem Postfachserver installiert sind.

Für jede automatische Telefonzentrale, die Sie erstellen, wird zunächst als Standardsprache Englisch (en-US) verwendet. Das Sprachpaket für Englisch (en-US) wird in allen Versionen von Microsoft Exchange 2013 standardmäßig installiert und kann nicht entfernt werden. Falls Sie eine andere Sprache, etwa Deutsch (de-DE), auswählen möchten, müssen Sie zunächst die EXE-Datei für das deutsche UM-Sprachpaket von der Seite [Exchange Server 2013 UM Language Packs - Deutsch](https://go.microsoft.com/fwlink/?linkid=266542) herunterladen und dann das UM-Sprachpaket mithilfe der Installationsdatei "UMLanguagePack.de-de.exe" auf dem Postfachserver installieren. Nach der Installation des UM-Sprachpakets können Sie eine andere Sprache als Englisch (en-US) als Standardsprache für automatische UM-Telefonzentralen festlegen.

Weitere Informationen zu Aufgaben im Zusammenhang mit UM-Sprachen finden Sie unter [UM-Sprachen, -Telefonansagen und -Begrüßungen – Verfahren](um-languages-prompts-and-greetings-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Standardspracheinstellung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Wählen Sie auf der Seite **Allgemein** unter **Sprache für automatisierte Sprachschnittstelle** aus der Dropdownliste die erforderliche Sprache aus.

5.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu übernehmen.

## Konfigurieren der Standardspracheinstellung mithilfe der Shell

In diesem Beispiel wird die Standardsprache für die automatische UM-Telefonzentrale `MyUMAutoAttendant` auf Englisch (Großbritannien) eingestelt.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -Language en-GB

In diesem Beispiel wird die Standardsprache für die automatische UM-Telefonzentrale `MyUMAutoAttendant` auf Deutsch eingestelt.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -Language de-DE


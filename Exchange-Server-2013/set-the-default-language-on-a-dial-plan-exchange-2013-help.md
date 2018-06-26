---
title: 'Festlegen der Standardsprache für einen Wählplan: Exchange 2013 Help'
TOCTitle: Festlegen der Standardsprache für einen Wählplan
ms:assetid: 7a1d2e7e-4053-40af-9ec1-ec714df12ad4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998914(v=EXCHG.150)
ms:contentKeyID: 50554848
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Festlegen der Standardsprache für einen Wählplan

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Sie können die Standardsprache für einen UM-Wählplan (Unified Messaging) festlegen. Für alle Wählpläne, die Sie erstellen, wird als Standardsprache Englisch (en-US) verwendet. Das Sprachpaket Englisch (en-US) wird in allen Versionen von Microsoft Exchange Server 2013 installiert und kann nicht entfernt werden.

Falls Sie eine andere Sprache, etwa Deutsch (de-DE), auswählen möchten, müssen Sie zunächst das deutsche Unified Messaging-Sprachpaket von der Seite [Exchange Server 2013 UM Language Packs - Deutsch](https://go.microsoft.com/fwlink/p/?linkid=266542) herunterladen und dann das UM-Sprachpaket mithilfe der ausführbaren Installationsdatei (UMLanguagePack.de-de.exe) auf dem Postfachserver installieren. Nach der Installation des UM-Sprachpakets können Sie eine andere Sprache als Englisch (en-US) als Standardsprache für UM-Wählpläne einrichten.

Weitere Informationen zu Aufgaben im Zusammenhang mit UM-Sprachen finden Sie unter [UM-Sprachen, -Telefonansagen und -Begrüßungen – Verfahren](um-languages-prompts-and-greetings-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Konfigurieren der Standardsprache für einen UM-Wählplan

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Wählen Sie auf der Seite **Einstellungen** unter **Audiosprache** in der Dropdownliste die gewünschte Sprache aus.

5.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu übernehmen.

## Verwenden der Shell zum Konfigurieren der Standardsprache für einen UM-Wählplan

In diesem Beispiel wird Deutsch als Standardsprache für den Satz UM-Wähleinstellungen "`MyUMDialPlan`" festgelegt.

    Set-UMDialPlan -Identity MyUMDialPlan -DefaultLanguage de-DE

In diesem Beispiel wird Japanisch als Standardsprache für den Satz UM-Wähleinstellungen "`MyUMDialPlan`" festgelegt.

    Set-UMDialPlan -Identity MyUMDialPlan -DefaultLanguage ja-JP

In diesem Beispiel wird australisches Englisch als Standardsprache für den Satz UM-Wähleinstellungen "`MyUMDialPlan`" festgelegt.

    Set-UMDialPlan -Identity MyUMDialPlan -DefaultLanguage en-AU


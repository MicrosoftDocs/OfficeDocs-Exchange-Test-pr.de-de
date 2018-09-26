---
title: 'Entfernen eines UM-Sprachpakets: Exchange 2013 Help'
TOCTitle: Entfernen eines UM-Sprachpakets
ms:assetid: a2bc2753-2c25-4ea0-a9d5-e3d42a699c6c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124004(v=EXCHG.150)
ms:contentKeyID: 50476375
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen eines UM-Sprachpakets

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-14_

Sie können die Exchange-Verwaltungskonsole oder die Shell verwenden, um Unified Messaging-Sprachen (UM) auf Postfachservern zu verwalten, auf denen der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird. Um jedoch eine Sprache aus der Liste in einem UM-Wählplan zu entfernen, müssen Sie das entsprechende UM-Sprachpaket unter Verwendung des Befehls**Setup.exe /RemoveUmLanguagePack** vom Postfachserver entfernen. Nachdem Sie das UM-Sprachpaket vom Postfachserver entfernt haben, steht die Sprache beim Konfigurieren eines UM-Wählplans oder einer automatischen UM-Telefonzentrale nicht mehr zur Verfügung. Sie können die installierten UM-Sprachpakete anzeigen, indem Sie die Eigenschaften des Postfachservers anzeigen oder das Cmdlet **Get-UMService** verwenden.

Weitere Informationen zu Aufgaben im Zusammenhang mit UM-Sprachen finden Sie unter [UM-Sprachen, -Telefonansagen und -Begrüßungen – Verfahren](um-languages-prompts-and-greetings-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachserver (UM-Dienst)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Überprüfen Sie, ob ein anderes Sprachpaket als das für Englisch (USA) installiert ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Entfernen eines UM-Sprachpakets mithilfe von "Setup.exe"

Führen Sie an einer Eingabeaufforderung den folgenden Befehl aus.

```powershell
Setup.exe /RemoveUmLanguagePack:<UmLanguagePackName>
```

Im vorangehenden Befehl stellt *\<UmLanguagePackName\>* den Namen des UM-Sprachpakets dar, z. B. fr-FR.


> [!WARNING]
> Nachdem Sie Updates installiert haben, können Sie die Datei "Setup.exe" im Ordner "\Bin" nicht mehr zum Entfernen eines UM-Sprachpakets verwenden. Sie müssen stattdessen die Datei "Setup.exe" auf der Exchange 2013-DVD oder in den heruntergeladenen Quelldateien verwenden. Anderenfalls wird die folgende Fehlermeldung angezeigt: Die Version der ausgeführten Anwendung entspricht nicht der Version der installierten Anwendung.



---
title: 'Importieren benutzerdefinierter Ansagen von Exchange 2007 zu Exchange 2013: Exchange 2013 Help'
TOCTitle: Importieren benutzerdefinierter Ansagen von Exchange 2007 zu Exchange 2013
ms:assetid: 70c0b0bc-c0de-4e3c-8144-1fe59f86ebf4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg309147(v=EXCHG.150)
ms:contentKeyID: 54652695
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Importieren benutzerdefinierter Ansagen von Exchange 2007 zu Exchange 2013

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können die Audiodateien mit den benutzerdefinierten Begrüßungen, Ansagen, Menüs und Eingaben aus Exchange 2007 Unified Messaging (UM) in Exchange 2013 Unified Messaging importieren. Die Eingaben werden mittels Shell-Skripten in ein Exchange-Systempostfach mit dem Namen {e0dc1c29-89c3-4034-b678-e6c29d823ed9} importiert, das bei der Installation von Microsoft Exchange 2013 erstellt wird. Dieses Systempostfach dient in Unified Messaging zum Speichern von Begrüßungen, Ansagen, Menüs, Eingaben und UM-Berichten für den Wählplan und die automatischer Telefonzentrale.

Die Audiodateien im Format .WAV oder .WMA dienen folgenden Zwecken:

  - Bei UM-Wählplänen werden Audiodateien für benutzerdefinierte Begrüßungen und Informationsansagen verwendet. Sie werden wiedergegeben, wenn Outlook Voice Access-Benutzer eine Outlook Voice Access-Nummer anrufen.

  - Bei automatischen UM-Telefonzentralen werden Audiodateien für benutzerdefinierte Begrüßung innerhalb und außerhalb der Geschäftszeiten, für Informationsansagen, Menüansagen und das Navigationsmenü verwendet. Sie werden abgespielt, wenn ein Anrufer eine automatische UM-Telefonzentrale anruft.

Mithilfe des Skripts "MigrateUMCustomPrompts.ps1" migrieren Sie eine Kopie aller benutzerdefinierten Exchange Server 2007 UM-Begrüßungen, Ansagen, Menüs und Eingaben zu Exchange 2013 UM für alle Exchange 2007 UM-Wählpläne und automatischen UM-Telefonzentralen.

Das Skript "MigrateUMCustomPrompts.ps1" befindet sich standardmäßig im Ordner \<Programme\>\\Microsoft\\Exchange Server\\V15\\Scripts auf dem Exchange 2013-Server.


> [!NOTE]
> Das Skript "MigrateUMCustomPrompts.ps1" ist in Exchange 2013 enthalten. Es muss auf einem Exchange 2013-Postfachserver in derselben Organisation ausgeführt werden, in der auch Ihre Exchange 2007 UM-Server gehostet sind.



Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wählpläne" und "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden Sie das Skript "MigrateUMCustomPrompts.ps1", um eine Kopie aller benutzerdefinierten Ansagen für UM-Wähleinstellungen und automatische Telefonzentralen zu migrieren.

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange Server 2013** \> **Exchange-Verwaltungsshell**.

2.  Geben Sie in der Shell an der Eingabeaufforderung den Pfad zum Skript ein. Geben Sie beispielsweise **cd "D:\\Programme\\Microsoft\\Exchange Server\\V15\\Scripts"** ein, und drücken Sie dann die EINGABETASTE.

3.  Geben Sie an der Shell-Eingabeaufforderung **".\\MigrateUMCustomPrompt"** ein, und drücken Sie die EINGABETASTE.


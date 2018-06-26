---
title: 'Deaktivieren Sie gängige PIN Muster für Voicemail: Exchange Online Help'
TOCTitle: Deaktivieren Sie gängige PIN Muster für Voicemail
ms:assetid: eecc40ae-fac7-41e4-a1e1-16330f4462a3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125160(v=EXCHG.150)
ms:contentKeyID: 50554939
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren Sie gängige PIN Muster für Voicemail

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-22_

Sie können gängige UM-PIN-Muster (Unified Messaging) für Outlook Voice Access-Benutzer aktivieren oder deaktivieren. Wenn Sie die Einstellung gängiger PIN-Muster für eine UM-Postfachrichtlinie aktivieren oder deaktivieren, gilt die Einstellung für alle UM-aktivierten Benutzer, die der UM-Postfachrichtlinie zugeordnet sind. Standardmäßig können UM-aktivierte Benutzer beim Erstellen einer PIN keine gängigen Muster verwenden.

Sie können mehrere PIN-bezogene Einstellungen für eine UM-Postfachrichtlinie konfigurieren. Die Einstellung **Gängige PIN-Muster zulassen** dient zum Aktivieren oder Deaktivieren der Verwendung gängiger Muster bei der PIN-Erstellung. Diese Einstellung ist standardmäßig deaktiviert und hindert Benutzer an der Verwendung der folgenden Zahlenmuster:

  - **Aufeinander folgende Zahlen**   Dies sind PIN-Werte, die ausschließlich aufeinander folgenden Zahlen enthalten. Beispiele für aufeinander folgende Zahlen sind PINs wie etwa 1234 und 65432.

  - **Wiederholte Zahlen**   Dies sind PIN-Werte, die ausschließlich aus wiederholten Zahlen bestehen. Beispiele für wiederholte Zahlen sind 11111 und 22222.

  - **Suffix der Postfachdurchwahl**   PIN-Werte, welche das Suffix der Postfachdurchwahl eines Benutzers enthalten. Beispiel: Wenn die Postfachdurchwahl eines Benutzer 36697 lautet, darf die PIN des Benutzers nicht 3669712 lauten.


> [!NOTE]
> Wenn die Einstellung <STRONG>Gängige PIN-Muster zulassen</STRONG> aktiviert ist, wird nur das Suffix der Postfachdurchwahl zurückgewiesen.



Weitere Aufgaben im Zusammenhang mit der Sicherheit von Outlook Voice Access-PINs finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Deaktivieren gängiger PIN-Muster

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Deaktivieren Sie auf der Seite **UM-Postfachrichtlinie** unter **PIN-Richtlinien** das Kontrollkästchen neben **Gängige PIN-Muster zulassen**.

4.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Deaktivieren gängiger PIN-Muster

In diesem Beispiel werden Benutzer, denen die UM-Postfachrichtlinie namens `MyUMMailboxPolicy` zugeordnet ist, an der Verwendung von PINs mit gängigen Mustern gehindert.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -AllowCommonPatterns $false


---
title: 'Konfig. d. Anz. Anmeldefehler vor Trennung von Outlook Voice Access-Benutzern'
TOCTitle: Konfigurieren der Anzahl von Anmeldefehlern, bevor Outlook Voice Access-Benutzer getrennt werden
ms:assetid: 02f93888-168c-44bb-8cf6-17f5fcc3d733
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423537(v=EXCHG.150)
ms:contentKeyID: 50474949
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren der Anzahl von Anmeldefehlern, bevor Outlook Voice Access-Benutzer getrennt werden

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-09_

Sie können die zulässige Anzahl von aufeinander folgenden Anmeldefehlversuchen angeben, bevor eine Verbindung getrennt wird. Der Wertbereich dieser Einstellung ist 1 bis 20. Bei einem zu niedrigen Wert reagieren Benutzer unter Umständen verärgert. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung von drei Versuchen festgelegt werden.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Anzahl von Anmeldefehlversuchen, bevor eine Verbindung getrennt wird, mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Geben Sie im Abschnitt **Einstellungen** unter **Anzahl der Anmeldefehler vor dem Trennen der Verbindung** die Anzahl von Anmeldefehlversuchen ein.

5.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Konfigurieren der Anzahl von Anmeldefehlversuchen, bevor eine Verbindung getrennt wird

In diesem Beispiel wird die Anzahl von Anmeldefehlversuchen, bevor eine Verbindung getrennt wird, für den Satz UM-Wähleinstellungen `MyUMDialPlan` auf 5 festgelegt.

    Set-UMDialPlan -identity MyUMDialPlan -LogonFailuresBeforeDisconnect 5


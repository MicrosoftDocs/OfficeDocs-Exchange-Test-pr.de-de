---
title: 'Konfigurieren der zu kontaktierenden Benutzergruppe: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren Sie die Gruppe von Benutzern, die kontaktiert werden können
ms:assetid: 45d9d6d5-c9d6-4b73-8aa2-a23599a4381c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423545(v=EXCHG.150)
ms:contentKeyID: 52062699
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie die Gruppe von Benutzern, die kontaktiert werden können

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-12-09_

Sie können die Gruppe der Benutzer angeben, die Anrufer erreichen können, wenn sie eine Verbindung mit einer automatischen Unified Messaging-Telefonzentrale (UM) herstellen. Standardmäßig können Anrufer Benutzer innerhalb desselben Satzes Wähleinstellungen kontaktieren, der der automatischen UM-Telefonzentrale zugeordnet ist. Sie können die Gruppierung von Benutzern jedoch ändern, um Anrufern die Übergabe von Anrufen oder das Senden von Sprachnachrichten an Benutzer, die im Adressbuch der Organisation enthalten sind, bzw. an eine bestimmte Auswahl von Benutzern zu ermöglichen.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Verwalten einer automatischen UM-Telefonzentrale](manage-a-um-auto-attendant-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Benutzergruppe, die von Anrufern kontaktiert werden kann, mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Treffen Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Zugriff auf Adressbuch und Vermittlungsstelle** unter **Optionen zum Durchsuchen des Adressbuchs** eine Auswahl aus folgenden Optionen:
    
      - **Nur in diesem Wählplan**   Mithilfe dieser Option können Sie Anrufern, die eine Verbindung mit der automatischen UM-Telefonzentrale herstellen, erlauben, Benutzer zu ermitteln und zu kontaktieren, die in dem Wählplan enthalten sind, der der automatischen UM-Telefonzentrale zugeordnet ist.
    
      - **In der gesamten Organisation**   Wählen Sie diese Option, um Benutzern, die eine Verbindung mit der automatischen UM-Telefonzentrale herstellen, das Auffinden und Kontaktieren aller Benutzer im Adressbuch der Organisation zu ermöglichen. Hierzu gehören alle postfachaktivierten Benutzer.

4.  Klicken Sie auf **Speichern**.

## Konfigurieren der Benutzergruppe, die von Anrufern kontaktiert werden kann, mithilfe der Shell

In diesem Beispiel wird der Bereich der Benutzer, die Anrufer über die automatische UM-Telefonzentrale `MyUMAutoAttendant` kontaktieren können, auf alle Benutzer im Adressbuch der Organisation festgelegt.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -ContactScope GlobalAddressList


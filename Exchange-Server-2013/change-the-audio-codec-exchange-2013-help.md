---
title: 'Ändern des Audiocodecs: Exchange Online Help'
TOCTitle: Ändern des Audiocodecs
ms:assetid: 139b2ccd-28c5-46c0-9050-777f4f59aade
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996342(v=EXCHG.150)
ms:contentKeyID: 50475143
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ändern des Audiocodecs

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-22_

Unified Messaging kann einen von vier Codecs zum Erstellen von Voicemailnachrichten verwenden: MP3, Windows Media Audio (WMA), Group System Mobile (GSM) 06.10 und G.711 Pulse Code Modulation (PCM) Linear. Beim Erstellen eines Unified Messaging-Wählplans wird standardmäßig der MP3-Audiocodec verwendet, um Sprachnachrichten aufzuzeichnen. Das MP3-Audioformat ist ein beliebtes Format, das mit verschiedenen Betriebssystemen, E-Mail-Clients und MP3-Playern verwendet werden kann. Nachdem Sie den UM-Wählplan erstellt haben, können Sie ihn jedoch für die Verwendung eines anderen Audioformats (einschließlich WMA-, GSM 06.10- oder G.711 PCM Linear-Audiocodecs) konfigurieren. Zum Wiedergeben einer Sprachnachricht muss auf einem Mobiltelefon oder Computer eine kompatible Audiosoftware installiert sein.

Zusätzliche Aufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern des Audiocodec für Unified Messaging-Wählpläne mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Wählen Sie in **Einstellungen** unter **Audiocodec** eine der folgenden Optionen aus der Dropdownliste aus:
    
      - MP3
    
      - WMA
    
      - GSM
    
      - G711

5.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Ändern des Audiocodec für Unified Messaging-Wähleinstellungen

In diesem Beispiel wird der Audiocodec für die UM-Wähleinstellungen `MyUMDialPlan` auf G.711 festgelegt.

    Set-UMDialPlan -Identity MyUMDialPlan -AudioCodec G711

In diesem Beispiel wird der Audiocodec für die UM-Wähleinstellungen `MyUMDialPlan` auf WMA festgelegt.

    Set-UMDialPlan -Identity MyUMDialPlan -AudioCodec Wma


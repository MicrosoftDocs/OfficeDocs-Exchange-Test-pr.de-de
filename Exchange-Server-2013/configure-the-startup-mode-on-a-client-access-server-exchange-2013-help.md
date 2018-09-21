---
title: 'Konfig. des Startmodus auf einem Clientzugriffsserver: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren des Startmodus auf einem Clientzugriffsserver
ms:assetid: 71cc9061-9e3c-4b4a-8dbe-f590ca5bcee8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673533(v=EXCHG.150)
ms:contentKeyID: 50554840
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren des Startmodus auf einem Clientzugriffsserver

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-15_

Sie können den Startmodus für den Microsoft Exchange Unified Messaging-Anrufrouterdienst auf einem Clientzugriffsserver angeben. Standardmäßig wird der Clientzugriffsserver im TCP-Modus gestartet. Wenn Sie jedoch TLS (Transport Layer Security) zum Verschlüsseln von VoIP-Datenverkehr (Voice over IP) verwenden, müssen Sie den Clientzugriffsserver so konfigurieren, dass TLS oder der Dualmodus verwendet wird. Es wird empfohlen, Clientzugriffsserver für den Startmodus "Dual" zu konfigurieren. Der Grund ist, dass alle Clientzugriffs- und Postfachserver alle eingehenden Anrufe für alle UM-Wählpläne beantworten, diese Wählpläne aber unterschiedliche Sicherheitseinstellungen aufweisen können. Wenn Sie den Startmodus ändern, müssen Sie den Microsoft Exchange Unified Messaging-Anrufrouterdienst erneut starten, damit die Änderung wirksam wird.


> [!IMPORTANT]
> Standardmäßig stehen Clientzugriffsserver zum Beantworten eingehender Anrufe zur Verfügung. Sie müssen einen Clientzugriffsserver einem UM-Wählplan nur dann zum Verarbeiten von UM-Anrufen hinzufügen, wenn Sie UM mit Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server integrieren.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Unified Messaging und Clientzugriffsserver finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Clientzugriffsserver (UM-Anrufrouterdienst)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Stellen Sie sicher, dass der Clientzugriffsserver installiert ist, entweder auf demselben Computer wie der Postfachserver oder auf einem anderen Computer.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren des Startmodus des Clientzugriffsservers mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Wählen Sie unter **UM-Anrufroutereinstellungen** \> **UM-Startmodus** in der Dropdownliste eine der folgenden Optionen aus:
    
      - **TCP**   Wählen Sie diese Option, wenn Sie nicht mTLS und nur ungesicherte Wählpläne verwenden.
    
      - **TLS**   Wählen Sie diese Option, wenn Sie mTLS und nur SIP-gesicherte oder gesicherte Wählpläne verwenden.
    
      - **DUAL**   Wählen Sie diese Option, wenn Sie mTLS und ungesicherte, SIP-gesicherte oder gesicherte Wählpläne verwenden.

5.  Nachdem Sie den UM-Startmodus ausgewählt haben, klicken Sie auf **Speichern**.

## Konfigurieren des Startmodus des Clientzugriffsservers mithilfe der Shell

In diesem Beispiel wird der Dualmodus als Startmodus für den Clientzugriffsserver `UMCallRouter1` festgelegt.

```powershell
Set-UMCallRouterSettings -Server UMCallRouter1 -UMStartUpMode Dual
```

In diesem Beispiel wird der TLS-Modus als Startmodus für den Clientzugriffsserver `UMCallRouter1` festgelegt.

```powershell
Set-UMCallRouterSettings -Server UMCallRouter1 -UMStartUpMode TLS
```


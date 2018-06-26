---
title: 'Konfigurieren des Startmodus auf einem Postfachserver: Exchange 2013 Help'
TOCTitle: Konfigurieren des Startmodus auf einem Postfachserver
ms:assetid: 4457d6a0-52bd-4269-8cb5-d34d7fe9bfc3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423544(v=EXCHG.150)
ms:contentKeyID: 50554786
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren des Startmodus auf einem Postfachserver

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-15_

Sie können den Startmodus für den Microsoft Exchange Unified Messaging-Dienst auf einem Postfachserver angeben. Standardmäßig wird der Postfachserver im TCP-Modus gestartet. Wenn Sie jedoch TLS (Transport Layer Security) zum Verschlüsseln von VoIP-Datenverkehr (Voice over IP) verwenden, müssen Sie den Postfachserver so konfigurieren, dass TLS oder der Dualmodus verwendet wird. Es empfiehlt sich, die Postfachserver zur Verwendung des Dualmodus als Startmodus zu konfigurieren. Grund hierfür ist, dass Clientzugriffs- und Postfachserver alle eingehenden Anrufe für alle UM-Wählpläne beantworten und diese Wählpläne unterschiedliche Sicherheitseinstellungen aufweisen können ("Ungesichert", "SIP-gesichert" oder "Gesichert"). Wenn Sie den Startmodus ändern, müssen Sie den Microsoft Exchange Unified Messaging-Dienst erneut starten, damit die Änderung wirksam wird.


> [!IMPORTANT]
> Standardmäßig stehen Postfachserver zur Beantwortung eingehender Anrufe zur Verfügung. Es ist nicht erforderlich, einen Postfachserver zu einem UM-Wählplan hinzuzufügen, damit dieser UM-Anrufe verarbeiten kann, es sei denn, Sie integrieren UM und Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Unified Messaging und Postfachservern finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachserver (UM-Dienst)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Stellen Sie sicher, dass der Postfachserver installiert ist, entweder auf demselben Computer wie der Clientzugriffsserver oder auf einem anderen Computer.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren des Startmodus auf einem Postfachserver mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Wählen Sie unter **UM-Diensteinstellungen** \> **UM-Startmodus** eine der folgenden Optionen aus der Dropdownliste aus:
    
      - **TCP**   Verwenden Sie diese Option, wenn Sie kein mTLS verwenden und nur ungesicherte Wählpläne einsetzen.
    
      - **TLS**   Verwenden Sie diese Option, wenn Sie mTLS verwenden und nur SIP-gesicherte oder gesicherte Wählpläne einsetzen.
    
      - **DUAL**   Verwenden Sie diese Option, wenn Sie mTLS und außerdem ungesicherte, SIP-gesicherte und gesicherte Wählpläne einsetzen.

5.  Nachdem Sie den UM-Startmodus ausgewählt haben, klicken Sie auf **Speichern**.

## Konfigurieren des Startmodus auf einem Postfachserver mithilfe der Shell

In diesem Beispiel wird der Dualmodus als Startmodus für den Postfachserver `MyUMServer1` festgelegt.

    Set-UMService -Identity MyUMServer1 -UMStartUpMode Dual

In diesem Beispiel wird der TLS-Modus als Startmodus für einen Postfachserver namens `MyUMServer1` festgelegt.

    Set-UMService -Identity MyUMServer1 -UMStartUpMode TLS


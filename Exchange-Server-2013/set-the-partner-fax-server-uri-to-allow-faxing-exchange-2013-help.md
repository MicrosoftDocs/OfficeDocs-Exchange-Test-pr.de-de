---
title: 'Festlegen des Partners Faxserver URI zum Senden von Faxen zulassen: Exchange Online Help'
TOCTitle: Festlegen des Partners Faxserver URI zum Senden von Faxen zulassen
ms:assetid: 77a9013b-d76b-4af2-8b2c-cef435cf67af
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ650873(v=EXCHG.150)
ms:contentKeyID: 52062722
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen des Partners Faxserver URI zum Senden von Faxen zulassen

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Sie können eingehende Faxe für Benutzer aktivieren oder deaktivieren, die einer UM-Postfachrichtlinie (Unified Messaging) zugeordnet sind. Beim Aktivieren von Benutzern für Unified Messaging können Benutzer Faxnachrichten erst empfangen, nachdem Sie den Faxeingang in der UM-Postfachrichtlinie aktiviert und den URI des Faxpartners des Partners eingegeben haben. Wenn die URIs in der UM-Postfachrichtlinie konfiguriert sind, aber die Option zum Zulassen eingehender Faxe im UM-Wählplan deaktiviert ist, können UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, keine Faxnachrichten empfangen.

Weitere Informationen zu Fax Partner finden Sie unter [Microsoft Hindernissen bei für Fax Partner](https://go.microsoft.com/fwlink/?linkid=190238).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Faxnachrichten finden Sie unter [Faxfunktion – Verfahren](faxing-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Festlegen des Faxpartner-URI mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die Richtlinie aus, die Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **UM-Postfachrichtlinie** \> **Allgemein** in das Feld **Partnerfaxserver-URI** entweder "TCP" oder "TLS URI" ein. Beispiel: *sip:faxserver1.contoso.com:5060;transport=tcp* oder *sip:faxserver2.contoso.com:5061;transport=tls*
    

    > [!NOTE]
    > Wenngleich das Feld mehrere Faxserver-URIs enthalten kann, wird nur einer verwendet. Wenn Sie zwei URIs eingeben, wird nur der erste verwendet.



4.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Festlegen des Faxpartner-URI mithilfe der Shell

Das folgende Beispiel ermöglicht Benutzern, die der UM-Postfachrichtlinie `UMDialPlan Default Policy` zugeordnet sind, das Verwenden von TCP mit Port 5060 für den Partnerfaxserver `faxserver1`.

    Set-UMMailboxPolicy "UMDialPlan Default Policy" -FaxServerURI sip:faxserver1.contoso.com:5060;transport=tcp

Dieses Beispiel ermöglicht Benutzern, die der UM-Postfachrichtlinie `UMDialPlan Default Policy` zugeordnet sind, das Verwenden von TLS mit Port 5061 für den Partnerfaxserver `faxserver2`.

    Set-UMMailboxPolicy "UMDialPlan Default Policy" -FaxServerURI sip:faxserver2.contoso.com:5061;transport=tls


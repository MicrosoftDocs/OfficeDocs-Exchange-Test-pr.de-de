---
title: 'Erstellen einer Transportschutzregel: Exchange 2013 Help'
TOCTitle: Erstellen einer Transportschutzregel
ms:assetid: 3a857185-ee16-4ee7-9e57-8be95f7e753a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd302432(v=EXCHG.150)
ms:contentKeyID: 50475501
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Transportschutzregel

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mithilfe von Transportschutzregeln können Sie den dauerhaften Rechteschutz auf Basis von Eigenschaften, z. B. Absender, Empfänger, Nachrichtenbetreff und Inhalt, auf Nachrichten anwenden.


> [!WARNING]
> Bevor Sie Transportregeln in der Produktionsumgebung erstellen, sollten Sie sie in einer Testumgebung erstellen und gründlich testen. Die in diesem Thema erstellten Transportregeln sind Beispiele. Sie können Transportregeln erstellen, indem Sie die entsprechenden Regelprädikate und Werte auf Grundlage Ihrer Anforderungen verwenden.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Verwaltung von Informationsrechten (Information Rights Management, IRM) finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2-5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportregeln" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - In Ihrer Organisation muss ein Server mit den [Active Directory-Rechteverwaltungsdiensten](https://technet.microsoft.com/de-de/library/hh831364.aspx) (AD RMS) verfügbar sein und RMS-Vorlagen enthalten.

  - Wenn Sie Transportschutzregeln konfigurieren, um Nachrichten mithilfe von IRM zu schützen und Sie außerdem Journale verwenden, erwägen Sie das Aktivieren der Journalberichtentschlüsselung, um es dem Journaling-Agent zu gestatten, eine nicht verschlüsselte Kopie der Nachricht im Journalbericht zu speichern. Weitere Informationen finden Sie unter [Journalberichtentschlüsselung](journal-report-decryption-exchange-2013-help.md).

  - Nachdem Sie eine Transportschutzregel erstellt haben, werden Nachrichten vom Transportdienst auf den Postfachservern in Warteschlangen gestellt, wenn die Regel aufgrund eines nicht verfügbaren AD RMS-Servers nicht auf Nachrichten angewendet werden kann. In Abhängigkeit vom Umfang dieser Nachrichten wird möglicherweise weiterer Speicherplatz auf den Postfachservern beansprucht. Exchange versucht drei Mal, die Nachricht mithilfe der Verwaltung von Informationsrechten (IRM) zu schützen. Nach diesen Versuchen wird dem Absender ein Unzustellbarkeitsbericht (Non-Delivery Report, NDR) gesendet, wenn der AD RMS-Server nicht erreichbar ist oder die Nachricht nicht mithilfe von IRM geschützt werden kann.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Transportschutzregel mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Nachrichtenfluss** \> **Regeln**.

2.  Klicken Sie in der Listenansicht auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Klicken Sie unter **Neue Regel** zunächst auf **Weitere Optionen**, und füllen Sie die folgenden Felder aus:
    
      - **Name**   Geben Sie einen Namen für die Transportregel ein.
    
      - **Diese Regel anwenden, wenn**   Wählen Sie eine Bedingung aus, und geben Sie die erforderlichen Werte für die Bedingung ein. Klicken Sie auf **Bedingung hinzufügen**, um weitere Bedingungen hinzuzufügen.
        

        > [!IMPORTANT]
        > Wenn Sie beim Erstellen einer Transportschutzregel keine Bedingungen auswählen, werden alle Nachrichten in Ihrer Organisation, die von Exchange&nbsp;2013-Servern mit Transportdienst verarbeitet werden, mithilfe von IRM geschützt. Der Schutz aller Nachrichten mithilfe von IRM erfordert weitere Ressourcen. Daher wird empfohlen, dass Sie Ihre Postfachserver und die AD&nbsp;RMS-Bereitstellung entsprechend planen.

    
      - **Gehen Sie wie folgt vor:**    Aktivieren Sie die Option **Rechteschutz auf Nachrichten anwenden mit**, und verwenden Sie dann das Dialogfeld **RMS-Vorlage auswählen**, um eine Vorlage auszuwählen.
    
      - **Außer wenn:**    (Optional) Klicken Sie auf **Ausnahme hinzufügen**, um eine Ausnahme von der Regel anzugeben.

4.  Klicken Sie auf **Speichern**, um die Transportregel zu erstellen.

## Verwenden der Shell zum Erstellen einer Transportschutzregel

  - In Ihrer AD RMS-Bereitstellung müssen RMS-Vorlagen vorhanden sein, um eine Transportschutzregel erstellen zu können. In diesem Beispiel werden die verfügbaren Vorlagen vom AD RMS-Cluster abgerufen.
    
        Get-RMSTemplate | format-list
    
    Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-RMSTemplate](https://technet.microsoft.com/de-de/library/dd297960\(v=exchg.150\)).

  - In diesem Beispiel wird die Transportschutzregel "Protect-BusinessCriticalProject" erstellt. Die Regel schützt Nachrichten, die den Begriff "Business Critical" im Feld "Betreff" mit der Vorlage **Nicht weiterleiten** enthalten.
    

    > [!NOTE]
    > In diesem Beispiel wird das Prädikat <CODE>SubjectContainsWords</CODE> verwendet. Sie können eine beliebige Kombination von Transportregelprädikaten verwenden, um Bedingungen und Ausnahmen für die Regel zu bilden. Informationen über die verfügbaren Prädikate finden Sie unter <A href="mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md">Transportregelbedingungen (Prädikate)</A>.

    
        New-TransportRule -Name "Protect-BusinessCriticalProject" -SubjectContainsWords "Business Critical" -ApplyRightsProtectionTemplate "Do Not Forward"
    
    Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-TransportRule](https://technet.microsoft.com/de-de/library/bb125138\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung einer Transportschutzregel zu überprüfen:

  - Überprüfen Sie mithilfe der Exchange-Verwaltungskonsole, ob die Regel erstellt wurde, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaften der Regel anzuzeigen.

  - Verwenden Sie das Cmdlet [Get-TransportRule](https://technet.microsoft.com/de-de/library/aa998585\(v=exchg.150\)), um die Regel abzurufen. Ein Beispiel zum Abrufen einer Regel finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/aa998585\(exchg.150\)#examples) in **Get-TransportRule**.

  - Verwenden Sie Outlook, Outlook Web App oder ein mobiles Gerät, um eine Testnachricht zu senden, die den Regelbedingungen entspricht. Überprüfen Sie, ob die Nachricht vom Empfänger als IRM-geschützte Nachricht empfangen wird.


---
title: 'Erstellen einer automatischen UM-Telefonzentrale: Exchange 2013 Help'
TOCTitle: Erstellen einer automatischen UM-Telefonzentrale
ms:assetid: 773f53fb-d80f-4a79-8bd3-bd753942489f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998875(v=EXCHG.150)
ms:contentKeyID: 50476035
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.UnifiedMessaging.CreateAutoAttendantWizardForm.CreateAutoAttendantWizardPage
ms.translationtype: HT
---

# Erstellen einer automatischen UM-Telefonzentrale

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-03-08_

Nachdem Sie eine automatische Telefonzentrale für Unified Messaging (UM) erstellt haben, werden an der externen Rufnummer eines Unternehmens eingehende Anrufe, die normalerweise von einem Telefonisten angenommen würden, von der automatischen Telefonzentrale beantwortet. Im Gegensatz zu anderen Unified Messaging-Komponenten, z. B. UM-Wählplänen und UM-IP-Gateways, ist die Einrichtung automatischer UM-Telefonzentralen nicht unbedingt erforderlich. Automatische Telefonzentralen helfen in- und externen Anrufern jedoch beim Auffinden von Benutzern oder Abteilungen in einer Organisation und leiten Anrufe an diese weiter.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen einer automatischen UM-Telefonzentrale mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wähleinstellungen**, wählen Sie die UM-Wähleinstellungen aus, für die Sie eine automatische Telefonzentrale hinzufügen möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wähleinstellungen** unterhalb von **Automatische UM-Telefonzentralen** auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Machen Sie auf der Seite **Neue automatische UM-Telefonzentrale** die folgenden Angaben:
    
      - **Name**   Geben Sie in dieses Feld den Anzeigenamen für die automatische UM-Telefonzentrale ein. Ein Name für die automatische UM-Telefonzentrale ist erforderlich und muss eindeutig sein. Er dient jedoch nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell.
        
        Falls Sie den Namen für die automatische Telefonzentrale nach ihrer Erstellung ändern möchten, müssen Sie zunächst die vorhandene automatische UM-Telefonzentrale löschen und anschließend eine andere automatische Telefonzentrale mit dem gewünschten Namen erstellen. Wenn in Ihrer Organisation mehrere automatische UM-Telefonzentralen eingesetzt werden, sollten Sie aussagekräftige Namen für Ihre automatischen UM-Telefonzentralen verwenden. Die maximale Länge für den Namen einer automatischen UM-Telefonzentrale beträgt 64 Zeichen inklusive Leerzeichen.
        
        Wenngleich der Name einer neuen UM-Telefonzentrale Leerzeichen enthalten darf, ist bei der Integration von Unified Messaging in Office Communications Server 2007 R2 oder Microsoft Lync Server die Verwendung von Leerzeichen im Namen von automatischen Telefonzentralen nicht zulässig. Wenn Sie daher eine automatische Telefonzentrale mit Leerzeichen im Anzeigenamen erstellt haben und Sie eine Integration in Office Communications Server 2007 R2 oder Lync Server durchführen, müssen Sie diese automatische Telefonzentrale zunächst löschen und eine andere automatische Telefonzentrale erstellen, die keine Leerzeichen im Anzeigenamen verwendet.
    
      - **Die automatische Telefonzentrale als aktiviert erstellen**   Aktivieren Sie dieses Kontrollkästchen, wenn nach dem Beenden des Assistenten für neue automatische UM-Telefonzentralen die automatische Telefonzentrale eingehende Anrufe beantworten soll. Standardmäßig wird eine neue automatische Telefonzentrale als deaktiviert erstellt.
        
        Wenn Sie die automatische UM-Telefonzentrale als deaktiviert erstellen, können Sie sie nach Beendigung des Assistenten in der Exchange-Verwaltungskonsole oder in der Verwaltungsshell aktivieren.
    
      - **Automatische Telefonzentrale zur Antwort auf Sprachbefehle einrichten**   Aktivieren Sie dieses Kontrollkästchen, um die automatische Telefonzentrale für die Spracherkennung zu aktivieren. Bei Sprachaktivierung der automatischen Telefonzentrale können Anrufer auf Systemansagen oder benutzerdefinierte Ansagen der automatischen UM-Telefonzentrale mit Tonwahl- oder Spracheingaben antworten. Standardmäßig wird die automatische Telefonzentrale bei ihrer Erstellung nicht sprachaktiviert.
        
        Damit Anrufern eine sprachaktivierte automatische Telefonzentrale zur Verfügung steht, müssen Sie das entsprechende UM-Sprachpaket installieren, das die automatische Spracherkennung unterstützt, und die Eigenschaften der automatischen Telefonzentrale für die Verwendung dieser Sprache konfigurieren.
    
      - **Zugriffsnummern**   Verwenden Sie dieses Feld, um die Durchwahl- oder Telefonnummer einzugeben, die Anrufer zum Erreichen der automatischen Telefonzentrale verwenden. Geben Sie eine Durchwahlnummer in das Feld ein, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Nummer der Liste hinzuzufügen. Die Anzahl von Ziffern der eingegebenen Durchwahl- oder Telefonnummer muss nicht mit der Anzahl von Ziffern einer Durchwahlnummer übereinstimmen, die im zugeordneten Satz UM-Wähleinstellungen konfiguriert ist. Der Grund dafür ist, dass direkte Anrufe bei automatischen UM-Telefonzentralen zulässig sind.
        
        Die Anzahl von Durchwahl- oder Telefonnummern ist unbegrenzt. Die neue automatische Telefonzentrale kann jedoch auch ohne eine in der Liste enthaltene Durchwahlnummer erstellt werden. Eine Durchwahl- oder Telefonnummer ist nicht erforderlich.
        
        Sie können eine vorhandene Durchwahl- oder Telefonnummer bearbeiten und löschen. Klicken Sie zum Bearbeiten einer vorhandenen Durchwahl- oder Telefonnummer auf **Bearbeiten**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Klicken Sie zum Entfernen einer vorhandenen Durchwahl- oder Telefonnummer aus der Liste auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

4.  Klicken Sie auf **Speichern**.

## Erstellen einer automatischen UM-Telefonzentrale mithilfe der Shell

In diesem Beispiel wird die neue automatische UM-Telefonzentrale `MyUMAutoAttendant` erstellt, die eingehende Anrufe annehmen kann, jedoch nicht sprachaktiviert ist.

    New-UMAutoAttendant -Name MyUMAutoAttendant -UMDialPlan MyUMDialPlan -PilotIdentifierList 55000 -Enabled $false

In diesem Beispiel wird die sprachaktivierte automatische UM-Telefonzentrale `MyUMAutoAttendant` erstellt.

    New-UMAutoAttendant -Name MyUMAutoAttendant -UMDialPlan MyUMDialPlan -PilotIdentifierList 56000,56100 -SpeechEnabled $true


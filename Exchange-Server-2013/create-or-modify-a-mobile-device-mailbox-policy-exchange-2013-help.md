---
title: 'Erstellen oder Ändern einer Postfachrichtlinie für mobile Geräte: Exchange 2013 Help'
TOCTitle: Erstellen oder Ändern einer Postfachrichtlinie für mobile Geräte
ms:assetid: b4a37a81-25e3-40ff-a18a-a62ae4493635
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124315(v=EXCHG.150)
ms:contentKeyID: 50476489
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen oder Ändern einer Postfachrichtlinie für mobile Geräte

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-16_

Mit einer Postfachrichtlinie für mobile Geräte können Sie allgemeine Sicherheitseinstellungen und Einstellungen für mobile Geräte auf eine Gruppe von Benutzern anwenden. Sie können mehrere Postfachrichtlinien für mobile Geräte erstellen. Jedem Empfänger in Ihrer Organisation muss eine Postfachrichtlinie für mobile Geräte zugewiesen sein. Wenn Sie Microsoft Exchange Server 2013 installieren, wird eine Standardpostfachrichtlinie für mobile Geräte erstellt. Neue Benutzer werden automatisch dieser Richtlinie zugewiesen. Informationen, wie Sie einer Postfachrichtlinie für mobile Geräte bestimmte Benutzer zuweisen, finden Sie unter [Hinzufügen oder Entfernen von Benutzern zu bzw. aus einer Postfachrichtlinie für mobile Geräte](add-or-remove-users-from-a-mobile-mailbox-policy-exchange-2013-help.md).

Weitere Informationen zu Postfachrichtlinien für mobile Geräte finden Sie unter [Postfachrichtlinien für mobile Geräte](mobile-device-mailbox-policies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachrichtlinie für mobile Geräte" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen einer neuen Postfachrichtlinie für mobile Geräte

Sie können eine neue Postfachrichtlinie für mobile Geräte auch mit der Exchange-Verwaltungskonsole oder mit der Shell erstellen.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachrichtlinie für mobile Geräte" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

## Erstellen einer neuen Postfachrichtlinie für mobile Geräte mit der Exchange-Verwaltungskonsole

Sie können eine neue Postfachrichtlinie für mobile Geräte mit der Exchange-Verwaltungskonsole erstellen.


> [!NOTE]
> In der Exchange-Verwaltungskonsole können Sie nur eine Teilmenge der Postfachrichtlinieneinstellungen für mobile Geräte festlegen. Wenn Sie alle Postfachrichtlinieneinstellungen für mobile Geräte festlegen möchten, müssen Sie die Shell verwenden.



1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Mobil** \> **Postfachrichtlinien für mobile Geräte**, und klicken Sie dann auf **Neu**.

2.  Verwenden Sie die verschiedenen Kontrollkästchen und Dropdownlisten, um die Postfachrichtlinie für mobile Geräte zu konfigurieren.
    

    > [!WARNING]
    > Wählen Sie <STRONG>Dies ist die Standardrichtlinie</STRONG> aus, damit diese neue Richtlinie die Standardpostfachrichtlinie für mobile Geräte wird. Nachdem Sie eine Postfachrichtlinie für mobile Geräte als Standardrichtlinie festgelegt haben, wird jeder neu erstellte Benutzer automatisch dieser Richtlinie zugewiesen.



3.  Klicken Sie auf **Speichern**.

## Erstellen einer neuen Postfachrichtlinie für mobile Geräte mit der Shell

Zum Erstellen einer neuen Postfachrichtlinie für mobile Geräte verwenden Sie das Cmdlet New-MobileDeviceMailboxPolicy.


> [!WARNING]
> Es gibt zwei Cmdlets, mit denen neue Postfachrichtlinien für mobile Geräte erstellt werden können. Die Cmdlets <STRONG>New-ActiveSyncMailboxPolicy</STRONG> und <STRONG>New-MobileDeviceMailboxPolicy</STRONG> führen dieselben Aufgaben aus. In einer zukünftigen Version von Microsoft Exchange Server wird das Cmdlet <STRONG>New-ActiveSyncMailboxPolicy</STRONG> entfernt. Sie sollten Ihre Skripts und Prozeduren daher so aktualisieren, dass das Cmdlet <STRONG>New-MobileDeviceMailboxPolicy</STRONG> verwendet wird.



1.  Führen Sie in der Shell den folgenden Befehl aus.
    
        New-MobileDeviceMailboxPolicy -Name:"Management" -AllowBluetooth:$true -AllowBrowser:$true -AllowCamera:$true -AllowPOPIMAPEmail:$false -PasswordEnabled:$true -AlphanumericPasswordRequired:$true -PasswordRecoveryEnabled:$true -MaxEmailAgeFilter:10 -AllowWiFi:$true -AllowStorageCard:$true -AllowPOPIMAPEmail:$false

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung einer Postfachrichtlinie für mobile Geräte zu überprüfen:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Mobil** \> **Postfachrichtlinien für mobile Geräte**, und vergewissern Sie sich, dass die neue Richtlinie in der Listenansicht angezeigt wird.

2.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-MobileDeviceMailboxPolicy -Identity <PolicyName> 

## Bearbeiten einer vorhandenen Postfachrichtlinie für mobile Geräte

Sie können eine Postfachrichtlinie für mobile Geräte mit der Exchange-Verwaltungskonsole oder mit der Shell bearbeiten.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachrichtlinie für mobile Geräte" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

## Bearbeiten einer Postfachrichtlinie für mobile Geräte mit der Exchange-Verwaltungskonsole

Sie können eine eine Postfachrichtlinie für mobile Geräte mit der Exchange-Verwaltungskonsole bearbeiten.


> [!NOTE]
> In der Exchange-Verwaltungskonsole können Sie nur eine Teilmenge der Postfachrichtlinieneinstellungen für mobile Geräte bearbeiten. Wenn Sie alle Postfachrichtlinieneinstellungen für mobile Geräte bearbeiten möchten, müssen Sie die Shell verwenden.



1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Mobil** \> **Postfachrichtlinien für mobile Geräte**.

2.  Wählen Sie in der Listenansicht eine Richtlinie aus, und klicken Sie auf die Schaltfläche **Bearbeiten**.

3.  Bearbeiten Sie die Postfachrichtlinieneinstellungen auf den Registerkarten **Allgemein** und **Sicherheit**.

4.  Klicken Sie auf **Speichern**, um die Richtlinie zu aktualisieren.

## Bearbeiten der Einstellungen einer Postfachrichtlinie für mobile Geräte mit der Shell

Sie können eine Postfachrichtlinie für mobile Geräte mit der Shell bearbeiten.


> [!WARNING]
> Es gibt zwei Cmdlets, mit denen eine Postfachrichtlinie für mobile Geräte bearbeitet werden kann. Die Cmdlets Set-ActiveSyncMailboxPolicy und Set-MobileDeviceMailboxPolicy führen dieselben Aufgaben aus. In einer zukünftigen Version von Microsoft Exchange Server wird das Cmdlet <STRONG>Set-ActiveSyncMailboxPolicy</STRONG> entfernt. Sie sollten Ihre Skripts und Prozeduren daher so aktualisieren, dass das Cmdlet <STRONG>Set-MobileDeviceMailboxPolicy</STRONG> verwendet wird.



1.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Set-MobileDeviceMailboxPolicy -Identity:Default -DevicePasswordEnabled:$true -AlphanumericDevicePasswordRequired:$true -PasswordRecoveryEnabled:$true -MaxEmailAgeFilter:ThreeDays -AllowWiFi:$false -AllowStorageCard:$true -AllowPOPIMAPEmail:$false -IsDefault:$true -AllowTextMessaging:$true -Confirm:$true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Bearbeitung einer Postfachrichtlinie für mobile Geräte zu überprüfen:

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Mobil** \> **Postfachrichtlinien für mobile Geräte**, und wählen Sie dann die gewünschte Richtlinie aus. Im Detailbereich werden einige der Richtlinieneinstellungen aufgelistet.

2.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-MobileDeviceMailboxPolicy -Identity <PolicyName>


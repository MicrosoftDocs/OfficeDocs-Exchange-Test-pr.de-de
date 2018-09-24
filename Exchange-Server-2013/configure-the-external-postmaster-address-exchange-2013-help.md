---
title: 'Konfigurieren der externen Postmasteradresse: Exchange 2013 Help'
TOCTitle: Konfigurieren der externen Postmasteradresse
ms:assetid: 6b0c8675-3238-462d-8973-b52305fb90d2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb430765(v=EXCHG.150)
ms:contentKeyID: 52062864
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der externen Postmasteradresse

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Die externe Postmasteradresse wird als Absender für vom System generierte Nachrichten und Benachrichtigungen verwendet, die an Nachrichtenabsender außerhalb Ihrer Microsoft Exchange Server 2013-Organisation gesendet werden. Ein externer Absender ist ein beliebiger Absender mit einer E-Mail-Adresse in einer Domäne, die in Ihrer Organisation nicht als akzeptierte Domäne konfiguriert ist.

Standardmäßig ist der Einstellungswert der externen Postmasteradresse leer. Dieser Standardwert bewirkt in Ihrer Exchange-Organisation das folgende Verhalten:

  - Die externe Postmasteradresse für alle Postfach- und abonnierten Edge-Transport-Server ist "postmaster@\<*standardmäßig akzeptierte Domäne*\>".

  - Die externe Postmasteradresse für alle nicht abonnierten Edge-Transport-Server ist "postmaster@\<*Edge Transport server FQDN*\>".

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportkonfiguration" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Wenn Sie eine benutzerdefinierte externe Postmasteradresse konfigurieren, gilt dieser Wert für alle Exchange 2013-Postfachserver und Exchange 2010-Hub-Transport-Server in Ihre Exchange-Organisation. Dieser Wert wird jedoch nicht auf Edge-Transport-Server repliziert. Wenn Sie einen benutzerdefinierten Wert für die externe Postmasteradresse festlegen, müssen Sie diese Adresse auf allen Edge-Transport-Servern manuell konfigurieren.

  - Wenn Ihre Organisation Exchange 2007-Hub-Transport- oder Edge-Transport-Server aufweist, müssen Sie mit dem Cmdlet **Set-TransportServer** die benutzerdefinierte externe Postmasteradresse auf allen diesen Servern konfigurieren. Weitere Informationen finden Sie unter [Verwalten der externen Postmasteradresse](https://go.microsoft.com/fwlink/?linkid=279922).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Konfigurieren der externen Postmasteradresse mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Empfangsconnectors** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") \> **Einstellungen für Organisationstransport** \> Registerkarte **Zustellung**.

2.  Geben Sie in das Feld **Externe Postmasteradresse** die SMTP-E-Mail-Adresse ein, z. B. `postmaster@contoso.com`. Wenn Sie die externe Postmasteradresse auf den Standardwert zurücksetzen möchten, löschen Sie vorhandene Werte, damit das Feld leer ist.

3.  Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Konfigurieren der externen Postmasteradresse mithilfe der Shell

Verwenden Sie folgende Syntax, um die externe Postmasteradresse zu konfigurieren.

```powershell
Set-TransportConfig -ExternalPostmasterAddress <postmaster address>
```

Um beispielsweise die externe Postmasteradresse auf den Wert `postmaster@contoso.com` festzulegen, führen Sie den folgenden Befehl aus:

```powershell
Set-TransportConfig -ExternalPostmasterAddress postmaster@contoso.com
```

Um die externe Postmasteradresse auf den Standardwert festzulegen, führen Sie den folgenden Befehl aus:

```powershell
Set-TransportConfig -ExternalPostmasterAddress $null
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die externe Postmasteradresse erfolgreich konfiguriert wurde:

1.  Führen Sie zum Überprüfen des Werts der externen Postmasteradresse auf einem Postfachserver den folgenden Befehl aus:
    
    ```powershell
    Get-TransportConfig | Format-List ExternalPostmasterAddress
    ```

2.  Senden Sie von einem externen E-Mail-Konto eine Nachricht an Ihre Exchange-Organisation, die eine Benachrichtigung über den Zustellungsstatus verursacht. Sie können beispielsweise eine Transportregel für das Senden eines Unzustellbarkeitsberichts bei einer Nachrichten von diesem Absender konfigurieren, die bestimmte Schlüsselwörter enthält. Prüfen Sie, ob die E-Mail-Adresse des Absenders in der Benachrichtigung über den Zustellungsstatus dem angegebenen Wert entspricht.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).
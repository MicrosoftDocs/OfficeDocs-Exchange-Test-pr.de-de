---
title: 'Importieren oder Exportieren von Zertifikaten für UM: Exchange 2013 Help'
TOCTitle: Importieren oder Exportieren von Zertifikaten für UM
ms:assetid: ee688c33-2e08-47e7-95fc-04ba10238341
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn205143(v=EXCHG.150)
ms:contentKeyID: 54652712
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Importieren oder Exportieren von Zertifikaten für UM

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-12-18_

Sie können selbstsignierte, interne PKI-Zertifikate (Public Key Infrastructure) oder kommerzielle Drittanbieterzertifikate über die Exchange-Verwaltungskonsole oder die Shell importieren oder exportieren. Für Unified Messaging (UM) können Sie eines dieser Zertifikate für den Microsoft Exchange Unified Messaging-Dienst und den Microsoft Exchange Unified Messaging Call Router-Dienst verwenden. Sie können für beide Dienste das gleiche Zertifikat oder jeweils unterschiedliche Zertifikate verwenden.

Das Importieren von Zertifikaten für Exchange kann hilfreich sein, wenn Sie eine der folgenden Aufgaben durchführen möchten:

  - Importieren eines Zertifikats, das in eine Datei exportiert wurde.

  - Importieren einer PKI-Zertifikatsdatei, die von einer internen Zertifizierungsstelle generiert wurde.

  - Importieren eines kommerziellen Drittanbieterzertifikats.

Das Exportieren eines bestehenden Zertifikats aus dem Zertifikatsspeicher auf dem lokalen Exchange-Server kann hilfreich sein, wenn Sie eine der folgenden Aufgaben durchführen möchten:

  - Exportieren des Zertifikats, sodass es auf einen anderen Exchange-Server importiert werden kann.

  - Exportieren des Zertifikats, sodass es auf einem VoIP-Gateway, einer IP-PBX-Anlage oder einer SIP-aktivierten PBX-Anlage importiert werden kann.

  - Exportieren des Zertifikats, sodass Sie das Zertifikat und dessen privaten Schlüssel sichern können.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit der Verwaltung von Zertifikaten für Unified Messaging finden Sie unter [Bereitstellen von Zertifikaten für UM Prozeduren](deploying-certificates-for-um-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Zertifikatverwaltung" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md) und "UM-Dienst" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md). Sie müssen sich zudem mit einem Konto anmelden, das Mitglied der lokalen Gruppe "Administratoren" auf diesem Computer ist.

  - Bevor Sie ein Zertifikat exportieren können, verwenden Sie das Cmdlet **Get-ExchangeCertificate**, um sich zu vergewissern, dass das Attribut *PrivateKeyExportable* auf dem Zertifikat auf `$true` festgelegt ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Exportieren eines Zertifikats mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Server** \> **Zertifikate** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") und dann auf **Exchange-Zertifikat exportieren**.

2.  Geben Sie auf der Seite **Exchange-Zertifikat exportieren** im Feld **Datei, in die exportiert wird** den Namen der Zertifikatsdatei ein.

3.  Geben Sie im Feld **Kennwort** das Kennwort ein, mit dem Sie den privaten Schlüssel schützen möchten, und klicken Sie dann auf **OK**.

## Exportieren eines Zertifikats mithilfe der Shell

Bei diesem Beispiel wird das Zertifikat mit dem Fingerabdruck A36DE2B9B62980A717EBD0C3052F5F0B08FBFFCC in eine Datei exportiert, nachdem Sie zur Eingabe eines Benutzernamens und Kennworts aufgefordert wurden.

    $file = Export-ExchangeCertificate -Thumbprint A36DE2B9B62980A717EBD0C3052F5F0B08FBFFCC -BinaryEncoded:$true -Password (Get-Credential).password

In diesem Beispiel werden folgende Schritte ausgeführt:

1.  Verwendung des Cmdlets **Get-ExchangeCertificate**, um das zu exportierende Zertifikat zu suchen.

2.  Verwendung des Cmdlets **Export-ExchangeCertificate**, um das Kennwort für das Zertifikat festzulegen.

3.  Ausgabe des Zertifikats in eine Datei, nachdem Sie den Benutzernamen und das Kennwort eingegeben haben.

<!-- end list -->

    $file = Get-ExchangeCertificate -DomainName umcorp.northwindtraders.com | Export-ExchangeCertificate -BinaryEncoded:$true -Password (Get-Credential).password

    Set-Content -Path "d:\umcerts\selfsigned.pfx" -Value $file.FileData =Encoding Byte

## Importieren eines Zertifikats mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Server** \> **Zertifikate** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") und dann auf **Exchange-Zertifikat importieren**.

2.  Geben Sie auf der Seite **Exchange-Zertifikat importieren** im Feld **Datei, aus der importiert wird** den freigegebenen Ordnerpfad und den Namen der Zertifikatsdatei ein. Wenn das Zertifikat mit einem Kennwort geschützt ist, geben Sie im Feld **Kennwort** das Kennwort ein, und klicken Sie dann auf **Weiter**.

3.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Server auszuwählen, auf die Sie das Zertifikat anwenden möchten, und klicken Sie dann auf **OK**. Wenn Sie einen Server aus der Listenansicht entfernen möchten, klicken Sie auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)") und dann auf **Fertig stellen**.

## Importieren eines Zertifikats mithilfe der Shell

Bei diesem Beispiel wird ein Zertifikat aus der Zertifikatsdatei D:\\Zertifikate\\Exchange\\SelfSignedUMCert.pfx importiert, nachdem Sie einen Benutzernamen und ein Kennwort eingegeben haben.

    Import-ExchangeCertificate -FileData ([Byte[]]$(Get-Content -Path d:\certificates\exchange\SelfSignedUMCert.pfx -Encoding Byte -ReadCount 0)) -Password:(Get-Credential).password


---
title: 'Erstellen einer Anforderung für ein digitales Zertifikat: Exchange 2013 Help'
TOCTitle: Erstellen einer Anforderung für ein digitales Zertifikat
ms:assetid: efb00de7-070b-46bf-a2fc-00d07ae085c1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125165(v=EXCHG.150)
ms:contentKeyID: 52062926
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Anforderung für ein digitales Zertifikat

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-02-21_

In Exchange Server 2013 können Sie Zertifikate mithilfe der Exchange-Verwaltungskonsole oder der Shell verwalten. Die Exchange-Verwaltungskonsole umfasst eine neue Benutzeroberfläche für die Zertifikatverwaltung. Über diese neue Benutzeroberfläche können Sie neue Zertifikate erstellen und vorhandene Zertifikate bearbeiten oder löschen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten zuzüglich der Zeit für die Antwort der Zertifizierungsstelle.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter Eintrag "Sicherheitseinstellungen für den Clientzugriffsserver" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen einer neuen Zertifikatanforderung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Zertifikate**.

2.  Wählen Sie in der Liste **Server auswählen** den Server aus, für den Sie ein Zertifikat erstellen möchten, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Aktivieren Sie im Assistenten für neue Zertifikate entweder **Anforderung eines Zertifikats von einer Zertifizierungsstelle erstellen** oder **Selbstsigniertes Zertifikat erstellen**, und klicken Sie dann auf **Weiter**.

4.  Geben Sie einen Anzeigenamen für das Zertifikat ein, und klicken Sie auf **Weiter**.

5.  Wenn Sie kein selbstsigniertes Zertifikat ausgewählt haben und ein Platzhalterzertifikat benötigen, aktivieren Sie das Kontrollkästchen **Platzhalterzertifikat anfordern**, und geben Sie die Stammdomäne ein, z. B. "\*.contoso.com". Klicken Sie anschließend auf **Weiter**. Wenn Sie ein selbstsigniertes Zertifikat ausgewählt haben, überspringen Sie diesen Schritt.

6.  Wählen Sie die Server aus, auf die Sie dieses Zertifikat anwenden möchten, und klicken Sie dann auf **Weiter**.

7.  Geben Sie die Domänen an, die Sie in das Zertifikat aufnehmen möchten, und klicken Sie dann auf **Weiter**.

8.  Vergewissern Sie sich, dass Sie die richtigen Domänen angegeben haben. Wenn Sie ein selbstsigniertes Zertifikat ausgewählt haben, klicken Sie auf **Fertig stellen**. Anderenfalls klicken Sie auf **Weiter**.

9.  Geben Sie den Namen der Organisation, den Namen der Abteilung, die Stadt bzw. den Ort, das Bundesland bzw. den Kanton sowie das Land bzw. die Region ein, und klicken Sie dann auf **Weiter**.

10. Geben Sie einen Speicherort zum Speichern der Zertifikatanforderung ein, und klicken Sie dann auf **Fertig stellen**.

Falls Sie kein selbstsigniertes Zertifikat ausgewählt haben, müssen Sie die Zertifikatanforderungsdatei zur Verarbeitung an die Zertifizierungsstelle senden.

## Erstellen einer neuen Zertifikatanforderung mithilfe der Shell

Führen Sie die folgenden Befehle aus:

    $reqfile = New-ExchangeCertificate -GenerateRequest -SubjectName "C=US,o=Contoso,cn=contosotocert" -DomainName "contoso.com" -PrivateKeyExportable $true

    $reqfile | out-file c:\certreq.txt

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn Sie ein selbstsigniertes Zertifikat erstellt haben, wird dieses auf der Benutzeroberfläche für die Zertifikatverwaltung angezeigt. Haben Sie eine Zertifikatanforderung von einer Zertifizierungsstelle erstellt, befindet sich die Zertifikatanforderungsdatei an dem Speicherort, der von Ihnen angegeben wurde. Senden Sie diese Datei an die Zertifizierungsstelle.


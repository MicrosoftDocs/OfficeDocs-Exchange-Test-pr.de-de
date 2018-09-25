---
title: 'Erstellen von Zertifikaten für UM: Exchange 2013 Help'
TOCTitle: Erstellen von Zertifikaten für UM
ms:assetid: 66807ee7-3d3f-482d-a3ac-d4e9baca3271
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn205141(v=EXCHG.150)
ms:contentKeyID: 54652689
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen von Zertifikaten für UM

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-29_

Im EAC oder in der Shell können Sie mithilfe des Assistenten für neue Exchange-Zertifikate selbstsignierte Zertifikate oder Anforderungen für ein internes Public Key-Infrastrukturzertifikat (PKI-Zertifikat) erstellen. Bei Unified Messaging (UM) können Sie eines dieser Zertifikate sowohl für den Microsoft Exchange Unified Messaging-Dienst als auch für die Microsoft Exchange Unified Messaging Call Router-Dienste verwenden. Sie verwenden entweder dasselbe Zertifikat für beide Dienste oder für jeden Dienst ein gesondertes Zertifikat. Für UM-Dienste können Sie aber auch ein Zertifikat eines Drittanbieters erwerben. Falls Sie sich für UM für ein selbstsigniertes Zertifikat entscheiden, müssen Sie möglicherweise den Namen Ihrer Clientzugriffs- und Postfachserver unter dem alternativen Antragstellernamen (SAN) angeben.

Wenn Sie Exchange Server 2013 installieren, werden standardmäßig zwei selbstsignierte Zertifikate erstellt: **Microsoft Exchange Server Auth Certificate** und **Microsoft Exchange**. Das selbstsignierte Zertifikat **Microsoft Exchange** dient UM zum Verschlüsseln von Daten. Sie müssen jedoch das Zertifikat zu UM- und UM-Anrufroutingdiensten zuweisen. Nachdem Sie den Unified Messaging-Diensten das Zertifikat zugewiesen haben, kann es kopiert und in VoIP-Gateways, IP-Festnetztelefonanlagen und SIP-aktivierte PBX-Anlagen importiert werden. Anstelle standardmäßiger selbstsignierter Zertifikate müssen Sie möglicherweise ein Zertifikat speziell für Unified Messaging erstellen.


> [!WARNING]
> Für die Integration von UM mit Microsoft Lync Server können selbstsignierte Zertifikate nicht verwendet werden.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Zertifikaten für Unified Messaging finden Sie unter [Bereitstellen von Zertifikaten für UM Prozeduren](deploying-certificates-for-um-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unterEintrag "Zertifikatsverwaltung" im [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md)-Thema sowie "UM-Dienst" im [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md)-Thema. Sie müssen sich zudem mit einem Konto anmelden, das Mitglied der lokalen Gruppe "Administratoren" auf diesem Computer ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden des EAC zum Erstellen einer Zertifikatsanforderung für UM

1.  Navigieren Sie im EAC zu **Server** \> **Zertifikate**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Wählen Sie auf der Seite **Neue Exchange-Zertifikate** die Option **Anforderung eines Zertifikats von einer Zertifizierungsstelle erstellen**, und klicken Sie dann auf **Weiter**.

3.  Geben Sie einen Anzeigenamen für das Zertifikat ein, und klicken Sie auf **Weiter**.

4.  Wenn Sie kein Platzhalterzertifikat benötigen, klicken Sie auf **Weiter**. Wenn Sie ein Platzhalterzertifikat brauchen, wählen Sie **Platzhalterzertifikat anfordern. Ein Platzhalterzertifikat kann verwendet werden, um alle Unterdomänen unter Ihrer Stammdomäne mit einem einzigen Zertifikat abzusichern**. Geben Sie den Namen der Stammdomäne ein, und klicken Sie auf **Weiter**.

5.  Klicken Sie unter der Option zum Speichern der Zertifikatsanforderung auf dem Server auf **Durchsuchen**, um zum Speicherplatz zu navigieren, an dem Sie die Datei speichern möchten. Sie können die Zertifikatsanforderung auf jedem Clientzugriffs- oder Postfachserver in Ihrer Exchange-Organisation speichern. Wählen Sie den Speicherort, und klicken Sie auf **OK** und dann auf **Weiter**.

6.  Wenn Sie ein Platzhalterzertifikat angefordert haben, fahren Sie mit Schritt 9 fort.

7.  Haben Sie kein Platzhalterzertifikat angefordert, müssen Sie die Domänen angeben, die in das Zertifikat mit aufgenommen werden sollen. Zum Bearbeiten einer Domäne klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol") und dann auf **Weiter**.

8.  Unter der Option, mit der basierend auf Ihrer Auswahl folgende Domänen in Ihr Zertifikat mit eingeschlossen werden und Sie weitere Domänen hinzufügen oder Änderungen vornehmen können, können Sie Namen der Domänen hinzufügen, bearbeiten, entfernen oder prüfen, die unter **Domäne** aufgeführt sind. Klicken Sie dann auf **Weiter**.

9.  Unter der Option zur Angabe von Informationen zu Ihrer Organisation, die von der Zertifizierungsstelle verlangt werden, geben Sie Folgendes ein:
    
      - **Name der Organisation**
    
      - **Name der Abteilung**
    
      - **Ort**
    
      - **Bundesland/Kanton**
    
      - **Name Land/Region**   Wählen Sie der Dropdownliste ein Land oder eine Region.

10. Geben Sie unter der Option für das Speichern der Zertifikatsanforderung in einer Datei den Namen der Zertifikatsdatei an, und klicken Sie auf **Fertig stellen**.

## Verwenden der Shell zum Erstellen einer Zertifikatsanforderung für UM

In diesem Beispiel wird eine neue Exchange-Zertifikatsanforderung für den Postfachserver `MyMailboxServer` mit dem Anzeigenamen `CertUM` erstellt.

```powershell
    New-ExchangeCertificate -FriendlyName 'CertUM' -GenerateRequest -PrivateKeyExportable $true -KeySize '2048' -DomainName '*.northwindtraders.com' -SubjectName 'C=US,S=wa,L=redmond,O=northwindtraders,OU=servers,CN= northwindtraders.com' -Server 'MyMailboxServer'
```

## Verwenden des EAC zum Erstellen eines selbstsignierten Zertifikats für UM

1.  Navigieren Sie im EAC zu **Server** \> **Zertifikate**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Wählen Sie auf der Seite **Neues Exchange-Zertifikat** die Option **Selbstsigniertes Zertifikat erstellen** und klicken dann auf **Weiter**.

3.  Geben Sie einen Anzeigenamen für das Zertifikat ein, und klicken Sie auf **Weiter**.

4.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Exchange-Server zu wählen, für die dieses Zertifikat gelten soll. Klicken Sie dann auf **Weiter**.

5.  Geben Sie die Domänen an, die Sie in das Zertifikat aufnehmen möchten, und klicken Sie dann auf **Weiter**. Wenn Sie eine Domäne für einen Dienst hinzufügen möchten, klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

6.  Vergewissern Sie sich, dass die hinzugefügten Domänen gültig sind, und klicken Sie auf **Fertig stellen**.


> [!IMPORTANT]
> Wenn Sie ein selbstsigniertes Zertifikat über das EAC erstellen, werden Sie nicht aufgefordert, Dienste für das Zertifikat zu aktivieren. Nachdem Erstellen des Zertifikats können Sie über das EAC oder das Cmdlet <STRONG>Enable-ExchangeCertificate</STRONG> in der Shell die Exchange-Dienste aktivieren. Weitere Informationen zum Zuweisen eines Zertifikats zu UM-Dienste finden Sie unter <A href="assign-a-certificate-to-the-um-and-um-call-router-services-exchange-2013-help.md">Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst</A>.



## Verwenden der Shell zum Erstellen eines selbstsignierten Zertifikats für UM

In diesem Beispiel wird ein neues selbstsigniertes Exchange-Zertifikat für den Postfachserver `MyMailboxServer` mit dem Anzeigenamen `UMCert` erstellt.
```powershell
    New-ExchangeCertificate -Services 'UM, UMCallRouter' -DomainName '*.northwindtraders.com' -FriendlyName 'UMSelfSigned' -SubjectName 'C=US,S=WA,L=Redmond,O=Northwindtraders,OU=Servers,CN= Northwindtraders.com' -PrivateKeyExportable $true
```


> [!TIP]
> Wenn Sie die zu aktivierenden Dienste mithilfe des Parameters <EM>Services</EM> angeben, werden Sie aufgefordert, diese Dienste zuzuweisen. In diesem Beispiel werden Sie aufgefordert, das Zertifikat für die UM- und die UM-Anrufroutingdienste zu aktivieren. Weitere Informationen zum Aktivieren eines Zertifikats für Dienste finden Sie unter <A href="assign-a-certificate-to-the-um-and-um-call-router-services-exchange-2013-help.md">Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst</A>.



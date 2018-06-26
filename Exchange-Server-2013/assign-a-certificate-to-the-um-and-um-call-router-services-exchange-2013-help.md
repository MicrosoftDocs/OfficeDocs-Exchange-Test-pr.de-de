---
title: 'Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst: Exchange 2013 Help'
TOCTitle: Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst
ms:assetid: 8a900e5f-9779-4213-92d7-ec157b15fbc5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn205140(v=EXCHG.150)
ms:contentKeyID: 54652697
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zuweisen eines Zertifikats an den UM-Dienst und den UM-Anrufrouterdienst

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-04-29_

Sie können mithilfe der Exchange-Verwaltungskonsole oder der Shell ein selbstsigniertes Zertifikat, ein Zertifikat einer internen Public Key-Infrastruktur (PKI) oder ein Drittanbieterzertifikat für bestimmte Exchange-Dienste zuweisen. Wenn Sie das Cmdlet **New-ExchangeCertificate** verwenden, um das Zertifikat Exchange-Diensten mit dem Parameter *Services* zuzuweisen, werden Sie aufgefordert, das Zertifikat Exchange-Diensten zuzuweisen. Wenn Sie mit der Exchange-Verwaltungskonsole ein Zertifikat erstellen, fordert Sie der Assistent für neue Exchange-Zertifikate nicht auf, das Zertifikat Exchange-Diensten zuzuweisen. Sie müssen die Eigenschaften des Zertifikats bearbeiten und das Zertifikat zuweisen, indem Sie die Dienste auswählen, denen Sie es zuweisen möchten.

Dienste weisen unterschiedliche Zertifikatanforderungen auf. So ist für manche Dienste nur ein Servername in den Feldern **Antragstellername** oder **Alternativer Antragstellername** eines Zertifikats erforderlich und für andere Dienste ein vollqualifizierter Domänenname (FQDN). Stellen Sie sicher, dass der Zertifikatname die von den Diensten erforderlichen Methoden unterstützt, für die Sie es aktivieren.


> [!WARNING]
> Selbstsignierte Zertifikate können nicht verwendet werden, wenn Sie Unified Messaging (UM) mit Microsoft Lync Server integrieren.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit der Verwaltung von Zertifikaten für Unified Messaging finden Sie unter [Bereitstellen von Zertifikaten für UM Prozeduren](deploying-certificates-for-um-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Zertifikatverwaltung" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md) und "UM-Dienst" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md). Sie müssen sich zudem mit einem Konto anmelden, das Mitglied der lokalen Gruppe "Administratoren" auf diesem Computer ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Zuweisen eines Zertifikats an den Unified Messaging-Dienst und den UM-Anrufrouterdienst mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Zertifikate**.

2.  Wählen Sie in der Listenansicht das Zertifikat aus, das Sie dem Unified Messaging-Dienst und dem UM-Anrufrouterdienst zuweisen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite *\<Zertifikatsname\>* zuerst **Dienste** und dann **UM** sowie **UM-Anrufrouter** aus.

4.  Klicken Sie auf **Speichern**.

## Zuweisen eines Zertifikats an den Unified Messaging-Dienst und den UM-Anrufrouterdienst mithilfe der Shell

In diesem Beispiel wird dem Unified Messaging-Dienst und dem UM-Anrufrouterdienst ein Zertifikat zugewiesen.

    Enable-ExchangeCertificate -Thumbprint 5113ae0233a72fccb75b1d0198628675333d010e -Services 'UM, UMCallRouter'


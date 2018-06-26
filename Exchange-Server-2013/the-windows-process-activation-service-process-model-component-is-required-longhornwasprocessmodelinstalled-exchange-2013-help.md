---
title: 'Der Windows-Prozessaktivierungsdienst - Prozessmodellkomponente erforderlich_LonghornWASProcessModelInstalled: Exchange 2013 Help'
TOCTitle: Der Windows-Prozessaktivierungsdienst - Prozessmodellkomponente erforderlich_LonghornWASProcessModelInstalled
ms:assetid: 8cc13dbb-4921-4c07-8602-d26613d7730a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.longhornwasprocessmodelinstalled(v=EXCHG.150)
ms:contentKeyID: 50476140
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Der Windows-Prozessaktivierungsdienst - Prozessmodellkomponente erforderlich\_LonghornWASProcessModelInstalled

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2015-04-07_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Exchange Server 2010-Setup kann die Installation auf dem Windows Server 2008- oder Windows Server 2008 R2-basierten Computer nicht fortsetzen, da die Prozessmodellfunktion des Windows-Prozessaktivierungsdiensts nicht auf dem Server installiert ist.

Der Windows-Prozessaktivierungsdienst generalisiert das Prozessmodell der Internetinformationsdienste (Internet Information Services, IIS) und hebt dessen Abhängigkeit von HTTP auf. Alle Features von IIS, die zuvor nur für HTTP-Anwendungen verfügbar waren, stehen jetzt mithilfe nicht HTTP-gestützter Protokolle auch Anwendungen zur Verfügung, die WCF-Dienste (Windows Communication Foundation) hosten. IIS 7.0 verwendet darüber hinaus den Windows-Prozessaktivierungsdienst für nachrichtenbasierte Aktivierung über HTTP.

Das Prozessmodell hostet Web- und WCF-Dienste. In IIS 6.0 eingeführt, stellt das Prozessmodell eine neue Architektur dar, die sich durch schnellen Schutz vor Ausfällen, Statusüberwachung und Recycling auszeichnet.

Zum Beheben dieses Problems installieren Sie die Prozessmodellfunktion des Windows-Prozessaktivierungsdiensts auf diesem Server und führen das Exchange 2010-Setup anschließend erneut aus.

Installieren des Prozessmodellfeatures des Windows-Prozessaktivierungsdiensts mithilfe des Server-Manager-Tools

1.  Klicken Sie auf **Start**, klicken Sie auf **Verwaltung** und dann auf **Server-Manager**.

2.  Klicken Sie im linken Navigationsbereich mit der rechten Maustaste auf **Funktionen**, und klicken Sie dann auf **Funktionen hinzufügen**.

3.  Führen Sie im Bereich **Funktionen auswählen** einen Bildlauf nach unten bis zum **Windows-Prozessaktivierungsdienst** aus.

4.  Aktivieren Sie die Kontrollkästchen für **Prozessmodell**.

5.  Klicken Sie im Bereich **Funktionen auswählen** auf **Weiter**, und klicken Sie dann im Bereich **Installationsauswahl bestätigen** auf **Installieren**.

6.  Klicken Sie auf **Schließen**, um den Assistenten für das Hinzufügen von Funktionsdiensten zu schließen.


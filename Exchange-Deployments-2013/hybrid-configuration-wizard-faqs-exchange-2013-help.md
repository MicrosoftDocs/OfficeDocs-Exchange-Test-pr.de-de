---
title: 'FAQs zum Assistenten für die Hybridkonfiguration: Exchange 2013 Help'
TOCTitle: FAQs zum Assistenten für die Hybridkonfiguration
ms:assetid: e911e6e0-e36e-4430-ac36-c745a10d6c26
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt488940(v=EXCHG.150)
ms:contentKeyID: 72045758
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# FAQs zum Assistenten für die Hybridkonfiguration

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Microsoft hat einen neuen Assistenten für die Hybridkonfiguration veröffentlicht, der die Konfiguration einer Hybridbereitstellung vereinfacht, eine flexiblere Hybridkonfiguration ermöglicht und sicherstellt, dass stets die aktuelle Benutzerumgebung verwendet wird. Diese Version des Hybridassistenten ist ab dem kumulativen Update 10 in Exchange 2016 und Releases von Exchange 2013 integriert. Sie können den neuen Assistenten jedoch auch dann herunterladen, wenn Sie ein älteres kumulatives Update (CU) von Exchange 2013 oder Exchange 2010 Service Pack 3 (SP3) verwenden.

Weitere Informationen zum Office 365 Assistenten für Hybridkonfigurationen finden Sie unter [Einführung des Assistenten für Hybridkonfigurationen für Microsoft Office 365](http://go.microsoft.com/fwlink/?linkid=717122) und unter [Office 365-Assistent für Hybridkonfigurationen für Exchange 2010](http://go.microsoft.com/fwlink/?linkid=730687) im Blog des Exchange-Teams.

Zum Herunterladen des Office 365-Hybridkonfigurationsassistenten rufen Sie [http://aka.ms/HybridWizard](http://aka.ms/hybridwizard) auf.

## Von Kunden häufig gestellte Fragen

  - F.: Welche Versionen von Exchange unterstützen den neuen Assistenten für Hybridkonfigurationen?  
    A.: Sie müssen über mindestens einen Server verfügen, der die folgenden Anforderungen erfüllt:
    
      - **Exchange 2010**Exchange 2010 SP3 muss auf mindestens einem Server ausgeführt werden, der die Postfach-, Hubtransport- und Clientzugriff-Serverrollen innehat. Es wird außerdem dringend empfohlen, dass Sie das aktuell verfügbare Updaterollup für Exchange 2010 SP3 installieren.
    
      - **Exchange 2013** Das aktuelle Exchange 2013-CU muss auf mindestens einem Server installiert sein, der die Postfach- und Clientzugriff-Serverrollen innehat. Wenn Sie das neueste kumulative Upate (CU) nicht installieren können, wird die unmittelbar vorherige Version ebenfalls unterstützt. Ältere CUs werden nicht unterstützt.
    
      - **Exchange 2016** Die aktuelle Version von Exchange 2016 muss auf mindestens einem Server installiert sein, der die Postfachserverrolle innehat.
    
    Nehmen wir beispielsweise an, dass Exchange 2013 CU8 in Ihrer lokalen Organisation installiert ist, und die neueste verfügbare Version von Exchange 2013 ist CU10. Um weiterhin in einer unterstützen Hybridkonfiguration zu bleiben, müssen Sie die Exchange 2013-Server mindestens auf CU9 aktualisieren. Es wird jedoch dringend empfohlen diese auf CU10 zu aktualisieren.
    
    Kumulative Updates werden vierteljährlich veröffentlicht, sodass Sie durch Aktualisierung Ihrer Server auf die neuesten kumulativen Updates von zusätzlicher Flexibilität profitieren, wenn Sie regelmäßig mehr Zeit zum Abschließen von Upgrades benötigen.

<!-- end list -->

  - F.: Funktioniert dieser Assistent für Hybridkonfigurationen mit Exchange 2007?  
    A.: Sie können in Ihrer Organisation eine Hybridbereitstellung mit Exchange 2007 konfigurieren. Dazu müssen Sie jedoch mindestens einen Server mit Exchange 2013 bereitstellen, der die oben genannten Anforderungen erfüllt.

<!-- end list -->

  - F.: Kann ich mich auch dazu entschließen, den neuen Assistenten für Hybridkonfigurationen nicht zu verwenden?  
    A.: Nein. Der neue Assistent für Hybridkonfigurationen ist der einzige Assistent, der in Exchange 2010, Exchange 2013 und Exchange 2016 unterstützt wird.

<!-- end list -->

  - F.: Kann ich meine aktuelle Exchange 2010-Hybridkonfiguration mit dem neuen Assistenten für Hybridkonfigurationen auf Exchange 2013 oder Exchange 2016 aktualisieren?  
    A.: Ja. Stellen Sie sicher, dass mindestens ein Server vorhanden ist, der die aktuellen Anforderungen des Assistenten für Hybridkonfigurationen erfüllt, und führen Sie diesen aus. Der Assistent erkennt den aktuellen Status der Hybridkonfiguration und führt Sie reibungslos durch das Upgradeverfahren.


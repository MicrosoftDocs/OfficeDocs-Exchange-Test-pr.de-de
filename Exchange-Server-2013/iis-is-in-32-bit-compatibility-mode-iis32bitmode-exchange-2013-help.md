---
title: 'IIS befindet sich im 32-Bit-Kompatibilitätsmodus_IIS32BitMode: Exchange 2013 Help'
TOCTitle: IIS befindet sich im 32-Bit-Kompatibilitätsmodus_IIS32BitMode
ms:assetid: 742dfc32-353c-46a2-830e-68aed6a68ce0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.iis32bitmode(v=EXCHG.150)
ms:contentKeyID: 50476015
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# IIS befindet sich im 32-Bit-Kompatibilitätsmodus\_IIS32BitMode

 

_**Gilt für:**Exchange Server_

_**Letztes Änderungsdatum des Themas:**2012-06-05_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da Microsoft Internet Information Service (IIS) auf dem 64-Bit-Computer im 32-Bit-Modus ausgeführt wird.

Exchange 2007 erfordert, dass IIS bei Ausführung auf einem 64-Bit-Computer im vollständigen 64-Bit-Modus betrieben wird.

Um dieses Problem zu beheben, schalten Sie IIS in den 64-Bit-Modus um, und führen Sie das Microsoft Exchange-Setup anschließend erneut aus.

So schalten Sie IIS in den 64-Bit-Modus um

1.  Öffnen Sie eine Eingabeaufforderung.

2.  Geben Sie Folgendes ein:
    
    **cscript c:\\inetpub\\adminscripts\\adsutil.vbs SET /w3svc/AppPools/Enable32BitAppOnWin64 False**

3.  Drücken Sie die EINGABETASTE.


---
title: 'Apps für Outlook: Exchange 2013 Help'
TOCTitle: Apps für Outlook
ms:assetid: 28b6f2a1-a235-4023-b561-6fd304962775
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ943753(v=EXCHG.150)
ms:contentKeyID: 52062840
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Apps für Outlook

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2017-03-13_

**Zusammenfassung:**  Eine Übersicht der Add-Ins für Outlook, die zusammen mit Outlook auf Windows- und MacIntosh-Computern, auf mobilen Geräten und in Outlook Web App sowie Outlook im Web verwendet werden können.

Add-Ins für Outlook sind Anwendungen, die den Nutzen von Outlook-Clients durch zusätzliche Informationen oder Tools erweitern, die Ihre Benutzer verwenden können, ohne Outlook beenden zu müssen. Add-Ins werden von Drittanbieterentwicklern erstellt und können aus einer Datei oder einer URL oder aus dem Office Store installiert werden. Standardmäßig können alle Benutzer Add-Ins installieren. Exchange-Administratoren können Rollen verwenden, um die Installation von Add-Ins durch Benutzer zu steuern.


> [!TIP]
> Informationen zu Add-Ins für Outlook aus der Sicht des Endbenutzers finden Sie im Hilfethema <A href="https://go.microsoft.com/fwlink/p/?linkid=28238">Installierte Add-Ins</A> auf Office.com. Dieses Thema bietet einen Überblick über Add-Ins für Outlook und zeigt Ihnen außerdem einige Add-Ins für Outlook, die standardmäßig installiert werden können.



## Office Store-Add-Ins und benutzerdefinierte Add-Ins

Outlook-Clients unterstützen eine Vielzahl von Add-Ins, die über den Office Store zur Verfügung stehen. Outlook unterstützt außerdem benutzerdefinierte Add-Ins, die Sie erstellen und an Benutzer in Ihrer Organisation verteilen können.


> [!NOTE]
> Zugriff auf Office Store wird für Postfächer oder Organisationen in bestimmten Regionen nicht unterstützt. Wenn <STRONG>Aus dem Office Store hinzufügen</STRONG> nicht als Option im <STRONG>Exchange Admin Center</STRONG> unter <STRONG>Organisation</STRONG> &gt; <STRONG>Add-Ins</STRONG> &gt; <IMG title="Hinzufügen (Symbol)" alt="Hinzufügen (Symbol)" src="images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif"> angezeigt wird, können Sie ein Add-In für Outlook über eine URL oder einen Dateispeicherort installieren. Weitere Informationen erhalten Sie von Ihrem Dienstanbieter.




> [!NOTE]
> Einige Add-Ins für Outlook werden standardmäßig installiert. Standard-Add-Ins für Outlook werden nur für englischsprachige Inhalte aktiviert. Beispielsweise wird durch deutsche Postadressen im Nachrichtentext das Bing Maps-Add-In nicht aktiviert.



## Add-Ins-Zugriff und -Installation

Standardmäßig können alle Benutzer Add-Ins installieren und entfernen. Exchange-Administratoren haben eine Reihe von Steuerungsmöglichkeiten für die Verwaltung von Add-Ins und den Benutzerzugriff auf diese Add-Ins. Administratoren können das Installieren von Add-Ins, die nicht aus dem Office Store heruntergeladen wurden, durch Benutzer deaktivieren (stattdessen werden sie per „Side-Loading“ aus einer Datei oder URL geladen). Administratoren können auch das Installieren von Office Store-Add-Ins und das Installieren von Add-Ins im Auftrag anderer Benutzer deaktivieren. Es ist auch möglich, Benutzer einer Rolle zuzuweisen, die es ihnen ermöglicht, Add-Ins für Ihre Organisation oder für einen Teil der Benutzer in Ihrer Organisation zu installieren.

Um zu verhindern, dass Benutzer ein Add-In, das nicht aus dem Office Store stammt, installieren, entfernen Sie die Rolle **Eigene benutzerdefinierte Apps**. Um zu verhindern, dass Benutzer Add-Ins aus dem Office Store installieren, entfernen Sie die Rolle **Eigene Marketplace-Apps**. Weitere Informationen finden Sie unter [Festlegen der Administratoren und Benutzer, die Add-Ins für Outlook installieren und verwalten dürfen](https://review.docs.microsoft.com/de-de/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins)

Informationen zum Installieren von Add-Ins für einige oder alle Benutzer in Ihrer Organisation finden Sie unter [Installieren oder Entfernen von Apps für Outlook für Ihre Organisation](https://review.docs.microsoft.com/de-de/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/install-or-remove-outlook-add-ins).

Bei Bedarf können Sie die Verfügbarkeit eines Add-Ins auf bestimmte Benutzer in der Organisation beschränken. Weitere Informationen finden Sie unter [Verwalten des Benutzerzugriffs auf Apps für Outlook](manage-user-access-to-add-ins-for-outlook-exchange-online-help.md).

## Gängige Verwaltungsaufgaben für Outlook-Add-Ins

Es gibt verschiedene gängige Szenarien, mit denen Sie als Exchange-Administrator in Ihrer Organisation häufig konfrontiert sind.

**Wenn Sie verhindern möchten, dass Endbenutzer Add-Ins für Outlook auf Outlook-Clients installieren, müssen Sie die Rollen der betreffenden Benutzer im Exchange Admin Center wie folgt anpassen:** 

  - Damit Benutzer keine Add-Ins aus dem Office Store installieren können, müssen Sie die Rolle **My Marketplace** für die betreffenden Benutzer entfernen.

  - Damit Benutzer keine Add-Ins aus anderen Quellen als dem Office Store laden können, müssen Sie die Rolle **My Custom Apps** für die betreffenden Benutzer entfernen.

  - Damit Benutzer keinerlei Add-Ins mehr installieren können, müssen Sie für die betreffenden Benutzer beide Rollen entfernen.

Weitere Informationen finden Sie unter [Festlegen der Administratoren und Benutzer, die Add-Ins für Outlook installieren und verwalten dürfen](https://review.docs.microsoft.com/de-de/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).

**Falls Ihre Endbenutzer aktuell Zugriff auf Add-Ins haben und Sie dies ändern möchten, können Sie mithilfe des Cmdlets `Get-App` anzeigen, welche Add-Ins die einzelnen Benutzer installiert haben.**

Verwenden Sie anschließend das Cmdlet `Remove-App`, um die gefundenen Add-Ins zu entfernen. Das Cmdlet lässt sich sowohl auf einen als auch auf mehrere Benutzer anwenden. 

Für Exchange 2013 finden Sie weitere Informationen unter [Get-App](https://technet.microsoft.com/de-de/library/jj218673\(v=exchg.150\)) und [Remove-App](https://technet.microsoft.com/de-de/library/jj218709\(v=exchg.150\)). Entsprechende Informationen für Exchange Online und Exchange 2016 finden Sie [hier](https://go.microsoft.com/fwlink/p/?linkid=84472).

## Zulassen der Installation von Add-Ins durch Administratoren und Benutzer

Sie können angeben, welche Administratoren in Ihrer Organisation die Berechtigung zum Installieren und Verwalten von Add-Ins für Outlook haben. Außerdem können Sie angeben, welche Benutzer in Ihrer Organisation die Berechtigung zum Installieren und Verwalten von Add-Ins zur eigenen Verwendung besitzen. Weitere Informationen finden Sie unter [Festlegen der Administratoren und Benutzer, die Add-Ins für Outlook installieren und verwalten dürfen](https://review.docs.microsoft.com/de-de/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).


---
title: 'Erstellen eines Postfachs für öffentliche Ordner: Exchange 2013 Help'
TOCTitle: Erstellen eines Postfachs für öffentliche Ordner
ms:assetid: 64437ffd-231b-4c10-84df-232ccbe9538f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ552410(v=EXCHG.150)
ms:contentKeyID: 50475831
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines Postfachs für öffentliche Ordner

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2014-10-23_

Bevor Sie einen öffentlichen Ordner erstellen können, müssen Sie zunächst ein Postfach für öffentliche Ordner erstellen. Postfächer für öffentliche Ordner enthalten die Hierarchieinformationen sowie den Inhalt öffentlicher Ordner. Das erste Postfach für öffentliche Ordner, das Sie erstellen, wird zum primären Hierarchiepostfach, das die einzige beschreibbare Kopie der Hierarchie enthält. Alle weiteren Postfächer für öffentliche Ordner, die Sie erstellen, werden sekundäre Postfächer, die eine schreibgeschützte Kopie der Hierarchie enthalten.


> [!NOTE]
> Weitere Informationen zu den Speicherkontingenten und -grenzwerten bei öffentlichen Ordnern finden Sie unter den folgenden Themen: 
> <UL>
> <LI>
> <P>Informationen zu öffentlichen Ordnern bei Office 365 finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=391188">Exchange Online-Begrenzungen</A>.</P>
> <LI>
> <P>Informationen zu öffentlichen Ordnern beim intern verwalteten Exchange Server 2013 finden Sie unter <A href="limits-for-public-folders-exchange-2013-help.md">Grenzwerte für öffentliche Ordner</A>.</P></LI></UL>



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner in Exchange 2013 finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner in Exchange Online finden Sie unter [Öffentliche Ordnerprozeduren in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj966272\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 5 Minuten.

  - Öffentliche Exchange 2013-Ordner und öffentliche Ordner auf Exchange-Servern aus Vorgängerversionen können nicht in derselben Organisation vorhanden sein. Wenn Sie versuchen, ein Postfach für öffentliche Ordner zu erstellen, wenn Sie weiterhin über öffentliche Ordner aus einer Vorgängerversion verfügen, wird der Fehler **Eine vorhandene Bereitstellung öffentlicher Ordner wurde festgestellt. Zum Migrieren vorhandener Daten öffentlicher Ordner erstellen Sie ein neues Öffentlicher Ordner-Postfach mithilfe der Option '-HoldForMigration'** angezeigt.
    
    Bevor Sie öffentliche Ordner in Exchange 2013 erstellen können, müssen Sie Ihre öffentlichen Ordner aus der Vorgängerversion zu Exchange 2013 migrieren. Befolgen Sie dazu die Schritte unter [Verwenden der seriellen Migration zum Migrieren von öffentlichen Ordnern zu Exchange 2013 aus vorherigen Versionen](https://technet.microsoft.com/de-de/library/jj150486\(v=exchg.150\)). Diese Schritte zeigen Ihnen das Erstellen eines Postfachs für öffentliche Ordner, das zum Speichern Ihrer migrierten öffentlichen Ordner verwendet werden kann.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Öffentliche Ordner" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Erstellen eines Postfachs für öffentliche Ordner mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Öffentliche Ordner** \> **Postfächer für den öffentlichen Ordner**, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie in **Postfach für öffentliche Ordner** einen Namen für das Postfach für den öffentlichen Ordner an.

3.  Klicken Sie auf **Speichern**.

## Erstellen eines Postfachs für öffentliche Ordner mithilfe der Shell

In diesem Beispiel wird das primäre Postfach für öffentliche Ordner erstellt.

    New-Mailbox -PublicFolder -Name MasterHierarchy

In diesem Beispiel wird ein sekundäres Postfach für öffentliche Ordner erstellt. Der einzige Unterschied zwischen der Erstellung des primären Hierarchiepostfachs und einem sekundären Hierarchiepostfach besteht darin, dass das primäre Postfach das erste Postfach ist, das in der Organisation erstellt wurde. Sie können zusätzliche Postfächer für öffentliche Ordner zum Zweck des Lastenausgleichs erstellen.

    New-Mailbox -PublicFolder -Name Istanbul 

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Shell-Befehl aus, um sicherzustellen, dass Sie das primäre Postfach für öffentliche Ordner erfolgreich erstellt haben:

    Get-OrganizationConfig | Format-List RootPublicFolderMailbox

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997571\(v=exchg.150\)).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).


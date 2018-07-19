---
title: 'Kurzwahlnummern konfigurieren: Exchange Online Help'
TOCTitle: Kurzwahlnummern konfigurieren
ms:assetid: e5b5efee-b734-4f70-8357-11be07b23bd0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124992(v=EXCHG.150)
ms:contentKeyID: 51409360
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Kurzwahlnummern konfigurieren

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können Kurzwahlnummern, Rufnummernpräfixe und Nummernformate, die von Unified Messaging verwendet werden so konfigurieren, dass UM-aktivierte Benutzer ein- und ausgehende Anrufe einleiten können. In den meisten Fällen konfigurieren Sie einen Wählplan mit den Kurzwahlnummern, Rufnummernpräfixen und Nummernformaten, die derzeit in Ihrem Telefonienetzwerk konfiguriert sind.

Anhand der Kurzwahlnummern und Nummernpräfixe ermittelt UM die ordnungsgemäße Nummer, die bei einem Anruf gewählt werden soll, der von einem UM-aktivierten Benutzer eingeleitet wird. *Outdialing* ist der Begriff zum Beschreibens des Vorgangs, bei dem ein Benutzer in einem UM-Wählplan einen ausgehenden Anruf einleitet. Nummernformate werden für eingehende Anrufe in einem Land oder einer Region, internationale Anrufe oder Anrufe verwendet, die innerhalb eines Wählplans eingeleitet werden. Sie können einen Wählplan entsprechend dem Nummernformat eingehender Anrufe für nationale und internationale Nummern konfigurieren. Bei der Konfiguration der nationalen und internationalen Nummernformate können Sie eingehende Anrufe für Benutzer einschränken, die einem Wählplan zugeordnet sind.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Outdialing finden Sie unter [Ermöglichen, dass Benutzer Anrufe Verfahren stellen](allowing-users-to-make-calls-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von Kurzwahlnummern, Rufnummernpräfixen und Nummernformaten über die Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie den UM-Wählplan aus, den Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Füllen Sie auf der Seite **UM-Wählplan** \> **Kurzwahlnummern** folgende Felder aus:
    
      - **Amtskennziffer**
    
      - **Internationale VAZ**
    
      - **Rufnummernpräfix, national**
    
      - **Länder-/Regionscode**

5.  Konfigurieren Sie unter **Nummernformate zum Wählen in Wählplänen** die folgenden Optionen:
    
      - **Nationales Nummernformat**
    
      - **Internationales Nummernformat**
    
      - **Nummernformate für eingehende Anrufe im gleichen Wählplan**   Klicken Sie zum Hinzufügen eines Nummernformats auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

6.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Konfigurieren von Kurzwahlnummern, Rufnummernpräfixen und Nummernformaten über die Shell

In diesem Beispiel wird der UM-Wählplan `MyUMDialPlan` mit einem nationalen Nummernformat und einem internationalen Nummernformat sowie den folgenden Kurzwahlnummern konfiguriert.

  - 9 für die Amtskennziffer

  - 011 für die internationale VAZ

  - 1 für das nationale Rufnummernpräfix

  - 1 für den Länder-/Regionscode

<!-- end list -->

    Set-UMDialPlan -Identity MyUMDialPlan -OutsideLineAccessCode 9 -InternationalAccessCode 011 -NationalNumberPrefix 1 CountryorRegionCode 1 -InCountryOrRegionNumberFormat 1425xxxxxxx -InternationalNumberFormat 441425xxxxxxx


---
title: 'Entfernen einer E-Mail-Adressrichtlinie: Exchange 2013 Help'
TOCTitle: Entfernen einer E-Mail-Adressrichtlinie
ms:assetid: f1d05223-7d41-406d-8fae-f4227be1c1c2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125181(v=EXCHG.150)
ms:contentKeyID: 50477062
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer E-Mail-Adressrichtlinie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-13_

Exchange enthält standardmäßig eine E-Mail-Adressrichtlinie, die den Alias des Empfängers als den lokalen Anteil der E-Mail-Adresse angibt und die akzeptierte Standarddomäne verwendet. Der lokale Anteil einer E-Mail-Adresse ist der Name, der vor dem @-Zeichen angezeigt wird. Diese E-Mail-Adressrichtlinie gilt für alle Benutzer in der Organisation. Diese E-Mail-Adressrichtlinie kann nicht entfernt werden.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf E-Mail-Adressrichtlinien finden Sie unter [Verfahren für die E-Mail-Adressrichtlinie](email-address-policy-procedures-exchange-2013-help.md).

## Was müssen Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Wenn Sie eine E-Mail-Adressrichtlinie entfernen, die von Empfängern als primäre Richtlinie verwendet wird, und keine weiteren Richtlinien für Empfänger konfiguriert wurden, wird die Standardrichtlinie verwendet.

  - Die Standardrichtlinie kann nicht gelöscht werden. Wenn Sie die Standardrichtlinie löschen möchten, müssen Sie zuerst eine andere Richtlinie als Standardrichtlinie festlegen.

  - Wenn die E-Mail-Adressrichtlinie, die Sie löschen möchten, mehr als 3.000 Empfänger enthält, sollten Sie dieses Verfahren mithilfe der Shell ausführen.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Adressrichtlinien" im Thema [E-Mail-Adressen und Adressbücher](email-addresses-and-address-books-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Entfernen einer E-Mail-Adressrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Nachrichtenfluss** \> **E-Mail-Adressrichtlinien**.

2.  Wählen Sie in der Listenansicht die E-Mail-Adressrichtlinie aus, die Sie löschen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

3.  Klicken Sie in der Warnung auf **Ja**, um die Richtlinie zu entfernen.

## Entfernen einer E-Mail-Adressrichtlinie mithilfe der Shell

In diesem Beispiel wird die E-Mail-Adressrichtlinie "South East Offices" entfernt.

    Remove-EmailAddressPolicy -Identity "South East Offices"

Geben Sie **Y** ein, um das Entfernen der Richtlinie zu bestätigen, und drücken Sie dann die EINGABETASTE.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-EmailAddressPolicy](https://technet.microsoft.com/de-de/library/bb124504\(v=exchg.150\)).


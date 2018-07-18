---
title: 'Erstellen einer E-Mail-Adressrichtlinie mithilfe der Empfängerfilterung: Exchange 2013 Help'
TOCTitle: Erstellen einer E-Mail-Adressrichtlinie mithilfe der Empfängerfilterung
ms:assetid: e3f446bd-1511-479c-8d87-2dfce5547c90
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232194(v=EXCHG.150)
ms:contentKeyID: 50476944
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer E-Mail-Adressrichtlinie mithilfe der Empfängerfilterung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-16_

Sie können mithilfe der Shell eine E-Mail-Adressrichtlinie mit Empfängerfilterung erstellen. Weitere Informationen zu E-Mail-Adressrichtlinien finden Sie unter [E-Mail-Adressrichtlinien](email-address-policies-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf E-Mail-Adressrichtlinien finden Sie unter [Verfahren für die E-Mail-Adressrichtlinie](email-address-policy-procedures-exchange-2013-help.md).

## Was müssen Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Wenn der Parameter *RecipientFilter* zum Erstellen eines benutzerdefinierten Filters verwendet werden soll, müssen Sie eine Zeichenfolge für den Filter angeben. Die Shell verwendet OPath für die Filtersyntax. OPath ist eine Abfragesprache, mit der Objektdatenquellen abgefragt werden können.
    

    > [!IMPORTANT]
    > Wenn Sie einen Empfängerfilter zum Erstellen oder Bearbeiten einer E-Mail-Adressrichtlinie verwenden, können Sie die E-Mail-Adressrichtlinie nicht in der Exchange-Verwaltungskonsole bearbeiten. Sie müssen die Shell verwenden. Ausführliche Informationen zu Syntax und Parametern finden Sie unter <A href="https://technet.microsoft.com/de-de/library/bb124517(v=exchg.150)">Set-EmailAddressPolicy</A>.



  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Adressrichtlinien" im Thema [E-Mail-Adressen und Adressbücher](email-addresses-and-address-books-exchange-2013-help.md).

  - Bevor eine SMTP-Adressendomäne in einer E-Mail-Adressrichtlinie verwendet werden kann, müssen Sie eine akzeptierte Domäne konfigurieren. Weitere Informationen finden Sie unter [Akzeptierte Domänen](accepted-domains-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen einer E-Mail-Adressrichtlinie mit Empfängerfilterung mithilfe der Shell

Verwenden Sie zum Erstellen einer E-Mail-Adressrichtlinie mit Empfängerfilterung die folgende Syntax.

    New-EmailAddressPolicy -Name <String> -RecipientFilter <String>

In diesem Beispiel wird eine E-Mail-Adressrichtlinie erstellt, die für alle Führungskräfte gilt und bei der der lokale Teil der E-Mail-Adresse aus den ersten beiden Buchstaben des Vornamens und dem vollständigen Nachnamen besteht.

    New-EmailAddressPolicy -Name 'Execs' -EnabledEmailAddressTemplates 'SMTP:%2g%s@contoso.com' -RecipientFilter {((RecipientType -eq 'UserMailbox') -and (Title -like 'executive'))}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-EmailAddressPolicy](https://technet.microsoft.com/de-de/library/aa996800\(v=exchg.150\)).


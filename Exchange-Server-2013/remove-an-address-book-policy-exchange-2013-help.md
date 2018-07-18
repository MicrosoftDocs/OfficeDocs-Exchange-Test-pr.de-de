---
title: 'Entfernen einer Adressbuchrichtlinie: Exchange 2013 Help'
TOCTitle: Entfernen einer Adressbuchrichtlinie
ms:assetid: c20c6f82-2f75-4116-9be1-c5af10113f71
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529946(v=EXCHG.150)
ms:contentKeyID: 50476644
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer Adressbuchrichtlinie

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-03-25_

Verwenden Sie dieses Verfahren, um eine Adressbuchrichtlinie (ABP) zu entfernen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adressbuchrichtlinien finden Sie unter [Verfahren für Adressbuchrichtlinien](address-book-policy-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adressbuchrichtlinien" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Sie können eine ABP nicht entfernen, wenn sie dem Postfach eines Benutzers oder einem vorläufig gelöschten Postfach zugewiesen ist. Um zu ermitteln, ob eine ABP einem Benutzer zugewiesen ist, führen Sie folgenden Befehl in der Shell aus:
    
    `Get-Mailbox | Where $._AddressBookPolicy -eq <AddressBookPolicyName>`
    
    Um zu ermitteln, ob eine ABP einem vorläufig gelöschten Postfach zugewiesen ist, führen Sie folgenden Befehl aus:
    
    `Get-Mailbox -SoftDeletedMailbox | Where $._AddressBookPolicy -eq <AddressBookPolicyName>`

  - Um eine ABP aus dem Postfach eines Benutzers zu entfernen, können Sie die Seite **Postfacheinstellungen** in den Eigenschaften des Postfachs oder das Cmdlet **Set-Mailbox** verwenden.

  - Eine ABP kann nicht in der Exchange-Verwaltungskonsole entfernt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Entfernen einer ABP mithilfe der Shell

In diesem Beispiel wird die ABP "ABP\_TailspinToys" entfernt.

    Remove-AddressBookPolicy -Identity "ABP_TailspinToys"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-AddressBookPolicy](https://technet.microsoft.com/de-de/library/hh529929\(v=exchg.150\)).


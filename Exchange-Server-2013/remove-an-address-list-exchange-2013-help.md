---
title: 'Entfernen einer Adressliste: Exchange 2013 Help'
TOCTitle: Entfernen einer Adressliste
ms:assetid: 39a313f3-41d4-4c8f-af67-df2316f3687f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997294(v=EXCHG.150)
ms:contentKeyID: 50475330
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer Adressliste

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-14_

In diesem Thema wird das Entfernen einer Adressliste erläutert. Sie können die standardmäßige globale Adressliste (GAL) nicht entfernen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adresslisten finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adresslisten" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Sie können keine übergeordnete Adressliste entfernen, die untergeordnete Adresslisten enthält. Sie können jedoch die unter- und übergeordneten Adresslisten zusammen entfernen, indem Sie auf der Tastatur STRG gedrückt halten und dann die unter- und übergeordneten Adresslisten auswählen. Wenn Sie versuchen, eine übergeordnete Adressliste zu entfernen, ohne die untergeordnete Adressliste zu entfernen, tritt ein Fehler auf.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Entfernen einer Adressliste mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Adressliste**.

2.  Wählen Sie in der Listenansicht die Adressliste aus, die Sie entfernen möchten, und klicken Sie auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

3.  Klicken Sie im Warnungsdialogfeld auf **Ja**, um die Adressliste zu entfernen.

## Verwenden der Shell zum Entfernen einer Adressliste

In diesem Beispiel wird die Adressliste "Sales Department" entfernt, die keine untergeordneten Adresslisten enthält.

```powershell
Remove-AddressList -Identity "Sales Department"
```

Geben Sie **J** ein, um das Entfernen dieser Adressliste zu bestätigen, und drücken Sie dann die EINGABETASTE.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-AddressList](https://technet.microsoft.com/de-de/library/bb124342\(v=exchg.150\)).

## Verwenden der Shell zum Entfernen einer Adressliste mit untergeordneten Adresslisten

In diesem Beispiel wird die übergeordnete Adressliste "Departments" mit allen untergeordneten Adresslisten entfernt.

```powershell
Remove-AddressList -Identity Departments -Recursive
```

Geben Sie **J** ein, um das Entfernen der über- und untergeordneten Adresslisten zu bestätigen, und drücken Sie dann die EINGABETASTE.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-AddressList](https://technet.microsoft.com/de-de/library/bb124342\(v=exchg.150\)).


---
title: 'Aktualisieren einer Adressliste: Exchange 2013 Help'
TOCTitle: Aktualisieren einer Adressliste
ms:assetid: 163e7099-cf14-4bb0-a84c-1401e9db670e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996375(v=EXCHG.150)
ms:contentKeyID: 50475154
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.Mailbox.UpdateAddressListWizardForm.ScheduleWizardPage
ms.translationtype: HT
---

# Aktualisieren einer Adressliste

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-14_

Adresslisten sind eine Sammlung von Empfänger- und anderen Active Directory-Objekten. Eine Adressliste wird angewendet, wenn die Filterregel für Adresslisten bearbeitet wurde. Um die Mitgliedschaft der Adressliste so zu aktualisieren, dass neue Empfänger aufgenommen und die Empfänger, die die Filterkriterien nicht mehr erfüllen, entfernt werden, müssen Sie die Adressliste anwenden.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adresslisten finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Abhängig von der Anzahl von Empfängern in der Adressliste kann der Vorgang sehr viel Zeit in Anspruch nehmen.

  - Einige Adresslisten enthalten abhängig von der Größe Ihrer Organisation und den Filtern, die Sie zur Adressliste hinzugefügt haben, Tausende oder Zehntausende Empfänger. Das Aktualisieren der Adresslisten kann sich als überaus ressourcenintensiv erweisen. Daher sollten Sie die Adressliste außerhalb der Spitzenzeiten aktualisieren.

  - Wenn die Adressliste mehr als 3.000 Empfänger enthält, sollten Sie die Adressliste mithilfe der Exchange-Verwaltungsshell aktualisieren.

Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktualisieren einer Adressliste mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Adressliste**.

2.  Wählen Sie in der Listenansicht die Adressliste aus, die aktualisiert werden soll.

3.  Klicken Sie im Detailbereich auf **Aktualisieren**.

## Aktualisieren einer Adressliste mithilfe der Shell

In diesem Beispiel wird die Adressliste "Washington State" aktualisiert.

```powershell
Update-AddressList "Washington State"
```

Wenn Sie mehrere Adresslisten gleichen Namens haben, müssen Sie den vollständigen Pfad zu der zu aktualisierenden Adressliste angeben. Wenn Sie beispielsweise die Adressliste "Sales" unter "North America" aktualisieren möchten, es aber ebenfalls eine Adressliste "Sales" unter "Europe" gibt, verwenden Sie den folgenden Befehl:

```powershell
    Update-AddressList "North America\Sales"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Update-AddressList](https://technet.microsoft.com/de-de/library/aa997982\(v=exchg.150\)).


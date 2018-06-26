---
title: 'Exportieren von vertraulichen DLP-Informationstypen aus Exchange 2013: Exchange Online Help'
TOCTitle: Exportieren von vertraulichen DLP-Informationstypen aus Exchange
ms:assetid: 8f02fbc2-dd1c-4276-be1a-517a43fe39b2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn479225(v=EXCHG.150)
ms:contentKeyID: 59634165
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Exportieren von vertraulichen DLP-Informationstypen aus Exchange 2013

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-05-04_

Sie können anzeigen oder ändern die Details innerhalb Ihrer DLP-Richtlinien, ohne mit dem Exchange-Verwaltungskonsole (EAC) oder Exchange-Verwaltungsshell-Cmdlets die Richtlinien exportieren, als XML-Datei speichern und diese XML-Datei ändern. In der Regel würden Sie dann die XML-Datei wieder in Exchange importieren. Auf diese Weise können Richtlinien unabhängig von Exchange bearbeitet werden. Sie müssen jedoch bestimmtes Format-Anforderungen, auch als XML-Schema, um die korrekte bezeichnet erfüllen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit DLP finden Sie unter [Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verhinderung von Datenverlust (Data Loss Prevention, DLP)" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

Das EAC stellt keine Möglichkeit zum Exportieren von DLP-Richtlinien oder -Vorlagen in eine externe Datei bereit. Führen Sie diese Aufgabe mit Exchange-Verwaltungsshell durch.

## Verwenden Sie die Exchange-Verwaltungsshell So exportieren Sie die vertrauliche DLP-Informationstypen

In diesem Beispiel werden alle vertraulichen DLP-Informationstypen zusammen mit ihren Attributen in einer XML-Datei unter dem Pfad "C:\\My Documents\\exportedInformationTypes.xml" exportiert. Sie sollten eine Sicherungskopie Ihrer aktuellen Sammlung für vertrauliche DLP-Informationstypen vornehmen. Dazu können Sie die XML-Datei exportieren und diese dann sofort kopieren und umbenennen.

1.  Öffnen Sie Exchange-Verwaltungsshell.

2.  Geben Sie **Get-ClassificationRuleCollection** ein, um die vertraulichen Informationstypen Ihrer Organisation auf dem Bildschirm anzuzeigen. Wenn Sie keine eigenen vertraulichen Informationstypen erstellt haben, werden nur die standardmäßigen, integrierten vertraulichen Informationstypensammlungen mit der Bezeichnung "Microsoft-Regelpaket" angezeigt.

3.  Speichern Sie vertrauliche Informationstypen durch Eingabe von **$ruleCollections = Get-ClassificationRuleCollection** in einer Variablen.

4.  Erstellen Sie jetzt durch Eingabe von **Set-Content -path "C:\\My Documents\\exportedRules.xml" -Encoding Byte -Value $ruleCollections.SerializedClassificationRuleCollection** eine formatierte XML-Datei mit allen Daten.

Jetzt können Sie die XML-Datei bearbeiten, um die Richtlinien ggf. anzupassen. Informationen zum Anpassen der integrierten vertraulichen Informationstypen finden Sie unter [Anpassen der integrierten vertraulichen DLP-Informationstypen](customize-the-built-in-dlp-sensitive-information-types-exchange-2013-help.md). Informationen zum Rückimportieren von Richtlinien in Exchange finden Sie unter [Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md).

## Weitere Informationen

[Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md)

[Anpassen der integrierten vertraulichen DLP-Informationstypen](customize-the-built-in-dlp-sensitive-information-types-exchange-2013-help.md)

[Importieren einer benutzerdefinierten DLP-Richtlinienvorlage aus einer Datei](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md)


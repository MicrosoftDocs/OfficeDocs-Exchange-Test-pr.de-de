---
title: 'Schutz von Formulardaten durch Dokumentfingerabdrücke: Exchange 2013 Help'
TOCTitle: Schutz von Formulardaten durch Dokumentfingerabdrücke
ms:assetid: 110c839b-7693-42f6-aa5d-58ce64f4c357
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn635175(v=EXCHG.150)
ms:contentKeyID: 61201331
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Schutz von Formulardaten durch Dokumentfingerabdrücke

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-09-11_

Wenn in Ihrem Unternehmen Formulare zur Zusammenfassung vertraulicher Informationen verwendet werden, kann es passieren, dass Benutzer diese Formulare an Kontakte außerhalb des Unternehmens senden, was ein Sicherheitsrisiko darstellt. Verhinderung von Datenverlust (Data Loss Prevention, DLP) in Exchange hilft Ihnen, diese Informationen zu schützen, indem sie an ihrem [Dokumentfingerabdrücke](overview-of-document-fingerprinting-in-exchange.md) erkannt werden. Wenn Sie Dokumentfingerabdrücke verwenden möchten, laden Sie einfach ein leeres Formular hoch, z. B. ein Dokument zu geistigem Eigentum, ein Behördenformular oder ein anderes in Ihrem Unternehmen verwendetes Formular. Fügen Sie dann dessen Dokumentfingerabdruck zu einer DLP-Richtlinie oder Transportregeln hinzu. Vorgehensweise:

> [!VIDEO https://www.microsoft.com/de-de/videoplayer/embed/581259e7-06ca-402f-a9f5-83b519bd01d1]

## Erstellen eines Dokumentfingerabdrucks mithilfe der Exchange-Verwaltungskonsole

![Pfad zum Erstellen eines digitalen Dokumentfingerabdrucks in EAC hervorgehoben](images/Dn635175.e8562ea7-40ba-4feb-adde-2e81f029fcda(EXCHG.150).png "Pfad zum Erstellen eines digitalen Dokumentfingerabdrucks in EAC hervorgehoben")

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Klicken Sie auf **Verwalten von Dokumentfingerabdrücken**.

3.  Klicken Sie auf der Seite "Dokumentfingerabdrücke" auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um einen neuen Dokumentfingerabdruck zu erstellen.

4.  Geben Sie dem Dokumentfingerabdruck einen **Namen**, und fügen Sie eine **Beschreibung** hinzu. (Der von Ihnen gewählte Name erscheint dann in der Liste der Arten von vertraulichen Informationen.)

5.  Klicken Sie zum Hochladen eines Formulars auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

6.  Wählen Sie ein Formular, und klicken Sie auf **Öffnen**. (Stellen Sie sicher, dass die Datei, die Sie hochladen, Text enthält, nicht kennwortgeschützt ist und zu den in Transportregeln unterstützten Dateitypen gehört. Eine Liste der unterstützten Dateitypen finden Sie unter [Überprüfen von Nachrichtenanlagen mithilfe von Nachrichtenflussregeln](https://technet.microsoft.com/de-de/library/jj919236\(v=exchg.150\)). Andernfalls erhalten Sie eine Fehlermeldung, wenn Sie den Fingerabdruck erstellen.) Wiederholen Sie den Vorgang für jede zusätzliche Datei, die Sie zur Dokumentenliste für diesen Dokumentfingerabdruck hinzufügen möchten. Sie können auch später Dateien von diesem Dokumentfingerabdruck entfernen oder zu ihm hinzufügen.

7.  Klicken Sie auf **Speichern**.

Der Dokumentfingerabdruck gehört nun zu den vertraulichen Informationen, und Sie können Ihn mithilfe der Bedingung **Die Nachricht enthält vertrauliche Informationen** zu einer DLP-Richtlinie oder einer Transportregel hinzufügen.

![Bedingung "Diese Regel anwenden, wenn" hervorgehoben](images/Dn635175.9355a513-a790-48eb-a61b-575ba2ecdfa6(EXCHG.150).png "Bedingung \"Diese Regel anwenden, wenn\" hervorgehoben")

Weitere Informationen zum Hinzufügen von Regeln zu einer DLP-Richtlinie finden Sie unter [Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md) im Abschnitt “Ändern einer DLP-Richtlinie”, und weitere Informationen über das Ändern von Transportregeln finden Sie unter [Integrieren von Regeln für vertrauliche Informationen in Transportregeln](integrating-sensitive-information-rules-with-transport-rules-exchange-2013-help.md). Informationen zum Erstellen einer neuen Richtlinie finden Sie unter [Erstellen einer DLP-Richtlinie aus einer Vorlage](how-to-new-dlp-data-loss-prevention-policy-template.md).

## Verwenden Sie die Shell zur Erstellung eines Klassifizierungsregelpakets auf Grundlage des Dokumentfingerabdrucks


> [!TIP]
> Auch wenn Sie in der Shell Regelpakete erstellen und ändern können, könnte Ihnen das Erstellen von Dokumentfingerabdrücken in der EAC etwas einfacher erscheinen. Wir empfehlen, dies zu versuchen, bevor Sie dieses Verfahren in der Shell ausführen.



DLP verwendet Klassifizierungsregelpakete zur Erkennung vertraulicher Inhalte in Nachrichten. Verwenden Sie zur Erstellung eines Klassifizierungsregelpakets auf Grundlage eines Dokumentfingerabdrucks die Cmdlets **New-Fingerprint** und **New-DataClassification**. Da die Ergebnisse von **New-Fingerprint** nicht außerhalb der Datenklassifizierungsregel gespeichert werden, führen Sie **New-Fingerprint** und **New-DataClassification** oder **Set-DataClassification** immer in derselben PowerShell-Sitzung aus. Im folgenden Beispiel wird ein neuer Dokumentfingerabdruck basierend auf der Datei "C:\\Eigene Dateien\\Contoso Employee Template.docx" erstellt. Sie speichern den neuen Fingerabdruck als Variable, damit Sie ihn mit dem Cmdlet **New-DataClassification** in derselben PowerShell-Sitzung verwenden können.

    $Employee_Template = Get-Content "C:\My Documents\Contoso Employee Template.docx" -Encoding byte
    $Employee_Fingerprint = New-Fingerprint -FileData $Employee_Template -Description "Contoso Employee Template"

Lassen Sie uns nun eine neue Datenklassifizierungsregel namens "Contoso Employee Confidential" erstellen, die den Dokumentfingerabdruck auf der Datei "C:\\Eigene Dateien\\Contoso Customer Information Form.docx" verwendet.

    $Employee_Template = Get-Content "C:\My Documents\Contoso Customer Information Form.docx" -Encoding byte
    $Customer_Fingerprint = New-Fingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
    New-DataClassification -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information." 

Nun können Sie das Cmdlet **Get-DataClassification** verwenden, um nach allen DLP-Datenklassifizierungsregelpaketen zu suchen. In diesem Beispiel befindet sich “Contoso Customer Confidential” auf der Liste der Datenklassifizierungsregelpakete.

Fügen Sie abschließend das Datenklassifizierungsregelpaket “Contoso Customer Confidential” zu einer DLP-Richtlinie hinzu.

    New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}

Der DLP Agent erkennt nun Dokumente, die zum Dokumentfingerabdruck von "Contoso Customer Form.docx" passen.

Informationen zu Syntax und Parametern finden Sie unter [New-Fingerprint](https://technet.microsoft.com/de-de/library/dn584142\(v=exchg.150\)), [New-DataClassification](https://technet.microsoft.com/de-de/library/dn584139\(v=exchg.150\)), [Set-DataClassification](https://technet.microsoft.com/de-de/library/dn584141\(v=exchg.150\)) und [Get-DataClassification](https://technet.microsoft.com/de-de/library/jj215720\(v=exchg.150\)).

## Weitere Informationen

[Dokumentfingerabdrücke](overview-of-document-fingerprinting-in-exchange.md)

[Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md)

[Integrieren von Regeln für vertrauliche Informationen in Transportregeln](integrating-sensitive-information-rules-with-transport-rules-exchange-2013-help.md)


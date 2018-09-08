---
title: 'Verwalten von E-Mail-Infos für Organisationsbeziehungen: Exchange 2013 Help'
TOCTitle: Verwalten von E-Mail-Infos für Organisationsbeziehungen
ms:assetid: 6e6b48ef-c41c-47ad-8063-66901765c2a5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ649324(v=EXCHG.150)
ms:contentKeyID: 50475914
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von E-Mail-Infos für Organisationsbeziehungen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können benutzerdefinierte Einstellungen für E-Mail-Infos zwischen verschiedenen Organisationen über die Exchange-Verwaltungsshell konfigurieren.

Durch das Einrichten einer Organisationsbeziehung können Sie die Benutzererfahrung für beide Organisationen verbessern, indem Frei/Gebucht-Daten freigegeben, der sichere Meldungsfluss konfiguriert und die Nachverfolgung von Nachrichten aktiviert wird. Weitere Informationen zu Organisationsbeziehungen finden Sie unter [E-Mail-Infos über Organisationsbeziehungen](https://technet.microsoft.com/de-de/library/JJ670165(v=EXCHG.150)).

Sie können mithilfe von verschiedenen Einstellungen steuern, wie E-Mail-Infos zwischen Organisationen verwendet werden, für die eine Organisationsbeziehung eingerichtet wurde. Die Verfahren in diesem Abschnitt veranschaulichen diese verschiedenen Steuermöglichkeiten. In sämtlichen Beispielen wird "contoso.com" als lokale Organisation und "online.contoso.com" als Remoteorganisation verwendet, und die Organisationsbeziehung wird als "Contoso Online" bezeichnet.

Verwenden Sie das Cmdlet **Set-OrganizationRelationship**, um diese Einstellungen zu konfigurieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Infos" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Aktivieren oder Deaktivieren von E-Mail-Infos zwischen zwei Organisationen

In diesem Beispiel wird die Organisationsbeziehung so konfiguriert, dass E-Mail-Infos an Absender in der Remoteorganisation zurückgegeben werden, wenn Nachrichten für Empfänger in Ihrer Organisation erstellt werden.

    Set-OrganizationRelationship "Contoso Online" -MailTipsAccessEnabled $true

In diesem Beispiel wird die Organisationsbeziehung so konfiguriert, dass keine E-Mail-Infos an Absender in der Remoteorganisation zurückgegeben werden, wenn Nachrichten für Empfänger in Ihrer Organisation erstellt werden.

    Set-OrganizationRelationship "Contoso Online" -MailTipsAccessEnabled $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OrganizationRelationship](https://technet.microsoft.com/de-de/library/ee332326\(v=exchg.150\)).

## Verwenden der Shell zum Konfigurieren, welche E-Mail-Infos an die Remoteorganisation zurückgegeben werden

Sie können für jede Organisationsbeziehung bestimmen, welche Gruppe von E-Mail-Infos an Absender in der anderen Organisation zurückgegeben werden. In diesem Beispiel für die Organisationsbeziehung so konfiguriert, dass alle E-Mail-Infos zurückgegeben werden.

    Set-OrganizationRelationship "Contoso Online" -MailTipsAccessLevel All

In diesem Beispiel wird die Organisationsbeziehung so konfiguriert, dass nur die E-Mail-Infos für automatische Antworten, übergroße Nachrichten, eingeschränkte Empfänger und volle Postfächer zurückgegeben werden.

    Set-OrganizationRelationship "Contoso Online" -MailTipsAccessLevel Limited

In diesem Beispiel für die Organisationsbeziehung so konfiguriert, dass keine E-Mail-Infos zurückgegeben werden.


> [!NOTE]
> Verwenden Sie diese Methode nicht, um für diese Beziehung E-Mail-Infos zu deaktivieren. Legen Sie zum Deaktivieren von E-Mail-Infos den Parameter <EM>MailTipsAccessEnabled</EM> auf <CODE>$false</CODE> fest.



    Set-OrganizationRelationship "Contoso Online" -MailTipsAccessLevel None

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OrganizationRelationship](https://technet.microsoft.com/de-de/library/ee332326\(v=exchg.150\)).

## Verwenden der Shell zum Konfigurieren einer bestimmten Gruppe von Benutzern, von denen empfängerspezifische E-Mail-Infos zurückgegeben werden

Sie können die Rückgabe empfängerspezifischer E-Mail-Infos nicht auf eine bestimmte Gruppe von Benutzern einschränken. Bei der Aktivierung von E-Mail-Infos für eine Organisationsbeziehung werden standardmäßig die folgenden empfängerspezifischen E-Mail-Infos für alle Benutzer zurückgegeben:

  - Automatische Antworten

  - Postfach voll

  - Benutzerdefinierte E-Mail-Infos

Sie können eine E-Mail-Info-Zugriffsgruppe für die Organisationsbeziehung festlegen. Nachdem sie eine Gruppe angegeben haben, werden die empfängerspezifischen E-Mail-Infos nur für Postfächer, E-Mail-Kontakte und E-Mail-Benutzer zurückgegeben, die Mitglied dieser Gruppe sind. In diesem Beispiel wird die Organisationsbeziehung so konfiguriert, dass die empfängerspezifischen E-Mail-Infos nur für Mitglieder der Gruppe "ShareMailTips@contoso.com" zurückgegeben werden.

    Set-OrganizationRelationship "Contoso Online" -MailTipsAccessScope ShareMailTips@contoso.com

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OrganizationRelationship](https://technet.microsoft.com/de-de/library/ee332326\(v=exchg.150\)).


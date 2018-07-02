---
title: 'Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle: Exchange 2013 Help'
TOCTitle: Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle
ms:assetid: c7188d53-e672-492b-b57d-cd711379ddb3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff459262(v=EXCHG.150)
ms:contentKeyID: 50553886
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-12-02_

Anhand der Administratorüberwachungsprotokolle können Sie ermitteln, welche Benutzer Änderungen an der Organisations-, Server- und Empfängerkonfiguration vorgenommen haben. Dies kann nützlich sein, um die Ursache eines unerwarteten Verhaltens oder einen böswilligen Administrator zu ermitteln bzw. die Einhaltung von Vorschriften zu überprüfen. Weitere Informationen zur Administrator-Überwachungsprotokollierung finden Sie unter [Administratorüberwachungsprotokollierung](administrator-audit-logging-exchange-2013-help.md).

Informationen zum Durchsuchen des Postfachüberwachungsprotokolls finden Sie unter [Überwachungsprotokollierung von Postfächern](mailbox-audit-logging-exchange-2013-help.md).


> [!TIP]
> In Exchange Online können Sie die Exchange-Verwaltungskonsole verwenden, um Einträge aus dem Administrator-Überwachungsprotokoll anzeigen zu lassen. Weitere Informationen finden Sie unter <A href="view-the-administrator-audit-log-exchange-2013-help.md">Anzeigen des Administratorüberwachungsprotokolls</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: Weniger als 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Überwachungsprotokollierung durch Administratoren mit Leserechten" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Die Administrator-Überwachungsprotokollierung ist standardmäßig aktiviert. Führen Sie zur Sicherstellung, dass die Administrator-Überwachungsprotokollierung aktiviert wurde, folgenden Befehl aus:
    
        Get-AdminAuditLogConfig | FL AdminAuditLogEnabled
    
    Ein Wert von `True` gibt an, dass die Administrator-Überwachungsprotokollierung aktiviert ist. Ein Wert von `False` gibt an, dass sie deaktiviert ist. Wenn Sie die Administrator-Überwachungsprotokollierung für eine lokale Exchange-Organisation aktivieren möchten, führen Sie den folgenden Befehl aus:
    
        Set-AdminAuditLogConfig -AdminAuditLogEnabled $true
    

    > [!NOTE]
    > Das Cmdlet <STRONG>Set-AdminAuditLogConfig</STRONG> steht in Exchange Online nicht zur Verfügung.

    
    Weitere Informationen finden Sie unter [Verwalten der Administratorüberwachungsprotokollierung](manage-administrator-audit-logging-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Ausführen des Berichts mit Änderungen an Verwaltungsrollengruppen über die Exchange-Verwaltungskonsole

Änderungen an der Mitgliedschaft in Verwaltungsrollengruppen, die in Rollengruppen innerhalb Ihrer Organisation vorgenommen wurden, können anhand des Administrator-Rollengruppenberichts in der Exchange-Verwaltungskonsole ermittelt werden. Anhand dieses Berichts kann eine Liste mit Rollengruppen angezeigt werden, die innerhalb eines angegebenen Datumsbereichs geändert wurden. Zudem können die Änderungen an bestimmten Rollengruppen angezeigt werden.

1.  Wählen Sie in der Exchange-Verwaltungskonsole **Verwaltung der Richtlinientreue** \> **Überwachung** aus, und klicken Sie anschließend auf **Administrator-Rollengruppenbericht ausführen**.

2.  Wählen Sie über die Felder **Startdatum** und **Enddatum** einen Datumsbereich aus.

3.  Klicken Sie auf **Rollengruppen auswählen**, und wählen Sie anschließend die Rollengruppen aus, deren Änderungen Sie prüfen möchten, oder lassen Sie dieses Feld leer, um in allen Rollengruppen nach Änderungen zu suchen.

4.  Klicken Sie auf **Suchen**.

Wenn anhand der angegebenen Kriterien Änderungen ermittelt werden, wird im Bereich **Ergebnisse** eine Liste der Änderungen angezeigt. Beim Klicken auf eine Rollengruppe werden die Änderungen an der Rollengruppe im Detailbereich angezeigt.

## Exportieren des Administratorüberwachungsprotokolls mithilfe der Exchange-Verwaltungskonsole

Um eine XML-Datei mit den an Ihrer Organisation vorgenommenen Änderungen zu erstellen, können Sie in der Exchange-Verwaltungskonsole den Bericht "Administratorüberwachungsprotokoll" verwenden. Anhand dieses Berichts kann ein Datumsbereich für die Suche nach Überwachungsprotokolleinträgen mit Änderungen angegeben werden, die von bestimmten Benutzern vorgenommen wurden. Die XML-Datei wird anschließend als E-Mail-Anlage an einen Empfänger gesendet. Die maximale Größe der XML-Datei beträgt 10 MB.


> [!NOTE]
> In Outlook Web App ist es standardmäßig nicht möglich, XML-Anlagen zu öffnen. Sie können Exchange entweder so konfigurieren, dass XML-Anlagen mit Outlook Web App angezeigt werden können, oder Sie verwenden einen anderen E-Mail-Client, beispielsweise Microsoft Outlook, um die Anlage anzuzeigen. Informationen zum Konfigurieren von Outlook Web App zum Zulassen der Anzeige einer XML-Anlage finden Sie unter <A href="view-or-configure-outlook-web-app-virtual-directories-exchange-2013-help.md">Anzeigen oder Konfigurieren der virtuellen Outlook Web App-Verzeichnisse</A>.



1.  Wählen Sie in der Exchange-Verwaltungskonsole **Verwaltung der Richtlinientreue** \> **Überwachung** aus, und klicken Sie anschließend auf **Administratorüberwachungsprotokoll exportieren**.

2.  Wählen Sie über die Felder **Startdatum** und **Enddatum** einen Datumsbereich aus.

3.  Klicken Sie im Feld **Überwachungsbericht senden an** auf **Benutzer auswählen**, und wählen Sie anschließend den Empfänger aus, an den der Bericht gesendet werden soll.

4.  Klicken Sie auf **Exportieren**.

Wenn anhand der angegebenen Kriterien Protokolleinträge ermittelt werden, wird eine XML-Datei erstellt und als E-Mail-Anlage an den angegebenen Empfänger gesendet.

## Suchen nach Überwachungsprotokolleinträgen mithilfe der Shell

Sie können die Shell zur Suche nach Überwachungsprotokolleinträgen verwenden, die mit angegebenen Kriterien übereinstimmen. Eine Liste mit Suchkriterien finden Sie unter [Administratorüberwachungsprotokollierung](administrator-audit-logging-exchange-2013-help.md). Bei diesem Verfahren wird das Cmdlet **Search-AdminAuditLog** verwendet, und die Suchergebnisse werden in der Shell angezeigt. Dieses Cmdlet kann verwendet werden, wenn eine Ergebnismenge zurückgegeben werden muss, die die im Cmdlet **New-AdminAuditLogSearch** oder in den Überwachungsberichten der Exchange-Verwaltungskonsole definierten Grenzwerte überschreitet.

Informationen zum Versenden der Suchergebnisse für Überwachungsprotokolle als E-Mail-Anlage an einen Empfänger finden Sie unter Suchen nach Überwachungsprotokolleinträgen und Senden der Ergebnisse an einen Empfänger mithilfe der Shell weiter unten in diesem Thema.

Verwenden Sie die folgende Syntax, um das Überwachungsprotokoll anhand angegebener Kriterien zu durchsuchen.

    Search-AdminAuditLog - Cmdlets <cmdlet 1, cmdlet 2, ...> -Parameters <parameter 1, parameter 2, ...> -StartDate <start date> -EndDate <end date> -UserIds <user IDs> -ObjectIds <object IDs> -IsSuccess <$True | $False >


> [!NOTE]
> Das Cmdlet <STRONG>Search-AdminAuditLog</STRONG> gibt standardmäßig maximal 1.000&nbsp;Protokolleinträge zurück. Verwenden Sie den Parameter <EM>ResultSize</EM>, um 250.000&nbsp;Protokolleinträge festzulegen. Um sämtliche Einträge zurückzugeben, verwenden Sie den Wert <CODE>Unlimited</CODE>.



In diesem Beispiel wird eine Suche nach allen Überwachungsprotokolleinträgen ausgeführt, welche die folgenden Kriterien erfüllen:

  - **Startdatum**   04/08/2012

  - **Enddatum**   03/10/2012

  - **Benutzer-IDs**   davids, chrisd, kima

  - **Cmdlets** **Set-Mailbox**

  - **Parameter** *ProhibitSendQuota*, *ProhibitSendReceiveQuota*, *IssueWarningQuota*, *MaxSendSize*, *MaxReceiveSize*

<!-- end list -->

    Search-AdminAuditLog -Cmdlets Set-Mailbox -Parameters ProhibitSendQuota, ProhibitSendReceiveQuota, IssueWarningQuota, MaxSendSize, MaxReceiveSize -StartDate 08/04/2012 -EndDate 10/03/2012 -UserIds davids, chrisd, kima

In diesem Beispiel werden Änderungen an einem bestimmten Postfach ermittelt. Dies ist bei der Problembehebung nützlich, oder wenn Sie Informationen für eine Untersuchung bereitstellen müssen. Die folgenden Kriterien werden verwendet:

  - **Startdatum**   05/01/2012

  - **Enddatum**   03/10/2012

  - **Objekt-ID**   contoso.com/Users/DavidS

<!-- end list -->

    Search-AdminAuditLog -StartDate 05/01/2012 -EndDate 10/03/2012 -ObjectID contoso.com/Users/DavidS

Wenn bei Ihrer Suche eine Vielzahl von Protokolleinträgen zurückgegeben werden, wird die unter Suchen nach Überwachungsprotokolleinträgen und Senden der Ergebnisse an einen Empfänger mithilfe der Shell weiter unten in diesem Thema beschriebene Vorgehensweise empfohlen. Bei dieser Vorgehensweise wird eine XML-Datei als E-Mail-Anlage an die angegebenen Empfänger gesendet, sodass die relevanten Daten einfacher extrahiert werden können.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Search-AdminAuditLog](https://technet.microsoft.com/de-de/library/ff459250\(v=exchg.150\)).

## Anzeigen der Details von Überwachungsprotokolleinträgen

Das Cmdlet **Search-AdminAuditLog** gibt die im Abschnitt "Inhalte von Überwachungsprotokollen" unter [Administratorüberwachungsprotokollierung](administrator-audit-logging-exchange-2013-help.md) beschriebenen Felder zurück. Zwei der zurückgegebenen Felder, **CmdletParameters** und **ModifiedProperties**, enthalten zusätzliche Informationen, die standardmäßig nicht angezeigt werden.

Führen Sie die folgenden Schritte aus, um die Inhalte der Felder **CmdletParameters** und **ModifiedProperties** anzuzeigen. Alternativ können Sie die unter Suchen nach Überwachungsprotokolleinträgen und Senden der Ergebnisse an einen Empfänger mithilfe der Shell weiter unten in diesem Thema beschriebenen Schritte ausführen, um eine XML-Datei zu erstellen.

In dieser Vorgehensweise werden die folgenden Konzepte verwendet:

  - [Arrays](https://technet.microsoft.com/de-de/library/aa998267\(v=exchg.150\))

  - [Benutzerdefinierte Variablen](https://technet.microsoft.com/de-de/library/bb123690\(v=exchg.150\))

<!-- end list -->

1.  Legen Sie die Suchkriterien fest, führen Sie das Cmdlet **Search-AdminAuditLog** aus, und speichern Sie die Ergebnisse über den folgenden Befehl in einer Variablen.
    
        $Results = Search-AdminAuditLog <search criteria>

2.  Jeder Überwachungsprotokolleintrag wird als Arrayelement in der Variablen `$Results` gespeichert. Zur Auswahl eines Arrayelements geben Sie den Arrayelementindex an. Arrayelementindizes beginnen für das erste Arrayelement bei 0. Verwenden Sie beispielsweise den folgenden Befehl, um das fünfte Arrayelement (mit dem Index 4) abzurufen.
    
        $Results[4]

3.  Der oben stehende Befehl gibt den im Arrayelement 4 gespeicherten Protokolleintrag zurück. Zum Anzeigen der Felder **CmdletParameters** und **ModifiedProperties** für diesen Protokolleintrag verwenden Sie die folgenden Befehle.
    
        $Results[4].CmdletParameters
        $Results[4].ModifiedProperties

4.  Um die Inhalte der Felder **CmdletParameters** und **ModifiedParameters** in einem anderen Protokolleintrag anzuzeigen, ändern Sie den Arrayelementindex.

## Suchen nach Überwachungsprotokolleinträgen und Senden der Ergebnisse an einen Empfänger mithilfe der Shell

Sie können die Shell für die Suche nach Überwachungsprotokolleinträgen verwenden, die mit angegebenen Kriterien übereinstimmen, und die Ergebnisse anschließend als XML-Dateianlage an einen angegebenen Empfänger senden. Die Ergebnisse werden innerhalb von 15 Minuten an den Empfänger gesendet. Eine Liste mit Suchkriterien finden Sie unter [Administratorüberwachungsprotokollierung](administrator-audit-logging-exchange-2013-help.md).


> [!NOTE]
> In Outlook Web App ist es standardmäßig nicht möglich, XML-Anlagen zu öffnen. Sie können Exchange entweder so konfigurieren, dass XML-Anlagen mit Outlook Web App angezeigt werden können, oder Sie verwenden einen anderen E-Mail-Client, beispielsweise Microsoft Outlook, um die Anlage anzuzeigen. Informationen zum Konfigurieren von Outlook Web App zum Zulassen der Anzeige einer XML-Anlage finden Sie unter <A href="view-or-configure-outlook-web-app-virtual-directories-exchange-2013-help.md">Anzeigen oder Konfigurieren der virtuellen Outlook Web App-Verzeichnisse</A>.



Verwenden Sie die folgende Syntax, um das Überwachungsprotokoll anhand angegebener Kriterien zu durchsuchen.

    New-AdminAuditLogSearch -Cmdlets <cmdlet 1, cmdlet 2, ...> -Parameters <parameter 1, parameter 2, ...> -StartDate <start date> -EndDate <end date> -UserIds <user IDs> -ObjectIds <object IDs> -IsSuccess <$True | $False > -StatusMailRecipients <recipient 1, recipient 2, ...> -Name <string to include in subject>

In diesem Beispiel wird eine Suche nach allen Überwachungsprotokolleinträgen ausgeführt, welche die folgenden Kriterien erfüllen:

  - **Startdatum**   04/08/2012

  - **Enddatum**   03/10/2012

  - **Benutzer-IDs**   davids, chrisd, kima

  - **CmdletsSet-Mailbox**

  - **Parameter***ProhibitSendQuota*, *ProhibitSendReceiveQuota*, *IssueWarningQuota*, *MaxSendSize*, *MaxReceiveSize*

Der Befehl sendet die Ergebnisse in einer Nachricht mit der Betreffzeile "Mailbox limit changes" an die SMTP-Adresse "davids@contoso.com".

    New-AdminAuditLogSearch -Cmdlets Set-Mailbox -Parameters ProhibitSendQuota, ProhibitSendReceiveQuota, IssueWarningQuota, MaxSendSize, MaxReceiveSize -StartDate 08/04/2012 -EndDate 10/03/2012 -UserIds davids, chrisd, kima -StatusMailRecipients davids@contoso.com -Name "Mailbox limit changes"


> [!NOTE]
> Für den vom Cmdlet <STRONG>New-AdminAuditLogSearch</STRONG> generierten Bericht gilt eine Höchstgröße von 10&nbsp;MB. Wenn bei der Suche ein Bericht mit einer Größe von mehr als 10&nbsp;MB zurückgegeben wird, ändern Sie die angegebenen Suchkriterien. Verringern Sie z.&nbsp;B. den Datumsbereich, und führen Sie mehrere Berichte aus (für je einen Abschnitt des ursprünglichen Datumsbereichs).



Weitere Informationen zum Format der XML-Datei finden Sie unter [Administrator-Überwachungsprotokollstruktur](administrator-audit-log-structure-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-AdminAuditLogSearch](https://technet.microsoft.com/de-de/library/ff459243\(v=exchg.150\)).


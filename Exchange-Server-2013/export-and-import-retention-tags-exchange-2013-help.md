---
title: 'Exportieren und Importieren von Aufbewahrungstags: Exchange 2013 Help'
TOCTitle: Exportieren und Importieren von Aufbewahrungstags
ms:assetid: 18405ea2-7ccc-475e-bd84-8b040e17bf44
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ907307(v=EXCHG.150)
ms:contentKeyID: 51409270
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exportieren und Importieren von Aufbewahrungstags

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-11-15_

In verschiedenen Szenarien ist der Export oder Import von Aufbewahrungstags erforderlich:

  - Anwenden derselben Aufbewahrungsrichtlinien auf alle Server in einer Exchange-Organisation mit mehreren Gesamtstrukturen

  - Anwenden derselben Aufbewahrungsrichtlinien in einer Hybridbereitstellung, in der sich einige Postfächer in der lokalen Exchange-Organisation und einige in Exchange Online befinden.

  - Anwenden von Aufbewahrungsrichtlinien in einem Szenario zur Exchange-Archivierung, in dem Benutzer mit lokalen Exchange 2010- oder höheren Postfächern über ein cloudbasiertes Archiv verfügen.

In diesen Szenarien kann der Assistent für verwaltete Ordner ein Element, auf das ein Aufbewahrungstag angewandt wurde, ordnungsgemäß verarbeiten, nachdem das Element oder das Postfach in eine andere Organisation verschoben wurde.


> [!WARNING]
> Zum Synchronisieren von Aufbewahrungstags und Aufbewahrungsrichtlinien zwischen zwei Organisationen müssen Sie dieses Verfahren jedes Mal ausführen, wenn Sie Änderungen an einem Aufbewahrungstag oder einer -richtlinie vornehmen, um Aufbewahrungstags oder -richtlinien aus der Quellorganisation zu exportieren und in die Zielorganisation zu importieren.<BR>Sie können keine bestimmten Aufbewahrungstags oder -richtlinien für den Export auswählen. Mit dem Skript "Export-RetentionTags.ps1" werden alle Aufbewahrungstags und -richtlinien aus einer Organisation exportiert.



Weitere Verwaltungsaufgaben im Zusammenhang mit der Messaging-Datensatzverwaltung (MRM) finden Sie unter [Verfahren der Messaging-Datensatzverwaltung](messaging-records-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Verfahren in diesem Abschnitt hängen von folgenden drei Dateien im Ordner `%ExchangeInstallPath%Scripts` auf IhremExchange-Server:
    
      - Export-RetentionTags.ps1
    
      - Import-RetentionTags.ps1
    
      - MigrateRetentionTags.strings.psd1

  - Sie können keine bestimmten Aufbewahrungstags oder -richtlinien für den Export oder Import auswählen. Mit dem Skript "Export-RetentionTags.ps1" werden alle Aufbewahrungstags und -richtlinien aus einer Organisation exportiert. Das Skript "Import-RetentionTags.ps1" importiert alle in der XML-Datei für den Import befindlichen Aufbewahrungstags und -richtlinien und ersetzt dabei alle vorhandenen Aufbewahrungstags und -richtlinien in einer Exchange-Organisation.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Schritt 1: Exportieren von Aufbewahrungstags aus einer lokalen Exchange-Organisation

1.  Führen Sie diesen Exchange-Verwaltungsshell-Befehl aus, um das Verzeichnis in das Unterverzeichnis **Skripts** im Exchange-Installationspfad zu ändern.
    
        Cd $Env:ExchangeInstallPath\Scripts

2.  Führen Sie das Skript „Export-RetentionTags.ps1“ aus, um Aufbewahrungstags in eine XML-Datei zu exportieren.
    

    > [!IMPORTANT]
    > Wenn Sie Aufbewahrungstags und Aufbewahrungsrichtlinien nach Exchange Online importieren oder daraus exportieren, müssen Sie Ihre Windows PowerShell-Sitzung mit Exchange Online verbinden. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/jj984289(v=exchg.150)">Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell</A>.

    
        .\Export-RetentionTags.ps1 "c:\docs\ExportedRetentionTags.xml"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass Aufbewahrungstags und -richtlinien erfolgreich exportiert wurden:

1.  Wechseln Sie zu dem Pfad, den Sie im Exportbefehl angegeben haben, und stellen Sie sicher, dass die XML-Datei mit dem von Ihnen angegebenen Namen erstellt wurde.

2.  Optional können Sie die XML-Datei in einem Text-Editor öffnen und ihren Inhalt überprüfen.

## Schritt 2: Importieren von Aufbewahrungstags in eine Exchange-Organisation

1.  Führen Sie diesen Exchange-Verwaltungsshell-Befehl aus, um das Verzeichnis in das Unterverzeichnis **Skripts** im Exchange-Installationspfad zu ändern.
    
        Cd $Env:ExchangeInstallPath\Scripts

2.  Führen Sie das Skript „Import-RetentionTags.ps1“ aus, um Aufbewahrungstags aus einer zuvor exportierten XML-Datei zu importieren.
    

    > [!IMPORTANT]
    > Wenn Sie Aufbewahrungstags und Aufbewahrungsrichtlinien nach Exchange Online importieren oder daraus exportieren, müssen Sie Ihre Windows PowerShell-Sitzung mit Exchange Online verbinden. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/jj984289(v=exchg.150)">Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell</A>.

    

    > [!NOTE]
    > Wenn dieses Skript inExchange Online ausgeführt wird, werden Sie möglicherweise aufgefordert, zu bestätigen, dass Sie Software eines nicht vertrauenswürdigen Herausgebers ausführen möchten. Überprüfen Sie, ob der Name des Herausgebers <CODE>CN=Microsoft Corporation, OU=MOPR, O=Microsoft Corporation, L=Redmond, S=Washington, C=US</CODE> lautet, und klicken Sie auf <STRONG>R</STRONG>, um zuzulassen, dass das Skript einmal ausgeführt wird, oder auf <STRONG>A</STRONG>, um zuzulassen, dass es immer ausgeführt wird.

    
        .\Import-RetentionTags.ps1 "c:\docs\ExportedRetentionTags.xml"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass Aufbewahrungstags und -richtlinien erfolgreich importiert wurden:

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Aufbewahrungstags**, und stellen Sie sicher, dass die Aufbewahrungstags erfolgreich importiert wurden. Wechseln Sie zu **Verwaltung der Richtlinientreue** \> **Aufbewahrungsrichtlinien**, und stellen Sie sicher, dass die Aufbewahrungsrichtlinien erfolgreich importiert wurden.

2.  Stellen Sie mithilfe der Cmdlets **Get-RetentionPolicy** und **Get-RetentionPolicyTag** sicher, dass die Tags und Richtlinien erstellt wurden. Ein Beispiel zum Abrufen von Aufbewahrungstags und -richtlinien finden Sie unter "Beispiele" in den Themen [Get-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd298009\(v=exchg.150\)) und [Get-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd298086\(v=exchg.150\)).


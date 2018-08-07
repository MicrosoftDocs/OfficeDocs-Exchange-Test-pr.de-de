---
title: 'N. in Schemamasterstandort/-dom._NotInSchemaMasterDomain: Exchange 2013-Hilfe'
TOCTitle: Nicht in Schemamasterstandort/-domäne_NotInSchemaMasterDomain
ms:assetid: 5e44eb33-4c30-4c3d-ba68-5c30bef1731f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.notinschemamasterdomain(v=EXCHG.150)
ms:contentKeyID: 50475782
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Nicht in Schemamasterstandort/-domäne\_NotInSchemaMasterDomain

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft® Exchange Server 2007 kann nicht fortgesetzt werden, da sich der Computer, auf dem das Setup ausgeführt wird, nicht am selben Standort oder in der selben Domäne des Active Directory®-Verzeichnisdienstes befindet, wie der Server, der die Funktion des Domänenschemamasters innehat (auch Flexible Single Master Operations/FSMO genannt).

Für das Setup von Exchange 2007 ist erforderlich, dass sich der Domänencontroller, der als Domänenschemamaster fungiert, am selben Standort und in derselben Domäne befindet, wie der Computer, auf dem das Exchange-Setup ausgeführt wird.

Der Domänenschemamaster steuert alle Updates und Änderungen am Active Directory-Schema.

Führen Sie das Exchange Server 2007-Setup mithilfe der Parameter **/prepareschema** und **/prepareAD** vom gleichen Standort und der gleichen Domäne wie der Domänenschemamaster aus.

Weitere Informationen zu den **Befehlszeilenoptionen/PrepareSchemaund/PrepareAD** finden Sie im Exchange 2007-Produkt Dokumentation Thema "Wie zum Vorbereiten der Active Directory und Domänen" (<https://go.microsoft.com/fwlink/?linkid=78453>)

Die Funktion kann mit dem Schemamastertool angegeben werden. Damit das Schematool als MMC-Snap-In verfügbar ist muss jedoch die DLL „Schmmgmt.dll\&quot; registriert werden.

So zeigen Sie den aktuellen Schemamaster an

1.  Geben Sie an der Eingabeaufforderung **regsvr32 schmmgmt.dll** ein.
    

    > [!NOTE]
    > <STRONG>RegSvr32</STRONG> wurde erfolgreich registriert, wenn das folgende Dialogfeld angezeigt wird:<BR>DllRegisterServer in schmmgmt.dll erfolgreich.



2.  Klicken Sie zum Öffnen einer Verwaltungskonsole auf **Start** und dann auf **Ausführen**, und geben Sie anschließend **mmc** ein.

3.  Klicken Sie im Konsolenmenü auf **Snap-In hinzufügen/entfernen**.

4.  Klicken Sie auf**Hinzufügen**, um das Dialogfeld **Eigenständiges Snap-In hinzufügen** zu öffnen.

5.  Wählen Sie **Active Directory-Schema** aus, und klicken Sie dann auf **Hinzufügen**.

6.  „Active Directory Schema\&quot; wird unter „Snap-In hinzufügen/entfernen\&quot; angezeigt. Klicken Sie auf **Schließen**, und klicken Sie dann auf **OK**, um zur Konsole zurückzukehren.

7.  Wählen Sie **Active Directory-Schema** aus. Die Abschnitte **Klassen** und **Attribute** werden daraufhin auf der rechten Seite angezeigt.

8.  Klicken Sie mit der rechten Maustaste auf **Active Directory Schema**, und klicken Sie dann auf **Betriebsmaster**.

9.  Der aktuelle Schemamaster wird angezeigt.

Nachdem Sie den aktuellen Schemamaster identifiziert haben, bestimmen Sie, in welchem Subnetz sich der Schemamaster befindet. Verwenden Sie eine der folgenden Methoden, um Exchange zu installieren:

  - Ändern Sie das Subnetz auf dem Exchange-Server, um es an den Standort zu verschieben, an dem sich der Schemamaster befindet. Installieren Sie dann Exchange.

  - Erzwingen Sie vorübergehend eine Änderung der Standortmitgliedschaft auf dem Exchange-Server, und installieren Sie Exchange. Nach der Installation von Exchange setzen Sie den Exchange-Server auf seinen ursprünglichen Standort zurück.

So erzwingen Sie die Standortmitgliedschaft

1.  Starten Sie auf dem Server, auf dem Sie Exchange installieren möchten, den Registrierungs-Editor. Klicken Sie dazu auf **Start**, dann auf **Ausführen**, geben Sie **regedit** ein, und klicken Sie dann auf **OK**.

2.  Wechseln Sie zu folgendem Registrierungsunterschlüssel:
    
    **HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\Netlogon\\Parameters**

3.  Erstellen Sie den folgenden neuen **Zeichenfolgen**wert:
    
    Wertname: **SiteName**
    
    Werttyp: **REG\_SZ**
    
    Wertdaten: **\< Standort,\_der\_den\_Schemamaster\_enthält \>**

4.  Beenden Sie den Registrierungs-Editor, und starten Sie den Netlogon-Dienst neu. Diese Aktion zwingt den Exchange-Server zur Teilnahme an dem von Ihnen angegebenen Standort.

5.  Installieren Sie Exchange.

6.  Entfernen Sie den Registrierungseintrag, den Sie in Schritt 3 hinzugefügt haben.

7.  Starten Sie den Netlogon-Dienst neu. Durch diese Aktion wird Exchange auf den ursprünglichen Standort zurückgesetzt.


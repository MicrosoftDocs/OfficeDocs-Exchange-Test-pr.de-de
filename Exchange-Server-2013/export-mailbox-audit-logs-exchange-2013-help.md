---
title: 'Exportieren von Postfachüberwachungsprotokollen: Exchange 2013 Help'
TOCTitle: Exportieren von Postfachüberwachungsprotokollen
ms:assetid: b458a95a-3321-4647-8884-cf97f8e7186a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150552(v=EXCHG.150)
ms:contentKeyID: 50474833
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exportieren von Postfachüberwachungsprotokollen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Bei aktivierter Postfachüberwachung für ein Postfach werden im *Postfachüberwachungsprotokoll* Informationen protokolliert, wenn ein Benutzer, bei dem es sich nicht um den Besitzer des Postfachs handelt, auf das Postfach zugreift. Jeder Protokolleintrag enthält Angaben zur zugreifenden Person und zur Zugriffszeit, zu den Aktionen, die der Nicht-Besitzer ausgeführt hat, sowie zum Status der Aktion. Einträge im Postfachüberwachungsprotokoll werden standardmäßig für 90 Tage beibehalten. Mithilfe des Postfachüberwachungsprotokolls können Sie feststellen, ob auf ein Postfach von einer Person zugegriffen wurde, bei der es sich nicht um den Besitzer des Postfachs handelt.

Wenn Sie Einträge aus Postfachüberwachungsprotokollen exportieren, speichert Microsoft Exchange die Einträge in einer XML-Datei und fügt diese einer E-Mail an die angegebenen Empfänger an.

**Inhalt**

Bevor Sie beginnen

Konfigurieren der Postfachüberwachungsprotokollierung

Exportieren des Postfachüberwachungsprotokolls

Anzeigen des Postfachüberwachungsprotokolls

Weitere Informationen

## Bevor Sie beginnen

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: Die Zeiten sind unterschiedlich. In Exchange Online wird das Postfachüberwachungsprotokoll binnen weniger Tage gesendet, nachdem Sie es exportiert haben.

  - In Exchange Online müssen Sie die Remote Windows PowerShell verwenden, um viele der in diesem Thema aufgeführten Prozeduren auszuführen. Details finden Sie unter [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://technet.microsoft.com/de-de/library/jj984289\(v=exchg.150\)).

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Konfigurieren der Postfachüberwachungsprotokollierung

Zum Exportieren und Anzeigen von Postfachüberwachungsprotokollen muss zunächst die Postfachüberwachungsprotokollierung für jedes Postfach aktiviert werden, das Sie überwachen möchten. Außerdem müssen Sie Outlook Web App so konfigurieren, dass XML-Anlagen zugelassen werden. Nur dann können Sie mit Outlook Web App auf das Überwachungsprotokoll zugreifen.

## Schritt 1: Aktivieren der Postfachüberwachungsprotokollierung

Die Postfachüberwachungsprotokollierung muss für jedes Postfach aktiviert werden, für das ein Bericht zum Postfachzugriff durch Nicht-Besitzer ausgeführt werden soll. Ist die Postfachüberwachungsprotokollierung für ein Postfach nicht aktiviert, erhalten Sie keine Ergebnisse für dieses Postfach, wenn Sie das Postfachüberwachungsprotokoll exportieren.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachüberwachungsprotokollierung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

Führen Sie den folgenden Befehl in der Shell aus, um die Postfachüberwachungsprotokollierung für ein einzelnes Postfach zu aktivieren.

    Set-Mailbox <Identity> -AuditEnabled $true

Führen Sie folgende Befehle aus, um die Postfachüberwachungsprotokollierung für alle Benutzerpostfächer in Ihrer Organisation zu aktivieren.

    $UserMailboxes = Get-mailbox -Filter {(RecipientTypeDetails -eq 'UserMailbox')}

    $UserMailboxes | ForEach {Set-Mailbox $_.Identity -AuditEnabled $true}

## Schritt 2: Konfigurieren von Outlook Web App, um XML-Anlagen zuzulassen

Beim Exportieren des Postfachüberwachungsprotokolls wird das Überwachungsprotokoll, das eine XML-Datei ist, an eine E-Mail angefügt. XML-Anlagen werden von Outlook Web App jedoch standardmäßig blockiert. Damit Sie auf das exportierte Überwachungsprotokoll zugreifen können, müssen Sie Microsoft Outlook verwenden oder Outlook Web App so konfigurieren, dass XML-Anlagen akzeptiert werden.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Outlook Web App-Postfachrichtlinien" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

Führen Sie die folgenden Prozeduren aus, um XML-Anlagen in Outlook Web App zuzulassen. Verwenden Sie in Exchange Server 2013 den `Default`-Wert für den *Identity*-Parameter.

1.  Führen Sie den folgenden Befehl aus, um XML zur Liste der zulässigen Dateitypen in Outlook Web App hinzuzufügen.
    
        Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -AllowedFileTypes @{add='.xml'}

2.  Führen Sie den folgenden Befehl aus, um XML aus der Liste der blockierten Dateitypen in Outlook Web App zu entfernen.
    
        Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -BlockedFileTypes @{remove='.xml'}

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob die Postfachüberwachungsprotokollierung erfolgreich konfiguriert wurde:

1.  Führen Sie den folgenden Befehl aus, um sich zu vergewissern, dass die Überwachungsprotokollierung für Postfächer aktiviert ist.
    
        Get-Mailbox | FL Name,AuditEnabled
    
    Durch Festlegen der Eigenschaft *AuditEnabled* auf `True` wird sichergestellt, dass die Überwachungsprotokollierung aktiviert ist.

2.  Führen Sie den folgenden Befehl aus, um sicherzustellen, dass XML-Anlagen in Outlook Web App zulässig sind.
    
        Get-OwaMailboxPolicy | Select-Object -ExpandProperty AllowedFileTypes
    
    Vergewissern Sie sich, dass `.xml` in der Liste der zulässigen Dateitypen enthalten ist.

3.  Führen Sie den folgenden Befehl aus, um sicherzustellen, dass XML-Anlagen aus der Liste für blockierte Dateien in Outlook Web App entfernt werden.
    
        Get-OwaMailboxPolicy | Select-Object -ExpandProperty BlockedFileTypes
    
    Vergewissern Sie sich, dass `.xml` nicht in der Liste der blockierten Dateitypen enthalten ist.

Zurück zum Seitenanfang

## Exportieren des Postfachüberwachungsprotokolls

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Überwachungsprotokollierung durch Administratoren mit Leserechten" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

1.  Wechseln Sie in Exchange Admin Center (EAC) zu **Verwaltung der Richtlinientreue** \> **Überwachung**.

2.  Klicken Sie auf **Postfachüberwachungsprotokolle exportieren**.

3.  Konfigurieren Sie die folgenden Suchkriterien zum Exportieren der Einträge aus dem Postfachüberwachungsprotokoll:
    
      - **Start- und Enddatum**   Wählen Sie den Datumsbereich für die Einträge aus, die in die exportierte Datei eingeschlossen werden sollen.
    
      - **Postfächer, nach denen das Überwachungsprotokoll durchsucht werden soll**   Wählen Sie die Postfächer aus, für die Überwachungsprotokolleinträge abgerufen werden sollen.
    
      - **Typ des Nicht-Besitzer-Zugriffs**   Wählen Sie eine der folgenden Optionen aus, um den Typ des Nicht-Besitzer-Zugriffs zu definieren, für den Einträge abgerufen werden sollen:
        
          - **Alle Nicht-Besitzer**   Dient zum Suchen nach Zugriffen durch Administratoren und delegierte Benutzer in der Organisation sowie durch Microsoft-Datencenteradministratoren in Exchange Online.
        
          - **Externe Benutzer**   Dient zum Suchen nach Zugriffen durch Microsoft-Datencenteradministratoren.
        
          - **Administratoren und delegierte Benutzer**   Dient zum Suchen nach Zugriffen durch Administratoren und delegierte Benutzer in der Organisation.
        
          - **Administratoren**   Dient zum Suchen nach Zugriffen durch Administratoren in der Organisation.
    
      - **Empfänger**   Wählen Sie die Benutzer aus, an die das Postfachüberwachungsprotokoll gesendet werden soll.

4.  Klicken Sie auf **Exportieren**.
    
    Microsoft Exchange ruft aus dem Postfachüberwachungsprotokoll die Einträge ab, die den Suchkriterien entsprechen, speichert die Einträge in einer Datei namens "SearchResult.xml", und fügt die XML-Datei dann an eine E-Mail an, die an die von Ihnen angegebenen Empfänger gesendet wird.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Melden Sie sich an dem Postfach an, an das das Postfachüberwachungsprotokoll gesendet wurde. Wenn das Überwachungsprotokoll erfolgreich exportiert wurde, erhalten Sie eine von Exchange gesendete Nachricht. In Exchange Online dauert es möglicherweise ein paar Tage, bis Sie diese Nachricht erhalten. Das Postfachüberwachungsprotokoll "SearchResult.xml" wird an diese Nachricht angefügt. Wenn Sie Outlook Web App ordnungsgemäß konfiguriert haben, um XML-Anlagen zuzulassen, können Sie die angefügte XML-Datei herunterladen.

Zurück zum Seitenanfang

## Anzeigen des Postfachüberwachungsprotokolls

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Überwachungsprotokollierung durch Administratoren mit Leserechten" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

So speichern Sie die Datei "SearchResult.xml" und zeigen sie an

1.  Melden Sie sich an dem Postfach an, an das das Postfachüberwachungsprotokoll gesendet wurde.

2.  Öffnen Sie im Posteingang die von Microsoft Exchange gesendete Nachricht mit der XML-Dateianlage. Der Text der E-Mail enthält die Suchkriterien.

3.  Klicken Sie auf die Anlage, und laden Sie die XML-Datei herunter.

4.  Öffnen Sie die Datei "SearchResult.xml" in Microsoft Excel.

Zurück zum Seitenanfang

## Weitere Informationen

  - **Einträge im Postfachüberwachungsprotokoll**   Im folgenden Beispiel finden Sie einen Eintrag aus dem Postfachüberwachungsprotokoll, das in der Datei "SearchResult.xml" enthalten ist. Jeder Eintrag beginnt mit dem XML-Tag **\<Event\>** und endet mit dem XML-Tag **\</Event\>**. Dieser Eintrag besagt, dass der Administrator die Nachricht mit dem Betreff "**Notification of litigation hold**" am 30. April 2010 aus dem Ordner "Wiederherstellbare Elemente" des Postfachs von David endgültig gelöscht hat.
    
        <Event MailboxGuid="6d4fbdae-e3ae-4530-8d0b-f62a14687939" 
          Owner="PPLNSL-dom\david50001-1363917750" 
          LastAccessed="2010-04-30T11:01:55.140625-07:00" 
          Operation="HardDelete" 
          OperationResult="Succeeded" 
          LogonType="Admin"
         FolderId="0000000073098C3277988F4CB882F5B82EBF64610100A7C317F68C24304BBD18ABE1F185E79B00000026BD4F0000"
          FolderPathName="\Recoverable Items\Deletions"
          ClientInfoString="Client=OWA;Action=ViaProxy" 
          ClientIPAddress="10.196.241.168" 
          InternalLogonType="Owner"
          MailboxOwnerUPN="david@contoso.com"
          MailboxOwnerSid="S-1-5-21-290112810-296651436-1966561949-1151" 
          CrossMailboxOperation="false" 
          LogonUserDN="Administrator"
          LogonUserSid="S-1-5-21-290112810-296651436-1966561949-1149">
          <SourceItems>
           <ItemId="0000000073098C3277988F4CB882F5B82EBF64610700A7C317F68C24304BBD18ABE1F185E79B00000026BD4F0000A7C317F68C24304BBD18ABE1F185E79B00000026BD540"
            Subject="Notification of litigation hold"
            FolderPathName="\Recoverable Items\Deletions" /> 
          </SourceItems>
        </Event>

  - **Hilfreiche Felder im Postfachüberwachungsprotokoll**   Hier finden Sie eine Beschreibung der nützlichen Felder im Postfachüberwachungsprotokoll. Diese Felder enthalten spezifische Informationen zu den einzelnen Instanzen von Nicht-Besitzer-Zugriffen eines Postfachs.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Feld</th>
    <th>Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Owner</strong></p></td>
    <td><p>Der Besitzer des Postfachs, auf das von einem Nicht-Besitzer zugegriffen wurde.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>LastAccessed</strong></p></td>
    <td><p>Das Datum und die Uhrzeit des Postfachzugriffs.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Operation</strong></p></td>
    <td><p>Die vom Nicht-Besitzer ausgeführte Aktion. Weitere Informationen finden Sie unter <a href="https://technet.microsoft.com/de-de/library/jj156300(v=exchg.150)">Weitere Informationen zum Ausführen eines Berichts zum Postfachzugriff durch Nicht-Besitzer</a> im Abschnitt &quot;Was wird im Postfachüberwachungsprotokoll protokolliert?&quot;.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>OperationResult</strong></p></td>
    <td><p>Gibt an, ob die vom Nicht-Besitzer ausgeführte Aktion erfolgreich war.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>LogonType</strong></p></td>
    <td><p>Der Typ des Nicht-Besitzer-Zugriffs. Hierzu zählen Zugriffe durch Administratoren, durch delegierte Benutzer und durch externe Benutzer.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>FolderPathName</strong></p></td>
    <td><p>Der Name des Ordners mit der Nachricht, die von der Aktion des Nicht-Besitzers betroffen war.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>ClientInfoString</strong></p></td>
    <td><p>Informationen zum E-Mail-Client, mit dem der Nicht-Besitzer auf das Postfach zugegriffen hat.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>ClientIPAddress</strong></p></td>
    <td><p>Die IP-Adresse des Computers, mit dem der Nicht-Besitzer auf das Postfach zugegriffen hat.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>InternalLogonType</strong></p></td>
    <td><p>Der Anmeldetyp des Kontos, mit dem der Nicht-Besitzer auf das Postfach zugegriffen hat.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>MailboxOwnerUPN</strong></p></td>
    <td><p>Die E-Mail-Adresse des Postfachbesitzers.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>LogonUserDN</strong></p></td>
    <td><p>Der Anzeigename des Nicht-Besitzers.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Subject</strong></p></td>
    <td><p>Die Betreffzeile der E-Mail, die von der Aktion des Nicht-Besitzers betroffen war.</p></td>
    </tr>
    </tbody>
    </table>
    
    Zurück zum Seitenanfang


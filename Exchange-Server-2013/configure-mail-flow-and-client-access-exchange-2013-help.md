---
title: 'Konfigurieren von Nachrichtenfluss und Clientzugriff: Exchange 2013 Help'
TOCTitle: Konfigurieren von Nachrichtenfluss und Clientzugriff
ms:assetid: 4acc7f2a-93ce-468c-9ace-d5f7eecbd8d4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ218640(v=EXCHG.150)
ms:contentKeyID: 50475583
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Nachrichtenfluss und Clientzugriff

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Aufgaben nach der Installation für Exchange Server 2013-E-Mail-Fluss und -Clientzugriff, einschließlich Konfigurieren eines SSL-Zertifikats

Nachdem Sie Microsoft Exchange Server 2013 in Ihrer Organisation installiert haben, müssen Sie Exchange Server 2013 für Nachrichtenfluss und Clientzugriff konfigurieren. Ohne diese zusätzlichen Schritte sind Sie nicht in der Lage, E-Mails an das Internet und externe Clients – z. B. Microsoft Office Outlook – zu senden, und Exchange ActiveSync-Geräte können keine Verbindung mit Ihrer Exchange-Organisation herstellen.

Bei den Schrittanleitungen in diesem Thema wird davon ausgegangen, dass Sie über eine Exchange-Basisbereitstellung mit einem einzelnen Active Directory-Standort und einem einzelnen SMTP-Namespace (Simple Mail Transport Protocol) verfügen.


> [!IMPORTANT]
> In diesem Thema werden Beispielwerte wie "Ex2013CAS", "contoso.com", "mail.contoso.com" und 172.16.10.11 verwendet. Ersetzen Sie die Beispielwerte durch die Servernamen, FQDNs und IP-Adressen für Ihre Organisation.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit dem E-Mail-Fluss sowie mit Clients und Geräten finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md) und [Clients und mobile Funktionen](clients-and-mobile-exchange-2013-help.md):

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 50 Minuten

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Sie erhalten bei der Verbindungsherstellung mit der Website der Exchange-Verwaltungskonsole möglicherweise Zertifikatwarnungen, bis Sie ein SSL-Zertifikat (Secure Sockets Layer) auf dem Clientzugriffsserver konfigurieren. Informationen zur Vorgehensweise für die Zertifikatkonfiguration finden Sie weiter unten in diesem Thema.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!IMPORTANT]
> Jede Organisation erfordert mindestens einen Clientzugriffsserver und einen Postfachserver in der Active Directory-Gesamtstruktur. Jeder Active Directory-Standort, der einen Postfachserver umfasst, muss zudem auch mindestens einen Clientzugriffsserver aufweisen. Wenn Sie die Serverrollen trennen, empfiehlt es sich, zuerst die Postfachserverrolle zu installieren.




> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen eines Sendeconnectors

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Sendeconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

Bevor Sie E-Mails an das Internet senden können, müssen Sie auf dem Postfachserver einen Sendeconnector erstellen. Gehen Sie hierzu wie nachfolgend beschrieben vor.

1.  Öffnen Sie die Exchange-Verwaltungskonsole, indem Sie zu der URL Ihres Clientzugriffsservers wechseln. Beispiel: https://Ex2013CAS/ECP.

2.  Geben Sie Ihren Benutzernamen und das zugehörige Kennwort in die Felder **Domäne\\Benutzername** und **Kennwort** ein, und klicken Sie dann auf **Anmelden**.

3.  Wechseln Sie zu **Nachrichtenfluss** \> **Sendeconnectors**. Klicken Sie auf der Seite **Sendeconnectors** auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Geben Sie im Assistenten für neue Sendeconnectors einen Namen für den Sendeconnector an, und wählen Sie **Internet**. Klicken Sie dann auf **Weiter**.

5.  Stellen Sie sicher, dass die Option **Mit der Empfängerdomäne verbundener MX-Eintrag** aktiviert ist. Klicken Sie dann auf **Weiter**.

6.  Klicken Sie unter **Adressraum** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Stellen Sie sicher, dass im Fenster **Domäne hinzufügen** als **Typ** die Einstellung **SMTP** aktiviert ist. Geben Sie im Feld **Vollqualifizierter Domänenname (FQDN)** den Wert **\*** ein. Klicken Sie auf **Speichern**.

7.  Stellen Sie sicher, dass das Kontrollkästchen **Sendeconnector mit Bereich** deaktiviert ist, und klicken Sie auf **Weiter**.

8.  Klicken Sie unterhalb von **Quellserver** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wählen Sie im Fenster **Server auswählen** einen Postfachserver aus. Nachdem Sie den Server ausgewählt haben, klicken Sie auf **Hinzufügen** und anschließend auf **OK**.

9.  Klicken Sie auf **Fertig stellen**.


> [!NOTE]
> Bei der Installation von Exchange 2013 wird ein standardmäßiger eingehender Empfangsconnector erstellt. Dieser Empfangsconnector akzeptiert anonyme SMTP-Verbindungen von externen Servern. Sie müssen keine zusätzliche Konfiguration durchführen, wenn dies die gewünschte Funktionalität ist. Wenn Sie eingehende Verbindungen von externen Server einschränken möchten, ändern Sie den Empfangsconnector <STRONG>Standard-Front-End &lt;Clientzugriffsserver&gt;</STRONG> auf dem Clientzugriffsserver.



## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass der ausgehende Sendeconnector erfolgreich erstellt wurde:

1.  Vergewissern Sie sich, dass der neue Sendeconnector in der Exchange-Verwaltungskonsole unter **Nachrichtenfluss** \> **Sendeconnectors** angezeigt wird.

2.  Öffnen Sie Outlook Web App, und senden Sie eine E-Mail-Nachricht an einen externen Empfänger. Wenn der Empfänger die Nachricht erhält, haben Sie den Sendeconnector erfolgreich konfiguriert.

## Schritt 2: Hinzufügen zusätzlicher akzeptierter Domänen

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Akzeptierte Domänen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

Bei der Bereitstellung einer neuen Exchange 2013-Organisation in einer Active Directory-Gesamtstruktur verwendet Exchange standardmäßig den Domänennamen der Active Directory-Domäne, in der "Setup /PrepareAD" ausgeführt wurde. Wenn Sie möchten, dass Empfänger Nachrichten an eine andere Domäne senden und von dieser empfangen könne, müssen Sie die Domäne als akzeptierte Domäne hinzufügen. Diese Domäne wird im nächsten Schritt als primäre SMTP-Adresse in die standardmäßige E-Mail-Adressrichtlinie eingefügt.


> [!IMPORTANT]
> Ein öffentlicher DNS-MX-Ressourceneintrag (Domain Name System) ist für jede SMTP-Domäne erforderlich, für die Sie E-Mails aus dem Internet akzeptieren möchten. Jeder MX-Eintrag muss sich in den für das Internet verwendeten Server auflösen, der E-Mails für Ihre Organisation empfängt.



1.  Öffnen Sie die Exchange-Verwaltungskonsole, indem Sie zu der URL Ihres Clientzugriffsservers wechseln. Beispiel: https://Ex2013CAS/ECP.

2.  Geben Sie Ihren Benutzernamen und das zugehörige Kennwort in die Felder **Domäne\\Benutzername** und **Kennwort** ein, und klicken Sie dann auf **Anmelden**.

3.  Wechseln Sie zu **Nachrichtenfluss** \> **Akzeptierte Domänen**. Klicken Sie auf der Seite **Akzeptierte Domänen** auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Geben Sie im Assistenten für neue akzeptierte Domänen einen Namen für die akzeptierte Domäne an.

5.  Geben Sie im Feld **Akzeptierte Domäne** die SMTP-Empfängerdomäne an, die Sie hinzufügen möchten, beispielsweise "contoso.com".

6.  Aktivieren Sie **Autoritative Domäne**, und klicken Sie auf **Speichern**.

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Erstellung einer akzeptierten Domäne zu überprüfen:

  - Vergewissern Sie sich, dass die neue akzeptierte Domäne in der Exchange-Verwaltungskonsole unter **Nachrichtenfluss** \> **Akzeptierte Domänen** angezeigt wird.

## Schritt 3: Konfigurieren der standardmäßigen E-Mail-Adressrichtlinie

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Adressrichtlinien" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

Wenn Sie im vorherigen Schritt eine akzeptierte Domäne hinzugefügt haben und möchten, dass diese Domäne jedem Empfänger in der Organisation hinzugefügt wird, müssen Sie die standardmäßige E-Mail-Adressrichtlinie aktualisieren.

1.  Öffnen Sie die Exchange-Verwaltungskonsole, indem Sie zu der URL Ihres Clientzugriffsservers wechseln. Beispiel: https://Ex2013CAS/ECP.

2.  Geben Sie Ihren Benutzernamen und das zugehörige Kennwort in die Felder **Domäne\\Benutzername** und **Kennwort** ein, und klicken Sie dann auf **Anmelden**.

3.  Wechseln Sie zu **Nachrichtenfluss** \> **E-Mail-Adressrichtlinien**. Wählen Sie auf der Registerkarte **Gruppenrichtlinie** die Option **E-Mail-Adressrichtlinien** aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Klicken Sie auf der Seite **Standardmäßige E-Mail-Adressrichtlinie** auf **E-Mail-Adressformat**.

5.  Klicken Sie unterhalb von **E-Mail-Adressformat** auf die SMTP-Adresse, die Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

6.  Geben Sie auf der Seite **E-Mail-Adressformat** unter **E-Mail-Adressparameter** die SMTP-Empfängerdomäne an, die Sie auf alle Empfänger in der Exchange-Organisation anwenden möchten. Diese Domäne muss mit der akzeptierten Domäne übereinstimmen, die Sie im vorherigen Schritt hinzugefügt haben. Beispiel: @contoso.com. Klicken Sie auf **Speichern**.

7.  Klicken Sie auf **Speichern**

8.  Klicken Sie im Detailbereich für **Standardrichtlinie** auf **Anwenden**.


> [!NOTE]
> Es wird empfohlen, einen Benutzerprinzipalnamen (User Principal Name, UPN) zu konfigurieren, der mit der primären E-Mail-Adresse für jeden Benutzer übereinstimmt. Wenn Sie keinen Benutzerprinzipalnamen angeben, der mit der E-Mail-Adresse des Benutzers übereinstimmt, muss der Benutzer zusätzlich zur E-Mail-Adresse den Namen im Format "Domäne\Benutzer" oder den Benutzerprinzipalnamen manuell angeben. Wenn der Benutzerprinzipalname mit der E-Mail-Adresse übereinstimmt, gleichen Outlook Web App, ActiveSync und Outlook automatisch die E-Mail-Adresse mit dem Benutzerprinzipalnamen ab.



## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die standardmäßige E-Mail-Adressrichtlinie erfolgreich konfiguriert wurde:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie ein Postfach aus, und vergewissern Sie sich, dass im Detailbereich das Feld **Benutzerpostfach** auf *\<Alias\>*@*\<neue akzeptierte Domäne\>* festgelegt ist. Beispiel: "david@contoso.com".

3.  (Optional) Erstellen Sie ein neues Postfach, und überprüfen Sie folgendermaßen, dass die E-Mail-Adresse des Postfachs den Namen der neuen akzeptierten Domäne enthält:
    
    1.  Wechseln Sie zu **Empfänger** \> **Postfächer**, klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie dann **Benutzerpostfach** aus.
    
    2.  Geben Sie auf der Seite für das neue Benutzerpostfach die erforderlichen Informationen zum Erstellen eines neuen Postfachs an. Klicken Sie auf **Speichern**.
    
    3.  Wählen Sie das neue Postfach aus, und vergewissern Sie sich, dass im Detailbereich das Feld **Benutzerpostfach** auf *\<Alias\>*@*\<neue akzeptierte Domäne\>* festgelegt ist. Beispiel: david@contoso.com.

## Schritt 4: Konfigurieren von externen URLs

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Einstellungen virtueller *\<Dienst\>*-Verzeichnisse" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

Bevor Clients vom Internet aus eine Verbindung mit Ihrem neuen Server herstellen können, müssen Sie die externen Domänen, oder URLs, in den virtuellen Verzeichnissen des Clientzugriffsservers konfigurieren und anschließend Ihre öffentlichen DNS-Einträge (Domain Name System) konfigurieren. Über die nachfolgenden Schritte wird dieselbe externe Domäne im externen URL jedes virtuellen Verzeichnisses konfiguriert. Wenn Sie unterschiedliche externe Domänen in mindestens einer externen URL für ein virtuelles Verzeichnis konfigurieren möchten, müssen Sie die externen URLs manuell konfigurieren. Weitere Informationen finden Sie unter [Verwaltung für virtuelle Verzeichnisse](virtual-directory-management-exchange-2013-help.md).

1.  Öffnen Sie die Exchange-Verwaltungskonsole, indem Sie zu der URL Ihres Clientzugriffsservers wechseln. Beispiel: https://Ex2013CAS/ECP.

2.  Geben Sie Ihren Benutzernamen und das zugehörige Kennwort in die Felder **Domäne\\Benutzername** und **Kennwort** ein, und klicken Sie dann auf **Anmelden**.

3.  Wechseln Sie zu **Server** \> **Server**, wählen Sie den Namen des mit dem Internet verbundenen Clientzugriffsservers aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Klicken Sie auf **Outlook Anywhere**.

5.  Geben Sie im Feld **Externer Hostname** den extern zugänglichen FQDN des Clientzugriffsservers an. Beispiel: "mail.contoso.com".

6.  An dieser Stelle können Sie auch den intern zugänglichen FQDN des Clientzugriffsservers festlegen. Geben Sie im Feld **Geben Sie den internen Hostnamen an** den FQDN ein, den Sie im vorigen Schritt verwendet haben. Beispiel: "mail.contoso.com".

7.  Klicken Sie auf **Speichern**.

8.  Wechseln Sie zu **Server** \> **Virtuelle Verzeichnisse**, und klicken Sie auf **Domäne mit externem Zugriff konfigurieren**![Symbol "Konfigurieren"](images/JJ218640.a9c33f23-3d44-44e7-a5d0-8446200c746e(EXCHG.150).gif "Symbol \"Konfigurieren\"").

9.  Klicken Sie unterhalb von **Wählen Sie die Clientzugriffsserver aus, die mit der externen URL verwendet werden** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)")

10. Wählen Sie den Clientzugriffsserver aus, den Sie konfigurieren möchten, und klicken Sie auf **Hinzufügen**. Wenn Sie alle Clientzugriffsserver hinzugefügt haben, die Sie konfigurieren möchten, klicken Sie auf **OK**.

11. Geben Sie in **Domänennamen eingeben, der mit externen Clientzugriffsservern verwendet wird** die externe Domäne ein, die Sie anwenden möchten. Beispiel: mail.contoso.com. Klicken Sie auf **Speichern**.
    

    > [!NOTE]
    > Einige Organisationen stellen sicher, dass der FQDN für Outlook Web App eindeutig ist, um Benutzer vor Änderungen am zugrunde liegenden FQDN für den Server zu schützen. Viele Organisationen verwenden "owa.contoso.com" anstelle von "mail.contoso.com" als FQDN für Outlook Web App. Wenn Sie einen eindeutigen FQDN für Outlook Web App konfigurieren möchten, gehen Sie wie folgt vor, wenn Sie den vorigen Schritt ausgeführt haben. In dieser Prüfliste wird davon ausgegangen, dass Sie einen eindeutigen FQDN für Outlook Web App konfiguriert haben. 
    > <OL>
    > <LI>
    > <P>Wählen Sie <STRONG>owa (Standardwebsite)</STRONG> aus, und klicken Sie auf <STRONG>Bearbeiten</STRONG>&nbsp;<IMG title=Bearbeitungssymbol alt=Bearbeitungssymbol src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif">.</P>
    > <LI>
    > <P>Geben Sie in <STRONG>Externe URLhttps://</STRONG> ein, dann den eindeutigen FQDN für Outlook Web App, den Sie verwenden möchten, und hängen Sie dann <STRONG>/owa</STRONG> an. Beispiel: "https://owa.contoso.com/owa".</P>
    > <LI>
    > <P>Klicken Sie auf <STRONG>Speichern</STRONG>.</P>
    > <LI>
    > <P>Wählen Sie <STRONG>ecp (Standardwebsite)</STRONG> aus, und klicken Sie auf <STRONG>Bearbeiten</STRONG>&nbsp;<IMG title=Bearbeitungssymbol alt=Bearbeitungssymbol src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif">.</P>
    > <LI>
    > <P>Geben Sie in <STRONG>Externe URLhttps://</STRONG> ein, dann denselben FQDN für Outlook Web App, den Sie im vorigen Schritt angegeben haben, und hängen Sie dann <STRONG>/ecp</STRONG> an. Beispiel: "https://owa.contoso.com/ecp".</P>
    > <LI>
    > <P>Klicken Sie auf <STRONG>Speichern</STRONG>.</P></LI></OL>



Nachdem Sie die externe URL in den virtuellen Verzeichnissen des Clientzugriffsservers konfiguriert haben, müssen Sie Ihre öffentlichen DNS-Einträge für AutoErmittlung, Outlook Web App und Nachrichtenfluss konfigurieren. Die öffentlichen DNS-Einträge sollten auf die externe IP-Adresse oder den FQDN des mit dem Internet verbundenen Clientzugriffsservers zeigen und die extern zugänglichen FQDNs verwenden, die Sie auf Ihrem Clientzugriffsserver konfiguriert haben. Nachfolgend werden Beispiele für empfohlene DNS-Einträge gezeigt, die Sie zur Aktivierung von Nachrichtenfluss und Konnektivität für externe Clients erstellen sollten.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>FQDN</th>
<th>DNS-Eintragstyp</th>
<th>Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Contoso.com</p></td>
<td><p>MX</p></td>
<td><p>Mail.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Mail.contoso.com</p></td>
<td><p>A</p></td>
<td><p>172.16.10.11</p></td>
</tr>
<tr class="odd">
<td><p>Owa.contoso.com</p></td>
<td><p>CNAME</p></td>
<td><p>Mail.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Autodiscover.contoso.com</p></td>
<td><p>CNAME</p></td>
<td><p>Mail.contoso.com</p></td>
</tr>
</tbody>
</table>


## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Konfiguration der externen URL in den virtuellen Verzeichnissen des Clientzugriffsservers zu überprüfen:

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Virtuelle Verzeichnisse**.

2.  Wählen Sie im Feld **Server auswählen** den mit dem Internet verbundenen Clientzugriffsserver.

3.  Wählen Sie ein virtuelles Verzeichnis, und vergewissern Sie sich, dass im Feld **Externe URL** im Detailbereich des virtuellen Verzeichnisses der richtige FQDN und Dienst angezeigt wird:
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Virtuelles Verzeichnis</th>
    <th>Wert für externe URL</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>AutoErmittlung</strong></p></td>
    <td><p>Keine externe URL angezeigt</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Exchange-Systemsteuerung</strong></p></td>
    <td><p>https://owa.contoso.com/ecp</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>EWS</strong></p></td>
    <td><p>https://mail.contoso.com/EWS/Exchange.asmx</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Microsoft-Server-ActiveSync</strong></p></td>
    <td><p>https://mail.contoso.com/Microsoft-Server-ActiveSync</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>OAB</strong></p></td>
    <td><p>https://mail.contoso.com/OAB</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>OWA</strong></p></td>
    <td><p>https://owa.contoso.com/owa</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>PowerShell</strong></p></td>
    <td><p>http://mail.contoso.com/PowerShell</p></td>
    </tr>
    </tbody>
    </table>


Gehen Sie folgendermaßen vor, um sicherzustellen, dass Sie Ihre öffentlichen DSN-Einträge erfolgreich konfiguriert haben:

1.  Öffnen Sie eine Eingabeaufforderung, und führen Sie `nslookup.exe` aus.

2.  Wechseln Sie zu einem DNS-Server, der Ihre öffentliche DNS-Zone abfragen kann.

3.  Suchen Sie in `nslookup` nach dem Eintrag für jeden erstellten FQDN. Stellen Sie sicher, dass der für jeden FQDN zurückgegebene Wert richtig ist.

4.  Geben Sie in `nslookup` den Befehl `set type=mx` ein, und suchen Sie dann nach der in Schritt 1 hinzugefügten akzeptierten Domäne. Vergewissern Sie sich, dass der zurückgegebene Wert mit dem FQDN des Clientzugriffsservers übereinstimmt.

## Schritt 5: Konfigurieren interner URLs

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Einstellungen virtueller *\<Dienst\>*-Verzeichnisse" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

Bevor Clients vom Intranet aus eine Verbindung mit Ihrem neuen Server herstellen können, müssen Sie die internen Domänen, oder URLs, in den virtuellen Verzeichnissen des Clientzugriffsservers konfigurieren und anschließend Ihre privaten DNS-Einträge (Domain Name System) konfigurieren.

Im nachfolgenden Verfahren können Sie wählen, ob Benutzer in Ihrem Intranet und im Internet dieselbe URL für den Zugriff auf Ihren Exchange-Server verwenden sollen oder ob eine andere URL eingesetzt werden soll. Ihre Auswahl hängt von dem Adressschema ab, das Sie bereits einsetzen oder das Sie implementieren möchten. Wenn Sie ein neues Adressschema implementieren, empfiehlt es sich, dieselbe URL sowohl für interne als auch für externe URLs zu verwenden. Durch die Verwendung derselben URL können Benutzer einfacher auf Ihren Exchange-Server zugreifen, da sie sich nur eine Adresse merken müssen. Unabhängig von Ihrer Wahl müssen Sie in jedem Fall eine private DNS-Zone für den von Ihnen konfigurierten Adressraum konfigurieren. Weitere Informationen zum Verwalten von DNS-Zonen finden Sie unter [Verwaltung von DNS-Server](http://go.microsoft.com/fwlink/p/?linkid=190631).

Weitere Informationen zu internen und externen URLs für virtuelle Verzeichnisse finden Sie unter [Verwaltung für virtuelle Verzeichnisse](virtual-directory-management-exchange-2013-help.md).

## Konfigurieren einer identischen internen und externen URL

1.  Öffnen Sie auf dem Clientzugriffsserver die Exchange-Verwaltungsshell.

2.  Speichern Sie den Hostnamen Ihres Clientzugriffsservers in einer Variablen. Diese wird im nächsten Schritt verwendet. Beispiel: "Ex2013CAS".
    
        $HostName = "Ex2013CAS"

3.  Führen Sie die folgenden Befehle in der Shell aus, um die einzelnen internen URLs so zu konfigurieren, dass sie mit der externen URL des virtuellen Verzeichnisses übereinstimmen.
    
        Set-EcpVirtualDirectory "$HostName\ECP (Default Web Site)" -InternalUrl ((Get-EcpVirtualDirectory "$HostName\ECP (Default Web Site)").ExternalUrl)
        
        Set-WebServicesVirtualDirectory "$HostName\EWS (Default Web Site)" -InternalUrl ((get-WebServicesVirtualDirectory "$HostName\EWS (Default Web Site)").ExternalUrl)
        
        Set-ActiveSyncVirtualDirectory "$HostName\Microsoft-Server-ActiveSync (Default Web Site)" -InternalUrl ((Get-ActiveSyncVirtualDirectory "$HostName\Microsoft-Server-ActiveSync (Default Web Site)").ExternalUrl)
        
        Set-OabVirtualDirectory "$HostName\OAB (Default Web Site)" -InternalUrl ((Get-OabVirtualDirectory "$HostName\OAB (Default Web Site)").ExternalUrl)
        
        Set-OwaVirtualDirectory "$HostName\OWA (Default Web Site)" -InternalUrl ((Get-OwaVirtualDirectory "$HostName\OWA (Default Web Site)").ExternalUrl)
        
        Set-PowerShellVirtualDirectory "$HostName\PowerShell (Default Web Site)" -InternalUrl ((Get-PowerShellVirtualDirectory "$HostName\PowerShell (Default Web Site)").ExternalUrl)

4.  Während wir in der Shell sind, lassen Sie uns auch das Offlineadressbuch (OAB) konfigurieren, sodass die automatische Erkennung das korrekte virtuelle Verzeichnis zum Verteilen des OABs auswählen kann. Führen Sie dazu die folgenden Befehle aus.
    
        Get-OfflineAddressBook | Set-OfflineAddressBook -GlobalWebDistributionEnabled $True -VirtualDirectories $Null

Nachdem Sie die interne URL in den virtuellen Verzeichnissen des Clientzugriffsservers konfiguriert haben, müssen Sie Ihre privaten DNS-Einträge für Outlook Web App und andere Konnektivität konfigurieren. Abhängig von Ihrer Konfiguration müssen Sie Ihre privaten DNS-Einträge so konfigurieren, dass sie auf die interne oder externe IP-Adresse bzw. auf den FQDN (Fully Qualified Domain Name, vollqualifizierter Domänenname) Ihres Clientzugriffsservers verweisen. Nachfolgend werden Beispiele für empfohlene DNS-Einträge gezeigt, die Sie zur Aktivierung der internen Clientkonnektivität erstellen sollten.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>FQDN</th>
<th>DNS-Eintragstyp</th>
<th>Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mail.contoso.com</p></td>
<td><p>CNAME</p></td>
<td><p>Ex2013CAS.corp.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>Owa.contoso.com</p></td>
<td><p>CNAME</p></td>
<td><p>Ex2013CAS.corp.contoso.com</p></td>
</tr>
</tbody>
</table>


## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Konfiguration der internen URL für die virtuellen Verzeichnisse des Clientzugriffsservers zu überprüfen:

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Virtuelle Verzeichnisse**.

2.  Wählen Sie im Feld **Server auswählen** den mit dem Internet verbundenen Clientzugriffsserver.

3.  Wählen Sie ein virtuelles Verzeichnis aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Stellen Sie sicher, dass das Feld **Interne URL** den richtigen FQDN und Dienst enthält, wie nachfolgend gezeigt:
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Virtuelles Verzeichnis</th>
    <th>Wert der internen URL</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>AutoErmittlung</strong></p></td>
    <td><p>Keine interne URL angezeigt</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Exchange-Systemsteuerung</strong></p></td>
    <td><p>https://owa.contoso.com/ecp</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>EWS</strong></p></td>
    <td><p>https://mail.contoso.com/EWS/Exchange.asmx</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Microsoft-Server-ActiveSync</strong></p></td>
    <td><p>https://mail.contoso.com/Microsoft-Server-ActiveSync</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>OAB</strong></p></td>
    <td><p>https://mail.contoso.com/OAB</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>OWA</strong></p></td>
    <td><p>https://owa.contoso.com/owa</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>PowerShell</strong></p></td>
    <td><p>http://mail.contoso.com/PowerShell</p></td>
    </tr>
    </tbody>
    </table>


Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Konfiguration Ihrer privaten DNS-Einträge erfolgreich abgeschlossen wurde:

1.  Öffnen Sie eine Eingabeaufforderung, und führen Sie `nslookup.exe` aus.

2.  Wechseln Sie zu einem DNS-Server, der Ihre private DNS-Zone abfragen kann.

3.  Suchen Sie in `nslookup` nach den Einträgen für die einzelnen erstellten FQDNs. Stellen Sie sicher, dass der für jeden FQDN zurückgegebene Wert richtig ist.

## Konfigurieren verschiedener interner und externer URLs

1.  Öffnen Sie die Exchange-Verwaltungskonsole, indem Sie die URL Ihres Clientzugriffsservers aufrufen. Beispiel: "https://Ex2013CAS/ECP".

2.  Rufen Sie **Server** \> **Virtuelle Verzeichnisse** auf.

3.  Wählen Sie im Feld **Server auswählen** den mit dem Internet verbundenen Clientzugriffsserver.

4.  Wählen Sie das virtuelle Verzeichnis, das geändert werden soll, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

5.  Ersetzen Sie unter **Interne URL** den Hostnamen zwischen **https://** und dem ersten Schrägstrich (**/**) durch den neuen FQDN, den Sie verwenden möchten. Wenn Sie beispielsweise den FQDN des virtuellen Verzeichnisses "EWS" von "Ex2013CAS.corp.contoso.com" in "internal.contoso.com" ändern möchten, ändern Sie die interne URL von "https://Ex2013CAS.corp.contoso.com/ews/exchange.asmx" in "https://internal.contoso.com/ews/exchange.asmx".

6.  Klicken Sie auf **Speichern**.

7.  Wiederholen Sie die Schritte 5 und 6 für jedes virtuelle Verzeichnis, das Sie ändern möchten.
    

    > [!NOTE]
    > Die internen URLs für das virtuelle Verzeichnis von Exchange-Systemsteuerung und OWA müssen identisch sein.<BR>Sie können keine interne URL für das virtuelle Verzeichnis für die AutoErmittlung festlegen.



8.  Abschließend müssen wir die Shell öffnen und das Offlineadressbuch (OAB) konfigurieren, sodass die automatische Erkennung das korrekte virtuelle Verzeichnis zum Verteilen des OABs auswählen kann. Führen Sie dazu die folgenden Befehle aus.
    
        Get-OfflineAddressBook | Set-OfflineAddressBook -GlobalWebDistributionEnabled $True -VirtualDirectories $Null

Nachdem Sie die interne URL in den virtuellen Verzeichnissen des Clientzugriffsservers konfiguriert haben, müssen Sie Ihre privaten DNS-Einträge für Outlook Web App und andere Konnektivität konfigurieren. Abhängig von Ihrer Konfiguration müssen Sie Ihre privaten DNS-Einträge so konfigurieren, dass sie auf die interne oder externe IP-Adresse bzw. auf den FQDN Ihres Clientzugriffsservers verweisen. Im Folgenden sehen Sie ein Beispiel für einen empfohlenen DNS-Eintrag, den Sie zum Ermöglichen der internen Clientkonnektivität erstellen sollten, wenn Sie die internen URLs der virtuellen Verzeichnisse als "internal.contoso.com" konfiguriert haben.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>FQDN</th>
<th>DNS-Eintragstyp</th>
<th>Wert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>internal.contoso.com</p></td>
<td><p>CNAME</p></td>
<td><p>Ex2013CAS.corp.contoso.com</p></td>
</tr>
</tbody>
</table>


## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Konfiguration der internen URL für die virtuellen Verzeichnisse des Clientzugriffsservers zu überprüfen:

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Virtuelle Verzeichnisse**.

2.  Wählen Sie im Feld **Server auswählen** den mit dem Internet verbundenen Clientzugriffsserver.

3.  Wählen Sie ein virtuelles Verzeichnis aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Stellen Sie sicher, dass das Feld **Interne URL** den richtigen FQDN enthält. Beispielsweise können Sie die internen URLs auf "internal.contoso.com" festgelegt haben.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Virtuelles Verzeichnis</th>
    <th>Wert der internen URL</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>AutoErmittlung</strong></p></td>
    <td><p>Keine interne URL angezeigt</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Exchange-Systemsteuerung</strong></p></td>
    <td><p>https://internal.contoso.com/ecp</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>EWS</strong></p></td>
    <td><p>https://internal.contoso.com/EWS/Exchange.asmx</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Microsoft-Server-ActiveSync</strong></p></td>
    <td><p>https://internal.contoso.com/Microsoft-Server-ActiveSync</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>OAB</strong></p></td>
    <td><p>https://internal.contoso.com/OAB</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>OWA</strong></p></td>
    <td><p>https://internal.contoso.com/owa</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>PowerShell</strong></p></td>
    <td><p>http://internal.contoso.com/PowerShell</p></td>
    </tr>
    </tbody>
    </table>


Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Konfiguration Ihrer privaten DNS-Einträge erfolgreich abgeschlossen wurde:

1.  Öffnen Sie eine Eingabeaufforderung, und führen Sie `nslookup.exe` aus.

2.  Wechseln Sie zu einem DNS-Server, der Ihre private DNS-Zone abfragen kann.

3.  Suchen Sie in `nslookup` nach den Einträgen für die einzelnen erstellten FQDNs. Stellen Sie sicher, dass der für jeden FQDN zurückgegebene Wert richtig ist.

## Schritt 6: Konfigurieren eines SSL-Zertifikats

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Zertifikatverwaltung" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

Einige Dienste, z. B. Outlook Anywhere und Exchange ActiveSync, erfordern die Konfiguration von Zertifikaten auf Ihrem Exchange 2013-Server. Die folgenden Schritte zeigen, wie Sie ein SSL-Zertifikat von einer externen Zertifizierungsstelle konfigurieren:

1.  Öffnen Sie die Exchange-Verwaltungskonsole, indem Sie zu der URL Ihres Clientzugriffsservers wechseln. Beispiel: https://Ex2013CAS/ECP.

2.  Geben Sie Ihren Benutzernamen und das zugehörige Kennwort in die Felder **Domäne\\Benutzername** und **Kennwort** ein, und klicken Sie dann auf **Anmelden**.

3.  Wechseln Sie zu **Server** \> **Zertifikate**. Stellen Sie sicher, dass auf der Seite **Zertifikate** im Feld **Server auswählen** Ihr Clientzugriffsserver ausgewählt ist, und klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Aktivieren Sie im Assistenten für neue Exchange-Zertifikate die Option **Anforderung eines Zertifikats von einer Zertifizierungsstelle erstellen**, und klicken Sie auf **Weiter**.

5.  Geben Sie einen Namen für das Zertifikat ein, und klicken Sie auf **Weiter**.

6.  Wenn Sie ein Platzhalterzertifikat anfordern möchten, aktivieren Sie die Option **Platzhalterzertifikat anfordern**, und geben Sie die Stammdomäne für alle Unterdomänen im Feld **Stammdomäne** an. Wenn Sie kein Platzhalterzertifikat anfordern, sondern stattdessen jede Domäne angeben möchten, die dem Zertifikat hinzugefügt werden soll, lassen Sie diese Seite leer. Klicken Sie dann auf **Weiter**.

7.  Klicken Sie auf **Durchsuchen**, und geben Sie einen Exchange-Server an, auf dem das Zertifikat gespeichert werden soll. Der ausgewählte Server sollte der mit dem Internet verbundene Clientzugriffsserver sein. Klicken Sie dann auf **Weiter**.

8.  Stellen Sie für jeden in der Liste angezeigten Dienst sicher, dass der externe oder interne Servername, den Benutzer zur Verbindungsherstellung mit dem Exchange-Server verwenden, richtig sind. Beispiel:
    
      - Wenn Sie festgelegt haben, dass interne und externe URLs identisch sind, sollten **Outlook Web App (bei Zugriff über das Internet)** und **Outlook Web App (bei Zugriff über das Intranet)** den Eintrag "owa.contoso.com" aufweisen. **OAB (bei Zugriff über das Internet)** und **OAB (bei Zugriff über das Intranet)** sollten "mail.contoso.com" aufweisen.
    
      - Wenn Sie die internen URLs auf "internal.contoso.com" festgelegt haben, sollte **Outlook Web App (bei Zugriff über das Internet)** den Eintrag "owa.contoso.com" und **Outlook Web App (bei Zugriff über das Intranet)** den Eintrag "internal.contoso.com" aufweisen.
    
    Diese Domänen werden verwendet, um die SSL-Zertifikatanforderung zu erstellen. Klicken Sie dann auf **Weiter**.

9.  Fügen Sie beliebige zusätzliche Domänen hinzu, die Sie in das SSL-Zertifikat einbeziehen möchten.

10. Wählen Sie die Domäne aus, die als gemeinsamer Name für das Zertifikat verwendet werden soll, und klicken Sie dann auf **Als allgemeinen Namen festlegen**. Beispiel: contoso.com. Klicken Sie auf **Weiter**.

11. Stellen Sie Informationen zu Ihrer Organisation bereit. Diese Informationen werden in das SSL-Zertifikat aufgenommen. Klicken Sie dann auf **Weiter**.

12. Geben Sie den Netzwerkspeicherort für die Zertifikatanforderung an. Klicken Sie auf **Fertig stellen**.

Senden Sie die Zertifikatanforderung nach ihrer Speicherung an die Zertifizierungsstelle. Hierbei kann es sich je nach Organisation um eine interne oder um eine externe Zertifizierungsstelle handeln. Clients, die eine Verbindung mit dem Clientzugriffsserver herstellen, müssen die verwendete Zertifizierungsstelle als vertrauenswürdig einstufen. Führen Sie die folgenden Schritte aus, nachdem Sie das Zertifikat von der Zertifizierungsstelle erhalten haben:

1.  Wählen Sie in der Exchange-Verwaltungskonsole auf der Seite **Server** \> **Zertifikate** die in den vorherigen Schritten erstellte Zertifikatanforderung aus.

2.  Klicken Sie im Detailbereich der Zertifikatanforderung unterhalb von **Status** auf **Abschließen**.

3.  Geben Sie auf der Seite **Anstehende Anforderungen abschließen** den Pfad zum SSL-Zertifikat an, und klicken Sie auf **OK**.

4.  Wählen Sie das soeben hinzugefügte neue Zertifikat aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

5.  Klicken Sie auf der Zertifikatseite auf **Dienste**.

6.  Wählen Sie die Dienste, die Sie diesem Zertifikat zuweisen möchten. Wählen Sie mindestens **SMTP** und **IIS** aus. Klicken Sie auf **Speichern**.

7.  Wenn die Warnung **Soll das vorhandene SMTP-Standardzertifikat überschrieben werden?** angezeigt wird, klicken Sie auf **Ja**.

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass das neue Zertifikat erfolgreich hinzugefügt wurde:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Zertifikate**.

2.  Wählen Sie das neue Zertifikat aus, und vergewissern Sie sich, dass im Detailbereich folgende Werte angezeigt werden:
    
      - **Status** wird als **Gültig** angezeigt
    
      - **Diensten zugewiesen** zeigt mindestens **IIS** und **SMTP** an.

## Woher wissen Sie, dass diese Aufgabe erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Konfiguration von Nachrichtenfluss und externem Clientzugriff zu überprüfen:

1.  Erstellen Sie in Outlook und/oder auf einem Exchange ActiveSync-Gerät ein neues Profil. Stellen Sie sicher, dass Outlook bzw. das mobile Gerät das neue Profil erfolgreich erstellt haben.

2.  Senden Sie über Outlook und/oder das mobile Gerät eine neue Nachricht an einen externen Empfänger. Überprüfen Sie, ob der externe Empfänger die Nachricht erhält.

3.  Antworten Sie im Postfach des externen Empfängers auf die soeben vom Exchange-Postfach gesendete Nachricht. Überprüfen Sie, ob das Exchange-Postfach die Nachricht empfängt.

4.  Wechseln Sie zu "https://owa.contoso.com/owa", und stellen Sie sicher, dass keine Zertifikatwarnungen angezeigt werden.


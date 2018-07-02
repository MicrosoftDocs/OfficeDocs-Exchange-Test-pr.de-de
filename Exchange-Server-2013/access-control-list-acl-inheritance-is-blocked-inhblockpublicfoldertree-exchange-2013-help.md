---
title: 'Vererbung von Zugriffssteuerungslisten (Access Control List, ACL) ist blockiert_InhBlockPublicFolderTree: Exchange 2013 Help'
TOCTitle: Vererbung von Zugriffssteuerungslisten (Access Control List, ACL) ist blockiert_InhBlockPublicFolderTree
ms:assetid: e3b89c8a-d6f8-4864-8bf0-35a78ce87cc4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.inhblockpublicfoldertree(v=EXCHG.150)
ms:contentKeyID: 50476949
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Vererbung von Zugriffssteuerungslisten (Access Control List, ACL) ist blockiert\_InhBlockPublicFolderTree

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 oder Exchange Server 2010 kann nicht fortgesetzt werden, da die erforderlichen Berechtigungen nicht verteilt werden konnten.

Das Setup von Exchange verlangt, dass die Vererbung von Berechtigungen für die folgenden Exchange-Objekte aktiviert ist:

  - Objekt "Exchange-Organisation"

  - Objekt "Administrative Exchange-Gruppe"

  - Containerobjekt "Exchange-Server"

  - Objekt "Exchange-Adressliste"

  - Objekt "Öffentlicher Exchange-Ordner"

  - Objekt "Öffentliche Exchange-Ordner-Struktur"

Wenn es verabsäumt wird, die Vererbung von Berechtigungen für diese Objekte zu aktivieren, können Probleme bei der Nachrichtenübermittlung, der Bereitstellung des Nachrichtenspeichers oder andere Dienstausfälle die Folge sein.

Stellen Sie zum Beheben dieses Problems sicher, dass die Einstellung für die Verteilung von Berechtigungen an dieses Objekt und untergeordnete Objekte für das Objekt aktiviert ist, und führen Sie das Exchange Server 2007- oder Exchange 2010-Setup dann erneut aus.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>So aktivieren Sie die Vererbung von Berechtigungen für ein Exchange-Konfigurationsobjekt mithilfe von Exchange-System-Manager von Exchange Server 2003 erneut</p></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Aktivieren Sie die Registerkarte <strong>Sicherheit</strong> für das Objekteigenschaftenfeld des Exchange-System-Managers, indem Sie einen Registrierungsparameter festlegen.</p>
<ol>
<li><p>Starten Sie den Registrierungs-Editor (<strong>Regedt32.exe</strong>).</p></li>
<li><p>Suchen Sie den folgenden Schlüssel in der Registrierung:</p>
<p><strong>HKEY_CURRENT_USER\Software\Microsoft\Exchange\EXAdmin</strong></p></li>
<li><p>Klicken Sie im Menü <strong>Bearbeiten</strong> auf <strong>Neu</strong>, und fügen Sie dann den folgenden Registrierungswert hinzu:</p>
<p><strong>Wertname</strong>: ShowSecurityPage</p>
<p><strong>Datentyp</strong>: REG_DWORD</p>
<p><strong>Basis</strong>: Binärdatei</p>
<p><strong>Wert</strong>: 1</p></li>
<li><p>Schließen Sie den Registrierungs-Editor.</p></li>
</ol>

> [!NOTE]
> Standardmäßig ist die Registerkarte <STRONG>Sicherheit</STRONG> im Eigenschaftenfeld des Konfigurationsobjekts deaktiviert.


</li>
<li><p>Öffnen Sie Exchange-System-Manager, suchen Sie nach dem betreffenden Objekt, klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie dann <strong>Eigenschaften</strong> aus.</p></li>
<li><p>Wählen Sie die Registerkarte <strong>Sicherheit</strong> aus, und klicken Sie dann auf <strong>Erweitert</strong>.</p></li>
<li><p>Wählen Sie <strong>Berechtigungen übergeordneter Objekte, sofern vererbbar, über alle untergeordneten Objekte verbreiten</strong> aus, um die Vererbung von Berechtigungen erneut zu aktivieren.</p></li>
<li><p>Starten Sie Exchange Server neu.</p></li>
</ol></td>
</tr>
</tbody>
</table>



> [!WARNING]
> Wenn Sie die ADSI-Bearbeitung, das LDP-Tool (<STRONG>ldp.exe</STRONG>) oder einen anderen LDAP-Client, Version&nbsp;3, verwenden und die Attribute der Active&nbsp;Directory-Objekte nicht ordnungsgemäß ändern, können schwerwiegende Probleme verursacht werden. Diese Probleme erfordern möglicherweise eine Neuinstallation von Microsoft&nbsp;Windows&nbsp;Server™&nbsp;2003, Exchange&nbsp;Server&nbsp;oder von beiden Anwendungen. Die Bearbeitung der Attribute von Active Directory-Objekten erfolgt auf eigene Gefahr.




<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>So aktivieren Sie die Vererbung von Berechtigungen für ein Exchange-Konfigurationsobjekt mithilfe von ADSIEdit aus Exchange Server 2007 oder Exchange Server 2010 erneut</p></td>
</tr>
<tr class="even">
<td><ol>
<li><p>Installieren Sie die ADSI-Bearbeitung.</p></li>
<li><p>Starten Sie die ADSI-Bearbeitung. Klicken Sie auf <strong>Start</strong>, klicken Sie auf <strong>Ausführen</strong>, geben Sie <strong>adsiedit.msc</strong> in das Textfeld ein, und klicken Sie dann auf <strong>OK</strong>.</p></li>
<li><p>Navigieren Sie zum entsprechenden Objekt, klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie dann <strong>Eigenschaften</strong> aus.</p></li>
<li><p>Wählen Sie die Registerkarte <strong>Sicherheit</strong> aus, und klicken Sie dann auf <strong>Erweitert</strong>.</p></li>
<li><p>Wählen Sie <strong>Berechtigungen übergeordneter Objekte, sofern vererbbar, über alle untergeordneten Objekte verbreiten</strong> aus, um die Vererbung von Berechtigungen erneut zu aktivieren.</p></li>
<li><p>Klicken Sie zweimal auf <strong>OK</strong>, um die Änderung zu übernehmen.</p></li>
<li><p>Warten Sie, bis die Active Directory-Replikation die Änderungen verteilt hat, oder erzwingen Sie die Active Directory-Replikation, indem Sie die Anweisungen im Microsoft Knowledge Base-Artikel 232072 „Einleiten der Replikation zwischen direkten Replikationspartnern&amp;quot; (<a href="http://go.microsoft.com/fwlink/?linkid=3052%26kbid=232072" class="uri">http://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=232072</a>) befolgen.</p></li>
</ol></td>
</tr>
</tbody>
</table>


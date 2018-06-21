---
title: 'Einmaliges Anmelden in Hybrid-Bereitstellungen: Exchange 2013 Help'
TOCTitle: Einmaliges Anmelden in Hybrid-Bereitstellungen
ms:assetid: 050606f9-718d-4a1f-b7a6-50b08c6e9e07
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh563846(v=EXCHG.150)
ms:contentKeyID: 50477177
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Einmaliges Anmelden in Hybrid-Bereitstellungen

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-01-29_

Mit der einmaligen Anmeldung (Single Sign-On, SSO) können Benutzer unter Verwendung derselben Anmeldeinformationen sowohl auf die lokale Organisation als auch auf Office 365-Organisationen zugreifen. Die einmalige Anmeldung bietet Benutzern ein vertrautes Anmeldeerlebnis und ermöglicht Administratoren das problemlose Steuern von Kontorichtlinien für Postfächer in der Exchange Online-Organisation über die lokalen Active Directory-Verwaltungstools. Sie müssen eine Hybridbereitstellung zwar nicht mit aktiviertem einmaligen Anmelden konfigurieren, allerdings wird dies dringend empfohlen. Ohne einmaliges Anmelden müssen sich die Benutzer zwei unterschiedliche Sätze von Anmeldeinformationen merken, einen für Ihre lokale Organisation und einen für Office 365. Es folgen einige weitere Vorteile des einmaligen Anmeldens:

  - **Exchange Online-Archivierung**   Wenn einmaliges Anmelden bereitgestellt ist, werden lokale Outlook-Benutzer beim Zugriff auf archivierte Inhalte in der Exchange Online-Organisation zur Eingabe ihrer Anmeldeinformationen aufgefordert. Ein Benutzer kann eine zukünftige Aufforderung zur Eingabe der Anmeldeinformationen jedoch vorübergehend durch Auswahl von "Kennwort speichern" deaktivieren, er wird jedoch erneut aufgefordert, nachdem sein lokales Kontokennwort geändert wurde. Wenn einmaliges Anmelden in Exchange-Organisationen nicht bereitgestellt ist und die Exchange Online-Archivierung aktiviert ist, muss der lokale Benutzerprinzipalname (UPN) mit seinem Exchange Online-Konto übereinstimmen, und Benutzer werden beim Zugriff auf ihr Archiv immer zur Eingabe ihrer lokalen Anmeldeinformationen aufgefordert.

  - **Richtliniensteuerung**   Kontorichtlinien können über Active Directory gesteuert werden. Auf diese Weise können Sie Kennwortrichtlinien, Einschränkungen für Arbeitsstationen, Sperroptionen und andere Einstellungen verwalten, ohne zusätzliche Aufgaben in Ihrer Office 365-Organisation ausführen zu müssen.

  - **Weniger Supportanfragen**   Vergessene Kennwörter sind in allen Unternehmen ein häufiger Grund für Anfragen an den Support. Wenn die Benutzer sich weniger Kennwörter merken müssen, vergessen sie diese auch nicht so leicht.

Beim Bereitstellen des einmaligen Anmeldens haben Sie zwei Optionen: Synchronisierung von Kennwörtern und Active Directory-Verbunddienste (AD FS). Beide Optionen werden von Azure Active Directory-Connect bereitgestellt. Es wird dringend empfohlen, die Kennwortsynchronisierungsmethode zu verwenden, es sei denn, Sie haben eine bestimmte Voraussetzung, die AD FS erfordert. Die Synchronisierung von Kennwörtern bietet viele der Vorteile von AD FS, aber ohne die Komplexität der Bereitstellung. In der folgenden Tabelle werden einige häufige Vor- und Nachteile der einzelnen Optionen beschrieben.


> [!NOTE]
> Wenn Sie AD FS bereitstellen und Ihre lokalen AD FS-Server aus irgendeinem Grund nicht aus dem Internet erreichbar sind, verwendet Office 365 standardmäßig wieder die Synchronisierung von Kennwörtern zum Authentifizieren von Benutzern. Dadurch können Benutzer mit Office 365-Postfächern auch dann unterbrechungsfrei weiterarbeiten, wenn Ihre lokalen Server nicht verfügbar sind.



Weitere Informationen zu den einzelnen Optionen finden Sie unter [Azure AD Connect-Optionen für die Benutzeranmeldung](http://go.microsoft.com/fwlink/p/?linkid=723514).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Methode für einmaliges Anmelden</p></th>
<th><p>Vorteile</p></th>
<th><p>Nachteile</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Kennwortsynchronisierung (empfohlen)</p></td>
<td><ul>
<li><p>Deutlich weniger komplex als AD FS.</p></li>
<li><p>Benutzer können sich bei Office 365 auch dann anmelden, wenn Ihr lokales Active Directory nicht verfügbar ist.</p></li>
<li><p>Zum Bereitstellen der Kennwortsynchronisierung sind weniger zusätzliche Server erforderlich.</p></li>
<li><p>Es sind keine Drittanbieterzertifikate erforderlich.</p></li>
<li><p>Externer Zugriff auf Ihr lokales Active Directory über AD FS ist nicht erforderlich.</p></li>
<li><p>Die Bereitstellung kann häufig innerhalb weniger Stunden abgeschlossen werden.</p></li>
</ul></td>
<td><ul>
<li><p>Durch das Deaktivieren eines Benutzerkontos in Ihrem lokalen Active Directory wird es nicht in Office 365 deaktiviert. Sie müssen das Konto manuell im Office 365 Admin-Portal deaktivieren.</p></li>
<li><p>Erfordert lokales Active Directory. Andere Verzeichnisdienste werden nicht unterstützt.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>AD FS</p></td>
<td><ul>
<li><p>Kennwortänderungen sind sofort wirksam.</p></li>
<li><p>Durch das Deaktivieren eines Benutzers in Ihrem lokalen Active Directory wird der lokale Netzwerkzugriff und das Office 365-Konto dieses Benutzers deaktiviert.</p></li>
<li><p>Unterstützt andere Verzeichnisdienste als Active Directory.</p></li>
<li><p>Unterstützt sehr umfangreiche und unterschiedliche Bereitstellungen.</p></li>
<li><p>Unterstützt Zwei-Faktor-Authentifizierung.</p></li>
</ul></td>
<td><ul>
<li><p>Erfordert mehr Server, mindestens einen, der sich im Umkreisnetzwerk befinden muss.</p></li>
<li><p>Erfordert eine öffentliche IP-Adresse und das Öffnen des TCP-Ports 443 in der Firewall.</p></li>
<li><p>Konnektivität mit Ihrem lokalen Active Directory ist erforderlich, um Änderungen an Kontokennwörtern und das kürzliche Aktivieren und Deaktivieren eines Kontos zu erkennen.</p></li>
</ul></td>
</tr>
</tbody>
</table>


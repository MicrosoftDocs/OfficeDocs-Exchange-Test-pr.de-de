---
title: 'Vereinfachen der Outlook Web App-URL für Office 365 Hybrid: Exchange 2013 Help'
TOCTitle: Vereinfachen der Outlook Web App-URL für Office 365 Hybrid
ms:assetid: 19449aee-3796-4298-90c6-c7579b8d2f7a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt791749(v=EXCHG.150)
ms:contentKeyID: 74259164
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Vereinfachen der Outlook Web App-URL für Office 365 Hybrid

 

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-11-11_

Erfahren Sie, wie Sie eine URL für Outlook im Web (Outlook Web App) für Benutzer mit Cloudpostfach in einer Hybridumgebung konfigurieren.

Eine wichtige Rolle spielt für Organisationen, die von einer lokalen Exchange-Version zu Office 365 wechseln, das Benutzererlebnis. Benutzer benötigen ununterbrochenen Zugriff auf ihre Postfächer, unabhängig davon, wohin oder wann das Postfach verschoben wird. In Anbetracht dessen spielt die Koexistenz von Outlook im Web (früher Outlook Web App) eine wesentliche Rolle.

Betrachten Sie das folgende Szenario: Eine Firma verwendet eine Hybridbereitstellung, um einige ihrer Postfächer von einer lokalen Exchange-Version zu Office 365 zu verschieben. Am Freitag vor dem Verschieben haben die Benutzer auf ihre lokal gehosteten Postfächer über die URL „https://mail.contoso.com/owa“ zugegriffen. Am Montag nach dem Verschieben erhalten die gleichen Benutzer eine Fehlermeldung, wenn sie versuchen, mit dieser URL auf ihre Postfächer zuzugreifen.

Damit die betroffenen Benutzer mit Outlook im Web eine Verbindung mit ihren Postfächern herstellen können, stehen Ihnen zwei Optionen zur Verfügung:

  - **Informieren Sie die Benutzer über die neue URL (z. B. https://outlook.com/owa/contoso.com)**   Die Probleme mit dieser Option sind:
    
      - Die URL ist komplex.
    
      - Der Übergang erfolgt für die betroffenen Benutzer nicht nahtlos.

  - **Konfigurieren Sie die TargetOWAUrl-Einstellung für die Organisationsbeziehung**   Die Probleme mit dieser Option sind:
    
      - Der Endpunkt für die Cloudpostfächer ist extern (er befindet sich nicht in der von den Benutzern erwarteten Domäne).
    
      - Der Endpunkt benötigt die Angabe der Domäne in der URL (zur Unterscheidung zwischen geschäftlichen Angeboten von Office 365 und Angeboten für Heimanwender von outlook.com).
    
      - Aufgrund des Endpunkts werden Benutzern Warnungen wegen Zertifikatkonflikten angezeigt.

Führen Sie die folgenden Schritte aus, um diese Probleme für Benutzer mit Cloudpostfächern zu beheben:

1.  **Erstellen eines CNAME-Eintrags in DNS (z. B. cloudowa.contoso.com), der auf „mail.office365.com“ verweist**
    
      - Achten Sie darauf, diesen CNAME-Eintrag in Ihrem internen und externen (öffentlichen) DNS zu erstellen, da Benutzer über interne oder externe Internetverbindungen eine Verbindung herstellen können.
    
      - In diesem Beispiel wird die Domäne „contoso.com“ in der Anforderung verwendet (der „cloudowa“-Teil wird gelöscht). Dies bedeutet, dass Sie die Domäne nicht in der URL angeben müssen.

2.  **Konfigurieren der Outlook im Web-Umleitung in der lokalen Organisationsbeziehung**   Zu diesem Zweck verwenden Sie die folgende Syntax in der Exchange-Verwaltungsshell in der lokalen Exchange-Version:
    
        Set-OrganizationRelationship -TargetOWAUrl http://<CNAME value>/owa
    
    Beispiel: Wenn der in Schritt 1 erstellte CNAME-Eintrag „cloudowa.contoso.com“ lautet, führen Sie den folgenden Befehl aus:
    
        Set-OrganizationRelationship -TargetOWAUrl http://cloudowa.contoso.com/owa
    
    **Hinweise:**
    
      - Verwenden Sie „http“, nicht „https“.
    
      - Der nachgestellte Wert "/owa" ist in der Organisationsbeziehung erforderlich, aber die Benutzer müssen "/owa" nicht in der URL eingeben.

## Mehrere Authentifizierungsaufforderungen

Benutzer erhalten möglicherweise mehrere Authentifizierungsaufforderungen, abhängig von folgenden Faktoren:

  - von wo sie die Verbindung herstellen (interne oder externe Internetverbindungen)

  - ob ihr Computer einer Domäne beigetreten ist oder nicht

  - ob Sie in Ihrer Hybridumgebung einen Identitätsverbund verwenden

Die Authentifizierungsaufforderungen, die Benutzer erwarten können, werden in der folgenden Tabelle beschrieben.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Authentifizierungsmethode</th>
<th>Clientcomputer</th>
<th>Authentifizierungsaufforderungserfahrung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Identitätsverbund</p></td>
<td><p>Interne Internetverbindung</p></td>
<td><p>Einzelne Aufforderung</p></td>
</tr>
<tr class="even">
<td><p>Identitätsverbund</p></td>
<td><p>Externe Internetverbindung</p></td>
<td><p>Doppelte Aufforderung</p></td>
</tr>
<tr class="odd">
<td><p>Kein Identitätsverbund</p></td>
<td><p>Einer Domäne beigetreten (intern oder extern)</p></td>
<td><p>Doppelte Aufforderung</p></td>
</tr>
<tr class="even">
<td><p>Mit oder ohne Identitätsverbund</p></td>
<td><p>Keiner Domäne beigetreten (intern oder extern)</p></td>
<td><p>Doppelte Aufforderung</p></td>
</tr>
</tbody>
</table>


**Hinweis:** Für einen Identitätsverbund muss der AD FS-Endpunkt in der Intranetzone von Internet Explorer konfiguriert sein, wie im Thema <https://go.microsoft.com/fwlink/p/?linkid=834460> beschrieben, und AD FS muss entsprechend der allgemeinen Office 365-Anleitung konfiguriert sein.


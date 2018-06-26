---
title: 'Account setup in Outlook for iOS and Android using basic authentication: Exchange 2013 Help'
TOCTitle: Account setup in Outlook for iOS and Android using basic authentication
ms:assetid: 013dbe8c-30de-4c9c-baa9-75081b9229e8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt829322(v=EXCHG.150)
ms:contentKeyID: 74518377
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Account setup in Outlook for iOS and Android using basic authentication

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2018-04-30_

**Zusammenfassung:** Hier erfahren Sie, wie Benutzer in Ihrer Exchange 2013-Organisation schnell ihre Outlook für IOS und Android-Konten mit der Standardauthentifizierung einrichten können.

Outlook für IOS und Android bietet Exchange-Administratoren die Möglichkeit, Kontokonfigurationen an ihre lokalen Benutzer zu senden, die Standardauthentifizierung über das ActiveSync-Protokoll verwenden. Dies funktioniert mit jedem MDM-Anbieter (Verwaltung mobiler Geräte), der den Kanal [Konfiguration verwalteter Apps](https://developer.apple.com/library/content/samplecode/sc2279/introduction/intro.html) für iOS oder den Kanal [Android im Unternehmen](https://developer.android.com/samples/apprestrictions/index.html) für Android verwendet.

Für lokale Benutzer, die in Microsoft Intune registriert sind, können Sie die Kontokonfigurationseinstellungen mithilfe von Intune im Azure-Portal bereitstellen.

Nachdem eine Kontokonfiguration erstellt wurde und der Benutzer sein Gerät registriert hat, erkennt Outlook für iOS und Android, dass ein Konto gefunden wurde, und fordert den Benutzer auf, das Konto hinzuzufügen. Die einzige Information, die der Benutzer eingeben muss, um die Einrichtung abzuschließen, ist sein Kennwort. Dann wird der Postfachinhalt des Benutzers geladen, und der Benutzer kann mit der Verwendung der App beginnen.

Das folgende Bild zeigt ein Beispiel für den Setupvorgang für Endbenutzer, nachdem Outlook für iOS und Android in Intune im Azure-Portal konfiguriert wurde.

![Outlook-Kontoeinrichtung auf lokalen iOS- und Android-Geräten](images/Mt829322.04bd56f2-5c45-4268-8762-436994acd656(EXCHG.150).png "Outlook-Kontoeinrichtung auf lokalen iOS- und Android-Geräten")

## Erstellen einer App-Konfigurationsrichtlinie für Outlook für iOS und Android mithilfe von Microsoft Intune

Wenn Sie Microsoft Intune als Anbieter für die Verwaltung mobiler Geräte verwenden, können Sie mit den folgenden Schritten Kontokonfigurationseinstellungen für Ihre lokalen Postfächer bereitstellen, die Standardauthentifizierung mit dem ActiveSync-Protokoll nutzen. Nachdem die Konfiguration erstellt wurde, können Sie die Einstellungen Gruppen von Benutzern zuweisen, wie im nächsten Abschnitt, Zuweisen von Konfigurationseinstellungen, beschrieben.


> [!NOTE]
> Wenn Benutzer in Ihrer Organisation sowohl IOS- als auch Android for Work-Geräte verwenden, müssen Sie gesonderte App-Konfigurationsrichtlinien für jede Plattform erstellen.



1.  Melden Sie sich beim Azure-Portal an.

2.  Wählen Sie **Weitere Dienste \> Überwachung und Verwaltung \> Intune**.

3.  Wählen Sie auf dem Blatt **Mobile Apps** der Liste „Verwalten\&quot; die Option **App-Konfigurationsrichtlinien** aus.

4.  Klicken Sie auf dem Blatt **App-Konfigurationsrichtlinien** auf **Hinzufügen**.

5.  Geben Sie auf dem Blatt **App-Konfiguration hinzufügen** einen **Namen** und eine optionale **Beschreibung** für die App-Konfigurationseinstellungen ein.

6.  Wählen Sie für den Typ **Geräteregistrierung** die Option **Verwaltete Geräte** aus.

7.  Wählen Sie für **Plattform** die Option **iOS** oder **Android for Work** aus.

8.  Wählen Sie **Zugeordnete Apps** aus, und wählen Sie dann auf dem Blatt **Ziel-Apps** die App **Microsoft Outlook für iOS** oder **Microsoft Outlook für Android** aus.

9.  Klicken Sie auf **OK**, um zum Blatt **App-Konfiguration hinzufügen** zurückzukehren.

10. Wählen Sie **Konfigurationseinstellungen** aus. Definieren Sie auf dem Blatt **Konfigurationseinstellungen** die Schlüssel-Wert-Paare, die Konfigurationen für Outlook für iOS und Android bereitstellen sollen. Die Schlüssel-Wert-Paare, die Sie eingeben, werden weiter unten in diesem Artikel im Abschnitt Schlüssel-Wert-Paare definiert.
    

    > [!NOTE]
    > Zur Eingabe der Schlüssel-Wert-Paare haben Sie die Wahl zwischen der Verwendung des Konfigurations-Designers oder der Eingabe einer Liste von XML-Eigenschaften.



11. Wenn Sie fertig sind, klicken Sie auf **OK**.

12. Klicken Sie auf dem Blatt **App-Konfiguration hinzufügen** auf **Erstellen**.

Die neu erstellte Konfigurationsrichtlinie wird auf dem Blatt **App-Konfigurationsrichtlinien** angezeigt.

## Zuweisen von Konfigurationseinstellungen

Sie weisen die Einstellungen, die Sie im vorherigen Abschnitt erstellt haben, Gruppen von Benutzern in Azure Active Directory zu. Wenn ein Benutzer die Microsoft Outlook-App installiert hat, wird die App von den Einstellungen verwaltet, die Sie angegeben haben. Gehen Sie zu diesem Zweck wie folgt vor:

1.  Wählen Sie auf dem Blatt **Mobile Apps** des Intune-Management-Dashboards für mobile Anwendungen **App-Konfiguration** aus.

2.  Wählen Sie in der Liste der App-Konfigurationsrichtlinien die Konfiguration aus, die Sie zuweisen möchten, und wählen Sie dann **Zuweisungen** aus.

3.  Klicken Sie auf dem Blatt **Zuweisungen** auf **Gruppen auswählen**.

4.  Wählen Sie auf dem Blatt **Gruppen auswählen** die Azure AD-Gruppe aus, der Sie die App-Konfigurationsrichtlinie zuweisen möchten. Klicken Sie anschließend auf **Auswählen** und dann auf **Speichern**.

## Schlüssel-Wert-Paare

Wenn Sie eine App-Konfigurationsrichtlinie im Azure-Portal oder über Ihren MDM-Anbieter erstellen, benötigen Sie die folgenden Schlüssel-Wert-Paare:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Schlüssel</th>
<th>Werte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>com.microsoft.outlook.EmailProfile.EmailAccountName</p></td>
<td><p>Dieser Wert gibt den Anzeigenamens des E-Mail-Kontos an, wie er für Benutzer auf ihren Geräten angezeigt werden soll.</p>
<p><strong>Akzeptierte Werte</strong>: String</p>
<p><strong>Standard, wenn nicht angegeben</strong>: &lt;leer&gt;</p>
<p><strong>Beispiel</strong>: user@companyname.com</p>
<p><strong>Intune Token*</strong>: {{username}}</p></td>
</tr>
<tr class="even">
<td><p>com.microsoft.outlook.EmailProfile.EmailAddress</p></td>
<td><p>Dieser Wert gibt die E-Mail-Adresse an, die zum Senden und Empfangen von E-Mail verwendet werden soll.</p>
<p><strong>Akzeptierte Werte</strong>: String</p>
<p><strong>Standard, wenn nicht angegeben</strong>: &lt;leer&gt;</p>
<p><strong>Beispiel</strong>: user@companyname.com</p>
<p><strong>Intune Token*</strong>: {{mail}}</p></td>
</tr>
<tr class="odd">
<td><p>com.microsoft.outlook.EmailProfile.EmailUPN</p></td>
<td><p>Dieser Wert gibt den User Principal Name für das E-Mail-Profil an, das verwendet wird, um das Konto zu authentifizieren.</p>
<p><strong>Akzeptierte Werte</strong>: String</p>
<p><strong>Standard, wenn nicht angegeben</strong>: &lt;leer&gt;</p>
<p><strong>Beispiel</strong>: userupn@companyname.com</p>
<p><strong>Intune Token*</strong>: {{userprincipalname}}</p></td>
</tr>
<tr class="even">
<td><p>com.microsoft.outlook.EmailProfile.ServerAuthentication</p></td>
<td><p>Dieser Wert gibt die Authentifizierungsmethode für den Benutzer an.</p>
<p><strong>Akzeptierte Werte</strong>: &quot;Benutzername und Kennwort&quot;; &quot;Zertifikate&quot;</p>
<p><strong>Standard, wenn nicht angegeben</strong>: &quot;Benutzername und Kennwort&quot;</p>
<p><strong>Beispiel</strong>: &quot;Benutzername und Kennwort&quot;</p></td>
</tr>
<tr class="odd">
<td><p>com.microsoft.outlook.EmailProfile.ServerHostName</p></td>
<td><p>Dieser Wert gibt den Hostnamen Ihres Exchange-Servers an.</p>
<p><strong>Akzeptierte Werte</strong>: String</p>
<p><strong>Standard, wenn nicht angegeben</strong>: &lt;leer&gt;</p></td>
</tr>
</tbody>
</table>


**\*** Microsoft Intune-Benutzer können Token verwenden, die entsprechend dem bei MDM registrierten Benutzer zum richtigen Wert erweitert werden. Weitere Informationen finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte](https://docs.microsoft.com/de-de/intune/app-configuration-policies-use-ios).


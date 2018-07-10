---
title: 'Ändern der AD LDS-Konfiguration: Exchange 2013 Help'
TOCTitle: Ändern der AD LDS-Konfiguration
ms:assetid: 381f582c-15ec-43bc-b674-5399fad72c97
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997269(v=EXCHG.150)
ms:contentKeyID: 61180466
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern der AD LDS-Konfiguration

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können das Skript **ConfigureAdam.ps1** (unter "$env:ExchangeInstallPath\\Scripts") verwenden, um die Standardkonfiguration für Active Directory Lightweight Directory Services (AD LDS) auf Edge-Transport-Servern zu ändern, bevor Sie die Exchange-Organisation für den Edge-Transport-Server abonnieren.


> [!IMPORTANT]
> Das Skript <STRONG>ConfigureAdam.ps1</STRONG> ruft den Befehl <STRONG>dsdbutil</STRONG> zum Ändern der Registrierungseinstellungen für AD&nbsp;LDS auf. Der Befehl <STRONG>dsdbutil</STRONG> ist ein Verwaltungstool für AD&nbsp;LDS, das nur von erfahrenen Administratoren verwendet werden sollte; empfohlen wird die Verwendung von <STRONG>ConfigureAdam.ps1</STRONG> zur Änderung der AD&nbsp;LDS-Konfiguration.



Die Parameter in der folgenden Tabelle sind für das Skript **ConfigureAdam.ps1** verfügbar. Sie können einen, alle oder eine Kombination aus diesen Parametern zum Ändern von AD LDS verwenden.

### Für das Skript "ConfigureAdam.ps1" verfügbare Parameter

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Ldapport</em></p></td>
<td><p>Ändert den für die LDAP-Kommunikation verwendeten Port. Standardmäßig verwendet der Edge-Transport-Server den nicht standardmäßigen Port 50389.</p></td>
</tr>
<tr class="even">
<td><p><em>Sslport</em></p></td>
<td><p>Ändert den für die sichere LDAP-Kommunikation verwendeten Port. Standardmäßig verwendet der Edge-Transport-Server den nicht standardmäßigen Port 50636.</p></td>
</tr>
<tr class="odd">
<td><p><em>LogPath</em></p></td>
<td><p>Ändert den Speicherort der Protokolldatei. Standardmäßig erstellt der Edge-Transport-Server Protokolldateien im Pfad &quot;%ExchangeInstallationspfad%Transport Roles\Data\adam&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>DataPath</em></p></td>
<td><p>Ändert den Speicherort der Verzeichnisdatenbankdatei. Standardmäßig speichert der Edge-Transport-Server die Verzeichnisdatenbank im Pfad &quot;%ExchangeInstallationspfad%Transport Roles\Data\adam&quot;.</p></td>
</tr>
</tbody>
</table>


## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Edge-Transport-Server" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Wenn Sie Änderungen an der AD LDS-Konfiguration des Edge-Transport-Servers vornehmen möchten, tun Sie dies, bevor Sie die Exchange-Organisation für den Edge-Transport-Server abonnieren. Wenn Sie die AD LDS-Konfiguration eines abonnierten Edge-Transport-Servers ändern, müssen Sie die Exchange-Organisation erneut für den Edge-Transport-Server abonnieren.

  - Verwenden Sie immer das Skript, um die Registrierungseinstellungen zu ändern. Nach manuellen Registrierungsänderungen an der AD LDS-Konfiguration ist die AD LDS-Instanz möglicherweise nicht mehr verfügbar.

  - Wenn Sie den von AD LDS verwendeten LDAP- oder SSL-Port ändern, stellen Sie zunächst sicher, dass der ausgewählte Port nicht von einer anderen Anwendung verwendet wird. Sie können den Befehl **netstat** verwenden, um die auf dem Edge-Transport-Server verwendeten Ports anzuzeigen.

  - Die Shell kann nur für diesen Vorgang verwendet werden.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Ändern der AD LDS-Konfiguration auf einem Edge-Transport-Server

In diesem Beispiel wird der von AD LDS verwendete LDAP-Port in 5000 geändert. Das kaufmännischen Und-Zeichen (&) ist Teil der Befehlssyntax.

    & $env:ExchangeInstallPath\Scripts\ConfigureAdam.ps1 -LdapPort:5000

In diesem Beispiel werden folgende Änderungen an der AD LDS-Konfiguration vorgenommen. Das kaufmännischen Und-Zeichen (&) ist Teil der Befehlssyntax. Beachten Sie den Doppelpunkt (:) zwischen jedem Parameter und seinem Wert:

  - Stellt den LDAP-Port auf "5000" ein

  - Stellt den SSL-Port auf "500" ein

  - Ändert den Protokollpfad in "D:\\Exchange Server\\Data\\ADLDS"

  - Ändert den Datenpfad in "D:\\Exchange Server\\Data\\ADLDS"

<!-- end list -->

    & $env:ExchangeInstallPath\Scripts\ConfigureAdam.ps1 -LdapPort:5000 -SslPort:5001 -LogPath:"D:\Exchange Server\Data\ADLDS" -DataPath:"D:\Exchange Server\Data\ADLDS"


---
title: 'Einrichten von eingehenden Faxen: Exchange 2013 Help'
TOCTitle: Einrichten von eingehenden Faxen
ms:assetid: 5d3cae58-1690-424d-9bef-011911d0b608
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633468(v=EXCHG.150)
ms:contentKeyID: 52062707
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Einrichten von eingehenden Faxen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Microsoft Exchange Unified Messaging (UM) verwendet zertifizierte Faxpartnerlösungen, um erweiterte Faxfunktionen bereitzustellen, z. B. ausgehende Faxe oder Faxrouting. Standardmäßig sind Exchange-Server nicht so konfiguriert, dass eingehende Faxe an einen UM-aktivierten Benutzer zugestellt werden. Stattdessen leitet ein Exchange-Server eingehende Faxanrufe an eine zertifizierte Faxpartnerlösung um. Der Server des Faxpartners empfängt die Faxdaten und sendet sie dann in einer E-Mail-Nachricht, in die das Fax als TIF-Anlage eingeschlossen ist, an das Benutzerpostfach.

Weitere Informationen zu Faxpartnern finden Sie unter [Microsoft Pinpoint für Faxpartner](https://go.microsoft.com/fwlink/?linkid=190238)

## Bereitstellen und Konfigurieren von Faxfunktionen

UM leitet eingehende Faxanrufe an eine dafür vorgesehene Faxpartnerlösung weiter, die dann die Faxverbindung mit dem Faxabsender aufbaut und die Nachricht für den UM-aktivierten Benutzer empfängt. Damit UM-aktivierte Benutzer Faxnachrichten in ihren Postfächern erhalten, müssen Sie jedoch zunächst die Funktion für eingehende Faxanrufe aktivieren und den URI des Faxpartners in der UM-Postfachrichtlinie festlegen, die mit den UM-aktivierten Benutzern verknüpft ist. Eingehende Faxanrufe können in UM-Wählplänen, UM-Postfachrichtlinien und im Postfach für einen UM-aktivierten Benutzer erlaubt oder verhindert werden. Weitere Informationen finden Sie in den folgenden Themen:

  - [Zulassen des Empfangs von Faxnachrichten für Benutzer mit demselben Wählplan](allow-users-in-the-same-dial-plan-to-receive-faxes-exchange-2013-help.md)

  - [Verhindern, dass Benutzer in den gleichen Wähleinstellungen empfangen von Faxnachrichten](prevent-users-in-the-same-dial-plan-from-receiving-faxes-exchange-2013-help.md)

  - [Aktivieren von Faxen für eine Gruppe von Benutzern](enable-faxing-for-a-group-of-users-exchange-2013-help.md)

  - [Deaktivieren von Faxen für eine Gruppe von Benutzern](disable-faxing-for-a-group-of-users-exchange-2013-help.md)

  - [Aktivieren eines Benutzers für den Faxempfang](enable-a-user-to-receive-faxes-exchange-2013-help.md)

  - [Verhindert, dass Benutzer empfangen von Faxnachrichten](prevent-a-user-from-receiving-faxes-exchange-2013-help.md)

## Schritt 1: Bereitstellen von Unified Messaging

Bevor Sie die Faxfunktion für ihre lokale oder Hybridorganisation einrichten können, müssen Sie Clientzugriffs- und Postfachserver bereitstellen und Ihre unterstützten VoIP-Gateways (Voice over IP) für die Faxfunktion konfigurieren. Weitere Informationen zum Bereitstellen von UM finden Sie unter [Bereitstellen von Exchange 2013 UM](deploy-exchange-2013-um-exchange-2013-help.md). Einzelheiten zur Bereitstellung von VoIP-Gateways und IP-Nebenstellenanlagen finden Sie unter [Verbinden von UM mit Ihrer Telefonanlage](connect-um-to-your-telephone-system-exchange-2013-help.md).


> [!IMPORTANT]
> Das Senden und Empfangen von Faxen mithilfe von T.38 oder G.711 wird in einer Umgebung, in der Unified Messaging und MicrosoftOfficeCommunications Server 2007 R2 oder Microsoft Lync Server integriert sind, nicht unterstützt.



## Schritt 2: Konfigurieren von Faxpartnerservern

Als Nächstes müssen Sie die Funktion für eingehende Faxanrufe aktivieren und den URI des Faxpartners in allen UM-Postfachrichtlinien festlegen, die Sie in Ihrer Organisation benötigen. Zur erfolgreichen Bereitstellung der Funktion für eingehende Faxanrufe müssen Sie eine zertifizierte Faxpartnerlösung in Exchange Unified Messaging integrieren. Weitere Informationen finden Sie unter [Faxratgeber für Exchange UM](fax-advisor-for-exchange-um-exchange-2013-help.md). Eine Liste zertifizierter Faxpartner finden Sie unter [Microsoft PinPoint für Faxpartner](https://go.microsoft.com/fwlink/?linkid=190238)


> [!NOTE]
> Da der Faxpartnerserver außerhalb Ihrer Organisation liegt, müssen Firewallports für das Zulassen der T.38-Protokollports konfiguriert werden, die die Faxfunktion über ein IP-basiertes Netzwerk ermöglichen. Standardmäßig verwendet das T.38-Protokoll TCP-Port 6004. Es kann auch UDP-Port 6044 (User Datagram Protocol) verwenden, dies wird jedoch vom Hardwarehersteller definiert. Die Firewallports müssen für das Zulassen von Faxdaten konfiguriert werden, welche die vom Hersteller definierten TCP- oder UDP-Ports oder Portbereiche verwenden.



## Schritt 3: Aktivieren der Faxfunktion unter Unified Messaging

Drei Komponenten müssen konfiguriert werden, damit Benutzer Faxnachrichten mithilfe von Unified Messaging empfangen können:

  - UM-Wähleinstellungen

  - UM-Postfachrichtlinien

  - UM-Postfächer

Die Faxfunktion kann in UM-Wählplänen, in UM-Postfachrichtlinien oder Postfach eines einzelnen UM-aktivierten Benutzer aktiviert oder deaktiviert werden. UM-Postfachrichtlinien können entweder über die Exchange-Verwaltungskonsole oder über die Exchange-Verwaltungsshell für die Faxfunktion aktiviert oder deaktiviert werden. Das Aktivieren und Deaktivieren von Wählplänen und einzelnen UM-aktivierten Benutzern muss mithilfe der Exchange-Verwaltungsshell erfolgen. Die folgende Tabelle zeigt die verfügbaren Optionen sowie die Cmdlets und Parameter, die zum Aktivieren und Deaktivieren der Faxfunktion verwendet werden.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>UM-Komponente</th>
<th>Aktivieren/Deaktivieren mithilfe der Exchange-Verwaltungskonsole?</th>
<th>Shellbeispiel zum Aktivieren der Faxfunktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Wählplan</p></td>
<td><p>Nein</p></td>
<td><p><code>Set-UMDialPlan -id MyUMDialPlan -faxenabled $true</code></p></td>
</tr>
<tr class="even">
<td><p>UM-Postfachrichtlinie</p></td>
<td><p>Ja</p></td>
<td><p><code>Set-UMMaiboxPolicy -id MyPolicy -AllowFax $true</code></p></td>
</tr>
<tr class="odd">
<td><p>UM-aktivierter Benutzer</p></td>
<td><p>Nein</p></td>
<td><p><code>Set-UMMailbox -id tonysmith -faxenabled $true</code></p></td>
</tr>
</tbody>
</table>


Obwohl der UM-Wählplan und das Postfach eines Benutzers den Empfang eingehender Faxe standardmäßig zulässt, müssen Sie zunächst den Faxeingang in der dem UM-aktivierten Benutzer zugeordneten UM-Postfachrichtlinie aktivieren und dann den URI des Faxpartnerservers eingeben.

Gehen Sie folgendermaßen vor, um den Faxempfang für UM-aktivierte Benutzer zu ermöglichen:

  - Stellen Sie sicher, dass alle UM-Wähleinstellungen den Faxempfang für Benutzer, die diesen Wähleinstellungen zugeordnet sind, zulassen. Standardmäßig können alle Benutzer, die einem Satz Wähleinstellungen zugeordnet sind, Faxnachrichten empfangen. Damit UM-aktivierte Benutzer Faxnachrichten in ihrem Postfach empfangen, muss jedes VoIP-Gateway bzw. jede IP-Nebenstellenanlage für die Annahme eingehender Faxanrufe konfiguriert werden. Ferner müssen Sie ermöglichen, dass Faxnachrichten von Benutzern empfangen werden können, die mit dem Wählplan verknüpft sind. Weitere Informationen zum Ermöglichen oder Verhindern des Faxempfangs für Benutzer, die mit einem Wählplan verknüpft sind, finden Sie unter [Aktivieren eines Benutzers für den Faxempfang](enable-a-user-to-receive-faxes-exchange-2013-help.md).
    

    > [!NOTE]
    > Wenn Sie das Empfangen von Faxnachrichten für einen Wählplan deaktivieren, kann keiner der Benutzer, die diesem Wählplan zugeordnet sind, Faxnachrichten empfangen, selbst wenn Sie die Eigenschaften eines einzelnen Benutzers für den Empfang von Faxnachrichten konfigurieren. Das Aktivieren bzw. Deaktivieren von Faxnachrichten für einen Satz UM-Wähleinstellungen hat Vorrang vor den Einstellungen für einen einzelnen UM-aktivierten Benutzer.



  - Konfigurieren Sie die UM-Postfachrichtlinie, die dem UM-aktivierten Benutzer zugeordnet ist. Die UM-Postfachrichtlinie muss so konfiguriert sein, dass Sie den Empfang eingehender Faxnachrichten zulässt, einschließlich des Faxpartner-URI und des Namens des Faxpartnerservers. Der Parameter *FaxServerURI* muss das folgende Format verwenden: sip:\<*Faxserver-URI*\>:\<*Port*\>;\<*Transport*\>, wobei "Faxserver-URI" entweder dem vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) oder der IP-Adresse des Faxpartnerservers entspricht. "Port" ist der Port, der vom Faxserver auf eingehende Faxanrufe überwacht wird. "Transport" ist das Transportprotokoll, das für das eingehende Fax verwendet wird (UDP, TCP oder TLS (Transport Layer Security)). Beispielsweise können Sie eine UM-Postfachrichtlinie folgendermaßen für den Empfang eines Faxes konfigurieren.
    
        Set-UMMailboxPolicy MyUMMailboxPolicy -AllowFax $true -FaxServerURI "sip:faxserver.abc.com:5060;transport=tcp"

  - Weitere Informationen finden Sie unter [Festlegen des Partners Faxserver URI zum Senden von Faxen zulassen](set-the-partner-fax-server-uri-to-allow-faxing-exchange-2013-help.md).
    

    > [!WARNING]
    > Auch wenn Sie im Format für den <EM>FaxServerURI</EM> mehrere Einträge, durch Semikolon voneinander getrennt, aufnehmen können, wird nur ein Eintrag verwendet. Dieser Parameter erlaubt nur die Verwendung eines einzigen Eintrags, und durch das Hinzufügen mehrerer Einträge können Sie keinen Lastenausgleich für Faxanforderungen vornehmen.



  - Stellen Sie sicher, dass das UM-aktivierte Postfach Faxnachrichten empfangen kann. Standardmäßig können alle Benutzer, die einem Satz Wähleinstellungen zugeordnet sind, Faxnachrichten empfangen. Es kann jedoch Situationen geben, in denen Benutzer keine Faxnachrichten empfangen können, da der Faxempfang für ihr Postfach deaktiviert wurde. Weitere Informationen zum Aktivieren von UM-aktivierten Benutzern für den Empfang von Faxnachrichten finden Sie unter [Aktivieren eines Benutzers für den Faxempfang](enable-a-user-to-receive-faxes-exchange-2013-help.md).
    
    Sie können verhindern, dass ein einzelner, mit einem Wählplan verknüpfter Benutzer Faxnachrichten empfängt. Konfigurieren Sie hierzu die Eigenschaften für den Benutzer mithilfe des Cmdlets **Set-UMMailbox** in der Shell. Sie können auch das Cmdlet **Set-UMMailboxPolicy** verwenden, um mehrere Benutzer am Empfang von Faxnachrichten zu hindern. Weitere Informationen zum Hindern eines oder mehrerer Benutzer am Empfang von Faxnachrichten finden Sie unter [Verhindert, dass Benutzer empfangen von Faxnachrichten](prevent-a-user-from-receiving-faxes-exchange-2013-help.md).

## Schritt 4: Konfigurieren der Authentifizierung

Neben den UM-Wähleinstellungen, UM-Postfachrichtlinien und UM-aktivierten Benutzern müssen Sie auch die Authentifizierung zwischen Ihren Exchange-Servern und dem Faxpartnerserver konfigurieren. Die Exchange-Server müssen den Ursprung der Nachrichten authentifizieren, die angeblich vom Server des Faxpartners stammen. Nicht authentifizierte Nachrichten, die angeblich von einem Faxpartnerserver stammen, werden von einem Exchange-Server nicht verarbeitet.

Für die Authentifizierung der Verbindung vom Faxpartnerserver zu den Exchange-Servern können Sie Folgendes verwenden:

  - Mutual TLS

  - Sender ID-Überprüfung

  - Einen dedizierten Empfangsconnector

Ein Empfangsconnector sollte ausreichen, um die in Ihrer Organisation bereitgestellten Faxpartnerserver zu authentifizieren. Der Empfangsconnector gewährleistet, dass die Exchange-Server den gesamten vom Faxpartnerserver eingehenden Datenverkehr als authentifiziert behandeln.

Der Empfangsconnector wird auf einem Exchange-Server konfiguriert, der vom Faxpartnerserver zum Senden von SMTP-Faxnachrichten verwendet wird. Er muss mit den folgenden Werten konfiguriert werden:

  - *AuthMechanism: ExternalAuthoritative*

  - *PermissionGroups: ExchangeServers, PartnersFax*

  - *RemoteIPRanges: {the fax server's IP address}*

  - *RequireTLS: False*

  - *EnableAuthGSSAPI: False*

  - *LiveCredentialEnabled: False*

Weitere Informationen finden Sie unter [Connectors](connectors-exchange-2013-help.md).

Wenn der Faxpartnerserver Netzwerkdatenverkehr über ein öffentliches Netzwerk an einen Exchange-Server sendet, z. B. ein in der Cloud gehosteter dienstbasierter Faxpartnerserver, sollten Sie den Faxpartnerserver anhand einer Sender ID-Prüfung authentifizieren. Diese Art der Authentifizierung gewährleistet, dass die IP-Adresse, von der die Faxnachricht stammt, autorisiert ist, eine E-Mail-Nachricht im Namen der Faxpartnerdomäne zu senden, von der die Nachricht angeblich stammt. Zum Speichern der Sender ID-Datensätze (oder SPF-Datensätze (Sender Policy Framework)) wird DNS verwendet, und Faxpartner müssen ihre SPF-Datensätze in der DNS-Forward-Lookupzone veröffentlichen. Exchange überprüft die IP-Adressen durch eine DNS-Abfrage. Der Sender ID-Agent muss jedoch auf einem Postfachserver ausgeführt werden, um eine DNS-Abfrage ausführen zu können.

Sie können auch TLS zum Verschlüsseln des Netzwerkdatenverkehrs oder MTLS (Mutual TLS) für die Verschlüsselung und Authentifizierung zwischen dem Faxpartnerserver und den Exchange-Servern verwenden.


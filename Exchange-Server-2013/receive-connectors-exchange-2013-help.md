---
title: 'Empfangsconnectors: Exchange 2013 Help'
TOCTitle: Empfangsconnectors
ms:assetid: 17751a60-39fe-433f-84d2-bfc14ff4ba51
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996395(v=EXCHG.150)
ms:contentKeyID: 50475092
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Empfangsconnectors

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Empfangsconnectors steuern den Fluss eingehender Nachrichten, die an Ihre Exchange-Organisation gesendet werden. Diese Connectors werden auf Computern konfiguriert, auf denen Microsoft Exchange Server 2013 mit dem Transportdienst ausgeführt wird, oder im Front-End-Dienst auf einem Clientzugriffsserver. Sie können in der Exchange-Verwaltungskonsole oder in der Exchange-Verwaltungsshell erstellt werden.

Die für die interne Nachrichtenübermittlung erforderlichen Empfangsconnectors werden standardmäßig bei der Installation eines Clientzugriffs- oder Postfachservers erstellt.

Exchange 2013-Server, auf denen der Transportdienst ausgeführt wird, benötigen Empfangsconnectors für den Empfang von Nachrichten aus dem Internet, von E-Mail-Clients und von anderen E-Mail-Servern. Ein Empfangsconnector steuert die eingehenden Verbindungen zur Exchange-Organisation.

Jeder Empfangsconnector überwacht eingehende Verbindungen, die seinen Einstellungen entsprechen. Ein Empfangsconnector überwacht Verbindungen, die über eine bestimmte lokale IP-Adresse/einen Port und von einem angegebenen IP-Adressbereich empfangen werden. Sie können einen Empfangsconnector erstellen, wenn Sie steuern möchten, welche Server Nachrichten von einer bestimmten IP-Adresse oder einem IP-Adressbereich empfangen, und wenn Sie spezielle Connectoreigenschaften für Nachrichten konfigurieren möchten, die von einer bestimmten IP-Adresse empfangen werden, beispielsweise das Zulassen größerer Nachrichten oder einer größeren Anzahl von Empfängern pro Nachricht. Außerdem können Sie mit dem Parameter *TlsCertificateName* des Cmdlets **Set-ReceiveConnector** einen Bereich für den Empfangsconnector festlegen. Mit diesem Parameter geben Sie das Zertifikat an, das für den Connector verwendet werden soll.

Empfangsconnectors sind auf einen einzelnen Server beschränkt und bestimmen, wie dieser spezielle Server Verbindungen überwacht. Wenn Sie einen Empfangsconnector auf einem Postfachserver mit dem Transportdienst erstellen, wird der Empfangsconnector in Active Directory als untergeordnetes Objekt des Servers gespeichert, auf dem er erstellt wird.

Wenn Sie für bestimmte Szenarien weitere Empfangsconnectors benötigen, können Sie diese mithilfe der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell erstellen. Für jeden Empfangsconnector muss eine eindeutige Kombination aus IP-Adressbindungen, Portnummernzuweisungen und Remote-IP-Adressbereichen angegeben werden, von denen E-Mails akzeptiert werden.

Weitere Informationen zum Erstellen eines Empfangsconnectors finden Sie unter [Verfahren für Empfangsconnectors](receive-connector-procedures-exchange-2013-help.md).

**Inhalt**

Während der Installation erstellte Standardempfangsconnectors

Standardempfangsconnectors, die auf einem Postfachserver mit dem Transportdienst erstellt werden

Standardempfangsconnectors, die auf einem Front-End-Transport-Server erstellt werden

Empfangsconnectortypen

Berechtigungsgruppen für Empfangsconnectors

Spezifikationen des Empfangsconnectortyps

Empfangsconnectorberechtigungen

Authentifizierungseinstellungen für Empfangsconnectors

Neue Empfangsconnectorfunktionen in Exchange 2013

## Während der Installation erstellte Standardempfangsconnectors

Bei der Installation der Postfachserverrolle werden standardmäßig bestimmte Connectors erstellt.

## Standardempfangsconnectors, die auf einem Postfachserver mit dem Transportdienst erstellt werden

Standardmäßig werden zwei Empfangsconnectors erstellt, wenn ein Postfachserver mit dem Transportdienst installiert wird. Für den Normalbetrieb sind keine zusätzlichen Empfangsconnectors erforderlich, und in den meisten Fällen erfordern Standardempfangsconnectors keine Konfigurationsänderung. Zu diesen Connectors gehören folgende:

  - **Standardmäßiger \<Servername\>**   Akzeptiert Verbindungen von Postfachservern, auf denen der Transportdienst ausgeführt wird, und von Edgeservern.

  - **Clientproxy-\<Servername\>**   Akzeptiert Verbindungen von Front-End-Servern. Nachrichten werden typischerweise über SMTP an einen Front-End-Server gesendet.

Jedem Connector wird ein *TransportRole*-Wert zugewiesen. Anhand dieses Werts können Sie die Rolle ermitteln, auf der der Connector ausgeführt wird. Dies kann nützlich sein, wenn Sie mehrere Rollen auf einem einzigen Server ausführen. Bei den zuvor erwähnten Empfangsconnectors lautet der *TransportRole*-Wert **HubTransport**.

Zum Anzeigen der Standardempfangsconnectors und ihrer Parameterwerte können Sie das Cmdlet [Get-ReceiveConnector](https://technet.microsoft.com/de-de/library/aa998618\(v=exchg.150\)) verwenden.

## Standardempfangsconnectors, die auf einem Front-End-Transport-Server erstellt werden

Während der Installation werden drei Empfangsconnectors auf dem Front-End-Transport- oder Clientzugriffsserver erstellt. Der standardmäßige Front-End-Empfangsconnector ist so konfiguriert, dass SMTP-Verbindungen aus allen IP-Adressbereichen zulässig sind. Zusätzlich ist ein Empfangsconnector vorhanden, der als ausgehender Proxy für Nachrichten agieren kann, die von Postfachservern an den Front-End-Server gesendet werden. Und schließlich ist ein sicherer Empfangsconnector vorhanden, der mit TLS (Transport Layer Security) verschlüsselte Nachrichten akzeptiert. Zu diesen Connectors gehören folgende:

  - **Standardmäßiger Front-End-\<Servername\>**   Akzeptiert Verbindungen von SMTP-Absendern an Port 25. Dies ist der gängige Eintrittspunkt für Nachrichten, die an Ihre Organisation gesendet werden.

  - **Ausgehender Proxy-Front-End-\<Servername\>**   Akzeptiert Nachrichten von einem Sendeconnector auf einem Back-End-Server, auf dem der Front-End-Proxy aktiviert ist.

  - **Client-Front-End-\<Servername\>**   Akzeptiert sichere Verbindungen mit Transport Layer Security (TLS).

In einer typischen Installation sind keine zusätzlichen Empfangsconnectors erforderlich.

## Empfangsconnectortypen

Der Typ eines Empfangsconnectors bestimmt die standardmäßigen Sicherheitseinstellungen, die auf diesen Connector angewendet werden.

In den Sicherheitseinstellungen eines Empfangsconnectors werden die Berechtigungen festgelegt, die für Sitzungen gewährt werden, in denen die Verbindung zum Empfangsconnector hergestellt wird, sowie die unterstützten Authentifizierungsmechanismen.

Wenn Sie zum Konfigurieren eines Empfangsconnectors die Exchange-Verwaltungskonsole verwenden, werden Sie auf der Seite für neue Empfangsconnectors aufgefordert, einen Typ für den Connector anzugeben. Abhängig von Ihrer Auswahl werden anschließend die entsprechenden Parameter für die gewählte Konfiguration festgelegt. In spezifischen Verfahren finden Sie weitere Informationen zu den Einstellungen für den Empfangsconnectortyp. Beispiele für diese Verfahren sind [Erstellen eines Empfangsconnectors zum Empfang von E-Mails aus dem Internet](create-a-receive-connector-to-receive-email-from-the-internet-exchange-2013-help.md) und [Erstellen eines sicheren Empfangsconnectors, um E-Mails von einem Partner zu empfangen](create-a-secure-receive-connector-to-receive-email-from-a-partner-exchange-2013-help.md).

## Berechtigungsgruppen für Empfangsconnectors

Eine Berechtigungsgruppe ist ein vordefinierter Satz Berechtigungen, die vertrauenswürdigen Sicherheitsprinzipalen gewährt und einem Empfangsconnector zugewiesen werden. Sicherheitsprinzipale beinhalten Benutzer, Computer und Sicherheitsgruppen. Die Verwendung von Berechtigungsgruppen vereinfacht die Konfiguration von Berechtigungen für Empfangsconnectors. Die Eigenschaft **PermissionGroups** definiert die Gruppen oder Rollen, die Nachrichten an den Empfangsconnector übermittelt können, sowie die Berechtigungen, die diesen Gruppen zugewiesen sind.

Zu den Berechtigungsgruppen zählen *Anonymous*, *ExchangeUsers*, *ExchangeServers*, *ExchangeLegacyServers* und *Partner*.

## Spezifikationen des Empfangsconnectortyps

Mit dem Typ werden die standardmäßigen Berechtigungsgruppen festgelegt, die dem Empfangsconnector zugewiesen werden, sowie die standardmäßigen Authentifizierungsmechanismen, die für die Sitzungsauthentifizierung zur Verfügung stehen. In der folgenden Liste sind die verfügbaren Typen beschrieben:

1.  **Client**   Dieser Typ wird üblicherweise für Verbindungen mit Clients verwendet, die nicht Microsoft Office Outlook verwenden. Mit diesem Typ kann die TLS-Authentifizierung verwendet werden.

2.  **Benutzerdefiniert**   Dieser Typ wird üblicherweise in einem gesamtstrukturübergreifenden Szenario oder in einem Szenario verwendet, in dem eine Organisation Nachrichten von einem Agent für die Übermittlung von SMTP-Nachrichten empfängt.

3.  **Intern**   Dieser Typ wird für die Kommunikation zwischen Servern verwendet, auf denen der Transportdienst ausgeführt wird, oder zwischen Postfachservern, auf denen der Transportdienst und Übermittlungs-Agents anderer Anbieter ausgeführt werden.

4.  **Internet**   Dieser Typ wird für den Empfang von SMTP-Nachrichten aus dem Internet verwendet.

5.  **Partner**   Verwenden Sie diesen Typ, um eine sichere Kommunikation mit einem Partner zu konfigurieren.

Jeder Typ ist für ein bestimmtes Verbindungsszenario ausgelegt. Wählen Sie den Typ, dessen Standardeinstellungen am besten für die gewünschte Konfiguration geeignet sind. Berechtigungen können mit den Cmdlets **Add-ADPermission** und **Remove-ADPermission** geändert werden. Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Add-ADPermission](https://technet.microsoft.com/de-de/library/bb124403\(v=exchg.150\))

  - [Remove-ADPermission](https://technet.microsoft.com/de-de/library/aa996048\(v=exchg.150\))

## Empfangsconnectorberechtigungen

Berechtigungen für Empfangsconnectors werden Sicherheitsprinzipalen zugewiesen, wenn Sie die Berechtigungsgruppen für den Connector festlegen. Wenn ein Sicherheitsprinzipal eine Sitzung zu einem Empfangsconnector aufbaut, bestimmen die Berechtigungen des Empfangsconnectors, ob die Sitzung akzeptiert wird und wie empfangene Nachrichten verarbeitet werden. Empfangsconnectorberechtigungen können mithilfe der Exchange-Verwaltungskonsole oder mit dem Cmdlet **Set-ReceiveConnector** und dem Parameter *PermissionGroups* in der Shell festgelegt werden. Zum Ändern der Standardberechtigungen für einen Empfangsconnector können Sie auch das Cmdlet **Add-ADPermission** verwenden.

[Empfangsconnectorberechtigungen](receive-connector-permissions-exchange-2013-help.md) enthält eine Tabelle, in der die Sicherheitsprinzipale und Berechtigungstypen im Detail aufgeführt sind.

## Authentifizierungseinstellungen für Empfangsconnectors

In der Exchange-Verwaltungskonsole verwenden Sie die Authentifizierungseinstellungen für einen Empfangsconnector, um die Authentifizierungsmechanismen anzugeben, die vom Exchange 2013-Transportserver unterstützt werden. In der Shell verwenden Sie den Parameter *AuthMechanisms*, um die unterstützten Authentifizierungsmechanismen anzugeben. Sie können für einen Empfangsconnector mehr als einen Authentifizierungsmechanismus konfigurieren. Weitere Informationen finden Sie unter [Authentifizierungsmechanismen für Empfangsconnectors](receive-connector-authentication-mechanisms-exchange-2013-help.md).

## Neue Empfangsconnectorfunktionen in Exchange 2013

Die folgenden Funktionen wurden in Exchange 2013 hinzugefügt:

  - Über den Parameter *TlsCertificateName* können Sie das von der lokalen Zertifizierungsstelle ausgegebene Zertifikat angeben, das für den sicheren E-Mail-Transport verwendet wird. Dadurch wird die Gefahr durch betrügerische Zertifikate gemindert.

  - Der Parameter *TransportRole* bestimmt die Serverrolle, die diesem Connector zugeordnet ist. Er wird in der Regel zum Angeben der Serverrolle verwendet, wenn Sie mehrere Serverrollen auf einem Computer hosten.

Weitere Informationen zu diesen Parametern und anderen Parametern für Empfangsconnectors finden Sie unter [New-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125139\(v=exchg.150\)).


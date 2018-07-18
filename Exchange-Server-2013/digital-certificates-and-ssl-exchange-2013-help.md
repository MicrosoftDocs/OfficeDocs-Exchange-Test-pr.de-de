---
title: 'Digitale Zertifikate und SSL: Exchange 2013 Help'
TOCTitle: Digitale Zertifikate und SSL
ms:assetid: a9e2e08c-d46a-4135-a387-eb653212b676
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351044(v=EXCHG.150)
ms:contentKeyID: 51409327
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Digitale Zertifikate und SSL

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-08-26_

SSL (Secure Sockets Layer) ist ein Verfahren zum Schutz der Kommunikation zwischen einem Client und einem Server. In Exchange Server 2013 wird SSL zur Absicherung der Kommunikation zwischen dem Server und Clients verwendet. Clients sind z. B. Mobiltelefone sowie Computer innerhalb und außerhalb des Netzwerks einer Organisation.

Bei der Installation von Exchange 2013 wird die Clientkommunikation standardmäßig mit SSL verschlüsselt, wenn Sie Outlook Web App, Exchange ActiveSync und Outlook Anywhere verwenden.

SSL setzt voraus, dass Sie digitale Zertifikate verwenden. In diesem Thema erhalten Sie einen Überblick über die verschiedenen Arten digitaler Zertifikate und Informationen dazu, wie Sie Exchange 2013 für die Verwendung dieser digitalen Zertifikate konfigurieren.

**Inhalt**

Übersicht über digitale Zertifikate

Digitale Zertifikate und Proxyfunktion

Bewährte Methoden für digitale Zertifikate

## Übersicht über digitale Zertifikate

Digitale Zertifikate sind elektronische Dateien, die wie Onlinekennwörter funktionieren, um die Identität eines Benutzers oder eines Computers zu überprüfen. Sie werden verwendet, um den SSL-verschlüsselten Kanal zu erstellen, der für die Clientkommunikation verwendet wird. Ein Zertifikat ist eine digitale Bescheinigung von einer Zertifizierungsstelle (Certification Authority, CA), die die Identität des Zertifikatinhabers bestätigt und den Parteien eine sichere Kommunikation durch die Verschlüsselung von Daten ermöglicht.

Digitale Zertifikate bewirken Folgendes:

  - Sie bestätigen, dass ihre Inhaber – Personen, Websites und sogar Netzwerkressourcen wie z. B. Router – wirklich das sind, was sie vorgeben zu sein.

  - Sie schützen online ausgetauschte Daten vor Diebstahl und Manipulation.

Digitale Zertifikate können von einer vertrauenswürdigen Zertifizierungsstelle eines Drittanbieters oder einer Windows-PKI (Public Key-Infrastruktur) unter Verwendung von Zertifikatdiensten ausgestellt werden oder selbstsigniert sein. Jeder Zertifikattyp hat Vor- und Nachteile. Alle Arten von digitalen Zertifikaten sind manipulationssicher und können nicht gefälscht werden.

Zertifikate können für verschiedene Zwecke ausgestellt werden. Zum Beispiel zur Webbenutzerauthentifizierung, zur Webserverauthentifizierung, für S/MIME (Secure/Multipurpose Internet Mail Extensions), IPsec (Internet Protocol Security), TLS (Transport Layer Security) und zur Codesignierung.

Ein Zertifikat enthält einen öffentlichen Schlüssel und bindet diesen an die Identität einer Person, eines Computers oder eines Diensts mit dem entsprechenden privaten Schlüssel. Öffentliche und private Schlüssel werden vom Client und vom Server zum Verschlüsseln von Daten vor deren Übertragung verwendet. Für Windows-basierte Benutzer, Computer und Dienste wird eine Vertrauensstellung mit einer Zertifizierungsstelle eingerichtet, wenn sich eine Kopie des Stammzertifikats im Informationsspeicher für vertrauenswürdige Stammzertifikate befindet und das Zertifikat einen gültigen Zertifizierungspfad enthält. Damit das Zertifikat gültig ist, darf es nicht gesperrt worden sein, und der Gültigkeitszeitraum darf nicht abgelaufen sein.

## Zertifikattypen

Es gibt drei wichtige Arten von digitalen Zertifikaten: selbstsignierte Zertifikate, Windows PKI-generierte Zertifikate und Zertifikate von Drittanbietern.

## Selbstsignierte Zertifikate

Bei der Installation von Exchange 2013 wird automatisch ein selbstsigniertes Zertifikat auf den Postfachservern konfiguriert. Ein selbstsigniertes Zertifikat wird von der Anwendung signiert, die es erstellt hat. Antragsteller und Name des Zertifikats stimmen überein. Der Aussteller und der Antragsteller sind im Zertifikat definiert. Das selbstsignierte Zertifikat dient zum Verschlüsseln der Kommunikation zwischen Clientzugriffs- und Postfachserver. Der Clientzugriffsserver vertraut dem selbstsignierten Zertifikat auf dem Postfachserver automatisch, sodass auf dem Postfachserver kein Drittanbieterzertifikat benötigt wird. Bei der Installation von Exchange 2013 wird auch ein selbstsigniertes Zertifikat auf dem Clientzugriffsserver erstellt. Dieses selbstsignierte Zertifikat erlaubt einigen Clientprotokollen die Verwendung von SSL für die Kommunikation. Exchange ActiveSync und Outlook Web App können eine SSL-Verbindung unter Verwendung eines selbstsignierten Zertifikats herstellen. Outlook Anywhere funktioniert nicht mit einem selbstsignierten Zertifikat auf dem Clientzugriffsserver. Selbstsignierte Zertifikate müssen manuell in den Informationsspeicher für vertrauenswürdige Stammzertifikate auf dem Clientcomputer oder auf dem mobilen Gerät kopiert werden. Wenn ein Client über SSL eine Verbindung zum Server herstellt und der Server ein selbstsigniertes Zertifikat anbietet, wird der Client aufgefordert zu überprüfen, ob das Zertifikat von einer vertrauenswürdigen Stelle ausgestellt wurde. Zwischen dem Client und dem Aussteller des Zertifikats muss eine ausdrückliche Vertrauensstellung bestehen. Wenn der Client die Vertrauensstellung bestätigt, kann die SSL-Kommunikation fortgesetzt werden.


> [!NOTE]
> Standardmäßig ist das auf Postfachservern installierte digitale Zertifikat ein selbstsigniertes Zertifikat. Sie müssen das selbstsignierte Zertifikat auf den Postfachservern in Ihrer Organisation nicht durch ein vertrauenswürdiges Drittanbieterzertifikat ersetzen. Der Clientzugriffsserver vertraut automatisch dem selbstsignierten Zertifikat auf dem Postfachserver, sodass auf dem Postfachserver keine andere Konfiguration für Zertifikate benötigt wird.



Kleine Organisationen entscheiden sich häufig gegen die Verwendung eines Drittanbieterzertifikats oder die Installation einer eigenen PKI zur Ausstellung eigener Zertifikate. Die Gründe hierfür lauten oft, dass sie die Kosten scheuen und/oder ihre Administratoren nicht über entsprechende Erfahrungen und Kenntnisse bei der Erstellung einer eigenen Zertifikathierarchie verfügen. Bei der Verwendung von selbstsignierten Zertifikaten sind die Kosten minimal, und die Einrichtung ist einfach. Das Erstellen einer Infrastruktur zur Lebenszyklusverwaltung, Erneuerung, Vertrauensverwaltung und Sperrung von Zertifikaten ist bei selbstsignierten Zertifikaten jedoch wesentlich schwieriger.

## Windows PKI-Zertifikate

Der zweite Zertifikattyp ist das Windows PKI-generierte Zertifikat. Bei einer PKI (Public Key-Infrastruktur) handelt es sich um ein System von digitalen Zertifikaten, Zertifizierungsstellen (Certification Authorities, CAs) und Registrierungsstellen (Registration Authorities, RAs), das zum Prüfen und Authentifizieren der Gültigkeit der an der elektronischen Transaktion beteiligten Parteien die Kryptografie mit öffentlichen Schlüsseln verwendet. Wenn Sie eine Public Key-Infrastruktur in einer Organisation implementieren, in der Active Directory verwendet wird, stellen Sie eine Infrastruktur für Lebenszyklusverwaltung, Erneuerung, Vertrauensverwaltung und Sperrung von Zertifikaten zur Verfügung. Bei der Bereitstellung von Servern und der Infrastruktur zum Erstellen und Verwalten von Windows PKI-generierten Zertifikaten entstehen jedoch zusätzliche Kosten.

Zur Bereitstellung einer Windows PKI sind die Zertifikatdienste erforderlich, die über die Option **Software** in der Systemsteuerung installiert werden können. Sie können die Zertifikatdienste auf jedem Server in der Domäne installieren.

Wenn Sie Zertifikate von einer mit der Domäne verbundenen Windows-Zertifizierungsstelle anfordern, können Sie über die Zertifizierungsstelle Zertifikate für Ihre eigenen Server oder Computer im Netzwerk anfordern oder signieren. Auf diese Weise können Sie eine PKI verwenden, die einem Zertifikatdrittanbieter ähnelt, jedoch weniger kostspielig ist. Diese PKI-Zertifikate können nicht wie andere Zertifikattypen öffentlich bereitgestellt werden. Wenn jedoch eine PKI-Zertifizierungsstelle das Zertifikat des Anforderers mithilfe des privaten Schlüssels signiert, wird der Anforderer überprüft. Der öffentliche Schlüssel dieser Zertifizierungsstelle ist Bestandteil des Zertifikats. Ein Server, in dessen Informationsspeicher für vertrauenswürdige Stammzertifikate sich dieses Zertifikat befindet, kann den öffentlichen Schlüssel zum Entschlüsseln des Anfordererzertifikats verwenden und den Anforderer authentifizieren.

Die Schritte zum Bereitstellen eines PKI-generierten Zertifikats gleichen denen zur Bereitstellung eines selbstsignierten Zertifikats. Sie müssen ebenfalls eine Kopie des vertrauenswürdigen Stammzertifikats aus der Public Key-Infrastruktur in den Informationsspeicher für vertrauenswürdige Stammzertifikate auf den Computern oder mobilen Geräten installieren, deren Verbindung mit Microsoft Exchange über SSL hergestellt werden soll.

Eine Windows PKI ermöglicht Organisationen, eigene Zertifikate zu veröffentlichen. Clients können Zertifikate von einer Windows PKI im internen Netzwerk anfordern und erhalten. Die Windows PKI kann Zertifikate erneuern oder sperren.

## Vertrauenswürdige Drittanbieterzertifikate

Bei Drittanbieter- oder kommerziellen Zertifikaten handelt es sich um Zertifikate, die von einer Drittanbieter- oder kommerziellen Zertifizierungsstelle erzeugt werden und die Sie anschließend zur Verwendung auf Ihren Netzwerkservern erwerben können. Bei selbstsignierten und PKI-basierten Zertifikaten besteht das Problem, dass das Zertifikat vom Clientcomputer oder mobilen Gerät nicht automatisch als vertrauenswürdig eingestuft wird. Sie müssen sicherstellen, dass das Zertifikat in den Informationsspeicher für vertrauenswürdige Stammzertifikate auf Clientcomputern und anderen Geräten importiert wird. Bei kommerziellen Zertifikaten oder Zertifikaten von Drittanbietern tritt dieses Problem nicht auf. Die meisten kommerziellen CA-Zertifikate werden bereits als vertrauenswürdig eingestuft, da sich das Zertifikat bereits im Informationsspeicher für vertrauenswürdige Stammzertifikate befindet. Da der Aussteller als vertrauenswürdig eingestuft wird, gilt dies auch für das Zertifikat. Die Verwendung von Drittanbieterzertifikaten vereinfacht die Bereitstellung erheblich.

Größere Organisationen oder Organisationen, die Zertifikate öffentlich bereitstellen müssen, sollten Drittanbieter- oder kommerzielle Zertifikate verwenden, auch wenn dies mit Kosten verbunden ist. Für kleine und mittelständische Organisationen stellen kommerzielle Zertifikate unter Umständen nicht die beste Lösung dar, und es sollten andere Zertifikatoptionen in Betracht gezogen werden.

Zurück zum Seitenanfang

## Auswählen eines Zertifikattyps

Bei der Auswahl des zu installierenden Zertifikattyps sind verschiedene Faktoren zu berücksichtigen. Ein Zertifikat ist nur gültig, wenn es signiert ist. Es kann selbstsigniert oder von einer Zertifizierungsstelle signiert sein. Für ein selbstsigniertes Zertifikat gelten bestimmte Einschränkungen. Beispielweise ist es nicht auf allen mobilen Geräte möglich, ein digitales Zertifikat im Informationsspeicher für vertrauenswürdige Stammzertifikate zu installieren. Ob Sie Zertifikate auf einem mobilen Gerät installieren können, hängt vom Hersteller des mobilen Geräts und vom Mobilfunkanbieter ab. Einige Hersteller und Mobilfunkanbieter deaktivieren den Zugriff auf den Informationsspeicher für vertrauenswürdige Stammzertifikate. In diesem Fall können Sie weder ein selbstsigniertes Zertifikat noch ein Zertifikat einer Windows PKI-Zertifizierungsstelle auf dem mobilen Gerät installieren.

## Exchange-Standardzertifikate

Exchange installiert standardmäßig ein selbstsigniertes Zertifikat sowohl auf dem Clientzugriffs- als auch auf dem Postfachserver, damit die gesamte Netzwerkkommunikation verschlüsselt wird. Zum Verschlüsseln der gesamten Netzwerkkommunikation ist es erforderlich, dass alle Exchange-Server über ein X.509-Zertifikat verfügen. Sie sollten dieses selbstsignierte Zertifikat auf dem Clientzugriffsserver durch ein Zertifikat ersetzen, dem Ihre Clients automatisch vertrauen.

"Selbstsigniert" bedeutet, dass ein Zertifikat durch den Exchange-Server erstellt und signiert wurde. Da das Zertifikat nicht durch eine vertrauenswürdige Zertifizierungsstelle erstellt und signiert wurde, wird das selbstsignierte Zertifikat nur von anderen Exchange-Servern, nicht jedoch von anderen Softwarekomponenten als vertrauenswürdig eingestuft. Das Standardzertifikat ist für alle Exchange-Dienste aktiviert. Der Name des alternativen Antragstellers im Zertifikat entspricht dem Namen des Exchange-Servers, auf dem das Zertifikat installiert ist. Darüber hinaus enthält das Zertifikat eine Liste von SANs, die sowohl den Servernamen als auch den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) des Servers umfasst.

Wenngleich andere Exchange-Server in Ihrer Exchange-Organisation diesem Zertifikat automatisch vertrauen, stufen Clients wie z. B. Webbrowser, Outlook-Clients, Mobiltelefone und andere E-Mail-Clients sowie externe E-Mail-Server das Zertifikat nicht automatisch als vertrauenswürdig ein. Erwägen Sie deshalb auf Ihren Exchange-Clientzugriffsservern das Austauschen dieses Zertifikats gegen ein vertrauenswürdiges Drittanbieterzertifikat. Wenn Sie über eine eigene Public Key-Infrastruktur verfügen und alle Ihre Clients dieser Entität vertrauen, können Sie auch Zertifikate verwenden, die Sie selbst ausgestellt haben.

## Zertifikatanforderungen nach Dienst

Zertifikate werden in Exchange für verschiedene Zwecke eingesetzt. Die meisten Kunden verwenden Zertifikate außerdem auf mehreren Exchange-Servern. Im Allgemeinen gilt die Regel, dass weniger Zertifikate einfacher zu verwalten sind.

## IIS

Die folgenden Exchange-Dienste verwenden auf einem Exchange-Clientzugriffsserver dasselbe Zertifikat:

  - Outlook Web App

  - Exchange-Verwaltungskonsole

  - Exchange-Webdienste

  - Exchange ActiveSync

  - Outlook Anywhere

  - AutoErmittlung

  - Outlook-Adressbuchverteilung

Da einer Website nur ein einziges Zertifikat zugeordnet werden kann und alle genannten Dienste standardmäßig über eine einzelne Website bereitgestellt werden, müssen alle Namen im Zertifikat aufgeführt werden (oder unter einen Platzhalternamen im Zertifikat fallen), die Clients für diese Dienste verwenden.

## POP/IMAP

Für POP oder IMAP verwendete Zertifikate können separat von dem Zertifikat angegeben werden, das für IIS verwendet wird. Um jedoch die Verwaltung zu vereinfachen, wird empfohlen, die POP- oder IMAP-Dienstnamen in Ihr IIS-Zertifikat aufzunehmen und ein einziges Zertifikat für sämtliche dieser Dienste zu verwenden.

## SMTP

Für jeden Empfangsconnector, den Sie konfigurieren, kann ein separates Zertifikat verwendet werden. Das Zertifikat muss den Namen des SMTP-Clients (oder anderer SMTP-Server) enthalten, der bzw. die zum Kontaktieren des Connectors verwendet werden. Zur einfacheren Zertifikatverwaltung können Sie alle Namen, für die TLS-Datenverkehr unterstützt werden muss, in einem einzelnen Zertifikat zusammenfassen.

## Digitale Zertifikate und Proxyfunktion

Als Proxyfunktion wird die Methode bezeichnet, mit der ein Server Clientverbindungen an einen anderen Server sendet. Bei Exchange 2013 erfolgt dies, wenn der Clientzugriffsserver eine eingehende Clientanforderung per Proxy an den Postfachserver sendet, die die aktive Kopie des Postfachs des Clients enthält.

Wenn Clientzugriffsserver Anforderungen über einen Proxy weiterleiten, wird SSL für die Verschlüsselung, nicht jedoch für die Authentifizierung verwendet. Das selbstsignierte Zertifikat auf dem Postfachserver verschlüsselt den Datenverkehr zwischen Clientzugriffs- und Postfachserver.

## Reverseproxys und Zertifikate

In vielen Exchange-Bereitstellungen werden Reverseproxys zum Veröffentlichen von Exchange-Diensten im Internet verwendet. Reverseproxys können so konfiguriert werden, dass sie die SSL-Verschlüsselung beenden, den Datenverkehr als Klartext auf dem Server untersuchen und dann einen neuen SSL-Verschlüsselungskanal vom Reverseproxyserver zu den Exchange-Servern öffnen, die sich hinter ihnen befinden. Dieser Vorgang wird als SSL-Bridging bezeichnet. Eine weitere Methode zum Konfigurieren der Reverseproxyserver besteht darin, die SSL-Verbindungen direkt an die Exchange-Server hinter den Reverseproxyservern weiterzuleiten. In beiden Bereitstellungsmodellen stellen die Clients im Internet über einen Hostnamen für den Exchange-Zugriff, z. B. mail.contoso.com, eine Verbindung zum Reverseproxyserver her. Dann verbindet sich der Reverseproxy über einen anderen Hostnamen, z. B. dem Computernamen des Exchange-Clientzugriffsservers, mit Exchange. Sie müssen den Computernamen nicht in das Zertifikat auf dem Exchange-Clientzugriffsserver aufnehmen, da die gängigen Reverseproxyserver in der Lage sind, den ursprünglichen Hostnamen, den der Client verwendet, dem internen Hostnamen des Exchange-Clientzugriffsservers zuzuordnen.

## SSL und Split-DNS

Split-DNS ist eine Technologie, die Ihnen das Konfigurieren unterschiedlicher IP-Adressen für denselben Hostnamen ermöglicht – abhängig davon, woher die ursprüngliche DNS-Anforderung stammt. Diese Technologie wird auch als Split-Horizon-DNS, Split-View-DNS oder Split-Brain-DNS bezeichnet. Mit Split-DNS können Sie die Anzahl von Hostnamen verringern, die für Exchange verwaltet werden. Dies wird erreicht, indem Sie Ihren Clients – unabhängig davon, ob sie sich über das Internet oder aus dem Intranet verbinden – ermöglichen, über denselben Hostnamen eine Verbindung mit Exchange herzustellen. Split-DNS macht es möglich, dass aus dem Intranet stammende Anforderungen eine andere IP-Adresse erhalten als Anforderungen, die aus dem Internet empfangen werden.

Split-DNS ist in einer kleinen Exchange-Bereitstellung üblicherweise nicht erforderlich, da Benutzer unabhängig davon, ob die Anforderung aus dem Intranet oder dem Internet stammt, auf denselben DNS-Endpunkt zugreifen. In größeren Bereitstellung jedoch führt diese Konfiguration zu einer Überlastung Ihrer ausgehenden Internetproxyserver und Ihrer Reverseproxyserver. In größeren Bereitstellungen sollte daher Split-DNS konfiguriert werden, damit beispielsweise externe Benutzer auf "mail.contoso.com" und interne Benutzer auf "internal.contoso.com" zugreifen. Die Verwendung von Split-DNS für diese Konfiguration stellt sicher, dass sich Ihre Benutzer keine unterschiedlichen Hostnamen für ihren jeweiligen Standort merken müssen.

## Windows PowerShell-Remotesitzungen

Kerberos-Authentifizierung und Kerberos-Verschlüsselung werden für den Zugriff auf Remote-PowerShell verwendet, sowohl von der Exchange-Verwaltungskonsole als auch von der Exchange-Verwaltungsshell. Daher müssen Sie Ihre SSL-Zertifikate nicht zur Verwendung mit Remote-Windows PowerShell konfigurieren.

Zurück zum Seitenanfang

## Bewährte Methoden für digitale Zertifikate

Wenngleich die Konfiguration der digitalen Zertifikate Ihrer Organisation basierend auf Ihren spezifischen Anforderungen variiert, sollen die nachfolgend aufgeführten bewährten Methoden Sie bei der Auswahl der richtigen Konfiguration für Ihre digitalen Zertifikate unterstützen.

## Bewährte Methode: Verwenden eines vertrauenswürdigen Drittanbieterzertifikats

Um zu verhindern, dass Clients Fehler zu nicht vertrauenswürdigen Zertifikaten erhalten, muss das von Ihrem Exchange-Server verwendete Zertifikat durch eine Stelle ausgegeben worden sein, die der Client als vertrauenswürdig einstuft. Wenngleich die meisten Clients so konfiguriert werden können, dass sie einem beliebigen Zertifikat oder Zertifikataussteller vertrauen, ist es einfacher, auf Ihrem Exchange-Server ein vertrauenswürdiges Drittanbieterzertifikat zu verwenden. Dies liegt daran, dass die meisten Clients bereits ihren Stammzertifikaten vertrauen. Es gibt verschiedene Drittanbieter-Zertifizierungsstellen, die speziell für Exchange konfigurierte Zertifikate anbieten. Sie können die Exchange-Verwaltungskonsole zum Generieren von Zertifikatanforderungen verwenden, die bei den meisten Zertifikatausstellern funktionieren.

## Auswählen einer Zertifizierungsstelle

Eine Zertifizierungsstelle ist ein Unternehmen, das Zertifikate ausstellt und deren Gültigkeit sicherstellt. Clientsoftware (beispielsweise Browser wie Microsoft Internet Explorer oder Betriebssysteme wie Windows oder Mac OS) verfügen über eine integrierte Liste vertrauenswürdiger Zertifizierungsstellen. Es ist im Allgemeinen möglich, dieser Liste Zertifizierungsstellen hinzuzufügen bzw. Zertifizierungsstellen aus der Liste zu entfernen, aber die Konfiguration ist häufig langwierig. Berücksichtigen Sie bei der Auswahl einer Zertifizierungsstelle für den Erwerb von Zertifikaten die folgenden Aspekte:

  - Stellen Sie sicher, dass die Clientsoftware (Betriebssysteme, Browser und Mobiltelefone), die eine Verbindung mit Ihren Exchange-Servern herstellen, die Zertifizierungsstelle als vertrauenswürdig einstufen.

  - Wählen Sie eine Zertifizierungsstelle, die "Unified Communications-Zertifikate" zur Verwendung mit dem Exchange-Server unterstützt.

  - Stellen Sie sicher, dass die Zertifizierungsstelle die Arten von Zertifikaten unterstützt, die Sie verwenden möchten. Ziehen Sie die Verwendung von SAN-Zertifikaten (Subject Alternative Name, alternativer Antragstellername) in Betracht. Nicht alle Zertifizierungsstellen unterstützen SAN-Zertifikate, und einige Zertifizierungsstellen unterstützen möglicherweise nicht die benötigte Anzahl von Hostnamen.

  - Stellen Sie sicher, dass die für die Zertifikate erworbene Lizenz es Ihnen ermöglicht, das Zertifikat für die Anzahl von Servern zu verwenden, die Sie einsetzen möchten. Bei einigen Zertifizierungsstellen darf ein Zertifikat nur auf einem Server verwendet werden.

  - Vergleichen Sie die Zertifikatpreise verschiedener Zertifizierungsstellen.

## Bewährte Methode: Verwenden von SAN-Zertifikaten

Je nachdem, wie Sie die Dienstnamen in Ihrer Exchange-Bereitstellung konfigurieren, erfordert Ihr Exchange-Server möglicherweise ein Zertifikat, das mehrere Domänennamen repräsentieren kann. Wenngleich ein Platzhalterzertifikat, z. B. für \*.contoso.com, dieses Problem lösen kann, haben viele Kunden Bedenken in Bezug auf die Sicherheitsrisiken eines solchen Zertifikats, das für eine beliebige Unterdomäne verwendet werden kann. Sicherer ist es, die erforderlichen Domänen als alternative Antragstellernamen (Subject Alternative Names, SANs) im Zertifikat aufzuführen. Beim Generieren von Zertifikatanforderungen in Exchange wird standardmäßig diese Methode gewählt.

## Bewährte Methode: Verwenden des Assistenten für Exchange-Zertifikate zum Anfordern von Zertifikaten

Es gibt zahlreiche Dienste in Exchange, die Zertifikate verwenden. Ein häufiger Fehler beim Anfordern von Zertifikaten besteht darin, bei der Anforderung nicht die richtigen Dienstnamen einzuschließen. Der Assistent zum Anfordern von Zertifikaten in der Exchange-Verwaltungskonsole unterstützt Sie dabei, die richtige Namensliste in die Zertifikatanforderung aufzunehmen. Der Assistent fragt ab, für welche Dienste das Zertifikat eingesetzt wird und erstellt basierend auf den ausgewählten Diensten die Namen, die in das Zertifikat eingefügt werden müssen. Führen Sie den Zertifikat-Assistenten aus, wenn Sie die ersten Exchange 2013-Server bereitgestellt und festgelegt haben, welche Hostnamen für die verschiedenen Dienste in Ihrer Bereitstellung verwendet werden sollen. Im Idealfall müssen Sie den Zertifikat-Assistenten nur einmal pro Active Directory-Standort mit einer Exchange-Bereitstellung ausführen.

Statt sich darüber Sorgen zu machen, dass ein Hostname in der SAN-Liste des erworbenen Zertifikats fehlt, können Sie eine Zertifizierungsstelle wählen, die innerhalb einer Kulanzzeit ohne Aufpreis ein Zertifikat zurücknimmt und dasselbe Zertifikat mit einigen zusätzlichen Hostnamen erneut ausstellt.

## Bewährte Methode: So wenige Hostnamen wie möglich

Zusätzlich dazu, so wenige Zertifikate wie möglich zu verwenden, sollten Sie auch die Anzahl der Hostnamen so gering wie möglich halten. So können Sie Geld sparen. Viele Zertifikatanbieter berechnen eine Gebühr basierend auf der Anzahl von Hostnamen in einem Zertifikat.

Um die Anzahl der erforderlichen Hostnamen und damit auch die Komplexität bei der Zertifikatverwaltung zu verringern, sollten Sie keine Hostnamen einzelner Server in die SANs Ihres Zertifikats einschließen.

Die Hostnamen, die Sie in Ihre Exchange-Zertifikate einschließen sollten, sind die Hostnamen, die von Clientanwendungen zur Verbindungsherstellung mit Exchange verwendet werden. In der nachfolgenden Liste werden typische Hostnamen aufgeführt, die für ein Unternehmen namens Contoso erforderlich wären:

  - **Mail.contoso.com**   Dieser Hostname deckt die meisten Verbindungen zu Exchange ab, einschließlich MicrosoftOutlook, Outlook Web App, Outlook Anywhere, Offlineadressbuch (OAB), Exchange-Webdienste, POP3, IMAP4, SMTP, Exchange-Systemsteuerung und ActiveSync.

  - **Autodiscover.contoso.com**   Dieser Hostname wird von Clients verwendet, die die AutoErmittlung unterstützen, einschließlich Microsoft Office Outlook 2007 und höheren Versionen, Exchange ActiveSync und Exchange-Webdiensteclients.

  - **Legacy.contoso.com**   Dieser Hostname ist in einem Koexistenzszenario mit Exchange 2007 und Exchange 2013 erforderlich. Wenn Sie über Clients verfügen, die entweder Postfächer von Exchange 2007 und Exchange 2013 verwenden, wird durch die Konfiguration eines entsprechenden Hostnamens verhindert, dass die Benutzer beim Upgrade eine zweite URL benötigen.

## Grundlegendes zu Platzhalterzertifikaten

Ein Platzhalterzertifikat ist zur Unterstützung einer Domäne und mehrerer Unterdomänen gedacht. Wenn Sie beispielsweise ein Platzhalterzertifikat für "\*.contoso.com" konfigurieren, kann dieses Zertifikat für "mail.contoso.com", "web.contoso.com" und "autodiscover.contoso.com" eingesetzt werden.

Zurück zum Seitenanfang


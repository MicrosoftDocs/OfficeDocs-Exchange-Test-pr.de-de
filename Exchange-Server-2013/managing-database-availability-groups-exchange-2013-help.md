---
title: 'Verwalten von Datenbankverfügbarkeitsgruppen: Exchange 2013 Help'
TOCTitle: Verwalten von Datenbankverfügbarkeitsgruppen
ms:assetid: 74be3f97-ec0f-4d2a-b5d8-7770cc489919
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298065(v=EXCHG.150)
ms:contentKeyID: 50475957
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten von Datenbankverfügbarkeitsgruppen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-10-04_

Eine Database Availability Group (DAG) ist eine Gruppe von bis zu 16 Microsoft Exchange Server 2013-Postfachservern, die eine automatische Wiederherstellung auf Datenbankebene nach einem Datenbank-, Server- oder Netzwerkfehler bieten. Für DAGs wird eine fortlaufende Replikation und ein Teil der Windows-Failoverclusteringtechnologien verwendet, um eine hohe Verfügbarkeit und Ausfallsicherheit für Standorte zu gewährleisten. Die Postfachserver in einer DAG überwachen sich gegenseitig auf Fehler. Wenn einer DAG ein Postfachserver hinzugefügt wird, ist dieser mit den anderen Servern in der DAG kompatibel, damit eine automatische Wiederherstellung auf Datenbankebene nach Datenbankausfällen bereitgestellt werden kann.

Wenn Sie eine DAG erstellen, ist diese zunächst leer. Wenn Sie der DAG den ersten Server hinzufügen, wird für die DAG automatisch ein Failovercluster erstellt. Darüber hinaus wird die Infrastruktur für die Überwachung der Server auf Netzwerk- oder Serverfehler initiiert. Der Failovercluster-Taktmechanismus und die Clusterdatenbank werden dann zum Verfolgen und Verwalten von Informationen zur DAG verwendet, die sich schnell ändern können, z. B. Datenbankeinbindungsstatus, Replikationsstatus und Standort der letzten Einbindung.

**Inhalt**

Creating DAGs

DAG membership

Configuring DAG properties

DAG networks

Configuring DAG members

Performing maintenance on DAG members

Shutting down DAG members

Installing updates on DAG members

## Erstellen von DAGs

Eine DAG kann mithilfe des Assistenten für neue DAGs in der Exchange-Verwaltungskonsole oder durch Ausführen des Cmdlets **New-DatabaseAvailabilityGroup** in der Exchange-Verwaltungsshell erstellt werden. Wenn Sie eine DAG erstellen, geben Sie einen Namen für die DAG, einen optionalen Zeugenserver und Einstellungen für das Zeugenverzeichnis an. Darüber hinaus können Sie der DAG eine oder mehrere IP-Adressen zuweisen, entweder durch Verwenden statischer IP-Adressen oder durch Zulassen der automatischen Zuweisung erforderlicher IP-Adressen zur DAG über DHCP (Dynamic Host Configuration Protocol). Sie können der DAG mit dem Parameter *DatabaseAvailabilityGroupIpAddresses* manuell IP-Adressen zuweisen. Wenn Sie diesen Parameter weglassen, versucht die DAG, mithilfe eines DHCP-Servers in Ihrem Netzwerk eine IP-Adresse zu erhalten.

Beim Erstellen einer DAG, die Postfachserver unter Windows Server 2012 R2 enthält, haben Sie auch die Möglichkeit, eine DAG ohne einen Cluster-Administratorzugriffspunkt zu erstellen. In dem Fall hat der Cluster kein Clusternamenobjekt (CNO) in Active Directory, und die Clusterkernressourcengruppe enthält weder eine Netzwerknamensressource noch eine IP-Adressenressource.

Genaue Anweisungen zum Erstellen einer DAG finden Sie unter [Erstellen einer Datenbankverfügbarkeitsgruppe](create-a-database-availability-group-exchange-2013-help.md).

Wenn Sie eine DAG erstellen, werden ein leeres Objekt für die DAG mit dem von Ihnen angegebenen Namen und die Objektklasse **msExchMDBAvailabilityGroup** in Active Directory erstellt.

DAGs nutzen einen Teil der Windows-Failoverclusteringtechnologien: Clustertakt, Clusternetzwerke und Clusterdatenbank (zum Speichern von Daten, die sich ändern oder schnell ändern können, beispielsweise Änderungen des Datenbankzustands von "Aktiv" zu "Passiv" oder umgekehrt oder von "Eingebunden" zu "Nicht eingebunden" und umgekehrt). Da DAGs sich auf das Windows-Failoverclustering stützen, können sie nur auf Exchange 2013-Postfachservern erstellt werden, auf denen eines der folgenden Betriebssysteme ausgeführt wird: Windows Server 2008 R2 Enterprise oder Datacenter, Windows Server 2012 Standard oder Datacenter oder Windows Server 2012 R2 Standard oder Datacenter.


> [!NOTE]
> Der erstellte und von der DAG verwendete Failovercluster muss für die DAG bestimmt sein. Der Cluster darf für keine andere Hochverfügbarkeitslösung oder zu einem anderen Zweck verwendet werden. Der Failovercluster darf z.&nbsp;B. nicht dazu verwendet werden, andere Anwendungen oder Dienste zu Clustern zusammenzufassen. Die Verwendung des Failoverclusters, der einer DAG zugrunde liegt, für einen anderen Zweck, wird nicht unterstützt.



## DAG-Zeugenserver und -Zeugenverzeichnis

Beim Erstellen einer DAG müssen Sie einen Namen für die DAG angeben, der maximal 15 Zeichen lang und innerhalb der Active Directory-Gesamtstruktur eindeutig ist. Darüber hinaus wird jede DAG mit einem Zeugenserver und einem Zeugenverzeichnis konfiguriert. Der Zeugenserver und sein Verzeichnis werden nur verwendet, wenn eine gerade Anzahl von Mitgliedern in der DAG vorliegt und auch dann nur zu Quorumzwecken. Sie müssen das Zeugenverzeichnis nicht im Voraus erstellen. Exchange erstellt und sichert das Verzeichnis automatisch für Sie auf dem Zeugenserver. Das Verzeichnis sollte ausschließlich für den DAG-Zeugenserver verwendet werden.

Der Zeugenserver muss folgende Anforderungen erfüllen:

  - Der Zeugenserver darf kein Mitglied der DAG sein.

  - Der Zeugenserver muss sich in derselben Active Directory-Gesamtstruktur wie die DAG befinden.

  - Der Zeugenserver muss eine unterstützte Version von Windows Server ausgeführt werden. Weitere Informationen finden Sie unter [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md).

  - Ein einzelner Server kann als Zeuge für mehrere DAGs fungieren. Für jede DAG ist jedoch ein eigenes Zeugenverzeichnis erforderlich.

Unabhängig von dem als Zeugenserver verwendeten Server müssen Sie, wenn die Windows-Firewall auf dem vorgesehenen Zeugenserver aktiviert ist, die Windows-Firewallausnahme für die Datei- und Druckerfreigabe aktivieren.


> [!IMPORTANT]
> Wenn der von Ihnen angegebene Zeugenserver kein Exchange 2013- oder Exchange 2010-Server ist, müssen Sie der lokalen Administratorgruppe auf dem Zeugenserver vor dem Erstellen der DAG die universelle Exchange-Sicherheitsgruppe "Vertrauenswürdiges Subsystem" hinzufügen. Diese Sicherheitsrechte sind erforderlich, um sicherzustellen, dass bei Bedarf mithilfe von Exchange ein Verzeichnis und eine Freigabe auf dem Zeugenserver erstellt werden kann.<BR>Der Zeugenserver verwendet SMB-Port 445.



Weder Zeugenserver noch Zeugenverzeichnis müssen fehlertolerant sein oder eine Form von Redundanz oder hoher Verfügbarkeit verwenden. Es besteht keine Notwendigkeit zur Verwendung eines Dateiclusterservers oder einer anderen Form von Ausfallsicherung für den Zeugenserver. Hierfür gibt es verschiedene Gründe. Bei größeren DAGs (z. B. mit sechs oder mehr Mitgliedern) können mehrere Fehler auftreten, bevor der Zeugenserver benötigt wird. Da eine DAG mit sechs Mitgliedern zwei Wählerfehler tolerieren kann, ohne dass das Quorum verloren geht, müssten drei Wähler ausfallen, bevor der Zeugenserver zur Aufrechterhaltung des Quorums benötigt wird. Wenn es einen Fehler gibt, der sich auf den aktuellen Zeugenserver auswirkt (wenn Sie beispielsweise den Zeugenserver wegen eines Hardwareausfalls verlieren), können Sie zudem mit dem Cmdlet [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) einen neuen Zeugenserver und ein neues Zeugenverzeichnis konfigurieren (vorausgesetzt, es besteht ein Quorum).


> [!NOTE]
> Sie können auch das Cmdlet <STRONG>Set-DatabaseAvailabilityGroup</STRONG> verwenden, um den Zeugenserver und das Zeugenverzeichnis am ursprünglichen Speicherort zu konfigurieren, wenn der Zeugenserver seinen Speicher verloren oder jemand das Zeugenverzeichnis oder gemeinsame Berechtigungen geändert hat.



## Überlegungen zur Platzierung von Zeugenservern

Die Platzierung eines Zeugenservers der DAG hängt von Ihren Geschäftsanforderungen und den für Ihre Organisation verfügbaren Optionen ab. Exchange 2013 bietet Unterstützung für neue DAG-Konfigurationsoptionen, die in früheren Versionen von Exchange nicht empfohlen werden oder nicht möglich sind. Diese Optionen beinhalten die Verwendung eines dritten Standorts wie ein drittes Rechenzentrum, eine Filiale oder ein virtuelles Microsoft Azure-Netzwerk.

In der folgenden Tabelle sind allgemeine Empfehlungen zur Platzierung von Zeugenservern für unterschiedliche Bereitstellungsszenarien aufgeführt.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Bereitstellungsszenario</th>
<th>Empfehlungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Einzelner DAG in einem einzelnen Rechenzentrum bereitgestellt</p></td>
<td><p>Platzieren Sie Zeugenserver im selben Rechenzentrum wie die DAG-Mitglieder.</p></td>
</tr>
<tr class="even">
<td><p>Einzelne DAG in zwei Rechenzentren bereitgestellt, keine weiteren Standorte verfügbar</p></td>
<td><p>Platzieren Sie Zeugenserver in einem virtuellen Microsoft Azure-Netzwerk, um das automatisierte Failover von Rechenzentren zu aktivieren.</p>
<p>Platzieren Sie Zeugenserver im primären Rechenzentrum.</p></td>
</tr>
<tr class="odd">
<td><p>Mehrere DAGs in einem einzelnen Rechenzentrum bereitgestellt</p></td>
<td><p>Platzieren Sie Zeugenserver im selben Rechenzentrum wie die DAG-Mitglieder. Weitere Optionen beinhalten Folgendes:</p>
<ul>
<li><p>Verwenden desselben Zeugenservers für mehrere DAGs</p></li>
<li><p>Verwenden eines DAG-Mitglieds als Zeugenserver für eine andere DAG</p></li>
</ul>
<p></p></td>
</tr>
<tr class="even">
<td><p>Mehrere DAGs in zwei Rechenzentren bereitgestellt</p></td>
<td><p>Platzieren Sie Zeugenserver in einem virtuellen Microsoft Azure-Netzwerk, um das automatisierte Failover von Rechenzentren zu aktivieren.</p>
<p>Platzieren Sie den Zeugenserver in dem Rechenzentrum, das für die einzelnen DAGs als primäres Rechenzentrum angesehen wird. Weitere Optionen beinhalten Folgendes:</p>
<ul>
<li><p>Verwenden desselben Zeugenservers für mehrere DAGs</p></li>
<li><p>Verwenden eines DAG-Mitglieds als Zeugenserver für eine andere DAG</p>
<p></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Einzelne oder mehrere DAGs in mehr als zwei Rechenzentren bereitgestellt</p></td>
<td><p>Bei dieser Konfiguration sollte sich der Zeugenserver in dem Rechenzentrum befinden, in dem die Mehrzahl der Quorumstimmen vorhanden sein soll.</p></td>
</tr>
</tbody>
</table>


Wenn eine DAG in zwei Rechenzentren bereitgestellt wurden, besteht eine neue Konfigurationsoption in Exchange 2013 darin, einen dritten Standort zum Hosten des Zeugenservers zu verwenden. Wenn Ihre Organisation über einen dritten Standort mit einer Netzwerkinfrastruktur verfügt, die von Netzwerkfehlern isoliert ist, die sich auf die beiden Rechenzentren auswirken, in denen Ihre DAG bereitgestellt ist, können Sie den Zeugenserver der DAG an diesem dritten Standort bereitstellen. Dabei können Sie Ihre DAG so konfigurieren, dass für Datenbanken im Falle eines Fehlers auf Rechenzentrumsebene automatisch ein Failover zum anderen Rechenzentrum vorgenommen wird. Wenn Ihre Organisation nur über zwei physische Standorte verfügt, können Sie ein virtuelles Microsoft Azure-Netzwerk als dritten Standort für die Platzierung Ihres Zeugenservers verwenden.

## Angeben eines Zeugenservers und Zeugenverzeichnisses bei der DAG-Erstellung

Beim Erstellen einer DAG müssen Sie einen Namen für die DAG angeben. Optional können Sie auch einen Zeugenserver und ein Zeugenverzeichnis angeben.

Beim Erstellen einer DAG sind die folgenden Kombinationen von Optionen und Verhalten verfügbar:

  - Sie können nur einen Namen für die DAG angeben und die Felder **Zeugenserver** und **Zeugenverzeichnis** leer lassen. In diesem Szenario sucht der Assistent auf dem lokalen Active Directory-Standort nach einem Clientzugriffsserver, auf dem die Postfachserverrolle nicht installiert ist, erstellt automatisch das Standardverzeichnis (%Systemlaufwerk%:\\DAGFileShareWitnesses\\\<*DAGFQDN*\>) und die Standardfreigabe ("\<*DAGFQDN*\>") auf diesem Server und verwendet den Clientzugriffsserver als Zeugenserver. Sie verfügen beispielsweise über einen Zeugenserver namens "CAS3", dessen Betriebssystem auf Laufwerk "C:" installiert wurde. Eine DAG namens "DAG1" in der Domäne "contoso.com" verwendet das Standardzeugenverzeichnis "C:\\DAGFileShareWitnesses\\DAG1.contoso.com", das als "\\\\CAS3\\DAG1.contoso.com" freigegeben wird.

  - Sie können einen Namen für die DAG, den Zeugenserver, den Sie verwenden möchten, sowie das Verzeichnis, das Sie erstellen und auf dem Zeugenserver freigeben möchten, angeben.

  - Sie können einen Namen für die DAG und den Zeugenserver angeben, den Sie verwenden möchten, und das Feld **Zeugenverzeichnis** leer lassen. In diesem Szenario erstellt der Assistent das Standardverzeichnis auf dem angegebenen Zeugenserver.

  - Sie können einen Namen für die DAG angeben, das Feld **Zeugenserver** leer lassen und das Verzeichnis angeben, das Sie erstellen und auf dem Zeugenserver freigeben möchten. In diesem Szenario sucht der Assistent nach einem Clientzugriffsserver, auf dem der Postfachserver nicht installiert ist, erstellt automatisch die angegebene DAG auf dem Server, gibt das Verzeichnis frei und verwendet den Clientzugriffsserver als Zeugenserver.

Eine neu erstellte DAG verwendet zunächst das Knotenmehrheits-Quorummodell. Wird der DAG der zweite Postfachserver hinzugefügt, wird das Quorum automatisch in ein Knoten- und Dateifreigabemehrheits-Quorummodell geändert. Kommt es zu dieser Änderung, beginnt der DAG-Cluster mit der Verwendung des Zeugenservers, um das Quorum aufrechtzuerhalten. Ist das Zeugenverzeichnis nicht vorhanden, wird es von Exchange automatisch erstellt und freigegeben, und die Freigabe wird mit den vollständigen Steuerungsberechtigungen für das CNO-Computerkonto für die DAG ausgestattet.


> [!NOTE]
> Die Verwendung einer Dateifreigabe, die zum Namespace eines verteilten Dateisystems gehört, wird nicht unterstützt.



Wenn die Windows-Firewall auf dem Zeugenserver aktiviert wird, bevor die DAG erstellt wurde, kann dies die Erstellung der DAG möglicherweise blockieren. Exchange verwendet die Windows Management Instrumentation (WMI), um das Verzeichnis und die Dateifreigabe auf dem Zeugenserver zu erstellen. Wenn die Windows-Firewall auf dem Zeugenserver aktiviert ist und für WMI keine Firewallausnahmen konfiguriert sind, schlägt das Cmdlet **New-DatabaseAvailabilityGroup** mit einem Fehler fehl. Wenn Sie einen Zeugenserver, aber kein Zeugenverzeichnis angeben, erhalten Sie die folgende Fehlermeldung.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Der Task konnte das Standardzeugenverzeichnis auf Server &lt;<em>Servername</em>&gt; nicht erstellen. Geben Sie manuell ein Zeugenverzeichnis an.</p></td>
</tr>
</tbody>
</table>


Wenn Sie einen Zeugenserver und ein Zeugenverzeichnis angeben, erhalten Sie die folgende Warnmeldung.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Kein Zugriff auf Dateifreigaben auf Zeugenserver '<em>Servername</em>'. Bis zur Behebung des Problems kann die DAG anfälliger für Fehler sein. Verwenden Sie das Cmdlet &quot;Set-DatabaseAvailabilityGroup&quot;, um den Vorgang zu wiederholen. Fehler: Der Netzwerkpfad wurde nicht gefunden.</p></td>
</tr>
</tbody>
</table>


Wenn die Windows-Firewall auf dem Zeugenserver aktiviert wird, nachdem die DAG erstellt wurde, aber bevor die Server hinzugefügt wurden, kann dies das Hinzufügen oder Entfernen von DAG-Mitgliedern blockieren. Wenn die Windows-Firewall auf dem Zeugenserver aktiviert ist und für WMI keine Firewallausnahmen konfiguriert sind, zeigt das Cmdlet **Add-DatabaseAvailabilityGroupServer** die folgende Warnmeldung an.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Fehler beim Erstellen des Dateifreigabe-Zeugenverzeichnisses 'C:\DAGFileShareWitnesses\DAG_FQDN' auf Zeugenserver <em>'Servername'</em>. Bis zur Behebung des Problems kann die DAG anfälliger für Fehler sein. Verwenden Sie das Cmdlet 'Set-DatabaseAvailabilityGroup', um den Vorgang zu wiederholen. Fehler: WMI-Ausnahme auf Server <em>'Servername'</em>: Der RPC-Server ist nicht verfügbar. (Ausnahme von HRESULT: 0x800706BA)</p></td>
</tr>
</tbody>
</table>


Führen Sie eine der folgenden Aktionen aus, um die vorangehenden Fehler und Warnungen zu beheben:

  - Erstellen Sie das Zeugenverzeichnis und die Freigabe auf dem Zeugenserver manuell, und weisen Sie dem Clusternamensobjekt für die DAG den Vollzugriff für das Verzeichnis und die Freigabe zu.

  - Aktivieren Sie die WMI-Ausnahme in der Windows-Firewall.

  - Deaktivieren Sie die Windows-Firewall.

Zurück zum Seitenanfang

## DAG-Mitgliedschaft

Nach dem Erstellen einer DAG können Sie Server hinzufügen oder daraus entfernen. Verwenden Sie dazu den Assistenten zum Verwalten einer DAG in der Exchange-Verwaltungskonsole oder die Cmdlets **Add-DatabaseAvailabilityGroupServer** oder **Remove-DatabaseAvailabilityGroupServer** in der Shell. Genaue Anweisungen zum Verwalten der DAG-Mitgliedschaft finden Sie unter [Verwalten der Mitgliedschaft in DAGs](manage-database-availability-group-membership-exchange-2013-help.md).


> [!NOTE]
> Für jeden Postfachserver, der Mitglied einer DAG ist, liegt ein Knoten im zugrunde liegenden Cluster vor, der von der DAG verwendet wird. Deshalb kann jeweils nur ein Postfachserver Mitglied einer DAG sein.



Wenn für den einer DAG hinzugefügten Postfachserver keine Failoverclusteringkomponente installiert ist, wird die Failoverclusteringfunktion mit der Methode installiert, die zum Hinzufügen des Servers verwendet wird (z. B. das Cmdlet **Add-DatabaseAvailabilityGroupServer** oder der Assistent zum Verwalten einer DAG).

Beim Hinzufügen des ersten Postfachservers zu einer DAG geschieht Folgendes:

  - Die Windows-Failoverclusteringkomponente wird installiert, wenn sie nicht bereits installiert ist.

  - Ein Failovercluster mit dem Namen der DAG wird erstellt. Dieser Failovercluster wird ausschließlich von der DAG verwendet, und der Cluster muss für die DAG bestimmt sein. Die Verwendung des Clusters für einen anderen Zweck wird nicht unterstützt.

  - Ein Clusternamensobjekt wird im Container des Standardcomputers erstellt.

  - Name und IP-Adresse der DAG werden als Datensatz "Host (A)" in DNS (Domain Name System) registriert.

  - Der Server wird dem DAG-Objekt in Active Directory hinzugefügt.

  - Die Clusterdatenbank wird anhand der Informationen in den eingebundenen Datenbanken auf dem hinzugefügten Server aktualisiert.

In einer großen oder mehrere Standorte umfassenden Umgebung, insbesondere mit DAGs, die sich über mehrere Active Directory-Standorte erstrecken, müssen Sie auf den Abschluss der Active Directory-Replikation des DAG-Objekts warten, das das erste DAG-Mitglied enthält. Wenn dieses Active Directory-Objekt nicht in der gesamten Umgebung repliziert wird, kann das Hinzufügen des zweiten Servers zum Erstellen eines neuen Clusters (und eines neuen Clusternetzwerkobjekts) für die DAG führen. Der Grund hierfür ist, dass das DAG-Objekt aus Sicht des zweiten hinzugefügten Mitglieds leer zu sein scheint. Dies führt dazu, dass das Cmdlet **Add-DatabaseAvailabilityGroupServer** einen Cluster und ein Clusternamensobjekt für die DAG erstellt, obwohl diese Objekte bereits vorhanden sind. Wenn Sie überprüfen möchten, ob das DAG-Objekt, das den ersten DAG-Server enthält, repliziert wurde, verwenden Sie das Cmdlet **Get-DatabaseAvailabilityGroup** auf dem zweiten Server. Dieser wurde hinzugefügt, um sicherzustellen, dass der erste von Ihnen hinzugefügte Server als Mitglied der DAG aufgelistet wird.

Beim Hinzufügen des zweiten sowie weiterer Server zur DAG geschieht Folgendes:

  - Der Server wird mit dem Windows-Failovercluster für die DAG verknüpft.

  - Das Quorum-Modell wird automatisch angepasst:
    
      - Für DAGs mit einer ungeraden Mitgliederzahl wird ein Knotenmehrheits-Quorummodell verwendet.
    
      - Für DAGs mit einer geraden Mitgliederzahl wird ein Knoten- und Dateifreigabemehrheits-Quorummodell verwendet.

  - Zeugenverzeichnis und -freigabe werden bei Bedarf automatisch von Exchange erstellt.

  - Der Server wird dem DAG-Objekt in Active Directory hinzugefügt.

  - Die Clusterdatenbank wird anhand von Informationen über eingebundene Datenbanken aktualisiert.


> [!NOTE]
> Die Änderung des Quorummodells sollte automatisch erfolgen. Wird das Quorummodell jedoch nicht automatisch in das richtige Modell geändert, können Sie das Cmdlet <STRONG>Set-DatabaseAvailabilityGroup</STRONG> nur mit dem Parameter <EM>Identity</EM> ausführen, um die Quorumeinstellungen für die DAG zu korrigieren.



## Provisorische Bereitstellung des Clusternamensobjekts für eine DAG

Das Clusternetzwerkobjekt (CNO) ist ein in Active Directory erstelltes Computerkonto und der Namensressource des Clusters zugeordnet. Die Namensressource des Clusters ist an das Clusternetzwerkobjekt gebunden, wobei es sich um ein Kerberos-fähiges Objekt handelt, das als Identität des Clusters dient und den Sicherheitskontext des Clusters bereitstellt. Die Formation des Clusters, der der DAG zugrunde liegt, und des Clusternetzwerkobjekts für diesen Cluster wird durchgeführt, wenn das erste Mitglied zur DAG hinzugefügt wird. Wenn der erste Server zur DAG hinzugefügt wird, kontaktiert Remote-Powershell den Microsoft Exchange-Replikationsdienst auf dem hinzuzufügenden Postfachserver. Der Microsoft Exchange-Replikationsdienst installiert die Failoverclusteringfunktion (sofern diese nicht bereits installiert ist) und beginnt mit der Clustererstellung. Der Microsoft Exchange-Replikationsdienst wird unter dem Sicherheitskontext LOKALES SYSTEM ausgeführt, unter dem auch die Clustererstellung durchgeführt wird.


> [!WARNING]
> Wenn Ihre DAG-Mitglieder Windows Server&nbsp;2012 ausführen, müssen Sie das Clusternetzwerkobjekt provisorisch bereitstellen, bevor Sie der DAG den ersten Server hinzufügen. Wenn Ihre DAG-Mitglieder Windows&nbsp;Server&nbsp;2012&nbsp;R2 ausführen und Sie eine DAG ohne Cluster-Administratorzugriffspunkt erstellen, wird kein CNO erstellt, und Sie müssen kein CNO für die DAG bereitstellen oder erstellen.



In Umgebungen, in denen die Erstellung von Computerkonten eingeschränkt ist oder in denen Computerkonten in einem anderen Container als dem Container der Standardcomputer erstellt werden, können Sie das Clusternetzwerkobjekt vorab bereitstellen und einrichten. Sie erstellen zuerst ein Computerkonto für das CNO, deaktivieren es, und führen dann einen der folgenden Schritte aus:

  - Zuweisen von Vollzugriff auf das Computerkonto an das Computerkonto des ersten Postfachservers, der der DAG hinzugefügt wird.

  - Zuweisen von Vollzugriff auf das Computerkonto an die universelle Sicherheitsgruppe "Exchange Trusted Subsystem".

Das Zuweisen des Vollzugriffs auf das Computerkonto zum Computerkonto des ersten Postfachservers, den Sie der DAG hinzufügen, stellt sicher, dass der Sicherheitskontext LOKALES SYSTEM in der Lage ist, das vorab bereitgestellte Computerkonto zu verwalten. Das Zuweisen des Vollzugriffs auf das Computerkonto an die universelle Sicherheitsgruppe "Exchange Trusted Subsystem" kann stattdessen verwendet werden, da die universelle Sicherheitsgruppe "Exchange Trusted Subsystem" die Computerkonten aller Exchange-Server in der Domäne enthält.

Genaue Anweisungen zum Vorabbereitstellen und Einrichten des Clusternetzwerkobjekts für eine DAG finden Sie unter [Provisorische Bereitstellung des Clusternamenobjekts für eine Database Availability Group](pre-stage-the-cluster-name-object-for-a-database-availability-group-exchange-2013-help.md).

## Entfernen von Servern aus einer DAG

Postfachserver können mithilfe des Assistenten zum Verwalten der Mitgliedschaft in einer DAG in der Exchange-Verwaltungskonsole oder mithilfe des Cmdlets **Remove-DatabaseAvailabilityGroupServer** in der Shell entfernt werden. Vor dem Entfernen eines Postfachservers aus einer DAG müssen zunächst alle replizierten Postfachdatenbanken vom Server entfernt werden. Der Versuch, einen Postfachserver mit replizierten Postfachdatenbanken aus einer DAG zu entfernen, schlägt fehl.

In manchen Szenarien müssen Sie einen Postfachserver aus einer DAG entfernen, bevor Sie bestimmte Vorgänge ausführen können. Diese Szenarien umfassen:

  - **Ausführen eines Serverwiederherstellungsvorgangs**   Wenn ein Postfachserver, der Mitglied einer DAG ist, verloren geht bzw. ausfällt, sich nicht wiederherstellen lässt und ersetzt werden muss, können Sie mit der Option **Setup /m:RecoverServer** einen Serverwiederherstellungsvorgang ausführen. Bevor Sie jedoch einen Wiederherstellungsvorgang ausführen können, müssen Sie zunächst den Server mithilfe des Cmdlets [Remove-DatabaseAvailabilityGroupServer](https://technet.microsoft.com/de-de/library/dd297956\(v=exchg.150\)) und des Parameters *ConfigurationOnly* aus der DAG entfernen.

  - **Entfernen der DAG**   In bestimmten Situationen müssen Sie eine DAG möglicherweise entfernen (z. B. beim Deaktivieren des Replikationsmodus eines Drittanbieters). Wenn Sie eine DAG entfernen müssen, müssen Sie zunächst alle Server aus der DAG entfernen. Beim Versuch, eine DAG mit Mitgliedern zu entfernen, tritt ein Fehler auf.

Zurück zum Seitenanfang

## Konfigurieren von DAG-Eigenschaften

Nachdem der DAG Server hinzugefügt wurden, können Sie mithilfe der Exchange-Verwaltungskonsole oder der Shell die Eigenschaften der DAG konfigurieren, einschließlich des von der DAG verwendeten Zeugenservers und -verzeichnisses sowie der IP-Adressen, die der DAG zugewiesen wurden.

Zu den konfigurierbaren Eigenschaften gehören folgende:

  - **Zeugenserver**   Der Name des Servers, auf dem die Dateifreigabe für den Dateifreigabenzeugen gehostet werden soll. Es empfiehlt sich, einen Clientzugriffsserver als Zeugenserver anzugeben. Auf diese Weise kann das System den Zeugenserver automatisch konfigurieren, sichern und bei Bedarf die Freigabe nutzen. Das System kann auch den Messagingadministrator über die Verfügbarkeit des Zeugenservers informieren.

  - **Zeugenverzeichnis**   Der Name eines Verzeichnisses, in dem Dateifreigabenzeugen-Daten gespeichert werden. Dieses Verzeichnis wird automatisch vom System auf dem angegebenen Zeugenserver erstellt.

  - **IP-Adressen der Datenbankverfügbarkeitsgruppe**   Der DAG muss mindestens eine IP-Adresse zugewiesen sein, es sei denn, die DAG-Mitglieder führen Windows Server 2012 R2 aus, und Sie erstellen eine DAG ohne IP-Adresse. Andernfalls können die IP-Adressen der DAG mithilfe manuell zugewiesener statischer IP-Adressen konfiguriert werden, oder sie können der DAG über einen DHCP-Server in Ihrer Organisation automatisch zugewiesen werden.

Mit der Shell können Sie DAG-Eigenschaften konfigurieren, die in der Exchange-Verwaltungskonsole nicht zur Verfügung stehen, z. B. DAG-IP-Adressen, Netzwerkverschlüssselungs- und -komprimierungseinstellungen, Netzwerkerkennung, den für die Replikation verwendeten TCP-Port und alternative Zeugenserver- und Zeugenverzeichniseinstellungen. Außerdem können Sie den Aktivierungsmodus des Datencenters (Datacenter Activation Coordination, DAC) aktivieren.

Genaue Anweisungen zum Konfigurieren der Eigenschaften von DAGs finden Sie unter [Konfigurieren der Eigenschaften einer DAG](configure-database-availability-group-properties-exchange-2013-help.md).

## DAG-Netzwerkverschlüsselung

DAGs unterstützen die Verwendung von Verschlüsselung durch die Nutzung der Verschlüsselungsfunktionen des Windows Server-Betriebssystems. DAGs verwenden die Kerberos-Authentifizierung zwischen Exchange-Servern. Die EncryptMessage- und DecryptMessage-APIs von Microsoft Kerberos Security Support Provider (SSP) verarbeiten die Verschlüsselung des DAG-Netzwerkdatenverkehrs. Microsoft Kerberos SSP unterstützt mehrere Verschlüsselungsalgorithmen. (Eine vollständige Liste finden Sie in Abschnitt 3.1.5.2 zum Thema "Verschlüsselungstypen" unter [Kerberos-Protokollerweiterungen](https://go.microsoft.com/fwlink/p/?linkid=179131)). Der Kerberos-Authentifizierungshandshake wählt das stärkste Verschlüsselungsprotokoll aus der Liste aus: Im Allgemeinen ist dies AES (Advanced Encryption Standard) mit 256 Bit, möglicherweise mit einem SHA-basierten Nachrichtenauthentifizierungscode (Hash-based Message Authentication Code, HMAC) zur Wahrung der Datenintegrität. Weitere Informationen finden Sie unter [HMAC](https://de.wikipedia.org/wiki/keyed-hash_message_authentication_code).

Die Netzwerkverschlüsselung ist eine Eigenschaft der DAG, nicht eines DAG-Netzwerks. Sie können die DAG-Netzwerkverschlüsselung mithilfe des Cmdlets **Set-DatabaseAvailabilityGroup** in der Shell konfigurieren. Die möglichen Verschlüsselungseinstellungen für die DAG-Netzwerkkommunikation sind in der folgenden Tabelle aufgelistet.

### Verschlüsselungseinstellungen für die DAG-Netzwerkkommunikation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Deaktiviert</p></td>
<td><p>Die Netzwerkverschlüsselung wird nicht verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Aktiviert</p></td>
<td><p>Die Netzwerkverschlüsselung wird in allen DAG-Netzwerken für Replikation und Seeding verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>InterSubnetOnly</p></td>
<td><p>Die Netzwerkverschlüsselung wird in DAG-Netzwerken bei der Replikation über verschiedene Subnetze verwendet. Dies ist die Standardeinstellung.</p></td>
</tr>
<tr class="even">
<td><p>SeedOnly</p></td>
<td><p>Die Netzwerkverschlüsselung wird in allen DAG-Netzwerken nur für Seeding verwendet.</p></td>
</tr>
</tbody>
</table>


## DAG-Netzwerkkomprimierung

DAGs unterstützen die integrierte Komprimierung. Ist die Komprimierung aktiviert, verwendet die DAG-Netzwerkkommunikation XPRESS, die Microsoft-Implementierung des LZ77-Algorithmus. Weitere Informationen finden Sie unter [An Explanation of the Deflate Algorithm](http://www.zlib.net/feldspar.html) und im Abschnitt 3.1.4.11.1.2.1 zum Thema "LZ77 Compression Algorithm" unter [Wire Format Protocol Specification](https://go.microsoft.com/fwlink/p/?linkid=179133). Es handelt sich um denselben Komprimierungstyp, der in zahlreichen Microsoft-Protokollen verwendet wird, insbesondere bei der MAPI-RPC-Komprimierung zwischen Outlook und Exchange.

Wie die Netzwerkverschlüsselung ist auch die Netzwerkkomprimierung eine Eigenschaft der DAG, nicht eines DAG-Netzwerks. Sie können die DAG-Netzwerkkomprimierung mithilfe des Cmdlets [Set-DatabaseAvailabilityGroup](https://technet.microsoft.com/de-de/library/dd297934\(v=exchg.150\)) in der Shell konfigurieren. Die möglichen Komprimierungseinstellungen für die DAG-Netzwerkkommunikation sind in der folgenden Tabelle aufgelistet.

### Komprimierungseinstellungen für die DAG-Netzwerkkommunikation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Deaktiviert</p></td>
<td><p>Die Netzwerkkomprimierung wird nicht verwendet.</p></td>
</tr>
<tr class="even">
<td><p>Aktiviert</p></td>
<td><p>Die Netzwerkkomprimierung wird in allen DAG-Netzwerken für Replikation und Seeding verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>InterSubnetOnly</p></td>
<td><p>Die Netzwerkkomprimierung wird in DAG-Netzwerken bei der Replikation über verschiedene Subnetze verwendet. Dies ist die Standardeinstellung.</p></td>
</tr>
<tr class="even">
<td><p>SeedOnly</p></td>
<td><p>Die Netzwerkkomprimierung wird in allen DAG-Netzwerken nur für Seeding verwendet.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## DAG-Netzwerke

Ein DAG-Netzwerk ist eine Sammlung von Subnetzen, die entweder für Replikationsdatenverkehr oder MAPI-Datenverkehr verwendet werden. Jedes DAG-Netzwerk enthält maximal ein MAPI-Netzwerk und null oder mehr Replikationsnetzwerke.

## Konfigurationen mit einem Netzwerkadapter

In Konfigurationen mit einem einzelnen Netzwerkadapter wird dasselbe Netzwerk sowohl für den MAPI- als auch für den Replikationsdatenverkehr verwendet. Zur Verringerung der Komplexität wird die Konfiguration mit einem einzelnen Netzwerkadapter für Exchange-Server empfohlen. Daher kann sowohl der MAPI- als auch der Replikationsdatenverkehr im gleichen Netzwerk enthalten sein.

## Konfigurationen mit zwei Netzwerkadaptern

Normalerweise müssen Sie nur dann zwei Netzwerkadapter verwenden, wenn der erhöhte Netzwerkdatenverkehr einen einzelnen Netzwerkadapter sättigen kann.

In Konfigurationen mit zwei Netzwerkadaptern ist ein Netzwerk im Allgemeinen für Replikationsdatenverkehr bestimmt, während das andere Netzwerk primär für MAPI-Datenverkehr verwendet wird. Sie können auch jedem DAG-Mitglied Netzwerkadapter hinzufügen und weitere DAG-Netzwerke als Replikationsnetzwerke konfigurieren.


> [!NOTE]
> Bei der Verwendung mehrerer Replikationsnetzwerke gibt es keine Möglichkeit, eine Priorität für die Netzwerkverwendung festzulegen. wählt ein Replikationsnetzwerk nach dem Zufallsprinzip aus der Gruppe der für den Protokollversand verfügbaren Replikationsnetzwerke aus.



In Exchange 2010 war in vielen Szenarien eine manuelle Konfiguration der DAG-Netzwerke erforderlich. In Exchange 2013 werden DAG-Netzwerke standardmäßig automatisch vom System konfiguriert. Bevor Sie DAG-Netzwerke erstellen oder ändern können, müssen Sie zunächst die manuelle DAG-Netzwerksteuerung aktivieren, indem Sie folgenden Befehl ausführen:

    Set-DatabaseAvailabilityGroup <DAGName> -ManualDagNetworkConfiguration $true

Nachdem Sie die manuelle DAG-Netzwerkkonfiguration aktiviert haben, können Sie das Cmdlet **New-DatabaseAvailabilityGroupNetwork** in der Shell verwenden, um ein DAG-Netzwerk zu erstellen. Genaue Anweisungen zum Erstellen eines Netzwerks mit DAGs finden Sie unter [Erstellen eines DAG-Netzwerks](create-a-database-availability-group-network-exchange-2013-help.md).

Mit dem Cmdlet **Set-DatabaseAvailabilityGroupNetwork** in der Shell können Sie DAG-Netzwerkeigenschaften konfigurieren. Genaue Anweisungen zum Konfigurieren der Eigenschaften von DAG-Netzwerken finden Sie unter [Konfigurieren der Eigenschaften von DAG-Netzwerken](configure-database-availability-group-network-properties-exchange-2013-help.md). In jedem DAG-Netzwerk müssen erforderliche und optionale Parameter konfiguriert werden:

  - **Netzwerkname**   Ein bis zu 128 Zeichen langer, eindeutiger Name für das DAG-Netzwerk.

  - **Netzwerkbeschreibung**   Eine bis zu 256 Zeichen lange Beschreibung für das DAG-Netzwerk.

  - **Netzwerksubnetze**   Ein oder mehrere Subnetze, die im Format "*IP-Adresse/Bitmaske*" eingegeben werden (Beispiel: 192.168.1.0/24 für IPv4-Subnetze; 2001:DB8:0:C000::/64 für IPv6-Subnetze).

  - **Replikation aktivieren**   Aktivieren Sie in der Exchange-Verwaltungskonsole das Kontrollkästchen, um das DAG-Netzwerk für Replikationsverkehr zu reservieren und MAPI-Verkehr zu blockieren. Deaktivieren Sie das Kontrollkästchen, um zu verhindern, dass die Replikation das DAG-Netzwerk verwendet, und um den MAPI-Verkehr zu aktivieren. Verwenden Sie in der Shell den Parameter *ReplicationEnabled* im Cmdlet [Set-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd298008\(v=exchg.150\)), um die Replikation zu aktivieren bzw. zu deaktivieren.


> [!NOTE]
> Das Deaktivieren der Replikation im MAPI-Netzwerk gewährleistet nicht, dass das MAPI-Netzwerk vom System nicht für die Replikation verwendet wird. Wenn alle konfigurierten Replikationsnetzwerke offline, ausgefallen oder anderweitig nicht verfügbar sind und nur ein MAPI-Netzwerk übrig bleibt (das nicht für die Replikation aktiviert ist), wird dieses Netzwerk vom System für die Replikation verwendet.



Die vom System erstellten anfänglichen DAG-Netzwerke (z. B. "MapiDagNetwork" und "ReplicationDagNetwork01") basieren auf den Subnetzen, die vom Clusterdienst aufgezählt wurden. Jedes DAG-Mitglied muss über dieselbe Anzahl von Netzwerkadaptern verfügen und jeder Netzwerkadapter muss eine IPv4-Adresse (und optional auch eine IPv6-Adresse) in einem eindeutigen Subnetz besitzen. Mehrere DAG-Mitglieder können IPv4-Adressen im gleichen Subnetz besitzen, aber jedes Paar aus Netzwerkadapter und IP-Adresse in einem bestimmten DAG-Mitglied muss sich in einem eindeutigen Subnetz befinden. Außerdem sollte nur der für das MAPI-Netzwerk verwendete Adapter mit einem Standardgateway konfiguriert werden. Replikationsnetzwerke sollten nicht mit einem Standardgateway konfiguriert werden.

Stellen Sie sich z. B. DAG1 vor, eine zwei Mitglieder umfassende DAG, in der jedes Mitglied zwei Netzwerkadapter besitzt (einer für das MAPI-Netzwerk und der andere für das Replikationsnetzwerk). In der nachfolgenden Tabelle sind Beispieleinstellungen für die IP-Adresskonfiguration enthalten.

### Beispieleinstellungen für den Netzwerkadapter

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Servernetzwerkadapter</th>
<th>IP-Adresse/Subnetzmaske</th>
<th>Standardgateway</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EX1-MAPI</p></td>
<td><p>192.168.1.15/24</p></td>
<td><p>192.168.1.1</p></td>
</tr>
<tr class="even">
<td><p>EX1-Replikation</p></td>
<td><p>10.0.0.15/24</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>EX2-MAPI</p></td>
<td><p>192.168.1.16</p></td>
<td><p>192.168.1.1</p></td>
</tr>
<tr class="even">
<td><p>EX2-Replikation</p></td>
<td><p>10.0.0.16</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


In der folgenden Konfiguration werden zwei Subnetze in der DAG konfiguriert: 192.168.1.0 und 10.0.0.0. Beim Hinzufügen von EX1 und EX2 zur DAG werden zwei Subnetze aufgezählt und zwei DAG-Netzwerke erstellt: MapiDagNetwork (192.168.1.0) und ReplicationDagNetwork01 (10.0.0.0). Diese Netzwerke werden, wie in der folgenden Tabelle gezeigt, konfiguriert.

### Aufgezählte DAG-Netzwerkeinstellungen für eine DAG mit einzelnem Subnetz

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Subnetze</th>
<th>Schnittstellen</th>
<th>MAPI-Zugriff aktiviert</th>
<th>Replikation aktiviert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MapiDagNetwork</p></td>
<td><p>192.168.1.0/24</p></td>
<td><p>EX1 (192.168.1.15)</p>
<p>EX2 (192.168.1.16)</p></td>
<td><p>Wahr</p></td>
<td><p>Wahr</p></td>
</tr>
<tr class="even">
<td><p>ReplicationDagNetwork01</p></td>
<td><p>10.0.0.0/24</p></td>
<td><p>EX1 (10.0.0.15)</p>
<p>EX2 (10.0.0.16)</p></td>
<td><p>False</p></td>
<td><p>Wahr</p></td>
</tr>
</tbody>
</table>


Deaktivieren Sie die Replikation für MapiDagNetwork, indem Sie den folgenden Befehl ausführen, um die Konfiguration von ReplicationDagNetwork01 als dediziertes Replikationsnetzwerk abzuschließen.

    Set-DatabaseAvailabilityGroupNetwork -Identity DAG1\MapiDagNetwork -ReplicationEnabled:$false

Nachdem die Replikation für MapiDagNetwork deaktiviert wurde, verwendet der Microsoft Exchange-Replikationsdienst ReplicationDagNetwork01 zur fortlaufenden Replikation. Wenn in ReplicationDagNetwork01 ein Fehler auftritt, verwendet der Microsoft Exchange-Replikationsdienst wieder MapiDagNetwork zur fortlaufenden Replikation. Das System geht bewusst auf diese Weise vor, um die hohe Verfügbarkeit zu erhalten.

## DAG-Netzwerke und Bereitstellungen mit mehreren Subnetzen

Im vorherigen Beispiel wird die DAG als DAG mit einzelnem Subnetz betrachtet, obwohl zwei unterschiedliche Subnetze verwendet werden (192.168.1.0 und 10.0.0.0), da jedes Mitglied dasselbe Subnetz verwendet, um das MAPI-Netzwerk zu bilden. Wenn die DAG-Mitglieder verschiedene Subnetze für das MAPI-Netzwerk verwenden, wird die DAG als *DAG mit mehreren Subnetzen* bezeichnet. In einer DAG mit mehreren Subnetzen werden automatisch jedem DAG-Netzwerk die richtigen Subnetze zugeordnet.

Stellen Sie sich z. B. DAG2 vor, eine zwei Mitglieder umfassende DAG, in der jedes Mitglied zwei Netzwerkadapter besitzt (einer für das MAPI-Netzwerk und der andere für das Replikationsnetzwerk), und jedes DAG-Mitglied befindet sich an einem separaten Active Directory-Standort, während das jeweiige MAPI-Netzwerk in einem anderen Subnetz enthalten ist. In der nachfolgenden Tabelle sind Beispieleinstellungen für die IP-Adresskonfiguration enthalten.

### Beispieleinstellungen für einen Netzwerkadapter für eine DAG mit mehreren Subnetzen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Servernetzwerkadapter</th>
<th>IP-Adresse/Subnetzmaske</th>
<th>Standardgateway</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EX1-MAPI</p></td>
<td><p>192.168.0.15/24</p></td>
<td><p>192.168.0.1</p></td>
</tr>
<tr class="even">
<td><p>EX1-Replikation</p></td>
<td><p>10.0.0.15/24</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>EX2-MAPI</p></td>
<td><p>192.168.1.15</p></td>
<td><p>192.168.1.1</p></td>
</tr>
<tr class="even">
<td><p>EX2-Replikation</p></td>
<td><p>10.0.1.15</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


In der folgenden Konfiguration werden vier Subnetze in der DAG konfiguriert: 192.168.0.0, 192.168.1.0, 10.0.0.0 und 10.0.1.0. Beim Hinzufügen von EX1 und EX2 zur DAG werden vier Subnetze aufgezählt, jedoch nur zwei DAG-Netzwerke erstellt: MapiDagNetwork (192.168.0.0, 192.168.1.0) und ReplicationDagNetwork01 (10.0.0.0, 10.0.1.0). Diese Netzwerke werden, wie in der folgenden Tabelle gezeigt, konfiguriert.

### Aufgezählte DAG-Netzwerkeinstellungen für eine DAG mit mehreren Subnetzen

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Subnetze</th>
<th>Schnittstellen</th>
<th>MAPI-Zugriff aktiviert</th>
<th>Replikation aktiviert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MapiDagNetwork</p></td>
<td><p>192.168.0.0/24</p>
<p>192.168.1.0/24</p></td>
<td><p>EX1 (192.168.0.15)</p>
<p>EX2 (192.168.1.15)</p></td>
<td><p>Wahr</p></td>
<td><p>Wahr</p></td>
</tr>
<tr class="even">
<td><p>ReplicationDagNetwork01</p></td>
<td><p>10.0.0.0/24</p>
<p>10.0.1.0/24</p></td>
<td><p>EX1 (10.0.0.15)</p>
<p>EX2 (10.0.1.15)</p></td>
<td><p>False</p></td>
<td><p>Wahr</p></td>
</tr>
</tbody>
</table>


## DAG-Netzwerke und iSCSI-Netzwerke

Standardmäßig führen DAGs die Ermittlung aller Netzwerke durch, die erkannt und für die Verwendung durch den zugrunde liegenden Cluster konfiguriert wurden. Dazu gehören alle iSCSI-Netzwerke (Internet SCSI), die sich als iSCSI-Speicher für ein oder mehrere DAG-Mitglieder in Verwendung befinden. Es wird empfohlen, dass iSCSI-Speicher dedizierte Netzwerke und Netzwerkadapter verwenden. Diese Netzwerke sollten nicht durch die DAG oder deren Cluster verwaltet oder als DAG-Netzwerke (MAPI oder Replikation) verwendet werden. Stattdessen sollten diese Netzwerke manuell für die Verwendung durch die DAG deaktiviert werden, damit sie für iSCSI-Speicherverkehr reserviert werden können. Damit iSCSI-Netzwerke nicht als DAG-Netzwerke erkannt und verwendet werden, konfigurieren Sie die DAG so, dass alle aktuell erkannten iSCSI-Netzwerke ignoriert werden. Verwenden Sie dazu das Cmdlet [Set-DatabaseAvailabilityGroupNetwork](https://technet.microsoft.com/de-de/library/dd298008\(v=exchg.150\)), wie in diesem Beispiel gezeigt:

    Set-DatabaseAvailabilityGroupNetwork -Identity DAG2\DAGNetwork02 -ReplicationEnabled:$false -IgnoreNetwork:$true

Dieser Befehl deaktiviert auch die Verwendung des Netzwerks durch den Cluster. Nach Ausführung des oben stehenden Befehls werden die iSCSI-Netzwerke zwar weiterhin als DAG-Netzwerke angezeigt, jedoch nicht für MAPI- oder Replikationsdatenverkehr verwendet.

Zurück zum Seitenanfang

## Konfigurieren von DAG-Mitgliedern

Postfachserver, die Mitglieder einer DAG sind, weisen einige für die hohe Verfügbarkeit spezifische Eigenschaften auf, die gemäß den Beschreibungen in den folgenden Abschnitten konfiguriert werden sollten:

  - Automatic database mount dial

  - Database copy automatic activation policy

  - Maximum active databases

## Automatische Datenbank-Einbindungswahl

Der Parameter *AutoDatabaseMountDial* gibt das Verhalten für das automatische Einbinden von Datenbanken nach einem Datenbankfailover an. Mithilfe des Cmdlets [Set-MailboxServer](https://technet.microsoft.com/de-de/library/aa998651\(v=exchg.150\)) können Sie den Parameter *AutoDatabaseMountDial* mit den folgenden Werten konfigurieren:

  - `BestAvailability`   Wenn dieser Wert angegeben wird, wird die Datenbank sofort nach einem Failover automatisch bereitgestellt, wenn die Länge der Kopiewarteschlange kleiner oder gleich 12 ist. Die Länge der Kopiewarteschlange entspricht der Anzahl von Protokollen, die von der passiven Kopie als zu replizieren erkannt werden. Wenn die Länge der Kopiewarteschlange größer als 12 ist, wird die Datenbank nicht automatisch bereitgestellt. Wenn die Länge der Kopiewarteschlange kleiner oder gleich 12 ist, versucht Exchange die verbleibenden Protokolle auf die passive Kopie zu replizieren und stellt die Datenbanken bereit.

  - `GoodAvailability`   Wenn dieser Wert angegeben wird, wird die Datenbank sofort nach einem Failover automatisch bereitgestellt, wenn die Länge der Kopiewarteschlange kleiner oder gleich sechs ist. Die Länge der Kopiewarteschlange entspricht der Anzahl von Protokollen, die von der passiven Kopie als zu replizieren erkannt werden. Wenn die Länge der Kopiewarteschlange größer als sechs ist, wird die Datenbank nicht automatisch bereitgestellt. Wenn die Länge der Kopiewarteschlange kleiner oder gleich sechs ist, versucht Exchange die verbleibenden Protokolle auf die passive Kopie zu replizieren und stellt die Datenbanken bereit.

  - `Lossless`   Wenn dieser Wert angegeben wird, werden die Datenbanken erst dann automatisch bereitgestellt, nachdem alle Protokolle, die auf der aktiven Kopie generiert wurden, auf die passive Kopie kopiert wurden. Diese Einstellung führt auch dazu, dass der Auswahlalgorithmus für den optimalen Kopiervorgang von Active Manager die potenziellen Kandidaten für die Aktivierung auf Grundlage des Aktivierungseinstellungswerts und nicht der Länge der Kopierwarteschlange sortiert wird.

Der Standardwert ist `GoodAvailability`. Wenn `BestAvailability` oder `GoodAvailability` angegeben wird und nicht alle Protokolle von der aktiven Kopie zur aktivierten passiven Kopie kopiert werden können, kann es zum Verlust von Postfachdaten kommen. Die Funktion "Sicherheitsnetz" (die standardmäßig aktiviert ist) unterstützt Sie aber beim Schutz vor den meisten Datenverlusten, indem Nachrichten, die sich in der Sicherheitsnetz-Warteschlange befinden, erneut übermittelt werden.

## Beispiel: Konfigurieren der automatischen Datenbank-Einbindungswahl

Im folgenden Beispiel wird ein Postfachserver mit einer *AutoDatabaseMountDial*-Einstellung von `GoodAvailability` konfiguriert.

    Set-MailboxServer -Identity EX1 -AutoDatabaseMountDial GoodAvailability

## Automatische Aktivierungsrichtlinie für die Datenbankkopie

Der Parameter *DatabaseCopyAutoActivationPolicy* gibt den Typ der automatischen Aktivierung an, der für Postfachdatenbankkopien auf ausgewählten Postfachservern verfügbar ist. Mithilfe des Cmdlets [Set-MailboxServer](https://technet.microsoft.com/de-de/library/aa998651\(v=exchg.150\)) können Sie den Parameter *DatabaseCopyAutoActivationPolicy* mit den folgenden Werten konfigurieren:

  - `Blocked`   Wenn Sie diesen Wert angeben, können Datenbanken auf den ausgewählten Postfachservern nicht automatisch aktiviert werden.

  - `IntrasiteOnly`   Wenn Sie diesen Wert angeben, kann die Datenbankkopie auf Servern am gleichen Active Directory-Standort aktiviert werden. Dadurch wird ein Failover oder eine Aktivierung zwischen Standorten vermieden. Diese Eigenschaft gilt für eingehende Postfachdatenbankkopien (z. B. für eine passive Kopie, die von einer aktiven Kopie erstellt wird). Datenbanken können auf diesem Postfachserver nicht für Datenbankkopien aktiviert werden, die an einem anderen Active Directory-Standort aktiv sind.

  - `Unrestricted`   Wenn Sie diesen Wert angeben, gelten keine besonderen Einschränkungen für die Aktivierung von Postfachdatenbankkopien auf den ausgewählten Postfachservern.

## Beispiel: Konfigurieren der automatischen Aktivierungsrichtlinie für die Datenbankkopie

Im folgenden Beispiel wird ein Postfachserver mit einer *DatabaseCopyAutoActivationPolicy*-Einstellung von `Blocked` konfiguriert.

    Set-MailboxServer -Identity EX1 -DatabaseCopyAutoActivationPolicy Blocked

## Maximale Anzahl von aktiven Datenbanken

Der Parameter *MaximumActiveDatabases* (der auch mit dem Cmdlet [Set-MailboxServer](https://technet.microsoft.com/de-de/library/aa998651\(v=exchg.150\)) verwendet wird) gibt die Anzahl von Datenbanken an, die auf einem Postfachserver eingebunden werden können. Sie können Postfachserver derart konfigurieren, dass sie Ihren Bereitstellungsanforderungen entsprechen, indem Sie sicherstellen, dass ein einzelner Postfachserver nicht überlastet wird.

Der Parameter *MaximumActiveDatabases* wird mit einem ganzzahligen Wert konfiguriert. Wenn die maximale Anzahl erreicht ist, werden die Datenbankkopien auf dem Server bei einem Failover oder Switchover nicht aktiviert. Sind die Kopien auf einem Server bereits aktiv, lässt der Server die Einbindung der Datenbanken nicht zu.

## Beispiel: Konfigurieren der maximalen Anzahl von aktiven Datenbanken

Im folgenden Beispiel wird ein Postfachserver für die Unterstützung von maximal 20 aktiven Datenbanken konfiguriert.

    Set-MailboxServer -Identity EX1 -MaximumActiveDatabases 20

Zurück zum Seitenanfang

## Ausführen des Wartungsprozesses auf DAG-Mitgliedern

Bevor Sie eine Software- oder Hardwarewartung für ein DAG-Mitglied ausführen, müssen Sie das DAG-Mitglied zunächst in den Wartungsmodus versetzen. Dies beinhaltet das Verschieben aller aktiven Datenbanken vom Server und das Verhindern, dass aktive Datenbanken auf den Server verschoben werden. Es stellt außerdem sicher, dass alle wichtigen DAG-Unterstützungsfunktionen, die sich möglicherweise auf dem Server befinden (z. B. die PAM-Rolle), auf einen anderen Server verschoben und daran gehindert werden, wieder auf diesen Server zurück verschoben zu werden. Sie sollten insbesondere die folgenden Aufgaben ausführen:

1.  Führen Sie `Set-ServerComponentState <ServerName> -Component HubTransport -State Draining -Requester Maintenance` aus, um mit dem Ausgleichen der Transportwarteschlangen zu beginnen.

2.  Führen Sie `Restart-Service MSExchangeTransport` aus, um mit dem Ausgleichen der Transportwarteschlangen zu beginnen.

3.  Führen Sie `Set-ServerComponentState <ServerName> -Component UMCallRouter -State Draining -Requester Maintenance` aus, um mit dem Ausgleichen aller Unified Messaging-Anrufe zu beginnen.

4.  Führen Sie `Redirect-Message -Server <ServerName> -Target <MailboxServerFQDN>` aus, um Nachrichten, für die die Übermittlung in den lokalen Warteschlangen noch aussteht, an den durch den Target-Parameter angegebenen Postfachserver umzuleiten.

5.  Führen Sie `Suspend-ClusterNode <ServerName>` aus, wenn Sie den Clusterknoten anhalten möchten, um zu verhindern, dass der Knoten der PAM ist oder wird.

6.  Führen Sie `Set-MailboxServer <ServerName> -DatabaseCopyActivationDisabledAndMoveNow $True` aus, um alle derzeit auf dem DAG-Mitglied gehosteten aktiven Datenbanken auf andere DAG-Mitglieder zu verschieben.

7.  Führen Sie `Set-MailboxServer <ServerName> -DatabaseCopyAutoActivationPolicy Blocked` aus, um zu verhindern, dass der Server aktive Datenbankkopien hostet.

8.  Führen Sie `Set-ServerComponentState <ServerName> -Component ServerWideOffline -State Inactive -Requester Maintenance` aus, um den Server in den Wartungsmodus zu versetzen.

Führen Sie die folgenden Aufgaben aus, um zu überprüfen, ob ein Server zur Wartung bereit ist:

1.  Führen Sie `Get-ServerComponentState <ServerName> | ft Component,State -Autosize` aus, um zu überprüfen, ob der Server in den Wartungsmodus versetzt wurde.

2.  Führen Sie `Get-MailboxServer <ServerName> | ft DatabaseCopy* -Autosize` aus, um zu überprüfen, ob der Server keine aktiven Datenbankkopien hostet.

3.  Führen Sie `Get-ClusterNode <ServerName> | fl` aus, um zu überprüfen, ob der Knoten angehalten wurde.

4.  Führen Sie `Get-Queue` aus, um zu überprüfen, ob für alle Transportwarteschlangen ein Ausgleich vorgenommen wurde.

Nachdem die Wartung abgeschlossen und das DAG-Mitglied bereit ist, den Dienst wieder aufzunehmen, können Sie das DAG-Mitglied aus dem Wartungsmodus zurück in den Produktionsmodus versetzen, indem Sie die folgenden Aufgaben ausführen:

  - Führen Sie `Set-ServerComponentState <ServerName> -Component ServerWideOffline -State Active -Requester Maintenance` aus, um anzugeben, dass sich der Server nicht mehr im Wartungsmodus befindet.

  - Führen Sie `Set-ServerComponentState <ServerName> -Component UMCallRouter -State Active -Requester Maintenance` aus, um zuzulassen, dass der Server Unified Messaging-Anrufe annimmt.

  - Führen Sie `Resume-ClusterNode <ServerName>` aus, um den Knoten im Cluster fortzusetzen und die vollständige Clusterfunktionalität für den Server zu aktivieren.

  - Führen Sie `Set-MailboxServer <ServerName> -DatabaseCopyActivationDisabledAndMoveNow $False` aus, um zuzulassen, dass Datenbanken auf dem Server aktiv werden.

  - Führen Sie `Set-MailboxServer <ServerName> -DatabaseCopyAutoActivationPolicy Unrestricted` aus, um die automatischen Aktivierungsblockierungen zu entfernen.

  - Führen Sie `Set-ServerComponentState <ServerName> -Component HubTransport -State Active -Requester Maintenance` aus, um die Transportwarteschlangen zu aktivieren und zuzulassen, dass der Server Nachrichten annimmt und verarbeitet.

  - Führen Sie `Restart-Service MSExchangeTransport` aus, um die Transportaktivität fortzusetzen.

Führen Sie die folgenden Aufgaben aus, um zu überprüfen, ob ein Server für den Produktionseinsatz bereit ist:

1.  Führen Sie `Get-ServerComponentState <ServerName> | ft Component,State -Autosize` aus, um sicherzustellen, dass sich der Server nicht im Wartungsmodus befindet.

Wenn Sie ein Exchange-Update installieren und der Updateprozess fehlschlägt, können dadurch einige Serverkomponenten in einem inaktiven Zustand verbleiben. Dies wird in der Ausgabe des oben aufgeführten Cmdlets "Get-ServerComponentState" angezeigt. Führen Sie zum Beheben des Problems die folgenden Befehle aus:

  - `Set-ServerComponentState <ServerName> -Component ServerWideOffline -State Active -Requester Functional`

  - `Set-ServerComponentState <ServerName> -Component Monitoring -State Active -Requester Functional`

  - `Set-ServerComponentState <ServerName> -Component RecoveryActionsEnabled -State Active -Requester Functional`

Zurück zum Seitenanfang

## Herunterfahren von DAG-Mitgliedern

Die Exchange 2013-Lösung mit hoher Verfügbarkeit ist in den Windows-Prozess zum Herunterfahren integriert. Wenn ein Administrator oder eine Anwendung das Herunterfahren eines Windows-Servers in einer DAG mit einer eingebundenen Datenbank initiiert, die an eine oder mehrere DAG-Mitglieder repliziert wird, versucht das System, eine andere Kopie der eingebundenen Datenbank zu aktivieren, bevor der Server heruntergefahren werden kann.

Dieses neue Verhalten gewährleistet jedoch keine `lossless`-Aktivierung aller Datenbanken auf dem Server, der heruntergefahren wird. Deshalb wird empfohlen, vor dem Herunterfahren eines Servers, der Mitglied einer DAG ist, einen Serverswitchover durchzuführen.

Zurück zum Seitenanfang

## Installieren von Updates auf DAG-Mitgliedern

Das Installieren von Microsoft Exchange Server 2013-Updates auf einem Server, der Mitglied einer DAG ist, ist ein relativ einfacher Prozess. Wenn Sie ein Update auf einem Server installieren, der Mitglied einer DAG ist, werden mehrere Dienste während der Installation angehalten, darunter auch alle Exchange-Dienste und der Clusterdienst. Die allgemeine Vorgehensweise zum Zuweisen von Updates zu einem DAG-Mitglied ist folgende:

1.  Führen Sie die oben beschriebenen Schritte aus, um das DAG-Mitglied in den Wartungsmodus zu versetzen.

2.  Installieren Sie das Update.

3.  Führen Sie die oben beschriebenen Schritte aus, um das DAG-Mitglied aus dem Wartungsmodus zurück in den Produktionsmodus zu versetzen.

4.  Verwenden Sie optional das Skript "RedistributeActiveDatabases.ps1", um die aktiven Datenbankkopien für die DAG neu auszugleichen.

Sie können das aktuelle Update für Exchange 2013 im [Microsoft Download Center](http://www.microsoft.com/downloads) herunterladen.

Zurück zum Seitenanfang


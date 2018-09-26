---
title: 'CSV-Dateien für Postfachmigration: Exchange 2013 Help'
TOCTitle: CSV-Dateien für Postfachmigration
ms:assetid: e67b3455-3946-4335-b80c-97823c76ac54
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn170437(v=EXCHG.150)
ms:contentKeyID: 54651516
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# CSV-Dateien für Postfachmigration

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-11-16_

Sie können eine CSV-Datei verwenden, um eine große Anzahl von Benutzerpostfächern gleichzeitig zu migrieren. Sie können eine CSV-Datei angeben, wenn Sie die Exchange-Verwaltungskonsole oder das Cmdlet **New-MigrationBatch** in der Exchange-Verwaltungsshell verwenden, um einen Migrationsbatch zu erstellen. Die Verwendung einer CSV-Datei, um mehrere Benutzer festzulegen, die in einem Migrationsbatch migriert werden, wird in den folgenden Migrationsszenarios unterstützt:

  - **Verschiebungen in lokalen Exchange-Organisationen**
    
      - **Lokale Verschiebung:**  Bei einer lokalen Verschiebung werden Postfächer von einer Postfachdatenbank in eine andere verschoben. Eine lokale Verschiebung erfolgt innerhalb einer einzigen Gesamtstruktur.
    
      - **Gesamtstrukturübergreifende Unternehmensverschiebung:**  Bei einer gesamtstrukturübergreifenden Unternehmensverschiebung werden Postfächer in eine andere Gesamtstruktur verschoben. Gesamtstrukturübergreifende Verschiebungen werden entweder in der Zielgesamtstruktur initiiert, bei der es sich um die Gesamtstruktur handelt, in welche die Postfächer verschoben werden sollen, oder in der Quellgesamtstruktur, bei der es sich um die Gesamtstruktur handelt, in der die Postfächer gegenwärtig gehostet werden.

  - **Onboarding und Offboarding in Exchange Online**
    
      - **Onboarding-Remoteverschiebungsmigration:**  In einer Exchange-Hybridbereitstellung können Sie Postfächer von einer lokalen Exchange-Organisation zu Exchange Online verschieben. Dies wird auch als *Onboarding*-Remoteverschiebungsmigration bezeichnet, da Postfächer zu Exchange Online hinzugefügt werden.
    
      - **Offboarding-Remoteverschiebungsmigration:**  Sie können auch eine *Offboarding*-Remoteverschiebungsmigration ausführen, bei der Exchange Online-Postfächer in die lokale Exchange-Organisation verschoben werden.
        

        > [!NOTE]
        > Sowohl Onboarding- als auch Offboarding-Remoteverschiebungsmigrationen werden von der Exchange Online-Organisation initiiert.

    
      - **Mehrstufige Exchange-Migration:**  Sie können auch eine Teilmenge von Postfächern aus einer lokalen Exchange-Organisation zu Exchange Online migrieren. Dies ist eine andere Art der Onboardingmigration. Bei einer mehrstufigen Exchange-Migration können nur Exchange 2003- und Exchange 2007-Postfächer migriert werden. Bei der Migration von Exchange 2010- und Exchange 2013-Postfächern wird keine mehrstufige Migration unterstützt. Vor einer mehrstufigen Migration müssen Sie eine Verzeichnissynchronisierung durchführen oder eine andere Methode verwenden, um die E-Mail-Benutzer in Ihrer Exchange Online-Organisation bereitzustellen.
    
      - **IMAP-Migration:**  Diese Art der Onboardingmigration dient dazu, Postfachdaten von einem IMAP-Server (einschließlich Exchange) zu Exchange Online zu migrieren. Bei einer IMAP-Migration müssen Sie die Postfächer in Exchange Online bereitstellen, bevor Sie Postfachdaten migrieren können.


> [!NOTE]
> Eine Exchange-Übernahmemigration unterstützt die Verwendung einer CSV-Datei nicht, da alle lokalen Benutzerpostfächer in einem einzigen Batch zu Exchange Online migriert werden.



## Unterstützte Attribute für CSV-Dateien für massenweise ausgeführte Verschiebungen und Migrationen

In der ersten Zeile (auch als Kopfzeile bezeichnet) einer CSV-Datei, die zur Migration von Benutzern verwendet wird, werden die Namen der Attribute oder Felder aufgelistet, die in den folgenden Zeilen angegeben werden. Die einzelnen Attributnamen werden jeweils durch ein Komma getrennt. Jede Zeile unter der Kopfzeile stellt einen einzelnen Benutzer dar und stellt die für die Migration erforderlichen Informationen zur Verfügung. Die Attribute in jeder einzelnen Benutzerzeile müssen die gleiche Reihenfolge aufweisen wie die Attributnamen in der Kopfzeile. Die einzelnen Attributwerte werden jeweils durch ein Komma getrennt. Wenn der Attributwert für einen bestimmten Eintrag null ist, geben Sie nichts für dieses Attribut ein. Stellen Sie jedoch sicher, dass das entsprechende Komma vorhanden ist, um den Nullwert vom nächsten Attribut zu trennen.

Attributwerte in der CSV-Datei überschreiben den Wert des entsprechenden Parameters, wenn der gleiche Parameter bei der Erstellung eines Migrationsbatch mit dem EAC oder der Exchange-Verwaltungsshellverwendet wird. Weitere Informationen und Beispiele finden Sie im Abschnitt Attributwerte in der CSV-Datei überschreiben die Werte für den Migrationsbatch.


> [!TIP]
> Sie können zur Erstellung der CSV-Datei einen beliebigen Texteditor verwenden. Eine Anwendung wie Microsoft&nbsp;Excel erleichtert jedoch das Importieren von Daten und das Konfigurieren und Organisieren von CSV-Dateien. Speichern Sie CSV-Dateien als CSV- oder TXT-Datei.



In den folgenden Abschnitten werden die für die Kopfzeile einer CSV-Datei unterstützten Attribute (für jeden Migrationstyp) beschrieben. Jeder Abschnitt enthält eine Tabelle, in der jedes unterstützte Attribut aufgeführt ist und angegeben ist, ob es erforderlich ist. Außerdem enthält die Tabelle ein Beispiel für einen Wert, der für das Attribut verwendet werden kann, und eine Beschreibung.


> [!NOTE]
> In den folgenden Abschnitten bezieht sich <EM>Quellumgebung</EM> auf den aktuellen Speicherort eines Benutzerpostfachs oder einer Datenbank. <EM>Zielumgebung</EM> bezieht sich auf den Speicherort, an den das Postfach migriert wird, oder auf die Datenbank, in welche das Postfach verschoben wird.



## Lokale Verschiebungen

Die folgende Tabelle beschreibt die unterstützten Attribute für eine CSV-Datei für lokale Verschiebungen. Weitere Informationen finden Sie unter [Verwalten von lokalen Verschiebungen](manage-on-premises-moves-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Erforderlich oder optional</th>
<th>Akzeptierte Werte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EmailAddress</p></td>
<td><p>Erforderlich</p></td>
<td><p>SMTP-Adresse für den Benutzer</p></td>
<td><p>Gibt den Benutzer an, der verschoben wird.</p></td>
</tr>
<tr class="even">
<td><p>TargetDatabase</p></td>
<td><p>Optional</p></td>
<td><p>Datenbankname</p></td>
<td><p>Gibt die Postfachdatenbank an, in welche das primäre Postfach des Benutzers verschoben wird. Sie können in den unterschiedlichen Zeilen der CSV-Datei unterschiedliche Datenbanken angeben, um Postfächer im gleichen Migrationsbatch in unterschiedliche Datenbanken zu verschieben.</p></td>
</tr>
<tr class="odd">
<td><p>TargetArchiveDatabase</p></td>
<td><p>Optional</p></td>
<td><p>Datenbankname</p></td>
<td><p>Gibt die Postfachdatenbank an, in welche das Archivpostfach des Benutzers (falls vorhanden) verschoben wird. Sie können in den unterschiedlichen Zeilen der CSV-Datei unterschiedliche Datenbanken angeben, um Archivpostfächer im gleichen Migrationsbatch in unterschiedliche Datenbanken zu verschieben.</p>

> [!NOTE]
> Wenn Sie keine Archivdatenbank angeben, wird das Archivpostfach in die gleiche Datenbank wie das primäre Postfach verschoben.


</td>
</tr>
<tr class="even">
<td><p>BadItemLimit</p></td>
<td><p>Optional</p></td>
<td><p><code>Unlimited</code> oder eine nicht negative ganze Zahl zwischen <code>0</code> (dem Standardwert) bis zu einem Maximalwert von <code>2147483647</code></p></td>
<td><p>Gibt die Anzahl ungültiger Elemente an, die übersprungen werden, wenn der Migrationsdienst im Postfach ein beschädigtes Element vorfindet. Wenn Sie dieses Attribut in die CSV-Datei aufnehmen, überschreibt es den Standardwert oder einen von Ihnen festgelegten Wert, wenn Sie bei der Erstellung des Migrationsbatch den Exchange-Verwaltungsshell-Parameter mithilfe des EAC oder der <em>BadItemLimit</em> einschließen.</p>

> [!TIP]
> Es wird empfohlen, den Standardwert 0 zu verwenden und die Grenze für ungültige Elemente nur für einen bestimmten Benutzer zu erhöhen, wenn die Verschiebung oder Migration für diesen Benutzer fehlschlägt.


<p></p></td>
</tr>
<tr class="odd">
<td><p>MailboxType</p></td>
<td><p>Optional</p></td>
<td><p>Verwenden Sie einen der folgenden Werte:</p>
<ul>
<li><p><code>PrimaryOnly</code></p></li>
<li><p><code>ArchiveOnly</code></p></li>
<li><p><code>PrimaryAndArchive</code> (der Standardwert)</p></li>
</ul></td>
<td><p>Gibt an, ob das primäre Postfach oder das Archivpostfach des Benutzers oder beides verschoben werden sollen.</p></td>
</tr>
</tbody>
</table>


## Onboarding-Remoteverschiebungsmigration in einer Hybridbereitstellung

Sie können Postfächer in einer Hybridbereitstellung von einer lokalen Exchange-Organisation zu Exchange Online verschieben. Beim Hinzufügen von Postfächern wird der Migrationsbatch in der Exchange Online-Organisation erstellt und durch einen Exchange Online-Administrator initiiert. Weitere Informationen finden Sie unter [Verschieben von Postfächern zwischen lokalen und Exchange Online-Organisationen in Hybridbereitstellungen](https://technet.microsoft.com/de-de/library/jj906432\(v=exchg.150\)).

Die folgende Tabelle beschreibt die unterstützten Attribute für eine CSV-Datei für Onboarding-Remoteverschiebungsmigrationen.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Erforderlich oder optional</th>
<th>Akzeptierte Werte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EmailAddress</p></td>
<td><p>Erforderlich</p></td>
<td><p>SMTP-Adresse für den Benutzer</p></td>
<td><p>Gibt die E-Mail-Adresse für den E-Mail-aktivierten Benutzer in der Exchange Online-Organisation an, der dem lokalen Benutzerpostfach entspricht, das migriert wird.</p></td>
</tr>
<tr class="even">
<td><p>BadItemLimit</p></td>
<td><p>Optional</p></td>
<td><p><code>Unlimited</code> oder eine nicht negative ganze Zahl zwischen <code>0</code> (dem Standardwert) bis zu einem Maximalwert von <code>2147483647</code></p></td>
<td><p>Gibt die Anzahl ungültiger Elemente an, die übersprungen werden, wenn der Migrationsdienst im Postfach ein beschädigtes Element vorfindet. Wenn Sie dieses Attribut in die CSV-Datei aufnehmen, überschreibt es den Standardwert oder den von Ihnen festgelegten Wert, wenn Sie bei der Erstellung des Migrationsbatch den Exchange-Verwaltungsshell-Parameter mithilfe des EAC oder der <em>BadItemLimit</em> einschließen.</p>

> [!TIP]
> Es wird empfohlen, den Standardwert 0 zu verwenden und die Grenze für ungültige Elemente nur für einen bestimmten Benutzer zu erhöhen, wenn die Verschiebung oder Migration für diesen Benutzer fehlschlägt.


</td>
</tr>
<tr class="odd">
<td><p>LargeItemLimit</p></td>
<td><p>Optional</p></td>
<td><p><code>Unlimited</code> oder eine nicht negative ganze Zahl zwischen <code>0</code> (dem Standardwert) bis zu einem Maximalwert.</p></td>
<td><p>Gibt die Anzahl großer Elemente in dem Postfach des Benutzers an, die übersprungen werden. Wenn die Anzahl großer Elemente diesen Wert übersteigt, tritt bei der Migration des Postfachs ein Fehler auf.</p>
<p>Der Standardwert lautet 0. In diesem Fall wird bei der Migration ein Fehler gemeldet, wenn das Postfach auch nur ein großes Element enthält.</p>
<p>Wenn Postfächer zu Exchange Online hinzugefügt werden, werden Elemente mit bis zu 35 MB migriert.</p></td>
</tr>
<tr class="even">
<td><p>MailboxType</p></td>
<td><p>Optional</p></td>
<td><p>Verwenden Sie einen der folgenden Werte:</p>
<ul>
<li><p><code>PrimaryOnly</code></p></li>
<li><p><code>ArchiveOnly</code></p></li>
<li><p><code>PrimaryAndArchive</code> (der Standardwert)</p></li>
</ul></td>
<td><p>Gibt an, ob das primäre Postfach oder das Archivpostfach des Benutzers oder beides verschoben werden sollen.</p></td>
</tr>
</tbody>
</table>


## Gesamtstrukturübergreifende Unternehmensverschiebungen und Offboarding-Remoteverschiebungsmigrationen in einer Hybridbereitstellung

Wie bereits erwähnt, werden gesamtstrukturübergreifende Verschiebungen entweder von der Zielgesamtstruktur oder der Quellgesamtstruktur initiiert. Offboarding-Remoteverschiebungsmigrationen werden von der Exchange Online-Organisation initiiert. Weitere Informationen finden Sie unter:

  - [Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungsanforderungen](prepare-mailboxes-for-cross-forest-move-requests-exchange-2013-help.md)

  - [Verschieben von Postfächern zwischen lokalen und Exchange Online-Organisationen in Hybridbereitstellungen](https://technet.microsoft.com/de-de/library/jj906432\(v=exchg.150\))

Die folgende Tabelle beschreibt die unterstützten Attribute für eine CSV-Datei für gesamtstrukturübergreifende Unternehmensverschiebungen und Offboarding-Remoteverschiebungsmigrationen in einer Exchange-Hybridbereitstellung.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Erforderlich oder optional</th>
<th>Akzeptierte Werte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EmailAddress</p></td>
<td><p>Erforderlich</p></td>
<td><p>SMTP-Adresse für den Benutzer</p></td>
<td><p>Bei gesamtstrukturübergreifenden Unternehmensverschiebungen gibt dieser Wert das Postfach oder den E-Mail-aktivierten Benutzer in der Quellgesamtstruktur an.</p>
<p>Bei Offboarding-Remoteverschiebungsmigrationen gibt der Wert das Exchange Online-Postfach an.</p></td>
</tr>
<tr class="even">
<td><p>TargetDatabase</p></td>
<td><p>Erforderlich bei Offboarding-Remoteverschiebungsmigrationen und gesamtstrukturübergreifenden Unternehmensverschiebungen, die von der Quellgesamtstruktur initiiert werden. Alternativ kann dieses Attribut bei der Erstellung des Migrationsbatch in der Exchange-Verwaltungskonsole oder mit der Exchange-Verwaltungsshell angegeben werden.</p>
<p>Dieses Attribut ist bei gesamtstrukturübergreifenden Unternehmensverschiebungen, die von der Zielgesamtstruktur initiiert werden, optional.</p></td>
<td><p>Datenbankname</p></td>
<td><p>Gibt die Postfachdatenbank in der Zielgesamtstruktur an, in welche das primäre Postfach des Benutzers verschoben wird. Sie können in den unterschiedlichen Zeilen der CSV-Datei eine unterschiedliche Datenbank angeben, um Postfächer im gleichen Migrationsbatch in unterschiedliche Datenbanken zu verschieben.</p></td>
</tr>
<tr class="odd">
<td><p>TargetArchiveDatabase</p></td>
<td><p>Optional</p></td>
<td><p>Datenbankname</p></td>
<td><p>Gibt die Postfachdatenbank in der Zielgesamtstruktur an, in welche das Archivpostfach des Benutzers verschoben wird. Sie können in den unterschiedlichen Zeilen der CSV-Datei eine unterschiedliche Datenbank angeben, um Archivpostfächer im gleichen Migrationsbatch in unterschiedliche Datenbanken zu verschieben.</p></td>
</tr>
<tr class="even">
<td><p>BadItemLimit</p></td>
<td><p>Optional</p></td>
<td><p><code>Unlimited</code> oder eine nicht negative ganze Zahl zwischen <code>0</code> (dem Standardwert) bis zu einem Maximalwert von <code>2147483647</code></p></td>
<td><p>Gibt die Anzahl ungültiger Elemente an, die übersprungen werden, wenn der Migrationsdienst im Postfach ein beschädigtes Element vorfindet. Wenn Sie dieses Attribut in die CSV-Datei aufnehmen, überschreibt es den Standardwert oder den von Ihnen festgelegten Wert, wenn Sie bei der Erstellung des Migrationsbatch den Exchange-Verwaltungsshell-Parameter mithilfe des EAC oder der <em>BadItemLimit</em> einschließen.</p>

> [!TIP]
> Es wird empfohlen, den Standardwert 0 zu verwenden und die Grenze für ungültige Elemente nur für einen bestimmten Benutzer zu erhöhen, wenn die Verschiebung oder Migration für diesen Benutzer fehlschlägt.


</td>
</tr>
<tr class="odd">
<td><p>LargeItemLimit</p></td>
<td><p>Optional</p></td>
<td><p><code>Unlimited</code> oder eine nicht negative ganze Zahl zwischen <code>0</code> (dem Standardwert) bis zu einem Maximalwert.</p></td>
<td><p>Gibt die Anzahl großer Elemente in dem Postfach des Benutzers an, die übersprungen werden. Wenn die Anzahl großer Elemente diesen Wert übersteigt, tritt bei der Migration des Postfachs ein Fehler auf.</p>
<p>Der Standardwert lautet 0. In diesem Fall wird bei der Migration ein Fehler gemeldet, wenn das Postfach auch nur ein großes Element enthält.</p>
<p>Wenn Postfächer zu Exchange Online hinzugefügt werden, werden Elemente mit bis zu 35 MB migriert.</p></td>
</tr>
<tr class="even">
<td><p>MailboxType</p></td>
<td><p>Optional</p></td>
<td><p>Verwenden Sie einen der folgenden Werte:</p>
<ul>
<li><p><code>PrimaryOnly</code></p></li>
<li><p><code>ArchiveOnly</code></p></li>
<li><p><code>PrimaryAndArchive</code> (der Standardwert)</p></li>
</ul></td>
<td><p>Gibt an, ob das primäre Postfach oder das Archivpostfach des Benutzers oder beides verschoben werden sollen.</p></td>
</tr>
</tbody>
</table>


## Mehrstufige Exchange-Migrationen

Sie müssen eine CSV-Datei verwenden, um die Gruppe von Benutzern für einen Migrationsbatch anzugeben, wenn Sie lokale Exchange 2003- und Exchange 2007-Postfächer mithilfe einer phasenweisen Exchange-Migration zu Exchange Online migrieren möchten. Es gibt keine Beschränkung der Anzahl von Postfächern, die Sie mit einer mehrstufigen Exchange-Migration zur Cloud migrieren können. Die CSV-Datei für einen Migrationsbatch kann jedoch maximal 1.000 Zeilen enthalten. Zum Migrieren von mehr als 1.0000 Postfächern müssen Sie zusätzliche CSV-Dateien erstellen und dann mit jeder dieser Dateien einen neuen Migrationsbatch erstellen. Weitere Informationen zu phasenweisen Exchange-Migrationen finden Sie unter [Migrieren von Postfächern zu Exchange Online mit einer mehrstufigen Migration](https://technet.microsoft.com/de-de/library/jj874018\(v=exchg.150\)).

Die folgende Tabelle beschreibt die unterstützten Attribute für eine CSV-Datei für eine phasenweise Exchange-Migration.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Erforderlich oder optional</th>
<th>Akzeptierte Werte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EmailAddress</p></td>
<td><p>Erforderlich</p></td>
<td><p>SMTP-Adresse für den Benutzer</p></td>
<td><p>Gibt die E-Mail-Adresse für den E-Mail-aktivierten Benutzer (oder ein Postfach, wenn Sie versuchen, die Migration erneut auszuführen) in Exchange Online an, der bzw. das dem lokalen Benutzerpostfach entspricht, das migriert wird. E-Mail-aktivierte Benutzer werden in Exchange Online durch den Verzeichnissynchronisierungsprozess oder einen anderen Bereitstellungsprozess erstellt. Die E-Mail-Adresse des E-Mail-aktivierten Benutzers muss der Eigenschaft <em>WindowsEmailAddress</em> für das entsprechende lokale Postfach entsprechen.</p></td>
</tr>
<tr class="even">
<td><p>Kennwort</p></td>
<td><p>Optional</p></td>
<td><p>Ein Kennwort muss eine Mindestlänge von acht Zeichen haben und alle Kennworteinschränkungen erfüllen, die auf Ihre Office 365-Organisation angewendet wurden.</p></td>
<td><p>Dieses Kennwort wird für das Benutzerkonto festgelegt, wenn der entsprechende E-Mail-aktivierte Benutzer in Exchange Online während der Migration in ein Postfach umgewandelt wird.</p></td>
</tr>
<tr class="odd">
<td><p>ForceChangePassword</p></td>
<td><p>Optional</p></td>
<td><p><code>True</code> oder <code>False</code></p></td>
<td><p>Gibt an, ob ein Benutzer das Kennwort ändern muss, wenn er sich das erste Mal am neuen Exchange Online-Postfach anmeldet.</p>

> [!NOTE]
> Wenn Sie eine Lösung für einmaliges Anmelden durch die Bereitstellung von Active Directory-Verbunddiensten 2.0 (AD FS 2.0) in Ihrer lokalen Organisation implementiert haben, müssen Sie <CODE>False</CODE> als Wert dieses Attributs verwenden.


</td>
</tr>
</tbody>
</table>


## IMAP-Migrationen

Eine CSV-Datei für einen IMAP-Migrationsbatch kann maximal 50.000 Zeilen enthalten. Es ist jedoch empfehlenswert, die Benutzer in mehreren kleineren Batches zu migrieren. Weitere Informationen zu IMAP-Migrationen finden Sie unter den folgenden Themen:

  - [Migrieren von E-Mails von einem IMAP-Server zu Exchange-Onlinepostfächern](https://technet.microsoft.com/de-de/library/jj874015\(v=exchg.150\))

  - [CSV-Dateien für IMAP-Migrationsbatches](https://technet.microsoft.com/de-de/library/jj200730\(v=exchg.150\))

Die folgende Tabelle beschreibt die unterstützten Attribute für eine CSV-Datei für eine IMAP-Migration.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Attribut</th>
<th>Erforderlich oder optional</th>
<th>Akzeptierte Werte</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EmailAddress</p></td>
<td><p>Erforderlich</p></td>
<td><p>SMTP-Adresse für den Benutzer.</p></td>
<td><p>Gibt die Benutzer-ID für das Exchange Online-Postfach des Benutzers an</p></td>
</tr>
<tr class="even">
<td><p>UserName</p></td>
<td><p>Erforderlich</p></td>
<td><p>Zeichenfolge, die den Benutzer in einem vom IMAP-Server unterstützten Format im IMAP-Messagingsystem identifiziert.</p></td>
<td><p>Gibt den Anmeldenamen für das Konto des Benutzers im IMAP-Messagingsystem (der Quellumgebung) an. Zusätzlich zum Benutzernamen können Sie die Anmeldeinformationen eines Kontos verwenden, dem die erforderlichen Berechtigungen für den Zugriff auf Postfächer auf dem IMAP-Server zugewiesen wurden. Weitere Informationen finden Sie unter <a href="https://technet.microsoft.com/de-de/library/jj200730(v=exchg.150)">CSV-Dateien für IMAP-Migrationsbatches</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Password</p></td>
<td><p>Erforderlich</p></td>
<td><p>Kennwortzeichenfolge.</p></td>
<td><p>Gibt das Kennwort für das vom Attribut &quot;UserName&quot; angegebene Benutzerkonto an.</p></td>
</tr>
</tbody>
</table>


## Attributwerte in der CSV-Datei überschreiben die Werte für den Migrationsbatch

Attributwerte in der CSV-Datei überschreiben den Wert des entsprechenden Parameters, wenn der gleiche Parameter bei der Erstellung eines Migrationsbatch mit der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell verwendet wird. Wenn der Migrationsbatchwert auf einen Benutzer angewendet werden soll, muss die Zelle in der CSV-Datei leer bleiben. So können Sie bestimmte Attributwerte für ausgewählte Benutzer in einem Migrationsbatch beliebig kombinieren.

Beispiel: Angenommen, Sie erstellen in der Exchange-Verwaltungsshell mit dem folgenden Exchange-Verwaltungsshell-Befehl einen Batch für eine gesamtstrukturübergreifende Unternehmensverschiebung, um das primäre und Archivpostfach der Benutzer in die Zielgesamtstruktur zu verschieben.

```powershell
    New-MigrationBatch -Name CrossForestBatch1 -SourceEndpoint ForestEndpoint1 -TargetDeliveryDomain forest2.contoso.com -TargetDatabases @(EXCH-MBX-02,EXCH-MBX-03) -TargetArchiveDatabases @(EXCH-MBX-A02,EXCH-MBX-A03) -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\CrossForestBatch1.csv")) -AutoStart
```

> [!NOTE]
> Da primäre und Archivpostfächer standardmäßig verschoben werden, müssen Sie dies im Exchange-Verwaltungsshell-Befehl nicht explizit angeben.



Ein Teil der Datei "CrossForestBatch1.csv" für diesen Migrationsbatch sieht folgendermaßen aus:

```powershell
    EmailAddress,TargetDatabase,TargetArchiveDatabase
    user1@contoso.com,EXCH-MBX-01,EXCH-MBX-A01
    user2@contoso.com,,
    user3@contoso.com,EXCH-MBX-01,
    ...
```

Da die Werte in der CSV-Datei die Werte für den Migrationsbatch überschreiben, werden das primäre und das Archivpostfach für Benutzer1 auf EXCH-MBX-01 bzw. EXCH-MBX-A01 in der Zielgesamtstruktur verschoben. Das primäre und das Archivpostfach für Benutzer2 werden auf EXCH-MBX-02 oder EXCH-MBX-03 verschoben. Das primäre Postfach für Benutzer3 wird auf EXCH-MBX-01 verschoben, und das Archivpostfach wird auf EXCH-MBX-A02 oder EXCH-MBX-A03 verschoben.

Ein weiteres Beispiel: Angenommen, Sie erstellen mit dem folgenden Befehl einen Batch für eine Onboarding-Remoteverschiebungsmigration in einer Hybridbereitstellung, um Archivpostfächer zu Exchange Online zu verschieben.

```powershell
    New-MigrationBatch -Name OnBoarding1 -SourceEndpoint RemoteEndpoint1 -TargetDeliveryDomain cloud.contoso.com -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\OnBoarding1.csv")) -MailboxType ArchiveOnly -AutoStart
```

Sie möchte allerdings für ausgewählte Benutzer auch die primären Postfächer verschieben. Somit würde ein Teil der Datei "OnBoarding1.csv" für diesen Migrationsbatch wie folgt aussehen:

```powershell
    EmailAddress,MailboxType
    user1@contoso.com,
    user2@contoso.com,
    user3@cloud.contoso.com,PrimaryAndArchive
    user4@cloud.contoso.com,PrimaryAndArchive
    ...
```

Da der Wert für den Postfachtyp in der CSV-Datei die Werte für den Parameter *MailboxType* im Befehl zur Erstellung des Batch überschreibt, wird bei Benutzer1 und Benutzer2 nur das Archivpostfach zu Exchange Online migriert. Bei Benutzer3 und Benutzer4 werden hingegen das primäre und das Archivpostfach zu Exchange Online verschoben.


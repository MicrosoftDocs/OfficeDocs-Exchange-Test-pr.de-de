---
title: 'Vorb. v. Postf. f. standortüb. Versch. m. „Prepare-MoveRequest.ps1 in Shell'
TOCTitle: Vorbereiten von Postfächern für eine standortübergreifende Verschiebung mit dem Skript „Prepare-MoveRequest.ps1“ in der Shell
ms:assetid: 2cea59fb-69b7-4a2f-833f-de4d93cf1810
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee861103(v=EXCHG.150)
ms:contentKeyID: 50475398
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Vorbereiten von Postfächern für eine standortübergreifende Verschiebung mit dem Skript „Prepare-MoveRequest.ps1\&quot; in der Shell

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-11-22_

**Zusammenfassung:**  erfahren Sie, wie gesamtstrukturübergreifenden postfachverschiebungen und-Migrationen in Exchange 2013 verwalten, indem Sie mit der Prepare-MoveRequest.ps1-Skripts in der Exchange-Verwaltungsshell.

Microsoft Exchange 2013 unterstützt das Verschieben von Postfächern und Migrationen von **New-MoveRequest** und **New-MigrationBatch** -Cmdlets. Sie können auch das Postfach über Exchange Administration Center (EAC) verschieben. Sie können eine Exchange 2010 oder Exchange 2013-Postfach aus einer Exchange Quellgesamtstruktur in einer Exchange 2013 Zielgesamtstruktur verschieben.

Zum Ausführen der Cmdlets **New-MoveRequest** und **New-MigrationBatch** muss in der Exchange-Zielgesamtstruktur ein E-Mail-Benutzer vorhanden sein, der über einen Mindestsatz an erforderlichen Active Directory-Attributen verfügt.

Das in diesem Thema beschriebene Windows PowerShell-Beispielskript unterstützt diese Aufgabe, indem es Postfachbenutzer aus einer Exchange 2013-Quellgesamtstruktur als E-Mail-aktivierte Benutzer in Exchange 2013-Zielgesamtstrukturen synchronisiert. Durch das Skript werden die Active Directory-Attribute der Postfachbenutzer aus der Quellgesamtstruktur in die Zielgesamtstruktur kopiert. Anschließend werden mithilfe des Cmdlets **Update-Recipient** die Zielobjekte in E-Mail-aktivierte Benutzer umgewandelt.

Weitere Informationen zum Verwenden und Schreiben von Skripts finden Sie unter [Skripterstellung mit der Exchange-Verwaltungsshell](https://technet.microsoft.com/de-de/library/bb123798\(v=exchg.150\)). Weitere Informationen zum Vorbereiten gesamtstrukturübergreifender Verschiebungen finden Sie unter [Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungsanforderungen](prepare-mailboxes-for-cross-forest-move-requests-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Remoteverschiebungsanforderungen gibt? Weitere Informationen finden Sie hier: [Verwalten von lokalen Verschiebungen](manage-on-premises-moves-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Suchen Sie das Skript im folgenden Pfad: Programme\\Microsoft\\Exchange Server\\V15\\Scripts

  - Um das Beispielskript auszuführen, benötigen Sie Folgendes:
    
      - Ein Exchange-Quellgesamtstruktur, das Postfach, in dem derzeit befindet. Dies kann ein Exchange 2010 oder Exchange 2013-Postfach sein.
    
      - Eine Zielgesamtstruktur mit Exchange 2013, in die das Postfach verschoben werden soll.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden des Skripts "Prepare-MoveRequest.ps1" für die Vorbereitung von Postfächern auf gesamtstrukturübergreifende Verschiebungen

Führen Sie das Skript von der Shell aus auf einer Serverrolle mit Exchange 2013 in der Exchange 2013-Zielgesamtstruktur aus. Das Skript kopiert die Postfachattribute aus der Quellgesamtstruktur.

Sie müssen zunächst das Windows PowerShell-Cmdlet **Get-Credential** ausführen und die Benutzereingabe in einer temporären Variablen speichern, um dem Domänencontroller der Remotegesamtstruktur bestimmte Anmeldeinformationen für die Authentifizierung zuzuweisen. Wenn das Cmdlet **Get-Credential** ausgeführt wird, wird nach dem Benutzernamen und dem Kennwort des Kontos gefragt, die bei der Authentifizierung für den Domänencontroller der Remotegesamtstruktur verwendet werden. Sie können die temporäre Variable dann im Skript "Prepare-MoveRequest.ps1" verwenden. Weitere Informationen zum Cmdlet **Get-Credential** finden Sie unter [Get-Credential](https://go.microsoft.com/fwlink/p/?linkid=142122).


> [!NOTE]
> Stellen Sie sicher, dass Sie beim Aufrufen dieses Skripts separate Anmeldeinformationen für die lokale Gesamtstruktur und die Remotegesamtstruktur verwenden.



1.  Führen Sie die folgenden Befehle aus, um die Anmeldeinformationen der lokalen Gesamtstruktur und der Remotegesamtstruktur abzurufen.
    
    ```powershell
        $LocalCredentials = Get-Credential
        $RemoteCredentials = Get-Credential
    ```
    
2.  Führen Sie die folgenden Befehle aus, um die Anmeldeinformationen an die Parameter *LocalForestCredential* und *RemoteForestCredential* im Skript "Prepare-MoveRequest.ps1" zu übergeben.

    ```powershell
        Prepare-MoveRequest.ps1 -Identity JohnSmith@Fabrikan.com -RemoteForestDomainController DC001.Fabrikam.com -RemoteForestCredential $RemoteCredentials -LocalForestDomainController DC001.Contoso.com -LocalForestCredential $LocalCredentials
    ```

## Parametersatz des Skripts

In der folgenden Tabelle wird der Parametersatz für das Skript beschrieben.

### Parametersatz des Skripts "Prepare-MoveRequest.ps1"

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Erforderlich</p></td>
<td><p>Mit dem Parameter <em>Identity</em> wird ein Postfach in der Quellgesamtstruktur eindeutig bezeichnet. &quot;Identity&quot; kann folgende Werte aufweisen:</p>
<ul>
<li><p>Allgemeiner Name (Common Name, CN)</p></li>
<li><p>Alias</p></li>
<li><p>Eigenschaft <strong>proxyAddress</strong></p></li>
<li><p>Eigenschaft <strong>objectGuid</strong></p></li>
<li><p>Eigenschaft <strong>DisplayName</strong></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><em>RemoteForestCredential</em></p></td>
<td><p>Erforderlich</p></td>
<td><p>Mit dem Parameter <em>RemoteForestCredential</em> wird der Administrator angegeben, der zum Kopieren von Daten aus der Active Directory-Quellgesamtstruktur berechtigt ist.</p></td>
</tr>
<tr class="odd">
<td><p><em>RemoteForestDomainController</em></p></td>
<td><p>Erforderlich</p></td>
<td><p>Der Parameter <em>RemoteForestDomainController</em> gibt einen Domänencontroller in der Quellgesamtstruktur an, in der sich das Postfach befindet.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableEmailAddressPolicy</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>DisableEmailAddressPolicy</em> gibt an, ob die E-Mail-Adressrichtlinie (EAP) bei der Erstellung eines Objekts <strong>MailUser</strong> in der Zielgesamtstruktur deaktiviert werden soll.</p>
<p>Wenn Sie diesen Parameter angeben, wird die E-Mail-Adressrichtlinie in der Zielgesamtstruktur nicht angewendet.</p>

> [!NOTE]
> Wenn Sie diesen Parameter angeben, wird für das Objekt <STRONG>MailUser</STRONG> die E-Mail-Adresszuordnung in der lokalen Gesamtstruktur nicht mit der Domäne markiert. In der Regel erfolgt diese Markierung durch die E-Mail-Adressrichtlinie.


</td>
</tr>
<tr class="odd">
<td><p><em>LinkedMailUser</em></p></td>
<td><p>Optional</p></td>
<td><p>Die Option <em>LinkedMailUser</em> gibt an, ob ein verknüpftes Objekt &quot;MailUser&quot; in der lokalen Gesamtstruktur für den Postfachbenutzer in der Remotegesamtstruktur erstellt werden soll.</p>
<p>Wenn die Option angegeben wird, erstellt das Skript ein <strong>MailUser</strong>-Zielobjekt, das mit dem Quellpostfach verknüpft ist. Wenn die Option nicht angegeben wird, erstellt das Skript einen reguläres <strong>MailUser</strong>-Zielobjekt.</p></td>
</tr>
<tr class="even">
<td><p><em>LocalForestCredential</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>LocalForestCredential</em> gibt den Administrator an, der zum Schreiben von Daten in die Active Directory-Zielgesamtstruktur berechtigt ist.</p>
<p>Sie sollten zur Vermeidung von Active Directory-Berechtigungsproblemen diesen Parameter explizit angeben.</p>
<p>Wenn zwischen der Remotegesamtstruktur und der lokalen Gesamtstruktur eine Vertrauensstellung konfiguriert ist, melden Sie sich nicht mit den Anmeldeinformationen eines Benutzerkontos aus der Remotegesamtstruktur bei der lokalen Gesamtstruktur an, und zwar auch dann nicht, wenn das Remotebenutzerkonto über Änderungsberechtigungen für Active Directory in der lokalen Gesamtstruktur verfügt.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalForestDomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>LocalForestDomainController</em> gibt einen Domänencontroller in der Zielgesamtstruktur an, in der der E-Mail-aktivierte Benutzer erstellt werden soll.</p>
<p>Sie sollten diesen Parameter angeben, um Verzögerungsprobleme bei der Domänencontrollerreplikation in der lokalen Gesamtstruktur zu vermeiden, die auftreten können, wenn ein zufälliger Domänencontroller ausgewählt wird.</p></td>
</tr>
<tr class="even">
<td><p><em>MailboxDeliveryDomain</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>MailboxDeliveryDomain</em> gibt eine autoritative Domäne der Quellgesamtstruktur an, sodass das Skript die Eigenschaft <strong>proxyAddress</strong> des richtigen Quellpostfachbenutzers als Eigenschaft <strong>targetAddress</strong> des E-Mail-aktivierten Zielbenutzers auswählen kann.</p>
<p>Standardmäßig wird die primäre SMTP-Adresse des Quellpostfachbenutzers als Eigenschaft <strong>targetAddress</strong> des E-Mail-aktivierten Zielbenutzers festgelegt.</p></td>
</tr>
<tr class="odd">
<td><p><em>OverWriteLocalObject</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>OverWriteLocalObject</em> wird für Benutzer verwendet, die mit dem Active Directory-Migrationstool erstellt wurden. Die Eigenschaften werden aus dem vorhandenen E-Mail-Kontakt in den neu erstellten E-Mail-Benutzer kopiert. Nach diesem Kopiervorgang kopiert das Skript außerdem die Eigenschaften aus dem Benutzer der Quellgesamtstruktur in den neu erstellten E-Mail-Benutzer.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetMailUserOU</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>TargetMailuserOU</em> gibt die Organisationseinheit an, in der der E-Mail-aktivierte Zielbenutzer erstellt wird.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseLocalObject</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>UseLocalObject</em> gibt an, ob das vorhandene lokale Objekt in den erforderlichen E-Mail-aktivierten Zielbenutzer konvertiert wird, wenn das Skript ein Objekt in der lokalen Gesamtstruktur erkennt, das mit dem zu erstellenden E-Mail-aktivierten Benutzer in Konflikt steht.</p></td>
</tr>
</tbody>
</table>


## Beispiele

Dieser Abschnitt enthält mehrere Beispiele zur Verwendung des Skripts "Prepare-MoveRequest.ps1".

## Beispiel: Einzelner, verknüpfter E-Mail-aktivierter Benutzer

In diesem Beispiel wird ein einzelner, verknüpfter E-Mail-aktivierter Benutzer in der lokalen Gesamtstruktur bereitgestellt, wobei eine Gesamtstruktur-Vertrauensstellung zwischen der Remotegesamtstruktur und der lokalen Gesamtstruktur besteht.

1.  Führen Sie die folgenden Befehle aus, um die Anmeldeinformationen der lokalen Gesamtstruktur und der Remotegesamtstruktur abzurufen.

    ```powershell
        $LocalCredentials = Get-Credential
        $RemoteCredentials = Get-Credential
    ```
    
2.  Führen Sie den folgenden Befehl aus, um die Anmeldeinformationen an die Parameter *LocalForestCredential* und *RemoteForestCredential* im Skript "Prepare-MoveRequest.ps1" zu übergeben.

    ```powershell
        Prepare-MoveRequest.ps1 -Identity JamesAlvord@Contoso.com -RemoteForestDomainController DC001.Fabrikam.com -RemoteForestCredential $RemoteCredentials -LocalForestDomainController DC001.Contoso.com -LocalForestCredential $LocalCredentials -LinkedMailUser 
    ```
    
## Beispiel: Pipelining

In diesem Beispiel wird Pipelining unterstützt, wenn Sie eine Liste von Postfachidentitäten angeben.

1.  Führen Sie den folgenden Befehl aus.
    
    ```powershell
    $UserCredentials = Get-Credential
    ```

2.  Führen Sie den folgenden Befehl aus, um die Anmeldeinformationen an den Parameter *RemoteForestCredential* im Skript "Prepare-MoveRequest.ps1" zu übergeben.

    ```powershell
        "IanP@Contoso.com", "JoeAn@Contoso.com" | Prepare-MoveRequest.ps1 -RemoteForestDomainController DC001.Fabrikam.com -RemoteForestCredential $UserCredentials
    ```
    
## Beispiel: Erstellen von E-Mail-aktivierten Benutzern per Massenvorgang mithilfe einer CSV-Datei

Sie können eine CSV-Datei mit einer Liste von Postfachidentitäten aus der Quellgesamtstruktur generieren, mit der Sie den Inhalt dieser Datei mittels Pipe an das Skript übergeben können, um die E-Mail-aktivierten Zielbenutzer per Massenvorgang zu erstellen.

Beispielsweise kann der Inhalt der CSV-Datei wie folgt lauten:

Identity

Ian@contoso.com

John@contoso.com

Cindy@contoso.com

In diesem Beispiel wird eine CSV-Datei aufgerufen, um die E-Mail-aktivierten Zielbenutzer per Massenvorgang zu erstellen.

1.  Führen Sie den folgenden Befehl aus, um die Anmeldeinformationen der Remotegesamtstruktur abzurufen.
    
    ```powershell
    $UserCredentials = Get-Credential
    ```

2.  Führen Sie den folgenden Befehl aus, um die Anmeldeinformationen an den Parameter *RemoteForestCredential* im Skript "Prepare-MoveRequest.ps1" zu übergeben.

    ```powershell
        Import-Csv Test.csv | Prepare-MoveRequest.ps1 -RemoteForestDomainController DC001.Fabrikam.com -RemoteForestCredential $UserCredentials
    ```
    
## Verhalten des Skripts für jedes Zielobjekt

In diesem Abschnitt wird das Verhalten des Skripts im Hinblick auf verschiedene Szenarien für Zielobjekte beschrieben.

## Doppeltes E-Mail-aktiviertes Zielobjekt

Wenn das Skript versucht, einen E-Mail-aktivierten Zielbenutzer aus dem Quellpostfachbenutzer zu erstellen, und dabei ein doppeltes, lokales E-Mail-aktiviertes Objekt erkannt wird, wird die folgende Logik verwendet:

  - Wenn das Attribut **masterAccountSid** des Quellpostfachbenutzers gleich des Attributs **objectSid** oder **masterAccountSid** des Zielobjekts ist:
    
      - Ist das Zielobjekt nicht E-Mail-aktiviert, gibt das Skript einen Fehler zurück, weil es die Konvertierung eines nicht E-Mail-aktivierten Objekts in einen E-Mail-aktivierten Benutzer nicht unterstützt.
    
      - Ist das Zielobjekt E-Mail-aktiviert ist, ist es ein Duplikat.

  - Wenn eine Adresse in den Eigenschaften **proxyAddress** (nur smtp/x500) des Quellpostfachbenutzers mit einer Adresse in der Eigenschaft **proxyAddress** (nur smtp/x500) eines Zielobjekts übereinstimmt, ist das Zielobjekt ein Duplikat.

Das Skript gibt eine Anfrage an den Benutzer hinsichtlich der doppelten Objekte aus.

Ist das E-Mail-aktivierte Zielobjekt ein E-Mail-aktivierter Benutzer oder Kontakt, der im Allgemeinen von einer gesamtstrukturübergreifenden (auf Identity Lifecycle Management 2007, Service Pack 1, basierenden) Synchronisierungsbereitstellung einer globalen Adressliste erstellt wurde, kann der Benutzer das Skript mit dem Parameter *UseLocalObject* erneut ausführen, um das E-Mail-aktivierte Zielobjekt für die Postfachmigration zu verwenden.

## E-Mail-aktivierter Benutzer

Wenn das Zielobjekt ein E-Mail-aktivierter Benutzer ist, kopiert das Skript die folgenden Attribute vom Quellpostfachbenutzer zum E-Mail-aktivierten Zielbenutzer:

  - **msExchMailboxGUID**

  - **msExchArchiveGUID**

  - **msExchArchiveName**

Ist der Parameter *LinkedMailUser* festgelegt, kopiert das Skript das Attribut **objectSid**/**masterAccountSid** der Quelle.

## E-Mail-aktivierter Kontakt

Wenn das Zielobjekt ein E-Mail-aktivierter Kontakt ist, löscht das Skript den vorhandenen Kontakt und kopiert alle Attribute dieses Kontakts in einen neuen E-Mail-aktivierten Benutzer. Das Skript kopiert außerdem die folgenden Attribute vom Quellpostfachbenutzer:

  - **msExchMailboxGUID**

  - **msExchArchiveGUID**

  - **msExchArchiveName**

  - **sAMAccountName**

  - **userAccountControl** (festgelegt auf: 514 //equivalent to 0x202, ACCOUNTDISABLE | NORMAL\_ACCOUNT)

  - **userPrincipalName**

Ist der Parameter *LinkedMailUser* festgelegt, wird vom Skript das Quellattribut **objectSid**/**masterAccountSid** kopiert.

## LegacyExchangeDN-Attribut

Wird das Cmdlet **Update-Recipient** aufgerufen, um das Zielobjekt in einen E-Mail-aktivierten Benutzer zu konvertieren, wird ein neues Attribut **LegacyExchangeDN** für den E-Mail-aktivierten Zielbenutzer generiert. Das Skript kopiert den Wert **LegacyExchangeDN** des E-Mail-aktivierten Zielbenutzers als x500-Adresse in die Eigenschaft **proxyAddress** des Quellpostfachbenutzers.


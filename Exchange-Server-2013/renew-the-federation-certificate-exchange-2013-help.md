---
title: 'Erneuern des Verbundzertifikats: Exchange 2013 Help'
TOCTitle: Erneuern des Verbundzertifikats
ms:assetid: 0f390713-3058-44d0-9c07-3c982616e790
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt779252(v=EXCHG.150)
ms:contentKeyID: 74429168
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erneuern des Verbundzertifikats

 

_**Letztes Änderungsdatum des Themas:** 2017-02-28_

In diesem Artikel wird erläutert, wie Sie das selbstsignierte Verbundzertifikat aktualisieren können, das in einer Verbundvertrauensstellung verwendet wird:

  - Wenn das Verbundzertifikat noch nicht abgelaufen ist: Führen Sie die Schritte im Abschnitt Aktualisieren eines funktionierenden Verbundzertifikats durch.

  - Wenn das Verbundzertifikat bereits abgelaufen ist: Führen Sie die Schritte im Abschnitt Ersetzen eines abgelaufenen Verbundzertifikats durch.

Weitere Informationen zu Verbundvertrauensstellungen sowie zum Thema Verbund finden Sie unter [Verbund](federation-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter Abschnitt „Verbund- und Zertifikatberechtigungen“ im Artikel [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - In den in diesem Artikel beschriebenen Verfahren wird die Exchange-Verwaltungsshell verwendet. Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).

  - Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um herauszufinden, ob Ihr aktuelles Verbundzertifikat abgelaufen ist:
    
        Get-ExchangeCertificate -Thumbprint (Get-FederationTrust).OrgCertificate.Thumbprint | Format-Table -Auto Thumbprint,NotAfter

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Aktualisieren eines funktionierenden Verbundzertifikats

Wenn das Verbundzertifikat noch nicht abgelaufen ist, können Sie die vorhandene Verbundvertrauensstellung mit einem neuen Verbundzertifikat aktualisieren.

## Schritt 1: Erstellen eines neuen Verbundzertifikats

Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um ein neues Verbundzertifikat zu erstellen:

    $SKI = [System.Guid]::NewGuid().ToString("N"); New-ExchangeCertificate -DomainName 'Federation' -FriendlyName "Exchange Delegation Federation" -Services Federation -SubjectKeyIdentifier $SKI -PrivateKeyExportable $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ExchangeCertificate](https://technet.microsoft.com/de-de/library/aa998327\(v=exchg.150\)).

Die Ausgabe des Befehls enthält den Fingerabdruckwert des neuen Zertifikats. Sie benötigen diesen Wert in den übrigen Schritten und können ihn direkt aus dem Fenster der Exchange-Verwaltungsshell kopieren:

1.  Klicken Sie an einer beliebigen Stelle im Fenster der Exchange-Verwaltungsshell mit der rechten Maustaste, und wählen Sie im dann angezeigten Dialogfeld **Markieren** aus.

2.  Wählen Sie den Fingerabdruckwert aus, und drücken Sie die EINGABETASTE.

Für die weiteren Verfahren in diesem Artikel verwenden wir den Verbundzertifikat-Fingerabdruckwert `6A99CED2E4F2B5BE96C5D17D662D217EF58B8F73`. Der Fingerabdruckwert Ihres Zertifikats wird ein anderer sein.

## Schritt 2: Konfigurieren des neuen Zertifikats als Verbundzertifikat

Verwenden Sie die folgende Syntax, um das neue Zertifikat mithilfe der Exchange-Verwaltungsshell als Verbundzertifikat zu konfigurieren:

    Set-FederationTrust -Identity "Microsoft Federation Gateway" -Thumbprint <Thumbprint> -RefreshMetaData

In diesem Beispiel wird der Zertifikat-Fingerabdruckwert `6A99CED2E4F2B5BE96C5D17D662D217EF58B8F73` aus Schritt 1 verwendet.

    Set-FederationTrust -Identity "Microsoft Federation Gateway" -Thumbprint 6A99CED2E4F2B5BE96C5D17D662D217EF58B8F73 -RefreshMetaData

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-FederationTrust](https://technet.microsoft.com/de-de/library/dd298034\(v=exchg.150\)).

**Hinweis:**  Die Ausgabe des Befehls enthält eine Warnung, dass Sie den als Nachweis des Domänenbesitzes im DNS hinterlegten TXT-Eintrag aktualisieren müssen. Das erledigen Sie im nächsten Schritt.

## Schritt 3: Aktualisieren des als Nachweis des Domänenbesitzes im externen DNS hinterlegten Verbund-TXT-Eintrags

Diesen Schritt können Sie bedenkenlos zu diesem Zeitpunkt durchführen, da der als Nachweis des Domänenbesitzes dienende TXT-Eintrag nur während der Aktivierung überprüft wird (Schritt 5). Nachdem Sie den TXT-Eintrag aktualisiert haben, müssen Sie jedoch eine Weile warten, bis der aktualisierte TXT-Eintrag verteilt wurde, bevor Sie mit dem nächsten Schritt fortfahren. (Die Wartezeit hängt von dem Gültigkeitsdauerwert \[TTL-Wert\] des DNS-Eintrags ab.)

1.  Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um die erforderlichen Werte des erforderlichen TXT-Eintrags abzurufen:
    
    ```powershell
Get-FederatedDomainProof -DomainName <Domain> | Format-List Thumbprint,Proof
```
    
    Ist Ihre Verbunddomäne „contoso.com“, würden Sie beispielsweise den folgenden Befehl ausführen:
    
    ```powershell
Get-FederatedDomainProof -DomainName contoso.com | Format-List Thumbprint,Proof
```
    
    Die Ausgabe des Befehls sieht wie folgt aus:
    
    `Thumbprint : <new certificate thumbprint>` (zum Beispiel `6A99CED2E4F2B5BE96C5D17D662D217EF58B8F73`)
    
    `Proof      : <new hash text>` (zum Beispiel `znMfbkgSbOQSsWFdsW+gm3to0nZSdE3zbcPPHGVAqdgsLFGsCPuLHiyVbKoPmgyZKX90NH2g1PbCZH0YTQF6oA==`)
    
    `Thumbprint : <old certificate thumbprint>` (zum Beispiel `CC9BC204BB4DC60D06FC1F10F3C373DC785DA2A5`)
    
    `Proof      : <old hash text>` (zum Beispiel `m4gZX7OLr9iOWYJMVjEklQpoSkPb5hSbcFjD7Q3/vsqmdJ2Z+HcSt7j5pzBKFmEW2s27JYr3xsK2POzAI/8Ffw==`)
    
    Beachten Sie, dass die Ausgabe des Befehls Informationen zu zwei als Nachweis des Domänenbesitzes dienenden Einträgen zurückgibt: einem Eintrag für das neue Zertifikat und einem Eintrag für das aktuelle Zertifikat, das ersetzt werden soll. Sie können die beiden Einträge anhand des Fingerabdruckwerts und des Hashtextwerts unterscheiden, der im TXT-Eintrag konfiguriert ist, der aktuell als Nachweis des Domänenbesitzes im externen (öffentlichen) DNS hinterlegt ist.

2.  Aktualisieren Sie den als Nachweis des Domänenbesitzes in Ihrem externen DNS hinterlegten Verbund-TXT-Eintrag. Wie das geht, variiert je nach DNS-Anbieter, Sie können jedoch den aktuellen Hashtextwert im aktuellen TXT-Eintrag durch den neuen Hashtextwert ersetzen. Weitere Informationen finden Sie im Abschnitt zu Exchange Online im Artikel [Externe DNS-Einträge für Office 365](https://go.microsoft.com/fwlink/p/?linkid=26552).

## Schritt 4: Überprüfen der erfolgreichen Verteilung des Verbundzertifikats an alle Exchange-Server

Exchange verteilt das neue Verbundzertifikat automatisch an alle Server. Sie müssen aber dennoch überprüfen, ob die Verteilung erfolgreich war, bevor Sie fortfahren.

Führen Sie den folgenden Befehl aus, um mithilfe der Exchange-Verwaltungsshell zu überprüfen, ob das neue Verbundzertifikat verteilt wurde:

    $Servers = Get-ExchangeServer; $Servers | foreach {Get-ExchangeCertificate -Server $_ | Where {$_.Services -match 'Federation'}} | Format-List Identity,Thumbprint,Services,Subject

**Hinweis:**  In Exchange 2010 enthält die Ausgabe des Cmdlets **Test-FederationCertificate** Servernamen. In Exchange 2013 oder höher enthält die Ausgabe des Cmdlets keine Servernamen.

## Schritt 5: Aktivieren des neuen Verbundzertifikats

Führen Sie den folgenden Befehl aus, um das neue Verbundzertifikat mithilfe der Exchange-Verwaltungsshell zu aktivieren:

```powershell
Set-FederationTrust -Identity "Microsoft Federation Gateway" -PublishFederationCertificate
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-FederationTrust](https://technet.microsoft.com/de-de/library/dd298034\(v=exchg.150\)).

**Hinweis:**  Die Ausgabe des Befehls enthält eine Warnung, dass Sie den als Nachweis des Domänenbesitzes im DNS hinterlegten TXT-Eintrag aktualisieren müssen. (Das haben Sie in Schritt 3 bereits getan.)

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob die vorhandene Verbundvertrauensstellung erfolgreich mit einem neuen Verbundzertifikat aktualisiert wurde:

  - Führen Sie in der Exchange-Verwaltungsshell den folgenden Befehl aus, um zu überprüfen, ob das neue Zertifikat verwendet wird:
    
        Get-FederationTrust | Format-List *priv*
    
      - Die Eigenschaft **OrgPrivCertificate** sollte den Fingerabdruck des neuen Verbundzertifikats enthalten.
    
      - Die Eigenschaft **OrgPrevPrivCertificate** sollte den Fingerabdruck des alten (ersetzten) Verbundzertifikats enthalten.

  - Ersetzen Sie in der Exchange-Verwaltungsshell*\<user's email address\>* durch die E-Mail-Adresse eines Benutzers in Ihrer Organisation, und überprüfen Sie mit dem folgenden Befehl, ob die Verbundvertrauensstellung funktioniert:
    
    ```powershell
Test-FederationTrust -UserIdentity <user's email address>
```

## Ersetzen eines abgelaufenen Verbundzertifikats

Wenn das Verbundzertifikat bereits abgelaufen ist, müssen Sie zunächst alle Verbunddomänen aus der Verbundvertrauensstellung entfernen und anschließend die Verbundvertrauensstellung entfernen und neu erstellen.

1.  Wenn Sie mehrere Verbunddomänen haben, müssen Sie die primäre freigegebenen Domäne identifizieren; sie muss zuletzt entfernt werden. Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um die primäre freigegebene Domäne und alle Verbunddomänen zu identifizieren:
    
    ```powershell
Get-FederatedOrganizationIdentifier | Format-List AccountNamespace,Domains
```
    
    Der Wert der Eigenschaft **AccountNamespace** enthält die primäre freigegebene Domäne im Format `FYDIBOHF25SPDLT<primary shared domain>`. Beispiel: Im Wert `FYDIBOHF25SPDLT.contoso.com` ist „contoso.com“ die primäre freigegebene Domäne.

2.  Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um alle Verbunddomänen außer der primären freigegebenen Domäne zu entfernen:
    
    ```powershell
Remove-FederatedDomain -DomainName <domain> -Force
```

3.  Sobald Sie alle übrigen Verbunddomänen entfernt haben, führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um die primäre freigegebene Domäne zu entfernen:
    
    ```powershell
Remove-FederatedDomain -DomainName <domain> -Force
```

4.  Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um die Verbundvertrauensstellung zu entfernen:
    
    ```powershell
Remove-FederationTrust "Microsoft Federation Gateway"
```

5.  Erstellen Sie die Verbundvertrauensstellung neu. Eine entsprechende Anleitung finden Sie unter [Erstellen einer Verbundvertrauensstellung](https://technet.microsoft.com/de-de/library/dd335198\(v=exchg.150\)).


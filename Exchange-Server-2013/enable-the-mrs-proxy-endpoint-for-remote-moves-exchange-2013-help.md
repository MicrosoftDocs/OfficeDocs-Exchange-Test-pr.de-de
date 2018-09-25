---
title: 'Aktiv. d. Proxyendp. f. Postf.repl.dienst f. Rem.versch.: Exchange 2013-Hilfe'
TOCTitle: Aktivieren des Proxyendpunkts für den Postfachreplikationsdienst für Remoteverschiebungen
ms:assetid: 9840f712-127e-4c2d-bfe5-1b35cdb2a31b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn155787(v=EXCHG.150)
ms:contentKeyID: 54652698
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren des Proxyendpunkts für den Postfachreplikationsdienst für Remoteverschiebungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-07-02_

Der Proxy für den Postfachreplikationsdienst (Mailbox Replication Service Proxy, MRS-Proxy) unterstützt gesamtstrukturübergreifende Postfachverschiebungen und Remoteverschiebungsmigrationen zwischen der lokalen Exchange-Organisation und Exchange Online. In Exchange 2013 ist der MRS-Proxy in der Postfachserverrolle (auch als *Postfachserver* bezeichnet) enthalten. Bei gesamtstrukturübergreifenden und Remoteverschiebungsmigrationen dient ein Clientzugriffsserver als Proxy für eingehende Verschiebungsanforderungen für den Postfachserver. Die Fähigkeit eines Clientzugriffsservers zur Annahme dieser Anforderungen ist standardmäßig deaktiviert. Um dem Clientzugriffsserver die Annahme eingehender Verschiebungsanforderungen zu ermöglichen, müssen Sie den MRS-Proxyendpunkt aktivieren.

Auf welchem Clientzugriffsserver der MRS-Proxyendpunkt aktiviert werden muss, hängt vom Typ und der Richtung der Postfachverschiebung ab.

  - **Gesamtstrukturübergreifende Unternehmensverschiebungen**   Für gesamtstrukturübergreifende Verschiebungen, die in der Zielumgebung initiiert wurden (auch als Verschiebungstyp *Pull* bezeichnet), müssen Sie den MRS-Proxyendpunkt auf Clientzugriffsservern in der Quellumgebung aktivieren. Für gesamtstrukturübergreifende Verschiebungen, die in der Quellumgebung initiiert wurden (auch als Verschiebungstyp *Push* bezeichnet), müssen Sie den MRS-Proxyendpunkt auf Clientzugriffsservern in der Zielumgebung aktivieren.

  - **Remoteverschiebungsmigrationen zwischen einer lokalen Exchange-Organisation und Exchange Online**   Für Onboarding- und Offboarding-Remoteverschiebungsmigrationen müssen Sie den MRS-Proxyendpunkt auf Clientzugriffsservern in der lokalen Organisation aktivieren.


> [!NOTE]
> Wenn Sie Postfächer mithilfe der Exchange-Verwaltungskonsole verschieben, stellen gesamtstrukturübergreifende Verschiebungen und Onboarding-Remoteverschiebungsmigrationen Pull-Verschiebungen dar, da die Anforderung in der Zielumgebung initiiert wird. Offboarding-Remoteverschiebungsmigrationen stellen Push-Verschiebungen dar, da die Anforderung in der Quellumgebung initiiert wird.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten pro Server.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für Exchange-Webdienste" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Wenn Sie mehrere Clientzugriffsserver in Ihrer Exchange-Organisation bereitgestellt haben, sollten Sie den MRS-Proxyendpunkt auf allen aktivieren. Wenn Sie weitere Clientzugriffsserver hinzufügen, müssen Sie den MRS-Proxyendpunkt auf den neuen Servern ebenfalls aktivieren. Bei gesamtstrukturübergreifenden Verschiebungen und Remoteverschiebungsmigrationen können Fehler auftreten, wenn der MRS-Proxyendpunkt nicht auf allen Clientzugriffsservern aktiviert ist.

  - Wenn Sie keine gesamtstrukturübergreifenden Verschiebungen oder Remoteverschiebungsmigrationen ausführen, sollten Sie die MRS-Proxyendpunkte deaktiviert lassen, um die Angriffsfläche Ihrer Organisation zu verringern.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren des MRS-Proxyendpunkts mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Server** \> **Virtuelle Verzeichnisse**.

2.  Wählen Sie in der Dropdownliste **Server auswählen** den Namen des Clientzugriffsservers aus, auf dem Sie den MRS-Proxyendpunkt aktivieren möchten. Oder wählen Sie **Alle Server** aus, um die virtuellen Verzeichnisse auf allen Clientzugriffsservern in der Organisation anzuzeigen.

3.  Wählen Sie in der Dropdownliste **Typ auswählen** den Eintrag **EWS** aus, um das virtuelle Verzeichnis des Exchange-Webdiensts (EWS) für den ausgewählten Server anzuzeigen.

4.  Klicken Sie in der Liste der virtuellen Verzeichnisse auf **EWS (Standardwebsite)** für den Clientzugriffsserver, den Sie konfigurieren möchten. Klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

5.  Aktivieren Sie auf der Eigenschaftenseite von **EWS (Standardwebsite)** das Kontrollkästchen **MRS-Proxy aktiviert**, und klicken Sie dann auf **Speichern**.

## Aktivieren des MRS-Proxyendpunkts mithilfe der Shell

Der folgende Befehl aktiviert den MRS-Proxyendpunkt auf einem Clientzugriffsserver mit dem Namen EXCH-SRV-01.
```powershell
    Set-WebServicesVirtualDirectory -Identity "EXCH-SRV-01\EWS (Default Web Site)" -MRSProxyEnabled $true
```

Der folgende Befehl aktiviert den MRS-Proxyendpunkt auf allen Clientzugriffsservern in der Exchange-Organisation.

```powershell
Get-WebServicesVirtualDirectory | Set-WebServicesVirtualDirectory -MRSProxyEnabled $true
```


> [!IMPORTANT]
> Wie bereits erwähnt, sollte der MRS-Proxyendpunkt auf jedem Clientzugriffsserver in Ihrer Organisation aktiviert werden. Führen Sie den vorherigen Befehl nach dem Hinzufügen eines neuen Clientzugriffsservers in der Organisation aus.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um zu überprüfen, ob der MRS-Proxyendpunkt erfolgreich aktiviert wurde:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Server** \> **Virtuelle Verzeichnisse**.

2.  Klicken Sie in der Liste der virtuellen Verzeichnisse auf **EWS (Standardwebsite)**, und überprüfen Sie im Detailbereich, ob der MRS-Proxyendpunkt aktiviert ist.
    
    Alternativ können Sie auch auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol") klicken, um die Eigenschaftenseite von **EWS (Standardwebsite)** anzuzeigen, und überprüfen, ob das Kontrollkästchen **MRS-Proxy aktiviert** aktiviert ist.

– oder –

Führen Sie in der Shell den folgenden Befehl aus:

```powershell
Get-WebServicesVirtualDirectory | FL Identity,MRSProxyEnabled
```

Überprüfen Sie, ob der Parameter *MRSProxyEnabled* auf `True` festgelegt ist.

Eine andere Möglichkeit, die Aktivierung des MRS-Proxyendpunkts zu überprüfen, besteht in der Verwendung des Cmdlets **Test-MigrationServerAvailability**. Überprüfen Sie hiermit die Kommunikation mit dem Remoteserver, der die zu verschiebenden Postfächer hostet, bzw. beim Offboarding von Exchange Online-Postfächern in Ihre lokale Organisation mit einem Server in Ihrer lokalen Organisation. Weitere Informationen finden Sie unter [Test-MigrationServerAvailability](https://technet.microsoft.com/de-de/library/jj219169\(v=exchg.150\)).

Im folgenden Beispiel wird die Verbindung mit einem Server in der Gesamtstruktur **corp.contoso.com** getestet.


```powershell
$Credentials = Get-Credential
```
```powershell
Test-MigrationServerAvailability -ExchangeRemoteMove -Autodiscover -EmailAddress administrator@corp.contoso.com -Credentials $Credentials
```

Damit dieser Befehl erfolgreich ausgeführt werden kann, muss der MRS-Proxyendpunkt aktiviert sein.


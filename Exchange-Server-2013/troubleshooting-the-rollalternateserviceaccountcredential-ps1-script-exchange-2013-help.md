---
title: 'Problembehandlung für das Skript "RollAlternateServiceAccountCredential.ps1": Exchange 2013 Help'
TOCTitle: Problembehandlung für das Skript "RollAlternateServiceAccountCredential.ps1"
ms:assetid: 2bbf36d3-eb89-4f92-a8de-259a7cb64d62
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff808310(v=EXCHG.150)
ms:contentKeyID: 63915381
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Problembehandlung für das Skript \"RollAlternateServiceAccountCredential.ps1\"

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-01-14_

In diesem Thema werden Lösungen und Informationen zu häufigen Fehlern bereitgestellt, die bei der Verwendung des Skripts "RollAlternateServiceAccountPassword.ps1" auftreten können.

## Auf mindestens einem Clientzugriffsserver kann das Kennwort nicht aktualisiert werden

## Problem

Bei Verwendung des Parameters *ToEntireForest* oder *ToArrayMembers* mit dem Skript wird in einigen Fällen mindestens ein Clientzugriffsserver nicht aktualisiert.

## Lösung

Überprüfen Sie mit dem Cmdlet **Get-ClientAccessArray**, ob das Skript sich auf alle erforderlichen Server bezieht, wie im folgenden Beispiel gezeigt.

    Get-ClientAccessArray | fl members

Wenn der Server, der nicht aktualisiert wird, Mitglied des Clientzugriffsserver-Arrays ist und dennoch weiterhin nicht ordnungsgemäß aktualisiert wird, führen Sie Exchange-Setup erneut aus, und fügen Sie dem Server erneut die Clientzugriffs-Serverrolle hinzu. Sie können auch mit dem Parameter *ToSpecificServers* einzelne Server als Ziel angeben.

## Einige Server reagieren nicht auf das Skript

## Problem

Unter einigen Umständen werden Server möglicherweise aufgrund vorübergehender Fehler, z. B. einer unzureichenden Netzwerkverbindung, nicht aktualisiert.

## Auflösung

Überprüfen Sie, ob die betreffenden Server über eine Netzwerkverbindung und Active Directory-Verbindung verfügen, und führen Sie das Skript erneut aus.

## Einige Arraymitglieder sind längere Zeit außer Betrieb

## Problem

Wenn ein Server längere Zeit außer Betrieb, aber weiterhin Mitglied des Arrays ist, wie vom **Get-ClientAccessArray cmdlet** festgelegt, beeinträchtigt dies bei Verwendung der Parameter *ToArrayMembers* und *ToEntireForest* möglicherweise das Ausführen des Skripts. Dasselbe Problem tritt auf, wenn ein Server permanent ausfällt, aber nicht sauber aus der Bereitstellung entfernt wurde.

## Auflösung

Entfernen Sie den Server mithilfe von Exchange-Setup aus der Bereitstellung, oder führen Sie das Skript im beaufsichtigten Modus aus, bis der Server entfernt werden kann.

Wenn der Server nur für kurze Zeit ausfällt und Sie Exchange nicht dauerhaft entfernen möchten, können Sie mithilfe des Parameters *ToSpecificServers* das Skript so anpassen, dass es für bestimmte Server, beispielsweise nur aktive Server, ausgeführt wird. Sie können auch den RPC-Clientzugriffsdienst vom Active Directory-Objekt des nicht reagierenden Servers entfernen. Verwenden Sie dazu das Cmdlet **Remove-ClientAccessArray**, wie im folgenden Beispiel gezeigt wird.

    Remove-RPCClientAccess -Server Server.Contoso.com

Nach dem Entfernen des RPC-Clientzugriffsdiensts wird der Server von [Get-ClientAccessArray](https://technet.microsoft.com/de-de/library/dd297976\(v=exchg.150\)) nicht mehr als Arraymitglied zurückgegeben, und das Skript bezieht sich nicht mehr auf ihn. Sobald der Server wieder funktionsfähig ist, können Sie den RPC-Clientzugriffsdienst mit dem Cmdlet **New-RpcClientAccess** wieder hinzufügen. Nach dem erneuten Hinzufügen des RPC-Clientzugriffsdiensts müssen Sie den Microsoft Exchange-Adressbuchdienst auf dem betroffenen Server neu starten.


> [!WARNING]
> Lesen Sie vor dem Entfernen des RPC-Clientzugriffsdiensts von einem Server das Thema <A href="https://technet.microsoft.com/de-de/library/dd298151(v=exchg.150)">Remove-RPCClientAccess</A>.



## Weitere Informationen

Weitere Informationen zur Verwendung der Kerberos-Authentifizierung mit einem Clientzugriffsserver-Array oder einer Lastenausgleichslösung finden Sie in den folgenden Themen:

  - [Konfigurieren der Kerberos-Authentifizierung für Clientzugriffsserver mit Lastenausgleich](configuring-kerberos-authentication-for-load-balanced-client-access-servers-exchange-2013-help.md)

  - [Verwenden des Skripts "RollAlternateserviceAccountCredential.ps1" in der Shell](using-the-rollalternateserviceaccountcredential-ps1-script-in-the-shell-exchange-2013-help.md)


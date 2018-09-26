---
title: 'Konfig. eines gesamtstrukturübergreif. Sendeconnectors: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren eines gesamtstrukturübergreifenden Sendeconnectors
ms:assetid: 7840d172-071e-4f13-9379-2fe1eee1a7cc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ945053(v=EXCHG.150)
ms:contentKeyID: 52062867
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren eines gesamtstrukturübergreifenden Sendeconnectors

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

In Active Directory stellt die *Gesamtstruktur* die äußere Begrenzung Ihres Verzeichnisdiensts dar. Sie können Sendeconnectors zum Aktivieren der Kommunikation zwischen Gesamtstrukturen erstellen. In diesem Beispiel verwenden die Connectors die Standardauthentifizierung.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit der Konfiguration von Connectors finden Sie unter [Connectors](connectors-exchange-2013-help.md).

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Bereitstellen von Exchange 2013 in einer gesamtstrukturübergreifenden Topologie](deploy-exchange-2013-in-a-cross-forest-topology-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 20 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Sendeconnectors" und "Empfangsconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Weitere Informationen finden Sie unter [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md), wenn Sie Ihre Installation starten. Nach der Installation können Sie die Schritte in diesem Thema ausführen, um Connectors zum Konfigurieren einer gesamtstrukturübergreifenden Topologie zu erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen eines Benutzerkontos in jeder Gesamtstruktur

Sie müssen in jeder Gesamtstruktur ein Benutzerkonto für die Verwendung der Standardauthentifizierung erstellen. Erstellen Sie in jeder Gesamtstruktur ein Konto, und fügen Sie die Konten der universellen Sicherheitsgruppe des Exchange-Servers hinzu, der für die Kommunikation verwendet wird. Dieses Konto wird vom Sendeconnector für die Authentifizierung beim Server verwendet, der E-Mail in der anderen Gesamtstruktur empfängt. Geben Sie zum Beispiel ein Benutzerkonto mit dem Benutzerprinzipalnamen (Universal Principal Name, UPN) "FourthCoffee@Contoso.com" als Anmeldeinformationen an, die für die Authentifizierung durch den Exchange-Server in der Domäne "Fourth Coffee" verwendet werden sollen, wenn E-Mails an den Exchange-Server in der Domäne "Contoso" gesendet werden.

## Erstellen eines Sendeconnectors zum Weiterleiten von E-Mail an eine andere Exchange 2013-Gesamtstruktur mithilfe der Exchange-Verwaltungskonsole

Richten Sie die gesamtstrukturübergreifende Nachrichtenübermittlung unter Verwendung der Standardauthentifizierung ein.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Sendeconnectors**. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im **Assistenten für neue Sendeconnectors** einen Namen für den Sendeconnector an, und wählen Sie für **Typ** die Option **Intern**. Klicken Sie auf **Weiter**.

3.  Wählen Sie **E-Mail über Smarthosts weiterleiten** aus, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Geben Sie im Fenster **Smarthost hinzufügen** die IP-Adresse des Zielservers in der zweiten Gesamtstruktur ein, z. B. 64.4.6.100. Klicken Sie auf **Speichern** und dann auf **Weiter**.
    
    Wählen Sie für **Smarthostauthentifizierung** die Option **Standardauthentifizierung**, und geben Sie einen Benutzernamen und ein Kennwort an. Hier können Sie **Standardauthentifizierung nur nach dem Starten von TLS anbieten** für eine sichere Kommunikation über TLS wählen.
    

    > [!NOTE]
    > Wenn Sie die Standardauthentifizierung über TLS verwenden, muss der Zielserver für die Verwendung eines X.509-Zertifikats konfiguriert sein.



4.  Klicken Sie unter **Adressbereich** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Stellen Sie im Fenster **Domäne hinzufügen** sicher, dass SMTP als **Typ** aufgelistet ist. Geben Sie für **Vollqualifizierter Domänenname (FQDN)** die empfangende Domäne ein, z. B. "fourthcoffee.com". Klicken Sie erst auf **Speichern** und dann auf **Weiter**.

5.  Klicken Sie für **Quellserver** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wählen Sie im Fenster **Server auswählen** den gewünschten Server aus, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Klicken Sie auf **OK**.

6.  Klicken Sie auf **Fertig stellen**. Der Connector wird in der Liste der Sendeconnectors angezeigt.

Nachdem Sie Ihren Sendeconnector erstellt haben, erstellen Sie einen Sendeconnector in der zweiten Gesamtstruktur, der E-Mail an die ursprüngliche Gesamtstruktur sendet. In diesem Fall ist der angegebene FQDN der Domänenname der ersten Gesamtstruktur. Beispiel: "contoso.com".

## Verwenden der Shell zum Festlegen von Berechtigungen für den Sendeconnector

In diesem Beispiel wird das Skript "Enable-CrossForestConnector.ps1" in der Shell verwendet, um Berechtigungen für den Sendeconnector für den Einsatz in einer gesamtstrukturübergreifenden Topologie festzulegen.

```powershell
    .\Enable-CrossForestConnector.ps1 -Connector "Cross-Forest" -user "ANONYMOUS LOGON"
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Senden Sie eine Nachricht von einem Benutzer in Ihrer Organisation (Sie können Outlook Web App verwenden) an die Domäne, die Sie unter **Adressraum** eingegeben haben, um die erfolgreiche Erstellung eines Sendeconnectors zum Weiterleiten von E-Mail an eine zweite Gesamtstruktur zu überprüfen. Wenn der Empfänger die Nachricht erhält, haben Sie den Sendeconnector erfolgreich erstellt.

## Weitere Informationen

[Erstellen eines Sendeconnectors für E-Mails, die über das Internet gesendet werden](create-a-send-connector-for-email-sent-to-the-internet-exchange-2013-help.md)

[Sendeconnectors](send-connectors-exchange-2013-help.md)


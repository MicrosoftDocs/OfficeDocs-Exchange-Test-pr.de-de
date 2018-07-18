---
title: 'Vereinfachen der Outlook Web App-URL: Exchange 2013 Help'
TOCTitle: Vereinfachen der Outlook Web App-URL
ms:assetid: 5fb6a873-f3cf-4f82-87d1-2ff6e47a0080
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998359(v=EXCHG.150)
ms:contentKeyID: 54652688
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Vereinfachen der Outlook Web App-URL

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-07-16_

**Zusammenfassung:**  Verwenden Sie die Verfahren in diesem Artikel, um die URL zu vereinfachen, über die Benutzer in ihrer Organisation auf OWA in Exchange 2013 zugreifen.

Sie können die MicrosoftOutlook Web App-URL vereinfachen, über die Benutzer auf ihre Exchange Server 2013-Postfächer zugreifen.

Damit der Zugriff auf Outlook Web App für Benutzer vereinfacht wird, können Sie die Outlook Web App-Webseite, die normalerweise die Standardwebsite in IIS ist, so konfigurieren, dass Benutzer automatisch zu "https" umgeleitet werden. Das Verfahren aus dem Abschnitt "Verwenden des IIS-Managers zum Vereinfachen der Outlook Web App-URL und Erzwingen der Weiterleitung zu SSL" leitet eine Anforderung für http://*server* an https://*server*/owa um. Zur Unterstützung der Sicherheit der zwischen dem Client und dem Server gesendeten Informationen wird für die Standardwebsite zum Installationszeitpunkt festgelegt, dass SSL (Secure Sockets Layer) erforderlich ist.

Wenn Sie die Umleitung in einem Verzeichnis der obersten Ebene in Windows Server 2008 konfigurieren, werden die Einstellungen an Verzeichnisse der unteren Ebenen weitergegeben. Wenn Sie z. B. auf der Standardwebsite die Umleitung zum virtuellen Verzeichnis "/owa" konfigurieren, werden die von Ihnen konfigurierten Einstellungen auch auf der Seite "HTTP-Umleitung" aller virtuellen Verzeichnisse angezeigt, z. B. "/Autodiscover", "/Exchange" und "/Public". Deshalb müssen Sie die Umleitung von allen virtuellen Verzeichnissen entfernen, außer von dem, das umgeleitet werden soll.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter-Eintrag "IIS Manager" im Abschnitt "Berechtigungen für Outlook Web App" des [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md)-Themas.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Schritt 1: Verwenden des IIS-Managers zum Vereinfachen der Outlook Web App-URL und Erzwingen der Weiterleitung zu SSL

1.  Starten Sie IIS-Manager.

2.  Erweitern Sie zuerst den lokalen Computer, dann **Sites**, und klicken Sie anschließend auf **Standardwebsite**.

3.  Klicken Sie im unteren Teil der Startseite der Standardwebsite auf **Ansicht "Funktionen"**, wenn diese Option nicht bereits aktiviert ist.

4.  Doppelklicken Sie im Abschnitt **IIS** auf **HTTP-Umleitung**.

5.  Aktivieren Sie das Kontrollkästchen **Anforderungen zu diesem Ziel umleiten**.

6.  Geben Sie den absoluten Pfad zum virtuellen Verzeichnis "/owa" ein. Geben Sie z. B. **https://mail.contoso.com/owa** ein.

7.  Aktivieren Sie unter **Umleitungsverhalten** das Kontrollkästchen **Anforderungen zu Inhalt in diesem Verzeichnis (nicht in Unterverzeichnisse) umleiten**.

8.  Klicken Sie in der Liste **Statuscode** auf **Gefunden (302)**.

9.  Klicken Sie im Aktionsbereich auf **Übernehmen**.

10. Klicken Sie auf **Standardwebsite**.

11. Doppelklicken Sie im Bereich für die Startseite der Standardwebsite auf **SSL-Einstellungen**.

12. Deaktivieren Sie unter **SSL-Einstellungen** die Option **SSL erforderlich**.
    

    > [!NOTE]
    > Wenn Sie die Option <STRONG>SSL erforderlich</STRONG> nicht deaktivieren, werden die Benutzer bei Eingabe einer ungesicherten URL nicht umgeleitet. Stattdessen erhalten sie eine Fehlermeldung des Typs "Zugriff verweigert".



## Schritt 2: Entfernen der Umleitung von allen virtuellen Verzeichnissen

Führen Sie die folgenden Schritte aus, um die Umleitung von einem virtuellen Verzeichnis zu entfernen:

1.  Öffnen Sie ein Eingabeaufforderungsfenster.

2.  Wechseln Sie in das Verzeichnis "\<*Windows-Verzeichnis*\>\\System32\\Inetsrv".

3.  Führen Sie die folgenden Befehle aus:
    
    1.  `appcmd set config "Default Web Site/autodiscover" /section:httpredirect /enabled:false -commit:apphost`
    
    2.  `appcmd set config "Default Web Site/ecp" /section:httpredirect /enabled:false -commit:apphost`
    
    3.  `appcmd set config "Default Web Site/ews" /section:httpredirect /enabled:false -commit:apphost`
    
    4.  `appcmd set config "Default Web Site/owa" /section:httpredirect /enabled:false -commit:apphost`
    
    5.  `appcmd set config "Default Web Site/oab" /section:httpredirect /enabled:false -commit:apphost`
    
    6.  `appcmd set config "Default Web Site/powershell" /section:httpredirect /enabled:false -commit:apphost`
    
    7.  `appcmd set config "Default Web Site/rpc" /section:httpredirect /enabled:false -commit:apphost`
    
    8.  `appcmd set config "Default Web Site/rpcwithcert" /section:httpredirect /enabled:false -commit:apphost`
    
    9.  `appcmd set config "Default Web Site/Microsoft-Server-ActiveSync" /section:httpredirect /enabled:false -commit:apphost`

4.  Führen Sie abschließend den Befehl `iisreset/noforce` aus.

Bei der Konfiguration der Umleitung in einem Verzeichnis der obersten Ebene wird möglicherweise eine Web.config-Datei unter \<*Laufwerk*\>\\Programme\\Microsoft\\Exchange Server\\\<*Version*\>\\ClientAccess\\oab erstellt. Ist dies der Fall, und Sie möchten die Umleitung zu einem späteren Zeitpunkt entfernen, reagiert Outlook möglicherweise nicht mehr, sobald Benutzer auf **Senden und empfangen** klicken. Sie können dieses Verhalten nach dem Entfernen der Umleitung vermeiden, indem Sie die Datei "Web.config" aus dem Verzeichnis \<*Laufwerk*\>\\Programme\\Microsoft\\Exchange Server\\\<*Version*\>\\ClientAccess\\oab löschen.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Für eine Überprüfung, ob die Outlook Web App-URL erfolgreich vereinfacht werden und an SSL weitergeleitet werden konnte, gehen Sie wie folgt vor:

1.  Öffnen Sie einen Webbrowser, und geben Sie die neue URL für Outlook Web App im Format http://\<*URL*\> ein.

2.  Sie werden über eine SSL-Verbindung zur Outlook Web App-Anmeldeseite weitergeleitet.


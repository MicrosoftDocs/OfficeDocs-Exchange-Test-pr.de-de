---
title: 'Installieren der Exchange 2013-Verwaltungstools: Exchange 2013 Help'
TOCTitle: Installieren der Exchange 2013-Verwaltungstools
ms:assetid: 71fcbe4c-783b-4f77-aabb-a21aa7a4ef23
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232090(v=EXCHG.150)
ms:contentKeyID: 50554841
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Installieren der Exchange 2013-Verwaltungstools

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-01-28_

Mithilfe der Microsoft Exchange Server 2013-Verwaltungstools können Sie Ihre Exchange-Organisation remote verwalten. Zu den Exchange 2013-Verwaltungstools zählen die Exchange-Verwaltungshell und die Exchange Toolbox. In diesem Thema wird erläutert, wie Sie entweder Setup.exe oder den unbeaufsichtigten Installationsmodus zur Installation der Exchange 2013-Verwaltungstools verwenden können.


> [!NOTE]
> Dieses Verfahren ist nicht erforderlich, um die Exchange-Verwaltungskonsole remote zu nutzen. Die Exchange-Verwaltungskonsole ist eine webbasierte Konsole, die auf Computern mit der Exchange 2013-Clientzugriffsserver-Rolle gehostet wird. Weitere Informationen zum Remotezugriff auf die Exchange-Verwaltungskonsole finden Sie unter <A href="exchange-admin-center-in-exchange-2013-exchange-2013-help.md">Exchange Admin Center in Exchange 2013</A>.



Weitere Informationen zum Verwalten von Exchange 2013 finden Sie unter [Exchange Admin Center in Exchange 2013](exchange-admin-center-in-exchange-2013-exchange-2013-help.md) und [Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten

  - Lesen Sie vor der Installation von Exchange 2013 in jedem Fall die Versionshinweise. Weitere Informationen finden Sie unter [Versionshinweise zu Exchange 2013](release-notes-for-exchange-2013-exchange-2013-help.md).

  - Der Computer, auf dem Sie die Verwaltungstools installieren, muss ein unterstütztes Betriebssystem (z. B. Windows Server 2012 oder Windows 8) und ausreichend Speicherplatz aufweisen, Mitglied einer Active Directory-Domäne sein und weitere Anforderungen erfüllen. Weitere Informationen zu den Systemanforderungen finden Sie unter [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md).

  - Zur Ausführung des Exchange 2013-Setups müssen Microsoft .NET Framework 4.5, Windows Management Framework 3.0 und weitere erforderliche Softwarekomponenten installiert sein. Informationen zu den Voraussetzungen für alle Serverrollen finden Sie unter [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden von Setup zum Installieren der Exchange 2013-Verwaltungstools

1.  Melden Sie sich an dem Computer an, auf dem Exchange 2013 installiert werden soll.

2.  Navigieren Sie zum Netzwerkspeicherort der Exchange 2013-Installationsdateien.

3.  Starten von Exchange 2013-Setup durch Doppelklicken auf `Setup.exe`
    

    > [!IMPORTANT]
    > Wenn die Benutzerzugriffssteuerung aktiviert ist, klicken Sie mit der rechten Maustaste auf <CODE>Setup.exe</CODE>, und wählen Sie <STRONG>Als Administrator ausführen</STRONG> aus.



4.  Legen Sie auf der Seite **Soll nach Updates gesucht werden?** fest, ob eine Verbindung mit dem Internet hergestellt werden soll und Produkt- und Sicherheitsupdates für Exchange 2013 heruntergeladen werden sollen. Wenn Sie **Verbindung mit dem Internet herstellen und nach Updates suchen** auswählen, werden Updates heruntergeladen und angewendet, bevor der Vorgang fortgesetzt wird. Wenn Sie die Option **Jetzt nicht nach Updates suchen** auswählen, können Sie die Updates später manuell herunterladen und installieren. Wir empfehlen, die Updates jetzt herunterzuladen und zu installieren. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

5.  Die Installation von Exchange in Ihrer Organisation beginnt mit der Seite **Einführung**. Sie werden durch die Installation geleitet. Es werden mehrere Links zu hilfreichem Inhalt zu Bereitstellungen aufgelistet. Es wird empfohlen, dass Sie diese Links aufrufen, bevor Sie Setup fortsetzen. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

6.  Lesen Sie die auf der Seite **Lizenzvertrag** angezeigten Lizenzbedingungen für die Software. Wenn Sie den Bedingungen zustimmen, wählen Sie **Ich stimme den Bedingungen des Lizenzvertrags zu**, und klicken Sie auf **Weiter**.

7.  Legen Sie auf der Seite **Empfohlene Einstellungen** fest, ob die empfohlenen Einstellungen verwendet werden sollen. Wenn Sie **Empfohlene Einstellungen verwenden** auswählen, werden automatisch Fehlerberichte und Informationen zu Ihrer Computerhardware sowie zur Verwendung von Exchange an Microsoft gesendet. Wenn Sie **Empfohlene Einstellungen nicht verwenden** auswählen, bleiben diese Einstellungen deaktiviert; Sie können sie jedoch jederzeit nach Abschluss von Setup aktivieren. Weitere Informationen zu diesen Einstellungen und dazu, wie an Microsoft gesendete Informationen verwendet werden, erhalten Sie durch Klicken auf **?**.

8.  Vergewissern Sie sich auf der Seite **Auswahl von Serverrollen**, dass **Verwaltungstools** ausgewählt ist.
    
    Wählen Sie **Für die Installation von Exchange Server erforderliche Windows Server-Rollen und -Funktionen automatisch installieren** aus, damit alle erforderlichen Windows-Voraussetzungen installiert werden. Möglicherweise müssen Sie den Computer neu starten, um die Installation einiger Windows-Funktionen abzuschließen. Wenn Sie diese Option nicht aktivieren, müssen Sie die Windows-Funktionen manuell installieren.
    

    > [!NOTE]
    > Diese Option installiert nur die Windows-Funktionen, die für Exchange erforderlich sind. Weitere Komponenten zur Erfüllung der Voraussetzungen müssen Sie manuell installieren. Weitere Informationen finden Sie unter <A href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</A>.

    
    Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

9.  Übernehmen Sie auf der Seite **Speicherplatz und Speicherort der Installation** den vorgegebenen Installationspfad, oder klicken Sie auf **Durchsuchen**, um einen anderen Installationspfad auszuwählen. Vergewissern Sie sich, dass der Pfad, unter dem Sie Exchange installieren möchten, ausreichend Speicherplatz aufweist. Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

10. Wenn es sich um die erste Ausführung des Exchange 2013-Setups in Ihrer Organisation handelt, geben Sie auf der Seite **Exchange-Organisation** einen Namen für Ihre Exchange-Organisation ein. Der Name der Exchange-Organisation darf nur die folgenden Zeichen enthalten:
    
      - A bis Z
    
      - a bis z
    
      - 0 bis 9
    
      - Leerzeichen (weder führend noch nachfolgend)
    
      - Bindestrich/Gedankenstrich
        

        > [!NOTE]
        > Der Name der Organisation darf maximal 64 Zeichen enthalten. und er darf nicht leer sein.

    
    Wählen Sie **Sicherheitsmodell mit geteilten Berechtigungen von Active Directory auf die Exchange-Organisation anwenden** aus, wenn Sie das Modell mit geteilten Berechtigungen von Active Directory verwenden möchten.
    

    > [!WARNING]
    > Für die meisten Organisationen ist es nicht erforderlich, das Modell mit geteilten Berechtigungen von Active Directory anzuwenden. Wenn Sie die Verwaltung von Active Directory-Sicherheitsprinzipalen und Exchange-Konfiguration voneinander trennen möchten, können Sie ggf. die geteilten Berechtigungen für die rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC) verwenden. Weitere Informationen erhalten Sie durch Klicken auf <STRONG>?</STRONG>.

    
    Klicken Sie auf **Weiter**, um den Vorgang fortzusetzen.

11. Überprüfen Sie auf der Seite **Abschließende Überprüfung** den Status, um zu ermitteln, ob die Überprüfung der Voraussetzungen für die Organisation und die Serverrollen erfolgreich abgeschlossen wurde. Wenn sie nicht erfolgreich abgeschlossen wurden, müssen Sie gemeldete Fehler beheben, bevor Sie Exchange 2013 installieren können. Sie müssen die Installation beim Beheben dieser Voraussetzungsfehler nicht beenden. Klicken Sie nach dem Beheben eines gemeldeten Fehlers auf **Zurück**, und klicken Sie dann auf **Weiter**, um die Überprüfung der Voraussetzungen erneut auszuführen. Stellen Sie sicher, dass Sie alle Warnungen überprüfen, die gemeldet werden. Wenn alle Überprüfungen der Bereitschaft erfolgreich abgeschlossen wurden, klicken Sie auf **Weiter**, um die Installation von Exchange 2013 zu starten.

12. Klicken Sie auf der Seite **Fertigstellung** auf **Fertig stellen**.

13. Starten Sie den Computer nach Abschluss der Exchange 2013-Installation neu.

## Verwenden des unbeaufsichtigten Installationsmodus zum Installieren der Exchange 2013-Verwaltungstools

1.  Melden Sie sich an dem Computer an, auf dem die Exchange 2013-Verwaltungstools installiert werden sollen.

2.  Navigieren Sie zum Netzwerkspeicherort der Exchange 2013-Installationsdateien.

3.  Führen Sie an der Eingabeaufforderung den folgenden Befehl aus.
    

    > [!IMPORTANT]
    > Wenn die Benutzerkontensteuerung aktiviert ist, müssen Sie <CODE>Setup.exe</CODE> über eine Eingabeaufforderung mit erhöhten Rechten ausführen.

    
    ```powershell
    Setup.exe /Role:ManagementTools /IAcceptExchangeServerLicenseTerms
    ```

Weitere Informationen finden Sie unter [Installieren von Exchange 2013 im unbeaufsichtigten Modus](install-exchange-2013-using-unattended-mode-exchange-2013-help.md).


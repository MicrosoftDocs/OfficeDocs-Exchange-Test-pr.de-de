---
title: 'Einrichtungsfehler bei der Installation einer Serverrolle'
TOCTitle: Einrichtungsfehler bei der Installation einer Serverrolle_InstallWatermark
ms:assetid: ad89ebd5-f9bb-40c1-8811-09b145c2b341
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.installwatermark(v=EXCHG.150)
ms:contentKeyID: 50476461
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Einrichtungsfehler bei der Installation einer Serverrolle\_InstallWatermark

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2007 kann nicht fortgesetzt werden, weil zuvor ein Installationsfehler beim Installieren einer Serverrolle aufgetreten ist.

Das Setup von Exchange 2007 erfordert, dass nach einem Installationsfehler einer Serverrolle diese erfolgreich erneut installiert oder aus dem Installationsvorgang entfernt wird, bevor andere Setuptasks fortgesetzt werden können.

Um dieses Problem zu beheben, installieren Sie die fehlerhaften Serverrollen neu, oder entfernen Sie die betreffenden Serverrollen.

**So installieren Sie die fehlerhafte Serverrolle über die Befehlszeile neu**

1.  Öffnen Sie ein Eingabeaufforderungsfenster, und navigieren Sie dann zu den Installationsdateien.

2.  Führen Sie den folgenden Befehl aus:
    
        Setup /roles:<Failed Server Role>
    
    Wählen Sie mindestens eine der folgenden Rollen aus, und geben Sie sie in einer durch Trennzeichen getrennten Liste an:
    
    ClientAccess (oder CA oder C)
    
    EdgeTransport (oder ET oder E)
    

    > [!NOTE]
    > Die Serverrolle Edge-Transport darf nicht auf dem gleichen Computer wie eine der anderen Serverrollen vorhanden sein.

    

    > [!NOTE]
    > Sie müssen die Edge-Transport-Serverrolle im Umkreisnetzwerk und außerhalb der Active Directory-Gesamtstruktur bereitstellen.

    
    HubTransport (oder HT oder H)
    
    Mailbox (oder MB oder M)
    
    UnifiedMessaging (oder UM oder U)
    
    ManagementTools (oder MT oder T)
    

    > [!NOTE]
    > Wenn Sie "ManagementTools" angeben, installieren Sie die Exchange-Verwaltungskonsole, die Exchange-Cmdlets für die Exchange-Verwaltungsshell, die Exchange-Hilfedatei, das Tool Exchange Best Practices Analyzer und den Exchange-Problembehandlungs-Assistenten. Wenn Sie eine andere Serverrolle installieren, werden die Verwaltungstools automatisch installiert.

    
    Um einem vorhandenen Postfachserver die Serverrolle "Hub-Transport" hinzuzufügen, geben Sie z. B. Folgendes ein: **%LocalExchangeInstallationDir%\\bin\\Setup.com /role:HubTransport /Mode:Install**


> [!NOTE]
> Wenn eine der Exchange Server&nbsp;2007-Serverrollen zuvor erfolgreich installiert wurde, wird der Setup-Assistent im Wartungsmodus ausgeführt. Wenn keine der Exchange Server&nbsp;2007-Serverrollen zuvor erfolgreich installiert wurde, fährt der Setup-Assistent dort fort, wo er beendet wurde.



**So verwenden Sie den Setup-Assistenten für Exchange Server 2007 im Wartungsmodus, um die fehlerhafte Serverrolle erneut zu installieren**

1.  Melden Sie sich an dem Server an, auf dem eine Serverrolle erneut installiert werden soll.

2.  Öffnen Sie die Systemsteuerung, und doppelklicken Sie dann auf **Software**.

3.  Wählen Sie auf der Seite **Software** die Option **Microsoft Exchange Server** aus, und klicken Sie dann auf **Ändern**.

4.  Klicken Sie im Exchange Server 2007-Installationsassistenten auf der Seite **Exchange-Wartungsmodus** auf **Weiter**.

5.  Aktivieren Sie auf der Seite **Auswahl von Serverrollen** die Kontrollkästchen für die Serverrollen, die installiert werden sollen, und klicken Sie dann auf **Weiter**.
    

    > [!NOTE]
    > Die Serverrolle Edge-Transport darf nicht auf dem gleichen Computer wie eine der anderen Serverrollen vorhanden sein.

    

    > [!NOTE]
    > Sie müssen die Edge-Transport-Serverrolle im Umkreisnetzwerk und außerhalb der Active Directory-Gesamtstruktur bereitstellen.

    

    > [!NOTE]
    > Wenn Sie "ManagementTools" auswählen, installieren Sie die Exchange-Verwaltungskonsole, die Exchange-Cmdlets für die Exchange-Verwaltungsshell und die Exchange-Hilfedatei. Die Verwaltungstools werden bei der Installation jeder anderen Serverrolle automatisch installiert.



6.  Wenn Sie die Serverrolle **Hub-Transport** ausgewählt haben und Exchange 2007 in einer Gesamtstruktur installieren, die eine vorhandene Exchange Server 2003- oder Exchange 2000 Server-Organisation aufweist, wählen Sie auf der Seite **Nachrichtenübermittlungseinstellungen** einen Bridgeheadserver in der vorhandenen Organisation aus, der Mitglied der Exchange 2003- oder Exchange 2000-Routinggruppe ist, für die Sie einen Routinggruppenconnector erstellen möchten.

7.  Zeigen Sie auf der Seite **Überprüfungen der Bereitschaft** den Status an, um zu ermitteln, ob die Voraussetzungsüberprüfungen für die Organisation und die Serverrolle erfolgreich abgeschlossen wurden. Wenn sie erfolgreich abgeschlossen wurden, klicken Sie auf **Installieren**, um Exchange 2007 zu installieren.

8.  Klicken Sie auf der Seite **Fertigstellung** auf **Fertig stellen**.

**So verwenden Sie den Setup-Assistenten für Exchange Server 2007 zum erneuten Installieren der fehlerhaften Serverrolle, wenn zuvor keine andere Serverrolle erfolgreich installiert wurde**

1.  Befolgen Sie die Anweisungen unter "Ausführen einer benutzerdefinierten Installation mithilfe des Exchange Server 2007-Setups" ([https://go.microsoft.com/fwlink/?LinkId=86648](https://go.microsoft.com/fwlink/?linkid=86648)) in der Exchange Server 2007-Produktdokumentation.

**So entfernen Sie eine fehlerhafte Serverrolle**

1.  Befolgen Sie die Anweisungen unter "Entfernen von Exchange 2007-Serverfunktionen" ([https://go.microsoft.com/fwlink/?LinkId=86649](https://go.microsoft.com/fwlink/?linkid=86649)) in der Exchange Server 2007-Produktdokumentation.

## Weitere Informationen

Weitere Informationen zum Installieren von Exchange 2007 im unbeaufsichtigten Modus finden Sie unter "Installieren von Exchange 2007 im unbeaufsichtigten Modus" ([https://go.microsoft.com/fwlink/?LinkId=86476](https://go.microsoft.com/fwlink/?linkid=86476)).


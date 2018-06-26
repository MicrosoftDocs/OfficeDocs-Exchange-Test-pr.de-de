---
title: 'Festlegen der Optionen für die Warteschlangenanzeige: Exchange 2013 Help'
TOCTitle: Festlegen der Optionen für die Warteschlangenanzeige
ms:assetid: 03a9134c-0714-4c13-b286-92bccc7ec05e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa995934(v=EXCHG.150)
ms:contentKeyID: 50474958
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Festlegen der Optionen für die Warteschlangenanzeige

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-03_

Sie können Optionen in der Warteschlangenanzeige festlegen, um die Anzahl der auf der Seite angezeigten Elemente und das Intervall für die automatische Aktualisierung anzupassen. Das Intervall für die automatische Aktualisierung bestimmt, wie häufig die Ergebnisse in der Warteschlangenanzeige aktualisiert werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Warteschlangen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Festlegen von Optionen für die Warteschlangenanzeige mithilfe der Exchange Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange Server 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**.

3.  Klicken Sie in der Warteschlangenanzeige auf **Ansicht** \> **Optionen**, um die folgenden Einstellungen im Dialogfeld **Warteschlangenanzeige - Optionen** zu konfigurieren:
    
    1.  Geben Sie im Feld **Aktualisierungsintervall (Sekunden)** die Häufigkeit ein, mit der die Warteschlangenanzeige die Anzeige aktualisieren soll.
        

        > [!NOTE]
        > Das Standardintervall für die automatische Aktualisierung beträgt 30&nbsp;Sekunden und kann nicht auf einen kürzeren Zeitraum festgelegt werden. Wenn Sie die automatische Aktualisierungsfunktion deaktivieren, indem Sie das Kontrollkästchen <STRONG>Bildschirm automatisch aktualisieren</STRONG> auf der Seite <STRONG>Warteschlangenanzeige - Optionen</STRONG> deaktivieren, müssen Sie die in der Warteschlangenanzeige angezeigten Ergebnisse manuell aktualisieren, indem Sie auf <STRONG>Aktualisieren</STRONG> klicken.

    
    2.  Geben Sie im Feld **Anzahl der pro Seite anzuzeigenden Elemente** die maximale Anzahl der in der Warteschlangenanzeige anzuzeigenden Elemente ein. Es ist eine Zahl von 1 bis 10.000 möglich. Wenn Sie über mehr Elemente verfügen, als die Grenze angibt, werden die Elemente in Gruppen mit der maximalen Elementanzahl angezeigt. Die folgende Abbildung zeigt beispielsweise eine Warteschlange mit 14 Nachrichten, wobei die Warteschlangenanzeige für die Anzeige von 10 Elementen pro Seite konfiguriert ist. Die Anzahl der auf der Seite aufgeführten Objekte wird rechts oben angezeigt. Im unteren Fensterbereich wird die Gesamtanzahl von Elementen in der Warteschlange angezeigt. Zur Anzeige der weiteren Warteschlangenelemente können Sie die Navigationssteuerelemente verwenden.

4.  Klicken Sie nach Abschluss des Vorgangs auf **OK**.
    
    **Warteschlangenanzeige**
    
    ![Warteschlangenanzeige mit einer Anzahl von Elementen, die über dem Grenzwert liegt](images/Aa995934.e82196e6-002a-4e9e-823d-b244b0bd25e2(EXCHG.150).gif "Warteschlangenanzeige mit einer Anzahl von Elementen, die über dem Grenzwert liegt")  

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Wenn in der Warteschlangenanzeige das festgelegte Aktualisierungsintervall und die festgelegte Anzahl von Elementen pro Seite verwendet werden, wurden die Einstellungen erfolgreich konfiguriert.


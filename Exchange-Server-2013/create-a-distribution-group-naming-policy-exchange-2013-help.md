---
title: 'Erstellen einer Benennungsrichtlinie für Verteilergruppen: Exchange 2013 Help'
TOCTitle: Erstellen einer Benennungsrichtlinie für Verteilergruppen
ms:assetid: b2ffb654-345d-4be1-be8e-83d28901373e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ218693(v=EXCHG.150)
ms:contentKeyID: 50474895
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Benennungsrichtlinie für Verteilergruppen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-01_

Eine *Benennungsrichtlinie für Gruppen* ermöglicht das Standardisieren und Verwalten der Namen von Verteilergruppen, die von Benutzern in der Organisation erstellt werden. Sie können festlegen, dass dem Namen der Verteilergruppe bei der Erstellung ein bestimmtes Präfix und Suffix hinzugefügt werden muss, und Sie können die Verwendung bestimmter Wörter unterbinden. Dadurch können Sie die Verwendung ungeeigneter Wörter in Gruppennamen verringern.

Eine Gruppenbenennungsrichtlinie:

  - Erzwingt eine konsistente Benennungsstrategie für Gruppen, die von Benutzern erstellt werden.

  - Identifiziert Verteilergruppen im freigegebenen Adressbuch.

  - Schlägt die Funktion oder Mitgliedschaft der Gruppe vor.

  - Bestimmt den Typ der Benutzer, die wahrscheinlich Mitglieder der Gruppe sind.

  - Kennzeichnet die geografische Region, in der die Gruppe verwendet wird.

  - Verhindert die Verwendung von ungeeigneten Wörtern in Gruppennamen.

Wie funktioniert eine Gruppenbenennungsrichtlinie? Wenn ein Benutzer eine Gruppe erstellt, gibt er im Feld "Anzeigename" einen Namen an. Nach Erstellung der Gruppe wendet Microsoft Exchange die Gruppenbenennungsrichtlinie an, indem jedes in der Richtlinie definierte Präfix oder Suffix hinzugefügt wird. Der vollständige Name wird in der Verteilergruppenliste in der Exchange-Verwaltungskonsole, im freigegebenen Adressbuch sowie in den E-Mail-Feldern "An:", "Cc:" und "Von:" angezeigt. Versucht ein Benutzer, ein blockiertes Wort zu verwenden, erhält er beim Speichern der neuen Gruppe eine Fehlermeldung und wird aufgefordert, das blockierte Wort zu entfernen und die Gruppe erneut zu speichern.

Es folgen einige Beispiele zu einer Gruppenbenennungsrichtlinie. In jedem Beispiel ist **\<Gruppenname\>** ein beschreibender Name, der von der Person eingegeben wird, die die Gruppe erstellt. Exchange fügt dem Anzeigenamen die in der Richtlinie definierten Präfixe und Suffixe hinzu, wenn die Gruppe erstellt wird.

  - Textzeichenfolgen (mit Unterstrichen), die für ein einzelnes Präfix (**DG**) und ein Suffix (**Benutzer**) verwendet werden:
    
    **DG\_\<Gruppenname\>\_Users**

  - Mehrere Präfixe (**DG** und **Contoso**) und ein Suffix (**Benutzer**) mit Textzeichenfolgen:
    
    **DG\_Contoso\_\<Gruppenname\>\_Users**

  - Ein als Präfix verwendetes Attribut (**Department**):
    
    **Department\_\<Gruppenname\>**
    
    Angenommen, von Ihrer Schule wird für Fakultätsmitglieder das Department-Attribut verwendet. Im Anschluss finden Sie ein Beispiel für einen Gruppennamen, der von einem Fakultätsmitglied aus der Psychologieabteilung erstellt wurde:
    
    **Psychologie\_Kognitiv201**
    
    In diesem Beispiel wird der Unterstrich (\_) in einem zweiten Präfix als einzige Textzeichenfolge angegeben, um den Abteilungsnamen vom Gruppennamen zu trennen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verteilergruppen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Die maximale Länge für einen Gruppennamen beträgt 64 Zeichen. Dies beinhaltet die kombinierte Anzahl von Zeichen im Präfix, im vom Benutzer angegebenen Gruppennamen und im Suffix.

  - Die Gruppenbenennungsrichtlinie wird nur auf Gruppen angewendet, die von Benutzern erstellt werden. Wenn Sie oder andere Administratoren mithilfe der Exchange-Verwaltungskonsole Verteilergruppen erstellen, wird die Gruppenbenennungsrichtlinie ignoriert und nicht auf den Gruppennamen angewendet.

  - Gruppennamen werden ohne Leerzeichen erstellt. Es empfiehlt sich, zwischen Textzeichenfolgen, Attributen und dem Gruppennamen einen Unterstrich (\_) oder einen anderen Platzhalter zu verwenden.

  - Mit Windows PowerShell können Sie die Gruppenbenennungsrichtlinie außer Kraft setzen, wenn Sie eine Verteilergruppe erstellen oder bearbeiten. Weitere Informationen finden Sie unter [Außerkraftsetzen der Benennungsrichtlinie für Verteilergruppen](https://review.docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-distribution-groups/override-group-naming-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Erstellen einer Gruppenbenennungsrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Wählen Sie in der Exchange-Verwaltungskonsole **Gruppen** \> **Mehr** \> **Gruppenbenennungsrichtlinie konfigurieren**.

2.  Konfigurieren Sie unter **Gruppenbenennungsrichtlinie** das Präfix, indem Sie im Pulldownmenü entweder **Attribut** oder **Text** auswählen.
    
      - **Attribut**   Wählen Sie das gewünschte Attribut aus, und klicken Sie anschließend auf **OK**.
    
      - **Text**   Geben Sie die gewünschte Textzeichenfolge ein, und klicken Sie anschließend auf **OK**.
    
    Beachten Sie, dass die eingegebene Textzeichenfolge bzw. das ausgewählte Attribut als Link dargestellt wird. Klicken Sie auf den Link, um die Textzeichenfolge oder das Attribut zu ändern.

3.  Klicken Sie auf **Hinzufügen**, um weitere Präfixe hinzuzufügen.

4.  Wählen Sie für das Suffix im Pulldownmenü entweder **Attribut** oder **Text** aus, und konfigurieren Sie das Suffix.

5.  Klicken Sie auf **Hinzufügen**, um weitere Suffixe hinzuzufügen.
    
    Nach dem Hinzufügen eines Präfix oder Suffix wird eine Vorschau der Gruppenbenennungsrichtlinie angezeigt.

6.  Klicken Sie auf **Entfernen**![Löschen](images/JJ218693.37ba42c3-6f0d-42f3-b69b-ff912a99b5b7(EXCHG.150).gif "Löschen"), um ein Präfix oder Suffix aus der Richtlinie zu löschen.

7.  Klicken Sie auf **Blockierte Wörter**, um blockierter Wörter hinzuzufügen oder zu entfernen.
    
      - Wenn Sie der Liste ein Wort hinzufügen möchten, geben Sie das zu blockierende Wort ein, und klicken Sie auf **Hinzufügen**![Hinzufügen eines Symbols für ausgeschlossene Ordner bei der E-Mail-Migration](images/JJ218693.444d5c83-821f-472c-b733-e84308e2531e(EXCHG.150).gif "Hinzufügen eines Symbols für ausgeschlossene Ordner bei der E-Mail-Migration").
    
      - Um ein Wort aus der Liste zu entfernen, wählen Sie es aus, und klicken Sie auf **Entfernen**.
    
      - Um ein vorhandenes blockiertes Wort zu bearbeiten, wählen Sie es aus, und klicken Sie auf **Bearbeiten**.

8.  Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Erstellung einer Gruppenbenennungsrichtlinie zu überprüfen:

  - Wählen Sie in der Exchange-Verwaltungskonsole **Gruppen** \> **Mehr** \> **Gruppenbenennungsrichtlinie konfigurieren**.
    
    Die Gruppenbenennungsrichtlinie, die Sie definiert haben, wird auf der Seite **Gruppenbenennungsrichtlinie** unter **Vorschau der Richtlinie** angezeigt.

  - Führen Sie in Windows PowerShell den folgenden Befehl aus, um die Gruppenbenennungsrichtlinie anzuzeigen.
    
        Get-OrganizationConfig | FL DistributionGroupNamingPolicy


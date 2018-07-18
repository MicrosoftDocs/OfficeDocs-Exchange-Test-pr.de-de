---
title: 'E-Mail-Adressrichtlinien: Exchange 2013 Help'
TOCTitle: E-Mail-Adressrichtlinien
ms:assetid: b63b63bb-6faf-4337-8441-50bc64b49bb8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232171(v=EXCHG.150)
ms:contentKeyID: 50476520
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# E-Mail-Adressrichtlinien

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-07-21_

Empfänger (wozu Benutzer, Ressourcen, Kontakte und Gruppen gehören) sind alle E-Mail-aktivierten Objekte in Active Directory, an die Exchange Nachrichten senden oder weiterleiten kann. Ein Empfänger muss über eine E-Mail-Adresse verfügen, um E-Mails senden oder empfangen zu können. E-Mail-Adressrichtlinien generieren die primären und sekundären E-Mail-Adressen für Ihre Empfänger, damit diese E-Mails empfangen und senden können.

Standardmäßig enthält Exchange eine E-Mail-Adressrichtlinie für jeden E-Mail-aktivierten Benutzer. Diese Standardrichtlinie gibt den Alias des Empfängers als lokalen Teil der E-Mail-Adresse an und verwendet die akzeptierte Standarddomäne. Der lokale Teil einer E-Mail-Adresse ist der Name, der vor dem @-Zeichen angezeigt wird. Sie können jedoch die Art und Weise ändern, wie die E-Mail-Adressen der Empfänger angezeigt werden. Sie können beispielsweise angeben, dass die E-Mail-Adressen mit dem Format "*firstname*.*lastname*@contoso.com" angezeigt werden.

Wenn Sie weitere E-Mail-Adressen für alle Empfänger oder nur eine Teilmenge der Empfänger festlegen möchten, können Sie außerdem die Standardrichtlinie ändern oder zusätzliche Richtlinien erstellen. Beispielsweise kann das Benutzerpostfach für David Hamilton E-Mails empfangen, die an "hdavid@mail.contoso.com" oder "hamilton.david@mail.contoso.com" adressiert sind.

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit E-Mail-Adressrichtlinien gibt? Weitere Informationen finden Sie unter [Verfahren für die E-Mail-Adressrichtlinie](email-address-policy-procedures-exchange-2013-help.md).

## Verhalten von Empfängerrichtlinien

Exchange wendet eine Richtlinie auf alle Empfänger an, die den Kriterien der Empfängerfilterung entsprechen:

  - Empfängerrichtlinien werden in der Reihenfolge von der Richtlinie mit der höchsten zu der Richtlinie mit der niedrigsten Priorität angewendet. Bei einem Konflikt zwischen zwei oder mehr Richtlinien wird die Richtlinie mit der höchsten Priorität angewendet. Die Standardempfängerichtlinie hat immer die niedrigste Priorität und wird angewendet, wenn keine anderen Richtlinien zugeordnet werden.
    
    Wenn Sie eine Empfängerrichtlinie erstellen, aber nicht explizit eine Priorität angeben, wird diese als höchste Priorität hinzugefügt. Wenn Sie eine Priorität angeben, die bereits einer vorhandenen Richtlinie zugeordnet ist, werden die vorhandene Richtlinie und alle Richtlinien mit einer niedrigeren Priorität um eine Ebene nach unten verschoben. Die neue Richtlinie wird an der von Ihnen angegebenen Priorität eingefügt.
    
    Die Funktionalität der Empfängerrichtlinie ist in zwei Funktionen unterteilt: E-Mail-Adressrichtlinien und akzeptierte Domänen. Weitere Informationen zu akzeptierten Domänen finden Sie unter [Akzeptierte Domänen](accepted-domains-exchange-2013-help.md).

  - Wenn Sie das Cmdlet **Update-EmailAddressPolicy** in der Exchange-Verwaltungsshell ausführen, wird das Empfängerobjekt mit der E-Mail-Adressrichtlinie aktualisiert.

  - Jedes Mal, nachdem ein Empfängerobjekt geändert und gespeichert wurde, wird von Exchange die richtige Anwendung der E-Mail-Adressenkriterien und -Einstellungen erzwungen. Wenn eine E-Mail-Adressrichtlinie geändert und gespeichert wurde, werden alle zugeordneten Empfänger mit der Änderung aktualisiert. Außerdem wird nach einer Änderung eines Empfängerobjekts dessen Mitgliedschaft zur E-Mail-Adressrichtlinie neu ausgewertet und erzwungen.

## Erstellen von E-Mail-Adressrichtlinien

Wenn Sie eine neue E-Mail-Adressrichtlinie erstellen, können Sie die folgenden E-Mail-Adresstypen verwenden:

  - **SMTP-E-Mail-Musteradressen**. SMTP-E-Mail-*Muster*adressen sind häufig verwendete E-Mail-Adresstypen, die für Sie bereitgestellt werden.

  - **Benutzerdefinierte SMTP-E-Mail-Adressen**. Wenn Sie keine der SMTP-E-Mail-Musteradressen verwenden möchten, können Sie eine benutzerdefinierte SMTP-E-Mail-Adresse angeben.
    
    Wenn Sie eine benutzerdefinierte SMTP-E-Mail-Adresse erstellen, können Sie die Variablen in der folgenden Tabelle zum Angeben von Alternativwerten für den lokalen Teil der E-Mail-Adresse verwenden.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Variable</th>
    <th>Wert</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>%g</p></td>
    <td><p>Vorname</p></td>
    </tr>
    <tr class="even">
    <td><p>%i</p></td>
    <td><p>Mittelinitial</p></td>
    </tr>
    <tr class="odd">
    <td><p>%s</p></td>
    <td><p>Nachname</p></td>
    </tr>
    <tr class="even">
    <td><p>%d</p></td>
    <td><p>Anzeigename</p></td>
    </tr>
    <tr class="odd">
    <td><p>%m</p></td>
    <td><p>Exchange-Alias</p></td>
    </tr>
    <tr class="even">
    <td><p>%<em>x</em>s</p></td>
    <td><p>Verwendet die ersten <em>x</em> Buchstaben des Nachnamens. Wenn z. B. <em>x</em> =2 ist, werden die ersten zwei Buchstaben des Nachnamens verwendet.</p></td>
    </tr>
    <tr class="odd">
    <td><p>%<em>x</em>g</p></td>
    <td><p>Verwendet die ersten <em>x</em> Buchstaben des Vornamens. Wenn z. B. <em>x</em> =2 ist, werden die ersten zwei Buchstaben des Vornamens verwendet.</p></td>
    </tr>
    </tbody>
    </table>


  - **Nicht-SMTP-E-Mail-Adressen**. Die folgenden Nicht-SMTP-E-Mail-Adresstypen werden unterstützt:
    
      - EX (Anzeigename des Präfixes der Legacy-DN-Proxyadresse)
    
      - X.500
    
      - X.400
    
      - MSMail
    
      - CcMail
    
      - Lotus Notes
    
      - Novell GroupWise
    
      - Exchange Unified Messaging-Proxyadresse (EUM-Proxyadresse)
    

    > [!IMPORTANT]
    > In Exchange werden alle Nicht-SMTP-E-Mail-Adressen als benutzerdefinierte Adressen angesehen. Exchange bietet für die E-Mail-Adresstypen X.400, GroupWise oder Lotus Notes keine eigenen Dialogfelder oder Eigenschaften an. Beim Hinzufügen einer benutzerdefinierten Nicht-SMTP-E-Mail-Adresse müssen Sie über die entsprechenden DLL-Dateien (Dynamic Link Library) verfügen. Wenn Sie die entsprechenden DLL-Dateien nicht bereitstellen, können Sie keine benutzerdefinierte E-Mail-Adressrichtlinie erstellen. Der folgende Fehler wird in der Ereignisanzeige protokolliert: "Das Beschreibungsobjekt für E-Mail-Adressen im Microsoft Exchange-Verzeichnis für den Adresstyp 'SADF' auf 'i386' Computern fehlt."



Ausführliche Anweisungen zum Erstellen einer E-Mail-Adressrichtlinie finden Sie in den folgenden Themen:

[Erstellen einer E-Mail-Adressrichtlinie](create-an-email-address-policy-exchange-2013-help.md)

[Erstellen einer E-Mail-Adressrichtlinie mithilfe der Empfängerfilterung](create-an-email-address-policy-by-using-recipient-filters-exchange-2013-help.md)


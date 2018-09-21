---
title: 'Vorbereitung von Active Directory und Domänen: Exchange 2013 Help'
TOCTitle: Vorbereitung von Active Directory und Domänen
ms:assetid: f895e1ce-d766-4352-ac46-ec959c9954a9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125224(v=EXCHG.150)
ms:contentKeyID: 50477113
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Vorbereitung von Active Directory und Domänen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Bevor Sie Microsoft Exchange Server 2013 installieren, müssen Sie Ihre Active Directory-Gesamtstruktur und deren Domänen vorbereiten. Exchange muss Active Directory so vorbereiten, dass Informationen über die Postfächer Ihrer Benutzer und die Konfiguration der Exchange-Server in der Organisation gespeichert werden können. Wenn Sie mit Active Directory-Gesamtstrukturen oder -Domänen nicht vertraut sind, finden Sie weitere Informationen unter [Übersicht über Active Directory-Domänendienste](https://go.microsoft.com/fwlink/p/?linkid=399226).


> [!NOTE]
> Unabhängig davon, ob dies die erste Installation von Exchange in Ihrer Umgebung ist oder Sie bereits über frühere Versionen von Exchange&nbsp;Server verfügen, müssen Sie Active&nbsp;Directory für Exchange&nbsp;2013 vorbereiten. Details zu den neuen Schemaklassen und -attributen, die Exchange&nbsp;2013 zu Active&nbsp;Directory hinzufügt, einschließlich der durch Service&nbsp;Packs (SP) und kumulative Updates (CU) implementierten, finden Sie unter <A href="exchange-2013-active-directory-schema-changes-exchange-2013-help.md">Änderungen des Active Directory-Schemas in Exchange&nbsp;2013</A>.



Sie können Active Directory auf verschiedene Weise für Exchange vorbereiten. Erstens können Sie diese Aufgabe vom Exchange 2013-Setup-Assistenten erledigen lassen. Wenn Sie weder eine große Active Directory-Bereitstellung noch ein separates Team für die Verwaltung von Active Directoryhaben, wird die Verwendung des Assistenten empfohlen. Das dafür verwendete Konto muss ein Mitglied der Sicherheitsgruppen Schema-Admins und Organisations-Admins sein. Weitere Informationen zur Verwendung des Setup-Assistenten finden Sie unter [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md).

Wenn Sie eine große Active Directory-Bereitstellung haben oder ein separates Team Active Directory verwaltet, ist dieses Thema richtig für Sie. Mit den Schritten in diesem Thema können Sie die jeweiligen Vorbereitungsphasen wesentlich besser steuern und festlegen, wer welchen Schritt ausführen kann. Exchange-Administratoren verfügen zum Beispiel möglicherweise nicht über die erforderlichen Berechtigungen für die Erweiterung des Active Directory-Schemas.

Was sollten Sie wissen, bevor Sie beginnen?

1\. Erweiterung des Active-Directory-Schemas

2\. Vorbereitung von Active Directory

3\. Vorbereitung von Active Directory-Domänen

Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Sind Sie neugierig, was geschieht, wenn Active Directory für Exchange vorbereitet wird? Weitere Informationen finden Sie unter [Welche Änderungen werden in Active Directory vorgenommen, wenn Exchange 2013 installiert wird?](what-changes-in-active-directory-when-exchange-2013-is-installed-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Mindestens 10 bis 15 Minuten (ohne Active Directory-Replikation), je nach Größe der Organisation und Anzahl der untergeordneten Domänen.

  - Der Computer, den Sie für die Ausführung dieser Schritte verwenden, muss die [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md) erfüllen. Außerdem muss Ihre Active Directory-Gesamtstruktur die im Abschnitt "Netzwerk- und Verzeichnisserver" unter [Exchange 2013 – Systemanforderungen](exchange-2013-system-requirements-exchange-2013-help.md) aufgeführten Voraussetzungen erfüllen.

  - Wenn Ihre Organisation mehrere Active Directory-Domänen hat, wird Folgendes empfohlen:
    
      - Führen Sie die unten beschriebenen Schritte von einem Active Directory-Standort mit einem Active Directory-Server von jeder Domäne aus.
    
      - Installieren Sie den ersten Exchange-Server an einem Active Directory-Standort mit einem beschreibbaren globalen Katalogserver von jeder Domäne aus.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## 1\. Erweiterung des Active-Directory-Schemas

Der erste Schritt zur Vorbereitung Ihrer Organisation für Exchange 2013 besteht in der Erweiterung des Active Directory-Schemas. Exchange speichert viele Informationen in Active Directory, muss aber zuvor Klassen, Attribute und andere Elemente hinzufügen und aktualisieren. Wenn Sie wissen möchten, was bei der Erweiterung Ihres Schemas geändert wird, finden Sie weitere Informationen unter [Änderungen des Active Directory-Schemas in Exchange 2013](exchange-2013-active-directory-schema-changes-exchange-2013-help.md).

Bevor Sie Ihr Schema erweitern, sollten Sie einige Dinge im Hinterkopf behalten:

  - Das Konto, mit dem Sie angemeldet sind, muss ein Mitglied der Sicherheitsgruppen Schema-Admins und Organisations-Admins sein.

  - Der Computer, auf dem Sie den Befehl für die Erweiterung des Schemas ausführen, muss sich in derselben Active Directory-Domäne und am selben Standort befinden wie der Schemamaster.

  - Wenn Sie den Parameter *DomainController* verwenden, vergewissern Sie sich, dass Sie den Namen des Domänencontrollers verwenden, der der Schemamaster ist.

  - Sie können das Schema für Exchange nur über die Schritte in diesem Thema oder mithilfe von Exchange 2013 Setup erweitern. Andere Methoden zum Erweitern des Schemas werden nicht unterstützt.


> [!TIP]
> Wenn Ihr Active Directory-Schema nicht von einem separaten Team verwaltet wird, können Sie diesen Schritt überspringen und direkt mit Vorbereitung von Active Directory fortfahren. Wenn das Schema in Schritt 1 nicht erweitert wird, wird es mit den Befehlen in Schritt 2 für Sie erweitert. Wenn Sie entscheiden, Schritt 1 zu überspringen, müssen die obigen Informationen trotzdem berücksichtigt werden.



Wenn Sie bereit sind, gehen Sie wie folgt vor, um Ihr Active Directory-Schema zu erweitern. Wenn Sie mehrere Active Directory-Gesamtstrukturen haben, vergewissern Sie sich, dass Sie bei der richtigen angemeldet sind.

1.  Vergewissern Sie sich, dass Ihr Computer für die Ausführung von Exchange 2013 Setup bereit ist. Informationen dazu, was Sie für die Ausführung von Setup benötigen, finden Sie im Abschnitt [Active Directory preparation](exchange-2013-prerequisites-exchange-2013-help.md) unter [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

2.  Öffnen Sie ein Windows-Eingabeaufforderungsfenster, und navigieren Sie zu dem Speicherplatz, an den Sie die Exchange-Installationsdateien gespeichert haben.

3.  Führen Sie den folgenden Befehl aus, um das Schema zu erweitern.
    
    ```powershell
Setup.exe /PrepareSchema /IAcceptExchangeServerLicenseTerms
```

Wenn Setup die Erweiterung des Schemas abgeschlossen hat, müssen Sie warten, während Active Directory die Änderungen auf alle Domänencontroller repliziert. Sie können das Tool `repadmin` verwenden, um zu prüfen, wie die Replikation verläuft. `Repadmin` ist Bestandteil des Tools für die Active Directory-Domänendienste in Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2. Weitere Informationen zur Verwendung des Tools finden Sie unter [Repadmin](https://go.microsoft.com/fwlink/p/?linkid=257879).

## 2\. Vorbereitung von Active Directory

Nachdem das Active Directory-Schema erweitert wurde, können Sie andere Bereiche von Active Directory für Exchange 2013 vorbereiten. Bei diesem Schritt erstellt Exchange Container, Objekte und andere Elemente in Active Directory, die zum Speichern von Informationen verwendet werden. Die Sammlung aller Exchange-Container, -Objekte, -Attribute und so weiter wird als *Exchange-Organisation* bezeichnet.

Bevor Sie Active Directory für Exchange vorbereiten, sollten Sie einige Dinge im Hinterkopf behalten:

  - Das Konto, mit dem Sie angemeldet sind, muss ein Mitglied der Sicherheitsgruppe Organisations-Admins sein. Wenn Sie Schritt 1 übersprungen haben, weil Sie das Schema mit dem Befehl *PrepareAD* erweitern möchten, muss das verwendete Konto auch ein Mitglied der Sicherheitsgruppe Schema-Admins sein.

  - Der Computer, auf dem Sie den Befehl ausführen, muss sich in derselben Active Directory-Domäne und am selben Standort befinden wie der Schemamaster. Er muss zudem alle Domänen in der Gesamtstruktur über TCP-Port 389 kontaktieren.

  - Warten Sie, bis Active Directory die in Schritt 1 vorgenommenen Änderungen an alle Domänencontroller repliziert hat, bevor Sie diesen Schritt ausführen.

Wenn Sie den Befehl unten ausführen, um Active Directory für Exchange vorzubereiten, müssen Sie die Exchange-Organisation benennen. Dieser Name wird intern von Exchange verwendet und ist normalerweise für Benutzer nicht sichtbar. Oft wird der Name des Unternehmens, in dem Exchange installiert wird, als Name für die Organisation verwendet. Der Name wirkt sich nicht auf die Funktionen von Exchange aus und bestimmt auch nicht, wie Ihre E-Mail-Adressen aussehen. Sie können jeden beliebigen Namen verwenden, solange Sie Folgendes berücksichtigen.

  - Sie können jeden kleinen oder großen Buchstaben von A bis Z verwenden.

  - Sie können die Ziffern 0 bis 9 verwenden.

  - Der Name kann Leerstellen enthalten, solange sich diese weder am Anfang noch am Ende des Namens befinden.

  - Sie können einen Bindestrich oder einen Gedankenstrich im Namen verwenden.

  - Der Name kann bis zu 64 Zeichen lang, darf aber nicht leer sein.

  - Der Name kann nicht geändert werden, nachdem er festgelegt wurde.

Wenn Sie bereit sind, gehen Sie wie folgt vor, um Active Directory für Exchange vorzubereiten. Wenn der gewünschte Name für die Organisation Leerzeichen enthält, schließen Sie den Namen in Anführungszeichen ein (").

1.  Öffnen Sie ein Windows-Eingabeaufforderungsfenster, und navigieren Sie zu dem Speicherplatz, an den Sie die Exchange-Installationsdateien gespeichert haben.

2.  Führen Sie den folgenden Befehl aus:
    
        Setup.exe /PrepareAD /OrganizationName:"<organization name>" /IAcceptExchangeServerLicenseTerms

Wenn Setup die Vorbereitung von Active Directory für Exchange abgeschlossen hat, müssen Sie warten, während Active Directory die Änderungen auf alle Domänencontroller repliziert. Sie können das Tool `repadmin` verwenden, um zu prüfen, wie die Replikation verläuft. `repadmin` ist Bestandteil des Tools für die Active Directory-Domänendienste in Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2. Weitere Informationen zur Verwendung des Tools finden Sie unter [Repadmin](https://go.microsoft.com/fwlink/p/?linkid=257879).

## 3\. Vorbereitung von Active Directory-Domänen

Der letzte Schritt bei der Vorbereitung von Active Directory für Exchange besteht darin, alle Active Directory-Domänen vorzubereiten, in denen Exchange installiert wird oder sich E-Mail-aktivierte Benutzer befinden. Mit diesem Schritt werden zusätzliche Container und Sicherheitsgruppen erstellt sowie Berechtigungen festgelegt, damit Exchange auf diese zugreifen kann.

Wenn Sie mehrere Domänen in Ihrer Active Directory-Gesamtstruktur haben, können Sie diese auf verschiedene Weise vorbereiten. Wählen Sie die Option aus, die dem entspricht, was Sie tun möchten. Wenn Sie nur eine Domäne haben, können Sie diesen Schritt überspringen, da die Domäne bereits mit dem Befehl *PrepareAD* in Schritt 2 für Sie vorbereitet wurde.

## Vorbereitung aller Domänen in der Active Directory-Gesamtstruktur

Zur Vorbereitung aller Active Directory-Domänen können Sie bei der Ausführung von Setup den Parameter *PrepareAllDomains* verwenden. Setup bereitet jede Domäne in Ihrer Active Directory-Gesamtstruktur für Exchange vor.

Bevor Sie alle Domänen in Ihrer Active Directory-Gesamtstruktur vorbereiten, behalten Sie Folgendes im Hinterkopf:

  - Das von Ihnen verwendete Konto muss ein Mitglied der Sicherheitsgruppe Organisations-Admins sein.

  - Warten Sie, bis Active Directory die in Schritt 2 vorgenommenen Änderungen an alle Domänencontroller repliziert hat. Wenn Sie das nicht tun, wird möglicherweise ein Fehler ausgegeben, wenn Sie versuchen, die Domäne vorzubereiten.

Wenn Sie bereit sind, gehen Sie wie folgt vor, um alle Domänen in Ihrer Active Directory-Gesamtstruktur für Exchange vorzubereiten.

1.  Öffnen Sie ein Windows-Eingabeaufforderungsfenster, und navigieren Sie zu dem Speicherplatz, an den Sie die Exchange-Installationsdateien gespeichert haben.

2.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
Setup.exe /PrepareAllDomains /IAcceptExchangeServerLicenseTerms
```

## Selber auswählen, welche Active Directory-Domänen vorbereitet werden

Wenn Sie auswählen möchten, welche Active Directory-Domänen vorbereitet werden sollen, können Sie bei der Ausführung von Setup den Parameter *PrepareDomain* verwenden. Bei der Verwendung des Parameters *PrepareDomain* müssen Sie den vollqualifizierten Domänennamen (FQDN) der Domäne angeben, die Sie vorbereiten möchten.

Bevor Sie die Domänen in Ihrer Active Directory-Gesamtstruktur vorbereiten, behalten Sie Folgendes im Hinterkopf:

  - Für das verwendete Konto sind Berechtigungen erforderlich, die davon abhängen, wann die Domäne erstellt wurde.
    
      - **Vor der Ausführung von PrepareAD erstellte Domäne**   Wenn die Domäne erstellt wurde, **bevor** Sie den Befehl *PrepareAD* in Schritt 2 oben ausgeführt haben, muss das verwendete Konto ein Mitglied der Gruppe Domänen-Admins in der vorzubereitenden Domäne sein.
    
      - **Nach der Ausführung von PrepareAD erstellte Domäne**   Wenn die Domäne erstellt wurde, **nachdem** Sie den Befehl *PrepareAD* in Schritt 2 oben ausgeführt haben, muss das verwendete Konto 1) ein Mitglied der Rollengruppe Organisationsverwaltung und 2) ein Mitglied der Gruppe Domänen-Admins in der vorzubereitenden Domäne sein.

  - Warten Sie, bis Active Directory die in Schritt 2 vorgenommenen Änderungen an alle Domänencontroller repliziert hat. Wenn Sie das nicht tun, wird möglicherweise ein Fehler ausgegeben, wenn Sie versuchen, die Domäne vorzubereiten.

  - Sie müssen jede Domäne vorbereiten, in der ein Exchange-Server installiert wird. Sie müssen außerdem jede Domäne vorbereiten, die E-Mail-aktivierte Benutzer enthält, selbst wenn diese Domänen keine Exchange-Server enthalten.

  - Sie müssen den Befehl *PrepareDomain* nicht in der Domäne ausführen, in der der Befehl *PrepareAD* ausgeführt wurde. Mit dem Befehl *PrepareAD* wird diese Domäne automatisch vorbereitet.

Wenn Sie bereit sind, gehen Sie wie folgt vor, um eine einzelne Domänen in Ihrer Active Directory-Gesamtstruktur für Exchange vorzubereiten.

1.  Öffnen Sie ein Windows-Eingabeaufforderungsfenster, und navigieren Sie zu dem Speicherplatz, an den Sie die Exchange-Installationsdateien gespeichert haben.

2.  Führen Sie den folgenden Befehl aus. Schließen Sie den FQDN der Domäne ein, die Sie vorbereiten möchten. Wenn Sie die Domäne vorbereiten möchten, in der Sie den Befehl ausführen, müssen Sie den FQDN nicht einschließen.
    
        Setup.exe /PrepareDomain:<FQDN of the domain you want to prepare> /IAcceptExchangeServerLicenseTerms

3.  Wiederholen Sie die Schritte für jede Active Directory-Domäne, in der Sie einen Exchange-Server installieren oder sich E-Mail-aktivierte Benutzer befinden.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Nachdem Sie alle oben beschriebenen Schritte abgeschlossen haben, können Sie überprüfen, ob alles reibungslos abgelaufen ist. Dafür verwenden Sie das Tool Active Directory-Dienstschnittstellen-Editor (ADSI-Editor). ADSI-Editor ist Bestandteil des Tools für die Active Directory-Domänendienste in Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2. Weitere Informationen zu dem Tool finden Sie unter [ADSI Edit (adsiedit.msc)](https://go.microsoft.com/fwlink/p/?linkid=294644).


> [!WARNING]
> Ändern Sie Werte in ADSI-Editor nur, wenn Sie vom Microsoft-Support dazu angewiesen werden. Das Ändern von Werten in ADSI-Editor kann zu irreparablen Schäden an Ihrer Exchange-Organisation und Active Directory führen.



Nachdem Exchange Ihr Active Directory-Schema erweitert und Active Directory für Exchange vorbereitet hat, werden verschiedene Eigenschaften aktualisiert, um anzuzeigen, dass die Vorbereitung abgeschlossen ist. Verwenden Sie die Informationen in der folgenden Liste, um sicherzustellen, dass diese Eigenschaften die richtigen Werte haben. Jede Eigenschaft muss mit dem in der folgenden Tabelle enthaltenen Wert für die von Ihnen zu installierende Version von Exchange 2013 übereinstimmen.

  - Überprüfen Sie im Namenskontext **Schema**, ob die Eigenschaft **rangeUpper** für **ms-Exch-Schema-Verision-Pt** auf den Wert für Ihre Exchange 2013-Version festgelegt ist, der in der Tabelle Exchange 2013 Active Directory-Versionen aufgeführt ist.
    
     

  - Überprüfen Sie im Namenskontext **Konfiguration**, ob die Eigenschaft **objectVersion** im Container CN=\<*your organization*\>,CN=Microsoft Exchange,CN=Dienste,CN=Konfiguration,DC=\<*domain*\> auf den Wert für Ihre Exchange 2013-Version festgelegt ist, der in der Tabelle Exchange 2013 Active Directory-Versionen aufgeführt ist.
    
     

  - Überprüfen Sie im Namenskontext **Standard**, ob die Eigenschaft **objectVersion** im Container **Microsoft Exchange-Systemobjekte** unter DC=\<*root domain* auf den Wert für Ihre Exchange 2013-Version festgelegt ist, der in der Tabelle Exchange 2013 Active Directory-Versionen aufgeführt ist.
    
     

Sie können auch im Exchange-Setupprotokoll überprüfen, ob die Active Directory-Vorbereitung erfolgreich abgeschlossen wurde. Weitere Informationen finden Sie unter [Überprüfen einer Exchange 2013-Installation](verify-an-exchange-2013-installation-exchange-2013-help.md). Sie können das im Thema [Überprüfen einer Exchange 2013-Installation](verify-an-exchange-2013-installation-exchange-2013-help.md) erwähnte Cmdlet **Get-ExchangeServer** erst verwenden, wenn Sie die Installation von mindestens einer Postfachserverrolle und einer Clientzugriffsserverrolle an einem Active Directory-Standort abgeschlossen haben.

## Exchange 2013 Active Directory-Versionen

In der folgenden Tabelle sind die Exchange 2013-Objekte in Active Directory aufgeführt, die jedes Mal aktualisiert werden, wenn Sie eine neue Version von Exchange 2013 installieren. Sie können die angezeigten Objektversionen mit den Werten in der Tabelle unten vergleichen, um zu überprüfen, ob Active Directory mit der von Ihnen installierten Version von Exchange 2013 während der Installation erfolgreich aktualisiert wurde.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th> </th>
<th>Exchange-Version</th>
<th>rangeUpper</th>
<th>objectVersion</th>
<th>objectVersion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Namenskontext</strong></p></td>
<td><p> </p></td>
<td><p>Schema</p></td>
<td><p>Default</p></td>
<td><p>Configuration</p></td>
</tr>
<tr class="even">
<td><p><strong>Container</strong></p></td>
<td><p> </p></td>
<td><p>ms-Exch-Schema-Version-Pt</p></td>
<td><p>Microsoft Exchange-Systemobjekte</p></td>
<td><p>CN=&lt;<em>your organization</em>&gt;,CN=Microsoft Exchange,CN=Dienste,CN=Konfiguration,DC=&lt;<em>domain</em>&gt;</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Exchange 2013 CU10 und neuer</p></td>
<td><p>15312</p></td>
<td><p>13236</p></td>
<td><p>16130</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Exchange 2013 CU9</p></td>
<td><p>15312</p></td>
<td><p>13236</p></td>
<td><p>15965</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Exchange 2013 CU8</p></td>
<td><p>15312</p></td>
<td><p>13236</p></td>
<td><p>15965</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Exchange 2013 CU7</p></td>
<td><p>15312</p></td>
<td><p>13236</p></td>
<td><p>15965</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Exchange 2013 CU6</p></td>
<td><p>15303</p></td>
<td><p>13236</p></td>
<td><p>15965</p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Exchange 2013 CU5</p></td>
<td><p>15300</p></td>
<td><p>13236</p></td>
<td><p>15870</p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Exchange 2013 SP1</p></td>
<td><p>15292</p></td>
<td><p>13236</p></td>
<td><p>15844</p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Exchange 2013 CU3</p></td>
<td><p>15283</p></td>
<td><p>13236</p></td>
<td><p>15763</p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Exchange 2013 CU2</p></td>
<td><p>15281</p></td>
<td><p>13236</p></td>
<td><p>15688</p></td>
</tr>
<tr class="even">
<td><p> </p></td>
<td><p>Exchange 2013 CU1</p></td>
<td><p>15254</p></td>
<td><p>13236</p></td>
<td><p>15614</p></td>
</tr>
<tr class="odd">
<td><p> </p></td>
<td><p>Exchange 2013 RTM</p></td>
<td><p>15137</p></td>
<td><p>13236</p></td>
<td><p>15449</p></td>
</tr>
</tbody>
</table>


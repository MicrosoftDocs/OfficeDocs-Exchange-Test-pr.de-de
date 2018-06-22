---
title: 'Konfigurieren von modernen Anlagen mit OneDrive for Business und Exchange-2016 (lokal): Exchange 2013 Help'
TOCTitle: Konfigurieren von modernen Anlagen mit OneDrive for Business und Exchange-2016 (lokal)
ms:assetid: 799518aa-7cfe-4708-92ee-98057ff168f5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt589761(v=EXCHG.150)
ms:contentKeyID: 70319586
ms.date: 01/03/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von modernen Anlagen mit OneDrive for Business und Exchange-2016 (lokal)

 

_<strong>Gilt für:</strong>Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-09_

**Zusammenfassung:** Informationen dazu, wie Sie Ihren lokalen Exchange Server 2016-Benutzern die Zusammenarbeit an Dokumenten mit OneDrive for Business und SharePoint Online in einer Hybridkonfiguration ermöglichen.

Vor kurzem wurde in Office 365 eine neue Anlageoption zur Verfügung gestellt. In Exchange 2016 ermöglicht diese als *Zusammenarbeit an Dokumenten* bezeichnete Option lokalen Benutzern, in OneDrive for Business gespeicherte Anlagen direkt in ihre Outlook im Web-Clients zu integrieren.


> [!NOTE]
> Seit der Veröffentlichung von Exchange Server 2016 heißt Outlook Web App jetzt Outlook im Web.



In der Vergangenheit hat ein Benutzer eine Datei an andere Personen gesendet, indem er die Datei an eine Nachricht anfügt. Ein oder mehrere Empfänger haben dann Änderungen in ihren jeweiligen Kopien der Datei vorgenommen, die dann ggf. alle irgendwann zusammengeführt werden mussten. Zudem belegten diese angefügten Dateien Speicherplatz im Postfach jedes Benutzers. Mit der Zusammenarbeit an Dokumenten fügen Benutzer stattdessen einen Link zu einer Datei ein, die in einem OneDrive for Business-Konto gespeichert ist. So kann die Datei von mehreren Personen am selben Quellspeicherort bearbeitet werden, ohne dass zusätzlicher Speicher erforderlich ist.

Bevor die Exchange 2016-Umgebung ordnungsgemäß für die Zusammenarbeit an Dokumenten konfiguriert ist, sieht das Dialogfeld für Anlagen eines Outlook im Web-Benutzers standardmäßig wie folgt aus:

![herkömmliches Anlagedialogfeld](images/Mt589761.f8c74d70-42f9-48c6-b263-ce6cef8591a8(EXCHG.150).png "herkömmliches Anlagedialogfeld")

Nach der Konfiguration Ihrer Umgebung nach den folgenden Anweisungen sehen Dialogfelder für Anlagen in Outlook im Web wie folgt aus:

![Anlagedialogfeld, in dem moderne Anlagen aktiviert sind](images/Mt589761.89eeae65-ce3a-4c47-b57e-db734a1de95b(EXCHG.150).png "Anlagedialogfeld, in dem moderne Anlagen aktiviert sind")

Benutzer in Ihrer Organisation mit lokalen Postfächern und OneDrive for Business-Konten in Office 365 haben die Möglichkeit, die moderne Anlagemethode zu verwenden, mit der sie ein in OneDrive for Business gespeichertes Dokument für mehrere Empfänger freigeben können. Der Ort der Empfänger (online oder lokal) spielt keine Rolle.

Weitere Informationen zu Hybridbereitstellungen finden Sie unter [Hybridbereitstellungen in Exchange Server](exchange-server-hybrid-deployments-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Lesen Sie [Hybridbereitstellungen in Exchange Server](exchange-server-hybrid-deployments-exchange-2013-help.md), und machen Sie sich klar, welche Bereiche vom Konfigurieren einer Hybridbereitstellung betroffen sind.

  - Sorgen Sie dafür, dass alle Anforderungen für eine Hybridbereitstellung erfüllt werden, die unter [Voraussetzungen für die Hybridbereitstellung](hybrid-deployment-prerequisites-exchange-2013-help.md) beschrieben sind.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](https://technet.microsoft.com/de-de/library/jj150484\(v=exchg.150\)).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren von Exchange 2016 zum Aktivieren der Zusammenarbeit an Dokumenten in einer Hybridumgebung

Stellen Sie sicher, dass die folgenden vorbereitenden Schritte abgeschlossen wurden, und aktivieren Sie dann mit dem darauf folgenden Verfahren die Zusammenarbeit an Dokumenten.

**Voraussetzungen**

  - Konfigurieren Sie Ihre Exchange-Hybridumgebung mit dem [Assistent für die Hybridkonfiguration](hybrid-configuration-wizard-exchange-2013-help.md) (Hybrid Configuration Wizard, HCW).

  - Exchange 2016 muss in Ihrer lokalen Organisation installiert sein. Exchange 2016 kann parallel mit früheren Versionen von Exchange verwendet werden, aber die Zusammenarbeit an Dokumenten funktioniert nur für Postfächer auf einem Exchange 2016-Server.

  - Bei der Installation des authentifizierenden Servers müssen alle Benutzer synchronisiert sein. Sie können das Cmdlet [Get-AuthServer](https://technet.microsoft.com/de-de/library/jj218613\(v=exchg.150\)) verwenden, um Ihren authentifizierenden Server zu ermitteln. Es wird empfohlen, den HCW von einem Exchange 2016-Server aus zu verwenden, um alle notwendigen OAuth-Konfigurationen vorzunehmen.
    

    > [!IMPORTANT]
    > OAuth zwischen Exchange 2016 und Office 365 muss ordnungsgemäß konfiguriert werden. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/dn594521(v=exchg.150)">Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen</A>.



  - Benutzer müssen über die richtigen Lizenzen verfügen. Benutzer mit einem OneDrive for Business-Konto müssen für SharePoint Online oder OneDrive for Business lizenziert werden. Sie können die Lizenz eines Benutzers überprüfen, indem Sie den Benutzer im Office 365-Portal auswählen und auf die Schaltfläche **Bearbeiten** klicken.
    

    > [!NOTE]
    > Weitere Informationen finden Sie unter <A href="http://go.microsoft.com/fwlink/p/?linkid=627455">Einrichten von OneDrive for Business in Office 365</A>.



Führen Sie die folgenden Schritte durch:

1.  Konfigurieren Sie die Standardpostfachrichtlinie von Outlook im Web so, dass die Host-URL von OneDrive for Business festgelegt wird.
    

    > [!NOTE]
    > Sie können zum Office 365 SharePoint Online-Mandantenadministrator wechseln, um die Host-URL von OneDrive for Business abzurufen. Zum Beispiel ist „https://contoso-my.sharepoint.com“ eine Host-URL für „Meine Website“ im O365-Mandanten von Contoso.<BR>Obwohl die Outlook im Web-Postfachrichtlinie aus dem Lieferumfang von Exchange 2016 als „Standard“ bezeichnet wird, wird sie nicht automatisch auf Postfächer angewendet, wenn Sie sie nicht entweder zur Standardrichtlinie erklären oder sie direkt einem Postfach zuweisen.

    
    Verwenden Sie mit dem folgenden Beispiel als Grundlage die Exchange-Verwaltungsshell, um die interne und externe MySite-URL in der Outlook im Web-Standardpostfachrichtlinie zu konfigurieren:
    
        Set-OwaMailboxPolicy Default -InternalSPMySiteHostURL https://Contoso-my.sharepoint.com -ExternalSPMySiteHostURL https://Contoso-my.sharepoint.com

2.  Als Nächstes legen Sie entweder die soeben konfigurierte Richtlinie als Standardrichtlinie fest, sodass sie auf alle Postfächer angewendet wird, oder weisen Sie die Richtlinie einzelnen Benutzern zu.
    
    Um die Richtlinie zur Outlook im Web-Standardpostfachrichtlinie zu machen, geben Sie den folgenden Befehl in die Exchange-Verwaltungsshell ein:
    
        Set-OwaMailboxPolicy Default -IsDefault 
    
    Um die Richtlinie dem Postfach einer einzelnen Person zuzuweisen, geben Sie den folgenden Befehl in die Exchange-Verwaltungsshell ein:
    
        Set-CASMailbox <user mailbox> -OwaMailboxPolicy Default

3.  (Optional) Starten Sie auf jedem Exchange 2016-Server **OWAApplicationPool** neu. Dadurch kann die Konfiguration sofort wirksam werden. Wenn Sie diesen Befehl nicht ausführen, dauert es ein paar Minuten, bis die aktualisierte Postfachrichtlinie auf Ihren Exchange 2016-Servern angewendet wird. Führen Sie in der Exchange-Verwaltungsshell Folgendes aus:
    
        Restart-WebAppPool MSExchangeOWAAppPool

Nach der Konfiguration wird Outlook im Web-Benutzern eine Auswahl für den Anlagetyp angeboten, den sie auf ihre Nachrichten anwenden möchten: traditionell oder modern.

![Dialogfeld für Anlageoptionen, Teilen mit OneDrive oder Als Anlage senden](images/Mt589761.7d2f27c2-3638-479a-a577-029ac61e7d95(EXCHG.150).png "Dialogfeld für Anlageoptionen, Teilen mit OneDrive oder Als Anlage senden")


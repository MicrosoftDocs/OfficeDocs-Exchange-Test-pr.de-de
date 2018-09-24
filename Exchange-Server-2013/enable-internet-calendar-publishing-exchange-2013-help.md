---
title: 'Aktiv. d. Veröff. von Kalenderinformationen im Internet: Exchange 2013-Hilfe'
TOCTitle: Aktivieren der Veröffentlichung von Kalenderinformationen im Internet
ms:assetid: b4c71696-52bb-492c-8259-0e419acd0bbc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ853046(v=EXCHG.150)
ms:contentKeyID: 50554908
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren der Veröffentlichung von Kalenderinformationen im Internet

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-08-22_

**Zusammenfassung:**  Verwenden Sie diese Verfahren, um OWA-Benutzern in Ihrer Exchange 2013-Organisation das Freigeben von Frei/Gebucht-Informationen im Kalender für externe Organisationen zu ermöglichen.

Benutzer in Microsoft Exchange Server 2013-Organisationen können Verfügbarkeitsinformationen aus Kalendern (Frei/Gebucht-Informationen) für Benutzer in Organisationen, bei denen es sich nicht um Exchange-Organisationen handelt, oder andere Personen mit Internetzugriff freigeben. Die Kalenderveröffentlichung im Internet sorgt für mehr Flexibilität und erhöht die Anzahl der Benutzer, die die Verfügbarkeitsinformationen im Kalender gemeinsam nutzen können.

Das Aktivieren der Kalenderveröffentlichung im Internet besteht aus drei allgemeinen Schritten:

1.  Konfigurieren der Webproxy-URL für den Postfachserver (dieser Schritt ist nur erforderlich, wenn in Ihrer Organisation bereits ein Webproxy-URL vorhanden ist, andernfalls fahren Sie mit Schritt 2 fort).

2.  Aktivieren des virtuellen Verzeichnisses für die Veröffentlichung für den Clientzugriffsserver.

3.  Erstellen einer dedizierten Freigaberichtlinie für die Kalenderveröffentlichung im Internet oder Aktualisieren der Standardfreigaberichtlinie zur Unterstützung der Domäne **Anonym**. Beide Methoden ermöglichen es Benutzern in Ihrer Exchange-Organisation, andere Benutzer mit Internetzugriff zum Anzeigen eingeschränkter Kalenderverfügbarkeitsinformationen einzuladen, auf die über eine veröffentlichte URL zugegriffen wird.


> [!IMPORTANT]
> Nach Abschluss von Schritt 3 müssen Benutzer dann ihre Kalender aus Outlook veröffentlichen. Durch die Kalenderveröffentlichung werden URLs erstellt, die Benutzer an Personen außerhalb der Organisation weitergeben können. Mit einer URL können Empfänger Kalender mithilfe von Outlook oder Outlook Web App abonnieren, mit der anderen kann der Empfänger einen Kalender in einem Webbrowser anzeigen. Jeder Benutzer kann steuern, wie viele Details andere Personen sehen können.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Freigaberichtlinien finden Sie unter [Freigaberichtlinien](sharing-policies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 15 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Kalender- und Freigabeberechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - In der Exchange-Organisation, in der die Kalenderinformationen von Benutzern freigegeben werden, ist ein Exchange 2013-Clientzugriffsserver vorhanden.

  - In der Exchange-Organisation, in der die Kalenderinformationen von Benutzern freigegeben werden, befinden sich die Benutzerpostfächer auf Exchange 2013-Postfachservern.

  - Nur Benutzer von Outlook 2010 oder höher und Outlook Web App können Einladungen zur Freigabe erstellen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Konfigurieren der Webproxy-URL mithilfe der Shell


> [!NOTE]
> Dieser Schritt ist nur erforderlich, wenn in Ihrer Organisation bereits eine Webproxy-URL vorhanden ist. Wenn dies nicht der Fall ist, fahren Sie mit Schritt2 fort.<BR>Die Exchange-Verwaltungskonsole kann nicht zum Konfigurieren der Webproxy-URL verwendet werden.



In diesem Beispiel wird eine Webproxy-URL auf dem Postfachserver "MAIL01" konfiguriert.

    Set-ExchangeServer -Identity "MAIL01" -InternetWebProxy "<Webproxy URL>"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ExchangeServer](https://technet.microsoft.com/de-de/library/bb123716\(v=exchg.150\)).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können genauer untersuchen, ob Sie die Webproxy-URL erfolgreich konfiguriert haben, indem Sie den folgenden Shell-Befehl ausführen und die Informationen des Parameters *InternetWebProxy* überprüfen.

    Get-ExchangeServer | format-list

## Schritt 2: Aktivieren des virtuellen Verzeichnisses für die Veröffentlichung mithilfe der Shell


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Aktivieren des virtuellen Verzeichnisses für die Veröffentlichung verwendet werden.



In diesem Beispiel wird das virtuelle Verzeichnis für die Veröffentlichung auf dem Clientzugriffsserver "CAS01" aktiviert.

    Set-OwaVirtualDirectory -Identity "CAS01\owa (Default Web Site)" -ExternalUrl "<URL for CAS01>" -CalendarEnabled $true

Dabei ist die Identität `CAS01\owa (Default Web Site)` sowohl der Servername als auch das virtuelle Verzeichnis von Outlook Web App.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/bb123515\(v=exchg.150\)).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können genauer untersuchen, ob Sie das virtuelle Verzeichnis für die Veröffentlichung erfolgreich aktiviert haben, indem Sie den folgenden Shell-Befehl ausführen und die Informationen des Parameters *ExternalURL* überprüfen.

    Get-OwaVirtualDirectory | format-list

## Schritt 3: Erstellen oder Konfigurieren einer speziellen Freigaberichtlinie für die Veröffentlichung von Kalenderinformationen im Internet


> [!NOTE]
> Die folgenden Optionen in Schritt 3 gelten nur für Exchange Online-Umgebungen.



Sie können eine Freigaberichtlinie für die Veröffentlichung von Kalenderinformationen im Internet erstellen (Option 1) oder die Standardfreigaberichtlinie für die Veröffentlichung von Kalenderinformationen im Internet konfigurieren (Option 2) . Bei beiden Optionen können Sie die Exchange-Verwaltungskonsole oder die Shell verwenden.

## Option 1: Erstellen einer speziellen Freigaberichtlinie für die Veröffentlichung von Kalenderinformationen im Internet

Wenn Sie eine Freigaberichtlinie spezifisch für die Veröffentlichung von Kalenderinformationen im Internet erstellen möchten, führen Sie die folgenden Schritte aus.

## Verwenden der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Klicken Sie in der Listenansicht unter **Einzelne Freigabe** auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie in **Freigaberichtlinie** im Feld **Richtlinienname** einen Anzeigenamen für die Freigaberichtlinie ein (z. B. **Internet**).

4.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Freigaberegeln für die Freigaberichtlinie zu definieren.

5.  Klicken Sie in **Freigaberegel** auf **Freigabe für eine bestimmte Domäne**, und geben Sie in das dazugehörige Feld **Anonymous** ein.

6.  Um Kalenderfreigabeebenen zu definieren, die Sie für die Freigaberichtlinie durchsetzen möchten, aktivieren Sie das Kontrollkästchen **Ihre Kalenderordner freigeben**, und wählen Sie eines der folgenden Optionsfelder aus:
    
      - **Frei/Gebucht-Kalenderinformationen nur mit Zeit**
    
      - **Frei/Gebucht-Kalenderinformationen mit Zeit, Betreff und Ort**
    
      - **Alle Informationen zum Termin einschließlich Uhrzeit, Betreff, Ort und Titel**

7.  Klicken Sie auf **Speichern**, um die Regeln für die Freigaberichtlinie festzulegen.

8.  Klicken Sie in **Freigaberichtlinie** auf **Speichern**, um die Freigaberichtlinie zu erstellen.

## Verwenden der Shell

In diesem Beispiel wird eine Freigaberichtlinie für die Veröffentlichung von Kalenderinformationen im Internet mit dem Namen "Internet" erstellt, und die Richtlinie wird so konfiguriert, dass lediglich Verfügbarkeitsinformationen freigegeben werden dürfen. Die Richtlinie wird aktiviert.

    New-SharingPolicy -Name "Internet" -Domains 'Anonymous: CalendarSharingFreeBusySimple' -Enabled $true

In diesem Beispiel wird die Freigaberichtlinie "Internet" zu einem Benutzerpostfach hinzugefügt.

    Set-Mailbox -Identity <user name> -SharingPolicy "Internet"

In diesem Beispiel wird die Freigaberichtlinie "Internet" zu einer Organisationseinheit hinzugefügt.

    Set-Mailbox -OrganizationalUnit <OU name> -SharingPolicy "Internet"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-SharingPolicy](https://technet.microsoft.com/de-de/library/dd298186\(v=exchg.150\)) und [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können untersuchen, ob Sie die Freigaberichtlinie erfolgreich erstellt haben, indem Sie den folgenden Shell-Befehl ausführen, um die Informationen zur Freigaberichtlinie zu überprüfen.

    Get-SharingPolicy <policy name> | format-list

## Option 2: Konfigurieren der Standardfreigaberichtlinie für die Kalenderveröffentlichung im Internet

Wenn Sie eine standardmäßige Freigaberichtlinie für die Veröffentlichung von Kalenderinformationen im Internet konfigurieren möchten, führen Sie die folgenden Schritte aus.

## Verwenden der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Wählen Sie in der Listenansicht unter **Einzelne Freigabe** die Standardfreigaberichtlinie aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie in **Freigaberichtlinie** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Freigaberegel der Richtlinie hinzuzufügen.

4.  Klicken Sie in **Freigaberegel** auf **Freigabe für eine bestimmte Domäne**, und geben Sie in das dazugehörige Feld **Anonymous** ein.

5.  Um Kalenderfreigabeebenen zu definieren, die Sie für die Freigaberichtlinie durchsetzen möchten, aktivieren Sie das Kontrollkästchen **Ihre Kalenderordner freigeben**, und wählen Sie eines der folgenden Optionsfelder aus:
    
      - **Frei/Gebucht-Kalenderinformationen nur mit Zeit**
    
      - **Frei/Gebucht-Kalenderinformationen mit Zeit, Betreff und Ort**
    
      - **Alle Informationen zum Termin einschließlich Uhrzeit, Betreff, Ort und Titel**

6.  Klicken Sie auf **Speichern**, um die Regeln für die Freigaberichtlinie festzulegen.

7.  Klicken Sie in **Freigaberichtlinie** auf **Speichern**, um die Änderungen zu speichern.

## Verwenden der Shell

In diesem Beispiel wird die Standardfreigaberichtlinie aktualisiert und die Richtlinie so konfiguriert, dass lediglich Verfügbarkeitsinformationen freigegeben werden dürfen. Die Richtlinie wird aktiviert.

    Set-SharingPolicy -Name "Default Sharing Policy" -Domains 'Anonymous: CalendarSharingFreeBusySimple' -Enabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie können genauer untersuchen, ob Sie die Standardfreigaberichtlinie erfolgreich aktualisiert haben, indem Sie den folgenden Shell-Befehl ausführen, um die Informationen zur Freigaberichtlinie zu überprüfen.

    Get-SharingPolicy <policy name> | format-list


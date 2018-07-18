---
title: 'Erstellen einer Freigaberichtlinie: Exchange 2013 Help'
TOCTitle: Erstellen einer Freigaberichtlinie
ms:assetid: cae8cab0-6265-448b-8add-5202cdb20678
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657494(v=EXCHG.150)
ms:contentKeyID: 50476732
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer Freigaberichtlinie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Mithilfe von Freigaberichtlinien können Sie steuern, wie Benutzer in Ihrer Exchange-Organisation Kalenderinformationen mit Benutzern außerhalb Ihrer Organisation teilen können. Freigaberichtlinien ermöglichen das durch den Benutzer eingerichtete personenbezogene Teilen von Kalenderinformationen mit verschiedenen Typen von externen Benutzern. Sie unterstützen das Teilen von Kalenderinformationen mit externen Verbundorganisationen (wie z. B. Office 365 oder einer anderen lokalen Exchange-Organisation), externen Nicht-Verbundorganisationen und einzelnen Benutzern mit Internetzugang. Informationen zum Anwenden einer bestimmten Freigaberichtlinie auf Benutzer finden Sie unter [Anwenden von Freigaberichtlinien für Postfächer](apply-a-sharing-policy-to-mailboxes-exchange-2013-help.md).


> [!IMPORTANT]
> Das Erstellen einer Freigaberichtlinie ist einer von mehreren Schritten, die zum Einrichten von Verbundfreigaben in Ihrer Exchange-Organisation ausgeführt werden müssen. Bevor Sie Kalenderinformationen mit anderen Exchange-Verbundorganisationen teilen können, müssen Sie mithilfe des Azure Active Directory-Authentifizierungssystems eine Verbundvertrauensstellung für Ihre lokale Exchange-Organisation einrichten. Eine Verbundvertrauensstellung ist für Freigaberichtlinien für das Internet nicht erforderlich.



Weitere Informationen zur Verbundfreigabe finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Verbundverfahren finden Sie unter [Verbundverfahren](federation-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Kalenderberechtigungen und gemeinsame Berechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Für Freigaberichtlinien zwischen Exchange-Verbundorganisationen gelten folgende Anforderungen:
    
      - In jeder Exchange-Organisation ist ein Exchange 2013-Clientzugriffsserver vorhanden. Freigaberichtlinien werden auch zwischen Exchange-Organisationen unterstützt, bei denen eine Organisation Clientzugriffsserver mit Exchange 2013 und die andere Organisation Clientzugriffsserver mit Exchange 2010 SP3 oder höher aufweist.
    
      - Jede Exchange-Organisation hat eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem erstellt. Weitere Informationen finden Sie unter [Konfigurieren einer Verbundvertrauensstellung](configure-a-federation-trust-exchange-2013-help.md).
    
      - Jede Exchange-Organisation hat eine Verbundorganisations-ID konfiguriert. Den Organisations-IDs wurden die zum Generieren der E-Mail-Adressen von Benutzern verwendeten Domänen hinzugefügt.
    
      - Die Benutzerpostfächer befinden sich in jeder Exchange-Organisation auf Exchange 2013- oder Exchange 2010-Postfachservern.
    
      - Nur Benutzer von Outlook 2010 oder höher und Outlook Web App können Einladungen zur Freigabe erstellen.

  - Für Freigaberichtlinien für Organisationen, die nicht zu den Exchange-Verbundorganisationen gehören, oder für einzelne Benutzer gelten folgende Anforderungen:
    
      - In der Exchange-Organisation, in der die Kalenderinformationen von Benutzern freigegeben werden, ist ein Exchange 2013-Clientzugriffsserver vorhanden.
    
      - In der Exchange-Organisation, in der die Kalenderinformationen von Benutzern freigegeben werden, befinden sich die Benutzerpostfächer auf Exchange 2013-Postfachservern.
    
      - Der Exchange 2013-Clientzugriffsserver muss für Outlook Web App-Zugriff aktiviert sein.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Erstellen einer Freigaberichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Klicken Sie in der Listenansicht unter **Einzelne Freigabe** auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie unter **Neue Freigaberichtlinie** einen Anzeigenamen für die Freigaberichtlinie im Feld **Richtlinienname** ein.

4.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Freigaberegeln für die Freigaberichtlinie anzugeben.

5.  Wählen Sie im Dialogfeld **Freigaberegel** eine der folgenden Optionen aus, um die Domänen für die Freigabe anzugeben:
    
      - **Freigabe für alle Domänen**
    
      - **Freigabe für eine bestimmte Domäne**

6.  Wenn Sie **Freigabe für eine bestimmte Domäne** auswählen, geben Sie die Domäne für die Freigabe ein. Falls Sie mehrere Domänen für diese Freigaberichtlinie eingeben müssen, speichern Sie zunächst die Einstellungen für die erste Domäne, und bearbeiten Sie anschließend die Freigaberegeln, sodass weitere Domänen hinzugefügt werden können.

7.  Um Kalenderfreigabeebenen anzugeben, die Sie für die Freigaberichtlinie durchsetzen möchten, aktivieren Sie das Kontrollkästchen **Ihre Kalenderordner freigeben**, und wählen Sie eine der folgenden Optionen aus:
    
      - **Frei/Gebucht-Kalenderinformationen nur mit Zeit**
    
      - **Frei/Gebucht-Kalenderinformationen mit Zeit, Betreff und Ort**
    
      - **Alle Informationen zum Termin einschließlich Uhrzeit, Betreff, Ort und Titel**

8.  Klicken Sie auf **Speichern**, um die Regeln für die Freigaberichtlinie festzulegen.

9.  Wenn diese Freigaberichtlinie die Standardfreigaberichtlinie für Benutzer in Ihrer Exchange-Organisation sein soll, aktivieren Sie das Kontrollkästchen **Diese Richtlinie als meine Standardfreigaberichtlinie verwenden**.

10. Klicken Sie auf **Speichern**, um die Freigaberichtlinie zu erstellen.

## Verwenden der Exchange-Verwaltungskonsole, um allen Benutzern die vollständige Freigabe von Kalenderdetails zu ermöglichen

Sie können die standardmäßige Freigaberichtlinie bearbeiten, um zu ermöglichen, dass alle Benutzer die vollständigen Kalenderdetails für Personen außerhalb der Organisation freigeben können.

1.  Navigieren Sie zu **Organisation** \> **Freigabe**.

2.  Wählen Sie in der Listenansicht unter **Einzelne Freigabe** die Standardfreigaberichtlinie aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie im Dialogfeld **Freigaberichtlinie** die Option **Freigabe für alle Domänen**, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Wählen Sie im Dialogfeld **Freigaberegel** unter **Informationen angeben, die freigegeben werden sollen** die Option **Alle Informationen zum Kalendertermin, einschließlich Uhrzeit, Betreff, Ort und Titel**, und klicken Sie auf **Speichern**.

5.  Klicken Sie im Dialogfeld **Freigaberichtlinie** auf **Speichern**, um die Regeln für die Freigaberichtlinie festzulegen.

## Erstellen einer Freigaberichtlinie mithilfe der Shell

  - In diesem Beispiel wird die Freigaberichtlinie "Contoso" für die externe Verbunddomäne "contoso.com" erstellt. Mithilfe dieser Richtlinie können Benutzer in der Domäne "contoso.com" ausführliche Verfügbarkeitsinformationen aus Kalendern (Frei/Gebucht-Informationen) Ihrer Benutzer anzeigen. Diese Richtlinie ist standardmäßig aktiviert.
    
        New-SharingPolicy -Name "Contoso" -Domains contoso.com: CalendarSharingFreeBusyDetail

  - In diesem Beispiel wird die Freigaberichtlinie "ContosoWoodgrove" für zwei verschiedene Verbunddomänen ("contoso.com" und "woodgrovebank.com") mit unterschiedlichen Freigabeaktionen für jede Domäne konfiguriert. Die Richtlinie wird deaktiviert.
    
        New-SharingPolicy -Name "ContosoWoodgrove" -Domains 'contoso.com: CalendarSharingFreeBusySimple', 'woodgrovebank.com: CalendarSharingFreeBusyDetail -Enabled $false

  - In diesem Beispiel wird die Freigaberichtlinie "Anonymous" für eine Exchange-Organisation mit dem Clientzugriffsserver "CAS01" und dem Postfachserver "MAIL01" mit der für eingeschränkte Verfügbarkeitsinformationen aus Kalendern konfigurierten Freigabeaktion erstellt. Diese Richtlinie ermöglicht es Benutzern in Ihrer Exchange-Organisation, Benutzer mit Internetzugriff zum Anzeigen ihrer Kalenderverfügbarkeitsinformationen einzuladen, indem sie diesen Benutzern einen Link senden. Die Richtlinie wird aktiviert.
    
    1.  Festlegen der Webproxy-URL für "MAIL01".
        
            Set-ExchangeServer -Identity "Mail01" -InternetWebProxy "<Webproxy URL>"
    
    2.  Aktivieren des virtuellen Verzeichnisses für die Veröffentlichung auf "CAS01".
        
            Set-OwaVirtualDirectory -Identity "CAS01" -ExternalURL "<URL for CAS01>" -CalendarPublishingEnabled $true
    
    3.  Erstellen der Freigaberichtlinie "Anonymous" und Konfigurieren der eingeschränkten Freigabe von Kalenderinformationen.
        
            New-SharingPolicy -Name "Anonymous" -Domains 'Anonymous: CalendarSharingFreeBusySimple' -Enabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [New-SharingPolicy](https://technet.microsoft.com/de-de/library/dd298186\(v=exchg.150\))

  - [Set-ExchangeServer](https://technet.microsoft.com/de-de/library/bb123716\(v=exchg.150\))

  - [Set-OwaVirtualDirectory](https://technet.microsoft.com/de-de/library/bb123515\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Sie können untersuchen, ob Sie die Freigaberichtlinie erfolgreich erstellt haben, indem Sie den folgenden Shell-Befehl ausführen, um die Informationen zur Freigaberichtlinie zu überprüfen.

    Get-SharingPolicy <policy name> | format-list


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



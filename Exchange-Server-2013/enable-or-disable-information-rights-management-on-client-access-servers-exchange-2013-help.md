---
title: 'Aktivieren oder Deaktivieren der Verwaltung von Informationsrechten auf Clientzugriffsservern: Exchange 2013 Help'
TOCTitle: Aktivieren oder Deaktivieren der Verwaltung von Informationsrechten auf Clientzugriffsservern
ms:assetid: c7ce069b-a572-4755-90a3-7105472e4c83
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876938(v=EXCHG.150)
ms:contentKeyID: 50476700
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren der Verwaltung von Informationsrechten auf Clientzugriffsservern

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Beim Aktivieren der Verwaltung von Informationsrechten (Information Rights Management, IRM) auf Clientzugriffsservern werden die folgenden Funktionen aktiviert:

  - Microsoft Office Outlook Web App

  - IRM in Microsoft Exchange ActiveSync

Wenn IRM auf Clientzugriffsservern aktiviert ist, können Outlook Web App-Benutzer Nachrichten mit IRM schützen, indem Sie eine Vorlage für [Active Directory-Rechteverwaltungsdienste (AD RMS)](https://technet.microsoft.com/de-de/library/hh831364.aspx) anwenden, die in Ihrem AD RMS-Cluster erstellt wurde. Outlook Web App-Benutzer können zudem IRM-geschützte Nachrichten und unterstützte Anlagen anzeigen. Bevor Sie IRM auf Clientzugriffsservern aktivieren, müssen Sie der Administratorengruppe im AD RMS-Cluster das Verbundpostfach hinzufügen.


> [!IMPORTANT]
> Mitglieder der Administratorengruppe erhalten eine Nutzungslizenz für Besitzer, wenn sie eine Lizenz vom AD&nbsp;RMS-Cluster anfordern. So können sie alle durch den Rechteverwaltungsdienst geschützten Inhalte von diesem Cluster entschlüsseln.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Konfiguration der Verwaltung von Informationsrechten" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - In der Active Directory-Gesamtstruktur muss ein AD RMS-Cluster installiert sein.

  - Das Verbundpostfach wurde zur AD RMS-Administratorengruppe hinzugefügt. Ausführliche Anweisungen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).

  - IRM-Funktionen müssen für die Organisation aktiviert sein. Ausführliche Anweisungen finden Sie unter [Aktivieren oder Deaktivieren von IRM für interne Nachrichten](enable-or-disable-irm-for-internal-messages-exchange-2013-help.md).

  - Sie können das Cmdlet **Set-IRMConfiguration** zum Aktivieren oder Deaktivieren von IRM in Outlook Web App und in Exchange ActiveSync in Ihrer gesamten Exchange-Organisation oder auf bestimmten Ebenen verwenden.
    
    Sie können IRM in Outlook Web App auf den folgenden Ebenen steuern:
    
      - **Pro virtuellem Outlook Web App-Verzeichnis**   Verwenden Sie zum Aktivieren oder Deaktivieren von IRM für ein virtuelles Outlook Web App-Verzeichnis das Cmdlet **Set-OWAVirtualDirectory**, und setzen Sie den Parameter *IRMEnabled* auf `$false` oder `$true` (Standard). Auf diese Weise können Sie IRM in Outlook Web App für ein virtuelles Verzeichnis auf einem Exchange 2013-Clientzugriffsserver deaktivieren, während es für ein anderes virtuelles Verzeichnis auf einem anderen Clientzugriffsserver aktiviert bleibt.
    
      - **Pro Outlook Web App-Postfachrichtlinie**   Verwenden Sie zum Aktivieren oder Deaktivieren von IRM für eine Outlook Web App-Postfachrichtlinie das Cmdlet **Set-OWAMailboxPolicy**, und setzen Sie den Parameter *IRMEnabled* auf `$false` oder `$true` (Standard). So können Sie IRM in Outlook Web App für eine Gruppe von Benutzern aktivieren und für eine andere Gruppe von Benutzern deaktivieren, indem Sie diesen eine andere Outlook Web App-Postfachrichtlinie zuweisen.
    
    Sie können IRM in Exchange ActiveSync über eine Exchange ActiveSync-Postfachrichtlinie steuern. Zum Deaktivieren oder Aktivieren von IRM in Exchange ActiveSync für eine Exchange ActiveSync-Postfachrichtlinie verwenden Sie das Cmdlet **Set-ActiveSyncMailboxPolicy** und legen den Parameter *IRMEnabled* auf `$false` oder `$true` (Standardwert) fest. IRM kann in Exchange ActiveSync für einige Benutzer aktiviert und für andere deaktiviert werden, indem Sie den Benutzergruppen unterschiedliche Exchange ActiveSync-Postfachrichtlinien zuweisen.

  - Die Exchange-Verwaltungskonsole (Exchange Administration Center, EAC) kann nicht zum Aktivieren oder Deaktivieren von IRM auf Clientzugriffsservern verwendet werden. Sie müssen die Shell verwenden.

## Was möchten Sie machen?

## Aktivieren der Verwaltung von Informationsrechten auf Clientzugriffsservern mithilfe der Shell

In diesem Beispiel wird IRM auf Clientzugriffsservern für eine Exchange-Organisation aktiviert.

    Set-IRMConfiguration -ClientAccessServerEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Deaktivieren der Verwaltung von Informationsrechten auf Clientzugriffsservern mithilfe der Shell

In diesem Beispiel wird IRM auf Clientzugriffsservern für eine Exchange-Organisation deaktiviert.

    Set-IRMConfiguration -ClientAccessServerEnabled $false

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Schritte aus, um zu überprüfen, ob Sie IRM auf Clientzugriffsservern erfolgreich aktiviert oder deaktiviert haben:

  - Führen Sie das Cmdlet **Get-IRMConfiguration** aus, und überprüfen Sie den Wert der Eigenschaft *ClientAccessServerEnabled*.
    
    Ein Beispiel für das Abrufen der IRM-Konfiguration finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/e1821219-fe18-4642-a9c2-58eb0aadd61a\(exchg.150\)#examples) zu **Get-IRMConfiguration**.

  - Verwenden Sie Outlook Web App, um eine IRM-geschützte Nachricht zu erstellen oder zu lesen.


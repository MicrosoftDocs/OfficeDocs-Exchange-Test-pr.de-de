---
title: 'Verwaltung von Informationsrechten in Outlook Web App: Exchange 2013 Help'
TOCTitle: Verwaltung von Informationsrechten in Outlook Web App
ms:assetid: 60a49dab-17ac-4d2c-9b41-7d87250d6c00
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876891(v=EXCHG.150)
ms:contentKeyID: 50475792
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwaltung von Informationsrechten in Outlook Web App

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Information-Worker verwenden zum Austausch vertraulicher Informationen zunehmend E-Mail-Nachrichten. Zur besseren Sicherung dieser Informationen können Organisationen die Verwaltung von Informationsrechten (IRM) verwenden und Nachrichteninhalte dauerhaft schützen. Vor Microsoft Exchange Server 2010 war die effektive Nutzung des IRM-Schutzes auf Outlook-Clients beschränkt. In Exchange Server 2007 mussten die Benutzer von Microsoft Outlook Web Access das Rechteverwaltungs-Add-In für Microsoft Internet Explorer herunterladen, um auf IRM-geschützte Inhalte zugreifen zu können.

In Exchange 2013 kann der Benutzer über die Verwaltung von Informationsrechten (IRM) in Outlook Web App auf die umfangreichen IRM-Funktionen von Exchange zugreifen und dauerhaften IRM-Schutz auf Nachrichteninhalte anwenden.

Die folgenden IRM-Funktionen sind in Outlook Web App verfügbar:

  - **Senden IRM-geschützter Nachrichten**   Wie aus der folgenden Abbildung hervorgeht, können Benutzer von Outlook Web App in der Berechtigungs-Dropdownliste eine Vorlage für Benutzerrechterichtlinien auswählen und auf die Nachricht anwenden. Dies ermöglicht Benutzern das Senden von IRM-geschützten Nachrichten aus Outlook Web App. Der IRM-Schutz wird von den Clientzugriffsservern auf die Nachrichten angewendet.
    
    ![Senden einer IRM-geschützten Nachricht von OWA](images/Dd876891.fa8cabb5-c049-46dc-8b29-9d9957dbfd3e(EXCHG.150).gif "Senden einer IRM-geschützten Nachricht von OWA")  

  - **IRM-geschützte Anlagen**   Wenn ein Benutzer eine IRM-geschützte Nachricht aus Outlook Web App sendet, wird derselbe IRM-Schutz auch auf alle der Nachricht angefügten Dateien angewendet. Auch hier kommt die schon für die Nachricht verwendete Vorlage für Benutzerrechterichtlinien zum Einsatz. In Exchange 2013 wird IRM-Schutz auf alle mit Microsoft Office Word, Excel und PowerPoint verknüpften Dateien sowie auf XPS-Dateien und E-Mail-Nachrichten angewendet. IRM-Schutz wird nur auf eine Anlage angewendet, wenn diese noch nicht IRM-geschützt ist. Weitere Informationen zu Rechterichtlinienvorlagen der Active Directory-Rechteverwaltungsdienste (AD RMS) finden Sie unter [Verwaltung von Informationsrechten](information-rights-management-exchange-2013-help.md).
    

    > [!NOTE]
    > Mit der Verwaltung von Informationsrechten (IRM) in Outlook Web App werden nur angefügte Dateien in dem in diesem Abschnitt beschriebenen Format geschützt. Anlagen in nicht unterstützten Dateiformaten werden nicht geschützt. Wenn ein Outlook Web App-Benutzer eine Nachricht schützt und eine Datei in einem nicht unterstützten Dateiformat anhängt, wird der Benutzer anhand einer eingeblendeten Benachrichtigung darüber informiert, dass nur unterstützte Dateiformate geschützt werden.

    

    > [!IMPORTANT]
    > IRM-Schutz kann nicht auf Nachrichten angewendet werden, die bereits mit S/MIME signiert oder verschlüsselt wurden. Wenn die Nachricht durch IRM geschützt werden soll, müssen die S/MIME-Signatur und -Verschlüsselung entfernt werden. Das Gleiche gilt analog für IRM-geschützte Nachrichten, die mit S/MIME weder signiert noch verschlüsselt werden können.



  - **Lesen von IRM-geschützten Nachrichten**   Nachrichten, die vom Absender mithilfe des AD RMS-Clusters in Ihrer Organisation geschützt wurden, werden in Outlook Web App im Vorschaufenster wiedergegeben. Es müssen keine Add-Ins installiert werden, und der Computer braucht auch nicht in der AD RMS-Bereitstellung registriert zu werden. Wenn ein Benutzer eine Nachricht öffnet oder im Vorschaufenster anzeigt, wird die Nachricht mithilfe der Verwendungslizenz entschlüsselt, die vom Vorlizenzierungs-Agent hinzugefügt wurde. Nach der Entschlüsselung wird die Nachricht im Vorschaufenster angezeigt. Wenn keine Vorlizenz verfügbar ist, fordert Outlook Web App eine Vorlizenz vom AD RMS-Server an und gibt anschließend die Nachricht wieder. Beim Lesen von IRM-geschützten Anlagen in Outlook Web App steht die webfähige Dokumentenanzeige nicht zur Verfügung.
    

    > [!NOTE]
    > IRM in Outlook Web App kann jedoch nicht verhindern, dass Benutzer mit der Funktion "Drucken" Bildschirmaufnahmen machen, wie sie auch in Outlook und anderen Office-Anwendungen verwendet werden. Das hat Auswirkungen auf das Benutzerrecht "Extrahieren", das verhindert, das Nachrichteninhalte kopiert werden (sofern in der Vorlage für AD&nbsp;RMS-Benutzerrechterichtlinien angegeben).



  - **IRM-Unterstützung in diversen Browsern und für mehrere Plattformen**   IRM in Outlook Web App bietet eine IRM-Unterstützung in diversen Browsern und für mehrere Plattformen an. IRM in Outlook Web App wird in allen Browsern unterstützt, die von Exchange 2013 unterstützt werden (auch unter den Betriebssystemen Apple Macintosh und Linux). Weitere Informationen zu unterstützten Browsern und Betriebssystemen finden Sie unter [Von Outlook Web App unterstützte Browser](https://go.microsoft.com/fwlink/p/?linkid=129362).

  - **WebReady Document Viewing**   In Exchange 2013 können Benutzer unterstützte, durch IRM geschützte Anlagen mithilfe von WebReady Document Viewing anzeigen. So können Benutzer unterstützte Anlagen anzeigen, ohne die Anlagen herunterladen und mithilfe der zugeordneten Anwendung öffnen zu müssen.

Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit der Verwaltung von Informationsrechten (IRM) gibt? Weitere Informationen finden Sie hier: [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Aktivieren von IRM in Outlook Web App

Um IRM in Outlook Web App zu aktivieren, müssen Sie das Verbundpostfach, ein vom Exchange 2013-Setup erstelltes Systempostfach, der Administratorengruppe in AD RMS hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md). Dies ermöglicht Exchange 2013-Servern das Zugreifen auf IRM-geschützte Nachrichten.

Außerdem müssen Sie IRM in Outlook Web App aktivieren, indem Sie das Cmdlet [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)) in der Exchange-Verwaltungsshell verwenden. Damit wird IRM in Outlook Web App für Ihre Exchange 2013-Organisation aktiviert. Sie können IRM in Outlook Web App für ein virtuelles Outlook Web App-Verzeichnis aktivieren oder deaktivieren. Außerdem können Sie IRM in Outlook Web App auf den folgenden Granularitätsstufen steuern:

  - **Pro virtuellem Outlook Web App-Verzeichnis**   Verwenden Sie zum Aktivieren oder Deaktivieren von IRM für ein virtuelles Outlook Web App-Verzeichnis das Cmdlet **Set-OWAVirtualDirectory**, und setzen Sie den Parameter *IRMEnabled* auf `$false` oder `$true` (Standard). Auf diese Weise können Sie IRM in Outlook Web App für ein virtuelles Verzeichnis auf einem Exchange 2013-Clientzugriffsserver deaktivieren, während es für ein anderes virtuelles Verzeichnis auf einem anderen Clientzugriffsserver aktiviert bleibt.

  - **Pro Outlook Web App-Postfachrichtlinie**   Verwenden Sie zum Aktivieren oder Deaktivieren von IRM für eine Outlook Web App-Postfachrichtlinie das Cmdlet **Set-OWAMailboxPolicy**, und setzen Sie den Parameter *IRMEnabled* auf `$false` oder `$true` (Standard). So können Sie IRM in Outlook Web App für eine Gruppe von Benutzern aktivieren und für eine andere Gruppe von Benutzern deaktivieren, indem Sie diesen eine andere Outlook Web App-Postfachrichtlinie zuweisen.

Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Verwaltung von Informationsrechten auf Clientzugriffsservern](enable-or-disable-information-rights-management-on-client-access-servers-exchange-2013-help.md).


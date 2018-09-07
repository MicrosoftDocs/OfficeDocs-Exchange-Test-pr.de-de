---
title: 'Adresslisten: Exchange 2013 Help'
TOCTitle: Adresslisten
ms:assetid: 8ee2672a-3a45-4897-8cc0-fa23c374dbf9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232119(v=EXCHG.150)
ms:contentKeyID: 50476156
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Adresslisten

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-12-02_

Eine *Adressliste* ist eine Sammlung von Empfänger- und anderen Active Directory-Objekten. Jede Adressliste kann einen oder mehrere Objekttypen beinhalten (z. B. Benutzer, Kontakte, Gruppen, öffentliche Ordner sowie Raum- und Geräteressourcen). Sie können Adresslisten zum Organisieren von Empfängern und Ressourcen verwenden und auf diese Weise das Auffinden gewünschter Empfänger und Ressourcen vereinfachen. Adresslisten werden dynamisch aktualisiert. Beim Hinzufügen neuer Benutzer zur Organisation werden diese daher automatisch allen entsprechenden Adresslisten hinzugefügt.

Wie in der folgenden Abbildung gezeigt, zeigen Clientanwendungen, z. B. Microsoft Outlook, die verfügbaren Adresslisten an, die von Exchange zur Verfügung gestellt werden.

**Globale Adressliste wie in Microsoft Office Outlook 2007 angezeigt**

![In Outlook 2007 angezeigte Adresslisten](images/Bb232119.54d7729c-2e28-4863-8944-b0c37dabbbb3(EXCHG.150).gif "In Outlook 2007 angezeigte Adresslisten")

Adresslisten befinden sich in Active Directory. Daher wird für Benutzer mobiler Geräte, die die Verbindung mit dem Netzwerk beenden, auch die Verbindung mit diesen Adresslisten beendet. Sie können jedoch Offlineadressbücher für Benutzer erstellen, die vom Netzwerk getrennt sind. Diese Offlineadressbücher können auf die Festplatte des Benutzers heruntergeladen werden. Um Ressourcen zu sparen, handelt es sich bei den OABs häufig um eine Teilmenge der Informationen in den tatsächlichen Adresslisten, die auf den Servern gespeichert sind. Weitere Informationen finden Sie unter [Offlineadressbücher](offline-address-books-exchange-2013-help.md).

**Inhalt**

Standardadresslisten

Benutzerdefinierte Adresslisten

Bewährte Methoden für das Erstellen von Adresslisten

## Standardadresslisten

Wenn Benutzer ihre Clientanwendung zum Suchen nach Empfängerinformationen verwenden möchten, können sie unter den verfügbaren Adresslisten auswählen. Mehrere Adresslisten, z. B. die GAL (Global Address List, globale Adressliste), werden standardmäßig erstellt. Exchange enthält die folgenden Standardadresslisten, die automatisch mit neuen Benutzern, Kontakten, Gruppen oder Räumen belegt werden, sobald diese Ihrer Organisation hinzugefügt werden:

  - **Alle Kontakte**   Diese Adressliste enthält alle E-Mail-aktivierten Kontakte in der Organisation. E-Mail-aktivierte Kontakte sind diejenigen Empfänger, die über eine externe E-Mail-Adresse verfügen. Wenn allen Benutzer in Ihrer Organisation Informationen zu E-Mail-aktivierte Kontakten zur Verfügung stehen sollen, müssen Sie den Kontakt in die GAL aufnehmen. Weitere Informationen zu E-Mail-Kontakten finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

  - **Alle Verteilerlisten**   Diese Adressliste enthält E-Mail-aktivierte Gruppen, wie beispielsweise E-Mail-aktivierte Sicherheitsgruppen, Verteilergruppen und dynamische Verteilergruppen in Ihrer Organisation. E-Mail-aktivierte Gruppen sind Listen von Empfängern, die erstellt wurden, um das Senden einer Vielzahl von E-Mails und anderer Informationen zu beschleunigen. Wenn eine E-Mail-Nachricht an eine E-Mail-aktivierte Gruppe gesendet wird, empfangen alle Mitglieder dieser Liste eine Kopie der Nachricht. Weitere Informationen zu E-Mail-aktivierten Gruppen finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

  - **Alle Räume**   Diese Adressliste enthält alle Ressourcen, die in Ihrer Organisation als Raum definiert wurden. Räume sind Ressourcen in Ihrer Organisation, die durch Senden einer Besprechungsanfrage von einer Clientanwendung geplant werden können. Das einem Raum zugeordnete Benutzerkonto ist deaktiviert. Weitere Informationen zu Ressourcenpostfächern finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

  - **Alle Benutzer**   Diese Adressliste enthält alle E-Mail-aktivierten Benutzer in der Organisation. Ein E-Mail-aktivierter Benutzer ist ein Benutzer außerhalb der Exchange-Organisation. Jeder E-Mail-aktivierte Benutzer verfügt über eine externe E-Mail-Adresse. Alle E-Mail-Nachrichten, die an den E-Mail-aktivierten Benutzer gesendet werden, werden an diese externe Adresse weitergeleitet. Ein E-Mail-aktivierter Benutzer gleicht einem E-Mail-Kontakt mit der Ausnahme, dass ein E-Mail-aktivierter Benutzer über Active Directory-Anmeldeinformationen verfügt und auf Ressourcen zugreifen kann. Weitere Informationen zu E-Mail-aktivierten Benutzern finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

  - **Globale Standardadressliste**   Diese Adressliste enthält alle E-Mail-aktivierten Benutzer, Kontakte, Gruppen oder Räume in der Organisation. Während der Installation erstellt Exchange verschiedene Standardadresslisten. Die bekannteste Adressliste ist die GAL. Die GAL enthält standardmäßig alle Empfänger in einer Exchange-Organisation. Anders ausgedrückt, wird jedes postfachaktivierte oder E-Mail-aktivierte Objekt in einer Active Directory-Gesamtstruktur, in der Exchange installiert ist, in der GAL aufgelistet. Zur einfacheren Verwendung ist die GAL nach Name und nicht nach E-Mail-Adresse organisiert. Weitere Informationen finden Sie unter [Erstellen einer globalen Adressliste](https://review.docs.microsoft.com/de-de/exchange/address-books/address-lists/create-global-address-list).

  - **Öffentliche Ordner**   Diese Adressliste enthält alle Öffentlichen Ordner in der Organisation. In den Zugriffsberechtigungen wird festgelegt, wer die Ordner anzeigen und verwenden kann. Öffentliche Ordner werden auf Computern gespeichert, die Exchange ausführen. Weitere Informationen zu Öffentlichen Ordnern in Exchange 2013 finden Sie unter [Öffentliche Ordner](public-folders-exchange-2013-help.md). Weitere Informationen zu Öffentlichen Ordnern in Exchange Online finden Sie unter [Öffentliche Ordner in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj200758\(v=exchg.150\)).

## Benutzerdefinierte Adresslisten

Eine Exchange-Organisation kann Tausende von Empfängern enthalten. Wenn Sie alle Ihre Empfänger in die Standardadresslisten aufnehmen, können diese Listen sehr groß werden. Um dies zu verhindern, können Sie benutzerdefinierte Adresslisten erstellen, damit die Benutzer in Ihrer Organisation das Gesuchte einfacher finden können.

Angenommen, eine Firma verfügt über zwei Unternehmensbereiche und eine Exchange-Organisation. Ein Bereich namens Fourth Coffee importiert und verkauft Kaffeebohnen. Der andere Bereich, Contoso, Ltd, schließt Versicherungspolicen ab. Bei den meisten alltäglichen Aktivitäten kommunizieren die Mitarbeiter von Fourth Coffee nicht mit den Mitarbeitern von Contoso, Ltd. Um den Mitarbeitern die Suche nach Empfängern zu vereinfachen, die nur im eigenen Bereich enthalten sind, können Sie daher zwei neue benutzerdefinierte Adresslisten erstellen – eine Adressliste für Fourth Coffee und eine Adressliste für Contoso, Ltd. Bei der Suche nach Empfängern in ihrem eigenen Bereich können Mitarbeiter durch diese benutzerdefinierten Adresslisten nur die Adressliste auswählen, die für ihren Bereich gilt. Wenn ein Mitarbeiter jedoch unsicher ist, in welchem Bereich der Empfänger vorhanden ist, kann er die GAL durchsuchen, die alle Empfänger in beiden Bereichen enthält.

Sie können auch Unterkategorien von Adresslisten erstellen, die als hierarchische Adresslisten bezeichnet werden. Beispielsweise können Sie eine Adressliste für alle Empfänger in Manchester und eine weitere Adressliste für alle Empfänger in Stuttgart erstellen.

## Bewährte Methoden für das Erstellen von Adresslisten

Adresslisten können nützliche Tools für Benutzer darstellen, doch sie können auch frustrieren, wenn sie schlecht geplant sind. Beachten Sie die folgenden bewährten Methoden, damit sichergestellt ist, dass die Adresslisten den praktischen Anforderungen Ihrer Benutzer genügen:

  - Erstellen Sie nicht zu viele Adresslisten, um zu verhindern, dass die Benutzer nicht wissen, in welcher Liste sie nach Empfängern suchen sollen.

  - Adresslisten sollten Benutzern das Auffinden von Adressen in der GAL erleichtern.

  - Sie sollten die Adresslisten so benennen, dass Benutzer anhand der Namen der Adresslisten sofort wissen, welche Empfängertypen in der Liste enthalten sind. Wenn Sie Schwierigkeiten haben, Ihre Adresslisten zu benennen, erstellen Sie weniger Listen und weisen die Benutzer darauf hin, dass sie in der globalen Adressliste jede Person in der Organisation finden können.
    

    > [!NOTE]
    > Standardmäßig wird die Adresslistenrolle in Exchange Online keiner Rollengruppe zugewiesen. Für die Verwendung von Cmdlets, die Adresslistenrolle benötigen, müssen Sie die Rolle einer Rollengruppe hinzufügen. Weitere Informationen finden Sie im Abschnitt „Hinzufügen einer Rolle zu einer Rollengruppe“ im Thema <A href="manage-role-groups-exchange-2013-help.md">Verwalten von Rollengruppen</A>.



Genaue Anweisungen zum Erstellen einer Adressliste in Exchange 2013 finden Sie unter [Erstellen einer Adressliste](create-an-address-list-exchange-2013-help.md). Genaue Anweisungen zum Erstellen einer Adressliste in Exchange Online finden Sie unter [Verwalten von Adresslisten in Exchange Online](https://technet.microsoft.com/de-de/library/jj983798\(v=exchg.150\)).


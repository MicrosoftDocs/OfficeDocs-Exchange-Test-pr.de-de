---
title: 'Absender-ID: Exchange 2013 Help'
TOCTitle: Absender-ID
ms:assetid: 0f628f83-df8c-43fb-bf49-7aaa9ec69ab1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996295(v=EXCHG.150)
ms:contentKeyID: 50475085
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Absender-ID

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Der Sender ID-Agent ist ein in Microsoft Exchange Server 2013 verfügbarer Antispam-Agent. Der Sender ID-Agent verwendet die SMTP-Kopfzeile RECEIVED sowie eine Abfrage des DNS-Diensts des sendenden Systems, um die Aktion zu ermitteln, die ggf. für eine eingehende Nachricht ausgeführt werden soll.

"Sender ID" soll dem Identitätswechsel eines Absenders und einer Domäne entgegenwirken, einem Verfahren, das häufig als *Spoofing* bezeichnet wird. Eine *Nachricht mit gefälschtem Absender* ist eine E-Mail-Nachricht, die eine Absenderadresse aufweist, die so geändert wurde, dass sie von einem anderen Absender als dem tatsächlichen Absender der Nachricht zu stammen scheint.

Nachrichten mit gefälschtem Absender enthalten normalerweise eine "Von"- Adresse, die vorgibt, von einer bestimmten Organisation zu stammen. In der Vergangenheit war es relativ einfach, Spoofing der "Von"- Adresse in der SMTP-Sitzung (z. B. in der "MAIL FROM"- Kopfzeile) und in den RFC 2822-Nachrichtendaten (z. B. From: "Masato Kawai" masato@contoso.com) durchzuführen, weil die Kopfzeilen nicht überprüft wurden.

**Inhalt**

Using Sender ID to combat spoofing

Updating your organization's Internet-facing DNS to support Sender ID

Specifying recipients and sender domains to exclude from Sender ID filtering

## Verwenden der Sender ID zur Bekämpfung von Spoofing

Mithilfe der Sender ID wird Spoofing schwieriger. Wenn Sie die Sender ID aktivieren, enthält jede Nachricht einen Sender ID-Status in den Metadaten der Nachricht. Wenn eine E-Mail-Nachricht empfangen wird, fragt der Exchange-Server den DNS-Server des Absenders ab, um zu bestätigen, dass die IP-Adresse, von der die Nachricht empfangen wurde, für das Senden von Nachrichten für die Domäne autorisiert ist, die in den Nachrichtenkopfzeilen angegeben ist. Die IP-Adresse des autorisierten sendenden Servers wird als PRA (Purported Responsible Address) bezeichnet.

Domänenadministratoren veröffentlichen Sender Policy Framework (SPF) Datensätze auf ihren DNS-Servern. SPF-Datensätze identifizieren autorisierten ausgehende e-Mail-Servern. Wenn ein SPF-Datensatzes auf der Adresse des Absenders DNS-Server konfiguriert ist, wird der Exchange-Server analysiert den SPF-Datensatz und bestimmt, ob die IP-Adresse, die von der die Nachricht empfangen wurde autorisiert ist, Senden von e-Mails im Namen der Domäne, die in der Nachricht angegeben ist. Weitere Informationen zu den Inhalt ein SPF-Datensatzes und zum Erstellen eines SPF-Datensatzes finden Sie unter [Sender ID](https://go.microsoft.com/fwlink/p/?linkid=50977).

Der Exchange-Server aktualisiert die Metadaten von Nachrichten mit dem Sender ID-Status auf der Grundlage des SPF-Datensatzes. Nachdem der Exchange-Server die Nachrichtenmetadaten aktualisiert hat, wird die Nachrichtenübermittlung wie üblich fortgesetzt.

## Werte für den Status der Sender ID

Der Auswertungsvorgang der Sender ID generiert einen Sender ID-Status für die Nachricht. Der Sender ID-Status wird verwendet, um die SCL-Bewertung (Spam Confidence Level) für die Nachricht auszuwerten. Dieser Status kann auf einen der folgenden Werte festgelegt werden:

  - **Pass**   Die IP-Adresse und die PRA (Purported Responsible Address) haben die Sender ID-Überprüfung bestanden.

  - **Neutral**   Die veröffentlichten Sender ID-Daten sind explizit nicht eindeutig.

  - **Soft fail**   Die IP-Adresse für die PRA ist möglicherweise im Nicht-Berechtigungssatz enthalten.

  - **Fail**   Die IP-Adresse ist nicht zulässig; die eingehende E-Mail enthält keine PRA, oder die sendende Domäne ist nicht vorhanden.

  - **None**   Es sind keine veröffentlichten SPF-Daten (Sender Policy Framework) im DNS des Absenders vorhanden.

  - **TempError**   Es liegt ein vorübergehender DNS-Fehler vor, z. B. ein nicht verfügbarer DNS-Server.

  - **PermError**   Der DNS-Datensatz ist ungültig, z. B. ein Fehler im Datensatzformat.

Der Sender ID-Status wird den Nachrichtenmetadaten hinzugefügt und später in eine MAPI-Eigenschaft umgewandelt. Der Junk-E-Mail-Filter in Microsoft Outlook verwendet während der Generierung des SCL-Werts die MAPI-Eigenschaft.

Outlook zeigt weder den Status der Sender ID an, noch wird eine Nachricht bei bestimmten Sender ID-Werten notwendigerweise als Junk-E-Mail markiert. Outlook verwendet den Statuswert der Sender ID nur während der Berechnung des SCL-Werts.

Neben den sieben Szenarien, die die Statuswerte der Sender ID generieren, kann der Auswertungsvorgang der Sender ID Fälle aufdecken, in denen die "Von"- IP-Adresse fehlt. Wenn die "Von"- IP-Adresse fehlt, kann der Sender ID-Status nicht festgelegt werden. Wenn der Status der Sender ID nicht festgelegt werden kann, fährt Exchange mit der Verarbeitung der Nachricht fort, ohne einen Sender ID-Status für die Nachricht einzuschließen. Die Nachricht wird nicht verworfen oder zurückgewiesen. In diesem Szenario wird der Sender ID-Status nicht festgelegt, und es wird ein Anwendungsereignis protokolliert.

Weitere Informationen zum Anzeigen von Sender ID-Statusinformationen in Nachrichten finden Sie unter [Antispamstempel](anti-spam-stamps-exchange-2013-help.md).

## Sender ID-Optionen für die Verarbeitung von Nachrichten mit gefälschten Absendern und nicht erreichbaren DNS-Servern

Sie können außerdem definieren, wie der Exchange-Server Nachrichten verarbeitet, die als Nachrichten mit gefälschtem Absender identifiziert werden, und wie der Exchange-Server Nachrichten verarbeitet, wenn ein DNS-Server nicht erreicht werden kann. Die Optionen für die Verarbeitung von Nachrichten mit gefälschtem Absender und nicht erreichbaren DNS-Servern durch den Exchange-Server umfassen die folgenden Aktionen:

  - **Stempeln des Status**   Diese Option ist die Standardaktion. Für alle in Ihrer Organisation eingehenden Nachrichten ist der Sender ID-Status in den Metadaten der Nachricht enthalten.

  - **Nachricht ablehnen**   Diese Option weist die Nachricht zurück und sendet eine SMTP-Fehlerantwort an den sendenden Server. Die SMTP-Fehlerantwort ist eine Protokollantwort auf Stufe 5*xx* mit Text, der dem Sender ID-Status entspricht.

  - **Löschen**   Diese Option löscht die Nachricht, ohne das sendende System über den Löschvorgang zu informieren. Der Exchange-Server sendet tatsächlich einen falschen SMTP-Befehl "OK" an den sendenden Server und löscht dann die Nachricht. Da der sendende Server davon ausgeht, dass die Nachricht gesendet wurde, versucht er nicht, die Nachricht in der gleichen Sitzung erneut zu senden.

Weitere Informationen zum Konfigurieren des Sender ID-Agents finden Sie unter [Verwalten der Absender-ID](manage-sender-id-exchange-2013-help.md).

Zurück zum Seitenanfang

## Aktualisieren der für des Internet verwendeten DNS der Organisation zum Unterstützen von Sender ID

Die Wirksamkeit von "Sender ID" hängt von bestimmten DNS-Daten ab. Je mehr Organisationen ihre für das Internet verwendeten DNS-Server mithilfe eines SPF-Datensatzes aktualisieren, desto wirksamer identifiziert Sender ID gefälschte E-Mail-Nachrichten.

Zur Unterstützung der Sender ID-Infrastruktur müssen Sie Ihre Internet verbundener DNS-Daten durch Erstellen eines SPF-Datensatzes und das hosting der SPF-Eintrag die öffentlichen DNS-Server aktualisieren. Weitere Informationen zum Erstellen und Bereitstellen von SPF-Datensätze finden Sie unter [Sender ID](https://go.microsoft.com/fwlink/p/?linkid=50977).

Zurück zum Seitenanfang

## Angeben von Empfänger- und Absenderdomänen zum Ausschließen von der Sender ID-Filterung

Es empfiehlt sich, bestimmte Empfänger- und Absenderdomänen von der Sender ID-Filterung auszuschließen. Zu diesem Zweck geben Sie die Empfänger- und Absenderdomänen über das Cmdlet **Set-SenderIdConfig** in der Exchange-Verwaltungsshell an. Weitere Informationen finden Sie unter [Set-SenderIdConfig](https://technet.microsoft.com/de-de/library/aa998859\(v=exchg.150\)).

Zurück zum Seitenanfang


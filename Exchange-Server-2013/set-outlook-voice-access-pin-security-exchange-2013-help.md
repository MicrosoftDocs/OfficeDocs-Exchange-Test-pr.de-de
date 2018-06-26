---
title: 'Festlegen von Outlook Voice Access-PIN-Sicherheit: Exchange 2013 Help'
TOCTitle: Festlegen von Outlook Voice Access-PIN-Sicherheit
ms:assetid: ef6d9151-d333-4f52-9338-273f7a291e54
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125162(v=EXCHG.150)
ms:contentKeyID: 50554940
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Festlegen von Outlook Voice Access-PIN-Sicherheit

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-04-16_

Wenn Unified Messaging-Benutzer (UM) sich per Telefon mit dem Voicemailsystem verbinden, nutzen sie für die Navigation durch das Menüsystem Outlook Voice Access. Bevor Benutzer jedoch auf das Voicemailsystem zugreifen können, werden sie vom System zur Eingabe ihrer PIN aufgefordert. Als Administrator können Sie PIN-Einstellungen und -Vorgaben konfigurieren sowie PIN-Verwaltungsaufgaben durchführen. Nachdem ein Benutzer für Voicemail aktiviert und eine PIN für ihn generiert wurde, wird diese PIN verschlüsselt im Postfach des Benutzers gespeichert.


> [!NOTE]
> Zum Eingeben der PIN für den Zugriff auf ein UM-aktiviertes Postfach müssen Outlook Voice Access-Benutzer ein Tastaturwahl- oder DTMF-Telefon (Dual-Tone Multi-Frequency) verwenden. Die Spracherkennung ist für die PIN-Eingabe nicht verfügbar.



**Inhalt**

PIN-Übersicht

PIN-Vorgaben

Verwalten von Outlook Voice Access-PINs

## PIN-Übersicht

Eine PIN ist eine numerische Zeichenfolge, die in bestimmten Systemen verwendet wird, damit ein Benutzer authentifiziert werden kann und Zugriff erhält. PINs werden am häufigsten für Geldautomaten verwendet. PINs werden auch für Voicemailsysteme anstelle alphanumerischer Kennwörter verwendet. Die Sicherheit einer PIN hängt von ihrer Länge, von der Stufe des Schutzes sowie davon ab, wie schwer sie zu erraten ist.

In Unified Messaging geben Outlook Voice Access-Benutzer ihre PIN über ein analoges, digitales oder Mobiltelefon ein, damit sie in ihrem Exchange Server-Postfach auf E-Mail-, Voicemail-, Kontakt- und Kalenderinformationen zugreifen können.

In Unified Messaging werden PIN-Richtlinien in einer UM-Postfachrichtlinie festgelegt und konfiguriert. Je nach Ihren Anforderungen können Sie mehrere UM-Postfachrichtlinien erstellen. Wenn Sie einen Benutzer für Voicemail aktivieren, verknüpfen Sie den Benutzer mit einer vorhandenen UM-Postfachrichtlinie. Die UM-PIN-Richtlinien, die in der UM-Postfachrichtlinie konfiguriert werden, müssen auf den Sicherheitsanforderungen Ihrer Organisation basieren.

## PIN-Vorgaben

Es folgen verschiedene PIN-Konfigurationseinstellungen, die Sie für eine UM-Postfachrichtlinie festlegen können.

## Minimale PIN-Länge

Die Einstellung **Minimale PIN-Länge** gibt die Mindestanzahl der Stellen an, die eine Postfach-PIN aufweisen muss. Der Wertebereich ist 4 bis 24, die Standardeinstellung lautet 6. Bei Eingabe von 0 werden die Benutzer nicht zur Eingabe einer PIN aufgefordert.


> [!IMPORTANT]
> Das Konfigurieren dieser Einstellung mit Null wird nicht empfohlen. Wenn Sie die Einstellung mit Null konfigurieren, verringern Sie die Sicherheitsstufe Ihres Netzwerk erheblich.



Wenn Sie die minimale PIN-Länge in einen höheren Wert ändern, werden derzeitige Outlook Voice Access-Benutzer aufgefordert, eine neue PIN mit der neuen Mindestanzahl von Stellen einzugeben, bevor sie fortfahren können.


> [!NOTE]
> Durch das Erhöhen dieses Werts wird die Sicherheit der UM-Umgebung gesteigert. Ein zu hoher Wert kann allerdings dazu führen, dass die Benutzer ihre PIN vergessen.



## PIN-Gültigkeitsdauer (Tage) erzwingen

Die Einstellung **PIN-Gültigkeitsdauer (Tage) erzwingen** bestimmt den Zeitraum in Tagen ab dem Datum, an dem ein Outlook Voice Access-Benutzer seine PIN zuletzt geändert hat, bis zum Datum, an dem er gezwungen wird, diese erneut zu ändern. Der Wertebereich ist 0 bis 999, der Standardwert lautet 60 Tage. Bei Eingabe von 0 läuft die PIN nicht ab.


> [!NOTE]
> Unified Messaging benachrichtigt Benutzer nicht, wenn ihre PIN in Kürze abläuft.



## Anzahl der Anmeldefehler vor dem Zurücksetzen der PIN

Die **Anzahl der Anmeldefehler vor dem Zurücksetzen der PIN** gibt die Anzahl der aufeinander folgenden erfolglosen Anmeldeversuche an, bevor die Postfach-PIN automatisch zurückgesetzt wird. Um diese Einstellung zu deaktivieren, legen Sie sie auf Unbegrenzt fest. Andernfalls muss der Wert dieser Einstellung niedriger als der Wert der Einstellung **Anzahl der Anmeldefehler vor dem Sperren** sein. Der Wertebereich ist 1 bis 998, der Standardwert lautet 5.


> [!NOTE]
> Um die Sicherheit für UM-aktivierte Benutzer zu erhöhen, geben Sie einen Wert unter 5 ein.



## Anzahl der Anmeldefehler vor dem Sperren

Die Einstellung **Anzahl der Anmeldefehler vor dem Sperren** gibt an, wie viele PIN-Eingabefehler Outlook Voice Access-Benutzer bei aufeinander folgenden Anrufen begehen dürfen, ehe der Zugriff auf ihr Postfach gesperrt wird. Nach 5 Versuchen wird die PIN standardmäßig automatisch zurückgesetzt. Der Wertebereich ist 1 bis 999, der Standardwert lautet 15.


> [!NOTE]
> Verringern Sie zum Erhöhen der Sicherheit die zulässige Anzahl der Fehlversuche. Bei Festlegung auf einen Wert, der wesentlich kleiner als der Standardwert ist, werden Benutzer jedoch ggf. unnötigerweise am Zugriff gehindert. Unified Messaging generiert Warnereignisse, die mithilfe der Ereignisanzeige angezeigt werden können, wenn ein Fehler bei der PIN-Authentifizierung für einen UM-aktivierten Benutzer auftritt oder der Anmeldeversuch des Benutzers am System nicht erfolgreich ist.



## Gängige PIN-Muster zulassen

Die Einstellung **Gängige Muster in PIN zulassen** dient zum Aktivieren oder Deaktivieren der Verwendung gängiger Muster bei der PIN-Erstellung. Diese Einstellung ist standardmäßig deaktiviert und hindert Benutzer von Outlook Voice Access an der Eingabe der folgenden Muster:

  - **Aufeinander folgende Zahlen**   PIN-Werte, die vollständig aus aufeinander folgenden Zahlen bestehen. Beispiele für aufeinander folgende Zahlen sind PINs wie etwa 1234 und 65432.

  - **Wiederholte Zahlen**   PIN-Werte, die ausschließlich aus wiederholten Zahlen bestehen. Beispiele für wiederholte Zahlen sind 11111 und 22222.

  - **Suffix der Postfachdurchwahl**   PIN-Werte, die aus dem Suffix der Postfachdurchwahl eines Benutzers bestehen. Wenn die Postfachdurchwahl 36697 lautet, ist die PIN nicht 6697 erlaubt.

## Anzahl der PIN-Wiederverwendungen

Die Einstellung **Anzahl der PIN-Wiederverwendungen** legt die Anzahl der unterschiedlichen PINs fest, die ein Benutzer verwenden muss, bevor zuvor verwendete PINs erneut verwendet werden dürfen. Der Wertebereich ist 1 bis 20, der Standardwert lautet 5.

## Verwalten von Outlook Voice Access-PINs

Bei der Planung von Outlook Voice Access-PINs müssen Sie die geeigneten Sicherheitsstufen für Ihre Organisation wählen. Sie müssen die Outlook Voice Access-PIN-Vorgaben sorgfältig untersuchen und prüfen, ob Ihre PIN-Sicherheitseinstellungen die Sicherheitsanforderungen Ihrer Organisation erfüllen bzw. übererfüllen.


> [!IMPORTANT]
> Aus Sicherheitsgründen empfiehlt es sich, strenge PIN-Anforderungen für Outlook Voice Access-Benutzer zu implementieren. Dazu empfiehlt sich das Erstellen von Unified Messaging-PIN-Richtlinien, die mindestens sechs Stellen für PINs vorsehen und die Sicherheitsstufe des Netzwerks erhöhen.



Nachdem Sie die Outlook Voice Access-PIN-Vorgaben festgelegt haben, müssen Sie eine UM-Postfachrichtlinie erstellen und konfigurieren, um die PIN-Vorgaben der Organisation durchzusetzen. Details zum Erstellen einer UM-Postfachrichtlinie finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md). Weitere Informationen zum Verwalten von UM-Postfachrichtlinien finden Sie unter [Verwalten einer UM-Postfachrichtlinie](manage-a-um-mailbox-policy-exchange-2013-help.md).


> [!NOTE]
> Nach dem Erstellen der UM-Postfachrichtlinie müssen Sie die UM-aktivierten Benutzer der entsprechenden UM-Postfachrichtlinie zuordnen. Verwenden Sie dazu das Cmdlet <STRONG>Enable-UMMailbox</STRONG> in der Exchange-Verwaltungsshell oder die Exchange-Verwaltungskonsole. Weitere Informationen zum Cmdlet der Exchange-Verwaltungsshell finden Sie unter <A href="https://technet.microsoft.com/de-de/library/aa998033(v=exchg.150)">Enable-UMMailbox</A>.



Es gibt Situationen, in denen Outlook Voice Access-Benutzer ihre PIN vergessen oder ihr Voicemailzugriff gesperrt wird. In beiden Fällen müssen Sie ggf. die PIN eines UM-aktivierten Benutzers zurücksetzen. Weitere Informationen finden Sie unter [Zurücksetzen einer Voicemail-PIN](reset-a-voice-mail-pin-exchange-2013-help.md).

Sie können PIN-Informationen für einen Benutzer abrufen, der für Unified Messaging (UM) aktiviert ist. Die zurückgegebenen Informationen werden mithilfe der verschlüsselten PIN-Daten berechnet, die im Postfach des Benutzers gespeichert sind. So können Sie PIN-Informationen für den Benutzer anzeigen. Außerdem wird angegeben, ob der Benutzer für sein Postfach gesperrt wurde. Weitere Informationen finden Sie unter [Abrufen von PIN-Informationen für Voicemail](retrieve-voice-mail-pin-information-exchange-2013-help.md).


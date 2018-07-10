---
title: 'Erstellen von Schadensberichten für DLP-Richtlinienerkennungen: Exchange 2013 Help'
TOCTitle: Erstellen von Schadensberichten für DLP-Richtlinienerkennungen
ms:assetid: 8e807f94-384c-43f5-be6f-06c5587175a0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150534(v=EXCHG.150)
ms:contentKeyID: 50474808
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen von Schadensberichten für DLP-Richtlinienerkennungen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

In Exchange Server 2013 können Sie eine Aktion zum Erstellen eines Schadensberichts innerhalb eines DLP-Richtlinienregelsatzes einrichten. Außerdem können Sie angeben, an wen der Bericht gesendet werden und was mit der ursprünglichen Nachricht geschehen soll. Der Schadensbericht kann folgende Informationen enthalten.

## Inhalt eines Vorfallmanagementberichts

Die Aktion **Schadensbericht generieren** ermöglicht Benutzern das Senden von Schadensberichten an ein Vorfallmanagement-Postfach. Für jede Nachricht wird nur dann ein einziger Schadensbericht generiert, wenn die Aktion **Schadensbericht generieren** innerhalb einer Richtlinie angewendet wird.

Die folgende Liste zeigt eine vollständige Auflistung der Zeilennamen in der Schadensberichtvorlage. Die Formatspalte beschreibt, wie die einzelnen Felder im Bericht zu erkennen sind. Die Spalte mit optionalen Feldern gibt an, welche Felder möglicherweise nicht für jede Regelübereinstimmung im Bericht aufgeführt werden. Die DLP-spezifische Spalte zeigt, welche Felder aufgrund der DLP-Funktion vorhanden sind.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Zeilen</strong> <strong>name</strong></p></td>
<td><p><strong>Beschreibung</strong></p></td>
<td><p><strong>Format</strong></p></td>
<td><p><strong>Optionales Feld</strong></p></td>
<td><p><strong>DLP-spezifisch</strong></p></td>
</tr>
<tr class="even">
<td><p>Nachrichten-ID</p></td>
<td><p>ID der ursprünglichen gesendeten Nachricht</p></td>
<td><p>Nachrichten-ID: ID der Nachricht</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="odd">
<td><p>Absender</p></td>
<td><p>Tatsächlicher Absender der Originalnachricht</p></td>
<td><p>Absender: E-Mail-Adresse des Absenders</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>Subject</p></td>
<td><p>Betreff der Originalnachricht</p></td>
<td><p>Betreff: Durch den Benutzer eingegebene Betreffdaten</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>An</p></td>
<td><p>Empfänger der ursprünglichen Nachricht</p>
<p>Jede An-Zeile enthält nur einen einzigen Empfänger, und im Schadensbericht können bis zu 10 Empfänger angezeigt werden. Gibt es weitere Empfänger, wird die übrige Anzahl von Empfängern in der nächsten An-Zeile aufgeführt.</p></td>
<td><p>An: E-Mail-Adresse des Empfängers</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>CC</p></td>
<td><p>CC-E-Mail-Adresse der ursprünglichen Nachricht; die Zeile ist optional</p>
<p>Jede CC-Zeile enthält nur eine einzige CC-E-Mail-Adresse, und es können nur bis zu 10 CC-E-Mail-Adressen im Schadensbericht aufgeführt werden. Gibt es weitere CC-Adressen, wird die übrige Anzahl von CC-E-Mail-Adressen in der nächsten CC-Zeile aufgeführt.</p></td>
<td><p>CC: E-Mail-Adresse des CC-Empfängers</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>BCC</p></td>
<td><p>BCC-E-Mail-Adresse der ursprünglichen Nachricht; die Zeile ist optional</p>
<p>Jede BCC-Zeile enthält nur eine einzige BCC-E-Mail-Adresse, und es können nur bis zu 10 BCC-Adressen im Schadensbericht aufgeführt werden. Gibt es weitere BCC-E-Mail-Adressen, wird die übrige Anzahl von BCC-E-Mail-Adressen in der nächsten BCC-Zeile aufgeführt.</p></td>
<td><p>BCC: E-Mail-Adresse des BCC-Empfängers</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>Schweregrad</p></td>
<td><p>Überwachungsschweregrad des Regeltreffers; zeigt den höchsten Schweregrad an, wenn eine Übereinstimmung mit mehreren Regeln vorliegt.</p></td>
<td><p>Schweregrad: Niedrig, Mittel oder Hoch</p></td>
<td><p>Optional</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>Überschreiben</p></td>
<td><p>Zeigt an, wenn für die Nachricht eine Außerkraftsetzung gemeldet wurde, sowie die Begründung für die Außerkraftsetzung, falls vorhanden.</p></td>
<td><p>Außerkraftsetzung: Ja, Begründung: IW (Zeichenfolge zur Eingabe der Begründung)</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Falsch positiv</p></td>
<td><p>Wird angezeigt, wenn ein falsch positives Ergebnis für die Nachricht gemeldet wurde.</p></td>
<td><p>Falsch positiv: Ja</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Datenklassifikation</p></td>
<td><p>Erkannte Datenklassifikationen aus der ursprünglichen Nachricht; die Zeile ist optional.</p>
<p>Jede Datenklassifikationszeile enthält nur eine einzige erkannte Klassifikation zusammen mit der Anzahl, der Bewertung und der empfohlenen Mindestbewertung. Bis zu 5 erkannte Klassifikationen werden im Schadensbericht angezeigt. Handelt es sich bei der erkannten Klassifikation um eine Affinität, ist der Zählwert nicht zutreffend und wird nicht angezeigt.</p></td>
<td><p>Datenklassifikation: vertraulicher Informationstyp, Anzahl: Instanzen der in der Nachricht gefundenen vertraulichen Informationen, Bewertung: Prozentwert, empfohlene Mindestbewertung: Prozentwert</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Regeltreffer</p></td>
<td><p>Zeigt alle Regeln an, die auf die ursprüngliche Nachricht zutreffen.</p>
<p>Enthält den Namen der getroffenen Regel, die DLP-Richtlinie (optional), in der die Regel enthalten ist, die Aktion(en), die aufgrund der Regel an der Nachricht durchgeführt wurde(n), die Datenklassifikation(en) in der Regel, aufgrund derer die Regel zutrifft, sowie die Definition der Regel.</p></td>
<td><p>Regeltreffer: Regelname, DLP-Richtlinie: DLP-Richtlinienname, falls zutreffend, Aktion: einzelne Aktion, Datenklassifikation: vertraulicher Informationstyp, Definition: Regeldefinition, falls zutreffend</p></td>
<td><p>Erforderlich</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>ID-Übereinstimmung</p></td>
<td><p>Zeigt die übereinstimmende Datenklassifikation, den genauen übereinstimmenden Inhalt aus der Nachricht und den Hauptnachweis für die Übereinstimmung der Datenklassifikation an; die Zeile ist optional.</p></td>
<td><p>ID-Übereinstimmung: vertraulicher Informationstyp, Wert: tatsächlicher Wert der vertraulichen Daten, Kontext: Text, der die vertraulichen Daten in der Nachricht umgibt</p></td>
<td><p>Optional</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


## Weitere Informationen

[Anzeigen von DLP-Richtlinienerkennungsberichten](view-dlp-policy-detection-reports-exchange-2013-help.md)

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)


---
title: 'Konfigurieren der Inhaltsübertragungsverschlüsselung: Exchange 2013 Help'
TOCTitle: Konfigurieren der Inhaltsübertragungsverschlüsselung
ms:assetid: c4922362-18d4-42f7-9189-9076720eb1d8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg144562(v=EXCHG.150)
ms:contentKeyID: 50476652
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Inhaltsübertragungsverschlüsselung

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mit der *Inhaltsübertragungscodierung* werden Codierungsmethoden für die Transformation von binären E-Maildaten in das Format "Einfacher US-ASCII-Text" definiert. Diese Transformation ermöglicht die Umleitung der Nachricht über ältere SMTP-Messagingservers, die nur Nachrichten in US-ASCII-Text unterstützen. Die Inhaltsübertragungscodierung ist in RFC 2045 definiert. Die Übertragungscodierungsmethode ist im Kopfzeilenfeld **Content-Transfer-Encoding** der Nachricht gespeichert. In Microsoft Exchange Server 2013 stehen die folgenden Methoden für die Inhaltsübertragungscodierung zur Verfügung:

  - **7-bit**   Dieser Wert gibt an, dass Nachrichtentextdaten bereits im einfachen US-ASCII-Textformat vorliegen und dass für die Nachricht keine Nachrichtencodierung erfolgt ist.

  - **Quoted-printable (QP)**   Diese Codierungsmethode verwendet druckbare US-ASCII-Zeichen zur Codierung der Nachrichtentextdaten. Besteht der ursprüngliche Nachrichtentext hauptsächlich aus US-ASCII-Text, erzeugt die QP-Codierung relativ lesbare und kompakte Ergebnisse. In der Standardeinstellung verwendet Exchange 2013 QP für die Codierung binärer Nachrichtendaten.

  - **Base64**   Diese Codiermethode basiert in erster Linie auf dem PEM-Standard (Privacy-Enhanced Mail), der in RFC 1421 definiert ist. Die Base64-Codierung verwendet die 64-Zeichenalphabet-Codiermethode sowie in PEM definierte Zeichen zum Auffüllen der Ausgabe, um die Nachrichtentextdaten zu codieren. Die Base64-Codierung erzeugt einen vorhersagbaren Zuwachs der Nachrichtengröße und eignet sich optimal für Binärdaten und Nicht-US-ASCII-Text.

Sie konfigurieren die Methode für die Inhaltsübertragungscodierung mit dem Parameter *ByteEncoderTypeFor7BitCharsets* der Cmdlets **Set-OrganizationConfig** und **Set-RemoteDomain**. Die Einstellungen für die Übertragungscodierung, die Sie mit **Set-OrganizationConfig** festlegen, gelten für alle Nachrichten in der Exchange-Organisation. Die Einstellungen für die Inhaltsübertragungscodierung, die Sie mit **Set-RemoteDomain** konfigurieren, gelten nur für Nachrichten, die an externe Empfänger in der Remotedomäne gesendet werden.

Die folgende Tabelle enthält die Werte, mit denen Sie die Methode der Transportcodierung festlegen können.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter in <strong>Set-OrganizationConfig</strong></th>
<th>Parameter in <strong>Set-RemoteDomain</strong></th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p><code>Use7Bit</code></p></td>
<td><p>Für HTML und Nur-Text wird stets die 7-Bit-Codierung verwendet. Dies ist der Standardwert.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p><code>UseQP</code></p></td>
<td><p>Für HTML und einfachen Text wird stets die QP-Codierung verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p><code>UseBase64</code></p></td>
<td><p>Für HTML und einfachen Text wird stets die Base64-Codierung verwendet.</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p><code>UseQPHtmlDetectTextPlain</code></p></td>
<td><p>Die QP-Codierung wird für HTML und einfachen Text verwendet, es sei denn, der Zeilenumbruch ist für einfachen Text aktiviert. Verwenden Sie in diesem Fall die 7-Bit-Codierung für einfachen Text.</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p><code>UseBase64HtmlDetectTextPlain</code></p></td>
<td><p>Die Base64-Codierung wird für HTML und einfachen Text verwendet, es sei denn, der Zeilenumbruch ist für einfachen Text aktiviert. Wenn der Zeilenumbruch für einfachen Text aktiviert ist, verwenden Sie die Base64-Codierung für HTML und die 7-Bit-Codierung für einfachen Text.</p></td>
</tr>
<tr class="even">
<td><p>13</p></td>
<td><p><code>UseQPHtml7BitTextPlain</code></p></td>
<td><p>Die QP-Codierung wird stets für HTML verwendet. Die 7-Bit-Codierung wird stets für einfachen Text verwendet.</p></td>
</tr>
<tr class="odd">
<td><p>14</p></td>
<td><p><code>UseBase64Html7BitTextPlain</code></p></td>
<td><p>Die Base64-Codierung wird stets für HTML verwendet. Die 7-Bit-Codierung wird stets für einfachen Text verwendet.</p></td>
</tr>
</tbody>
</table>


Detaillierte Informationen zum Kopfzeilenfeld **Content-Transfer-Encoding** finden Sie im Abschnitt "Grundlegendes zur Struktur von E-Mails" unter [Inhaltskonvertierung](content-conversion-exchange-2013-help.md).

Weitere Informationen zu Remotedomänen finden Sie unter [Remotedomänen](remote-domains-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportdienst" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren der Methode für die Inhaltsübertragungscodierung der Organisation mit der Shell

Führen Sie zum Konfigurieren der Methode für die Inhaltsübertragungscodierung den folgenden Befehl aus:

```powershell
Set-OrganizationConfig -ByteEncoderTypeFor7BitCharsets <Integer>
```

Führen Sie z. B. folgenden Befehl aus, um die Codierungsmethode für die Inhaltsübertragung auf Base64 festzulegen:

```powershell
Set-OrganizationConfig -ByteEncoderTypeFor7BitCharsets 2
```

## Konfigurieren der Methode für die Inhaltsübertragungscodierung für eine Remotedomäne mit der Shell

Führen Sie zum Konfigurieren der Methode für die Inhaltsübertragungscodierung für alle Empfänger in einer Remotedomäne den folgenden Befehl aus:

```powershell
Set-RemoteDomain -ByteEncoderTypeFor7BitCharsets <Value>
```

Führen Sie z. B. folgenden Befehl aus, um die Codierungsmethode für die Inhaltsübertragung auf Base64 festzulegen:

```powershell
Set- RemoteDomain -ByteEncoderTypeFor7BitCharsets UseBase64
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob Sie die Methode für die Inhaltsübertragungsmethode erfolgreich konfiguriert haben:

1.  Senden Sie eine Testnachricht, die eine Mischung aus US-ASCII-Text und Binärdaten oder Nicht-US-ASCII-Text enthält, an ein internes oder externes Testkonto. Verwenden Sie ein internes Konto zum Testen der Organisationseinstellungen und ein externes Konto in der Remotedomäne zum Testen der Einstellungen der Remotedomäne.

2.  Zeigen Sie in einem E-Mail-Client das Kopfzeilenfeld **Content-Transfer-Encoding** der Nachricht an, und prüfen Sie, ob die in der Nachricht verwendete Methode für die Inhaltsübertragungscodierung der von Ihnen konfigurierten Methode entspricht.


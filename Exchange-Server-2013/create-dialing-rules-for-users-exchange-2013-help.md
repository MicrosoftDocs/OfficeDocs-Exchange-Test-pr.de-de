---
title: 'Erstellen von Wählregeln für Benutzer: Exchange 2013 Help'
TOCTitle: Erstellen von Wählregeln für Benutzer
ms:assetid: c11e3d62-3eb1-4d7e-8741-9bede593e2df
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ898502(v=EXCHG.150)
ms:contentKeyID: 51409339
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen von Wählregeln für Benutzer

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Wählregelgruppen bestehen aus Wählregeleinträgen. Wählregeln werden verwendet, um eine Telefonnummer zu ändern, bevor sie an die lokale Telefonanlage oder IP-Nebenstellenanlage für ausgehende Anrufe gesendet wird. Wählregeln dienen zwei Zwecken:

  - Sie geben die Nummern an, die für ausgehende Anrufe gewählt werden können. Beim Erstellen einer Wählregel geben Sie die Nummernformate an, die gewählt werden können. Entspricht eine Nummer keinem der angegebenen Formate, wird sie abgelehnt. Wenn Sie keine Wählregeln festlegen, können die Anrufer zwar Anrufe innerhalb der Organisation tätigen, ausgehende Anrufe sind jedoch nicht möglich.

  - Sie wandeln die gewählten Nummern um, bevor sie an die lokale Telefonanlage gesendet werden. Mit Wählregeln können Zahlen aus der gewählten Nummer entfernt oder Zahlen zur gewählten Nummer hinzugefügt werden. Sie können beispielsweise mithilfe von Wählregeln die Amtskennziffer für Ihre Telefonanlage hinzufügen oder den Länder-/Regionscode für Fern- oder Ortsgespräche hinzufügen oder entfernen.

Zum Angeben der Typen ausgehender Anrufe, die Sie für einen UM-Wählplan zulassen möchten, erstellen Sie eine Wählregelgruppe mit Wählregeln, mit denen Sie anschließend ausgehende Anrufe für Outlook Voice Access-Benutzer und Anrufer zulassen, die sich in die automatische UM-Telefonzentrale einwählen. Für nationale/regionale Anrufe und internationale Anrufe erstellen Sie gesonderte Wählregeln.


> [!NOTE]
> Wenn Sie UM mit Microsoft Lync Server integrieren, wird empfohlen, dass Sie mindestens eine Wählregelgruppe erstellen und diese in den SIP-URI-Wählplänen, UM-Postfachrichtlinien und automatischen UM-Telefonzentralen für die Weiterleitung ausgehender Anrufe an Server mit Lync autorisieren.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Outdialing finden Sie unter [Ermöglichen, dass Benutzer Anrufe Verfahren stellen](allowing-users-to-make-calls-procedures-exchange-2013-help.md).

## Beispiele für häufig verwendete Wählregeln


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Nummernmuster</strong></p></td>
<td><p><strong>Gewählte Nummer</strong></p></td>
<td><p><strong>Mögliches Szenario für diese Wählregel</strong></p></td>
</tr>
<tr class="even">
<td><p>*</p></td>
<td><p>*</p></td>
<td><p>Ermöglichen aller ausgehenden Anrufe.</p></td>
</tr>
<tr class="odd">
<td><p>1425xxxxxxx</p></td>
<td><p>91425xxxxxxx</p></td>
<td><p>Verhindern, dass Benutzer eine interne Durchwahl anrufen oder ein Fehler auftritt, wenn die Benutzer vergessen, die Amtskennziffer zu wählen.</p></td>
</tr>
<tr class="even">
<td><p>1xxxxxxxxxx</p></td>
<td><p>1xxxxxxxxxx</p></td>
<td><p>Zulassen aller Nummern, die mit &quot;1&quot; beginnen.</p></td>
</tr>
<tr class="odd">
<td><p>xxxxxxx</p></td>
<td><p>1425xxxxxxx</p></td>
<td><p>Hinzufügen einer &quot;1&quot; und der Ortsvorwahl 425 zu siebenstelligen Nummern.</p></td>
</tr>
</tbody>
</table>


## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Wenn Sie Wählregelgruppen auf UM-Postfachrichtlinien anwenden, müssen Sie bestätigen, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Wenn Sie Wählregelgruppen auf automatische UM-Telefonzentralen anwenden, müssen Sie bestätigen, dass eine automatische UM-Telefonzentrale erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Erstellen einer Wählregel mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

3.  Klicken Sie auf der Seite **UM-Wählplan** \> **Wählregeln** unter **Nationale Wählregeln** oder **International Wählregeln** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Geben Sie auf der Seite **Neue Wählregel** die folgenden Informationen ein:
    
      - **Name der Wählregel**   Geben Sie den Namen der Wählregelgruppe ein, der diese Regel angehören soll. Wenn Sie die Regel mit anderen Regeln kombinieren möchten, verwenden Sie den gleichen Gruppennamen. Wenn Sie eine neue Wählregelgruppe erstellen möchten, geben Sie einen neuen eindeutigen Namen ein.
    
      - **Nummernmuster für Transformation (Nummernmaske)**   Geben Sie das Nummernmuster ein, das vor dem Wählen umgewandelt werden soll (beispielsweise "91425xxxxxxx"). Wenn ein Anrufer eine entsprechende Nummer wählt, wird diese von UM in die gewählte Nummer umgewandelt, bevor der Anruf getätigt wird. Geben Sie nur Zahlen und den Platzhalter (x) ein. Das Nummernmuster wird auch als *Nummernmaske* bezeichnet.
    
      - **Gewählte Nummer   **Geben Sie die zu wählende Nummer ein. Verwenden Sie nur Zahlen und den Platzhalter (x) wie beim Nummernmuster "9xxxxxxx". Platzhalter (x) werden mit den Ziffern der Nummer ersetzt, die der Benutzer ursprünglich gewählt hat. Stellen Sie sicher, dass die Anzahl der Platzhalter in der gewählten Nummer der Anzahl der Platzhalter im Nummernmuster entspricht.
    
      - **Kommentar   **Geben Sie einen Kommentar oder eine Beschreibung für diese Wählregel ein. Der Kommentar dient zum Beschreiben der Funktion der Regel (beispielsweise: "Hinzufügen einer 9 zu ausgehenden Anrufen").

5.  Klicken Sie auf **OK**, um die Wählregel zu speichern. Geben Sie ggf. weitere Regeln ein, und verwenden Sie dabei für Regeln, die gemeinsam autorisiert werden sollen, den gleichen Namen für die Wählregelgruppe.


---
title: 'Richtlinientipps verwalten: Exchange 2013 Help'
TOCTitle: Richtlinientipps verwalten
ms:assetid: cec50a35-1d00-47b3-b72f-ac1bb0fd630e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ619307(v=EXCHG.150)
ms:contentKeyID: 50474840
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Richtlinientipps verwalten

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Richtlinientipps sind informative Hinweise, die E-Mail-Absendern beim Verfassen einer Nachricht angezeigt werden. Der Zweck von Richtlinientipps ist es, Benutzern zu vermitteln, dass sie möglicherweise Unternehmenspraktiken oder -richtlinien verletzen, die Sie mit den von Ihnen eingerichteten DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust) durchsetzen möchten. Die folgenden Verfahren helfen Ihnen, mit dem Einsatz von Richtlinientipps zu beginnen. Schauen Sie dieses Video, um mehr zu erfahren.

> [!VIDEO https://www.microsoft.com/de-de/videoplayer/embed/dd629bb7-063d-49f3-b7e1-8f2e0aa4de13]

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 30 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verhinderung von Datenverlust (Data Loss Prevention, DLP)" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Richtlinientipps werden E-Mail-Absendern angezeigt, wenn die folgenden Bedingungen erfüllt sind:
    
    1.  Das Clientprogramm für Nachrichten des Absenders ist Microsoft Outlook 2013. Wenn in Ihrer Organisation Exchange 2013 SP1 bereitgestellt wird oder Exchange Online zum Einsatz kommt, werden Richtlinientipps sowohl in Outlook Web App als auch in OWA für Geräte angezeigt.
    
    2.  Eine Transportregel ist vorhanden, die Benachrichtigungen zu Richtlinientipps aufruft. Sie können eine solche Transportregel erstellen, indem Sie eine DLP-Richtlinie konfigurieren, die die Aktion **Absender mit Richtlinientipp benachrichtigen** enthält.
    
    3.  Der Inhalt eines Nachrichtenkopfs, eines Nachrichtentexts oder einer Nachrichtenanlage, der bzw. die vom Transport-Agent überprüft wird, erfüllt die Bedingungen, die in den DLP-Richtlinien oder -Regeln festgelegt sind, die auch Benachrichtigungsregeln für Richtlinientipps enthalten. Der Richtlinientipp wird also Endbenutzern nur angezeigt, wenn sie etwas tun, das zum Auslösen der zughörigen Regel führt.

  - Der standardmäßige Benachrichtigungstext für Richtlinientipps, der im System implementiert ist, wird angezeigt, wenn Sie nicht mit dem Feature für die Einstellungen von Richtlinientipps den Text von Richtlinientipps anpassen. Weitere Informationen zum Standardtext finden Sie unter [Richtlinientipps](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/policy-tips).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen oder Ändern eines nur als Benachrichtigung dienenden Richtlinientipps

Dieses Verfahren führt zu einem informierenden Richtlinientipp, der einem E-Mail-Absender angezeigt wird, wenn die Bedingungen einer bestimmten Regel erfüllt sind. Mit einem Dialogfeld für Optionen von Richtlinientipps kann der Absender in Microsoft Outlook verhindern, dass der Tipp angezeigt wird. Informationen zum Konfigurieren von benutzerdefiniertem Text für Richtlinientipps finden Sie unter Erstellen von benutzerdefiniertem Benachrichtigungstext für Richtlinientipps.

## Konfigurieren von nur als Benachrichtigung dienenden Richtlinientipps mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Doppelklicken Sie auf eine der Richtlinien in der Richtlinienliste, oder markieren Sie ein Element, und wählen Sie **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **DLP-Richtlinie bearbeiten** die Option **Regeln**.

4.  Zum Hinzufügen von Richtlinientipps zu einer vorhandenen Regel markieren Sie die Regel und wählen **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    Zum Hinzufügen einer neuen leeren Regel, die Sie vollständig anpassen können, wählen Sie **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") und dann **Neue Regel erstellen**.

5.  Wählen Sie unter **Diese Regel anwenden** die Option **Wenn die Nachricht vertrauliche Informationen enthält**. Diese Bedingung ist erforderlich.

6.  Wählen Sie ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), wählen Sie die Arten der vertraulichen Informationen, wählen Sie **Hinzufügen**, wählen Sie **OK**, und wählen Sie dann **OK**.

7.  Wählen Sie im Feld **Folgendes ausführen** die Option **Absender mit Richtlinientipp benachrichtigen**, wählen Sie dann eine Option aus der Dropdownliste zum **Auswählen, ob die Nachricht blockiert ist oder gesendet werden kann** aus, und wählen Sie dann **OK**.

8.  Wenn Sie weitere Bedingungen oder Aktionen hinzufügen möchten, wählen Sie unten im Fenster **Weitere Optionen**.
    

    > [!NOTE]
    > Es können nur die folgenden Bedingungen verwendet werden: 
    > <UL>
    > <LI>
    > <P><STRONG>SentTo (Der Empfänger ist)</STRONG></P>
    > <LI>
    > <P><STRONG>SentToScope (Der Empfänger befindet sich)</STRONG></P>
    > <LI>
    > <P><STRONG>From (Der Absender ist)</STRONG></P>
    > <LI>
    > <P><STRONG>FromMemberOf (Der Absender ist Mitglied von)</STRONG></P>
    > <LI>
    > <P><STRONG>FromScope (Der Absender befindet sich in)</STRONG></P></LI></UL>Die folgenden Aktionen können nicht verwendet werden: 
    > <UL>
    > <LI>
    > <P><STRONG>RejectMessageReasonText (Nachricht ablehnen und Erklärung einschließen)</STRONG></P>
    > <LI>
    > <P><STRONG>RejectMessageEnhancedStatusCode (Nachricht ablehnen mit erweitertem Statuscode)</STRONG></P>
    > <LI>
    > <P><STRONG>DeletedMessage (Löschen der Nachricht ohne Benachrichtigung)</STRONG></P></LI></UL>



9.  Wählen Sie in der Liste zum Auswählen des Modus für diese Regel aus, ob die Regel erzwungen werden soll. Es wird empfohlen, die Regel zuerst zu testen.

10. Wählen Sie **Speichern**, um die Bearbeitung der Regel zu beenden und Ihre Änderungen zu speichern.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritt aus, um zu überprüfen, ob Sie erfolgreich einen Richtlinientipp erstellt haben, mit dem ein Absender nur informiert wird:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Wählen Sie die Richtlinie aus, von der Sie erwarten, dass sie eine Benachrichtigung enthält.

3.  Wählen Sie **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol") und dann **Regeln**.

4.  Wählen Sie die Regel aus, von der Sie erwarten, dass sie eine Benachrichtigung enthält.

5.  Überprüfen Sie, ob die Aktion **Absender benachrichtigen** im unteren Teil der Regelzusammenfassung angezeigt wird.

## Erstellen oder Ändern eines Richtlinientipps zum Blockieren von Nachrichten

Dieses Verfahren führt dazu, dass einem E-Mail-Absender ein Richtlinientipp angezeigt wird, der darauf hinweist, dass eine Nachricht abgelehnt wurde und erst zugestellt wird, wenn die problematische Bedingung nicht mehr gilt. Der Absender kann angeben, dass die E-Mail die problematische Bedingung nicht enthält. Dies wird auch als Außerkraftsetzung eines falsch positiven Ergebnisses bezeichnet. Wenn der Absender dies angibt, kann die Nachricht den Postausgang verlassen, und die Angabe des Benutzers kann überprüft werden. Jedoch wird von Exchange verhindert, dass die Nachricht gesendet wird. Informationen zum Konfigurieren von benutzerdefiniertem Text für Richtlinientipps finden Sie unter Erstellen von benutzerdefiniertem Benachrichtigungstext für Richtlinientipps.

## Konfigurieren von Richtlinientipps zum Blockieren von Nachrichten mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Doppelklicken Sie auf eine der Richtlinien in der Richtlinienliste, oder markieren Sie ein Element, und wählen Sie **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **DLP-Richtlinie bearbeiten** die Option **Regeln**.

4.  Zum Hinzufügen von Richtlinientipps zu einer vorhandenen Regel markieren Sie die Regel und wählen **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

5.  Wählen Sie **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue leere Regel hinzuzufügen, die Sie vollständig anpassen können.

6.  Um eine Aktion hinzuzufügen, mit der ein Richtlinientipp angezeigt wird, wählen Sie **Weitere Optionen** und dann die Schaltfläche **Aktion hinzufügen**.

7.  Wählen Sie in der Dropdownliste **Absender mit Richtlinientipp benachrichtigen** aus, und wählen Sie dann **Nachricht blockieren** aus.

8.  Wählen Sie **OK** und dann **Speichern**, um die Bearbeitung der Regel zu beenden und Ihre Änderungen zu speichern.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie erfolgreich einen Richtlinientipp zum Ablehnen von Nachrichten erstellt haben:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Wählen Sie einmal aus, um die Richtlinie zu markieren, von der Sie annehmen, dass sie eine Benachrichtigungsmeldung enthält.

3.  Wählen Sie **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol") und dann **Regeln**.

4.  Wählen Sie einmal aus, um die Regel zu markieren, von der Sie annehmen, dass sie eine Benachrichtigungsmeldung enthält.

5.  Überprüfen Sie, ob die Aktion **Absender benachrichtigen, dass die Nachricht nicht gesendet werden kann** im unteren Teil der Regelzusammenfassung angezeigt wird.

## Erstellen oder Ändern eines Richtlinientipps zum Blockieren von Nachrichten, sofern keine Außerkraftsetzung erfolgt

Es gibt vier Optionen für Richtlinientipps, mit denen Nachrichten abgelehnt werden können oder mit denen verhindert werden kann, dass Nachrichten den Postausgang des Absenders verlassen. Weitere Informationen zu diesen Optionen finden Sie unter [Richtlinientipps](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/policy-tips).

## Konfigurieren von Richtlinientipps zum Blockieren von Nachrichten, sofern keine Außerkraftsetzung erfolgt, mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Doppelklicken Sie auf eine der Richtlinien in der Richtlinienliste, oder markieren Sie ein Element, und wählen Sie **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **DLP-Richtlinie bearbeiten** die Option **Regeln**.

4.  Zum Hinzufügen von Richtlinientipps zu einer vorhandenen Regel markieren Sie die Regel und wählen **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    Zum Hinzufügen einer neuen leeren Regel, die Sie vollständig anpassen können, wählen Sie **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") und dann **Weitere Optionen**.

5.  Zum Hinzufügen einer Aktion, durch die ein Richtlinientipp angezeigt wird, wählen Sie die Schaltfläche **Aktion hinzufügen**.

6.  Wählen Sie in der Dropdownliste **Absender mit Richtlinientipp benachrichtigen** aus, und wählen Sie dann **Die Nachricht blockieren, dem Absender aber Außerkraftsetzen und Senden gestatten** aus.

7.  Wählen Sie **OK** und dann **Speichern**, um die Bearbeitung der Regel zu beenden und Ihre Änderungen zu speichern.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie erfolgreich einen Richtlinientipp zum Ablehnen von Nachrichten, sofern keine Außerkraftsetzung erfolgt, erstellt haben:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Wählen Sie einmal aus, um die Richtlinie zu markieren, von der Sie annehmen, dass sie eine Benachrichtigungsmeldung enthält.

3.  Wählen Sie **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol") und dann **Regeln**.

4.  Wählen Sie einmal aus, um die Regel zu markieren, von der Sie annehmen, dass sie eine Benachrichtigungsmeldung enthält.

5.  Überprüfen Sie, ob die Aktion **Die Nachricht blockieren, dem Absender aber Außerkraftsetzen und Senden gestatten** im unteren Teil der Regelzusammenfassung angezeigt wird.

## Erstellen von benutzerdefiniertem Benachrichtigungstext für Richtlinientipps

Mithilfe dieses optionalen Verfahrens können Sie den Benachrichtigungstext für Richtlinientipps anpassen, der E-Mail-Absendern in ihrem E-Mail-Programm angezeigt wird. Wenn Sie dieses Verfahren durchführen, wird der benutzerdefinierte Benachrichtigungstext für Richtlinientipps erst angezeigt, wenn Sie zudem eine DLP-Richtlinienregel mit einer Aktion konfigurieren, die die Anzeige der Benachrichtigung auslöst. Bedenken Sie, dass es standardmäßige Systembenachrichtigungen für Richtlinientipps gibt, die angezeigt werden können, wenn Sie den Benachrichtigungstext für Richtlinientipps nicht anpassen. Weitere Informationen zum Standardtext finden Sie unter [Richtlinientipps](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/policy-tips).

## Erstellen und Verwalten von benutzerdefiniertem Benachrichtigungstext für Richtlinientipps mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Wählen Sie **Einstellungen für Richtlinientipps**![Einstellungen für Richtlinientipps](images/JJ619307.54d1813d-3289-4765-a9a3-a7303a5ab3c7(EXCHG.150).gif "Einstellungen für Richtlinientipps").

3.  Wählen Sie **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um einen neuen Richtlinientipp mit Ihrer eigenen angepassten Nachricht hinzuzufügen. Weitere Informationen zu den verfügbaren Aktionsoptionen finden Sie unter [Richtlinientipps](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/policy-tips).
    
    Um einen vorhandenen Richtlinientipp zu ändern, markieren Sie den Tipp, und wählen Sie **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    Um einen vorhandenen Richtlinientipp zu löschen, markieren Sie ihn und wählen **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"). Bestätigen Sie dann die Aktion.

4.  Wählen Sie **Speichern**, um die Bearbeitung des Richtlinientipps zu beenden und Ihre Änderungen zu speichern.

5.  Wählen Sie **Schließen**, um die Verwaltung der Richtlinientipps zu beenden und die Änderungen zu speichern.

## Erstellen von benutzerdefiniertem Benachrichtigungstext für Richtlinientipps mithilfe der Shell

Im folgenden Beispiel wird ein neuer englischer Richtlinientipp erstellt, der das Senden einer Nachricht verhindert. Der Text dieser benutzerdefinierten Richtlinieninfo wird in den folgenden Wert geändert: "This message appears to contain restricted content and will not be delivered."

    New-PolicyTipConfig -Name en\Reject -Value "This message appears to contain restricted content and will not be delivered."

Weitere Informationen zu DLP-Cmdlets finden Sie unter [Richtlinien- und Richtlinientreue-Cmdlets](https://technet.microsoft.com/de-de/library/dd298082\(v=exchg.150\)).

## Ändern von benutzerdefiniertem Benachrichtigungstext für Richtlinientipps mithilfe der Shell

Im folgenden Beispiel wird ein vorhandener englischer Richtlinientipp, der nur der Benachrichtigung dient, geändert. Der Text dieses benutzerdefinierten Richtlinientipps wird in "Sending bank account numbers in email is not recommended" geändert.

    Set-PolicyTipConfig en\NotifyOnly "Sending bank account numbers in email is not recommended."

Weitere Informationen zu DLP-Cmdlets finden Sie unter [Richtlinien- und Richtlinientreue-Cmdlets](https://technet.microsoft.com/de-de/library/dd298082\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie erfolgreich einen benutzerdefinierten Text für Richtlinientipps erstellt haben:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Wählen Sie **Einstellungen für Richtlinientipps**![Einstellungen für Richtlinientipps](images/JJ619307.54d1813d-3289-4765-a9a3-a7303a5ab3c7(EXCHG.150).gif "Einstellungen für Richtlinientipps").

3.  Wählen Sie **Aktualisieren**![Aktualisieren (Symbol)](images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif "Aktualisieren (Symbol)").

4.  Überprüfen Sie, ob die Aktion, das Gebietsschema und der Text für das Gebietsschema in der Liste angezeigt werden.

## Weitere Informationen

[Verhinderung von Datenverlust](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)

[Richtlinientipps](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/policy-tips)

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)Exchange 2013

[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\))Exchange Online

[Exchange 2010 E-Mail-Info](https://go.microsoft.com/fwlink/?linkid=265179)


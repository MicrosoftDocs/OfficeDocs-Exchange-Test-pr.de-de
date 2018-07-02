---
title: 'Erstellen eines UM-Wählplans: Exchange 2013 Help'
TOCTitle: Erstellen eines UM-Wählplans
ms:assetid: 963ff2e1-515d-439a-953a-664174e5e283
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)
ms:contentKeyID: 50476265
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.CreateUMDialPlanWizardForm.CreateUMDialPlanWizardPage
ms.translationtype: HT
---

# Erstellen eines UM-Wählplans

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-16_

In einem Unified Messaging (UM)-Wählplan sind die Konfigurationsinformationen enthalten, die Ihr Telefonienetzwerk betreffen. UM-Wähleinstellungen richten eine Verknüpfung zwischen der Telefon-Durchwahlnummer eines Voicemail-aktivierten Benutzers und seinem Postfach ein. Wenn Sie UM-Wähleinstellungen erstellen, können Sie die Anzahl der Ziffern in den Durchwahlnummern, den URI-Typ (Uniform Resource Identifier) und die VoIP-Sicherheitseinstellung (Voice over IP) für die Wähleinstellungen konfigurieren.

Immer, wenn UM-Wähleinstellungen erstellt werden, wird gleichzeitig eine UM-Postfachrichtlinie erstellt. Die UM-Postfachrichtlinie wird als \<*Wähleinstellungenname*\>-Standardrichtlinie bezeichnet.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen von UM-Wähleinstellungen mithilfe der Exchange-Verwaltungskonsole

1.  
    
    Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, und klicken Sie dann auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Füllen Sie auf der Seite **Neue UM-Wähleinstellungen** folgende Felder aus:
    
      - **Name**   Geben Sie den Namen für die Wähleinstellungen ein. Ein Name für die UM-Wähleinstellungen ist erforderlich und muss eindeutig sein. Er wird allerdings nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell verwendet. Wenn Sie den Anzeigenamen der Wähleinstellungen nach dem Erstellen ändern müssen, müssen zuerst die vorhandenen UM-Wähleinstellungen gelöscht und dann andere Wähleinstellungen mit dem entsprechenden Namen erstellt werden. Wenn in Ihrer Organisation verschiedene UM-Wähleinstellungen verwendet werden, empfiehlt sich die Verwendung aussagekräftiger Namen für die UM-Wähleinstellungen. Der Name der UM-Wähleinstellungen kann eine Länge von maximal 64 Zeichen haben und Leerzeichen enthalten. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
        
        Auch wenn der Name von UM-Wähleinstellungen Leerzeichen enthalten darf, ist bei der Integration von Unified Messaging in Office Communications Server 2007 R2 oder Microsoft Lync Server die Verwendung von Leerzeichen im Namen von Wähleinstellungen nicht zulässig. Wenn Sie daher Wähleinstellungen mit Leerzeichen im Anzeigenamen erstellt haben und Sie eine Integration in Office Communications Server 2007 R2 oder Lync Server durchführen, müssen Sie diese Wähleinstellungen zunächst löschen und einen anderen Satz von Wähleinstellungen erstellen, der keine Leerzeichen im Anzeigenamen aufweist.
        

        > [!IMPORTANT]
        > Das Feld für den Wählplannamen kann zwar 64&nbsp;Zeichen aufnehmen, der Wählplanname darf jedoch höchstens 49&nbsp;Zeichen umfassen. Wenn Sie versuchen, einen Namen von Wähleinstellungen mit mehr als 49 Zeichen zu erstellen, wird eine Fehlermeldung angezeigt. Die Meldung besagt, dass die UM-Postfachrichtlinie nicht generiert werden konnte, weil der Name der UM-Wähleinstellungen zu lang ist. Das liegt daran, dass wie erwähnt bei der Erstellung der Wähleinstellungen auch eine UM-Standardpostfachrichtlinie mit dem Namen "Standardrichtlinie für <EM>&lt;Name_der_Wähleinstellungen&gt;</EM>" erstellt wird. Wenn die Zeichen für "Standardrichtlinie" dem Namen der Wähleinstellungen hinzugefügt werden, überschreitet die Gesamtlänge den Grenzwert. Der Parameter <EM>name</EM> für die UM-Wähleinstellungen und die UM-Postfachrichtlinie kann eine Länge von 64 Zeichen haben. Wenn der Name der Wähleinstellungen allerdings aus mehr als 49 Zeichen besteht, hat der Name der standardmäßigen UM-Postfachrichtlinie eine Länge von mehr als 64 Zeichen. Dies wird vom System nicht unterstützt.

    
      - **Durchwahllänge (Stellen)**   Geben Sie die Anzahl der Stellen für die Wähleinstellungen ein. Die Anzahl der Stellen für Durchwahlnummern basiert auf den Telefoniewähleinstellungen, die auf einer Nebenstellenanlage (Private Branch eXchange, PBX) oder IP-Nebenstellenanlage erstellt werden. Wenn beispielsweise ein Benutzer, der bestimmten Telefoniewähleinstellungen zugeordnet ist, eine 4-stellige Durchwahl wählt, um einen anderen Benutzer mit den gleichen Telefoniewähleinstellungen anzurufen, dann wählen Sie 4 als die Anzahl der Stellen in der Durchwahl aus.
        
        Dies ist ein erforderliches Feld mit Werten im Bereich von 1 bis 20. Die typische Durchwahllänge liegt zwischen 3 und 7. Wenn die vorhandene Telefonieumgebung Durchwahlnummern umfasst, dann müssen Sie eine Anzahl für die Stellen festlegen, die mit der Anzahl der Stellen in diesen Durchwahlnummern übereinstimmt.
        
        Auch wenn Sie SIP- oder E.164-Wähleinstellungen (Session Inititation Protocol) erstellen und einen UM-aktivierten Benutzer diesen Wähleinstellungen zuordnen, müssen Sie dennoch eine Durchwahlnummer eingeben, die von diesem Benutzer verwendet wird. Die Nummer wird von Outlook Voice Access-Benutzern verwendet, wenn sie auf ihr Postfach zugreifen.
    
      - UNRESOLVED\_TOKENBLOCK\_VAL(UI\_URI-Typ)
    
      - UNRESOLVED\_TOKENBLOCK\_VAL(UI\_VoIP-Sicherheit)
    
      - **Audiosprache**   Mithilfe dieser Liste können Sie die von Outlook Voice Access-Benutzern zu verwendende Standardsprache festlegen. Diese Einstellung gilt nicht für die Spracheinstellung einer automatischen UM-Telefonzentrale. Sie können für Outlook Voice Access dieselbe oder eine andere Sprache wie für eine automatische UM-Zentrale festlegen. Wenn ein Benutzer einen Benutzer anruft, der mit bestimmten Wähleinstellungen verbunden ist, ist die Audiosprache die Standardsprache, die bei Sprachaufzeichnungen der Vermittlungsstelle verwendet wird. Die Systemansagen, die ein Anrufer hört, werden in derselben Sprache wiedergegeben. Die in den UM-Wähleinstellungen gewählte Sprache dient zum Vorlesen von E-Mails, Voicemails und Kalenderelementen, Sagen des Namens des Benutzers, wenn eine persönliche Begrüßungsnachricht nicht aufgezeichnet wurde, Transkribieren einer Sprachnachricht mithilfe des Voicemailvorschau-Features und Aktivieren des ordnungsgemäßen Betriebs der automatischen Spracherkennung.
    
      - **Länder-/Regionscode**   Verwenden Sie dieses Feld zur Eingabe des Länder-/Regionscodes für ausgehende Anrufe. Diese Nummer wird vor der eigentlichen Telefonnummer gewählt. In diesem Feld werden nur 1 bis 4 Ziffern akzeptiert. In den USA wird beispielsweise als Landes-/Regionskennzahl 1, in Großbritannien 44 verwendet.

3.  Klicken Sie auf **Speichern**.

## Erstellen von UM-Wähleinstellungen mithilfe der Shell

In diesem Beispiel werden neue UM-Wähleinstellungen mit dem Namen `MyUMDialPlan` erstellt, in denen 4-stellige Durchwahlnummern verwendet werden.

    New-UMDialplan -Name MyUMDialPlan -NumberofDigits 4

In diesem Beispiel werden neue UM-Wähleinstellungen mit dem Namen `MyUMDialPlan` erstellt, in denen 5-stellige Durchwahlnummern verwendet und SUP-URIs unterstützt werden.

    New-UMDialplan -Name MyUMDialPlan -UriType SIPName -NumberofDigits 5


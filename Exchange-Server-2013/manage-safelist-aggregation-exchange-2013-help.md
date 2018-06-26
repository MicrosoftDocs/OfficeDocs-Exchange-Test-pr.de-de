---
title: 'Verwalten der Aggregation von Listen sicherer Adressen: Exchange 2013 Help'
TOCTitle: Verwalten der Aggregation von Listen sicherer Adressen
ms:assetid: 5ac17168-f411-4cb7-ae98-ebefb865b210
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998280(v=EXCHG.150)
ms:contentKeyID: 50475747
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten der Aggregation von Listen sicherer Adressen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

*Aggregation von Listen sicherer Adressen* bezieht sich auf eine Antispamfunktionalität, die von Microsoft Outlook bis Microsoft Exchange Server 2013 gemeinsam genutzt wird. Diese Funktionalität sammelt Daten aus Listen sicherer Empfänger, Listen sicherer Absender, Listen blockierter Absender und Kontaktdaten, die Outlook-Benutzer konfigurieren, und stellt diese Daten den Antispam-Agents von Exchange zur Verfügung. Die Aggregation von Listen sicherer Adressen dient zum Verringern des Vorkommens falsch positiver Ergebnisse bei der Antispamfilterung durch die Exchange-Server, auf denen Antispam-Agents ausgeführt werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md), und Abschnitt "Antispamfunktionen" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Berücksichtigen Sie den Netzwerk- und Replikationsdatenverkehr, der bei der Ausführung des Cmdlets **Update-SafeList** möglicherweise hervorgerufen wird. Wenn der Befehl für mehrere Postfächer ausgeführt wird, die in großem Umfang von Listen sicherer IP-Adressen Gebrauch machen, kann dies erheblichen Datenverkehr verursachen. Wenn der Befehl für mehrere Postfächer ausgeführt werden soll, ist es empfehlenswert, den Befehl außerhalb von Spitzen- und Arbeitszeiten auszuführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren von Grenzwerten für die Erfassung von Listen sicherer Adressen für Postfächer mithilfe der Shell

Sie können die maximale Anzahl sicherer und blockierter Absender konfigurieren, die ein Benutzer konfigurieren kann. Standardmäßig können Benutzer bis zu 5.000 sichere Absender und 500 blockierte Absender konfigurieren.

Führen Sie den folgenden Befehl aus, um die maximale Anzahl von sicheren und blockierten Absendern zu konfigurieren:

    Set-Mailbox <MailboxIdentity> -MaxSafeSenders <Integer> -MaxBlockedSenders <Integer>

In diesem Beispiel wird für das Postfach "john@contoso.com" ein Maximum von 2.000 sicheren Absendern und 200 blockierten Absendern konfiguriert.

    Set-Mailbox john@contoso.com -MaxSafeSenders 2000 -MaxBlockedSenders 200

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Grenzwerten für die Erfassung von Listen sicherer Adressen für Postfächer erfolgreich konfiguriert wurden:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-Mailbox <Identity> | Format-List Name,Max*Senders

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

## Verwenden der Shell zum Ausführen des Befehls "Update-Safelist"

In Exchange 2013 erfolgt die Aggregation von Listen sicherer Adressen automatisch. Sie müssen das Cmdlet **Update-Safelist** deshalb weder manuell ausführen noch dessen Ausführung planen. Sie können dieses Cmdlet jedoch von Zeit zu Zeit ausführen, um die Aggregation von Listen sicherer Absender zu testen.

In diesem Beispiel wird die Liste sicherer Absender für das Postfach "john@contoso.com" in Active Directory geschrieben.

    Update-Safelist john@contoso.com -Type SafeSenders

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Update-SafeList](https://technet.microsoft.com/de-de/library/bb125034\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Schritte aus, um die erfolgreiche Konfiguration der Aggregation von Listen sicherer Adressen zu überprüfen:

## Schritt 1: Überprüfen der Aktivierung des Inhaltsfilter-Agents auf dem Exchange-Server mithilfe der Shell

1.  Führen Sie den folgenden Befehl aus:
    
        Get-ContentFilterConfig | Format-List Enabled

2.  Wenn die Ausgabe den Parameter *Enabled* mit dem Wert `True` zeigt, ist die Inhaltsfilterung aktiviert. Andernfalls führen Sie den folgenden Befehl aus, um die Inhaltsfilterung und den Inhaltsfilter-Agent auf dem Exchange-Server zu aktivieren:
    
        Set-ContentFilterConfig -Enabled $true

## Schritt 2: (Optional) Überprüfen der Replikation der Daten zur Aggregation von Listen sicherer Adressen auf die Edge-Transport-Server mithilfe von ADSI Edit

Dieser Schritt ist nur erforderlich, wenn Sie den Inhaltsfilter-Agent auf einem Edge-Transport-Server in Ihrem Umkreisnetzwerk ausführen.

Sie können die Benutzerobjekte in der Active Directory Lightweight Directory Services-Instanz (AD LDS) auf dem Edge-Transport-Server anzeigen, um zu überprüfen, ob die Sammlungsdaten der Listen sicherer Adressen für die Benutzerobjekte aktualisiert werden und ob der Microsoft Exchage-EdgeSync-Dienst die Daten an die AD LDS-Instanz repliziert hat.

Es gibt drei Attribute für die Sammlung von Listen sicherer Adressen für jedes Benutzerobjekt:

  - **msExchSafeRecipientsHash**   Dieses Attribut speichert den Hash der Sammlung der Liste sicherer Empfänger für den betreffenden Benutzer.

  - **msExchSafeSendersHash**   Dieses Attribut speichert den Hash der Sammlung der Liste sicherer Absender für den betreffenden Benutzer.

  - **msExchBlockedSendersHash**   Dieses Attribut speichert den Hash der Sammlung der Liste blockierter Absender für den betreffenden Benutzer.

Wenn eine hexadezimale Zeichenfolge, wie etwa `0xac 0xbd 0x03 0xca` im Attribut vorhanden ist, wurde das Benutzerobjekt aktualisiert. Wenn das Attribut einen Wert von `<Not Set>` aufweist, wurde es nicht aktualisiert.

Die Attribute können mithilfe des AD LDS-ADSI EditSnap-Ins (Active Directory Service Interfaces) gesucht und angezeigt werden.

## Schritt 3: Senden einer Testnachricht zur Überprüfung der ordnungsgemäßen Funktion der Aggregation von Listen sicherer Adressen

Zum Testen der ordnungsgemäßen Funktion der Aggregation von Listen sicherer Adressen müssen Sie sich selbst eine Nachricht von einem sicheren Absender schicken, der andernfalls durch die Inhaltsfilterung blockiert würde. Wenn die Aggregation von Listen sicherer Adressen funktioniert, sollte die Nachricht in Ihrem Posteingang ankommen.

1.  Suchen Sie nach einem externen E-Mail-Konto, das Sie verwenden können, oder erstellen Sie ein E-Mail-Konto bei einem kostenlosen webbasierten E-Mail-Anbieter wie z. B. Microsoft Hotmail.

2.  Fügen Sie dieses Konto der Liste sicherer Absender in Microsoft Outlook hinzu.

3.  Kopieren Sie die Sammlung von Listen sicherer Absender aus dem Postfach mithilfe des Cmdlets **Update-SafeList** in Active Directory.

4.  Optional: Wenn Sie den Inhaltsfilter-Agent auf einem Edge-Transport-Server im Umkreisnetzwerk ausführen, verwenden Sie das Cmdlet **Start-EdgeSynchronization**, um eine EdgeSync-Replikation zu erzwingen.

5.  Fügen Sie Ihrer Inhaltsfilterungskonfiguration ein bestimmtes Wort als blockierten Ausdruck hinzu. Weitere Informationen finden Sie unter [Verwalten der Inhaltsfilterung](manage-content-filtering-exchange-2013-help.md).

6.  Senden Sie über das in Schritt 1 erstellte externe E-Mail-Konto eine Nachricht mit dem in Schritt 5 konfigurierten blockierten Ausdruck an Ihr Exchange-Postfach.
    
    Wenn die Nachricht erfolgreich an Ihren Posteingang gesendet wird, funktioniert die Aggregation von Listen sicherer Adressen ordnungsgemäß.


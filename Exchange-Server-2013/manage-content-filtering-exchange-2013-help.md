---
title: 'Verwalten der Inhaltsfilterung: Exchange 2013 Help'
TOCTitle: Verwalten der Inhaltsfilterung
ms:assetid: 05bd9d39-81dc-4514-8b75-7be386d5bcad
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa995953(v=EXCHG.150)
ms:contentKeyID: 50474973
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten der Inhaltsfilterung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Die Inhaltsfilterung wird durch den Inhaltsfilter-Agent bereitgestellt. Der Inhaltsfilter-Agent filtert alle Nachrichten, die durch alle Empfangsconnectors auf dem Exchange-Server eingehen. Nur Nachrichten aus nicht authentifizierten Quellen werden gefiltert.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfunktion" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Aktivieren oder Deaktivieren der Inhaltsfilterung

Führen Sie zum Deaktivieren der Inhaltsfilterung folgenden Befehl aus:

```powershell
Set-ContentFilterConfig -Enabled $false
```

Führen Sie den folgenden Befehl aus, um die Inhaltsfilterung zu aktivieren:

```powershell
Set-ContentFilterConfig -Enabled $true
```


> [!NOTE]
> Wenn Sie die Inhaltsfilterung deaktivieren, bleibt der zugrunde liegende Inhaltsfilter-Agent weiterhin aktiviert. Führen Sie den folgenden Befehl aus, um den Inhaltsfilter-Agent zu deaktivieren: <CODE>Disable-TransportAgent "Content Filter Agent"</CODE>.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Inhaltsfilterung erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-ContentFilterConfig | Format-List Enabled
    ```

2.  Überprüfen Sie den angezeigten Wert der Eigenschaft *Enabled*.

## Aktivieren oder Deaktivieren der Inhaltsfilterung für externe Nachrichten mithilfe der Shell

Standardmäßig ist die Funktionalität zur Inhaltsfilterung für externe Nachrichten aktiviert.

Führen Sie den folgenden Befehl aus, um die Inhaltsfilterung für externe Nachrichten zu deaktivieren:

```powershell
Set-ContentFilterConfig -ExternalMailEnabled $false
```

Führen Sie den folgenden Befehl aus, um die Inhaltsfilterung für externe Nachrichten zu aktivieren:

```powershell
Set-ContentFilterConfig -ExternalMailEnabled $true
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Inhaltsfilterung für externe Nachrichten erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-ContentFilterConfig | Format-List ExternalMailEnabled
    ```

2.  Überprüfen Sie den angezeigten Wert der Eigenschaft *ExternalMailEnabled*.

## Aktivieren oder Deaktivieren der Inhaltsfilterung für interne Nachrichten mithilfe der Shell

Als bewährte Methode hat sich herausgestellt, Nachrichten von vertrauenswürdigen Partnern oder aus der eigenen Organisation nicht zu filtern. Beim Ausführen von Antispamfiltern besteht immer die Gefahr, dass die Filter falsch positive Ergebnisse ermitteln. Sie sollten Antispam-Agents nur für Nachrichten aus möglicherweise nicht vertrauenswürdigen und unbekannten Quellen aktivieren, um die Gefahr zu verringern, dass legitime E-Mail-Nachrichten durch Filter falsch eingeordnet werden.

Führen Sie den folgenden Befehl aus, um die Inhaltsfilterung für interne Nachrichten zu aktivieren:

```powershell
Set-ContentFilterConfig -InternalMailEnabled $true
```

Führen Sie den folgenden Befehl aus, um die Inhaltsfilterung für interne Nachrichten zu deaktivieren:

```powershell
Set-ContentFilterConfig -InternalMailEnabled $false
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Inhaltsfilterung für interne Nachrichten erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-ContentFilterConfig | Format-List InternalMailEnabled
    ```

2.  Überprüfen Sie den angezeigten Wert der Eigenschaft *InternalMailEnabled*.

## Konfigurieren von Empfänger- und Absenderausnahmen mithilfe der Verwaltungsshell

Führen Sie den folgenden Befehl aus, um die vorhandenen Werte zu ersetzen:

```powershell
Set-ContentFilterConfig -BypassedRecipients <recipient1,recipient2...> -BypassedSenders <sender1,sender2...> -BypassedSenderDomains <domain1,domain2...>
```

In diesem Beispiel werden die folgenden Ausnahmen für die Inhaltsfilterung konfiguriert:

  - Die Empfänger "laura@contoso.com" und "julia@contoso.com" werden bei der Inhaltsfilterung nicht überprüft.

  - Die Absender "steve@fabrikam.com" und "cindy@fabrikam.com" werden bei der Inhaltsfilterung nicht überprüft.

  - Alle Absender in der Domäne "nwtraders.com" und allen Unterdomänen werden bei der Inhaltsfilterung nicht überprüft.

<!-- end list -->

```powershell
Set-ContentFilterConfig -BypassedRecipients laura@contoso.com,julia@contoso.com -BypassedSenders steve@fabrikam.com,cindy@fabrikam.com -BypassedSenderDomains *.nwtraders.com
```

Führen Sie folgenden Befehl aus, um Einträge hinzuzufügen bzw. zu entfernen, ohne vorhandene Werte zu ändern:

```powershell
Set-ContentFilterConfig -BypassedRecipients @{Add="<recipient1>","<recipient2>"...; Remove="<recipient1>","<recipient2>"...} -BypassedSenders @{Add="<sender1>","<sender2>"...; Remove="<sender1>","<sender2>"...} -BypassedSenderDomains @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...}
```

In diesem Beispiel werden die folgenden Ausnahmen für die Inhaltsfilterung konfiguriert:

  - "tiffany@contoso.com" und "chris@contoso.com" werden zur Liste der vorhandenen Empfänger hinzugefügt, die bei der Inhaltsfilterung nicht überprüft werden.

  - "joe@fabrikam.com" und "michelle@fabrikam.com" werden zur Liste der vorhandenen Absender hinzugefügt, die bei der Inhaltsfilterung nicht überprüft werden.

  - "blueyonderairlines.com" wird zur Liste der vorhandenen Domänen hinzugefügt, deren Absender bei der Inhaltsfilterung nicht überprüft werden.

  - Die Domäne "woodgrovebank.com" und alle Unterdomänen werden aus der Liste der vorhandenen Domänen entfernt, deren Absender bei der Inhaltsfilterung nicht überprüft werden.

<!-- end list -->

```powershell
Set-ContentFilterConfig -BypassedRecipients @{Add="tiffany@contoso.com","chris@contoso.com"} -BypassedSenders @{Add="joe@fabrikam.com","michelle@fabrikam.com"} -BypassedSenderDomains @{Add="blueyonderairlines.com"; Remove="*.woodgrovebank.com"}
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Ausnahmen für Empfänger und Absender erfolgreich konfiguriert wurden:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-ContentFilterConfig | Format-List Bypassed*
    ```

2.  Überprüfen Sie, ob die angezeigten Werte den Einstellungen entsprechen, die Sie angegeben haben.

## Konfigurieren zugelassener und blockierter Ausdrücke mithilfe der Verwaltungsshell

Führen Sie den folgenden Befehl aus, um zulässige und blockierte Wörter und Ausdrücke hinzuzufügen:

```powershell
Add-ContentFilterPhrase -Influence GoodWord -Phrase <Phrase> -Influence BadWord -Phrase <Phrase>
```

In diesem Beispiel werden alle Nachrichten mit dem Text "customer feedback" zugelassen.

```powershell
Add-ContentFilterPhrase -Influence GoodWord -Phrase "customer feedback"
```

In diesem Beispiel werden alle Nachrichten mit dem Text "stock tip" blockiert.

```powershell
Add-ContentFilterPhrase -Influence BadWord -Phrase "stock tip"
```

Führen Sie den folgenden Befehl aus, um zulässige oder blockierte Ausdrücke zu entfernen:

```powershell
Remove-ContentFilterPhrase -Phrase <Phrase>
```

In diesem Beispiel wird der Ausdruck "stock tip" entfernt:

```powershell
Remove-ContentFilterPhrase -Phrase "stock tip"
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die zulässigen und blockierten Ausdrücke erfolgreich konfiguriert wurden:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-ContentFilterPhrase | Format-List Influence,Phrase
    ```

2.  Überprüfen Sie, ob die angezeigten Werte den Einstellungen entsprechen, die Sie angegeben haben.

## Konfigurieren von SCL-Schwellenwerten mithilfe der Verwaltungsshell

Führen Sie den folgenden Befehl aus, um die SCL (Spam Confidence Level)-Schwellenwerte und -Aktionen zu konfigurieren:

```powershell
Set-ContentFilterConfig -SCLDeleteEnabled <$true | $false> -SCLDeleteThreshold <Value> -SCLRejectEnabled <$true | $false> -SCLRejectThreshold <Value> -SCLQuarantineEnabled <$true | $false> -SCLQuarantineThreshold <Value>
```

> [!NOTE]  
> Die Löschaktion hat Vorrang vor der Zurückweisungsaktion, und die Zurückweisungsaktion hat Vorrang vor der Isolieraktion. Daher muss der SCL-Schwellenwert für die Löschaktion größer sein als der SCL-Schwellenwert für die Zurückweisungsaktion, deren SCL-Schwellenwert wiederum größer als der der Isolieraktion sein muss. Standardmäßig ist nur die Zurückweisungsaktion aktiviert. Für diese Aktion ist der SCL-Schwellenwert&nbsp;7 festgelegt.

In diesem Beispiel werden die folgenden Werte für die SCL-Schwellenwerte konfiguriert:

  - Die Löschaktion wird aktiviert, und der zugehörige SCL-Schwellenwert wird auf 9 festgelegt.

  - Die Zurückweisungsaktion wird aktiviert, und der zugehörige SCL-Schwellenwert wird auf 8 festgelegt.

  - Die Isolieraktion wird aktiviert, und der zugehörige SCL-Schwellenwert wird auf 7 festgelegt.

<!-- end list -->

```powershell
Set-ContentFilterConfig -SCLDeleteEnabled $true -SCLDeleteThreshold 9 -SCLRejectEnabled $true -SCLRejectThreshold 8 -SCLQuarantineEnabled $true -SCLQuarantineThreshold 7
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die SCL-Schwellenwerte erfolgreich konfiguriert wurden:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-ContentFilterConfig | Format-List SCL*
    ```

2.  Überprüfen Sie, ob die angezeigten Werte den Einstellungen entsprechen, die Sie angegeben haben.

## Konfigurieren der Zurückweisungsantwort mithilfe der Verwaltungsshell

Wenn die Zurückweisungsaktion aktiviert ist, können Sie die Zurückweisungsantwort anpassen, die an den Absender der Nachricht gesendet wird. Die Zurückweisungsantwort darf maximal 240 Zeichen umfassen.

Führen Sie den folgenden Befehl aus, um eine benutzerdefinierte Zurückweisungsantwort zu konfigurieren:

```powershell
Set-ContentFilterConfig -RejectionResponse "<Custom Text>"
```

In diesem Beispiel wird der Inhaltsfilter-Agent so konfiguriert, dass eine angepasste Zurückweisungsantwort gesendet wird.

```powershell
Set-ContentFilterConfig -RejectionResponse "Your message was rejected because it appears to be SPAM."
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Zurückweisungsantwort erfolgreich konfiguriert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-ContentFilterConfig | Format-List *Reject*
    ```

2.  Überprüfen Sie, ob die angezeigten Werte den Einstellungen entsprechen, die Sie angegeben haben.

## Aktivieren oder Deaktivieren von Outlook-E-Mail-Poststempeln mithilfe der Shell

Bei der *E-Mail-Poststempelüberprüfung von Outlook* handelt es sich um einen rechnerischen Nachweis, den Microsoft Outlook ausgehenden Nachrichten hinzufügt, um Messagingsystemen von Empfängern die Unterscheidung zwischen legitimen E-Mails und Junk-E-Mails zu erleichtern. Poststempel sind ab Outlook 2007 verfügbar. Mithilfe von Poststempeln lässt sich die Anzahl von falsch positiven Ergebnissen reduzieren. Outlook-E-Mail-Poststempel sind standardmäßig aktiviert.

Führen Sie den folgenden Befehl aus, um Outlook-E-Mail-Poststempel zu deaktivieren:

```powershell
Set-ContentFilterConfig -OutlookEmailPostmarkValidationEnabled $false
```

Führen Sie den folgenden Befehl aus, um Outlook-E-Mail-Poststempel zu aktivieren:

```powershell
Set-ContentFilterConfig -OutlookEmailPostmarkValidationEnabled $true
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Outlook-E-Mail-Poststempelfunktion erfolgreich konfiguriert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-ContentFilterConfig | Format-List OutlookEmailPostmarkValidationEnabled
    ```

2.  Überprüfen Sie, ob der angezeigte Wert der Einstellung entspricht, die Sie angegeben haben.
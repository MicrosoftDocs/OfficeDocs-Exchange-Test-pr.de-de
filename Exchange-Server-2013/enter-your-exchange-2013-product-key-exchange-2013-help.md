---
title: 'Eingeben Ihres Product Key für Exchange 2013: Exchange 2013 Help'
TOCTitle: Eingeben Ihres Product Key für Exchange 2013
ms:assetid: ccb14685-4bdc-42a4-a985-35cd2a1a415c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124582(v=EXCHG.150)
ms:contentKeyID: 51409347
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.EnterProductKeyWizardForm.EnterProductKeyWizardPage
ms.translationtype: HT
---

# Eingeben Ihres Product Key für Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Ein Product Key teilt Exchange Server 2013 mit, dass Sie eine Lizenz für die Standard- oder die Enterprise Edition erworben haben. Wenn der von Ihnen gekaufte Product Key für eine Enterprise Edition-Lizenz gilt, können Sie zusätzlich zu allen Leistungen der Standard-Edition mehr als fünf Datenbanken pro Server implementieren. Weitere Informationen zu Exchange-Lizenzen finden Sie unter [Exchange 2013: Editionen und Versionen](exchange-2013-editions-and-versions-exchange-2013-help.md).

Wenn Sie keinen Product Key eingeben, wird Ihr Server automatisch als Testversion lizenziert. Die Testversion funktioniert genauso wie ein Exchange Standard Edition-Server und ist hilfreich, wenn Sie Exchange ausprobieren möchten, bevor Sie das Produkt kaufen, oder in einer Testumgebung Tests durchführen möchten. Der einzige Unterschied ist, dass Sie einen als Testversion lizenzierten Exchange-Server nur bis zu 180 Tage verwenden können. Wenn Sie den Server über die 180 Tage hinaus verwenden möchten, müssen Sie einen Product Key eingeben, oder im Exchange Admin Center (EAC) werden Erinnerungsmeldungen ausgegeben, dass Sie einen Produktschlüssel eingeben müssen, um den Server zu lizenzieren.


> [!TIP]
> Wir haben festgestellt, dass einige Besucher dieser Seite nach Informationen zur Installation oder Aktivierung von Office suchen. Wenn Sie dazu zählen, probieren Sie es einmal auf diesen Seiten: 
> <UL>
> <LI>
> <P><A href="http://go.microsoft.com/fwlink/p/?linkid=403360">Installieren von Office</A></P>
> <LI>
> <P><A href="http://go.microsoft.com/fwlink/p/?linkid=403361">Benötigen Sie Hilfe mit dem Office Product Key?</A></P></LI></UL>Wenn Sie auf einem Exchange 2010-Server einen Product Key eingeben möchten, lesen Sie <A href="http://go.microsoft.com/fwlink/p/?linkid=403370">Eingeben eines Exchange 2010 Product Key</A>.<BR>Wenn Sie auf einem Exchange 2013-Server einen Product Key eingeben möchten, sind Sie hier richtig. Lesen Sie weiter.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieses Verfahrens: Weniger als 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Product Key" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Wenn Sie einen Exchange-Server lizenzieren, der die Postfachserverrolle ausführt, müssen Sie nach Eingabe des Product Key den Microsoft Exchange-Informationsspeicherdienst auf dem Server neu starten.

  - Wenn Sie ein Upgrade eines Exchange-Servers von einer Standard Edition-Lizenz auf eine Enterprise Edition-Lizenz durchführen möchten, befolgen Sie die Schritte in diesem Thema.

  - Wenn Sie ein Downgrade eines Exchange-Servers von einer Enterprise Edition-Lizenz auf eine Standard Edition-Lizenz durchführen möchten, müssen Sie Exchange neu installieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Eingeben des Product Keys mithilfe der Exchange-Verwaltungskonsole

1.  Öffnen Sie das Exchange Admin Center, indem Sie in Ihrem Browser zur Adresse "https://\<*Name des Clientzugriffsservers*\>/ecp" wechseln.

2.  Geben Sie Ihren Benutzernamen und das zugehörige Kennwort in die Felder **Domäne\\Benutzername** und **Kennwort** ein, und klicken Sie dann auf **Anmelden**.

3.  Wechseln Sie zu **Server** \> **Server**. Wählen Sie den Server aus, den Sie lizenzieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  (Optional) Wenn Sie ein Upgrade des Servers von einer Standard Edition-Lizenz zu einer Enterprise Edition-Lizenz durchführen möchten, klicken Sie auf der Seite **Allgemein** auf **Product Key ändern**. Diese Option wird nur angezeigt, wenn der Server bereits lizenziert ist.

5.  Geben Sie auf das Seite **Allgemein** Ihren Product Key in das Textfeld **Gültigen Product Key eingeben** ein.

6.  Klicken Sie auf **Speichern**.

7.  Wenn Sie einen Exchange-Server lizenziert haben, der die Postfachserverrolle ausführt, gehen Sie folgendermaßen vor, um den Microsoft Exchange-Informationsspeicherdienst neu zu starten:
    
    1.  Öffen Sie die **Systemsteuerung**, wechseln Sie zu **Verwaltungstools**, und öffnen Sie dann **Dienste**.
    
    2.  Klicken Sie mit der rechten Maustaste auf den Dienst **Microsoft Exchange-Informationsspeicher**, und klicken Sie auf **Neu starten**.

## Eingabe des Product Keys mithilfe der Shell

In diesem Beispiel wird das Cmdlet **set-ExchangeServer** verwendet, um den Product Key einzugeben.


> [!NOTE]
> Sie können diesen Befehl nochmals auf demselben Server ausführen, um ein Upgrade von einer Standard Edition-Lizenz zu einer Enterprise Edition-Lizenz auszuführen.



```powershell
Set-ExchangeServer ExServer01 -ProductKey aaaaa-aaaaa-aaaaa-aaaaa-aaaaa
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ExchangeServer](https://technet.microsoft.com/de-de/library/bb123716\(v=exchg.150\)).

Wenn Sie einen Exchange-Server lizenziert haben, der die Postfachserverrolle ausführt, gehen Sie folgendermaßen vor, um den Microsoft Exchange-Informationsspeicherdienst neu zu starten:

1.  Öffnen Sie die **Systemsteuerung**, wechseln Sie zu **Verwaltungstools**, und öffnen Sie dann **Dienste**.

2.  Klicken Sie mit der rechten Maustaste auf den **Microsoft Exchange-Informationsspeicher**, und klicken Sie auf **Neu starten**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um mithilfe der Exchange-Verwaltungskonsole zu prüfen, ob Sie den Server erfolgreich als Standard Edition oder Enterprise Edition lizenziert haben, gehen Sie wie folgt vor:

1.  Geben Sie Ihren Benutzernamen und das zugehörige Kennwort in die Felder **Domäne\\Benutzername** und **Kennwort** ein, und klicken Sie dann auf **Anmelden**.

2.  Wechseln Sie zu **Server** \> **Server**.

3.  Wählen Sie den gewünschten Server aus, und schauen Sie sich dann den Serverdetailbereich an. Wenn der Product Key akzeptiert wurde, wird **Lizenziert** sowie die Exchange 2013-Edition angezeigt.

Um mithilfe der Shell zu prüfen, ob Sie den Server erfolgreich als Standard Edition oder Enterprise Edition lizenziert haben, gehen Sie wie folgt vor:

1.  Öffnen Sie die Shell.

2.  Führen Sie den folgenden Befehl aus, um den Lizenzierungsstatus eines bestimmten Exchange-Servers anzuzeigen.

    ```powershell
        Get-ExchangeServer ExServer01 | Format-Table Edition,*Trial*
    ```

3.  (Optional) Führen Sie den folgenden Befehl aus, um den Lizenzierungsstatus aller Exchange-Server in Ihrer Organisation anzuzeigen.

    ```powershell
        Get-ExchangeServer | Format-Table Name, Edition, *Trial* -Auto
    ```

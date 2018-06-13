---
title: 'Erstellen eines cloudbasierten Archivs für ein lokales primäres Postfach in einer Exchange-Hybridbereitstellung: Exchange Online Help'
TOCTitle: Erstellen eines cloudbasierten Archivs für ein lokales primäres Postfach in einer Hybridbereitstellung
ms:assetid: ecc0a687-6c05-47bd-a079-a43d83cba9ea
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt791517(v=EXCHG.150)
ms:contentKeyID: 74253087
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen eines cloudbasierten Archivs für ein lokales primäres Postfach in einer Exchange-Hybridbereitstellung

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2017-01-20_

In einer Exchange-Hybridbereitstellung können Sie ein lokales primäres Postfach mit einem cloudbasierten Archivpostfach in Exchange Online konfigurieren.

Schritt 1: Aktivieren eines cloudbasierten Archivpostfachs für ein lokales primäres Postfach

Schritt 2: Überprüfen, ob das cloudbasierte Archivpostfach erstellt wurde

(Optional) Ausführen einer Verzeichnissynchronisierung

## Vorbereitung

  - Der Benutzer mit dem lokalen primären Postfach muss ein Benutzerkonto in Ihrer Office 365-Organisation sein.

  - Dem Office 365-Benutzerkonto muss eine Exchange Online-Archivierungslizenz für Exchange Server zugewiesen werden. Die Schritte für das Zuweisen einer Lizenz sind in den Vorgehensweisen in Schritt 1 enthalten.

  - Nach Aktivierung des cloudbasierten Archivpostfachs in Schritt 1 kann es bis zu 30 Minuten dauern, bis das cloudbasierte Archivpostfach bereitgestellt wird. Grund hierfür ist, dass das cloudbasierte Archivpostfach anhand des Prozesses der Verzeichnissynchronisierung erstellt wird, bei dem die lokale Active Directory-Bereitstellung mit Azure Active Directory (Azure AD) in Office 365 synchronisiert wird. Standardmäßig erfolgt die Verzeichnissynchronisierung alle 30 Minuten.

## Schritt 1: Aktivieren eines cloudbasierten Archivpostfachs für ein lokales primäres Postfach

Verwenden Sie eine der folgenden Vorgehensweisen zum Aktivieren eines cloudbasierten Archivpostfachs für ein lokales primäres Postfach. Führen Sie diese Schritte im Exchange-Verwaltungskonsole in der lokalen Exchange-Organisation und im Office 365 Admin Center durch.

Erstellen eines cloudbasierten Archivpostfachs für einen neuen Benutzer

Erstellen eines cloudbasierten Archivpostfachs für einen vorhandenen Benutzer

## Erstellen eines cloudbasierten Archivpostfachs für einen neuen Benutzer

1.  Wählen Sie im EAC in der lokalen **Empfänger**  \> **Postfächer**.

2.  Klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/Mt791517.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") \> **Benutzerpostfach**.

3.  Erstellen Sie auf der Seite **Neues Benutzerpostfach** ein Postfach für einen neuen oder vorhandenen Benutzer. Weitere Informationen zum Erstellen von Benutzerpostfächern finden Sie unter [Erstellen von Benutzerpostfächern](https://technet.microsoft.com/de-de/library/jj991919\(v=exchg.150\)).

4.  Klicken Sie zum Aktivieren eines cloudbasierten Archivpostfachs auf **Weitere Optionen**.

5.  Aktivieren Sie unter **Archiv** das Kontrollkästchen **In-Situ-Archiv für diesen Benutzer erstellen**, und klicken Sie anschließend auf **Cloudbasiertes Archiv**. Es wird der Name der Domäne angezeigt, in der das Archivpostfach bereitgestellt wird.
    
    ![Aktivieren Sie unter „Archiv\&quot; das Kontrollkästchen „Cloudbasiertes Archiv\&quot;.](images/Mt791517.43d0473e-30ad-4021-94bc-a9c5449f43ba(EXCHG.150).png "Aktivieren Sie unter „Archiv&quot; das Kontrollkästchen „Cloudbasiertes Archiv&quot;.")  

6.  Klicken Sie auf **Speichern**, um das Postfach und das cloudbasierte Archiv zu erstellen.
    
    Beachten Sie, dass der Wert **Benutzer (Archiv)** auf der Seite **Postfächer** in der Spalte **Postfachtyp** für das ausgewählte Postfach angezeigt wird.

7.  Warten Sie bis zu 30 Minuten, bis die Verzeichnissynchronisierung ein entsprechendes Benutzerkonto in Office 365 erstellt hat.
    

    > [!TIP]
    > Navigieren Sie im Office 365 Admin Center zu <STRONG>Integrität</STRONG> &gt; <STRONG>Status für Verzeichnissynchronisierung</STRONG>, um den Zeitpunkt der letzten Verzeichnissynchronisierung zu erfahren.



8.  Nachdem Sie sichergestellt haben, dass nach Erstellen des neuen lokalen Postfachs eine Verzeichnissynchronisierung erfolgt ist, navigieren Sie im Office 365 Admin Center zu **Benutzer** \> **Aktive Benutzer**, und wählen Sie dann das neue Office 365-Benutzerkonto, das für das neue lokale Postfach erstellt wurde.

9.  Klicken Sie auf der Seite mit Benutzereigenschaften im Abschnitt **Produktlizenzen** auf **Bearbeiten**.
    
    ![Klicken Sie im Detailbereich auf „Bearbeiten\&quot;, um dem ausgewählten Benutzer eine Lizenz zuzuweisen.](images/Mt791517.383a9068-53cb-420a-a05e-823e8b5a2c25(EXCHG.150).png "Klicken Sie im Detailbereich auf „Bearbeiten&quot;, um dem ausgewählten Benutzer eine Lizenz zuzuweisen.")  

10. Wählen Sie im Dropdownmenü **Ort** einen Ort für den Benutzer aus.

11. Erweitern Sie die Liste der Office 365 Enterprise-Lizenzen, weisen Sie anschließend die Lizenz für **Exchange Online-Archivierung für Exchange Server** zu, und speichern Sie die Änderungen.
    
    Beachten Sie, dass dem Benutzer unter der Spalte **Status** in der Liste der Benutzer nun eine Lizenz zugewiesen ist.

12. Warten Sie erneut bis zu 30 Minuten, bis die Verzeichnissynchronisierung ein cloudbasiertes Archivpostfach bereitstellt. Wechseln Sie zu Schritt 2, um sicherzustellen dass das cloudbasierte Archivpostfach erstellt wurde. Nach Erstellung des Archivpostfachs kann der Benutzer mithilfe von Outlook oder Outlook im Web auf dieses Postfach zugreifen.

Zurück zum Seitenanfang

## Erstellen eines cloudbasierten Archivpostfachs für einen vorhandenen Benutzer

1.  Wechseln Sie im Office 365 Admin Center zu **Benutzer** \> **Aktive Benutzer**, und wählen Sie das Benutzerkonto, für das Sie ein cloudbasiertes Archivpostfach erstellen möchten.

2.  Klicken Sie auf der Seite mit Benutzereigenschaften im Abschnitt **Produktlizenzen** auf **Bearbeiten**.
    
    ![Klicken Sie im Detailbereich auf „Bearbeiten\&quot;, um dem ausgewählten Benutzer eine Lizenz zuzuweisen.](images/Mt791517.383a9068-53cb-420a-a05e-823e8b5a2c25(EXCHG.150).png "Klicken Sie im Detailbereich auf „Bearbeiten&quot;, um dem ausgewählten Benutzer eine Lizenz zuzuweisen.")  

3.  Wählen Sie im Dropdownmenü **Ort** einen Ort für den Benutzer aus.

4.  Erweitern Sie die Liste der Office 365 Enterprise-Lizenzen, weisen Sie anschließend die Lizenz für **Exchange Online-Archivierung für Exchange Server** zu, und speichern Sie die Änderungen.
    
    Beachten Sie, dass dem Benutzer unter der Spalte **Status** in der Liste der Benutzer nun eine Lizenz zugewiesen ist.

5.  Wählen Sie im EAC in der lokalen **Empfänger**  \> **Postfächer**.

6.  Wählen Sie in der Liste der Postfächer den Benutzer, dem Sie die Lizenz zugewiesen haben.

7.  Klicken Sie im Detailbereich unter **Compliance-Archiv** auf **Aktivieren**.
    
    ![Klicken Sie im Detailbereich auf „Aktivieren\&quot;, um das Archivpostfach für den ausgewählten Benutzer zu aktivieren.](images/Mt791517.17ce99f7-d154-4e21-bec1-c938af1d4a0a(EXCHG.150).png "Klicken Sie im Detailbereich auf „Aktivieren&quot;, um das Archivpostfach für den ausgewählten Benutzer zu aktivieren.")  

8.  Klicken Sie auf der Seite **In-Situ-Archiv erstellen** auf **Cloudbasiertes Archiv**, und klicken Sie dann auf **OK**. Es wird der Name der Domäne angezeigt, in der das Archivpostfach bereitgestellt wird.
    
    ![Klicken Sie auf der Seite „In-Situ-Archiv erstellen\&quot; auf „Cloudbasiertes Archiv\&quot;.](images/Mt791517.9ad047c9-ef47-47df-93cc-0fab872f1ae1(EXCHG.150).png "Klicken Sie auf der Seite „In-Situ-Archiv erstellen&quot; auf „Cloudbasiertes Archiv&quot;.")  
    
    Beachten Sie, dass der Wert **Benutzer (Archiv)** auf der Seite **Postfächer** in der Spalte **Postfachtyp** für das ausgewählte Postfach angezeigt wird.

9.  Warten Sie bis zu 30 Minuten, bis die Verzeichnissynchronisierung ein cloudbasiertes Archivpostfach erstellt. Wechseln Sie zu Schritt 2, um sicherzustellen dass das cloudbasierte Archivpostfach erstellt wurde. Nach Erstellung des Archivpostfachs kann der Benutzer mithilfe von Outlook oder Outlook im Web auf dieses Postfach zugreifen.
    

    > [!TIP]
    > Navigieren Sie im Office 365 Admin Center zu <STRONG>Integrität</STRONG> &gt; <STRONG>Status für Verzeichnissynchronisierung</STRONG>, um den Zeitpunkt der letzten Verzeichnissynchronisierung zu erfahren.



Zurück zum Seitenanfang

## Schritt 2: Überprüfen, ob das cloudbasierte Archivpostfach erstellt wurde

Wie zuvor beschrieben gibt es möglicherweise eine Verzögerung zwischen dem Zeitpunkt, zu dem Sie ein cloudbasiertes Archivpostfach aktivieren und dem Zeitpunkt, zu dem es tatsächlich erstellt wird. Grund hierfür ist, dass eine Verzeichnissynchronisierung erfolgen muss, damit das cloudbasierte Archivpostfach erstellt wird. Im Folgenden wird erläutert, wie Sie überprüfen können, ob das cloudbasierte Archivpostfach erstellt wurde.

Führen Sie in Ihrer Organisation Exchange Online den folgenden PowerShell-Befehl zum Anzeigen von Eigenschaften im Zusammenhang mit dem Postfach eines Benutzers archivieren. Zum Verbinden mit Exchange Online mithilfe von remote-PowerShell finden Sie unter [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/?/linkid=396554).

    Get-MailUser <cloud mail user> | FL *archive*

Die folgenden Screenshots zeigen die Eigenschaften, die zurückgegeben werden, wenn die Bereitstellung des cloudbasierten Archivpostfachs noch aussteht und wenn die Erstellung des Archivpostfachs abgeschlossen ist.

**Eigenschaften des E-Mail-Benutzers vor der Bereitstellung des cloudbasierten Archivpostfachs mithilfe der Verzeichnissynchronisierung**

![Cloudbasierte E-Mail-Benutzereigenschaften vor der Bereitstellung des cloudbasierten Archivs](images/Mt791517.c6a42713-f061-4761-93c1-2b5478953e46(EXCHG.150).png "Cloudbasierte E-Mail-Benutzereigenschaften vor der Bereitstellung des cloudbasierten Archivs")

Bevor die Verzeichnissynchronisierung das cloudbasierte Archiv bereitstellt, ist die *ArchiveStatus*-Eigenschaft auf `None` festgelegt. Beachten Sie auch, dass die *ArchiveGuid*- und *ArchiveName*-Eigenschaften leer sind.

**Eigenschaften des E-Mail-Benutzers nach der Bereitstellung des cloudbasierten Archivpostfachs mithilfe der Verzeichnissynchronisierung**

![Cloudbasierte E-Mail-Benutzereigenschaften nach der Bereitstellung des cloudbasierten Archivs](images/Mt791517.005fcc87-6253-4218-aafc-50f212de54fa(EXCHG.150).png "Cloudbasierte E-Mail-Benutzereigenschaften nach der Bereitstellung des cloudbasierten Archivs")

Nachdem die Verzeichnissynchronisierung das cloudbasierte Archiv bereitgestellt hat, ist die *ArchiveStatus*-Eigenschaft auf `Active` festgelegt, und die *ArchiveGuid*- und *ArchiveName*-Eigenschaften sind aufgefüllt. An diesem Punkt kann der Benutzer auf das cloudbasierte Archivpostfach in Outlook oder Outlook im Web zugreifen.

![Benutzer kann in Outlook oder Outlook im Web auf sein cloudbasiertes Archivpostfach zugreifen](images/Mt791517.8777bc4d-05c3-4489-8d8c-ff5429a0b2c3(EXCHG.150).png "Benutzer kann in Outlook oder Outlook im Web auf sein cloudbasiertes Archivpostfach zugreifen")

Sie können auch den folgenden PowerShell-Befehl in der lokalen Exchange-Organisation ausführen, um die Eigenschaften anzuzeigen, die mit dem cloudbasierten Archivpostfach eines Benutzers zusammenhängen.

    Get-Mailbox <on-premises user mailbox> | FL *archive*

**Eigenschaften des lokalen Postfachs vor der Bereitstellung des cloudbasierten Archivpostfachs mithilfe der Verzeichnissynchronisierung**

![Postfacheigenschaften vor der Bereitstellung des cloudbasierten Archivs](images/Mt791517.d5625bc8-03de-439a-8a0a-051ff537a0bf(EXCHG.150).png "Postfacheigenschaften vor der Bereitstellung des cloudbasierten Archivs")

Bevor die Verzeichnissynchronisierung das cloudbasierte Archiv bereitstellt, sind die *ArchiveStatus*-Eigenschaft auf `None` und die *ArchiveState*-Eigenschaft auf `HostedPending` festgelegt.

**Eigenschaften des lokalen Postfachs nach der Bereitstellung des cloudbasierten Archivpostfachs mithilfe der Verzeichnissynchronisierung**

![Postfacheigenschaften nach der Bereitstellung des cloudbasierten Archivs](images/Mt791517.9b42d562-1b0a-4722-97aa-35d0ef6f9372(EXCHG.150).png "Postfacheigenschaften nach der Bereitstellung des cloudbasierten Archivs")

Nachdem die Verzeichnissynchronisierung das cloudbasierte Archiv bereitgestellt hat, sind die *ArchiveStatus*-Eigenschaft auf `Active` und die *ArchiveState*-Eigenschaft auf `HostedProvisioned` festgelegt. An diesem Punkt kann der Benutzer auf das cloudbasierte Archivpostfach in Outlook oder Outlook im Web zugreifen.

Zurück zum Seitenanfang

## (Optional) Ausführen einer Verzeichnissynchronisation

Wie zuvor beschrieben, wird das cloudbasierte Archivpostfach durch den Prozess der Verzeichnissynchronisierung erstellt. Standardmäßig wird Ihr lokales Active Directory alle 30 Minuten mit Azure AD in Office 365 synchronisiert. Den Zeitpunkt der letzten Verzeichnissynchronisierung erfahren Sie, indem Sie im Office 365 Admin Center zu **Integrität** \> **Status für Verzeichnissynchronisierung** navigieren.

In einigen Fällen möchten Sie die Verzeichnissynchronisierung zum Bereitstellen des cloudbasierten Archivpostfachs vor der nächsten geplanten Synchronisierung starten. Dazu führen Sie den folgenden PowerShell-Befehl auf dem Server aus, auf dem Azure AD Connect installiert ist.

    Start-ADSyncSyncCycle -PolicyType Delta

Weitere Informationen finden Sie unter [Azure AD Connect Sync: Scheduler](https://go.microsoft.com/fwlink/p/?linkid=836813).

Zurück zum Seitenanfang


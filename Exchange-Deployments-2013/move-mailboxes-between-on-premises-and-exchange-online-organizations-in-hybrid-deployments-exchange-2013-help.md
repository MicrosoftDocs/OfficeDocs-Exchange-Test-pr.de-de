---
title: 'Verschieben von Postfächern zwischen lokalen und Exchange Online-Organisationen in Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Verschieben von Postfächern zwischen lokalen und Exchange Online-Organisationen in Hybridbereitstellungen
ms:assetid: d6289f7b-f67e-48db-9570-9fd3c9547548
ms:mtpsurl: https://technet.microsoft.com/de-de/library/o365e_hrcmoverequest_fl312271(v=EXCHG.150)
ms:contentKeyID: 51406943
ms.date: 01/03/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verschieben von Postfächern zwischen lokalen und Exchange Online-Organisationen in Hybridbereitstellungen

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2017-10-02_

Mit einer Exchange-basierten Hybridbereitstellung können Sie entweder lokale Exchange-Postfächer in die Exchange Online-Organisation oder Exchange Online-Postfächer in die lokale Exchange-Organisation verschieben. Verwenden Sie beim Verschieben von Postfächern zwischen den lokalen und Exchange Online-Organisationen Migrationsbatches zum Ausführen der Verschiebungsanforderung für Remotepostfächer. Dieser Ansatz ermöglicht es, vorhandene Postfächer zu verschieben, statt neue Benutzerpostfächer zu erstellen und Benutzerinformationen zu importieren. Dieser Ansatz unterscheidet sich von der Migration von Benutzerpostfächern von einer lokalen Exchange-Organisation zu Exchange Online, die im Rahmen einer vollständigen Exchange-Migration in die Cloud ausgeführt wird. Die in diesem Thema erläuterte Postfachverschiebung wird im Rahmen der Exchange-Verwaltung in einer längerfristigen Koexistenzbeziehung zwischen lokalen Exchange- und Exchange Online-Organisationen ausgeführt.

Weitere Informationen über die Migration von lokalen Exchange-Organisationen zu Exchange Online finden Sie unter [Methoden zum Migrieren mehrerer E-Mail-Konten zu Office 365](https://go.microsoft.com/fwlink/p/?linkid=524030).


> [!IMPORTANT]
> Sie müssen eine Hybridbereitstellung zwischen Ihren lokalen und Exchange Online-Organisationen konfiguriert haben, um die in diesem Thema beschriebenen Postfachverschiebungen durchführen zu können. Weitere Informationen zu Hybridbereitstellungen finden Sie unter <A href="exchange-server-hybrid-deployments-exchange-2013-help.md">Hybridbereitstellungen in Exchange Server</A>.<BR><BR>Bevor Sie UM-fähige (Unified Messaging) Postfächer nach Exchange Online verschieben, müssen Sie sicherstellen, dass Skype for Business 2015 (lokal), Skype for Business Online und Exchange Online die in <A href="hybrid-deployment-prerequisites-exchange-2013-help.md">Voraussetzungen für die Hybridbereitstellung</A> angegebenen Anforderungen erfüllen. Informationen zum Zuordnen Ihrer lokalen UM-Postfachrichtlinien zu Richtlinien in Exchange Online finden Sie unter <A href="https://technet.microsoft.com/de-de/library/bb124903(v=exchg.150)">Set-UMMailboxPolicy</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten zum Konfigurieren des Migrationsbatches, die Gesamtzeit zum Abschließen der Migration hängt von der Anzahl von Postfächern ab, die in jedem Migrationsbatch enthalten sind.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für Postfachverschiebungen und -migrationen" im Thema [Empfängerberechtigungen](https://technet.microsoft.com/de-de/library/dd638132\(v=exchg.150\)).

  - Die Hybridbereitstellung zwischen den lokalen und den Exchange Online-Organisationen ist konfiguriert.

  - Stellen Sie beim Ausführen von Exchange 2013 sicher, dass der Postfachreplikations-Proxydienst (MRSProxy) auf Ihren lokalen Exchange 2013-Clientzugriffsservern aktiviert ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](https://technet.microsoft.com/de-de/library/jj150484\(v=exchg.150\)).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Schritt 1: Erstellen eines Migrationsendpunkts

Vor dem Onboarding und Offboarding von remote ausgeführten Verschiebungsmigrationen in einer Exchange-Hybridbereitstellung sollten Sie Endpunkte für die Exchange-Remotemigration erstellen. Der Migrationsendpunkt enthält die Verbindungseinstellungen für einen lokalen Exchange-Server, auf dem der MRS-Proxydienst ausgeführt wird, der zum Ausführen von Remoteverschiebungsmigrationen zu und von Exchange Online erforderlich ist.

Schritt-für-Schritt-Verfahren finden Sie unter Erstellen von Migrationsendpunkten.

## Schritt 2: Aktivieren des MRSProxy-Diensts

Wenn der MRSProxy-Dienst nicht bereits für Ihre lokalen Exchange 2013-Clientzugriffsserver aktiviert ist, führen Sie diese Schritte in der Exchange-Verwaltungskonsole (EAC) aus:

1.  Öffnen Sie die EAC, und navigieren Sie zu **Server** \> **Virtuelle Verzeichnisse**.

2.  Wählen Sie den Clientzugriffsserver und anschließend das virtuelle Verzeichnis **EWS** aus, und klicken Sie auf **Bearbeiten** ![Bearbeitungssymbol](images/JJ906432.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie das Kontrollkästchen **MRS-Proxy aktiviert**, und klicken Sie dann auf **Speichern**.

## Schritt 3: Verwenden der EAC zum Verschieben von Postfächern

Sie können den Assistenten für Remoteverschiebungsmigrationen auf der Registerkarte **Office 365** in der EAC auf einem Exchange-Server verwenden, um entweder vorhandene Benutzerpostfächer in der lokalen Organisation in die Exchange Online-Organisation oder Exchange Online-Postfächer in die lokale Organisation zu verschieben. Wählen Sie eines der folgenden Verfahren aus:

## Verschieben von lokalen Postfächern nach Exchange Online

Sie können den Assistenten für Remoteverschiebungsmigrationen auf der Registerkarte **Office 365** in der EAC auf einem Exchange-Server verwenden, um vorhandene Benutzerpostfächer in der lokalen Organisation in die Exchange Online-Organisation zu verschieben. Führen Sie die folgenden Schritte aus:

1.  Öffnen Sie die EAC, und navigieren Sie zu **Office 365** \> **Empfänger** \> **Migration**.

2.  Klicken Sie auf **Hinzufügen** ![Hinzufügen (Symbol)](images/Mt791517.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie **Zu Exchange Online migrieren**.

3.  Wählen Sie auf der Seite **Migrationstyp auswählen** die Option **Remoteverschiebungsmigration** aus, und klicken Sie dann auf **Weiter**.

4.  Klicken Sie auf der Seite **Benutzer auswählen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/Mt791517.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), wählen Sie die lokalen Benutzer aus, die Sie nach Office 365 verschieben möchten, und klicken Sie dann auf **Hinzufügen** und **OK**. Klicken Sie dann auf **Weiter**.

5.  Geben Sie auf der Seite **Anmeldeinformationen für das Windows-Benutzerkonto eingeben** im Textfeld **Name des lokalen Administrators** den Namen für das lokale Administratorkonto ein, und geben Sie im Textfeld **Kennwort für den lokalen Administrator** das zugehörige Kennwort ein. Beispiel: "corp\\administrator" und ein Kennwort. Klicken Sie dann auf **Weiter**.
    

    > [!NOTE]
    > Wenn Sie bereits einen Migrationsendpunkt erstellt haben, erhalten Sie an dieser Stelle eine Aufforderung zur Endpunktbestätigung. Wenn Sie zwei oder mehr Migrationsendpunkte erstellt haben, müssen Sie einen Endpunkt aus dem Dropdownmenü für Migrationsendpunkte auswählen.



6.  Vergewissern Sie sich auf der Seite **Migrationsendpunkt bestätigen**, dass der FQDN des lokalen Exchange-Servers aufgeführt ist, wenn der Assistent den Migrationsendpunkt bestätigt. Beispiel: „mail.contoso.com“. Klicken Sie dann auf **Weiter**.
    

    > [!NOTE]
    > Standardmäßig schränkt der MRSProxy-Dienst auf dem Exchange-Server die Postfachverschiebungsanforderungen automatisch ein, wenn Sie mehrere Postfächer zum Verschieben nach Exchange Online auswählen. Die zum Abschließen der Postfachverschiebung erforderliche Gesamtzeit hängt von der Gesamtanzahl ausgewählter Postfächer, der Größe der Postfächer und der MRSProxy-Konfiguration ab. Weitere Informationen zum Anpassen von MRSProxy finden Sie unter <A href="https://technet.microsoft.com/de-de/library/bb232205(v=exchg.150)">Nachrichteneinschränkungen</A>.



7.  Geben Sie auf der Seite **Verschiebungskonfiguration** im Textfeld **Name des neuen Migrationsbatches** einen Namen für den Migrationsbatch ein. Verwenden Sie den nach unten weisenden Pfeil ![NACH-UNTEN-TASTE (Symbol)](images/JJ906432.ef5ca57d-a033-457b-bd92-6361877c33d0(EXCHG.150).gif "NACH-UNTEN-TASTE (Symbol)"), um die **Zieldomäne für Postfächer für die Migration zu Office 365** auszuwählen. In den meisten Hybridbereitstellungen ist dies die primäre SMTP-Domäne, die für Exchange Online-Organisationspostfächer verwendet wird, beispielsweise „contoso.mail.onmicrosoft.com“. Stellen Sie sicher, dass die Option **Primäres Postfach mit Archivpostfach verschieben** aktiviert ist, und klicken Sie dann auf **Weiter**.

8.  Wählen Sie auf der Seite **Batch starten** mindestens einen Empfänger aus, der den Bericht zum Batchabschluss erhalten soll. Vergewissern Sie sich, dass die Option **Batch automatisch starten** ausgewählt ist, und aktivieren Sie das Kontrollkästchen **Migrationsbatch automatisch abschließen**. Klicken Sie auf **Neu**.

## Verschieben von Exchange Online-Postfächern in die lokale Organisation

Sie können den Assistenten für Remoteverschiebungsmigrationen auf der Registerkarte **Office 365** in der EAC auf einem Exchange-Server verwenden, um vorhandene Benutzerpostfächer in der lokalen Organisation in die Exchange Online-Organisation zu verschieben.

1.  Öffnen Sie die EAC, und navigieren Sie zu **Office 365** \> **Empfänger** \> **Migration**.

2.  Klicken Sie auf **Hinzufügen** ![Hinzufügen (Symbol)](images/Mt791517.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie **Von Exchange Online migrieren**.

3.  Wählen Sie auf der Seite **Benutzer auswählen** die Option **Zu verschiebende Benutzer auswählen**, und klicken Sie auf **Weiter**.

4.  Klicken Sie auf der Seite **Benutzer auswählen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/Mt791517.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), wählen Sie die Exchange Online-Benutzer aus, die Sie in die lokale Organisation verschieben möchten, und klicken Sie dann auf **Hinzufügen** und **OK**. Klicken Sie dann auf **Weiter**.

5.  Vergewissern Sie sich auf der Seite **Migrationsendpunkt bestätigen**, dass der FQDN des lokalen Exchange-Servers aufgeführt ist, wenn der Assistent den Migrationsendpunkt bestätigt. Beispiel: „mail.contoso.com“. Klicken Sie dann auf **Weiter**.
    

    > [!NOTE]
    > Standardmäßig schränkt der MRSProxy-Dienst auf dem Exchange-Server die Postfachverschiebungsanforderungen automatisch ein, wenn Sie mehrere Postfächer zum Verschieben nach Exchange Online auswählen. Die zum Abschließen der Postfachverschiebung erforderliche Gesamtzeit hängt von der Gesamtanzahl ausgewählter Postfächer, der Größe der Postfächer und den Eigenschaften von MRSProxy ab. Weitere Informationen zum Anpassen von MRSProxy finden Sie unter <A href="https://technet.microsoft.com/de-de/library/bb232205(v=exchg.150)">Nachrichteneinschränkungen</A>.



6.  Geben Sie auf der Seite **Verschiebungskonfiguration** im Textfeld **Name des neuen Migrationsbatches** einen Namen für den Migrationsbatch ein. Geben Sie dann die Zielzustellungsdomäne im Feld **Zielzustellungsdomäne für Postfächer für die Migration zu Office 365** ein. In den meisten Hybridbereitstellungen ist dies die primäre SMTP-Domäne, die sowohl für lokale als auch für Exchange Online-Organisationspostfächer verwendet wird. Beispiel: "contoso.com".

7.  Geben Sie an, ob auch das Archivpostfach für den ausgewählten Benutzer verschoben werden soll, und geben Sie im Textfeld **Zieldatenbank** die Datenbank an, in die das Postfach verschoben werden soll. Beispiel: "Postfachdatenbank 123456789" Klicken Sie auf **Weiter**.

8.  Wählen Sie auf der Seite **Batch starten** mindestens einen Empfänger aus, der den Bericht zum Batchabschluss erhalten soll. Vergewissern Sie sich, dass **Batch automatisch starten** ausgewählt ist, und aktivieren Sie das Kontrollkästchen **Migrationsbatch automatisch abschließen**. Klicken Sie auf **Neu**.

## Schritt 4: Entfernen von abgeschlossenen Migrationsbatches

Nach Abschluss der Postfachverschiebungen wird empfohlen, die abgeschlossenen Migrationsbatches zu entfernen, um die Wahrscheinlichkeit von Fehlern zu minimieren, wenn dieselben Benutzer erneut verschoben werden.

So entfernen Sie einen abgeschlossenen Migrationsbatch:

1.  Öffnen Sie die EAC, und navigieren Sie zu **Office 365** \> **Empfänger** \> **Migrationen**.

2.  Klicken Sie auf einen abgeschlossenen Migrationsbatch, und klicken Sie dann auf **Löschen** ![Löschen (Symbol)](images/JJ906432.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

3.  Klicken Sie im Warndialogfeld zur Bestätigung des Löschvorgangs auf **Ja**.

## Schritt 5: Erneutes Aktivieren des Offlinezugriffs für Outlook im Web

Mit dem Offlinezugriff in Outlook im Web (wurde zuvor als Outlook Web App bezeichnet) können Benutzer auf ihr Postfach zugreifen, wenn sie nicht mit einem Netzwerk verbunden sind. Beim Migrieren von Exchange-Postfächern zu Exchange Online müssen Benutzer die Offlinezugriffseinstellung in ihrem Browser zurücksetzen, um Outlook im Web offline verwenden zu können. Weitere Informationen über den Offlinezugriff in Outlook im Web, über die Browser, die diesen unterstützen, und darüber, wie er aktiviert werden kann, finden Sie unter [Offlineverwendung von Outlook Web App](https://go.microsoft.com/fwlink/p/?linkid=286942).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Beim Verschieben vorhandener Benutzerpostfächer zwischen den lokalen und den Exchange Online-Organisationen ist der erfolgreiche Abschluss des Assistenten für Remoteverschiebungen ein erster Hinweis darauf, dass das Postfach erwartungsgemäß verschoben wurde.

Da die Postfachverschiebung mehrere Minuten in Anspruch nehmen kann, können Sie den erfolgreichen Abschluss auch überprüfen, indem Sie die EAC öffnen und **Office 365** \> **Empfänger** \> **Migration** auswählen, um den Verschiebungsstatus für die im Assistenten für Remoteverschiebungen ausgewählten Postfächer anzuzeigen. Während der Postfachverschiebung zeigt der **Status** den Wert **Synchronisierung** bzw. den Wert **Abgeschlossen** an, wenn das Postfach erfolgreich in die lokale oder die Exchange Online-Organisation verschoben wurde.

Nach Abschluss der Postfachverschiebung können Sie die Postfacheigenschaften überprüfen, um sicherzustellen, dass das in der lokalen oder Exchange Online-Organisation befindliche Remotepostfach erfolgreich verschoben wurde. Navigieren Sie dazu in der EAC für die lokale Organisation oder die Exchange Online-Organisation zu **Empfänger** \> **Postfächer**. Das Benutzerpostfach sollte für Exchange Online-Postfächer als **Postfachtyp** den Wert **Office 365** und für lokale Postfächer den Wert **Benutzer** aufweisen.

Sie können auch das folgende Cmdlet in der Exchange-Verwaltungsshell ausführen, um den Status des Migrationsbatches zu überprüfen.

    Get-MigrationBatch -Identity <batch name>

Liegt ein Problem vor? Bitten Sie in den Office 365-Foren um Hilfe. Für den Zugriff auf die Foren müssen Sie sich mit einem Konto anmelden, das über Administratorzugriff auf Ihren cloudbasierten Dienst verfügt. Besuchen Sie die Foren unter: [Office 365-Foren](https://go.microsoft.com/fwlink/p/?linkid=201915)

## Neu bei Office 365?


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/Dn249373.eac8a413-9498-4220-8544-1e37d1aaea13(EXCHG.150).png" title="Das Kurzsymbol für LinkedIn Learning" alt="Das Kurzsymbol für LinkedIn Learning" /> <strong>Neu bei Office 365?</strong><br />
Entdecken Sie die kostenlosen Videokurse für <a href="https://support.office.com/de-de/article/office-365-admin-and-it-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5">Office 365 admins and IT pros</a>, präsentiert von LinkedIn Learning.</p></td>
</tr>
</tbody>
</table>


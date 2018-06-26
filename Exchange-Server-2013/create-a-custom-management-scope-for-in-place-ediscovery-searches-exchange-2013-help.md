---
title: 'Erstellen eines benutzerdefinierten Verwaltungsbereichs für die Compliance-eDiscovery-Suche: Exchange 2013 Help'
TOCTitle: Erstellen eines benutzerdefinierten Verwaltungsbereichs für die Compliance-eDiscovery-Suche
ms:assetid: 1543aefe-3709-402c-b9cd-c11fe898aad1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn741464(v=EXCHG.150)
ms:contentKeyID: 62219860
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines benutzerdefinierten Verwaltungsbereichs für die Compliance-eDiscovery-Suche

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-01-21_

Sie können einen benutzerdefinierten Verwaltungsbereich verwenden, damit bestimmte Personen oder Gruppen Compliance-eDiscovery verwenden können, um eine Teilmenge der Postfächer in Ihrer Exchange 2013- oder Exchange Online-Organisation zu durchsuchen. Beispielsweise können Sie einen Discovery-Manager nur die Postfächer der Benutzer an einem bestimmten Standort oder in einer bestimmten Abteilung durchsuchen lassen. Zu diesem Zweck können Sie einen benutzerdefinierten Verwaltungsbereich erstellen. In diesem benutzerdefinierten Verwaltungsbereich wird über einen Empfängerfilter gesteuert, welche Postfächer durchsucht werden können. In Bereichen mit Empfängerfiltern werden Filter verwendet, um bestimmte Empfänger basierend auf dem Empfängertyp oder anderen Eigenschaften zu erfassen.

Bei Verwendung von Compliance-eDiscovery ist die einzige Eigenschaft eines Benutzerpostfachs, die Sie zum Erstellen eines Empfängerfilters für einen benutzerdefinierten Bereich verwenden können, die Mitgliedschaft in Verteilergruppen (der tatsächliche Name der Eigenschaft ist *MemberOfGroup*). Wenn Sie andere Eigenschaften verwenden, wie beispielsweise *CustomAttributeN*, *Department* oder *PostalCode* schlägt die Suche fehl, wenn sie von einem Mitglied der Rollengruppe ausgeführt wird, der der benutzerdefinierte Bereich zugewiesen ist.

Weitere Informationen zu Verwaltungsbereichen finden Sie unter:

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichs-Filtern](understanding-management-role-scope-filters-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Wie bereits erwähnt, können Sie nur die Gruppenmitgliedschaft als Empfängerfilter verwenden, um einen benutzerdefinierten Empfängerfilterbereich zu erstellen, der für eDiscovery verwendet werden soll. Alle anderen Empfängereigenschaften können nicht zum Einrichten eines benutzerdefinierten Bereichs für eDiscovery-Suchen verwendet werden. Beachten Sie, dass die Mitgliedschaft in einer dynamischen Verteilergruppe ebenfalls nicht verwendet werden kann.

  - Führen Sie die Schritte 1 bis 3 durch, damit ein Discovery-Manager die Suchergebnisse einer eDiscovery-Suche exportiert, bei der ein benutzerdefinierter Verwaltungsbereich verwendet wird.

  - Wenn Ihr Discovery-Manager keine Vorschau der Suchergebnisse anzeigen muss, können Sie Schritt 4 überspringen.

  - Wenn Ihr Discovery-Manager die Suchergebnisse nicht kopieren muss, können Sie Schritt 5 überspringen.

## Schritt 1: Organisieren von Benutzern in Verteilergruppen für eDiscovery

Um eine Teilmenge der Postfächer in Ihrer Organisation zu durchsuchen oder um den Bereich der Quellpostfächer einzuschränken, die ein Discovery-Manager durchsuchen kann, müssen Sie die Teilmenge der Postfächer in einer oder mehreren Verteilergruppen zusammenfassen. Wenn Sie einen benutzerdefinierten Verwaltungsbereich in Schritt 2 erstellen, verwenden Sie diese Verteilergruppen als Empfängerfilter zum Erstellen eines benutzerdefinierten Verwaltungsbereichs. Dadurch erhält ein Discovery-Manager die Möglichkeit, nur die Postfächer der Benutzer zu durchsuchen, die Mitglied einer bestimmten Gruppe sind.

Sie können bereits vorhandene Verteilergruppen mit eDiscovery verwenden oder neue Verteilergruppen erstellen. Unter Weitere Informationen am Ende dieses Themas erhalten Sie Tipps zum Erstellen von Verteilergruppen, die verwendet werden können, um den Umfang von eDiscovery-Suchen festzulegen.

## Schritt 2: Erstellen eines benutzerdefinierten Verwaltungsbereichs

Nun erstellen Sie einen benutzerdefinierten Verwaltungsbereich, der durch die Mitgliedschaft in einer Verteilergruppe definiert ist (mit dem Empfängerfilter *MemberOfGroup*). Wenn dieser Bereich auf eine für eDiscovery verwendete Rollengruppe angewendet wird, können die Mitglieder der Rollengruppe die Postfächer der Benutzer durchsuchen, die Mitglieder der Verteilergruppe sind, die zum Erstellen des benutzerdefinierten Bereichs verwendet wurde.

Bei diesem Verfahren wird ein benutzerdefinierter Bereich namens "eDiscovery-Bereich für Ottawa-Benutzer" (Ottawa Users eDiscovery Scope) mit Befehlen der Exchange-Verwaltungsshell erstellt. Die Verteilergruppe "Ottawa-Benutzer" (Ottawa Users) wird in diesem Verfahren für den Empfängerfilter des benutzerdefinierten Bereichs festgelegt.

1.  Führen Sie diesen Befehl aus, um die Eigenschaften der Gruppe "Ottawa-Benutzer" (Ottawa Users) abzurufen und in einer Variablen zu speichern, die im nächsten Befehl verwendet wird.
    
        $DG = Get-DistributionGroup -Identity "Ottawa Users"

2.  Führen Sie diesen Befehl aus, um einen benutzerdefinierten Verwaltungsbereich basierend auf der Mitgliedschaft in der Verteilergruppe "Ottawa-Benutzer" (Ottawa Users) zu erstellen.
    
        New-ManagementScope "Ottawa Users eDiscovery Scope" -RecipientRestrictionFilter "MemberOfGroup -eq '$($DG.DistinguishedName)'"
    
    Der Distinguished Name der Verteilergruppe, der in der Variablen **$DG** enthalten ist, wird zum Erstellen des Empfängerfilters für den neuen Verwaltungsbereich verwendet.

## Schritt 3: Erstellen einer Verwaltungsrollengruppe

In diesem Schritt erstellen Sie eine neue Verwaltungsrollengruppe und weisen den in Schritt 2 erstellten benutzerdefinierten Bereich zu. 2. Fügen Sie die Rollen "Gesetzliche Aufbewahrungsfrist" und "Postfachsuche" hinzu, sodass die Rollenmitglieder Compliance-eDiscovery-Suchen durchführen und Compliance-Archive oder das Beweissicherungsverfahren für Postfächer festlegen können. Sie können dieser Rollengruppe auch Mitglieder hinzufügen, die dann die Postfächer der Mitglieder der Verteilergruppe durchsuchen können, die zum Erstellen des benutzerdefinierten Bereichs in Schritt 2 verwendet wurde.

In den folgenden Beispielen wird die Sicherheitsgruppe "eDiscovery-Manager für Ottawa-Benutzer" (Ottawa Users eDiscovery Managers) als Mitglied dieser Rollengruppe hinzugefügt. Für diesen Schritt können Sie entweder die Shell oder das EAC verwenden.

## Erstellen einer Verwaltungsrollengruppe mit der Shell

Führen Sie diesen Befehl aus, um eine neue Rollengruppe zu erstellen, die den in Schritt 2 erstellten benutzerdefinierten Bereich verwendet. 2. Mit dem Befehl werden auch die Rollen "Gesetzliche Aufbewahrungsfrist" und "Postfachsuche" und die Sicherheitsgruppe "eDiscovery-Manager für Ottawa-Benutzer" (Ottawa Users eDiscovery Managers) als Mitglieder der neuen Rollengruppe hinzugefügt.

    New-RoleGroup "Ottawa Discovery Management" -Roles "Mailbox Search","Legal Hold" -CustomRecipientWriteScope "Ottawa Users eDiscovery Scope" -Members "Ottawa Users eDiscovery Managers"

## Erstellen einer Verwaltungsrollengruppe im Exchange Admin Center

1.  Gehen Sie im Exchange Admin Center zu **Berechtigungen** \> **Administratorrollen**, und klicken Sie dann auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie unter **Neue Rollengruppe** die folgenden Informationen an:
    
      - **Name**: Geben Sie einen aussagekräftigen Name für die neue Rollengruppe ein. Verwenden Sie bei diesem Beispiel **Ottawa-Discoveryverwaltung**.
    
      - **Schreibbereich**: Wählen Sie den benutzerdefinierten Verwaltungsbereich aus, den Sie in Schritt 2 erstellt haben. Dieser Bereich wird auf die neue Rollengruppe angewendet.
    
      - **Rollen**: Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und fügen Sie der neuen Rollengruppe die Rollen **Gesetzliche Aufbewahrungsfrist** und **Postfachsuche** hinzu.
    
      - **Mitglieder**: Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie die Benutzer, die Sicherheitsgruppe oder die Rollengruppen aus, die Sie der neuen Rollengruppe als Mitglieder hinzufügen möchten. Bei diesem Beispiel können die Mitglieder der Sicherheitsgruppe **eDiscovery-Manager für Ottawa-Benutzer** (Ottawa Users eDiscovery Managers) nur die Postfächer der Benutzer durchsuchen, die Mitglieder der Verteilergruppe **Ottawa-Benutzer** (Ottawa Users) sind.

3.  Klicken Sie auf **Speichern**, um die Rollengruppe zu erstellen.
    
    Nachfolgend finden Sie ein Beispiel, wie das Fenster **Neue Rollengruppe** anschließend aussieht.
    
    ![Eine neue Rollengruppe für einen benutzerdefinierten Bereich erstellen](images/Dn741464.a6e3419f-d5d9-404f-890d-ad35f499756f(EXCHG.150).gif "Eine neue Rollengruppe für einen benutzerdefinierten Bereich erstellen")  

## (Optional) Schritt 4: Hinzufügen von Discovery-Managern als Mitglieder der Verteilergruppe, die zum Erstellen des benutzerdefinierten Verwaltungsbereichs verwendet wurde

Diesen Schritt müssen Sie nur ausführen, wenn ein Discovery-Manager eine Vorschau der eDiscovery-Suchergebnisse anzeigen soll.

Führen Sie diesen Befehl aus, um die Sicherheitsgruppe "eDiscovery-Manager für Ottawa-Benutzer" (Ottawa Users eDiscovery Managers) als Mitglied der Verteilergruppe "Ottawa-Benutzer" (Ottawa Users) hinzuzufügen.

    Add-DistributionGroupMember -Identity "Ottawa Users" -Member "Ottawa Users eDiscovery Managers"

Sie können Mitglieder einer Verteilergruppe auch im Exchange Admin Center hinzufügen. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Verteilergruppen](create-and-manage-distribution-groups-exchange-2013-help.md).

## (Optional) Schritt 5: Hinzufügen eines Discoverypostfachs als Mitglied der Verteilergruppe, die zum Erstellen des benutzerdefinierten Verwaltungsbereichs verwendet wurde

Diesen Schritt müssen Sie nur ausführen, wenn ein Discovery-Manager eDiscovery-Suchergebnisse kopieren soll.

Führen Sie diesen Befehl aus, um das Discoverypostfach "Ottawa-Discoverypostfach" (Ottawa Discovery Mailbox) als Mitglied der Verteilergruppe "Ottawa-Benutzer" (Ottawa Users) hinzuzufügen.

    Add-DistributionGroupMember -Identity "Ottawa Users" -Member "Ottawa Discovery Mailbox"


> [!NOTE]
> Zum Öffnen eines Discoverypostfachs und Anzeigen der Suchergebnisse muss Discovery-Managern Vollzugriff für das Discoverypostfach gewährt werden. Weitere Informationen finden Sie unter <A href="create-a-discovery-mailbox-exchange-2013-help.md">Erstellen eines Discoverypostfachs</A>.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Im Folgenden sind einige Möglichkeiten aufgeführt, wie Sie überprüfen können, ob die benutzerdefinierten Verwaltungsbereiche für eDiscovery erfolgreich implementiert wurden. Vergewissern Sie sich bei der Überprüfung, dass der Benutzer, der die eDiscovery-Suchen ausführt, ein Mitglied der Rollengruppe ist, die den benutzerdefinierten Verwaltungsbereich verwendet.

  - Erstellen Sie eine eDiscovery-Suche, und wählen Sie die Verteilergruppe, mit der der benutzerdefinierte Verwaltungsbereich erstellt wurde, als Quelle der zu durchsuchenden Postfächer aus. Alle Postfächer sollten erfolgreich durchsucht werden.

  - Erstellen Sie eine eDiscovery-Suche, und durchsuchen Sie die Postfächer von Benutzern, die keine Mitglieder der Verteilergruppe sind, die zum Erstellen des benutzerdefinierten Bereichs verwendet wurde. Die Suche sollte fehlschlagen, da der Discovery-Manager nur Postfächer der Benutzer durchsuchen kann, die Mitglieder der Verteilergruppe sind, mit der der benutzerdefinierte Verwaltungsbereich erstellt wurde. In diesem Fall wird die folgende Fehlermeldung zurückgegeben: "Postfach \<*name of mailbox*\> kann nicht durchsucht werden, da der aktuelle Benutzer keine Berechtigung für den Zugriff auf das Postfach besitzt".

  - Erstellen Sie eine eDiscovery-Suche, und durchsuchen Sie die Postfächer der Benutzer, die Mitglieder der Verteilergruppe sind, die zum Erstellen des benutzerdefinierten Bereichs verwendet wurde. Schließen Sie in diese Suche auch die Postfächer der Benutzer ein, die keine Mitglieder sind. Die Suche sollte teilweise erfolgreich sein. Die Postfächer der Mitglieder der Verteilergruppe, mit der der benutzerdefinierte Verwaltungsbereich erstellt wurde, sollten erfolgreich durchsucht werden. Das Durchsuchen der Postfächer der Benutzer, die keine Mitglieder der Gruppe sind, sollte fehlschlagen.

## Weitere Informationen

  - Da Verteilergruppen in diesem Szenario nicht zur Nachrichtenübermittlung sondern zum Festlegen des Umfangs von eDiscovery-Suchen verwendet werden, sollten Sie Folgendes erwägen, wenn Sie Verteilergruppen für eDiscovery erstellen und konfigurieren:
    
      - Erstellen Sie Verteilergruppen mit geschlossener Mitgliedschaft, sodass Mitglieder nur von Gruppenbesitzern hinzugefügt oder aus der Gruppe entfernt werden können. Wenn Sie die Gruppe in der Shell erstellen, verwenden Sie die Syntax `MemberJoinRestriction closed` und `MemberDepartRestriction closed`.
    
      - Aktivieren Sie die Moderation der Gruppe, sodass jede an die Gruppe gesendete Nachricht zunächst an die Gruppenmoderatoren gesendet wird, die die Nachricht genehmigen oder zurückweisen können. Wenn Sie die Gruppe in der Shell erstellen, verwenden Sie die Syntax `ModerationEnabled $true`. Im Exchange Admin Center können Sie die Moderation aktivieren, nachdem die Gruppe erstellt wurde.
    
      - Blenden Sie die Verteilergruppe im freigegebenen Adressbuch der Organisation aus. Verwenden Sie das Exchange Admin Center oder das Cmdlet **Set-DistributionGroup**, nachdem die Gruppe erstellt wurde. Bei Verwendung der Shell verwenden Sie die Syntax `HiddenFromAddressListsEnabled $true`.
    
    Im folgenden Beispiel erstellt der erste Befehl eine Verteilergruppe mit geschlossener Mitgliedschaft und aktivierter Moderation. Der zweite Befehl blendet die Gruppe im freigegebenen Adressbuch aus.
    
        New-DistributionGroup -Name "Vancouver Users eDiscovery Scope" -Alias VancouverUserseDiscovery -MemberJoinRestriction closed -MemberDepartRestriction closed -ModerationEnabled $true
    
        Set-DistributionGroup "Vancouver Users eDiscovery Scope" -HiddenFromAddressListsEnabled $true
    
    Weitere Informationen zum Erstellen und Verwalten von Verteilergruppen finden Sie unter [Erstellen und Verwalten von Verteilergruppen](create-and-manage-distribution-groups-exchange-2013-help.md).

  - Obwohl Sie nur die Mitgliedschaft in Verteilergruppen als Empfängerfilter für einen für eDiscovery genutzten benutzerdefinierten Verwaltungsbereich verwenden können, können Sie jedoch Benutzer dieser Verteilergruppe mithilfe weiterer Empfängereigenschaften hinzufügen. Hier sind einige Beispiele dafür, wie mit den Cmdlets **Get-Mailbox** und **Get-Recipient** eine bestimmte Gruppe von Benutzern basierend auf allgemeinen Benutzer- oder Postfachattributen zurückgegeben wird.
    
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'Department -eq "HR"'
    
        Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'CustomAttribute15 -eq "VancouverSubsidiary"'
    
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'PostalCode -eq "98052"'
    
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'StateOrProvince -eq "WA"'
    
        Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize unlimited -OrganizationalUnit "namsr01a002.sdf.exchangelabs.com/Microsoft Exchange Hosted Organizations/contoso.onmicrosoft.com"

  - Sie können die Beispiele aus dem vorherigen Punkt der Auflistung verwenden, um eine Variable zu erstellen, die mit dem Cmdlet **Add-DistributionGroupMember** verwendet werden kann, um eine Gruppe von Benutzern einer Verteilergruppe hinzuzufügen. Im folgenden Beispiel erstellt der erste Befehl eine Variable, die alle Benutzerpostfächer enthält, die den Wert **Vancouver** für die Eigenschaft *Department* in ihrem Benutzerkonto aufweisen. Der zweite Befehl fügt diese Benutzer der Verteilergruppe "Vancouver-Benutzer" (Vancouver Users) hinzu.
    
        $members = Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'Department -eq "Vancouver"'
    
        $members | ForEach {Add-DistributionGroupMember "Ottawa Users" -Member $_.Name}

  - Mit dem Cmdlet **Add-RoleGroupMember** können Sie ein Mitglied einer bestehenden Rollengruppe hinzufügen, mit der der Umfang von eDiscovery-Suchen festgelegt wird. Der folgende Befehl beispielsweise fügt den Benutzer "admin@ottawa.contoso.com" der Rollengruppe "Ottawa-Discoveryverwaltung" (Ottawa Discovery Management) hinzu.
    
        Add-RoleGroupMember "Vancouver Discovery Management" -Member paralegal@vancouver.contoso.com
    
    Sie können Mitglieder einer Rollengruppe auch im Exchange Admin Center hinzufügen. Weitere Informationen finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md) im Abschnitt "Hinzufügen von Mitgliedern zu einer Rollengruppe".

  - In Exchange Online können Sie einen benutzerdefinierten Verwaltungsbereich, der für eDiscovery verwendet wird, nicht zum Durchsuchen inaktiver Postfächer verwenden. Der Grund dafür ist, dass das inaktive Postfach nicht Mitglied einer Verteilergruppe sein kann. Nehmen wir beispielsweise an, dass ein Benutzer Mitglied einer Verteilergruppe ist, die verwendet wurde, um einen benutzerdefinierten Verwaltungsbereich für eDiscovery zu erstellen. Der Benutzer verlässt die Organisation und sein Postfach wird deaktiviert (durch Aktivieren des Beweissicherungsverfahrens oder des Compliance-Archivs und Löschen des zugehörigen Office 365-Benutzerkontos). Daraufhin ist der Benutzer als Mitglied aus allen Verteilergruppen entfernt, einschließlich der Gruppe, die zur Erstellung des benutzerdefinierten Verwaltungsbereichs für eDiscovery verwendet wurde. Versucht ein Discovery-Manager (der Mitglied der Rollengruppe ist, die dem benutzerdefinierten Verwaltungsbereich zugeordnet ist), das inaktive Postfach zu durchsuchen, tritt ein Fehler auf. Um inaktive Postfächer durchsuchen zu können, muss der Discovery-Manager Mitglied der Rollengruppe "Discoveryverwaltung" oder einer anderen Rollengruppe sein, die über Berechtigungen zum Durchsuchen der gesamten Organisation verfügt.
    
    Weitere Informationen zu inaktiven Postfächern finden Sie unter [Inaktive Postfächer in Exchange Online](https://technet.microsoft.com/de-de/library/dn798632\(v=exchg.150\)).


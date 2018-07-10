---
title: 'Aktivieren oder Deaktivieren von hierarchischen Adressbüchern: Exchange 2013 Help'
TOCTitle: Aktivieren oder Deaktivieren von hierarchischen Adressbüchern
ms:assetid: b4c3a175-ce5e-4bfb-a4a0-92d25f3644b3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff607473(v=EXCHG.150)
ms:contentKeyID: 50476492
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren von hierarchischen Adressbüchern

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können ein hierarchisches Adressbuch konfigurieren, eine Funktion, die Benutzern in Microsoft Outlook 2010 oder höher zur Verfügung steht. Mit einem hierarchischen Adressbuch können Benutzer anhand einer auf Rang- oder Führungsstruktur basierenden Organisationshierarchie nach Empfängern in ihrer Exchange-Organisation suchen. Weitere Informationen zu hierarchischen Adressbüchern finden Sie unter [Hierarchische Adressbücher](hierarchical-address-books-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Stunde.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verteilergruppen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Bevor Sie beginnen, sollten Sie das Thema [Hierarchische Adressbücher](hierarchical-address-books-exchange-2013-help.md) lesen. Sie sollten wissen, ob ein hierarchisches Adressbuch für Ihre Exchange-Organisation geeignet ist.

  - Machen Sie sich mit der aktuellen Konfiguration von Organisationseinheiten, Gruppen, Benutzern und Kontakten in Ihrer Exchange-Organisation vertraut.

  - Machen Sie sich mit den Cmdlets und den zugehörigen Parametern in der folgenden Tabelle vertraut, die zur Konfiguration eines hierarchischen Adressbuchs erforderlich sind.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Cmdlet</th>
    <th>Parameter</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><a href="https://technet.microsoft.com/de-de/library/aa997443(v=exchg.150)">Set-OrganizationConfig</a></p></td>
    <td><p><em>HierarchicalAddressBookRoot</em></p></td>
    </tr>
    <tr class="even">
    <td><p><a href="https://technet.microsoft.com/de-de/library/bb123770(v=exchg.150)">Set-Group</a></p></td>
    <td><p><em>IsHierarchicalGroup</em></p>
    <p><em>SeniorityIndex</em></p>
    <p><em>PhoneticDisplayName</em></p></td>
    </tr>
    <tr class="odd">
    <td><p><a href="https://technet.microsoft.com/de-de/library/aa998221(v=exchg.150)">Set-User</a></p></td>
    <td><p><em>SeniorityIndex</em></p>
    <p><em>PhoneticDisplayName</em></p></td>
    </tr>
    <tr class="even">
    <td><p><a href="https://technet.microsoft.com/de-de/library/bb124535(v=exchg.150)">Set-Contact</a></p></td>
    <td><p><em>SeniorityIndex</em></p>
    <p><em>PhoneticDisplayName</em></p></td>
    </tr>
    </tbody>
    </table>


  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren eines hierarchischen Adressbuchs mit der Shell


> [!NOTE]
> Ein hierarchisches Adressbuch kann nicht mit der Exchange-Verwaltungskonsole aktiviert werden. Nach der Aktivierung des Adressbuchs kann die Exchange-Verwaltungskonsole aber dazu verwendet werden, die Mitgliedschaft der Gruppen in der Organisationshierarchie zu verwalten.



Für dieses Beispiel wird eine Organisationseinheit "HAB" für das hierarchische Adressbuch erstellt. Der Name der Domäne für die Organisation lautet "Contoso-dom", der Name der Organisation auf oberster Ebene innerhalb der Hierarchie (die *Stammorganisation*) lautet "Contoso,Ltd". Unterhalb von "Contoso,Ltd" werden als untergeordnete Organisationen die Gruppen "Corporate Office", "Product Support Organization" und "Sales & Marketing Organization" erstellt. Zusätzlich werden unterhalb von "Corporate Office" als untergeordnete Organisationen die Gruppen "Human Resources", "Accounting Group" und "Administration Group" erstellt.

Weitere Informationen zum Erstellen von Verteilergruppen finden Sie unter [Erstellen und Verwalten von Verteilergruppen](create-and-manage-distribution-groups-exchange-2013-help.md).

1.  Erstellen einer Organisationseinheit "HAB" in der Organisation "Contoso". Sie können Active Directory-Benutzer und -Computer verwenden oder an einer Eingabeaufforderung den folgenden Befehl eingeben.
    

    > [!NOTE]
    > Alternativ können Sie eine vorhandene Organisationseinheit in Ihrer Exchange-Gesamtstruktur verwenden.

    
        dsadd ou "OU=HAB,DC=Contoso-dom,DC=Contoso,DC=com"
    

    > [!NOTE]
    > Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=198986">Erstellen einer neuen Organisationseinheit</A>.



2.  Erstellen der Stammverteilergruppe "Contoso,Ltd" für das hierarchische Adressbuch.
    

    > [!NOTE]
    > Für das Beispiel in diesem Thema wird die Shell verwendet. Sie können eine Verteilergruppe jedoch auch mit der Exchange-Verwaltungskonsole erstellen. Weitere Informationen finden Sie unter <A href="create-and-manage-distribution-groups-exchange-2013-help.md">Erstellen und Verwalten von Verteilergruppen</A>.

    
        New-DistributionGroup -Name "Contoso,Ltd" -DisplayName "Contoso,Ltd" -Alias "ContosoRoot" -OrganizationalUnit "Contoso-dom.Contoso.com/HAB" -SamAccountName "ContosoRoot" -Type "Distribution"

3.  Festlegen von "Contoso,Ltd" als Stammorganisation für das hierarchische Adressbuch.
    
        Set-OrganizationConfig -HierarchicalAddressBookRoot "Contoso,Ltd"

4.  Erstellen von Verteilergruppen für die anderen Ebenen innerhalb des hierarchischen Adressbuchs. Für dieses Beispiel würden Sie die folgenden Gruppen erstellen: "Corporate Office", "Product Support Organization", "Sales & Marketing Organization", "Human Resources", "Accounting Group" und "Administration Group". In diesem Beispiel wird die Verteilergruppe "Corporate Office" erstellt.
    

    > [!NOTE]
    > Für das Beispiel in diesem Thema wird die Shell verwendet. Sie können Verteilergruppen jedoch auch mit der Exchange-Verwaltungskonsole erstellen. Weitere Informationen finden Sie unter <A href="create-and-manage-distribution-groups-exchange-2013-help.md">Erstellen und Verwalten von Verteilergruppen</A>.

    
        New-DistributionGroup -Name "Corporate Office" -DisplayName "Corporate Office" -Alias "CorporateOffice" -OrganizationalUnit "Contoso-dom.Contoso.com/HAB" -SamAccountName "CorporateOffice" -Type "Distribution"

5.  Festlegen der einzelnen Gruppen als Mitglieder des hierarchischen Adressbuchs. Für dieses Beispiel würden die folgenden Gruppen als hierarchische Gruppen festgelegt: "Contoso,Ltd", "Corporate Office", "Product Support Organization", "Sales & Marketing Organization", "Human Resources", "Accounting Group" und "Administration Group". In diesem Beispiel wird die Verteilergruppe "Contoso,Ltd" als Mitglied des hierarchischen Adressbuchs festgelegt.
    
        Set-Group -Identity "Contoso,Ltd" -IsHierarchicalGroup $true

6.  Hinzufügen aller untergeordneten Gruppen als Mitglieder der Stammorganisation. In diesem Beispiel werden die Verteilergruppen "Corporate Office", "Product Support Organization" und "Sales & Marketing Organization" als Mitglieder der Stammorganisation "Contoso,Ltd" im hierarchischen Adressbuch hinzugefügt. In diesem Beispiel wird die Verteilergruppe "Corporate Office" als Mitglied der Stammverteilergruppe "Contoso,Ltd" hinzugefügt.
    

    > [!NOTE]
    > In diesem Beispiel wird der Alias der Verteilergruppen verwendet.

    
        Add-DistributionGroupMember -Identity "ContosoRoot" -Member "CorporateOffice"

7.  Hinzufügen aller untergeordneten Gruppen der Verteilergruppe "Corporate Office" als Mitglieder dieser Gruppe. Für dieses Beispiel werden die Verteilergruppen "Human Resources", "Accounting Group" und "Administration Group" als Mitglieder der Verteilergruppe "Corporate Office" hinzugefügt. In diesem Beispiel wird die Verteilergruppe "Human Resources" als Mitglied der Verteilergruppe "Corporate Office" hinzugefügt.
    

    > [!NOTE]
    > In diesem Beispiel wird der Alias der Verteilergruppen verwendet, und es wird davon ausgegangen, dass "HumanResources" der Alias der Verteilergruppe "Human Resources" ist.

    
        Add-DistributionGroupMember -Identity "CorporateOffice" -Member "HumanResources"

8.  Hinzufügen von Benutzern zu den Gruppen im hierarchischen Adressbuch. Für dieses Beispiel ist "David Hamilton" (SMTP-Adresse "DHamilton@contoso.com") ein vorhandener Benutzer in der Organisationseinheit "Contoso-dom.Contoso.com/Users" und wird zur Gruppe "Corporate Office" hinzugefügt. Wiederholen Sie diesen Schritt, um andere Benutzer zu Gruppen im hierarchischen Adressbuch hinzuzufügen.
    
        Add-DistributionGroupMember -Identity "CorporateOffice" -Member "DHamilton"

9.  Festlegen des Parameters *SeniorityIndex* für Gruppen im hierarchischen Adressbuch. Für dieses Beispiel enthält die Gruppe "Corporate Office" drei untergeordnete Gruppen: "Human Resources", "Accounting Group" und "Administration Group". Für dieses Beispiel werden die Gruppen nicht aufsteigend in alphabetischer Reihenfolge (die Standardeinstellung) sortiert. Stattdessen lautet die bevorzugte Sortierung "Human Resources" (*SeniorityIndex* = 100), "Accounting Group" (*SeniorityIndex* = 50) und dann "Administration Group" (*SeniorityIndex* = 25). In diesem Beispiel wird der Parameter *SeniorityIndex* für die Gruppe "Human Resources" auf 100 festgelegt.
    
        Set-Group -Identity "Human Resources" -SeniorityIndex 100
    

    > [!NOTE]
    > Der Parameter <EM>SeniorityIndex</EM> ist ein numerischer Wert, um Gruppen oder Benutzer in einem hierarchischen Adressbuch in absteigender numerischer Reihenfolge zu sortieren. Wenn der Parameter <EM>SeniorityIndex</EM> nicht gesetzt wird oder für zwei oder mehr Benutzer übereinstimmt, wird für die Sortierreihenfolge des hierarchischen Adressbuchs der Parameterwert von <EM>PhoneticDisplayName</EM> verwendet, um die Benutzer in aufsteigender alphabetischer Reihenfolge aufzulisten. Wenn der Parameter <EM>PhoneticDisplayName</EM> nicht festgelegt wird, wird für die Sortierung des hierarchischen Adressbuchs standardmäßig der Parameterwert von <EM>DisplayName</EM> verwendet, und die Benutzer werden in aufsteigender alphabetischer Reihenfolge aufgelistet.



10. Festlegen des Parameters *SeniorityIndex* für Benutzer in den Gruppen des hierarchischen Adressbuchs. Für dieses Beispiel enthält die Gruppe "Corporate Office" drei Benutzer: "Amy Alberts", "David Hamilton" und "Rajesh M. Patel". Für dieses Beispiel werden die Benutzer nicht in aufsteigender alphabetischer Reihenfolge (die Standardeinstellung) sortiert. Stattdessen lautet die bevorzugte Sortierung "David Hamilton" (*SeniorityIndex* = 100), "Rajesh M. Patel" (*SeniorityIndex* = 50) und dann "Amy Alberts" (*SeniorityIndex* = 25). In diesem Beispiel wird der Parameter *SeniorityIndex* für den Benutzer "David Hamilton" auf 100 festgelegt.
    
        Set-User -Identity "DHamilton@contoso.com" -SeniorityIndex 100

Nach dem Ausführen der vorangehenden Schritte ist das hierarchische Adressbuch in Outlook sichtbar. Öffnen Sie Outlook, und klicken Sie auf **Adressbuch**, um das hierarchische Adressbuchs anzuzeigen. Das hierarchische Adressbuch wird auf der Registerkarte **Organisation** angezeigt und entspricht in etwa der folgenden Abbildung.

**Beispiel eines hierarchischen Adressbuchs für "Contoso,Ltd"**

![Hierarchisches Adressbuch – Dialogfeld](images/Ff629379.d8cc782f-61cd-44c4-9c74-432ebea0c3db(EXCHG.150).gif "Hierarchisches Adressbuch – Dialogfeld")

Nach dem Erstellen des hierarchischen Adressbuchs können Sie die Exchange-Verwaltungskonsole verwenden, um die Mitgliedschaft der Gruppen in der Organisationshierarchie zu verwalten. Zum Ändern des Parameters *SeniorityIndex* für neue Gruppen oder Benutzer muss jedoch die Shell verwendet werden.

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [New-DistributionGroup](https://technet.microsoft.com/de-de/library/aa998856\(v=exchg.150\))

  - [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\))

  - [Set-Group](https://technet.microsoft.com/de-de/library/bb123770\(v=exchg.150\))

  - [Add-DistributionGroupMember](https://technet.microsoft.com/de-de/library/bb124340\(v=exchg.150\))

  - [Set-User](https://technet.microsoft.com/de-de/library/aa998221\(v=exchg.150\))

## Deaktivieren eines hierarchischen Adressbuchs mithilfe der Shell

In diesem Beispiel wird die für das hierarchische Adressbuch verwendete Stammorganisation deaktiviert.

    Set-OrganizationConfig -HierarchicalAddressBookRoot $null


> [!NOTE]
> Die in der Struktur des hierarchischen Adressbuchs verwendete Stammorganisation oder die untergeordneten Gruppen werden über diesen Befehl nicht gelöscht, und die <EM>SeniorityIndex</EM>-Werte für Gruppen oder Benutzer werden nicht zurückgesetzt. Der Befehl verhindert lediglich, dass das hierarchische Adressbuch in Outlook angezeigt wird. Um das hierarchische Adressbuch erneut mit denselben Konfigurationseinstellungen zu aktivieren, muss lediglich die Stammorganisation aktiviert werden.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)).


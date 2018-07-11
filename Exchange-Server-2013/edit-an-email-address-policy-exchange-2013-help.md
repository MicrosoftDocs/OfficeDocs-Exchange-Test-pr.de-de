---
title: 'Bearbeiten einer E-Mail-Adressrichtlinie: Exchange 2013 Help'
TOCTitle: Bearbeiten einer E-Mail-Adressrichtlinie
ms:assetid: cc8b36a0-95f4-43e9-bc64-87646d2e14e4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124580(v=EXCHG.150)
ms:contentKeyID: 50476740
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.EditEmailAddressPolicyWizardForm.EmailAddressPolicyIntroductionPage
ms.translationtype: HT
---

# Bearbeiten einer E-Mail-Adressrichtlinie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-12-10_

E-Mail-Adressrichtlinien generieren die primären und sekundären E-Mail-Adressen für Ihre Empfänger (einschließlich Benutzern, Kontakten und Gruppen), damit diese E-Mails empfangen und senden können.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf E-Mail-Adressrichtlinien finden Sie unter [Verfahren für die E-Mail-Adressrichtlinie](email-address-policy-procedures-exchange-2013-help.md).

## Was müssen Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Mit der Exchange-Verwaltungskonsole (Exchange Administration Center, EAC) können Sie eine E-Mail-Adressrichtlinie nicht bearbeiten, wenn die Richtlinie mit der Shell erstellt wurde.

  - Wenn die E-Mail-Adressrichtlinie mit einem Empfängerfilter erstellt wurde, müssen Sie die Shell zum Bearbeiten der E-Mail-Adressrichtlinie verwenden. Weitere Informationen finden Sie unter [Erstellen einer E-Mail-Adressrichtlinie mithilfe der Empfängerfilterung](create-an-email-address-policy-by-using-recipient-filters-exchange-2013-help.md).

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Adressrichtlinien" im Thema [E-Mail-Adressen und Adressbücher](email-addresses-and-address-books-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Ändern der Empfänger, für die die Richtlinie gilt, mit der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Nachrichtenübermittlung** \> **E-Mail-Adressrichtlinien**.

2.  Wählen Sie in der Listenansicht die E-Mail-Adressrichtlinie aus, die Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie in **E-Mail-Adressrichtlinie** auf **Anwenden auf**, und ändern Sie die Einstellungen.

## Ändern der Priorität der E-Mail-Adressrichtlinie mithilfe der Exchange-Verwaltungskonsole

Ein Benutzer kann über mehrere Proxy-E-Mail-Adressen für dasselbe E-Mail-Konto verfügen (Beispiel: "ayla@exchange.mail.contoso.com" oder "ayla@contoso.com"). Diese E-Mail-Adressen können dann nach Priorität angewendet werden. Stellen Sie sich z. B. dieses Szenario vor: Sie verfügen über zwei E-Mail-Adressrichtlinien, denen Sie die Prioritäten 1 und 2 zuweisen. Wenn Sie eine weitere Richtlinie erstellen, wird ihr automatisch die Priorität 3 zugewiesen. Nehmen wir jedoch an, dass Sie zwei Richtlinien haben und angeben, dass eine davon die Priorität 1 erhält. Der anderen Richtlinie wurde dagegen beim Erstellen die Standardpriorität 2 zugewiesen. In diesem Fall erhält die als Nächstes von Ihnen erstellte Richtlinie standardmäßig die Priorität 2. Die vorherige Richtlinie mit der Priorität 2 erhält dann die Priorität 3.

1.  Navigieren Sie zu **Nachrichtenübermittlung** \> **E-Mail-Adressrichtlinien**.

2.  Wählen Sie die E-Mail-Adressrichtlinie aus, für die Sie die Priorität ändern möchten, und klicken Sie dann auf **Priorität erhöhen**![NACH-OBEN-TASTE (Symbol)](images/JJ150576.1732c727-328b-4a1a-b84d-6d7252c7dcab(EXCHG.150).gif "NACH-OBEN-TASTE (Symbol)") oder **Priorität heruntersetzen**![NACH-UNTEN-TASTE (Symbol)](images/JJ150576.ef5ca57d-a033-457b-bd92-6361877c33d0(EXCHG.150).gif "NACH-UNTEN-TASTE (Symbol)").

## Bearbeiten einer E-Mail-Adressrichtlinie mithilfe der Shell

In diesem Beispiel wird die E-Mail-Adressrichtlinie "South East Offices", die zurzeit Empfänger in Georgia, Alabama und Louisiana enthält, so bearbeitet, dass auch Empfänger in Texas berücksichtigt werden.

    Set-EmailAddressPolicy -Identity "South East Offices" -ConditionalStateorProvince "Georgia","Alabama","Louisiana","Texas"


> [!NOTE]
> Obwohl die E-Mail-Adressrichtlinie bereits für Empfänger in Georgia, Alabama und Louisiana gilt, müssen Sie auch diese im Parameter angeben, weil der Parameter Werte überschreibt. Er hängt keine Werte an bereits vorhandene Werte an.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-EmailAddressPolicy](https://technet.microsoft.com/de-de/library/bb124517\(v=exchg.150\)).


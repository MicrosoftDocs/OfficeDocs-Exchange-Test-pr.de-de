---
title: 'Voicemail für Benutzer: Exchange 2013 Help'
TOCTitle: Voicemail für Benutzer
ms:assetid: 48e1f43b-fb7e-4a52-a2cb-0fb5da6ca65f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997885(v=EXCHG.150)
ms:contentKeyID: 50475569
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Voicemail für Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-19_

Mit Unified Messaging (UM) können Benutzer in einer Exchange-Organisation ihre gesamten E-Mail- und Sprachnachrichten in einem einzigen Postfach empfangen. Die Unified Messaging- und Voicemailfunktionen steigern die Benutzerproduktivität erheblich und ermöglichen ein flexibleres Messaging in der gesamten Organisation.

Wenn Sie Ihrer Organisation einen Benutzer hinzufügen, haben Sie die Möglichkeit, ein Postfach zu erstellen oder eine Verbindung mit einem vorhandenen Postfach herzustellen. Nachdem das Postfach erstellt wurde oder der Benutzer mit einem vorhandenen Postfach verbunden wurde, können Sie das Postfach für Unified Messaging aktivieren, damit der Benutzer das Voicemailsystem und die zugehörigen Funktionen nutzen kann. Sobald der Benutzer fü̈r Unified Messaging aktiviert wurde, werden sä̈mtliche E-Mail-, Voicemail- und Faxnachrichten an das Postfach des Benutzers zugestellt. Mit Microsoft Office Outlook 2007 (oder höher), Outlook Web App, einem für Microsoft ExchangeActiveSync aktivierten Mobiltelefon, einem normalen Telefon oder Mobiltelefon können Benutzer auf ihre E-Mail- und Sprachnachrichten, auf ihre persönlichen Kontakte und auf Kalenderinformationen zugreifen.

**Inhalt**

Eigenschaften für Voicemailbenutzer

Beziehung zwischen einem Voicemailbenutzer und anderen UM-Komponenten

Durchwahlnummern und SIP-Adressen

Aktivieren eines Benutzers für UM und Voicemail mithilfe der Exchange-Verwaltungskonsole

Aktivieren eines Benutzers für UM und Voicemail mithilfe der Shell

Deaktivieren von Unified Messaging für einen Benutzer

## Eigenschaften für Voicemailbenutzer

Ein Benutzer muss über ein Postfach verfügen, bevor eine Aktivierung für Unified Messaging durchgeführt werden kann. Standardmäßig ist ein Benutzer, der über ein Postfach verfügt, nicht für Unified Messaging aktiviert. Nach der UM-Aktivierung können Sie die UM-Eigenschaften und Voicemailfunktionen für den Benutzer verwalten, ändern und konfigurieren. Sie können einen Benutzer mithilfe der Exchange-Verwaltungskonsole oder der Shell für Unified Messaging aktivieren. Weitere Informationen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)). Wenn Sie mehrere UM-Benutzer aktivieren möchten, verwenden Sie die Exchange-Verwaltungskonsole oder das Cmdlet **Enable-UMMailbox** in der Exchange-Verwaltungsshell.

## Beziehung zwischen einem Voicemailbenutzer und anderen UM-Komponenten

Wenn Sie einen Benutzer für Unified Messaging aktivieren, muss eine Zuordnung zu oder eine Verknüpfung mit einer vorhandenen UM-Postfachrichtlinie bestehen, und Sie müssen eine Durchwahlnummer angeben. Sie können einen Benutzer einer UM-Postfachrichtlinie zuordnen, indem Sie bei der UM-Aktivierung des Benutzers das Cmdlet **Enable-UMMailbox** in der Shell verwenden oder die UM-Postfachrichtlinie auswählen. Standardmäßig wird beim Erstellen eines UM-Wählplans eine neue UM-Postfachrichtlinie erstellt. Sie können diese Richtlinie entweder ändern, oder Sie erstellen eine weitere Richtlinie und verknüpfen diese mit dem Wählplan, um festzulegen, welche Funktionen oder Einstellungen auf einen Benutzer oder eine Gruppe von Benutzern angewendet werden.

Eine UM-Postfachrichtlinie enthält Einstellungen wie die Wähleinschränkungen oder die PIN-Richtlinien für einen Benutzer. Wenn eine UM-Postfachrichtlinie erstellt wird, kann sie nur einem UM-Wählplan zugeordnet werden. Jeder Clientzugriffs- oder Postfachserver kann eingehende Anrufe beantworten und Voicemaildienste für beliebige UM-aktivierte Benutzer bereitstellen, die dem UM-Wählplan zugeordnet sind. Nachdem der Benutzer für Unified Messaging aktiviert wurde, werden die Einstellungen aus einer UM-Postfachrichtlinie auf den UM-aktivierten Benutzer angewendet.

## Durchwahlnummern und SIP-Adressen

Wenn Sie einen Benutzer für Unified Messaging aktivieren, müssen Sie mindestens eine Durchwahlnummer definieren, die von Unified Messaging verwendet wird, wenn Voicemailnachrichten an das Benutzerpostfach übermittelt werden. Nachdem Sie den Benutzer für Unified Messaging aktiviert haben, können Sie dem Benutzerpostfach sekundäre Durchwahlnummern hinzufügen, diese ändern oder entfernen, indem Sie die Exchange Unified Messaging-Proxyadresse (EUM-Proxyadresse) für das Benutzerpostfach konfigurieren oder zusätzliche oder sekundäre Durchwahlnummern für die Benutzer in der Exchange-Verwaltungskonsole hinzufügen oder entfernen. Sie können die primäre Durchwahlnummer in der Exchange-Verwaltungskonsole entfernen, indem Sie die EUM-Proxyadresse entfernen. Es wird jedoch empfohlen, diese Adresse nicht zu entfernen. Das Entfernen der primären Durchwahlnummer führt dazu, dass Anrufe nicht ordnungsgemäß an das Benutzerpostfach weitergeleitet werden können.


> [!NOTE]
> Für die Anzahl von sekundären Durchwahlnummern, die Sie für einen UM-aktivierten Benutzer hinzufügen können, gilt keine Einschränkung, pro Benutzer kann jedoch nur eine primäre Durchwahlnummer angegeben werden.



Das Postfach eines UM-aktivierten Benutzers kann nur einem einzigen Satz UM-Wähleinstellungen zugeordnet werden. Einem UM-aktivierten Benutzer können folgende Elemente zugewiesen werden:

  - Eine einzelne primäre Durchwahlnummer, eine SIP-Adresse (Session Initiation Protocol) oder eine E.164-Adresse in einem einzelnen Wählplan.

  - Mehrere sekundäre Durchwahlnummern, SIP-Adressen oder E.164-Adressen in einem einzelnen Wählplan.

  - Mehrere primäre Durchwahlnummern, SIP-Adressen oder E.164-Adressen in zwei getrennten Wählplänen.


> [!NOTE]
> Jede Durchwahlnummer, SIP-Adresse und E.164-Nummer muss innerhalb eines Wählplans identisch sein, und die Anzahl von Stellen im Wählplan werden für alle Benutzer verwendet, die dem Wählplan zugeordnet sind.



Angenommen, ein UM-aktivierter Benutzer reist häufig von New York nach Tokio. Das Postfach des Benutzers ist dem Satz Wähleinstellungen "New York" zugeordnet, und für das Postfach des Benutzers ist eine einzige Durchwahlnummer konfiguriert. Eine zweite Durchwahlnummer ist für das Postfach des Benutzers für den Satz Wähleinstellungen "Tokio" konfiguriert. Wenn ein Anrufer nun eine dieser Durchwahlnummern wählt und eine Sprachnachricht für den Benutzer hinterlässt, wird diese Sprachnachricht an das gleiche UM-aktivierte Postfach übermittelt.

Zurück zum Seitenanfang

## Aktivieren eines Benutzers für UM und Voicemail mithilfe der Exchange-Verwaltungskonsole

Nachdem Sie ein Exchange-Postfach für den Benutzer erstellt haben, können Sie die UM-Postfacheinstellungen über **Details anzeigen** unterhalb von **Unified Messaging** in der Exchange-Verwaltungskonsole konfigurieren. Wenn Sie einen Benutzer aktivieren, müssen Sie verschiedene Einstellungen konfigurieren:

1.  **SIP-Adresse**   Dies ist die SIP-Adresse für den Benutzer. Sie sehen diese Einstellung, wenn der Benutzer, den Sie für UM aktivieren, einer UM-Postfachrichtlinie zugeordnet ist, die mit einem SIP-URI-Wählplan verknüpft ist. SIP-URI-Wählpläne werden verwendet, wenn Sie Office Communications Server 2007 R2 oder Microsoft Lync Server integrieren. Wenn Sie den Benutzer einer UM-Postfachrichtlinie zuweisen, die mit einem SIP-URI oder einem E.164-Wählplan verknüpft ist, müssen Sie auch eine Durchwahlnummer für den Benutzer eingeben. Die primäre Durchwahlnummer wird vom Benutzer dazu verwendet, auf Outlook Voice Access zuzugreifen.

2.  **Durchwahlnummer**   Sie müssen die Durchwahlnummer für den Benutzer, den Sie für UM aktivieren, manuell eingeben.
    
    Sie müssen eine gültige Durchwahlnummer für den Benutzer angeben, die mit der in den Wähleinstellungen angegebenen Anzahl von Stellen übereinstimmt. Sie können nur Zahlenwerte von 1 bis 20 eingeben. Eine typische Durchwahlnummer umfasst 3 bis 7 Ziffern und wird in dem Wählplan konfiguriert, der die UM-Postfachrichtlinie zugeordnet ist, die dem Benutzer zugewiesen ist.

3.  **PIN-Einstellungen für den Benutzer:** 
    
      - **PIN automatisch generieren**   Bei Auswahl dieser Einstellung wird automatisch eine PIN für den UM-aktivierten Benutzer generiert, die für den Voicemailzugriff über Outlook Voice Access verwendet werden kann. Dies ist die Standardeinstellung. Wenn Sie auf diese Schaltfläche klicken wird automatisch eine PIN basierend auf den PIN-Richtlinien erstellt, die in der dem Empfänger zugeordneten UM-Postfachrichtlinie konfiguriert sind. Es wird empfohlen, diese Einstellung zum Schutz der Benutzer-PIN zu verwenden. Die PIN wird in der Begrüßungsnachricht an den Benutzer gesendet, die er nach der Aktivierung für UM erhält. Standardmäßig muss diese PIN bei der ersten Anmeldung beim Postfach zum Abrufen der Voicemail geändert werden.
    
      - **PIN eingeben**   Bei Auswahl dieser Einstellung können Sie manuell eine PIN eingeben, die der Benutzer für den Zugriff auf das Voicemailsystem verwenden kann.
        
        Die PIN muss den PIN-Richtlinieneinstellungen entsprechen, die in der diesem UM-aktivierten Benutzer zugeordneten UM-Postfachrichtlinie konfiguriert sind. Wenn die UM-Postfachrichtlinie beispielsweise so konfiguriert wurde, dass ausschließlich PINs mit sieben oder mehr Ziffern akzeptiert werden, muss die in diesem Feld eingegebene PIN mindestens sieben Ziffern umfassen.
    
      - **Benutzer muss PIN bei der ersten Anmeldung zurücksetzen**   Bei Auswahl dieser Einstellung wird der Benutzer gezwungen, die Voicemail-PIN zurückzusetzen, wenn sie sich von einem Telefon aus über Outlook Voice Access zum ersten Mal beim Voicemailsystem anmelden. Sie werden dazu aufgefordert, eine ihnen vertrautere PIN einzugeben. Dabei handelt es sich um eine bewährte Sicherheitsmethode, mit der UM-aktivierte Benutzer gezwungen werden, ihre PIN bei der ersten Anmeldung zu ändern. Auf diese Weise werden die Daten und Posteingänge besser vor unbefugtem Zugriff geschützt. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## Aktivieren eines Benutzers für UM und Voicemail mithilfe der Shell

In diesem Beispiel werden Unified Messaging und Voicemail für das Postfach für "tonysmith@contoso.com" aktiviert, es werden die Durchwahl und eine manuelle PIN für den Benutzer festgelegt, und dem Postfach des Benutzers wird eine UM-Postfachrichtlinie namens `MyUMMailboxPolicy` zugewiesen.

    Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -PINExpired $true

In diesem Beispiel werden Unified Messaging und Voicemail für ein Postfach für "tonysmith@contoso.com" aktiviert, der Benutzer wird einer UM-Postfachrichtlinie namens `MyUMMailboxPolicy` zugewiesen, und es werden die Durchwahl, eine SIP-Adresse und eine manuelle PIN für den Benutzer festgelegt.

    Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -SIPResourceIdentifier "tonysmith@contoso.com" -PINExpired $true

## Deaktivieren von Unified Messaging für einen Benutzer

Wenn Sie Unified Messaging für einen Benutzer deaktivieren, kann das Benutzerkonto immer noch angezeigt werden, wenn ein Anrufer eine Verzeichnissuche über ein Menü der automatischen UM-Telefonzentrale oder unter Verwendung von Outlook Voice Access durchführt. Anrufern ist es eventuell möglich, einen Benutzer im Verzeichnis zu ermitteln; beim Versuch der Kontaktaufnahme werden sie jedoch zurück zum Hauptmenü in Unified Messaging geleitet. Dies kann Verwirrung stiften und dazu führen, dass Anrufer sich über das System ärgern. Sie können verhindern, dass Anrufer über eine Verzeichnissuche Kontakt zu einem für Unified Messaging deaktivierten Benutzer aufnehmen, indem der Benutzer mit einem anderen Voicemailsystem verbunden oder aus der Verzeichnissuche der automatischen UM-Telefonzentrale entfernt wird, oder indem das Benutzerkonto entfernt wird.

Nachdem das Konto eines UM-aktivierten Benutzers für Unified Messaging deaktiviert wurde, kann dieser möglicherweise weiterhin mithilfe von Outlook Voice Access oder Microsoft Outlook auf sein persönliches UM-aktiviertes Postfach zugreifen. Dies kann passieren, wenn die Änderungen im Verzeichnis nicht konsistent sind. Um das Risiko zu verringern, dass ein Benutzer Zugriff auf das Postfach erhält, obwohl das Konto für Unified Messaging deaktiviert wurde, können Sie die Replikation manuell erzwingen oder alle Unified Messaging-Informationen aus dem Postfach des Benutzers entfernen, sobald der Benutzer für Unified Messaging deaktiviert ist.


---
title: 'Benutzerdefinierte Attribute: Exchange 2013 Help'
TOCTitle: Benutzerdefinierte Attribute
ms:assetid: 2b043878-0b34-4563-a9c2-28a9efa7447e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423541(v=EXCHG.150)
ms:contentKeyID: 50475250
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Benutzerdefinierte Attribute

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-17_

Microsoft Exchange Server 2013 umfasst 15 Erweiterungsattribute. Sie können diese Attribute verwenden, um Informationen über einen Empfänger hinzuzufügen, z. B. eine Mitarbeiter-ID, eine Organisationseinheit (Organizational Unit, OU) oder einen anderen benutzerdefinierten Wert, für den kein Attribut vorhanden ist. Diese benutzerdefinierten Attribute haben in Active Directory die Bezeichnungen von **ms-Exch-Extension-Attribute1** bis **ms-Exch-Extension-Attribute15**. In der Exchange-Verwaltungsshell sind die entsprechenden Parameter *CustomAttribute1* bis *CustomAttribute15*. Diese Attribute werden von Exchange-Komponenten nicht verwendet. Sie können zum Speichern von Active Directory-Daten verwendet werden, ohne dass dabei das Active Directory-Schema erweitert werden muss.

Wenn Sie in Exchange Server 2003 oder früheren Versionen diese Informationen in Active Directory speichern wollten, mussten Sie ein Attribut durch Erweitern des Active Directory-Schemas erstellen. Eine Schemaerweiterung erfordert Planung, die Beschaffung von Objekt-IDs (OIDs) für neue Attribute sowie das Testen des Erweiterungsprozesses in einer Testumgebung, bevor die Erweiterung in einer Produktionsumgebung implementiert werden kann. In Exchange 2013 können Schemaerweiterungen nicht in Empfängerfiltern verwendet werden, die von Adresslisten, E-Mail-Adressrichtlinien und dynamischen Verteilergruppen genutzt werden.

**Inhalt**

Vorteile von benutzerdefinierten Attributen

Beispiele für benutzerdefinierte Attribute

Beispiel für benutzerdefiniertes Attribut mit dem Parameter "ConditionalCustomAttributes"

Beispiel für benutzerdefiniertes Attribut mit dem Parameter "ExtensionCustomAttributes"

## Vorteile von benutzerdefinierten Attributen

Dies sind einige der Vorteile der Verwendung von benutzerdefinierten Attributen:

  - Sie vermeiden das Erweitern des Active Directory-Schemas.

  - Die Attribute werden von Exchange Setup erstellt.

  - Sie können die Attribute über die Exchange-Verwaltungskonsole oder über die Exchange-Verwaltungsshell verwalten. Sie müssen zum Füllen und Anzeigen der Attribute keine benutzerdefinierten Steuerelemente erstellen oder Skripts schreiben.

  - Bei den Attributen handelt es sich um filterbare Eigenschaften, die im Parameter *Filter* mit Empfänger-Cmdlets wie **Get-Mailbox** verwendet werden können. Sie können auch in der Exchange-Verwaltungskonsole und der Shell zum Erstellen von E-Mail-Adressrichtlinien, Adresslisten und dynamischen Verteilergruppen verwendet werden.

## Mehrwertige benutzerdefinierte Attribute

In Exchange 2010 Service Pack 2 (SP2) wurden fünf mehrwertige benutzerdefinierte Attribute hinzugefügt, damit Sie zusätzliche Informationen für E-Mail-Empfänger speichern können, falls die herkömmlichen benutzerdefinierten Attribute Ihren Anforderungen nicht genügen. Die Parameter *ExtensionCustomAttribute1* bis *ExtensionCustomAttribute5* können jeweils bis zu 1.300 Werte enthalten. Sie können mehrere Werte in Form einer durch Trennzeichen getrennten Liste angeben. Die folgenden Cmdlets unterstützen diese neue Parameter:

  - [Set-DistributionGroup](https://technet.microsoft.com/de-de/library/bb124955\(v=exchg.150\))

  - [Set-DynamicDistributionGroup](https://technet.microsoft.com/de-de/library/bb123796\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

  - [Set-MailContact](https://technet.microsoft.com/de-de/library/aa995950\(v=exchg.150\))

  - [Set-MailPublicFolder](https://technet.microsoft.com/de-de/library/bb123707\(v=exchg.150\))

  - [Set-RemoteMailbox](https://technet.microsoft.com/de-de/library/ff607302\(v=exchg.150\))

Weitere Informationen zu mehrwertigen Eigenschaften finden Sie unter [Ändern von mehrwertigen Eigenschaften](modifying-multivalued-properties-exchange-2013-help.md).

## Beispiele für benutzerdefinierte Attribute

In zahlreichen Exchange-Bereitstellungen ist das Erstellen einer E-Mail-Adressrichtlinie für alle Empfänger in einer Organisationseinheit ein gängiges Szenario. Die Organisationseinheit ist keine filterbare Eigenschaft, die im Parameter *RecipientFilter* einer E-Mail-Adressrichtlinie oder einer Adressliste verwendet werden kann.


> [!NOTE]
> Dynamische Verteilergruppen verfügen über einen zusätzlichen Parameter, mit dem Sie diese auf Empfänger in einer bestimmten Organisationseinheit oder einem bestimmten Container beschränken können.



Wenn die Empfänger in der jeweiligen Organisationseinheit nicht über gemeinsame Eigenschaften wie Abteilung oder Standort verfügen, nach denen Sie filtern können, können Sie eines der benutzerdefinierten Attribute mit einem gemeinsamen Wert füllen, wie in diesem Beispiel gezeigt.

    Get-Mailbox -OrganizationalUnit Sales | Set-Mailbox CustomAttribute1 "SalesOU"

Nun können Sie eine E-Mail-Adressrichtlinie für alle Empfänger erstellen, deren Eigenschaft *CustomAttribute1* den Wert "SalesOU" hat, wie in diesem Beispiel dargestellt.

    New-EmailAddressPolicy -Name "Sales" -RecipientFilter { CustomAttribute1 -eq "SalesOU"} -EnabledEmailAddressTemplates "SMTP:%s%2g@sales.contoso.com"

## Beispiel für benutzerdefiniertes Attribut mit dem Parameter "ConditionalCustomAttributes"

Sie müssen beim Erstellen von dynamischen Verteilergruppen, E-Mail-Adressrichtlinien oder Adresslisten nicht den Parameter *RecipeintFilter* verwenden, um benutzerdefinierte Attribute anzugeben. Sie können stattdessen die Parameter von *ConditionalCustomAttribute1* bis *ConditionalCustomAttribute15* verwenden.

In diesem Beispiel wird eine dynamische Verteilergruppe basierend auf den Empfängern erstellt, deren *CustomAttribute1* auf "SalesOU" festgelegt ist.

    New-DynamicDistributionGroup -Name "Sales Users and Contacts" -IncludedRecipients "MailboxUsers,MailContacts" -ConditionalCustomAttribute1 "SalesOU"


> [!NOTE]
> Sie müssen den Parameter <EM>IncludedRecipients</EM> verwenden, wenn Sie den Parameter <EM>Conditional</EM> verwenden. Außerdem können Sie nicht den Parameter <EM>Conditional</EM> verwenden, wenn Sie den Parameter <EM>RecipientFilter</EM> verwenden. Wenn Sie weitere Filter hinzufügen möchten, um dynamische Verteilergruppen, E-Mail-Adressrichtlinien oder Adresslisten zu erstellen, sollten Sie den Parameter <EM>RecipientFilter</EM> verwenden.



## Beispiel für benutzerdefiniertes Attribut mit dem Parameter "ExtensionCustomAttributes"

In diesem Beispiel wird das *ExtensionCustomAttribute1* für das Postfach für Kweku aktualisiert, um anzuzeigen, dass er in folgenden Kursen eingeschrieben ist: MATH307, ECON202 und ENGL300.

    Set-Mailbox -Identity Kweku -ExtensionCustomAttribute1 MATH307,ECON202,ENGL300

Anschließend wird eine dynamische Verteilergruppe für alle Studierenden des Kurses MATH307 erstellt. Hierbei wird der Parameter *RecipientFilter* verwendet, dessen *ExtensionCustomAttribute1* "MATH307" lautet. In den Parametern für *ExtentionCustomAttributes* können Sie den Operator `-eq` anstelle des Operators `-like` verwenden.

    New-DynamicDistributionGroup -Name Students_MATH307 -RecipientFilter {ExtensionCustomAttribute1 -eq "MATH307"}

In diesem Beispiel werden die *ExtensionCustomAttribute1*-Werte für Kewku aktualisiert, um anzuzeigen, dass er den Kurs ENGL210 hinzugefügt und den Kurs "ECON202" abgewählt hat.

    Set-Mailbox -Identity Kweku -ExtensionCustomAttribute1 @{Add="ENGL210"; Remove="ECON202"}


---
title: 'Terminologie für die Messaging-Datensatzverwaltung in Exchange 2013: Exchange 2013 Help'
TOCTitle: Terminologie für die Messaging-Datensatzverwaltung in Exchange 2013
ms:assetid: de3e3503-6de3-4666-aeb9-cd877efb93bb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb408414(v=EXCHG.150)
ms:contentKeyID: 50476898
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Terminologie für die Messaging-Datensatzverwaltung in Exchange 2013

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-30_

In der folgenden Tabelle sind die wichtigsten Komponenten im Zusammenhang mit der Messaging-Datensatzverwaltung (MRM) in Microsoft Exchange Server 2013 definiert. MRM ist eine Technologie für die Verwaltung von Datensätzen in Exchange 2013, die Organisationen dabei unterstützt, die mit E-Mail und anderen Kommunikationsformen einhergehenden Risiken zu verringern. MRM vereinfacht die zum Erfüllen der Anforderungen von Unternehmensrichtlinien, amtlichen Vorschriften oder rechtlichen Vorgaben notwendige Aufbewahrung von Nachrichten, sowie das Entfernen von Inhalten, die keinen juristischen oder geschäftlichen Nutzen mehr haben.

  - **Standardrichtlinientag**  
    Bei einem Standardrichtlinientag handelt es sich um ein Aufbewahrungstag, das auf alle Elemente in einem Postfach angewendet wird, für die noch kein anderes Aufbewahrungstag festgelegt ist. Eine Aufbewahrungsrichtlinie kann nur ein einziges Standardrichtlinientag enthalten.

<!-- end list -->

  - **"Filer"**  
    Ein Benutzer, der Postfachelemente regelmäßig in Ordnern archiviert.
    
    Vergleiche "Piler".

<!-- end list -->

  - **Journal**  
    Die Fähigkeit, Kommunikationsvorgänge, einschließlich der E-Mail-Kommunikation, in einer Organisation für die Verwendung in den Aufbewahrungsstrategien oder der Archivierungsstrategie einer Organisation aufzuzeichnen. In MRM bezieht sich die Journalfunktion üblicherweise auf das Senden eines Journalberichts zu Nachrichten in einem verwalteten Ordner an die angegebene SMTP-Adresse. Dieser Vorgang wird vom Assistenten für verwaltete Ordner ausgeführt.

<!-- end list -->

  - **Einstellungen für verwaltete Inhalte**  
    Die für verwaltete Ordner für das MRM-Feature in Exchange Server 2007 und Exchange Server 2010 erstellte Aufbewahrungsinformationen. Ein verwalteter Ordner kann mehrere Inhaltseinstellungen für unterschiedliche Nachrichtentypen aufweisen, z. B. für E-Mail-Nachrichten, Voicemail und Kalenderelemente. Die in den Inhaltseinstellungen für einen verwalteten Ordner definierten Einstellungen für die Nachrichtenaufbewahrung werden auf Nachrichten in diesem verwalteten Ordner angewendet.

<!-- end list -->

  - **Verwalteter Ordner**  
    Ein für das MRM-Feature in Exchange Server 2007 und Exchange Server 2010 verwendeter Ordner ist ein Active Directory-Objekt, das einen Postfachordner darstellt, auf den Einstellungen für verwaltete Inhalte angewendet werden. In einem Postfach ist ein verwalteter Ordner ein Ordner, auf den Einstellungen für verwaltete Inhalte angewendet wurden.

<!-- end list -->

  - **Assistent für verwaltete Ordner**  
    Einer der Microsoft Exchange-Postfach-Assistenten in Exchange 2013. Der Assistent für verwaltete Ordner ist für die Archivierung, den Nachrichtenablauf und die Richtlinientreue verantwortlich. Er verarbeitet Postfächer und wendet Aufbewahrungsrichtlinien an.

<!-- end list -->

  - **Postfachrichtlinie für verwaltete Ordner**  
    Eine logische Gruppe verwalteter Ordner. Wenn in Exchange 2010 und Exchange 2007 eine Sicherheitsrichtlinie für verwaltete Ordner auf das Postfach eines Benutzers angewendet wird, werden alle verwalteten Ordner, die mit der Richtlinie verknüpft sind, in einem einzigen Vorgang bereitgestellt.

<!-- end list -->

  - **Persönliches Tag**  
    Bei einem persönlichen Tag handelt es sich um ein Aufbewahrungstag, das für die Benutzer von Outlook Web App und Outlook 2010 und höher verfügbar ist, damit diese Aufbewahrungseinstellungen auf benutzerdefinierte Ordner und einzelne Elemente, z. B. E-Mails, anwenden können.

<!-- end list -->

  - **"Piler"**  
    Ein Benutzer, der Postfachelemente nicht regelmäßig archiviert. Diese Benutzer verfügen üblicherweise über große Postfächer und nutzen zum Auffinden von Nachrichten die Suchfunktion.
    
    Vergleiche "Filer".

<!-- end list -->

  - **Richtlinie**  
    Siehe *Aufbewahrungsrichtlinie* oder *Sicherheitsrichtlinie für verwaltete Ordner*.

<!-- end list -->

  - **Aufbewahrungsrichtlinientag**  
    Bei einem Aufbewahrungsrichtlinientag handelt es sich um ein Aufbewahrungstag, das auf Standardordner wie "Posteingang" und "Gelöschte Elemente" angewendet wird.

<!-- end list -->

  - **Aufbewahrungsrichtlinie**  
    Bei einer Aufbewahrungsrichtlinie handelt es sich um eine logische Gruppierung von Aufbewahrungstags. Wenn eine Aufbewahrungsrichtlinie auf das Postfach eines Benutzers angewendet wird, werden alle Aufbewahrungstags, die mit der Richtlinie verknüpft sind, in einem einzigen Vorgang bereitgestellt.

<!-- end list -->

  - **Aufbewahrungstag**  
    Mithilfe von Aufbewahrungstags werden Aufbewahrungseinstellungen auf Nachrichten und Ordner in Benutzerpostfächern angewendet. Es gibt drei Typen von Aufbewahrungstags:
    
      - Standardrichtlinientags
    
      - Aufbewahrungsrichtlinientags
    
      - Persönliche Tags


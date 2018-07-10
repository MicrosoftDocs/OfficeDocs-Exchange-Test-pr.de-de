---
title: 'Grundlegendes zur rollenbasierten Zugriffssteuerung: Exchange 2013 Help'
TOCTitle: Grundlegendes zur rollenbasierten Zugriffssteuerung
ms:assetid: fd268867-2ae5-441b-8103-7a7583eb2bbe
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298183(v=EXCHG.150)
ms:contentKeyID: 50477163
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Grundlegendes zur rollenbasierten Zugriffssteuerung

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-01-31_

Bei der rollenbasierten Zugriffssteuerung (*Role Based Access Control*, RBAC) handelt es sich um das in Microsoft Exchange Server 2013 verwendete Berechtigungsmodell. Mit RBAC ist eine Änderung und Verwaltung der Zugriffssteuerungslisten (Access Control Lists, ACLs) wie in Exchange Server 2007 nicht länger erforderlich. ACLs boten in Exchange 2007 einige Herausforderungen, z. B. das Ändern der ACLs ohne unvorhersehbare Folgen, die Verwaltung von ACL-Änderungen bei Upgrades und die Behandlung von Problemen, die durch eine nicht standardmäßige Verwendung von ACLs verursacht wurden.

Mithilfe von RBAC können Sie sowohl auf allgemeiner als auch auf detaillierter Ebene steuern, welche Aktionen von Administratoren und Endbenutzern ausgeführt werden können. RBAC ermöglicht Ihnen außerdem eine genauere Anpassung der den Benutzern und Administratoren zugewiesenen Rollen an ihre tatsächlichen Positionen, die sie innerhalb der Organisation einnehmen. In Exchange 2007 galt das Serverberechtigungsmodell nur für die Administratoren, die für die Verwaltung der Exchange 2007-Infrastruktur zuständig waren. In Exchange 2013 steuert RBAC jetzt sowohl, welche Verwaltungstasks durchgeführt werden können, als auch den Umfang, in dem Benutzer jetzt ihre eigenen Postfach- und Verteilergruppen verwalten können.

Bei der rollenbasierten Zugriffssteuerung gibt es zwei Hauptmethoden zum Zuordnen von Berechtigungen zu Benutzern in einer Organisation, die davon abhängen, ob es sich bei dem Benutzer um einen Administrator oder spezialisierten Benutzer oder um einen Endbenutzer handelt: Verwaltungsrollengruppen und Richtlinien für die Zuweisung von Verwaltungsrollen. Jede Methode ordnet Benutzern Berechtigungen zu, die sie für ihre Tätigkeit benötigen. Auch eine dritte, fortgeschrittenere Methode kann verwendet werden: die direkte Benutzerrollenzuweisung. In den folgenden Abschnitten dieses Themas wird die rollenbasierte Zugriffssteuerung erläutert, und Sie erhalten Beispiele für deren Verwendung.


> [!NOTE]
> Inhalt dieses Themas ist die erweiterte RBAC-Funktionalität. Informationen zum Verwalten grundlegender Exchange 2013-Berechtigungen finden Sie unter <A href="permissions-exchange-2013-help.md">Berechtigungen</A>. In diesem Thema wird z.&nbsp;B. beschrieben, wie Sie das Exchange Admin Center (EAC) verwenden, um Mitglieder zu Rollengruppen hinzuzufügen oder aus diesen zu entfernen oder um Rollengruppen und Rollenzuweisungsrichtlinien zu erstellen oder zu ändern.



**Inhalt**

Management role groups

Management role assignment policies

Direct user role assignment

Summary and examples

For more information

## Verwaltungsrollengruppen

*Verwaltungsrollengruppen* ordnen Verwaltungsrollen einer Gruppe von Administratoren oder spezialisierten Benutzern zu. Administratoren verwalten eine umfassende Exchange-Organisations- oder Empfängerkonfiguration. Spezialisierte Benutzer verwalten die spezifischen Funktionen von Exchange, beispielsweise die Richtlinientreue. Möglicherweise erfüllen sie auch eingeschränkte Verwaltungsaufgaben, wie z. B. Helpdeskmitarbeiter, erhalten jedoch keine umfassenden Administratorrechte. Rollengruppen weisen in der Regel administrative Verwaltungsrollen zu, die Administratoren und spezialisierten Benutzern das Verwalten der Konfiguration ihrer Organisation und der entsprechenden Empfänger ermöglichen. Ob Administratoren Empfänger verwalten oder Postfachdiscoveryfunktionen verwenden können, wird beispielsweise durch Rollengruppen gesteuert.

Berechtigungen werden den Administratoren oder spezialisierten Benutzern normalerweise durch Hinzufügen oder Entfernen der Benutzer zu bzw. aus den Rollengruppen erteilt. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md).

Rollengruppen bestehen aus den folgenden Komponenten, durch welche die von den Administratoren und spezialisierten Benutzern durchgeführten Aufgaben definiert werden:

  - **Verwaltungsrollengruppe**   Die *Verwaltungsrollengruppe* ist eine spezielle universelle Sicherheitsgruppe (Universal Security Group, USG) mit Postfächern, Benutzern, USGs und anderen Rollengruppen, die Mitglieder der Rollengruppe sind. Hier werden Mitglieder hinzugefügt und entfernt und auch Verwaltungsrollen zugewiesen. Die Kombination all dieser Rollen in einer Rollengruppe definiert all das, was die einer Rollengruppe hinzugefügten Benutzer in der Exchange-Organisation verwalten können.

  - **Verwaltungsrolle**   Eine *Verwaltungsrolle* ist ein Container für eine Gruppierung von Verwaltungsrolleneinträgen. Anhand von Rollen werden die spezifischen Tasks definiert, die von den Mitgliedern einer Rollengruppe, der die Rolle zugewiesen wird, ausgeführt werden können. Ein *Verwaltungsrolleneintrag* ist ein Cmdlet, Skript oder eine spezielle Berechtigung zur Ausführung der einzelnen spezifischen Tasks in einer Rolle. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

  - **Verwaltungsrollenzuweisung**   Eine *Verwaltungsrollenzuweisung* verknüpft eine Rolle mit einer Rollengruppe. Durch das Zuweisen einer Rolle zu einer Rollengruppe wird Mitgliedern der Rollengruppe die Möglichkeit gegeben, die in der Rolle definierten Cmdlets und Parameter zu verwenden. ‏Rollenzuweisungen können Verwaltungsbereiche verwenden, um zu steuern, an welchen Stellen die Zuweisung eingesetzt werden kann. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

  - **Verwaltungsrollenbereich**   Ein *Verwaltungsrollenbereich* ist der Einfluss- oder Wirkungsbereich einer Rollenzuweisung. Wird eine Rolle mit einem Bereich einer Rollengruppe zugewiesen, grenzt der Verwaltungsbereich genau ein, welche Objekte diese Zuweisung verwalten darf. Die Zuweisung und ihr Bereich werden dann auf die Mitglieder der Rollengruppe übertragen und schränken die Verwaltungsmöglichkeiten dieser Mitglieder ein. Ein Bereich kann aus einer Liste von Servern oder Datenbanken, Organisationseinheiten oder Filtern für Server-, Datenbank- oder Empfängerobjekte bestehen. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Wenn Sie einen Benutzer einer Rollengruppe hinzufügen, erhält der Benutzer sämtliche Rollen, die der Rollengruppe zugewiesen sind. Gelten Bereiche für einige Rollenzuweisungen zwischen der Rollengruppe und den Rollen, wird durch diese Bereiche gesteuert, welche Serverkonfiguration oder Empfänger der Benutzer verwalten kann.

Wenn Sie die den Rollengruppen zugewiesenen Rollen ändern möchten, müssen Sie die Rollenzuweisungen ändern, durch welche die Rollengruppen mit den Rollen verknüpft sind. Wenn die in Exchange 2013 vorgegebenen Zuweisungen Ihren Anforderungen entsprechen, müssen diese nicht geändert werden. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Weitere Informationen zu Rollengruppen finden Sie unter [Grundlegendes zu Verwaltungsrollengruppen](understanding-management-role-groups-exchange-2013-help.md).

## Richtlinien für die Verwaltungsrollenzuweisung

Durch die Richtlinien für die Verwaltungsrollenzuweisung werden Endbenutzer-Verwaltungsrollen den Benutzern zugeordnet. Rollenzuweisungsrichtlinien bestehen aus Rollen, die steuern, welche Aufgaben ein Benutzer an seinem Postfach oder seinen Verteilergruppen durchführen kann. Diese Rollen lassen nicht die Verwaltung von Funktionen zu, die dem Benutzer nicht direkt zugeordnet sind. Beim Erstellen einer Rollenzuweisungsrichtlinie definieren Sie alle Aufgaben, die ein Benutzer an seinem Postfach durchführen kann. Beispielsweise kann eine Rollenzuweisungsrichtlinie einem Benutzer das Festlegen des Anzeigenamens, das Einrichten von Voicemail und das Konfigurieren von Posteingangsregeln ermöglichen. Eine weitere Rollenzuweisungsrichtlinie kann einem Benutzer das Ändern der Adresse, die Verwendung von Textnachrichten und das Einrichten von Verteilergruppen gestatten. Alle Benutzer mit einem Exchange 2013-Postfach, einschließlich Administratoren, erhalten standardmäßig eine Rollenzuweisungsrichtlinie. Sie können entscheiden, welche Rollenzuweisungsrichtlinie standardmäßig zugewiesen werden soll, auswählen, was die Standard-Rollenzuweisungsrichtlinie enthalten soll, den Standard für bestimmte Postfächer außer Kraft setzen oder auch überhaupt keine Rollenzuweisungsrichtlinien standardmäßig zuweisen.

In den meisten Fällen werden Sie Benutzerberechtigungen zur Verwaltung ihrer eigenen Postfach- und Verteilergruppenoptionen durch die Zuweisung eines Benutzers zu einer Zuweisungsrichtlinie verwalten. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien](understanding-management-role-assignment-policies-exchange-2013-help.md).

Rollenzuweisungsrichtlinien bestehen aus den folgenden Komponenten, welche die Aufgaben definieren, die Benutzer an ihren eigenen Postfächern vornehmen können. Beachten Sie, dass einige derselben Komponenten auch für Rollengruppen gelten. Wenn sie mit Rollenzuweisungsrichtlinien verwendet werden, sind diese Komponenten darauf beschränkt, Benutzern nur die Verwaltung ihres eigenen Postfachs zu ermöglichen:

  - **Richtlinie für die Verwaltungsrollenzuweisung**   Die *Richtlinie für die Verwaltungsrollenzuweisung* ist ein spezielles Objekt in Exchange 2013. Benutzern wird eine Rollenzuweisungsrichtlinie zugeordnet, wenn ihr Postfach erstellt wird oder Sie die Rollenzuweisungsrichtlinie für ein Postfach ändern. Der Rollenzuweisungsrichtlinie weisen Sie auch Endbenutzerverwaltungsrollen zu. Die Kombination aller Rollen in einer Rollenzuweisungsrichtlinie definiert all das, was der Benutzer in seinem Postfach oder in Verteilergruppen verwalten kann.

  - **Verwaltungsrolle**   Eine *Verwaltungsrolle* ist ein Container für eine Gruppierung von Verwaltungsrolleneinträgen. Rollen werden zum Definieren der spezifischen Tasks verwendet, die Benutzer an ihrem Postfach oder ihren Verteilergruppen ausführen können. Ein *Verwaltungsrolleneintrag* ist ein Cmdlet, Skript oder eine spezielle Berechtigung zur Ausführung der einzelnen spezifischen Tasks in einer Verwaltungsrolle. Sie können nur Endbenutzerverwaltungsrollen mit Rollenzuweisungsrichtlinien verwenden. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

  - **Verwaltungsrollenzuweisung**   Eine *Verwaltungsrollenzuweisung* ist die Verknüpfung zwischen einer Rolle und einer Rollenzuweisungsrichtlinie. Durch das Zuweisen einer Rolle zu einer Rollenzuweisungsrichtlinie wird die Möglichkeit gegeben, die in der Rolle definierten Cmdlets und Parameter zu verwenden. Beim Erstellen einer Rollenzuweisung zwischen einer Rollenzuweisungsrichtlinie und einer Rolle können Sie keinen Bereich angeben. Der durch die Zuweisung angewendete Bereich lautet entweder `Self` oder `MyGAL`. Alle Rollenzuweisungen sind auf das Postfach oder die Verteilergruppen des Benutzers beschränkt. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Wenn Sie die den Rollenzuweisungsrichtlinien zugewiesenen Rollen ändern möchten, müssen Sie die Rollenzuweisungen ändern, durch welche die Rollenzuweisungsrichtlinien mit den Rollen verknüpft sind. Wenn die in Exchange 2013 vorgegebenen Zuweisungen Ihren Anforderungen entsprechen, müssen diese nicht geändert werden. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien](understanding-management-role-assignment-policies-exchange-2013-help.md).

## Direkte Benutzerrollenzuweisung

Die *direkte Benutzerrollenzuweisung* ist eine fortgeschrittene Methode, um Verwaltungsrollen direkt einem Benutzer oder einer USG zuzuweisen, ohne eine Rollengruppe oder eine Rollenzuweisungsrichtlinie zu verwenden. Direkte Rollenzuweisungen können hilfreich sein, wenn Sie einen detaillierten Satz Berechtigungen nur einem bestimmten Benutzer bereitstellen möchten. Die Verwendung direkter Rollenzuweisungen kann die Komplexität Ihres Berechtigungsmodells jedoch erheblich erhöhen. Wenn ein Benutzer die Position wechselt oder das Unternehmen verlässt, müssen Sie die Zuweisungen manuell entfernen und dem neuen Mitarbeiter hinzufügen. Es empfiehlt sich, Rollengruppen zum Zuweisen von Berechtigungen für Administratoren und spezialisierte Benutzer sowie Rollenzuweisungsrichtlinien zum Zuweisen von Berechtigungen für Benutzer zu verwenden.

Weitere Informationen zur direkten Benutzerrollenzuweisung finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

## Zusammenfassung und Beispiele

In der folgenden Abbildung werden die Komponenten in RBAC und deren Zusammenhänge veranschaulicht:

  - Rollengruppen:
    
      - Ein oder mehrere Administratoren können Mitglieder einer Rollengruppe sein. Sie können auch mehreren Rollengruppen angehören.
    
      - Der Rollengruppe wird eine oder mehrere Rollenzuweisungen zugewiesen. Durch diese wird die Rollengruppe mit einer oder mehreren Administratorrollen verknüpft, welche die durchführbaren Tasks definieren.
    
      - Die Rollenzuweisungen können Verwaltungsbereiche enthalten, durch welche definiert wird, an welchen Stellen die Benutzer der Rollengruppe Aktionen durchführen können. Die Bereiche legen fest, an welchen Stellen die Benutzer der Rollengruppe die Konfiguration ändern können.

  - Rollenzuweisungsrichtlinien:
    
      - Ein oder mehrere Benutzer können einer Rollenzuweisungsrichtlinie zugeordnet werden.
    
      - Der Rollenzuweisungsrichtlinie wird eine oder mehrere Rollenzuweisungen zugewiesen. Diese verknüpfen die Rollenzuweisungsrichtlinie mit einer oder mehreren Endbenutzerrollen. Die Endbenutzerrollen definieren, welche Komponenten der Benutzer in seinem Postfach konfigurieren kann.
    
      - Die Rollenzuweisungen zwischen den Rollenzuweisungsrichtlinien und den Rollen weisen vorgegebene Bereiche auf, welche die Zuweisungen auf das eigene Postfach oder die eigenen Verteilergruppen des Benutzers einschränken.

  - Direkte Rollenzuweisung (fortgeschritten):
    
      - Eine Rollenzuweisung kann direkt zwischen einem Benutzer oder einer USG und einem oder mehreren Rollen erstellt werden. Die Rolle definiert die Tasks, die der Benutzer oder die USG ausführen kann.
    
      - Die Rollenzuweisungen können Verwaltungsbereiche enthalten, durch welche definiert wird, an welchen Stellen der Benutzer oder die USG Aktionen durchführen kann. Die Bereiche legen fest, an welchen Stellen der Benutzer oder die USG die Konfiguration ändern kann.

**Übersicht über RBAC**

![RBAC-Komponentenbeziehungen](images/Dd298183.1dee60cc-1d58-4d36-b34e-639f091e7a56(EXCHG.150).jpg "RBAC-Komponentenbeziehungen")

Wie in der obigen Abbildung gezeigt, stehen viele Komponenten der rollenbasierten Zugriffssteuerung miteinander in Zusammenhang. Durch die Zusammensetzung der einzelnen Komponenten werden die Berechtigungen definiert, die auf die einzelnen Administratoren oder Benutzer angewendet werden. Die folgenden Beispiele bieten zusätzlichen Kontext zur Verwendung von Rollengruppen und Rollenzuweisungsrichtlinien in einer Organisation.

## Die Administratorin Jane

Jane ist Administratorin beim mittelständischen Unternehmen Contoso. Sie ist verantwortlich für die Verwaltung der Empfänger des Unternehmens in deren Niederlassung in Vancouver. Bei der Erstellung des Berechtigungsmodells für Contoso wurde Jane Mitglied in der benutzerdefinierten Rollengruppe "Empfängerverwaltung - Vancouver". Die benutzerdefinierte Rollengruppe "Empfängerverwaltung - Vancouver" kam den Aufgaben ihrer Position am nächsten. Hierzu gehören das Erstellen und Entfernen von Empfängern (also Postfächern und Kontakten), das Verwalten von Mitgliedschaften in Verteilergruppen, das Verwalten von Postfacheigenschaften und ähnliche Tasks.

Zusätzlich zur benutzerdefinierten Rollengruppe "Empfängerverwaltung - Vancouver" benötigt Jane außerdem eine Rollenzuweisungsrichtlinie für die Verwaltung der Konfigurationseinstellungen ihres eigenen Postfachs. Die Administratoren der Organisation haben beschlossen, dass alle Benutzer mit Ausnahme des Führungsstabs dieselben Berechtigungen zur Verwaltung ihrer eigenen Postfächer erhalten. Sie können ihre Voicemail konfigurieren, Aufbewahrungsrichtlinien einrichten und ihre Adressinformationen ändern. Die in Exchange 2013 bereitgestellte Standard-Rollenzuweisungsrichtlinie entspricht jetzt diesen Anforderungen.


> [!NOTE]
> Möglicherweise ist Ihnen aufgefallen, dass Jane aufgrund ihrer Mitgliedschaft in der benutzerdefinierten Rollengruppe "Empfängerverwaltung - Vancouver" die Berechtigungen zum Verwalten ihres eigenen Postfachs bereits besitzen sollte. Das ist richtig; allerdings stellt die Rollengruppe ihr nicht alle Berechtigungen bereit, die für die Verwaltung aller Funktionen ihres Postfachs erforderlich sind. Die zum Verwalten der Einstellungen für Voicemail und Aufbewahrungsrichtlinien nötigen Berechtigungen sind in ihrer Rollengruppe nicht enthalten. Sie werden nur durch die ihr zugewiesene Standard-Rollenzuweisungsrichtlinie bereitgestellt.



Sehen Sie sich dazu die Rollengruppe an, die Janes Administratorberechtigungen für die Empfänger in Vancouver bereitstellt:

1.  Eine benutzerdefinierte Rollengruppe namens "Empfängerverwaltung - Vancouver" wurde erstellt. Bei der Erstellung geschah Folgendes:
    
    1.  Der Rollengruppe wurden dieselben Verwaltungsrollen zugewiesen, die auch der vorgegebenen Empfängerverwaltung-Rollengruppe zugewiesen sind. Benutzer, die der benutzerdefinierten Rollengruppe "Empfängerverwaltung - Vancouver" hinzugefügt werden, erhalten damit dieselben Berechtigungen wie die Benutzer, die der Empfängerverwaltung-Rollengruppe hinzugefügt werden. Allerdings wird durch folgende Schritte der Bereich eingeschränkt, in dem sie diese Berechtigungen nutzen können.
    
    2.  Der benutzerdefinierte Verwaltungsbereich "Vancouver Recipients" wurde erstellt, der nur den in Vancouver befindlichen Empfängern entspricht. Dies erfolgte durch Erstellen eines Bereichs, der anhand der Stadt oder einer anderen eindeutigen Benutzerinformation filtert.
    
    3.  Die Rollengruppe wurde mit dem benutzerdefinierten Verwaltungsbereich "Vancouver Recipients" erstellt. Damit besitzen die der benutzerdefinierten Rollengruppe "Empfängerverwaltung - Vancouver" hinzugefügten Administratoren zwar vollständige Berechtigungen zur Empfängerverwaltung, können diese Berechtigungen jedoch nur für Empfänger in Vancouver verwenden.
    
    Weitere Informationen zum Erstellen einer benutzerdefinierten Rollengruppe finden Sie unter [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md).

2.  Jane wird anschließend der benutzerdefinierten Rollengruppe "Empfängerverwaltung - Vancouver" als Mitglied hinzugefügt.
    
    Weitere Informationen zum Hinzufügen von Mitgliedern zu einer Rollengruppe finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

Um Jane die Möglichkeit zu geben, ihre eigenen Postfacheinstellungen zu verwalten, muss eine Rollenzuweisungsrichtlinie mit den erforderlichen Berechtigungen konfiguriert werden. Die Standard-Rollenzuweisungsrichtlinie wird verwendet, um Benutzern die Berechtigungen bereitzustellen, die sie zum Konfigurieren ihres eigenen Postfachs benötigen. Alle Endbenutzerrollen werden aus der Standard-Rollenzuweisungsrichtlinie entfernt, mit folgenden Ausnahmen: `MyBaseOptions`, `MyContactInformation`, `MyVoicemail` und `MyRetentionPolicies`. `MyBaseOptions` ist enthalten, da diese Verwaltungsrolle die grundlegende Benutzerfunktionalität in Outlook Web App bereitstellt, also Posteingangsregeln, Kalenderkonfiguration und andere Tasks.

Ansonsten sind keine weiteren Maßnahmen erforderlich, weil die Standard-Rollenzuweisungsrichtlinie Jane bereits zugewiesen wurde. Die Änderungen an dieser Rollenzuweisungsrichtlinie werden daher sofort auf ihr Postfach und auf alle weiteren Postfächer angewendet, die der Standard-Rollenzuweisungsrichtlinie zugewiesen sind.

Weitere Informationen über das Anpassen der Standard-Rollenzuweisungsrichtlinie finden Sie unter [Verwalten von Rollenzuweisungsrichtlinien](manage-role-assignment-policies-exchange-2013-help.md).

## Der spezialisierte Benutzer Joe

Joe arbeitet bei Contoso, dasselbe Unternehmen, das auch Jane beschäftigt. Er ist für die Durchführung der Offenlegungspflicht, das Festlegen von Aufbewahrungsrichtlinien sowie das Konfigurieren von Transportregeln und der Journalfunktion für die gesamte Organisation verantwortlich. Wie Jane wurde Joe bei der Erstellung des Berechtigungsmodells für Contoso den Rollengruppen hinzugefügt, die den Aufgaben seiner Position entsprechen. Die Datensatzverwaltung-Rollengruppe verleiht Joe die Berechtigungen zum Konfigurieren von Aufbewahrungsrichtlinien, der Journalfunktion und von Transportregeln. Die Discoveryverwaltung-Rollengruppe ermöglicht ihm die Durchführung von Postfachsuchvorgängen.

Wie Jane benötigt auch Joe Berechtigungen zum Verwalten seines eigenen Postfachs. Er erhält die gleichen Berechtigungen wie Jane: Er kann seine Voicemail und Aufbewahrungsrichtlinien einrichten sowie seine Adressinformationen ändern.

Um Joe die für seine Aufgaben erforderlichen Berechtigungen zu erteilen, wird Joe den Rollengruppen Datensatzverwaltung und Discoveryverwaltung hinzugefügt. Die Rollengruppen müssen nicht verändert werden, da sie ihm bereits die benötigten Berechtigungen verleihen, und die darauf angewendeten Verwaltungsbereiche erstrecken sich auf die gesamte Organisation.

Weitere Informationen zum Hinzufügen eines Benutzers zu einer Rollengruppe finden Sie unter [Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md).

Joes Postfach wird ebenfalls dieselbe Standard-Rollenzuweisungsrichtlinie wie Janes Postfach zugewiesen. Auf diese Weise erhält er alle Berechtigungen, die er in dem ihm gestatteten Umfang zum Verwalten der Postfachfunktionen benötigt.

## Die Vizepräsidentin Isabel

Isabel ist Marketingdirektorin bei Contoso. Isabel erhält mehr Berechtigungen als ein normaler Benutzer, da sie zum Führungsstab von Contoso gehört. Dies schließt auch die Berechtigungen ein, die ihr zum Verwalten ihres Postfachs bereitgestellt werden, mit einer Ausnahme: Isabel darf aufgrund der Einhaltung gesetzlicher Bestimmungen ihre eigenen Aufbewahrungsrichtlinien nicht verwalten. Isabel kann ihre Voicemail konfigurieren, ihre Kontaktinformationen ändern, ihre Profilinformationen ändern, eigene Verteilergruppen erstellen und verwalten und sich selbst vorhandenen Verteilergruppen anderer Personen hinzufügen bzw. aus diesen Gruppen entfernen.

Isabel werden daher andere Berechtigungen für ihr eigenes Postfach erteilt. Den meisten Benutzern bei Contoso wird die Standard-Rollenzuweisungsrichtlinie zugewiesen. Der Führungsstab wird jedoch der Rollenzuweisungsrichtlinie "Senior Leadership" zugewiesen. Um die benutzerdefinierte Rollenzuweisungsrichtlinie zu erstellen, werden folgende Schritte durchgeführt:

1.  Eine benutzerdefinierte Rollenzuweisungsrichtlinie namens "Senior Leadership" wird erstellt. Der Rollenzuweisungsrichtlinie werden die Rollen `MyBaseOptions`, `MyContactInformation`, `MyVoicemail`, `MyProfileInformation`, `MyDistributionGroupMembership` und ` MyDistributionGroups` zugewiesen. `MyBaseOptions` ist enthalten, da diese Rolle die grundlegende Benutzerfunktionalität in Microsoft Outlook Web App bereitstellt, also Posteingangsregeln, Kalenderkonfiguration und andere Tasks.

2.  Die Rollenzuweisungsrichtlinie "Senior Leadership" wird Isabel anschließend manuell zugewiesen.

Isabels Postfach besitzt jetzt die Berechtigungen, die durch die Rollenzuweisungsrichtlinie "Senior Leadership" bereitgestellt werden. Änderungen an dieser Rollenzuweisungsrichtlinie werden automatisch auf ihr Postfach und auf alle weiteren Postfächer angewendet, die derselben Rollenzuweisungsrichtlinie zugewiesen sind.

## Weitere Informationen

[Verwalten von Rollenzuweisungsrichtlinien](manage-role-assignment-policies-exchange-2013-help.md)

[Ändern der Zuweisungsrichtlinie für ein Postfach](change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md)


---
title: Überblick über Dokumentfingerabdrücke in Exchange
TOCTitle: Dokumentfingerabdrücke
ms:assetid: 1e0c579c-26e0-462a-a1b0-d7506dfe05fa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn635176(v=EXCHG.150)
ms:contentKeyID: 61201332
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Dokumentfingerabdrücke

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-09-11_

Information-Worker in Ihrer Organisation verarbeiten im Lauf eines Arbeitstags viele Arten von vertraulichen Informationen. *Dokumentfingerabdrücke* erleichtern Ihnen den Schutz dieser Informationen durch Identifikation von Standardformularen, die in Ihrer gesamten Organisation verwendet werden. Dieses Thema beschreibt die Konzepte für Dokumentfingerabdrücke. Informationen zum Erstellen eines Dokumentfingerabdrucks finden Sie unter [Schutz von Formulardaten durch Dokumentfingerabdrücke](https://technet.microsoft.com/de-de/library/Dn635175(v=EXCHG.150)).

## Grundlegendes Szenario für Dokumentfingerabdrücke

Der Dokumentfingerabdruck ist eine Funktion zur Verhinderung von Datenverlust, mit deren Hilfe ein Standardformular in ein Formular für vertrauliche Informationen umgewandelt wird, das Sie zur Definition von Transportregeln und DLP (Data Loss Prevention)-Richtlinien verwenden können. Sie können z. B. einen Dokumentfingerabdruck auf Grundlage einer leeren Patentvorlage erstellen und eine DLP-Richtlinie festlegen, die alle ausgehenden Patentvorlagen mit vertraulichem Inhalt erkennt und blockiert. Optional können Sie [Richtlinientipps](https://technet.microsoft.com/de-de/library/JJ150512(v=EXCHG.150)) einrichten, um einen Absender darüber zu benachrichtigen, dass er eventuell vertrauliche Informationen sendet. Der Absender sollte dann prüfen, ob die Empfänger dazu berechtigt sind, diese Patente zu erhalten. Dieser Prozess funktioniert mit allen textbasierten Formularen in Ihrer Organisation. Weitere Beispiele für Formulare, die Sie hochladen können

  - Regierungsformulare

  - HIPAA (Health Insurance Portability and Accountability Act)-kompatible Formulare

  - Formulare mit Mitarbeiterinformationen für die Personalabteilung

  - Speziell für Ihre Organisation erstellte benutzerdefinierte Formulare

Ideal wäre es, wenn es in Ihrer Organisation bereits eine etablierte Routine beim Umgang mit der Versendung vertraulicher Informationen gäbe. Wenn Sie ein leeres Formular hochgeladen haben, das in einen Dokumentfingerabdruck umgewandelt werden soll, und eine entsprechende Richtlinie einrichten, erkennt der DLP Agent alle Dokumente in ausgehenden Mails, die zu diesem Fingerabdruck passen.

## Funktionsweise von Dokumentfingerabdrücken

Wahrscheinlich haben Sie schon erraten, dass sich auf den Dokumenten keine echten Fingerabdrücke befinden – aber der Name erklärt sehr gut die Funktion. Genauso, wie der Fingerabdruck eines Menschen einzigartige Muster hat, haben Dokumente eine einzigartige Wortstruktur. Wenn Sie eine Datei hochladen, identifiziert der DLP Agent die einzigartige Wortstruktur des Dokuments, erstellt aus dieser Struktur einen Dokumentfingerabdruck und verwendet diesen Fingerabdruck zur Erkennung ausgehender Dokumente mit derselben Struktur. Aus diesem Grund werden die effektivsten Dokumentfingerabdrücke durch Hochladen von Formularen oder Vorlagen erstellt. Jede Person, die ein Formular ausfüllt, verwendet denselben Originalsatz von Wörtern und fügt dann ihre eigenen Wörter in das Dokument ein. Solange das ausgehende Dokument nicht durch ein Kennwort geschützt ist und sämtlichen Text aus dem Originalformular enthält, kann der DLP Agent bestimmen, ob das Dokument zum Dokumentfingerabdruck passt.

Im folgenden Beispiel wird gezeigt, was passiert, wenn Sie einen Dokumentfingerabdruck auf Grundlage einer Patentvorlage erstellen. Sie können aber auch jedes andere Formular dafür verwenden.

**Beispiel für ein Patentdokument, das zum Fingerabdruck einer Patentvorlage passt**

![Ein Patentdokument, das einem Dokumentfingerabdruck entspricht.](images/Dn635176.9c952770-2cd4-4f62-9735-6d073344be7f(EXCHG.150).png "Ein Patentdokument, das einem Dokumentfingerabdruck entspricht.")

Die Patentvorlage enthält die leeren Felder "Patenttitel", "Erfinder" und "Beschreibung" sowie Beschreibungen für alle diese Felder. Dies ist die Wortstruktur. Wenn Sie die Original-Patentvorlage hochladen, geschieht dies sowohl in Form eines der unterstützten Dateitypen als auch in reinem Textformat. Der DLP Agent verwendet einen Algorithmus zur Umwandlung dieser Wortstruktur in einen Dokumentfingerabdruck. Dies ist eine kleine Unicode-XML-Datei mit einem eindeutigen Hash-Wert, der für den Originaltext steht, und der Fingerabdruck wird als Datenklassifizierung in Active Directory gespeichert. (Als Sicherheitsmaßnahme wird das Originaldokument selbst nicht auf dem Dienst gespeichert. Es wird nur der Hash-Wert gespeichert, aus dem das Originaldokument rekonstruiert werden kann.) Der Patentfingerabdruck wird dann zu einer Art von vertraulicher Information, die Sie mit einer DLP-Richtlinie verbinden können. Wenn Sie den Fingerabdruck mit einer DLP-Richtlinie verbunden haben, erkennt der DLP Agent alle ausgehenden E-Mails mit Dokumenten, die zu diesem Fingerabdruck passen, und verarbeitet sie entsprechend der Richtlinie Ihrer Organisation. Sie können z. B. eine DLP-Richtlinie einrichten, die verhindert, dass nicht berechtigte Mitarbeiter Nachrichten absenden, die Patente enthalten. Der DLP Agent erkennt die Patente anhand des Patentfingerabdrucks und blockiert diese E-Mals. Optional können Sie einrichten, dass Ihre Rechtsabteilung die Erlaubnis haben soll, Patente an andere Organisationen zu senden, da dies ein geschäftliches Erfordernis ist. Sie können bestimmten Abteilungen erlauben, vertrauliche Informationen zu senden, indem Sie in Ihrer DLP-Richtlinie Ausnahmen für diese Abteilungen einrichten, oder Sie können ihnen erlauben, einen Richtlinientipp mit einer geschäftlichen Begründung zu überschreiben. Weitere detailliertere Informationen zur Erstellung von Richtlinienregeln und -ausnahmen finden Sie unter [DLP-Verfahren](https://technet.microsoft.com/de-de/library/jj938003\(v=exchg.150\)). Weitere Informationen zum Einrichten von Richtlinientipps, die von Anwendern überschrieben werden können, finden Sie unter [Richtlinientipps verwalten](https://technet.microsoft.com/de-de/library/JJ619307(v=EXCHG.150)).

## Unterstützte Dateitypen

Die Dokumentenfingerabdruck-Funktion unterstützt dieselben Dateitypen, die auch in Transportregeln unterstützt werden. Eine Liste der unterstützten Dateitypen finden Sie unter [Überprüfen von Nachrichtenanlagen mithilfe von Nachrichtenflussregeln](https://technet.microsoft.com/de-de/library/jj919236\(v=exchg.150\)). Eine kurze Bemerkung zu Dateitypen: Der Dateityp .dotx wird weder in den Transportregeln noch beim Dokumentfingerabdruck unterstützt, da er mit einer Vorlagendatei in Word verwechselt werden kann. Der Begriff "Vorlage" in diesem und anderen Themen zum Dokumentfingerabdruck bezieht sich auf ein Dokument, das Sie als Standardformular eingerichtet haben, nicht auf den Dateityp "Vorlage".

## Einschränkungen der Funktion "Dokumentfingerabdruck"

Der DLP Agent für Dokumentfingerabdrücke erkennt in den folgenden Fällen keine vertraulichen Informationen:

  - Kennwortgeschützte Dateien

  - Dateien, die nur Bilder enthalten

  - Dokumente, die nicht den gesamten Text aus dem Originalformular enthalten, aus dem der Dokumentfingerabdruck erstellt wurde

## Weitere Informationen

[Schutz von Formulardaten durch Dokumentfingerabdrücke](https://technet.microsoft.com/de-de/library/Dn635175(v=EXCHG.150))

[Integrieren von Regeln für vertrauliche Informationen in Transportregeln](https://technet.microsoft.com/de-de/library/JJ150583(v=EXCHG.150))

[DLP-Verfahren](https://technet.microsoft.com/de-de/library/jj938003\(v=exchg.150\))


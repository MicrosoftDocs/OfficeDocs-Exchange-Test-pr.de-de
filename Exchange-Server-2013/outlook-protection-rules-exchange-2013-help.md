---
title: 'Outlook-Schutzregeln: Exchange 2013 Help'
TOCTitle: Outlook-Schutzregeln
ms:assetid: bd7d0ad7-1f8e-46da-a74b-58c58f3eff93
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638178(v=EXCHG.150)
ms:contentKeyID: 50476588
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Outlook-Schutzregeln

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Jeden Tag tauschen Information-Worker sicherheitsrelevante Informationen per E-Mail aus, wozu Finanzberichte und -daten ebenso gehören wie Informationen zu Kunden und Mitarbeitern sowie vertrauliche Produktinformationen und -spezifikationen. In Microsoft Exchange Server 2013, Microsoft Outlook und Microsoft OfficeOutlook Web App können Benutzer ihre Nachrichten mit der Verwaltung von Informationsrechten (IRM) schützen, indem sie eine Vorlage für Benutzerrechterichtlinien für den Active Directory-Rechteverwaltungsdienst (AD RMS) anwenden. Hierfür ist eine AD RMS-Bereitstellung in der Organisation erforderlich. Weitere Informationen zu AD RMS finden Sie unter [Active Directory-Rechteverwaltungsdienste](https://go.microsoft.com/fwlink/p/?linkid=129823).

Im Ermessen der Benutzer können Nachrichten jedoch ohne IRM-Schutz unverschlüsselt gesendet werden. In Organisationen, die E-Mail als gehosteten Dienst verwenden, besteht das Risiko von Informationslecks, da die Nachricht den Client verlässt und an Standorte außerhalb der Grenzen einer Organisation weitergeleitet und dort gespeichert wird. Obwohl E-Mail-Hostingunternehmen über sorgfältig definierte Verfahren und Prüfungen verfügen, die dazu beitragen, das Risiko von Informationslecks zu minimieren, verliert die Organisation die Kontrolle über die Daten, sobald eine Nachricht die Grenzen der Organisation verlassen hat. Outlook-Schutzregeln können als Schutz gegen diese Art von Informationsleck dienen.

Verwaltungsaufgaben im Zusammenhang mit der Verwaltung von IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Automatischer IRM-Schutz in Outlook

In Exchange 2013 helfen Outlook-Schutzregeln der Organisation, sich gegen das Risiko von Informationslecks zu schützen, indem auf die Nachrichten in Exchange 2013 automatisch der IRM-Schutz angewendet wird. Nachrichten werden mit IRM-Schutz versehen, bevor Sie den Outlook-Client verlassen. Dieser Schutz gilt auch für alle Anlagen mit unterstützten Dateiformaten.

Wenn Sie auf einem Exchange 2013-Server Outlook-Schutzregeln erstellen, werden die Regeln mithilfe von Exchange-Webdiensten automatisch an Outlook 2010 verteilt. Damit Outlook 2010 die Regel anwenden kann, muss die AD RMS-Vorlage für Benutzerrechterichtlinien auf den Computern der Benutzer vorhanden sein.


> [!IMPORTANT]
> Wenn eine Vorlage für Benutzerrechterichtlinien vom AD&nbsp;RMS-Server entfernt wird, müssen Sie alle Outlook-Schutzregeln ändern, die auf der entfernten Vorlage basieren. Wenn eine Outlook-Schutzregel weiterhin auf einer Vorlage für Benutzerrechterichtlinien basiert, die entfernt wurde, und wenn in der Organisation die Transportentschlüsselung aktiviert ist, kann der Entschlüsselungs-Agent die Nachricht nicht entschlüsseln, die mit einer nicht mehr vorhandenen Vorlage geschützt wird. Wenn die Transportentschlüsselung als erforderlich konfiguriert wurde, weist der Transportdienst die Nachricht zurück und sendet einen Unzustellbarkeitsbericht (Non-Delivery Report, NDR) an den Absender. Weitere Informationen zur Transportentschlüsselung finden Sie unter <A href="transport-decryption-exchange-2013-help.md">Transportentschlüsselung</A>. Weitere Einzelheiten zu AD&nbsp;RMS-Vorlagen für Benutzerrechterichtlinien finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=179455">Überlegungen zu Vorlagen für AD RMS-Benutzerrechterichtlinien</A>.<BR>In Windows Server 2008 und höher können Vorlagen für Benutzerrechterichtlinien archiviert werden, statt dass sie gelöscht werden. Archivierte Vorlagen können weiterhin zum Lizenzieren von Inhalten verwendet werden. Wenn Sie jedoch eine Outlook-Schutzregel erstellen oder ändern, werden archivierte Vorlagen nicht die Vorlagenliste eingeschlossen.



Outlook-Schutzregeln sind mit Transportschutzregeln vergleichbar. Beide werden basierend auf Nachrichtenbedingungen angewendet, und beide schützen Nachrichten durch Anwenden einer AD RMS-Vorlage für Benutzerrechterichtlinien. Transportschutzregeln werden jedoch im Transportdienst auf dem Postfachserver vom Transportregel-Agent angewendet. Outlook-Schutzregeln werden in Outlook 2010 angewendet, bevor die Nachricht den Computer des Benutzers verlässt. Bei Nachrichten, die von einer Outlook-Schutzregel geschützt werden, ist der IRM-Schutz bereits aktiv, wenn sie an die Transportpipeline übergeben werden. Darüber hinaus werden Nachrichten, die mit einer Outlook-Schutzregel geschützt werden, auch in einem verschlüsselten Format im Ordner "Gesendete Elemente" im Postfach des Absenders gespeichert.


> [!NOTE]
> Wenn in Ihrer Exchange-Organisation die Transportentschlüsselung aktiviert ist, können Nachrichten, die von einer Outlook-Schutzregel auf dem AD&nbsp;RMS-Server in Ihrer Organisation durch IRM geschützt sind, von Entschlüsselungs-Agents im Transportdienst entschlüsselt werden. Der Nachrichteninhalt kann vom Transportregel-Agent und weiteren Transport-Agents, die im Transportdienst installiert sind, geprüft werden. Weitere Informationen zur Transportentschlüsselung finden Sie unter <A href="transport-decryption-exchange-2013-help.md">Transportentschlüsselung</A>.



Wenn Sie mit Transportschutzregeln arbeiten, ist für die Benutzer nicht ersichtlich, ob eine Nachricht im Transportdienst automatisch geschützt wird. Wenn auf eine Nachricht in Outlook 2010 eine Outlook-Schutzregel angewendet wird, sehen die Benutzer, ob die Nachricht mit IRM geschützt wird. Bei Bedarf können Benutzer auch eine andere Vorlage für Benutzerrichtlinien auswählen.

## Erstellen von Outlook-Schutzregeln

Zum Erstellen von Outlook-Schutzregeln müssen Sie das Cmdlet [New-OutlookProtectionRule](https://technet.microsoft.com/de-de/library/dd298182\(v=exchg.150\)) in der Exchange-Verwaltungsshell verwenden. Ausführliche Anweisungen finden Sie unter [Erstellen einer Outlook-Schutzregel](create-an-outlook-protection-rule-exchange-2013-help.md).

Beim Erstellen einer Regel können Sie angeben, ob der Benutzer sie außer Kraft setzen kann, indem entweder der IRM-Schutz aufgehoben oder eine andere AD RMS-Vorlage für Benutzerrichtlinien als diejenige angewendet wird, die in der Regel angegeben ist. Wenn ein Benutzer den IRM-Schutz, der von einer Outlook-Schutzregel angewendet wurde, außer Kraft setzt, fügt Outlook 2010 die Kopfzeile `X-MS-Outlook-Client-Rule-Overridden` in die Nachricht ein. Auf diese Weise können Sie sehen, dass die Regel vom Benutzer außer Kraft gesetzt wurde.

## Prädikate in Outlook-Schutzregeln

Outlook-Schutzregeln ermöglichen die Verwendung von drei Prädikaten, die in Outlook 2010 automatisch auf den IRM-Schutz angewendet werden:

  - **FromDepartment**   Mit dem Prädikat *FromDepartment* wird in Active Directory nach dem Abteilungsattribut des Absenders gesucht, und die Nachricht wird automatisch durch IRM geschützt, wenn die Abteilung des Absenders der in der Regel angegebenen Abteilung entspricht. So können Sie beispielsweise eine Outlook-Schutzregel erstellen, mit der automatisch alle Nachrichten geschützt werden, die von der Forschungsabteilung gesendet werden.

  - **SentTo**   Ihre Organisation muss ggf. Nachrichten schützen, die an bestimmte vertrauliche Empfänger gesendet werden, z. B. an die Verteilergruppen "Gesamtes Unternehmen" oder "Finanzen". Mithilfe des *SentTo*-Prädikats können Sie eine Outlook-Schutzregel erstellen, mit der Nachrichten an bestimmte Empfänger automatisch durch IRM geschützt werden.

  - **SentToScope**   Mit dem Prädikat *SentToScope* können Sie eine Outlook-Schutzregel erstellen, um automatisch alle Nachrichten durch IRM zu schützen, die innerhalb oder außerhalb der Organisation gesendet werden. Sie können beispielsweise das Prädikat *SentToScope* zusammen mit dem Prädikat *FromDepartment* verwenden, um Nachrichten mit IRM-Schutz zu versehen, die von einer bestimmten Abteilung an interne Benutzer gesendet werden.


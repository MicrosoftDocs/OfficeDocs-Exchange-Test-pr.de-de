---
title: 'UM-Postfachrichtlinien: Exchange 2013 Help'
TOCTitle: UM-Postfachrichtlinien
ms:assetid: dfae629e-ee89-4494-a3ed-9655b67eb87e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124909(v=EXCHG.150)
ms:contentKeyID: 50554930
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# UM-Postfachrichtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-15_

Unified Messaging-Postfachrichtlinien (UM) sind erforderlich, wenn Sie Benutzer für Unified Messaging aktivieren. Sie erstellen UM-Postfachrichtlinien, um einen gemeinsamen Satz an Richtlinien oder Sicherheitseinstellungen auf eine Sammlung von Postfächern von Voicemailbenutzern anzuwenden. UM-Postfachrichtlinien werden wie folgt zum Angeben von UM-Einstellungen verwendet:

  - PIN-Richtlinien

  - Wähleinschränkungen

  - Andere allgemeine Eigenschaften von UM-Postfachrichtlinien

Sie können beispielsweise eine UM-Postfachrichtlinie zum Erhöhen der PIN-Sicherheit erstellen, indem Sie die maximale Anzahl von Anmeldefehlversuchen für eine bestimmte Gruppe von UM-aktivierten Benutzern, z. B. von Führungskräften, verringern.

## UM-Postfachrichtlinien

Mindestens eine UM-Postfachrichtlinie muss erstellt worden sein, ehe Sie Benutzer für Unified Messaging aktivieren können. Sie können zusätzliche UM-Postfachrichtlinien erstellen, um eine gemeinsame Gruppe von Einstellungen auf Benutzergruppen anzuwenden.

Sie können UM-Postfachrichtlinien mithilfe der Exchange-Verwaltungsshell und Exchange-Verwaltungskonsole erstellen. Wenn Sie UM-Wähleinstellungen erstellen, wird standardmäßig eine einzige UM-Postfachrichtlinie erstellt. Die neue UM-Postfachrichtlinie wird automatisch dem UM-Wählplan zugeordnet, und ein Teil des Namens des Wählplans wird dem Anzeigenamen der UM-Postfachrichtlinie hinzugefügt. Sie können diese standardmäßige UM-Postfachrichtlinie bearbeiten.

Mehrere UM-aktivierte Benutzer können einer einzelnen UM-Postfachrichtlinie zugeordnet sein. Das Postfach jedes UM-aktivierten Benutzers muss jedoch mit einer einzelnen UM-Postfachrichtlinie verknüpft sein. Dadurch können Sie PIN-Sicherheitseinstellungen steuern, z. B. die Mindestanzahl an Stellen einer PIN oder die Höchstanzahl von Anmeldeversuchen für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind. Sie können außerdem Nachrichtentexteinstellungen oder Wähleinschränkungen für dieselben UM-aktivierten Postfächer steuern.


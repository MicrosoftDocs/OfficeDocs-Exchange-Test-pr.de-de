---
title: 'Gängige Szenarien der Nachrichtengenehmigung: Exchange 2013 Help'
TOCTitle: Gängige Szenarien der Nachrichtengenehmigung
ms:assetid: 5c13a07e-c21d-4502-a9f9-fb801197e1dd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298007(v=EXCHG.150)
ms:contentKeyID: 50475725
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Gängige Szenarien der Nachrichtengenehmigung

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-09-29_

In Ihrer Organisation müssen möglicherweise bestimmte Arten von Nachrichten genehmigt werden, um rechtliche Anforderungen zu erfüllen, Vorschriften einzuhalten oder einen bestimmten Geschäftsworkflow zu implementieren. Nachfolgend finden Sie einige Beispiele für gängige Szenarien, die Sie mithilfe von Exchange einrichten können:

  - Beispiel 1: Vermeiden eines Nachrichtenansturms auf eine große Verteilergruppe

  - Beispiel 2: Weiterleiten von Nachrichten zur Genehmigung an den Vorgesetzten eines Absenders

  - Beispiel 3: Einrichten einer Nachrichtengenehmigungskette

  - Beispiel 4: Weiterleiten von Nachrichten, die eines von mehreren Kriterien erfüllen

  - Beispiel 5: Weiterleiten einer Nachricht, die vertrauliche Informationen enthält

## Beispiel 1: Vermeiden eines Nachrichtenansturms auf eine große Verteilergruppe

Zum Steuern der Nachrichten, die an eine große Verteilergruppe gesendet werden, können Sie festlegen, dass ein Moderator die an diese Gruppe gesendeten Nachrichten genehmigen muss. Wenn keine Kriterien dafür angegeben wurden, welche Nachrichten genehmigt werden müssen, können Sie dies am einfachsten festlegen, indem Sie die Gruppe so konfigurieren, dass Nachrichten genehmigt werden müssen.

In diesem Beispiel müssen alle Nachrichten genehmigt werden, die an die Gruppe "All Employees" gesendet werden. Ausgenommen davon sind Absender, die Mitglieder der Verteilergruppe "Legal Team" sind.

![Nachrichtenbestätigungseinstellungen für eine Verteilergruppe](images/Dd298007.77721509-93f9-4a90-8d77-986db2b0acf4(EXCHG.150).png "Nachrichtenbestätigungseinstellungen für eine Verteilergruppe")

Um festzulegen, dass an eine bestimmte Verteilergruppe gesendete Nachrichten genehmigt werden müssen, navigieren Sie im Exchange Admin Center (EAC) zu **Empfänger** \> **Gruppen**, bearbeiten Sie die Verteilergruppe, und wählen Sie dann **Nachrichtengenehmigung** aus.

## Beispiel 2: Weiterleiten von Nachrichten zur Genehmigung an den Vorgesetzten eines Absenders

Im Folgenden sind einige gängige Nachrichtentypen aufgeführt, für die möglicherweise die Genehmigung des Vorgesetzten erforderlich ist:

  - Von einem Benutzer an bestimmte Verteilergruppen oder Empfänger gesendete Nachrichten

  - An externe Benutzer oder Partner gesendete Nachrichten

  - Zwischen zwei Gruppen gesendete Nachrichten

  - Gesendete Nachrichten mit bestimmten Inhalten, beispielsweise dem Namen eines bestimmten Kunden

  - Von einem Praktikanten gesendete Nachrichten

Um festzulegen, dass eine Nachricht zur Genehmigung übermittelt werden muss, erstellen Sie zuerst eine Regel mithilfe der Vorlage **Nachrichten an einen Moderator senden**, und geben Sie dann an, dass die Nachrichten an den Vorgesetzten des Absenders geleitet werden müssen, wie in den folgenden Screenshots dargestellt.

![Verwenden Sie eine Vorlage zum Erstellen neuer Regeln](images/Dd298007.051a5653-1a09-4db4-908f-48b56cc8d13f(EXCHG.150).png "Verwenden Sie eine Vorlage zum Erstellen neuer Regeln")

Legen Sie anschließend fest, welche Nachrichten genehmigt werden müssen.

Hier finden Sie ein Beispiel, bei dem für alle von einem Praktikanten namens Garth Fort an Empfänger außerhalb der Organisation gesendeten Nachrichten die Genehmigung des Vorgesetzten erforderlich ist.

![Regel, mit der Nachrichten an den Manager des Benutzers weitergeleitet werden](images/Dd298007.7f94c22e-b5ba-45a3-9ccd-31996b6c863a(EXCHG.150).png "Regel, mit der Nachrichten an den Manager des Benutzers weitergeleitet werden")

Navigieren Sie zuerst zum EAC \> **Nachrichtenfluss** \> **Regeln**, und erstellen Sie dann eine neue Regel mithilfe der Vorlage **Nachrichten an einen Moderator senden**.


> [!IMPORTANT]
> Einige Bedingungen und Aktionen, einschließlich der Weiterleitung von Nachrichten an den Vorgesetzten des Absenders, sind auf der Seite <STRONG>Neue Regel</STRONG> standardmäßig ausgeblendet. Wählen Sie <STRONG>Weitere Optionen</STRONG> aus, um alle Bedingungen und Aktionen anzuzeigen.



## Beispiel 3: Einrichten einer Nachrichtengenehmigungskette

Sie können mehrere Genehmigungsstufen für Nachrichten festlegen. Beispielsweise können Sie festlegen, dass Nachrichten an einen bestimmten Kunden zuerst vom Kundenbeziehungs-Manager und danach von einem Compliance Officer genehmigt werden müssen. Oder Sie legen fest, dass Spesenabrechnungen von Vorgesetzten auf zwei Ebenen genehmigt werden müssen.

Erstellen Sie eine Transportregel für jede Genehmigungsstufe, um diesen Typ mehrstufiger Genehmigung zu erstellen. Jede Regel erkennt die gleichen Muster in den Nachrichten, wie nachfolgend erläutert:

  - Die erste Regel leitet die Nachricht an die erste genehmigende Person weiter. Wenn die erste genehmigende Person die Nachricht akzeptiert, wird die Nachricht automatisch an die genehmigende Person in der zweiten Regel geleitet.

  - Wenn alle genehmigenden Personen in der Kette bei Erhalt der Genehmigungsanforderung **Genehmigen** auswählen, wird die ursprüngliche Nachricht, nachdem die letzte Genehmigung in der Kette abgeschlossen wurde, an die vorgesehenen Empfänger gesendet.

  - Wählt eine Person in der Genehmigungskette bei Erhalt der Genehmigungsanforderung **Ablehnen** aus, erhält der Absender eine Ablehnungsmeldung.

  - Wird eine der Genehmigungsanforderungen innerhalb der Ablaufzeit (2 Tage für Exchange Online, 5 Tage für Exchange Server 2013) nicht genehmigt, erhält der Absender eine Ablaufmeldung.

Im folgenden Beispiel wird davon ausgegangen, dass Sie einen Kunden namens Blue Yonder Airlines haben. Sowohl der Kundenbeziehungs-Manager als auch der Compliance Officer soll alle Nachrichten an diesen Kunden genehmigen. Sie erstellen zwei Regeln, eine für jede genehmigende Person. Die erste Regel ist für die genehmigende Person der ersten Stufe. Die zweite Regel ist für die genehmigende Person der zweiten Stufe.

![Zwei Regeln, die für zwei Genehmigungsebenen verwendet werden](images/Dd298007.29686c05-eaa0-42b9-86ad-d577f656392c(EXCHG.150).png "Zwei Regeln, die für zwei Genehmigungsebenen verwendet werden")

Die erste Regel ermittelt alle Nachrichten, bei denen der Firmenname Blue Yonder Airlines im Betreff oder im Nachrichtentext enthalten ist, und sendet diese Nachrichten dann an den internen Kundenbeziehungs-Manager für Blue Yonder Airlines, Garret Vargas.

![Regel für die Genehmigung auf erster Ebene](images/Dd298007.e22d1c04-85c5-4227-88e6-b118d5593350(EXCHG.150).png "Regel für die Genehmigung auf erster Ebene")

Die zweite Regel sendet diese Nachrichten an den Compliance Officer Tony Krijnen.

![Regel für Genehmigung auf zweiter Ebene mit gleichen Kriterien](images/Dd298007.5d888786-8e48-4459-ab86-8a4b9a016d58(EXCHG.150).png "Regel für Genehmigung auf zweiter Ebene mit gleichen Kriterien")

## Beispiel 4: Weiterleiten von Nachrichten, die eines von mehreren Kriterien erfüllen

Innerhalb einer Transportregel müssen alle in der Regel konfigurierten Bedingungen zutreffen, damit die Regel erfüllt ist. Wenn die gleichen Aktionen einzelnen Bedingungen zugeordnet werden sollen, müssen Sie für jede eine eigene Regel erstellen.

Erstellen Sie hierzu im EAC auf der Seite **Regeln** eine Regel für die erste Bedingung. Wählen Sie dann die Regel aus, wählen Sie **Kopieren** aus, und ändern Sie die Bedingungen in der neuen Regel, sodass sie mit der zweiten Bedingung übereinstimmen.

Gehen Sie sorgfältig vor, wenn Sie mehrere Regeln mit Bedingungen vom Typ ODER erstellen, damit eine Nachricht nicht letztlich mehrere Male an die genehmigende Person gesendet wird. Um dies zu vermeiden, fügen Sie der zweiten Regel eine Ausnahme hinzu, sodass Nachrichten ignoriert werden, die die Bedingungen in der ersten Regel erfüllen.

Beispiel: Mit einer einzelnen Regel kann nicht geprüft werden, ob in einer Nachricht der Text "Verkaufsangebot" im Betreff vorkommt oder der Titel der Anlage ist. Damit die Nachricht nicht mehrmals an die genehmigende Person gesendet wird, ist Folgendes erforderlich: Wenn die erste Regel prüft, ob der Text "Verkaufsangebot" im Betreff oder im Nachrichtentext enthalten ist, wird für die zweite Regel, die prüft, ob der Text "Verkaufsangebot" in der Anlage vorkommt, eine Ausnahme benötigt, die die Kriterien der ersten Regel enthält.

![Ausnahme für die zweite Regel verwenden](images/Dd298007.c39bbdcf-c619-4f84-8922-114ad1da824d(EXCHG.150).png "Ausnahme für die zweite Regel verwenden")


> [!NOTE]
> Ausnahmen werden standardmäßig auf der Seite <STRONG>Neue Regel</STRONG> ausgeblendet. Wählen Sie <STRONG>Weitere Optionen</STRONG> aus, um alle Bedingungen und Aktionen anzuzeigen.



## Beispiel 5: Weiterleiten einer Nachricht, die vertrauliche Informationen enthält

Wenn Sie über das Feature [Verhinderung von Datenverlust](https://technet.microsoft.com/de-de/library/JJ150527(v=EXCHG.150)) (DLP) verfügen, sind zahlreiche vertrauliche Informationstypen vordefiniert. Bei Verwendung von DLP wird Ihnen angezeigt, dass die Nachricht eine Bedingung für vertrauliche Informationen enthält. Unabhängig davon, ob Sie über DLP verfügen oder nicht, können Sie Bedingungen erstellen, die bestimmte vertrauliche Informationsmuster ausschließlich für Ihre Organisation ermitteln.

Hier finden Sie ein Beispiel, bei dem Nachrichten mit vertraulichen Informationen genehmigt werden müssen. In diesem Beispiel müssen Nachrichten genehmigt werden, die eine Kreditkartennummer enthalten.

![Regel, mit der eine E-Mail mit vertraulichen Informationen weitergeleitet wird](images/Dd298007.7ec1ca74-5d20-42ea-a9ee-3a8b25beb7df(EXCHG.150).png "Regel, mit der eine E-Mail mit vertraulichen Informationen weitergeleitet wird")

## Siehe auch


[Verwalten der Nachrichtengenehmigung](https://technet.microsoft.com/de-de/library/Dd297936(v=EXCHG.150))


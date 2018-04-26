---
title: Verfahren in Verbindung mit der Bereitstellung
TOCTitle: Verfahren in Verbindung mit der Bereitstellung
ms:assetid: 6b7682bd-fe3d-43b9-a7db-66c0ac17656f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn195909(v=EXCHG.150)
ms:contentKeyID: 53181881
ms.date: 04/03/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verfahren in Verbindung mit der Bereitstellung

 

_**Letztes Änderungsdatum des Themas:** 2013-04-17_

Dieser Abschnitt behandelt die Verfahren, die Sie als Referenz bei der Verwendung von Exchange Server 2013 Management Pack nutzen können. Weitere Informationen bezüglich der Verfahren nach der Bereitstellung finden Sie unter [Procedures related to post-deployment operation](procedures-related-to-post-deployment-operation.md).

## Überprüfen des Agent-Bereitstellungsstatus

Bevor Sie das Exchange Server 2013 Management Pack importieren, prüfen Sie, dass die SCOM-Agents auf Ihrem Exchange-Server betriebsbereit sind und die Integrität des Betriebssystem korrekt in SCOM gemeldet wird.

Ihr Benutzerkonto muss ein Mitglied der Operations Manager-Administratorrolle sein, um dieses Verfahren ausführen zu dürfen.

1.  Melden Sie sich beim SCOM-Server an, und öffnen Sie die SCOM-Konsole.

2.  Klicken Sie auf **Überwachen**und dann auf **Windows-Computer**.

3.  Stellen Sie sicher, dass alle Exchange-Server den Status **Fehlerfrei** haben.

![Intakte Agents in der SCOM-Konsole](images/Dn195909.7d1ff0bb-419e-40dc-babf-5fa2fb7229a8(EXCHG.150).png "Intakte Agents in der SCOM-Konsole")

## Überprüfen der Agent-Proxykonfiguration

Bevor Sie das Exchange Server 2013 Management Pack importieren, stellen Sie, dass der Agent-Proxy für die Ermittlung in SCOM aktiviert ist. Andernfalls werden die Agents auf Ihren Exchange-Servern den Exchange-Integritätsstatus nicht melden. Diese Konfiguration müssen Sie bei allen Ihren Exchange-Servern überprüfen.

Ihr Benutzerkonto muss ein Mitglied der Operations Manager-Administratorrolle sein, um dieses Verfahren ausführen zu dürfen.

1.  Melden Sie sich beim SCOM-Server an, und öffnen Sie die SCOM-Konsole.

2.  Klicken Sie in der Betriebskonsole auf **Verwaltung**.

3.  Klicken Sie auf **Mit Agents verwaltet**. Klicken Sie mit der rechten Maustaste auf Ihren Exchange-Server, und wählen Sie dann **Eigenschaften**.

4.  Vergewissern Sie sich, dass auf der Registerkarte **Sicherheit** das Kontrollkästchen **Diesen Agent als Proxyagent zur Ermittlung verwalteter Objekte auf anderen Computern verwenden** aktiviert ist.

5.  Klicken Sie auf **OK**.

## Überprüfen der Agent-Sicherheitskonfiguration

Aufgrund des Sicherheitsmodells, mit dem Exchange 2013 getestet wurde, kann der SCOM-Agent, der auf Ihren Exchange-Servern ausgeführt wird, ausschließlich mit dem Konto **LocalSystem** ausgeführt werden. Wenn Sie den Agent nicht mit dem Konto "LocalSystem" ausführen, treten beim Ausführen der synthetischen Transaktionen Fehler auf. Es können darüber hinaus auch andere Probleme auftreten.

Ihr Benutzerkonto muss ein Mitglied der Server Manager-Rollengruppe sein, um dieses Verfahren ausführen zu dürfen.

1.  Melden Sie sich bei Ihrem Exchange-Server an.

2.  Klicken Sie auf **Start** \> **Verwaltung** \> **Dienste**.

3.  Führen Sie einen Bildlauf nach unten in der Liste der Dienste bis zum Dienst **System Center-Verwaltung** durch.

4.  Stellen Sie sicher, dass in der Spalte **Anmelden alsLokales System** angezeigt wird.

5.  Wird in der Spalte **Anmelden als** etwas anderes angezeigt, ändern Sie dies in "Lokales System".
    
    1.  Klicken Sie mit der rechten Maustaste auf den Dienst **System Center-Verwaltung** und wählen **Eigenschaften**.
    
    2.  Wählen Sie die Registerkarte **Anmelden**.
    
    3.  Klicken Sie auf **Lokales Systemkonto**.
    
    4.  Klicken Sie auf **OK**.


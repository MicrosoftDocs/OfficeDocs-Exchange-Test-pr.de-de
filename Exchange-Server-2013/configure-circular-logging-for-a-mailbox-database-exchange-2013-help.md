---
title: 'Konfigurieren der Umlaufprotokollierung für eine Postfachdatenbank: Exchange 2013 Help'
TOCTitle: Konfigurieren der Umlaufprotokollierung für eine Postfachdatenbank
ms:assetid: 29cbd7cd-382b-4e0d-8368-2e49e75df2fc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn756374(v=EXCHG.150)
ms:contentKeyID: 62524851
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Umlaufprotokollierung für eine Postfachdatenbank

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-24_

Wenn Sie für eine Postfachdatenbank Umlaufprotokollierung aktivieren, hängt die Art der Umlaufprotokollierung, die Sie erhalten, davon ab, ob die Postfachdatenbank mithilfe fortlaufender Replikation repliziert wird:

  - Wenn die Postfachdatenbank nicht repliziert wird, wird JET-Umlaufprotokollierung verwendet. In diesem Fall ist zur Aktivierung oder Deaktivierung der JET-Umlaufprotokollierung eine Aufhebung der Bereitstellung der Datenbank und eine erneute Bereitstellung erforderlich.

  - Wenn die Postfachdatenbank repliziert wird, wird CRCL (Continuous Replication Circular Logging, fortlaufende Umlaufprotokollierungsreplikation) verwendet. In diesem Fall wird das Aktivieren oder Deaktivieren der CRCL dynamisch wirksam. Es ist nicht erforderlich, die Bereitstellung der Datenbank aufzuheben und die Datenbank erneut bereitzustellen.

Weitere Informationen zu Umlaufprotokollierung und CRCL finden Sie unter [Exchange Native Data Protection](backup-restore-and-disaster-recovery-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbankberechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

## Konfigurieren der Umlaufprotokollierung für eine Datenbank mithilfe des EAC

1.  Navigieren Sie im EAC zu **Server** \> **Datenbanken**.

2.  Wählen Sie die Postfachdatenbank aus, die Sie konfigurieren möchten, und klicken Sie auf ![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren oder deaktivieren Sie das Kontrollkästchen **Umlaufprotokollierung aktivieren**, und klicken Sie dann auf **Speichern**.

4.  Wenn ein Aufheben der Bereitstellung und eine erneute Bereitstellung der Datenbank erforderlich ist, wird eine Warnmeldung angezeigt. Klicken Sie auf **OK**, um die Warnmeldung zu schließen.
    
    1.  Um die Bereitstellung der Datenbank aufzuheben, klicken Sie auf **Weiter**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") und dann auf **Bereitstellung aufheben**. Klicken Sie auf **Ja**, wenn die Warnmeldung angezeigt wird.
    
    2.  Um die Datenbank bereitzustellen, klicken Sie auf **Weiter**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") und dann auf **Bereitstellen**. Klicken Sie auf **Ja**, wenn die Warnmeldung angezeigt wird.

## Konfigurieren der Umlaufprotokollierung für eine Datenbank mithilfe der Shell

In diesem Beispiel wird die Umlaufprotokollierung für Datenbank DB1 aktiviert.

    Set-MailboxDatabase DB1 -CircularLoggingEnabled $True

In diesem Beispiel wird die Umlaufprotokollierung für Datenbank DB1 deaktiviert.

    Set-MailboxDatabase DB1 -CircularLoggingEnabled $False

Unter [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)) finden Sie weitere Postfachdatenbankparameter, die Sie konfigurieren können.


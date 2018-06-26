---
title: 'Provisorische Bereitstellung des Clusternamenobjekts für eine Database Availability Group: Exchange 2013 Help'
TOCTitle: Provisorische Bereitstellung des Clusternamenobjekts für eine Database Availability Group
ms:assetid: 51ebf2f6-8a02-44ef-a489-ca361cb0f63a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff367878(v=EXCHG.150)
ms:contentKeyID: 50475651
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Provisorische Bereitstellung des Clusternamenobjekts für eine Database Availability Group

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-08-14_

In Umgebungen, in denen die Erstellung von Computerkonten eingeschränkt ist oder in denen Computerkonten nicht im Standardcontainer für Computer, sondern in einem anderen Container erstellt werden, können Sie das Clusternamenobjekt (CNO) zuerst provisorisch und anschließend durch Zuweisen von Berechtigungen endgültig bereitstellen. Die provisorische Bereitstellung des Clusternetzwerkobjekts ist außerdem für DAG-Mitglieder unter Windows Server 2012 und Windows Server 2012 R2 aufgrund von Berechtigungsänderungen unter Windows für Computerobjekte erforderlich. Beim Bereitstellen einer Database Availability Group (DAG) mithilfe von Postfachservern unter Windows Server 2012 oder Windows Server 2012 R2 müssen Sie das Clusternetzwerkobjekt zuerst provisorisch und anschließend endgültig bereitstellen. Das trifft nicht zu, wenn Sie eine DAG ohne einen Cluster-Administratorzugriffspunkt bereitstellen. DAGs ohne Administratorzugriffspunkte verwenden keine CNOs. Daher ist für diese DAGs keine provisorische Bereitstellung erforderlich.

Sie erstellen zuerst ein Computerkonto für das CNO, deaktivieren es, und führen dann einen der folgenden Schritte aus:

  - Zuweisen von Vollzugriff auf das Computerkonto an das Computerkonto des ersten Postfachservers, der der DAG hinzugefügt wird.

  - Zuweisen von Vollzugriff auf die universelle Sicherheitsgruppe "Exchange Trusted Subsystem".

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Sie müssen ein Konto verwenden, das über Berechtigungen zum Erstellen von Computerobjekten in Active Directory verfügt.

  - Nachdem Sie die folgenden Schritte ausgeführt haben, müssen Sie warten, bis die Replikation von Active Directory erfolgt ist. Nach der Objektreplikation können Sie der DAG das erste Mitglied hinzufügen.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Provisorische Bereitstellung des Clusternetzwerkobjekts (CNO)

1.  Öffnen Sie "Active Directory-Benutzer und -Computer".

2.  Erweitern Sie den Gesamtstrukturknoten.

3.  Klicken Sie mit der rechten Maustaste auf die Organisationseinheit, in der das neue Konto erstellt werden soll. Wählen Sie im Kontextmenü zuerst die Option **Neu** und anschließend **Computer** aus.

4.  Geben Sie unter **Neues Objekt - Computer** im Feld **Computername** den Namen des Computerkontos für das CNO ein. Dies ist der Name, der für die DAG verwendet wird. Klicken Sie auf **OK**, um das Konto zu erstellen.

5.  Klicken Sie mit der rechten Maustaste auf das neue Computerkonto, und klicken Sie dann auf **Konto deaktivieren**. Klicken Sie auf **Ja**, um den Deaktivierungsvorgang zu bestätigen, und klicken Sie dann auf **OK**.

## Zuweisen von Berechtigungen zum Clusternetzwerkobjekt (CNO)

1.  Öffnen Sie "Active Directory-Benutzer und -Computer".

2.  Wenn "Erweiterte Funktionen" nicht aktiviert ist, klicken Sie auf **Ansicht** und dann auf **Erweiterte Funktionen**, um diese zu aktivieren.

3.  Klicken Sie mit der rechten Maustaste auf das neue Computerkonto, und klicken Sie dann auf **Eigenschaften**.

4.  Klicken Sie unter **Eigenschaften von \<Computername\>** auf der Registerkarte **Sicherheit** auf **Hinzufügen**, um entweder das Computerkonto für den ersten, der DAG hinzugefügten Knoten oder die universelle Sicherheitsgruppe "Exchange Trusted Subsystem" hinzuzufügen:
    
      - Geben Sie **Exchange Trusted Subsystem** im Feld **Auszuwählende Objektnamen eingeben** ein, um das vertrauenswürdige Exchange-Subsystem hinzuzufügen. Klicken Sie auf **OK**, um die universelle Sicherheitsgruppe hinzuzufügen. Wählen Sie die universelle Exchange-Gruppe "Vertrauenswürdiges Subsystem" und anschließend im Feld **Berechtigungen für vertrauenswürdiges Subsystem** in der Spalte **Zulassen** die Option **Vollzugriff** aus. Klicken Sie zum Speichern der Berechtigungseinstellungen auf **OK**.
    
      - Wenn Sie das Computerkonto für den ersten, der DAG hinzugefügten Knoten hinzufügen möchten, klicken Sie auf **Objekttypen**. Deaktivieren Sie im Dialogfeld **Objekttypen** die Kontrollkästchen **Integrierte Sicherheitsprinzipale**, **Gruppen** und **Benutzer**. Aktivieren Sie das Kontrollkästchen **Computer**, und klicken Sie dann auf **OK**. Geben Sie im Feld **Geben Sie die zu verwendenden Objektnamen ein** den Namen des ersten Postfachservers ein, der der DAG hinzugefügt werden soll, und klicken Sie dann auf **OK**. Wählen Sie das Computerkonto des ersten Knotens und anschließend im Feld **Berechtigungen für \<Knotenname\>** in der Spalte **Zulassen** die Option **Vollzugriff** aus. Klicken Sie zum Speichern der Berechtigungseinstellungen auf **OK**.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass das Clusternetzwerkobjekt erfolgreich erstellt wurde:

1.  Öffnen Sie "Active Directory-Benutzer und -Computer".

2.  Erweitern Sie den Gesamtstrukturknoten.

3.  Öffnen Sie die Organisationseinheit, in der Sie das Konto erstellt haben, und stellen Sie sicher, dass das Konto aufgeführt wird.


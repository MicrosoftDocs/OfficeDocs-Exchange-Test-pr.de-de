---
title: 'Konfigurieren der Suchliste für DNS-Suffixe für einen nicht zusammenhängenden Namespace: Exchange 2013 Help'
TOCTitle: Konfigurieren der Suchliste für DNS-Suffixe für einen nicht zusammenhängenden Namespace
ms:assetid: cfa715ac-7b69-47c3-b206-933ec2cf677b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb847901(v=EXCHG.150)
ms:contentKeyID: 50476759
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Suchliste für DNS-Suffixe für einen nicht zusammenhängenden Namespace

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In diesem Thema wird erläutert, wie die Gruppenrichtlinien-Verwaltungskonsole (Group Policy Management Console, GPMC) zum Konfigurieren der Suchliste für DNS-Suffixe (Domain Name System) verwendet wird. In einigen Microsoft Exchange 2013-Szenarios müssen Sie die Suchliste für DNS-Suffixe so konfigurieren, dass mehrere DNS-Suffixe berücksichtigt werden, wenn Sie einen nicht zusammenhängenden Namespace verwenden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten

  - Damit Sie dieses Verfahren ausführen können, muss die Mitgliedschaft in der Gruppe Domänenadministratoren an das verwendete Konto delegiert worden sein.

  - Stellen Sie sicher, dass .NET Framework 3.0 auf dem Computer installiert ist, auf dem die GPMC installiert werden soll.
    

    > [!NOTE]
    > Die aktuelle Version der GPMC, die Sie aus dem Microsoft Download Center herunterladen können, kann mit den 32-Bit-Versionen der Betriebssysteme Windows Server 2003 und Windows XP eingesetzt und für die Remoteverwaltung von Gruppenrichtlinienobjekten auf 32-Bit- und 64-Bit-Domänencontrollern verwendet werden. Diese Version der GPMC enthält keine 64-Bit-Version, und die 32-Bit-Version kann nicht auf 64-Bit-Plattformen ausgeführt werden. Sowohl die 32-Bit-Version von Windows Server 2008&nbsp;als auch die 32-Bit-Version von Windows Vista&nbsp;enthalten eine 32-Bit-Version der GPMC. Sowohl die 64-Bit-Version von Windows Server 2008&nbsp;als auch die 64-Bit-Version von Windows Vista&nbsp;enthalten eine 64-Bit-Version der GPMC.



  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren der Suchliste für DNS-Suffixe mithilfe der GPMC

1.  Installieren Sie auf einem 32-Bit-Computer in Ihrer Domäne die GPMC mit Service Pack 1 (SP1). Informationen zum Download finden Sie unter [Gruppenrichtlinien-Verwaltungskonsole mit Service Pack 1](https://go.microsoft.com/fwlink/p/?linkid=100126).
    

    > [!NOTE]
    > Wenn Sie einen Computer in Ihrer Domäne verwenden, der Windows Server 2008&nbsp;oder Windows Vista ausführt, können Sie diesen Schritt überspringen.



2.  Klicken Sie auf **Start** \> **Programme** \> **Verwaltung** \> **Gruppenrichtlinienverwaltung**.

3.  Erweitern Sie in **Gruppenrichtlinienverwaltung** die Gesamtstruktur und die Domäne, in der Sie die Gruppenrichtlinie anwenden möchten. Klicken Sie mit der rechten Maustaste auf **Gruppenrichtlinienobjekte**, und klicken Sie dann auf **Neu**.

4.  Geben Sie in **Neues Gruppenrichtlinienobjekt** einen Namen für die Richtlinie ein, und klicken Sie dann auf **OK**.

5.  Klicken Sie mit der rechten Maustaste auf die in Schritt 4 neu erstellte Richtlinie, und klicken Sie dann auf **Bearbeiten**.

6.  Erweitern Sie in **Gruppenrichtlinienobjekt-EditorComputerkonfiguration**, **Richtlinien**, **Administrative Vorlagen** und **Netzwerk**, und klicken Sie dann auf **DNS-Client**.

7.  Klicken Sie mit der rechten Maustaste auf **Suchliste für DNS-Suffix**, klicken Sie auf **Alle Tasks** und dann auf **Bearbeiten**.

8.  Wählen Sie auf der Seite **Eigenschaften von Suchliste für DNS-Suffix** die Option **Aktiviert** aus. Geben Sie im Feld **DNS-Suffixe** das primäre DNS-Suffix des nicht zusammenhängenden Namespaces des Computers, den DNS-Domänennamen und alle weiteren Namespaces für andere Servers ein, mit denen Exchange ggf. zusammenarbeitet, z. B. Überwachungsserver oder Server für Anwendungen von Drittanbietern. Klicken Sie auf **OK**.

9.  Erweitern Sie in **Gruppenrichtlinienverwaltung** die Option **Gruppenrichtlinienobjekte**, und wählen Sie dann die Richtlinie aus, die Sie in Schritt 4 erstellt haben. Wählen Sie auf der Registerkarte **Bereich** den Gültigkeitsbereich der Richtlinie so aus, dass er nur für die Computer gilt, die einen nicht zusammenhängenden Namespace besitzen.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Überprüfen Sie nach der Installation von Exchange 2013, ob Sie E-Mails innerhalb und außerhalb der Organisation senden können.

## Weitere Informationen

[Windows Server-Gruppenrichtlinie](https://go.microsoft.com/fwlink/p/?linkid=100128)

[Gruppenrichtlinie](https://go.microsoft.com/fwlink/?linkid=268043)

[Szenarien mit nicht zusammenhängenden Namespaces](disjoint-namespace-scenarios-exchange-2013-help.md)


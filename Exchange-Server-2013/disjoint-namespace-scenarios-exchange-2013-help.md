---
title: 'Szenarien mit nicht zusammenhängenden Namespaces: Exchange 2013 Help'
TOCTitle: Szenarien mit nicht zusammenhängenden Namespaces
ms:assetid: 90101d49-6f45-44be-8a93-eeb2c8283e3b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb676377(v=EXCHG.150)
ms:contentKeyID: 50476239
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Szenarien mit nicht zusammenhängenden Namespaces

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In diesem Thema erhalten Sie Informationen zum Konzept nicht zusammenhängender Namespaces und zu den unterstützten Szenarien für die Bereitstellung von Microsoft Exchange 2013 in einer Domäne mit einem nicht zusammenhängenden Namespace.

**Inhalt**

DNS- und NetBIOS-Domänennamen

Nicht zusammenhängende Namespaces

Exchange 2013 und nicht zusammenhängende Namespaces

Zulassen des Zugriffs von Servern mit Exchange 2013 auf disjunkte Domänencontroller

Anzeigen von Informationen im Zusammenhang mit DNS- und NetBIOS-Namen für einen Computer unter Windows Server 2008

## DNS- und NetBIOS-Domänennamen

Zunächst einige Hintergrundinformationen. Jeder Computer, der mit dem Internet verbunden ist, verfügt über einen DNS-Namen (Domain Name System). Dieser wird auch als *Computername* oder *Hostname* bezeichnet. Jeder Computer unter einem Windows-Betriebssystem mit Netzwerkfunktionen verfügt auch über einen NetBIOS-Namen.

Ein Computer unter Windows in einer Active Directory-Domäne besitzt sowohl einen DNS-Domänennamen als auch einen NetBIOS-Domänennamen, wie folgt:

  - **DNS-Domänenname**   Der DNS-Domänenname besteht aus einer oder mehreren Unterdomänen, die durch einen Punkt (**.**) getrennt sind, und wird durch einen Domänennamen der obersten Ebene abgeschlossen. Beispielsweise lauten im DNS-Domänennamen "corp.contoso.com" die Unterdomänen "corp" und "contoso", und der Domänenname der obersten Ebene lautet "com".

  - **NetBIOS-Domänenname**   Im Allgemeinen ist der NetBIOS-Domänenname die Unterdomäne des DNS-Domänennamens. Wenn beispielsweise der DNS-Domänenname "contoso.com" ist, ist der NetBIOS-Domänenname "contoso". Wenn der DNS-Domänenname "corp.contoso.com" ist, ist der NetBIOS-Domänenname "corp".


> [!NOTE]
> Wie Sie die DNS- und NetBIOS-Informationen für Computer unter Windows Server 2008 herausfinden, finden Sie unter Anzeigen von Informationen im Zusammenhang mit DNS- und NetBIOS-Namen für einen Computer unter Windows Server 2008.



Ein Computer in einer Active Directory-Domäne weist außerdem ein primäres DNS-Suffix auf und kann über weitere DNS-Suffixe verfügen. Standardmäßig ist das primäre DNS-Suffix gleich dem DNS-Domänennamen. Genaue Anweisungen zum Ändern des primären DNS-Suffixes finden Sie in den Verfahrensweisen weiter unten in diesem Thema.

Der DNS-Domänenname und der NetBIOS-Domänenname einer Active Directory-Domäne werden bei der Konfiguration des ersten Domänencontrollers in der Domäne festgelegt. Weitere Informationen zur Konfiguration von Domänencontrollern finden Sie unter [Domain Controller Roles](https://go.microsoft.com/fwlink/p/?linkid=268367) sowie unter [Übersicht über Active Directory-Domänendienste](https://go.microsoft.com/fwlink/p/?linkid=268366).

## Nicht zusammenhängende Namespaces

In den meisten Domänentopologien ist das primäre DNS-Suffix der Computer in der Domäne gleich dem DNS-Domänennamen.

In einigen Fällen kann jedoch die Verschiedenheit dieser Namespaces erforderlich sein. Dies wird als *nicht zusammenhängender Namespace* bezeichnet. Zum Beispiel kann ein Firmenzusammenschluss oder eine Firmenübernahme zu einer Topologie mit einem nicht zusammenhängenden Namespace führen. Darüber hinaus kann eine Topologie mit nicht zusammenhängendem Namespace erforderlich werden, wenn die DNS-Verwaltung in Ihrem Unternehmen zwischen Administratoren, die Active Directory verwalten, und Administratoren, die Netzwerke verwalten, aufgeteilt ist.

Ein nicht zusammenhängender Namespace ist ein Szenario, in dem das primäre DNS-Suffix eines Computers nicht dem DNS-Domänennamen der Domäne entspricht, in der der Computer enthalten ist. Der Computer mit dem primären DNS-Suffix, das nicht übereinstimmt, wird als *disjunkt* bezeichnet. Ein anderes Szenario mit nicht zusammenhängendem Namespace tritt ein, wenn der NetBIOS-Domänenname eines Domänencontrollers nicht dem DNS-Domänennamen entspricht.

## Exchange 2013 und nicht zusammenhängende Namespaces

Exchange 2013 unterstützt die folgenden drei Szenarien für die Bereitstellung von Exchange in einer Domäne mit einem nicht zusammenhängenden Namespace:

  - **Primäres DNS-Suffix und DNS-Domänenname sind unterschiedlich**   Das primäre DNS-Suffix des Domänencontrollers ist nicht gleich dem DNS-Domänennamen. Computer, die Mitglieder der Domäne sind, können entweder nicht zusammenhängend oder zusammenhängend sein.

  - **Mitgliedscomputer ist disjunkt**   Ein Mitgliedscomputer in einer Active Directory-Domäne ist disjunkt, obwohl der Domänencontroller nicht disjunkt ist.

  - **Der NetBIOS-Name des Domänencontrollers unterscheidet sich von der Unterdomäne seines DNS-Domänennamens**   Der NetBIOS-Domänenname des Domänencontrollers ist nicht gleich der Unterdomäne des DNS-Domänennamens dieses Domänencontrollers.

Diese Szenarien werden in den folgenden Abschnitten ausführlich behandelt.


> [!NOTE]
> Die Ausführung von Exchange 2013 in den in diesem Artikel beschriebenen Szenarien mit nicht zusammenhängenden Namespaces wird unterstützt. Wenn bei Ihnen hingegen ein Szenario mit nicht zusammenhängenden Namespaces vorliegt, das nicht von einem der in diesem Artikel beschriebenen Szenarien abgedeckt ist, müssen Sie mit Microsoft Services zusammenarbeiten, um Exchange 2013 bereitzustellen. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=94845">Microsoft Services</A>.



## Szenario: Primäre DNS-Suffix und DNS-Domänenname sind unterschiedlich

In diesem Szenario ist das primäre DNS-Suffix des Domänencontrollers nicht gleich dem DNS-Domänennamen. Der Domänencontroller ist in diesem Szenario disjunkt. Computer, die Mitglieder der Domäne sind, einschließlich Exchange-Servern und Microsoft Outlook-Clientcomputern, können ein primäres DNS-Suffix aufweisen, das entweder dem primären DNS-Suffix des Domänencontrollers oder dem DNS-Domänennamen entspricht.

## Szenario: Der Mitgliedscomputer ist disjunkt

In diesem Szenario ist das primäre DNS-Suffix eines Mitgliedscomputers, auf dem Exchange 2013 installiert ist, nicht gleich dem DNS-Domänennamen, obwohl das primäre DNS-Suffix des Domänencontrollers gleich dem DNS-Domänennamen ist. In diesem Szenario liegen ein nicht disjunkter Domänencontroller und ein disjunkter Mitgliedscomputer vor. Mitgliedscomputer, auf denen Outlook ausgeführt wird, können ein primäres DNS-Suffix aufweisen, das entweder dem primären DNS-Suffix des disjunkten Exchange-Servers oder dem DNS-Domänennamen entspricht.

## Szenario: NetBIOS-Name des Domänencontrollers unterscheidet sich von der Unterdomäne seines DNS-Domänennamens

In diesem Szenario ist der NetBIOS-Domänenname des Domänencontrollers nicht gleich dem DNS-Domänennamen desselben Domänencontrollers.

**NetBIOS-Domänenname entspricht nicht dem DNS-Domänennamen**

![NetBIOS-Domänenname entspricht nicht dem DNS-Domänennamen](images/Bb676377.1ee18cb6-0296-4875-b572-0ddf33f65f7c(EXCHG.150).gif "NetBIOS-Domänenname entspricht nicht dem DNS-Domänennamen")

## Zulassen des Zugriffs von Servern mit Exchange 2013 auf disjunkte Domänencontroller

Um Exchange 2013-Servern den Zugriff auf Domänencontroller zu ermöglichen, die disjunkt sind, müssen Sie das Attribut **msDS-AllowedDNSSuffixes**Active Directory im Container des Domänenobjekts ändern. Dem Attribut müssen beide DNS-Suffixe hinzugefügt werden. Detaillierte Schritte zum Ändern des Attributs finden Sie unter [Das primäre DNS-Suffix des Computers entspricht nicht dem FQDN der Domäne, in der sich der Computer befindet](https://go.microsoft.com/fwlink/p/?linkid=98848).

Darüber hinaus muss die Suchliste für jeden Computer in der disjunkten Domäne konfiguriert werden, um sicherzustellen, dass die Suchliste für DNS-Suffixe alle in der Organisation bereitgestellten DNS-Namespaces enthält. Die Liste der Namespaces soll nicht nur das primäre DNS-Suffix des Domänencontrollers und den DNS-Domänennamen enthalten, sondern auch alle weiteren Namespaces für andere Server, mit denen Exchange zusammenarbeiten soll (etwa Überwachungsserver oder Server für Anwendungen von Drittanbietern). Dies kann durch Festlegen von Gruppenrichtlinien für die Domäne erfolgen. Weitere Informationen zu Gruppenrichtlinien finden Sie unter den folgenden Themen:

  - [Group Policy Frequently Asked Questions (FAQ)](https://go.microsoft.com/fwlink/p/?linkid=100128)

  - [Neue Gruppenrichtlinien für DNS in Windows Server 2003](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=294785)

  - [Gruppenrichtlinien](https://go.microsoft.com/fwlink/p/?linkid=268043)

Genaue Anweisungen zum Konfigurieren der Gruppenrichtlinie für die DNS-Suffix-Suchliste finden Sie unter [Konfigurieren der Suchliste für DNS-Suffixe für einen nicht zusammenhängenden Namespace](configure-the-dns-suffix-search-list-for-a-disjoint-namespace-exchange-2013-help.md).

## Anzeigen von Informationen im Zusammenhang mit DNS- und NetBIOS-Namen für einen Computer unter Windows Server 2008

1.  Klicken Sie auf **Start**, klicken Sie mit der rechten Maustaste auf **Computer**, und klicken Sie dann auf **Eigenschaften**.

2.  Unter **System** werden der DNS-Hostname und das primäre DNS-Suffix unter **Einstellungen für Computernamen, Domäne und Arbeitsgruppe** neben **Vollständiger Computername** angezeigt. Der DNS-Domänenname wird neben **Domäne** angezeigt.

3.  Klicken Sie auf **Einstellungen ändern**.

4.  Klicken Sie in **Systemeigenschaften** auf der Registerkarte **Computername** auf **Ändern**.

5.  Klicken Sie in **Computernamen- bzw. -domänenänderungen** auf **Weitere**. Das primäre DNS-Suffix wird unter **Primäres DNS-Suffix dieses Computers** angezeigt. Der NetBIOS-Computername wird unter **NetBIOS-Computername** angezeigt.
    
    Geben Sie zum Ändern des primären DNS-Suffixes das neue primäre DNS-Suffix unter **Primäres DNS-Suffix dieses Computers** ein, und klicken Sie dann auf **OK**.

6.  Geben Sie in einem Fenster der Eingabeaufforderung **set** ein. Der DNS-Domänenname wird in der Variablen USERDNSDOMAIN angezeigt. Der NetBIOS-Domänenname wird in der Variablen USERDOMAIN angezeigt.


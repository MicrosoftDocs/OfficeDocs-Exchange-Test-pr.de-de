---
title: 'Kurzwahlnummern, Rufnummernpräfixe und Nummernformate: Exchange 2013 Help'
TOCTitle: Kurzwahlnummern, Rufnummernpräfixe und Nummernformate
ms:assetid: 26d61e55-f8dd-4d25-81f1-78a87cf88bad
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb266967(v=EXCHG.150)
ms:contentKeyID: 51409275
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Kurzwahlnummern, Rufnummernpräfixe und Nummernformate

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-05-04_

Sie können mehrere Kurzwahlnummern konfigurieren, die dann von einem Unified Messaging-Server (UM) zur Anwahl interner und externer Rufnummern für UM-aktivierte Benutzer verwendet werden. In vielen Fällen möchten Sie Wähleinstellungen in Verbindung mit den Kurzwahl- oder Zugriffscodes, einem nationalen Nummernpräfix oder den nationalen/regionalen oder internationalen Nummernformaten konfigurieren, damit Sie das Outdialing für Benutzer in Ihrer Organisation steuern können. Dieses Thema befasst sich mit Kurzwahlnummern, Nummernpräfixen und Nummernformaten und erläutert, wie diese zum Steuern des Outdialings in Ihrer Organisation verwendet werden können.

**Inhalt**

Übersicht

Amtskennziffer

Rufnummernpräfix, national

Länder-/Regionszugriffscode

Internationale VAZ

Nationale/regionale und internationale Nummernformate

## Übersicht

Das *Outdialing* ist der Prozess, mit dem sich Benutzer über einen UM-Wählplan oder bei einer automatischen UM-Telefonzentrale einwählen und dann einen Anruf bei einer internen oder externen Rufnummer tätigen. Wenn sich ein Benutzer über einen UM-Wählplan oder bei einer automatischen UM-Telefonzentrale einwählt und einen Anruf tätigt, verwendet Unified Messaging die für die Wähleinstellungen, die automatische Telefonzentrale und die UM-Postfachregel konfigurierten Einstellungen, um den Anruf durchzuführen. UM tätigt in den folgenden Situationen einen ausgehenden Anruf:

  - Wenn für einen Anrufer eine externe Telefonnummer gewählt wird

  - Wenn einen Anruf an eine automatische Telefonzentrale übergeben wird

  - Wenn ein Anruf an einen (UM-aktivierten oder nicht UM-aktivierten) Benutzer in Ihrer Organisation übergeben wird

  - Wenn ein UM-aktivierter Benutzer die Funktion "Wiedergabe über Telefon" verwendet

Zwei Typen von Benutzern verwenden Outdialing: authentifizierte Benutzer und nicht authentifizierte Benutzer. Nicht authentifizierte Benutzer rufen eine Outlook Voice Access-Nummer an, die in einem UM-Wählplan konfiguriert ist, ohne sich jedoch bei ihrem Postfach anzumelden. Nicht authentifizierte Benutzer rufen auch eine Nummer an, die in einer automatischen UM-Telefonzentrale konfiguriert ist. Authentifizierte Benutzer rufen eine Outlook Voice Access-Nummer an und melden sich erfolgreich bei ihrem Postfach an. Wenn Benutzer eine Outlook Voice Access-Nummer anrufen, gelten sie zunächst als nicht authentifiziert, weil sie nicht ihre Durchwahlnummer und PIN angegeben und sich nicht bei ihrem Postfach angemeldet haben. Benutzer sind authentifiziert, nachdem sie ihre Durchwahlnummer mit PIN angegeben und sich erfolgreich bei ihrem Postfach angemeldet haben.

Wenn ein nicht authentifizierter Benutzer bei einer UM-Telefonzentrale anruft und einen Anruf mithilfe von Outdialing tätigt, werden die Einstellungen für das Outdialing verwendet, die in den UM-Wähleinstellungen und für die Telefonzentrale konfiguriert sind. Wenn ein nicht authentifizierter Benutzer eine Outlook Voice Access-Nummer wählt, die in einem Wählplan konfiguriert ist, werden einzig die für den Wählplan konfigurierten Einstellungen verwendet. Wenn sich Benutzer jedoch erfolgreich bei ihrem Postfach angemeldet haben, werden für die authentifizierten Benutzer die Konfigurationseinstellungen des Wählplans sowie die UM-Postfachrichtlinie angewendet, die den authentifizierten Benutzern zugeordnet sind.

Sie müssen mehrere Einstellungen konfigurieren, um Outdialingregeln für Ihre Organisation zu aktivieren. Zum Steuern des Outdialings müssen Sie den UM-Wählplan, automatischen Telefonzentralen und UM-Postfachrichtlinien in Unified Messaging konfigurieren. Die folgenden Einstellungen können für UM-Wähleinstellungen, automatische Telefonzentralen und UM-Postfachrichtlinien konfiguriert werden, um das Outdialing zu steuern:

  - Amtskennziffer, nationale/regionale und internationale Zugriffscodes

  - Nationales Rufnummernpräfix

  - Nationale/regionale und internationale Nummernformate

  - Nationale/regionale und internationale Wählregelgruppen

  - Zulässige nationale/regionale und internationale Wählregelgruppen

  - Wählregeleinträge

Zugriffsnummern, Nummernpräfixe und Nummernformate für einen UM-Wählplan können Sie auf der Seite **Kurzwahlnummern** im Exchange-Verwaltungskonsole (EAC) konfigurieren. Sie können auch die Einstellungen mit dem Cmdlet **Set-UMDialPlan** in der Exchange-Verwaltungsshell konfigurieren. Sie können wählen, ob Sie alle Einstellungen, keine der Einstellungen oder nur einige der Einstellungen konfigurieren möchten. Jede Einstellung steuert einen bestimmten Teil des Outdialing-Prozesses.

UM verwendet Zugriffscodes, Rufnummernpräfixe und Zahlenformate zur Ermittlung der richtigen zu wählenden Nummer. Sie können konfiguriert werden, um ausgehende Anrufer für Benutzer zu beschränken, die sich bei einer mit einem UM-Wählplan verknüpften automatischen UM-Telefonzentrale oder bei einer im Wählplan konfigurierten Outlook Voice Access-Nummer einwählen.

Weitere Informationen zum Outdialing in Unified Messaging finden Sie unter [Kurzwahlnummern, Rufnummernpräfixe und Nummernformate](dial-codes-number-prefixes-and-number-formats-exchange-2013-help.md).

Übersicht

## Amtskennziffer

Sie können eine Amtskennziffer, auch als *Amtsvorwahl* bezeichnet, für jeden Satz Wähleinstellungen konfigurieren, den Sie erstellen. Dies ist die Nummer, die für den Zugriff auf eine Amtsleitung verwendet wird. Diese Nummer ist auch für die PBX-Anlagen (Private Branch eXchange, Nebenstellenanlage) oder die IP-PBX-Anlagen in der Organisation konfiguriert. In den meisten Telefonienetzwerken wählen die Benutzer die Nummer "9", um auf eine Amtsleitung zuzugreifen und eine externe Telefonnummer anzurufen.

Für jeden von Ihnen erstellten Wählplan sollte eine Amtskennziffer konfiguriert werden. Diese Kurzwahlnummer gilt für alle Benutzer, denen eine UM-Postfachrichtlinie zugeordnet ist, die wiederum mit dem UM-Wählplan verknüpft ist. Tätigt ein mit dem Wählplan verknüpfter Anrufer einen Anruf und wählt der Wählplan für den ausgehenden Anruf, fügt UM den Zugriffscode der Amtsleitung (üblicherweise die 9) vor der gewählten Nummernfolge hinzu, damit die PBX- oder IP PBX-Anlage die Nummer richtig wählt. Konfigurieren Sie den Amtsleitungs-Zugriffscode nicht, erkennt die PBX- oder IP-PBX-Anlage die gesendete Nummer nicht. Wie bereits erwähnt, lautet der Zugriffscode, den die Benutzer wählen, um auf eine Amtsleitung zuzugreifen, in vielen Organisationen beispielsweise "9", und diese Nummer wird auch für die PBX- oder IP-PBX-Anlage konfiguriert. Unified Messaging muss der Telefonnummernzeichenfolge für die PBX- oder IP-PBX-Anlage die Nummer "9" hinzufügen, damit die externe Nummer ordnungsgemäß gewählt wird. Wenn Sie die Kurzwahlnummer so konfigurieren, dass Unified Messaging den Zugriffscode der Amtsleitung hinzufügt, kann Unified Messaging mit diesem Zugriffscode auf eine Amtsleitung zugreifen, bevor die externe Telefonnummernfolge gewählt wird. Die von Ihnen konfigurierte Kurzwahlnummer gilt für alle Benutzer, denen eine UM-Postfachrichtlinie zugeordnet ist, die wiederum mit dem UM-Wählplan verknüpft ist.

## Rufnummernpräfix, national

Das nationale Rufnummernpräfix und die Landes-/Regionskennzahl können ebenfalls in UM-Wähleinstellungen konfiguriert werden. Unified Messaging verwendet die zum Wählen des korrekten nationalen Rufnummernpräfixes bzw. der korrekten Landes-/Regionskennzahl eingegebene Nummer, wenn ein Benutzer eine externe Rufnummer innerhalb des gleichen Landes/der gleichen Region anruft oder wenn es sich um einen internationalen Anruf handelt. Wenn ein Benutzer beispielsweise einen internationalen Anruf von Nordamerika nach Europa tätigt, stellt UM das nationale Nummernpräfix der Rufnummernfolge voran, die an die PBX- oder IP-PBX-Anlage gesendet wird, damit der ausgehende Anruf getätigt wird. Die Nummer "1" wird als nationales Nummernpräfix für Nordamerika verwendet.

## Länder-/Regionszugriffscode

In einem UM-Wählplan kann ein Länder-/Regionszugriffscode konfiguriert werden. Der Länder-/Regionszugriffscode besteht aus den Ziffern, die einem bestimmten Land oder einer Region zugeordnet sind. Der Länder-/Regionszugriffscode wird von Unified Messaging verwendet, um die richtige Telefonnummer zu wählen, wenn eine Rufnummer innerhalb des gleichen Landes oder der gleichen Region angerufen wird. UM diese Nummer der Rufnummernfolge voran, die er an die PBX- oder IP-PBX-Anlage sendet, wenn ein externer Anruf getätigt wird. Beispielsweise fügt der UM die Nummer "1" hinzu, wenn innerhalb der Vereinigten Staaten eine Rufnummer gewählt wird. Der Länder-/Regionscode für Großbritannien lautet "44".

## Internationale VAZ

In den UM-Wähleinstellungen kann eine internationale VAZ konfiguriert werden. Die internationale VAZ setzt sich aus den Ziffern zusammen, die für den Zugriff auf internationale Telefonnummern verwendet werden. Der internationale Zugriffscode wird von Unified Messaging zum Wählen des richtigen internationalen Zugriffscode verwendet, wenn ein Anruf von einer Telefonnummer innerhalb eines Landes/einer Region getätigt wird, der angerufene Anschluss sich jedoch in einem anderen Land/einer anderen Region befindet. UM diese Nummer der Rufnummernfolge voran, die er an die PBX- oder IP-PBX-Anlage sendet, wenn ein externer Anruf getätigt wird. Beispielsweise verwendet UM die Nummer "011" als internationalen Zugriffscode für die Vereinigten Staaten. Für Europa lautet die internationale VAZ "00".

Übersicht

## Nationale/regionale und internationale Nummernformate

Sie können die Konfiguration für eingehende Anrufe für nationale/regionale und internationale Nummernformate in einem UM-Wählplan festlegen. Nach der Konfiguration dieser Einstellungen ist Unified Messaging in der Lage, aus dem Inland/der Region und aus dem Ausland zwischen UM-Wählplänen innerhalb einer Organisation eingehende Anrufe zu erkennen. Sie können auch Zahlenformate für eingehende Anrufe hinzufügen, die in einen einzelnen Wählplan eingefügt werden. Mit der Konfiguration dieser Optionen kann die Organisation Geld sparen, indem externe Anrufe verhindert werden, die die Benutzer nicht vom Arbeitsplatz aus tätigen dürfen. Außerdem tragen sie dazu bei, Betrug in Verbindung mit Telefongebühren zu vermeiden. UM verwendet die von Ihnen konfigurierten Informationen, um das Nummernformat des eingehenden Anrufs zu vergleichen und sicherzustellen, dass das Nummernmuster den Vorgaben entspricht, bevor der Anruf entgegengenommen wird. So können beispielsweise in einer Organisation mehrere Wählpläne vorhanden sein. Wenn Sie über einen Wählplan für die Vereinigten Staaten und einen weiteren für Großbritannien verfügen, möchten Sie möglicherweise dafür sorgen, dass die Benutzer im Wählplan für die Vereinigten Staaten über UM zwar Benutzer im Wählplan für Großbritannien anrufen können, jedoch keine direkten Anrufe zu Anschlüssen in anderen Ländern/Regionen oder von internationalen Anschlüssen tätigen können.


---
title: 'Registrieren von Filterpaket-IFiltern für Exchange 2013: Exchange 2013 Help'
TOCTitle: Registrieren von Filterpaket-IFiltern für Exchange 2013
ms:assetid: 0338980f-3a64-49d3-bc3c-bf6f10f88cb4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ837174(v=EXCHG.150)
ms:contentKeyID: 50554764
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Registrieren von Filterpaket-IFiltern für Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Transportregeln mit Bedingungen für die Anlagenprüfung extrahieren den Text bei der Analyse des Inhalts von Anlagen. Exchange 2013 verfügt über systemeigene Funktionen zum Überprüfen der am häufigsten verwendeten Anlagentypen. Weitere Anlagentypen können durch die Registrierung von IFiltern für Exchange 2013 aufgenommen werden. In diesem Thema wird gezeigt, wie die von Microsoft und Drittanbietern veröffentlichten IFilter registriert werden.

Nachdem Sie einen IFilter für einen bestimmten Dateityp registriert haben, können Transportregeln mit Bedingungen für die Anlagenprüfung diese Anlagen überprüfen. Infolgedessen lösen diese Dateitypen die Bedingung *AttachmentIsUnsupported* nicht mehr aus.


> [!WARNING]
> Zu den in diesem Thema aufgeführten Verfahren gehört das Ändern der Registrierung auf den Exchange-Servern. Eine fehlerhafte Bearbeitung der Registrierung kann zu schwerwiegenden Problemen führen, die eine Neuinstallation des Betriebssystems erforderlich machen kann. Durch fehlerhafte Bearbeitung der Registrierung verursachte Probleme können unter Umständen nicht mehr behoben werden. Sichern Sie alle wichtigen Daten, bevor Sie die Registrierung bearbeiten.<BR>Für diese Verfahren müssen Sie zudem den Microsoft Exchange-Transportdienst auf den Postfachservern beenden und neu starten.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Transportregeln finden Sie unter [Verwalten von Nachrichtenflussregeln](https://docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten pro Server.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Exchange Server-Konfigurationseinstellungen" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Sie müssen die folgenden Verfahren auf den Servern ausführen, auf denen die Exchange 2013-Postfachserverrolle bereits installiert ist. Wenn Sie weitere Postfachserver hinzufügen, nachdem Sie diese Verfahren ausgeführt haben, müssen Sie sie auf den neu bereitgestellten Servern erneut ausführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Registrieren von Microsoft Office 2010 Filter Pack

Standardmäßig werden die folgenden Office-Dateitypen von Exchange-Transportregeln nicht unterstützt:

  - Office OneNote

  - Office Publisher

Wenn Sie diese Dateien unterstützen möchten, müssen Sie Microsoft Office 2010 Filter Pack bereitstellen. Dieses Filter Pack wird beim Exchange 2013-Setup nicht bereitgestellt und ist keine Voraussetzung für die Bereitstellung.

## Bereitstellen von Microsoft Office 2010 Filter Pack

Das Bereitstellen von Office 2010 Filter Pack besteht aus zwei Hauptschritten:

  - Herunterladen und Installieren des Filter Pack, wodurch die IFilter in Windows (Suche) registriert werden.

  - Ändern der Registrierung, sodass die IFilter auch in Exchange 2013 registriert sind. Dadurch wird in Exchange das Überprüfen von Anlagen mit den Dateiformaten unterstützt.


> [!IMPORTANT]
> Sie müssen dieses Verfahren auf allen Postfachservern in Ihrer Organisation ausführen.



1.  Laden Sie Microsoft Office 2010 Filter Pack (`FilterPack64bit.exe`) aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=191548) herunter, und speichern Sie es.

2.  Führen Sie die Datei `FilterPack64bit.exe` auf dem Postfachserver aus, und folgen Sie den Anweisungen, um die Installation abzuschließen.

3.  Starten Sie den Registrierungs-Editor, und suchen Sie den folgenden Registrierungsunterschlüssel:
    
    ```powershell
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\HubTransportRole\CLSID
    ```

4.  Fügen Sie wie folgt unter **CLSID** einen Unterschlüssel für OneNote-Dateien hinzu:
    
    1.  Klicken Sie mit der rechten Maustaste auf **CLSID**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Schlüssel**.
    
    2.  Ändern Sie den Namen des neuen Schlüssels in `{B8D12492-CE0F-40AD-83EA-099A03D493F1}`.
    
    3.  Klicken Sie auf den soeben erstellten Schlüssel, und legen Sie den Wert **(Standard)** auf den Installationsort von Office 2010 Filter Pack fest. Standardmäßig wird das Filter Pack unter `C:\Program Files\Common Files\Microsoft Shared\Filters\ONIFilter.dll` installiert.
    
    4.  Klicken Sie mit der rechten Maustaste auf **{B8D12492-CE0F-40AD-83EA-099A03D493F1}**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Zeichenfolgenwert**.
    
    5.  Nennen Sie den neuen Zeichenfolgenwert `ThreadingModel`, und legen Sie ihn auf `Both` fest.

5.  Fügen Sie wie folgt unter **CLSID** einen Unterschlüssel für Publisher-Dateien hinzu:
    
    1.  Klicken Sie mit der rechten Maustaste auf **CLSID**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Schlüssel**.
    
    2.  Ändern Sie den Namen des neuen Schlüssels in `{A7FD8AC9-7ABF-46FC-B70B-6A5E5EC9859A}`.
    
    3.  Klicken Sie auf den soeben erstellten Schlüssel, und legen Sie den Wert **(Standard)** auf den Installationsort von Office 2010 Filter Pack fest. Standardmäßig wird das Filter Pack unter `C:\Program Files\Common Files\Microsoft Shared\Filters\PUBFILT.dll` installiert.
    
    4.  Klicken Sie mit der rechten Maustaste auf **{A7FD8AC9-7ABF-46FC-B70B-6A5E5EC9859A}**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Zeichenfolgenwert**.
    
    5.  Nennen Sie den neuen Zeichenfolgenwert `ThreadingModel`, und legen Sie ihn auf `Both` fest.

6.  Suchen Sie den folgenden Registrierungsschlüssel:
    
    ```powershell
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\HubTransportRole\filters
    ```

7.  Fügen Sie wie folgt unter **filters** einen Unterschlüssel für die Erweiterung ONE hinzu.
    
    1.  Klicken Sie mit der rechten Maustaste auf **filters**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Schlüssel**.
    
    2.  Ändern Sie den Namen des neuen Schlüssels in `.one`.
    
    3.  Klicken Sie auf den soeben erstellten Schlüssel, und legen Sie den Wert **(Standard)** auf `{B8D12492-CE0F-40AD-83EA-099A03D493F1}` fest.

8.  Fügen Sie wie folgt unter **filters** einen Unterschlüssel für die Erweiterung PUB hinzu:
    
    1.  Klicken Sie mit der rechten Maustaste auf **filters**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Schlüssel**.
    
    2.  Ändern Sie den Namen des neuen Schlüssels in `.pub`.
    
    3.  Klicken Sie auf den soeben erstellten Schlüssel, und legen Sie den Wert **(Standard)** auf `{A7FD8AC9-7ABF-46FC-B70B-6A5E5EC9859A}` fest.

9.  Schließen Sie den Registrierungs-Editor.

10. Beenden Sie auf dem Postfachserver die folgenden Dienste, und starten Sie sie dann neu. Gehen Sie dabei in der angegebenen Reihenfolge vor:
    
    1.  Beenden Sie den Microsoft Exchange-Transportdienst.
    
    2.  Beenden Sie den Microsoft-Filterverwaltungsdienst.
    
    3.  Starten Sie den Microsoft-Filterverwaltungsdienst.
    
    4.  Starten Sie den Microsoft Exchange-Transportdienst.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob Sie die IFilter von Microsoft Office 2010 Filter Pack erfolgreich registriert haben:

1.  Erstellen Sie eine Transportregel mit den folgenden Eigenschaften. Genaue Anweisungen zum Erstellen von Transportregeln finden Sie unter [Verwalten von Nachrichtenflussregeln](https://docs.microsoft.com/de-de/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).
    
      - Der Absender ist Ihr Postfach.
    
      - Inhalt mindestens einer Anlage enthält "Testen von IFiltern".
    
      - Generieren Sie einen Schadensbericht, und senden Sie ihn an Ihr Postfach.

2.  Erstellen Sie eine OneNote-Datei, die die Wendung "Testen von IFiltern" enthält, fügen Sie sie der neuen E-Mail an, und senden Sie sie an sich selbst.

3.  Überprüfen Sie, ob Sie den Schadensbericht einer Transportregel für die soeben erstellte Regel erhalten. Dadurch wird bestätigt, dass das Regelmodul den Inhalt der OneNote-Datei analysieren konnte.

4.  Wiederholen Sie die Schritte 2 und 3 mit einer Publisher-Datei.

## Registrieren der IFilter von Drittanbietern, um weitere Dateiformate zu unterstützen

Sie können die Funktion zur Überprüfung von Anlagen auf weitere Dateitypen erweitern, indem Sie IFilter von Drittanbietern registrieren. Die Unterstützung weiterer Dateien kann ergänzt werden, indem der IFilter für den Dateityp auf allen Postfachservern installiert und registriert wird.


> [!IMPORTANT]
> Microsoft hat IFilter von Drittanbietern nicht mit Transportregeln getestet. Deshalb empfehlen wir, IFilter von Drittanbietern in einer Testumgebung bereitzustellen und zu testen, bevor Sie sie in der Produktionsumgebung bereitstellen.



## Bereitstellen von Adobe PDF IFilter

In diesem Verfahren wird gezeigt, wie der [Adobe PDF IFilter](https://www.adobe.com/support/downloads/detail.jsp?ftpid=4025) bereitgestellt wird, um die Verarbeitung von PDF-Anlagen in Transportregeln zu unterstützen.


> [!NOTE]
> Standardmäßig unterstützt Exchange 2013 das Überprüfen von PDF-Dateien in Transportregeln. Mit diesem PDF-Beispiel soll nur veranschaulicht werden, wie Sie die Unterstützung für weitere Dateitypen mit IFiltern von Drittanbietern erweitern können.



1.  Laden Sie [Adobe PDF IFilter](https://www.adobe.com/support/downloads/detail.jsp?ftpid=4025) herunter, und befolgen Sie die Installationsanweisungen.

2.  Starten Sie den Registrierungs-Editor, und suchen Sie den folgenden Unterschlüssel:
    
    ```powershell
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\HubTransportRole\CLSID
    ```

3.  Fügen Sie wie folgt unter **CLSID** einen Unterschlüssel für PDF-Dateien hinzu:
    
    1.  Klicken Sie mit der rechten Maustaste auf **CLSID**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Schlüssel**.
    
    2.  Ändern Sie den Namen des neuen Schlüssels in `{E8978DA6-047F-4E3D-9C78-CDBE46041603}`.
        

        > [!NOTE]
        > Jeder IFilter verfügt über eine eindeutige Klassen-ID (CLSID). Sie finden die CLSID in der Installationsdokumentation für den IFilter, den Sie registrieren, oder indem Sie unter dem Schlüssel <CODE>HKEY_CLASSES_ROOT\CLSID</CODE> in der Registrierung nach der Dateierweiterung suchen.

    
    3.  Klicken Sie auf den soeben erstellten Schlüssel, und legen Sie den Wert **(Standard)** auf den PDF IFilter-Installationsort fest. Standardmäßig wird der PDF IFilter unter `C:\Program Files\Adobe\Adobe PDF IFilter 9 for 64-bit platforms\bin\PDFFilter.dll` installiert.

4.  Suchen Sie den folgenden Registrierungsschlüssel:
    
    ```powershell
    HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\HubTransportRole\filters
    ```

5.  Fügen Sie wie folgt unter **filters** einen Unterschlüssel für die Erweiterung PDF hinzu:
    
    1.  Klicken Sie mit der rechten Maustaste auf **filters**, zeigen Sie auf **Neu**, und klicken Sie dann auf **Schlüssel**.
    
    2.  Ändern Sie den Namen des neuen Schlüssels in `.pdf`.
    
    3.  Klicken Sie auf den soeben erstellten Schlüssel, und legen Sie den Wert **(Standard)** auf `{E8978DA6-047F-4E3D-9C78-CDBE46041603}` fest.

6.  Schließen Sie den Registrierungs-Editor.

7.  Beenden Sie auf dem Postfachserver die folgenden Dienste, und starten Sie sie dann neu. Gehen Sie dabei in der angegebenen Reihenfolge vor:
    
    1.  Beenden Sie den Microsoft Exchange-Transportdienst.
    
    2.  Beenden Sie den Microsoft-Filterverwaltungsdienst.
    
    3.  Starten Sie den Microsoft-Filterverwaltungsdienst.
    
    4.  Starten Sie den Microsoft Exchange-Transportdienst.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Verwenden Sie das Verfahren, das im Abschnitt Woher wissen Sie, dass dieses Verfahren erfolgreich war? weiter oben in diesem Thema angegeben ist. Ersetzen Sie dabei Publisher-Dateien durch Adobe PDF-Dateien.

## Weitere Informationen

[Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln](use-transport-rules-to-inspect-message-attachments-exchange-2013-help.md)

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)

[Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md)

[Transportregelaktionen](mail-flow-rule-actions-in-exchange-2013-exchange-2013-help.md)


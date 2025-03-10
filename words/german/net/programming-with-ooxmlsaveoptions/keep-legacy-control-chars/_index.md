---
title: Behalten Sie die alten Steuerzeichen bei
linktitle: Behalten Sie die alten Steuerzeichen bei
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET alte Steuerzeichen in Word-Dokumenten beibehalten.
weight: 10
url: /de/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Behalten Sie die alten Steuerzeichen bei

## Einführung

Haben Sie sich schon einmal über diese seltsamen, unsichtbaren Steuerzeichen in Ihren Word-Dokumenten gewundert? Sie sind wie kleine, versteckte Gremlins, die Formatierung und Funktionalität durcheinanderbringen können. Glücklicherweise bietet Aspose.Words für .NET eine praktische Funktion, um diese alten Steuerzeichen beim Speichern von Dokumenten intakt zu halten. In diesem Tutorial werden wir uns eingehend damit befassen, wie diese Steuerzeichen mit Aspose.Words für .NET verwaltet werden. Wir werden es Schritt für Schritt aufschlüsseln und sicherstellen, dass Sie dabei jedes Detail verstehen. Bereit, loszulegen? Lassen Sie uns eintauchen!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET: Herunterladen und installieren von[Hier](https://releases.aspose.com/words/net/).
2.  Eine gültige Aspose-Lizenz: Sie können eine temporäre Lizenz erhalten[Hier](https://purchase.aspose.com/temporary-license/).
3. Entwicklungsumgebung: Visual Studio oder jede andere IDE, die .NET unterstützt.
4. Grundkenntnisse in C#: Vertrautheit mit der Programmiersprache C# ist hilfreich.

## Namespaces importieren

Bevor Sie Ihren Code schreiben, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie oben in Ihrer C#-Datei die folgenden Zeilen hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Einrichten Ihres Projekts

Zuerst müssen Sie Ihr Projekt in Visual Studio (oder Ihrer bevorzugten IDE) einrichten. 

1. Erstellen Sie ein neues C#-Projekt: Öffnen Sie Visual Studio und erstellen Sie ein neues C#-Konsolenanwendungsprojekt.
2. Installieren Sie Aspose.Words für .NET: Verwenden Sie den NuGet Package Manager, um Aspose.Words für .NET zu installieren. Klicken Sie im Solution Explorer mit der rechten Maustaste auf Ihr Projekt, wählen Sie „NuGet-Pakete verwalten“, suchen Sie nach „Aspose.Words“ und installieren Sie es.

## Schritt 2: Laden Sie Ihr Dokument

Als Nächstes laden Sie das Word-Dokument, das die alten Steuerzeichen enthält.

1. Geben Sie den Dokumentpfad an: Legen Sie den Pfad zu Ihrem Dokumentverzeichnis fest.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2.  Laden Sie das Dokument: Verwenden Sie die`Document` Klasse, um Ihr Dokument zu laden.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Schritt 3: Speicheroptionen konfigurieren

Konfigurieren wir nun die Speicheroptionen so, dass die alten Steuerzeichen erhalten bleiben.

1.  Optionen zum Speichern erstellen: Initialisieren Sie eine Instanz von`OoxmlSaveOptions` und legen Sie die`KeepLegacyControlChars`Eigentum an`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Schritt 4: Speichern Sie das Dokument

Speichern Sie abschließend das Dokument mit den konfigurierten Speicheroptionen.

1.  Speichern Sie das Dokument: Verwenden Sie die`Save` Methode der`Document` Klasse, um das Dokument mit den angegebenen Speicheroptionen zu speichern.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie sicherstellen, dass Ihre alten Steuerzeichen beim Arbeiten mit Word-Dokumenten in Aspose.Words für .NET erhalten bleiben. Diese Funktion kann lebensrettend sein, insbesondere beim Umgang mit komplexen Dokumenten, bei denen Steuerzeichen eine entscheidende Rolle spielen. 

## Häufig gestellte Fragen

### Was sind Legacy-Steuerzeichen?

Legacy-Steuerzeichen sind nicht druckbare Zeichen, die in älteren Dokumenten zur Steuerung von Formatierung und Layout verwendet werden.

### Kann ich diese Steuerzeichen entfernen, anstatt sie beizubehalten?

Ja, Sie können Aspose.Words für .NET verwenden, um diese Zeichen bei Bedarf zu entfernen oder zu ersetzen.

### Ist diese Funktion in allen Versionen von Aspose.Words für .NET verfügbar?

Diese Funktion ist in den neuesten Versionen verfügbar. Stellen Sie sicher, dass Sie die neueste Version verwenden, um auf alle Funktionen zugreifen zu können.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?

 Ja, Sie benötigen eine gültige Lizenz. Sie können eine temporäre Lizenz zu Testzwecken erhalten[Hier](https://purchase.aspose.com/temporary-license/).

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?

 Eine ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

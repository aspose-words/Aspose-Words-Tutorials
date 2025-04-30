---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET alte Steuerzeichen in Word-Dokumenten beibehalten."
"linktitle": "Behalten Sie die alten Steuerzeichen bei"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Behalten Sie die alten Steuerzeichen bei"
"url": "/de/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Behalten Sie die alten Steuerzeichen bei

## Einführung

Haben Sie sich schon einmal über diese seltsamen, unsichtbaren Steuerzeichen in Ihren Word-Dokumenten gewundert? Sie sind wie winzige, versteckte Gremlins, die Formatierung und Funktionalität durcheinanderbringen können. Glücklicherweise bietet Aspose.Words für .NET eine praktische Funktion, um diese alten Steuerzeichen beim Speichern von Dokumenten zu erhalten. In diesem Tutorial erfahren Sie ausführlich, wie Sie diese Steuerzeichen mit Aspose.Words für .NET verwalten. Wir erklären es Schritt für Schritt, damit Sie jedes Detail verstehen. Bereit zum Start? Los geht’s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. Aspose.Words für .NET: Herunterladen und installieren von [Hier](https://releases.aspose.com/words/net/).
2. Eine gültige Aspose-Lizenz: Sie können eine temporäre Lizenz erhalten [Hier](https://purchase.aspose.com/temporary-license/).
3. Entwicklungsumgebung: Visual Studio oder eine andere IDE, die .NET unterstützt.
4. Grundkenntnisse in C#: Kenntnisse der Programmiersprache C# sind hilfreich.

## Namespaces importieren

Bevor Sie Ihren Code schreiben, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie die folgenden Zeilen oben in Ihre C#-Datei ein:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Einrichten Ihres Projekts

Zuerst müssen Sie Ihr Projekt in Visual Studio (oder Ihrer bevorzugten IDE) einrichten. 

1. Erstellen Sie ein neues C#-Projekt: Öffnen Sie Visual Studio und erstellen Sie ein neues C#-Konsolenanwendungsprojekt.
2. Installieren Sie Aspose.Words für .NET: Verwenden Sie den NuGet-Paketmanager, um Aspose.Words für .NET zu installieren. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, wählen Sie „NuGet-Pakete verwalten“, suchen Sie nach „Aspose.Words“ und installieren Sie es.

## Schritt 2: Laden Sie Ihr Dokument

Als Nächstes laden Sie das Word-Dokument, das die alten Steuerzeichen enthält.

1. Geben Sie den Dokumentpfad an: Legen Sie den Pfad zu Ihrem Dokumentverzeichnis fest.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. Laden Sie das Dokument: Verwenden Sie die `Document` Klasse, um Ihr Dokument zu laden.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Schritt 3: Speicheroptionen konfigurieren

Konfigurieren wir nun die Speicheroptionen, um die alten Steuerzeichen beizubehalten.

1. Optionen zum Speichern erstellen: Initialisieren Sie eine Instanz von `OoxmlSaveOptions` und legen Sie die `KeepLegacyControlChars` Eigentum zu `true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Schritt 4: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend mit den konfigurierten Speicheroptionen.

1. Speichern Sie das Dokument: Verwenden Sie die `Save` Methode der `Document` Klasse, um das Dokument mit den angegebenen Speicheroptionen zu speichern.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Abschluss

Und da haben Sie es! Mit diesen Schritten können Sie sicherstellen, dass Ihre alten Steuerzeichen bei der Arbeit mit Word-Dokumenten in Aspose.Words für .NET erhalten bleiben. Diese Funktion kann lebensrettend sein, insbesondere bei komplexen Dokumenten, bei denen Steuerzeichen eine entscheidende Rolle spielen. 

## Häufig gestellte Fragen

### Was sind Legacy-Steuerzeichen?

Legacy-Steuerzeichen sind nicht druckbare Zeichen, die in älteren Dokumenten zur Steuerung der Formatierung und des Layouts verwendet werden.

### Kann ich diese Steuerzeichen entfernen, anstatt sie beizubehalten?

Ja, Sie können Aspose.Words für .NET verwenden, um diese Zeichen bei Bedarf zu entfernen oder zu ersetzen.

### Ist diese Funktion in allen Versionen von Aspose.Words für .NET verfügbar?

Diese Funktion ist in aktuellen Versionen verfügbar. Verwenden Sie die neueste Version, um alle Funktionen nutzen zu können.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?

Ja, Sie benötigen eine gültige Lizenz. Sie können eine temporäre Lizenz zu Testzwecken erhalten. [Hier](https://purchase.aspose.com/temporary-license/).

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?

Eine ausführliche Dokumentation finden Sie [Hier](https://reference.aspose.com/words/net/).
 


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
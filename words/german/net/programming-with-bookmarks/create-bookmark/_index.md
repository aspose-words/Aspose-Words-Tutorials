---
"description": "Erfahren Sie in dieser detaillierten Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Lesezeichen in Word-Dokumenten erstellen. Perfekt für die Dokumentennavigation und -organisation."
"linktitle": "Lesezeichen im Word-Dokument erstellen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Lesezeichen im Word-Dokument erstellen"
"url": "/de/net/programming-with-bookmarks/create-bookmark/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lesezeichen im Word-Dokument erstellen

## Einführung

Das Erstellen von Lesezeichen in einem Word-Dokument kann entscheidend sein, insbesondere wenn Sie mühelos durch große Dokumente navigieren möchten. Heute zeigen wir Ihnen, wie Sie Lesezeichen mit Aspose.Words für .NET erstellen. Dieses Tutorial führt Sie Schritt für Schritt durch die einzelnen Schritte und stellt sicher, dass Sie jeden Teil des Prozesses verstehen. Also, los geht‘s!

## Voraussetzungen

Bevor wir beginnen, benötigen Sie Folgendes:

1. Aspose.Words für .NET-Bibliothek: Herunterladen und installieren von [Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung.
3. Grundkenntnisse in C#: Verständnis der grundlegenden C#-Programmierkonzepte.

## Namespaces importieren

Um mit Aspose.Words für .NET zu arbeiten, müssen Sie die erforderlichen Namespaces importieren:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Einrichten des Dokuments und des DocumentBuilders

Initialisieren des Dokuments

Zuerst müssen wir ein neues Dokument erstellen und das `DocumentBuilder`Dies ist der Ausgangspunkt für das Hinzufügen von Inhalten und Lesezeichen zu Ihrem Dokument.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Erklärung: Die `Document` Objekt ist Ihre Leinwand. Die `DocumentBuilder` ist wie Ihr Stift, mit dem Sie Inhalte schreiben und Lesezeichen im Dokument erstellen können.

## Schritt 2: Erstellen Sie das Hauptlesezeichen

Starten und Beenden des Hauptlesezeichens

Um ein Lesezeichen zu erstellen, müssen Sie Start- und Endpunkt angeben. Hier erstellen wir ein Lesezeichen mit dem Namen „Mein Lesezeichen“.

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

Erklärung: Die `StartBookmark` Methode markiert den Anfang des Lesezeichens und `Writeln` fügt Text innerhalb des Lesezeichens hinzu.

## Schritt 3: Erstellen Sie ein verschachteltes Lesezeichen

Verschachteltes Lesezeichen innerhalb des Hauptlesezeichens hinzufügen

Sie können Lesezeichen in andere Lesezeichen einbetten. Hier fügen wir „Verschachteltes Lesezeichen“ in „Meine Lesezeichen“ ein.

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

Erläuterung: Das Verschachteln von Lesezeichen ermöglicht eine strukturiertere und hierarchischere Organisation der Inhalte. Die `EndBookmark` Methode schließt das aktuelle Lesezeichen.

## Schritt 4: Text außerhalb des verschachtelten Lesezeichens hinzufügen

Weitere Inhalte hinzufügen

Nach dem verschachtelten Lesezeichen können wir innerhalb des Hauptlesezeichens weitere Inhalte hinzufügen.

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

Erklärung: Dadurch wird sichergestellt, dass das Hauptlesezeichen sowohl das verschachtelte Lesezeichen als auch zusätzlichen Text umfasst.

## Schritt 5: PDF-Speicheroptionen konfigurieren

PDF-Speicheroptionen für Lesezeichen einrichten

Beim Speichern des Dokuments als PDF können wir Optionen zum Einschließen von Lesezeichen konfigurieren.

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

Erklärung: Die `PdfSaveOptions` Mit der Klasse können Sie festlegen, wie das Dokument als PDF gespeichert werden soll. Die `BookmarksOutlineLevels` Die Eigenschaft definiert die Hierarchie der Lesezeichen im PDF.

## Schritt 6: Speichern Sie das Dokument

Speichern Sie das Dokument als PDF

Speichern Sie das Dokument abschließend mit den angegebenen Optionen.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

Erklärung: Die `Save` Die Methode speichert das Dokument im angegebenen Format und am angegebenen Speicherort. Die PDF-Datei enthält nun die von uns erstellten Lesezeichen.

## Abschluss

Das Erstellen von Lesezeichen in einem Word-Dokument mit Aspose.Words für .NET ist unkompliziert und äußerst nützlich für die Dokumentennavigation und -organisation. Ob Sie Berichte erstellen, E-Books erstellen oder große Dokumente verwalten – Lesezeichen erleichtern Ihnen das Leben. Folgen Sie den Schritten in diesem Tutorial, und Sie haben im Handumdrehen ein mit Lesezeichen versehenes PDF.

## Häufig gestellte Fragen

### Kann ich mehrere Lesezeichen auf unterschiedlichen Ebenen erstellen?

Auf jeden Fall! Sie können beliebig viele Lesezeichen anlegen und deren Hierarchieebenen beim Speichern des Dokuments als PDF definieren.

### Wie aktualisiere ich den Text eines Lesezeichens?

Sie können zum Lesezeichen navigieren mit `DocumentBuilder.MoveToBookmark` und aktualisieren Sie dann den Text.

### Ist es möglich, ein Lesezeichen zu löschen?

Ja, Sie können ein Lesezeichen löschen, indem Sie `Bookmarks.Remove` Methode, indem Sie den Namen des Lesezeichens angeben.

### Kann ich Lesezeichen in anderen Formaten als PDF erstellen?

Ja, Aspose.Words unterstützt Lesezeichen in verschiedenen Formaten, einschließlich DOCX, HTML und EPUB.

### Wie kann ich sicherstellen, dass die Lesezeichen im PDF korrekt angezeigt werden?

Definieren Sie unbedingt die `BookmarksOutlineLevels` richtig in der `PdfSaveOptions`Dadurch wird sichergestellt, dass die Lesezeichen in die Gliederung der PDF-Datei aufgenommen werden.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
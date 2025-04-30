---
"description": "Konvertieren Sie Word-Dokumente mit Aspose.Words für .NET in Markdown mit korrekter Tabellenausrichtung. Folgen Sie unserer ausführlichen Anleitung für perfekte Ergebnisse."
"linktitle": "Bilderordner festlegen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Bilderordner festlegen"
"url": "/de/net/programming-with-markdownsaveoptions/set-images-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bilderordner festlegen

## Einführung

Wollten Sie schon immer Ihr Word-Dokument in Markdown exportieren und dabei sicherstellen, dass Tabellen und Inhalte perfekt ausgerichtet sind? Aspose.Words für .NET ist die perfekte Lösung für diese Aufgabe. In diesem Artikel führen wir Sie durch die Einrichtung von Aspose.Words, die Vorbereitung Ihres Dokuments und den Export in Markdown mit korrekt ausgerichteten Tabelleninhalten. Wir erklären jeden Schritt, damit er leicht nachvollziehbar und verständlich ist. Legen wir also los und verwandeln Sie Ihre Word-Dokumente in perfekt ausgerichtete Markdown-Dateien!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Aspose.Words für .NET: Sie können es herunterladen [Hier](https://releases.aspose.com/words/net/).
- Eine gültige Lizenz: Erhalten Sie eine kostenlose Testversion [Hier](https://releases.aspose.com/) oder eine vorläufige Lizenz [Hier](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Oder jede andere IDE, die die .NET-Entwicklung unterstützt.
- Grundkenntnisse in C#: Verständnis der Programmiersprache C#.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Diese Namespaces ermöglichen Ihnen den Zugriff auf die Aspose.Words-Funktionalität.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## Schritt 1: Richten Sie Ihr Projekt ein

Richten Sie zunächst Ihr .NET-Projekt in Ihrer IDE ein. Erstellen Sie eine neue Konsolenanwendung und fügen Sie einen Verweis auf Aspose.Words für .NET hinzu.

### 1.1 Neues Projekt erstellen

Öffnen Sie Visual Studio und erstellen Sie ein neues Konsolenanwendungsprojekt. Nennen Sie es „MarkdownExporter“ oder ähnlich.

### 1.2 Aspose.Words-Referenz hinzufügen

Um Aspose.Words zu Ihrem Projekt hinzuzufügen, können Sie die DLL entweder von der [Aspose-Website](https://releases.aspose.com/words/net/) und fügen Sie es manuell hinzu oder verwenden Sie den NuGet-Paket-Manager:

```bash
Install-Package Aspose.Words
```

## Schritt 2: Schreiben Sie den Code zum Exportieren als Markdown

Schreiben wir nun den Code zum Lesen des Word-Dokuments und speichern es als Markdown-Datei mit der richtigen Tabellenausrichtung.

### 2.1 Definieren Sie den Pfad zu Ihrem Dokument

Legen Sie den Pfad zu Ihrem Word-Dokument und den Ordner fest, in dem Sie Bilder speichern möchten.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 Laden Sie das Dokument

Laden Sie Ihr Word-Dokument mit Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 Markdown-Speicheroptionen konfigurieren

Konfigurieren Sie die `MarkdownSaveOptions` um anzugeben, wo Bilder gespeichert werden sollen.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Speichern Sie das Dokument als Markdown

Verwenden Sie ein `MemoryStream` um das Dokument im Markdown-Format zu speichern.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Abschluss

Der Export eines Word-Dokuments nach Markdown mit Tabelleninhaltsausrichtung mit Aspose.Words für .NET ist mit diesen Schritten ganz einfach. Mit wenigen Codezeilen automatisieren Sie den Konvertierungsprozess und stellen sicher, dass Ihr Inhalt korrekt formatiert ist. Jetzt können Sie Ihre Dokumente problemlos im Markdown-Format freigeben und sich darauf verlassen, dass sie gut aussehen und ihre Struktur beibehalten.

## Häufig gestellte Fragen

### Kann ich Aspose.Words für .NET mit anderen Programmiersprachen verwenden?

Ja, Aspose.Words für .NET kann mit jeder .NET-kompatiblen Sprache wie VB.NET, F# und mehr verwendet werden.

### Wie erhalte ich eine temporäre Lizenz für Aspose.Words?

Sie können eine vorübergehende Lizenz erhalten [Hier](https://purchase.aspose.com/temporary-license/).

### Welche Dokumenttypen kann ich in Markdown konvertieren?

Sie können verschiedene Word-Dokumente konvertieren, darunter .doc, .docx, .rtf und mehr.

### Gibt es Einschränkungen in der Testversion von Aspose.Words?

Die Testversion hat einige Einschränkungen, wie z. B. Wasserzeichen in den Ausgabedateien. Sie können eine kostenlose Testversion erhalten [Hier](https://releases.aspose.com/).

### Wo finde ich weitere Beispiele und Dokumentation für Aspose.Words?

Eine ausführliche Dokumentation und Beispiele finden Sie auf der [Aspose-Website](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
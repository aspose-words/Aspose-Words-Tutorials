---
title: Bilderordner festlegen
linktitle: Bilderordner festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Konvertieren Sie Word-Dokumente mit der richtigen Tabellenausrichtung in Markdown mit Aspose.Words für .NET. Folgen Sie unserer ausführlichen Anleitung für perfekte Ergebnisse.
weight: 10
url: /de/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bilderordner festlegen

## Einführung

Wollten Sie schon immer Ihr Word-Dokument in das Markdown-Format exportieren und dabei sicherstellen, dass Tabellen und Inhalt perfekt ausgerichtet sind? Aspose.Words für .NET ist Ihre Lösung für diese Aufgabe. In diesem Artikel führen wir Sie durch den Prozess der Einrichtung von Aspose.Words, der Vorbereitung Ihres Dokuments und des Exports in Markdown mit korrekt ausgerichtetem Tabelleninhalt. Wir werden jeden Schritt aufschlüsseln, damit er leicht nachvollziehbar und verständlich ist. Lassen Sie uns also loslegen und Ihre Word-Dokumente in schön ausgerichtete Markdown-Dateien umwandeln!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.Words für .NET: Sie können es herunterladen[Hier](https://releases.aspose.com/words/net/).
-  Eine gültige Lizenz: Erhalten Sie eine kostenlose Testversion[Hier](https://releases.aspose.com/) oder eine temporäre Lizenz[Hier](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Oder jede andere IDE, die .NET-Entwicklung unterstützt.
- Grundkenntnisse in C#: Verständnis der Programmiersprache C#.

## Namespaces importieren

Zu Beginn müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Diese Namespaces ermöglichen Ihnen den Zugriff auf die Aspose.Words-Funktionalität.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## Schritt 1: Richten Sie Ihr Projekt ein

Als Erstes richten Sie Ihr .NET-Projekt in Ihrer IDE ein. Erstellen Sie eine neue Konsolenanwendung und fügen Sie einen Verweis auf Aspose.Words für .NET hinzu.

### 1.1 Neues Projekt erstellen

Öffnen Sie Visual Studio und erstellen Sie ein neues Konsolenanwendungsprojekt. Nennen Sie es „MarkdownExporter“ oder etwas Ähnliches.

### 1.2 Aspose.Words-Referenz hinzufügen

 Um Aspose.Words zu Ihrem Projekt hinzuzufügen, können Sie die DLL entweder von der[Aspose-Website](https://releases.aspose.com/words/net/) und fügen Sie es manuell hinzu oder verwenden Sie den NuGet-Paket-Manager:

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

### 2.2 Dokument laden

Laden Sie Ihr Word-Dokument mit Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 Markdown-Speicheroptionen konfigurieren

 Konfigurieren Sie die`MarkdownSaveOptions` um anzugeben, wo Bilder gespeichert werden sollen.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Speichern Sie das Dokument als Markdown

 Verwenden Sie ein`MemoryStream` um das Dokument im Markdown-Format zu speichern.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Abschluss

Wenn Sie diese Schritte befolgen, ist das Exportieren eines Word-Dokuments nach Markdown mit Ausrichtung des Tabelleninhalts mithilfe von Aspose.Words für .NET ganz einfach. Mit ein paar Zeilen Code können Sie den Konvertierungsprozess automatisieren und sicherstellen, dass Ihr Inhalt gut formatiert ist. Jetzt können Sie Ihre Dokumente ganz einfach im Markdown-Format freigeben und dabei sicher sein, dass sie gut aussehen und ihre Struktur beibehalten.

## Häufig gestellte Fragen

### Kann ich Aspose.Words für .NET mit anderen Programmiersprachen verwenden?

Ja, Aspose.Words für .NET kann mit jeder .NET-kompatiblen Sprache wie VB.NET, F# und mehr verwendet werden.

### Wie erhalte ich eine temporäre Lizenz für Aspose.Words?

Sie können eine temporäre Lizenz erhalten[Hier](https://purchase.aspose.com/temporary-license/).

### Welche Dokumenttypen kann ich in Markdown konvertieren?

Sie können verschiedene Word-Dokumente konvertieren, darunter .doc, .docx, .rtf und mehr.

### Gibt es irgendwelche Einschränkungen bei der Testversion von Aspose.Words?

Die Testversion hat einige Einschränkungen, wie z. B. Wasserzeichen in den Ausgabedateien. Sie können eine kostenlose Testversion erhalten[Hier](https://releases.aspose.com/).

### Wo finde ich weitere Beispiele und Dokumentation für Aspose.Words?

 Eine ausführliche Dokumentation und Beispiele finden Sie auf der[Aspose-Website](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

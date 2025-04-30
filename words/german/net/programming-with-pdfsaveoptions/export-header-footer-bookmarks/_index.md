---
"description": "Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Kopf- und Fußzeilenlesezeichen aus einem Word-Dokument in PDF exportieren."
"linktitle": "Kopf- und Fußzeilenlesezeichen eines Word-Dokuments in ein PDF-Dokument exportieren"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Kopf- und Fußzeilenlesezeichen eines Word-Dokuments in ein PDF-Dokument exportieren"
"url": "/de/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kopf- und Fußzeilenlesezeichen eines Word-Dokuments in ein PDF-Dokument exportieren

## Einführung

Das Konvertieren von Word-Dokumenten in PDF ist eine häufige Aufgabe, insbesondere wenn Sie Dokumente unter Beibehaltung ihrer Formatierung teilen oder archivieren möchten. Manchmal enthalten diese Dokumente wichtige Lesezeichen in den Kopf- und Fußzeilen. In diesem Tutorial zeigen wir Ihnen Schritt für Schritt, wie Sie diese Lesezeichen mit Aspose.Words für .NET aus einem Word-Dokument in ein PDF exportieren.

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes haben:

- Aspose.Words für .NET: Sie müssen Aspose.Words für .NET installiert haben. Sie können es herunterladen von [Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Richten Sie Ihre Entwicklungsumgebung ein. Sie können Visual Studio oder eine andere .NET-kompatible IDE verwenden.
- Grundkenntnisse in C#: Um den Codebeispielen folgen zu können, sind Kenntnisse in der C#-Programmierung erforderlich.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Fügen Sie diese Zeilen oben in Ihre Codedatei ein:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Prozess in leicht verständliche Schritte unterteilen.

## Schritt 1: Initialisieren des Dokuments

Der erste Schritt besteht darin, Ihr Word-Dokument zu laden. So geht's:

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

In diesem Schritt geben Sie lediglich den Pfad zu Ihrem Dokumentverzeichnis an und laden das Word-Dokument.

## Schritt 2: PDF-Speicheroptionen konfigurieren

Als nächstes müssen Sie die PDF-Speicheroptionen konfigurieren, um sicherzustellen, dass Lesezeichen in den Kopf- und Fußzeilen korrekt exportiert werden.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

Hier richten wir die `PdfSaveOptions`. Der `DefaultBookmarksOutlineLevel` Eigenschaft legt die Gliederungsebene für Lesezeichen fest, und die `HeaderFooterBookmarksExportMode` Die Eigenschaft stellt sicher, dass nur das erste Vorkommen von Lesezeichen in Kopf- und Fußzeilen exportiert wird.

## Schritt 3: Speichern Sie das Dokument als PDF

Speichern Sie Ihr Dokument abschließend mit den konfigurierten Optionen als PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

In diesem Schritt speichern Sie das Dokument mit den von Ihnen konfigurierten Optionen im angegebenen Pfad.

## Abschluss

Und fertig! Mit diesen Schritten können Sie Lesezeichen aus den Kopf- und Fußzeilen eines Word-Dokuments mit Aspose.Words für .NET ganz einfach in ein PDF exportieren. Diese Methode stellt sicher, dass wichtige Navigationshilfen im PDF-Format erhalten bleiben und Lesern die Navigation erleichtert wird.

## Häufig gestellte Fragen

### Kann ich alle Lesezeichen aus dem Word-Dokument in PDF exportieren?

Ja, das können Sie. Im `PdfSaveOptions`, können Sie die Einstellungen anpassen, um bei Bedarf alle Lesezeichen einzuschließen.

### Was ist, wenn ich auch Lesezeichen aus dem Hauptteil des Dokuments exportieren möchte?

Sie können die `OutlIneOptions` in `PdfSaveOptions` um Lesezeichen aus dem Hauptteil des Dokuments einzuschließen.

### Ist es möglich, die Lesezeichenebenen im PDF anzupassen?

Absolut! Sie können die `DefaultBookmarksOutlineLevel` -Eigenschaft, um verschiedene Gliederungsebenen für Ihre Lesezeichen festzulegen.

### Wie gehe ich mit Dokumenten ohne Lesezeichen um?

Wenn Ihr Dokument keine Lesezeichen enthält, wird die PDF-Datei ohne Lesezeichenstruktur erstellt. Stellen Sie sicher, dass Ihr Dokument Lesezeichen enthält, wenn Sie diese in der PDF-Datei benötigen.

### Kann ich diese Methode für andere Dokumenttypen wie DOCX oder RTF verwenden?

Ja, Aspose.Words für .NET unterstützt verschiedene Dokumenttypen, darunter DOCX, RTF und andere.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
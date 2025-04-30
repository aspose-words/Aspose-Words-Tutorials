---
"description": "Reduzieren Sie die Größe von PDF-Dokumenten durch Downsampling von Bildern mit Aspose.Words für .NET. Optimieren Sie Ihre PDFs für schnellere Upload- und Download-Zeiten."
"linktitle": "Reduzieren Sie die Größe von PDF-Dokumenten durch Downsampling von Bildern"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Reduzieren Sie die Größe von PDF-Dokumenten durch Downsampling von Bildern"
"url": "/de/net/programming-with-pdfsaveoptions/downsampling-images/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reduzieren Sie die Größe von PDF-Dokumenten durch Downsampling von Bildern

## Einführung

PDFs sind ein fester Bestandteil der digitalen Welt und werden für alles verwendet, vom Teilen von Dokumenten bis zum Erstellen von E-Books. Ihre Größe kann jedoch manchmal eine Hürde darstellen, insbesondere bei bildreichen Inhalten. Hier kommt das Downsampling von Bildern ins Spiel. Durch die Reduzierung der Bildauflösung im PDF können Sie die Dateigröße deutlich reduzieren, ohne die Qualität zu sehr zu beeinträchtigen. In diesem Tutorial erklären wir die Schritte dazu mit Aspose.Words für .NET.

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass die Aspose.Words-Bibliothek installiert ist. Falls nicht, können Sie sie herunterladen. [Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Jede .NET-Entwicklungsumgebung wie Visual Studio.
3. Grundkenntnisse in C#: Kenntnisse der Grundlagen der C#-Programmierung sind hilfreich.
4. Ein Beispieldokument: Ein Word-Dokument (zB `Rendering.docx`) mit Bildern zum Konvertieren in PDF.

## Namespaces importieren

Zuerst müssen Sie die erforderlichen Namespaces importieren. Fügen Sie diese oben in Ihre Codedatei ein:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Prozess nun in überschaubare Schritte unterteilen.

## Schritt 1: Laden Sie das Dokument

Im ersten Schritt laden Sie Ihr Word-Dokument. Hier geben Sie den Pfad zu Ihrem Dokumentverzeichnis an.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

In diesem Schritt laden wir das Word-Dokument aus dem angegebenen Verzeichnis. Ersetzen Sie `"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem sich Ihr Dokument befindet.

## Schritt 2: Downsampling-Optionen konfigurieren

Als nächstes müssen wir die Downsampling-Optionen konfigurieren. Dazu müssen wir die Auflösung und den Auflösungsschwellenwert für die Bilder festlegen.

```csharp
// Wir können einen Mindestschwellenwert für das Downsampling festlegen.
// Dieser Wert verhindert, dass das zweite Bild im Eingabedokument herunterskaliert wird.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

Hier erstellen wir eine neue Instanz von `PdfSaveOptions` und Festlegen der `Resolution` bis 36 DPI und die `ResolutionThreshold` auf 128 DPI. Das bedeutet, dass jedes Bild mit einer Auflösung über 128 DPI auf 36 DPI heruntergerechnet wird.

## Schritt 3: Speichern Sie das Dokument als PDF

Abschließend speichern wir das Dokument mit den konfigurierten Optionen als PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

In diesem letzten Schritt speichern wir das Dokument als PDF im selben Verzeichnis mit den angegebenen Downsampling-Optionen.

## Abschluss

Und da haben Sie es! Sie haben die Größe Ihrer PDF-Datei erfolgreich reduziert, indem Sie Bilder mit Aspose.Words für .NET herunterskaliert haben. Dies macht Ihre PDFs nicht nur übersichtlicher, sondern sorgt auch für schnellere Uploads und Downloads sowie ein flüssigeres Anzeigeerlebnis.

## Häufig gestellte Fragen

### Was ist Downsampling?
Beim Downsampling wird die Auflösung von Bildern reduziert, wodurch die Dateigröße von Dokumenten, die diese Bilder enthalten, verringert wird.

### Beeinträchtigt das Downsampling die Bildqualität?
Ja, Downsampling reduziert die Bildqualität. Die Auswirkung hängt jedoch vom Grad der Auflösungsreduzierung ab. Es handelt sich um einen Kompromiss zwischen Dateigröße und Bildqualität.

### Kann ich auswählen, welche Bilder heruntergerechnet werden sollen?
Ja, durch die Einstellung der `ResolutionThreshold`können Sie steuern, welche Bilder basierend auf ihrer Originalauflösung herunterskaliert werden.

### Was ist die ideale Auflösung für das Downsampling?
Die ideale Auflösung hängt von Ihren spezifischen Anforderungen ab. Üblicherweise werden 72 DPI für Webbilder verwendet, während höhere Auflösungen für die Druckqualität verwendet werden.

### Ist Aspose.Words für .NET kostenlos?
Aspose.Words für .NET ist ein kommerzielles Produkt, aber Sie können eine kostenlose Testversion herunterladen [Hier](https://releases.aspose.com/) oder bewerben Sie sich für eine [vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
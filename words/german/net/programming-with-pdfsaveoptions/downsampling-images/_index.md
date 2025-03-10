---
title: Reduzieren Sie die Größe von PDF-Dokumenten durch Downsampling von Bildern
linktitle: Reduzieren Sie die Größe von PDF-Dokumenten durch Downsampling von Bildern
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Reduzieren Sie die Größe von PDF-Dokumenten, indem Sie Bilder mit Aspose.Words für .NET herunterskalieren. Optimieren Sie Ihre PDFs für schnellere Upload- und Downloadzeiten.
weight: 10
url: /de/net/programming-with-pdfsaveoptions/downsampling-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Reduzieren Sie die Größe von PDF-Dokumenten durch Downsampling von Bildern

## Einführung

PDFs sind ein Grundnahrungsmittel in der digitalen Welt und werden für alles verwendet, vom Teilen von Dokumenten bis zum Erstellen von E-Books. Ihre Größe kann jedoch manchmal ein Hindernis darstellen, insbesondere bei bildreichen Inhalten. Hier kommt das Downsampling von Bildern ins Spiel. Indem Sie die Auflösung der Bilder im PDF reduzieren, können Sie die Dateigröße erheblich verringern, ohne zu große Kompromisse bei der Qualität einzugehen. In diesem Tutorial führen wir Sie durch die Schritte, um dies mit Aspose.Words für .NET zu erreichen.

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Aspose.Words-Bibliothek installiert haben. Wenn nicht, können Sie sie herunterladen[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Jede .NET-Entwicklungsumgebung wie Visual Studio.
3. Grundkenntnisse in C#: Kenntnisse der Grundlagen der C#-Programmierung sind hilfreich.
4.  Ein Beispieldokument: Ein Word-Dokument (z. B.`Rendering.docx`) mit Bildern zum Konvertieren in PDF.

## Namespaces importieren

Als Erstes müssen Sie die erforderlichen Namespaces importieren. Fügen Sie diese oben in Ihrer Codedatei hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Prozess nun in überschaubare Schritte unterteilen.

## Schritt 1: Dokument laden

Im ersten Schritt laden Sie Ihr Word-Dokument. Hier geben Sie den Pfad zu Ihrem Dokumentverzeichnis an.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

In diesem Schritt laden wir das Word-Dokument aus dem angegebenen Verzeichnis. Achten Sie darauf,`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem sich Ihr Dokument befindet.

## Schritt 2: Downsampling-Optionen konfigurieren

Als nächstes müssen wir die Downsampling-Optionen konfigurieren. Dazu gehört das Einstellen der Auflösung und der Auflösungsschwelle für die Bilder.

```csharp
// Wir können einen Mindestschwellenwert für das Downsampling festlegen.
// Dieser Wert verhindert, dass das zweite Bild im Eingabedokument herunterskaliert wird.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

 Hier erstellen wir eine neue Instanz von`PdfSaveOptions` und Festlegen der`Resolution` bis zu 36 DPI und die`ResolutionThreshold` auf 128 DPI. Das bedeutet, dass jedes Bild mit einer Auflösung über 128 DPI auf 36 DPI heruntergerechnet wird.

## Schritt 3: Speichern Sie das Dokument als PDF

Abschließend speichern wir das Dokument mit den konfigurierten Optionen als PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

In diesem letzten Schritt speichern wir das Dokument als PDF im selben Verzeichnis mit den angegebenen Downsampling-Optionen.

## Abschluss

Und da haben Sie es! Sie haben die Größe Ihrer PDF-Datei erfolgreich reduziert, indem Sie Bilder mit Aspose.Words für .NET herunterskaliert haben. Dadurch werden Ihre PDF-Dateien nicht nur übersichtlicher, sondern auch schnellere Uploads und Downloads sowie ein flüssigeres Anzeigeerlebnis ermöglicht.

## Häufig gestellte Fragen

### Was ist Downsampling?
Beim Downsampling wird die Auflösung von Bildern verringert, wodurch die Dateigröße der Dokumente, die diese Bilder enthalten, verringert wird.

### Wird die Bildqualität durch Downsampling beeinträchtigt?
Ja, durch Downsampling verringert sich die Bildqualität. Die Auswirkung hängt jedoch vom Grad der Auflösungsreduzierung ab. Es handelt sich um einen Kompromiss zwischen Dateigröße und Bildqualität.

### Kann ich auswählen, welche Bilder herunterskaliert werden sollen?
 Ja, durch die Einstellung der`ResolutionThreshold`können Sie steuern, welche Bilder basierend auf ihrer Originalauflösung herunterskaliert werden.

### Was ist die ideale Auflösung für Downsampling?
Die ideale Auflösung hängt von Ihren spezifischen Anforderungen ab. Normalerweise werden 72 DPI für Webbilder verwendet, während höhere Auflösungen für die Druckqualität verwendet werden.

### Ist Aspose.Words für .NET kostenlos?
 Aspose.Words für .NET ist ein kommerzielles Produkt, aber Sie können eine kostenlose Testversion herunterladen[Hier](https://releases.aspose.com/) oder bewerben Sie sich für eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

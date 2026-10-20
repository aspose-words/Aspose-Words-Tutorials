---
category: general
date: 2026-06-02
description: Wie man ein PDF aus einer DOCX mit Aspose.Words speichert, Formen als
  Inline‑Span‑Tags exportiert und Word in wenigen Schritten in PDF konvertiert.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: de
og_description: Wie man ein PDF aus einem Word‑Dokument mit Aspose.Words speichert,
  indem schwebende Formen als Inline‑Span‑Tags exportiert werden, um ein sauberes
  Word‑zu‑PDF‑Ergebnis zu erhalten.
og_title: Wie man ein PDF aus Word speichert – Inline‑Shape‑Export‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Wie man PDF aus Word mit Inline-Shape-Export speichert – Komplettanleitung
url: /de/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man PDF aus Word mit Inline-Shape-Export speichert – Vollständige Anleitung

Haben Sie sich jemals gefragt, **wie man PDF** aus einer Word‑Datei speichert, während jede schwebende Form sauber im Fluss bleibt? Sie sind nicht allein. In vielen Unternehmensanwendungen müssen wir *Word in PDF konvertieren*, ohne dass Bilder falsch platziert oder Zeichnungsobjekte verloren gehen. Die gute Nachricht? Aspose.Words macht das mühelos, und Sie können der Bibliothek sogar mitteilen, **Formen als Inline‑`<span>`‑Tags zu exportieren**, sodass das PDF genauso aussieht wie das ursprüngliche DOCX.

In diesem Tutorial führen wir Sie durch den gesamten Prozess – Laden eines DOCX, Anpassen der `PdfSaveOptions` und schließlich Speichern eines sauberen PDFs. Am Ende wissen Sie **wie man PDF speichert**, **docx als pdf speichert** und sogar **wie man Formen exportiert** mithilfe von *inline‑Span‑Tags*.

## Was Sie benötigen

- **Aspose.Words for .NET** (neueste Version, 24.x zum Zeitpunkt des Schreibens).  
- **.NET 6.0** oder höher – der Code funktioniert auch mit .NET Framework 4.7.2, aber .NET 6 ist optimal.  
- Ein einfaches Word‑Dokument, das mindestens eine schwebende Form (Bild, Textfeld oder Zeichnung) enthält.  
- Beliebige IDE Ihrer Wahl (Visual Studio, Rider, VS Code + C#‑Erweiterung).  

Das war's – keine zusätzlichen NuGet‑Pakete, kein umständliches COM‑Interop. Bereit? Dann legen wir los.

## Schritt 1: Projekt einrichten und Aspose.Words hinzufügen

Zuerst erstellen Sie eine Konsolen‑App (oder integrieren den Code in Ihren bestehenden Service).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Pro‑Tipp:** Wenn Sie Visual Studio verwenden, können Sie das Paket über die NuGet‑Package‑Manager‑UI hinzufügen – einfach nach *Aspose.Words* suchen.

## Schritt 2: Quell‑Dokument laden

Jetzt, wo die Bibliothek referenziert ist, können wir das DOCX laden. Dies ist der erste konkrete Schritt des **how to save pdf**‑Teils – das Laden der Quelle in den Speicher.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Warum das wichtig ist:** Das Laden der Datei prüft, ob der Pfad korrekt ist und ob Aspose die Word‑Struktur parsen kann. Enthält die Datei schwebende Formen, werden diese Teil des Knotenbaums des `Document`‑Objekts.

## Schritt 3: PDF‑Speicheroptionen konfigurieren – Formen als Inline‑Tags exportieren

Hier liegt das Kernstück von **how to export shapes**. Standardmäßig rendert Aspose.Words schwebende Formen als separate Objekte im PDF, was das Layout verschieben kann. Das Setzen von `ExportFloatingShapesAsInlineTag` auf `true` weist die Engine an, jede Form in ein Inline‑`<span>`‑Element zu verpacken und so den Fluss beizubehalten.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Warum dieses Flag aktivieren?** Stellen Sie sich einen Vertrag mit einem Unterschriftsfeld vor, das über dem Text schwebt. Wenn Sie ihn ohne diese Einstellung in PDF konvertieren, kann das Feld auf einer anderen Seite erscheinen. Inline‑`<span>`‑Tags verankern die Form im umgebenden Absatz und erzeugen eine getreue visuelle Kopie.

## Schritt 4: Dokument als PDF speichern

Schließlich rufen wir `doc.Save` mit den gerade erstellten Optionen auf. Das ist der Moment, in dem Sie tatsächlich **docx als pdf speichern**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Führen Sie das Programm (`dotnet run`) aus und prüfen Sie die `output.pdf`. Sie sollten Ihre schwebenden Formen inline gerendert sehen, genau wie sie in Word erschienen sind.

## Schritt 5: Ergebnis überprüfen – Schnell‑Checkliste

1. **Alle Texte sind vorhanden** – keine fehlenden Absätze.  
2. **Schwebende Formen erscheinen dort, wo sie sollten** – sie sind jetzt Teil des Textflusses.  
3. **PDF‑Größe ist angemessen** – das Exportieren als Inline‑Tags reduziert in der Regel die Dateigröße im Vergleich zu separaten Bild‑Streams.  

Wenn etwas nicht stimmt, prüfen Sie erneut, ob das Quell‑DOCX wirklich *schwebende* Formen verwendet (Rechtsklick → Layout → „Im Textfluss“ vs. „Quadrat/Hinter dem Text“). Das Umstellen einer Form auf „Im Textfluss“ vor der Konvertierung funktioniert ebenfalls, aber die Inline‑Tag‑Option gibt Ihnen Kontrolle, ohne die Originaldatei zu bearbeiten.

## Sonderfälle & häufige Fragen

### Was ist, wenn mein Dokument **SmartArt** oder **Diagramme** enthält?

SmartArt und Diagramme werden als Zeichenobjekte behandelt. Das Flag `ExportFloatingShapesAsInlineTag` wird sie weiterhin in `<span>`‑Tags einbetten, aber komplexe Grafiken können an Detailtreue verlieren. In solchen Fällen sollten Sie das Diagramm zuerst als Bild exportieren (`Chart.ToImage()`) und dann inline einfügen.

### Kann ich **Hyperlinks** und **Lesezeichen** beibehalten?

Ja, selbstverständlich. Diese Elemente werden durch die Einstellung `ExportFloatingShapesAsInlineTag` nicht beeinflusst. Aspose.Words behält alle Hyperlink‑ und Lesezeichen‑Informationen automatisch bei.

### Wie ändere ich die **PDF‑Kompression** oder **Schriften einbetten**?

`PdfSaveOptions` bietet viele zusätzliche Eigenschaften:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

Passen Sie diese Einstellungen nach Bedarf an Ihre nachgelagerten Anforderungen an (z. B. PDF/A‑Konformität).

## Vollständiges funktionierendes Beispiel (Copy‑Paste‑bereit)

Unten finden Sie das vollständige Programm, das Sie in `Program.cs` kopieren können. Ersetzen Sie `YOUR_DIRECTORY` durch einen tatsächlichen Ordnerpfad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Erwartete Ausgabe in der Konsole:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Öffnen Sie `output.pdf` – Sie sehen das ursprüngliche Layout, wobei jede schwebende Form eng im Textfluss platziert ist.

## Fazit

Wir haben **wie man PDF** aus einem Word‑Dokument speichert, wobei schwebende Formen zu Inline‑`<span>`‑Tags werden, behandelt. Durch das Laden des DOCX, das Konfigurieren von `PdfSaveOptions` und das Aufrufen von `doc.Save` können Sie zuverlässig **docx als pdf speichern** und **word in pdf konvertieren**, ohne Layout‑Überraschungen.  

Nächste Schritte? Versuchen Sie, diesen Ansatz mit **PDF/A**‑Konformität für die Archivierung zu kombinieren, oder verarbeiten Sie einen Ordner mit DOCX‑Dateien stapelweise mittels einer einfachen `foreach`‑Schleife. Sie können auch **benutzerdefiniertes Rendering** (z. B. Wasserzeichen hinzufügen) erkunden, indem Sie die `DocumentVisitor`‑API von Aspose.Words nutzen.

Haben Sie weitere Fragen zur Form‑Verarbeitung, Schrifteinbettung oder Leistungsoptimierung? Hinterlassen Sie unten einen Kommentar, und viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Dokument als PDF mit Aspose.Words für Java speichert](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Word zu PDF konvertieren mit Aspose.Words für Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – DOCX zu PDF in Java konvertieren](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
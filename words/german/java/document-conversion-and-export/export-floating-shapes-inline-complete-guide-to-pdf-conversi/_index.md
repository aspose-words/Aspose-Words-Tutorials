---
category: general
date: 2026-07-03
description: Exportiere schwebende Formen inline beim Konvertieren von Word in PDF.
  Erfahren Sie, wie Sie PDF‑Optionen festlegen und Word als PDF mit Optionen in Java
  speichern.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: de
og_description: Exportieren Sie schwebende Formen inline, wenn Sie ein Word‑Dokument
  in PDF konvertieren. Dieses Tutorial zeigt, wie Sie PDF‑Optionen festlegen und Word
  als PDF speichern.
og_title: Exportieren von schwebenden Formen inline – Java PDF‑Konvertierungsleitfaden
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Export von schwebenden Formen inline – Vollständiger Leitfaden zur PDF-Konvertierung
url: /de/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Floating Shapes Inline – Vollständiger Leitfaden zur PDF‑Konvertierung

Haben Sie schon einmal **schwebende Formen inline exportieren** müssen, wenn Sie ein Word‑Dokument in PDF konvertieren? Sie sind nicht allein – vielen Entwicklern passiert das, wenn ihre Diagramme oder Symbole plötzlich in separate Ebenen verschoben werden. Die gute Nachricht: Eine einzige PDF‑Option kann diese Formen innerhalb von `<span>`‑Tags halten und das Layout exakt so bewahren, wie Sie es in Word sehen.

In diesem Tutorial zeigen wir Ihnen **wie Sie PDF‑Optionen** in Java setzen, geben Ihnen den genauen Code zum **Speichern von Word mit PDF‑Optionen** und erklären, warum Sie **Word zu PDF inline konvertieren** sollten anstatt des standardmäßigen Block‑Exports. Am Ende haben Sie ein einsatzbereites Snippet, das Sie in jedes Maven‑ oder Gradle‑Projekt einbinden können.

## Was Sie lernen werden

- Der Unterschied zwischen Inline‑`<span>`‑ und Block‑`<div>`‑Export für schwebende Formen.  
- Wie Sie `PdfSaveOptions` konfigurieren, um das Inline‑Rendering zu erzwingen.  
- Schritt‑für‑Schritt‑Code, der eine `.docx` lädt, die Option anwendet und ein PDF schreibt.  
- Häufige Stolperfallen (fehlende Schriften, nicht unterstützte Formen) und wie Sie diese vermeiden.  
- Tipps zum Testen der Ausgabe und zum Erweitern des Ansatzes auf andere Dokumentelemente.

**Voraussetzungen** – Sie benötigen Java 8 oder neuer, die Aspose.Words for Java‑Bibliothek (oder eine API, die die Klasse `PdfSaveOptions` nachbildet) und eine Beispiel‑Word‑Datei mit schwebenden Formen (im Tutorial wird `FloatingShapes.docx` verwendet). Keine weiteren externen Tools sind nötig.

---

## Schritt 1: Das Quell‑Word‑Dokument laden

Das Erste, was Sie tun, ist die `.docx` zu öffnen, die Sie transformieren möchten. Das ist unkompliziert, achten Sie jedoch darauf, dass der Pfad absolut ist oder korrekt aus dem Klassenpfad aufgelöst wird.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Warum das wichtig ist:*  
Wenn das Dokument nicht korrekt geladen wird, wirft die nachfolgende PDF‑Konvertierung eine `FileNotFoundException`. Die Verwendung von `Document` stellt sicher, dass das interne Objektmodell vollständig befüllt ist, einschließlich aller schwebenden Formen, die sich auf der Seite befinden.

---

## Schritt 2: PDF‑Speicheroptionen erstellen und schwebende Formen auf Inline setzen

Hier passiert die Magie. Standardmäßig exportiert Aspose.Words schwebende Formen als Block‑`<div>`‑Elemente, was den Fluss in HTML‑basierten PDFs zerstören kann. Durch Aufruf von `setExportFloatingShapesAsInlineTag(true)` wird jede Form stattdessen in ein Inline‑`<span>`‑Tag eingebettet.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Warum das wichtig ist:*  
- **Layout‑Treue** – Inline‑Tags halten die Form an der umgebenden Textzeile ausgerichtet und vermeiden unerwünschte Lücken.  
- **Durchsuchbarkeit** – Inline‑Elemente werden von PDF‑Readern eher korrekt indiziert.  
- **Styling‑Kontrolle** – Sie können das `<span>` später mit CSS ansprechen, wenn Sie das PDF zurück nach HTML konvertieren.

> **Pro‑Tipp:** Wenn Sie für ein bestimmtes Dokument das alte Block‑Verhalten benötigen, übergeben Sie einfach `false` oder lassen Sie den Aufruf ganz weg.

---

## Schritt 3: Das Dokument mit den konfigurierten Optionen als PDF speichern

Jetzt kombinieren Sie das geladene `Document` mit den `PdfSaveOptions` und schreiben die Datei. Diese eine Zeile erledigt die schwere Arbeit.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Warum das wichtig ist:*  
Die `save`‑Methode respektiert jedes Flag, das Sie auf `pdfOptions` gesetzt haben. Wird die Option nicht übergeben, fällt die Ausgabe auf den Standard‑Block‑Export zurück und macht den Zweck des **Export Floating Shapes Inline** zunichte.

---

## Vollständiges funktionierendes Beispiel

Alles zusammengefügt, hier ein kompaktes Programm, das Sie jetzt kompilieren und ausführen können. Ersetzen Sie `YOUR_DIRECTORY` durch einen tatsächlichen Pfad auf Ihrem Rechner.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Erwartete Ausgabe** – Nach dem Ausführen des Programms öffnen Sie `FloatingShapes.pdf`. Die Formen sollten bündig mit dem Text sitzen, ohne zusätzlichen Weißraum, und die HTML‑Repräsentation (wenn Sie die interne Struktur des PDFs inspizieren) wird `<span>`‑Tags um jede Form enthalten.

![Export schwebende Formen inline Beispiel](https://example.com/export-inline.png "Screenshot, der schwebende Formen inline im PDF zeigt")

*Bild‑Alt‑Text:* **export floating shapes inline** Screenshot des PDFs mit Inline‑Formen.

---

## Häufige Fragen & Sonderfälle

### 1. „Was, wenn mein Dokument komplexes SmartArt enthält?“

SmartArt wird als Zeichenobjekt behandelt. Das Inline‑Flag funktioniert für die meisten Vektorformen, aber sehr komplexes SmartArt kann weiterhin als Bild gerendert werden. In solchen Fällen sollten Sie das SmartArt in Word vor der Konvertierung flachlegen oder `pdfOptions.setExportSmartArtAsImage(true)` verwenden, um den Bild‑Export zu erzwingen.

### 2. „Kann ich Inline‑ und Block‑Export im selben Dokument kombinieren?“

Leider gilt die Einstellung global für die gesamte API. Wenn Sie gemischtes Verhalten benötigen, teilen Sie das Dokument in Abschnitte, exportieren jeden Abschnitt separat mit unterschiedlichen Optionen und fügen die PDFs anschließend mit `PdfMerger` zusammen.

### 3. „Beeinflusst das die Schrift‑Einbettung?“

Nein. Die Schrift‑Einbettung wird über `pdfOptions.setEmbedFullFonts(true)` gesteuert (Standard). Sie können sie sicher ein‑ oder ausschalten, ohne das Inline‑Form‑Flag zu berühren.

### 4. „Wie prüfe ich, ob die Formen wirklich `<span>` sind?“

Öffnen Sie das resultierende PDF in einem Tool wie **PDF.js** oder **Adobe Acrobat** → **PDF bearbeiten** → **Objekt‑Inspektor**. Dort sehen Sie die Form in einem `<span>`‑Element im zugrunde liegenden XML. Wenn Sie `<div>` sehen, wurde die Option nicht angewendet.

---

## Erweiterung des Ansatzes – Verwandte Optionen

Während Sie hier sind, könnten Sie auch andere PDF‑Konvertierungs‑Regler erkunden:

| Option | Was sie bewirkt | Typischer Anwendungsfall |
|--------|----------------|--------------------------|
| `setCompressImages(true)` | Reduziert Bildgröße | Schnellere Downloads |
| `setUseHighQualityRendering(true)` | Verbessert Vektor‑Rendering | Druck‑fertige PDFs |
| `setExportDocumentStructure(true)` | Fügt strukturelle Tags für Barrierefreiheit hinzu | WCAG‑Konformität |
| `setSaveFormat(SaveFormat.PDF)` | Setzt das Format explizit (selten nötig) | Multi‑Format‑Pipelines |

Diese Einstellungen passen gut zu **convert word to pdf inline**‑Szenarien, bei denen Sie sowohl Layout‑Treue als auch Performance benötigen.

---

## Ihre Konvertierung testen

1. **Visueller Check** – Öffnen Sie das PDF in zwei Betrachtern (Chrome und Adobe Reader), um sicherzustellen, dass die Formen ausgerichtet sind.  
2. **Automatisierter Vergleich** – Nutzen Sie eine Bibliothek wie `pdfbox`, um das XML zu extrahieren und das Vorhandensein von `<span>`‑Tags zu prüfen.  
3. **Performance‑Benchmark** – Messen Sie die Laufzeit mit und ohne `setCompressImages`, um den Kompromiss zu sehen.

Ein kurzes JUnit‑Beispiel:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Fazit

Sie besitzen nun eine solide End‑zu‑End‑Lösung für **export floating shapes inline**, wenn Sie **Word zu PDF inline konvertieren**. Durch das Konfigurieren von `PdfSaveOptions` bestimmen Sie das HTML‑Tag, das für jede Form verwendet wird, und halten Ihre PDFs übersichtlich und durchsuchbar. Denken Sie daran, die Ausgabe zu testen, verwandte Optionen wie Bildkompression anzupassen und Sonderfälle wie komplexes SmartArt zu berücksichtigen.

Bereit für den nächsten Schritt? Versuchen Sie dieselbe Technik, um **schwebende Tabellen inline zu exportieren** oder experimentieren Sie mit CSS‑gestylten PDFs über Aspose’s `HtmlSaveOptions`. Das gleiche Muster – laden, konfigurieren, speichern – gilt für fast jedes Dokument‑zu‑PDF‑Szenario.

Haben Sie weitere Fragen zu **how to set pdf options** oder benötigen Hilfe bei **save word as pdf options** für eine andere Bibliothek? Hinterlassen Sie einen Kommentar und happy coding!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungs‑Ansätze in Ihren eigenen Projekten erkunden können.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
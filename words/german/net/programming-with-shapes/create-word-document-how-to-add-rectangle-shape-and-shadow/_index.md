---
category: general
date: 2026-03-19
description: Erstelle ein Word‑Dokument in C# mit Aspose.Words, lerne, wie man eine
  Form hinzufügt, ein Rechteck einfügt, einen Schatten anwendet und das Dokument in
  wenigen Minuten als DOCX speichert.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: de
og_description: Erstellen Sie ein Word‑Dokument mit Aspose.Words, fügen Sie eine Rechteckform
  hinzu, wenden Sie einen äußeren Schatten an und speichern Sie das Dokument als DOCX.
  Schritt‑für‑Schritt‑Anleitung.
og_title: Word-Dokument erstellen – Rechteckform & Schatten hinzufügen
tags:
- Aspose.Words
- C#
- Document Automation
title: Word‑Dokument erstellen – Wie man ein Rechteck und einen Schatten hinzufügt
url: /de/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument erstellen – So fügen Sie ein Rechteck-Shape und Schatten hinzu

Haben Sie jemals **create word document** programmatisch erstellen müssen und sich gefragt, wo Sie anfangen sollen? Sie sind nicht allein. Viele Entwickler stoßen an dieselbe Wand, wenn sie zum ersten Mal versuchen, eine .docx-Datei zu erzeugen, die benutzerdefinierte Grafiken enthält. In diesem Tutorial gehen wir den gesamten Prozess durch – wie man ein Shape hinzufügt, speziell ein **add rectangle shape**, ihm einen stilvollen **add shadow to shape** verleiht und schließlich **save document as docx**.  

Am Ende des Leitfadens haben Sie ein einsatzbereites C#‑Snippet, das Sie in jedes .NET‑Projekt einfügen können. Keine vagen Verweise, nur ein vollständiges, ausführbares Beispiel.  

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework).  
- Aspose.Words für .NET installiert (NuGet‑Paket `Aspose.Words`).  
- Grundlegendes Verständnis der C#‑Syntax – nichts Besonderes erforderlich.  

Wenn Ihnen die Bibliothek fehlt, führen Sie aus:

```bash
dotnet add package Aspose.Words
```

Das war's – keine zusätzlichen SDKs, kein COM‑Interop, nur ein einzelner NuGet‑Verweis.

---

## Schritt 1: Word-Dokument erstellen (Hauptziel)

Das Erste, was wir benötigen, ist eine leere Leinwand. Betrachten Sie die `Document`‑Klasse als eine frische Seite in Microsoft Word; sie enthält Abschnitte, Absätze und alles andere, was Sie später hinzufügen werden.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Warum mit einem leeren `Document` beginnen? Weil es garantiert, dass keine versteckte Formatierung aus einer Vorlage eingeschlichen wird. Nach meiner Erfahrung verhindert das Starten von Grund auf mysteriöse Layout‑Verschiebungen, wenn Sie später Shapes einfügen.

---

## Schritt 2: Rechteck‑Shape einfügen – Das visuelle Element hinzufügen

Jetzt, wo wir ein Dokument haben, fügen wir dem ersten Absatz ein **add rectangle shape** hinzu. Das `Shape`‑Objekt ist vielseitig; Sie können `ShapeType.Rectangle`, `Ellipse` oder sogar benutzerdefinierte Zeichnungen auswählen. Hier ist der minimale Code:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Was passiert im Hintergrund?**  
- `ShapeType.Rectangle` teilt Aspose mit, dass wir ein einfaches Rechteck wollen.  
- `WrapType.Inline` sorgt dafür, dass das Rechteck mit dem Textfluss mitbewegt, was in der Regel in einer Textverarbeitungs‑Situation erwartet wird.  
- Durch das Anhängen an `FirstParagraph` vermeiden wir das manuelle Einfügen eines neuen Absatzes; Aspose erstellt bei einem wirklich leeren Dokument einen für uns.

> **Pro‑Tipp:** Wenn das Shape *hinter* dem Text liegen soll, ändern Sie `WrapType` zu `WrapType.Transparent`. Diese kleine Änderung kann einen großen visuellen Unterschied bewirken.

---

## Schritt 3: Äußeren Schatten anwenden – Das Aussehen verbessern

Ein flaches Rechteck ist… nun ja, flach. Das Hinzufügen eines **add shadow to shape** verleiht ihm Tiefe ohne zusätzliche Bilder. Asposes `ShadowFormat` macht das zu einer Einzeiler‑Anweisung.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Warum diese konkreten Werte?  
- **Blur** von `5.0` erzeugt eine subtile, federartige Kante, die auf den meisten Monitoren professionell wirkt.  
- **Distance** von `3.0` und **Angle** von `45` erzeugen eine natürliche Lichtquelle von oben‑links, eine gängige Design‑Konvention.  
- **Color.Gray** funktioniert sowohl in hellen als auch dunklen Themes; Sie können es durch `Color.Black` ersetzen, wenn Sie einen stärkeren Kontrast benötigen.

Falls Sie jemals einen *inneren* Schatten benötigen (denken Sie an einen eingelassenen Button), ändern Sie einfach `ShadowType.OuterShadow` zu `ShadowType.InnerShadow`. Die gleichen Eigenschaften gelten weiterhin.

---

## Schritt 4: Dokument als DOCX speichern – Ihre Arbeit sichern

All das ist schön, aber irgendwann möchten Sie eine Datei auf der Festplatte haben. Der Schritt **save document as docx** ist unkompliziert:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Ein paar Anmerkungen:  
- Das `SaveFormat.Docx`‑Enum garantiert das moderne Office Open XML‑Format, das mit Word 2007+ kompatibel ist.  
- Wenn Sie die Datei direkt in eine Web‑Antwort streamen müssen, ersetzen Sie den Dateipfad durch einen `MemoryStream` und schreiben Sie ihn in die HTTP‑Antwort.

Nach dem Ausführen des Codes öffnen Sie `ShadowedRectangle.docx` in Microsoft Word. Sie sollten ein graues Rechteck mit einem weichen Schatten sehen, das inline mit dem ersten Absatz sitzt – genau das, was wir erreichen wollten.

---

## Shape hinzufügen – Alternative Ansätze

Das obige Beispiel verwendet den *inline*‑Ansatz, aber manchmal möchten Sie ein Shape, das über dem Text schwebt. Dort kommt **how to add shape** mit unterschiedlicher Umbruchart ins Spiel.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Hier haben wir `WrapType` zu `Square` geändert und das Shape auf der Seite zentriert. Dieses Muster ist nützlich für Deckblätter oder dekorative Banner. Denken Sie daran: schwebende Shapes erhöhen die Dateigröße leicht, da Word zusätzliche Positionierungsdaten speichert.

---

## Erwartete Ausgabe & Verifizierung

Wenn Sie die erzeugte Datei öffnen, sollten Sie sehen:

- Einen einzelnen Absatz, der ein graues Rechteck enthält.  
- Das Rechteck misst ungefähr 2,8 × 1,4 Zoll.  
- Einen dezenten äußeren Schatten, der nach unten‑rechts versetzt ist.

Falls das Shape *außerhalb* des Absatzes erscheint, überprüfen Sie `WrapType` erneut. Wenn der Schatten zu hart wirkt, reduzieren Sie den `Blur`‑Wert oder wechseln Sie die `Color` zu einem helleren Farbton.

---

## Häufige Fallstricke & wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|-------|-------------------|--------|
| Shape verschwindet nach dem Speichern | `WrapType` auf `Inline` gesetzt, aber Absatz wurde entfernt | Stellen Sie sicher, dass der Absatz existiert; verwenden Sie `doc.FirstSection.Body.FirstParagraph`, um ihn zu garantieren. |
| Schatten wirkt pixelig | Sehr niedriger `Blur`‑Wert verwendet | Erhöhen Sie `Blur` auf mindestens `3.0` für glatte Kanten. |
| Dateigröße explodiert | Viele hochauflösende Bilder zusammen mit Shapes hinzugefügt | Verwenden Sie `doc.RemoveUnusedResources()` vor dem Speichern, falls Sie Bilder hinzugefügt haben. |
| Farbe wird im Dark‑Mode nicht angezeigt | Dunkle `Color` für das Shape selbst verwendet | Wählen Sie eine kontrastierende Farbe (z. B. `Color.White`) für bessere Sichtbarkeit. |

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie den vollständigen, kopier‑und‑einfüg‑fertigen Code, der alles, was wir besprochen haben, beinhaltet. Sie können ihn gerne als Konsolen‑App ausführen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Erklärung jedes Blocks** ist inline als Kommentare enthalten, was sowohl SEO‑Lesern als auch KI‑Assistenten, die selbständige Antworten lieben, gerecht wird.

---

## Fazit

Wir haben gerade ein **create word document** von Grund auf erstellt, gelernt **how to add shape**, speziell ein **add rectangle shape**, ihm ein **add shadow to shape** verliehen und schließlich **save document as docx**. Die Schritte sind einfach, der Code kompakt und das Ergebnis wirkt professionell.  

Wenn Sie bereit sind, weiterzugehen, versuchen Sie, das Rechteck durch ein benutzerdefiniertes Bild zu ersetzen, experimentieren Sie mit verschiedenen Schattenfarben oder erzeugen Sie einen kompletten Bericht mit mehreren Shape‑Abschnitten. Die Aspose.Words‑API ist flexibel genug, um alles von Rechnungen bis hin zu Marketing‑Broschüren zu bewältigen.  

Haben Sie Fragen zu anderen Shape‑Typen oder benötigen Hilfe bei der Integration in einen ASP.NET Core‑Dienst? Hinterlassen Sie unten einen Kommentar und viel Spaß beim Coden! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-01-08
description: Erstellen Sie ein leeres Word‑Dokument und lernen Sie, wie Sie einem
  Rechteck einen Schatten hinzufügen. Fügen Sie Shape‑Word‑Dateien ein und fügen Sie
  den Shape‑Schatten in C# mit Aspose.Words hinzu.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: de
og_description: Erstellen Sie ein leeres Word-Dokument und sehen Sie, wie Sie einem
  Rechteck mit C# einen Schatten hinzufügen. Vollständiger Code, Erklärungen und Tipps.
og_title: Leeres Word‑Dokument erstellen – Schattiertes Rechteck einfügen
tags:
- Aspose.Words
- C#
- Document Automation
title: Leeres Word‑Dokument mit schattiertem Rechteck erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines leeren Word-Dokuments mit schattierter Rechteckform – Komplettes Tutorial

Haben Sie jemals **leere Word**‑Dateien programmgesteuert erstellen müssen und sie dann mit einem schönen schattierten Rechteck versehen? Sie sind nicht allein. Viele Entwickler stoßen auf ein Problem, wenn sie feststellen, dass das Einfügen von Formen und das Anwenden von Effekten nicht so einfach ist wie das Eingeben von Text.

In diesem Leitfaden führen wir Sie durch den gesamten Prozess – vom Erzeugen einer leeren `.docx`‑Datei über **wie man einem rectangle shape word‑Objekt Schatten hinzufügt** bis hin zum **Einfügen von shape word‑Inhalten** mit einem polierten **add shape shadow**‑Effekt. Am Ende haben Sie ein einsatzbereites Snippet, das mit dem neuesten Aspose.Words für .NET funktioniert.

## Was Sie benötigen

- **Aspose.Words for .NET** (v24.10 oder neuer) – die Bibliothek, die alles unten ermöglicht.  
- Eine .NET‑Entwicklungsumgebung (Visual Studio, Rider oder die `dotnet`‑CLI).  
- Grundkenntnisse in C# – wenn Sie „Hello World“ schreiben können, sind Sie bereit.  

Es sind keine zusätzlichen NuGet‑Pakete erforderlich; alles befindet sich in `Aspose.Words` und `System.Drawing`.

## Schritt 1: Erstellen eines leeren Word-Dokuments

Der erste Schritt besteht darin, ein leeres `Document`‑Objekt zu erzeugen. Betrachten Sie es als eine frische Leinwand – ähnlich wie das manuelle Öffnen einer neuen Word‑Datei.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Warum das wichtig ist:*  
Eine `Document`‑Instanz repräsentiert die gesamte Word‑Datei. Wenn Sie mit einem leeren Dokument beginnen, haben Sie die volle Kontrolle über jedes Element, das Sie später hinzufügen, von Absätzen bis zu Formen.

## Schritt 2: Definieren einer Rechteckform (Rectangle Shape Word)

Jetzt benötigen wir eine Form, mit der wir arbeiten können. Ein Rechteck ist die einfachste Geometrie und eignet sich gut für Banner, Platzhalter oder einfache UI‑Mock‑Ups.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Warum das wichtig ist:*  
Durch das Festlegen von `Width` und `Height` können Sie den visuellen Fußabdruck der Form steuern. `ShapeType.Rectangle` weist Aspose an, ein klassisches Rechteck zu rendern – perfekt, um später **add shape shadow** zu demonstrieren.

## Schritt 3: Einen Schatten auf die Form anwenden (How to Add Shadow)

Schatten verleihen Tiefe und lassen ein flaches Rechteck wie ein physisches Objekt wirken. Aspose.Words stellt eine `Shadow`‑Eigenschaft bereit, über die Sie Farbe, Abstand, Unschärfe und Transparenz anpassen können.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Warum das wichtig ist:*  

- **Enabled** – ohne diese Einstellung werden die anderen Parameter ignoriert.  
- **Color** – wählen Sie einen Farbton, der zum Thema Ihres Dokuments passt.  
- **Distance** – größere Werte schieben den Schatten weiter vom Objekt weg.  
- **BlurRadius** – höhere Werte machen den Schatten weicher.  
- **Transparency** – justieren Sie die Opazität für subtile Effekte.  

Experimentieren Sie gern; für einen dramatischen Effekt erhöhen Sie `Distance` auf `10` und setzen `Transparency` auf `0.5`.

## Schritt 4: Einfügen der Form in das Dokument (Insert Shape Word)

Nachdem das Rechteck fertig ist, benötigen wir einen Platz, um es einzufügen. Der einfachste Ort ist der erste Absatz des Dokumentenkörpers.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Warum das wichtig ist:*  
`FirstSection.Body.FirstParagraph` ist in einem neuen `Document` immer vorhanden. Wenn Sie die Form hier anhängen, stellen Sie sicher, dass sie oben im Dokument erscheint – nützlich für Kopfzeilen oder Titelbanner.

Falls Sie die Form an anderer Stelle einfügen müssen, können Sie einen bestimmten `Paragraph` oder `Run` finden und `InsertAfter` oder `InsertBefore` verwenden.

## Schritt 5: Speichern der Word‑Datei

Der letzte Schritt besteht darin, das im Speicher befindliche Dokument auf die Festplatte zu schreiben. Wählen Sie einen Ordner, in den Sie Schreibzugriff haben, und geben Sie der Datei einen aussagekräftigen Namen.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Warum das wichtig ist:*  
Durch Aufruf von `Save` wird eine vollständig konforme `.docx`‑Datei geschrieben. Öffnen Sie sie in Microsoft Word, LibreOffice oder einem beliebigen Viewer, und Sie sehen ein Rechteck mit einem weichen grauen Schatten – genau das, was wir konfiguriert haben.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette Programm, das Sie in eine Konsolenanwendung kopieren können. Es enthält alle `using`‑Anweisungen, die Erstellung der Form, die Schattenkonfiguration, das Einfügen und das Speichern.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Erwartete Ausgabe:**  
Öffnen Sie `ShadowedRectangle.docx` und Sie sehen ein hellgraues Rechteck, das oben auf der Seite zentriert ist, mit einem dezenten Schlagschatten, der um 5 pt versetzt ist. Kein zusätzlicher Text, nur die Form – genau das, was der Code erzeugt.

## Häufige Fragen & Sonderfälle

### Was, wenn ich eine andere Form benötige?

Ersetzen Sie `ShapeType.Rectangle` durch einen anderen `ShapeType`‑Enum‑Wert (`Ellipse`, `Triangle`, `Star` usw.). Die Schatten‑Eigenschaften funktionieren auf dieselbe Weise.

### Kann ich mehrere Schatten hinzufügen?

Aspose.Words unterstützt nur einen einzelnen Schatten pro Form. Wenn Sie geschichtete Effekte benötigen, erstellen Sie zwei überlappende Formen mit unterschiedlichen Schatten‑Einstellungen.

### Wie funktioniert das unter .NET Core?

Die gleiche API funktioniert unter .NET 6/7/8. Stellen Sie lediglich sicher, dass Sie das **Aspose.Words.NETCore**‑Paket referenzieren (oder das Standardpaket, das jetzt plattformübergreifend ist).

### Wird `System.Drawing` noch unter Linux unterstützt?

`System.Drawing.Common` ist ab .NET 6 nur noch für Windows verfügbar. Für plattformübergreifende Projekte verwenden Sie `Aspose.Drawing` (ein separates NuGet) oder bleiben Sie bei Farben, die von `Aspose.Words` selbst definiert werden.

### Was ist mit DPI‑Skalierung?

Die Formabmessungen werden in Punkten angegeben (1 pt = 1/72 Zoll). Wenn Sie pixelgenaue Größen für eine bestimmte DPI benötigen, berechnen Sie die Punkte als `pixels * 72 / dpi`.

## Profi‑Tipps & Stolperfallen

- **Pro‑Tipp:** Setzen Sie `rectangleShape.WrapType = WrapType.Inline;` wenn die Form mit dem Text fließen soll, anstatt darüber zu schweben.  
- **Achten Sie auf:** Das Vergessen, den Schatten zu aktivieren (`Enabled = true`). Die anderen Einstellungen werden stillschweigend ignoriert.  
- **Leistungshinweis:** Das Hinzufügen vieler Formen in einer engen Schleife kann langsam sein. Stapeln Sie sie in einer einzigen `Section` und rufen Sie am Ende einmal `document.UpdatePageLayout()` auf.  
- **Versionsprüfung:** Die Schatten‑API wurde in Aspose.Words 20.2 eingeführt. Wenn Sie eine ältere Version verwenden, aktualisieren Sie, um fehlende Eigenschaften zu vermeiden.

## Fazit

Wir haben ein **leeres Word**‑Dokument erstellt, eine **rectangle shape word** gebaut, gelernt **wie man einen Schatten hinzufügt**, und schließlich **shape word**‑Inhalte mit einem polierten **add shape shadow**‑Effekt eingefügt – alles mit Aspose.Words für .NET.  

Das Snippet ist vollständig ausführbar, funktioniert unter Windows und plattformübergreifendem .NET und kann auf andere Formen, Farben oder sogar animierte GIFs erweitert werden. Als Nächstes könnten Sie Text in das Rechteck einfügen, Farbverläufe anwenden oder einen kompletten Bericht mit mehreren gestalteten Formen generieren.  

Haben Sie weitere Ideen? Versuchen Sie, den grauen Schatten durch einen blauen zu ersetzen, erhöhen Sie die Unschärfe für einen verträumten Look oder kombinieren Sie mehrere Formen zu einem benutzerdefinierten Logo. Der Himmel ist die Grenze, und jetzt haben Sie die Bausteine, um das zu realisieren.  

Viel Spaß beim Programmieren, und möge Ihre Dokumente immer scharf aussehen (mit genau der richtigen Menge an Schatten)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
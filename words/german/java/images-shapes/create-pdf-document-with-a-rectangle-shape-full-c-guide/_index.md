---
category: general
date: 2026-03-25
description: Erstellen Sie ein PDF‑Dokument in C# und lernen Sie, wie Sie eine Rechteckform
  hinzufügen, die Füllfarbe festlegen, die Größe der Form anpassen und die Transparenz
  der Form in nur wenigen Schritten einstellen.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: de
og_description: Erstellen Sie ein PDF-Dokument in C# und erfahren Sie, wie Sie ein
  Rechteck hinzufügen, dessen Füllfarbe, Größe und Transparenz festlegen, um ein hochwertiges
  PDF‑Ergebnis zu erzielen.
og_title: PDF-Dokument mit Rechteckform erstellen – C#‑Tutorial
tags:
- C#
- PDF
- Aspose.Words
title: PDF-Dokument mit Rechteckform erstellen – Vollständige C#‑Anleitung
url: /de/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF-Dokument mit einer Rechteckform erstellen – Vollständige C#‑Anleitung

Haben Sie jemals ein **PDF-Dokument erstellen** müssen, das eine benutzerdefinierte Form enthält, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein. Egal, ob Sie einen Berichtsgenerator oder einen Marketing‑Flyer erstellen, die Möglichkeit, programmgesteuert ein Rechteck zu zeichnen, dessen Füllfarbe festzulegen, die Größe anzupassen und sogar die Transparenz zu steuern, kann Ihre PDFs deutlich professioneller wirken lassen.

In diesem Tutorial führen wir Sie durch ein vollständiges, sofort ausführbares C#‑Beispiel, das **ein PDF-Dokument erstellt**, **eine Rechteckform hinzufügt**, **die Füllfarbe festlegt**, **die Größe der Form definiert** und **die Transparenz der Form** für einen dezenten äußeren Schatten einstellt. Am Ende haben Sie eine einzelne PDF‑Datei (`shadow.pdf`), die Sie öffnen können, um das Ergebnis zu sehen.

> **Profi‑Tipp:** Der gleiche Ansatz funktioniert mit anderen Formtypen (Ellipse, Linie usw.) – ersetzen Sie einfach `ShapeType.RECTANGLE` durch den benötigten Typ.

## Was Sie benötigen

| Prerequisite | Why it matters |
|--------------|----------------|
| **.NET 6+** (or .NET Framework 4.6+) | Die Aspose.Words‑Bibliothek richtet sich an moderne Laufzeiten. |
| **Aspose.Words for .NET** NuGet package | Stellt `Document`, `Shape`, `ShadowEffect` und verwandte Klassen bereit. |
| **A C# IDE** (Visual Studio, Rider, VS Code) | Ermöglicht einfaches Debuggen und Ausführen des Beispiels. |
| **Basic C# knowledge** | Sie verstehen die Syntax, ohne tief einsteigen zu müssen. |

Sie können die Bibliothek über die Befehlszeile installieren:

```bash
dotnet add package Aspose.Words
```

Das war's – keine zusätzlichen DLLs, keine nativen Abhängigkeiten. Sobald das Paket installiert ist, lässt sich der nachfolgende Code kompilieren und ausführen.

## Schritt‑für‑Schritt‑Implementierung

Im Folgenden teilen wir den Prozess in fünf logische Schritte auf. Jeder Schritt hat eine klare Überschrift (damit KI‑Modelle ihn indexieren können) und einen kurzen Code‑Block, den Sie direkt kopieren und einfügen können.

### ## 1. PDF-Dokument erstellen und die Zeichenfläche vorbereiten

Das allererste, was wir tun, ist ein `Document` zu instanziieren. Betrachten Sie es als eine leere Zeichenfläche, die schließlich Ihre PDF‑Datei wird.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Warum?** `Document` enthält alle Abschnitte, Absätze und Formen. Der Start mit einem sauberen Objekt garantiert, dass keine versteckten Artefakte aus vorherigen Durchläufen vorhanden sind.

### ## 2. Rechteckform hinzufügen – Füllfarbe festlegen und Größe der Form bestimmen

Jetzt erstellen wir ein Rechteck, geben ihm eine leuchtend gelbe Füllung und definieren seine Abmessungen. Das deckt sowohl **Rechteckform hinzufügen** als auch **Füllfarbe festlegen** sowie **Größe der Form festlegen** ab.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Hinweis:** Breite/Höhe werden in Punkten gemessen (1 Punkt = 1/72 Zoll). Passen Sie diese Werte an Ihr Layout an.

### ## 3. Äußeren Schatten anwenden und Transparenz der Form festlegen

Schatten verleihen Tiefe, und die Steuerung ihrer Opazität ist das Wesentliche von **Transparenz der Form festlegen**. Im Folgenden konfigurieren wir einen grauen äußeren Schatten mit 30 % Transparenz.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Warum Transparenz einstellen?** Ein zu 30 % transparenter Schatten wirkt dezent und verhindert, dass das Rechteck auf der Seite „flach“ aussieht.

### ## 4. Form in den Dokumentenkörper einfügen

Jetzt platzieren wir das Rechteck im ersten Absatz des ersten Abschnitts des Dokuments. Dieser Schritt verbindet alles.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Sonderfall:** Wenn Sie die Form auf einer neuen Seite benötigen, fügen Sie vor dem Anhängen der Form `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` hinzu.

### ## 5. Dokument als PDF‑Datei speichern

Abschließend speichern wir die In‑Memory‑Struktur in einer physischen PDF‑Datei. Die Datei wird in den von Ihnen angegebenen Ordner geschrieben.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Wenn Sie das Programm ausführen, erscheint eine Datei namens `shadow.pdf`. Beim Öffnen sehen Sie ein gelbes Rechteck mit einem weichen grauen Schatten, der um 4 Punkte versetzt ist – genau das, was unser Code beschreibt.

> **Erwartete Ausgabe:** Ein einseitiges PDF, bei dem das Rechteck nahe der oberen linken Ecke der Seite sitzt, gelb gefüllt, 200 × 100 Punkte groß ist und einen halbtransparenten äußeren Schatten wirft.

## Vollständiges funktionierendes Beispiel (Kopieren‑und‑Einfügen bereit)

Unten finden Sie die gesamte Quelldatei, bereit, in ein neues Konsolenprojekt eingefügt zu werden.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tipp:** Ersetzen Sie `YOUR_DIRECTORY` durch einen absoluten Pfad wie `C:\Temp` oder einen relativen Pfad wie `.\output`. Das Programm erstellt den Ordner, falls er noch nicht existiert.

## Häufig gestellte Fragen (FAQ)

**Q: Kann ich die Position des Rechtecks auf der Seite ändern?**  
A: Absolut. Setzen Sie `rectangle.Left` und `rectangle.Top` (beide in Punkten gemessen), bevor Sie es dem Absatz hinzufügen.

**Q: Was, wenn ich eine transparente Füllung statt eines transparenten Schattens benötige?**  
A: Verwenden Sie `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – das erste Argument ist der Alpha‑Kanal (0‑255), wobei 128 etwa 50 % Transparenz ergibt.

**Q: Funktioniert das mit .NET Core?**  
A: Ja. Aspose.Words unterstützt .NET Standard 2.0+, sodass Sie denselben Code auf .NET 6, .NET 7 oder .NET Framework 4.6+ ausführen können.

**Q: Wie kann ich mehrere Formen hinzufügen?**  
A: Wiederholen Sie einfach die Schritte 2‑4 für jede Form und fügen Sie sie ggf. in verschiedene Absätze oder Abschnitte ein.

## Fazit

Wir haben gerade **ein PDF‑Dokument** von Grund auf **erstellt**, **eine Rechteckform hinzugefügt**, **die Füllfarbe festgelegt**, **die Größe definiert** und **die Transparenz der Form angepasst**, um einen hochwertigen Schatteneffekt zu erzielen. Der Beispielcode ist eigenständig, läuft in weniger als einer Minute und demonstriert die Kernkonzepte, die Sie für aufwändigere PDF‑Layouts benötigen.

Bereit für die nächste Herausforderung? Versuchen Sie, das Rechteck durch eine Form mit abgerundeten Ecken zu ersetzen, ein Bild in die Form einzubetten oder automatisch ein Inhaltsverzeichnis zu erzeugen. Mit derselben API können Sie Text, Bilder und Vektoren schichten – die Möglichkeiten sind grenzenlos.

Wenn Ihnen diese Anleitung gefallen hat, geben Sie ihr einen Stern auf GitHub, teilen Sie sie mit einem Teamkollegen oder hinterlassen Sie einen Kommentar mit Ihren eigenen Varianten. Viel Spaß beim Coden!

![PDF-Dokument mit Rechteckform Beispiel](/images/rectangle-shadow.png "Screenshot, der das erstellte PDF mit einem gelben Rechteck und einem grauen äußeren Schatten zeigt")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
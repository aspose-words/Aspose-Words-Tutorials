---
category: general
date: 2026-01-03
description: Erstelle ein Rechteck in Word mit C# und füge dem Objekt einen Schatten
  hinzu. Erfahre, wie man ein Objekt in Word einfügt, dem Objekt einen Schatten hinzufügt
  und Word‑Dokumente programmgesteuert erzeugt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: de
og_description: Erstelle ein Rechteck in Word mit C# und füge dem Objekt einen Schatten
  hinzu. Befolge diese Anleitung, um ein Objekt in Word einzufügen, Schatten zu konfigurieren
  und Dokumente programmgesteuert zu erzeugen.
og_title: Rechteckform in Word mit C# erstellen – Komplettes Tutorial
tags:
- C#
- Word Automation
- Aspose.Words
title: Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Word mit C# – Komplettes Tutorial

Haben Sie jemals eine **create rectangle shape** in einem Word-Dokument erstellen müssen, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein – viele Entwickler stoßen auf dasselbe Problem, wenn sie **add shadow to shape** für ein professionelles Aussehen hinzufügen wollen. In diesem Tutorial führen wir Sie durch die genauen Schritte, um **insert shape in Word** einzufügen, einen dezenten Schatten anzuwenden und schließlich **c# generate word document** Dateien zu erzeugen, die Sie an Benutzer ausliefern können.

Wir decken alles ab, von der Einrichtung des Projekts bis zum Anpassen der Schatten‑Eigenschaften, und schließen mit einem sofort ausführbaren Code‑Beispiel ab. Kein Schnickschnack, nur die praktischen Details, die die Aufgabe erledigen.

## Was Sie lernen werden

- Wie man **create rectangle shape** mit Aspose.Words (oder Open XML) in C# verwendet  
- Die genauen Eigenschaften, die Sie benötigen, um **add shadow to shape** für Tiefe hinzuzufügen  
- Wo Sie die Form mit `DocumentBuilder` platzieren  
- Wie Sie die Datei speichern, damit sie korrekt in Microsoft Word geöffnet wird  
- Tipps, Fallstricke und Varianten für reale Szenarien  

### Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auf .NET Core und .NET Framework)  
- Ein NuGet‑Paket, das Word‑Dateien manipulieren kann – wir verwenden **Aspose.Words for .NET**, weil seine API kompakt ist. Wenn Sie das Open XML SDK bevorzugen, sind die Konzepte dieselben, nur die Klassen unterscheiden sich.  
- Visual Studio, VS Code oder jede C#‑IDE Ihrer Wahl  

> **Pro‑Tipp:** Wenn Sie ein begrenztes Budget haben, bietet Aspose eine kostenlose Testversion, die ideal zum Lernen ist. Ersetzen Sie einfach die Lizenzzeile durch einen Kommentar, wenn Sie testen.

## Schritt 1: Installieren der Word‑Verarbeitungsbibliothek

Zuerst fügen Sie die Bibliothek zu Ihrem Projekt hinzu. Öffnen Sie ein Terminal im Ordner Ihrer Lösung und führen Sie aus:

```bash
dotnet add package Aspose.Words
```

Wenn Sie das Open XML SDK verwenden, lautet der Befehl `dotnet add package DocumentFormat.OpenXml`. Der Rest dieses Leitfadens geht von Aspose.Words aus, aber das Austauschen der API‑Aufrufe ist unkompliziert.

## Schritt 2: Erstellen eines neuen leeren Dokuments

Jetzt, wo die Bibliothek bereit ist, können wir **create rectangle shape** erzeugen, indem wir mit einem leeren `Document`‑Objekt beginnen. Betrachten Sie dies als eine frische Leinwand.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

Der `DocumentBuilder` bietet uns eine hoch‑level Methode, Inhalte einzufügen, ohne in niedrige Knotenbäume einzutauchen.

## Schritt 3: Einfügen der Rechteckform

Mit dem Builder in der Hand können wir **insert shape in Word**. Die Methode `InsertShape` nimmt den Formtyp und seine Abmessungen (Breite, Höhe) in Punkten.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

An diesem Punkt erscheint das Rechteck im Dokument, wirkt jedoch etwas flach. Hier kommt der nächste Schritt ins Spiel.

## Schritt 4: Schatten zur Form hinzufügen

Schatten verleihen der Form ein Gefühl von Tiefe. Das `Shadow`‑Objekt ermöglicht das feine Abstimmen von Unschärfe, Abstand, Winkel, Farbe und Transparenz. Unten steht eine vollständige Konfiguration, die für die meisten Berichte gut funktioniert.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Warum diese Werte?**  
- **BlurRadius** von `5.0` hält die Kante glatt, ohne unscharf zu wirken.  
- **Distance** von `4.0` verschiebt den Schatten gerade genug, um bemerkbar zu sein.  
- **Angle** `45` ahmt natürliches Licht von oben‑links nach, eine gängige UI‑Konvention.  
- **Transparency** `0.3` verhindert, dass der Schatten die Füllung der Form überlagert.

Wenn Sie einen dramatischeren Effekt benötigen, erhöhen Sie `BlurRadius` und verringern Sie `Transparency`. Für eine subtile, fast unsichtbare Hebung tauschen Sie diese Werte um.

## Schritt 5: Dokument speichern

Schließlich schreiben Sie die Datei auf die Festplatte. Die Methode `Save` erkennt das Format anhand der Dateierweiterung, sodass `.docx` Ihnen das moderne Word‑Format liefert.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Öffnen Sie `ShadowRectangle.docx` in Microsoft Word, und Sie sehen ein klares Rechteck mit einem weichen Schatten – genau das, was Sie wollten, als Sie nach “**how to add shape**” mit einem professionellen Finish fragten.

![Rechteckform mit Schatten in Word erstellen](placeholder-image.png "Rechteckform mit Schatten in Word erstellen")

*Bild‑Alt‑Text: create rectangle shape with shadow in Word*

## Vollständiges funktionierendes Beispiel

Alles zusammengefügt, hier das komplette, sofort ausführbare Programm. Kopieren‑Sie es in eine Konsolen‑App und drücken Sie **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Erwartetes Ergebnis

- Die erzeugte `ShadowRectangle.docx` enthält **one rectangle shape** zentriert an der Position des Cursors.  
- Das Rechteck zeigt einen **soft, 30 % transparent black shadow** mit einem Versatz von 45° an.  
- Es wird kein weiterer Inhalt hinzugefügt, wodurch die Datei leichtgewichtig bleibt und sich einfach in größere Berichte einbetten lässt.

## Häufige Fragen & Sonderfälle

### Was, wenn ich eine andere Form benötige?

Ersetzen Sie `ShapeType.Rectangle` durch einen anderen `ShapeType`‑Enum‑Wert (z. B. `Ellipse`, `Triangle`). Die Schatten‑API funktioniert auf dieselbe Weise, sodass Sie die Konfiguration wiederverwenden können.

### Wie ändere ich die Füllfarbe?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Kann ich die Form zu einem bestimmten Absatz hinzufügen?

Ja. Verschieben Sie den `DocumentBuilder` mit `builder.MoveToParagraph(index)` zum Zielabsatz, bevor Sie `InsertShape` aufrufen. Dadurch erscheint die Form genau dort, wo Sie sie benötigen.

### Was ist mit älteren Word‑Formaten (.doc)?

Einfach die Erweiterung ändern:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

Die Schatten‑Funktion wird in Word 2003 und später unterstützt, sodass Sie den Effekt weiterhin sehen.

### Verwendung des Open XML SDK anstelle von Aspose?

Die Schritte bleiben gleich: ein `WordprocessingDocument` erstellen, ein `Drawing`‑Element hinzufügen, `<a:shadow>`‑Eigenschaften setzen. Das XML ist ausführlicher, aber dieselben Konzepte (Größe, Unschärfe, Abstand, Winkel) gelten.

## Tipps zur Vermeidung von Fallstricken

- **Don’t forget the license** wenn Sie eine kostenpflichtige Aspose‑Version verwenden; sonst erhalten Sie ein Wasserzeichen.  
- **Units are points**, nicht Pixel. Ein typisches Bildschirm‑Pixel ≈ 0.75 pt, passen Sie also die Abmessungen entsprechend an.  
- **Shadow properties are ignored** wenn der `WrapType` der Form auf `Inline` gesetzt ist. Verwenden Sie `WrapType = WrapType.Square` für schwebende Formen, die die Schatten‑Darstellung respektieren.  
- **Saving to a network share** kann entsprechende Berechtigungen erfordern; testen Sie immer zuerst den Pfad.

## Fazit

Sie wissen jetzt, wie man **create rectangle shape** in einem Word‑Dokument mit C# erstellt, **add shadow to shape** hinzufügt und **c# generate word document** Dateien erzeugt, die sofort professionell aussehen. Die Kernschritte – Bibliothek installieren, `Document` instanziieren, die Form einfügen, den Schatten konfigurieren und speichern – sind leicht zu merken und an andere Formen, Farben oder sogar dynamische Daten anpassbar.

Was kommt als Nächstes? Versuchen Sie, mehrere Formen zu schichten, Bilder einzubetten oder einen vollständigen Bericht mit Tabellen und Diagrammen zu erzeugen. Sie können auch bedingte Formatierung erkunden – die Schattenintensität basierend auf Datenwerten ändern – um Ihre Dokumente nicht nur funktional, sondern auch visuell ansprechend zu machen.

Fühlen Sie sich frei zu experimentieren, und wenn Sie auf Eigenheiten stoßen, hinterlassen Sie unten einen Kommentar. Viel Spaß beim Coden, und mögen Ihre Word‑Dokumente stets den perfekten Schlagschatten haben!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
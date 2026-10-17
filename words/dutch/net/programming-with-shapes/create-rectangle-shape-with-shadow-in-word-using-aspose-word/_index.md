---
category: general
date: 2026-03-06
description: Maak een rechthoekvorm in Word en voeg een vormschaduw toe met Aspose.Words.
  Leer hoe je een rechthoek in Word invoegt en hoe je in C# een schaduw aan een vorm
  toevoegt.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: nl
og_description: Maak een rechthoekvorm in Word en voeg een vormschaduw toe met Aspose.Words.
  Stapsgewijze handleiding over hoe je een rechthoek in Word invoegt en hoe je een
  schaduw aan de vorm toevoegt.
og_title: Maak een rechthoekvorm met schaduw in Word met Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Maak een rechthoekvorm met schaduw in Word met Aspose.Words
url: /nl/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken met schaduw in Word met Aspose.Words

Heb je ooit een **create rectangle shape** nodig gehad in een Word‑document, maar wist je niet hoe je het die gepolijste uitstraling kunt geven? Je bent niet de enige—de meeste ontwikkelaars lopen tegen hetzelfde probleem aan wanneer ze voor het eerst visuele flair aan geautomatiseerde documenten willen toevoegen. Het goede nieuws? Met Aspose.Words for .NET kun je zowel **create rectangle shape** als **add shape shadow** uitvoeren in slechts een paar regels C#.

In deze tutorial lopen we precies door **how to insert rectangle in Word**, vervolgens laten we **how to add shadow to shape** zien zodat het van de pagina springt. Aan het einde heb je een kant‑klaar `Shadow.docx` dat je in Word kunt openen en een grijs getinte rechthoek met een zachte slagschaduw ziet. Geen extra afbeeldingsbestanden, geen handmatige aanpassingen—alleen code.

## Wat je zult leren

- De exacte C#‑statements die nodig zijn om **create rectangle shape** met Aspose.Words uit te voeren.  
- Hoe je een schaduw inschakelt en configureert met het `Shadow`‑object.  
- Waarom elke eigenschap belangrijk is (bijv. `Transparency`, `Blur`, `Angle`).  
- Veelvoorkomende valkuilen (eenheden, versie‑compatibiliteit) en snelle oplossingen.  
- Een compleet, copy‑and‑paste‑klaar programma dat je vandaag kunt uitvoeren.

### Vereisten

- .NET 6+ (of .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 of later (het NuGet‑pakket is `Aspose.Words`).  
- Een basisbegrip van C# en Visual Studio (of een IDE naar keuze).  

Als je die al hebt, laten we meteen beginnen.

## Stap 1: Het project instellen en namespaces importeren

Eerst, maak een nieuwe console‑app (of hergebruik een bestaande) en voeg het Aspose.Words NuGet‑pakket toe:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Breng nu de vereiste namespaces naar je `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** Als je .NET 6+ target, kun je globale `using`‑directieven inschakelen om te voorkomen dat je deze regels in elk bestand moet herhalen.

## Stap 2: **Create rectangle shape** in een leeg Word‑document

We beginnen met een nieuw `Document`‑object en een `DocumentBuilder` om het te manipuleren. De `InsertShape`‑methode van de builder is waar de magie gebeurt.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Waarom 200 × 100 punten? In Word is één punt gelijk aan 1/72 van een inch, dus de rechthoek wordt ongeveer 2,8 × 1,4 inch—groot genoeg om op te merken maar niet overweldigend. Je kunt deze getallen aanpassen aan je lay‑out; onthoud alleen dat ze gemeten worden in **points**, niet in pixels.

## Stap 3: **Add shape shadow** – het uiterlijk configureren

Nu we een rechthoek hebben, geven we hem een subtiele grijze schaduw. Het `Shadow`‑object zit op de `Shape` en biedt verschillende handige eigenschappen.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Wat elke eigenschap doet

| Eigenschap | Effect | Typische waarden |
|------------|--------|------------------|
| **Enabled** | Schakelt de schaduw in/uit | `true` of `false` |
| **Color** | Basiskleur van de schaduw | Elke `System.Drawing.Color` |
| **Transparency** | Opaciteit (0 = solid, 1 = invisible) | 0.0 – 1.0 |
| **Blur** | Zachtheid van de rand | 0 – 10 (hoger = zachter) |
| **Distance** | Afstand tussen vorm en schaduw | 0 – 20 points |
| **Angle** | Richting waar het licht vandaan lijkt te komen | 0 – 360 graden |
| **Size** | Schaal van de schaduw ten opzichte van de vorm | 0 – 200 % |

> **Waarom deze instellingen gebruiken?**  
> Het fijn afstellen van de schaduw stelt je in staat om te voldoen aan de huisstijlrichtlijnen (bijv. een subtiele 20 % transparantie voor een professionele uitstraling) zonder externe beeldbewerkingsprogramma's te gebruiken.

## Stap 4: Het document opslaan en het resultaat verifiëren

Schrijf tenslotte het bestand naar schijf. Je kunt elke gewenste map kiezen; vervang gewoon `YOUR_DIRECTORY` door een echt pad.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Open `Shadow.docx` in Microsoft Word en je zou een grijze rechthoek met een zachte slagschaduw, verschoven onder een hoek van 45°, moeten zien. Die visuele aanwijzing laat de vorm “van de pagina tillen”—precies wat je verwacht van een gepolijste rapport of factuur.

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt copy‑pasten in `Program.cs`. Er ontbreken geen onderdelen; het compileert en draait direct.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Verwachte output

- **Bestand:** `Shadow.docx` geplaatst in de uitvoermap van het project.  
- **Visueel:** Een enkele rechthoek gecentreerd op de pagina, gevuld met de standaard witte kleur, en een grijze schaduw verschoven 4 points naar rechtsonder, licht vervaagd voor een natuurlijke uitstraling.

## Veelgestelde vragen & randgevallen

### 1. Wat als ik een andere eenheid nodig heb (bijv. centimeters)?

Aspose.Words werkt met points, maar je kunt centimeters omrekenen naar points met de eenvoudige formule:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Werkt dit met oudere Aspose.Words‑versies?

De `Shadow`‑API werd geïntroduceerd in versie 14.0. Als je een oudere release gebruikt, moet je upgraden via NuGet. De rest van de code (vormen maken) is al jarenlang stabiel, dus je zult geen breaking changes tegenkomen.

### 3. Kan ik een schaduw toevoegen aan andere vormen (bijv. cirkels)?

Zeker—elk `Shape`‑object heeft een `Shadow`‑eigenschap. Vervang gewoon `ShapeType.Rectangle` door `ShapeType.Ellipse` of `ShapeType.Cloud`, en pas vervolgens dezelfde schaduwinstellingen toe.

### 4. Wat als ik een gekleurde schaduw nodig heb (bijv. blauw voor een merk)?

Vervang `Color.Gray` door elke `Color` die je wilt:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Vergeet niet `Transparency` aan te passen zodat de kleur niet te dominant wordt.

## 🎨 Visueel overzicht

![rechthoekvorm maken met schaduw in Word met Aspose.Words](image-placeholder.png "rechthoekvorm maken met schaduw in Word met Aspose.Words")

*Alt‑tekst: rechthoekvorm maken met schaduw in Word met Aspose.Words*

De screenshot (placeholder) toont het uiteindelijke document—alleen de rechthoek en zijn zachte grijze schaduw.

## Conclusie

Je weet nu hoe je **create rectangle shape** in een Word‑bestand kunt maken, **add shape shadow**, en elk visueel aspect kunt afstemmen met Aspose.Words for .NET. Het korte programma dat we hebben gebouwd dekt de volledige workflow—van

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
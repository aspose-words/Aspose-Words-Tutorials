---
category: general
date: 2025-12-25
description: Hoe je schaduw toevoegt in C# met een eenvoudig codevoorbeeld. Leer hoe
  je de schaduwafstand instelt, de kleur aanpast en diepte creëert voor je graphics.
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: nl
og_description: Hoe je schaduw toevoegt in C# wordt stap voor stap uitgelegd. Volg
  de gids om de schaduwafstand, kleur en vervaging in te stellen voor professioneel
  uitziende vormen.
og_title: Hoe je schaduw toevoegt in C# – Complete programmeergids
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: Hoe voeg je een schaduw toe in C# – Complete programmeergids
url: /nl/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe schaduw toe te voegen in C# – Complete programmeergids

Hoe schaduw toe te voegen in C# is een veelvoorkomende behoefte wanneer je wilt dat je graphics van de pagina springen. In deze tutorial lopen we stap voor stap door hoe je een vorm‑schaduw instelt, inclusief het instellen van de schaduwadstand, het aanpassen van de vervaging en het kiezen van de juiste kleur.  

Als je ooit naar een plat rechthoekje hebt gekeken en dacht “dit kan wel een beetje diepte gebruiken”, ben je hier op het juiste adres. We beginnen met een leeg document, voegen een vorm toe, en eindigen met een gepolijste schaduw die eruitziet alsof hij door een ontwerper is geplaatst. Geen poespas, alleen een praktisch, uitvoerbaar voorbeeld dat je vandaag nog kunt copy‑pasten.

## Wat je zult leren

- Een nieuw document maken en een vorm programmatisch invoegen.  
- Een zachte vervaging toepassen op de schaduw van de vorm.  
- **Hoe je de schaduwadstand instelt** zodat de schaduw natuurlijk verschoven verschijnt.  
- Een schaduwkleur kiezen die op elke achtergrond werkt.  
- Het resultaat opslaan als PDF (of elk ander formaat dat je nodig hebt).  

### Vereisten

- .NET 6.0 of later (de code werkt met .NET Core en .NET Framework).  
- Aspose.Words for .NET (gratis proefversie of gelicentieerde versie).  
- Een basisbegrip van C#‑syntaxis.  

Dat is alles—geen extra libraries, geen magie. Laten we beginnen.

![Voorbeeld van een vorm met een zachte zwarte schaduw – hoe schaduw toe te voegen](https://example.com/placeholder-shadow.png "how to add shadow example")

## Stap 1: Het project opzetten en namespaces importeren

Maak eerst een nieuwe console‑app (of elk C#‑project) en voeg het Aspose.Words NuGet‑pakket toe:

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

Open nu `Program.cs` en breng de benodigde namespaces in scope:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **Pro tip:** Als je Visual Studio gebruikt, zal de IDE de `using`‑statements voor je voorstellen terwijl je `Document` typt.

## Stap 2: Een nieuw document maken en een vorm toevoegen

Met de libraries klaar, kunnen we een `Document`‑object instantieren en een eenvoudige rechthoek op de eerste pagina plaatsen.

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

Waarom een rechthoek? Het is een neutraal canvas dat het effect van de schaduw laat beoordelen zonder afleiding. Je kunt `ShapeType.Rectangle` vervangen door `Ellipse` of `Star`—de schaduwlogica blijft hetzelfde.

## Stap 3: Hoe schaduw toe te voegen – Vervaging, afstand en kleur toepassen

Nu volgt het hart van de tutorial: **hoe schaduw toe te voegen** aan die rechthoek. Aspose.Words biedt een `Shadow`‑object op elke vorm, waarmee je vervaging, afstand en kleur kunt aanpassen.

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

Let op de commentaar `// 3b) Set the shadow's offset distance`. Die regel beantwoordt direct **hoe je de schaduwadstand instelt**. Door `shadow.Distance` aan te passen, beheer je de visuele kloof tussen de vorm en zijn schaduw, alsof er een lichtbron onder een specifieke hoek staat.

### Waarom deze waarden?

- **Blur = 5.0** – Een zachte vervaging voorkomt een harde silhouet terwijl hij toch zichtbaar blijft.
- **Distance = 3.0** – Houdt de schaduw dicht genoeg bij de vorm zodat het lijkt alsof hij door de vorm zelf wordt geworpen.
- **Color = Black** – Garandeert contrast op zowel lichte als donkere achtergronden.

Voel je vrij om deze cijfers aan te passen; de API accepteert elke `double`‑waarde die je nodig hebt.

## Stap 4: Het document opslaan en het resultaat verifiëren

Met de schaduw geconfigureerd, schrijven we het bestand simpelweg naar schijf. Aspose.Words kan veel formaten exporteren; PDF is een veelgebruikte keuze voor delen.

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

Open `ShadowedShape.pdf` en je zou een grijze rechthoek moeten zien met een zachte zwarte schaduw die iets naar rechtsonder is verschoven. Als de schaduw te zwak lijkt, verhoog dan `shadow.Blur` of `shadow.Distance` en voer het programma opnieuw uit.

## Veelgestelde vragen & randgevallen

### Wat als ik een transparante schaduw nodig heb?

Gebruik een ARGB‑kleur met een alfa‑kanaal kleiner dan 255:

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### Kan ik dezelfde schaduw op meerdere vormen toepassen?

Absoluut. Maak een hulpfunctie:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

Roep `ApplyStandardShadow(rectangle);` aan voor elke vorm die je toevoegt.

### Werkt dit met oudere .NET Framework‑versies?

Ja. Aspose.Words 22.9+ ondersteunt .NET Framework 4.5 en hoger. Pas je project‑bestand hierop aan.

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren naar `Program.cs`. Het compileert en draait meteen (ervan uitgaande dat het NuGet‑pakket geïnstalleerd is).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

Voer het programma uit:

```bash
dotnet run
```

Je vindt `ShadowedShape.pdf` in de projectmap. Open het met een PDF‑viewer om te bevestigen dat de schaduw eruitziet zoals beschreven.

## Conclusie

We hebben **hoe schaduw toe te voegen** aan een vorm in C# van begin tot eind behandeld, en we hebben **hoe je de schaduwadstand instelt** naast vervaging en kleur laten zien. Met slechts een paar regels code kun je je graphics een professioneel, driedimensionaal gevoel geven—zonder externe ontwerptools.

Nu je de basis onder de knie hebt, experimenteer gerust:

- Verander de schaduwkleur naar een subtiele blauw voor een koelere sfeer.  
- Verhoog de vervaging voor een dromerig, diffuus effect.  
- Pas dezelfde techniek toe op grafieken, afbeeldingen of tekstvakken.  

Elke variatie versterkt dezelfde kernconcepten, zodat je comfortabel schaduwen kunt aanpassen voor elke situatie.  

Heb je meer vragen? Laat een reactie achter, en happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
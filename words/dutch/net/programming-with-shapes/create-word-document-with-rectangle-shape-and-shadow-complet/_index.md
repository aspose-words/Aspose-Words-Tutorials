---
category: general
date: 2026-01-02
description: Maak een Word‑document met een rechthoekvorm, stel de vulkleur van de
  vorm in en sla het docx‑bestand op met Aspose.Words. Leer in enkele minuten hoe
  je een rechthoek met schaduw maakt.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: nl
og_description: Maak een Word‑document met een aangepaste rechthoek, stel de vulkleur
  in, voeg een schaduw toe en sla het op als DOCX. Volledige code en uitleg.
og_title: Maak Word‑document met rechthoekvorm – Stap‑voor‑stap
tags:
- Aspose.Words
- C#
- Document Generation
title: Maak Word-document met rechthoekvorm en schaduw – Complete gids
url: /nl/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-document maken met rechthoekvorm en schaduw – Complete gids

Heb je je ooit afgevraagd hoe je een **create word document** maakt dat een mooi gestylede rechthoek bevat? Misschien heb je een placeholder voor een logo, een gekleurde banner, of gewoon een visuele aanwijzing in een rapport nodig. In deze tutorial zullen we **add rectangle shape**, een vulkleur geven, een subtiele schaduw toepassen, en uiteindelijk **save docx file** – allemaal met Aspose.Words voor .NET.

Je krijgt een kant‑klaar C#‑fragment, een duidelijke uitleg van elke regel, en een reeks tips die je in je eigen projecten kunt hergebruiken. Geen poespas, alleen een praktische oplossing die je kunt kopiëren‑plakken.

## Wat je nodig hebt

- .NET 6 of later (de code werkt ook op .NET Framework)  
- Visual Studio 2022 (of elke editor die je verkiest)  
- **Aspose.Words** NuGet‑pakket (`Install-Package Aspose.Words`)  

Als je die al hebt, prima – laten we erin duiken.

## Stap 1 – Een nieuw document initialiseren (How to create word document)

Het eerste wat je moet doen is **create word document** in het geheugen. Beschouw het als het openen van een leeg canvas waarop je later je rechthoek zult tekenen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Waarom dit belangrijk is:** `Document` vertegenwoordigt het hele DOCX‑bestand, terwijl `DocumentBuilder` een handige helper is die je tekst, tabellen, afbeeldingen en vormen laat invoegen zonder handmatig de onderliggende knoopboom te beheren.

## Stap 2 – Een rechthoekvorm invoegen (Add rectangle shape)

Nu gaan we **add rectangle shape** aan het document toevoegen. De `InsertShape`‑methode neemt het vormtype en de afmetingen in punten (1 punt = 1/72 inch).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro‑tip:** Als je ooit een andere geometrie moet maken (ellipse, driehoek, enz.), wijzig dan gewoon `ShapeType.Rectangle` naar de gewenste enum‑waarde.

## Stap 3 – De schaduw configureren (Set shape fill color & shadow)

Een schaduw kan een platte vorm meer driedimensionaal laten aanvoelen. Hier schakelen we de schaduw in en passen we het uiterlijk aan.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Waarom deze waarden?** Een bescheiden vervagingsradius en een afstand van 5 punten voorkomen dat de schaduw de vorm overweldigt, terwijl 45° een lichtbron nabootst die van links‑boven komt – een gangbare UI‑conventie.

## Stap 4 – Het document opslaan (Save docx file)

Tot slot **save docx file** naar schijf. Pas het pad aan voor jouw omgeving.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Wanneer je `ShadowDemo.docx` in Word opent, zou je een lichtblauwe rechthoek met een zachte grijze schaduw moeten zien, net als de schermafbeelding hieronder.

![Word-document maken met rechthoekvorm en schaduw](https://example.com/images/rectangle-shadow.png "Word-document maken met rechthoekvorm en schaduw")

*Afbeeldingsalt‑tekst:* **Create Word Document** toont een rechthoekvorm met een schaduw.

## Volledig, kant‑klaar voorbeeld (How to create rectangle and save)

Alles samengevoegd, hier is het volledige programma dat je kunt kopiëren naar een console‑applicatie:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Verwacht resultaat

- Een bestand genaamd **ShadowDemo.docx** verschijnt in de doelmap.  
- Bij het openen in Microsoft Word wordt een enkele pagina getoond met de tekst “Shadow Demo” gevolgd door een lichtblauwe rechthoek.  
- De rechthoek werpt een zachte grijze schaduw onder een hoek van 45°, waardoor het een subtiel 3‑D‑gevoel krijgt.

## Veelgestelde vragen & randgevallen

### Wat als ik een andere grootte nodig heb?

Verander gewoon de `200, 100`‑argumenten in `InsertShape`. Deze getallen zijn de breedte en hoogte in punten. Voor een vierkant gebruik je identieke waarden.

### Kan ik de schaduw meer accentueren?

Verhoog `BlurRadius` voor een zachtere rand, verhoog `Distance` voor een grotere offset, of verlaag `Transparency` (bijv. `0.1`) om deze donkerder te maken.

### Hoe voeg ik een rand toe rond de rechthoek?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Is dit compatibel met oudere versies van Aspose.Words?

Ja. De `ShadowFormat`‑klasse bestaat al sinds de vroege 2020‑releases. Als je een zeer oude versie gebruikt, moet je mogelijk upgraden om alle eigenschappen te kunnen gebruiken.

## Tips & valkuilen

- **Pro tip:** Zorg ervoor dat je grote documenten (`doc.Dispose()`) altijd vrijgeeft wanneer je klaar bent, vooral in webapplicaties, om native resources vrij te maken.  
- **Let op:** Het gebruik van een relatief pad zonder de juiste permissies kan een `UnauthorizedAccessException` veroorzaken. Geef de voorkeur aan absolute paden of zorg ervoor dat de app‑pool schrijfrechten heeft.  
- **Onthoud:** De `FillColor`‑eigenschap accepteert elke `System.Drawing.Color`. Voel je vrij om `Color.FromArgb(255, 173, 216, 230)` te gebruiken voor een aangepaste pasteltoon.

## Volgende stappen

Nu je weet hoe je **create word document**, **add rectangle shape**, **set shape fill color**, en **save docx file** kunt doen, kun je verder experimenteren:

- Voeg meerdere vormen in en rangschik ze met `RelativeHorizontalPosition` en `RelativeVerticalPosition`.  
- Combineer de rechthoek met tekst via `Shape.TextBox` voor bijschriften.  
- Exporteer hetzelfde document naar PDF (`doc.Save("output.pdf")`) voor distributie.

Als je nieuwsgierig bent naar geavanceerdere graphics, bekijk dan de ondersteuning van Aspose.Words voor **WordArt**, **charts**, en **inline images**. Elk volgt hetzelfde patroon: een node maken, de eigenschappen configureren, en opslaan.

---

### TL;DR

- Gebruik `Document` en `DocumentBuilder` om **create word document**.  
- Roep `InsertShape(ShapeType.Rectangle, …)` aan om **add rectangle shape**.  
- Stel `FillColor` in voor de gewenste achtergrond.  
- Schakel `ShadowFormat` in en pas de eigenschappen aan voor een gepolijste uitstraling.  
- Eindig met `document.Save("yourPath.docx")` om **save docx file**.

Veel plezier met coderen, en geniet ervan om je Word‑bestanden er een beetje stijlvoller uit te laten zien!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
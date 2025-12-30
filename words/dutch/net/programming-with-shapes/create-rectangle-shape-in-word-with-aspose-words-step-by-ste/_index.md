---
category: general
date: 2025-12-29
description: Maak een rechthoekvorm in een Word‑document met Aspose.Words C#. Leer
  hoe je de transparantie van de vorm instelt, de schaduwkleur instelt en het Word‑document
  moeiteloos opslaat.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: nl
og_description: Maak een rechthoekvorm in een Word‑document met Aspose.Words C#. Deze
  gids laat zien hoe je de transparantie van de vorm instelt, de schaduwkleur instelt
  en het Word‑document opslaat.
og_title: Maak een rechthoekvorm in Word – Complete Aspose.Words-tutorial
tags:
- Aspose.Words
- C#
- Word Automation
title: Rechthoekvorm maken in Word met Aspose.Words – Stapsgewijze handleiding
url: /nl/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken in Word – Complete Aspose.Words Tutorial

Heb je ooit **een rechthoekvorm** in een Word‑document moeten maken, maar wist je niet waar je moest beginnen? Je bent niet de enige; veel ontwikkelaars lopen tegen dit probleem aan bij het automatiseren van rapporten of facturen. In deze gids lopen we de exacte stappen door om een rechthoek te maken, de transparantie van de vorm in te stellen, de schaduwkleur in te stellen, en uiteindelijk **het Word‑document op te slaan** met Aspose.Words voor .NET.  

We behandelen alles, van het initiële documentobject tot het uiteindelijke `.docx`‑bestand op schijf, zodat je aan het einde **een Word‑document** programmatisch kunt **maken** zonder te gokken. Geen externe referenties, alleen een zelfstandige oplossing die je kunt kopiëren‑plakken in je project.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)
- Basiskennis van C#‑syntaxis
- Een IDE naar keuzeVisual Studio, Rider, VS Code, enz.)

> **Pro tip:** Als je een gratis proefversie van Aspose.Words gebruikt, voegt de bibliotheek een watermerk toe aan het uitvoerbestand. Voor productie heb je een geldige licentie nodig.

## Stap 1: Initialiseer het Document en de Builder

Het eerste wat we doen is een nieuw, leeg Word‑document maken en een `DocumentBuilder` die ons in staat stelt inhoud in te voegen. Beschouw de builder als een virtuele pen die op de pagina tekent.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Waarom dit belangrijk is:** Zonder een `DocumentBuilder` zou je de low‑level knoopboom direct moeten manipuleren, wat foutgevoelig en moeilijker leesbaar is.

## Stap 2: Rechthoekvorm maken

Nu maken we daadwerkelijk **een rechthoekvorm**. De `InsertShape`‑methode neemt een `ShapeType`‑enum, breedte en hoogte (in points). Het geretourneerde `Shape`‑object stelt ons later in staat visuele eigenschappen aan te passen.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Op dit moment is de rechthoek een solide zwarte doos die verankerd is aan de huidige alinea. Je kunt hem verplaatsen, van grootte veranderen, of later zelfs roteren indien nodig.

![rechthoekvorm met schaduw](/images/rectangle-shadow.png "Een Word‑document dat een rechthoekvorm met een grijze schaduw toont")

*Afbeeldings‑alt‑tekst: rechthoekvorm met schaduw in een Word‑document*

## Stap 3: Transparantie van de vorm instellen

Transparantie is het “doorzichtigheids‑niveau” van de vulling van de vorm. Aspose.Words gebruikt een `Transparency`‑eigenschap die varieert van `0.0` (ondoorzichtig) tot `1.0` (volledig transparant). Hier **stellen we de transparantie van de vorm** in op 40 % zodat de onderliggende tekst leesbaar blijft.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Randgeval:** Als je een volledig onzichtbare vorm nodig hebt maar de schaduw wel wilt laten verschijnen, stel `Transparency` in op `1.0` en geef de vorm een niet‑nul omtrekbreedte.

## Stap 4: De schaduw configureren

Een subtiele slagschaduw voegt diepte toe. We zullen de **schaduwkleur** instellen op een mediumgrijs, de vervagingsradius aanpassen, en de schaduw een paar points zowel horizontaal als verticaal verplaatsen.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Waarom dit belangrijk is:** Een schaduw die te scherp of te donker is, kan eruitzien als een afdrukartefact. Pas `Blur` en `Transparency` aan totdat het natuurlijk aanvoelt.

## Stap 5: Het Word‑document opslaan

Tot slot **slaan we het Word‑document** op schijf op. De `Save`‑methode bepaalt automatisch het bestandsformaat aan de hand van de extensie; `.docx` is het moderne OpenXML‑formaat.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Als de map niet bestaat, zal Aspose.Words een `ArgumentException` gooien. Zorg ervoor dat het pad geldig is of maak de directory vooraf aan.

## Volledig Werkend Voorbeeld

Hieronder staat het volledige, kant‑klaar programma dat alle stappen samenvoegt. Kopieer dit naar een nieuw console‑project en druk op **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Verwacht resultaat

Open `ShadowRectangle.docx` in Microsoft Word. Je zou een lichtgrijze rechthoek moeten zien met een zachte, licht verschoven schaduw, beide gerenderd met 40 % transparantie. De vorm staat op een lege pagina, klaar voor extra inhoud.

## Veelgestelde Vragen & Variaties

**Wat als ik een andere vorm nodig heb?**  
Vervang `ShapeType.Rectangle` door een andere enum‑waarde (`Ellipse`, `Triangle`, `Star`, enz.). De rest van de code blijft hetzelfde.

**Kan ik de omtrekkleur wijzigen?**  
Ja—gebruik `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` en stel eventueel `rectangleShape.StrokeWeight = 1.5;` in.

**Hoe plaats ik de vorm op een specifieke locatie op de pagina?**  
Stel `rectangleShape.WrapType = WrapType.None;` in en pas vervolgens de eigenschappen `rectangleShape.Left` en `rectangleShape.Top` aan (waarden zijn in points).

**Is het mogelijk om tekst binnen de rechthoek toe te voegen?**  
Absoluut. Na het maken van de vorm kun je `rectangleShape.AppendChild(new Paragraph(document))` aanroepen en vervolgens een `Run` met je tekst toevoegen. Vergeet niet de `rectangleShape.TextBox`‑eigenschappen in te stellen als je rijkere opmaak wilt.

## Pro‑tips & Valkuilen

- **Licentie vroeg toepassen:** Als je vergeet een licentie toe te passen, zal Aspose.Words een watermerk op de eerste pagina invoegen, wat verwarrend kan zijn tijdens het testen.
- **Prestatie‑tip:** Bij het genereren van veel documenten in een lus, hergebruik één `Document`‑instantie en roep `document.RemoveAllChildren();` aan na elke opslaan om overmatige GC‑druk te vermijden.
- **Zichtbaarheid van schaduw:** Op schermen met lage resolutie kan een subtiele schaduw onzichtbaar lijken. Verhoog `Blur` of `OffsetX/Y` voor debugging, en verlaag daarna weer voor productie.

## Volgende stappen

Nu je weet hoe je **een rechthoekvorm maakt**, **de transparantie van de vorm instelt**, **de schaduwkleur instelt**, en **het Word‑document opslaat**, overweeg dan om de tutorial uit te breiden:

- Voeg meerdere vormen toe en groepeer ze.
- Plaats de rechthoek in een tabelcel voor een rapportlay-out.
- Combineer de vorm met `DocumentBuilder.InsertHtml` om HTML‑gestylede inhoud te overlappen.
- Verken andere visuele effecten zoals `Glow` of `Reflection` voor rijkere UI‑achtige documenten.

Experimenteer, breek dingen, en verfijn vervolgens—programmerende documentgeneratie is een speeltuin waar visueel ontwerp en code samenkomen.

---

*Veel programmeerplezier! Als je tegen problemen aanloopt, laat dan een reactie achter en we lossen het samen op.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
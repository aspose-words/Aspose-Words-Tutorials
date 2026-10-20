---
category: general
date: 2026-03-01
description: Voeg snel een rechthoek toe aan PDF met Aspose.Words. Leer hoe je een
  vorm in PDF invoegt, grafische elementen aan PDF toevoegt en een PDF-document programmatisch
  maakt met een aangepaste schaduw.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: nl
og_description: Rechthoek toevoegen aan PDF met Aspose.Words. Deze tutorial laat zien
  hoe je een vorm in PDF invoegt, graphics aan PDF toevoegt en een PDF-document programmeert
  in C#.
og_title: Rechthoek toevoegen aan PDF met Aspose.Words – Complete gids
tags:
- pdf
- aspnet
- csharp
- graphics
title: Rechthoek toevoegen aan PDF met Aspose.Words – Stapsgewijze handleiding
url: /nl/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoek toevoegen aan PDF met Aspose.Words – Complete gids

Heb je ooit **rechthoek toevoegen aan PDF** moeten doen maar wist je niet welke API‑aanroep het doet? Je bent niet de enige—ontwikkelaars vragen voortdurend: “Hoe voeg ik een vorm PDF in en houd ik het bestand toch lichtgewicht?” Het goede nieuws is dat Aspose.Words het kinderspel maakt. In deze tutorial lopen we het hele proces door, van het programmeermatig maken van een PDF‑document tot het stylen van de rechthoek met een schaduw.

We zullen ook een paar extra's toevoegen: je leert hoe je **grafische elementen aan PDF toevoegen** kunt, zie de exacte stappen om **vorm PDF invoegen** te doen, en eindig met een kant‑klaar voorbeeld dat **PDF met vorm maakt**. Geen externe verwijzingen, alleen een zelfstandige oplossing die je vandaag kunt copy‑paste.

## Vereisten

- .NET 6.0 of later (Aspose.Words werkt met .NET Standard 2.0+)
- Een geldige Aspose.Words for .NET licentie of een tijdelijke evaluatiesleutel
- Visual Studio 2022 (of een IDE naar keuze)
- Basis C#‑kennis—niets bijzonders, alleen het vermogen om een console‑applicatie uit te voeren

Dat is alles. Als je dat hebt, ben je klaar om te beginnen.

## Stap 1: Een PDF‑document programmeermatig maken

Het eerste wat je doet wanneer je **rechthoek toevoegen aan PDF** wilt, is een leeg document aanmaken. Beschouw de `Document`‑klasse als een blanco canvas; alles wat je later toevoegt, leeft erin.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Waarom beginnen met een leeg document? Omdat het je volledige controle over elk element garandeert—geen verborgen paginakoppen of voetteksten waar je later mee moet worstelen.

## Stap 2: Een DocumentBuilder initialiseren om vorm PDF in te voegen

Een `DocumentBuilder` is je tekengereedschap. Het weet hoe tekst, afbeeldingen en, cruciaal voor ons, vormen geplaatst moeten worden. Zonder dit zou je zelf de low‑level knoopboom moeten manipuleren—een nachtmerrie voor de meeste ontwikkelaars.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Let op, we hebben nog geen pagina's toegevoegd. De builder maakt automatisch een pagina aan de eerste keer dat je iets invoegt, waardoor de code netjes blijft.

## Stap 3: Een rechthoekvorm invoegen – de kern van “rechthoek toevoegen aan PDF”

Nu komt het leuke gedeelte: de rechthoek invoegen. De `InsertShape`‑methode ondersteunt tientallen `ShapeType`‑waarden; we kiezen `ShapeType.Rectangle` en geven het een grootte van 200 × 100 punten.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Op dit punt bevat de PDF al een eenvoudige rechthoek. Als je het bestand nu opent, zie je een simpele doos in de linkerbovenhoek van de eerste pagina. Dat is de basis voor **grafische elementen aan PDF toevoegen**.

## Stap 4: De rechthoek stylen – een aangepaste schaduw toevoegen

Een rechthoek zonder stijl is saai. Laten we er een subtiele slagschaduw aan geven zodat hij *opvalt* wanneer de PDF wordt gerenderd. Het `ShadowFormat`‑object regelt alles van de vervagingsradius tot de doorzichtigheid.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Waarom een schaduw? Naast de esthetische verbetering kan een schaduw helpen overlappende grafische elementen te onderscheiden—iets wat je nodig kunt hebben wanneer je **grafische elementen aan PDF toevoegen** in complexere rapporten.

## Stap 5: Het bestand opslaan – de workflow “PDF met vorm maken” voltooien

De laatste regel schrijft alles naar schijf. Aspose.Words kiest automatisch de juiste PDF‑versie en embedde de benodigde resources.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Open `ShapeWithShadow.pdf` en je ziet een mooi geschaduwde rechthoek trots op de pagina staan. Dat is de volledige **PDF‑document programmeermatig maken** flow, samengevat in minder dan 30 regels code.

## Volledig werkend voorbeeld – PDF met vorm maken van begin tot eind

Hieronder staat het volledige programma dat je kunt copy‑pasten in een nieuw Console‑App‑project. Het bevat alle `using`‑statements, de `Main`‑methode, en een korte commentaar‑header voor toekomstig gebruik.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Verwacht resultaat:** een één‑pagina PDF waarin een 200 × 100‑punt rechthoek zich bevindt nabij de linkerbovenhoek, versierd met een zachte, 45‑graden schaduw. Open het bestand in een PDF‑viewer om te verifiëren.

## Veelgestelde vragen & randgevallen

### Werkt dit met andere vormtypen?
Absoluut. Vervang `ShapeType.Rectangle` door `ShapeType.Ellipse`, `ShapeType.Triangle`, of een van de 150+ opties die Aspose.Words ondersteunt. Dezelfde `ShadowFormat`‑eigenschappen zijn van toepassing.

### Wat als ik de rechthoek op een specifieke pagina nodig heb?
Na het invoegen van de vorm kun je deze naar een andere pagina verplaatsen door de `CurrentPage`‑eigenschap van de builder aan te passen vóór het aanroepen van `InsertShape`. Bijvoorbeeld:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Kan ik de vulkleur van de rechthoek wijzigen?
Zeker. Gebruik de `FillColor`‑eigenschap:

```csharp
rect.FillColor = Color.LightBlue;
```

### Hoe beïnvloedt dit de bestandsgrootte?
Het toevoegen van een eenvoudige vorm en een schaduw voegt slechts enkele kilobytes toe. Als je veel grafische elementen stapelt, overweeg dan afbeeldingen te comprimeren of vector‑gebaseerde vormen te gebruiken om de PDF slank te houden.

### Is een licentie vereist voor productie?
Aspose.Words werkt in evaluatiemodus, maar de gegenereerde PDF bevat een watermerk. Schaf een licentie aan voor onbeperkt gebruik en om het watermerk te verwijderen.

## Tips & trucs (Pro‑niveau)

- **Batchinvoer:** Als je tientallen rechthoeken nodig hebt, loop dan over een collectie coördinaten en hergebruik dezelfde `DocumentBuilder`—de prestaties blijven lineair.
- **Laagstructuur:** Stel `rect.WrapType = WrapType.Inline` in als je wilt dat de rechthoek met tekst meevloeit, of `WrapType.Square` om tekst eromheen te laten wikkelen.
- **PDF/A‑conformiteit:** Roep `doc.CompatibilityOptions.OptimizeForPdfA = true;` aan vóór het opslaan als je een archief‑vriendelijke PDF nodig hebt.

## Visuele samenvatting

![voorbeeld van rechthoek toevoegen aan pdf](https://example.com/rectangle-shadow.png "voorbeeld van rechthoek toevoegen aan pdf")

De afbeelding illustreert de uiteindelijke PDF‑lay-out: een nette rechthoek met een subtiele schaduw, precies wat onze code produceert.

## Conclusie

Je weet nu **hoe je een rechthoek aan PDF toevoegt** met Aspose.Words, hoe je **vorm PDF invoegt**, en hoe je **grafische elementen aan PDF toevoegt** met aangepaste styling—terwijl je **PDF‑document programmeermatig maakt** en eindigt met een **PDF met vorm maken** voorbeeld dat je morgen opnieuw kunt gebruiken.  

Probeer nu de rechthoek te vervangen door een logo, of combineer meerdere vormen om een eenvoudig diagram te bouwen. Je kunt ook tekstomloop, rotatie, of zelfs het insluiten van een hyperlink in de vorm verkennen. De API is zo uitgebreid dat je een statische PDF kunt omzetten in een interactieve, grafisch rijke rapportage zonder C# te verlaten.

Voel je vrij om te experimenteren, en als je tegen een probleem aanloopt, laat dan een reactie achter. Veel plezier met coderen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
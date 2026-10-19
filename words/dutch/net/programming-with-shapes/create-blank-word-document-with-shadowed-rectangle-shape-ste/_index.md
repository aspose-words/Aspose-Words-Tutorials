---
category: general
date: 2026-01-08
description: Maak een leeg Word‑document en leer hoe je een schaduw aan een rechthoekvorm
  toevoegt. Voeg Word‑bestanden met vormen in en voeg vormschaduw toe in C# met Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: nl
og_description: Maak een leeg Word‑document en zie hoe je met C# een schaduw aan een
  rechthoekvorm toevoegt. Complete code, uitleg en tips.
og_title: Maak een leeg Word‑document – Voeg een rechthoek met schaduw toe
tags:
- Aspose.Words
- C#
- Document Automation
title: Maak een leeg Word‑document met een rechthoek met schaduw – Stapsgewijze handleiding
url: /nl/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document met een rechthoek met schaduw – Complete tutorial

Heb je ooit **lege Word**‑bestanden moeten maken via code en ze vervolgens willen opvrolijken met een mooie rechthoek met schaduw? Je bent niet de enige. Veel ontwikkelaars lopen tegen een muur aan wanneer ze ontdekken dat het invoegen van vormen en het toepassen van effecten niet zo eenvoudig is als tekst typen.  

In deze gids lopen we het volledige proces door — van het aanmaken van een lege `.docx` tot **hoe je een schaduw toevoegt** aan een **rectangle shape word**‑object, en uiteindelijk **shape word**‑inhoud invoegt met een gepolijste **add shape shadow**‑effect. Aan het einde heb je een kant‑klaar fragment dat werkt met de nieuwste Aspose.Words voor .NET.

---

## Wat je nodig hebt

- **Aspose.Words for .NET** (v24.10 of nieuwer) – de bibliotheek die alles hieronder aandrijft.  
- Een .NET‑ontwikkelomgeving (Visual Studio, Rider, of de `dotnet` CLI).  
- Basiskennis van C# — als je “Hello World” kunt schrijven, ben je klaar.  

Er zijn geen extra NuGet‑pakketten nodig; alles zit in `Aspose.Words` en `System.Drawing`.

---

## Stap 1: Maak een leeg Word‑document

Het eerste wat je moet doen is een leeg `Document`‑object aanmaken. Beschouw het als een schoon canvas — net zoals je handmatig een nieuw Word‑bestand opent.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Waarom dit belangrijk is:*  
Een `Document`‑instantie vertegenwoordigt het volledige Word‑bestand. Beginnen met een leeg document geeft je volledige controle over elk element dat je later toevoegt, van alinea’s tot vormen.

---

## Stap 2: Definieer een rechthoekige vorm (Rectangle Shape Word)

Nu hebben we een vorm nodig om mee te werken. Een rechthoek is de eenvoudigste geometrie en werkt goed voor banners, placeholders of eenvoudige UI‑mock‑ups.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Waarom dit belangrijk is:*  
Door `Width` en `Height` in te stellen bepaal je de visuele voetafdruk van de vorm. `ShapeType.Rectangle` vertelt Aspose om een klassieke doos te renderen — perfect om later **add shape shadow** te demonstreren.

---

## Stap 3: Pas een schaduw toe op de vorm (How to Add Shadow)

Schaduwen geven diepte, waardoor een platte rechthoek aanvoelt als een fysiek object. Aspose.Words biedt een `Shadow`‑eigenschap waarmee je kleur, afstand, vervaging en transparantie kunt aanpassen.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Waarom dit belangrijk is:*  
Elke eigenschap beïnvloedt de visuele cue:

- **Enabled** – zonder deze worden de andere instellingen genegeerd.  
- **Color** – kies een tint die past bij het thema van je document.  
- **Distance** – hogere waarden duwen de schaduw verder weg.  
- **BlurRadius** – grotere getallen maken de schaduw zachter.  
- **Transparency** – verfijn de opacity voor subtiliteit.

Voel je vrij om te experimenteren; voor een dramatisch effect, verhoog `Distance` naar `10` en stel `Transparency` in op `0.5`.

---

## Stap 4: Voeg de vorm toe aan het document (Insert Shape Word)

Met de rechthoek klaar, hebben we een plek nodig om deze te plaatsen. De eenvoudigste locatie is de eerste alinea van de body van het document.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Waarom dit belangrijk is:*  
`FirstSection.Body.FirstParagraph` is altijd aanwezig in een nieuw `Document`. Door de vorm hier toe te voegen, garandeer je dat de vorm bovenaan het bestand verschijnt — handig voor headers of titel‑banners.

Als je de vorm ergens anders wilt invoegen, kun je een specifieke `Paragraph` of `Run` zoeken en `InsertAfter` of `InsertBefore` gebruiken.

---

## Stap 5: Sla het Word‑bestand op

De laatste stap is het in‑memory document naar schijf schrijven. Kies een map waar je schrijfrechten voor hebt, en geef het bestand een betekenisvolle naam.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Waarom dit belangrijk is:*  
`Save` schrijft een volledig conforme `.docx`‑file. Open het in Microsoft Word, LibreOffice of een andere viewer, en je ziet een rechthoek met een zachte grijze schaduw — precies wat we hebben ingesteld.

---

## Volledig werkend voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren‑plakken in een console‑applicatie. Het bevat alle `using`‑directieven, de vormcreatie, schaduwconfiguratie, invoeging en opslaan.

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

**Verwacht resultaat:**  
Open `ShadowedRectangle.docx` en je ziet een lichtgrijze rechthoek gecentreerd bovenaan de pagina met een subtiele slagschaduw van 5 pt offset. Geen extra tekst, alleen de vorm — precies wat de code produceert.

---

## Veelgestelde vragen & randgevallen

### Wat als ik een andere vorm nodig heb?

Vervang `ShapeType.Rectangle` door een andere `ShapeType`‑enumwaarde (`Ellipse`, `Triangle`, `Star`, enz.). De schaduweigenschappen werken op dezelfde manier.

### Kan ik meerdere schaduwen toevoegen?

Aspose.Words ondersteunt slechts één schaduw per vorm. Als je gelaagde effecten wilt, maak dan twee overlappende vormen met verschillende schaduwinstellingen.

### Hoe werkt dit op .NET Core?

Dezelfde API werkt op .NET 6/7/8. Zorg er alleen voor dat je het **Aspose.Words.NETCore**‑pakket (of het standaardpakket, dat nu cross‑platform is) referentieert.

### Wordt `System.Drawing` nog ondersteund op Linux?

`System.Drawing.Common` is vanaf .NET 6 alleen nog Windows‑only. Voor cross‑platform projecten gebruik je `Aspose.Drawing` (een apart NuGet) of blijf je bij kleuren die door `Aspose.Words` zelf worden gedefinieerd.

### Wat met DPI‑schaling?

De afmetingen van de vorm staan in points (1 pt = 1/72 inch). Als je pixel‑perfecte afmetingen nodig hebt voor een specifieke DPI, bereken dan points als `pixels * 72 / dpi`.

---

## Pro‑tips & valkuilen

- **Pro tip:** Stel `rectangleShape.WrapType = WrapType.Inline;` in als je wilt dat de vorm meevloeit met de tekst in plaats van erboven te zweven.  
- **Let op:** Het vergeten van `Enabled = true` voor de schaduw. De andere instellingen worden dan stilletjes genegeerd.  
- **Prestatienota:** Het toevoegen van veel vormen in een strakke lus kan traag zijn. Batch ze in één `Section` en roep `document.UpdatePageLayout()` één keer aan het einde aan.  
- **Versiecheck:** De schaduw‑API werd geïntroduceerd in Aspose.Words 20.2. Als je een oudere versie gebruikt, upgrade dan om ontbrekende eigenschappen te vermijden.

---

## Conclusie

We hebben **een leeg Word‑document** gemaakt, een **rectangle shape word** opgebouwd, geleerd **hoe je een schaduw toevoegt**, en uiteindelijk **shape word**‑inhoud ingevoegd met een gepolijste **add shape shadow**‑effect — alles met Aspose.Words voor .NET.  

Het fragment is volledig uitvoerbaar, werkt op Windows en cross‑platform .NET, en kan worden uitgebreid naar andere vormen, kleuren of zelfs geanimeerde GIF’s. Als volgende stap kun je tekst in de rechthoek plaatsen, gradient‑vullingen toepassen, of een heel rapport genereren met meerdere gestylede vormen.

Heb je meer ideeën? Probeer de grijze schaduw te vervangen door een blauwe, vergroot de blur voor een dromerige look, of combineer meerdere vormen tot een eigen logo. De mogelijkheden zijn eindeloos, en nu heb je de bouwblokken om het te realiseren.

Happy coding, en moge je documenten er altijd scherp uitzien (met precies de juiste hoeveelheid schaduw)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
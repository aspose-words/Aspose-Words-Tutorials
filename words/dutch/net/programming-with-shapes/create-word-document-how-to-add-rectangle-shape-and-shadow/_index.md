---
category: general
date: 2026-03-19
description: Maak een Word‑document in C# met Aspose.Words, leer hoe je een vorm toevoegt,
  een rechthoekige vorm toevoegt, een schaduw toepast en het document binnen enkele
  minuten als docx opslaat.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: nl
og_description: Maak een Word‑document met Aspose.Words, voeg een rechthoekvorm toe,
  pas een buitenschaduw toe en sla het document op als docx. Stapsgewijze handleiding.
og_title: Maak Word-document – Voeg rechthoekvorm en schaduw toe
tags:
- Aspose.Words
- C#
- Document Automation
title: Word-document maken – Hoe een rechthoekvorm en schaduw toe te voegen
url: /nl/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-document maken – Hoe een rechthoekvorm en schaduw toe te voegen

Altijd al een **create word document** programmatically nodig gehad en je afgevraagd waar je moet beginnen? Je bent niet de enige. Veel ontwikkelaars lopen tegen dezelfde muur aan wanneer ze voor het eerst proberen een .docx‑bestand te genereren dat aangepaste grafische elementen bevat. In deze tutorial lopen we het volledige proces door – hoe je een vorm toevoegt, specifiek een **add rectangle shape**, deze een stijlvolle **add shadow to shape** geeft, en uiteindelijk **save document as docx**.  

Aan het einde van de gids heb je een kant‑klaar C#‑fragment dat je in elk .NET‑project kunt plaatsen. Geen vage verwijzingen, alleen een compleet, uitvoerbaar voorbeeld.  

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework).  
- Aspose.Words voor .NET geïnstalleerd (NuGet‑pakket `Aspose.Words`).  
- Een basisbegrip van C#‑syntaxis – niets ingewikkelds nodig.  

Als je de bibliotheek mist, voer dan uit:

```bash
dotnet add package Aspose.Words
```

Dat is alles – geen extra SDK's, geen COM‑interop, alleen een enkele NuGet‑referentie.

---

## Stap 1: Een Word-document maken (Primair doel)

Het eerste wat we nodig hebben is een schoon canvas. Beschouw de `Document`‑klasse als een lege pagina in Microsoft Word; hij bevat secties, alinea's en alles wat je later toevoegt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Waarom beginnen met een lege `Document`? Omdat het garandeert dat er geen verborgen opmaak van een sjabloon binnensluipt. Naar mijn ervaring voorkomt een start vanaf nul mysterieuze lay‑outverschuivingen wanneer je later vormen invoegt.

---

## Stap 2: Een rechthoekvorm invoegen – Het visuele element toevoegen

Nu we een document hebben, laten we **add rectangle shape** toevoegen aan de eerste alinea. Het `Shape`‑object is veelzijdig; je kunt `ShapeType.Rectangle`, `Ellipse` of zelfs aangepaste tekeningen kiezen. Hier is de minimale code:

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

**Wat gebeurt er onder de motorkap?**  
- `ShapeType.Rectangle` vertelt Aspose dat we een eenvoudige doos willen.  
- `WrapType.Inline` zorgt ervoor dat de rechthoek meebeweegt met de tekststroom, wat meestal is wat je verwacht in een tekstverwerkingsscenario.  
- Door toe te voegen aan `FirstParagraph` vermijden we de noodzaak om handmatig een nieuwe alinea in te voegen; Aspose maakt er een voor ons aan als het document echt leeg is.

> **Pro tip:** Als je wilt dat de vorm *achter* de tekst staat, schakel `WrapType` over naar `WrapType.Transparent`. Die kleine wijziging kan een enorm visueel verschil maken.

---

## Stap 3: Een buitenste schaduw toepassen – Het uiterlijk verbeteren

Een platte rechthoek is… nou ja, plat. Het toevoegen van een **add shadow to shape** geeft diepte zonder extra afbeeldingen. Aspose’s `ShadowFormat` maakt hiervan een één‑regelige code.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Waarom die specifieke waarden gebruiken?  
- **Blur** van `5.0` geeft een subtiele, vederige rand die er professioneel uitziet op de meeste monitoren.  
- **Distance** van `3.0` en **Angle** van `45` creëren een natuurlijke lichtbron van links‑boven, een veelvoorkomende ontwerpconventie.  
- **Color.Gray** werkt zowel in lichte als donkere thema’s; je kunt het vervangen door `Color.Black` als je een sterker contrast nodig hebt.

Als je ooit een *inner* shadow nodig hebt (denk aan een verzonken knop), verander dan `ShadowType.OuterShadow` naar `ShadowType.InnerShadow`. Dezelfde eigenschappen blijven van toepassing.

---

## Stap 4: Het document opslaan als DOCX – Je werk behouden

Alle pret is leuk, maar uiteindelijk wil je een bestand op schijf hebben. De **save document as docx** stap is eenvoudig:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Een paar opmerkingen:  
- De `SaveFormat.Docx`‑enum garandeert het moderne Office Open XML‑formaat, dat compatibel is met Word 2007+.  
- Als je het bestand direct naar een web‑respons wilt streamen, vervang dan het bestandspad door een `MemoryStream` en schrijf het naar de HTTP‑respons.

Na het uitvoeren van de code, open `ShadowedRectangle.docx` in Microsoft Word. Je zou een grijze rechthoek met een zachte schaduw moeten zien, inline met de eerste alinea – precies wat we wilden bereiken.

---

## Hoe een vorm toe te voegen – Alternatieve benaderingen

Het bovenstaande voorbeeld gebruikt de *inline*‑benadering, maar soms wil je een vorm die boven de tekst zweeft. Dan komt **how to add shape** met verschillende omhulsels in beeld.

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

Hier hebben we `WrapType` gewijzigd naar `Square` en de vorm gecentreerd op de pagina. Dit patroon is handig voor omslagpagina's of decoratieve banners. Onthoud: zwevende vormen vergroten de bestandsgrootte een beetje omdat Word extra positioneringsgegevens opslaat.

---

## Verwachte output & verificatie

Wanneer je het gegenereerde bestand opent, zou je moeten zien:

- Een enkele alinea met een grijze rechthoek.  
- De rechthoek meet ongeveer 2,8 × 1,4 inch.  
- Een subtiele buitenste schaduw die naar rechtsonder is verschoven.  

Als de vorm *buiten* de alinea verschijnt, controleer dan de `WrapType`. Als de schaduw te hard lijkt, verlaag dan de `Blur`‑waarde of wissel de `Color` naar een lichtere tint.

---

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Vorm verdwijnt na opslaan | `WrapType` ingesteld op `Inline` maar alinea werd verwijderd | Zorg dat de alinea bestaat; gebruik `doc.FirstSection.Body.FirstParagraph` om dit te garanderen. |
| Schaduw ziet er gepixeld uit | Een zeer lage `Blur`‑waarde gebruiken | Verhoog `Blur` tot minstens `3.0` voor vloeiende randen. |
| Bestandsgrootte stijgt enorm | Veel hoge resolutie‑afbeeldingen toevoegen naast vormen | Gebruik `doc.RemoveUnusedResources()` vóór het opslaan als je afbeeldingen hebt toegevoegd. |
| Kleur wordt niet weergegeven in donkere modus | Een donkere `Color` voor de vorm zelf gebruiken | Kies een contrasterende kleur (bijv. `Color.White`) voor betere zichtbaarheid. |

---

## Volledig werkend voorbeeld

Hieronder staat de volledige, kant‑klaar te kopiëren code die alles bevat wat we hebben besproken. Voel je vrij om het als console‑applicatie uit te voeren.

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

**Uitleg van elk blok** staat inline als commentaar, wat zowel SEO‑lezers als AI‑assistenten die van zelf‑bevatte antwoorden houden, tevreden stelt.

---

## Conclusie

We hebben zojuist **create word document** vanaf nul gemaakt, geleerd **how to add shape**, specifiek een **add rectangle shape**, het een **add shadow to shape** gegeven, en uiteindelijk **save document as docx**. De stappen zijn eenvoudig, de code is compact, en het resultaat ziet er gepolijst uit.  

Als je klaar bent om verder te gaan, probeer dan de rechthoek te vervangen door een aangepaste afbeelding, experimenteer met verschillende schaduwkleur­en, of genereer een volledig rapport met meerdere vorm‑secties. De Aspose.Words‑API is flexibel genoeg om alles aan te kunnen, van facturen tot marketingbrochures.

Heb je vragen over andere vorm‑typen of heb je hulp nodig bij het integreren hiervan in een ASP.NET Core‑service? Laat een reactie achter hieronder, en happy coding! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
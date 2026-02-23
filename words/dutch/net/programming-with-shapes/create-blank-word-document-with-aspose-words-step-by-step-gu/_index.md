---
category: general
date: 2026-02-23
description: Maak een leeg Word‑document met C# en Aspose.Words. Leer hoe je een rechthoekvorm
  toevoegt, een schaduw aan het woord toevoegt, en het Word‑document met de vorm in
  enkele minuten opslaat.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: nl
og_description: Maak snel een leeg Word‑document. Deze gids laat zien hoe je een rechthoekvorm
  toevoegt, een schaduw aan het woord toevoegt, en het Word‑document met vorm opslaat
  met behulp van Aspose.Words.
og_title: Maak een leeg Word‑document – Volledige C#‑tutorial
tags:
- Aspose.Words
- C#
- Document Automation
title: Maak een leeg Word‑document met Aspose.Words – Stapsgewijze handleiding
url: /nl/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

- Keep the backtop button shortcode unchanged.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document – Volledige C#‑tutorial

Heb je je ooit afgevraagd hoe je **een leeg Word‑document** programmatically kunt maken zonder Microsoft Word te openen? Je bent niet de enige. In veel automatiseringsprojecten hebben we een nieuw .docx‑bestand nodig, plaatsen we er een vorm op, geven die vorm een mooie schaduw, en **slaan we Word met vorm** op voor later gebruik.  

In deze gids lopen we precies dat door—beginnend met een leeg document, **een rechthoekvorm toevoegen**, een **add shadow word**‑effect configureren, en uiteindelijk het bestand opslaan. Aan het einde heb je een compleet, uitvoerbaar fragment dat je in elke .NET‑console‑app kunt plakken. Geen mysterie, geen ontbrekende stukjes.

## Wat je nodig hebt

- **Aspose.Words for .NET** (een recente versie, bijv. 24.10).  
- .NET 6 of later (de code werkt ook met .NET Framework 4.7+).  
- Een basis C#‑IDE—Visual Studio, Rider, of zelfs VS Code met de C#‑extensie.  

Dat is alles. Geen extra NuGet‑pakketten naast Aspose.Words, en geen Word‑installatie vereist.

---

## Stap 1: Een leeg Word‑document maken

Het eerste wat je doet wanneer je een **leeg Word‑document** wilt **maken**, is de `Document`‑klasse instantieren. Zie het als een schoon canvas dat Aspose.Words je aanbiedt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Waarom dit belangrijk is:** Het `Document`‑object bevat alle secties, alinea’s en vormen. Beginnen met een lege instantie garandeert dat je controle hebt over elk element dat later wordt toegevoegd.

---

## Stap 2: Een rechthoekvorm aan het document toevoegen

Nu we een schoon document hebben, laten we een **rechthoekvorm toevoegen**. Een rechthoek is een eenvoudige `Shape` met `ShapeType.Rectangle`. Je kunt natuurlijk andere types kiezen, maar een rechthoek werkt prima voor demonstratie.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Pro‑tip:** Als je je ooit afvraagt **hoe je een vorm toevoegt** die geen rechthoek is, wijzig je gewoon `ShapeType.Rectangle` naar een andere enum‑waarde zoals `ShapeType.Ellipse` of `ShapeType.Polygon`. De rest van de code blijft gelijk.

---

## Stap 3: Een aangepaste schaduw voor de vorm configureren

Een eenvoudige rechthoek ziet er een beetje saai uit, dus we **voegen een add shadow word** toe om het meer te laten opvallen. Aspose.Words biedt een `ShadowFormat`‑object met veel eigenschappen.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Waarom dit belangrijk is:** De schaduw geeft een subtiel diepte‑effect, vooral wanneer het document op een scherm wordt bekeken. Pas `OffsetX`, `OffsetY` en `BlurRadius` aan om bij je ontwerp te passen.

---

## Stap 4: De vorm in het document invoegen

Met de vorm klaar, moeten we deze ergens plaatsen. De eenvoudigste plek is de eerste alinea van de eerste sectie. Als het document nog geen alinea’s heeft, maakt Aspose er automatisch één aan.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Randgeval:** Als je de vorm op een specifieke locatie wilt invoegen (bijv. na een bepaalde kop), zoek dan de doel‑`Paragraph` via `document.GetChildNodes(NodeType.Paragraph, true)` en gebruik `InsertAfter` of `InsertBefore` naar behoefte.

---

## Stap 5: Het Word‑document met de vorm opslaan

Tot slot **slaan we Word met vorm** op schijf. De `Save`‑methode bepaalt automatisch het formaat aan de hand van de bestandsextensie.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **Wat je zult zien:** Open `shadowedRectangle.docx` in Word (of een andere compatibele viewer) en je ziet een grijze rechthoek met een zachte schaduw bovenaan de eerste pagina.

---

## Volledig werkend voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren‑plakken in een console‑app. Het bevat alle using‑directives, commentaren en de exacte stappen die we hebben besproken.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Voer het programma uit, navigeer naar `YOUR_DIRECTORY` en open het gegenereerde `shadow.docx`. Je zou de rechthoek met een subtiele grijze schaduw moeten zien—precies wat we wilden bereiken.

---

## Veelgestelde vragen & tips

### Hoe verander ik de kleur van de vorm?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Stel gewoon `FillColor` in voordat je de vorm toevoegt.

### Wat als ik meerdere vormen op dezelfde pagina nodig heb?
Maak extra `Shape`‑objecten en voeg elk toe aan dezelfde alinea of aan verschillende alinea’s. Je kunt ook de lay‑out regelen met `WrapType` en `RelativeHorizontalPosition`.

### Kan ik exporteren naar PDF terwijl de schaduw behouden blijft?
Zeker. Gebruik `document.Save("output.pdf")`—Aspose.Words behoudt het schaduweffect bij de PDF‑conversie.

### Werkt dit op .NET Core?
Ja. Aspose.Words is cross‑platform; dezelfde code draait op .NET Core, .NET 5+, en .NET Framework.

### Hoe voeg ik een vorm toe zonder alinea?
Je kunt de vorm direct aan een `Run` of aan een `Story` toevoegen. Voor preciezere positionering stel je `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` in en pas je de eigenschappen `Left`/`Top` aan.

---

## Visueel resultaat

![Rectangle shape with gray shadow in a Word document – add shadow word example](https://example.com/placeholder-image.png "add shadow word voorbeeld")

*Afbeeldings‑alt‑tekst bevat het secundaire zoekwoord **add shadow word** om SEO‑vereisten te vervullen.*

---

## Conclusie

We hebben zojuist laten zien hoe je **een leeg Word‑document** maakt, **een rechthoekvorm** toevoegt, een **add shadow word**‑effect toepast, en uiteindelijk **Word met vorm** opslaat met Aspose.Words for .NET. Het proces is eenvoudig: instantiate een `Document`, bouw een `Shape`, pas de `ShadowFormat` aan, voeg de vorm toe, en roep `Save` aan.  

Vanaf hier kun je experimenteren—probeer verschillende vormtypes, speel met kleuren, of stapel meerdere vormen. Als je dit document wilt combineren met bestaande inhoud, laad dan gewoon het bestaande bestand via `new Document("existing.docx")` en volg dezelfde stappen.  

Heb je meer vragen? Laat een reactie achter, en happy coding!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
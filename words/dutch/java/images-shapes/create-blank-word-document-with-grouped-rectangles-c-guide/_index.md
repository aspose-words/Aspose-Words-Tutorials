---
category: general
date: 2026-07-23
description: Maak een leeg Word‑document en voeg een rechthoekvorm toe in C#. Leer
  hoe je vormen kunt invoegen en vormen kunt groeperen in Word met behulp van Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: nl
lastmod: 2026-07-23
og_description: Maak een leeg Word‑document in C# en leer hoe je vormen kunt invoegen,
  een rechthoekvorm kunt toevoegen en vormen kunt groeperen in Word met Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Maak een leeg Word‑document met gegroepeerde rechthoeken – C#‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Maak een leeg Word‑document met gegroepeerde rechthoeken – C#‑gids
url: /nl/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document met gegroepeerde rechthoeken – C#‑handleiding

Heb je ooit een **leeg Word‑document maken** moeten, dat al een set vormen bevat, maar wist je niet hoe je ze netjes kunt groeperen? Je bent niet de enige. In veel rapportage‑ of sjabloongeneratiescenario’s wil je een schoon canvas met een paar rechthoeken die fungeren als tijdelijke aanduidingen, en je wilt dat ze samen als één geheel bewegen.

In deze tutorial lopen we stap voor stap door hoe je een **leeg Word‑document maakt**, een **rechthoekvorm toevoegt**, en vervolgens **vormen groeperen in Word** met de Aspose.Words‑bibliotheek. Aan het einde heb je een kant‑klaar `.docx`‑bestand waarin de twee rechthoeken deel uitmaken van een groep, zodat elke latere positionering of grootte‑aanpassing beide tegelijk beïnvloedt.  

We beantwoorden ook de veelvoorkomende vragen “**hoe vormen in te voegen**” en “**hoe vormen te groeperen**” die op forums en Stack Overflow opduiken. Geen externe documentatie nodig – alles wat je nodig hebt staat hier.

---

## Prerequisites

- .NET 6 of later (de code compileert ook met .NET Core)  
- Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`)  
- Een basisbegrip van C#‑syntaxis (als je een “Hello World” hebt geschreven, ben je klaar)  

Als je Aspose.Words nog niet hebt geïnstalleerd, voer dan uit:

```bash
dotnet add package Aspose.Words
```

Dat is alles – geen extra DLL’s, geen COM‑interop, alleen een nette NuGet‑referentie.

---

## Step 1: Create blank word document and initialize the builder

Het eerste wat we doen is een leeg `Document`‑object aanmaken. Beschouw het als een vers vel papier. Vervolgens koppelen we een `DocumentBuilder`, het handige hulpmiddel dat Aspose biedt voor het invoegen van inhoud.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** Zonder een `DocumentBuilder` zou je de low‑level node‑boom handmatig moeten manipuleren, wat foutgevoelig is. De builder abstraheert de XML‑complexiteit van een `.docx`‑bestand.

---

## Step 2: How to insert shapes – add a group container first

Aspose laat je een *group shape* invoegen die later andere vormen kan bevatten. Dit is de basis voor **vormen groeperen in Word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Pro tip:** De groep zelf is onzichtbaar totdat je kind‑vormen toevoegt, dus je ziet geen artefacten in het resulterende document tot de volgende stap.

---

## Step 3: Add rectangle shape – the actual visible objects

Nu **voegen we twee keer een rechthoekvorm toe**, elk met zijn eigen afmetingen. De `InsertShape`‑methode neemt een `ShapeType` en afmetingen in points (1 pt ≈ 1/72 inch).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Why rectangles?** Ze zijn de eenvoudigste geometrische vorm, perfect als tijdelijke aanduidingen, knop‑achtige UI‑mockups, of eenvoudige grafische elementen.

---

## Step 4: How to group shapes – attach rectangles to the group

Met de rechthoeken aangemaakt, **groeperen we de vormen** door ze als kinderen aan de eerder ingevoegde groepsvorm toe te voegen.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **What happens under the hood?** De groepsvorm wordt het bovenliggende knooppunt in de XML‑boom van het document. Het verplaatsen van de groep verplaatst beide rechthoeken samen, waarbij hun relatieve posities behouden blijven.

---

## Step 5: Save the document – you now have a grouped‑shape Word file

Tot slot slaan we het document op schijf op. Pas het pad aan naar een locatie die op jouw machine bestaat.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Dat is het volledige programma. Voer het uit, open `GroupShape.docx`, en je ziet twee rechthoeken naast elkaar. Als je er één selecteert, wordt de hele groep gemarkeerd – precies wat **vormen groeperen in Word** zou moeten doen.

---

## Full source code in one place

Voor het gemak staat hier het complete, kant‑klaar voorbeeld:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Verwachte output:** Het openen van `GroupShape.docx` toont een lege pagina met twee rechthoeken die gegroepeerd zijn. Het selecteren van één rechthoek selecteert automatisch de andere, wat bevestigt dat de groepering geslaagd is.

---

## Common questions & edge‑case handling

### What if I need more than two shapes?

Blijf gewoon `builder.InsertShape(...)` en `group.AppendChild(...)` aanroepen voor elke nieuwe vorm. De groep kan een willekeurig aantal kinderen bevatten.

### Can I set fill colour or border on the rectangles?

Zeker. Nadat je een rechthoek hebt aangemaakt kun je `FillColor`, `OutlineColor` en `LineWidth` aanpassen:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### How do I move the whole group after it’s been created?

Gebruik de eigenschappen `Left` en `Top` van de groep, gemeten in points:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### What about scaling the group?

Stel `group.Width` en `group.Height` in of gebruik `group.ScaleX` / `group.ScaleY`. De kind‑rechthoeken behouden hun verhoudingen ten opzichte van de groep.

### Does this work with older .doc files?

Aspose.Words abstraheert het bestandsformaat, dus dezelfde code werkt voor `.doc` en `.docx`. De enige beperking is dat sommige nieuwere vorm‑features mogelijk worden teruggebracht bij het opslaan naar het oudere binaire formaat.

---

## Pro tips for production‑ready code

- **Dispose of resources** – Plaats `Document` in een `using`‑block als je met grote bestanden werkt om het geheugen tijdig vrij te geven.  
- **Error handling** – Vang `Aspose.Words.Fonts.FontSettingsException` op als je van plan bent aangepaste lettertypen in te sluiten.  
- **Performance** – Schakel bij het invoegen van veel vormen tijdelijk lay‑outupdates uit met `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` en schakel ze daarna weer in.

---

## Conclusion

Je weet nu **hoe je een leeg Word‑document maakt**, **een rechthoekvorm toevoegt**, en **vormen groeperen in Word** met Aspose.Words in C#. Het voorbeeld behandelt de essentiële “**hoe vormen in te voegen**” en “**hoe vormen te groeperen**” stappen, legt uit waarom elke regel bestaat, en raakt zelfs aan aanpassing, randgevallen en best practices.

Vervolgens kun je **hoe je afbeeldingen invoegt**, **tekst toevoegt binnen gegroepeerde vormen**, of **het document exporteert naar PDF** verkennen – allemaal volgens hetzelfde patroon van `DocumentBuilder` en vormmanipulatie. Blijf experimenteren; de Aspose‑API is rijk genoeg om bijna elke Word‑automatiseringsscenario te ondersteunen dat je kunt bedenken.

Happy coding, and feel free to drop a comment if you hit any snags!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step‑by‑step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
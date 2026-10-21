---
category: general
date: 2026-07-19
description: Stel placeholder‑tekst in een StructuredDocumentTag in met Aspose.Words.
  Leer hoe je een besturingselement toevoegt, naar het besturingselement verplaatst
  en een tagattribuut instelt in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- move to control
- how to add control
- how to create sdt
- set tag attribute
language: nl
lastmod: 2026-07-19
og_description: Stel tijdelijke tekst in een StructuredDocumentTag in met Aspose.Words.
  Volg deze stapsgewijze handleiding om een besturingselement toe te voegen, naar
  het besturingselement te gaan en het tag‑attribuut in te stellen.
og_image_alt: Screenshot showing a Word document with placeholder text inside a content
  control created by Aspose.Words
og_title: Placeholder-tekst instellen in Aspose.Words – Snelle C#‑handleiding
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  headline: Set Placeholder Text in Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  name: Set Placeholder Text in Aspose.Words – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6+ (or .NET Framework 4.7.2) – the code works on any recent runtime.
      - Aspose.Words for .NET (NuGet package `Aspose.Words` version 23.12 or later).
      - A basic understanding of C# and Visual Studio (or your favorite IDE).'
  - name: Expected Result
    text: 'Open `SDTExample.docx` in Microsoft Word:'
  - name: What if I need a **dropdown** instead of plain text?
    text: Replace `SdtType.PlainText` with `SdtType.DropDownList` and populate the
      `ListItems` collection. The rest of the workflow—`InsertNode`, `MoveTo`, `SetTagAttribute`—remains
      the same.
  - name: Can I **set the tag attribute** after insertion?
    text: 'Absolutely. The `Tag` property can be modified at any time:'
  - name: How do I **find a control later** in a large document?
    text: Use the `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` method
      and filter by `Tag` or `Title`. This is handy when you need to replace placeholder
      text in bulk.
  - name: What if I want the placeholder to appear in **all languages**?
    text: Aspose.Words supports localized placeholder text via the `PlaceholderName`
      property. Set it to a resource string that varies per culture.
  type: HowTo
tags:
- Aspose.Words
- C#
- ContentControl
title: Placeholder‑tekst instellen in Aspose.Words – Complete C#‑gids
url: /nl/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Placeholder‑tekst instellen in Aspose.Words – Complete C#‑gids

Heb je je ooit afgevraagd hoe je **placeholder‑tekst** kunt instellen in een Word‑contentcontrol met Aspose.Words? Je bent niet de enige. Of je nu een document‑generatie‑engine bouwt of gewoon een herbruikbare sjabloon nodig hebt, weten hoe je een control toevoegt, naar de control verplaatst en een tag‑attribuut instelt, is essentieel.

In deze tutorial lopen we een real‑world voorbeeld door dat precies laat zien hoe je een SDT (StructuredDocumentTag) maakt, er een tag aan geeft, placeholder‑tekst instelt en standaardinhoud schrijft — allemaal in plain C#. Aan het einde heb je een kant‑klaar fragment dat je in elk .NET‑project kunt plaatsen.

## Wat je zult leren

- Hoe je **SDT** (StructuredDocumentTag) programmatically maakt.
- De juiste manier om **placeholder‑tekst** in te stellen zodat gebruikers nuttige aanwijzingen zien.
- Het gebruik van **move to control** om de cursor binnen de nieuw toegevoegde control te positioneren.
- Een **tag‑attribuut** toewijzen voor latere identificatie.
- Het document opslaan en het resultaat verifiëren.

### Vereisten

- .NET 6+ (of .NET Framework 4.7.2) – de code werkt op elke recente runtime.
- Aspose.Words for .NET (NuGet‑package `Aspose.Words` versie 23.12 of later).
- Een basisbegrip van C# en Visual Studio (of je favoriete IDE).

Er zijn geen andere externe libraries nodig.

## Stap 1: Initialiseert het Document en de Builder

Allereerst – maak een lege `Document` en een `DocumentBuilder`. De builder is je penseel; het document is het doek.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Create a brand‑new blank document.
Document document = new Document();

// DocumentBuilder lets us insert text, tables, and controls.
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

> **Waarom dit belangrijk is:** Beginnen met een schoon `Document` garandeert dat de placeholder die later wordt ingesteld niet conflicteert met bestaande inhoud.

## Stap 2: Maak de StructuredDocumentTag (SDT)

Nu laten we **hoe je een sdt maakt** – een contentcontrol die platte tekst, data, dropdowns, enz. kan bevatten. In dit geval hebben we een plain‑text control nodig.

```csharp
// Create a plain‑text StructuredDocumentTag (content control).
StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
    document, SdtType.PlainText, true);

// Give the control a friendly name and a tag for later lookup.
plainTextSdt.Title = "CustomerName";
plainTextSdt.Tag   = "CustomerNameTag";

// Here’s the crucial part: set the placeholder text that the user sees.
plainTextSdt.PlaceholderText = "Enter name here";
```

> **Pro tip:** De `PlaceholderText`‑eigenschap is wat de gebruiker ziet voordat hij iets typt. Het verschilt van de standaardtekst die je later eventueel schrijft.

## Stap 3: Voeg de Control toe aan het Document

Met de SDT klaar, moeten we **hoe je een control toevoegt** aan het document. De `InsertNode`‑methode doet precies dat.

```csharp
// Insert the content control at the current cursor position.
docBuilder.InsertNode(plainTextSdt);
```

> **Wat er onder de motorkap gebeurt:** `InsertNode` plaatst de SDT als kind van de huidige alinea, waarbij eventuele omliggende opmaak behouden blijft.

## Stap 4: Verplaats naar de Control en Schrijf Standaardinhoud (optioneel)

Als je de control vooraf wilt vullen met een waarde (bijv. een standaardklantnaam), verplaats je eerst **naar de control** en schrijf je daarna.

```csharp
// Optionally clear the placeholder and write a default name.
plainTextSdt.RemoveAllChildren();          // Remove the placeholder node.
docBuilder.MoveTo(plainTextSdt);           // Move cursor inside the SDT.
docBuilder.Write("John Doe");              // Write default text.
```

> **Waarom we de placeholder verwijderen:** De placeholder is een visuele aanwijzing, geen feitelijke documentinhoud. Verwijderen vóór het schrijven zorgt ervoor dat het uiteindelijke document alleen de echte tekst bevat.

## Stap 5: Sla het Document op

Tot slot, persisteer het bestand op schijf. Je kunt het ook streamen naar een response in een web‑app – vervang gewoon de `Save`‑aanroep.

```csharp
// Save the Word document to the desired location.
document.Save("C:/Temp/SDTExample.docx");
```

### Verwacht Resultaat

Open `SDTExample.docx` in Microsoft Word:

- Je ziet een plain‑text contentcontrol met de titel **CustomerName**.
- De control toont “Enter name here” als vage placeholder‑tekst (als je geen standaardinhoud hebt geschreven).
- Als je de regel `Write("John Doe")` hebt behouden, verschijnt “John Doe” binnen de control en verdwijnt de placeholder.

## Volledig Werkend Voorbeeld

Hieronder staat het complete, copy‑and‑paste‑klare programma. Het bevat alle bovenstaande stappen, plus een paar defensieve controles.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise document and builder.
        Document document = new Document();
        DocumentBuilder docBuilder = new DocumentBuilder(document);

        // 2️⃣ Create a plain‑text SDT (content control).
        StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
            document, SdtType.PlainText, true);
        plainTextSdt.Title = "CustomerName";
        plainTextSdt.Tag   = "CustomerNameTag";
        plainTextSdt.PlaceholderText = "Enter name here";

        // 3️⃣ Insert the control into the document.
        docBuilder.InsertNode(plainTextSdt);

        // 4️⃣ (Optional) Move to the control and set default text.
        plainTextSdt.RemoveAllChildren();   // Clear placeholder.
        docBuilder.MoveTo(plainTextSdt);    // Move cursor inside.
        docBuilder.Write("John Doe");       // Write default value.

        // 5️⃣ Save the file.
        string outputPath = @"C:\Temp\SDTExample.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Voer het programma uit, open het gegenereerde bestand, en je ziet alles precies werken zoals beschreven.

## Veelgestelde Vragen & Randgevallen

### Wat als ik een **dropdown** nodig heb in plaats van plain text?

Vervang `SdtType.PlainText` door `SdtType.DropDownList` en vul de `ListItems`‑collectie. De rest van de workflow — `InsertNode`, `MoveTo`, `SetTagAttribute` — blijft gelijk.

### Kan ik de **tag‑attribuut** na invoegen instellen?

Absoluut. De `Tag`‑eigenschap kan op elk moment worden aangepast:

```csharp
plainTextSdt.Tag = "NewTagValue";
```

Vergeet alleen niet het document opnieuw op te slaan zodat de wijziging wordt vastgelegd.

### Hoe vind ik later een control in een groot document?

Gebruik de methode `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` en filter op `Tag` of `Title`. Handig wanneer je placeholder‑tekst in bulk wilt vervangen.

```csharp
foreach (StructuredDocumentTag sdt in document.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    if (sdt.Tag == "CustomerNameTag")
    {
        // Do something with this control.
    }
}
```

### Wat als ik wil dat de placeholder in **alle talen** verschijnt?

Aspose.Words ondersteunt gelokaliseerde placeholder‑tekst via de `PlaceholderName`‑eigenschap. Stel deze in op een resource‑string die per cultuur varieert.

## Tips & Tricks (Pro Tips)

- **Herbruik dezelfde SDT** in meerdere documenten door deze te clonen (`plainTextSdt.Clone(true)`), en de kloon vervolgens in te voegen waar nodig.
- **Vermijd dubbele tags**; ze maken latere zoekopdrachten ambigu. Houd tags uniek per document.
- **Performance tip:** Als je duizenden documenten genereert, hergebruik dan één `Document`‑instantie als sjabloon en vervang alleen de placeholder‑tekst. Dit vermindert de overhead van objectcreatie.

## Conclusie

We hebben alles behandeld wat je nodig hebt om **placeholder‑tekst** in een Aspose.Words StructuredDocumentTag in te stellen, van het maken van de control tot het verplaatsen ernaartoe, het schrijven van standaardinhoud en het toewijzen van een tag‑attribuut. Met deze kennis kun je dynamische Word‑sjablonen bouwen die gebruikers begeleiden, invoerregels afdwingen en gemakkelijk te onderhouden zijn.

Klaar voor de volgende uitdaging? Probeer de plain‑text SDT te vervangen door een **date picker** of een **combo box**, of verken hoe je SDT’s kunt binden aan XML‑datasources voor nog rijkere documentautomatisering.

Happy coding, en moge je documenten altijd perfect getemplateerd zijn!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Set Content Control Style](/words/hindi/net/programming-with-sdt/set-content-control-style/)
- [Set Content Control Color](/words/hindi/net/programming-with-sdt/set-content-control-color/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
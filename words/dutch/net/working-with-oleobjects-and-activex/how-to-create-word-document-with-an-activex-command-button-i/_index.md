---
category: general
date: 2026-09-05
description: Maak een Word‑document met Aspose.Words C# en leer hoe je een ActiveX‑opdrachtknop
  invoegt, de knopgrootte instelt en interactieve functionaliteit aan de knop toevoegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: nl
lastmod: 2026-09-05
og_description: Maak een Word-document in C# en voeg een ActiveX-opdrachtknop toe.
  Deze tutorial laat zien hoe je de knopgrootte instelt en interactieve knopfuncties
  toevoegt.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Maak een Word‑document met een ActiveX‑opdrachtknop in C# – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Hoe maak je een Word‑document met een ActiveX‑opdrachtknop in C#
url: /nl/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word‑document te maken met een ActiveX‑opdrachtknop in C#

Als je **een Word‑document** programmatisch wilt **maken** en een klikbaar UI‑element wilt insluiten, laat deze gids je precies zien hoe. Met Aspose.Words voor .NET kun je **een Word‑document maken**, **een opdrachtknop toevoegen**, en het uiterlijk ervan regelen – alles zonder Microsoft Word te openen.

Je leert **hoe je ActiveX**‑besturingselementen invoegt, **de knopgrootte instelt**, en de knop laat functioneren als een interactieve UI‑component. Er is geen voorafgaande ervaring met COM of VBA vereist; alleen een .NET‑ontwikkelomgeving en de Aspose.Words‑bibliotheek.

## Wat je zult bereiken

Aan het einde van deze tutorial kun je:

* **Een Word‑document** vanaf nul maken met C#.
* **Een ActiveX‑opdrachtknop** (de klassieke “Click Me”‑knop) invoegen.
* **De knopgrootte** en positie nauwkeurig instellen.
* Optioneel eenvoudige **interactieve knop**‑logica toevoegen (bijv. een macro‑placeholder).
* Het bestand opslaan als een `.docx` dat geopend kan worden in Microsoft Word of een compatibele viewer.

### Voorvereisten

| Vereiste | Reden |
|----------|-------|
| .NET 6.0 of later | Biedt de runtime voor C#‑code. |
| Aspose.Words for .NET (nieuwste versie) | Levert de `Document`, `DocumentBuilder` en `Forms2OleControl` API’s die in het voorbeeld worden gebruikt. |
| Visual Studio 2022 (of een andere C#‑IDE) | Maakt het eenvoudig om het voorbeeld te compileren en uit te voeren. |
| Basiskennis van C# | Nodig om de code‑stroom te begrijpen. |

> **Pro tip:** Als je een trial‑versie van Aspose.Words gebruikt, zorg er dan voor dat je de licentie instelt voordat je de code uitvoert om evaluatiewatermerken te vermijden.

## Hoe een Word‑document te maken – algemene workflow

Het proces bestaat uit vier logische stappen:

1. **Initialiseer een nieuw document** en een `DocumentBuilder` om het te bewerken.  
2. **Voeg een ActiveX‑opdrachtknop in** met `InsertForms2OleControl`.  
3. **Configureer de knop** – bijschrift, grootte en positie.  
4. **Sla** het document op schijf.

Elke stap wordt hieronder in een eigen sectie uitgelegd.

![Word-document met een ActiveX-knop](/images/activex-button.png "Schermafbeelding van een Word-document dat een ActiveX-opdrachtknop bevat, gemaakt met C#")

## Hoe ActiveX‑opdrachtknop in te voegen

Het **hoe‑te‑invoegen‑activex**‑deel begint met de `InsertForms2OleControl`‑methode. Deze methode maakt een COM‑gebaseerd besturingselement dat Word behandelt als een ActiveX‑object.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Waarom dit werkt:** `OleControlType.CommandButton` vertelt Aspose.Words om de klassieke VB‑stijlknop te maken. De grootte en locatie worden uitgedrukt in points (1 point = 1/72 inch), wat precieze controle over de lay-out geeft.

## Hoe opdrachtknop toe te voegen en knopgrootte in te stellen

Nadat het besturingselement is ingevoegd, kun je de visuele eigenschappen aanpassen. De **voeg‑opdrachtknop‑toe**‑stap behandelt ook **knopgrootte instellen**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Uitleg:**  

* `Caption` is het label dat op de knop wordt weergegeven.  
* `Width` en `Height` laten je **knopgrootte instellen** na de initiële invoeging – handig wanneer de grootte afhankelijk is van runtime‑data.  
* `Left` en `Top` verplaatsen het besturingselement zonder het document opnieuw te maken.

> **Veelvoorkomende valkuil:** Het gebruik van pixels in plaats van points zal ervoor zorgen dat de knop te klein of te groot verschijnt. Converteer pixelwaarden altijd (`px * 72 / DPI`) als je vanuit schermmetingen werkt.

## Hoe interactieve knop toe te voegen (optioneel)

Een ActiveX‑knop kan een macro uitvoeren wanneer erop geklikt wordt, maar het insluiten van VBA‑code vanuit C# valt buiten de scope van een puur Aspose.Words‑werkproces. In plaats daarvan kun je een placeholder‑eigenschap toevoegen die Word herkent als een macro‑naam.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Wanneer de gebruiker het gegenereerde `.docx` in Word opent, zal een klik op de knop proberen `MyMacroName` uit te voeren. Als de macro niet bestaat, vraagt Word de gebruiker om deze aan te maken.

**Waarom je dit zou gebruiken:** Voor bedrijfsformulieren waarbij een macro velden invult, hoeft de C#‑code alleen de knop te plaatsen; de macro‑logica leeft in het VBA‑project van het document.

## Document opslaan en resultaat verifiëren

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Verwachte output:** Het openen van `CommandButton.docx` in Microsoft Word toont een knop met het label **Click Me** die 100 pts vanaf de linkermarge en 120 pts vanaf de bovenkant is gepositioneerd. De afmetingen van de knop zijn **200 pts × 80 pts**. Een klik op de knop activeert de macro‑placeholder (indien aanwezig).

## Volledig werkend voorbeeld

Hieronder staat het complete, uitvoerbare programma dat alles samenbrengt. Kopieer het naar een nieuw Console‑App‑project, voeg het Aspose.Words‑NuGet‑pakket toe, en voer het uit.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Voer het programma uit en open vervolgens het gegenereerde bestand. Je ziet de **interactieve knop** klaar voor verdere aanpassing.

## Veelgestelde vragen

| Vraag | Antwoord |
|-------|----------|
| **Werkt dit met .NET Core?** | Ja. Aspose.Words ondersteunt .NET Standard, dus dezelfde code draait op .NET 5/6/7. |
| **Kan ik andere ActiveX‑besturingselementen gebruiken (bijv. CheckBox)?** | Absoluut. Vervang `OleControlType.CommandButton` door `OleControlType.CheckBox`, `OleControlType.OptionButton`, enz. |
| **Wat als ik een grotere knop nodig heb op een liggende pagina?** | Pas de eigenschappen `Width`, `Height`, `Left` en `Top` proportioneel aan. Onthoud dat points gelijk blijven, ongeacht de paginarichting. |
| **Is een macro vereist om de knop klikbaar te maken?** | Nee. De knop functioneert volledig als UI‑element; een macro voegt alleen aangepast gedrag toe bij klikken. |

## Conclusie

Je weet nu hoe je **een Word‑document** maakt met Aspose.Words, **een opdrachtknop toevoegt**, **knopgrootte instelt**, en optioneel de knop koppelt aan een macro voor **interactieve knop**‑gedrag. Deze aanpak stelt je in staat om formuliercreatie te automatiseren, dynamische rapporten te genereren, of Word‑gebaseerde UI‑prototypes direct vanuit C# te bouwen.

Vervolgens kun je verkennen:

* **Hoe ActiveX‑selectievakjes** in te voegen voor enquêtes.  
* **Hoe rijke tekstinhoud** rond de knop toe te voegen met `DocumentBuilder`.  
* **Hoe het document te beveiligen** terwijl de knop functioneel blijft.  

Voel je vrij om te experimenteren met verschillende besturingselementtypen, groottes en macro‑namen om aan jouw specifieke scenario te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
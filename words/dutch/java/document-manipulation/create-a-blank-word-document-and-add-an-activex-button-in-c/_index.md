---
category: general
date: 2026-10-23
description: Maak een leeg Word‑document met C# en leer hoe je ActiveX‑besturingselementen,
  inclusief een knop, kunt invoegen met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: nl
lastmod: 2026-10-23
og_description: Maak een leeg Word‑document met C# en leer hoe je ActiveX‑besturingselementen,
  inclusief een knop, kunt invoegen met Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Maak een leeg Word‑document en voeg een ActiveX‑knop toe in C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Maak een leeg Word‑document en voeg een ActiveX‑knop toe in C#
url: /nl/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document en voeg een ActiveX‑knop toe in C#

Als je **een leeg Word‑document** programmatisch moet maken, laat deze gids je precies zien hoe. Je ziet een volledig, uitvoerbaar voorbeeld dat een nieuw document maakt, een ActiveX CommandButton invoegt en het bestand opslaat — allemaal met Aspose.Words voor .NET.

Werken met Word‑bestanden vereist vaak meer dan platte tekst. Het toevoegen van een **ActiveX‑knop** stelt je in staat interactieve functionaliteit in te sluiten die kan worden gebruikt in macro‑ingeschakelde sjablonen of Windows‑only oplossingen. Aan het einde van deze tutorial kun je elk ActiveX‑besturingselement invoegen, maar we richten ons op het meest voorkomende scenario: een **word document activex button** die een formulier verzendt.

## Vereisten

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
* Visual Studio 2022 (of een andere C#‑IDE)
* **Aspose.Words for .NET** NuGet‑pakket  
  ```bash
  dotnet add package Aspose.Words
  ```
* Basiskennis van C#‑syntaxis

> **Pro tip:** Aspose.Words is een commerciële bibliotheek, maar biedt een gratis tijdelijke licentie voor testen. Installeer de licentie vroegtijdig om het evaluatiewatermerk te vermijden.

## Stap 1: Maak een leeg Word‑document met Aspose.Words

De eerste stap is het instantieren van een `Document`‑object. Dit vertegenwoordigt een leeg `.docx`‑bestand in het geheugen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` begint zonder secties, pagina's of inhoud. Het is een schone lei die je nodig hebt voor **create blank word document** scenario's, zoals het genereren van rapporten vanaf nul.

## Stap 2: Verkrijg een DocumentBuilder om het document te bewerken

`DocumentBuilder` biedt een handige API voor het toevoegen van tekst, afbeeldingen en besturingselementen. We zullen het gebruiken om het ActiveX‑besturingselement te positioneren.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

De builder voegt automatisch een standaardsectie en een eerste pagina toe, zodat je meteen objecten kunt invoegen.

## Stap 3: Hoe ActiveX‑besturingselementen in het document in te voegen

Aspose.Words biedt `InsertForms2OleControl` voor het insluiten van OLE/ActiveX‑objecten. De methode vereist het type besturingselement, de breedte en de hoogte (in points). Hieronder voegen we een **CommandButton** in — de klassieke formulierknop die je ziet in legacy Word‑sjablonen.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Waarom dit werkt:** `Forms2OleControlType.COMMANDBUTTON` vertelt Word om een knop te maken die kan reageren op klik‑events wanneer het document wordt geopend in een Windows‑omgeving die ActiveX ondersteunt.

## Stap 4: Maak een ActiveX‑besturingselement – stel de eigenschappen in

Nu geven we de knop een programmatische naam en een zichtbare bijschrift. Dit is het deel van **create activex control** dat ontwikkelaars vaak over het hoofd zien.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` is de identifier die je vanuit VBA‑macros zult aanroepen (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` is het label dat op de knop zelf wordt weergegeven.

## Stap 5: Sla het Word‑document op met de ActiveX‑knop

Tot slot schrijf je het document naar schijf. De bestandsextensie moet `.docx` zijn (of `.docm` als je later macro's wilt toevoegen). Het voorbeeld slaat op in een tijdelijke map — vervang dit door je eigen pad.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wanneer je het resulterende bestand opent in Microsoft Word (alleen Windows), zie je een functionele **word document activex button** die kan worden gekoppeld aan VBA‑code.

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een nieuw console‑project.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Verwachte output wanneer je het programma uitvoert**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Open het gegenereerde `ActiveXButton.docx` in Word, en je zult een knop met het label **Submit** zien, geplaatst bovenaan de eerste pagina.

## Randgevallen en veelvoorkomende valkuilen

| Situatie | Waar je op moet letten | Aanbeveling |
|-----------|-------------------|----------------|
| Uitvoeren op macOS of Linux | ActiveX is een Windows‑only technologie, dus de knop verschijnt als een tijdelijke aanduiding. | Gebruik de tutorial alleen voor op Windows gerichte sjablonen. |
| Document geopend in Word Online | ActiveX‑besturingselementen worden niet ondersteund in de browserweergave. | Bied een fallback‑UI of instrueer gebruikers het bestand te openen in de desktopclient. |
| Een macro‑ingeschakeld bestand nodig | `.docx`‑bestanden kunnen geen VBA‑code opslaan. | Sla op als `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) en voeg de macro apart toe. |
| Mismatching besturingselementgrootte | Breedte/hoogte waarden zijn in points (1 pt ≈ 1/72 in). | Pas de numerieke waarden aan om de gewenste visuele grootte te bereiken. |

## Veelgestelde vragen

**Hoe ActiveX‑besturingselementen invoegen die geen knop zijn?**  
Gebruik dezelfde `InsertForms2OleControl`‑methode maar geef een andere `Forms2OleControlType`‑enumwaarde door, zoals `COMBOBOX` of `LISTBOX`.

**Kan ik het lettertype of de kleur van de knop wijzigen?**  
Het uiterlijk van de ActiveX‑knop wordt bepaald door de host‑applicatie (Word) en het onderliggende Windows‑thema. Je kunt eigenschappen zoals `ForeColor` en `BackColor` via VBA aanpassen nadat het document is geopend.

**Is er een manier om een klik‑handler direct vanuit C# toe te voegen?**  
Nee. Het klik‑event moet worden afgehandeld door VBA of een Word‑add‑in omdat de knop draait binnen het Word‑proces, niet in jouw .NET‑applicatie.

## Conclusie

Je weet nu hoe je **een leeg Word‑document** programmatisch kunt maken en een **ActiveX‑knop** kunt insluiten met Aspose.Words voor .NET. De behandelde stappen:

1. Instantieer een `Document`.
2. Gebruik `DocumentBuilder` om met het bestand te werken.
3. Roep `InsertForms2OleControl` aan om **how to insert activex** besturingselementen toe te voegen.
4. Configureer de eigenschappen van het besturingselement (**create activex control**).
5. Sla het bestand op, waardoor je een **word document activex button** krijgt die klaar is voor VBA‑integratie.

Vanaf hier kun je andere besturingselementtypen verkennen, VBA‑macro's koppelen, of het document naar PDF converteren terwijl je de knop behoudt (als een statische afbeelding). Experimenteer met verschillende groottes, bijschriften en namen.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een ActiveX‑knop toe te voegen in een Word‑document met Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Word‑document maken met ActiveX‑knop – C#‑gids](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
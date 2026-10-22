---
category: general
date: 2026-08-10
description: Maak een Word‑document programmatisch met Aspose.Words, voeg vervolgens
  een ActiveX‑besturingselement (woordknop) toe. Voeg een ActiveX‑opdrachtknop in
  enkele minuten in.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: nl
lastmod: 2026-08-10
og_description: Maak een Word‑document programmatisch met Aspose.Words en voeg vervolgens
  een ActiveX‑besturingselement toe als Word‑knop. Leer hoe je snel een ActiveX‑opdrachtknop
  kunt invoegen.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Maak een Word‑document programmatisch – voeg een ActiveX‑knop toe in C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Maak een Word-document via code en voeg een ActiveX-knop toe
url: /nl/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document programmatisch aan en voeg ActiveX-knop toe

Als je **een Word-document programmatisch wilt maken**, leidt deze gids je door het volledige proces met Aspose.Words for .NET. Je leert ook hoe je **ActiveX‑besturingselementen voor Word** kunt toevoegen en **ActiveX‑opdrachtknoppen** kunt invoegen in één zelf‑bevat voorbeeld.

Het genereren van Word‑bestanden vanuit code verwijdert de handmatige stap van het openen van Microsoft Word, waardoor je rapporten, facturen of datagestuurde contracten automatisch kunt bouwen. Aan het einde van deze tutorial heb je een kant‑klaar C# console‑applicatie die een `.docx`‑bestand produceert met een interactieve ActiveX CommandButton.

## Vereisten

* .NET 6.0 SDK of later (de code werkt ook met .NET Framework 4.6+)
* Visual Studio 2022 of een IDE die .NET‑ontwikkeling ondersteunt
* Een geldige Aspose.Words for .NET‑licentie (je kunt de gratis evaluatiesleutel gebruiken voor testen)
* Basiskennis van C#‑syntaxis en het concept van COM/ActiveX‑besturingselementen

> **Pro tip:** Als je van plan bent het gegenereerde document te distribueren naar gebruikers die geen Word geïnstalleerd hebben, embed dan de runtime‑bestanden van het ActiveX‑besturingselement naast het `.docx`‑bestand of lever een macro‑ingeschakeld sjabloon.

## Maak Word-document programmatisch – initiële setup

Eerst voeg je het Aspose.Words NuGet‑pakket toe aan je project:

```bash
dotnet add package Aspose.Words
```

Maak vervolgens een nieuw console‑project aan (als je er nog geen hebt):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Open het gegenereerde `Program.cs`‑bestand – we zullen de inhoud ervan vervangen door de volledige oplossing hieronder.

## Stap 1: Namespaces importeren en de licentie configureren

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Waarom dit belangrijk is*: Het importeren van `Aspose.Words.Drawing` geeft je toegang tot `Forms2OleControl`, de klasse die een ActiveX‑besturingselement binnen een Word‑document vertegenwoordigt. Het vroeg instellen van een licentie voorkomt runtime‑waarschuwingen in productie.

## Stap 2: Een leeg document en een DocumentBuilder maken

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Het `Document`‑object is de in‑memory weergave van een `.docx`‑bestand. `DocumentBuilder` werkt als een cursor die je door het document beweegt om elementen in te voegen.

## Stap 3: Een ActiveX CommandButton‑besturingselement invoegen

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` maakt een OLE‑object dat Word als een ActiveX‑besturingselement beschouwt. Het coördinatensysteem gebruikt punten (1 punt = 1/72 inch), wat overeenkomt met de layout‑engine van Word.

## Stap 4: De bijschrift van de knop en optionele eigenschappen instellen

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Het instellen van de `Caption`‑eigenschap is de meest gebruikelijke manier om de knop te labelen. Als je wilt dat de knop een VBA‑macro uitvoert, wijs dan de macro‑naam toe aan `OnAction`. Deze tutorial richt zich op het visuele deel; macro‑integratie wordt behandeld in de sectie “Volgende stappen”.

## Stap 5: Het document opslaan

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Wanneer je het programma uitvoert, zie je een console‑bericht dat bevestigt dat `ActiveX_CommandButton.docx` naar schijf is geschreven.

### Volledige broncode (klaar om te kopiëren en plakken)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Het uitvoeren van de snippet levert een Word‑bestand op dat een klikbare **ActiveX‑opdrachtknop** bevat. Open het bestand in Microsoft Word, schakel over naar **Ontwerpmodus** (Ontwikkelaars‑tab → Ontwerpmodus), en je ziet de knop precies op de plaats waar je deze hebt geplaatst.

## Stap 6: Het resultaat verifiëren

1. Open `ActiveX_CommandButton.docx` in Microsoft Word.  
2. Schakel het **Developer**‑tab in als het niet zichtbaar is (`File → Options → Customize Ribbon → check Developer`).  
3. Klik op **Design Mode**. De knop zou moeten verschijnen met het label “Submit”.  
4. Als je een `OnAction`‑macro hebt toegevoegd, klik dan op de knop terwijl Ontwerpmodus uitgeschakeld is om de macro te activeren.

Als de knop niet wordt weergegeven, controleer dan of de beveiligingsinstellingen van Word ActiveX‑besturingselementen toestaan (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Kan ik andere ActiveX‑typen invoegen?** | Ja. De `Forms2OleControlType`‑enum bevat `CheckBox`, `OptionButton`, `ComboBox`, enz. Vervang `CommandButton` door de gewenste enum‑waarde |

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak Groepvorm in Word-document met Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Maak Word-document met kop‑ en voettekst met Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Voeg inline‑afbeelding in Word-document in met Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
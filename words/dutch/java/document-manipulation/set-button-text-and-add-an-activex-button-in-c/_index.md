---
category: general
date: 2026-10-10
description: Stel de knoptekst in en voeg een ActiveX‑knop toe in C# met Aspose.Words.
  Leer hoe je een knop invoegt, een knopbesturingselement maakt en de bijschrift aanpast
  in een Word‑document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: nl
lastmod: 2026-10-10
og_description: Stel de knoptekst in en voeg een ActiveX‑knop toe in C# met Aspose.Words.
  Volg deze stapsgewijze handleiding om een knop in te voegen, een knopbesturingselement
  te maken en het bijschrift aan te passen.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Stel knoptekst in en voeg een ActiveX‑knop toe in C# – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Stel knoptekst in en voeg een ActiveX‑knop toe in C#
url: /nl/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Stel knoptekst in en voeg een ActiveX‑knop toe in C#

Als je **knoptekst wilt instellen** op een ActiveX‑knop in een Word‑document, laat deze gids je precies zien hoe. Aan het einde van de tutorial kun je **knop invoegen**, een **knop‑control** maken en de bijschrift aanpassen met slechts een paar regels C#‑code.

Werken met ActiveX‑besturingselementen is gebruikelijk wanneer je interactieve formulieren in Word wilt maken — of je nu een contracttemplate, een enquête of een intern hulpmiddel bouwt. Het voorbeeld maakt gebruik van Aspose.Words for .NET, een bibliotheek waarmee je Word‑bestanden kunt manipuleren zonder dat Microsoft Office geïnstalleerd is.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd  
* Visual Studio 2022 (of een IDE die C# ondersteunt)  
* Een Aspose.Words for .NET‑licentie (de gratis evaluatie werkt voor leerdoeleinden)  

Je hebt ook een referentie naar het `Aspose.Words` NuGet‑pakket nodig:

```bash
dotnet add package Aspose.Words
```

## Hoe een knop in een Word‑document in te voegen

De eerste stap is het maken van een nieuw `Document` en een `DocumentBuilder`. De builder is het startpunt voor het toevoegen van inhoud, inclusief ActiveX‑besturingselementen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:** `Document` vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` high‑level‑methoden biedt zoals `InsertParagraph` en `InsertFormField`. Beginnen met een leeg document zorgt ervoor dat de knop precies op de gewenste plaats verschijnt.

## Maak een knop‑control met Forms2OleControl

Nu maken we het daadwerkelijke knop‑control. `Forms2OleControl` is de klasse die Aspose.Words gebruikt voor alle ActiveX‑objecten, en het type `COMMANDBUTTON` wordt weergegeven als een klikbare knop in Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Uitleg:**  
* `InsertForms2OleControl` plaatst het control op de exacte coördinaten die je opgeeft.  
* De grootte wordt gedefinieerd in points (1 point = 1/72 inch). Pas deze getallen aan om je lay‑out te laten passen.

## Voeg een ActiveX‑control toe en geef het een unieke naam

Elk ActiveX‑object moet een unieke naam hebben zodat je er later naar kunt verwijzen (bijvoorbeeld bij het afhandelen van events in VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tip:** Vermijd spaties of speciale tekens in de naam; Word behandelt de naam als een identifier in het interne formuliermodel.

## Stel knoptekst (bijschrift) in op de ActiveX‑knop

Hier komt het primaire trefwoord **set button text** (knoptekst instellen) in beeld. De `Caption`‑eigenschap bepaalt het label dat gebruikers op de knop zien.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Je kunt het bijschrift op elk moment vóór het opslaan van het document wijzigen. Als je later de UI wilt lokaliseren, roep je simpelweg `SetCaption` opnieuw aan met een andere tekenreeks.

## Sla het document op en controleer het resultaat

Tot slot schrijf je het document naar schijf. Het openen van het bestand in Microsoft Word toont de knop met het aangepaste bijschrift.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Verwachte output:** Wanneer je *ActiveXButton.docx* in Word opent, zie je een knop die op de opgegeven coördinaten is geplaatst, gelabeld **Click Me**. Het klikken op de knop activeert het standaardgedrag van een Word‑commandobutton (dat je later kunt aanpassen met VBA).

![Voorbeeld van knoptekst instellen](https://example.com/activex-button.png){alt="Voorbeeld van knoptekst instellen"}

## Voeg een ActiveX‑knop toe en verwerk events (optioneel)

Als je wilt dat de knop een aangepaste actie uitvoert, kun je een VBA‑macro toevoegen die reageert op het `Click`‑event. De macro kan programmatisch worden geïnjecteerd, maar dat valt buiten de scope van deze tutorial. Het belangrijke is dat de knop al aanwezig is en dat het bijschrift is ingesteld — klaar voor elke event‑afhandeling die je kiest.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| Knop verschijnt scheef | Coördinaten zijn in points, niet in pixels | Converteer pixelwaarden naar points (`points = pixels * 72 / DPI`) |
| Bijschrift verandert niet na opslaan | `SetCaption` aangeroepen na `Save` | Stel het bijschrift altijd **voor** het aanroepen van `doc.Save` in |
| Control niet zichtbaar in oudere Word‑versies | Sommige oudere Word‑versies hebben geen volledige ActiveX‑ondersteuning | Test op de doel‑Word‑versie; overweeg een `CheckBox` of `DropDownList` als fallback te gebruiken |
| Licentie‑waarschuwing in output | Evaluatielicentie verloopt | Pas een geldige Aspose.Words‑licentie toe via `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren. Het bevat alle benodigde `using`‑directieven en demonstreert de volledige workflow van het maken van een document tot het opslaan.

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
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Voer het programma uit met `dotnet run`. Na uitvoering open je *ActiveXButton.docx* om te bevestigen dat het bijschrift van de knop **Click Me** luidt.

## Samenvatting van wat je geleerd hebt

* Je hebt geleerd hoe je **set button text** (knoptekst instelt) op een ActiveX‑knop kunt zetten met Aspose.Words.  
* Je hebt de exacte stappen gezien om **how to insert button**, **create button control**, en **add activex control** in een Word‑document te doen.  
* Je beschikt nu over een herbruikbare code‑snippet die je kunt aanpassen voor elk formulier‑gebaseerd Word‑automatiseringsproject.

## Volgende stappen

* Verken andere `Forms2OleControlType`‑waarden zoals `CHECKBOX` of `LISTBOX` om uitgebreidere formulieren te bouwen.  
* Combineer de knop met een VBA‑macro om berekeningen of gegevensvalidatie uit te voeren.  
* Gebruik Aspose.Words’ `FormField`‑API om gebruikersinvoer te lezen nadat het document is ingevuld.

Voel je vrij om te experimenteren met de grootte, positie en het bijschrift om aan je ontwerpvereisten te voldoen. Als je tegen problemen aanloopt, biedt de Aspose.Words‑documentatie gedetailleerde referenties voor elke klasse die in deze tutorial wordt gebruikt.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak een leeg Word‑document met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Voeg schaduw toe aan vorm in Word met Aspose.Words – Stapsgewijs](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Voeg paginanummers toe aan de voettekst van een Word‑document met Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
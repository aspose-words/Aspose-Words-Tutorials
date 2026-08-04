---
category: general
date: 2026-08-04
description: Maak een Word‑document programmatisch met C#. Leer hoe je programmatisch
  een commandoknop kunt toevoegen met Aspose.Words in slechts een paar stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: nl
lastmod: 2026-08-04
og_description: Maak een Word‑document programmatisch met Aspose.Words. Deze gids
  laat zien hoe je programmatisch een commandoknop toevoegt, deze configureert en
  het bestand opslaat.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Maak een Word‑document programmatically – volledige C#‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Maak een Word‑document programmatisch – stapsgewijze handleiding
url: /nl/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑document programmatically maken – volledige C#‑tutorial

Als je **een Word‑document programmatically wilt maken**, laat deze gids je precies zien hoe je dat doet met Aspose.Words voor .NET. Met slechts een paar regels C# kun je een leeg `.docx`‑bestand genereren, **programmatically command‑button**‑besturingselementen toevoegen, hun eigenschappen instellen en het resultaat opslaan.  

De onderstaande stappen behandelen alles, van projectopzet tot het afhandelen van randgevallen, zodat je de code kunt kopiëren naar je eigen applicatie en uitvoeren zonder aanpassingen.

## Wat je zult bereiken

Aan het einde van deze tutorial kun je:

* Een nieuw Word‑document volledig in het geheugen initialiseren.  
* **Programmatically command‑button** OLE‑besturingselementen op elke locatie en grootte toevoegen.  
* De caption, interne naam en andere OLE‑eigenschappen van de knop configureren.  
* Het gegenereerde document opslaan op schijf of in een stream voor verdere verwerking.

### Vereisten

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+).  
* Een geldige Aspose.Words voor .NET‑licentie (of een gratis evaluatie).  
* Basiskennis van C# en Visual Studio (of een andere IDE naar keuze).  

> **Pro tip:** Als je het voorbeeld zonder licentie uitvoert, voegt Aspose.Words een klein evaluatiewatermerk toe aan de eerste pagina.

## Stap 1: Het project opzetten en vereiste namespaces importeren

Maak een nieuwe Console App (of integreer in een bestaande service) en voeg het Aspose.Words‑NuGet‑pakket toe:

```bash
dotnet add package Aspose.Words
```

Voeg vervolgens de essentiële namespaces toe aan de bovenkant van je `.cs`‑bestand:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Deze imports geven je toegang tot `Document`, `DocumentBuilder`, `Forms2OleControl` en de `RectangleF`‑structuur die wordt gebruikt voor positionering.

## Stap 2: Een nieuw Word‑document initialiseren

De eerste handeling in elke **create word document programmatically**‑workflow is het instantieren van een `Document`‑object. Dit object bestaat alleen in het geheugen totdat je het expliciet opslaat.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` werkt als een cursor die bijhoudt waar het volgende element wordt geplaatst. Het gebruik ervan houdt de code beknopt en bootst de manier na waarop je direct in Word zou typen.

## Stap 3: Een command‑button OLE‑control invoegen

Aspose.Words biedt de methode `InsertForms2OleControl` om OLE‑objecten zoals command‑buttons, check‑boxes of combo‑boxes in te sluiten. De methode vereist drie argumenten:

1. De `ControlType`‑enumwaarde (hier `CommandButton`).  
2. Een `RectangleF` die de X‑Y‑positie en de breedte‑hoogte van de control definieert (gemeten in points, waarbij 72 pt = 1 inch).  
3. Optioneel extra OLE‑eigenschappen (niet nodig voor de basis‑knop).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Waarom dit werkt:** `InsertForms2OleControl` maakt een OLE‑container in het document en retourneert een `Forms2OleControl`‑wrapper. Met de wrapper kun je het onderliggende OLE‑object (de daadwerkelijke knop) manipuleren zonder low‑level COM‑interop.

## Stap 4: De caption en interne naam van de knop configureren

Na het invoegen wil je meestal de knop een gebruikers‑zichtbare label en een interne identifier geven die je macro of add‑in later kan aanroepen.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` is de tekst die op de knop wordt weergegeven in de Word‑UI.  
* `Name` is de programmatic identifier die door VBA of externe automatiseringsscripts wordt gebruikt.

### Optioneel: Een macro aan de knop toewijzen

Als je een VBA‑macro wilt laten uitvoeren wanneer op de knop wordt geklikt, kun je de macro‑naam koppelen:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Randgeval:** Wanneer het doel‑document wordt geopend op een machine zonder de macro, toont Word een beveiligingswaarschuwing. Onderteken je macro’s altijd of informeer gebruikers over de benodigde instellingen.

## Stap 5: Het document opslaan

Je kunt het bestand naar schijf, een `MemoryStream` of direct naar een response‑object in een web‑API schrijven. De eenvoudigste aanpak voor een console‑demo is opslaan naar een lokale map:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Het resulterende `.docx`‑bestand opent in Microsoft Word met een functionele command‑button die “Click Me” toont. Klikken op de knop activeert de toegewezen macro (indien aanwezig) of toont simpelweg een standaardbericht.

## Volledig werkend voorbeeld

Kopieer het volgende programma naar `Program.cs` en voer het uit. Het demonstreert de volledige **create word document programmatically**‑stroom, inclusief foutafhandeling.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Verwacht resultaat:** Het openen van `CommandButton.docx` in Word toont een knop met het label “Click Me”. Als je met de muis over de knop gaat, verschijnt de naam `cmdClickMe` in het eigenschappen‑paneel.

## Veelgestelde vragen en probleemoplossing

| Vraag | Antwoord |
|----------|--------|
| *Kan ik de knop toevoegen aan een bestaand document?* | Ja. Laad het bestand met `new Document("Existing.docx")` en gebruik vervolgens dezelfde `InsertForms2OleControl`‑aanroep. |
| *Welke eenheden gebruikt `RectangleF`?* | Points (1 inch = 72 pt). Pas de waarden aan om de knop precies te positioneren. |
| *Werkt de knop in Word voor Mac?* | OLE‑controls worden alleen ondersteund in Windows‑Word. Op Mac verschijnt de knop als een statische afbeelding. |
| *Heb ik een licentie nodig voor productiegebruik?* | Een commerciële licentie verwijdert evaluatiewatermerken en ontgrendelt volledige functionaliteit. |
| *Hoe wijzig ik de grootte van de knop na invoegen?* | Pas `commandButton.Width` en `commandButton.Height` aan of voer een nieuwe invoeging uit met een andere `RectangleF`. |

## De oplossing uitbreiden

Nu je weet hoe je **programmatically command‑button**‑controls kunt toevoegen, kun je de volgende gerelateerde onderwerpen verkennen:

* **Andere form‑controls invoegen** – gebruik `ControlType.CheckBox`, `ControlType.OptionButton`, enz. (dekt secundaire zoekterm *Aspose.Words InsertForms2OleControl*).  
* **Het document vullen met dynamische data** – merge data uit een database in tabellen of mail‑merge‑velden.  
* **Exporteren naar PDF** – na het toevoegen van de knop, roep `doc.Save("output.pdf", SaveFormat.Pdf)` aan om een PDF‑versie te maken (relevant voor *C# Word automation*).  

## Conclusie

Je beschikt nu over een compleet, productie‑klaar patroon voor **create word document programmatically** en **programmatically command‑button** toevoegen met Aspose.Words voor .NET. De tutorial behandelde projectopzet, documentinitialisatie, OLE‑knop‑invoeging, eigenschapsconfiguratie en het opslaan van het bestand. Voel je vrij om de code aan te passen om andere form‑controls in te voegen, macro’s te koppelen of de logica te integreren in webservices of achtergrondtaken.

Happy coding, en veel plezier met het automatiseren van Word‑documenten!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Maak Word‑document met Aspose.Words – Stapsgewijze gids](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Maak een Word‑document met tabel met Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Groep‑shape in Word‑document invoegen met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
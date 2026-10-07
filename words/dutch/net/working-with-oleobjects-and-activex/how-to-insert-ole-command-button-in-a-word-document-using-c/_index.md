---
category: general
date: 2026-10-07
description: Leer hoe je een OLE‑opdrachtknop in een Word‑document kunt invoegen met
  Aspose.Words C#. Stapsgewijze handleiding die DocumentBuilder, eigenschappen en
  het opslaan van het bestand behandelt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: nl
lastmod: 2026-10-07
og_description: Voeg een OLE-opdrachtknop in een Word‑document toe met C#. Volg deze
  beknopte tutorial om een functionele CommandButton toe te voegen, te configureren
  en op te slaan met Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: OLE-opdrachtknop invoegen in Word met C# – volledige Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Hoe een OLE-opdrachtknop in een Word-document invoegen met C#
url: /nl/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een OLE command button in een Word-document in te voegen met C#

Als je **insert OLE command button** in een Word‑bestand programmatically moet invoegen, laat deze gids je precies zien hoe je dat doet met Aspose.Words for .NET. Of je nu een formulier‑gevuld rapport bouwt of een sjabloon automatiseert dat gebruikersinteractie vereist, de onderstaande stappen geven je een complete, uitvoerbare oplossing.

Je leert hoe je een leeg document maakt, de `DocumentBuilder` gebruikt om een `Forms2OleControl` te plaatsen, de bijschrift en naam van de knop instelt, en uiteindelijk de `.docx` opslaat. Er zijn geen externe tools nodig, behalve de Aspose.Words‑bibliotheek.

## Vereisten

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
* Een geldige Aspose.Words for .NET‑licentie of een gratis evaluatiesleutel
* Visual Studio 2022 (of een andere C#‑IDE die je verkiest)
* Basiskennis van C#‑syntaxis en Word OLE‑concepten

> **Pro tip:** Als je de gratis evaluatie gebruikt, zal het gegenereerde document een klein watermerk bevatten. Een gelicentieerde versie verwijdert dit automatisch.

## Stap 1: Installeer Aspose.Words

Voeg het Aspose.Words‑pakket toe aan je project via NuGet:

```bash
dotnet add package Aspose.Words
```

Het pakket bevat de `Aspose.Words.Drawing` en `Aspose.Words.Drawing.Ole` namespaces die nodig zijn voor OLE‑besturingselementen.

## Stap 2: OLE command button invoegen met DocumentBuilder

De kern van de tutorial is de `InsertForms2OleControl`‑methode. Deze maakt een **Forms2 OLE CommandButton** op een specifieke locatie en grootte.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Waarom dit werkt

* `DocumentBuilder` is de primaire API voor het programmatisch bouwen van Word‑documenten.  
* `InsertForms2OleControl` vertelt Aspose.Words om een **Forms2 OLE control** in te sluiten, wat de legacy Word‑formuliertechnologie is die command buttons, check boxes, enz. ondersteunt.  
* De enum‑waarde `OleControlType.CommandButton` specificeert dat het ingevoegde besturingselement een **command button** is — het exacte type dat je vroeg toen je een **insert OLE command button** wilde.  
* De `Rectangle` bepaalt de visuele plaatsing. Pas de X/Y‑coördinaten of de breedte/hoogte aan om bij je lay‑out te passen.

## Stap 3: Sla het document op

Na het configureren van de knop, schrijf je het document naar schijf. Je kunt elk formaat kiezen dat door Aspose.Words wordt ondersteund (`.docx`, `.pdf`, `.odt`, …). Voor deze tutorial slaan we op als een Word‑document.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wanneer je `CommandButton.docx` opent in Microsoft Word, zie je een klikbare knop met het label **Click Me**. Het indrukken ervan in Word activeert het standaard “Run Macro”-dialoogvenster omdat de knop een OLE‑formulierbesturingselement is; je kunt later een macro of VBA‑code eraan koppelen indien nodig.

## Stap 4: Verifieer het resultaat (verwachte output)

Open het gegenereerde bestand:

1. De knop verschijnt op de coördinaten die je hebt opgegeven (ongeveer 1,4 in van de linkerkant en bovenkant van de pagina).  
2. Het bijschrift luidt **Click Me**.  
3. De naam‑eigenschap (`cmdSubmit`) is zichtbaar in het **Developer → Properties**‑paneel van Word, wat handig is wanneer je het besturingselement vanuit VBA wilt refereren.

![Voorbeeld van een Insert OLE command button in een Word‑document](insert-ole-button.png)

*Afbeeldings‑alt‑tekst*: **Voorbeeld van een Insert OLE command button in een Word‑document** (bevat het primaire trefwoord voor toegankelijkheid en SEO).

## Randgevallen & Veelgestelde Vragen

### 1. Wat als de knop niet verschijnt waar ik verwacht?

- Word gebruikt punten, niet pixels. Converteer schermpixels naar punten (`points = pixels * 72 / DPI`).  
- Zorg ervoor dat de rechthoek niet snijdt met de paginamarges; anders kan Word het besturingselement verplaatsen.

### 2. Kan ik de knop in een bestaand document invoegen?

Ja. Laad het document met `new Document("Existing.docx")` en gebruik dezelfde `DocumentBuilder`‑workflow. Vergeet niet de cursor van de builder te verplaatsen (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, enz.) voordat je `InsertForms2OleControl` aanroept.

### 3. Hoe koppel ik een macro aan de knop?

Aspose.Words creëert geen VBA‑code, maar je kunt na het genereren van het document een macro insluiten:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Werkt dit met .NET Core op Linux?

Het OLE‑besturingselement is een Windows‑specifieke functie omdat het afhankelijk is van COM. Op Linux wordt de knop wel ingevoegd, maar verschijnt deze als een statisch plaatje zonder interactieve functionaliteit. Voor cross‑platform interactieve formulieren kun je beter content controls (`StructuredDocumentTag`) gebruiken.

### 5. Wat als ik een andere grootte of meerdere knoppen nodig heb?

Maak extra `Rectangle`‑objecten met unieke coördinaten en herhaal de `InsertForms2OleControl`‑aanroep. Elke knop kan zijn eigen `Caption` en `Name` hebben.

## Volledig Werkend Voorbeeld

Hieronder staat het volledige programma dat je kunt copy‑pasten in een console‑applicatie. Het bevat alle benodigde `using`‑directieven, foutafhandeling en commentaren.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Voer het programma uit, open het gegenereerde `CommandButton.docx`, en je ziet de **Click Me**‑knop klaar voor verdere aanpassing.

## Conclusie

Je weet nu hoe je een **insert OLE command button** in een Word‑document kunt invoegen met C# en Aspose.Words. De tutorial behandelde:

- Het installeren van het Aspose.Words‑pakket  
- Het gebruiken van `DocumentBuilder.InsertForms2OleControl` met `OleControlType.CommandButton`  
- Het instellen van knop‑eigenschappen (`Caption`, `Name`)  
- Het opslaan en verifiëren van de output  

Vanaf hier kun je gerelateerde onderwerpen verkennen, zoals **Aspose.Words OLE control** voor selectievakjes, keuzelijsten, of het insluiten van volledige Excel‑werkbladen. Je kunt ook experimenteren met **Word OLE command button**‑automatisering in grotere sjablonen, of OLE‑besturingselementen vervangen door moderne **content controls** voor betere cross‑platform ondersteuning.

Voel je vrij om de rectangle‑waarden aan te passen, meerdere knoppen toe te voegen, of VBA‑macro's te koppelen om aan de eisen van je applicatie te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Ole‑object in Word‑document invoegen](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Ole‑object in Word‑document invoegen als pictogram](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Ole‑object in Word invoegen met Ole‑pakket](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
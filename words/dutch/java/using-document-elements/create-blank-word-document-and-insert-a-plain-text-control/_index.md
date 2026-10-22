---
category: general
date: 2026-09-18
description: Maak een leeg Word‑document met C# en stel placeholder‑tekst in, sla
  het document vervolgens op als docx. Leer een platte‑tekst‑inhoudsbesturingselement
  in te voegen en een placeholder‑naam toe te voegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: nl
lastmod: 2026-09-18
og_description: Maak een leeg Word‑document met C#. Stel placeholder‑tekst in, voeg
  een plain‑text‑besturingselement toe, voeg een placeholder‑naam toe en sla het document
  op als docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Maak een leeg Word‑document met tijdelijke tekst – C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Maak een leeg Word‑document en voeg een platte‑tekstbesturingselement in.
url: /nl/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document en voeg een platte‑tekst‑besturingselement in

Als je **een leeg Word‑document** programmatisch moet **maken**, laat deze gids je zien hoe je dat doet met C#. Je leert hoe je een **platte‑tekst‑besturingselement** **invoegt**, **placeholder‑tekst** **instelt**, een **placeholder‑naam** **toevoegt**, en uiteindelijk **het document opslaat als docx**. De stappen zijn volledig zelfstandig, zodat je de code kunt kopiëren naar elk .NET‑project en direct kunt uitvoeren.

Werken met Word‑bestanden vereist vaak een schoon startpunt—een leeg document dat al de besturingselementen bevat die je gebruikers later zullen invullen. Aan het einde van deze tutorial heb je een `.docx`‑bestand dat een platte‑tekst‑content‑control bevat met een handige placeholder, gevolgd door reguliere inhoud.

## Prerequisites

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
- Een referentie naar de **Aspose.Words for .NET**‑bibliotheek (beschikbaar via NuGet `Install-Package Aspose.Words`)
- Basiskennis van C#‑console‑applicaties
- Schrijfrechten voor de output‑map die je opgeeft in `doc.save(...)`

## What you will build

Het uiteindelijke document (`SDT.docx`) bevat:

1. Een leeg Word‑bestand (het **blank Word document** dat je hebt aangemaakt)
2. Een platte‑tekst‑content‑control (de stap **insert plain text control**)
3. Placeholder‑tekst die in de control verschijnt totdat de gebruiker iets typt (de stap **set placeholder text**)
4. Een placeholder‑naam die later programmatisch kan worden gebruikt (de stap **add placeholder name**)
5. Een regel reguliere tekst na de control, om te laten zien dat normale inhoud kan volgen

## Step 1: Create a blank Word document

De eerste handeling is het instantieren van een leeg `Document`‑object. Dit object vertegenwoordigt een volledig nieuw, **blank Word document** in het geheugen.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Waarom dit belangrijk is:* Een leeg `Document` geeft je volledige controle over elk element dat je toevoegt, zodat er geen verborgen stijlen of secties interfereren met de content‑control die je later zult invoegen.

## Step 2: Initialize a DocumentBuilder

`DocumentBuilder` is de hulpprogrammaklasse die je in staat stelt om in het `Document` te schrijven. Hij houdt de huidige cursorpositie bij en biedt methoden voor het invoegen van allerlei Word‑objecten.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is:* Het gebruik van een `DocumentBuilder` vereenvoudigt het toevoegen van een **plain‑text control**, omdat de builder precies weet waar moet worden ingevoegd.

## Step 3: Insert plain text control

Nu voegen we een **plain‑text content control** toe (ook wel een Structured Document Tag, of SDT, genoemd). Het controltype `StructuredDocumentTagType.PLAIN_TEXT` vertelt Word de inhoud als platte tekst te behandelen, niet als rijke opmaak.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Waarom dit belangrijk is:* De methode `InsertStructuredDocumentTag` maakt de control aan en retourneert een referentie (`sdt`) die je verder kunt configureren, bijvoorbeeld door placeholder‑tekst of een aangepaste naam toe te voegen.

## Step 4: Set placeholder text and add placeholder name

Placeholder‑tekst geeft gebruikers een visuele hint over wat ze moeten typen. De stap **add placeholder name** kent een programmatische identifier toe die je later kunt opvragen met `doc.GetChildNodes` of soortgelijke API‑s.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Waarom dit belangrijk is:* `SetPlaceholderName` bepaalt de grijze hint‑tekst die binnen de content‑control wordt getoond. Het instellen van `Tag` (de **add placeholder name**‑actie) stelt je in staat de control te vinden in de documentboom zonder het hele bestand te doorzoeken.

## Step 5: Add regular content after the control

Om te bewijzen dat het document normaal doorgaat na de control, schrijven we een eenvoudige regel tekst.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Step 6: Save document as docx

Tot slot slaan we het in‑memory document op schijf op. Dit is de **save document as docx**‑operatie die het bestand produceert dat je in Microsoft Word kunt openen.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Waarom dit belangrijk is:* Het gebruik van het `.docx`‑formaat zorgt voor maximale compatibiliteit met moderne versies van Word, Google Docs en andere Office‑compatibele tools.

## Complete, runnable example

Hieronder staat het volledige programma dat je kunt kopiëren naar een console‑app‑project. Vervang `YOUR_DIRECTORY` door een daadwerkelijk pad op jouw machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Expected result

- Het openen van `SDT.docx` in Word toont een leeg grijs vak met de tekst **Enter text…** erin.
- Het vak is een platte‑tekst‑content‑control; je kunt er direct in typen.
- Onder het vak verschijnt de regel **After the tag.** als reguliere alinea‑tekst.

Als de placeholder niet verschijnt, controleer dan of je een recente versie van Aspose.Words gebruikt (v23.1 of later) en dat het document wordt geopend in een Word‑versie die content‑controls ondersteunt (Word 2007+).

## Common variations and edge cases

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Multiple placeholders** | Call `InsertStructuredDocumentTag` again with a different tag ID and placeholder name. |
| **Rich‑text control** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Setting default text** | After insertion, assign `sdt.Text = "Default value";` – this text replaces the placeholder when the document loads. |
| **Saving to a stream** | Replace `doc.Save(outputPath);` with `doc.Save(stream, SaveFormat.Docx);` to send the file over HTTP. |
| **Changing placeholder color** | Use `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (requires `using System.Drawing`). |

## Pro tips

- **Reuse the tag ID**: Keeping the tag (`MyTag`) consistent across documents lets you automate data population later with `doc.Range.Replace` or the `StructuredDocumentTagCollection`.
- **Avoid hard‑coded paths**: Use `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` for a portable output location.
- **Performance**: If you need to generate thousands of documents, create a single `Document` template with the SDT already present, then clone it with `doc.Clone()` for each iteration.

## Conclusion

Je weet nu hoe je **een leeg Word‑document** maakt, **een platte‑tekst‑control invoegt**, **placeholder‑tekst instelt**, **een placeholder‑naam toevoegt**, en **het document opslaat als docx** met Aspose.Words for .NET. Dit patroon vormt de basis voor het bouwen van formulier‑gevulde Word‑templates, geautomatiseerde rapporten, of elke oplossing die bewerkbare placeholders vereist.

Voel je vrij om te experimenteren met andere control‑types, meerdere placeholders te combineren, of deze code te integreren in een web‑API die het gegenereerde `.docx`‑bestand direct naar de aanroeper retourneert. Voor de volgende stap, verken **een content‑control programmatically vullen met data** of **het gegenereerde Word‑bestand converteren naar PDF** met de ingebouwde conversiefuncties van Aspose.Words. Happy coding!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step‑by‑step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
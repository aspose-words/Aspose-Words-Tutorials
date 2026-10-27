---
category: general
date: 2026-10-13
description: Maak een nieuw Word‑document in C# en voeg een contentcontrol toe met
  placeholder‑tekst. Leer hoe je placeholder‑tekst instelt en het Word‑document efficiënt
  opslaat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: nl
lastmod: 2026-10-13
og_description: Maak een nieuw Word‑document in C# met Aspose.Words, voeg een contentcontrol
  toe, stel de placeholder‑tekst in en sla het Word‑document op — allemaal in één
  gids.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Maak een nieuw Word‑document en voeg een contentcontrol toe in C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Maak een nieuw Word‑document en voeg een inhoudsbesturingselement toe in C#
url: /nl/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak nieuw Word-document en voeg content control in C# toe

Als je programmatically **een nieuw Word-document** moet maken, laat deze gids je zien hoe je dat doet met Aspose.Words for .NET. Je leert **content control in te voegen**, **placeholder-tekst** toe te wijzen, en uiteindelijk **Word-document opslaan C#** code die je kunt kopiëren naar je project.

De tutorial loopt elke stap door, legt uit waarom elke API‑aanroep belangrijk is, en behandelt veelvoorkomende variaties zoals het toevoegen van een rich‑text SDT of het verwerken van bestaande documenten. Aan het einde heb je een compleet, uitvoerbaar voorbeeld dat je kunt aanpassen voor facturen, contracten of elke getemplateerde Word‑output.

## Vereisten

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
* Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)
* Een IDE zoals Visual Studio 2022 of Visual Studio Code

Er zijn geen extra libraries nodig.

## Maak nieuw Word-document met Aspose.Words

De eerste stap is het instantieren van een `Document`‑object. Dit object vertegenwoordigt een leeg Word‑bestand in het geheugen.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` biedt je een fluent API voor het invoegen van elementen op de huidige cursorpositie. Omdat het document leeg is, start de cursor aan het begin van de eerste (en enige) sectie.

## Voeg content control toe (StructuredDocumentTag)

Een **content control** in Word wordt een Structured Document Tag (SDT) genoemd. De volgende code maakt een plain‑text SDT, stelt de titel in en definieert placeholder‑tekst die verschijnt wanneer de gebruiker het bestand opent.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Waarom dit belangrijk is:**  
* `SdtType.PlainText` beperkt de inhoud tot één regel platte tekst, wat ideaal is voor eenvoudige velden zoals een naam of e‑mail.  
* Het instellen van `PlaceholderName` geeft een visuele hint (`Enter name here`) die de eindgebruiker begeleidt.  

Als je een rijker veld nodig hebt (bijv. meerregelige tekst of een datumkiezer), vervang je `SdtType.PlainText` door `SdtType.RichText` of `SdtType.Date`.

## Voeg optionele omringende tekst toe

De meeste sjablonen bevatten een label vóór de content control. Je kunt dit toevoegen met dezelfde `DocumentBuilder`‑instance:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

Het resulterende Word‑bestand toont:

```
Customer Name: [Enter name here]
```

## Sla Word-document op in C#-stijl

Tot slot schrijf je het document naar schijf. Aspose.Words bepaalt automatisch het formaat aan de hand van de bestandsextensie.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wanneer je `output.docx` opent in Microsoft Word, zie je de placeholder‑tekst binnen een grijs‑getinte content control. Gebruikers kunnen op de control klikken en de placeholder vervangen door hun eigen waarde.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat een zelfstandige console‑applicatie die alles samenbrengt. Kopieer de code naar een nieuw console‑project en voer het uit.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Verwachte output** (console):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Het openen van `output.docx` toont een enkele regel met het label *Customer Name:* gevolgd door een content control die *Enter name here* weergeeft.

## Veelvoorkomende variaties en randgevallen

| Scenario | Code change | Reden |
|----------|-------------|--------|
| **Rich‑text veld** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Staat invoer over meerdere regels en basisopmaak toe. |
| **Alleen‑lezen control** | `sdt.LockContentControl = true;` | Voorkomt dat gebruikers de inhoud van de control bewerken. |
| **Vooraf vullen met data** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Voegt een standaardwaarde in die de placeholder overschrijft. |
| **Toevoegen aan een bestaand document** | Load with `new Document("template.docx")` instead of an empty `Document` | Maakt templating‑scenario's mogelijk waarbij de control wordt geplaatst in een vooraf gedefinieerde lay-out. |
| **Meerdere controls** | Repeat the creation block with different titles and placeholders | Handig voor formulieren die meerdere gegevens verzamelen. |

### Pro tip

Wanneer je grote documenten genereert, hergebruik je een enkele `DocumentBuilder`‑instance in plaats van elke keer een nieuwe te maken voor elke control. Dit vermindert het geheugenverbruik en verbetert de prestaties.

## Het resultaat testen

1. Voer de console‑app uit.  
2. Open `output.docx` in Microsoft Word.  
3. Controleer of de placeholder‑tekst verschijnt binnen een grijs‑getinte doos.  
4. Klik op de doos, typ een naam, en sla het bestand op. De ingevoerde tekst vervangt de placeholder.

Als de placeholder niet verschijnt, controleer dan of je Aspose.Words versie 23.9 of later gebruikt, aangezien oudere releases een bug hadden met `PlaceholderName` op plain‑text SDT’s.

## Conclusie

Je weet nu hoe je **een nieuw Word-document** maakt, **content control** invoegt, **placeholder‑tekst** instelt, en **Word-document opslaat C#** met behulp van Aspose.Words. Het volledige voorbeeld toont het standaardpatroon, en de variatietabel laat zien hoe je de oplossing kunt aanpassen voor rijkere scenario’s.

Vervolgens kun je verkennen:

* **Content control voor datums invoegen** – gebruik de `SdtType.Date`‑enumeratie.  
* **Een sjabloon vullen met data** – combineer `StructuredDocumentTag` met mail‑merge‑velden.  
* **Exporteren naar PDF** – roep `doc.Save("output.pdf")` aan na het toevoegen van controls.

Voel je vrij om te experimenteren met verschillende SDT‑typen, lock‑instellingen en styling om te voldoen aan de eisen van je project. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Nieuw Word-document maken](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Tekstinvoerveld invoegen in Word-document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Word-document maken met Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
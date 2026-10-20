---
category: general
date: 2026-08-07
description: Hoe maak je een contentcontrol in C# met Aspose.Words – leer hoe je een
  SDT toevoegt, een placeholder instelt, standaardtekst schrijft en een platte‑tekst
  control invoegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create content control
- how to add sdt
- how to set placeholder
- how to write default text
- insert plain text control
language: nl
lastmod: 2026-08-07
og_description: Hoe maak je een inhoudsbesturingselement in C# met Aspose.Words. Deze
  tutorial laat zien hoe je een SDT toevoegt, een placeholder instelt, standaardtekst
  schrijft en een platte‑tekst besturingselement invoegt.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Hoe maak je een inhoudsbesturingselement in C# – volledige Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  headline: How to create content control in C# with Aspose.Words
  type: TechArticle
- description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  name: How to create content control in C# with Aspose.Words
  steps:
  - name: Expected output
    text: '- A `.docx` file on the desktop named `CustomerNameControl.docx`. - Inside
      the file, a single content control containing the text **John Doe**. - The placeholder
      text appears in light gray until the user types a new value.'
  - name: Adding multiple content controls
    text: You can repeat the **how to add sdt** steps to insert several controls in
      the same document. Just create a new `StructuredDocumentTag` for each field
      and move the builder accordingly.
  - name: Reading a placeholder programmatically
    text: 'If you need to verify that a placeholder was set correctly, inspect the
      `PlaceholderName` property:'
  - name: Using other SDT types
    text: Aspose.Words supports dropdown lists, date pickers, and rich‑text controls.
      Replace `SdtType.PlainText` with `SdtType.DropDownList` or `SdtType.RichText`
      to change the control type.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- SDT
title: Hoe maak je een inhoudsbesturingselement in C# met Aspose.Words
url: /nl/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe content control te maken in C# met Aspose.Words

Als je **hoe een content control te maken** in een Word‑document programmatically nodig hebt, laat deze gids je precies dat zien. Je ziet hoe je een SDT toevoegt, een placeholder instelt, standaardtekst schrijft en een plain‑text control invoegt — alles met Aspose.Words for .NET.

De tutorial behandelt elke stap, van project‑opzet tot het opslaan van het uiteindelijke `.docx`‑bestand. Aan het einde kun je documenten genereren die volledig geconfigureerde content controls bevatten, klaar voor verdere verwerking of gebruikersinteractie.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
- Een Aspose.Words for .NET‑licentie of een tijdelijke evaluatiesleutel
- Visual Studio 2022 (of een andere IDE die C# ondersteunt)
- Basiskennis van C#‑syntaxis

Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words`.

## Hoe een content control te maken – stap 1: het project opzetten

Maak een nieuwe console‑applicatie en voeg het Aspose.Words‑pakket toe:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Het **hoe een content control te maken**‑proces begint met een nieuw `Document`‑object. Dit object vertegenwoordigt het Word‑bestand dat je gaat manipuleren.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Pro tip:** Houd de `DocumentBuilder`‑instance gedurende de hele levenscyclus van het document alive; onnodig opnieuw aanmaken voegt overhead toe.

## Hoe een SDT toe te voegen – stap 2: een plain‑text Structured Document Tag invoegen

Een SDT (Structured Document Tag) is de technische benaming voor een content control. Om **hoe een sdt toe te voegen** te doen, instantiateer je een `StructuredDocumentTag` met het gewenste type.

```csharp
        // Create a plain‑text SDT (content control)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document,
            SdtType.PlainText,   // Plain‑text control
            true);               // Is it a repeating section? false for single use

        // Give the control a title – this is how you reference it later
        sdt.Title = "CustomerName";

        // Insert the SDT at the current cursor position
        builder.InsertNode(sdt);
```

De optie `SdtType.PlainText` maakt een eenvoudige tekstvak dat gebruikers kunnen bewerken. Het instellen van de `Title` helpt je de control later te vinden wanneer je de inhoud wilt ophalen of wijzigen.

## Hoe een placeholder in te stellen – stap 3: placeholder‑tekst configureren

Een placeholder begeleidt de eindgebruiker door voorbeeldtekst te tonen voordat ze iets typen. Om **hoe een placeholder in te stellen** te doen, ken je de eigenschap `PlaceholderName` toe.

```csharp
        // Define the placeholder that appears when the control is empty
        sdt.PlaceholderName = "Enter name here";
```

Wanneer het document wordt geopend in Microsoft Word, verschijnt de grijze placeholder‑tekst binnen de control totdat de gebruiker een waarde invoert.

## Hoe standaardtekst te schrijven – stap 4: initiële inhoud in de SDT toevoegen

Wil je dat de control vooraf gedefinieerde inhoud bevat, dan moet je de builder naar binnen de SDT verplaatsen en de tekst schrijven. Dit demonstreert **hoe standaardtekst te schrijven**.

```csharp
        // Position the builder inside the SDT so we can add content
        builder.MoveTo(sdt);

        // Write the default text that will be visible initially
        builder.Write("John Doe");
```

De aanroep van `MoveTo` verplaatst de cursor naar het interieur van de SDT. Na `Write` toont de control “John Doe” als initiële waarde.

## Plain‑text control invoegen – stap 5: het document opslaan

Sla tenslotte het document op schijf op. Hiermee is de **plain‑text control invoegen**‑operatie voltooid.

```csharp
        // Save the document with the content control embedded
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CustomerNameControl.docx");

        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wanneer je `CustomerNameControl.docx` in Word opent, zie je een plain‑text content control met de titel **CustomerName**, de placeholder “Enter name here” en de standaardtekst “John Doe”.

### Verwachte output

- Een `.docx`‑bestand op het bureaublad genaamd `CustomerNameControl.docx`.
- In het bestand één content control met de tekst **John Doe**.
- De placeholder‑tekst verschijnt in lichtgrijs totdat de gebruiker een nieuwe waarde invoert.

## Aanvullende variaties en randgevallen

### Meerdere content controls toevoegen

Je kunt de **hoe een sdt toe te voegen**‑stappen herhalen om verschillende controls in hetzelfde document te plaatsen. Maak simpelweg een nieuwe `StructuredDocumentTag` voor elk veld en verplaats de builder overeenkomstig.

```csharp
// Example: add a second control for "OrderNumber"
StructuredDocumentTag orderTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
orderTag.Title = "OrderNumber";
orderTag.PlaceholderName = "Enter order #";
builder.InsertNode(orderTag);
builder.MoveTo(orderTag);
builder.Write("12345");
```

### Een placeholder programmatisch lezen

Als je wilt verifiëren dat een placeholder correct is ingesteld, inspecteer je de eigenschap `PlaceholderName`:

```csharp
string placeholder = sdt.PlaceholderName; // returns "Enter name here"
```

### Andere SDT‑types gebruiken

Aspose.Words ondersteunt dropdown‑lijsten, datumkiezers en rich‑text controls. Vervang `SdtType.PlainText` door `SdtType.DropDownList` of `SdtType.RichText` om het type control te wijzigen.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Symptoom | Oorzaak | Oplossing |
|----------|---------|-----------|
| Placeholder verschijnt nooit | Het document werd opgeslagen voordat de placeholder werd toegewezen | Zorg dat `PlaceholderName` **vóór** het aanroepen van `Save` is ingesteld. |
| Standaardtekst ontbreekt | Builder is niet naar binnen de SDT verplaatst | Roep `builder.MoveTo(sdt)` aan vóór `builder.Write`. |
| Control‑titel is leeg | Eigenschap `Title` niet ingesteld | Ken altijd een betekenisvolle `Title` toe voor later ophalen. |

## Conclusie

Je weet nu **hoe een content control te maken** in C# met Aspose.Words, inclusief **hoe een sdt toe te voegen**, **hoe een placeholder in te stellen**, **hoe standaardtekst te schrijven**, en **plain‑text control invoegen**. Het volledige voorbeeld compileert tot een kant‑klaar Word‑bestand dat elk concept demonstreert.

Vanaf hier kun je meer geavanceerde scenario’s verkennen, zoals het binden van content controls aan XML‑data, het behandelen van herhalende secties, of het converteren van het document naar PDF terwijl de controls behouden blijven. Elk van die onderwerpen bouwt direct voort op de basisprincipes die in deze tutorial behandeld zijn.

Happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rich Text Box Content Control](/words/hindi/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/hongkong/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/spanish/net/programming-with-sdt/rich-text-box-content-control/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
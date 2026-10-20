---
category: general
date: 2026-10-20
description: Stel placeholder-tekst in een Word‑document in met C#. Leer hoe je snel
  controle toevoegt en een placeholder instelt met Aspose.Words voor .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: nl
lastmod: 2026-10-20
og_description: Stel placeholder‑tekst in een Word‑document in met C#. Deze tutorial
  laat zien hoe je een controle toevoegt, een placeholder instelt en Word‑bestanden
  automatisch genereert.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Placeholder‑tekst instellen in een Word‑document met C# – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Placeholder‑tekst instellen in een Word‑document met C#
url: /nl/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Placeholdertekst instellen in een Word‑document met C#

Als je **placeholdertekst wilt instellen** in een Microsoft Word‑bestand terwijl je het genereert met C#, laat deze gids je precies zien hoe. Je ziet een beknopte, end‑to‑end‑oplossing die een content control toevoegt, de placeholder definieert en het document opslaat — allemaal met Aspose.Words voor .NET.

Veel ontwikkelaars vragen zich af **hoe je een control toevoegt** aan een Word‑document of **hoe je een placeholder instelt** zonder Word handmatig te openen. Deze tutorial beantwoordt die vragen en laat ook een nette manier zien om **Word C# genereren**‑bestanden te maken die klaar zijn voor gebruikersinvoer.

## Wat je zult bereiken

* Maak een leeg Word‑document programmatically aan.  
* Een platte‑tekst Structured Document Tag (SDT) invoegen, wat de technische naam is voor een content control.  
* Een betekenisvolle titel en placeholder‑tekst toewijzen aan de SDT.  
* Het resulterende `.docx`‑bestand opslaan op schijf.

Geen extra tools zijn vereist naast de Aspose.Words‑bibliotheek en een .NET 6 (of later) ontwikkelomgeving.

## Vereisten

* .NET 6 SDK of nieuwer geïnstalleerd.  
* Visual Studio 2022 (of een IDE die .NET ondersteunt).  
* Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`).  

> **Pro tip:** Gebruik de gratis evaluatieversie van Aspose.Words als je alleen test; deze voegt een watermerk toe maar werkt verder hetzelfde als de gelicentieerde versie.

## Stap 1: Het project instellen en namespaces importeren

Maak een nieuw console‑project aan en voeg de vereiste `using`‑directieven toe. Deze brengen de kern‑klassen van Aspose.Words en de markup‑namespace in scope.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Waarom deze stap belangrijk is:* Het importeren van `Aspose.Words.Markup` geeft je toegang tot `StructuredDocumentTag`, `SdtType` en `MarkupLevel` — de objecten die nodig zijn om **control toevoegen** en **placeholder instellen** toe te voegen.

## Stap 2: Een leeg document en een DocumentBuilder maken

Een `Document` vertegenwoordigt het volledige Word‑bestand, terwijl een `DocumentBuilder` een handige cursor biedt voor het invoegen van elementen.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom deze stap belangrijk is:* Beginnen met een schoon document zorgt ervoor dat de placeholder die je instelt precies op de gewenste plek verschijnt, zonder interferentie van bestaande inhoud.

## Stap 3: De content control maken (Structured Document Tag)

Hier maken we een platte‑tekst SDT, geven het een titel en stellen we de placeholder‑tekst in die de gebruiker ziet wanneer de control leeg is.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Waarom deze stap belangrijk is:* De eigenschap `Title` stelt je in staat om later naar de control te verwijzen (bijv. voor databinding). `PlaceholderName` is precies de **placeholdertekst instellen** die je wilt laten verschijnen, en begeleidt de eindgebruiker.

## Stap 4: De control op de huidige cursorpositie invoegen

Gebruik de `DocumentBuilder` om de SDT in het document in te voegen op de positie waar de builder zich momenteel bevindt.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Waarom deze stap belangrijk is:* Het invoegen van de node koppelt de control aan de DOM van het document. Als je meerdere placeholders moet toevoegen, kun je de cursor van de builder verplaatsen en deze stap herhalen.

## Stap 5: Het document opslaan

Schrijf tenslotte het document naar schijf. Vervang `YOUR_DIRECTORY` door een daadwerkelijk pad op jouw machine.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wanneer je `SDT.docx` opent in Microsoft Word, zie je een grijs gekleurde inline‑tekstvak met de tekst **Enter name here**. Als je in het vak klikt, verdwijnt de placeholder, waardoor de gebruiker een klantnaam kan typen.

### Verwachte output

| Bestandslocatie | Inhoudsvoorbeeld |
|-----------------|------------------|
| `C:\Temp\SDT.docx` | Inline placeholder **Enter name here** in een platte‑tekst content control met de titel *CustomerName*. |

## Randgevallen en variaties

| Situatie | Aanbevolen aanpassing |
|----------|-----------------------|
| **Multiple placeholders** | Maak extra `StructuredDocumentTag`‑objecten aan met verschillende `Title`‑ en `PlaceholderName`‑waarden, en voeg elk in waar nodig. |
| **Rich‑text placeholder** | Gebruik `SdtType.RichText` in plaats van `PlainText` om opmaak binnen de placeholder toe te staan. |
| **Block‑level control** | Verander `MarkupLevel.Inline` naar `MarkupLevel.Block` zodat de control zich gedraagt als een volledige alinea. |
| **Placeholder not visible** | Zorg ervoor dat de weergave‑instellingen van het document in Word niet zijn ingesteld om content controls te verbergen (`File → Options → Advanced → Show content controls`). |
| **Saving to a stream** | Roep `doc.Save(stream, SaveFormat.Docx)` aan als je het bestand via HTTP wilt verzenden in plaats van naar schijf te schrijven. |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren. Het bevat alle bovenstaande stappen in één `Main`‑methode.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Voer het programma uit, open het gegenereerde bestand, en je ziet de placeholder‑tekst klaar voor gebruikersinvoer.

## Veelgestelde vragen beantwoord

**Q: Werkt dit met .NET Core?**  
A: Ja. Aspose.Words for .NET is compatibel met .NET Core, .NET 5 en .NET 6+. Dezelfde code werkt ongewijzigd.

**Q: Kan ik een standaardwaarde instellen naast de placeholder?**  
A: Gebruik `sdt.SetText("Default value")` na het aanmaken van de SDT. De placeholder verdwijnt zodra er een waarde is ingesteld.

**Q: Wat als ik later de ingevoerde waarde moet ophalen?**  
A: Laad het document, zoek de SDT op basis van zijn `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) en lees `sdt.GetText()`.

## Conclusie

Je weet nu hoe je **placeholdertekst kunt instellen** in een Word‑document met C#. Door een platte‑tekst `StructuredDocumentTag` te maken, een titel en placeholder toe te wijzen, deze in te voegen met een `DocumentBuilder` en het bestand op te slaan, kun je **control toevoegen** en **Word C#**‑bestanden programmatically genereren.

Vanuit hier kun je verder gaan met:

* Rich‑text of dropdown‑lijst controls toevoegen (`SdtType.RichText`, `SdtType.DropDownList`).  
* Meerdere placeholders vullen vanuit een database.  
* Het gegenereerde `.docx` naar PDF converteren met Aspose.Words.

Experimenteer met verschillende control‑types en placeholder‑stijlen om aan de behoeften van je applicatie te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Placeholdertekst instellen in Aspose.Words – Complete C#‑gids](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Word‑document programmatically maken – content control en placeholder toevoegen](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Hoe content control toe te voegen en Word‑document te maken met Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-08-04
description: Maak een Word‑document via code met C#. Leer hoe je een contentcontrol
  toevoegt aan Word en placeholder‑tekst instelt voor dynamische sjablonen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: nl
lastmod: 2026-08-04
og_description: Maak een Word‑document programmatisch met C#. Deze gids laat zien
  hoe je een inhoudsbesturingselement toevoegt aan Word en placeholder‑tekst instelt
  voor herbruikbare sjablonen.
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: Maak een Word‑document programmatically – voeg inhoudsbesturingselement
  en placeholder toe
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: Maak een Word-document programmatisch – voeg een inhoudsbesturingselement en
  een placeholder toe
url: /nl/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑document programmatically maken – content control en placeholder toevoegen

Als je **een Word‑document programmatically wilt maken**, laat deze tutorial je een complete, kant‑klaar werkende oplossing zien. Je ziet hoe je **content control aan Word toevoegt**, het een betekenisvolle titel geeft, en **placeholder‑tekst voor Word instelt** zodat eindgebruikers later gegevens kunnen invullen.

De gids loopt stap voor stap door elke regel code, legt uit waarom elke stap belangrijk is, en wijst op veelvoorkomende valkuilen. Aan het einde heb je een herbruikbaar .docx‑bestand dat kan dienen als sjabloon voor facturen, contracten of elk formulier‑gebaseerd document.

## Prerequisites

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 (of later) geïnstalleerd – de code maakt gebruik van de nieuwste C#‑taalfeatures.
* Een Aspose.Words for .NET‑licentie (de gratis trial werkt voor ontwikkeling).
* Visual Studio 2022 of een andere IDE die .NET‑projecten kan bouwen.
* Basiskennis van C# en het concept van Structured Document Tags (SDT’s).

> **Pro tip:** Als je het voorbeeld zonder licentie uitvoert, voegt Aspose.Words een klein watermerk toe aan het opgeslagen bestand. Plaats je licentie vroeg in het programma om dit te voorkomen.

## Stap 1: Het project opzetten en namespaces importeren

Maak een nieuw console‑project en voeg het Aspose.Words NuGet‑pakket toe.

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

Importeer nu de benodigde namespaces in `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Deze namespaces geven je toegang tot de klassen `Document`, `DocumentBuilder` en `StructuredDocumentTag`, die essentieel zijn voor **het programmatically maken van een Word‑document**.

## Stap 2: Een leeg document en een builder initialiseren

De `Document`‑klasse vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` je in staat stelt inhoud op een specifieke cursorlocatie te plaatsen.

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Waarom dit belangrijk is*: Beginnen met een leeg `Document` zorgt ervoor dat je volledige controle hebt over elk element dat je invoegt. De `DocumentBuilder` onderhoudt een interne cursor, zodat je knooppunten precies kunt invoegen waar je ze nodig hebt.

## Stap 3: Een plain‑text Structured Document Tag (SDT) maken

Een Structured Document Tag is de technische naam voor een **content control** in Word. We maken een inline plain‑text‑tag die zich gedraagt als een placeholder‑veld.

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*Waarom dit belangrijk is*: Het gebruik van `StructuredDocumentTagType.PlainText` vertelt Word dat de control alleen platte tekst accepteert. `MarkupLevel.Inline` laat de control zich gedragen als een gewoon woord binnen een alinea, wat ideaal is voor formulier‑velden.

## Stap 4: Een titel en placeholder‑tekst toewijzen

De **title** is de interne identifier die je applicatie later kan opvragen. De **placeholder** is de grijs weergegeven hint die aan de gebruiker wordt getoond voordat hij iets typt.

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

Hier **stellen we placeholder‑tekst voor Word in** op “Enter name here”. Wanneer het document wordt geopend in Microsoft Word, verschijnt de placeholder in lichtgrijs totdat de gebruiker een waarde invoert.

## Stap 5: De content control op de huidige cursorpositie invoegen

`DocumentBuilder.InsertNode` plaatst de SDT precies waar de cursor van de builder zich bevindt. Standaard staat de cursor aan het begin van de eerste alinea.

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

Als je de control binnen een specifieke alinea nodig hebt, verplaats dan eerst de cursor:

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

Dit voorbeeld laat zien hoe je **content control aan Word toevoegt** terwijl je de omliggende tekst behoudt.

## Stap 6: Het document opslaan

Sla tenslotte het bestand op schijf op. Je kunt elke map kiezen; zorg er alleen voor dat de applicatie schrijfrechten heeft.

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wanneer je `SDT.docx` opent in Microsoft Word, zie je de placeholder “Enter name here” in een lichtgrijze doos. Gebruikers kunnen op de doos klikken en de hint vervangen door de daadwerkelijke klantnaam.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het complete programma dat je kunt kopiëren, plakken en uitvoeren zonder aanpassingen (behalve het output‑pad).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Verwachte output** – Wanneer je het programma uitvoert, print de console het bestandspad, en het gegenereerde Word‑bestand bevat één regel tekst gevolgd door een grijze placeholder met de tekst “Enter name here”.

## Veelvoorkomende variaties en randgevallen

| Scenario | Hoe de code aan te passen |
|----------|---------------------------|
| **Meerdere regels placeholder** | Gebruik `StructuredDocumentTagType.RichText` in plaats van `PlainText` en stel `plainTextTag.MultipleLines = true;` in. |
| **Dezelfde control herhalen** | Clone de tag met `plainTextTag.Clone(true)` en voeg de kloon in waar nodig. |
| **Binden aan gegevensbron** | Nadat de gebruiker het document heeft ingevuld, haal je de waarde op met `document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();`. |
| **Control vergrendelen** | Stel `plainTextTag.LockContentControl = true;` in om te voorkomen dat gebruikers de control verwijderen. |
| **Placeholder‑kleur wijzigen** | Word biedt geen placeholder‑styling via de SDK; je moet de sjabloon handmatig bewerken of een Word‑macro gebruiken. |

Deze variaties laten je **content control aan Word toevoegen** in complexere scenario’s, zoals herhaalbare tabellen of vergrendelde secties.

## Best practices en probleemoplossing

* **Altijd een title instellen** – Zonder title wordt het later lastig om de control te vinden.
* **Vermijd lege placeholders** – Word verbergt een lege placeholder als de eigenschap `ShowPlaceholderText` van de control `false` is. Houd deze `true` voor een betere UX.
* **Valideer het output‑pad** – Als `document.Save` een `UnauthorizedAccessException` gooit, controleer dan of de map bestaat en of je proces schrijfrechten heeft.
* **Licentie vroeg plaatsen** – Plaats de licentiecode vóórdat er Aspose.Words‑objecten worden gecreëerd om het trial‑watermerk te voorkomen.

## Conclusie

Je weet nu hoe je **een Word‑document programmatically maakt**, **content control aan Word toevoegt**, en **placeholder‑tekst voor Word instelt** met Aspose.Words for .NET. Het volledige voorbeeld toont elke vereiste stap, van het initialiseren van het document tot het opslaan van een sjabloon dat eindgebruikers kunnen invullen.

Vervolgens kun je verkennen:

* Het toevoegen van **herhalende content controls** voor tabellen (secundaire zoekterm: add content control to word).
* Het vullen van de placeholders met gegevens uit een database (secundaire zoekterm: set placeholder text word).
* Het converteren van de gegenereerde .docx naar PDF of HTML voor downstream verwerking.

Voel je vrij om te experimenteren met verschillende tag‑types, styling en data‑binding technieken. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑features onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
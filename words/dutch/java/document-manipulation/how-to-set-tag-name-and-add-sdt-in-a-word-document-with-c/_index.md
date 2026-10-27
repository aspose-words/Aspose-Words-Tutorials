---
category: general
date: 2026-09-08
description: Stel de tagnaam in en maak een contentcontrol (SDT) in een Word‑document
  met C#. Leer hoe je een SDT toevoegt, tekst naar de tag schrijft en het document
  wijzigt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: nl
lastmod: 2026-09-08
og_description: Stel de tagnaam in en maak een contentcontrol (SDT) in een Word‑document
  met C#. Volg deze stapsgewijze handleiding om een SDT toe te voegen, tekst naar
  de tag te schrijven en het document te wijzigen.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Stel tagnaam in en voeg SDT toe in een Word‑document – C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een tagnaam instellen en een SDT toevoegen in een Word‑document met C#
url: /nl/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe tagnaam instellen en SDT toevoegen in een Word-document met C#

Als je **tagnaam moet instellen** voor een StructuredDocumentTag (SDT) tijdens het werken met Word‑bestanden, laat deze gids je precies zien hoe. Je ziet een volledig, uitvoerbaar voorbeeld dat **een content control maakt**, tekst naar de tag schrijft, en **het Word‑document** van begin tot eind **wijzigt**.

Ontwikkelaars vragen vaak: *“hoe sdt toe te voegen* aan een bestaande .docx en vervolgens *tekst naar tag te schrijven*?” – het antwoord ligt in het gebruik van de Aspose.Words for .NET API. Aan het einde van deze tutorial kun je een Word‑bestand openen, een platte‑tekst SDT invoegen, de tagnaam instellen, deze vullen met inhoud, en de wijzigingen opslaan zonder achtergebleven resources.

## Vereisten

* .NET 6.0 of later geïnstalleerd.
* Een geldige Aspose.Words for .NET licentie (of je kunt werken met de evaluatieversie).
* Visual Studio 2022 (of een IDE die C# ondersteunt).
* Een invoer‑Word‑document (`input.docx`) geplaatst in een map die je vanuit code kunt refereren.

## Stap 1: Het project opzetten en namespaces importeren

Maak een nieuw Console‑App‑project aan en voeg het Aspose.Words NuGet‑pakket toe:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Voeg vervolgens de benodigde `using`‑directieven toe aan de bovenkant van `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Deze namespaces geven je toegang tot `Document`, `DocumentBuilder` en de `StructuredDocumentTag`‑klasse, die essentieel zijn voor **het wijzigen van een Word‑document**.

## Stap 2: Het bestaande Word‑document laden

De eerste handeling is het laden van het bestand dat je wilt bewerken. Deze stap is vereist voor elk scenario waarin je **inhoud van een Word‑document** wijzigt.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Waarom we het document eerst laden** – Het `Document`‑object vertegenwoordigt het volledige .docx‑pakket in het geheugen. Alleen na het laden kun je veilig nieuwe knooppunten zoals een SDT invoegen.

## Stap 3: Een StructuredDocumentTag (SDT) invoegen en de tagnaam instellen

Nu beantwoorden we de kernvraag: **hoe sdt toe te voegen** en **tagnaam in te stellen**. We gebruiken `DocumentBuilder.InsertStructuredDocumentTag` met `SdtType.PlainText`. Het tweede argument is de tagnaam, die je later programmatisch of via de UI van Word kunt refereren.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Uitleg** – `InsertStructuredDocumentTag` retourneert een `StructuredDocumentTag`‑instantie. Door `"MyTag"` door te geven, **stellen we de tagnaam** direct bij het maken in. Als je deze later wilt wijzigen, kun je een nieuwe waarde toewijzen aan `sdt.Tag`.

## Stap 4: Tekst schrijven naar de nieuw aangemaakte tag

Nadat de SDT bestaat, wil je doorgaans **tekst naar de tag schrijven** zodat eindgebruikers een placeholder of standaardinhoud zien. De `SetText`‑methode doet precies dat.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Waarom SetText gebruiken** – Direct toewijzen aan de `Text`‑eigenschap zou de volledige knooppunt‑hiërarchie vervangen. `SetText` werkt de binnenste tekst van de content control veilig bij terwijl de structuur behouden blijft.

## Stap 5: Het gewijzigde document opslaan

Sla tenslotte de wijzigingen op in een nieuw bestand. Dit voltooit de **wijzig Word‑document** workflow.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Wanneer je `output.docx` opent in Microsoft Word, zie je een platte‑tekst content control met het label **MyTag** dat de tekst “Sample content” bevat. De control kan handmatig worden bewerkt, en de tagnaam blijft toegankelijk via de ontwikkelaarstools van Word.

## Volledige broncode

Hieronder staat het volledige, zelfstandige programma. Kopieer het naar `Program.cs` en voer het uit; er zijn geen extra fragmenten nodig.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Verwachte uitvoer in de console

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Hoe het resulterende Word‑bestand eruitziet

![Word-document dat een content control toont met de naam MyTag en de tekst “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Voorbeeld van tagnaam instellen in een Word-document"}

*De screenshot illustreert de SDT met de **tagnaam** ingesteld op *MyTag* en de ingesloten tekst zichtbaar.*

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe op te lossen |
|-----------|------------------|
| **Een rich‑text SDT maken** | Gebruik `SdtType.RichText` in plaats van `PlainText`. |
| **Een andere tagnaam instellen na invoegen** | `sdt.Tag = "NewTag";` – je kunt de tagnaam op elk moment opnieuw toewijzen. |
| **De SDT toevoegen binnen een specifieke alinea** | Verplaats de cursor van de builder (`builder.MoveToParagraph(index)`) voordat je `InsertStructuredDocumentTag` aanroept. |
| **Meerdere SDT's in hetzelfde document** | Herhaal stappen 3‑4 voor elke control; elk kan een unieke tagnaam hebben. |
| **Werken met beveiligde documenten** | Zorg ervoor dat het document niet beveiligd is (`doc.Unprotect()`) voordat je een SDT invoegt. |

## Pro‑tips voor robuuste Word‑automatisering

* **Licentie vroeg** – Roep `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` aan het begin van `Main` aan om evaluatiewatermerken te vermijden.
* **Objecten vrijgeven** – Plaats `Document` in een `using`‑blok als je .NET Framework target om te garanderen dat bestands‑handles worden vrijgegeven.
* **Tag‑bestaan valideren** – Bij het later lezen van een document, gebruik `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` om tags te vinden op basis van de `Tag`‑eigenschap.
* **Prestaties** – Voor grote documenten, laad alleen de benodigde secties met `LoadOptions` en `LoadFormat.Docx` en `LoadFormat.Auto`.  

## Conclusie

Je weet nu hoe je **tagnaam instelt**, **een content control maakt**, **tekst naar tag schrijft**, en **een Word‑document wijzigt** met C#. Het volledige voorbeeld toont het standaardpatroon voor **hoe sdt toe te voegen** en wijzigingen veilig te bewaren.  

Vanaf hier

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Word Document - How to Remove Content](/words/english/net/remove-content/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
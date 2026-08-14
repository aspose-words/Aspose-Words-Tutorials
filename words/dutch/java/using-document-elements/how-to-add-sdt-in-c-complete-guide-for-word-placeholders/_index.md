---
category: general
date: 2026-08-14
description: Hoe voeg je snel een SDT toe met Aspose.Words. Leer hoe je een woordplaceholder
  maakt en een platte‑tekst besturingselement invoegt in een .docx‑bestand.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: nl
lastmod: 2026-08-14
og_description: Hoe voeg je SDT toe in C# met Aspose.Words. Volg deze tutorial om
  een placeholder te maken en een platte‑tekstbesturingselement in te voegen voor
  dynamische documenten.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Hoe SDT toe te voegen in C# – stap‑voor‑stap Word‑plaatsaanduidingsgids
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Hoe SDT toe te voegen in C# – volledige gids voor Word-plaatsaanduidingen
url: /nl/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe SDT toe te voegen in C# – volledige gids voor Word-plaatsaanduidingen

Als je **how to add sdt** in een Word‑bestand moet toevoegen, laat deze tutorial je de exacte stappen zien met Aspose.Words for .NET. Aan het einde van de gids kun je **create word placeholder**‑tags maken waarmee eindgebruikers direct in een document kunnen typen, en begrijp je hoe je **insert plain text control** betrouwbaar kunt invoegen.

Werken met Structured Document Tags (SDTs) verwijdert de noodzaak voor handmatige formuliervelden en biedt je een schone, programmeerbare manier om dynamische contracten, rapporten of brieven te bouwen. Het voorbeeld hieronder behandelt alles van projectopzet tot het opslaan van het uiteindelijke .docx‑bestand, zodat je de code kunt kopiëren‑plakken in je eigen oplossing zonder enige afhankelijkheid te missen.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
- Visual Studio 2022 of een C#‑IDE naar keuze
- Een Aspose.Words for .NET‑licentie (een gratis tijdelijke licentie werkt voor testen)
- Basiskennis van C#‑syntaxis en het concept van SDTs

> **Pro tip:** Als je van plan bent de gegenereerde documenten te distribueren, voeg dan een licentiebestand in om de evaluatiewatermark te vermijden.

## Stap 1: Het project instellen en Aspose.Words importeren

Maak een nieuwe console‑applicatie en voeg het Aspose.Words NuGet‑pakket toe:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Deze `using`‑directieven geven je toegang tot de `Document`, `DocumentBuilder` en `StructuredDocumentTag`‑klassen die nodig zijn voor **insert plain text control**‑operaties.

## Stap 2: Het document en de builder initialiseren

Het eerste code‑blok maakt een leeg Word‑document en een `DocumentBuilder` waarmee je inhoud kunt schrijven.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` werkt als een cursor; elke volgende aanroep voegt inhoud toe op de huidige positie. Het initialiseren van het document is de basis voor elk **how to add sdt**‑scenario omdat de SDT moet behoren tot een actief `Document`‑object.

## Stap 3: Een platte‑tekst Structured Document Tag (SDT) invoegen

Nu **insert plain text control** die fungeert als een placeholder waar een gebruiker een naam, datum of een willekeurige waarde kan typen.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` vertelt Aspose.Words om een eenvoudig tekstveld te maken.
- `SdtAppearanceTags.Default` geeft de tag de standaard Word‑visuele stijl (een schaduwvak wanneer het document in Word wordt geopend).

## Stap 4: De SDT configureren met een titel en placeholder‑tekst

Een goed benoemde SDT maakt het document zelfverklarend voor eindgebruikers. Hier **create word placeholder**‑metadata en stellen we de hint in die in het veld verschijnt.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` is de interne identifier die je later kunt gebruiken bij het programmatically extraheren of bijwerken van de waarde.
- `PlaceholderName` is de grijs weergegeven hint die in Word wordt getoond, zodat de gebruiker weet wat hij moet typen.

## Stap 5: Omringende inhoud toevoegen

Een document bestaat zelden uit één enkele SDT. Meestal heb je gewone alinea's vóór en na de placeholder nodig. Gebruik de `WriteLine`‑methode van de builder om statische tekst toe te voegen.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

De aanroep van `InsertNode` plaatst de eerder gemaakte SDT precies waar je het nodig hebt, en behoudt de omringende tekststroom.

## Stap 6: Het document opslaan als een .docx‑bestand

Sla tenslotte het document op schijf op. Het pad kan absoluut of relatief ten opzichte van de projectmap zijn.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Het openen van `SDT.docx` in Microsoft Word toont een grijze placeholder met de tekst **Enter name here**. Gebruikers kunnen op het veld klikken, een waarde typen, en het document zal die waarde behouden bij opnieuw opslaan.

## Volledig, uitvoerbaar voorbeeld

Alle onderdelen samenvoegen levert een zelfstandige applicatie op die je direct kunt uitvoeren:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Verwachte output** wanneer je het programma uitvoert:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Het openen van het gegenereerde `SDT.docx` toont:

```
Dear [Enter name here],
After the SDT
```

De tekst tussen haakjes is de **insert plain text control**‑placeholder die gebruikers kunnen vervangen.

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe de code aan te passen |
|-----------|---------------------------|
| **Meerdere placeholders** | Call `InsertStructuredDocumentTag` repeatedly and give each tag a unique `Title`. |
| **Rich‑text SDT** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Placeholder vergrendelen** | Set `plainTextTag.LockContentControl = true;` to prevent users from deleting the field. |
| **Vooraf invullen met een waarde** | Assign `plainTextTag.Text = "John Doe";` before saving. |
| **Voorwaardelijke weergave** | Use `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` for a tick‑box control. |

Deze variaties laten je **create word placeholder**‑structuren maken die bijna elk formulier‑achtig scenario passen.

## Tips voor probleemoplossing

- **Placeholder not visible** – Zorg ervoor dat je het bestand opent in Microsoft Word (of een compatibele viewer). Sommige lichte editors verbergen SDTs.
- **License warning** – Als je een evaluatiewatermark ziet, controleer dan of je licentiebestand correct is geladen (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Na het invoegen van een SDT blijft de cursor van de builder *na* de tag staan. Als je tekst *binnen* de tag moet toevoegen, gebruik dan `builder.MoveTo(plainTextTag);` vóór het schrijven.

## Conclusie

Je weet nu **how to add sdt** aan een Word‑document met Aspose.Words for .NET, hoe je **create word placeholder**‑tags maakt, en hoe je **insert plain text control** kunt invoegen die gebruikers direct in Word kunnen bewerken. Het volledige voorbeeld toont initialisatie, tag‑invoeging, configuratie, omringende inhoud en opslaan — allemaal in één enkel uitvoerbaar programma.

Vervolgens kun je gerelateerde onderwerpen verkennen zoals **insert rich text control**, **populate SDTs from a database**, of **convert the final document to PDF**. Al deze bouwen voort op dezelfde basisprincipes die hier behandeld zijn, zodat je jouw automatiseringspipeline vol vertrouwen kunt uitbreiden.

Veel plezier met coderen, en voel je vrij om te experimenteren met verschillende SDT‑typen om aan je document‑automatiseringsbehoeften te voldoen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe formuliervelden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hoe bewerkbare bereiken te maken in alleen‑lezen documenten met Aspose.Words voor Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Bladwijzers toevoegen in Word met Aspose.Words voor Java – Invoegen, bijwerken, verwijderen](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
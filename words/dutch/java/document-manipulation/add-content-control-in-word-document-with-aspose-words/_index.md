---
category: general
date: 2026-09-11
description: Voeg een contentcontrol toe in een Word‑document met Aspose.Words. Volg
  deze stapsgewijze handleiding om een platte‑tekst Structured Document Tag (SDT)
  programmeermatig in te voegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: nl
lastmod: 2026-09-11
og_description: Voeg een inhoudsbesturingselement toe aan een Word‑document met Aspose.Words.
  Deze gids laat zien hoe je via code een platte‑tekst Structured Document Tag (SDT)
  kunt invoegen en aanpassen.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Contentcontrol toevoegen in Word‑document – volledige Aspose.Words‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: Inhoudsbesturingselement toevoegen in Word‑document met Aspose.Words
url: /nl/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Content control toevoegen in Word-document met Aspose.Words

Als je programmatically **content control toevoegen in Word-document** wilt, laat deze tutorial je precies zien hoe je dat doet met Aspose.Words voor .NET. Of je nu een document‑generatieservice bouwt of het maken van formulieren automatiseert, je leert een plain‑text Structured Document Tag (SDT) in te voegen en er een betekenisvolle titel aan te geven.

In deze gids zie je een volledig, uitvoerbaar voorbeeld dat elke vereiste import behandelt, uitlegt waarom elke API‑aanroep belangrijk is, en laat zien hoe je het resultaat kunt verifiëren. Er zijn geen externe referenties nodig—kopieer gewoon de code, voer deze uit en open het gegenereerde *.docx*-bestand.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd  
* Visual Studio 2022 (of elke C#‑IDE)  
* Aspose.Words for .NET 23.5 of nieuwer – je kunt een gratis proef‑NuGet‑pakket verkrijgen  

Deze items vormen de minimale setup voor **word automation** met Aspose.Words.

## Stap 1: Het project instellen en namespaces importeren

Maak een nieuw console‑project aan en voeg het Aspose.Words‑pakket toe:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Open nu `Program.cs` en voeg de vereiste `using`‑directieven toe:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

Deze namespaces geven je toegang tot `DocumentBuilder`, `StructuredDocumentTag` en andere kern‑typen die nodig zijn om **content control toevoegen in Word-document**.

## Stap 2: Maak een nieuw document en een DocumentBuilder

Een `DocumentBuilder` is het primaire toegangspunt voor het bouwen van Word‑bestanden. Het bevat een cursor die bijhoudt waar het volgende element wordt ingevoegd.

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is*: Het `Document`‑object vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` het invoegen van alinea’s, tabellen en **content controls** zoals Structured Document Tags vereenvoudigt.

## Stap 3: Een plain‑text Structured Document Tag (SDT) invoegen

De kern van onze oplossing is de `insertStructuredDocumentTag`‑methode. Deze maakt een **content control** die platte tekst, datums, vervolgkeuzelijsten, enz. kan bevatten. Hier gebruiken we de enum‑waarde `SdtType.PLAIN_TEXT`.

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*Waarom dit belangrijk is*: Het instellen op `true` zorgt ervoor dat de control verschijnt als een lichtgrijze placeholder, wat eindgebruikers aangeeft dat ze het veld moeten invullen.

## Stap 4: Geef de SDT een titel voor latere identificatie

Een titel (of tag) stelt je in staat de control later te vinden, bijvoorbeeld wanneer je de inhoud programmatically wilt vervangen.

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

De titel verschijnt niet in de gebruikersinterface van het document, maar wordt opgeslagen in de onderliggende XML en kan worden opgevraagd via de Aspose.Words‑API.

## Stap 5: Voeg placeholder‑tekst toe binnen de SDT

Om de control gebruiksvriendelijker te maken, voeg je een standaard‑run toe die de gebruiker vertelt wat hij moet typen.

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*Waarom dit belangrijk is*: Het `Run`‑object vertegenwoordigt een stuk tekst. Door het aan de SDT toe te voegen, creëer je een zichtbare hint die verdwijnt zodra de gebruiker begint te typen.

## Stap 6: Sla het document op

Schrijf tenslotte het document naar schijf zodat je het kunt openen in Microsoft Word.

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

Wanneer je `ContentControlExample.docx` opent, zie je een grijs‑getinte content control met de titel **CustomerName** en de placeholder‑tekst *Enter name here*.

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt copy‑paste in `Program.cs`. Het bevat alle stappen, commentaren en benodigde foutafhandeling.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Verwachte output

Het uitvoeren van het programma geeft het volgende weer:

```
Document saved to ContentControlExample.docx
```

Het openen van het gegenereerde bestand in Word toont één content control met de grijze placeholder **Enter name here**. De control kan later worden bewerkt, verwijderd of programmatically benaderd met behulp van de titel *CustomerName*.

## Veelvoorkomende variaties en randgevallen

| Scenario | Hoe de code aan te passen |
|----------|---------------------------|
| **Meerdere content controls** | Roep `InsertStructuredDocumentTag` herhaaldelijk aan en wijs elke keer een unieke `Title` toe. |
| **Rich‑text content control** | Gebruik `SdtType.RichText` in plaats van `PlainText`. |
| **Date picker control** | Gebruik `SdtType.Date` en stel eventueel `sdt.DateDisplayFormat` in. |
| **Locking the control** | Stel `sdt.LockContentControl = true` in om te voorkomen dat gebruikers de control verwijderen. |
| **Finding a control later** | Gebruik `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` en filter op `Title`. |

Deze variaties illustreren de flexibiliteit van **Aspose.Words** wanneer je **content control moet toevoegen in Word-document** voor verschillende formulier‑invulscenario's.

## Pro‑tips

* **Performance** – Als je veel documenten in een lus genereert, hergebruik dan een enkele `DocumentBuilder`‑instantie en roep `doc.Clone()` aan voor elke iteratie om herhaalde objectconstructie te vermijden.  
* **Styling** – Je kunt een `ParagraphFormat` of `Font` toepassen op de placeholder‑`Run` om overeen te komen met het visuele thema van je document.  
* **Validatie** – Na het invoegen van een control kun je `sdt.IsShowingPlaceholderText` inspecteren om te bevestigen dat de placeholder correct wordt weergegeven.  

## Conclusie

Je weet nu hoe je **content control moet toevoegen in Word-document** met Aspose.Words, van het maken van een `DocumentBuilder` tot het invoegen van een plain‑text `StructuredDocumentTag`, het toewijzen van een titel en het toevoegen van placeholder‑tekst. Het volledige voorbeeld kan worden uitgebreid naar andere SDT‑typen, meerdere controls en geavanceerde lock‑ of styling‑opties.

Klaar om verder te gaan? Verken deze gerelateerde onderwerpen:

* **Werken met tabellen binnen content controls** – gebruik `DocumentBuilder.InsertTable` na de SDT.  
* **Gegevens extraheren uit ingevulde controls** – haal de `Sdt`‑node op via de titel en lees de `Text`‑eigenschap.  
* **Gebruik van OpenXML SDK** – een alternatieve aanpak als je de voorkeur geeft aan een gratis, door Microsoft ondersteunde bibliotheek.

Experimenteer met de code, pas deze aan je eigen workflow voor formulier‑generatie aan, en geniet van de kracht van programmatic Word automation.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Inhoud toevoegen met Document Builder in Aspose.Words voor .NET](/words/english/net/add-content-using-document-builder/)
- [Inline‑afbeelding invoegen in Word-document met Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Een Word-document met tabel maken met Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
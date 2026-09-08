---
category: general
date: 2026-09-08
description: Haal het scheidingsteken voor eindnoten op en toon het scheidingsteken
  voor voetnoten wanneer je een Word‑document laadt met Aspose.Words voor .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: nl
lastmod: 2026-09-08
og_description: Haal de eindnootseparator op en toon de voetnootseparator wanneer
  u een Word‑document laadt met Aspose.Words voor .NET.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: Eindnootscheiding ophalen tijdens het laden van een Word‑document in C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: Eindnoot scheidingsteken ophalen tijdens het laden van een Word‑document in
  C#
url: /nl/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Eindnootseparator ophalen tijdens het laden van een Word-document in C#

Als je een **eindnootseparator** uit een Word‑bestand moet **ophalen**, laat deze gids je precies zien hoe je dat doet. Je leert ook hoe je een **Word‑document** kunt **laden** met Aspose.Words en **de voetnootseparator**‑tekst in de console kunt **weergeven**, allemaal in één uitvoerbaar voorbeeld.

Werken met voetnoten en eindnoten is een veelvoorkomende eis voor juridische, academische of uitgeversapplicaties. Deze tutorial behandelt alles wat je nodig hebt—van het openen van het bestand tot het afhandelen van gevallen waarin een separator ontbreekt—zodat je de oplossing kunt integreren in elk .NET‑project zonder giswerk.

## Wat deze tutorial behandelt

* Hoe je een **Word‑document laadt** met de Aspose.Words API.  
* Hoe je een **eindnootseparator ophaalt** en waarom de separator belangrijk is.  
* Hoe je een **voetnootseparator weergeeft** op de console voor debugging of logging.  
* Afhandelen van edge‑cases wanneer een document geen voetnoten of eindnoten bevat.  
* Een volledige, kant‑klaar‑te‑kopiëren code‑voorbeeld dat draait op .NET 6 of hoger.  

### Vereisten

| Vereiste | Reden |
|----------|-------|
| .NET 6 SDK or newer | Levert de runtime voor het C#‑voorbeeld. |
| Aspose.Words for .NET (NuGet package `Aspose.Words`) | De bibliotheek die `Document.Footnotes` en `Document.Endnotes` beschikbaar maakt. |
| Een Word‑bestand (`Footnotes.docx`) dat minstens één voetnoot of eindnoot bevat | Toont de separators. |
| Any IDE (Visual Studio, Rider, VS Code) | Om het programma te compileren en uit te voeren. |

> **Pro tip:** Als je geen document met voetnoten hebt, maak dan snel een document in Microsoft Word: Invoegen → Voetnoot → typ wat tekst, en sla vervolgens op als `Footnotes.docx`.

## Word‑document laden met Aspose.Words

De eerste stap is om een **Word‑document te laden** in het geheugen. Aspose.Words leest het bestandsformaat en bouwt een objectmodel dat je kunt bevragen.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*Waarom dit belangrijk is*: Het laden van het document is de voorwaarde voor elke verdere manipulatie. Als het bestandspad onjuist is, gooit `Document` een `FileNotFoundException`, controleer dus het pad voordat je uitvoert.

## Voetnootseparator‑paragraaf ophalen

Een voetnootseparator is de paragraaf die visueel de hoofdtekst scheidt van de lijst met voetnoten. Het ophalen ervan stelt je in staat om de opmaak te inspecteren of aan te passen.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*Waarom dit belangrijk is*: **Voetnootseparator weergeven** helpt je te verifiëren dat de juiste paragraaf wordt benaderd, vooral wanneer je aangepaste opmaak moet toepassen (bijv. een lijn of een specifiek lettertype).

## Eindnootseparator‑paragraaf ophalen

Nu **halen we de eindnootseparator op**. Het proces is vergelijkbaar met de verwerking van voetnoten, maar maakt gebruik van de `Endnotes`‑collectie.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*Waarom dit belangrijk is*: De stap **eindnootseparator ophalen** is essentieel wanneer je de visuele scheiding tussen de hoofdinhoud en de lijst met eindnoten moet aanpassen—veelvoorkomend in academische publicaties waar eindnoten aan het einde van een hoofdstuk verschijnen.

### Ontbrekende separators afhandelen

Zowel `Footnotes.Separator` als `Endnotes.Separator` retourneren `null` wanneer het document geen separator definieert. Controleer altijd op `null` voordat je `GetText()` aanroept om een `NullReferenceException` te voorkomen. Als je een standaardseparator nodig hebt, kun je er een maken:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

Deze code injecteert een minimale separator zodat latere verwerking kan rekenen op het bestaan ervan.

## Verwachte console‑output

Wanneer het voorbeeld wordt uitgevoerd tegen een document dat één voetnoot en één eindnoot bevat, zie je iets vergelijkbaars:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

Als het document geen voetnoten of eindnoten bevat, print het programma de bijbehorende “niet gevonden”‑berichten, wat een nette foutafhandeling demonstreert.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren naar een nieuw C#‑console‑project. Er is geen extra code nodig.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

Sla het bestand op als `Program.cs`, voeg het Aspose.Words NuGet‑pakket toe (`dotnet add package Aspose.Words`), en voer `dotnet run` uit. Het programma zal de separator‑teksten afdrukken of je informeren als ze ontbreken.

## Veelvoorkomende variaties en wat‑als scenario's

| Scenario | Hoe de code aan te passen |
|----------|---------------------------|
| **Meerdere aangepaste separators** | Gebruik `doc.Footnotes.Separator` om de standaard te vervangen, en voeg vervolgens handmatig extra separator‑paragrafen toe met `doc.Footnotes.Add(separatorParagraph)`. |
| **Separatorstijl wijzigen** | Na het ophalen van de separator, wijzig de `ParagraphFormat` (bijv. `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **Werken met .doc‑bestanden** | Dezelfde API werkt; zorg er alleen voor dat het bestandspad eindigt op `.doc`. |
| **Verwerken van veel documenten** | Plaats het laden en ophalen van separators in een `foreach`‑lus; hergebruik een enkele `Document`‑instantie alleen als je deze reset met `doc = new Document(path)`. |

## Checklist best practices

- ✅ **Altijd controleren op `null`** voordat je de separator‑tekst benadert.  
- ✅ **Trim** het resultaat van `GetText()` om verborgen regeleinde‑tekens te verwijderen.  
- ✅ **Dispose** grote `Document`‑objecten als je veel bestanden in een batch verwerkt (gebruik `using` of roep `doc.Dispose()` aan).  
- ✅ **Log** separator‑tekst alleen tijdens ontwikkeling; vermijd het blootstellen ervan in productie‑logboeken tenzij vereist.  

## Conclusie

Je weet nu hoe je een **eindnootseparator kunt ophalen** terwijl je een **Word‑document laadt** en een **voetnootseparator weergeeft** in een .NET‑console‑applicatie. Het volledige voorbeeld toont het laden, opvragen en veilig afhandelen van ontbrekende separators, waardoor je een stevige basis krijgt voor elke taak met voetnoten of eindnoten.

Vervolgens kun je het volgende verkennen:

* **Aanpassen van voetnoot-/eindnootopmaak** – pas lettertypen, randen of nummeringsstijlen aan.  
* **Extractie van voetnoot-/eindnootinformatie** – doorloop de `doc.Footnotes`‑ of `doc.Endnotes`‑collecties.  
* **Het gewijzigde document opslaan** – gebruik `doc.Save("output.docx")` om de wijzigingen te bewaren.

Voel je vrij om te experimenteren met verschillende Word‑bestanden, separator‑stijlen en Aspose.Words‑functies. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe Word‑documenten te laden met Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Paragraaf‑stijlseparator ophalen in Word‑document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Een Word‑document maken en opmaken in Aspose.Words voor .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
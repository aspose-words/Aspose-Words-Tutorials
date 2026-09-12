---
category: general
date: 2026-09-11
description: Mail merge Aspose stelt je in staat om een Word‑sjabloon te laden en
  het Word‑sjabloon met gegevens te vullen, waardoor de documentgeneratie wordt geautomatiseerd
  voor het maken van gepersonaliseerde brieven.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: nl
lastmod: 2026-09-11
og_description: Mail merge Aspose stelt je in staat om een Word-sjabloon te laden
  en te vullen, waardoor de documentgeneratie wordt gestroomlijnd zodat je snel gepersonaliseerde
  brieven kunt maken.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mail merge aspose: een Word‑sjabloon in enkele minuten invullen'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Hoe een mail‑merge uit te voeren met Aspose om een Word‑sjabloon te vullen
url: /nl/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe voer je een mail‑merge uit met Aspose om een Word‑sjabloon te vullen

Als je **mail merge aspose** nodig hebt om een batch gepersonaliseerde brieven te genereren, laat deze gids je precies zien hoe je een Word‑sjabloon laadt, vult met gegevens en documentgeneratie automatiseert in een paar regels C#. Of je nu een mailing‑systeem of een rapportagetool bouwt, het volledige voorbeeld hieronder stelt je in staat gepersonaliseerde brieven te maken zonder handmatige merge‑logica te schrijven.

Je leert hoe je **word‑sjabloon laadt**, de low‑code `MailMerger`‑klasse gebruikt, en **word‑sjabloon vult** met een anonieme gegevensbron. Aan het einde van de tutorial heb je een kant‑klaar console‑applicatie die een samengevoegd Word‑document produceert dat je kunt e‑mailen, afdrukken of archiveren.

## Prerequisites

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 SDK of later geïnstalleerd  
* Een geldige Aspose.Words for .NET‑licentie (of een gratis evaluatiesleutel)  
* Het NuGet‑pakket `Aspose.Words` (versie 23.10 of nieuwer) geïnstalleerd in je project  
* Een Word‑bestand (`MailMergeTemplate.docx`) dat MERGEFIELD‑plaatsaanduidingen bevat, zoals **«Name»** en **«Age»**  

Je kunt het sjabloon maken in Microsoft Word door *Insert → Quick Parts → Field → MergeField* te kiezen en de velden exact dezelfde naam te geven als de eigenschapsnamen in je gegevensbron.

## Stap 1 – Bereid de gegevensbron voor de mail‑merge voor

De low‑code merge werkt met elke doorzoekbare collectie. In dit voorbeeld gebruiken we een array van anonieme objecten, maar je kunt ook een `DataTable`, een lijst van POCO’s, of gegevens uit een database doorgeven.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Waarom dit belangrijk is:**  
De eigenschapsnaam van elk object (`Name`, `Age`) moet overeenkomen met een MERGEFIELD in het sjabloon. De `MailMerger`‑klasse mappt de eigenschappen automatisch naar de velden, waardoor handmatige `FieldMerging`‑events overbodig worden.

## Stap 2 – Laad het Word‑sjabloon dat MERGEFIELDs bevat

Het laden van het sjabloon is eenvoudig met de `Document`‑klasse. Het pad kan absoluut zijn of relatief ten opzichte van de werkmap van het uitvoerbare bestand.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Pro tip:**  
Als je de code vanuit Visual Studio uitvoert, stel dan *Copy to Output Directory* voor het sjabloonbestand in op **Copy always**. Dit garandeert dat het bestand beschikbaar is wanneer de gecompileerde binary wordt uitgevoerd.

## Stap 3 – Maak een MailMerger‑instantie gekoppeld aan het sjabloon

De `MailMerger`‑klasse bevindt zich in de `Aspose.Words.LowCode`‑namespace en biedt een enkele `Execute`‑methode die de gegevensbron accepteert.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Waarom MailMerger gebruiken?**  
`MailMerger` abstraheert de boilerplate‑aanroepen van `MailMerge.Execute`, behandelt velddetectie, databinding en documentklonen intern. Dit maakt de code ideaal voor **automatiseren van documentgeneratie**‑scenario’s waarbij je een schone, low‑code oplossing wilt.

## Stap 4 – Voer de low‑code merge uit met de voorbereide gegevens

Het aanroepen van `Execute` retourneert een nieuw `Document` dat bevat


## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hernoem Word‑merge‑velden met Aspose.Words for Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Maak Word‑document met kop‑ en voettekst met Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Maak en style een Word‑document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
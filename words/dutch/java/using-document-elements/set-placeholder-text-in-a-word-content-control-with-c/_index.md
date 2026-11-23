---
category: general
date: 2026-11-22
description: Stel placeholder‑tekst in een Word‑inhoudsbesturingselement in met C#.
  Leer hoe je een aangepast label maakt, een platte‑tekst besturingselement invoegt
  en een placeholder aan het label toevoegt met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: nl
lastmod: 2026-11-22
og_description: Stel placeholder‑tekst in een Word‑inhoudsbesturingselement in met
  C#. Deze tutorial laat zien hoe je een aangepast label maakt, een platte‑tekst besturingselement
  invoegt en een placeholder aan het label toevoegt voor betere documentinteractiviteit.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Stel placeholder‑tekst in een Word‑inhoudsbesturingselement in – C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Stel placeholdertekst in een Word‑inhoudsbesturingselement in met C#
url: /nl/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Placeholder‑tekst instellen in een Word‑inhoudsbesturingselement met C#

Als je **placeholder‑tekst instellen** in een Word‑document programmeermatig wilt, laat deze gids je precies zien hoe je dat doet. Met Aspose.Words for .NET kun je een aangepast label maken, een platte‑tekst besturingselement invoegen, en een placeholder aan het label toevoegen zodat het document klaar is voor gebruikersinvoer.

In deze tutorial leer je hoe je **aangepast label maken**, **een inhoudsbesturingselement invoegen**, en **placeholder aan het label toevoegen** terwijl je de code beknopt en productie‑klaar houdt. Er zijn geen externe tools nodig—alleen een .NET‑project en de Aspose.Words‑bibliotheek.

## Vereisten

Before you start, make sure you have:

* .NET 6.0 SDK of later geïnstalleerd  
* Een geldige Aspose.Words for .NET‑licentie (of een gratis evaluatiesleutel)  
* Basiskennis van C# en Visual Studio (of een IDE naar keuze)  

De volgende secties gaan ervan uit dat je een console‑project hebt aangemaakt met de naam `WordPlaceholderDemo`.

## Stap 1: Installeer Aspose.Words

Voeg het NuGet‑pakket toe aan je project:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Gebruik de `--version`‑vlag om het pakket vast te zetten op de nieuwste stabiele release (bijv. `Aspose.Words.NET 24.9`).

## Stap 2: Laad het bron‑document en maak een `DocumentBuilder`

Het eerste wat je doet, is een bestaand `.docx`‑bestand laden (of een nieuw leeg document aanmaken) en een `DocumentBuilder` instantieren. De builder biedt een vloeiende API om besturingselementen en tekst in te voegen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Deze code **bereidt de basis** voor het invoegen van een inhoudsbesturingselement. De `DocumentBuilder` werkt direct op het `doc`‑object, zodat alle wijzigingen die je maakt automatisch worden weergegeven.

## Stap 3: Maak een aangepast label (StructuredDocumentTag)

Een *aangepast label* in Word wordt een **StructuredDocumentTag (SDT)** genoemd. Je kunt het zien als een inhoudsbesturingselement dat een unieke identifier draagt. Het maken ervan is de kern van de **aangepast label maken** stap.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

De `InsertStructuredDocumentTag`‑methode neemt twee argumenten:

1. Het type besturingselement (`PlainText` in dit geval).  
2. Een string die het label uniek identificeert (`"MyTag"`).  

Door een **aangepast label** te gebruiken, kun je later het besturingselement programmatic vinden of manipuleren.

## Stap 4: Stel een titel in voor toegankelijkheid

Een titel verbetert de toegankelijkheid en maakt het besturingselement makkelijker te vinden in de Word‑UI.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

De `Title`‑eigenschap is optioneel, maar het toevoegen ervan is een best practice wanneer je **placeholder aan het label toevoegen** voor een betere gebruikerservaring.

## Stap 5: Voeg placeholder‑tekst toe aan het label

Nu volgt het hoofddoel: **placeholder‑tekst instellen**. Deze tekst verschijnt wanneer het besturingselement leeg is en begeleidt de gebruiker bij wat er getypt moet worden.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

De `PlaceholderText`‑eigenschap is precies wat je nodig hebt om **placeholder aan het label toe te voegen**. Het gedraagt zich als de grijze hint die je ziet in moderne formuliervelden.

## Stap 6: Sla het gewijzigde document op

Na het configureren van het besturingselement, schrijf je het document terug naar de schijf.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Wanneer je `output.docx` opent in Microsoft Word, zie je een platte‑tekst inhoudsbesturingselement met het label “CustomerName” en de placeholder “Enter name…”. Klikken binnen het besturingselement verwijdert de placeholder, zodat de gebruiker kan typen.

### Verwachte output

* Een Word‑bestand (`output.docx`) met één platte‑tekst inhoudsbesturingselement.  
* Het besturingselement toont de placeholder “Enter name…” totdat de gebruiker iets typt.  
* De tag‑identifier van het besturingselement is `MyTag`, die je later kunt opvragen met `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Stap 7: Hoe je een inhoudsbesturingselement elders invoegt (geavanceerd)

Als je **een inhoudsbesturingselement wilt invoegen** op een specifieke locatie—bijvoorbeeld na een bepaalde alinea—gebruik dan de `MoveTo`‑methode voordat je het label invoegt:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Dit fragment toont **een platte‑tekst besturingselement invoegen** meerdere keren binnen hetzelfde document.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| Placeholder niet zichtbaar | Het besturingselement bevat al tekst (zelfs een spatie) | Zorg ervoor dat `sdt.Text` leeg is voordat je `PlaceholderText` instelt. |
| Tag‑identifier botsing | Het hergebruiken van dezelfde tag‑naam (`MyTag`) in hetzelfde document | Gebruik unieke identifiers voor elke `StructuredDocumentTag`. |
| Licentie‑exception | Uitvoeren zonder een geldige Aspose.Words‑licentie | Pas een licentiebestand toe (`license.SetLicense("Aspose.Words.lic")`) aan het begin van `Main`. |
| Document niet opgeslagen | Vergeten `doc.Save` aan te roepen of een alleen‑lezen pad te gebruiken | Controleer of het uitvoerpad beschrijfbaar is en roep `doc.Save` aan. |

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in `Program.cs`. Het bevat alle stappen—**aangepast label maken**, **een inhoudsbesturingselement invoegen**, **placeholder aan het label toevoegen**, en **een platte‑tekst besturingselement invoegen**—in één samenhangende stroom.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Voer het programma uit met `dotnet run`. Na uitvoering, open `output.docx` om te verifiëren dat beide besturingselementen hun respectieve placeholders tonen.

## Volgende stappen

* **Uiterlijk aanpassen** – Gebruik `sdt.Font` om lettergrootte, kleur of stijl binnen het besturingselement te wijzigen.  
* **Koppelen aan XML‑gegevens** – Verken `sdt.XmlMapping` als je het besturingselement wilt laten mappen

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
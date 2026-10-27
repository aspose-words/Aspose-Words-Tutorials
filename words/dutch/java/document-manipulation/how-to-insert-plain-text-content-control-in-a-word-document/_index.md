---
category: general
date: 2026-10-26
description: Leer hoe je een platte‑tekst contentcontrol invoegt met Aspose.Words
  in C#. Stapsgewijze handleiding over StructuredDocumentTag, titels en tag‑ID’s.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: nl
lastmod: 2026-10-26
og_description: Voeg een platte-tekstinhoudsbesturingselement in met Aspose.Words
  in C#. Volg deze gids om titels, tag‑ID’s toe te voegen en de weergave aan te passen.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Platte‑tekstinhoudsbesturing invoegen in Word met C# – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een platte‑tekstinhoudsbesturingselement in een Word‑document in te voegen
  met C#
url: /nl/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Platte‑tekst content control invoegen in een Word‑document met C#

Als je **platte‑tekst content control** in een Word‑bestand wilt invoegen, laat deze tutorial je precies zien hoe je dat doet met Aspose.Words voor .NET. Of je nu een document‑generatieservice bouwt of formulier‑creatie automatiseert, de onderstaande stappen laten je een herbruikbaar, bewerkbaar gebied toevoegen dat eindgebruikers kunnen invullen.

Je leert hoe je een `Document` maakt, `DocumentBuilder` gebruikt om een platte‑tekst Structured Document Tag (SDT) te plaatsen, een vriendelijke titel instelt en een unieke tag‑identifier toewijst. De gids legt ook veelvoorkomende variaties uit — zoals het wijzigen van het uiterlijk of het nesten van controls — zodat je de oplossing kunt aanpassen aan elk project.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
- Een geldige Aspose.Words voor .NET‑licentie (of een gratis evaluatiesleutel)
- Visual Studio 2022 of een andere C#‑compatibele IDE
- Basiskennis van C#‑syntaxis

> **Pro tip:** Als je de gratis evaluatie gebruikt, onthoud dan dat het uitvoer‑document een watermerk bevat. Een gelicentieerde versie verwijdert dit automatisch.

## Hoe een platte‑tekst content control invoegen met Aspose.Words

De kern van de oplossing is een proces in drie stappen:

1. **Maak een `Document` en een `DocumentBuilder`.**  
2. **Voeg een platte‑tekst Structured Document Tag (SDT) in met de standaardweergave.**  
3. **Ken een titel en een tag‑identifier toe aan de SDT.**  

Elke stap wordt hieronder uitgelegd, met volledige, uitvoerbare code.

### Stap 1: Initialiseert het document en de builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` methoden biedt zoals `InsertParagraph`, `InsertImage` en, cruciaal voor deze tutorial, `InsertStructuredDocumentTag`. Door ze eerst te initialiseren, krijg je een canvas waarop je de **platte‑tekst content control** kunt plaatsen.

### Stap 2: Voeg de platte‑tekst content control (SDT) in

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` vertelt Aspose.Words een **platte‑tekst content control** te maken, die zich gedraagt als een eenvoudig tekstvak dat gebruikers kunnen bewerken. `SdtAppearance.Default` geeft de control weer met een subtiele achtergrond, waardoor duidelijk wordt dat het gebied bewerkbaar is in het document.

> **Waarom `SdtAppearance.Default` gebruiken?**  
> De standaardweergave is de meest universeel compatibele stijl over verschillende Word‑versies heen. Als je een zonder rand wilt, kun je later overschakelen naar `SdtAppearance.Hidden`.

### Stap 3: Stel een titel en een tag‑identifier in

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Titel** (`sdt.Title`) verschijnt in het *Content Controls*‑paneel van Word, waardoor eindgebruikers de bedoeling van het veld begrijpen.  
- **Tag** (`sdt.Tag`) is een ontwikkelaar‑gerichte identifier die je later kunt opvragen via `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** biedt grijs getoonde begeleidende tekst, wat de gebruikerservaring verbetert.

Het volledige code‑fragment hierboven vormt een zelfstandig programma dat je kunt compileren en uitvoeren. Na uitvoering bevat `output.docx` één platte‑tekst content control met de titel *MyTag* en tag *TagId*.

![Diagram showing insert plain text content control in a Word document](image.png){alt="platte‑tekst content control invoegen"}

## Inzicht in StructuredDocumentTag (SDT) en de eigenschappen

Een **Structured Document Tag** (SDT) is het onderliggende objectmodel voor Word‑content controls. De meest relevante eigenschappen voor het invoegen van een platte‑tekst control zijn:

| Eigenschap | Doel | Typische waarden |
|------------|------|------------------|
| `SdtType` | Bepaalt het type control (plain text, rich text, picture, etc.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Visuele stijl van de control | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Menselijk leesbare naam weergegeven in het *Content Controls*‑paneel | Elke korte tekenreeks |
| `Tag` | Machine‑leesbare identifier gebruikt in code | Alfanumerieke tekenreeks |
| `PlaceholderName` | Tekst die wordt getoond wanneer de control leeg is | Aangepaste hint‑tekst |

Wanneer je `SdtType.PlainText` instelt, beperkt Word de inhoud tot platte tekens, waardoor opmaak wordt voorkomen. Dit maakt de control ideaal voor eenvoudige formulier‑velden zoals *Naam*, *E‑mail* of *Telefoonnummer*.

### Variaties die je mogelijk nodig hebt

| Scenario | Code‑wijziging |
|----------|----------------|
| **Geen visuele schaduw** (zonder rand) | Gebruik `SdtAppearance.Hidden` in plaats van `Default`. |
| **Alleen‑lezen veld** | Na invoegen `sdt.LockContentControl = true` instellen. |
| **Vooraf vullen met data** | `sdt.Text = "John Doe";` na het maken van de tag. |
| **Meerdere controls in een tabel** | Plaats de SDT in een tabelcel met `builder.InsertCell();` vóór de `InsertStructuredDocumentTag`‑aanroep. |

## Veelvoorkomende valkuilen en hoe ze te vermijden

1. **Vergeten een titel in te stellen** – Word maakt de control nog steeds, maar gebruikers zien geen betekenisvolle beschrijving in het *Content Controls*‑paneel. Altijd `sdt.Title` toewijzen.  
2. **Het verkeerde `SdtType` gebruiken** – Als je platte tekst nodig hebt maar per ongeluk `RichText` kiest, staat de control opmaak toe, wat downstream verwerking kan breken. Controleer de enum‑waarde.  
3. **Opslaan naar een alleen‑lezen map** – De `doc.Save`‑aanroep gooit een `UnauthorizedAccessException`. Zorg dat de doelmap schrijfbaar is of gebruik `Path.GetTempPath()` voor testen.  
4. **Licentie niet toegepast** – Zonder geldige licentie bevat het uitvoer‑document een evaluatiewatermerk. Pas de licentie vroeg in je programma toe:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma, klaar om te kopiëren‑plakken in een nieuw console‑project.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Verwacht resultaat:** Het openen van `output.docx` in Microsoft Word toont een regel tekst *“Please fill in the following field:”* gevolgd door een lichtgrijze, ingekaderde regio met de label *MyTag*. De placeholder *Enter your text here* verschijnt in lichtgrijs totdat de gebruiker typt.

## Conclusie

Je weet nu hoe je **platte‑tekst content control** in een Word‑document kunt invoegen met Aspose.Words voor .NET. De tutorial behandelde het initialiseren van een `Document`, het invoegen van een `StructuredDocumentTag` van het type `PlainText`, en het aanpassen van titel, tag en placeholder. Door de `SdtAppearance`‑opties en veelvoorkomende valkuilen te begrijpen, kun je vol vertrouwen formulieren, sjablonen en geautomatiseerde rapporten bouwen die afhankelijk zijn van bewerkbare content controls.

### Wat nu?

- Verken andere SDT‑types zoals `RichText` of `ComboBox` voor vervolgkeuzelijsten.  
- Combineer meerdere content controls binnen tabellen of herhaal ze met `RepeatingSection`.  
- Gebruik `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` om control‑waarden programmatisch te lezen of te wijzigen.

Experimenteer gerust met de eerder getoonde variaties en integreer het patroon in je grotere document‑generatie‑pijplijnen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to create content control in C# with Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
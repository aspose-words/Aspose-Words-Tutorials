---
category: general
date: 2026-09-05
description: Leer hoe je een groepsvorm‑docx maakt, een ActiveX‑commando‑knop invoegt
  en Markdown laadt in een Word‑document met een volledig C#‑voorbeeld.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: nl
lastmod: 2026-09-05
og_description: Maak een groepsvorm‑docx, voeg een ActiveX‑opdrachtknop toe en laad
  Markdown in een Word‑document met C#. Volg deze stap‑voor‑stap tutorial.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Groepsvorm docx maken en ActiveX‑besturingselementen insluiten – C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Hoe een groepsvorm in docx te maken en interactieve besturingselementen toe
  te voegen in C#
url: /nl/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een groepsvorm docx en voeg je interactieve besturingselementen toe in C#

Als je programmatically **group shape docx** bestanden moet maken, laat deze gids je precies zien hoe. Je ziet ook hoe je **ActiveX command button** besturingselementen kunt **invoegen** en **Markdown in een Word‑document kunt laden** zonder onderstrepingsopmaak te verliezen. Aan het einde van de tutorial heb je een volledig functioneel `.docx` dat vector‑graphics, interactieve UI‑elementen en markdown‑gebaseerde inhoud combineert.

Deze tutorial gaat ervan uit dat je een basis C#‑ontwikkelomgeving en de Aspose.Words for .NET‑bibliotheek geïnstalleerd hebt. Er zijn geen externe tools nodig—alles draait binnen een standaard .NET‑console‑ of desktop‑applicatie.

## Vereisten

- .NET 6.0 SDK of later (de code werkt ook met .NET Framework 4.7+)
- Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`)
- Een geldig X.509‑certificaat (`.pfx`) als je de ondertekeningsstap wilt testen
- Een afbeeldingsbestand (bijv. `logo.png`) en een markdown‑bestand (`sample.md`) geplaatst in een bekende map

> **Pro tip:** Houd alle invoerbestanden in één *resources* map om relatieve paden te vereenvoudigen.

## Stap 1: Zet het project op en importeer namespaces

Maak een nieuw console‑project aan en voeg de vereiste `using`‑directieven toe. Dit blok laat ook zien hoe je de Aspose.Words‑klassen waar je later gebruik van maakt, kunt refereren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

De `using`‑statements geven je directe toegang tot `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` en andere types die door de hele tutorial worden gebruikt.

## Stap 2: **Create group shape docx** – voeg een gegroepeerde vorm met kind‑elementen toe

Een *group shape* laat je meerdere tekenobjecten als één eenheid behandelen. Dit is handig om gerelateerde graphics samen te verplaatsen of van grootte te wijzigen.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Waarom een group shape?**  
Groeperen houdt het rechthoek en de ellips uitgelijnd wanneer de gebruiker ze in Word versleept. Het vereenvoudigt ook latere bewerkingen, zoals het toepassen van een gemeenschappelijke rand of het programmatically verplaatsen van de hele grafiek.

## Stap 3: Voeg een platte‑tekst content control toe (placeholder voor gebruikersinvoer)

Content controls geven eindgebruikers een gestructureerd gebied om tekst te typen. De placeholder‑tekst verdwijnt zodra de gebruiker begint te typen.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

De `PlaceholderName`‑eigenschap is wat Word toont als een lichtgrijze aanwijzing. Gebruikers kunnen deze vervangen door hun eigen tekst, en de onderliggende XML blijft goed gevormd.

## Stap 4: **Insert ActiveX command button** – voeg interactieve UI toe aan het document

ActiveX‑besturingselementen worden nog steeds ondersteund in moderne Word‑bestanden en kunnen macro's of externe automatisering activeren. Hieronder voegen we een *command button* toe en stellen we de bijschrift in.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Wanneer een ActiveX‑knop gebruiken?**  
Als je het document verspreidt binnen een bedrijfsomgeving die afhankelijk is van VBA‑macro's, kan een ActiveX‑knop een macro starten of een externe applicatie openen. Voor pure HTML‑gebaseerde interactiviteit, overweeg in plaats daarvan *content controls* met *Office.js* te gebruiken.

## Stap 5: Voeg een verborgen afbeelding toe (bijv. een logo) voor branding of later script‑toegang

Verborgen vormen worden niet weergegeven in het afgedrukte document, maar blijven in de XML, waardoor je ze later programmatically kunt ophalen.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Stap 6: **Load markdown into a Word document** terwijl onderstrepingsopmaak behouden blijft

Aspose.Words kan Markdown direct importeren. Het inschakelen van `ImportUnderlineFormatting` zorgt ervoor dat markdown‑onderstrepingen (`<u>` of `__text__`) Word‑onderstrepingsstijlen worden in plaats van platte tekst.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Randgeval:** Als het markdown‑bestand tabellen bevat, worden deze automatisch omgezet naar Word‑tabellen. Als je aangepaste tabelstijlen nodig hebt, pas dan een `DocumentBuilder` toe na het invoegen.

## Stap 7: Onderteken het document met XAdES‑EPES (optionele beveiligingsstap)

Digitale handtekeningen garanderen de integriteit van het document. De volgende code ondertekent het **create group shape docx**‑bestand met een XAdES‑EPES‑profiel.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Beveiligingsopmerking:** Houd het certificaatwachtwoord buiten versiebeheer. Gebruik omgevingsvariabelen of een veilige kluis in productie.

## Volledig uitvoerbaar voorbeeld

Door alle stappen samen te voegen krijg je een enkel, zelf‑containend programma. Sla het bestand op als `Program.cs` en voer het uit vanaf de opdrachtregel.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Het uitvoeren van het programma genereert `CompleteGroupShape.docx` met:

- Een gegroepeerde rechthoek + ellips (de **create group shape docx**‑kern)
- Een platte‑tekst content control met placeholder‑tekst
- Een **insert ActiveX command button** gelabeld “Click Me”
- Een verborgen logo‑afbeelding
- Markdown‑inhoud met behouden onderstrepingen
- Een XAdES‑EPES‑digitale handtekening (indien certificaat geleverd)

## Veelgestelde vragen en probleemoplossing

| Vraag | Antwoord |
|---|---|
| **Werkt de ActiveX‑knop op macOS Word?** | macOS Word ondersteunt geen ActiveX‑besturingselementen. De knop verschijnt als een statische afbeelding. Gebruik content controls met Office.js voor cross‑platform interactiviteit. |
| **Wat als het markdown‑bestand aangepaste CSS bevat?** | Aspose.Words negeert CSS; alleen standaard markdown‑syntaxis wordt verwerkt. Converteer CSS‑gestylede elementen handmatig naar Word‑stijlen na import. |
| **Kan ik later meer vormen aan dezelfde groep toevoegen?** | Ja. Haal de `GroupShape` op via de naam of index, en roep vervolgens `AppendChild(newShape)` aan. Vergeet niet het document opnieuw op te slaan na wijzigingen. |
| **Hoe wijzig ik het ondertekeningsalgoritme?** | Stel `signature.SignatureAlgorithm` in vóór het aanroepen van `Sign`. Standaard is SHA‑256, wat aan de meeste compliance‑eisen voldoet. |
| **Is de verborgen afbeelding zichtbaar in de Word‑UI?** | Nee, maar hij kan worden weergegeven door *Show hidden text* in de Word‑opties in te schakelen. Dit is handig om metadata op te slaan zonder de lay-out te vervuilen. |

## Volgende stappen

Nu je **group shape docx** kunt **maken**, **ActiveX command button** kunt **invoegen**, en **markdown in een Word‑document** kunt **laden**, kun je het volgende verkennen:

- **VBA‑macro's insluiten** die reageren op de klik van de ActiveX‑knop.
- **Aangepaste stijlen toepassen** op de door markdown gegenereerde alinea's.
- **PDF's genereren** uit hetzelfde document met `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Batchverwerking automatiseren** van meerdere markdown‑bestanden naar één samengesteld rapport.

Deze uitbreidingen stellen je in staat volledig geautomatiseerde document‑pijplijnen te bouwen die rijke graphics, interactieve besturingselementen en markdown‑gebaseerde auteurschap combineren—allemaal vanuit C#.

---

*Veel plezier met coderen! Als je deze tutorial

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies te beheersen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Groepsvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechthoekvorm maken in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Markdown maken vanuit Word – Complete C#‑gids](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
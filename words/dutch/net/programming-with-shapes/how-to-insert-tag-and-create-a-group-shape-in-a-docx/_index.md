---
category: general
date: 2026-09-14
description: Leer hoe je een tag invoegt, vormen toevoegt, een groep maakt en het
  document opslaat als DOCX met Aspose.Words in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: nl
lastmod: 2026-09-14
og_description: Hoe een tag in te voegen, vormen toe te voegen, een groep te maken
  en het document op te slaan als DOCX met Aspose.Words. Volg de stapsgewijze handleiding.
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: Hoe een tag in te voegen en een gegroepeerde vorm te maken in een DOCX met
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to insert tag, add shapes, create a group, and save document
    as DOCX using Aspose.Words in C#.
  headline: How to insert tag and create a group shape in a DOCX
  type: TechArticle
tags:
- Aspose.Words
- C#
- DOCX manipulation
title: Hoe een tag in te voegen en een groepsvorm te maken in een DOCX
url: /nl/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een tag in te voegen en een groepsvorm te maken in een DOCX

Als je moet weten **hoe een tag in te voegen** tijdens het bouwen van een complexe lay-out, laat deze gids je een volledige, uitvoerbare oplossing zien. Je ziet hoe je vormen toevoegt, een groep maakt, en uiteindelijk **document opslaat als DOCX** met Aspose.Words for .NET.

Documentgeneratie vereist vaak het combineren van teksttags met grafische elementen. In deze tutorial leer je precies **hoe een tag in te voegen**, hoe **vormen toe te voegen**, hoe **een groep te maken**, en de juiste manier om **docx op te slaan** zodat het bestand in Word kan worden geopend zonder verlies van kwaliteit.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)
- Basiskennis van C#‑syntaxis
- Een IDE zoals Visual Studio of VS Code

Geen extra bibliotheken zijn vereist; het volledige voorbeeld draait met één NuGet‑referentie.

## Hoe een groep te maken en vormen toe te voegen

De eerste logische stap is om een **groep** te maken die meerdere vormen bevat. Groeperen houdt de vormen bij elkaar wanneer je ze later verplaatst of roteert.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

// 1️⃣ Create an empty document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// 2️⃣ Build a GroupShape (200 × 200 points) and set its bounds
GroupShape groupShape = new GroupShape(document, 200, 200);
groupShape.Bounds = new RectangleF(50, 50, 200, 200);

// 3️⃣ Add a rectangle shape
groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
{
    Width = 80,
    Height = 80,
    Left = 0,
    Top = 0
});

// 4️⃣ Add an ellipse shape next to the rectangle
groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
{
    Width = 80,
    Height = 80,
    Left = 100,
    Top = 0
});
```

**Waarom dit belangrijk is:**  
`GroupShape` fungeert als een container. Wanneer je later de groep verplaatst, reizen zowel het rechthoek als de ellips samen, waardoor hun relatieve posities behouden blijven. Dit is de aanbevolen manier om meerdere grafische elementen te beheren die tot hetzelfde logische blok behoren.

## Hoe een tag in het document in te voegen

Nu de groep klaar is, kun je **een tag invoegen** (een StructuredDocumentTag, ook wel een SDT genoemd) direct na de groep. De tag kan platte tekst, rich‑text of zelfs herhalende inhoud bevatten.

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**Waarom je een StructuredDocumentTag zou moeten gebruiken:**  
Een SDT biedt een semantische marker die Word kan herkennen voor inhoudsbesturingselementen, databinding of formulier‑invulscenario's. Door `InsertStructuredDocumentTag` te gebruiken, geef je expliciet **hoe een tag in te voegen** op een manier die overleeft bij latere bewerkingen in Microsoft Word.

## Hoe docx op te slaan en het resultaat te verifiëren

De laatste stap is het document op te slaan. De onderstaande code toont de juiste manier om **document op te slaan als docx** en waar je het uitvoerbestand kunt vinden.

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Wanneer je *GroupAndSDT.docx* opent in Word, zou je een gegroepeerde rechthoek‑ellips grafiek moeten zien, gevolgd door een platte‑tekst inhoudsbesturingselement met de titel **MyTag** dat de regel “Content inside the SDT” bevat.

### Verwachte output

- Een groep van 200 × 200 punten gepositioneerd op (50, 50) op de pagina.
- Binnen de groep: een blauwe rechthoek aan de linkerkant en een ellips aan de rechterkant (standaardkleuren).
- Direct onder de groep: een inhoudsbesturingselement gelabeld **MyTag** met de tekst “Content inside the SDT”.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren en plakken in een console‑applicatie. Het bevat alle benodigde `using`‑directieven, foutafhandeling en commentaren die elke stap uitleggen.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeWordsGroupAndTag
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document and a DocumentBuilder to work with it
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Build a GroupShape (200x200) and define its bounds
            GroupShape groupShape = new GroupShape(document, 200, 200);
            groupShape.Bounds = new RectangleF(50, 50, 200, 200);

            // Add a rectangle to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
            {
                Width = 80,
                Height = 80,
                Left = 0,
                Top = 0
            });

            // Add an ellipse to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
            {
                Width = 80,
                Height = 80,
                Left = 100,
                Top = 0
            });

            // Insert the group into the document at the current builder position
            builder.InsertNode(groupShape);

            // Insert a plain‑text StructuredDocumentTag (SDT) and write some content inside it
            builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
            builder.Writeln("Content inside the SDT");

            // Save the resulting document
            string outputPath = Path.Combine(
                Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
                "GroupAndSDT.docx");

            document.Save(outputPath);
            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

Voer het programma uit, navigeer naar je bureaublad, en dubbelklik op *GroupAndSDT.docx* om te verifiëren dat de groep en de tag verschijnen zoals beschreven.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Kan ik meer dan twee vormen aan de groep toevoegen?** | Ja. Roep `groupShape.AppendChild(new Shape(...))` aan voor elke extra vorm voordat je de groep invoegt. |
| **Wat als ik een rich‑text tag nodig heb in plaats van platte tekst?** | Gebruik `StructuredDocumentTagType.RichText` in `InsertStructuredDocumentTag`. |
| **Hoe verander ik de kleur van de rechthoek of ellips?** | Stel de `FillColor`‑eigenschap in op elk `Shape`‑object, bijvoorbeeld `shape.FillColor = Color.LightBlue;`. |
| **Is het mogelijk om de hele groep te roteren?** | Stel `groupShape.Rotation = 45;` (graden) in vóór het invoegen van de node. |
| **Moet ik `Dispose()` aanroepen op enige objecten?** | Aspose.Words beheert de meeste bronnen intern; het disposen van de `Document` is optioneel in een kortlevende console‑app. |

## Best practices voor het opslaan van DOCX‑bestanden

- **Gebruik altijd een absoluut pad** (of een goed gedefinieerd relatief pad) bij het aanroepen van `document.Save`. Dit voorkomt de “file not found”‑fout die kan optreden bij onduidelijke werkmappen.
- **Geef de voorkeur aan `Save`‑overloads die een stream accepteren** als je het document via HTTP moet verzenden of in een database wilt opslaan.
- **Stel de `CompatibilityOptions` in** als je oudere versies van Word moet targeten (bijv. Word 2003). Voor de meeste moderne scenario's werken de standaardinstellingen prima.

## Volgende stappen

Nu je weet **hoe een tag in te voegen**, hoe **vormen toe te voegen**, hoe **een groep te maken**, en hoe **docx op te slaan**, kun je meer geavanceerde scenario's verkennen:

- Combineer meerdere groepen om complexe diagrammen te bouwen.
- Gebruik `StructuredDocumentTag` voor databinding in Word‑templates.
- Exporteer hetzelfde document naar PDF (`document.Save("output.pdf")`) terwijl je de gegroepeerde grafieken behoudt.
- Automatiseer formulier‑invulling door programmatisch de inhoud van de SDT in te stellen (`builder.MoveToDocumentEnd(); builder.Write("New value");`).

Experimenteer met verschillende `ShapeType`‑waarden (bijv. `ShapeType.Polygon`, `ShapeType.Line`) om te zien hoe ze zich gedragen binnen een `GroupShape`. Hetzelfde patroon werkt voor tabellen, afbeeldingen of elke andere node die je samen wilt houden.

---

**Samenvatting:** Deze tutorial toonde **hoe een tag in te voegen** binnen een gegroepeerde vorm, hoe **vormen toe te voegen**, hoe **een groep te maken**, en de juiste methode om **document op te slaan als docx** met Aspose.Words for .NET. Je hebt nu een solide basis voor het programmatisch bouwen van rijke, interactieve DOCX‑bestanden.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe Markdown op te slaan vanuit DOCX – Stapsgewijze gids](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Hoe DOCX te herstellen – Complete gids met Aspose.Words](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [Hoe grammatica te controleren in DOCX met Aspose.Words – gebruik gpt-4 turbo](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
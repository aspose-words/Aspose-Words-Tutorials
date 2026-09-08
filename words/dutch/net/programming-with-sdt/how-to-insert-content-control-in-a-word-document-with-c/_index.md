---
category: general
date: 2026-09-08
description: Leer hoe je een contentcontrol in een Word‑document invoegt met C# en
  Aspose.Words. Inclusief stappen om een contentcontrol te maken, een tijdelijke aanduiding
  in te stellen en het bestand op te slaan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: nl
lastmod: 2026-09-08
og_description: Voeg een contentcontrol toe in een Word‑bestand met C# en Aspose.Words.
  Volg deze gids om een contentcontrol te maken, placeholder‑tekst in te stellen en
  het document op te slaan.
og_image_alt: Insert content control example in a Word document
og_title: Inhoudsbesturingselement invoegen in Word met C# – stap‑voor‑stap gids
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Hoe een contentcontrol in een Word‑document in te voegen met C#
url: /nl/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe content control in een Word‑document in te voegen met C#

Als je een **content control** in een Word‑document moet **invoegen**, laat deze gids je een volledige, uitvoerbare oplossing zien. Je leert ook hoe je programmatically een **content control** maakt, placeholder‑tekst instelt en het bestand naar schijf schrijft.

Content controls laten je gebieden definiëren die gebruikers kunnen invullen, herhalen of vergrendelen. Ze worden veel gebruikt voor sjablonen, formulieren en dynamische rapporten. De onderstaande stappen gebruiken de Aspose.Words for .NET‑bibliotheek, die werkt met .NET 6+, .NET Framework 4.6+ en .NET Core.

## Hoe content control in een Word‑document in te voegen

1. **Aspose.Words aan je project toevoegen**  
   Open een terminal in de projectmap en voer uit:

   ```bash
   dotnet add package Aspose.Words
   ```

   Het pakket bevat de klassen `Document`, `DocumentBuilder` en `StructuredDocumentTag` die nodig zijn voor content controls.

2. **Een nieuw leeg document maken**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   Het `Document`‑object vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` een handige cursor biedt voor het invoegen van knooppunten.

## Een content control maken met Aspose.Words

Content controls worden weergegeven door de `StructuredDocumentTag` (SDT)‑klasse. De volgende code maakt een **plain‑text** content control en geeft het een titel die later kan worden opgevraagd.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Waarom dit belangrijk is:*  
- `SdtType.PlainText` zorgt ervoor dat de control alleen platte tekens accepteert.  
- `MarkupLevel.Block` laat de control zich gedragen als een volledige alinea, wat ideaal is voor formuliervelden.  
- De eigenschap `Title` is een stabiele identifier die je kunt gebruiken bij zoeken of het binden van gegevens.

## Placeholder‑ en standaardtekst instellen

Een placeholder begeleidt de gebruiker voordat hij iets typt. Je kunt de control ook vooraf vullen met standaardinhoud.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

Het XML‑fragment moet overeenkomen met het gegevenstype van de control. Voor plain‑text controls is het `<text>`‑element vereist. Als je deze stap weglaten, wordt de eerder gedefinieerde placeholder getoond.

## De content control op de gewenste locatie invoegen

De cursor van `DocumentBuilder` bepaalt waar de control verschijnt. Standaard staat de cursor aan het begin van het document.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Als je de control in een tabel, koptekst of na bestaande alinea's nodig hebt, verplaats je de builder eerst:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Het document opslaan met de ingevoegde content control

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

Het bestand `SDT.docx` bevat nu een plain‑text content control met de titel **CustomerName**, de placeholder “Enter name here” en de standaardtekst “John Doe”.

![Insert content control example in a Word document](insert-content-control.png)

*Image alt text:* Voorbeeld van invoegen van content control in een Word‑document

### Verwacht resultaat

Wanneer je `SDT.docx` opent in Microsoft Word:

- Een grijze placeholder “Enter name here” verschijnt als je de standaardtekst verwijdert.  
- De control wordt gemarkeerd wanneer je erin klikt, wat aangeeft dat hij bewerkbaar is.  
- Het tabblad **Developer** (indien ingeschakeld) toont de titel van de control **CustomerName** in het eigenschappen‑paneel.

## Volledig werkend voorbeeld

Hieronder staat een enkel, zelfstandig programma dat je kunt kopiëren, compileren en uitvoeren. Het demonstreert elke stap van projectconfiguratie tot het opslaan van het bestand.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Voer het programma uit met `dotnet run`. Na uitvoering open je het gegenereerde bestand om te verifiëren dat de content control verschijnt zoals beschreven.

## Praktische tips en veelvoorkomende valkuilen

| Situatie | Aanbevolen aanpak |
|-----------|----------------------|
| **Meerdere controls van hetzelfde type** | Geef elke control een unieke `Title`. Je kunt later een control ophalen met `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Control niet zichtbaar in Word** | Zorg ervoor dat je het document hebt opgeslagen met de extensie `.docx` en dat de `Aspose.Words`‑versie compatibel is met jouw Office‑versie. |
| **Een rich‑text control nodig** | Gebruik `SdtType.RichText` in plaats van `PlainText`. Het XML‑fragment gebruikt dan `<w:richText>`‑elementen. |
| **De control in een tabelcel plaatsen** | Verplaats de builder eerst naar de cel: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Prestaties bij grote documenten** | Maak de `StructuredDocumentTag` één keer aan en hergebruik deze als je veel identieke controls nodig hebt; kloon hem via `sdt.Clone(true)`. |

## Volgende stappen

- **Herhalende content controls maken** (`SdtType.RepeatingSection`) voor tabellen die dynamisch groeien.  
- **Content controls binden aan XML‑gegevens** met `sdt.XmlMapping.LoadXml(xmlString)`.  
- **De control vergrendelen** (`sdt.LockContentControl = true`) om gebruikersbewerkingen te voorkomen terwijl programmatic updates nog wel mogelijk zijn.  

Het verkennen van deze onderwerpen verdiept je vermogen om robuuste Word‑sjablonen te bouwen met Aspose.Words.

---

**Conclusie**  
Je weet nu hoe je een **content control** in een Word‑document kunt **invoegen** met C#. De tutorial behandelde het maken van de control, het instellen van placeholder‑ en standaardtekst, het invoegen op de gewenste locatie en het opslaan van het uiteindelijke bestand. Met deze basis kun je geavanceerde formulieren, mail‑merge‑sjablonen en geautomatiseerde rapporten bouwen die gebruikmaken van de native content‑control‑functies van Word.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Set Content Control Style](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Set Content Control Color](/words/english/net/programming-with-sdt/set-content-control-color/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
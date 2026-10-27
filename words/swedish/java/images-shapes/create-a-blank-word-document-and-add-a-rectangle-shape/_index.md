---
category: general
date: 2026-10-23
description: Skapa ett tomt Word‑dokument, lägg till en rektangelform och dölj formen
  i Word med Aspose.Words. Steg‑för‑steg‑kod för .NET‑utvecklare.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: sv
lastmod: 2026-10-23
og_description: Skapa ett tomt Word‑dokument, lägg till en rektangel och dölj formen
  i Word med Aspose.Words. Följ det kompletta C#‑exemplet.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Skapa ett tomt Word‑dokument och lägg till en dold rektangelform
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Skapa ett tomt Word‑dokument och lägg till en rektangel.
url: /sv/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument och lägg till en rektangelform

Om du behöver **skapa ett tomt Word-dokument**, visar den här guiden hur du gör det med Aspose.Words för .NET. Du får också lära dig **hur du infogar en form**—specifikt en rektangel—och **döljer form i Word** så att den inte påverkar layouten.

Tutorialen går igenom varje kodrad, förklarar varför varje steg är viktigt och täcker vanliga fallgropar såsom synlighet för dolda former i olika Word‑vyer. I slutet har du en fullt fungerande `.docx`‑fil som innehåller en dold rektangelform som du senare kan avslöja eller manipulera programmässigt.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.6+)
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`)
- En utvecklingsmiljö såsom Visual Studio 2022 eller VS Code med C#‑tillägg
- Grundläggande kunskap om C#‑syntax och Word‑dokumentkoncept

Ingen extra Office‑installation krävs eftersom Aspose.Words körs helt i minnet.

## Skapa ett tomt Word-dokument

Det första steget är att instansiera ett tomt `Document`‑objekt. Detta objekt representerar en Word‑fil som ännu inte innehåller några sektioner, stycken eller annat innehåll.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Varför detta är viktigt:**  
Ett tomt `Document` ger dig en ren arbetsyta. Om du börjar från en befintlig mall kan dolda former ärva oönskade stilar. Att börja från grunden säkerställer att rektangelformen du lägger till senare är det enda innehållet du kontrollerar.

## Lägg till en rektangelform i dokumentet

Nästa steg är att använda en `DocumentBuilder` för att placera innehåll i dokumentet. Builderns `InsertShape`‑metod är det vanliga sättet **att infoga en form**, såsom rektanglar, cirklar eller anpassade teckningar.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Varför detta är viktigt:**  
`InsertShape` returnerar ett `Shape`‑objekt som du kan konfigurera vidare (färg, linjestil osv.). Dimensionerna anges i punkter (1 punkt = 1/72 tum), vilket matchar Words interna mätsystem.

### Valfritt: formatera rektangeln (optional)

Om du vill att rektangeln ska ha en synlig kant när du senare visar den igen, kan du sätta dess linjebredd och färg:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Dessa rader är valfria eftersom formen kommer att döljas i nästa steg.

## Dölj formen i Word

Word tillåter att former döljs från layouten samtidigt som de fortfarande är en del av dokumentets objektmodell. Genom att sätta egenskapen `Hidden` till `true` blir formen osynlig i normal vy men fortfarande valbar via API‑et.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Varför detta är viktigt:**  
En dold form är användbar för att lagra metadata, platshållare för senare bearbetning eller villkorligt innehåll som du bara visar under vissa omständigheter (t.ex. när en slutrapport genereras). Formen finns kvar i filen, så du kan programmässigt avdöja den senare med `rectangleShape.Hidden = false;`.

## Spara dokumentet

Till sist skriver du dokumentet till disk. Filändelsen bestämmer Word‑formatet; `.docx` är det moderna Open XML‑formatet.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Resultat:**  
När du öppnar `HiddenShape.docx` i Microsoft Word visas en i övrigt tom sida. Rektangeln är inte synlig, men om du går till **Home → Select → Selection Pane** ser du formen listad och kan växla dess synlighet.

## Fullständigt fungerande exempel

Nedan är hela programmet som du kan kopiera, klistra in och köra. Det innehåller alla nödvändiga `using`‑satser och kommentarer.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Förväntat resultat:**  

- Konsolen skriver ut sparvägen.  
- `HiddenShape.docx` öppnas som en tom sida i Word.  
- Rektangelformen finns men är dold; du kan verifiera den via *Selection Pane* eller genom att programatiskt sätta `Hidden = false` och öppna filen igen.

## Vanliga frågor och specialfall

| Fråga | Svar |
|----------|--------|
| **Kan jag dölja andra formtyper?** | Ja. Alla `Shape` (t.ex. `ShapeType.Ellipse`, `ShapeType.Picture`) stöder egenskapen `Hidden`. |
| **Kommer den dolda formen att öka filstorleken?** | Ökningen är försumbar (några kilobytes) eftersom formdata lagras som XML i `.docx`‑paketet. |
| **Vad händer om jag bara vill att formen ska visas i utskriftsvyn?** | Använd egenskapen `Shape.IsPrint` istället för `Hidden`. Att sätta `IsPrint = false` döljer formen i utskriften men den förblir synlig på skärmen. |
| **Hur avdöjer jag formen senare?** | Läs in dokumentet, lokalisera formen (t.ex. via `Shape.Name`), sätt sedan `shape.Hidden = false;` och spara. |
| **Fungerar detta med .doc (binärt) format?** | Ja, Aspose.Words kan spara till `.doc` med `document.Save("file.doc");`. Den dolda flaggan bevaras. |

## Proffstips

- **Ge dina former namn**: `rectangleShape.Name = "PlaceholderRectangle";` gör det enklare att hitta senare via `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Batch‑bearbetning**: Om du behöver lägga till dolda former i många dokument, omslut koden i en metod och återanvänd `DocumentBuilder`‑instansen.
- **Prestanda**: Att skapa en form är billigt, men att spara stora dokument ofta kan vara I/O‑begränsat. Överväg att använda `MemoryStream` för mellansteg.

## Slutsats

Du vet nu hur du **skapar ett tomt Word-dokument**, **lägger till en rektangelform** och **döljer form i Word** med Aspose.Words för .NET. Denna teknik låter dig bädda in osynliga platshållare som du senare kan avslöja eller manipulera, ett mönster som är användbart för dynamisk rapportgenerering, villkorligt innehåll och dokumentmallning.

Nästa steg du kan utforska:

- Byt ut rektangeln mot en bild eller ett diagram med `ShapeType.Picture`.
- Använd **how to insert shape** i sidhuvud-/sidfot‑sektioner för vattenstämpel‑liknande platshållare.
- Kombinera dolda former med **add rectangle shape**‑baserad datavalidering (t.ex. lagra JSON i en forms `AlternativeText`‑egenskap).

Lycka till med kodningen, och känn dig fri att experimentera med andra formtyper och synlighetsalternativ för att passa dina behov av dokumentautomatisering!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument – Hur man lägger till rektangelform och skugga](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa ett tomt Word-dokument med en dold ellipsform – Fullständig C#‑guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
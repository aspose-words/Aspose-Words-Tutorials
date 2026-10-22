---
category: general
date: 2026-08-10
description: Infoga rektangelform i Word med C#. Lär dig hur du döljer formen, döljer
  formen i Word och skapar en dold form med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: sv
lastmod: 2026-08-10
og_description: Infoga en rektangelform i Word med C#. Den här handledningen förklarar
  hur man döljer en form, döljer en form i Word och skapar en dold form med fullständiga
  kodexempel.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Infoga rektangelform i Word med C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Infoga rektangel i Word med C# – komplett guide
url: /sv/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga rektangelform i Word med C# – komplett guide

Om du behöver **insert rectangle shape** i ett Word‑dokument med C#, visar den här guiden de exakta stegen. Du kommer också att lära dig **how to hide shape** så att den inte visas i den slutliga filen, vilket svarar på den vanliga frågan **hide shape in Word** och demonstrerar hur man **create hidden shape** programatiskt.

Handledningen täcker allt från att konfigurera Aspose.Words SDK till att verifiera att formen är dold. I slutet av artikeln har du ett återanvändbart kodexempel som du kan klistra in i vilket .NET‑projekt som helst.

## Förutsättningar

- .NET 6.0 eller senare installerat (koden fungerar också med .NET Framework 4.6+)
- En giltig Aspose.Words för .NET-licens eller en tillfällig utvärderingsnyckel
- Visual Studio 2022 (eller någon IDE som stödjer C#)
- Grundläggande kunskap om C#‑syntax och Document Object Model (DOM) för Word‑filer

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Steg 1: Skapa ett nytt tomt dokument och en DocumentBuilder

Den första operationen är att instansiera ett `Document`‑objekt. `DocumentBuilder` tillhandahåller ett bekvämt API för att infoga innehåll såsom former, stycken och tabeller.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Varför detta är viktigt:** `Document` representerar hela .docx‑filen, medan `DocumentBuilder` håller ett markör som spårar var nästa element kommer att placeras. Att initiera båda objekten är grunden för alla Word‑automatiseringsuppgifter.

## Steg 2: Infoga rektangelform

Nu infogar du rektangeln. Metoden `InsertShape` kräver formtypen och dess dimensioner i punkter (1 punkt ≈ 1/72 tum). En storlek på **200 × 100 points** ger en rektangel på ungefär 2,78 × 1,39 tum.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Varför detta är viktigt:** `Shape`‑objektet du får är fullt konfigurerbart—färg, kant, text och synlighet kan alla ändras innan dokumentet sparas.

## Steg 3: Dölj formen

För att förhindra att rektangeln visas eller skrivs ut, sätt dess `Hidden`‑egenskap till `true`. Denna egenskap motsvarar direkt Word‑attributet “Hidden”, som Word respekterar både i visnings‑ och utskriftsläge.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Varför detta är viktigt:** Att sätta `Hidden` är det standardmässiga sättet att **hide shape in Word** utan att ta bort den från dokumentstrukturen. Formen förblir tillgänglig för kod, vilket möjliggör senare manipulationer såsom villkorsstyrd formatering eller datadrivna synlighetsväxlingar.

## Steg 4: Spara dokumentet

Till sist sparas dokumentet till disk. Välj någon mapp du vill; exemplet använder en platshållar‑sökväg som du bör ersätta med en riktig.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Varför detta är viktigt:** Sparandet slutför filen och skriver den dolda flaggan i den underliggande Open XML. När du öppnar dokumentet i Microsoft Word kommer rektangeln att vara osynlig, vilket bekräftar att du framgångsrikt **created hidden shape**.

## Steg 5: Verifiera den dolda formen

Öppna den genererade `HiddenShape.docx` i Microsoft Word:

1. Gå till **File → Options → Display** och se till att *“Show hidden text”* är **avmarkerat**.  
2. Rektangeln bör inte vara synlig på någon sida.  
3. För att dubbelkolla, aktivera *“Show hidden text”*; rektangeln visas med en svag prickad kontur, vilket bevisar att formen finns men är dold.

Om rektangeln fortfarande är synlig, kontrollera att du sparade filen efter att ha satt `Hidden = true` och att du öppnar rätt fil.

## Fullt körbart exempel

Nedan är det kompletta programmet som du kan kopiera, klistra in och köra direkt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Förväntad utskrift:** Konsolen skriver ut filsökvägen och en kort påminnelse. När filen öppnas i Word är rektangeln osynlig såvida inte dold text är aktiverad.

## Vanliga frågor och edge‑cases

### Kan jag dölja endast konturen men behålla fyllningen synlig?

Ja. Istället för att sätta `Hidden = true` kan du sätta `rectangle.LineFormat.Visible = false` för att dölja kanten medan fyllningsfärgen behålls. Detta är en variation av **how to hide shape** som bevarar en del av den visuella framtoningen.

### Fungerar den dolda flaggan i äldre Word‑versioner (2003, 2007)?

Det dolda attributet är en del av Open XML‑specifikationen som introducerades med Word 2007. Dokument som sparas i det äldre binära `.doc`‑formatet bevarar inte flaggan. För att stödja äldre format, spara dokumentet som `.docx` och, om så behövs, konvertera det senare med Aspose.Words `SaveFormat.Doc`.

### Vad händer om jag behöver dölja flera former samtidigt?

Iterera över samlingen `Document.GetChildNodes(NodeType.Shape, true)` och sätt `Hidden = true` på varje form som uppfyller dina kriterier (t.ex. en specifik `ShapeType` eller ett anpassat `AlternativeText`‑värde).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Finns det någon prestandapåverkan när man döljer former?

Den dolda flaggan lägger till ett litet XML‑attribut; den påverkar inte renderingshastigheten. Däremot kan ett mycket stort antal dolda objekt öka filstorleken marginellt. Ta bort former du aldrig behöver för att hålla dokumentet slimmat.

## Tips och bästa praxis

- **Ge formen ett meningsfullt namn** med `rectangle.Name = "MyHiddenRectangle"`; detta hjälper när du senare söker efter formen i DOM‑en.
- **Sätt `AlternativeText`** till en anpassad tagg (t.ex. `"HiddenShape"`). Detta låter dig hitta formen utan att förlita dig på dess index.
- **Omge koden med ett try‑catch‑block** för att hantera licensfel eller I/O‑undantag på ett smidigt sätt.
- **Disposera Document** efter sparning om du bearbetar många filer i en loop för att frigöra ohanterade resurser: `document.Dispose();`.

## Slutsats

Du vet nu hur man **insert rectangle shape** i ett Word‑dokument med C#, hur man **hide shape in Word**, och hur man **create hidden shape** som förblir en del av dokumentstrukturen men är osynlig för slutanvändare. Det kompletta, körbara exemplet demonstrerar hela arbetsflödet, från dokumentskapande till verifiering.

Nästa steg kan vara att utforska **how to hide shape** baserat på användarinmatning, eller kombinera dolda former med innehållskontroller för dynamisk dokumentgenerering. Du kan också tillämpa samma teknik på andra formtyper såsom ellipser, pilar eller anpassade ritningar.

Känn dig fri att experimentera med olika dimensioner, färger och synlighetsinställningar. Om du stöter på problem, gå tillbaka till stegen ovan eller konsultera Aspose.Words‑dokumentationen för djupare API‑detaljer. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Skapa rektangelform i Word med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow‑handledning – Lägg till en skugga på Word‑form i C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
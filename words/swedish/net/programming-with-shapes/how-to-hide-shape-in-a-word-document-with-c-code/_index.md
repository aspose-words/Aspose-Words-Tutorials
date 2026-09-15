---
category: general
date: 2026-09-14
description: Lär dig hur du döljer en form i Word med C# — inklusive kod för att skapa
  ett Word‑dokument, infoga en rektangel‑form i Word och dölja formen i Word programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: sv
lastmod: 2026-09-14
og_description: Hur man döljer en form i Word med C# — steg‑för‑steg‑guide som också
  visar hur man skapar kod för Word‑dokument och infogar en rektangulär form i Word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Hur man döljer en form i ett Word-dokument med C#-kod
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man döljer en form i ett Word‑dokument med C#‑kod
url: /sv/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man döljer en form i ett Word‑dokument med C#‑kod

Om du behöver **hur man döljer en form** i en Word‑fil, visar den här handledningen den kompletta lösningen. Du får se hur du skapar ett Word‑dokument, infogar en rektangel, lägger till en ellips och döljer ellipsen så att bara rektangeln visas när filen öppnas.

Guiden täcker allt du behöver – inga externa referenser, bara koden och förklaringarna. När du är klar kan du bädda in dolda grafikobjekt i vilket Word‑dokument du än genererar programmässigt.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
- Aspose.Words for .NET (gratis provversion eller licensierad version)  
  Installera via NuGet: `dotnet add package Aspose.Words`
- Grundläggande kunskap om C# och Visual Studio eller någon IDE du föredrar

## Steg 1: Ställ in projektet och importera namnrymder

Starta ett nytt konsolprogram och lägg till de nödvändiga `using`‑satserna. Dessa importeringar ger dig åtkomst till `Document`, `DocumentBuilder` och ritklasserna som behövs för att manipulera former.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Varför detta är viktigt** – Att importera rätt namnrymder förhindrar kompileringsfel och gör API‑ytan tillgänglig för skapande av former och kontroll av synlighet.

## Steg 2: Skapa ett nytt Word‑dokument och en builder

Ett `Document` representerar filen, medan en `DocumentBuilder` erbjuder ett flytande API för att lägga till innehåll. Detta är det första stället där du tillämpar **hur man döljer en form**‑logiken: du behöver ett dokumentkontext innan någon form kan existera.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Förklaring** – `Document`‑objektet startar tomt. `DocumentBuilder` är placerad i början av det första stycket, redo att infoga former eller text.

## Steg 3: Infoga en synlig rektangel‑form

Rektangeln blir den form som förblir synlig när dokumentet öppnas. Du kan kontrollera dess storlek, position och formatering direkt via form‑objektet.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Varför detta steg** – Att lägga till en rektangel demonstrerar kravet **insert rectangle shape word**. Genom att sätta `FillColor` och `LineColor` blir formen lätt att upptäcka i det färdiga dokumentet.

## Steg 4: Infoga en ellips‑form och dölj den

Nu lägger du till den form du avser att dölja. `Hidden`‑egenskapen talar om för Word att inte rendera formen i UI, men den finns kvar i dokumentstrukturen.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Förklaring** – Att sätta `Hidden = true` är kärnan i **hide shape in word**. Word respekterar denna flagga vid normal visning och utskrift, men formen kan fortfarande nås programmässigt om så behövs.

## Steg 5: Spara dokumentet

Skriv slutligen dokumentet till disk. Välj en mapp där du har skrivbehörighet och ge filen ett tydligt namn som speglar handledningens syfte.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Resultat** – När du öppnar `ShapeVisibility.docx` i Microsoft Word visas bara den ljusblå rektangeln. Den dolda ellipsen syns inte, vilket bekräftar att du framgångsrikt har lärt dig **hur man döljer en form** i en Word‑fil.

## Fullt fungerande exempel

När du sätter ihop alla kodsnuttar får du ett enda, körbart program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Förväntat resultat

- **Visuellt**: När du öppnar `ShapeVisibility.docx` ser du en ljusblå rektangel placerad nära vänstermarginalen. Ingen ellips är synlig.
- **Programmässigt**: Den dolda ellipsen finns kvar i dokumentets XML (`<w:drawing>`‑element) med attributet `w:hidden` satt, vilket du kan verifiera genom att öppna filen som en zip och inspektera `document.xml`.

## Vanliga frågor och edge‑cases

| Fråga | Svar |
|----------|--------|
| *Kan jag dölja flera former?* | Ja. Sätt `Hidden = true` på varje form du vill dölja. |
| *Skriver dolda former ut?* | Som standard skriver Word inte ut dolda objekt. Om du vill ha dem med i utskriften, rensa `Hidden`‑flaggan innan utskrift. |
| *Stöds den dolda egenskapen i äldre Word‑versioner?* | `Hidden`‑attributet är en del av Office Open XML‑standarden och fungerar i Word 2007 och senare. |
| *Vad händer om jag vill växla synlighet vid körning?* | Hämta formen via `document.GetChildNodes(NodeType.Shape, true)` och växla `Hidden`‑egenskapen baserat på din logik. |

## Pro‑tips

- **Prestanda**: Om du genererar många dokument, återanvänd en enda `DocumentBuilder`‑instans istället för att skapa en ny för varje fil.
- **Versionskontroll**: Lagra de genererade `.docx`‑filerna i en versionskontrollerad mapp; dolda former kan fungera som metadata‑markörer för efterföljande bearbetning.
- **Testning**: Automatisera ett snabbt visuellt test genom att konvertera DOCX till PDF med Aspose.Words (`document.Save("out.pdf")`). PDF‑filen döljer också ellipsen, vilket bekräftar att den dolda flaggan propageras genom formatkonverteringar.

## Slutsats

Du vet nu **hur man döljer en form** i ett Word‑dokument med C#. Handledningen gick igenom att skapa ett dokument, **insert rectangle shape word**, lägga till en ellips och applicera `Hidden`‑flaggan för att uppnå **hide shape in word**‑beteende. Med den kompletta, körbara koden kan du integrera dolda grafikobjekt i vilken automatiserad rapport‑ eller mallningsprocess som helst.

### Nästa steg

- Utforska andra form‑egenskaper såsom rotation, skugga och textomslag.  
- Kombinera dolda former med anpassade dokumentegenskaper för att bädda in maskinläsbara data.  
- Titta på **create word document code**‑mönster för tabeller, diagram och innehållskontroller för att utöka ditt automatiseringsverktyg.

Känn dig fri att experimentera med olika formtyper och synlighetsinställningar – ditt nästa Word‑automatiseringsprojekt är bara några kodrader bort!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
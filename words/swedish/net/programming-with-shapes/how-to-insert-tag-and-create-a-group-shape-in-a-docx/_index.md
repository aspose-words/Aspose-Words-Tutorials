---
category: general
date: 2026-09-14
description: Lär dig hur du infogar tagg, lägger till former, skapar en grupp och
  sparar dokumentet som DOCX med Aspose.Words i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: sv
lastmod: 2026-09-14
og_description: Hur man infogar tagg, lägger till former, skapar en grupp och sparar
  dokument som DOCX med Aspose.Words. Följ den steg‑för‑steg‑guiden.
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: Hur man infogar tagg och bygger en grupperad form i ett DOCX med C#
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
title: Hur man infogar en tagg och skapar en gruppform i ett DOCX
url: /sv/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar tagg och skapar en gruppform i ett DOCX

Om du behöver veta **hur man infogar tagg** när du bygger en komplex layout, visar den här guiden en komplett, körbar lösning. Du kommer att se hur man lägger till former, skapar en grupp och slutligen **sparar dokument som DOCX** med Aspose.Words för .NET.

Dokumentgenerering kräver ofta en blandning av texttaggar med grafiska element. I den här handledningen lär du dig exakt **hur man infogar tagg**, hur man **lägger till former**, hur man **skapar grupp**, och det korrekta sättet att **spara docx** så att filen kan öppnas i Word utan förlust av kvalitet.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
- Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`)
- Grundläggande kunskap om C#‑syntax
- En IDE såsom Visual Studio eller VS Code

Inga ytterligare bibliotek krävs; hela exemplet körs med en enda NuGet‑referens.

## Hur man skapar grupp och lägger till former

Det första logiska steget är att skapa en **grupp** som kommer att hålla flera former. Gruppering håller formerna tillsammans när du senare flyttar eller roterar dem.

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

**Varför detta är viktigt:**  
`GroupShape` fungerar som en behållare. När du senare flyttar gruppen, färdas både rektangeln och ellipsen tillsammans, vilket bevarar deras relativa positioner. Detta är det rekommenderade sättet att hantera flera grafikobjekt som tillhör samma logiska block.

## Hur man infogar tagg i dokumentet

Nu när gruppen är klar kan du **infoga tagg** (en StructuredDocumentTag, även känd som en SDT) precis efter gruppen. Taggen kan innehålla vanlig text, rik text eller till och med upprepande innehåll.

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**Varför du bör använda en StructuredDocumentTag:**  
En SDT ger en semantisk markör som Word kan känna igen för innehållskontroller, databindning eller formulärifyllningsscenarier. Genom att använda `InsertStructuredDocumentTag` anger du explicit **hur man infogar tagg** på ett sätt som överlever efterföljande redigering i Microsoft Word.

## Hur man sparar docx och verifierar resultatet

Det sista steget är att spara dokumentet. Koden nedan demonstrerar det korrekta sättet att **spara dokument som docx** och var du hittar utdatafilen.

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

När du öppnar *GroupAndSDT.docx* i Word bör du se en grupperad rektangel‑ellips‑grafik följt av en vanlig text‑innehållskontroll med titeln **MyTag** som innehåller raden “Content inside the SDT”.

### Förväntat resultat

- En 200 × 200 punkters grupp placerad vid (50, 50) på sidan.
- Inuti gruppen: en blå rektangel till vänster och en ellips till höger (standardfärger).
- Direkt under gruppen: en innehållskontroll märkt **MyTag** med texten “Content inside the SDT”.

## Fullständigt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i en konsolapplikation. Det inkluderar alla nödvändiga `using`‑direktiv, felhantering och kommentarer som förklarar varje steg.

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

Kör programmet, navigera till ditt skrivbord och dubbelklicka på *GroupAndSDT.docx* för att verifiera att gruppen och taggen visas som beskrivs.

## Vanliga frågor och edge‑cases

| Fråga | Svar |
|----------|--------|
| **Kan jag lägga till fler än två former i gruppen?** | Ja. Anropa `groupShape.AppendChild(new Shape(...))` för varje ytterligare form innan du infogar gruppen. |
| **Vad händer om jag behöver en rich‑text‑tagg istället för vanlig text?** | Använd `StructuredDocumentTagType.RichText` i `InsertStructuredDocumentTag`. |
| **Hur ändrar jag färgen på rektangeln eller ellipsen?** | Sätt `FillColor`‑egenskapen på varje `Shape`‑instans, t.ex. `shape.FillColor = Color.LightBlue;`. |
| **Är det möjligt att rotera hela gruppen?** | Sätt `groupShape.Rotation = 45;` (grader) innan du infogar noden. |
| **Behöver jag anropa `Dispose()` på några objekt?** | Aspose.Words hanterar de flesta resurser internt; att disponera `Document` är valfritt i en kortlivad konsolapp. |

## Bästa praxis för att spara DOCX‑filer

- **Använd alltid en absolut sökväg** (eller en väl definierad relativ sökväg) när du anropar `document.Save`. Detta undviker felet “file not found” som kan uppstå med oklara arbetskataloger.
- **Föredra `Save`‑överladdningar som accepterar en ström** om du behöver skicka dokumentet via HTTP eller lagra det i en databas.
- **Ställ in `CompatibilityOptions`** om du måste rikta in dig på äldre versioner av Word (t.ex. Word 2003). För de flesta moderna scenarier fungerar standardinställningarna bra.

## Nästa steg

Nu när du vet **hur man infogar tagg**, hur man **lägger till former**, hur man **skapar grupp**, och hur man **sparar docx**, kan du utforska mer avancerade scenarier:

- Kombinera flera grupper för att bygga komplexa diagram.
- Använd `StructuredDocumentTag` för databindning i Word‑mallar.
- Exportera samma dokument till PDF (`document.Save("output.pdf")`) samtidigt som du bevarar de grupperade grafikerna.
- Automatisera formulärifyllning genom att programatiskt sätta innehållet i SDT (`builder.MoveToDocumentEnd(); builder.Write("New value");`).

Experimentera med olika `ShapeType`‑värden (t.ex. `ShapeType.Polygon`, `ShapeType.Line`) för att se hur de beter sig inom en `GroupShape`. Samma mönster fungerar för tabeller, bilder eller någon annan nod du vill hålla ihop.

---

**Sammanfattning:** Denna handledning demonstrerade **hur man infogar tagg** i en grupperad form, hur man **lägger till former**, hur man **skapar grupp**, och den korrekta metoden att **spara dokument som docx** med Aspose.Words för .NET. Du har nu en solid grund för att programatiskt bygga rika, interaktiva DOCX‑filer.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [How to Recover DOCX – Complete Guide Using Aspose.Words](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [How to Check Grammar in DOCX with Aspose.Words – use gpt-4 turbo](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
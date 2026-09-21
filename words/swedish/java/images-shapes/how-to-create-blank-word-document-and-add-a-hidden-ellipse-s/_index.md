---
category: general
date: 2026-09-21
description: Skapa ett tomt Word‑dokument med en dold ellips med C#. Lär dig hur du
  döljer en form i Word och genererar en dold form programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: sv
lastmod: 2026-09-21
og_description: Skapa ett tomt Word‑dokument med en dold ellips med C#. Den här guiden
  visar hur man döljer en form i Word och bygger dolda former programatiskt.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Skapa ett tomt Word‑dokument med en dold ellipsform i C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man skapar ett tomt Word‑dokument och lägger till en dold ellipsform i
  C#
url: /sv/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du ett tomt Word-dokument och lägger till en dold ellipsform i C#

Om du behöver **skapa ett tomt Word-dokument** som innehåller en osynlig grafik, visar den här guiden exakt hur du gör. I slutet av handledningen har du en .docx‑fil som ser tom ut men faktiskt lagrar en ellipsform som är dold i layouten.

Vi kommer att använda Aspose.Words for .NET för att bygga dokumentet, infoga en ellips, dölja den och spara filen. Stegen täcker också **how to create ellipse**‑objekt, det korrekta sättet att **hide shape in Word**, och hur man **create hidden shape**‑kod som fungerar med alla .NET‑projekt.

## Förutsättningar

* .NET 6.0 SDK eller senare installerat  
* Visual Studio 2022 (eller någon C#‑redigerare)  
* En Aspose.Words for .NET‑licens eller en gratis utvärderingskopi  
* Grundläggande kunskap om C#‑syntax  

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Skapa ett tomt Word-dokument med Aspose.Words

Det första steget är att generera en tom Word‑fil. Detta ger oss en ren canvas där vi senare kan infoga dolda grafik.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Varför vi börjar med ett tomt dokument** – Att börja från en tom fil garanterar att inget oönskat innehåll stör den dolda formen. Det håller också filstorleken minimal, vilket är användbart när dokumentet senare används som en mall.

## Hur man skapar en ellips i det tomma dokumentet

Nästa steg är att vi behöver en `DocumentBuilder` för att lägga till innehåll. Buildern låter oss placera former exakt där vi vill ha dem.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Förklaring** – `ShapeType.Ellipse` talar om för Aspose.Words att rita en cirkel‑liknande figur. Bredden och höjden mäts i punkter (1 pt ≈ 1/72 tum). Du kan justera dessa värden för att passa dina designbehov.

## Dölj form i Word så den inte visas i layouten

En form som är dold finns fortfarande i dokumentets XML, vilket kan vara användbart för metadata, villkorlig formatering eller senare programatiska ändringar. För att dölja den sätter vi egenskapen `Hidden` till `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Varför dölja formen** – Dolda former ignoreras av layout‑motorn, så sidan ser helt tom ut. Formdata kvarstår dock, vilket kan vara användbart för att lagra markörer, bokmärken eller anpassad XML som efterföljande processer kan läsa.

## Spara dokumentet med den dolda formen

Till sist skriver vi filen till disk. Den sparade `.docx`‑filen öppnas i Microsoft Word utan synligt innehåll, men den dolda ellipsen finns fortfarande kvar.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verifiering** – Öppna den genererade filen i Word, tryck sedan `Alt+F9` för att växla fältkoder och `Ctrl+A` → `Ctrl+Shift+F9` för att visa dolda objekt. Du kommer att se ellipsen i dokumentets XML (`word/document.xml`) men inget på sidan.

---

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i ett nytt konsolprojekt. Det inkluderar alla `using`‑direktiv och `Main`‑metoden så att du kan köra det utan ytterligare uppbyggnad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Förväntad output** – När du kör programmet skriver konsolen ut filsökvägen, och den resulterande Word‑filen innehåller inga synliga objekt. Om du inspekterar dokumentet med ett zip‑verktyg (`.docx` är ett zip‑arkiv) hittar du `<w:pict>`‑elementet som beskriver ellipsen i `word/document.xml`.

---

## Vanliga variationer och kantfall

| Scenario | Vad som ska ändras | Varför det är viktigt |
|----------|--------------------|-----------------------|
| **Olika form** | Byt ut `ShapeType.Ellipse` mot `ShapeType.Rectangle`, `ShapeType.Line` osv. | Gör att du kan dölja annan grafik samtidigt som du behåller samma arbetsflöde. |
| **Flera dolda former** | Anropa `InsertShape` flera gånger och sätt `Hidden = true` på var och en. | Användbart för att bädda in en samling av markörer eller platshållare. |
| **Villkorlig synlighet** | Använd `shape.Visible = false` tillsammans med `shape.Hidden = true` för extra säkerhet. | Vissa äldre Word‑versioner hanterar `Visible` annorlunda; att sätta båda täcker alla fall. |
| **Spara till en ström** | Byt ut `doc.Save(path)` mot `doc.Save(stream, SaveFormat.Docx)`. | Gör det möjligt att skicka dokumentet direkt via HTTP eller lagra det i en databas. |
| **Applicera en stil** | Efter insättning, modifiera `ellipse.FillColor`, `ellipse.LineWeight` osv. innan du döljer. | Formens stil bevaras i XML, vilket kan vara användbart för senare avdöljning. |

**Proffstips:** Testa alltid den dolda formen på mål‑Word‑versionen (t.ex. Word 2019, Word 365) eftersom renderings‑buggar ibland uppstår när dolda objekt interagerar med komplexa sidlayouter.

---

## Vanliga frågor

**Q: Påverkar dolda former dokumentstorleken?**  
A: Formens XML lägger till några hundra byte, vilket är försumligt för de flesta användningsområden. Filen förblir i princip samma storlek som ett riktigt tomt dokument.

**Q: Kan jag avdölja formen senare programatiskt?**  
A: Ja. Ladda dokumentet, lokalisera formen (`doc.GetChildNodes(NodeType.Shape, true)`) och sätt `shape.Hidden = false`.

**Q: Kommer den dolda formen att visas vid utskrift?**  
A: Nej. Dolda objekt exkluderas från utskriftslayouten, så den utskrivna sidan förblir tom.

**Q: Är detta tillvägagångssätt endast kompatibelt med Office Open XML (OOXML)?**  
A: `Hidden`‑egenskapen är en del av OOXML‑specifikationen, så alla ordbehandlare som fullt implementerar OOXML (Word, LibreOffice, Google Docs) kommer att respektera den dolda flaggan.

---

## Slutsats

Du vet nu hur du **create blank Word document**, **how to create ellipse**, **hide shape in Word** och **create hidden shape** med Aspose.Words for .NET. Handledningen täckte hela livscykeln – från att initiera en tom fil till att infoga, dölja och spara formen – samt verifieringssteg och vanliga variationer.

Nästa steg kan du utforska:

* Lägga till dolda textrutor för metadata (`hide shape in word`‑teknik tillämpad på text)  
* Använda anpassade XML‑delar för att lagra strukturerad data tillsammans med dolda former  
* Konvertera dokumentet med dold form till PDF samtidigt som de dolda elementen bevaras  

Experimentera med olika former och synlighetsinställningar för att se hur dolt innehåll kan fungera som en lättviktig datalagring i Word‑filer.

Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Skapa gruppform i Word‑dokument med Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa Word‑dokument med en skuggad rektangel – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
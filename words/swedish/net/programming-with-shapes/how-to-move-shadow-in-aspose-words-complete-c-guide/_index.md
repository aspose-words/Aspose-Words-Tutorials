---
category: general
date: 2026-05-01
description: Hur man flyttar skuggan på en form i Aspose.Words med C#. Lär dig att
  lägga till skugga på en form, ändra oskärpa, ställa in transparens och rotera skuggan
  på några minuter.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: sv
og_description: Hur man flyttar skugga på en form i Aspose.Words med C#. Denna handledning
  visar hur du lägger till skugga på en form, ändrar oskärpa, ställer in transparens
  och roterar skuggan.
og_title: Hur man flyttar skugga i Aspose.Words – Komplett C#-guide
tags:
- Aspose.Words
- C#
- Document Automation
title: Hur man flyttar skugga i Aspose.Words – Komplett C#‑guide
url: /sv/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så flyttar du skugga i Aspose.Words – Komplett C#-guide

Har du någonsin undrat **how to move shadow** på en form i ett Word‑dokument utan att öppna Word manuellt? I mitt dagliga arbete har jag ofta behövt justera en formes skugga programatiskt—oavsett om det är för en polerad rapport eller en dynamisk mall. Den goda nyheten? Med Aspose.Words kan du göra det på några få rader, och du kommer också att lära dig **add shadow to shape**, **how to change blur**, **how to set transparency**, och **how to rotate shadow** i samma steg.

I den här handledningen går vi igenom ett verkligt scenario: att ladda en befintlig DOCX som redan innehåller en form, justera skuggans position, mjukhet, opacitet och riktning, och slutligen spara resultatet. I slutet har du ett återanvändbart kodsnutt som du kan klistra in i vilket .NET‑projekt som helst, och du kommer att förstå varför varje egenskap är viktig.

## Förutsättningar – Vad du behöver innan du börjar

- **Aspose.Words for .NET** (version 23.12 eller senare). Du kan hämta det från NuGet med `Install-Package Aspose.Words`.
- En .NET 6+ utvecklingsmiljö (Visual Studio, VS Code, Rider—vad du än föredrar).
- En inmatnings‑Word‑fil (`input.docx`) som redan innehåller minst en form (en rektangel, cirkel eller bild räcker).
- Grundläggande kunskap om C#‑syntax—inget avancerat.

Om du saknar någon av dessa, pausa en stund och installera biblioteket; resten av guiden förutsätter att paketet redan är refererat.

## Steg 1: Ladda dokumentet och hämta målformen – **How to Move Shadow** börjar här

Det första vi gör är att ladda källdokumentet och hitta den form vi vill ändra. Aspose.Words behandlar varje objekt (paragrafer, tabeller, former) som en nod i ett träd, så vi kan fråga den direkt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Varför detta är viktigt:** Att ladda dokumentet en gång och återanvända samma `Document`‑instans är effektivt. Anropet `GetChild` är säkert eftersom det returnerar `null` om indexet är utanför intervallet, vilket låter oss hantera saknade former på ett smidigt sätt.

## Steg 2: Justera suddradie – Master **How to Change Blur**

En mjuk skugga ser professionell ut, medan en hård kant kan kännas billig. Egenskapen `BlurRadius` styr mjukheten i punkter (1 pt ≈ 1/72 tum). Låt oss öka den till 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Proffstips:** Standardvärdet för sudd är 0,5 pt. Allt över 5 pt märks vanligtvis, men var försiktig så att du inte gör den för stor—det kan få formen att se fristående från sidan.

## Steg 3: Ställ in transparens – Svaret på **How to Set Transparency**

Transparens bestämmer hur genomskinlig skuggan är. Ett värde på `0` betyder helt ogenomskinlig; `1` betyder helt osynlig. För en subtil effekt använder vi `0.3` (30 % transparent).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Varför du kan bry dig:** Om formen är mörk kan en helt ogenomskinlig skugga dränka den underliggande texten. Genom att justera transparensen behåller du dokumentets läsbarhet samtidigt som du ger djup.

## Steg 4: Flytta skuggan – Kärnan i **How to Move Shadow**

`Distance`‑egenskapen definierar hur långt skuggan är förskjuten från formen, mätt i punkter. Ett större avstånd skjuter skuggan längre bort, vilket skapar en mer dramatisk effekt.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **Vad om du behöver en liten förskjutning?** Att sätta `Distance` till `0` gör att skuggan sitter direkt bakom formen, vilket kan vara användbart för präglade effekter.

## Steg 5: Rotera ljuskällan – Lösning på **How to Rotate Shadow**

Skuggor är inte bara rakt ner; de följer ljuskällans vinkel. Egenskapen `Angle` (i grader) roterar skuggan runt formen. Låt oss luta den 45°.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Snabbt experiment:** Prova `90` för en högerskugga eller `-30` för en vänstersläntrande. Den visuella förändringen är omedelbar.

## Steg 6: Spara dokumentet – Se resultatet av **Add Shadow to Shape**

Nu när vi har justerat skuggan skriver vi dokumentet tillbaka till disk. Du kan skriva över originalet eller skapa en ny fil; exemplet använder en ny utdatafil.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Förväntat resultat:** Öppna `output.docx`. Formens skugga kommer att vara mjukare, lätt förskjuten, semi‑transparent och vinklad 45°. Om du jämför sida‑vid‑sida med `input.docx` är skillnaden tydlig.

### Fullt fungerande exempel (Klar att kopiera och klistra in)

Nedan är hela programmet i ett block. Klistra in det i ett nytt konsolprojekt, ersätt `YOUR_DIRECTORY` med en faktisk mappväg, och kör.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Vanliga frågor & kantfall

### Vad händer om dokumentet har flera former?

Du kan loopa igenom alla former:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### Kan jag lägga till en skugga på en form som för närvarande saknar någon?

Absolut. `ShadowFormat`‑objektet finns alltid; du behöver bara aktivera det:

```csharp
shape.ShadowFormat.Enabled = true;
```

### Fungerar detta med bilder och SmartArt?

Ja. Alla noder som ärver från `Shape`—inklusive bilder, diagram och SmartArt—exponerar `ShadowFormat`. Samma egenskaper gäller.

### Hur styr jag skuggans färg?

Använd egenskapen `Color`:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Kompatibilitetsfrågor?

Aspose.Words 23.12+ stödjer .NET 6, .NET Core 3.1 och .NET Framework 4.6.2+. API‑et som visas är stabilt över dessa versioner.

## Slutsats

Vi har just gått igenom **how to move shadow** på en form med Aspose.Words, och på vägen har vi också demonstrerat **add shadow to shape**, **how to change blur**, **how to set transparency** och **how to rotate shadow**. Det kompletta, körbara exemplet låter dig justera vilken form som helsts skugga på några sekunder, vilket ger dina dokument ett polerat, professionellt utseende utan att någonsin öppna Word.

Redo för nästa steg? Prova att kombinera dessa skuggjusteringar med **conditional formatting**—till exempel, applicera bara en djupare skugga på rubriker eller diagram som överstiger en viss storlek. Eller utforska **gradient fills** för själva formen för att skapa en riktigt iögonfallande design.

Om du stöter på problem, lämna en kommentar nedan. Lycka till med kodandet, och må dina skuggor alltid falla precis där du vill ha dem!

![Diagram som visar effekten av att flytta en skugga på en form – exempel på hur man flyttar skugga](https://example.com/images/shadow-demo.png "exempel på hur man flyttar skugga")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
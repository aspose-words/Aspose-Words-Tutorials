---
category: general
date: 2026-01-13
description: Skapa ett Word‑dokument med Aspose.Words och lär dig hur du infogar en
  rektangulär form, hur du lägger till skugga och hur du lägger till formskugga i
  C#. Fullständigt exempel inkluderat.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: sv
og_description: Skapa Word-dokument med Aspose.Words, se hur du infogar en rektangelform
  och hur du lägger till skugga. Följ det kompletta C#‑exemplet.
og_title: Skapa Word-dokument med en skuggad rektangel – Fullständig handledning
tags:
- Aspose.Words
- C#
- Document Automation
title: Skapa Word-dokument med en skuggad rektangel – steg‑för‑steg‑guide
url: /sv/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument med en skuggad rektangel – Steg‑för‑steg‑guide

Har du någonsin behövt **create word document** som innehåller en snygg skuggad rektangel, men var osäker på var du skulle börja? Du är inte ensam—många utvecklare stöter på samma problem när de först börjar använda Aspose.Words.  

I den här handledningen går vi igenom allt du behöver för att **create word document** programatiskt, **insert rectangle shape**, och visar **how to add shadow** så att formen verkligen sticker ut. I slutet har du ett färdigt C#‑snutt som du kan klistra in i vilket .NET‑projekt som helst.

## Vad du kommer att lära dig

- Den exakta koden för **how to insert shape** (en rektangel) i en Word‑fil.
- De egenskaper du måste justera för att **add shape shadow** och kontrollera dess utseende.
- Hur du sparar resultatet och verifierar att skuggan är synlig.
- Några praktiska tips och edge‑case‑anteckningar som sparar dig huvudvärk senare.

Ingen extern dokumentation behövs—allt finns här.

## Förutsättningar

Innan vi dyker ner, se till att du har:

1. **.NET 6.0** (eller någon nyare .NET‑version) installerad.  
2. En **license** för Aspose.Words för .NET, eller så kan du använda gratis utvärderingsläge för testning.  
3. En utvecklingsmiljö—Visual Studio 2022 fungerar utmärkt, men vilken editor som helst som kan kompilera C# räcker.

Det är allt. Inga extra NuGet‑paket utöver `Aspose.Words` behövs.

## Steg 1 – Skapa projektet och referera Aspose.Words

Först, skapa en ny konsolapp och lägg till Aspose.Words‑paketet:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Om du använder gratisprovversionen, kom ihåg att anropa `License.SetLicense` med din licensfil; annars kommer biblioteket att lägga till ett vattenstämpel.

## Steg 2 – Initiera Document Builder

Nu påbörjar vi den faktiska **create word document**‑processen. Klassen `Document` ger oss en tom canvas, och `DocumentBuilder` låter oss måla på den.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Varför behöver vi en builder? Den abstraherar bort de lågnivå‑OpenXML‑detaljerna, så att du kan fokusera på *vad* du vill snarare än *hur* filen är strukturerad. Detta är kärnan i **how to insert shape** snabbt.

## Steg 3 – Infoga rektangel‑form

Här är där vi faktiskt **insert rectangle shape**. Rektangeln kommer att vara 150 × 100 punkter (ungefär 2 tum × 1,3 tum).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

`InsertShape`‑metoden returnerar ett `Shape`‑objekt, som vi kan anpassa vidare. Vid detta tillfälle är rektangeln bara en solid vit ruta—ingen skugga ännu.

## Steg 4 – Hur man lägger till skugga (Add Shape Shadow)

Att lägga till en skugga är förvånansvärt enkelt när du vet vilka egenskaper du ska justera. Objektet `ShadowFormat` styr synlighet, färg, oskärpa, förskjutning och storlek.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Det blocket svarar på **how to add shadow** på enkel engelska: slå på den, välj en färg, justera transparens, förskjutning, oskärpa och storlek. Du kan experimentera med dessa siffror för att få en kraftig drop‑shadow eller en nästan osynlig.

### Vanliga variationer

- **Olika färger:** Använd `Color.Black` för en klassisk drop‑shadow, eller `Color.BlueViolet` för en stiliserad effekt.  
- **Ingen oskärpa:** Sätt `BlurRadius = 0` för en skarp, tydlig kant.  
- **Större förskjutningar:** Öka `OffsetX`/`OffsetY` för att flytta skuggan längre bort från formen.

## Steg 5 – Spara dokumentet och verifiera

Till sist, skriv dokumentet till disk. Filen blir en standard `.docx` som vilken modern ordbehandlare som helst kan öppna.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Öppna den resulterande *ShadowRectangle.docx* i Microsoft Word. Du bör se en rektangel med en mjuk grå skugga förskjuten till nedre‑höger—precis vad koden specificerade.

> **Förväntat resultat:** En enkelsidig Word‑fil som innehåller en 150 × 100‑punkts rektangel med en 30 % transparent grå skugga, förskjuten med 5 pt, oskärpad med 4 pt och storlek på 75 % av formen.

## Fullt fungerande exempel

När vi sätter ihop allt, här är det kompletta, färdiga programmet:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kör programmet (`dotnet run`) så får du en ny Word‑fil med en snyggt skuggad rektangel—perfekt för rapporter, certifikat eller någon visuell indikation du behöver.

## Vanliga frågor (FAQ)

**Q: Kan jag infoga andra former (ellips, stjärna) och fortfarande använda samma skuggkod?**  
A: Absolut. `InsertShape`‑metoden accepterar vilket `ShapeType`‑enum‑värde som helst. När du har en `Shape`‑instans fungerar `ShadowFormat`‑egenskaperna identiskt, så **how to add shadow** är form‑oberoende.

**Q: Vad händer om jag behöver skuggan på båda sidor av formen?**  
A: Aspose.Words stödjer endast en enda drop‑shadow per form. För att simulera en dubbelsidig effekt, duplicera formen, förskjut varje kopia olika, och sätt den ena `ShadowFormat.Visible` till `false` medan den andra behåller sin skugga synlig.

**Q: Fungerar detta på .NET Framework 4.8?**  
A: Ja. API‑et är versionsoberoende; referera bara till rätt Aspose.Words‑DLL för ditt mål‑ramverk.

## Tips & fallgropar

- **Glöm inte att sätta `Visible = true`**—skuggegenskaperna ignoreras annars.  
- **Transparensvärdena ligger mellan 0.0 (opak) och 1.0 (fullt transparent).** Ett vanligt misstag är att använda `30` istället för `0.3`.  
- **Att spara till en skrivskyddad mapp kastar ett undantag.** Se till att målatalogen är skrivbar.

## Nästa steg

Nu när du vet **how to insert shape**, **add shape shadow**, och **create word document** med Aspose.Words, kanske du vill utforska:

- Lägga till **text inuti rektangeln** med `builder.InsertParagraph()` innan du infogar formen.  
- Applicera **gradientfyllningar** eller **mönstrade kanter** för rikare visuell stil.  
- Automatisera genereringen av flera sidor, var och en med en annan skuggad form, för att bygga dynamiska rapporter.

Känn dig fri att experimentera—att ändra skuggans färg, oskärpa eller storlek kan dramatiskt förändra ditt dokuments utseende.

---

*Redo att sätta detta i produktion? Hämta koden, justera parametrarna, och se hur dina Word‑filer får en professionell finish på sekunder.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
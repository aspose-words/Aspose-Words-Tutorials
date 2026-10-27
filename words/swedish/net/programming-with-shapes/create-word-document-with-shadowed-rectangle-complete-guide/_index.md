---
category: general
date: 2026-04-21
description: Skapa ett Word‑dokument med en stylad rektangel och skugga. Lär dig hur
  du lägger till skugga, infogar rektangel‑formen, ställer in skuggfärgen och mer
  i C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: sv
og_description: Skapa ett Word-dokument och lägg till en skuggad rektangel i C#. Följ
  den här guiden för att enkelt ställa in skuggfärg, oskärpa och förskjutningar.
og_title: Skapa Word-dokument med skuggad rektangel – steg för steg
tags:
- Aspose.Words
- C#
- Document Automation
title: Skapa Word-dokument med skuggad rektangel – Komplett guide
url: /sv/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument med skuggad rektangel – Komplett guide

Har du någonsin behövt **create word document** som ser lite mer polerat ut än en enkel textsida? Kanske bygger du en rapportmall eller en flyer och en enkel rektangel med en subtil skugga skulle lösa det. I den här handledningen går vi igenom exakt det—hur man infogar en rektangelform, slår på skuggan och anpassar dess färg, oskärpa och förskjutningar—allt med C# och Aspose.Words.

Vi kommer också att gå igenom **how to add shadow** på ett sätt som fungerar oavsett om du riktar dig mot Word 2016, 2019 eller den senaste Office 365‑versionen. I slutet har du en färdig‑att‑spara *.docx*-fil som visar en snyggt skuggad rektangel, och du kommer att förstå “varför” bakom varje egenskap du sätter.

## Förutsättningar

- .NET 6 (eller någon recent .NET Framework‑version)  
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`)  
- Grundläggande kunskap om C#‑syntax  
- En IDE såsom Visual Studio (men vilken editor som helst fungerar)

Inga ytterligare bibliotek krävs; allt annat finns i Aspose.Words.

## Steg 1 – Initiera dokumentet och byggaren (Create Word Document)

För att **create word document** programatiskt börjar du med `Document`‑klassen. `DocumentBuilder` är din pensel; den låter dig lägga till text, former och andra element.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Varför detta är viktigt:* `Document`‑objektet representerar hela .docx‑filen. Utan det har du ingen plats att fästa rektangeln eller dess skugga.

## Steg 2 – Infoga en rektangelform (Insert Rectangle Shape)

Nu **insert rectangle shape** faktiskt. Metoden `InsertShape` tar en `ShapeType`‑enum, samt bredd och höjd i punkter.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Proffstips:* 1 punkt ≈ 1/72 tum, så 200 pts är ungefär 2,78 tum bred. Justera dessa siffror för att passa din layout.

## Steg 3 – Aktivera skuggan (How to Add Shadow)

Skuggor är inaktiverade som standard. Vänd på `Visible`‑flaggan för att slå på den.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Vad händer?* När `Visible` är true kommer Word att rendera en drop‑shadow baserat på de andra egenskaperna du sätter härnäst.

## Steg 4 – Anpassa skuggans utseende (Set Shadow Color, Blur, Offsets)

Här **set shadow color**, oskärpe‑radie och X/Y‑förskjutningar. Känn dig fri att experimentera—olika värden ger en mjuk glöd, ett djupare fall eller till och med en “flytande” effekt.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Varför dessa siffror?* En oskärpa på 5 pts ger en mjuk fjäderkant, medan en förskjutning på 4 pts flyttar skuggan ner‑höger, vilket efterliknar en ljuskälla från övre vänstra. Ändra `Color` till `Color.Black` för starkare kontrast, eller använd `Color.FromArgb(128, 0, 0, 0)` för en halvtransparent svart.

### Kantfall & variationer

- **Ingen oskärpa:** Sätt `Blur = 0` för en skarp, hårdkantad skugga.  
- **Negativa förskjutningar:** Använd `OffsetX = -4` för att skjuta skuggan åt vänster.  
- **Olika former:** Samma skuggegenskaper fungerar för cirklar, trianglar eller till och med frihandsritade former—byt bara `ShapeType` i Steg 2.  
- **Kompatibilitet:** Aspose.Words skriver skuggdata i Office Open XML‑formatet, vilket fungerar över Word 2010‑2021 och Office 365.

## Steg 5 – Spara dokumentet (Create Word Document)

Till sist sparar du filen till disk. Du kan välja vilket som helst stödformat (`.docx`, `.pdf`, `.odt`, …) men för den här guiden håller vi oss till det klassiska Word‑formatet.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

När du öppnar **ShadowRectangle.docx** i Microsoft Word kommer du att se en grå rektangel med en subtil, oskarp skugga förskjuten till nedre‑höger—precis vad vi kodade.

### Förväntat resultat

- En enkelsidig *.docx*-fil.  
- En 200 pt × 100 pt rektangel centrerad där markören var när `InsertShape` anropades.  
- En grå skugga som visas 4 pts åt höger och 4 pts nedåt, med en 5 pt oskärpa.

Om formen ser felplacerad ut kan du flytta markören med `builder.MoveTo` innan du infogar, eller justera formens `Left`‑ och `Top`‑egenskaper efter infogning.

## Vanliga frågor & felsökning

**Q: Skuggan visas inte i Word.**  
A: Se till att `ShadowFormat.Visible` är `true`. Verifiera också att du använder en recent version av Aspose.Words (skuggfunktionen lades till i version 20.3).  

**Q: Kan jag applicera en gradient på skuggan?**  
A: Inte direkt via `ShadowFormat`. Word‑gränssnittet stödjer gradient‑skuggor, men Open XML‑schemat (som Aspose.Words följer) exponerar bara solida färgskuggor. Du skulle behöva redigera den underliggande XML‑filen manuellt—ett mer avancerat scenario.

**Q: Vad händer om jag behöver en transparent rektangel med bara en skugga?**  
A: Sätt `rectangle.FillColor = Color.Transparent;` efter infogning. Skuggan renderas fortfarande eftersom den är oberoende av fyllningen.

## Proffstips för produktionskod

- **Återanvänd byggaren:** Om du lägger till flera former, behåll samma `DocumentBuilder`‑instans—att skapa en ny för varje form ger onödig overhead.  
- **Batch‑sparningar:** Spara en gång efter alla ändringar; frekvent I/O saktar ner stor dokumentgenerering.  
- **Felhantering:** Omslut hela blocket i ett `try / catch` och logga `Aspose.Words`‑undantag; de innehåller ofta hjälpsamma radnummer om dokumentmallen är korrupt.

## Nästa steg (Relaterade ämnen)

- **How to add shadow** till bilder eller textrutor (liknande `ShadowFormat`‑användning).  
- **Insert rectangle shape** i en tabellcell för anpassad cellstil.  
- **Create rectangle in Word** med Words inbyggda XML (för de som föredrar rå Open XML).  
- **Set shadow color** dynamiskt baserat på användarinput eller temafärger.

Experimentera med olika färger, oskärpe‑radier och förskjutningar—kanske en mjuk blå glöd för en företagsrapport, eller en djup svart skugga för en dramatisk flyer. Möjligheterna är oändliga, och kodändringarna är minimala.

---

### Snabb sammanfattning

- Vi **created a word document** från grunden.  
- Vi **inserted a rectangle shape** och aktiverade dess skugga.  
- Vi **set shadow color**, oskärpa och förskjutningar för att uppnå ett professionellt utseende.  
- Vi sparade filen, klar för distribution.

Nu har du en solid grund för att lägga till visuellt flair i vilket Word‑automatiseringsprojekt som helst. Har du fler idéer? Lämna en kommentar, så fortsätter vi samtalet. Lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
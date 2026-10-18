---
category: general
date: 2026-03-01
description: Skapa ett Word‑dokument med Aspose.Words och lär dig hur du lägger till
  en rektangel, hur du lägger till skugga, hur du ställer in transparens och hur du
  skapar en form – allt i C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: sv
og_description: Skapa Word-dokument med Aspose.Words i C#. Lär dig hur du lägger till
  en rektangel, applicerar en yttre skugga och sätter transparens på bara några steg.
og_title: Skapa Word-dokument med en rektangelform och skugga – Guide
tags:
- Aspose.Words
- C#
- Document Generation
title: Skapa Word-dokument med en rektangelform och skugga – Steg‑för‑steg‑guide
url: /sv/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word‑dokument med en rektangelform och skugga – steg‑för‑steg‑guide

Har du någonsin behövt **skapa ett Word‑dokument** som innehåller en egen‑designad rektangel? Kanske bygger du en rapportmall och vill ha en subtil skugga för att få layouten att sticka ut. Du är inte ensam – utvecklare frågar ständigt: ”Hur lägger jag till en rektangelform och en skugga programatiskt?” Den goda nyheten är att du med Aspose.Words kan göra det på bara några rader kod.

I den här handledningen går vi igenom hela processen: från att skapa ett tomt Word‑dokument, till att lägga till en rektangelform, till att konfigurera en yttre skugga med transparens. I slutet har du ett färdigt `Shadow.docx` som du kan öppna i Word och se effekten direkt. Inga externa verktyg, ingen krånglig XML – bara ren C#‑kod och tydliga förklaringar.

## Vad du kommer att lära dig

- **Hur man skapar shape‑objekt** i ett Word‑dokument med Aspose.Words.  
- **Hur man lägger till en rektangelform** i ett stycke utan att störa befintligt innehåll.  
- **Hur man lägger till en skugga** (yttre skugga) och styr färg, offset, oskärpa och transparens.  
- **Hur man sätter transparens** på skuggan så att den ser professionell ut.  
- Tips, fallgropar och varianter du kan behöva i verkliga projekt.

### Förutsättningar

- .NET 6.0 eller senare (API‑et fungerar även med .NET Framework 4.6+).  
- Aspose.Words för .NET installerat via NuGet (`Install-Package Aspose.Words`).  
- Grundläggande förståelse för C#‑syntax – inget avancerat, bara vanliga `using`‑satser och objekt‑skapande.

> **Pro‑tips:** Om du använder Visual Studio, aktivera “nullable reference types” för att fånga potentiella null‑referens‑buggar tidigt.

## Steg 1 – Skapa ett tomt Word‑dokument

För att **skapa ett Word‑dokument** börjar vi med `Document`‑klassen. Tänk på den som en tom canvas; du kan senare lägga till sektioner, stycken, tabeller eller former.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Varför behöver vi en ny `Document`‑instans? För varje shape, stycke eller stil lever de i ett dokument‑objektmodell (DOM). Att börja med ett rent dokument garanterar att rektangeln du lägger till inte stör befintligt innehåll.

## Steg 2 – Definiera rektangelformen

Nu visar vi **hur man skapar shape** en rektangel. `Shape`‑konstruktorn tar det ägande dokumentet och formtypen. Vi sätter också bredd och höjd i punkter (1 pt ≈ 1/72 tum).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Du kanske undrar: ”Kan jag använda centimeter istället för punkter?” API‑et accepterar bara punkter, men du kan konvertera: `points = centimeters * 28.35`. Denna lilla konvertering är praktisk när du anpassar former till sidmarginalerna.

## Steg 3 – Lägg till en yttre skugga och sätt transparens

Här händer magin: **hur man lägger till skugga** och **hur man sätter transparens** på den skuggan. `ShadowFormat`‑egenskapen ger dig full kontroll.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Varför dessa inställningar?**  
- **Transparency** låter den underliggande sidans textur skymta igenom, så att skuggan inte blir för tung.  
- **OffsetX/Y** skapar illusionen att formen lyfts från sidan.  
- **BlurRadius** mjukar upp kanterna – utan den blir skuggan en hård rektangel, vilket ser onaturligt ut.  

Om du vill ha en mer dramatisk effekt, öka `OffsetX/Y` till 10 och `BlurRadius` till 8. För en subtil hint, håll dem på 2 respektive 2.

## Steg 4 – Infoga formen i dokumentet

Vi **lägger till rektangelformen** i dokumentets första stycke. Om dokumentet saknar innehåll skapas `FirstParagraph` automatiskt åt dig.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Vad händer om du vill ha formen i en specifik tabellcell eller i ett senare stycke? Hitta bara den noden (`doc.GetChild(NodeType.Paragraph, index, true)`) och anropa `AppendChild` på den. Samma shape‑objekt kan klonas om du behöver flera kopior.

## Steg 5 – Spara dokumentet

Till sist **skapar vi Word‑dokument**‑filen på disk. Använd en sökväg som passar din miljö; exemplet använder en platshållare.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

När du öppnar `Shadow.docx` i Microsoft Word ser du en ljusgrå rektangel med en mjuk yttre skugga förskjuten till nedre‑höger. Skuggans 30 % transparens säkerställer att den inte dominerar sidan.

---

![Create word document with a shadowed rectangle shape](image.png "Create word document with a shadowed rectangle")

*Image alt text: create word document with a shadowed rectangle shape*

## Fullständig, körklar kod

Nedan är hela programmet som du kan kopiera‑klistra in i en konsolapp. Inga saknade delar, inga ”se dokumentationen för mer”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Förväntat resultat

- En fil med namnet **Shadow.docx** skapas i mål‑mappen.  
- När du öppnar den i Word visas en rektangel (200 × 100 pt) med en mörkgrå yttre skugga.  
- Skuggan är förskjuten 5 pt horisontellt och vertikalt, har oskärpa och är 30 % transparent.

## Vanliga frågor & kantfall

| Fråga | Svar |
|----------|--------|
| **Kan jag ändra skuggans färg så den matchar mitt varumärke?** | Absolut – byt bara ut `System.Drawing.Color.DarkGray` mot någon `Color` du föredrar, t.ex. `Color.FromArgb(255, 0, 120, 215)` för en blå accent. |
| **Vad händer om jag behöver en inre skugga istället för en yttre?** | Sätt `ShadowFormat.Style = ShadowStyle.InnerShadow`. Resten av egenskaperna fungerar på samma sätt. |
| **Stöds transparens i äldre Word‑versioner?** | Ja. Aspose.Words skriver rätt XML som Word 2007+ förstår. Äldre versioner kan ignorera transparensvärdet men visar ändå skuggan. |
| **Kan jag lägga till flera former med olika skuggor?** | Självklart – skapa bara nya `Shape`‑instanser, konfigurera varje skugga separat och lägg till dem i önskade noder. |
| **Hur är prestandan för hundratals former?** | Många former kan öka minnesanvändningen. Återanvänd en enda `Document`‑instans och lägg till former i en loop; frigör temporära objekt om du får tryck på minnet. |

## Tips för verkliga projekt

- **Batch‑generering:** När du skapar rapporter för många användare, instansiera en enda `Document`‑mall och klona den för varje iteration. Ersätt platshållare innan du lägger till former.  
- **Dynamisk storlek:** Använd sidmått (`document.FirstSection.PageSetup.PageWidth`) för att beräkna formens storlek relativt till sidan, så att layouten blir konsekvent på olika papperstorlekar.  
- **Testning:** Öppna alltid den genererade `.docx`‑filen i Word efter en ändring av skuggparametrarna. Visuell återkoppling är snabbare än att gissa på siffror.  

## Nästa steg

Nu när du vet **hur man lägger till rektangelform**, **hur man lägger till skugga** och **hur man sätter transparens**, kan du utforska:

- Att lägga till **gradient‑fyllningar** i former (`Shape.FillFormat`).  
- Att bädda in **bilder** i former för vattenstämpelseffekter.  
- Att använda **tabeller** för att placera flera skuggade former i ett rutnät.  
- Att exportera samma dokument till PDF (`document.Save("output.pdf")`) samtidigt som skuggorna bevaras.  

Alla dessa bygger på samma grundkoncept, så du kommer snabbt känna dig bekväm med att utöka koden.

---

### Sammanfattning

Vi började med att **skapa ett Word‑dokument** med Aspose.Words, sedan **hur man skapar shape** en rektangel, applicerade **hur man lägger till skugga**, justerade **hur man sätter transparens**, och sparade resultatet. Hela processen ryms i ett kompakt, återanvändbart mönster som du kan anpassa till vilken automatiseringssituation som helst.

Känn dig fri att experimentera – ändra färger, lek med offset eller stapla flera former. Stöter du på problem, gå tillbaka till avsnitten ovan; de är avsedda som snabb referens. Lycka till med kodandet, och må dina dokument alltid se polerade ut!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
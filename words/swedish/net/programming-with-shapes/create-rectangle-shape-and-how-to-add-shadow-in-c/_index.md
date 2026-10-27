---
category: general
date: 2026-04-04
description: Skapa en rektangelform i C# med Aspose.Words och lär dig hur du lägger
  till skugga, applicerar oskärpa på skuggan och gör skuggan genomskinlig – steg‑för‑steg‑guide.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: sv
og_description: Skapa rektangelform i C# med Aspose.Words. Lär dig hur du lägger till
  skugga, applicerar oskärpa på skuggan och gör skuggan transparent i en kortfattad
  handledning.
og_title: Skapa rektangelform och hur man lägger till skugga i C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Skapa en rektangel och hur man lägger till skugga i C#
url: /sv/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform och hur man lägger till skugga i C#

Har du någonsin behövt **create rectangle shape** i ett Word‑dokument men varit osäker på hur du ger det en subtil drop‑shadow? Du är inte ensam. I många rapporterings‑ eller varumärkes‑scenarier kan en enkel rektangel med en mjuk, halvtransparent skugga få layouten att kännas polerad utan mycket ansträngning.

I den här handledningen går vi igenom **how to create document** med Aspose.Words, sedan visar vi **how to add shadow**, **apply blur to shadow** och även **make shadow transparent**. I slutet har du ett färdigt C#‑snippet som producerar en *.docx*-fil med en snyggt skuggad rektangel – allt på några minuter.

## Vad du behöver

- .NET 6 eller senare (API:et fungerar även med .NET Framework 4.6+)
- Aspose.Words for .NET (gratis provversion fungerar för detta exempel)
- En kodredigerare – Visual Studio, VS Code, Rider, vad du föredrar
- Grundläggande C#‑kunskaper – inget avancerat, bara förmågan att köra en konsolapp

Om du har det, kan vi hoppa rakt in i lösningen.

## Steg 1 – How to create document och initiera canvas

Först och främst: du behöver ett tomt `Document`‑objekt. Tänk på det som ett tomt papper som Aspose.Words senare omvandlar till en Word‑fil.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Varför instansierar vi `Document` istället för att ladda en mall? Att börja från början garanterar att inga dolda stilar eller sektioner stör vår rektangel. Det håller också filstorleken liten – en bra vana när du genererar många dokument i en loop.

## Steg 2 – Create rectangle shape (kärnan i vårt primära nyckelord)

Nu **create rectangle shape** faktiskt. `Shape`‑klassen är flexibel; du anger typen (Rectangle), storlek och hur den ska omslutas av omgivande text.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Observera användningen av objekt‑initialiseringssyntax – den är koncis och minskar risken att glömma att sätta en egenskap senare. Rektangeln kommer att ligga i det första stycket, som vi lägger till i nästa steg.

## Steg 3 – How to add shadow och anpassa dess utseende

Att lägga till en skugga är inte bara en enda rad; du har flera egenskaper att justera. Här kommer de sekundära nyckelorden **apply blur to shadow** och **make shadow transparent** in i bilden.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

En snabb notering om siffrorna: `BlurRadius` på 5 ger en mjuk fjädring; öka till 10 för ett mjukare utseende, eller sänk till 2 för en skarp kant. `Transparency`‑värdet varierar från 0 (opak) till 1 (osynlig). Justera efter ditt varumärkes kontrastkrav.

### Proffstips

Om du någonsin behöver en färgad skugga (t.ex. en företagsblå), ersätt bara `Color.DarkGray` med `Color.FromArgb(80, 0, 120, 215)`. Det första argumentet är alfa‑kanalen – håll den låg för subtilitet.

## Steg 4 – Insert the shape i dokumentet

Med rektangeln och dess skugga redo placerar vi den nu i dokumentets första stycke. Detta steg säkerställer att formen visas högst upp i filen.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Varför det första stycket? Det är ett säkert standardval som fungerar även när dokumentet är helt tomt. Om du har en specifik plats (t.ex. efter en rubrik) skulle du hitta den noden och infoga formen där istället.

## Steg 5 – Save the file och verifiera resultatet

Till sist sparar vi dokumentet till disk. Du kan välja vilken sökväg du vill; se bara till att mappen finns.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

När du öppnar *ShadowRectangle.docx* i Microsoft Word bör du se en 200 × 100‑punkts rektangel med en mörkgrå, lätt suddig, 30 % transparent skugga som är förskjuten tre punkter åt höger och ner. Effekten är subtil men ger djup till annars platta layouter.

![Skapa rektangelform med skugga i Aspose.Words](https://example.com/placeholder-image.png "Skapa rektangelform med skugga i Aspose.Words")

*Bild alt‑text:* **create rectangle shape with shadow in Aspose.Words** – bilden visar det färdiga dokumentet med den skuggade rektangeln.

## Vanliga variationer och kantfall

### Ändra skuggans färg dynamiskt

Om din applikation stödjer teman kan du hämta skuggans färg från en konfigurationsfil:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Göra formen icke‑inline

Ibland vill du att rektangeln ska flyta över text. Byt `WrapType` till `WrapType.Square` och sätt `RelativeHorizontalPosition` till `RelativeHorizontalPosition.Margin` för mer kontroll.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Hantera flera sidor

Om du behöver en rektangel på varje sida, loopa igenom `doc.Sections` och lägg till en klonad form i varje sections första stycke. Kom ihåg att anropa `rect.Clone(true)` för att även duplicera skugginställningarna.

## Sammanfattning – Vad vi uppnådde

- **Created rectangle shape** med Aspose.Words
- **How to add shadow** med färg, förskjutning, suddighet och transparens
- Visade **apply blur to shadow** och **make shadow transparent**
- Sparade en Word‑fil som du kan öppna omedelbart

Allt detta uppnåddes med bara ett fåtal rader, vilket visar att sofistikerade visuella justeringar inte alltid kräver tunga grafikbibliotek.

## Vad blir nästa?

- Experimentera med andra `ShapeType`s (Ellipse, Cloud, etc.) och se hur skuggor beter sig.
- Kombinera rektangeln med textrutor för att bygga märkta call‑outs.
- Fördjupa dig i **how to create document**‑mallar som redan innehåller platshållare för former, och fyll sedan i dem programmässigt.

Känn dig fri att justera suddradie‑radien, färgen eller transparensen tills skuggan ser precis rätt ut för ditt designspråk. API:et är förlåtande, och förändringarna syns omedelbart när du kör konsolappen igen.

Lycka till med kodandet, och må dina dokument alltid ha den extra djupkänslan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
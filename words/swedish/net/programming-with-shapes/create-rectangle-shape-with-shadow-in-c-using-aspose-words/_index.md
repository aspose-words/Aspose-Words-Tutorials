---
category: general
date: 2026-03-22
description: Skapa en rektangelform i C# och lägg till skugga på formen med Aspose.Words.
  Lär dig hur du lägger till skugga, hur du skapar en rektangel och hur du ställer
  in skuggans egenskaper.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: sv
og_description: Skapa rektangel i C# och lägg till skugga på formen med Aspose.Words.
  Steg‑för‑steg‑guide som täcker hur du lägger till skugga, hur du skapar en rektangel
  och hur du ställer in skuggan.
og_title: Skapa rektangel med skugga i C# – Fullständig guide
tags:
- Aspose.Words
- C#
- Document Automation
title: Skapa rektangelform med skugga i C# med Aspose.Words
url: /sv/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform med skugga i C# med Aspose.Words

Har du någonsin behövt **create rectangle shape** i ett Word‑dokument men varit osäker på hur du ger det en subtil drop‑shadow? Du är inte ensam—många utvecklare stöter på detta när de första gången provar dokumentautomatisering. I den här guiden går vi igenom exakt hur du **add shadow to shape** med Aspose.Words, och vi svarar också på “**how to add shadow**”, “**how to create rectangle**” och “**how to set shadow**” längs vägen.

Vi börjar med ett tomt `Document`, ritar en rektangel, slår på dess skugga, justerar suddighet, avstånd, vinkel och färg, och sparar slutligen filen. När du är klar har du en färdig `.docx` som visar en gråtonad rektangel som svävar precis ovanför sidan. Ingen gåta, bara rak kod som du kan kopiera‑klistra in i vilket .NET‑projekt som helst.

## Förutsättningar

* **Aspose.Words for .NET** (den senaste versionen i mars 2026). Du kan hämta den från NuGet med `Install-Package Aspose.Words`.
* En .NET‑utvecklingsmiljö – Visual Studio, Rider eller till och med VS Code med C#‑tillägget fungerar bra.
* Grundläggande kunskaper i C# – inget avancerat, bara förmågan att skapa en konsol‑ eller WinForms‑app.

Det är allt. Inga extra bibliotek, inga dolda steg. Är du redo? Låt oss börja.

## Steg 1: Initiera ett nytt tomt dokument

För att **create rectangle shape** behöver vi först en behållare – ett `Document`‑objekt – som representerar Word‑filen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

`Document`‑klassen är startpunkten för allt Aspose.Words gör. Tänk på den som en tom duk; utan den kan du inte lägga till några former, tabeller eller text.

## Steg 2: Skapa rektangeln som ska hålla skuggan

Nu kommer vi att **how to create rectangle** genom att instansiera en `Shape` av typen `Rectangle`. Vi sätter också dess storlek i punkter (1 punkt ≈ 1/72 tum).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Varför välja 200 × 100 punkter? Det är en lagom storlek för en demo – tillräckligt stor för att se skuggan tydligt, men inte så enorm att den överväldigar sidan. Känn dig fri att justera dessa siffror för att passa din layout.

## Steg 3: Aktivera skuggeffekten och konfigurera dess utseende

Här är kärnan i handledningen: **how to add shadow** och **how to set shadow**‑egenskaper. Aspose.Words exponerar ett `Shadow`‑objekt på varje form, vilket låter dig slå på effekten och justera visuella parametrar.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** mjukar upp kanterna – ett högre värde får skuggan att se mer diffust ut.
* **Distance** skjuter skuggan längre bort från rektangeln.
* **Angle** bestämmer var ljuset verkar komma ifrån; 45° ger en diagonal, naturlig look.
* **Color** låter dig välja vilken `System.Drawing.Color` som helst. Grå är ett säkert standardval, men du kan gå djärvt med `Color.Black` eller subtilt med `Color.LightGray`.

Proffstips: Om du sätter `Enabled = false` ignoreras alla andra skuggeinställningar, så dubbelkolla alltid den flaggan.

## Steg 4: Infoga formen i dokumentets kropp

När rektangeln är klar och dess skugga konfigurerad måste vi placera den i dokumentet. Det enklaste sättet är att lägga till den i det första stycket i den första sektionen.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Om ditt dokument redan innehåller text kan du hitta ett specifikt `Paragraph` eller till och med en `Table`‑cell och infoga formen där. Metoden `AppendChild` är mångsidig – den fungerar med vilken `Node`‑typ som helst.

## Steg 5: Spara dokumentet och verifiera resultatet

Till sist skriver vi filen till disk. Ändra sökvägen till var du vill; mappen måste finnas, annars får du ett undantag.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Öppna den resulterande `ShadowedRectangle.docx` i Microsoft Word (eller LibreOffice) så bör du se en grå rektangel med en skarp, diagonal skugga som drar ner‑höger. Om skuggan ser för svag ut, öka `BlurRadius` eller `Distance` och kör koden igen – experimentering är en del av det roliga.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Skapa rektangelform med skugga exempel"}

### Förväntat resultat

* Ett ensidigt Word‑dokument.
* En 200 × 100‑punkts grå rektangel placerad längst upp till vänster på sidan.
* En subtil grå skugga förskjuten med 8 pixlar i en 45°‑vinkel, suddad med 5 pixlar.

## Så lägger du till skugga på en form – djupdykning

Du kanske undrar, *“Kan jag animera skuggan eller få den att ändras baserat på användarinmatning?”* Även om Aspose.Words i sig inte stödjer animation kan du programatiskt justera skuggegenskaperna innan du sparar, vilket effektivt skapar flera versioner av samma dokument med olika utseenden. Till exempel, loopa över en samling färger:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Det där lilla kodsnutten demonstrerar **how to set shadow** dynamiskt—perfekt för att generera tematiska rapporter.

## Så skapar du rektangel – alternativa former

Om du behöver en rundad rektangel, byt helt enkelt `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Eller, för en perfekt kvadrat, sätt `Width` lika med `Height`. Samma skuggegenskaper gäller, så du är redan täckt på **how to add shadow** för vilken form du än väljer.

## Vanliga fallgropar och felsökning

| Symptom | Trolig orsak | Lösning |
|---------|--------------|---------|
| Skuggan visas inte | `Shadow.Enabled` lämnades som `false` | Sätt `rectangleShape.Shadow.Enabled = true;` |
| Skuggan ser för skarp ut | `BlurRadius` satt till 0 | Öka `BlurRadius` till minst 3 |
| Dokumentet kastar `FileNotFoundException` vid sparning | Målmappen finns inte | Skapa mappen först eller använd en giltig sökväg |
| Formen är osynlig | Width/Height satt till 0 | Se till att båda dimensionerna är > 0 |

## Sammanfattning – vad vi har åstadkommit

* **Create rectangle shape** i ett nytt Word‑dokument med Aspose.Words.  
* **Add shadow to shape** genom att växla `Shadow.Enabled`‑flaggan och justera suddighet, avstånd, vinkel och färg.  
* Visade **how to add shadow**, **how to create rectangle**, och **how to set shadow** i ett rent, återanvändbart kodexempel.  
* Tillhandahöll ett komplett, färdigt‑att‑köra exempel som du kan klistra in i vilket C#‑projekt som helst.

## Vad blir nästa?

Nu när du behärskar grunderna, överväg att utforska:

* **How to add shadow to images** – samma `Shadow`‑API fungerar för `ShapeType.Image`.
* **Combining multiple shapes** – skapa flödesscheman eller infografik direkt i Word.
* **Exporting to PDF** – anropa `document.Save("output.pdf")` efter att ha lagt till skuggor för en utskrivbar version.

Känn dig fri att experimentera med olika färger, vinklar eller till och med gradientfyllningar. API:et är tillräckligt flexibelt för att låta dig skapa professionellt utseende dokument utan att någonsin öppna Word manuellt.

Lycka till med kodningen! Om du stöter på problem, lämna en kommentar nedan eller kolla Aspose.Words‑forumet – communityn hjälper snabbt.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
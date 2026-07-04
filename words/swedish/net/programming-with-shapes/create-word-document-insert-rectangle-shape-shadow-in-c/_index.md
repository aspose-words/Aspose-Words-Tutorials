---
category: general
date: 2026-05-26
description: Skapa Word-dokument i C# med Aspose.Words, infoga en rektangulär form,
  ange fyllningsfärg och lägg till skuggeffekt – steg‑för‑steg‑guide.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: sv
og_description: Skapa Word-dokument i C# med Aspose.Words. Lär dig hur du infogar
  en rektangel, ställer in dess fyllningsfärg och lägger till en skuggeffekt.
og_title: Skapa Word-dokument – Infoga rektangel och skugga i C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa Word-dokument – Infoga rektangelform och skugga i C#
url: /sv/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument – Infoga rektangelform & skugga i C#

Har du någonsin undrat hur man **skapar Word-dokument** programatiskt utan att först öppna Microsoft Word? Du är inte ensam. I många automatiseringsscenarier—tänk fakturor, kontrakt eller massrapportgenerering—behöver du ett pålitligt sätt att skapa en .docx‑fil, lägga till en form, ge den en färg och kanske även en skugga för ett polerat utseende.

I den här handledningen går vi igenom exakt det: med Aspose.Words för .NET för att **skapa Word-dokument**, **infoga rektangelform**, applicera en fyllning och **lägga till skugga**. I slutet har du en färdig‑att‑spara fil som du kan skicka vidare i vilken efterföljande arbetsflöde som helst.

Vi kommer också att beröra **hur man infogar form** på ett flexibelt sätt, och varför **hur man sätter fyllning** är viktigt för visuell konsistens. Inga onödiga detaljer, bara koden du kan kopiera‑klistra in och köra.

## Förutsättningar

- .NET 6+ (eller .NET Framework 4.7+) installerat.
- En giltig Aspose.Words för .NET-licens (eller en tillfällig utvärderingsnyckel).
- Visual Studio, Rider eller någon annan C#‑IDE du föredrar.
- Grundläggande kunskap om C#‑syntax—inget avancerat krävs.

Har du dem? Bra, låt oss börja.

## Steg 1 – Skapa Word-dokument

Det första du behöver är ett tomt dokumentobjekt. Detta är duken där allt annat lever.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` representerar .docx‑filen i minnet, medan `DocumentBuilder` ger oss ett bekvämt API för att infoga text, tabeller och former. **Att skapa Word-dokumentet** på detta sätt är omedelbart—ingen UI, ingen COM‑interop, bara ren .NET.

## Steg 2 – Infoga rektangelform

Nu när vi har ett dokument, låt oss **infoga rektangelform**. Metoden `InsertShape` tar en `ShapeType`‑enum, bredd och höjd (i punkter). Vi kommer att använda en rektangel på 150 × 80 punkter, vilket ungefär motsvarar 2 × 1 tum.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Bakom kulisserna skapar Aspose ett `Shape`‑objekt, lägger till det i det aktuella stycket och returnerar en referens som du kan formatera. Detta är kärnan i **hur man infogar form**—endast en kodrad, men otroligt kraftfull.

## Steg 3 – Hur man sätter fyllning

En form utan fyllning är osynlig på en vit sida. Låt oss ge den en behaglig ljusblå bakgrund.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Du kan också använda gradienter, texturer eller till och med en bildfyllning, men en solid färg håller exemplet enkelt. Detta visar **hur man sätter fyllning** på vilken form du än skapar, vilket säkerställer den visuella signalen dina läsare förväntar sig.

## Steg 4 – Hur man lägger till skugga

Skuggor ger djup och får formen att sticka ut. Aspose.Words exponerar ett `ShadowFormat`‑objekt där du kan slå på/av synlighet, välja färg och finjustera suddighet, avstånd och vinkel.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Varför just dessa värden? En 45°‑vinkel ger en naturlig ljuskälla från övre‑höger, en måttlig suddighet håller skuggan subtil, och ett kort avstånd förhindrar att formen ser fristående ut. Känn dig fri att experimentera—om du ändrar vinkeln till 135° faller skuggan till nedre‑vänster, till exempel.

## Steg 5 – Spara dokumentet

Allt arbete är klart; nu skriver vi filen till disk. Välj vilken sökväg du vill; se bara till att mappen finns.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

När du öppnar `ShadowShape.docx` i Microsoft Word kommer du att se en ljusblå rektangel med en mjuk grå skugga—precis som vi kodade.

## Fullt fungerande exempel

Sätter vi ihop allt får du det kompletta, kopiera‑klistra‑klara programmet:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Förväntat resultat

- En fil med namnet **ShadowShape.docx** visas i mål‑mappen.
- När du öppnar den i Word visas en ljusblå rektangel centrerad på första sidan.
- Rektangeln kastar en grå skugga i en 45°‑vinkel, vilket ger en subtil 3‑D‑effekt.

## Vanliga frågor & specialfall

**Vad händer om jag behöver en annan form?**  
Byt ut `ShapeType.Rectangle` mot något annat enum‑värde (`Ellipse`, `Star`, `Arrow` osv.). Resten av koden förblir densamma.

**Kan jag lägga till text i formen?**  
Ja—efter att ha skapat formen, anropa `shape.AppendChild(new Paragraph(doc))` och infoga sedan ett `Run` med din text. Kom ihåg att sätta `shape.TextBox`‑egenskaper om du vill ha omslag.

**Vad gäller DPI eller måttenheter?**  
Aspose arbetar i punkter (1 pt = 1/72 tum). Om du föredrar centimeter, multiplicera med 28,35 (eftersom 1 cm ≈ 28,35 pt).

**Behöver jag en licens för att detta ska fungera?**  
Utvärderingsversionen lägger till ett vattenmärke på första sidan. En riktig licens tar bort det och låser upp hela API‑et.

## Tips & fallgropar

- **Proffstips:** Anropa `builder.MoveToDocumentEnd()` innan du infogar en form om du vill ha den helt i slutet av dokumentet.
- **Se upp för:** Att spara till en skrivskyddad mapp kastar ett `UnauthorizedAccessException`. Säkerställ att din app har skrivrättigheter.
- **Prestanda‑notering:** Vid massgenerering (hundratals dokument) återanvänd en enda `Document`‑instans som mall och klona den med `doc.Clone(true)` för att undvika upprepad initieringskostnad.

## Slutsats

Du vet nu hur man **skapar Word-dokument**, **infogar rektangelform**, **sätter fyllning** och **lägger till skugga** med Aspose.Words för .NET. Kodsnutten ovan är en fristående lösning som du kan lägga in i vilket C#‑projekt som helst, oavsett om det är en konsolapp, ett webb‑API eller en bakgrundstjänst.

Från här kan du utforska:

- Att lägga till flera former med varierande färger.
- Att använda gradienter eller bildfyllningar (`shape.FillColor = ...` → `shape.FillPattern`).
- Att kombinera former med tabeller för komplexa rapportlayouter.

Prova det, justera parametrarna, och se hur dina automatiserade Word‑filer ser mer professionella ut med bara några rader kod. Lycka till med kodandet!

## Relaterade handledningar

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-02-18
description: Skapa en rektangel med Aspose.Words och lär dig hur du lägger till skugga,
  ställer in formens storlek och sparar Word-dokumentet på några minuter.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: sv
og_description: Skapa en rektangel i en Word‑fil, lär dig hur du lägger till skugga,
  ställer in formens storlek och sparar dokumentet med Aspose.Words i C#.
og_title: Skapa rektangulär form i Word – Komplett Aspose.Words-handledning
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa rektangelform i Word med Aspose.Words – Steg‑för‑steg‑guide
url: /sv/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

placeholders.

Now produce final content with all translations.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Word med Aspose.Words – Steg‑för‑steg‑guide

Har du någonsin behövt **create rectangle shape** i en Word‑fil men varit osäker på var du ska börja? Du är inte ensam—utvecklare frågar ofta, “hur lägger jag till en skugga på en form och ändå behåller dokumentet redigerbart?” I den här handledningen svarar vi på det och visar dig också **how to add shadow**, **set shape size** och **save Word document** i ett smidigt flöde.

Vi går igenom allt du behöver, från att initiera ett nytt dokument (ja, det är det första steget till **how to create document**) till att spara den slutliga *.docx*-filen på disk. Inga externa referenser, bara ett självständigt exempel som du kan kopiera‑klistra in i Visual Studio och köra idag.

---

## Förutsättningar

- .NET 6+ (eller .NET Framework 4.7+). Aspose.Words fungerar med alla moderna .NET‑runtime.
- En giltig Aspose.Words‑licens (eller den kostnadsfria utvärderingsnyckeln) – annars ser du ett vattenmärke.
- Visual Studio, Rider eller någon C#‑redigerare du föredrar.
- Grundläggande C#‑kunskaper—inget avancerat, bara förmågan att köra en konsolapp.

> **Proffstips:** Om du använder en Mac körs samma kod under .NET 6 med VS Code—se bara till att du refererar `Aspose.Words`‑NuGet‑paketet.

## Steg 1: Initiera dokumentet – grunden för **how to create document**

Innan vi kan rita något behöver vi en tom duk. Aspose.Words kallar detta för en `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Varför detta är viktigt:** `Document`‑objektet representerar hela *.docx*-filen. Alla former, stycken och sektioner du lägger till blir barn till detta objekt. Att börja med ett rent dokument säkerställer att inga dolda stilar stör din rektangel.

## Steg 2: Definiera rektangeln och **set shape size**

En rektangel är bara en `Shape` med `ShapeType.Rectangle`. Vi ger den explicita dimensioner så att den ser exakt ut som avsett.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Vad siffrorna betyder:** Aspose.Words använder punkter (1 pt = 1/72 in). Justera värdena för att passa din layout; för en vanlig A4‑sida är 200 pt en bekväm bredd.

## Steg 3: **How to add shadow** – får formen att sticka ut

Skuggor ger en visuell ledtråd att formen är “lyft” från sidan. `Shadow`‑egenskapen låter dig justera färg, avstånd, transparens och oskärpa.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Varför använda transparens?** En helt ogenomskinlig skugga kan se hård ut. Att sätta den till 0,4 gör effekten subtil och professionell.

## Steg 4: Positionera rektangeln – inline‑flöde med omgivande text

Om du vill att formen ska bete sig som ett tecken i ett stycke, sätt dess `WrapType` till `Inline`. Detta håller layouten förutsägbar, särskilt när dokumentet redigeras senare.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Särskilt fall:** Om du behöver att rektangeln flyter över text (t.ex. ett vattenmärke), ändra `WrapType` till `Square` eller `BehindText`.

## Steg 5: Infoga formen i dokumentkroppen

Nu placerar vi faktiskt rektangeln i det första stycket. Om dokumentet ännu inte har något innehåll skapas `FirstParagraph` automatiskt.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Tips:** Du kan också skapa ett nytt stycke först och sedan lägga till formen—användbart när du behöver omgivande text.

## Steg 6: **Save Word document** – sista steget

När allt är på plats är sparandet av filen en enkel rad. Välj vilken sökväg du vill; exemplet använder en platshållare som du bör ersätta med din egen katalog.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Resultat:** Öppna den genererade *.docx* i Microsoft Word. Du kommer att se en svartskuggad rektangel, 200 pt bred och 100 pt hög, placerad inline med det första stycket.

## Förväntat resultat

När du öppnar **ShadowShape.docx**, visar dokumentet:

- Ett enda stycke som innehåller en rektangulär form.
- Rektangeln har en subtil svart skugga förskjuten med 5 pt.
- Formens storlek matchar dimensionerna som angavs i Steg 2.
- Ingen extra text visas om du inte lägger till den manuellt.

Om formen inte visas, dubbelkolla att du har refererat rätt version av Aspose.Words och att din licens (eller provperiod) är aktiv.

## Vanliga frågor & variationer

| Question | Answer |
|----------|--------|
| *Can I change the shadow color to something other than black?* | Absolut—sätt `rectangleShape.Shadow.Color = Color.Blue;` eller någon `System.Drawing.Color`. |
| *What if I need a larger rectangle?* | Justera `Width`‑ och `Height`‑värdena. Kom ihåg att de är i punkter; 72 pt = 1 in. |
| *Is it possible to place the shape at an absolute position?* | Ja—använd `WrapType = WrapType.Absolute` och sätt `Top`/`Left`‑egenskaperna. |
| *Does this work with .NET Core?* | Det gör det. Aspose.Words är plattformsoberoende; installera bara NuGet‑paketet för .NET Standard. |
| *Can I add text inside the rectangle?* | Inte direkt; du måste infoga en `TextBox`‑form istället för en vanlig rektangel. |

## Fullt fungerande exempel (Klar att kopiera‑klistra in)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Kör programmet, navigera till `C:\Temp\ShadowShape.docx`, och du kommer att se rektangeln med en skugga exakt som beskrivet.

## Slutsats

Du vet nu hur du **create rectangle shape** i en Word‑fil med Aspose.Words, hur du **set shape size**, **add shadow**, och slutligen **save Word document** med ändringarna. Hela processen—från **how to create document** till att spara resultatet—ryms i några få rader C# och kan utökas för mer komplexa layouter.

Redo för nästa utmaning? Prova att byta rektangeln mot en form med rundade hörn, experimentera med olika skuggfärger, eller bädda in formen i en tabellcell. Varje justering förstärker samma grundläggande koncept som vi gick igenom här.

Om du fann den här guiden hjälpsam, dela den, lämna en kommentar med dina egna variationer, eller utforska våra andra handledningar om Word‑automatisering, som att infoga bilder eller generera tabeller med Aspose.Words. Lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
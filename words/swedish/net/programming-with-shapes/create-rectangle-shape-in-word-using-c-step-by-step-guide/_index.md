---
category: general
date: 2026-01-03
description: Skapa en rektangelform i Word med C# och lägg till skugga på formen.
  Lär dig hur du infogar en form i Word, lägger till skugga på formen och genererar
  Word‑dokument programatiskt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: sv
og_description: Skapa en rektangelform i Word med C# och lägg till skugga på formen.
  Följ den här guiden för att infoga en form i Word, konfigurera skuggor och generera
  dokument programatiskt.
og_title: Skapa rektangel i Word med C# – Komplett handledning
tags:
- C#
- Word Automation
- Aspose.Words
title: Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide
url: /sv/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Word med C# – Komplett handledning

Har du någonsin behövt **create rectangle shape** i ett Word‑dokument men varit osäker på var du ska börja? Du är inte ensam—många utvecklare stöter på samma problem när de vill **add shadow to shape** för ett polerat utseende. I den här handledningen går vi igenom de exakta stegen för att **insert shape in Word**, applicera en subtil skugga och slutligen **c# generate word document**‑filer som du kan leverera till användare.

Vi täcker allt från att sätta upp projektet till att finjustera skugg‑egenskaper, och vi avslutar med ett färdigt kodexempel som kan köras direkt. Ingen onödig text, bara de praktiska delarna som får jobbet gjort.

## Vad du kommer att lära dig

- Hur man **create rectangle shape** med Aspose.Words (eller Open XML) i C#
- De exakta egenskaperna du behöver för att **add shadow to shape** för djup
- Var du placerar formen med `DocumentBuilder`
- Hur du sparar filen så att den öppnas korrekt i Microsoft Word
- Tips, fallgropar och variationer för verkliga scenarier

### Förutsättningar

- .NET 6.0 eller senare (koden fungerar på .NET Core och .NET Framework)
- Ett NuGet‑paket som kan manipulera Word‑filer – vi använder **Aspose.Words for .NET** eftersom dess API är koncist. Om du föredrar Open XML SDK är koncepten desamma, bara klasserna skiljer sig.
- Visual Studio, VS Code eller någon C#‑IDE du föredrar

> **Pro tip:** Om du har en begränsad budget erbjuder Aspose en gratis provperiod som är perfekt för lärande. Byt bara ut licensraden mot en kommentar när du testar.

## Steg 1: Installera Word‑bearbetningsbiblioteket

Först, lägg till biblioteket i ditt projekt. Öppna en terminal i din lösningsmapp och kör:

```bash
dotnet add package Aspose.Words
```

Om du använder Open XML SDK skulle kommandot vara `dotnet add package DocumentFormat.OpenXml`. Resten av guiden förutsätter Aspose.Words, men att byta API‑anrop är enkelt.

## Steg 2: Skapa ett nytt tomt dokument

Nu när biblioteket är klart kan vi **create rectangle shape** genom att börja med ett rent `Document`‑objekt. Tänk på detta som en tom canvas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` ger oss ett hög‑nivå sätt att infoga innehåll utan att dyka ner i lågnivå‑nodträd.

## Steg 3: Infoga rektangelformen

Med byggaren i handen kan vi **insert shape in Word**. Metoden `InsertShape` tar formtypen och dess dimensioner (bredd, höjd) i punkter.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Vid den här punkten visas rektangeln i dokumentet, men den ser lite platt ut. Där kommer nästa steg in.

## Steg 4: Lägg till skugga på formen

Skuggor ger formen en känsla av djup. `Shadow`‑objektet låter oss finjustera suddighet, avstånd, vinkel, färg och transparens. Nedan är en komplett konfiguration som fungerar bra för de flesta rapporter.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Varför dessa värden?**  
- **BlurRadius** på `5.0` håller kanten mjuk utan att se suddig ut.  
- **Distance** på `4.0` förskjuter skuggan lagom för att vara märkbar.  
- **Angle** `45` efterliknar naturligt ljus från övre vänstra hörnet, en vanlig UI‑konvention.  
- **Transparency** `0.3` förhindrar att skuggan dominerar formens fyllning.

Om du behöver en mer dramatisk effekt, öka `BlurRadius` och sänk `Transparency`. För en subtil, nästan osynlig lyftning, vänd på dessa siffror.

## Steg 5: Spara dokumentet

Till sist, skriv filen till disk. Metoden `Save` upptäcker formatet från filändelsen, så `.docx` ger dig det moderna Word‑formatet.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Öppna `ShadowRectangle.docx` i Microsoft Word, så ser du en skarp rektangel med en mjuk skugga—precis vad du ville ha när du frågade “**how to add shape**” med en professionell finish.

![Skapa rektangelform med skugga i Word](placeholder-image.png "Skapa rektangelform med skugga i Word")

*Bildtext: skapa rektangelform med skugga i Word*

## Fullt fungerande exempel

När vi sätter ihop allt, här är det kompletta, körklara programmet. Kopiera‑klistra in i en konsolapp och tryck **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Förväntat resultat

- Den genererade `ShadowRectangle.docx` innehåller **en rektangelform** centrerad där markören var placerad.  
- Rektangeln visar en **mjuk, 30 % transparent svart skugga** förskjuten med en 45°‑vinkel.  
- Ingen annan innehåll läggs till, vilket håller filen lättviktig och enkel att bädda in i större rapporter.

## Vanliga frågor & specialfall

### Vad om jag behöver en annan form?

Byt `ShapeType.Rectangle` mot någon annan `ShapeType`‑enum‑värde (t.ex. `Ellipse`, `Triangle`). Skugg‑API:t fungerar på samma sätt, så du kan återanvända konfigurationen.

### Hur ändrar jag fyllningsfärgen?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Kan jag lägga till formen i ett specifikt stycke?

Ja. Flytta `DocumentBuilder` till målstycket med `builder.MoveToParagraph(index)` innan du anropar `InsertShape`. Detta säkerställer att formen visas exakt där du behöver den.

### Vad sägs om äldre Word‑format (.doc)?

Byt bara filändelsen:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

Skugg‑funktionen stöds i Word 2003 och senare, så du kommer fortfarande att se effekten.

### Använda Open XML SDK istället för Aspose?

Stegen är desamma: skapa ett `WordprocessingDocument`, lägg till ett `Drawing`‑element, sätt `<a:shadow>`‑egenskaper. XML‑koden är mer utförlig, men samma koncept (storlek, suddighet, avstånd, vinkel) gäller.

## Tips för att undvika fallgropar

- **Glöm inte licensen** om du använder en betald Aspose‑version; annars får du ett vattenmärke.  
- **Enheter är punkter**, inte pixlar. En typisk skärm‑pixel ≈ 0.75 pt, så justera dimensionerna därefter.  
- **Skugg‑egenskaper ignoreras** om formens `WrapType` är satt till `Inline`. Använd `WrapType = WrapType.Square` för flytande former som respekterar skugg‑rendering.  
- **Spara till en nätverksdelning** kan kräva rätt behörigheter; testa alltid sökvägen först.

## Slutsats

Du vet nu hur du **create rectangle shape** i ett Word‑dokument med C#, **add shadow to shape**, och **c# generate word document**‑filer som ser polerade ut direkt. De grundläggande stegen—installera biblioteket, skapa `Document`, infoga formen, konfigurera skuggan och spara—är enkla att komma ihåg och kan anpassas till andra former, färger eller till och med dynamiska data.

Vad blir nästa steg? Prova att lagerlägga flera former, bädda in bilder eller generera en fullständig rapport med tabeller och diagram. Du kan också utforska villkorlig formatering—ändra skugg‑intensiteten baserat på datavärden—för att göra dina dokument inte bara funktionella utan även visuellt tilltalande.

Känn dig fri att experimentera, och om du stöter på problem, lämna en kommentar nedan. Lycka till med kodandet, och må dina Word‑dokument alltid ha den perfekta skugg‑effekten!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-04-10
description: hur du sätter skugga på en form i C# – lär dig hur du applicerar kastskugga,
  ändrar transparens, justerar oskärpa och lägger till formskugga med Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: sv
og_description: hur man sätter skugga på en form i C# – den här handledningen visar
  hur man applicerar en kastskugga, ändrar transparens, justerar oskärpa och lägger
  till formskugga med tydliga kodexempel.
og_title: hur man sätter skugga på en form i C# – Komplett guide
tags:
- Aspose.Words
- C#
- Document Automation
title: hur man sätter skugga på en form i C# – steg‑för‑steg‑guide
url: /sv/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hur man lägger till skugga på en form i C# – Komplett guide

Har du någonsin undrat **hur man lägger till skugga** på en form när du programatiskt bygger ett Word‑dokument? Du är inte ensam. Många utvecklare stöter på problem när de behöver en subtil drop‑shadow för en textruta, en logotyp eller en call‑out‑ruta, och API‑dokumentationen känns lite tunn.  

I den här handledningen går vi igenom hela processen: från att ladda en `.docx`, hämta den första `Shape`, till att applicera en drop shadow, justera dess transparens, justera blur‑radien och slutligen placera den exakt rätt. I slutet har du ett återanvändbart kodsnutt som fungerar med Aspose.Words .NET 2023 eller senare, och du förstår *varför* varje egenskap är viktig.

## Vad du behöver

- **Aspose.Words for .NET** (NuGet‑paket `Aspose.Words`) – biblioteket som ger oss klasserna `Document`, `Shape` och `ShadowFormat`.  
- **.NET 6+** (eller .NET Framework 4.7.2) – någon modern runtime räcker.  
- En enkel Word‑fil (`input.docx`) som redan innehåller minst en form, till exempel en textruta.  
- Visual Studio, VS Code eller din favoriteditor.

Det är allt. Inga extra tredjepartsverktyg, ingen COM‑interop, bara ren C#.

![how to set shadow example](image-placeholder.png){:alt="hur man lägger till skugga på en form i ett Word-dokument"}

## Så här ställer du in skugga – Översikt

Kärnidén bakom **hur man lägger till skugga** är att manipulera `ShadowFormat`‑objektet som finns på en `Shape`. Tänk på `ShadowFormat` som ett litet “style sheet” för själva skuggan: det talar om för renderaren om skuggan är synlig, vilken färg den ska ha, hur transparent den är, hur suddig den är och var den sitter i förhållande till formen.  

Nedan är det *kompletta* körbara programmet. Kopiera‑klistra gärna in det i en konsolapp, tryck **F5**, och se skuggan dyka upp i den sparade `output.docx`.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Varför dessa inställningar är viktiga

- **Visible** – Utan att slå på den här flaggan ignoreras alla andra egenskaper.  
- **Color** – En mörkgrå färg efterliknar en typisk UI‑drop shadow; du kan byta till vilken `Color` som helst.  
- **Transparency** – 0,3 ger ett *mjukt* utseende samtidigt som formen förblir läsbar.  
- **Size** – Styr blur; ett värde på 6 är vanligtvis tillräckligt för ett professionellt intryck.  
- **Distance & Angle** – Tillsammans definierar de *offset*; 2 pt vid 45° ger en subtil diagonal skugga.

Det är kärnan i **hur man lägger till skugga**. Nästa steg bryter ner varje del så att du kan **applicera drop shadow**, **ändra transparens**, **justera blur** och **lägga till formskugga** isolerat.

---

## Applicera drop shadow på en form

När folk frågar “hur gör jag **apply drop shadow** i C#?” så behöver de ofta bara synlighets‑växeln och en färg. Följande kodsnutt isolerar just de två raderna:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Om du riktar dig mot äldre Word‑versioner (2003‑2007), håll dig till standardfärger. Vissa exotiska ARGB‑värden kan ignoreras av den äldre renderaren.

---

## Hur man ändrar transparens för skuggan

Transparens uttrycks som ett **float mellan 0 och 1**. Ett värde på **0** betyder en helt ogenomskinlig skugga; **1** gör den osynlig. De flesta designers siktar på **0,2‑0,4** för ett naturligt utseende.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Särskilda fall

- **Negative values** – Aspose.Words kommer att klämma dem till 0, men det är bättre att validera indata.  
- **Values > 1** – Kläms till 1, vilket i praktiken döljer skuggan.  

Om du behöver låta användare välja en procentandel, konvertera den först:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Hur man justerar blur (storlek) för skuggan

**Size**‑egenskapen styr blur‑radien. Större tal ger en mjukare, mer diffust skugga. Den mäts i points (pt), inte pixlar.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### När man använder liten vs. stor blur

- **Small blur (2‑4 pt)** – Bra för UI‑stil‑callouts där du vill ha en skarp kant.  
- **Large blur (8‑12 pt)** – Fungerar väl för utskrivna rapporter eller när formen ligger långt från bakgrunden.

---

## Lägg till formskugga – Positionering och riktning

Den sista delen av **lägga till formskugga** är offseten. Två egenskaper arbetar tillsammans:

| Egenskap | Betydelse |
|----------|-----------|
| **Distance** | Hur långt skuggan sitter från formen (i punkter). |
| **Angle**    | Riktning för offseten (0° = höger, 90° = ner, 180° = vänster, 270° = upp). |

Exempel som skapar en subtil ned‑höger‑skugga:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Du kan experimentera med vinklar för att simulera ljus som kommer från olika källor. Ett vanligt knep är att låta användaren välja en “ljuskälla” från en dropdown‑lista och mappa den till ett vinkelvärde.

---

## Fullt fungerande exempel (alla steg kombinerade)

Nedan är samma program som tidigare, men med **extra kommentarer** som gör logiken kristallklar. Kopiera detta till `Program.cs` och kör det; utdatafilen kommer att innehålla en textruta med en perfekt avstämd skugga.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Expected result:** Öppna `output.docx`. Den första textrutan kommer att visa en mörkgrå, 30 % transparent skugga som är lätt suddig (size = 6) och har ett offset på 2 pt vid 45° vinkel. Effekten är subtil men märkbar – exakt vad de flesta UI‑designers siktar på.

---

## Vanliga frågor & fallgropar

- **“Does this work with images as well?”**  
  Ja. Alla `Shape`—oavsett om det är en textruta, bild eller auto‑shape—exponerar `ShadowFormat`. Byt bara ut logiken för att hämta formen mot rätt index eller namn.

- **“What if the document has multiple shapes?”**  
  Loopa igenom `doc.GetChildNodes(NodeType.Shape, true)` och applicera samma inställningar på varje. Du kan också filtrera på `shape.Name` eller `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
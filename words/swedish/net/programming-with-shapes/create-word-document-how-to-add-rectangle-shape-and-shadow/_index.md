---
category: general
date: 2026-03-19
description: Skapa ett Word‑dokument i C# med Aspose.Words, lär dig hur du lägger
  till en form, lägger till en rektangel, applicerar skugga och sparar dokumentet
  som docx på några minuter.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: sv
og_description: Skapa ett Word‑dokument med Aspose.Words, lägg till en rektangelform,
  applicera yttre skugga och spara dokumentet som docx. Steg‑för‑steg‑guide.
og_title: Skapa Word-dokument – Lägg till rektangelform och skugga
tags:
- Aspose.Words
- C#
- Document Automation
title: Skapa Word-dokument – Hur man lägger till en rektangel och skugga
url: /sv/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word-dokument – Hur man lägger till rektangelform och skugga

Har du någonsin behövt **create word document** programatiskt och undrat var du ska börja? Du är inte ensam. Många utvecklare stöter på samma hinder när de för första gången försöker generera en .docx‑fil som innehåller anpassad grafik. I den här handledningen går vi igenom hela processen – hur man lägger till en form, specifikt en **add rectangle shape**, ger den en stilfull **add shadow to shape**, och slutligen **save document as docx**.  

I slutet av guiden har du ett färdigt C#‑snutt som du kan klistra in i vilket .NET‑projekt som helst. Inga vaga referenser, bara ett komplett, körbart exempel.  

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Framework).  
- Aspose.Words för .NET installerat (NuGet‑paketet `Aspose.Words`).  
- En grundläggande förståelse för C#‑syntax – inget avancerat krävs.  

Om du saknar biblioteket, kör:

```bash
dotnet add package Aspose.Words
```

Det är allt—inga extra SDK:er, ingen COM‑interop, bara en enda NuGet‑referens.

---

## Steg 1: Skapa ett Word-dokument (Primärt mål)

Det första vi behöver är en ren canvas. Tänk på `Document`‑klassen som en ny sida i Microsoft Word; den innehåller sektioner, stycken och allt annat du kommer att lägga till senare.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Varför börja med ett tomt `Document`? För att det garanterar att ingen dold formatering smyger in från en mall. Enligt min erfarenhet undviker man mystiska layoutförändringar när man senare infogar former genom att börja från början.

---

## Steg 2: Infoga en rektangelform – Lägg till det visuella elementet

Nu när vi har ett dokument, låt oss **add rectangle shape** till det första stycket. `Shape`‑objektet är mångsidigt; du kan välja `ShapeType.Rectangle`, `Ellipse` eller till och med egna ritningar. Här är den minsta koden:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Vad händer under huven?**  
- `ShapeType.Rectangle` talar om för Aspose att vi vill ha en enkel ruta.  
- `WrapType.Inline` säkerställer att rektangeln rör sig med textflödet, vilket vanligtvis är vad du förväntar dig i ett ordbehandlingsscenario.  
- Genom att lägga till i `FirstParagraph` undviker vi att manuellt infoga ett nytt stycke; Aspose skapar ett åt oss om dokumentet verkligen är tomt.  

> **Proffstips:** Om du behöver att formen ska ligga *bakom* texten, byt `WrapType` till `WrapType.Transparent`. Den lilla förändringen kan göra en enorm visuell skillnad.

---

## Steg 3: Tillämpa en yttre skugga – Förbättra utseendet

En platt rektangel är… ja, platt. Att lägga till en **add shadow to shape** ger den djup utan extra bilder. Asposes `ShadowFormat` gör detta till en endaste rad.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Varför bry sig om just de specifika värdena?  
- **Blur** på `5.0` ger en subtil fjäderkant som ser professionell ut på de flesta skärmar.  
- **Distance** på `3.0` och **Angle** på `45` skapar en naturlig ljuskälla från övre vänstra hörnet, en vanlig designkonvention.  
- **Color.Gray** fungerar både i ljusa och mörka teman; du kan byta ut den mot `Color.Black` om du behöver starkare kontrast.  

Om du någonsin behöver en *inre* skugga (tänk på en nedsänkt knapp), byt bara `ShadowType.OuterShadow` till `ShadowType.InnerShadow`. Samma egenskaper gäller fortfarande.

---

## Steg 4: Spara dokumentet som DOCX – Spara ditt arbete

Allt det roliga är bra, men så småningom vill du ha en fil på disken. Steget **save document as docx** är enkelt:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Ett par kommentarer:  
- `SaveFormat.Docx`‑enumet garanterar det moderna Office Open XML‑formatet, som är kompatibelt med Word 2007+.  
- Om du behöver strömma filen direkt till ett webbsvar, ersätt filsökvägen med en `MemoryStream` och skriv den till HTTP‑svaret.  

Efter att ha kört koden, öppna `ShadowedRectangle.docx` i Microsoft Word. Du bör se en grå rektangel med en mjuk skugga, placerad inline med det första stycket – exakt det vi ville uppnå.

---

## Hur man lägger till form – Alternativa tillvägagångssätt

Exemplet ovan använder *inline*-metoden, men ibland vill du ha en form som flyter över texten. Det är då **how to add shape** med olika omslag blir relevant.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Här bytte vi `WrapType` till `Square` och centrerade formen på sidan. Detta mönster är användbart för framsidor eller dekorativa bannrar. Kom ihåg: flytande former ökar filstorleken något eftersom Word lagrar extra placeringsdata.

---

## Förväntat resultat & verifiering

När du öppnar den genererade filen bör du se:

- Ett enda stycke som innehåller en grå rektangel.  
- Rektangeln är ungefär 2,8 × 1,4 tum.  
- En subtil yttre skugga förskjuten mot nedre högra hörnet.  

Om formen visas *utanför* stycket, dubbelkolla `WrapType`. Om skuggan ser för hård ut, sänk `Blur`‑värdet eller byt `Color` till en ljusare nyans.

---

## Vanliga fallgropar & hur man undviker dem

| Problem | Varför det händer | Lösning |
|-------|----------------|-----|
| Form försvinner efter sparning | `WrapType` set to `Inline` but paragraph was removed | Ensure the paragraph exists; use `doc.FirstSection.Body.FirstParagraph` to guarantee it. |
| Skugga ser pixelerad ut | Using a very low `Blur` value | Increase `Blur` to at least `3.0` for smooth edges. |
| Filstorleken ökar kraftigt | Adding many high‑resolution images alongside shapes | Use `doc.RemoveUnusedResources()` before saving if you added images. |
| Färgen visas inte i mörkt läge | Using a dark `Color` for the shape itself | Choose a contrasting color (e.g., `Color.White`) for better visibility. |

---

## Fullständigt fungerande exempel

Nedan är den kompletta, kopiera‑och‑klistra‑klara koden som innehåller allt vi har gått igenom. Känn dig fri att köra den som en konsolapp.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Förklaring av varje block** finns inline som kommentarer, vilket tillfredsställer både SEO‑läsare och AI‑assistenter som älskar självständiga svar.

---

## Slutsats

Vi har precis **create word document** från grunden, lärt oss **how to add shape**, specifikt en **add rectangle shape**, gett den en **add shadow to shape**, och slutligen **save document as docx**. Stegen är enkla, koden är kompakt, och resultatet ser polerat ut.  

Om du är redo att gå vidare, prova att byta ut rektangeln mot en egen bild, experimentera med olika skuggfärger, eller generera en hel rapport med flera formade sektioner. Aspose.Words‑API:et är tillräckligt flexibelt för att hantera allt från fakturor till marknadsföringsbroschyrer.

Har du frågor om andra formtyper eller behöver hjälp med att integrera detta i en ASP.NET Core‑tjänst? Lägg en kommentar nedan, och lycka till med kodandet! 

![skapa word-dokument med rektangelform och skugga](placeholder-image.png "skapa word-dokument med rektangelform och skugga

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
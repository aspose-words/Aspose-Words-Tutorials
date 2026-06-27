---
category: general
date: 2026-06-27
description: Ändra teckensnittsstil i Word‑dokument med C#. Lär dig hur du ställer
  in teckensnittsvikt, anger fet stil och justerar teckensnittets bredd för exakt
  typografi.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: sv
og_description: Ändra teckensnittsstil i Word‑dokument med C#. Upptäck hur du ställer
  in teckensnittsvikt, sätter fet vikt och justerar teckensnittsbredd i några enkla
  steg.
og_title: Ändra teckensnittsstil i Word-dokument – Komplett C#-guide
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: Ändra teckensnittsstil i Word‑dokument – Komplett C#‑guide
url: /sv/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ändra teckensnittsstil i Word‑dokument – Komplett C#‑guide

Har du någonsin behövt **ändra teckensnittsstil** i en Word‑fil men varit osäker på vilket API‑anrop som faktiskt gör jobbet? Du är inte ensam – de flesta utvecklare stöter på den muren när de första gången försöker programmera typografi.  

Det goda nyheten är att med några få rader C# kan du **ange teckensnittsvikt**, till och med öka till en fet vikt, och finjustera bredden på varje glyf. I den här handledningen går vi igenom ett komplett, körbart exempel som modifierar en `.docx`‑fil från början till slut.

## Vad den här guiden täcker

Vi börjar med att ladda ett befintligt dokument, sedan skapar vi ett `FontSettings`‑objekt som innehåller en `FontVariation`. Därefter **anger vi teckensnittsvikt**, **anger fet vikt**, och **justerar teckensnittsbredde** innan vi slutligen tillämpar ändringarna och sparar resultatet. Inga externa konfigurationsfiler, inga magiska strängar – bara ren C# och Aspose.Words‑biblioteket. När du är klar kan du **modifiera teckensnitt i Word**‑dokument med självförtroende, oavsett om du bygger en rapportgenerator eller ett verktyg för massformattering.

### Förutsättningar

- .NET 6.0 eller senare (koden kompileras även på .NET Core)  
- Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`)  
- En exempel‑`input.docx` placerad i en mapp du kan referera till (vi kallar den `YOUR_DIRECTORY`)  

Om du har dessa grunder på plats, låt oss dyka ner.

---

## Steg 1: Ändra teckensnittsstil – Ladda Word‑dokumentet

Det första du behöver göra är att läsa in målfilen i minnet. Tänk på det som att öppna en tom duk där du senare målar din nya typografi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **Proffstips:** Om du kör detta på en server utan UI, se till att Aspose.Words‑licensen antingen är satt till en provversion eller att du har applicerat en korrekt licensfil för att undvika vattenstämpelmeddelanden.

---

## Steg 2: Ange teckensnittsvikt och ange fet vikt

Nu när dokumentet är i minnet skapar vi en `FontSettings`‑behållare. Detta objekt är porten till varje teckensnittsnivå‑justering du kan göra.  

Klassen `FontVariation` låter dig specificera tre grundläggande attribut:

| Property | Vad den gör | Typiskt intervall |
|----------|--------------|-------------------|
| `Weight` | Styr hur tung glyfen framstår. Värdet **700** är standard‑“bold”. | 100‑900 |
| `Width`  | Sträcker eller komprimerar glyfen horisontellt. **100** betyder normal bredd. | 50‑200 |
| `Slant`  | Lägger till en lutning liknande kursiv. Positiva tal lutar åt höger. | -90‑90 |

Nedan **anger vi teckensnittsvikt** till 700 (bold) och visar också hur du kan höja den ännu mer om ditt teckensnitt stödjer en “extra‑bold” stil.

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **Varför det är viktigt:** Att ange **set bold weight** direkt via `SetWeight` kringgår behovet av ett separat “Bold”‑stilsobjekt, vilket ger dig pixel‑perfekt kontroll över hur tjocka strecken blir.

---

## Steg 3: Justera teckensnittsbredde

Om du någonsin behövt göra ett teckensnitt tajtare för en rubrik eller mer rymligt för ett stycke, kommer du att uppskatta detta steg. `Width`‑egenskapen gör exakt det.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **Vanligt fallgropp:** Inte alla typsnitt respekterar breddvariationer. Om du inte ser någon visuell förändring, kontrollera att den teckensnittsfamilj du använder stödjer kondenserade/expanderade glyfer.

---

## Steg 4: Tillämpa teckensnittinställningarna – Modifiera teckensnitt i Word

Med vårt `FontSettings`‑objekt fullt konfigurerat är nästa steg att tala om för dokumentet att använda dem. Här **modifierar vi teckensnitt i Word** på dokumentnivå, vilket påverkar varje text‑run som ärver standardstilen.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

Om du bara vill rikta in dig på ett specifikt stycke eller en specifik run, kan du hämta den noden och sätta dess `FontSettings` individuellt. Exemplet ovan demonstrerar den breda metoden, vilket är perfekt för mass‑formattering.

---

## Steg 5: Spara och verifiera ändringarna

Sparandet är den sista, men definitivt inte minst, delen av arbetsflödet. Efter att filen har skrivits kan du öppna den i Microsoft Word för att se den nya stilen i aktion.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Förväntat resultat

- All brödtext som tidigare använde standardteckensnittet visas nu **fet** (vikt 700).  
- Om du experimenterade med `SetWidth(80)`, kommer tecknen att se lite tajtare ut; `SetWidth(120)` sprider dem.  
- Inget annat innehåll (bilder, tabeller osv.) ändras – endast teckensnittsegenskaperna för text‑runs påverkas.

Öppna `output.docx` i Word, markera ett stycke och kontrollera **Font**‑dialogen. Du kommer att se att **Bold**‑rutan är ikryssad och **Scale** (bredd) visar det värde du valde.

---

## Vanliga frågor & kantfall

### Kan jag ändra teckensnittsfamiljen samtidigt?

Absolut. Efter att du har satt `FontVariation` kan du också tilldela en ny `FontInfo` till `FontSettings`:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### Vad händer om jag bara vill **ange fet vikt** för rubriker?

Hämta rubrikstils‑noden och applicera en separat `FontSettings`‑instans:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### Fungerar detta med .NET Core på Linux?

Ja – Aspose.Words är plattformsoberoende. Se bara till att du har de nödvändiga runtime‑biblioteken installerade (`libgdiplus` på vissa distributioner) om du planerar att rendera dokumentet till PDF senare.

---

## Slutsats

Vi har just **ändrat teckensnittsstil** i ett Word‑dokument från början till slut, och gått igenom hur man **anger teckensnittsvikt**, **anger fet vikt**, och **justerar teckensnittsbredde** med C#. Det kompletta, körbara exemplet visar varje nödvändig import, objekt‑skapande och metodanrop, så att du kan kopiera‑klistra in det i ditt eget projekt och se typografin förändras omedelbart.

Nu när du vet hur du **modifierar teckensnitt i Word**, kan du utforska relaterade ämnen som **inbäddning av anpassade teckensnitt**, **applicering av färggradienter**, eller **skapande av dynamiska tabeller**. Alla dessa bygger på samma `FontSettings`‑grund som vi använde här, så du ligger redan ett steg före.

Har du ett scenario som inte täcks? Lämna en kommentar så dyker vi djupare tillsammans. Lycka till med kodandet – och må dina dokument alltid se exakt ut som du tänkt dig!  

![change font style example](placeholder.png){alt="exempel på ändring av teckensnittsstil"}

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Set Font Emphasis Mark](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Set Font Fallback Settings](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Set Font Formatting](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
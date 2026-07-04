---
category: general
date: 2026-06-02
description: Lär dig hur du använder ett variabelt vikttyp‑typsnitt i C# och ställer
  in teckensnittsvikten programatiskt samtidigt som du ändrar kod för teckensnittsstretch
  för dynamisk typografi.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: sv
og_description: Använd variabelvikt‑typsnitt i C# för att programatiskt ställa in
  teckensnittsvikt och ändra kod för teckensnittsstretch, vilket möjliggör dynamisk
  typografi i dina dokument.
og_title: Använd variabelvikt‑typsnitt i C# – Fullständig guide
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Använd variabelvikt‑typsnitt i C# – Komplett programmeringsguide
url: /sv/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Använd variabelviktigt typsnitt i C# – Komplett programmeringsguide

Har du någonsin behövt **använda variabelviktigt typsnitt** i ett .NET‑projekt men varit osäker på hur du får vikten och stretch att svara på användarens inmatning? Du är inte ensam. I många UI‑ eller rapporteringsscenarier vill du att texten ska anpassas – kanske en lätt rubrik som blir fet vid hovring, eller ett stycke som breddas för betoning. Den goda nyheten är att du med Aspose.Words kan **sätta teckensnittsvikt programatiskt** och även **ändra teckensnittsstretch‑kod** i farten.

I den här handledningen går vi igenom ett praktiskt exempel som visar exakt hur du laddar ett variabelviktigt typsnitt, applicerar en anpassad vikt och justerar stretch‑inställningen – allt med tydlig C#‑kod som du kan kopiera och klistra in. I slutet har du ett körbart konsolprogram som producerar en PDF som demonstrerar effekten.

---

## Vad du behöver

- **Aspose.Words for .NET** (v23.12 eller senare). Biblioteket levereras med fullt stöd för variabelviktiga typsnitt.
- En mapp som innehåller minst ett variabelviktigt typsnitt, t.ex. *RobotoFlex‑Variable.ttf*. Du kan ladda ner det från Google Fonts.
- .NET 6 SDK (eller någon nyare .NET‑version) och en IDE du föredrar.
- Grundläggande kunskaper i C# – inget avancerat, bara några rader kod.

Det är allt. Inga extra NuGet‑paket utöver Aspose.Words och inga kryptiska konfigurationsfiler.

---

![Use variable weight font example](https://example.com/variable-weight-sample.png "Use variable weight font demonstration")

*Alt text: skärmdump som visar användning av variabelviktigt typsnitt i ett genererat PDF-dokument.*

---

## Steg 1: Ställ in FontSettings och peka på din teckensnittsmapp  

Först och främst – Aspose.Words måste veta var dina variabelviktiga teckensnitt finns. Det gör du genom att skapa ett `FontSettings`‑objekt och bifoga en `FolderFontSource`. Flaggan `true` talar om för motorn att även söka i undermappar, vilket är praktiskt om du har flera teckensnittsfamiljer samlade.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Varför detta är viktigt:** Utan att registrera mappen faller Aspose.Words tillbaka på systemteckensnitt och ignorerar den variabelviktiga data som är inbäddad i ditt anpassade teckensnitt. Detta steg är grunden för allt som följer.

---

## Steg 2: Bifoga FontSettings till dokumentet  

Nu skapar vi ett nytt `Document` (eller laddar ett befintligt) och talar om för det att använda de `FontSettings` vi just förberett. Denna bindning gör de variabelviktiga data tillgängliga för varje `Run` vi lägger till senare.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Om du redan har en mall – säg en Word‑fil med platshållare – kan du ersätta `new Document()` med `new Document("Template.docx")`. Samma `FontSettings` kommer att gälla.

---

## Steg 3: Lägg till ett Run‑textstycke som ska använda det variabelviktiga typsnittet  

Ett **Run** är den minsta enheten för textformatering i Aspose.Words. Vi skapar ett, sätter in det i ett nytt stycke och ändrar sedan dess teckensnittsegenskaper.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Vid detta tillfälle renderas texten med standardtypsnittet (vanligtvis Times New Roman). Magin händer när vi tilldelar den variabelviktiga familjen.

---

## Steg 4: Välj den variabelviktiga teckensnittsfamiljen  

Här använder vi faktiskt **variabelviktigt typsnitt**. Sätt `Font.Name` till exakt familjenamn som definieras i teckensnittsfilen. För Roboto Flex är namnet `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Om du är osäker på familjenamnet, öppna `.ttf`‑filen i en teckensnittsvy eller använd metoden `fontSettings.GetFonts()` för att lista tillgängliga familjer.

---

## Steg 5: Ställ in teckensnittsvikt och stretch programatiskt  

Nu kommer kärnan i handledningen: vi **sätter teckensnittsvikt programatiskt** och **ändrar teckensnittsstretch‑kod**. Båda egenskaperna accepterar heltal som motsvarar OpenType‑specifikationen.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Välj vilket värde som helst som det variabela typsnittet stödjer.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Standardvärdet är 100 (Normal).

> **Proffstips:** Inte alla variabela typsnitt exponerar hela intervallet. Om du sätter ett värde som inte stöds, kommer motorn att klämma in till närmaste tillgängliga vikt eller stretch.

---

## Steg 6: Spara dokumentet och verifiera resultatet  

Till sist skriver vi ut dokumentet till PDF (eller DOCX) och öppnar det för att se effekten. PDF är ett utmärkt format för visuell verifiering eftersom rendering är konsekvent över plattformar.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

När du öppnar *VariableWeightDemo.pdf* bör du se frasen “Variable‑weight text demo” renderad i en lätt, något utökad version av Roboto Flex. Ändra `FontWeight` till `700` och `FontStretch` till `80` och kör igen – se hur texten blir fet och mer kompakt.

---

## Vanliga frågor och specialfall  

### Vad händer om teckensnittet inte visas alls?  

- **Saknad FontSettings**: Dubbelkolla att `doc.FontSettings = fontSettings;` körs **innan** någon text läggs till.
- **Fel familjenamn**: Använd `fontSettings.GetFonts()` för att lista alla upptäckta familjer; kopiera exakt den sträng som visas.
- **Vikt/stretch ej stödd**: Vissa variabela typsnitt stödjer bara en delmängd av 100‑900‑intervallet. Använd `run.Font.FontWeight = 400;` som en säker återgång.

### Kan jag ändra vikten efter att dokumentet sparats?  

Ja. `Run`‑objektet är muterbart, så du kan justera `FontWeight` eller `FontStretch` när som helst innan den slutgiltiga `Save`. Om du behöver växla vikter dynamiskt (t.ex. baserat på användarinteraktion) kan du överväga att generera separata runs för varje tillstånd.

### Fungerar detta med DOCX‑utmatning?  

Absolut. De variabelviktiga metadatan lagras i den underliggande OpenXML‑strukturen, och moderna versioner av Word kan tolka den. Äldre Word‑versioner kan dock ignorera stretch‑inställningen.

---

## Fullständigt fungerande exempel  

Nedan finns ett komplett konsolprogram som du kan kompilera och köra direkt. Det innehåller alla nödvändiga `using`‑direktiv, felhantering och kommentarer.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Förväntad utdata:** Konsolen skriver ut sparvägen, och den genererade PDF‑filen visar texten i en lätt, utökad stil – exakt som vi konfigurerade.

---

## Sammanfattning  

Vi har gått igenom hur du **använder variabelviktigt typsnitt** i C# med Aspose.Words, demonstrerat hur du **sätter teckensnittsvikt programatiskt**, och visat den exakta **ändra teckensnittsstretch‑koden** som behövs för att expandera eller komprimera glyferna. Stegen är enkla: konfigurera `FontSettings`, knyt dem till ett `Document`, skapa ett `Run`, välj den variabelviktiga familjen och justera sedan `FontWeight` och `FontStretch`.

---

## Vad blir nästa?  

- **Dynamisk UI‑integration**: Koppla samma logik till en WinForms‑ eller WPF‑app så att användare kan välja vikt/stretch via reglage.
- **Flera runs**: Kombinera flera runs med olika vikter i samma stycke för rika typografiska hierarkier.
- **Avancerade axlar**: Vissa variabela typsnitt har extra axlar (t.ex. slant, optisk storlek). Använd `run.Font.FontStyle` eller utforska `FontVariationSettings` för ännu finare kontroll.
- **Prestandatips**: Cacha `FontSettings`‑instansen när du bearbetar många dokument för att undvika upprepade mappskanningar.

Känn dig fri att experimentera – byt ut *Roboto Flex* mot *Inter Variable* eller något annat OpenType‑variabelt typsnitt, och se hur dina dokument får en ny nivå av visuell flexibilitet. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker nära besläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Använd teckensnitt från målmaskinen](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Använd teckensnitt från målmaskinen](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Använd teckensnitt från målmaskinen](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
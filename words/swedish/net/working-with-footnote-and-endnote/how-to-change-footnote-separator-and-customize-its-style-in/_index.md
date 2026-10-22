---
category: general
date: 2026-10-13
description: Hur man ändrar fotnotseparator i ett Word‑dokument med Aspose.Words.
  Lär dig att ändra teckenfärg i ett Word‑dokument programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: sv
lastmod: 2026-10-13
og_description: Hur man ändrar fotnotseparator i ett Word‑dokument med Aspose.Words.
  Den här handledningen visar hur du ändrar teckenfärgen i ett Word‑dokument med C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Hur man ändrar fotnotseparator i ett Word‑dokument – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Hur du ändrar fotnotseparatorn och anpassar dess stil i ett Word‑dokument
url: /sv/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man ändrar fotnotseparator och anpassar dess stil i ett Word‑dokument

Om du behöver **how to change footnote separator** i ett Word‑dokument, ger den här guiden dig en komplett, färdig‑att‑köra lösning. Med Aspose.Words för .NET kan du också **change font color in Word document** element såsom fotnot‑ och slutnotseparatorer, så att den slutliga filen matchar ditt varumärke eller stilguide.

Dokumentförfattare frågar ofta: *Varför ser standardfotnotseparatorn så enkel ut, och hur kan jag få den att sticka ut?* Svaret är att direkt komma åt separator‑paragrafobjekten, justera deras teckensnittsegenskaper och spara resultatet. Denna handledning guidar dig genom varje steg, från att ladda en .docx‑fil till att spara den stylade utdata.

Du kommer att lära dig hur du:

* Laddar en Word‑fil som redan innehåller fotnoter och slutnoter.  
* Hittar fotnot‑ och slutnotseparator‑paragraferna.  
* Ändrar teckensnittsfärgen för varje separator (röd för fotnoter, blå för slutnoter).  
* Sparar det modifierade dokumentet utan att förlora befintligt innehåll.

Inga externa verktyg krävs utöver Aspose.Words‑biblioteket och en .NET‑utvecklingsmiljö.

## Förutsättningar

* .NET 6.0 SDK eller senare (koden fungerar också med .NET Framework 4.7+).  
* Visual Studio 2022, Rider eller någon annan C#‑redigerare du föredrar.  
* Aspose.Words för .NET NuGet‑paket (`Aspose.Words`).  
* En exempel‑Word‑fil (`Footnotes.docx`) som innehåller minst en fotnot och en slutnot.

> **Pro tip:** Om du inte har en exempel‑fil, skapa ett nytt Word‑dokument, infoga en fotnot (`References → Insert Footnote`) och en slutnot (`References → Insert Endnote`). Spara den som `Footnotes.docx` i en mapp som du kan referera till från koden.

## Hur man ändrar fotnotseparator med Aspose.Words

Kärnan i uppgiften är att hämta de speciella paragrafer som Aspose.Words exponerar som *separator*‑noder. Dessa noder är av typen `Paragraph` och kan formateras som vilken annan paragraf som helst.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Varför varje rad är viktig

* **Loading the document** (`new Document`) ger dig en in‑memory‑representation som Aspose.Words kan manipulera.  
* **`GetChild` med `ParagraphNodeType.FootnoteSeparator`** returnerar den dolda paragraf som Word använder för att rita linjen som separerar fotnoter från huvudtexten. Samma metod fungerar för slutnotseparatorn.  
* **Changing `Font.Color`** påverkar direkt linjens utseende eftersom Word renderar separatorn som en paragraf med ett enda “‑”‑tecken. Att sätta färgen till `Color.Red` (eller någon `System.Drawing.Color`) uppdaterar den visuella stilen.  
* **Saving** skriver tillbaka ändringarna till en .docx‑fil som vilken Word‑processor som helst kan öppna.

### Förväntat resultat

När du öppnar `FootnoteSeparatorsStyled.docx` i Microsoft Word:

* Fotnotseparatorns linje visas **röd**.  
* Slutnotseparatorns linje visas **blå**.  

Allt originalt fotnot‑ och slutnotinnehåll förblir orört.

## Ändra teckensnittsfärg i Word‑dokument med C#

Operationen som demonstrerats ovan är ett specifikt fall av en bredare möjlighet: **change font color in Word document** programatiskt. När du har ett `Paragraph`, `Run` eller någon `Node` som innehåller text, kan du justera dess `Font.Color`‑egenskap.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Detta kodsnutt itererar över varje paragraf, kontrollerar om den använder stilen `Heading 1` och sätter dess teckensnittsfärg.  
* Du kan anpassa villkoret för att rikta in dig på fotnoter, tabeller eller någon annan nodtyp.

## Steg‑för‑steg‑genomgång

### 1. Installera Aspose.Words

Öppna en terminal i din projektmapp och kör:

```bash
dotnet add package Aspose.Words
```

Paketet innehåller alla assemblys som krävs för koden som visades tidigare.

### 2. Förbered indatafilen

Placera `Footnotes.docx` i en känd katalog (t.ex. `C:\Docs`). Säkerställ att filen innehåller minst en fotnot och en slutnot så att separator‑noderna finns.

### 3. Skriv C#‑programmet

Skapa ett nytt konsolprojekt (`dotnet new console -n FootnoteStyler`) och ersätt den genererade `Program.cs` med hela kodblocket från avsnittet **How to change footnote separator**. Kom ihåg att justera filsökvägarna så att de matchar din miljö.

### 4. Kör och verifiera

Kör programmet:

```bash
dotnet run
```

När körningen är klar, öppna `FootnoteSeparatorsStyled.docx`. Du bör se de röda och blå separatorlinjerna som beskrivits.

### 5. Utöka lösningen

* **Different colors:** Använd vilket `System.Drawing.Color`‑värde som helst, t.ex. `Color.FromArgb(255, 128, 0)` för orange.  
* **Custom line style:** Istället för att ändra färgen kan du modifiera `ParagraphFormat`‑egenskaper som `LineSpacing`, `Shading` eller till och med ersätta separator‑tecknet.  
* **Multiple documents:** Packa in logiken i en metod som accepterar in‑ och ut‑sökvägar, och anropa den i en loop för batch‑bearbetning.

## Vanliga fallgropar och hur du undviker dem

| Symptom | Orsak | Åtgärd |
|---------|-------|-----|
| `GetChild` returns `null` | Källdokumentet har ingen fotnot-/slutnotseparator (t.ex. inga fotnoter). | Lägg till minst en fotnot eller slutnot, eller kontrollera `null` innan du åtkommer `Font`. |
| Color change not visible | Separatorn renderas som en linje snarare än ett tecken i vissa Word‑versioner. | Sätt `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` och `ParagraphFormat.LineSpacing = 1` för att tvinga ett synligt tecken. |
| Runtime exception `FileNotFoundException` | Felaktig filsökväg. | Använd absoluta sökvägar eller `Path.Combine` med `Environment.CurrentDirectory`. |

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i en konsolapp. Det innehåller felhantering och kommentarer som förklarar varje operation.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Att köra detta program skapar en Word‑fil där fotnotseparatorns linje är röd och slutnotseparatorns linje är blå, vilket uppfyller kravet **how to change footnote separator** samtidigt som det demonstrerar **change font color in word document**.

## Slutsats

Du vet nu **how to change footnote separator** i ett Word‑dokument med Aspose.Words för .NET och hur du **change font color in Word document** programatiskt. Tillvägagångssättet är:

1. Ladda dokumentet.  
2. Hämta de dolda separator‑paragraferna.  
3. Sätt deras `Font.Color`‑egenskaper.  
4. Spara den modifierade filen.

Härifrån kan du utforska mer avancerad styling—justera linjetjocklek, använda olika teckensnitt eller automatisera processen över många filer. Att behärska dessa tekniker ger dig fin‑granulär kontroll över Word‑dokumentets utseende direkt från C#‑kod.

---

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Hämta stycke‑stilsseparator i Word‑dokument](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Skapa Word‑dokument med sidhuvud och sidfot med Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Lägg till sidnummer i sidfoten på ett Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
title: Skapa roterad text‑tabell i Word‑dokument med Aspose.Words för .NET
weight: 110
limit:
description: Lär dig att bygga en Word‑tabell med fasta kolumnbredder, roterad text, precisa radhöjder och ifyllda celler med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Lär dig att bygga en Word‑tabell med fasta kolumnbredder, roterad text,
    precisa radhöjder och ifyllda celler med Aspose.Words för .NET.
  headline: Skapa roterad text‑tabell i Word‑dokument med Aspose.Words för .NET
  type: TechArticle
- description: Lär dig att bygga en Word‑tabell med fasta kolumnbredder, roterad text,
    precisa radhöjder och ifyllda celler med Aspose.Words för .NET.
  name: Skapa roterad text‑tabell i Word‑dokument med Aspose.Words för .NET
  steps:
  - name: Instansiera ett nytt Document och en DocumentBuilder som kommer att användas
      för att konstruera tabellen.
    text: Instansiera ett nytt Document och en DocumentBuilder som kommer att användas
      för att konstruera tabellen.
  - name: Starta en ny tabell, infoga den första cellen och fixera kolumnbredderna
      så att de inte justeras automatiskt.
    text: Starta en ny tabell, infoga den första cellen och fixera kolumnbredderna
      så att de inte justeras automatiskt.
  - name: Centrera innehållet vertikalt i den aktuella cellen och skriv texten i den
      första radens första cell.
    text: Centrera innehållet vertikalt i den aktuella cellen och skriv texten i den
      första radens första cell.
  - name: Infoga den andra cellen i den första raden och skriv dess text.
    text: Infoga den andra cellen i den första raden och skriv dess text.
  - name: Avsluta den första raden, vilket slutför dess layout.
    text: Avsluta den första raden, vilket slutför dess layout.
  - name: Starta den första cellen i den andra raden, sätt radhöjden till exakt 100
      punkter, rotera texten uppåt och skriv cellens text.
    text: Starta den första cellen i den andra raden, sätt radhöjden till exakt 100
      punkter, rotera texten uppåt och skriv cellens text.
  - name: Infoga den andra cellen i den andra raden, rotera dess text nedåt och skriv
      cellens text.
    text: Infoga den andra cellen i den andra raden, rotera dess text nedåt och skriv
      cellens text.
  - name: Avsluta den andra raden, vilket fullbordar tabellens andra rad.
    text: Avsluta den andra raden, vilket fullbordar tabellens andra rad.
  - name: Avsluta tabellkonstruktionen, vilket förseglar tabellstrukturen.
    text: Avsluta tabellkonstruktionen, vilket förseglar tabellstrukturen.
  - name: Spara det färdiga dokumentet till en .docx‑fil.
    text: Spara det färdiga dokumentet till en .docx‑fil.
  type: HowTo
- questions:
  - answer: Efter att ha fixerat kolumnbredderna, tilldela en bredd till varje cell
      med `builder.CellFormat.Width = <valueInPoints>;` innan nästa cell infogas;
      tabellen behåller då de exakta bredderna.
    question: Hur kan jag ange specifika kolumnbredder efter att ha anropat `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` är en cellnivå‑inställning, så
      du måste sätta den igen för cellerna i den andra raden (t.ex. `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) innan du skriver deras innehåll.'
    question: Varför påverkar den vertikala justeringen bara den första raden och
      inte den andra raden?
  - answer: Ja – sätt `builder.RowFormat.Height` och `builder.RowFormat.HeightRule
      = HeightRule.Exactly` innan varje anrop av `builder.EndRow();`; nästa rad kan
      ha ett annat höjdvärde.
    question: Kan jag ge varje rad en annan exakt höjd, och i så fall hur?
  - answer: Återställ orienteringen genom att tilldela `builder.CellFormat.Orientation
      = TextOrientation.Horizontal;` innan du skriver till nästa cell.
    question: Hur återställer jag textorienteringen till standard efter att ha använt
      `TextOrientation.Upward` eller `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Skapa roterad text‑tabell i Word med Aspose.Words
og_description: Steg‑för‑steg‑kod för att bygga en tabell med fasta bredder, vertikalt roterad text och exakta radhöjder.
og_image_alt: Skärmbild som visar ett Word‑dokument med en tabell som har fasta kolumnbredder, roterad text i cellerna och definierade radhöjder, skapad med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa roterad text‑tabell i Word‑dokument med Aspose.Words för .NET
Denna handledning visar hur du genererar ett Word‑dokument och lägger till en tabell vars kolumner har fasta bredder, rader har exakta höjder och celltext är roterad vertikalt. Du kommer att lära dig att sätta vertikal justering, tillämpa textorientering, fylla varje cell med innehåll och slutligen spara dokumentet – allt med Aspose.Words för .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Hur kan jag ange specifika kolumnbredder efter att ha anropat `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: Efter att ha fixerat kolumnbredderna, tilldela en bredd till varje cell med `builder.CellFormat.Width = <valueInPoints>;` innan nästa cell infogas; tabellen behåller då de exakta bredderna.

**Q: Varför påverkar den vertikala justeringen bara den första raden och inte den andra raden?**  
A: `builder.CellFormat.VerticalAlignment` är en cellnivå‑inställning, så du måste sätta den igen för cellerna i den andra raden (t.ex. `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) innan du skriver deras innehåll.

**Q: Kan jag ge varje rad en annan exakt höjd, och i så fall hur?**  
A: Ja – sätt `builder.RowFormat.Height` och `builder.RowFormat.HeightRule = HeightRule.Exactly` innan varje anrop av `builder.EndRow();`; nästa rad kan ha ett annat höjdvärde.

**Q: Hur återställer jag textorienteringen till standard efter att ha använt `TextOrientation.Upward` eller `Downward`?**  
A: Återställ orienteringen genom att tilldela `builder.CellFormat.Orientation = TextOrientation.Horizontal;` innan du skriver till nästa cell.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
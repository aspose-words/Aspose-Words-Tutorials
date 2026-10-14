---
title: Formatera sekundär X‑axel och sätt displayenheter till tusental i Word‑linjediagram med Aspose.Words för .NET
weight: 710
limit:
description: Skapa ett Word‑linjediagram, lägg till en sekundär X‑axel, sätt dess displayenhet till tusental och applicera ett anpassat numeriskt format med Aspose.Words för .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Skapa ett Word‑linjediagram, lägg till en sekundär X‑axel, sätt dess
    displayenhet till tusental och applicera ett anpassat numeriskt format med Aspose.Words
    för .NET.
  headline: Formatera sekundär X‑axel och sätt displayenheter till tusental i Word‑linjediagram
    med Aspose.Words för .NET
  type: TechArticle
- description: Skapa ett Word‑linjediagram, lägg till en sekundär X‑axel, sätt dess
    displayenhet till tusental och applicera ett anpassat numeriskt format med Aspose.Words
    för .NET.
  name: Formatera sekundär X‑axel och sätt displayenheter till tusental i Word‑linjediagram
    med Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt Document och en DocumentBuilder för att börja bygga Word‑filen.
    text: Skapa ett nytt Document och en DocumentBuilder för att börja bygga Word‑filen.
  - name: Infoga ett linjediagram med storleken 500×300 i dokumentet och hämta Chart‑objektet.
    text: Infoga ett linjediagram med storleken 500×300 i dokumentet och hämta Chart‑objektet.
  - name: Ta bort den förinställda demoserien som Aspose.Words lägger till automatiskt.
    text: Ta bort den förinställda demoserien som Aspose.Words lägger till automatiskt.
  - name: Definiera en array med kategorirubriker som ska användas för X‑axeln.
    text: Definiera en array med kategorirubriker som ska användas för X‑axeln.
  - name: Lägg till den primära dataserien med namnet "Main Data" med hjälp av rubrikerna
      och värdena.
    text: Lägg till den primära dataserien med namnet "Main Data" med hjälp av rubrikerna
      och värdena.
  - name: Skapa en sekundär seriegroupp av typen Line och tilldela den till den sekundära
      axelgruppen.
    text: Skapa en sekundär seriegroupp av typen Line och tilldela den till den sekundära
      axelgruppen.
  - name: Ställ in den sekundära X‑axelns displayenhet till tusental så att värdena
      visas i K.
    text: Ställ in den sekundära X‑axelns displayenhet till tusental så att värdena
      visas i K.
  - name: Applicera det anpassade numeriska formatet "#,##0.0" på den sekundära X‑axelns
      tick‑etiketter.
    text: Applicera det anpassade numeriska formatet "#,##0.0" på den sekundära X‑axelns
      tick‑etiketter.
  - name: Lägg eventuellt till en hjälpsats med data till den sekundära gruppen.
    text: Lägg eventuellt till en hjälpsats med data till den sekundära gruppen.
  - name: Spara dokumentet som en .docx‑fil.
    text: Spara dokumentet som en .docx‑fil.
  type: HowTo
- questions:
  - answer: Nej – `AxisX`‑inställningarna tillhör `ChartSeriesGroup`, så du kan sätta
      `secondaryGroup.AxisX.DisplayUnit.Unit` och `secondaryGroup.AxisX.NumberFormat.FormatCode`
      före eller efter att du har lagt till serier; konfigurationen kommer att tillämpas
      på gruppens axel i båda fallen.
    question: Måste jag lägga till den sekundära serien innan jag ställer in displayenheten
      och talformatet på den sekundära X‑axeln?
  - answer: Ja – tilldela vilket `AxisBuiltInUnit`‑värde som helst, t.ex. `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` för att visa axelvärdena i miljoner istället för
      tusental.
    question: Kan jag använda en annan inbyggd enhet, till exempel miljoner, för den
      sekundära X‑axeln?
  - answer: Nej – formatkoden appliceras endast på den axel du modifierar (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      så den primära X‑axeln behåller sin standardformatering.
    question: Kommer det anpassade formatet `"#,##0.0"` att påverka den primära X‑axelns
      etiketter?
  - answer: Diagrammet kommer att innehålla den förinställda demoserien utöver de
      du lägger till, vilket kan leda till extra linjer och felaktiga kategorier;
      att rensa samlingen säkerställer att endast den avsedda datan visas.
    question: Vad händer om jag glömmer att rensa demoserien med `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatera sekundär X‑axel och sätt enheter till tusental
og_description: Lägg till en sekundär X‑axel i ett Word‑linjediagram och formatera dess etiketter i tusental med ett anpassat mönster.
og_image_alt: Guide som visar hur man lägger till en sekundär X‑axel i ett Word‑linjediagram och formaterar dess etiketter så att enheterna visas i tusental med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatera sekundär X‑axel och sätt displayenheter till tusental i Word‑linjediagram med Aspose.Words för .NET
Den här handledningen guidar dig genom att skapa ett Word‑dokument som innehåller ett linjediagram, lägga till en sekundär X‑axel och konfigurera den axeln så att den visar värden i tusental. Du får även lära dig hur du applicerar ett anpassat numeriskt format på den sekundära axelns etiketter, vilket ger dig exakt kontroll över hur data presenteras. Följ stegen för att förbättra läsbarheten i diagram med flera axlar i dina Word‑rapporter.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Måste jag lägga till den sekundära serien innan jag ställer in displayenheten och talformatet på den sekundära X‑axeln?**  
A: Nej – `AxisX`‑inställningarna tillhör `ChartSeriesGroup`, så du kan sätta `secondaryGroup.AxisX.DisplayUnit.Unit` och `secondaryGroup.AxisX.NumberFormat.FormatCode` före eller efter att du har lagt till serier; konfigurationen kommer att tillämpas på gruppens axel i båda fallen.

**Q: Kan jag använda en annan inbyggd enhet, till exempel miljoner, för den sekundära X‑axeln?**  
A: Ja – tilldela vilket `AxisBuiltInUnit`‑värde som helst, t.ex. `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` för att visa axelvärdena i miljoner istället för tusental.

**Q: Kommer det anpassade formatet `"#,##0.0"` att påverka den primära X‑axelns etiketter?**  
A: Nej – formatkoden appliceras endast på den axel du modifierar (`secondaryGroup.AxisX.NumberFormat.FormatCode`), så den primära X‑axeln behåller sin standardformatering.

**Q: Vad händer om jag glömmer att rensa demoserien med `lineChart.Series.Clear();`?**  
A: Diagrammet kommer att innehålla den förinställda demoserien utöver de du lägger till, vilket kan leda till extra linjer och felaktiga kategorier; att rensa samlingen säkerställer att endast den avsedda datan visas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
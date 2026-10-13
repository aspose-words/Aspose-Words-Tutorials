---
title: Formatera sekundär Y‑axel som valuta i ett Word‑diagram med Aspose.Words för .NET
weight: 710
limit:
description: Lär dig att lägga till och formatera en sekundär Y‑axel som valuta i ett Word‑linjediagram med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig att lägga till och formatera en sekundär Y‑axel som valuta
    i ett Word‑linjediagram med Aspose.Words för .NET.
  headline: Formatera sekundär Y‑axel som valuta i ett Word‑diagram med Aspose.Words
    för .NET
  type: TechArticle
- description: Lär dig att lägga till och formatera en sekundär Y‑axel som valuta
    i ett Word‑linjediagram med Aspose.Words för .NET.
  name: Formatera sekundär Y‑axel som valuta i ett Word‑diagram med Aspose.Words för
    .NET
  steps:
  - name: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
    text: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
  - name: Infoga ett linjediagram med storleken 450×250 punkter i dokumentet och hämta
      dess Chart‑objekt.
    text: Infoga ett linjediagram med storleken 450×250 punkter i dokumentet och hämta
      dess Chart‑objekt.
  - name: Ta bort den standardplatshållarserien som Aspose lägger till i ett nytt
      diagram.
    text: Ta bort den standardplatshållarserien som Aspose lägger till i ett nytt
      diagram.
  - name: Definiera kvartalsetiketter och lägg till en primär dataserie med exempelvärden
      i diagrammet.
    text: Definiera kvartalsetiketter och lägg till en primär dataserie med exempelvärden
      i diagrammet.
  - name: Skapa en sekundär series group av typen Line och tilldela den till den sekundära
      axelgruppen.
    text: Skapa en sekundär series group av typen Line och tilldela den till den sekundära
      axelgruppen.
  - name: Dölj den sekundära X‑axeln så att endast den sekundära Y‑axeln är synlig.
    text: Dölj den sekundära X‑axeln så att endast den sekundära Y‑axeln är synlig.
  - name: Visa titeln för den sekundära Y‑axeln och sätt dess text till "Sales (USD)".
    text: Visa titeln för den sekundära Y‑axeln och sätt dess text till "Sales (USD)".
  - name: Ställ in nummerformatet för den sekundära Y‑axeln till ett valutamönster
      med två decimaler och koppla bort det från källformatet.
    text: Ställ in nummerformatet för den sekundära Y‑axeln till ett valutamönster
      med två decimaler och koppla bort det från källformatet.
  - name: Lägg till en hjälpserie i den sekundära gruppen som tillhandahåller data
      som ska plottas mot den sekundära Y‑axeln.
    text: Lägg till en hjälpserie i den sekundära gruppen som tillhandahåller data
      som ska plottas mot den sekundära Y‑axeln.
  - name: Spara det färdiga dokumentet till en fil med namnet ProfitChart.docx i den
      aktuella katalogen.
    text: Spara det färdiga dokumentet till en fil med namnet ProfitChart.docx i den
      aktuella katalogen.
  type: HowTo
- questions:
  - answer: Diagrammet behåller den standardplatshållarserie som Aspose.Words infogar,
      så din anpassade "Main Series" kommer att visas tillsammans med oönskade datapunkter.
    question: Vad händer om jag utelämnar anropet `lineChart.Series.Clear()`?
  - answer: Sätt `secondarySeriesGroup.AxisX.Hidden = false;` (eller utelämna helt
      enkelt raden som sätter den till `true`).
    question: Hur kan jag visa den sekundära X‑axeln istället för att dölja den?
  - answer: Ja – ändra formatsträngen, t.ex. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\"€\"#,##0.00";` för euro eller justera mönstret så att det passar din lokala
      inställning.
    question: Kan jag använda en annan valutasymbol eller ett annat format för den
      sekundära Y‑axeln?
  - answer: När `IsLinkedToSource` är true ärver axeln nummerformatet från den underliggande
      datakällan, vilket åsidosätter eventuella egna `FormatCode`; att sätta den till
      false tvingar diagrammet att använda det format du anger.
    question: Varför måste jag sätta `IsLinkedToSource = false` när jag använder ett
      eget nummerformat?
  - answer: Ja, tilldela `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (eller `Right` för standard) för att styra på vilken sida axeln ritas.
    question: Är det möjligt att flytta den sekundära Y‑axeln till diagrammets vänstra
      sida?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatera ett diagrams sekundära axel som valuta
og_description: Lär dig att lägga till en sekundär Y‑axel i ett Word‑linjediagram och formatera den som valuta med två decimaler.
og_image_alt: Skärmbild som visar ett Word‑linjediagram med en sekundär Y‑axel formaterad som valuta med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatera sekundär Y‑axel som valuta i ett Word‑diagram med Aspose.Words för .NET
I den här handledningen kommer du att se hur du bygger ett Word‑dokument, infogar ett linjediagram, lägger till en sekundär Y‑axel, formaterar den axeln som valuta med två decimaler och binder en sekundär dataserie till den med hjälp av Aspose.Words för .NET. Att formatera den sekundära axeln som valuta gör att du tydligt kan presentera finansiella data tillsammans med den primära serien. Följ den steg‑för‑steg‑koden för att se diagrammet renderas direkt i det genererade dokumentet.

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

**Q: Vad händer om jag utelämnar anropet `lineChart.Series.Clear()`?**  
A: Diagrammet behåller den standardplatshållarserie som Aspose.Words infogar, så din anpassade "Main Series" kommer att visas tillsammans med oönskade datapunkter.

**Q: Hur kan jag visa den sekundära X‑axeln istället för att dölja den?**  
A: Sätt `secondarySeriesGroup.AxisX.Hidden = false;` (eller utelämna helt enkelt raden som sätter den till `true`).

**Q: Kan jag använda en annan valutasymbol eller ett annat format för den sekundära Y‑axeln?**  
A: Ja – ändra formatsträngen, t.ex. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\"€\"#,##0.00";` för euro eller justera mönstret så att det passar din lokala inställning.

**Q: Varför måste jag sätta `IsLinkedToSource = false` när jag använder ett eget nummerformat?**  
A: När `IsLinkedToSource` är true ärver axeln nummerformatet från den underliggande datakällan, vilket åsidosätter eventuella egna `FormatCode`; att sätta den till false tvingar diagrammet att använda det format du anger.

**Q: Är det möjligt att flytta den sekundära Y‑axeln till diagrammets vänstra sida?**  
A: Ja, tilldela `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (eller `Right` för standard) för att styra på vilken sida axeln ritas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
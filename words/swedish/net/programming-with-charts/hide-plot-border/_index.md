---
title: Dölj plotområdesram i ett stapeldiagram med Aspose.Words för .NET
weight: 410
limit:
description: Lär dig att dölja ett diagrams plotområdesram samtidigt som du behåller axellinjerna synliga i ett Word‑stapeldiagram med Aspose.Words för .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig att dölja ett diagrams plotområdesram samtidigt som du behåller
    axellinjerna synliga i ett Word‑stapeldiagram med Aspose.Words för .NET.
  headline: Dölj plotområdesram i ett stapeldiagram med Aspose.Words för .NET
  type: TechArticle
- description: Lär dig att dölja ett diagrams plotområdesram samtidigt som du behåller
    axellinjerna synliga i ett Word‑stapeldiagram med Aspose.Words för .NET.
  name: Dölj plotområdesram i ett stapeldiagram med Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
    text: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
  - name: Infoga ett 432×252 stapeldiagram i dokumentet och hämta dess Chart‑objekt.
    text: Infoga ett 432×252 stapeldiagram i dokumentet och hämta dess Chart‑objekt.
  - name: Rensa eventuella befintliga serier, definiera tre kategorietiketter och
      lägg till en serie med exempelvärden i diagrammet.
    text: Rensa eventuella befintliga serier, definiera tre kategorietiketter och
      lägg till en serie med exempelvärden i diagrammet.
  - name: Ställ in plotområdets stroke‑tjocklek till noll, vilket tar bort dess ram
      men låter axellinjerna vara synliga.
    text: Ställ in plotområdets stroke‑tjocklek till noll, vilket tar bort dess ram
      men låter axellinjerna vara synliga.
  - name: Spara det modifierade dokumentet som en .docx‑fil.
    text: Spara det modifierade dokumentet som en .docx‑fil.
  type: HowTo
- questions:
  - answer: '`Stroke`‑egenskapen tillhör `Chart`‑objektets övergripande format, som
      ritar den rektangulära ramen runt plotområdet; axellinjer är separata `Axis`‑objekt
      och påverkas inte av diagrammets `Stroke`‑inställningar.'
    question: Varför tar inställningen `columnChart.Format.Stroke.Weight = 0` bort
      plotområdesramen men låter axellinjerna vara synliga?
  - answer: Nej, `Stroke`‑egenskapen styr hela plotområdesramen som en enda rektangel,
      så delvisa ramar kan inte döljas via Aspose.Words; du måste lägga över anpassade
      former eller redigera diagrammet manuellt.
    question: Kan jag dölja bara en sida av plotområdesramen (t.ex. vänstra sidan)
      samtidigt som de andra tre sidorna förblir synliga?
  - answer: Ja, `Stroke`‑egenskapen är oberoende av `ChartType`, så att sätta dess
      `Weight` till 0 tar bort plotområdesramen för Linje, Paj eller någon annan stödjande
      diagramtyp.
    question: Om jag ändrar diagramtypen till Linje eller Paj, kommer `columnChart.Format.Stroke.Weight
      = 0` fortfarande att dölja plotområdesramen?
  - answer: Ingen extra uppdatering krävs; att rensa serierna och lägga till en ny
      uppdaterar diagrammet internt, och `wordDoc.Save(...)` skriver det aktuella
      tillståndet till .docx‑filen.
    question: Efter att ha anropat `columnChart.Series.Clear()`, behöver jag uppdatera
      diagrammet innan jag sparar dokumentet?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Dölj plotram i ett Word‑stapeldiagram
og_description: Ta bort plotområdesramen samtidigt som du behåller axellinjerna synliga i ett Word‑stapeldiagram med Aspose.Words för .NET.
og_image_alt: Guide som visar ett Word‑dokument med ett stapeldiagram där plotområdesramen är dold men axellinjerna förblir synliga med Aspose.Words för .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dölj plotområdesram i ett stapeldiagram med Aspose.Words för .NET
I den här handledningen kommer du att lära dig hur man genererar ett Word‑dokument, infogar ett stapeldiagram, fyller det med exempeldata och sedan döljer diagrammets plotområdesram medan axellinjerna förblir synliga. Steg‑för‑steg‑koden demonstrerar varje operation och avslutas med att spara dokumentet, så att du kan se resultatet omedelbart.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: Varför tar inställningen `columnChart.Format.Stroke.Weight = 0` bort plotområdesramen men låter axellinjerna vara synliga?**  
A: `Stroke`‑egenskapen tillhör `Chart`‑objektets övergripande format, som ritar den rektangulära ramen runt plotområdet; axellinjer är separata `Axis`‑objekt och påverkas inte av diagrammets `Stroke`‑inställningar.

**Q: Kan jag dölja bara en sida av plotområdesramen (t.ex. vänstra sidan) samtidigt som de andra tre sidorna förblir synliga?**  
A: Nej, `Stroke`‑egenskapen styr hela plotområdesramen som en enda rektangel, så delvisa ramar kan inte döljas via Aspose.Words; du måste lägga över anpassade former eller redigera diagrammet manuellt.

**Q: Om jag ändrar diagramtypen till Linje eller Paj, kommer `columnChart.Format.Stroke.Weight = 0` fortfarande att dölja plotområdesramen?**  
A: Ja, `Stroke`‑egenskapen är oberoende av `ChartType`, så att sätta dess `Weight` till 0 tar bort plotområdesramen för Linje, Paj eller någon annan stödjande diagramtyp.

**Q: Efter att ha anropat `columnChart.Series.Clear()`, behöver jag uppdatera diagrammet innan jag sparar dokumentet?**  
A: Ingen extra uppdatering krävs; att rensa serierna och lägga till en ny uppdaterar diagrammet internt, och `wordDoc.Save(...)` skriver det aktuella tillståndet till .docx‑filen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
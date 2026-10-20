---
title: Verwijder een Chart Series uit een Word Document met Aspose.Words for .NET
weight: 510
limit:
description: Leer hoe je een specifieke gegevensreeks uit een kolomgrafiek in een Word‑document verwijdert met Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Leer hoe je een specifieke gegevensreeks uit een kolomgrafiek in een
    Word‑document verwijdert met Aspose.Words for .NET.
  headline: Verwijder een Chart Series uit een Word Document met Aspose.Words for
    .NET
  type: TechArticle
- description: Leer hoe je een specifieke gegevensreeks uit een kolomgrafiek in een
    Word‑document verwijdert met Aspose.Words for .NET.
  name: Verwijder een Chart Series uit een Word Document met Aspose.Words for .NET
  steps:
  - name: Maak een nieuw Word Document en een DocumentBuilder die eraan gekoppeld
      is.
    text: Maak een nieuw Word Document en een DocumentBuilder die eraan gekoppeld
      is.
  - name: Voeg een kolomgrafiek van 432×252 punten in en verkrijg het Chart‑object
      voor verdere manipulatie.
    text: Voeg een kolomgrafiek van 432×252 punten in en verkrijg het Chart‑object
      voor verdere manipulatie.
  - name: Definieer de nul‑gebaseerde index van de reeks die verwijderd moet worden
      (de tweede reeks).
    text: Definieer de nul‑gebaseerde index van de reeks die verwijderd moet worden
      (de tweede reeks).
  - name: Als de index geldig is, roep RemoveAt aan op de Series‑collectie van de
      grafiek om die reeks te verwijderen.
    text: Als de index geldig is, roep RemoveAt aan op de Series‑collectie van de
      grafiek om die reeks te verwijderen.
  - name: Sla het bijgewerkte document op als een .docx‑bestand.
    text: Sla het bijgewerkte document op als een .docx‑bestand.
  type: HowTo
- questions:
  - answer: De `if`‑controle (`targetSeriesIdx < columnChart.Series.Count`) zal falen,
      waardoor `RemoveAt` nooit wordt aangeroepen en de grafiek ongewijzigd blijft.
    question: Wat gebeurt er als ik een index doorgeef die gelijk is aan het aantal
      reeksen in de grafiek?
  - answer: Ja, na `columnChart.Series.RemoveAt` wordt de legenda opnieuw gegenereerd
      om de resterende reeksen weer te geven, waardoor het verwijderde item uit de
      legenda verdwijnt.
    question: Werkt het verwijderen van een reeks automatisch de legenda van de grafiek
      bij?
  - answer: De code werkt voor elk grafiektype dat een `Series`‑collectie ondersteunt;
      wijzig gewoon `ChartType.Column` naar het gewenste type bij het invoegen van
      de grafiek.
    question: Kan ik dezelfde code gebruiken om een reeks uit een lijngrafiek of cirkeldiagram
      te verwijderen?
  - answer: Een grafiek zonder reeksen is nog steeds een geldige `Shape` en wordt
      opgeslagen, maar zal leeg verschijnen in het resulterende document.
    question: Als ik de enige reeks in een grafiek verwijder, wordt de grafiek dan
      nog correct opgeslagen?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Verwijder een Chart Series in een Word Document
og_description: Stapsgewijze handleiding om een gegevensreeks uit een Word‑grafiek te verwijderen met Aspose.Words for .NET.
og_image_alt: Gids die laat zien hoe je een specifieke gegevensreeks uit een kolomgrafiek in een Word‑document verwijdert met Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verwijder een Chart Series uit een Word Document met Aspose.Words
Deze tutorial laat zien hoe je een Word‑document maakt, een kolomgrafiek toevoegt met DocumentBuilder, en vervolgens een specifieke gegevensreeks uit die grafiek verwijdert met de ChartSeriesCollection.RemoveAt‑methode. Aan het einde heb je een opgeslagen document waarin de ongewenste reeks is verwijderd, waardoor je directe en nauwkeurige controle over de grafiekinhoud vanuit .NET‑code krijgt.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Wat gebeurt er als ik een index doorgeef die gelijk is aan het aantal reeksen in de grafiek?**  
A: De `if`‑controle (`targetSeriesIdx < columnChart.Series.Count`) zal falen, waardoor `RemoveAt` nooit wordt aangeroepen en de grafiek ongewijzigd blijft.

**Q: Werkt het verwijderen van een reeks automatisch de legenda van de grafiek bij?**  
A: Ja, na `columnChart.Series.RemoveAt` wordt de legenda opnieuw gegenereerd om de resterende reeksen weer te geven, waardoor het verwijderde item uit de legenda verdwijnt.

**Q: Kan ik dezelfde code gebruiken om een reeks uit een lijngrafiek of cirkeldiagram te verwijderen?**  
A: De code werkt voor elk grafiektype dat een `Series`‑collectie ondersteunt; wijzig gewoon `ChartType.Column` naar het gewenste type bij het invoegen van de grafiek.

**Q: Als ik de enige reeks in een grafiek verwijder, wordt de grafiek dan nog correct opgeslagen?**  
A: Een grafiek zonder reeksen is nog steeds een geldige `Shape` en wordt opgeslagen, maar zal leeg verschijnen in het resulterende document.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
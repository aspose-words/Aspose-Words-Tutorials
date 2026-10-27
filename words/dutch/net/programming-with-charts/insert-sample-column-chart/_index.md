---
title: Voeg een voorbeeld kolomgrafiek toe aan een Word‑document met Aspose.Words for .NET
weight: 410
limit:
description: Stapsgewijze gids om een Word‑bestand te maken, een standaard kolomgrafiek in te voegen met DocumentBuilder.InsertChart, toegang te krijgen tot het chart‑object en op te slaan als .docx.
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Stapsgewijze gids om een Word‑bestand te maken, een standaard kolomgrafiek
    in te voegen met DocumentBuilder.InsertChart, toegang te krijgen tot het chart‑object
    en op te slaan als .docx.
  headline: Voeg een voorbeeld kolomgrafiek toe aan een Word‑document met Aspose.Words
    for .NET
  type: TechArticle
- description: Stapsgewijze gids om een Word‑bestand te maken, een standaard kolomgrafiek
    in te voegen met DocumentBuilder.InsertChart, toegang te krijgen tot het chart‑object
    en op te slaan als .docx.
  name: Voeg een voorbeeld kolomgrafiek toe aan een Word‑document met Aspose.Words
    for .NET
  steps:
  - name: Maak een leeg Word‑document en een DocumentBuilder om het te bewerken.
    text: Maak een leeg Word‑document en een DocumentBuilder om het te bewerken.
  - name: Voeg een kolomgrafiek van 432 × 252 punten toe aan het document.
    text: Voeg een kolomgrafiek van 432 × 252 punten toe aan het document.
  - name: Haal het Chart‑object op uit de ingevoegde shape voor verdere aanpassing
      indien nodig.
    text: Haal het Chart‑object op uit de ingevoegde shape voor verdere aanpassing
      indien nodig.
  - name: Sla het document, dat nu de ingevoegde kolomgrafiek bevat, op als een .docx‑bestand.
    text: Sla het document, dat nu de ingevoegde kolomgrafiek bevat, op als een .docx‑bestand.
  type: HowTo
- questions:
  - answer: De afmetingen worden opgegeven in points (1 point = 1/72 inch), dus 432
      pt ≈ 6 in en 252 pt ≈ 3,5 in.
    question: Welke eenheden worden gebruikt voor de breedte‑ en hoogte‑parameters
      (432, 252) in InsertChart?
  - answer: Ja—na het invoegen heb je het Chart‑object via `chartContainer.Chart`;
      je kunt de SeriesCollection, Categories en Values aanpassen om de voorbeeldgegevens
      te vervangen.
    question: Kan ik de chart‑gegevens wijzigen nadat ik InsertChart heb aangeroepen
      met de standaard dataset?
  - answer: Vervang simpelweg `ChartType.Column` door een andere enum‑waarde, zoals
      `ChartType.Line`, in de `InsertChart`‑aanroep.
    question: Is het mogelijk om een ander type grafiek (bijv. een lijngrafiek) in
      te voegen met dezelfde code?
  - answer: Nee—`docBuilder.InsertChart` voegt de chart automatisch in als een `Shape`;
      het aanroepen van `wordDoc.Save` schrijft de chart mee met het document.
    question: Moet ik nog een extra methode aanroepen om de chart in te sluiten voordat
      ik het document opsla?
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: Voeg een voorbeeld kolomgrafiek toe aan een Word‑document
og_description: Voeg binnen enkele minuten een kant‑klaar kolomgrafiek toe aan een Word‑document met Aspose.Words for .NET.
og_image_alt: Schermafbeelding die een Word‑document toont met een voorbeeld kolomgrafiek ingevoegd via Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg een voorbeeld kolomgrafiek toe aan een Word‑document met Aspose.Words
Deze tutorial leidt je stap voor stap door het maken van een nieuw Word‑document en het invoegen van een standaard kolomgrafiek met DocumentBuilder.InsertChart. Je ziet ook hoe je het ingesloten Chart‑object kunt ophalen voor verdere manipulatie. Ten slotte laat de gids zien hoe je het document opslaat als een .docx‑bestand.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: Welke eenheden worden gebruikt voor de breedte‑ en hoogte‑parameters (432, 252) in InsertChart?**  
A: De afmetingen worden opgegeven in points (1 point = 1/72 inch), dus 432 pt ≈ 6 in en 252 pt ≈ 3,5 in.

**Q: Kan ik de chart‑gegevens wijzigen nadat ik InsertChart heb aangeroepen met de standaard dataset?**  
A: Ja—na het invoegen heb je het Chart‑object via `chartContainer.Chart`; je kunt de SeriesCollection, Categories en Values aanpassen om de voorbeeldgegevens te vervangen.

**Q: Is het mogelijk om een ander type grafiek (bijv. een lijngrafiek) in te voegen met dezelfde code?**  
A: Vervang simpelweg `ChartType.Column` door een andere enum‑waarde, zoals `ChartType.Line`, in de `InsertChart`‑aanroep.

**Q: Moet ik nog een extra methode aanroepen om de chart in te sluiten voordat ik het document opsla?**  
A: Nee—`docBuilder.InsertChart` voegt de chart automatisch in als een `Shape`; het aanroepen van `wordDoc.Save` schrijft de chart mee met het document.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
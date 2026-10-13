---
title: Formatteer de secundaire Y‑as als valuta in een Word-diagram met Aspose.Words for .NET
weight: 710
limit:
description: Leer hoe je een secundaire Y‑as toevoegt en formatteert als valuta in een Word-lijndiagram met Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Leer hoe je een secundaire Y‑as toevoegt en formatteert als valuta
    in een Word-lijndiagram met Aspose.Words for .NET.
  headline: Formatteer de secundaire Y‑as als valuta in een Word-diagram met Aspose.Words
    for .NET
  type: TechArticle
- description: Leer hoe je een secundaire Y‑as toevoegt en formatteert als valuta
    in een Word-lijndiagram met Aspose.Words for .NET.
  name: Formatteer de secundaire Y‑as als valuta in een Word-diagram met Aspose.Words
    for .NET
  steps:
  - name: Maak een nieuw leeg Word-document en een DocumentBuilder om het te bewerken.
    text: Maak een nieuw leeg Word-document en een DocumentBuilder om het te bewerken.
  - name: Voeg een lijndiagram van 450×250 punten toe aan het document en verkrijg
      het Chart‑object.
    text: Voeg een lijndiagram van 450×250 punten toe aan het document en verkrijg
      het Chart‑object.
  - name: Verwijder de standaard placeholder‑reeks die Aspose toevoegt aan een nieuw
      diagram.
    text: Verwijder de standaard placeholder‑reeks die Aspose toevoegt aan een nieuw
      diagram.
  - name: Definieer kwartaal‑labels en voeg een primaire gegevensreeks met voorbeeldwaarden
      toe aan het diagram.
    text: Definieer kwartaal‑labels en voeg een primaire gegevensreeks met voorbeeldwaarden
      toe aan het diagram.
  - name: Maak een secundaire series‑groep van het type Line en wijs deze toe aan
      de secundaire as‑groep.
    text: Maak een secundaire series‑groep van het type Line en wijs deze toe aan
      de secundaire as‑groep.
  - name: Verberg de secundaire X‑as zodat alleen de secundaire Y‑as zichtbaar is.
    text: Verberg de secundaire X‑as zodat alleen de secundaire Y‑as zichtbaar is.
  - name: Toon de titel van de secundaire Y‑as en stel de tekst in op "Sales (USD)".
    text: Toon de titel van de secundaire Y‑as en stel de tekst in op "Sales (USD)".
  - name: Stel het getalformaat van de secundaire Y‑as in op een valutapatroon met
      twee decimalen en ontkoppel het van de bronformattering.
    text: Stel het getalformaat van de secundaire Y‑as in op een valutapatroon met
      twee decimalen en ontkoppel het van de bronformattering.
  - name: Voeg een aanvullende reeks toe aan de secundaire groep, met gegevens die
      tegen de secundaire Y‑as worden uitgezet.
    text: Voeg een aanvullende reeks toe aan de secundaire groep, met gegevens die
      tegen de secundaire Y‑as worden uitgezet.
  - name: Sla het voltooide document op in een bestand met de naam ProfitChart.docx
      in de huidige map.
    text: Sla het voltooide document op in een bestand met de naam ProfitChart.docx
      in de huidige map.
  type: HowTo
- questions:
  - answer: Het diagram behoudt de standaard placeholder‑reeks die Aspose.Words invoegt,
      waardoor je aangepaste "Main Series" naast ongewenste datapunten verschijnt.
    question: Wat gebeurt er als ik de aanroep `lineChart.Series.Clear()` weglaat?
  - answer: Stel `secondarySeriesGroup.AxisX.Hidden = false;` in (of laat simpelweg
      de regel die het op `true` zet weg).
    question: Hoe kan ik de secundaire X‑as weergeven in plaats van deze te verbergen?
  - answer: Ja – wijzig de opmaak‑string, bijv. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"\\\"€\\\"#,##0.00\";` voor euro’s of pas het patroon aan aan je locale.
    question: Kan ik een ander valutasymbool of -formaat gebruiken voor de secundaire
      Y‑as?
  - answer: Wanneer `IsLinkedToSource` true is, erft de as het getalformaat van de
      onderliggende gegevensbron, waardoor elk aangepast `FormatCode` wordt overschreven;
      door het op false te zetten, dwing je het diagram om het door jou opgegeven
      formaat te gebruiken.
    question: Waarom moet ik `IsLinkedToSource = false` instellen bij het toepassen
      van een aangepast getalformaat?
  - answer: Ja, wijs `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` toe
      (of `Right` voor de standaard) om te bepalen aan welke kant de as wordt getekend.
    question: Is het mogelijk om de secundaire Y‑as naar de linkerkant van het diagram
      te verplaatsen?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatteer de secundaire as van een diagram als valuta
og_description: Leer hoe je een secundaire Y‑as toevoegt aan een Word-lijndiagram en deze styleert als valuta met twee decimalen.
og_image_alt: Schermafbeelding die een Word-lijndiagram toont met een secundaire Y‑as geformatteerd als valuta met behulp van Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatteer de secundaire Y‑as als valuta in een Word-diagram met Aspose.Words
In deze tutorial zie je hoe je een Word-document maakt, een lijndiagram invoegt, een secundaire Y‑as toevoegt, die as formatteert als valuta met twee decimalen, en er een secundaire gegevensreeks aan bindt met behulp van Aspose.Words for .NET. Het formatteren van de secundaire as als valuta stelt je in staat financiële gegevens duidelijk naast de primaire reeks weer te geven. Volg de stapsgewijze code om het diagram direct in het gegenereerde document te zien.

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

**Q: Wat gebeurt er als ik de aanroep `lineChart.Series.Clear()` weglaat?**  
A: Het diagram behoudt de standaard placeholder‑reeks die Aspose.Words invoegt, waardoor je aangepaste "Main Series" naast ongewenste datapunten verschijnt.

**Q: Hoe kan ik de secundaire X‑as weergeven in plaats van deze te verbergen?**  
A: Stel `secondarySeriesGroup.AxisX.Hidden = false;` in (of laat simpelweg de regel die het op `true` zet weg).

**Q: Kan ik een ander valutasymbool of -formaat gebruiken voor de secundaire Y‑as?**  
A: Ja – wijzig de opmaak‑string, bijv. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` voor euro’s of pas het patroon aan aan je locale.

**Q: Waarom moet ik `IsLinkedToSource = false` instellen bij het toepassen van een aangepast getalformaat?**  
A: Wanneer `IsLinkedToSource` true is, erft de as het getalformaat van de onderliggende gegevensbron, waardoor elk aangepast `FormatCode` wordt overschreven; door het op false te zetten, dwing je het diagram om het door jou opgegeven formaat te gebruiken.

**Q: Is het mogelijk om de secundaire Y‑as naar de linkerkant van het diagram te verplaatsen?**  
A: Ja, wijs `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` toe (of `Right` voor de standaard) om te bepalen aan welke kant de as wordt getekend.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
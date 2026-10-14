---
title: Formatteer de secundaire X‑as en stel weergave‑eenheden in op duizenden in Word‑lijndiagrammen met Aspose.Words voor .NET
weight: 710
limit:
description: Maak een Word‑lijndiagram, voeg een secundaire X‑as toe, stel de weergave‑eenheid in op duizenden, en pas een aangepast numeriek formaat toe met Aspose.Words voor .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Maak een Word‑lijndiagram, voeg een secundaire X‑as toe, stel de weergave‑eenheid
    in op duizenden, en pas een aangepast numeriek formaat toe met Aspose.Words voor
    .NET.
  headline: Formatteer de secundaire X‑as en stel weergave‑eenheden in op duizenden
    in Word‑lijndiagrammen met Aspose.Words voor .NET
  type: TechArticle
- description: Maak een Word‑lijndiagram, voeg een secundaire X‑as toe, stel de weergave‑eenheid
    in op duizenden, en pas een aangepast numeriek formaat toe met Aspose.Words voor
    .NET.
  name: Formatteer de secundaire X‑as en stel weergave‑eenheden in op duizenden in
    Word‑lijndiagrammen met Aspose.Words voor .NET
  steps:
  - name: Doe een nieuw Document en een DocumentBuilder aan om te beginnen met het
      bouwen van het Word‑bestand.
    text: Doe een nieuw Document en een DocumentBuilder aan om te beginnen met het
      bouwen van het Word‑bestand.
  - name: Voeg een lijndiagram van grootte 500×300 in het document in en verkrijg
      het Chart‑object.
    text: Voeg een lijndiagram van grootte 500×300 in het document in en verkrijg
      het Chart‑object.
  - name: Verwijder de standaard demo‑reeks die Aspose.Words automatisch toevoegt.
    text: Verwijder de standaard demo‑reeks die Aspose.Words automatisch toevoegt.
  - name: Definieer een array met categorielabels die voor de X‑as worden gebruikt.
    text: Definieer een array met categorielabels die voor de X‑as worden gebruikt.
  - name: Voeg de primaire gegevensreeks met de naam \"Main Data\" toe met behulp
      van de labels en waarden.
    text: Voeg de primaire gegevensreeks met de naam \"Main Data\" toe met behulp
      van de labels en waarden.
  - name: Maak een secundaire seriesgroep van het type Line aan en wijs deze toe aan
      de secundaire as‑groep.
    text: Maak een secundaire seriesgroep van het type Line aan en wijs deze toe aan
      de secundaire as‑groep.
  - name: Stel de weergave‑eenheid van de secundaire X‑as in op duizenden zodat waarden
      worden weergegeven als K.
    text: Stel de weergave‑eenheid van de secundaire X‑as in op duizenden zodat waarden
      worden weergegeven als K.
  - name: Pas een aangepast numeriek formaat \"#,##0.0\" toe op de tick‑labels van
      de secundaire X‑as.
    text: Pas een aangepast numeriek formaat \"#,##0.0\" toe op de tick‑labels van
      de secundaire X‑as.
  - name: Voeg optioneel een aanvullende gegevensreeks toe aan de secundaire groep.
    text: Voeg optioneel een aanvullende gegevensreeks toe aan de secundaire groep.
  - name: Sla het document op als een .docx‑bestand.
    text: Sla het document op als een .docx‑bestand.
  type: HowTo
- questions:
  - answer: Nee – de `AxisX`‑instellingen behoren tot de `ChartSeriesGroup`, dus je
      kunt `secondaryGroup.AxisX.DisplayUnit.Unit` en `secondaryGroup.AxisX.NumberFormat.FormatCode`
      instellen vóór of na het toevoegen van reeksen; de configuratie wordt in beide
      gevallen op de as van de groep toegepast.
    question: Moet ik de secundaire reeks toevoegen voordat ik de weergave‑eenheid
      en het getalformaat op de secundaire X‑as instel?
  - answer: Ja – wijs een willekeurige `AxisBuiltInUnit`‑waarde toe, bijvoorbeeld
      `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` om de aswaarden
      in miljoenen weer te geven in plaats van in duizenden.
    question: Kan ik een andere ingebouwde eenheid, zoals miljoenen, gebruiken voor
      de secundaire X‑as?
  - answer: Nee – de opmaakcode wordt alleen toegepast op de as die je wijzigt (`secondaryGroup.AxisX.NumberFormat.FormatCode`),
      dus de primaire X‑as behoudt zijn standaardopmaak.
    question: Zal het aangepaste formaat \"#,##0.0\" invloed hebben op de labels van
      de primaire X‑as?
  - answer: Het diagram bevat dan de standaard demo‑reeks naast de door jou toegevoegde
      reeksen, wat kan leiden tot extra lijnen en niet‑overeenkomende categorieën;
      het wissen van de collectie zorgt ervoor dat alleen de door jou bedoelde gegevens
      verschijnen.
    question: Wat gebeurt er als ik vergeet de demo‑reeks te wissen met `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatteer de secundaire X‑as en stel eenheden in op duizenden
og_description: Voeg een secundaire X‑as toe aan een Word‑lijndiagram en formatteer de labels in duizenden met een aangepast patroon.
og_image_alt: Gids die laat zien hoe je een secundaire X‑as toevoegt aan een Word‑lijndiagram en de labels formatteert om eenheden in duizenden weer te geven met Aspose.Words voor .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatteer de secundaire X‑as en stel weergave‑eenheden in op duizenden in Word‑lijndiagrammen met Aspose.Words voor .NET
Deze tutorial leidt je stap voor stap door het maken van een Word‑document met een lijndiagram, het toevoegen van een secundaire X‑as, en het configureren van die as om waarden in duizenden weer te geven. Je leert ook hoe je een aangepast numeriek formaat toepast op de labels van de secundaire as, waardoor je nauwkeurige controle krijgt over hoe gegevens worden gepresenteerd. Volg de stappen om de leesbaarheid van multi‑as diagrammen in je Word‑rapporten te verbeteren.

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

**Q: Moet ik de secundaire reeks toevoegen voordat ik de weergave‑eenheid en het getalformaat op de secundaire X‑as instel?**  
A: Nee – de `AxisX`‑instellingen behoren tot de `ChartSeriesGroup`, dus je kunt `secondaryGroup.AxisX.DisplayUnit.Unit` en `secondaryGroup.AxisX.NumberFormat.FormatCode` instellen vóór of na het toevoegen van reeksen; de configuratie wordt in beide gevallen op de as van de groep toegepast.

**Q: Kan ik een andere ingebouwde eenheid, zoals miljoenen, gebruiken voor de secundaire X‑as?**  
A: Ja – wijs een willekeurige `AxisBuiltInUnit`‑waarde toe, bijvoorbeeld `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` om de aswaarden in miljoenen weer te geven in plaats van in duizenden.

**Q: Zal het aangepaste formaat \"#,##0.0\" invloed hebben op de labels van de primaire X‑as?**  
A: Nee – de opmaakcode wordt alleen toegepast op de as die je wijzigt (`secondaryGroup.AxisX.NumberFormat.FormatCode`), dus de primaire X‑as behoudt zijn standaardopmaak.

**Q: Wat gebeurt er als ik vergeet de demo‑reeks te wissen met `lineChart.Series.Clear();`?**  
A: Het diagram bevat dan de standaard demo‑reeks naast de door jou toegevoegde reeksen, wat kan leiden tot extra lijnen en niet‑overeenkomende categorieën; het wissen van de collectie zorgt ervoor dat alleen de door jou bedoelde gegevens verschijnen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
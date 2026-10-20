---
title: Grafiektitel bijwerken en legenda‑zichtbaarheid schakelen in Word met Aspose.Words voor .NET
weight: 810
limit:
description: Leer hoe je een grafiektitel wijzigt en de zichtbaarheid van de legenda regelt in een Word‑document met Aspose.Words voor .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Leer hoe je een grafiektitel wijzigt en de zichtbaarheid van de legenda
    regelt in een Word‑document met Aspose.Words voor .NET.
  headline: Grafiektitel bijwerken en legenda‑zichtbaarheid schakelen in Word met
    Aspose.Words voor .NET
  type: TechArticle
- description: Leer hoe je een grafiektitel wijzigt en de zichtbaarheid van de legenda
    regelt in een Word‑document met Aspose.Words voor .NET.
  name: Grafiektitel bijwerken en legenda‑zichtbaarheid schakelen in Word met Aspose.Words
    voor .NET
  steps:
  - name: Definieer de door de gebruiker opgegeven grafiektitel en of de legenda moet
      worden weergegeven.
    text: Definieer de door de gebruiker opgegeven grafiektitel en of de legenda moet
      worden weergegeven.
  - name: Maak een nieuw Word‑document en een DocumentBuilder aan om inhoud toe te
      voegen.
    text: Maak een nieuw Word‑document en een DocumentBuilder aan om inhoud toe te
      voegen.
  - name: Voeg een kolomgrafiek van 432 × 252 pt in het document in en controleer
      of de shape daadwerkelijk een grafiek bevat.
    text: Voeg een kolomgrafiek van 432 × 252 pt in het document in en controleer
      of de shape daadwerkelijk een grafiek bevat.
  - name: Haal het grafiekobject op, stel de titeltekst in op de waarde van de gebruiker,
      en zorg ervoor dat de titel wordt weergegeven.
    text: Haal het grafiekobject op, stel de titeltekst in op de waarde van de gebruiker,
      en zorg ervoor dat de titel wordt weergegeven.
  - name: 'Configureer de legenda: toon deze rechts indien gevraagd, anders verberg
      hem, en sta toe dat hij de plot‑area overlapt.'
    text: 'Configureer de legenda: toon deze rechts indien gevraagd, anders verberg
      hem, en sta toe dat hij de plot‑area overlapt.'
  - name: Sla het gewijzigde document op schijf op als CustomChart.docx.
    text: Sla het gewijzigde document op schijf op als CustomChart.docx.
  type: HowTo
- questions:
  - answer: Wanneer `displayLegend` `true` is, stelt de code `chartLegend.Position`
      in op `LegendPosition.Right`, waardoor de legenda zichtbaar wordt aan de rechterkant
      van de plot‑area; de eigenschap `Overlay` blijft `true`, zodat de legenda de
      grafiek kan overlappen om ruimte te besparen.
    question: Wat verandert het instellen van `displayLegend` op `true` in de gegenereerde
      grafiek?
  - answer: Stel `chartTitle.Show = false` in (of laat simpelweg het instellen van
      `Show` op `true` weg) na het toewijzen van `chartTitle.Text`; de titel wordt
      niet gerenderd in het Word‑document.
    question: Hoe kan ik de grafiektitel verbergen als de gebruiker er geen opgeeft?
  - answer: Ja—`InsertChart` retourneert een `Shape` die een grafiek zou moeten bevatten,
      maar het verifiëren van `HasChart` zorgt ervoor dat de shape daadwerkelijk een
      `Chart`‑object bevat; anders gooit de code een `InvalidOperationException`.
    question: Is het noodzakelijk om `chartContainer.HasChart` te controleren na het
      aanroepen van `InsertChart`?
  - answer: Zeker; ken een willekeurige waarde uit de `LegendPosition`‑enum toe (bijv.
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) aan `chartLegend.Position`
      om de legenda naar behoefte te verplaatsen.
    question: Kan ik de legenda ergens anders dan aan de rechterkant plaatsen?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Grafiektitel & legenda wijzigen in Word
og_description: Leer hoe je een aangepaste grafiektitel instelt en de weergave van de legenda regelt in een Word‑document met Aspose.Words voor .NET.
og_image_alt: Gids die code toont die een grafiektitel bijwerkt en de legenda schakelt in een Word‑document met Aspose.Words voor .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Grafiektitel bijwerken en legenda‑zichtbaarheid schakelen in Word met Aspose.Words voor .NET
Deze tutorial laat zien hoe je programmatically een grafiek in een Word‑document kunt aanpassen met Aspose.Words voor .NET. Je leert een kolomgrafiek in te voegen, de titel te vervangen door door de gebruiker geleverde tekst, en de zichtbaarheid en overlay van de legenda te regelen op basis van gebruikersvoorkeuren. Deze stappen stellen je in staat de weergave van de grafiek dynamisch aan te passen zonder handmatige bewerking.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Wat verandert het instellen van `displayLegend` op `true` in de gegenereerde grafiek?**  
A: Wanneer `displayLegend` `true` is, stelt de code `chartLegend.Position` in op `LegendPosition.Right`, waardoor de legenda zichtbaar wordt aan de rechterkant van de plot‑area; de eigenschap `Overlay` blijft `true`, zodat de legenda de grafiek kan overlappen om ruimte te besparen.

**Q: Hoe kan ik de grafiektitel verbergen als de gebruiker er geen opgeeft?**  
A: Stel `chartTitle.Show = false` in (of laat simpelweg het instellen van `Show` op `true` weg) na het toewijzen van `chartTitle.Text`; de titel wordt niet gerenderd in het Word‑document.

**Q: Is het noodzakelijk om `chartContainer.HasChart` te controleren na het aanroepen van `InsertChart`?**  
A: Ja—`InsertChart` retourneert een `Shape` die een grafiek zou moeten bevatten, maar het verifiëren van `HasChart` zorgt ervoor dat de shape daadwerkelijk een `Chart`‑object bevat; anders gooit de code een `InvalidOperationException`.

**Q: Kan ik de legenda ergens anders dan aan de rechterkant plaatsen?**  
A: Zeker; ken een willekeurige waarde uit de `LegendPosition`‑enum toe (bijv. `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) aan `chartLegend.Position` om de legenda naar behoefte te verplaatsen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
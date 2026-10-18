---
title: Grafiek proportioneel schalen bij het wijzigen van de paginagrootte in Word met Aspose.Words for .NET
weight: 210
limit:
description: Leer hoe je een Word‑kolomgrafiek automatisch laat schalen bij het wijzigen van het document naar A4 met Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Leer hoe je een Word‑kolomgrafiek automatisch laat schalen bij het
    wijzigen van het document naar A4 met Aspose.Words for .NET.
  headline: Grafiek proportioneel schalen bij het wijzigen van de paginagrootte in
    Word met Aspose.Words for .NET
  type: TechArticle
- description: Leer hoe je een Word‑kolomgrafiek automatisch laat schalen bij het
    wijzigen van het document naar A4 met Aspose.Words for .NET.
  name: Grafiek proportioneel schalen bij het wijzigen van de paginagrootte in Word
    met Aspose.Words for .NET
  steps:
  - name: Maak een nieuw Document‑object en een DocumentBuilder om het te bewerken.
    text: Maak een nieuw Document‑object en een DocumentBuilder om het te bewerken.
  - name: Voeg een kolomgrafiek van 432×252 punten in en verkrijg het bijbehorende
      Chart‑object.
    text: Voeg een kolomgrafiek van 432×252 punten in en verkrijg het bijbehorende
      Chart‑object.
  - name: Stel de titeltekst van de grafiek in op \"Quarterly Revenue\" en maak deze
      zichtbaar.
    text: Stel de titeltekst van de grafiek in op \"Quarterly Revenue\" en maak deze
      zichtbaar.
  - name: Sla het document op in een bestand waarin de oorspronkelijke grafiekgrootte
      wordt weergegeven.
    text: Sla het document op in een bestand waarin de oorspronkelijke grafiekgrootte
      wordt weergegeven.
  - name: Wijzig de papiergrootte van het document naar A4 en ververst de lay-out.
    text: Wijzig de papiergrootte van het document naar A4 en ververst de lay-out.
  - name: Bereken een nieuwe grafiekbreedte gelijk aan 80 % van de paginabreedte,
      terwijl de oorspronkelijke beeldverhouding behouden blijft.
    text: Bereken een nieuwe grafiekbreedte gelijk aan 80 % van de paginabreedte,
      terwijl de oorspronkelijke beeldverhouding behouden blijft.
  - name: Als de vorm een grafiek bevat, pas dan de berekende breedte en hoogte toe
      om deze te schalen.
    text: Als de vorm een grafiek bevat, pas dan de berekende breedte en hoogte toe
      om deze te schalen.
  - name: Sla het document op nadat de grafiek is geschaald om de nieuwe paginagrootte
      weer te geven.
    text: Sla het document op nadat de grafiek is geschaald om de nieuwe paginagrootte
      weer te geven.
  type: HowTo
- questions:
  - answer: Ja. Het wijzigen van `docBuilder.PageSetup.PaperSize` schaalt bestaande
      vormen niet automatisch, dus je moet zelf `chartContainer.Width` en `Height`
      opnieuw berekenen en toewijzen zoals getoond.
    question: Moet ik de grafiek handmatig schalen na het wijzigen van de papiergrootte
      van het document?
  - answer: Het slaat `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      op en berekent vervolgens `newChartHeight = newChartWidth * originalAspectRatio`
      nadat de nieuwe breedte is bepaald.
    question: Hoe behoudt de code de oorspronkelijke breedte‑tot‑hoogteverhouding
      van de grafiek bij het schalen?
  - answer: '`UpdatePageLayout()` dwingt de lay-outengine om de paginadimensies opnieuw
      te evalueren, zodat `docBuilder.PageSetup.PageWidth` de nieuwe A4‑breedte weergeeft
      voordat de grafiekgrootte opnieuw wordt berekend.'
    question: Waarom wordt `myDoc.UpdatePageLayout()` aangeroepen na het instellen
      van de papiergrootte op A4?
  - answer: De `if (chartContainer.HasChart)`‑controle voorkomt dat de code `Width`
      en `Height` toewijst wanneer er geen grafiek aanwezig is, waardoor een runtime‑exception
      wordt vermeden.
    question: Wat gebeurt er als de ingevoegde vorm eigenlijk geen grafiek bevat?
  - answer: Zeker—vervang de `0.8`‑vermenigvuldiger door elke gewenste verhouding;
      de rest van de schaallogica behoudt nog steeds de oorspronkelijke beeldverhouding.
    question: Kan ik de 80 %‑schaalfactor wijzigen naar een andere waarde?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Grafiek in Word schalen bij overschakelen naar A4
og_description: Houd je grafiek evenredig door deze automatisch te schalen nadat het document naar A4 is gewijzigd.
og_image_alt: Schermafbeelding die een kolomgrafiek toont die automatisch is geschaald om te passen in een A4‑groot Word‑document met Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Grafiek proportioneel schalen bij het wijzigen van de paginagrootte in Word met Aspose.Words
Deze tutorial laat zien hoe je een kolomgrafiek in een Word‑document invoegt, de paginagrootte van het document wijzigt naar A4, en de grafiek automatisch laat schalen zodat deze evenredig blijft met de nieuwe paginabreedte. Door de stappen te volgen, zie je hoe de grafiek zijn afmetingen aanpast zonder handmatige schaalverandering, waardoor een consistente lay-out ontstaat over verschillende paginavormen.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Moet ik de grafiek handmatig schalen na het wijzigen van de papiergrootte van het document?**  
A: Ja. Het wijzigen van `docBuilder.PageSetup.PaperSize` schaalt bestaande vormen niet automatisch, dus je moet zelf `chartContainer.Width` en `Height` opnieuw berekenen en toewijzen zoals getoond.

**Q: Hoe behoudt de code de oorspronkelijke breedte‑tot‑hoogteverhouding van de grafiek bij het schalen?**  
A: Het slaat `originalAspectRatio = chartContainer.Height / chartContainer.Width` op en berekent vervolgens `newChartHeight = newChartWidth * originalAspectRatio` nadat de nieuwe breedte is bepaald.

**Q: Waarom wordt `myDoc.UpdatePageLayout()` aangeroepen na het instellen van de papiergrootte op A4?**  
A: `UpdatePageLayout()` dwingt de lay-outengine om de paginadimensies opnieuw te evalueren, zodat `docBuilder.PageSetup.PageWidth` de nieuwe A4‑breedte weergeeft voordat de grafiekgrootte opnieuw wordt berekend.

**Q: Wat gebeurt er als de ingevoegde vorm eigenlijk geen grafiek bevat?**  
A: De `if (chartContainer.HasChart)`‑controle voorkomt dat de code `Width` en `Height` toewijst wanneer er geen grafiek aanwezig is, waardoor een runtime‑exception wordt vermeden.

**Q: Kan ik de 80 %‑schaalfactor wijzigen naar een andere waarde?**  
A: Zeker—vervang de `0.8`‑vermenigvuldiger door elke gewenste verhouding; de rest van de schaallogica behoudt nog steeds de oorspronkelijke beeldverhouding.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
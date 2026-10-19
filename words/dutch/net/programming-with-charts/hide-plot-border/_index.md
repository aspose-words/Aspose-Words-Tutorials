---
title: Plot Area Border verbergen in een column chart met Aspose.Words for .NET
weight: 410
limit:
description: Leer hoe je de plot area border van een chart verbergt terwijl de aslijnen zichtbaar blijven in een Word column chart met Aspose.Words for .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Leer hoe je de plot area border van een chart verbergt terwijl de aslijnen
    zichtbaar blijven in een Word column chart met Aspose.Words for .NET.
  headline: Plot Area Border verbergen in een column chart met Aspose.Words for .NET
  type: TechArticle
- description: Leer hoe je de plot area border van een chart verbergt terwijl de aslijnen
    zichtbaar blijven in een Word column chart met Aspose.Words for .NET.
  name: Plot Area Border verbergen in een column chart met Aspose.Words for .NET
  steps:
  - name: Maak een nieuw leeg Word‑document en een DocumentBuilder om het te bewerken.
    text: Maak een nieuw leeg Word‑document en een DocumentBuilder om het te bewerken.
  - name: Voeg een column chart van 432×252 toe aan het document en verkrijg het Chart‑object.
    text: Voeg een column chart van 432×252 toe aan het document en verkrijg het Chart‑object.
  - name: Verwijder eventuele bestaande series, definieer drie categorie‑labels en
      voeg een serie met voorbeeldwaarden toe aan de chart.
    text: Verwijder eventuele bestaande series, definieer drie categorie‑labels en
      voeg een serie met voorbeeldwaarden toe aan de chart.
  - name: Stel het stroke‑gewicht van het plot‑gebied in op nul, waardoor de rand
      wordt verwijderd terwijl de aslijnen zichtbaar blijven.
    text: Stel het stroke‑gewicht van het plot‑gebied in op nul, waardoor de rand
      wordt verwijderd terwijl de aslijnen zichtbaar blijven.
  - name: Sla het gewijzigde document op als een .docx‑bestand.
    text: Sla het gewijzigde document op als een .docx‑bestand.
  type: HowTo
- questions:
  - answer: De `Stroke`‑eigenschap behoort tot het algemene formaat van het `Chart`‑object,
      dat de rechthoekige rand rond het plot‑gebied tekent; aslijnen zijn afzonderlijke
      `Axis`‑objecten en worden niet beïnvloed door de `Stroke`‑instellingen van de
      chart.
    question: Waarom zorgt het instellen van `columnChart.Format.Stroke.Weight = 0`
      ervoor dat de plot area border wordt verwijderd, maar de aslijnen zichtbaar
      blijven?
  - answer: Nee, de `Stroke`‑eigenschap regelt de volledige plot area border als één
      rechthoek, dus gedeeltelijke randen kunnen niet worden verborgen via Aspose.Words;
      je zou aangepaste vormen moeten overleggen of de chart handmatig moeten bewerken.
    question: Kan ik slechts één zijde van de plot area border verbergen (bijv. de
      linkerkant) terwijl de andere drie zijden zichtbaar blijven?
  - answer: Ja, de `Stroke`‑eigenschap staat los van `ChartType`, dus het instellen
      van de `Weight` op 0 verwijdert de plot area border voor Line, Pie of elk ander
      ondersteund chart‑type.
    question: Als ik het chart‑type wijzig naar Line of Pie, zal `columnChart.Format.Stroke.Weight
      = 0` dan nog steeds de plot area border verbergen?
  - answer: Er is geen extra vernieuwing nodig; het wissen van de series en het toevoegen
      van een nieuwe werkt de chart intern bij, en `wordDoc.Save(...)` schrijft de
      huidige staat naar het .docx‑bestand.
    question: Moet ik de chart vernieuwen na het aanroepen van `columnChart.Series.Clear()`,
      voordat ik het document opsla?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Plot‑rand verbergen in een Word column chart
og_description: Verwijder de plot area border terwijl de aslijnen zichtbaar blijven in een Word column chart met Aspose.Words for .NET.
og_image_alt: Gids die een Word‑document toont met een column chart waarin de plot area border verborgen is, maar de aslijnen zichtbaar blijven, met Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Plot Area Border verbergen in een column chart met Aspose.Words
In deze tutorial leer je hoe je een Word‑document genereert, een column chart invoegt, deze vult met voorbeeldgegevens, en vervolgens de plot area border van de chart verbergt terwijl de aslijnen zichtbaar blijven. De stap‑voor‑stap code demonstreert elke bewerking en eindigt met het opslaan van het document, zodat je het resultaat meteen kunt zien.

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

**Q: Waarom zorgt het instellen van `columnChart.Format.Stroke.Weight = 0` ervoor dat de plot area border wordt verwijderd, maar de aslijnen zichtbaar blijven?**  
A: De `Stroke`‑eigenschap behoort tot het algemene formaat van het `Chart`‑object, dat de rechthoekige rand rond het plot‑gebied tekent; aslijnen zijn afzonderlijke `Axis`‑objecten en worden niet beïnvloed door de `Stroke`‑instellingen van de chart.

**Q: Kan ik slechts één zijde van de plot area border verbergen (bijv. de linkerkant) terwijl de andere drie zijden zichtbaar blijven?**  
A: Nee, de `Stroke`‑eigenschap regelt de volledige plot area border als één rechthoek, dus gedeeltelijke randen kunnen niet worden verborgen via Aspose.Words; je zou aangepaste vormen moeten overleggen of de chart handmatig moeten bewerken.

**Q: Als ik het chart‑type wijzig naar Line of Pie, zal `columnChart.Format.Stroke.Weight = 0` dan nog steeds de plot area border verbergen?**  
A: Ja, de `Stroke`‑eigenschap staat los van `ChartType`, dus het instellen van de `Weight` op 0 verwijdert de plot area border voor Line, Pie of elk ander ondersteund chart‑type.

**Q: Moet ik de chart vernieuwen na het aanroepen van `columnChart.Series.Clear()`, voordat ik het document opsla?**  
A: Er is geen extra vernieuwing nodig; het wissen van de series en het toevoegen van een nieuwe werkt de chart intern bij, en `wordDoc.Save(...)` schrijft de huidige staat naar het .docx‑bestand.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
---
title: Uppdatera diagramtitel och växla legendens synlighet i Word med Aspose.Words för .NET
weight: 810
limit:
description: Lär dig att ändra en diagramtitel och kontrollera legendens synlighet i ett Word‑dokument med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig att ändra en diagramtitel och kontrollera legendens synlighet
    i ett Word‑dokument med Aspose.Words för .NET.
  headline: Uppdatera diagramtitel och växla legendens synlighet i Word med Aspose.Words
    för .NET
  type: TechArticle
- description: Lär dig att ändra en diagramtitel och kontrollera legendens synlighet
    i ett Word‑dokument med Aspose.Words för .NET.
  name: Uppdatera diagramtitel och växla legendens synlighet i Word med Aspose.Words
    för .NET
  steps:
  - name: Definiera den användar‑tillhandahållna diagramtiteln och om legenden ska
      visas.
    text: Definiera den användar‑tillhandahållna diagramtiteln och om legenden ska
      visas.
  - name: Skapa ett nytt Word‑dokument och en DocumentBuilder för att lägga till innehåll.
    text: Skapa ett nytt Word‑dokument och en DocumentBuilder för att lägga till innehåll.
  - name: Infoga ett stapeldiagram på 432 × 252 pt i dokumentet och verifiera att
      formen faktiskt innehåller ett diagram.
    text: Infoga ett stapeldiagram på 432 × 252 pt i dokumentet och verifiera att
      formen faktiskt innehåller ett diagram.
  - name: Hämta diagramobjektet, sätt dess titeltext till användarvärdet och säkerställ
      att titeln visas.
    text: Hämta diagramobjektet, sätt dess titeltext till användarvärdet och säkerställ
      att titeln visas.
  - name: 'Konfigurera legenden: visa den till höger om så begärs, annars dölj den,
      och låt den överlappa plotområdet.'
    text: 'Konfigurera legenden: visa den till höger om så begärs, annars dölj den,
      och låt den överlappa plotområdet.'
  - name: Spara det modifierade dokumentet på disk som CustomChart.docx.
    text: Spara det modifierade dokumentet på disk som CustomChart.docx.
  type: HowTo
- questions:
  - answer: När `displayLegend` är `true` sätter koden `chartLegend.Position` till
      `LegendPosition.Right`, vilket gör legenden synlig på högra sidan av plotområdet;
      egenskapen `Overlay` förblir `true`, så legenden kan överlappa diagrammet för
      att spara utrymme.
    question: Vad förändras i det genererade diagrammet när `displayLegend` sätts
      till `true`?
  - answer: Sätt `chartTitle.Show = false` (eller utelämna helt enkelt att sätta `Show`
      till `true`) efter att ha tilldelat `chartTitle.Text`; titeln kommer inte att
      renderas i Word‑dokumentet.
    question: Hur kan jag dölja diagramtiteln om användaren inte anger någon?
  - answer: Ja—`InsertChart` returnerar en `Shape` som bör innehålla ett diagram,
      men att verifiera `HasChart` säkerställer att formen faktiskt har ett `Chart`‑objekt;
      annars kastar koden ett `InvalidOperationException`.
    question: Är det nödvändigt att kontrollera `chartContainer.HasChart` efter att
      ha anropat `InsertChart`?
  - answer: Absolut; tilldela ett valfritt värde från `LegendPosition`‑enumet (t.ex.
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) till `chartLegend.Position`
      för att omplacera legenden efter behov.
    question: Kan jag placera legenden någon annanstans än på högra sidan?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Ändra diagramtitel och legend i Word
og_description: Lär dig att ange en anpassad diagramtitel och kontrollera legendens visning i ett Word‑dokument med Aspose.Words för .NET.
og_image_alt: Guide som visar kod som uppdaterar en diagramtitel och växlar legenden i ett Word‑dokument med Aspose.Words för .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uppdatera diagramtitel och växla legendens synlighet i Word med Aspose.Words för .NET
Denna handledning visar hur man programatiskt modifierar ett diagram i ett Word‑dokument med Aspose.Words för .NET. Du kommer att lära dig att infoga ett stapeldiagram, ersätta dess titel med text som användaren har angett, samt kontrollera legendens synlighet och överlagring baserat på användarens preferenser. Dessa steg låter dig anpassa diagrampresentationen dynamiskt utan manuell redigering.

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

**Q: Vad förändras i det genererade diagrammet när `displayLegend` sätts till `true`?**  
A: När `displayLegend` är `true` sätter koden `chartLegend.Position` till `LegendPosition.Right`, vilket gör legenden synlig på högra sidan av plotområdet; egenskapen `Overlay` förblir `true`, så legenden kan överlappa diagrammet för att spara utrymme.

**Q: Hur kan jag dölja diagramtiteln om användaren inte anger någon?**  
A: Sätt `chartTitle.Show = false` (eller utelämna helt enkelt att sätta `Show` till `true`) efter att ha tilldelat `chartTitle.Text`; titeln kommer inte att renderas i Word‑dokumentet.

**Q: Är det nödvändigt att kontrollera `chartContainer.HasChart` efter att ha anropat `InsertChart`?**  
A: Ja—`InsertChart` returnerar en `Shape` som bör innehålla ett diagram, men att verifiera `HasChart` säkerställer att formen faktiskt har ett `Chart`‑objekt; annars kastar koden ett `InvalidOperationException`.

**Q: Kan jag placera legenden någon annanstans än på högra sidan?**  
A: Absolut; tilldela ett valfritt värde från `LegendPosition`‑enumet (t.ex. `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) till `chartLegend.Position` för att omplacera legenden efter behov.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
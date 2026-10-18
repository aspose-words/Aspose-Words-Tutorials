---
title: Ställ in enhetliga data‑labels i ett stapeldiagram med Aspose.Words för .NET
weight: 110
limit:
description: Lär dig skapa ett Word‑stapeldiagram och tillämpa enhetlig data‑label teckenstorlek och färg på alla serier med Aspose.Words för .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Lär dig skapa ett Word‑stapeldiagram och tillämpa enhetlig data‑label
    teckenstorlek och färg på alla serier med Aspose.Words för .NET.
  headline: Ställ in enhetliga data‑labels i ett stapeldiagram med Aspose.Words för
    .NET
  type: TechArticle
- description: Lär dig skapa ett Word‑stapeldiagram och tillämpa enhetlig data‑label
    teckenstorlek och färg på alla serier med Aspose.Words för .NET.
  name: Ställ in enhetliga data‑labels i ett stapeldiagram med Aspose.Words för .NET
  steps:
  - name: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
    text: Skapa ett nytt tomt Word‑dokument och en DocumentBuilder för att redigera
      det.
  - name: Infoga ett 500×300 stapeldiagram i dokumentet och hämta dess Chart‑objekt.
    text: Infoga ett 500×300 stapeldiagram i dokumentet och hämta dess Chart‑objekt.
  - name: Ta bort den förvalda exempelserien som Aspose.Words lägger till i ett nytt
      diagram.
    text: Ta bort den förvalda exempelserien som Aspose.Words lägger till i ett nytt
      diagram.
  - name: Definiera kategorimärkningar och lägg till två dataserier (Item Alpha och
      Item Beta) med deras värden i diagrammet.
    text: Definiera kategorimärkningar och lägg till två dataserier (Item Alpha och
      Item Beta) med deras värden i diagrammet.
  - name: Ange grundteckenstorlek och färg som kommer att tillämpas på alla data‑labels.
    text: Ange grundteckenstorlek och färg som kommer att tillämpas på alla data‑labels.
  - name: Aktivera data‑labels för varje serie, visa det numeriska värdet och tillämpa
      den fördefinierade teckenstorleken och färgen.
    text: Aktivera data‑labels för varje serie, visa det numeriska värdet och tillämpa
      den fördefinierade teckenstorleken och färgen.
  - name: Spara dokumentet som en .docx‑fil.
    text: Spara dokumentet som en .docx‑fil.
  type: HowTo
- questions:
  - answer: '`InsertChart` skapar ett diagram med en förvald exempelserie; genom att
      rensa den tas platshållaren bort så att diagrammet endast visar de serier du
      lägger till (`Item Alpha` och `Item Beta`).'
    question: Varför måste jag anropa `chart.Series.Clear()` innan jag lägger till
      mina egna serier?
  - answer: Byt ut `Color.White` mot vilket `System.Drawing.Color`‑värde som helst,
      t.ex. `Color.Black` eller `Color.FromArgb(255, 30, 144, 255)`; den nya färgen
      tillämpas via `series.DataLabels.Font.Color` i loopen.
    question: Hur kan jag ändra data‑label färgen till något annat än vitt?
  - answer: Data‑labels kommer att döljas, så de teckensnittinställningar du applicerat
      blir osynliga; du måste behålla `HasDataLabels` satt till `true` för att etiketterna
      (och deras stil) ska visas.
    question: Vad händer om jag sätter `series.HasDataLabels = false` efter att ha
      konfigurerat teckenstorlek och färg?
  - answer: Ja—varje `ChartSeries` har sitt eget `DataLabels`‑objekt, så varje serie
      som läggs till efter den första loopen måste också ha `HasDataLabels`, `ShowValue`
      och teckensnittsegenskaperna satta, antingen genom att loopa igen eller genom
      att extrahera stilen till en hjälpfunktion.
    question: Behöver jag loopa igenom serierna igen om jag lägger till en annan serie
      senare i koden?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Tillämpa enhetliga data‑labels på ett Word‑diagram
og_description: Ge snabbt varje diagrametikett samma teckenstorlek och färg med Aspose.Words för .NET.
og_image_alt: Guide som visar ett Word‑dokument med ett stapeldiagram där alla data‑labels delar samma teckenstorlek och färg, skapat med Aspose.Words för .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in enhetliga data‑labels i ett stapeldiagram med Aspose.Words för .NET
Denna handledning visar hur man genererar ett Word‑dokument, infogar ett stapeldiagram och lägger till anpassade dataserier med Aspose.Words för .NET. Den demonstrerar sedan hur man definierar standard data‑label teckenstorlek och färg så att varje serie i diagrammet visar identiska etiketter. Genom att använda en enda stil säkerställer du en konsekvent visuell framtoning i hela diagrammet.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: Varför måste jag anropa `chart.Series.Clear()` innan jag lägger till mina egna serier?**  
A: `InsertChart` skapar ett diagram med en förvald exempelserie; genom att rensa den tas platshållaren bort så att diagrammet endast visar de serier du lägger till (`Item Alpha` och `Item Beta`).

**Q: Hur kan jag ändra data‑label färgen till något annat än vitt?**  
A: Byt ut `Color.White` mot vilket `System.Drawing.Color`‑värde som helst, t.ex. `Color.Black` eller `Color.FromArgb(255, 30, 144, 255)`; den nya färgen tillämpas via `series.DataLabels.Font.Color` i loopen.

**Q: Vad händer om jag sätter `series.HasDataLabels = false` efter att ha konfigurerat teckenstorlek och färg?**  
A: Data‑labels kommer att döljas, så de teckensnittinställningar du applicerat blir osynliga; du måste behålla `HasDataLabels` satt till `true` för att etiketterna (och deras stil) ska visas.

**Q: Behöver jag loopa igenom serierna igen om jag lägger till en annan serie senare i koden?**  
A: Ja—varje `ChartSeries` har sitt eget `DataLabels`‑objekt, så varje serie som läggs till efter den första loopen måste också ha `HasDataLabels`, `ShowValue` och teckensnittsegenskaperna satta, antingen genom att loopa igen eller genom att extrahera stilen till en hjälpfunktion.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
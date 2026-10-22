---
title: Nastavte jednotné popisky dat ve sloupcovém grafu pomocí Aspose.Words pro .NET
weight: 110
limit:
description: Naučte se vytvořit sloupcový graf ve Wordu a aplikovat jednotnou velikost písma a barvu popisků dat na všechny řady pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se vytvořit sloupcový graf ve Wordu a aplikovat jednotnou velikost
    písma a barvu popisků dat na všechny řady pomocí Aspose.Words pro .NET.
  headline: Nastavte jednotné popisky dat ve sloupcovém grafu pomocí Aspose.Words
    pro .NET
  type: TechArticle
- description: Naučte se vytvořit sloupcový graf ve Wordu a aplikovat jednotnou velikost
    písma a barvu popisků dat na všechny řady pomocí Aspose.Words pro .NET.
  name: Nastavte jednotné popisky dat ve sloupcovém grafu pomocí Aspose.Words pro
    .NET
  steps:
  - name: Vytvořte nový prázdný dokument Word a DocumentBuilder pro jeho úpravu.
    text: Vytvořte nový prázdný dokument Word a DocumentBuilder pro jeho úpravu.
  - name: Vložte do dokumentu sloupcový graf o rozměrech 500×300 a získejte jeho objekt
      Chart.
    text: Vložte do dokumentu sloupcový graf o rozměrech 500×300 a získejte jeho objekt
      Chart.
  - name: Odstraňte výchozí ukázkovou řadu, kterou Aspose.Words přidává do nového
      grafu.
    text: Odstraňte výchozí ukázkovou řadu, kterou Aspose.Words přidává do nového
      grafu.
  - name: Definujte štítky kategorií a přidejte do grafu dvě datové řady (Item Alpha
      a Item Beta) s jejich hodnotami.
    text: Definujte štítky kategorií a přidejte do grafu dvě datové řady (Item Alpha
      a Item Beta) s jejich hodnotami.
  - name: Nastavte základní velikost písma a barvu, které budou použity pro všechny
      popisky dat.
    text: Nastavte základní velikost písma a barvu, které budou použity pro všechny
      popisky dat.
  - name: Povolte popisky dat pro každou řadu, zobrazte číselnou hodnotu a použijte
      předdefinovanou velikost písma a barvu.
    text: Povolte popisky dat pro každou řadu, zobrazte číselnou hodnotu a použijte
      předdefinovanou velikost písma a barvu.
  - name: Uložte dokument do souboru .docx.
    text: Uložte dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` vytvoří graf s výchozí ukázkovou řadou; její vymazání odstraní
      tento zástupný prvek, takže graf zobrazí pouze řady, které přidáte (`Item Alpha`
      a `Item Beta`).'
    question: Proč musím zavolat `chart.Series.Clear()` před přidáním vlastních řad?
  - answer: Nahraďte `Color.White` libovolnou hodnotou `System.Drawing.Color`, např.
      `Color.Black` nebo `Color.FromArgb(255, 30, 144, 255)`; nová barva se aplikuje
      pomocí `series.DataLabels.Font.Color` uvnitř smyčky.
    question: Jak mohu změnit barvu popisku dat na jinou než bílou?
  - answer: Popisky dat budou skryté, takže nastavené vlastnosti písma budou neviditelné;
      musíte ponechat `HasDataLabels` nastaveno na `true`, aby se popisky (a jejich
      styl) zobrazily.
    question: Co se stane, když po nastavení velikosti písma a barvy nastavím `series.HasDataLabels
      = false`?
  - answer: Ano — každá `ChartSeries` má svůj vlastní objekt `DataLabels`, takže jakákoli
      řada přidaná po úvodní smyčce musí mít také nastavené `HasDataLabels`, `ShowValue`
      a vlastnosti písma, a to buď dalším průchodem smyčkou, nebo extrahováním stylování
      do pomocné metody.
    question: Musím projít řady znovu, pokud později v kódu přidám další řadu?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Použijte jednotné popisky dat v grafu Wordu
og_description: Rychle nastavte stejnou velikost písma a barvu pro všechny popisky grafu pomocí Aspose.Words pro .NET.
og_image_alt: Průvodce ukazující dokument Word se sloupcovým grafem, kde všechny popisky dat sdílejí stejnou velikost písma a barvu, vytvořený pomocí Aspose.Words pro .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte jednotné popisky dat ve sloupcovém grafu pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak vytvořit dokument Word, vložit sloupcový graf a přidat vlastní datové řady pomocí Aspose.Words pro .NET. Poté demonstruje definování výchozí velikosti písma a barvy popisků dat, aby každá řada v grafu zobrazovala identické popisky. Použitím jedné styly zajistíte konzistentní vizuální vzhled celého grafu.

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

**Q: Proč musím zavolat `chart.Series.Clear()` před přidáním vlastních řad?**  
A: `InsertChart` vytvoří graf s výchozí ukázkovou řadou; její vymazání odstraní tento zástupný prvek, takže graf zobrazí pouze řady, které přidáte (`Item Alpha` a `Item Beta`).

**Q: Jak mohu změnit barvu popisku dat na jinou než bílou?**  
A: Nahraďte `Color.White` libovolnou hodnotou `System.Drawing.Color`, např. `Color.Black` nebo `Color.FromArgb(255, 30, 144, 255)`; nová barva se aplikuje pomocí `series.DataLabels.Font.Color` uvnitř smyčky.

**Q: Co se stane, když po nastavení velikosti písma a barvy nastavím `series.HasDataLabels = false`?**  
A: Popisky dat budou skryté, takže nastavené vlastnosti písma budou neviditelné; musíte ponechat `HasDataLabels` nastaveno na `true`, aby se popisky (a jejich styl) zobrazily.

**Q: Musím projít řady znovu, pokud později v kódu přidám další řadu?**  
A: Ano — každá `ChartSeries` má svůj vlastní objekt `DataLabels`, takže jakákoli řada přidaná po úvodní smyčce musí mít také nastavené `HasDataLabels`, `ShowValue` a vlastnosti písma, a to buď dalším průchodem smyčkou, nebo extrahováním stylování do pomocné metody.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
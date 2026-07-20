---
category: general
date: 2026-07-19
description: Oddělte výseč koláčového grafu pomocí Aspose.Words pro C#. Naučte se,
  jak oddělit výseč koláče, upravit velikost díry v donut grafu a rychle měnit datové
  body grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: cs
lastmod: 2026-07-19
og_description: Rozbalte výseč koláčového grafu pomocí Aspose.Words pro C#. Tento
  průvodce vám ukáže, jak rozbalit výseč koláče, upravit velikost díry v prstenci
  a efektivně měnit datové body grafu.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Oddělit výsek koláčového grafu v C# – tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Rozbalení výseče koláčového grafu v C# s Aspose.Words – Kompletní průvodce
url: /cs/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozdělení výseče koláčového grafu v C# pomocí Aspose.Words – Kompletní průvodce

Už jste se někdy zamýšleli, jak **rozdělit výseč koláčového grafu** v dokumentu Word pomocí C#? Nejste jediní. Ať už připravujete obchodní prezentaci nebo vizualizujete výsledky průzkumu, rozdělená výseč přitáhne pozornost přesně tam, kde ji chcete. V tomto tutoriálu projdeme celý proces – načtení dokumentu, získání grafu, rozdělení první výseče, úpravu velikosti díry u prstencového grafu a dokonce změnu datových bodů grafu.

Dozvíte se také o sekundárních konceptech, které můžete hledat: **jak rozdělit výseč koláčového grafu**, **upravit velikost díry prstence** a **změnit datové body grafu**. Žádné zbytečnosti, jen kompletní řešení připravené ke zkopírování a vložení.

---

## Co budete potřebovat

Než začneme, ujistěte se, že máte:

- **Aspose.Words for .NET** (nejnovější verze k 19. 07. 2026). Můžete ji získat z NuGet pomocí `Install-Package Aspose.Words`.
- Projekt **.NET 6+** (nebo .NET Framework 4.7.2+, pokud stále používáte starší verzi).
- Soubor Word (`Chart.docx`), který již obsahuje koláčový nebo prstencový graf. Pokud ho nemáte, rychle si vytvořte graf ve Wordu a uložte jej.

To je vše – žádné další knihovny, žádné COM interop, jen čistý spravovaný kód.

---

## Rozdělení výseče koláčového grafu – krok za krokem

Níže rozdělujeme úkol na malé kroky. Každá část má jasný nadpis, úryvek kódu a stručné vysvětlení *proč* děláme to, co děláme.

### Krok 1: Instalace a reference Aspose.Words

Nejprve přidejte balíček Aspose.Words do svého projektu. V Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Tip:** Pokud používáte vestavěné NuGet UI ve Visual Studiu, vyhledejte „Aspose.Words“ a klikněte na Install. Tím získáte nejnovější opravy chyb a možnost pracovat s grafy přímo z krabice.

### Krok 2: Načtení dokumentu Word obsahujícího graf

Potřebujeme objekt `Document`, který ukazuje na `.docx` s grafem, který chcete upravit.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Proč je to důležité:** `Document` je vstupní bod pro každou operaci v Aspose.Words. Kontrolou existence grafu už na začátku se vyhneme výjimce null reference, když budeme chtít rozdělit výseč.

### Krok 3: Získání prvního uzlu grafu

Většina příkladů předpokládá jediný graf, takže si vezmeme první. Pokud máte více grafů, upravte index podle potřeby.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Poznámka:** Přetypování na `Chart` je bezpečné poté, co jsme potvrdili, že graf existuje. Tento objekt nám poskytuje přístup k sériím, datovým bodům a nastavením specifickým pro typ grafu.

### Krok 4: Rozdělení první výseče koláčového grafu

Teď hlavní část – **jak rozdělit výseč koláčového grafu**. Nastavíme vlastnost `Exploded` prvního datového bodu.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Proč to funguje:** `Exploded` říká Wordu, aby tuto výseč vytáhl od středu, čímž vytvoří klasický efekt „exploded pie“. Vlastnost je typu boolean, takže nastavení na `true` stačí.

### Krok 5: Úprava velikosti díry prstence (pokud jde o prstencový graf)

Pokud je váš graf prstencový, můžete **upravit velikost díry prstence**. Velikost díry je procento poloměru grafu.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Co číslo znamená:** Hodnota `30` znamená, že vnitřní kruh zabere 30 % celkového poloměru, což zanechá silnější vnější prstenec.

### Krok 6: Změna datových bodů grafu (volitelné)

Někdy potřebujete **změnit datové body grafu** – třeba jste aktualizovali podkladová čísla a chcete, aby se vizualizace automaticky přizpůsobila.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Proč to dělat:** Změna hodnoty datového bodu automaticky přepočítá procenta výsečí, takže graf zůstane přesný bez ruční úpravy ve Wordu.

### Krok 7: Uložení upraveného dokumentu

Nakonec zapíšeme změny na disk. Můžete přepsat původní soubor nebo vytvořit nový – jak vám to vyhovuje.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Tip:** Použijte `SaveFormat.Docx`, pokud chcete být explicitní, ale `Save(string)` automaticky detekuje formát podle přípony souboru.

---

## Očekávaný výsledek

Po otevření `FormattedChart.docx` v Microsoft Word byste měli vidět:

- První výseč koláčového grafu **roztaženou** ven.
- Pokud jde o prstencový graf, středová díra nyní zabírá **30 %** poloměru.
- Jakékoli upravené datové body odrážejí nové hodnoty, které jste nastavili.

Níže je ilustrativní náhled, jak vypadá rozdělená výseč (obrázek jen pro ilustraci).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Alt text:* **exploded pie chart slice** zobrazující oddělený segment v dokumentu Word.

---

## Často kladené otázky a okrajové případy

**Co když graf není koláčový ani prstencový?**  
Kód kontroluje `ChartType` před aplikací `Exploded` nebo `HoleSize`. U sloupcových, čárových nebo plošných grafů tyto vlastnosti neexistují, takže logika je bezpečně přeskočena.

**Mohu rozdělit více výsečí?**  
Určitě. Projděte `chart.PieChartData.Series[0].DataPoints` a nastavte `Exploded = true` na libovolném indexu.

**Musím řešit formáty čísel podle kultury?**  
Aspose.Words ukládá číselné hodnoty jako double, nezávisle na locale, takže se nemusíte starat o čárky vs tečky.

**Co když jsou grafy vloženy do záhlaví/pati?**  
Použijte `doc.GetChildNodes(NodeType.Chart, true)` k získání všech grafů a pak zkontrolujte `ParentNode` každého uzlu, abyste zjistili, kde se nachází. Stejná logika rozdělení se použije.

---

## Závěr

Nyní máte solidní, připravené řešení ke **rozdělení výseče koláčového grafu** pomocí Aspose.Words v C#. Prošli jsme celým pracovním tokem – od načtení dokumentu, získání grafu, rozdělení výseče, **úpravou velikosti díry prstence**, až po **změnu datových bodů grafu** a nakonec uložení souboru.

Klidně experimentujte: rozdělete jinou výseč, nastavte velikost díry na 45 %, nebo najednou aktualizujte několik datových bodů. API Aspose.Words tyto úpravy provádí bez námahy a změny se projeví okamžitě po otevření souboru Word.

---

### Co dál?

- **Formátování rozdělené výseče** (změna barvy výplně, okraje nebo přidání popisku dat). Vyhledejte „Aspose.Words chart formatting“.
- **Automatizace hromadného zpracování** více dokumentů – projděte složku, rozdělete výseče a uložte nové verze.
- **Kombinace s Aspose.Slides**, pokud potřebujete stejný graf v prezentaci PowerPoint.

Máte další otázky ohledně manipulace s grafy, nebo chcete jít hlouběji do dalších typů grafů? Zanechte komentář níže a šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným krok‑za‑krokem vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
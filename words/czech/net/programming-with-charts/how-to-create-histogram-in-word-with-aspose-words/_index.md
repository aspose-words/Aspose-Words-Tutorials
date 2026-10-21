---
category: general
date: 2026-09-21
description: Jak vytvořit histogram ve Wordu s Aspose.Words. Naučte se nastavit intervaly
  histogramu a konfigurovat je pro přesnou vizualizaci dat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: cs
lastmod: 2026-09-21
og_description: Jak vytvořit histogram ve Wordu pomocí Aspose.Words. Tento tutoriál
  vám ukáže, jak nastavit intervaly histogramu a nakonfigurovat je pro přesné grafy.
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: Vytvořte histogram ve Wordu s Aspose.Words – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: Jak vytvořit histogram ve Wordu pomocí Aspose.Words
url: /cs/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit histogram ve Wordu pomocí Aspose.Words

Pokud potřebujete ve Wordu vytvořit histogram, Aspose.Words proces zjednodušuje. Tento průvodce vás provede každým krokem, od nastavení projektu až po konfiguraci intervalů histogramu pro přehlednou prezentaci dat. Také uvidíte, jak nastavit intervaly histogramu a nakonfigurovat je tak, aby odpovídaly vašim požadavkům na reportování.

## Jak vytvořit histogram ve Wordu – celkový workflow

Celkový workflow se skládá ze čtyř logických fází:

1. Připravte vývojové prostředí.  
2. Vytvořte prázdný Word dokument a získejte `DocumentBuilder`.  
3. Vložte histogram a upravte jeho vlastnosti.  
4. Uložte dokument a ověřte výsledek.

Každá fáze je podrobně popsána níže a kompletní zdrojový kód je uveden na konci článku.

## Nastavení vývojového prostředí

Než napíšete jakýkoli kód, ujistěte se, že máte následující předpoklady:

| Požadavek | Důvod |
|--------------|--------|
| .NET 6.0 nebo novější | Poskytuje runtime pro C# projekty. |
| Visual Studio 2022 (nebo jakékoli IDE podporující .NET) | Umožňuje kompilovat a ladit ukázkový kód. |
| Aspose.Words for .NET NuGet balíček | Dodává třídy `Document`, `DocumentBuilder` a grafy. |

Balíček Aspose.Words můžete přidat pomocí NuGet CLI:

```bash
dotnet add package Aspose.Words
```

> **Tip:** Použijte pevnou verzi (např. `23.9.0`) v produkci, aby se předešlo neočekávaným breaking changes.

## Vložení histogramu

S připraveným prostředím vytvořte nový konzolový projekt a otevřete soubor `Program.cs`. První dva řádky kódu vytvoří prázdný dokument a `DocumentBuilder`, který vám umožní dokument manipulovat:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Dále zavolejte `InsertChart` pro přidání histogramu. Metoda vyžaduje typ grafu, šířku a výšku v bodech:

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

V tomto okamžiku dokument obsahuje prázdný placeholder histogramu. Když otevřete vygenerovaný soubor *.docx*, uvidíte šedou oblast grafu připravenou pro data.

![Placeholder histogramu ve Word dokumentu](/images/histogram-placeholder.png){: .img-fluid alt="Snímek obrazovky Word dokumentu zobrazující placeholder histogramu vytvořený pomocí Aspose.Words"}

## Jak nastavit intervaly histogramu

Histogram vizualizuje rozdělení číselných dat seskupením hodnot do *intervalů*. Vlastnost `HistogramBins` určuje, kolik intervalů graf zobrazí. Nastavení této vlastnosti před přidáním dat zajistí, že graf rezervuje správný počet sloupců.

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

Počet intervalů můžete upravit tak, aby odpovídal granularitě vašeho datového souboru. Například datový soubor od 0 do 100 s počtem intervalů 10 vytvoří intervaly po 10 jednotkách (0‑9, 10‑19, …, 90‑100).

> **Proč je to důležité:** Příliš malý počet intervalů může skrýt důležité vzory, zatímco příliš mnoho intervalů může vytvořit šumivý graf. Otestujte několik hodnot a najděte optimální nastavení pro vaše konkrétní data.

## Konfigurace intervalů histogramu pro lepší čitelnost

Kromě počtu intervalů často chcete každý interval označit, aby čtenáři viděli přesný počet. Vlastnost `ShowBinLabels` přepíná viditelnost těchto popisků:

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

Když je `ShowBinLabels` nastaveno na `true`, Word vykreslí číselný popisek nad každým sloupcem. Tento malý konfigurační krok výrazně zlepšuje interpretovatelnost grafu, zejména v reportech, kde čtenáři nemusí mít k dispozici původní datový soubor.

Můžete také přizpůsobit vzhled popisků, například velikost písma nebo barvu, pomocí objektu `HistogramLabel` (k dispozici v novějších verzích Aspose.Words). Následující úryvek ukazuje běžnou úpravu:

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **Hraniční případ:** Pokud nastavíte `HistogramBins` na hodnotu větší než počet odlišných datových bodů, některé intervaly budou prázdné. Graf se stále vykreslí správně, ale vizuálně může vypadat řídký. V takových situacích zvažte snížení počtu intervalů.

## Přidání datové řady do histogramu

Histogram vyžaduje jedinou datovou řadu, která představuje podkladové číselné hodnoty. Řadu můžete naplnit pomocí pole, `List<double>` nebo jakékoli kolekce implementující `IEnumerable`. Níže je stručný příklad, který přidá náhodný datový soubor:

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

Metoda `AddRange` převádí každou hodnotu do příslušného intervalu podle dříve definovaného `HistogramBins`. Po tomto kroku graf zobrazí plně naplněný histogram.

## Uložení a zobrazení výsledného dokumentu

Nakonec zapište dokument na disk. Můžete zvolit libovolné umístění, ke kterému má vaše aplikace přístup. Následující řádek uloží soubor jako `output.docx`:

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

Otevřete `output.docx` v Microsoft Word a uvidíte histogram s deseti intervaly, označenými hodnotami a vzorovými daty, která jste zadali. Graf bude vypadat podobně jako obrázek níže:

![Dokončený histogram ve Wordu](/images/histogram-complete.png){: .img-fluid alt="Word dokument zobrazující dokončený histogram s deseti intervaly a popisky"}

## Kompletní, spustitelný příklad

Sestavením všech částí dohromady získáte samostatný program, který můžete zkopírovat, vložit a spustit:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**Očekávaný výstup:** Otevření `output.docx` zobrazí histogram s deseti rovnoměrně rozmístěnými sloupci, z nichž každý je označen svým počtem. Graf odráží rozdělení pole `data`, čímž okamžitě zviditelní trendy.

## Časté otázky a řešení problémů

| Otázka | Odpověď |
|----------|--------|
| *Co když potřebuji více než jednu datovou řadu?* | Histogramy typicky představují jediné rozdělení. Pokud potřebujete více řad, zvažte místo toho sloupcový graf. |
| *Mohu změnit velikost grafu po vložení?* | Ano. Upravit vlastnosti `histogram.Width` a `histogram.Height`, nebo znovu zavolat `builder.InsertChart` s jinými rozměry. |
| *Funguje to s .NET Framework 4.8?* | Rozhodně. Aspose.Words podporuje .NET Framework 4.5 a novější, takže stejný kód běží beze změny. |
| *Jak exportovat graf jako obrázek?* | Použijte `histogram.ToImage()` k získání objektu `System.Drawing.Image` a poté jej uložte pomocí `image.Save("chart.png")`. |

## Závěr

Nyní víte, jak ve Wordu vytvořit histogram pomocí Aspose.Words, jak nastavit intervaly histogramu a jak je nakonfigurovat pro přehledný, označený výstup. Kompletní příklad demonstruje produkčně připravený přístup, který můžete přizpůsobit libovolnému scénáři reportování založenému na datech.  

Dále prozkoumejte související témata, jako **jak vytvořit koláčové grafy ve Wordu**, **přizpůsobení barev grafu** a **vkládání zdrojů dat z Excelu**. Každé z nich staví na stejném workflow `DocumentBuilder`, takže řešení můžete rozšířit s minimálním úsilím.

Happy charting!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Jak vytvořit sloupcový graf pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Jak vytvořit PDF z Wordu – kompletní průvodce C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Jak načíst Word dokumenty pomocí Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
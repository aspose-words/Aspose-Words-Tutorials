---
"description": "Naučte se, jak nastavit výchozí možnosti pro popisky dat v grafu pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu a bez námahy vytvářejte a upravujte grafy."
"linktitle": "Nastavení výchozích možností pro popisky dat v grafu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení výchozích možností pro popisky dat v grafu"
"url": "/cs/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení výchozích možností pro popisky dat v grafu

## Zavedení

Ahoj! Těšíte se na ponoření do světa automatizace dokumentů? Dnes se podíváme na to, jak pomocí Aspose.Words pro .NET programově vytvářet úžasné dokumenty. Aspose.Words je výkonná knihovna, která vám umožňuje snadno manipulovat s dokumenty Wordu, a v tomto tutoriálu se zaměříme na nastavení výchozích možností pro popisky dat v grafu. Ať už jste zkušený vývojář nebo nováček, tento průvodce vás provede každým krokem a zvládnete to co nejdříve.

## Předpoklady

Než začneme, ujistěte se, že máte vše potřebné k dodržování tohoto tutoriálu. Zde je stručný kontrolní seznam:

- Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET: Zde budete psát a spouštět svůj kód.
- Aspose.Words pro .NET: Můžete [stáhněte si nejnovější verzi](https://releases.aspose.com/words/net/) a nainstalujte si ho do projektu.
- Základní znalost programování v C#: I když je tato příručka vhodná pro začátečníky, trocha seznámení s C# bude užitečná.
- Nainstalovaný .NET Framework: Ujistěte se, že máte v počítači nainstalovaný .NET Framework.
- Dočasná licence pro Aspose.Words: Pořiďte si jednu [zde](https://purchase.aspose.com/temporary-license/) pro odemknutí plné funkčnosti.

Jakmile splníte tyto předpoklady, můžeme začít!

## Importovat jmenné prostory

Nejdříve si nastavme náš projekt a importujme potřebné jmenné prostory. Tyto jmenné prostory jsou klíčové pro přístup k funkcím Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Krok 1: Vytvořte nový dokument


Cesta začíná vytvořením nového dokumentu a inicializací `DocumentBuilder`Ten/Ta/To `DocumentBuilder` třída poskytuje sadu metod pro snadnou manipulaci s obsahem dokumentu.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Vytvořit nový dokument
Document doc = new Document();

// Inicializace nástroje DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Vysvětlení

tomto kroku jsme nastavili dokument a nástroj pro tvorbu, který použijeme k vkládání a formátování našeho obsahu. `dataDir` proměnná obsahuje cestu, kam uložíme náš finální dokument.

## Krok 2: Vložení grafu

Dále do našeho dokumentu přidáme koláčový graf. `InsertChart` metoda `DocumentBuilder` třída to velmi usnadňuje.

```csharp
// Vložení koláčového grafu
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Přístup k objektu grafu
Chart chart = shape.Chart;
```

### Vysvětlení

Zde vkládáme do našeho dokumentu koláčový graf. `InsertChart` Metoda vyžaduje jako parametry typ grafu, šířku a výšku. Po vložení grafu přistupujeme k objektu grafu, abychom s ním mohli dále manipulovat.

## Krok 3: Přizpůsobení série grafů

Nyní vymažeme všechny existující řady v grafu a přidáme naši vlastní řadu. Tato řada bude reprezentovat naše datové body.

```csharp
// Vymazat existující řadu grafů
chart.Series.Clear();

// Přidat novou sérii do grafu
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Vysvětlení

tomto kroku se ujistíme, že je náš graf prázdný, a to vymazáním všech existujících řad. Poté přidáme novou řadu s vlastními kategoriemi a hodnotami, které se zobrazí v našem koláčovém grafu.

## Krok 4: Nastavení výchozích možností pro popisky dat

Popisky dat jsou klíčové pro informativní zobrazení grafu. Nastavíme možnosti pro zobrazení procent, hodnot a přizpůsobíme oddělovač.

```csharp
// Přístup ke kolekci popisků dat
ChartDataLabelCollection labels = series.DataLabels;

// Nastavení možností popisků dat
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Vysvětlení

Zde přistupujeme k `DataLabels` naší řady pro přizpůsobení vzhledu a informací zobrazených na každém popisku dat. Zvolili jsme zobrazení procenta i hodnoty, skrytí odkazových čar a nastavení vlastního oddělovače.

## Krok 5: Uložte dokument

Nakonec uložíme náš dokument do zadaného adresáře. Tento krok zajistí, že všechny naše změny budou zapsány do souboru.

```csharp
// Uložit dokument
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Vysvětlení

V tomto posledním kroku uložíme náš dokument pomocí `Save` metoda. Dokument bude uložen do adresáře určeného metodou `dataDir`s názvem „WorkingWithCharts.DefaultOptionsForDataLabels.docx“.

## Závěr

A tady to máte! Úspěšně jste vytvořili dokument Word s přizpůsobeným koláčovým grafem pomocí Aspose.Words pro .NET. Tato výkonná knihovna usnadňuje automatizaci vytváření a manipulace s dokumenty, což vám šetří čas a úsilí. Ať už generujete zprávy, faktury nebo jakýkoli jiný typ dokumentu, Aspose.Words vám s tím pomůže.

Neváhejte a prozkoumejte [Dokumentace k Aspose.Words](https://reference.aspose.com/words/net/) pro více funkcí a příkladů. Šťastné programování!

## Často kladené otázky

### Mohu používat Aspose.Words zdarma?
Aspose.Words můžete používat zdarma s [dočasná licence](https://purchase.aspose.com/temporary-license/) nebo prozkoumejte jeho funkce pomocí [bezplatná zkušební verze](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Words?
Podporu můžete získat prostřednictvím [Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).

### Mohu přidat i jiné typy grafů?
Ano, Aspose.Words podporuje různé typy grafů, jako jsou sloupcové, čárové a sloupcové grafy. Zaškrtněte [dokumentace](https://reference.aspose.com/words/net/) pro více informací.

### Je Aspose.Words kompatibilní s .NET Core?
Ano, Aspose.Words je kompatibilní s .NET Core. Více informací naleznete v [dokumentace](https://reference.aspose.com/words/net/).

### Jak si mohu zakoupit licenci pro Aspose.Words?
Licenci si můžete zakoupit od [Obchod Aspose](https://purchase.aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
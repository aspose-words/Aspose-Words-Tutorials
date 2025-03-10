---
title: Nastavit výchozí možnosti pro štítky dat v grafu
linktitle: Nastavit výchozí možnosti pro štítky dat v grafu
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak nastavit výchozí možnosti pro popisky dat v grafu pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce a vytvořte a přizpůsobte grafy bez námahy.
weight: 10
url: /cs/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavit výchozí možnosti pro štítky dat v grafu

## Zavedení

Ahoj! Rádi se ponoříte do světa automatizace dokumentů? Dnes se podíváme na to, jak používat Aspose.Words pro .NET k vytváření úžasných dokumentů programově. Aspose.Words je výkonná knihovna, která vám umožňuje snadno manipulovat s dokumenty Wordu, a v tomto tutoriálu se zaměříme na nastavení výchozích možností pro popisky dat v grafu. Ať už jste ostřílený vývojář nebo nováček, tento průvodce vás provede každým krokem, abyste mohli okamžitě začít pracovat.

## Předpoklady

Než začneme, ujistíme se, že spolu s tímto návodem máte vše, co potřebujete. Zde je rychlý kontrolní seznam:

- Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET: Zde budete psát a spouštět svůj kód.
-  Aspose.Words pro .NET: Můžete[stáhnout nejnovější verzi](https://releases.aspose.com/words/net/) a nainstalujte jej do svého projektu.
- Základní znalost programování v C#: I když je tato příručka vhodná pro začátečníky, trocha znalosti C# vám pomůže.
- Nainstalované rozhraní .NET Framework: Ujistěte se, že máte na počítači nastaveno rozhraní .NET Framework.
-  Dočasná licence pro Aspose.Words: Získejte jednu[zde](https://purchase.aspose.com/temporary-license/) pro odemknutí plné funkčnosti.

Jakmile máte tyto předpoklady vyřešené, jsme připraveni začít!

## Importovat jmenné prostory

Nejprve nastavíme náš projekt a importujeme potřebné jmenné prostory. Tyto jmenné prostory jsou klíčové pro přístup k funkci Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Krok 1: Vytvořte nový dokument


 Cesta začíná vytvořením nového dokumentu a inicializací`DocumentBuilder` . The`DocumentBuilder` class poskytuje sadu metod pro snadnou manipulaci s obsahem dokumentu.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Vytvořte nový dokument
Document doc = new Document();

// Inicializujte DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Vysvětlení

 V tomto kroku jsme nastavili dokument a tvůrce, které budeme používat k vkládání a formátování našeho obsahu. The`dataDir` proměnná obsahuje cestu, kam uložíme náš konečný dokument.

## Krok 2: Vložte graf

 Dále do našeho dokumentu přidáme koláčový graf. The`InsertChart` metoda`DocumentBuilder` třída to velmi usnadňuje.

```csharp
// Vložte výsečový graf
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Přístup k objektu grafu
Chart chart = shape.Chart;
```

### Vysvětlení

Zde do našeho dokumentu vkládáme výsečový graf. The`InsertChart` vyžaduje typ grafu, šířku a výšku jako parametry. Po vložení grafu přistoupíme k objektu grafu, abychom s ním dále manipulovali.

## Krok 3: Přizpůsobte řadu grafů

Nyní vymažeme všechny existující řady v grafu a přidáme vlastní řadu. Tato řada bude představovat naše datové body.

```csharp
// Vymazat existující řady grafů
chart.Series.Clear();

// Přidejte do grafu novou řadu
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Vysvětlení

V tomto kroku se ujišťujeme, že je náš graf prázdný, tím, že vymažeme všechny již existující řady. Poté přidáme novou řadu s vlastními kategoriemi a hodnotami, které se zobrazí v našem koláčovém grafu.

## Krok 4: Nastavte výchozí možnosti pro štítky dat

Datové štítky jsou zásadní pro to, aby byl váš graf informativní. Nastavíme možnosti pro zobrazení procenta, hodnoty a přizpůsobení oddělovače.

```csharp
// Přístup ke kolekci datových štítků
ChartDataLabelCollection labels = series.DataLabels;

// Nastavte možnosti štítku dat
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Vysvětlení

 Zde přistupujeme k`DataLabels`vlastnost naší řady přizpůsobit vzhled a informace zobrazené na každém štítku s údaji. Rozhodli jsme se zobrazit procento i hodnotu, skrýt odkazové čáry a nastavit vlastní oddělovač.

## Krok 5: Uložte dokument

Nakonec náš dokument uložíme do zadaného adresáře. Tento krok zajistí, že všechny naše změny budou zapsány do souboru.

```csharp
// Uložte dokument
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Vysvětlení

 V tomto posledním kroku uložíme náš dokument pomocí`Save` metoda. Dokument bude uložen do adresáře určeného uživatelem`dataDir`, s názvem "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Závěr

A tady to máte! Úspěšně jste vytvořili dokument aplikace Word s přizpůsobeným výsečovým grafem pomocí Aspose.Words for .NET. Tato výkonná knihovna usnadňuje automatizaci vytváření dokumentů a manipulaci s nimi, což vám šetří čas a námahu. Ať už generujete zprávy, faktury nebo jakýkoli jiný typ dokumentu, Aspose.Words vám pomůže.

 Neváhejte a prozkoumejte[Dokumentace Aspose.Words](https://reference.aspose.com/words/net/) pro další funkce a příklady. Šťastné kódování!

## FAQ

### Mohu používat Aspose.Words zdarma?
Aspose.Words můžete používat zdarma s a[dočasná licence](https://purchase.aspose.com/temporary-license/) nebo prozkoumejte jeho funkce pomocí[zkušební verze zdarma](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Words?
 Podporu můžete získat prostřednictvím[Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).

### Mohu přidat další typy grafů?
 Ano, Aspose.Words podporuje různé typy grafů, jako jsou pruhové, spojnicové a sloupcové grafy. Zkontrolujte[dokumentace](https://reference.aspose.com/words/net/) pro více podrobností.

### Je Aspose.Words kompatibilní s .NET Core?
 Ano, Aspose.Words je kompatibilní s .NET Core. Více informací najdete v[dokumentace](https://reference.aspose.com/words/net/).

### Jak si mohu zakoupit licenci pro Aspose.Words?
 Licenci si můžete zakoupit od[Aspose obchod](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

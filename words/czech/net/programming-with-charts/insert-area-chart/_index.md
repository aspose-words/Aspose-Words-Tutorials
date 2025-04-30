---
"description": "Naučte se, jak vložit plošný graf do dokumentu pomocí Aspose.Words pro .NET. Přidejte data řady a uložte dokument s grafem."
"linktitle": "Vložení plošného grafu do dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložení plošného grafu do dokumentu Word"
"url": "/cs/net/programming-with-charts/insert-area-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení plošného grafu do dokumentu Word

## Zavedení

Vítejte v tomto podrobném návodu, jak vložit plošný graf do dokumentu Word pomocí Aspose.Words pro .NET. Ať už jste zkušený vývojář, nebo teprve začínáte, tento tutoriál vás provede vším, co potřebujete vědět k vytvoření úžasných a informativních plošných grafů ve vašich dokumentech Word. Probereme předpoklady, ukážeme vám, jak importovat potřebné jmenné prostory, a provedeme vás každým krokem procesu pomocí jasných a snadno srozumitelných pokynů.

## Předpoklady

Než se do toho pustíme, ujistěte se, že máte vše, co potřebujete k zahájení:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovaný Aspose.Words pro .NET. Můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
2. .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.
3. IDE: Integrované vývojové prostředí (IDE) podobné Visual Studiu pro psaní a spouštění kódu.
4. Základní znalost C#: Základní znalost programování v C# bude užitečná.

Jakmile budete mít tyto předpoklady splněny, můžete začít vytvářet krásné plošné grafy ve svých dokumentech Wordu.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Tyto jmenné prostory poskytují třídy a metody potřebné pro práci s dokumenty Word a grafy v Aspose.Words pro .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Nyní, když jsme importovali základní jmenné prostory, pojďme k vytvoření dokumentu a vložení plošného grafu krok za krokem.

## Krok 1: Vytvořte nový dokument Wordu

Začněme vytvořením nového dokumentu Wordu. Ten bude základem, kam vložíme náš plošný graf.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

V tomto kroku inicializujeme nový `Document` objekt, který představuje náš dokument Wordu.

## Krok 2: Vložení grafu pomocí nástroje DocumentBuilder

Dále použijeme `DocumentBuilder` třída pro vložení plošného grafu do našeho dokumentu.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

Zde vytváříme `DocumentBuilder` objekt a pomocí něj vložit do dokumentu plošný graf o specifických rozměrech (432x252).

## Krok 3: Přístup k objektu grafu

Po vložení grafu potřebujeme přístup k `Chart` objekt pro přizpůsobení našeho plošného grafu.

```csharp
Chart chart = shape.Chart;
```

Tento řádek kódu načte `Chart` objekt z tvaru, který jsme právě vložili.

## Krok 4: Přidání dat řady do grafu

Nyní je čas přidat do našeho grafu nějaká data. Přidáme řadu s daty a odpovídajícími hodnotami.

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

V tomto kroku přidáme sérii s názvem „Aspose Series 1“ se sadou dat a odpovídajících hodnot.

## Krok 5: Uložte dokument

Nakonec uložíme náš dokument s vloženým plošným grafem.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Tento řádek kódu uloží dokument do zadaného adresáře s daným názvem souboru.

## Závěr

Gratulujeme! Úspěšně jste vložili plošný graf do dokumentu Word pomocí Aspose.Words pro .NET. Tato příručka vás provede každým krokem, od nastavení prostředí až po uložení finálního dokumentu. S Aspose.Words pro .NET můžete ve svých dokumentech Word vytvářet širokou škálu grafů a dalších složitých prvků, díky čemuž budou vaše zprávy a prezentace dynamičtější a informativnější.

## Často kladené otázky

### Mohu používat Aspose.Words pro .NET s jinými jazyky .NET?
Ano, Aspose.Words pro .NET podporuje i další jazyky .NET, například VB.NET.

### Je možné si vzhled grafu přizpůsobit?
Rozhodně! Aspose.Words pro .NET nabízí rozsáhlé možnosti pro přizpůsobení vzhledu vašich grafů.

### Mohu do jednoho dokumentu Wordu přidat více grafů?
Ano, do jednoho dokumentu Wordu můžete vložit libovolný počet grafů.

### Podporuje Aspose.Words pro .NET i jiné typy grafů?
Ano, Aspose.Words pro .NET podporuje různé typy grafů, včetně sloupcových, čárových, koláčových a dalších.

### Kde mohu získat dočasnou licenci pro Aspose.Words pro .NET?
Dočasné povolení můžete získat od [zde](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
---
title: Vložit plošný graf do dokumentu aplikace Word
linktitle: Vložit plošný graf do dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vložit plošný graf do dokumentu pomocí Aspose.Words for .NET. Přidejte data série a uložte dokument s grafem.
weight: 10
url: /cs/net/programming-with-charts/insert-area-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit plošný graf do dokumentu aplikace Word

## Zavedení

Vítejte v tomto podrobném návodu, jak vložit plošný graf do dokumentu aplikace Word pomocí Aspose.Words for .NET. Ať už jste zkušený vývojář nebo teprve začínáte, tento tutoriál vás provede vším, co potřebujete vědět, abyste vytvořili úžasné a informativní plošné grafy ve svých dokumentech Word. Pokryjeme předpoklady, ukážeme vám, jak importovat potřebné jmenné prostory, a provedeme vás každým krokem procesu pomocí jasných a snadno pochopitelných pokynů.

## Předpoklady

Než se do toho pustíme, ujistěte se, že máte vše, co potřebujete, abyste mohli začít:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou aplikaci Aspose.Words for .NET. Můžete si jej stáhnout[zde](https://releases.aspose.com/words/net/).
2. .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
3. IDE: Integrované vývojové prostředí (IDE), jako je Visual Studio, k psaní a spouštění vašeho kódu.
4. Základní znalost C#: Základní znalost programování v C# bude užitečná.

Jakmile splníte tyto předpoklady, jste připraveni začít vytvářet nádherné plošné grafy v dokumentech aplikace Word.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Tyto jmenné prostory poskytují třídy a metody potřebné pro práci s dokumenty a grafy aplikace Word v Aspose.Words for .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Nyní, když jsme importovali základní jmenné prostory, přejděme k vytvoření našeho dokumentu a vložení plošného grafu krok za krokem.

## Krok 1: Vytvořte nový dokument aplikace Word

Začněme vytvořením nového dokumentu aplikace Word. Toto bude základ, kam vložíme náš plošný graf.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 V tomto kroku inicializujeme nový`Document` objekt, který představuje náš dokument aplikace Word.

## Krok 2: Použijte DocumentBuilder k vložení grafu

 Dále použijeme`DocumentBuilder` třídy k vložení plošného grafu do našeho dokumentu.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

 Zde vytvoříme a`DocumentBuilder` objekt a použijte jej k vložení plošného grafu konkrétních rozměrů (432x252) do našeho dokumentu.

## Krok 3: Přístup k objektu grafu

 Po vložení grafu potřebujeme přistupovat k`Chart` objekt přizpůsobit náš plošný graf.

```csharp
Chart chart = shape.Chart;
```

 Tento řádek kódu načte`Chart` objekt z tvaru, který jsme právě vložili.

## Krok 4: Přidejte do grafu data řady

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

tomto kroku přidáme řadu s názvem „Aspose Series 1“ se sadou dat a odpovídajících hodnot.

## Krok 5: Uložte dokument

Nakonec náš dokument s vloženým plošným grafem uložíme.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Tento řádek kódu uloží dokument do zadaného adresáře s daným názvem souboru.

## Závěr

Gratuluji! Úspěšně jste vložili plošný graf do dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato příručka vás provede každým krokem, od nastavení prostředí až po uložení konečného dokumentu. S Aspose.Words for .NET můžete ve svých dokumentech aplikace Word vytvářet širokou škálu grafů a dalších složitých prvků, díky čemuž budou vaše zprávy a prezentace dynamičtější a informativnější.

## FAQ

### Mohu používat Aspose.Words pro .NET s jinými jazyky .NET?
Ano, Aspose.Words for .NET podporuje další jazyky .NET, jako je VB.NET.

### Je možné upravit vzhled grafu?
Absolutně! Aspose.Words for .NET poskytuje rozsáhlé možnosti přizpůsobení vzhledu vašich grafů.

### Mohu přidat více grafů do jednoho dokumentu aplikace Word?
Ano, do jednoho dokumentu aplikace Word můžete vložit tolik grafů, kolik potřebujete.

### Podporuje Aspose.Words pro .NET jiné typy grafů?
Ano, Aspose.Words for .NET podporuje různé typy grafů včetně sloupcových, čárových, koláčových a dalších.

### Kde mohu získat dočasnou licenci pro Aspose.Words pro .NET?
 Dočasnou licenci můžete získat od[zde](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

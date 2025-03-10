---
title: Nastavení preferované šířky
linktitle: Nastavení preferované šířky
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vytvářet tabulky s absolutním, relativním a automatickým nastavením šířky v Aspose.Words for .NET pomocí tohoto podrobného průvodce.
weight: 10
url: /cs/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení preferované šířky

## Zavedení

Tabulky představují účinný způsob, jak organizovat a prezentovat informace v dokumentech aplikace Word. Při práci s tabulkami v Aspose.Words pro .NET máte několik možností pro nastavení šířky buněk tabulky, aby se zajistilo, že budou dokonale odpovídat rozvržení vašeho dokumentu. Tato příručka vás provede procesem vytváření tabulek s preferovaným nastavením šířky pomocí Aspose.Words pro .NET se zaměřením na absolutní, relativní a automatické možnosti velikosti. 

## Předpoklady

Než se pustíte do výukového programu, ujistěte se, že máte následující:

1.  Aspose.Words for .NET: Ujistěte se, že máte ve svém vývojovém prostředí nainstalovanou aplikaci Aspose.Words for .NET. Můžete si jej stáhnout[zde](https://releases.aspose.com/words/net/).

2. Vývojové prostředí .NET: Mějte nastavené vývojové prostředí .NET, jako je Visual Studio.

3. Základní znalost C#: Znalost programování v C# vám pomůže lépe porozumět úryvkům kódu a příkladům.

4.  Dokumentace Aspose.Words: Viz[Dokumentace Aspose.Words](https://reference.aspose.com/words/net/) pro podrobné informace o API a další čtení.

## Importovat jmenné prostory

Než začnete kódovat, musíte do svého projektu C# importovat potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Tyto jmenné prostory poskytují přístup k základním funkcím Aspose.Words a objektu Table, což vám umožňuje manipulovat s tabulkami dokumentů.

Rozdělme si proces tvorby tabulky s různým preferovaným nastavením šířky do jasných, zvládnutelných kroků.

## Krok 1: Inicializujte Document a DocumentBuilder

Nadpis: Vytvoření nového dokumentu a DocumentBuilder

 Vysvětlení: Začněte vytvořením nového dokumentu aplikace Word a a`DocumentBuilder` instance. The`DocumentBuilder` class poskytuje jednoduchý způsob, jak přidat obsah do vašeho dokumentu.

```csharp
// Definujte cestu k uložení dokumentu.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Vytvořte nový dokument.
Document doc = new Document();

// Vytvořte DocumentBuilder pro tento dokument.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Zde určíte adresář, kam bude dokument uložen, a inicializujete jej`Document` a`DocumentBuilder` objektů.

## Krok 2: Vložte první buňku tabulky s absolutní šířkou

Vložte první buňku do tabulky s pevnou šířkou 40 bodů. To zajistí, že tato buňka si vždy zachová šířku 40 bodů bez ohledu na velikost tabulky.

```csharp
// Vložte buňku absolutní velikosti.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

 tomto kroku začnete vytvářet tabulku a vložíte buňku s absolutní šířkou. The`PreferredWidth.FromPoints(40)` metoda nastaví šířku buňky na 40 bodů a`Shading.BackgroundPatternColor` použije světle žlutou barvu pozadí.

## Krok 3: Vložte buňku relativní velikosti

Vložte další buňku o šířce 20 % celkové šířky tabulky. Tato relativní velikost zajišťuje, že se buňka přizpůsobí úměrně šířce tabulky.

```csharp
// Vložte buňku relativní (procentuální) velikosti.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Šířka této buňky bude 20 % celkové šířky tabulky, takže ji lze přizpůsobit různým velikostem obrazovky nebo rozvržení dokumentu.

### Krok 4: Vložte buňku s automatickou velikostí

Nakonec vložte buňku, která se automaticky přizpůsobí velikosti podle zbývajícího dostupného místa v tabulce.

```csharp
// Vložte buňku s automatickou velikostí.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 The`PreferredWidth.Auto` nastavení umožňuje, aby se tato buňka roztahovala nebo smršťovala na základě prostoru, který zbyde po započtení ostatních buněk. To zajišťuje, že rozložení stolu vypadá vyváženě a profesionálně.

## Krok 5: Dokončete a uložte dokument

Jakmile vložíte všechny buňky, vyplňte tabulku a uložte dokument do zadané cesty.

```csharp
// Uložte dokument.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Tento krok dokončí tabulku a uloží dokument s názvem "WorkingWithTables.PreferredWidthSettings.docx" do vámi určeného adresáře.

## Závěr

Vytváření tabulek s preferovaným nastavením šířky v Aspose.Words pro .NET je jednoduché, jakmile pochopíte různé dostupné možnosti velikosti. Ať už potřebujete pevnou, relativní nebo automatickou šířku buněk, Aspose.Words poskytuje flexibilitu pro efektivní zpracování různých scénářů rozvržení tabulek. Dodržováním kroků uvedených v této příručce můžete zajistit, aby vaše tabulky byly v dokumentech aplikace Word dobře strukturované a vizuálně přitažlivé.

## FAQ

### Jaký je rozdíl mezi absolutní a relativní šířkou buněk?
Absolutní šířky buněk jsou pevné a nemění se, zatímco relativní šířky se upravují na základě celkové šířky tabulky.

### Mohu pro relativní šířky použít záporná procenta?
Ne, záporná procenta neplatí pro šířky buněk. Povolena jsou pouze kladná procenta.

### Jak funguje funkce automatického přizpůsobení velikosti?
Automatická změna velikosti upraví šířku buňky tak, aby zaplnila veškerý zbývající prostor v tabulce poté, co byla změněna velikost ostatních buněk.

### Mohu použít různé styly na buňky s různým nastavením šířky?
Ano, na buňky můžete použít různé styly a formátování bez ohledu na nastavení jejich šířky.

### Co se stane, když je celková šířka tabulky menší než součet šířek všech buněk?
Tabulka automaticky upraví šířky buněk tak, aby se vešly do dostupného prostoru, což může způsobit zmenšení některých buněk.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

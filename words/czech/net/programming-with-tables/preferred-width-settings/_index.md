---
"description": "Naučte se, jak v Aspose.Words pro .NET vytvářet tabulky s absolutním, relativním a automatickým nastavením šířky s pomocí tohoto podrobného návodu."
"linktitle": "Preferované nastavení šířky"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Preferované nastavení šířky"
"url": "/cs/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Preferované nastavení šířky

## Zavedení

Tabulky představují účinný způsob, jak organizovat a prezentovat informace v dokumentech Wordu. Při práci s tabulkami v Aspose.Words pro .NET máte několik možností, jak nastavit šířku buněk tabulky, abyste zajistili, že dokonale odpovídají rozvržení dokumentu. Tato příručka vás provede procesem vytváření tabulek s preferovaným nastavením šířky pomocí Aspose.Words pro .NET, se zaměřením na absolutní, relativní a automatické možnosti změny velikosti. 

## Předpoklady

Než se pustíte do tutoriálu, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Ujistěte se, že máte ve svém vývojovém prostředí nainstalovaný Aspose.Words pro .NET. Můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).

2. Vývojové prostředí .NET: Mějte nastavené vývojové prostředí .NET, například Visual Studio.

3. Základní znalost C#: Znalost programování v C# vám pomůže lépe porozumět úryvkům kódu a příkladům.

4. Dokumentace k Aspose.Words: Viz [Dokumentace k Aspose.Words](https://reference.aspose.com/words/net/) pro podrobné informace o API a další informace.

## Importovat jmenné prostory

Než začnete programovat, musíte do svého projektu v C# importovat potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Tyto jmenné prostory poskytují přístup k základním funkcím Aspose.Words a objektu Table, což vám umožňuje manipulovat s tabulkami dokumentů.

Rozdělme si proces vytvoření tabulky s různými preferovanými nastaveními šířky do jasných a snadno zvládnutelných kroků.

## Krok 1: Inicializace dokumentu a nástroje DocumentBuilder

Nadpis: Vytvoření nového dokumentu a nástroj DocumentBuilder

Vysvětlení: Začněte vytvořením nového dokumentu Word a `DocumentBuilder` instance. Ten `DocumentBuilder` třída poskytuje jednoduchý způsob, jak do dokumentu přidat obsah.

```csharp
// Definujte cestu pro uložení dokumentu.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Vytvořte nový dokument.
Document doc = new Document();

// Vytvořte pro tento dokument nástroj Document Builder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Zde určíte adresář, kam bude dokument uložen, a inicializujete `Document` a `DocumentBuilder` objekty.

## Krok 2: Vložení první buňky tabulky s absolutní šířkou

Vložte do tabulky první buňku s pevnou šířkou 40 bodů. Tím zajistíte, že tato buňka si vždy zachová šířku 40 bodů bez ohledu na velikost tabulky.

```csharp
// Vložte buňku absolutní velikosti.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

V tomto kroku začnete vytvářet tabulku a vložíte buňku s absolutní šířkou. `PreferredWidth.FromPoints(40)` metoda nastaví šířku buňky na 40 bodů a `Shading.BackgroundPatternColor` použije světle žlutou barvu pozadí.

## Krok 3: Vložení buňky relativní velikosti

Vložte další buňku o šířce, která je 20 % celkové šířky tabulky. Toto relativní nastavení velikosti zajistí, že se buňka úměrně přizpůsobí šířce tabulky.

```csharp
// Vložte buňku s relativní (procentní) velikostí.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Šířka této buňky bude 20 % celkové šířky tabulky, takže ji lze přizpůsobit různým velikostem obrazovky nebo rozvržení dokumentu.

### Krok 4: Vložení buňky s automatickou změnou velikosti

Nakonec vložte buňku, která se automaticky zvětší na základě zbývajícího dostupného místa v tabulce.

```csharp
// Vložit buňku s automatickou velikostí.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. Ten/Ta/To size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` Toto nastavení umožňuje této buňce roztahovat se nebo zmenšovat v závislosti na prostoru, který zbývá po započítání ostatních buněk. Díky tomu bude rozvržení tabulky vypadat vyváženě a profesionálně.

## Krok 5: Dokončete a uložte dokument

Jakmile vložíte všechny buňky, vyplňte tabulku a uložte dokument do zadané cesty.

```csharp
// Uložte dokument.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Tento krok finalizuje tabulku a ukládá dokument s názvem souboru „WorkingWithTables.PreferredWidthSettings.docx“ do vámi určeného adresáře.

## Závěr

Vytváření tabulek s preferovaným nastavením šířky v Aspose.Words pro .NET je jednoduché, jakmile pochopíte různé dostupné možnosti změny velikosti. Ať už potřebujete pevnou, relativní nebo automatickou šířku buněk, Aspose.Words poskytuje flexibilitu pro efektivní zpracování různých scénářů rozvržení tabulek. Dodržováním kroků uvedených v této příručce zajistíte, že vaše tabulky budou v dokumentech Word dobře strukturované a vizuálně přitažlivé.

## Často kladené otázky

### Jaký je rozdíl mezi absolutní a relativní šířkou buněk?
Absolutní šířky buněk jsou pevné a nemění se, zatímco relativní šířky se upravují na základě celkové šířky tabulky.

### Mohu pro relativní šířky použít záporná procenta?
Ne, záporná procenta nejsou platná pro šířku buněk. Povolena jsou pouze kladná procenta.

### Jak funguje funkce automatické změny velikosti?
Automatická změna velikosti upraví šířku buňky tak, aby vyplnila veškerý zbývající prostor v tabulce po změně velikosti ostatních buněk.

### Mohu použít různé styly na buňky s různým nastavením šířky?
Ano, na buňky můžete použít různé styly a formátování bez ohledu na jejich nastavení šířky.

### Co se stane, když je celková šířka tabulky menší než součet šířek všech buněk?
Tabulka automaticky upraví šířku buněk tak, aby se vešla do dostupného prostoru, což může způsobit zmenšení některých buněk.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
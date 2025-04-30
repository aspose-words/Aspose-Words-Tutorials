---
"description": "Naučte se, jak formátovat čísla os grafu pomocí Aspose.Words pro .NET s tímto podrobným návodem. Bez námahy vylepšete čitelnost a profesionalitu svého dokumentu."
"linktitle": "Číselný formát pro osu v grafu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Číselný formát pro osu v grafu"
"url": "/cs/net/programming-with-charts/number-format-for-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Číselný formát pro osu v grafu

## Zavedení

Ahoj! Pracovali jste někdy s grafy ve svých dokumentech a přáli jste si, abyste mohli formátovat čísla na ose, aby vypadaly profesionálněji? Máte štěstí! V tomto tutoriálu se ponoříme do toho, jak toho můžete dosáhnout pomocí Aspose.Words pro .NET. Tato výkonná knihovna vám umožňuje pracovat s dokumenty Wordu hračkami. A dnes se zaměříme na to, jak osy grafů proměnit v nové díky vlastním formátům čísel.

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete. Zde je stručný kontrolní seznam:

- Aspose.Words pro .NET: Ujistěte se, že jej máte nainstalovaný. Pokud ne, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
- .NET Framework: Ujistěte se, že máte nainstalovaný kompatibilní .NET Framework.
- Vývojové prostředí: IDE jako Visual Studio bude fungovat perfektně.
- Základní znalost C#: To vám pomůže sledovat příklady kódování.

## Importovat jmenné prostory

Nejdříve je potřeba do projektu importovat potřebné jmenné prostory. Je to jako položit základy před stavbou domu. Na začátek souboru s kódem přidejte následující pomocí direktiv:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Nyní si celý proces rozdělme na jednoduché a snadno sledovatelné kroky.

## Krok 1: Nastavení dokumentu

Nadpis: Inicializace dokumentu

Nejprve je třeba vytvořit nový dokument a nástroj pro tvorbu dokumentů. Představte si tento krok jako přípravu plátna a štětce před zahájením tvorby svého mistrovského díla.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Zde, `dataDir` je cesta k adresáři s dokumenty, kam uložíte výsledný soubor. `Document` a `DocumentBuilder` jsou třídy z Aspose.Words, které vám pomáhají vytvářet a manipulovat s dokumenty aplikace Word.

## Krok 2: Vložení grafu

Nadpis: Přidání grafu do dokumentu

Dále přidáme do dokumentu graf. Tady začíná kouzlo. Vložíme sloupcový graf, který bude sloužit jako naše prázdné plátno.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

Ten/Ta/To `InsertChart` Metoda vloží do dokumentu graf zadaného typu (v tomto případě sloupcový) a dimenzí.

## Krok 3: Přizpůsobení série grafů

Nadpis: Naplnění grafu daty

Nyní musíme do našeho grafu přidat nějaká data. Tento krok je podobný naplnění grafu smysluplnými informacemi.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

Zde přidáváme novou sérii s názvem „Aspose Series 1“ s pěti datovými body. `Series.Clear` Metoda zajišťuje, že před přidáním nové série budou odstraněna veškerá existující data.

## Krok 4: Formátování čísel os

Nadpis: Zkrášlete si čísla os

Nakonec naformátujeme čísla na ose Y, aby byla lépe čitelná. Je to jako dotvářet vaši kresbu.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

Ten/Ta/To `FormatCode` Vlastnost umožňuje nastavit vlastní formát čísel na ose. V tomto příkladu `#,##0` zajišťuje, že velká čísla jsou zobrazena s čárkami pro tisíce.

## Krok 5: Uložení dokumentu

Nadpis: Zachraňte své mistrovské dílo

Nyní, když je vše nastaveno, je čas uložit dokument. Tento krok je velkým odhalením vaší práce.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

Zde, `Save` Metoda uloží dokument do zadané cesty s názvem souboru `WorkingWithCharts.NumberFormatForAxis.docx`.

## Závěr

A tady to máte! Úspěšně jste naformátovali čísla na ose Y vašeho grafu pomocí Aspose.Words pro .NET. Díky tomu budou vaše grafy nejen vypadat profesionálněji, ale také se zlepší jejich čitelnost. Aspose.Words nabízí nepřeberné množství funkcí, které vám pomohou programově vytvářet úžasné dokumenty Wordu. Proč tedy neprozkoumat více a nezjistit, co dalšího můžete dělat?

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, manipulovat a převádět dokumenty Wordu.

### Mohu formátovat i jiné aspekty grafu než čísla os?
Rozhodně! Aspose.Words pro .NET umožňuje formátovat názvy, popisky a dokonce i přizpůsobit vzhled grafu.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
Ano, můžete získat [bezplatná zkušební verze zde](https://releases.aspose.com/).

### Mohu používat Aspose.Words pro .NET s jinými jazyky .NET kromě C#?
Ano, Aspose.Words pro .NET je kompatibilní s jakýmkoli jazykem .NET, včetně VB.NET a F#.

### Kde najdu podrobnější dokumentaci?
Podrobná dokumentace je k dispozici na [Dokumentace k Aspose.Words pro .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
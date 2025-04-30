---
"description": "Naučte se, jak vodorovně sloučit buňky v dokumentu Word pomocí Aspose.Words pro .NET v tomto podrobném návodu krok za krokem."
"linktitle": "Horizontální sloučení"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Horizontální sloučení"
"url": "/cs/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Horizontální sloučení

## Zavedení

Ahoj! Jste připraveni ponořit se do světa Aspose.Words pro .NET? Dnes se budeme věnovat super užitečné funkci: horizontálnímu slučování v tabulkách. Může to znít trochu technicky, ale nebojte se, kryji vám záda. Po skončení tohoto tutoriálu budete profesionálem v programovém slučování buněk v dokumentech Word. Tak si vyhrňme rukávy a pusťme se do toho!

## Předpoklady

Než se pustíme do detailů, je třeba mít připraveno několik věcí:

1. Knihovna Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si knihovnu Aspose.Words pro .NET. Můžete si ji stáhnout [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Ujistěte se, že máte nastavené vhodné vývojové prostředí, například Visual Studio.
3. Základní znalost C#: Základní znalost programování v C# bude výhodou.

Jakmile tohle vyřešíte, můžete vyrazit!

## Importovat jmenné prostory

Než se pustíme do kódu, ujistěte se, že máme importované potřebné jmenné prostory. Ve vašem projektu C# nezapomeňte zahrnout:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dobře, pojďme si rozebrat proces horizontálního slučování buněk tabulky v dokumentu Word pomocí Aspose.Words pro .NET.

## Krok 1: Nastavení dokumentu

Nejdříve musíme vytvořit nový dokument Wordu a inicializovat ho. `DocumentBuilder`:

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Tento úryvek kódu nastaví nový dokument a připraví `DocumentBuilder` pro akci.

## Krok 2: Vložení první buňky

Dále začneme vložením první buňky a jejím označením pro horizontální sloučení:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

Zde vložíme novou buňku a nastavíme její `HorizontalMerge` majetek `CellMerge.First`, což znamená, že tato buňka je začátkem sloučené sekvence buněk.

## Krok 3: Vložení sloučené buňky

Nyní vložíme buňku, která bude sloučena s předchozí:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

Tato buňka je nastavena tak, aby se sloučila s předchozí buňkou pomocí `CellMerge.Previous`Všimněte si, jak řádek končíme `builder.EndRow()`.

## Krok 4: Vložení nesloučených buněk

Pro ilustraci rozdílu vložme několik nesloučených buněk:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Zde vkládáme dvě buňky bez horizontálního sloučení. To ukazuje, jak se buňky chovají, když nejsou součástí sloučené sekvence.

## Krok 5: Dokončení stolu

Nakonec tabulku ukončíme a dokument uložíme:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Tento úryvek kódu dokončí tabulku a uloží dokument do zadaného adresáře.

## Závěr

A tady to máte! Právě jste zvládli umění horizontálního slučování buněk v dokumentu Wordu pomocí Aspose.Words pro .NET. Dodržováním těchto kroků můžete snadno vytvářet složité tabulkové struktury. Experimentujte a objevujte možnosti Aspose.Words, abyste si dokumenty udělali tak dynamické a flexibilní, jak potřebujete. Přeji vám příjemné programování!

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, upravovat a manipulovat s dokumenty Wordu v aplikacích .NET.

### Mohu sloučit buňky vertikálně pomocí Aspose.Words pro .NET?
Ano, buňky můžete také sloučit svisle pomocí `CellFormat.VerticalMerge` vlastnictví.

### Je Aspose.Words pro .NET zdarma k použití?
Aspose.Words pro .NET nabízí bezplatnou zkušební verzi, ale pro plnou funkčnost si budete muset zakoupit licenci. Můžete získat dočasnou licenci. [zde](https://purchase.aspose.com/temporary-license/).

### Jak se mohu dozvědět více o Aspose.Words pro .NET?
Můžete si prohlédnout podrobnou dokumentaci [zde](https://reference.aspose.com/words/net/).

### Kde mohu získat podporu pro Aspose.Words pro .NET?
V případě jakýchkoli dotazů nebo problémů můžete navštívit fórum podpory Aspose. [zde](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
---
title: Horizontální sloučení
linktitle: Horizontální sloučení
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak horizontálně sloučit buňky v dokumentu aplikace Word pomocí Aspose.Words for .NET pomocí tohoto podrobného, podrobného tutoriálu.
weight: 10
url: /cs/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Horizontální sloučení

## Zavedení

Ahoj! Jste připraveni ponořit se do světa Aspose.Words pro .NET? Dnes se budeme zabývat super užitečnou funkcí: horizontálním slučováním v tabulkách. Může to znít trochu technicky, ale nebojte se, držím vám záda. Na konci tohoto kurzu budete profesionálem v programovém slučování buněk v dokumentech Wordu. Takže, vyhrňme si rukávy a začněme!

## Předpoklady

Než se pustíme do toho, je několik věcí, které musíte mít na svém místě:

1. Knihovna Aspose.Words for .NET: Pokud jste tak ještě neučinili, stáhněte si knihovnu Aspose.Words for .NET. Můžete to chytit[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Ujistěte se, že máte nastavené vhodné vývojové prostředí, jako je Visual Studio.
3. Základní znalost C#: Základní znalost programování v C# bude přínosem.

Jakmile si to vyřešíte, můžete vyrazit!

## Importovat jmenné prostory

Než se ponoříme do kódu, ujistěte se, že máme importované potřebné jmenné prostory. Ve svém projektu C# nezapomeňte zahrnout:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dobře, pojďme si rozebrat proces horizontálního slučování buněk tabulky v dokumentu aplikace Word pomocí Aspose.Words for .NET.

## Krok 1: Nastavení dokumentu

 Nejprve musíme vytvořit nový dokument aplikace Word a inicializovat jej`DocumentBuilder`:

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Tento fragment kódu nastaví nový dokument a připraví soubor`DocumentBuilder` pro akci.

## Krok 2: Vložení první buňky

Dále začneme vložením první buňky a jejím označením pro horizontální sloučení:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Zde vložíme novou buňku a nastavíme ji`HorizontalMerge`majetek do`CellMerge.First`, což znamená, že tato buňka je začátkem sloučené buněčné sekvence.

## Krok 3: Vložení sloučené buňky

Nyní vložíme buňku, která bude sloučena s předchozí:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Tato buňka je nastavena na sloučení s předchozí buňkou pomocí`CellMerge.Previous` . Všimněte si, jak končíme řadu`builder.EndRow()`.

## Krok 4: Vložení nesloučených buněk

Pro ilustraci rozdílu vložíme několik nesloučených buněk:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Zde vložíme dvě buňky bez horizontálního sloučení. To ukazuje, jak se buňky chovají, když nejsou součástí sloučené sekvence.

## Krok 5: Dokončení tabulky

Nakonec tabulku ukončíme a dokument uložíme:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Tento fragment kódu dokončí tabulku a uloží dokument do určeného adresáře.

## Závěr

A tady to máte! Právě jste zvládli umění horizontálního slučování buněk v dokumentu aplikace Word pomocí Aspose.Words for .NET. Podle těchto kroků můžete snadno vytvářet složité struktury tabulek. Pokračujte v experimentování a zkoumání možností Aspose.Words, aby byly vaše dokumenty tak dynamické a flexibilní, jak potřebujete. Šťastné kódování!

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna, která umožňuje vývojářům vytvářet, upravovat a manipulovat s dokumenty Wordu programově v aplikacích .NET.

### Mohu sloučit buňky vertikálně pomocí Aspose.Words pro .NET?
 Ano, buňky můžete také sloučit vertikálně pomocí`CellFormat.VerticalMerge` vlastnictví.

### Je Aspose.Words for .NET zdarma k použití?
 Aspose.Words for .NET nabízí bezplatnou zkušební verzi, ale pro plnou funkčnost si budete muset zakoupit licenci. Můžete získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

### Jak se mohu dozvědět více o Aspose.Words pro .NET?
 Můžete prozkoumat podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).

### Kde mohu získat podporu pro Aspose.Words pro .NET?
 V případě jakýchkoli dotazů nebo problémů můžete navštívit fórum podpory Aspose[zde](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

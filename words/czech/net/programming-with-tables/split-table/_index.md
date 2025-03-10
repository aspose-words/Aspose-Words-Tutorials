---
title: Rozdělený stůl
linktitle: Rozdělený stůl
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se rozdělit tabulky v dokumentech aplikace Word pomocí Aspose.Words for .NET. Náš podrobný průvodce usnadňuje a zefektivňuje správu stolu.
weight: 10
url: /cs/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozdělený stůl

## Zavedení

Stalo se vám někdy, že pracujete s velkou tabulkou v dokumentu aplikace Word a přáli byste si, abyste ji mohli rozdělit na dvě menší, lépe ovladatelné tabulky? No, dnes se ponoříme do toho, jak přesně toho můžete dosáhnout pomocí Aspose.Words pro .NET. Ať už máte co do činění s rozsáhlými datovými tabulkami nebo složitými strukturami dokumentů, rozdělení tabulek může pomoci zlepšit čitelnost a organizaci. Pojďme prozkoumat krok za krokem proces rozdělení tabulky pomocí Aspose.Words for .NET.

## Předpoklady

Než se pustíme do výukového programu, ujistěte se, že máte následující:

1.  Knihovna Aspose.Words for .NET: Ujistěte se, že jste si stáhli a nainstalovali knihovnu Aspose.Words for .NET. Můžete to získat z[Aspose stránku vydání](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Nastavte vývojové prostředí s podporou rozhraní .NET, jako je Visual Studio.
3. Ukázkový dokument: Připravte dokument Word (`Tables.docx`) s alespoň jednou tabulkou pro použití operace rozdělení.

## Importovat jmenné prostory

Nejprve do projektu importujte potřebné jmenné prostory. To vám umožní přístup ke třídám a metodám poskytovaným Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Vložte dokument

Začněme načtením dokumentu obsahujícího tabulku, kterou chcete rozdělit. Ujistěte se, že jste zadali správnou cestu k dokumentu.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Krok 2: Identifikujte tabulku k rozdělení

Dále identifikujte a načtěte tabulku, kterou chcete rozdělit. V tomto příkladu zacílíme na první tabulku v dokumentu.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Krok 3: Vyberte řádek k rozdělení

Určete řádek, kde chcete tabulku rozdělit. Zde rozdělujeme tabulku na třetí řádek (včetně).

```csharp
Row row = firstTable.Rows[2];
```

## Krok 4: Vytvořte nový kontejner tabulky

Vytvořte nový kontejner tabulky pro uložení řádků, které budou přesunuty z původní tabulky.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Krok 5: Vložte nový kontejner tabulky

Vložte nový kontejner tabulky hned za původní tabulku v dokumentu.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Krok 6: Přidejte odstavec vyrovnávací paměti

Přidejte odstavec vyrovnávací paměti mezi dvě tabulky, abyste zajistili, že zůstanou oddělené.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## Krok 7: Přesuňte řádky do nové tabulky

Přesuňte řádky z původní tabulky do nového kontejneru tabulky. Tato smyčka pokračuje, dokud není zadaný řádek (včetně) přesunut.

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## Krok 8: Uložte dokument

Nakonec uložte upravený dokument s rozdělenými tabulkami.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Závěr

A tady to máte! Podle těchto kroků můžete snadno rozdělit tabulku v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tento přístup vám pomáhá efektivněji spravovat velké tabulky a zlepšuje čitelnost a organizaci vašich dokumentů. Vyzkoušejte a uvidíte, jak vám zjednoduší práci s tabulkami v dokumentech aplikace Word.

## FAQ

### Mohu rozdělit tabulku na více řádků?
Ano, tabulku můžete rozdělit na více řádků opakováním procesu pro každý dělicí bod.

### Co se stane s formátováním původní tabulky?
Nová tabulka zdědí formátování původní tabulky. Na novou tabulku lze podle potřeby použít jakékoli konkrétní změny formátování.

### Je možné sloučit tabulky zpět dohromady?
Ano, tabulky můžete sloučit přesouváním řádků z jedné tabulky do druhé pomocí podobných metod.

### Funguje tato metoda s vnořenými tabulkami?
Ano, Aspose.Words for .NET podporuje také operace na vnořených tabulkách.

### Mohu tento proces automatizovat pro více dokumentů?
Absolutně! Můžete vytvořit skript nebo aplikaci pro automatizaci procesu rozdělování tabulky pro více dokumentů.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
"description": "Naučte se, jak zakázat zalomení řádků napříč stránkami v dokumentech Word pomocí Aspose.Words pro .NET a zachovat tak čitelnost a formátování tabulek."
"linktitle": "Formát řádků Zakázat zalomení napříč stránkami"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Formát řádků Zakázat zalomení napříč stránkami"
"url": "/cs/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formát řádků Zakázat zalomení napříč stránkami

## Zavedení

Při práci s tabulkami v dokumentech aplikace Word se můžete ujistit, že se řádky nezalomí napříč stránkami, což může být nezbytné pro zachování čitelnosti a formátování dokumentů. Aspose.Words pro .NET nabízí snadný způsob, jak zakázat zalomení řádků napříč stránkami.

tomto tutoriálu vás provedeme procesem zakázání zalomení řádků napříč stránkami v dokumentu Word pomocí Aspose.Words pro .NET.

## Předpoklady

Než začneme, ujistěte se, že máte následující předpoklady:
- Nainstalována knihovna Aspose.Words pro .NET.
- Dokument aplikace Word s tabulkou, která se rozkládá na více stránkách.

## Importovat jmenné prostory

Nejprve importujte potřebné jmenné prostory do projektu:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Vložení dokumentu

Načtěte dokument obsahující tabulku, která se rozkládá na více stránkách.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Krok 2: Přístup k tabulce

Otevřete první tabulku v dokumentu. Předpokládá se, že tabulka, kterou chcete upravit, je první tabulkou v dokumentu.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Krok 3: Zakázat rozdělení na stránky pro všechny řádky

Projděte každý řádek v tabulce a nastavte `AllowBreakAcrossPages` majetek `false`Tím je zajištěno, že se řádky nebudou napříč stránkami zalomovat.

```csharp
// Zakázat rozdělení na stránky pro všechny řádky v tabulce.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Krok 4: Uložte dokument

Uložte upravený dokument do vámi určeného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Závěr

V tomto tutoriálu jsme si ukázali, jak zakázat zalomení řádků napříč stránkami v dokumentu Word pomocí Aspose.Words pro .NET. Dodržením výše uvedených kroků zajistíte, že řádky tabulky zůstanou neporušené a nebudou se rozdělovat napříč stránkami, čímž si zachováte čitelnost a formátování dokumentu.

## Často kladené otázky

### Mohu zakázat zalomení řádků napříč stránkami pro konkrétní řádek místo pro všechny řádky?  
Ano, zalomení řádků pro konkrétní řádky můžete zakázat tak, že se dostanete k požadovanému řádku a nastavíte jeho `AllowBreakAcrossPages` majetek `false`.

### Funguje tato metoda i pro tabulky se sloučenými buňkami?  
Ano, tato metoda funguje pro tabulky se sloučenými buňkami. Vlastnost `AllowBreakAcrossPages` platí pro celý řádek bez ohledu na sloučení buněk.

### Bude tato metoda fungovat, pokud je tabulka vnořená uvnitř jiné tabulky?  
Ano, k vnořeným tabulkám můžete přistupovat a upravovat je stejným způsobem. Ujistěte se, že na vnořenou tabulku správně odkazujete pomocí jejího indexu nebo jiných vlastností.

### Jak mohu zkontrolovat, zda řádek umožňuje zalomení napříč stránkami?  
Zda řádek umožňuje rozdělení na další stránky, můžete zkontrolovat přístupem k `AllowBreakAcrossPages` majetek `RowFormat` a kontrolu jeho hodnoty.

### Existuje způsob, jak toto nastavení použít na všechny tabulky v dokumentu?  
Ano, můžete procházet všechny tabulky v dokumentu a toto nastavení použít na každou z nich.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
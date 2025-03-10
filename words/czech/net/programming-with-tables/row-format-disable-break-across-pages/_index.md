---
title: Formát řádku Zakázat zalomení mezi stránkami
linktitle: Formát řádku Zakázat zalomení mezi stránkami
second_title: Aspose.Words API pro zpracování dokumentů
description: Zjistěte, jak zakázat zalomení řádků mezi stránkami v dokumentech aplikace Word pomocí Aspose.Words for .NET, abyste zachovali čitelnost a formátování tabulky.
weight: 10
url: /cs/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formát řádku Zakázat zalomení mezi stránkami

## Zavedení

Při práci s tabulkami v dokumentech aplikace Word můžete chtít zajistit, aby se řádky na stránkách nelámaly, což může být nezbytné pro zachování čitelnosti a formátování dokumentů. Aspose.Words for .NET poskytuje snadný způsob, jak zakázat zalomení řádků na stránkách.

V tomto tutoriálu vás provedeme procesem deaktivace zalomení řádků na stránkách v dokumentu aplikace Word pomocí Aspose.Words for .NET.

## Předpoklady

Než začneme, ujistěte se, že máte následující předpoklady:
- Nainstalovaná knihovna Aspose.Words for .NET.
- Dokument aplikace Word s tabulkou, která zahrnuje více stránek.

## Importovat jmenné prostory

Nejprve do projektu importujte potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Vložte dokument

Vložte dokument obsahující tabulku, která zahrnuje více stránek.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Krok 2: Přístup k tabulce

Přístup k první tabulce v dokumentu. To předpokládá, že tabulka, kterou chcete upravit, je první tabulkou v dokumentu.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Krok 3: Zakažte rozdělení stránek na všechny řádky

 Procházejte každý řádek v tabulce a nastavte`AllowBreakAcrossPages`majetek do`false`. Tím je zajištěno, že se řádky na stránkách nebudou lámat.

```csharp
// Zakázat rozdělení na stránky pro všechny řádky v tabulce.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Krok 4: Uložte dokument

Uložte upravený dokument do určeného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Závěr

V tomto tutoriálu jsme ukázali, jak zakázat zalomení řádků mezi stránkami v dokumentu aplikace Word pomocí Aspose.Words for .NET. Dodržením výše uvedených kroků můžete zajistit, že řádky tabulky zůstanou nedotčené a nebudou se rozdělovat na stránky, čímž se zachová čitelnost a formátování dokumentu.

## FAQ

### Mohu zakázat zalomení řádků na stránkách pro konkrétní řádek namísto všech řádků?  
 Ano, zalomení řádků pro konkrétní řádky můžete zakázat přístupem k požadovanému řádku a jeho nastavením`AllowBreakAcrossPages`majetek do`false`.

### Funguje tato metoda pro tabulky se sloučenými buňkami?  
 Ano, tato metoda funguje pro tabulky se sloučenými buňkami. Nemovitost`AllowBreakAcrossPages` platí pro celý řádek bez ohledu na sloučení buněk.

### Bude tato metoda fungovat, pokud je tabulka vnořena do jiné tabulky?  
Ano, stejným způsobem můžete přistupovat a upravovat vnořené tabulky. Ujistěte se, že správně odkazujete na vnořenou tabulku pomocí jejího indexu nebo jiných vlastností.

### Jak mohu zkontrolovat, zda řádek umožňuje přerušení mezi stránkami?  
 Můžete zkontrolovat, zda řádek umožňuje přerušení mezi stránkami přístupem k`AllowBreakAcrossPages` vlastnictvím`RowFormat` a kontrolu jeho hodnoty.

### Existuje způsob, jak toto nastavení použít na všechny tabulky v dokumentu?  
Ano, můžete procházet všechny tabulky v dokumentu a použít toto nastavení pro každou z nich.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
title: Escape URI v dokumentu PDF
linktitle: Escape URI v dokumentu PDF
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak uniknout z URI v souborech PDF pomocí Aspose.Words for .NET. Tento podrobný průvodce vás provede procesem krok za krokem.
weight: 10
url: /cs/net/programming-with-pdfsaveoptions/escape-uri/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Escape URI v dokumentu PDF

## Zavedení

Ahoj! Přemýšleli jste někdy, jak zacházet s URI při ukládání dokumentu aplikace Word jako PDF pomocí Aspose.Words for .NET? Jste na správném místě! Dnes se ponoříme hluboko do únikových URI v dokumentech PDF, abychom zajistili jejich správnou funkci při převodu dokumentu. Vydejme se na tuto cestu společně, krok za krokem, a ujistěte se, že na cestě pochopíte každý koncept.

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words for .NET: Ujistěte se, že máte nejnovější verzi. Můžete si jej stáhnout[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí .NET.
3. Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti o programování v C#.

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory. To je zásadní pro přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dobře, pojďme si tento proces rozdělit na stravitelné kroky. Postupujte podle toho a okamžitě budete profesionálem v úniku z URI!

## Krok 1: Nastavte adresář dokumentů

Než se ponoříte do kódu, nastavte cestu k adresáři dokumentů. Zde budou uloženy vaše soubory.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete uložit dokument PDF.

## Krok 2: Vytvořte nový dokument

Dále vytvoříme nový dokument pomocí Aspose.Words. Tento dokument bude sloužit jako naše plátno pro vkládání hypertextových odkazů.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Zde,`Document` je váš nový dokument aplikace Word a`DocumentBuilder` je pomocná třída, která zjednodušuje proces vytváření dokumentu.

## Krok 3: Vložte hypertextový odkaz

Nyní do dokumentu vložíme hypertextový odkaz. Tento hypertextový odkaz bude středem našeho procesu úniku z URI.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose", false);
```

 V tomto řádku`"Testlink"` je zobrazovaný text pro hypertextový odkaz a`"https://www.google.com/search?q= aspose"` je URL. The`false` parametr označuje, že odkaz by neměl být formátován jako hypertextový odkaz (tj. nebude podtržený a modrý).

## Krok 4: Uložte dokument jako PDF

Nakonec dokument uložte jako PDF. Zde se Aspose.Words stará o únik z URI ve výstupu PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

 Tento řádek uloží dokument do zadaného adresáře s názvem souboru`WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## Závěr

A tady to máte! Právě jste se naučili, jak uniknout URI při ukládání dokumentu aplikace Word jako PDF pomocí Aspose.Words for .NET. Tento proces zajišťuje, že vaše hypertextové odkazy zůstanou ve výsledném PDF funkční a správně naformátované. 

Pamatujte, že zvládnutí těchto malých, ale významných technik může výrazně zlepšit kvalitu a funkčnost vašich dokumentů. Šťastné kódování!

## FAQ

### Co je Aspose.Words for .NET?

Aspose.Words for .NET je výkonná knihovna, která umožňuje vývojářům vytvářet, manipulovat a převádět dokumenty aplikace Word v aplikacích .NET.

### Proč je escapování URI důležité v souborech PDF?

Escapování URI zajišťuje správnou interpretaci speciálních znaků v adresách URL, zabraňuje nefunkčním odkazům a zajišťuje, že fungují tak, jak mají.

### Mohu v Aspose.Words pro .NET použít jiné typy odkazů?

Absolutně! Aspose.Words podporuje různé typy odkazů, včetně odkazů na interní dokumenty, záložek a externích adres URL.

### Jak mohu získat bezplatnou zkušební verzi Aspose.Words pro .NET?

 Můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?

 Můžete najít podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

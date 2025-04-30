---
"description": "Naučte se, jak pomocí Aspose.Words pro .NET escapovat URI v PDF souborech. Tato podrobná příručka vás krok za krokem provede celým procesem."
"linktitle": "URI escape v dokumentu PDF"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "URI escape v dokumentu PDF"
"url": "/cs/net/programming-with-pdfsaveoptions/escape-uri/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# URI escape v dokumentu PDF

## Zavedení

Ahoj! Přemýšleli jste někdy, jak zacházet s URI při ukládání dokumentu Word jako PDF pomocí Aspose.Words pro .NET? Jste na správném místě! Dnes se podrobně ponoříme do escapování URI v dokumentech PDF, abychom zajistili jejich správné fungování při převodu dokumentu. Pojďme se na tuto cestu společně vydat krok za krokem a ujistit se, že pochopíte každý koncept.

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete:

1. Aspose.Words pro .NET: Ujistěte se, že máte nejnovější verzi. Můžete si ji stáhnout [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí pro .NET.
3. Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti programování v C#.

## Importovat jmenné prostory

Nejdříve je potřeba importovat potřebné jmenné prostory. To je klíčové pro přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dobře, pojďme si celý proces rozdělit na srozumitelné kroky. Sledujte je a brzy se stanete profesionálem v escapování URI!

## Krok 1: Nastavení adresáře dokumentů

Než se ponoříte do kódu, nastavte cestu k adresáři s dokumenty. Zde budou vaše soubory uloženy.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete dokument PDF uložit.

## Krok 2: Vytvořte nový dokument

Dále vytvoříme nový dokument pomocí Aspose.Words. Tento dokument bude sloužit jako naše plátno pro vkládání hypertextových odkazů.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Zde, `Document` je váš nový dokument Wordu a `DocumentBuilder` je pomocná třída, která zjednodušuje proces vytváření dokumentů.

## Krok 3: Vložení hypertextového odkazu

Nyní vložme do dokumentu hypertextový odkaz. Tento hypertextový odkaz bude středem našeho procesu escapování URI.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose", false);
```

V tomto řádku, `"Testlink"` je zobrazovaný text pro hypertextový odkaz a `"https://www.google.com/search?q= aspose"` je URL adresa. `false` Parametr označuje, že odkaz by neměl být formátován jako hypertextový odkaz (tj. nebude podtržený a modře zobrazený).

## Krok 4: Uložte dokument jako PDF

Nakonec uložte dokument jako PDF. Zde se Aspose.Words postará o escapování URI ve výstupu PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

Tento řádek uloží dokument do zadaného adresáře s názvem souboru `WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## Závěr

A tady to máte! Právě jste se naučili, jak escapovat URI při ukládání dokumentu Word jako PDF pomocí Aspose.Words pro .NET. Tento proces zajišťuje, že vaše hypertextové odkazy zůstanou ve výsledném PDF funkční a správně naformátované. 

Nezapomeňte, že zvládnutí těchto malých, ale důležitých technik může výrazně zlepšit kvalitu a funkčnost vašich dokumentů. Přeji vám šťastné programování!

## Často kladené otázky

### Co je Aspose.Words pro .NET?

Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům vytvářet, manipulovat a převádět dokumenty Wordu v aplikacích .NET.

### Proč je v PDF důležité escapovat URI?

Řízení URI kódů zajišťuje správnou interpretaci speciálních znaků v URL adresách, čímž se zabraňuje nefunkčním odkazům a zajišťuje se jejich fungování podle očekávání.

### Mohu v Aspose.Words pro .NET použít i jiné typy odkazů?

Rozhodně! Aspose.Words podporuje různé typy odkazů, včetně interních odkazů na dokumenty, záložek a externích URL adres.

### Jak mohu získat bezplatnou zkušební verzi Aspose.Words pro .NET?

Můžete získat bezplatnou zkušební verzi [zde](https://releases.aspose.com/).

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?

Podrobnou dokumentaci naleznete [zde](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
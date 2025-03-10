---
title: Exportujte záložky Záhlaví dokumentu Word do dokumentu PDF
linktitle: Exportujte záložky Záhlaví dokumentu Word do dokumentu PDF
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se exportovat záložky záhlaví a zápatí z dokumentu aplikace Word do PDF pomocí Aspose.Words for .NET s naším podrobným průvodcem.
weight: 10
url: /cs/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportujte záložky Záhlaví dokumentu Word do dokumentu PDF

## Zavedení

Převod dokumentů aplikace Word do formátu PDF je běžný úkol, zejména pokud chcete dokumenty sdílet nebo archivovat při zachování jejich formátování. Někdy tyto dokumenty obsahují důležité záložky v záhlaví a zápatí. V tomto tutoriálu projdeme procesem exportu těchto záložek z dokumentu Word do PDF pomocí Aspose.Words for .NET.

## Předpoklady

Než se ponoříme, ujistěte se, že máte následující:

- Aspose.Words for .NET: Musíte mít nainstalovanou aplikaci Aspose.Words for .NET. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Nastavte své vývojové prostředí. Můžete použít Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
- Základní znalost C#: Spolu s příklady kódu je vyžadována znalost programování C#.

## Importovat jmenné prostory

Nejprve musíte do svého projektu C# importovat potřebné jmenné prostory. Přidejte tyto řádky do horní části souboru kódu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Pojďme si tento proces rozdělit do snadno pochopitelných kroků.

## Krok 1: Inicializujte dokument

Prvním krokem je načtení dokumentu aplikace Word. Můžete to udělat takto:

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

V tomto kroku jednoduše zadáte cestu k adresáři dokumentů a načtete dokument aplikace Word.

## Krok 2: Nakonfigurujte možnosti uložení PDF

Dále musíte nakonfigurovat možnosti ukládání PDF, abyste zajistili, že se záložky v záhlaví a zápatí exportují správně.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Zde nastavujeme`PdfSaveOptions` . The`DefaultBookmarksOutlineLevel` vlastnost nastavuje úroveň osnovy pro záložky a`HeaderFooterBookmarksExportMode` vlastnost zajišťuje, že se exportuje pouze první výskyt záložek v záhlaví a zápatí.

## Krok 3: Uložte dokument jako PDF

Nakonec uložte dokument jako PDF s nakonfigurovanými možnostmi.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

V tomto kroku ukládáte dokument do zadané cesty s možnostmi, které jste nakonfigurovali.

## Závěr

tady to máte! Podle těchto kroků můžete snadno exportovat záložky ze záhlaví a zápatí dokumentu aplikace Word do PDF pomocí Aspose.Words for .NET. Tato metoda zajišťuje zachování důležitých navigačních pomůcek v dokumentu ve formátu PDF, což čtenářům usnadňuje procházení dokumentu.

## FAQ

### Mohu exportovat všechny záložky z dokumentu Word do PDF?

 Ano, můžete. V`PdfSaveOptions`, můžete v případě potřeby upravit nastavení tak, aby zahrnovala všechny záložky.

### Co když chci exportovat záložky i z těla dokumentu?

 Můžete nakonfigurovat`OutlineOptions` v`PdfSaveOptions` zahrnout záložky z těla dokumentu.

### Je možné upravit úrovně záložek v PDF?

 Absolutně! Můžete si přizpůsobit`DefaultBookmarksOutlineLevel` vlastnost pro nastavení různých úrovní obrysu pro vaše záložky.

### Jak mohu pracovat s dokumenty bez záložek?

Pokud váš dokument nemá žádné záložky, bude PDF vygenerováno bez obrysu záložek. Ujistěte se, že váš dokument obsahuje záložky, pokud je v PDF potřebujete.

### Mohu tuto metodu použít pro jiné typy dokumentů, jako je DOCX nebo RTF?

Ano, Aspose.Words for .NET podporuje různé typy dokumentů, včetně DOCX, RTF a dalších.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
"description": "Naučte se, jak exportovat záložky záhlaví a zápatí z dokumentu Word do PDF pomocí Aspose.Words pro .NET s naším podrobným návodem."
"linktitle": "Export záložek záhlaví, zápatí a patičky dokumentu Word do dokumentu PDF"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Export záložek záhlaví, zápatí a patičky dokumentu Word do dokumentu PDF"
"url": "/cs/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Export záložek záhlaví, zápatí a patičky dokumentu Word do dokumentu PDF

## Zavedení

Převod dokumentů Word do PDF je běžný úkol, zejména pokud chcete sdílet nebo archivovat dokumenty a zároveň zachovat jejich formátování. Někdy tyto dokumenty obsahují důležité záložky v záhlaví a zápatí. V tomto tutoriálu si projdeme procesem exportu těchto záložek z dokumentu Word do PDF pomocí Aspose.Words pro .NET.

## Předpoklady

Než se do toho pustíme, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Musíte mít nainstalovaný Aspose.Words pro .NET. Můžete si ho stáhnout z [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Nastavte si vývojové prostředí. Můžete použít Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
- Základní znalost C#: Pro sledování příkladů kódu je nutná znalost programování v C#.

## Importovat jmenné prostory

Nejdříve je potřeba importovat potřebné jmenné prostory do vašeho projektu v C#. Na začátek souboru s kódem přidejte tyto řádky:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Rozdělme si proces na snadno sledovatelné kroky.

## Krok 1: Inicializace dokumentu

Prvním krokem je načtení dokumentu Word. Zde je návod, jak to udělat:

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

V tomto kroku jednoduše zadáte cestu k adresáři dokumentů a načtete dokument aplikace Word.

## Krok 2: Konfigurace možností ukládání PDF

Dále je třeba nakonfigurovat možnosti ukládání PDF, abyste zajistili správný export záložek v záhlaví a zápatí.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

Zde nastavujeme `PdfSaveOptions`Ten/Ta/To `DefaultBookmarksOutlineLevel` Vlastnost nastavuje úroveň osnovy pro záložky a `HeaderFooterBookmarksExportMode` Vlastnost zajišťuje, že se exportuje pouze první výskyt záložek v záhlaví a zápatí.

## Krok 3: Uložte dokument jako PDF

Nakonec uložte dokument jako PDF s nakonfigurovanými možnostmi.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

V tomto kroku ukládáte dokument do zadané cesty s nastaveními, která jste nakonfigurovali.

## Závěr

máte to! Pomocí těchto kroků můžete snadno exportovat záložky ze záhlaví a zápatí dokumentu Word do PDF pomocí Aspose.Words pro .NET. Tato metoda zajišťuje, že důležité navigační pomůcky v dokumentu zůstanou zachovány ve formátu PDF, což čtenářům usnadní navigaci v dokumentu.

## Často kladené otázky

### Mohu exportovat všechny záložky z dokumentu Word do PDF?

Ano, můžete. V `PdfSaveOptions`, můžete v případě potřeby upravit nastavení tak, aby zahrnovalo všechny záložky.

### Co když chci exportovat záložky i z těla dokumentu?

Můžete nakonfigurovat `OutlveOptions` in `PdfSaveOptions` zahrnout záložky z těla dokumentu.

### Je možné přizpůsobit úrovně záložek v PDF?

Rozhodně! Můžete si to přizpůsobit `DefaultBookmarksOutlineLevel` vlastnost pro nastavení různých úrovní osnovy pro záložky.

### Jak mám pracovat s dokumenty bez záložek?

Pokud váš dokument neobsahuje žádné záložky, bude PDF vygenerován bez obrysu záložek. Pokud je v PDF potřebujete, ujistěte se, že dokument obsahuje záložky.

### Mohu tuto metodu použít i pro jiné typy dokumentů, jako je DOCX nebo RTF?

Ano, Aspose.Words pro .NET podporuje různé typy dokumentů, včetně DOCX, RTF a dalších.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
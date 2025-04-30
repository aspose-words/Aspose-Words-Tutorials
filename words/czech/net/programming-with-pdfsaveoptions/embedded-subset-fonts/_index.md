---
"description": "Zmenšete velikost PDF souboru vložením pouze nezbytných podmnožin písem pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu k efektivní optimalizaci vašich PDF souborů."
"linktitle": "Vložení podmnožin písem do dokumentu PDF"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložení podmnožin písem do dokumentu PDF"
"url": "/cs/net/programming-with-pdfsaveoptions/embedded-subset-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení podmnožin písem do dokumentu PDF

## Zavedení

Všimli jste si někdy, že některé soubory PDF jsou mnohem větší než jiné, i když obsahují podobný obsah? Příčinou jsou často písma. Vkládání písem do PDF souboru zajišťuje, že bude vypadat stejně na jakémkoli zařízení, ale může také zvětšit velikost souboru. Naštěstí Aspose.Words pro .NET nabízí praktickou funkci pro vkládání pouze nezbytných podmnožin písem, čímž udrží vaše PDF soubory štíhlé a efektivní. Tento tutoriál vás krok za krokem provede celým procesem.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
- Prostředí .NET: Ujistěte se, že máte funkční vývojové prostředí .NET.
- Základní znalost C#: Znalost programování v C# vám pomůže se v textu orientovat.

## Importovat jmenné prostory

Chcete-li používat Aspose.Words pro .NET, musíte do projektu importovat potřebné jmenné prostory. Přidejte je na začátek souboru C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Vložení dokumentu

Nejprve musíme načíst dokument Wordu, který chceme převést do PDF. To se provádí pomocí `Document` třída poskytovaná Aspose.Words.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Tento úryvek kódu načte dokument umístěný na adrese `dataDir`Nezapomeňte vyměnit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu dokumentu.

## Krok 2: Konfigurace možností ukládání PDF

Dále nakonfigurujeme `PdfSaveOptions` aby se zajistilo, že budou vloženy pouze potřebné podmnožiny písem. Nastavením `EmbedFullFonts` na `false`, říkáme Aspose.Words, aby vložil pouze glyfy použité v dokumentu.

```csharp
// Výstupní PDF bude obsahovat podmnožiny písem v dokumentu.
// V písmech PDF jsou zahrnuty pouze glyfy použité v dokumentu.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Tento malý, ale zásadní krok pomáhá výrazně zmenšit velikost souboru PDF.

## Krok 3: Uložte dokument jako PDF

Nakonec dokument uložíme jako PDF pomocí `Save` metoda s použitím nakonfigurovaného `PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

Tento kód vygeneruje PDF soubor s názvem `WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` zadaném adresáři, s vloženými pouze potřebnými podmnožinami písem.

## Závěr

A tady to máte! Dodržováním těchto jednoduchých kroků můžete efektivně zmenšit velikost souborů PDF vložením pouze potřebných podmnožin písem pomocí Aspose.Words pro .NET. To nejen šetří úložný prostor, ale také zajišťuje rychlejší načítání a lepší výkon, zejména u dokumentů s rozsáhlým množstvím písem.

## Často kladené otázky

### Proč bych měl do PDF vkládat pouze podmnožiny písem?
Vložení pouze nezbytných podmnožin písem může výrazně zmenšit velikost souboru PDF, aniž by to ovlivnilo vzhled a čitelnost dokumentu.

### Mohu se v případě potřeby vrátit k vkládání plných písem?
Ano, můžete. Jednoduše nastavte `EmbedFullFonts` majetek `true` v `PdfSaveOptions`.

### Podporuje Aspose.Words pro .NET i další funkce optimalizace PDF?
Rozhodně! Aspose.Words pro .NET nabízí řadu možností pro optimalizaci PDF souborů, včetně komprese obrázků a odstraňování nepoužívaných objektů.

### Jaké typy písem lze vkládat do podmnožin pomocí Aspose.Words pro .NET?
Aspose.Words pro .NET podporuje vkládání podmnožin pro všechna písma TrueType použitá v dokumentu.

### Jak mohu ověřit, která písma jsou vložena do mého PDF?
PDF soubor můžete otevřít v programu Adobe Acrobat Reader a vložená písma zobrazit ve vlastnostech na kartě Písma.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
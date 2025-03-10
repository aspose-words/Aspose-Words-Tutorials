---
title: Vložení podmnožin písem do dokumentu PDF
linktitle: Vložení podmnožin písem do dokumentu PDF
second_title: Aspose.Words API pro zpracování dokumentů
description: Zmenšete velikost souboru PDF vložením pouze nezbytných podmnožin písem pomocí Aspose.Words for .NET. Chcete-li efektivně optimalizovat soubory PDF, postupujte podle našeho podrobného průvodce.
weight: 10
url: /cs/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení podmnožin písem do dokumentu PDF

## Zavedení

Všimli jste si někdy, že některé soubory PDF jsou mnohem větší než jiné, i když obsahují podobný obsah? Viník často leží v písmech. Vložení písem do PDF zajistí, že bude vypadat stejně na jakémkoli zařízení, ale také může zvětšit velikost souboru. Naštěstí Aspose.Words for .NET nabízí šikovnou funkci pro vložení pouze nezbytných podmnožin písem, takže vaše PDF budou štíhlé a efektivní. Tento tutoriál vás provede procesem krok za krokem.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

-  Aspose.Words for .NET: Můžete si ji stáhnout[zde](https://releases.aspose.com/words/net/).
- Prostředí .NET: Ujistěte se, že máte funkční vývojové prostředí .NET.
- Základní znalost C#: Znalost programování v C# vám pomůže pokračovat.

## Importovat jmenné prostory

Chcete-li používat Aspose.Words pro .NET, musíte do projektu importovat potřebné jmenné prostory. Přidejte je do horní části souboru C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Vložte dokument

 Nejprve musíme načíst dokument Word, který chceme převést do PDF. To se provádí pomocí`Document` třídy poskytuje Aspose.Words.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Tento fragment kódu načte dokument umístěný na`dataDir` . Nezapomeňte vyměnit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu dokumentu.

## Krok 2: Nakonfigurujte možnosti uložení PDF

 Dále nakonfigurujeme`PdfSaveOptions` abyste zajistili, že budou vloženy pouze nezbytné podmnožiny písem. Nastavením`EmbedFullFonts` na`false`, řekneme Aspose.Words, aby vložil pouze glyfy použité v dokumentu.

```csharp
// Výstupní PDF bude obsahovat podmnožiny písem v dokumentu.
// Do písem PDF jsou zahrnuty pouze glyfy použité v dokumentu.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Tento malý, ale zásadní krok pomáhá výrazně snížit velikost souboru PDF.

## Krok 3: Uložte dokument jako PDF

 Nakonec dokument uložíme jako PDF pomocí`Save` metoda, použití nakonfigurovaného`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

 Tento kód vygeneruje soubor PDF s názvem`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` v zadaném adresáři s vloženými pouze nezbytnými podmnožinami písem.

## Závěr

tady to máte! Pomocí těchto jednoduchých kroků můžete efektivně zmenšit velikost souborů PDF vložením pouze nezbytných podmnožin písem pomocí Aspose.Words for .NET. To nejen šetří úložný prostor, ale také zajišťuje rychlejší načítání a lepší výkon, zejména u dokumentů s rozsáhlými písmy.

## FAQ

### Proč bych měl do PDF vkládat pouze podmnožiny písem?
Vložení pouze nezbytných podmnožin písem může výrazně snížit velikost souboru PDF, aniž by došlo ke snížení vzhledu a čitelnosti dokumentu.

### Mohu se v případě potřeby vrátit k vkládání plných písem?
 Ano, můžete. Jednoduše nastavte`EmbedFullFonts`majetek do`true` v`PdfSaveOptions`.

### Podporuje Aspose.Words for .NET další funkce pro optimalizaci PDF?
Absolutně! Aspose.Words for .NET nabízí řadu možností pro optimalizaci souborů PDF, včetně komprese obrázků a odstranění nepoužívaných objektů.

### Jaké typy písem lze vložit pomocí Aspose.Words pro .NET?
Aspose.Words for .NET podporuje vkládání podmnožin pro všechna písma TrueType použitá v dokumentu.

### Jak mohu ověřit, která písma jsou vložena do mého PDF?
Soubor PDF můžete otevřít v aplikaci Adobe Acrobat Reader a zkontrolovat vlastnosti na kartě Písma, abyste viděli vložená písma.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

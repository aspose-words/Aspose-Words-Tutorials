---
title: Nastavit systém složek písem a vlastní složku
linktitle: Nastavit systém složek písem a vlastní složku
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit systémové a vlastní složky písem v dokumentech aplikace Word pomocí Aspose.Words for .NET, abyste zajistili správné zobrazení dokumentů v různých prostředích.
weight: 10
url: /cs/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavit systém složek písem a vlastní složku

## Zavedení

Představte si, že vytváříte dokument s jedinečným stylem písma, jen abyste zjistili, že se písma na jiném počítači nezobrazují správně. Frustrující, že? Zde přichází na řadu konfigurace složek písem. S Aspose.Words for .NET můžete definovat systémové a vlastní složky písem, abyste zajistili, že vaše dokumenty budou vždy vypadat tak, jak bylo zamýšleno. Pojďme se ponořit do toho, jak toho můžete dosáhnout.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

-  Aspose.Words for .NET Library: Pokud jste tak ještě neučinili, stáhněte si ji[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: IDE jako Visual Studio.
- Základní znalost C#: Znalost C# vám pomůže sledovat příklady kódu.

## Importovat jmenné prostory

Nejprve do projektu importujte potřebné jmenné prostory:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si celý proces rozdělíme do jednoduchých kroků.

## Krok 1: Vložte dokument

 Chcete-li začít, načtěte dokument aplikace Word do souboru Aspose.Words`Document` objekt. Tento dokument bude ten, kde chcete nastavit složky písem.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 2: Inicializujte nastavení písma

 Vytvořte novou instanci`FontSettings`. Tento objekt vám umožní spravovat zdroje písem.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Krok 3: Načtení systémových zdrojů písem

Načtěte výchozí systémové zdroje písem. Na počítači se systémem Windows to obvykle zahrnuje "Windows\Fonts\" adresář.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Krok 4: Přidejte vlastní složku písem

Přidejte vlastní složku, která obsahuje vaše další písma. To je užitečné, pokud nemáte v systémovém adresáři fontů nainstalována specifická písma.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Krok 5: Aktualizujte zdroje písem

 Převeďte seznam zdrojů písem zpět na pole a nastavte jej na`FontSettings` objekt.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Krok 6: Použijte nastavení písma na dokument

 Nakonec použijte nakonfigurované`FontSettings` do dokumentu a uložte jej v požadovaném formátu, například PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Závěr

tady to máte! Pomocí těchto kroků můžete zajistit, že vaše dokumenty Word používají správná písma, ať už se jedná o systémová písma nebo vlastní písma uložená v určitém adresáři. Toto nastavení pomáhá zachovat integritu vzhledu vašeho dokumentu v různých prostředích.

## FAQ

### Co se stane, když písmo chybí v systémové i vlastní složce?

Aspose.Words použije výchozí písmo k nahrazení chybějícího písma, což zajistí, že dokument zůstane čitelný.

### Mohu přidat více vlastních složek písem?

 Ano, můžete přidat více vlastních složek písem opakováním procesu vytváření`FolderFontSource` objektů a jejich přidání do seznamu zdrojů písem.

### Je možné použít síťové cesty pro vlastní složky písem?

 Ano, můžete zadat síťovou cestu v`FolderFontSource` konstruktér.

### Jaké formáty souborů podporuje Aspose.Words pro ukládání dokumentů?

Aspose.Words podporuje různé formáty, včetně DOCX, PDF, HTML a dalších.

### Jak zpracuji oznámení o záměně písem?

 Oznámení o nahrazení písem můžete zpracovat pomocí`FontSettings` třídy`FontSubstitutionWarning`událost.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

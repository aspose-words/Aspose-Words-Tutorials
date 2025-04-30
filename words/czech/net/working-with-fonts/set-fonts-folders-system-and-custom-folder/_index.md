---
"description": "Naučte se, jak nastavit systémové a vlastní složky s písmy v dokumentech Wordu pomocí Aspose.Words pro .NET a jak zajistit, aby se vaše dokumenty zobrazovaly správně v různých prostředích."
"linktitle": "Nastavení systémových a vlastních složek písem"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení systémových a vlastních složek písem"
"url": "/cs/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení systémových a vlastních složek písem

## Zavedení

Představte si, že vytváříte dokument s jedinečným stylem písma a zjistíte, že se písma na jiném počítači nezobrazují správně. Frustrující, že? A tady přichází na řadu konfigurace složek s písmy. S Aspose.Words pro .NET můžete definovat systémové a vlastní složky s písmy, abyste zajistili, že vaše dokumenty vždy vypadají tak, jak mají. Pojďme se ponořit do toho, jak toho můžete dosáhnout.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

- Knihovna Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si ji [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: IDE, podobné Visual Studiu.
- Základní znalost jazyka C#: Znalost jazyka C# vám pomůže sledovat příklady kódu.

## Importovat jmenné prostory

Nejprve importujte potřebné jmenné prostory do projektu:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si celý proces rozdělme na jednoduché kroky.

## Krok 1: Vložení dokumentu

Chcete-li začít, nahrajte dokument Word do souboru Aspose.Words. `Document` objekt. Tento dokument bude ten, ve kterém chcete nastavit složky písem.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 2: Inicializace nastavení písma

Vytvořte novou instanci `FontSettings`Tento objekt vám umožní spravovat zdroje písem.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Krok 3: Načtení zdrojů systémových písem

Načíst výchozí zdroje systémových písem. V počítači se systémem Windows se obvykle nachází adresář „Windows\Fonts“.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Krok 4: Přidání vlastní složky písem

Přidejte vlastní složku, která bude obsahovat vaše další písma. To je užitečné, pokud máte v systémovém adresáři písem nainstalovaná specifická písma.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Krok 5: Aktualizace zdrojů písem

Převeďte seznam zdrojů písem zpět do pole a nastavte ho na `FontSettings` objekt.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Krok 6: Použití nastavení písma v dokumentu

Nakonec aplikujte nakonfigurované `FontSettings` do dokumentu a uložte jej v požadovaném formátu, například PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Závěr

A je to! Dodržováním těchto kroků zajistíte, že vaše dokumenty Wordu budou používat správná písma, ať už se jedná o systémová písma nebo vlastní písma uložená v určitém adresáři. Toto nastavení pomáhá zachovat integritu vzhledu dokumentu v různých prostředích.

## Často kladené otázky

### Co se stane, když písmo chybí v systémové i vlastní složce?

Aspose.Words použije výchozí písmo k nahrazení chybějícího písma a zajistí tak, aby dokument zůstal čitelný.

### Mohu přidat více vlastních složek s písmy?

Ano, můžete přidat více vlastních složek písem opakováním procesu vytváření `FolderFontSource` objekty a jejich přidání do seznamu zdrojů písem.

### Je možné použít síťové cesty pro vlastní složky písem?

Ano, můžete zadat síťovou cestu v `FolderFontSource` konstruktér.

### Jaké formáty souborů Aspose.Words podporuje pro ukládání dokumentů?

Aspose.Words podporuje různé formáty, včetně DOCX, PDF, HTML a dalších.

### Jak mám zpracovat oznámení o nahrazování písem?

Oznámení o nahrazování písem můžete zpracovat pomocí `FontSettings` třídy `FontSubstitutionWarning` událost.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
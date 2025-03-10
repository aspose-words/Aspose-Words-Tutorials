---
title: Nastavte složky písem s prioritou
linktitle: Nastavte složky písem s prioritou
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit složky písem s prioritou v dokumentech aplikace Word pomocí Aspose.Words for .NET. Náš průvodce zajistí, že se vaše dokumenty pokaždé dokonale vykreslí.
weight: 10
url: /cs/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte složky písem s prioritou

## Zavedení

Ve světě manipulace s dokumenty může nastavení vlastních složek písem znamenat velký rozdíl v zajištění dokonalého vykreslení vašich dokumentů bez ohledu na to, kde jsou zobrazeny. Dnes se ponoříme do toho, jak můžete nastavit složky písem s prioritou v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tento komplexní průvodce vás provede každým krokem a celý proces bude co nejhladší.

## Předpoklady

Než začneme, ujistěte se, že máme vše, co potřebujeme. Zde je rychlý kontrolní seznam:

-  Aspose.Words for .NET: Tuto knihovnu musíte mít nainstalovanou. Pokud ho ještě nemáte, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Ujistěte se, že máte funkční vývojové prostředí .NET, jako je Visual Studio.
-  Adresář dokumentů: Ujistěte se, že máte adresář pro své dokumenty. Pro naše příklady použijeme`"YOUR DOCUMENT DIRECTORY"` jako zástupný symbol pro tuto cestu.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. Tyto jmenné prostory jsou nezbytné pro přístup ke třídám a metodám poskytovaným Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si rozeberme jednotlivé kroky nastavení složek písem s prioritou.

## Krok 1: Nastavte zdroje písem

Chcete-li začít, budete chtít definovat zdroje písem. Zde řeknete Aspose.Words, kde hledat písma. Můžete určit více složek písem a dokonce nastavit jejich prioritu.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

V tomto příkladu nastavujeme dva zdroje písem:
- SystemFontSource: Toto je výchozí zdroj písem, který zahrnuje všechna písma nainstalovaná ve vašem systému.
-  FolderFontSource: Toto je vlastní složka písem umístěná na`C:\\MyFonts\\` . The`true` parametr určuje, že tato složka by měla být kontrolována rekurzivně a`1` stanoví svou prioritu.

## Krok 2: Vložte svůj dokument

Dále načtěte dokument, se kterým chcete pracovat. Ujistěte se, že je dokument umístěn ve vámi určeném adresáři.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Tento řádek kódu načte dokument s názvem`Rendering.docx` z vašeho adresáře dokumentů.

## Krok 3: Uložte dokument s nastavením nového písma

Nakonec dokument uložte. Když dokument uložíte, Aspose.Words použije nastavení písma, které jste zadali.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

 Tím se dokument uloží jako PDF do adresáře dokumentů s názvem`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Závěr

A tady to máte! Úspěšně jste nastavili složky písem s prioritou pomocí Aspose.Words pro .NET. Zadáním vlastních složek písem a priorit můžete zajistit konzistentní vykreslování dokumentů bez ohledu na to, kde jsou zobrazeny. To je užitečné zejména v prostředích, kde nejsou ve výchozím nastavení nainstalována specifická písma.

## FAQ

### Proč bych potřeboval nastavit vlastní složky písem?
Nastavení vlastních složek písem zajišťuje správné vykreslení dokumentů, i když používají písma, která nejsou nainstalována v systému, kde jsou prohlíženy.

### Mohu nastavit více vlastních složek písem?
Ano, můžete zadat více složek písem. Aspose.Words vám umožňuje nastavit prioritu pro každou složku a zajistit, že nejdůležitější písma budou nalezena jako první.

### Co se stane, když písmo chybí ve všech zadaných zdrojích?
Pokud písmo chybí ze všech zadaných zdrojů, Aspose.Words použije záložní písmo, aby bylo zajištěno, že dokument bude stále čitelný.

### Mohu změnit prioritu systémových písem?
Systémová písma jsou ve výchozím nastavení vždy zahrnuta, ale můžete nastavit jejich prioritu vzhledem k vašim vlastním složkám písem.

### Je možné použít síťové cesty pro vlastní složky písem?
Ano, můžete zadat síťové cesty jako vlastní složky písem, což vám umožní centralizovat zdroje písem v síťovém umístění.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

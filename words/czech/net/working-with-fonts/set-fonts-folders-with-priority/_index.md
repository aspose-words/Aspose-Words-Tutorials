---
"description": "Naučte se, jak nastavit prioritu složek s písmy v dokumentech Word pomocí Aspose.Words pro .NET. Náš průvodce zajistí, že se vaše dokumenty budou pokaždé vykreslovat perfektně."
"linktitle": "Nastavení složek s písmy s prioritou"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení složek s písmy s prioritou"
"url": "/cs/net/working-with-fonts/set-fonts-folders-with-priority/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení složek s písmy s prioritou

## Zavedení

Ve světě manipulace s dokumenty může nastavení vlastních složek písem znamenat zásadní rozdíl v zajištění perfektního vykreslení dokumentů bez ohledu na to, kde jsou zobrazeny. Dnes se ponoříme do toho, jak můžete nastavit prioritní složky písem v dokumentech Word pomocí Aspose.Words pro .NET. Tato komplexní příručka vás provede každým krokem a usnadní vám celý proces co nejvíce.

## Předpoklady

Než začneme, ujistěme se, že máme vše, co potřebujeme. Zde je stručný kontrolní seznam:

- Aspose.Words pro .NET: Musíte mít tuto knihovnu nainstalovanou. Pokud ji ještě nemáte, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Ujistěte se, že máte funkční vývojové prostředí .NET, například Visual Studio.
- Adresář dokumentů: Ujistěte se, že máte adresář pro své dokumenty. V našich příkladech použijeme `"YOUR DOCUMENT DIRECTORY"` jako zástupný symbol pro tuto cestu.

## Importovat jmenné prostory

Nejdříve musíme importovat potřebné jmenné prostory. Tyto jmenné prostory jsou nezbytné pro přístup ke třídám a metodám poskytovaným Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si rozeberme jednotlivé kroky pro nastavení složek písem s prioritou.

## Krok 1: Nastavení zdrojů písem

Nejprve budete chtít definovat zdroje písem. Zde sdělíte Aspose.Words, kde má hledat písma. Můžete zadat více složek s písmy a dokonce nastavit jejich prioritu.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

tomto příkladu nastavujeme dva zdroje písma:
- SystemFontSource: Toto je výchozí zdroj písem, který obsahuje všechna písma nainstalovaná ve vašem systému.
- FolderFontSource: Toto je složka s vlastními fonty, která se nachází na adrese `C:\\MyFonts\\`Ten/Ta/To `true` Parametr určuje, že tato složka by měla být prohledána rekurzivně a `1` stanoví si svou prioritu.

## Krok 2: Vložte dokument

Dále načtěte dokument, se kterým chcete pracovat. Ujistěte se, že se dokument nachází ve vámi zadaném adresáři.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Tento řádek kódu načte dokument s názvem `Rendering.docx` z vašeho adresáře dokumentů.

## Krok 3: Uložte dokument s novým nastavením písma

Nakonec dokument uložte. Po uložení dokumentu Aspose.Words použije vámi zadané nastavení písma.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

Tím se dokument uloží jako PDF do adresáře dokumentů s názvem `WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Závěr

tady to máte! Úspěšně jste nastavili složky s písmy s prioritou pomocí Aspose.Words pro .NET. Zadáním vlastních složek s písmy a priorit můžete zajistit, aby se vaše dokumenty vykreslovaly konzistentně bez ohledu na to, kde jsou zobrazeny. To je obzvláště užitečné v prostředích, kde nejsou specifická písma ve výchozím nastavení nainstalována.

## Často kladené otázky

### Proč bych si měl/a nastavit vlastní složky písem?
Nastavení vlastních složek písem zajistí, že se vaše dokumenty budou vykreslovat správně, i když používají písma, která nejsou nainstalována v systému, kde jsou prohlíženy.

### Mohu nastavit více vlastních složek s písmy?
Ano, můžete zadat více složek s písmy. Aspose.Words umožňuje nastavit prioritu pro každou složku, čímž se zajistí, že nejdůležitější písma budou nalezena jako první.

### Co se stane, když písmo chybí ve všech zadaných zdrojích?
Pokud písmo chybí ve všech zadaných zdrojích, Aspose.Words použije záložní písmo, aby zajistila, že dokument bude stále čitelný.

### Mohu změnit prioritu systémových písem?
Systémová písma jsou vždy ve výchozím nastavení zahrnuta, ale můžete nastavit jejich prioritu vzhledem k vašim vlastním složkám písem.

### Je možné použít síťové cesty pro vlastní složky písem?
Ano, můžete zadat síťové cesty jako vlastní složky písem, což vám umožní centralizovat zdroje písem v síťovém umístění.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
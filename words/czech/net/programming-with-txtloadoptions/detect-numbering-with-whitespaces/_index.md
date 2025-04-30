---
"description": "Zjistěte, jak pomocí Aspose.Words pro .NET detekovat číslování s mezerami v dokumentech v prostém textu a zajistit, aby vaše seznamy byly správně rozpoznány."
"linktitle": "Detekce číslování s bílými znaky"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Detekce číslování s bílými znaky"
"url": "/cs/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Detekce číslování s bílými znaky

## Zavedení

Aspose.Words pro nadšence .NET! Dnes se ponoříme do fascinující funkce, která může usnadnit práci se seznamy v dokumentech v prostém textu. Už jste někdy pracovali s textovými soubory, kde některé řádky měly být seznamy, ale po načtení do dokumentu Wordu prostě nevypadaly správně? No, máme v rukávu šikovný trik: detekci číslování s mezerami. Tento tutoriál vás provede používáním... `DetectNumberingWithWhitespaces` možnost v Aspose.Words pro .NET, která zajistí správné rozpoznání seznamů, a to i v případě, že mezi čísly a textem jsou mezery.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Můžete si jej stáhnout z [Aspose Releases](https://releases.aspose.com/words/net/) strana.
- Vývojové prostředí: Visual Studio nebo jakékoli jiné C# IDE.
- Na vašem počítači nainstalovaný .NET Framework.
- Základní znalost C#: Pochopení základů vám pomůže sledovat příklady.

## Importovat jmenné prostory

Než se pustíte do kódu, ujistěte se, že máte v projektu importovány potřebné jmenné prostory. Zde je krátký úryvek pro začátek:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Rozdělme si proces na jednoduché a snadno zvládnutelné kroky. Každý krok vás provede potřebným kódem a vysvětlí, co se děje.

## Krok 1: Definujte adresář dokumentů

Nejdříve si nastavme cestu k adresáři s dokumenty. Zde budou uloženy vaše vstupní a výstupní soubory.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvořte dokument v prostém textu

Dále vytvoříme dokument v prostém textu jako řetězec. Tento dokument bude obsahovat části, které lze interpretovat jako seznamy.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Krok 3: Konfigurace LoadOptions

Pro detekci číslování s bílými znaky musíme nastavit `DetectNumberingWithWhitespaces` možnost `true` v `TxtLoadOptions` objekt.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Krok 4: Vložení dokumentu

Nyní načtěme dokument pomocí `TxtLoadOptions` jako parametr. Tím je zajištěno, že čtvrtý seznam (s mezerami) bude správně detekován.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Krok 5: Uložte dokument

Nakonec dokument uložte do vámi určeného adresáře. Tím se vytvoří dokument Word se správně detekovanými seznamy.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Závěr

tady to máte! S pouhými několika řádky kódu jste zvládli umění detekce číslování s mezerami v dokumentech v prostém textu pomocí Aspose.Words pro .NET. Tato funkce může být neuvěřitelně užitečná při práci s různými textovými formáty a při zajištění toho, aby vaše seznamy byly v dokumentech Word přesně reprezentovány. Takže až příště narazíte na tyto záludné seznamy, budete přesně vědět, co dělat.

## Často kladené otázky

### Co je `DetectNumberingWithWhitespaces` v Aspose.Words pro .NET?
`DetectNumberingWithWhitespaces` je volbou v `TxtLoadOptions` To umožňuje Aspose.Words rozpoznávat seznamy, i když je mezi číslováním a textem položky seznamu mezera.

### Mohu tuto funkci použít i pro jiné oddělovače, jako jsou odrážky a závorky?
Ano, Aspose.Words automaticky detekuje seznamy s běžnými oddělovači, jako jsou odrážky a závorky. `DetectNumberingWithWhitespaces` pomáhá zejména se seznamy, které obsahují mezery.

### Co se stane, když nepoužiji `DetectNumberingWithWhitespaces`?
Bez této možnosti nemusí být seznamy s mezerami mezi číslováním a textem rozpoznány jako seznamy a položky se mohou zobrazit jako obyčejné odstavce.

### Je tato funkce dostupná i v jiných produktech Aspose?
Tato specifická funkce je přizpůsobena pro Aspose.Words pro .NET a je navržena pro zpracování dokumentů Word.

### Jak mohu získat dočasnou licenci pro Aspose.Words pro .NET?
Dočasné povolení můžete získat od [Dočasná licence Aspose](https://purchase.aspose.com/temporary-license/) strana.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
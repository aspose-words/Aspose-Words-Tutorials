---
"description": "Naučte se, jak zachovat starší řídicí znaky v dokumentech Wordu pomocí Aspose.Words pro .NET v tomto podrobném návodu."
"linktitle": "Zachovat starší řídicí znaky"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zachovat starší řídicí znaky"
"url": "/cs/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zachovat starší řídicí znaky

## Zavedení

Už vás někdy mátly ty podivné, neviditelné řídicí znaky ve vašich dokumentech Wordu? Jsou to jako malí, skrytí skřítci, kteří mohou narušit formátování a funkčnost. Naštěstí Aspose.Words pro .NET nabízí praktickou funkci, která tyto starší řídicí znaky zachovává při ukládání dokumentů. V tomto tutoriálu se podrobně ponoříme do toho, jak tyto řídicí znaky spravovat pomocí Aspose.Words pro .NET. Rozebereme si to krok za krokem, abyste pochopili každý detail. Jste připraveni začít? Pojďme se do toho pustit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Stáhnout a nainstalovat z [zde](https://releases.aspose.com/words/net/).
2. Platná licence Aspose: Můžete získat dočasnou licenci [zde](https://purchase.aspose.com/temporary-license/).
3. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE, které podporuje .NET.
4. Základní znalost C#: Znalost programovacího jazyka C# bude užitečná.

## Importovat jmenné prostory

Před napsáním kódu je třeba importovat potřebné jmenné prostory. Na začátek souboru C# přidejte následující řádky:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavení projektu

Nejprve budete muset nastavit svůj projekt ve Visual Studiu (nebo vašem preferovaném IDE). 

1. Vytvoření nového projektu C#: Otevřete Visual Studio a vytvořte nový projekt konzolové aplikace C#.
2. Instalace Aspose.Words pro .NET: K instalaci Aspose.Words pro .NET použijte Správce balíčků NuGet. Klikněte pravým tlačítkem myši na projekt v Průzkumníku řešení, vyberte „Spravovat balíčky NuGet“, vyhledejte „Aspose.Words“ a nainstalujte jej.

## Krok 2: Vložte dokument

Dále načtete dokument aplikace Word, který obsahuje starší řídicí znaky.

1. Zadejte cestu k dokumentu: Nastavte cestu k adresáři s dokumenty.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. Vložení dokumentu: Použijte `Document` třída pro načtení dokumentu.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Krok 3: Konfigurace možností ukládání

Nyní nakonfigurujme možnosti ukládání tak, aby starší řídicí znaky zůstaly zachovány.

1. Vytvoření možností uložení: Inicializace instance `OoxmlSaveOptions` a nastavte `KeepLegacyControlChars` majetek `true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Krok 4: Uložte dokument

Nakonec uložte dokument s nakonfigurovanými možnostmi ukládání.

1. Uložení dokumentu: Použijte `Save` metoda `Document` třída pro uložení dokumentu se zadanými možnostmi uložení.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Závěr

A tady to máte! Dodržováním těchto kroků zajistíte, že vaše starší řídicí znaky budou zachovány při práci s dokumenty Word v Aspose.Words pro .NET. Tato funkce může být záchranou, zejména při práci se složitými dokumenty, kde řídicí znaky hrají klíčovou roli. 

## Často kladené otázky

### Co jsou to starší kontrolní znaky?

Starší řídicí znaky jsou netisknutelné znaky používané ve starších dokumentech k řízení formátování a rozvržení.

### Mohu tyto řídicí znaky odstranit, místo abych je ponechal?

Ano, v případě potřeby můžete tyto znaky odstranit nebo nahradit pomocí Aspose.Words pro .NET.

### Je tato funkce dostupná ve všech verzích Aspose.Words pro .NET?

Tato funkce je k dispozici v novějších verzích. Pro přístup ke všem funkcím používejte nejnovější verzi.

### Potřebuji licenci k používání Aspose.Words pro .NET?

Ano, potřebujete platnou licenci. Můžete získat dočasnou licenci pro účely hodnocení. [zde](https://purchase.aspose.com/temporary-license/).

### Kde najdu další dokumentaci k Aspose.Words pro .NET?

Podrobnou dokumentaci naleznete [zde](https://reference.aspose.com/words/net/).
 


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
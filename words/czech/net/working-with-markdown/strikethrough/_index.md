---
"description": "Naučte se, jak pomocí Aspose.Words pro .NET formátovat text přeškrtnutím pomocí našeho podrobného návodu. Zlepšete si své dovednosti v oblasti zpracování dokumentů."
"linktitle": "Přeškrtnuté"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přeškrtnuté"
"url": "/cs/net/working-with-markdown/strikethrough/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přeškrtnuté

## Zavedení

Vítejte v tomto podrobném návodu, jak pomocí Aspose.Words pro .NET formátovat text přeškrtnutím. Pokud chcete zlepšit své dovednosti v oblasti zpracování dokumentů a dodat textu jedinečný nádech, jste na správném místě. Pojďme se do toho pustit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Stáhněte si jej [zde](https://releases.aspose.com/words/net/).
- .NET Framework: Ujistěte se, že máte v systému nainstalovaný .NET Framework.
- Vývojové prostředí: IDE, podobné Visual Studiu.
- Základní znalost C#: Znalost programování v C# je nezbytná.

## Importovat jmenné prostory

Pro začátek budete muset importovat potřebné jmenné prostory. Ty jsou nezbytné pro přístup ke knihovně Aspose.Words a jejím funkcím.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Inicializace DocumentBuilderu

Ten/Ta/To `DocumentBuilder` třída je mocný nástroj v Aspose.Words, který vám umožňuje snadno přidávat obsah do dokumentu.

```csharp
// Inicializujte DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Krok 2: Nastavení vlastnosti přeškrtnutí

Nyní aplikujme na náš text vlastnost přeškrtnutí. To zahrnuje nastavení `StrikeThrough` majetek `Font` námitka proti `true`.

```csharp
// Text přeškrtněte.
builder.Font.StrikeThrough = true;
```

## Krok 3: Napište text s přeškrtnutím

S nastavenou vlastností přeškrtnutí nyní můžeme přidat náš text. `Writeln` Metoda přidá text do dokumentu.

```csharp
// Pište text s přeškrtnutím.
builder.Writeln("This text will be StrikeThrough");
```

## Závěr

A tady to máte! Úspěšně jste do textu přidali přeškrtnuté formátování pomocí Aspose.Words pro .NET. Tato výkonná knihovna otevírá svět možností pro zpracování a přizpůsobení dokumentů. Ať už vytváříte zprávy, dopisy nebo jakýkoli jiný typ dokumentu, zvládnutí těchto funkcí nepochybně zvýší vaši produktivitu a kvalitu vašich výstupů.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro zpracování dokumentů, která umožňuje vývojářům programově vytvářet, manipulovat a převádět dokumenty Wordu.

### Mohu použít Aspose.Words pro .NET v komerčním projektu?
Ano, Aspose.Words pro .NET můžete použít v komerčních projektech. Možnosti nákupu naleznete na [koupit stránku](https://purchase.aspose.com/buy).

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
Ano, můžete si stáhnout bezplatnou zkušební verzi [zde](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Words pro .NET?
Podporu můžete získat od komunity Aspose a odborníků na [fórum podpory](https://forum.aspose.com/c/words/8).

### Mohu použít jiné možnosti formátování textu pomocí Aspose.Words pro .NET?
Rozhodně! Aspose.Words pro .NET podporuje širokou škálu možností formátování textu, včetně tučného písma, kurzívy, podtržení a dalších.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
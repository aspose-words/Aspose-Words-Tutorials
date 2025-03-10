---
title: Přeškrtnutí
linktitle: Přeškrtnutí
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak použít přeškrtnuté formátování na text pomocí Aspose.Words for .NET s naším podrobným průvodcem. Vylepšete své dovednosti ve zpracování dokumentů.
weight: 10
url: /cs/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přeškrtnutí

## Zavedení

Vítejte v tomto podrobném průvodci, jak použít přeškrtnuté formátování na text pomocí Aspose.Words for .NET. Pokud chcete zlepšit své dovednosti při zpracování dokumentů a dodat svému textu jedinečný nádech, jste na správném místě. Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

-  Aspose.Words pro .NET: Stáhněte si ji[zde](https://releases.aspose.com/words/net/).
- .NET Framework: Ujistěte se, že máte v systému nainstalované rozhraní .NET Framework.
- Vývojové prostředí: IDE jako Visual Studio.
- Základní znalost C#: Je nutná znalost programování v C#.

## Importovat jmenné prostory

Chcete-li začít, budete muset importovat potřebné jmenné prostory. Ty jsou nezbytné pro přístup ke knihovně Aspose.Words a jejím funkcím.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Inicializujte DocumentBuilder

 The`DocumentBuilder` class je výkonný nástroj v Aspose.Words, který vám umožňuje snadno přidávat obsah do vašeho dokumentu.

```csharp
// Inicializujte DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Krok 2: Nastavte vlastnost přeškrtnutí

Nyní aplikujme vlastnost přeškrtnutí na náš text. To zahrnuje nastavení`StrikeThrough` vlastnictvím`Font` namítat proti`true`.

```csharp
// Proveďte přeškrtnutí textu.
builder.Font.StrikeThrough = true;
```

## Krok 3: Napište text s přeškrtnutím

 S nastavenou vlastností přeškrtnutí nyní můžeme přidat náš text. The`Writeln` metoda přidá text do dokumentu.

```csharp
// Napište text pomocí přeškrtnutého textu.
builder.Writeln("This text will be StrikeThrough");
```

## Závěr

A tady to máte! Úspěšně jste do textu přidali přeškrtnuté formátování pomocí Aspose.Words for .NET. Tato výkonná knihovna otevírá svět možností pro zpracování a přizpůsobení dokumentů. Ať už vytváříte zprávy, dopisy nebo jakýkoli jiný typ dokumentu, zvládnutí těchto funkcí nepochybně zvýší vaši produktivitu a kvalitu vašich výstupů.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro zpracování dokumentů, která umožňuje vývojářům vytvářet, manipulovat a převádět dokumenty aplikace Word programově.

### Mohu použít Aspose.Words pro .NET v komerčním projektu?
 Ano, Aspose.Words pro .NET můžete používat v komerčních projektech. Pro možnosti nákupu navštivte[koupit stránku](https://purchase.aspose.com/buy).

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Words for .NET?
Můžete získat podporu od komunity Aspose a odborníků na[fórum podpory](https://forum.aspose.com/c/words/8).

### Mohu použít jiné možnosti formátování textu pomocí Aspose.Words for .NET?
Absolutně! Aspose.Words for .NET podporuje širokou škálu možností formátování textu včetně tučného písma, kurzívy, podtržení a dalších.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

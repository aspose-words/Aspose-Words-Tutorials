---
title: Vložený kód
linktitle: Vložený kód
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se používat styly vloženého kódu v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tento výukový program pokrývá jeden a více backticks pro formátování kódu.
weight: 10
url: /cs/net/working-with-markdown/inline-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložený kód

## Zavedení

Pokud pracujete na programovém generování nebo manipulaci s dokumenty Wordu, možná budete muset naformátovat text tak, aby připomínal kód. Ať už jde o dokumentaci nebo úryvky kódu v sestavě, Aspose.Words for .NET poskytuje robustní způsob, jak zvládnout stylování textu. V tomto tutoriálu se zaměříme na to, jak aplikovat styly vloženého kódu na text pomocí Aspose.Words. Prozkoumáme, jak definovat a používat vlastní styly pro jednotlivá a vícenásobná zpětná zaškrtnutí, aby segmenty kódu ve vašich dokumentech jasně vynikly.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words for .NET Library: Ujistěte se, že máte Aspose.Words nainstalované ve vašem prostředí .NET. Můžete si jej stáhnout z[Stránka vydání Aspose.Words for .NET](https://releases.aspose.com/words/net/).

2. Základní znalosti programování .NET: Tato příručka předpokládá, že máte základní znalosti o programování v C# a .NET.

3. Vývojové prostředí: Měli byste mít nastavené vývojové prostředí .NET, jako je Visual Studio, kde můžete psát a spouštět kód C#.

## Importovat jmenné prostory

Chcete-li začít používat Aspose.Words ve svém projektu, budete muset importovat potřebné jmenné prostory. Postup je následující:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Rozdělme si proces do jasných kroků:

## Krok 1: Inicializujte Document a DocumentBuilder

 Nejprve musíte vytvořit nový dokument a`DocumentBuilder` instance. The`DocumentBuilder`class vám pomůže přidat obsah a formátovat jej v dokumentu aplikace Word.

```csharp
// Inicializujte DocumentBuilder pomocí nového dokumentu.
DocumentBuilder builder = new DocumentBuilder();
```

## Krok 2: Přidejte styl vloženého kódu s jedním zpětným zaškrtnutím

V tomto kroku definujeme styl pro vložený kód s jedním zpětným zaškrtnutím. Tento styl naformátuje text tak, aby vypadal jako vložený kód.

### Definujte styl

```csharp
// Definujte nový znakový styl pro vložený kód jedním zpětným zaškrtnutím.
Style inlineCode1BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode");
inlineCode1BackTicks.Font.Name = "Courier New"; // Typické písmo pro kód.
inlineCode1BackTicks.Font.Size = 10.5; // Velikost písma pro vložený kód.
inlineCode1BackTicks.Font.Color = System.Drawing.Color.Blue; // Barva textu kódu.
inlineCode1BackTicks.Font.Bold = true; // Udělejte text kódu tučným písmem.
```

### Použijte styl

Nyní můžete tento styl použít na text v dokumentu.

```csharp
// Použijte DocumentBuilder k vložení textu s vloženým stylem kódu.
builder.Font.Style = inlineCode1BackTicks;
builder.Writeln("Text with InlineCode style with 1 backtick");
```

## Krok 3: Přidejte styl vloženého kódu se třemi zpětnými znaménky

Dále definujeme styl pro vložený kód se třemi zpětnými zaškrtnutími, který se obvykle používá pro bloky víceřádkového kódu.

### Definujte styl

```csharp
// Definujte nový styl znaků pro vložený kód se třemi zpětnými zaškrtnutími.
Style inlineCode3BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode.3");
inlineCode3BackTicks.Font.Name = "Courier New"; // Konzistentní písmo pro kód.
inlineCode3BackTicks.Font.Size = 10.5; // Velikost písma pro blok kódu.
inlineCode3BackTicks.Font.Color = System.Drawing.Color.Green; //Různé barvy pro viditelnost.
inlineCode3BackTicks.Font.Bold = true; // Pro zdůraznění ponechte tučně.
```

### Použijte styl

Použijte tento styl na text, abyste jej naformátovali jako víceřádkový blok kódu.

```csharp
// Použijte styl pro blok kódu.
builder.Font.Style = inlineCode3BackTicks;
builder.Writeln("Text with InlineCode style with 3 backticks");
```

## Závěr

Formátování textu jako vloženého kódu v dokumentech aplikace Word pomocí Aspose.Words for .NET je jednoduché, jakmile znáte kroky. Definováním a použitím vlastních stylů s jedním nebo více zaškrtnutím můžete úryvky kódu jasně vyniknout. Tato metoda je zvláště užitečná pro technickou dokumentaci nebo jakýkoli dokument, kde je zásadní čitelnost kódu.

Nebojte se experimentovat s různými styly a možnostmi formátování, aby co nejlépe vyhovovaly vašim potřebám. Aspose.Words nabízí rozsáhlou flexibilitu a umožňuje vám do značné míry přizpůsobit vzhled vašeho dokumentu.

## FAQ

### Mohu použít různá písma pro styly vloženého kódu?
Ano, můžete použít jakékoli písmo, které vyhovuje vašim potřebám. Písma jako „Courier New“ se obvykle používají pro kód kvůli jejich povaze bez mezer.

### Jak změním barvu textu vloženého kódu?
 Barvu můžete změnit nastavením`Font.Color` vlastnost stylu komukoli`System.Drawing.Color`.

### Mohu použít více stylů na stejný text?
V Aspose.Words můžete použít pouze jeden styl najednou. Pokud potřebujete kombinovat styly, zvažte vytvoření nového stylu, který bude obsahovat veškeré požadované formátování.

### Jak mohu použít styly na existující text v dokumentu?
 Chcete-li použít styly na existující text, musíte nejprve vybrat text a poté použít požadovaný styl pomocí`Font.Style` vlastnictví.

### Mohu použít Aspose.Words pro jiné formáty dokumentů?
Aspose.Words je navržen speciálně pro dokumenty aplikace Word. Pro jiné formáty budete možná muset použít jiné knihovny nebo převést dokumenty do kompatibilního formátu.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

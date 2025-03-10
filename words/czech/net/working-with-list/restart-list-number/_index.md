---
title: Restartovat číslo seznamu
linktitle: Restartovat číslo seznamu
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak restartovat čísla seznamů v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tento podrobný průvodce o 2000 slovech pokrývá vše, co potřebujete vědět, od nastavení až po pokročilé přizpůsobení.
weight: 10
url: /cs/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Restartovat číslo seznamu

## Zavedení

Chcete zvládnout umění manipulace se seznamy v dokumentech aplikace Word pomocí Aspose.Words pro .NET? Tak to jste na správném místě! V tomto tutoriálu se ponoříme hluboko do čísel restartování seznamů, což je šikovná funkce, která posune vaše dovednosti v automatizaci dokumentů na další úroveň. Připoutejte se a můžeme začít!

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words for .NET: Musíte mít nainstalovanou aplikaci Aspose.Words for .NET. Pokud jste jej ještě nenainstalovali, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Ujistěte se, že máte vhodné vývojové prostředí, jako je Visual Studio.
3. Základní znalost C#: Základní znalost C# vám pomůže postupovat společně s výukovým programem.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Ty jsou klíčové pro přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Nyní si tento proces rozdělíme do snadno pochopitelných kroků. Probereme vše od vytvoření seznamu až po restart jeho číslování.

## Krok 1: Nastavte svůj dokument a tvůrce

Než budete moci začít manipulovat se seznamy, potřebujete dokument a DocumentBuilder. DocumentBuilder je váš oblíbený nástroj pro přidávání obsahu do vašeho dokumentu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vytvořte a přizpůsobte svůj první seznam

Dále vytvoříme seznam na základě šablony a přizpůsobíme jeho vzhled. V tomto příkladu používáme arabský formát čísel se závorkami.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Zde jsme nastavili barvu písma na červenou a text zarovnali doprava.

## Krok 3: Přidejte položky do svého prvního seznamu

 Když je váš seznam připraven, je čas přidat nějaké položky. The DocumentBuilder's`ListFormat.List` vlastnost pomáhá při aplikaci formátu seznamu na text.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Krok 4: Restartujte číslování seznamu

Chcete-li znovu použít seznam a restartovat jeho číslování, musíte vytvořit kopii původního seznamu. To vám umožní upravit nový seznam nezávisle.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

V tomto příkladu začíná nový seznam číslem 10.

## Krok 5: Přidejte položky do nového seznamu

Stejně jako předtím přidejte položky do nového seznamu. To ukazuje, že se seznam restartuje na zadaném čísle.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Krok 6: Uložte dokument

Nakonec uložte dokument do určeného adresáře.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Závěr

Restartování čísel seznamů v dokumentech aplikace Word pomocí Aspose.Words for .NET je přímočaré a neuvěřitelně užitečné. Ať už generujete sestavy, vytváříte strukturované dokumenty nebo jen potřebujete lepší kontrolu nad svými seznamy, tato technika vás pokryje.

## FAQ

### Mohu použít jiné šablony seznamů než NumberArabicParenthesis?

Absolutně! Aspose.Words nabízí různé šablony seznamů, jako jsou odrážky, písmena, římské číslice a další. Můžete si vybrat ten, který nejlépe vyhovuje vašim potřebám.

### Jak změním úroveň seznamu?

 Úroveň seznamu můžete změnit úpravou`ListLevels` vlastnictví. Například,`list1.ListLevels[1]` odkazuje na druhou úroveň seznamu.

### Mohu restartovat číslování na libovolném čísle?

 Ano, počáteční číslo můžete nastavit na libovolnou celočíselnou hodnotu pomocí`StartAt` vlastnost úrovně seznamu.

### Je možné mít různé formátování pro různé úrovně seznamu?

Opravdu! Každá úroveň seznamu může mít vlastní nastavení formátování, jako je písmo, zarovnání a styl číslování.

### Co když chci pokračovat v číslování z předchozího seznamu místo restartování?

Pokud chcete pokračovat v číslování, nemusíte vytvářet kopii seznamu. Jednoduše pokračujte v přidávání položek do původního seznamu.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

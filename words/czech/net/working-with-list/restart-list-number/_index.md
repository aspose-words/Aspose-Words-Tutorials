---
"description": "Naučte se, jak restartovat číslování seznamů v dokumentech Word pomocí Aspose.Words pro .NET. Tato podrobná příručka o délce 2000 slov pokrývá vše, co potřebujete vědět, od nastavení až po pokročilé přizpůsobení."
"linktitle": "Číslo seznamu pro restart"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Číslo seznamu pro restart"
"url": "/cs/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Číslo seznamu pro restart

## Zavedení

Chcete zvládnout umění manipulace se seznamy ve vašich dokumentech Word pomocí Aspose.Words pro .NET? Jste na správném místě! V tomto tutoriálu se ponoříme do hlubokého restartování čísel seznamů, což je šikovná funkce, která posune vaše dovednosti v automatizaci dokumentů na další úroveň. Připoutejte se a pojďme na to!

## Předpoklady

Než se pustíme do kódu, ujistěme se, že máte vše potřebné:

1. Aspose.Words pro .NET: Musíte mít nainstalovaný Aspose.Words pro .NET. Pokud jste ho ještě nenainstalovali, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Ujistěte se, že máte vhodné vývojové prostředí, jako je Visual Studio.
3. Základní znalost jazyka C#: Základní znalost jazyka C# vám pomůže s plněním úkolů v tutoriálu.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Ty jsou klíčové pro přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Nyní si celý proces rozdělme na snadno sledovatelné kroky. Probereme vše od vytvoření seznamu až po jeho restartování.

## Krok 1: Nastavení dokumentu a nástroje pro tvorbu

Než začnete manipulovat se seznamy, potřebujete dokument a nástroj DocumentBuilder. DocumentBuilder je váš hlavní nástroj pro přidávání obsahu do dokumentu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vytvořte a upravte svůj první seznam

Dále vytvoříme seznam založený na šabloně a upravíme jeho vzhled. V tomto příkladu používáme formát arabských čísel se závorkami.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Zde jsme nastavili barvu písma na červenou a zarovnali text doprava.

## Krok 3: Přidejte položky do svého prvního seznamu

Jakmile máte seznam připravený, je čas přidat další položky. Nástroj DocumentBuilder `ListFormat.List` Vlastnost pomáhá s použitím formátu seznamu na text.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Krok 4: Obnovte číslování seznamu

Chcete-li seznam znovu použít a restartovat jeho číslování, je třeba vytvořit kopii původního seznamu. To vám umožní nový seznam nezávisle upravovat.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

V tomto příkladu začíná nový seznam číslem 10.

## Krok 5: Přidání položek do nového seznamu

Stejně jako předtím přidejte položky do nového seznamu. Tím se demonstruje restartování seznamu od zadaného čísla.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Krok 6: Uložte dokument

Nakonec uložte dokument do vámi určeného adresáře.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Závěr

Restartování číslování seznamů v dokumentech Wordu pomocí Aspose.Words pro .NET je jednoduché a neuvěřitelně užitečné. Ať už generujete sestavy, vytváříte strukturované dokumenty nebo jen potřebujete lepší kontrolu nad svými seznamy, tato technika vám pomůže.

## Často kladené otázky

### Mohu použít jiné šablony seznamů než NumberArabicParenthesis?

Rozhodně! Aspose.Words nabízí různé šablony seznamů, jako jsou odrážky, písmena, římské číslice a další. Můžete si vybrat tu, která nejlépe vyhovuje vašim potřebám.

### Jak změním úroveň seznamu?

Úroveň seznamu můžete změnit úpravou `ListLevels` majetek. Například `list1.ListLevels[1]` by se vztahovalo na druhou úroveň seznamu.

### Mohu číslování znovu spustit od libovolného čísla?

Ano, počáteční číslo můžete nastavit na libovolnou celočíselnou hodnotu pomocí `StartAt` vlastnost úrovně seznamu.

### Je možné mít různé formátování pro různé úrovně seznamu?

Vskutku! Každá úroveň seznamu může mít svá vlastní nastavení formátování, jako je písmo, zarovnání a styl číslování.

### Co když chci pokračovat v číslování od předchozího seznamu, místo abych začal znovu?

Pokud chcete v číslování pokračovat, nemusíte vytvářet kopii seznamu. Jednoduše pokračujte v přidávání položek do původního seznamu.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
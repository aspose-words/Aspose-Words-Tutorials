---
"description": "Naučte se, jak v tomto komplexním průvodci zpracovávat revize tvarů v dokumentech Word pomocí Aspose.Words pro .NET. Zvládněte sledování změn, vkládání tvarů a další."
"linktitle": "Revize tvaru"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Revize tvaru"
"url": "/cs/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Revize tvaru

## Zavedení

Programová úprava dokumentů Wordu může být náročný úkol, zejména pokud jde o práci s tvary. Ať už vytváříte sestavy, navrhujete šablony nebo jednoduše automatizujete vytváření dokumentů, schopnost sledovat a spravovat revize tvarů je klíčová. Aspose.Words pro .NET nabízí výkonné API, které tento proces usnadňuje a zefektivňuje. V tomto tutoriálu se ponoříme do specifik revizí tvarů v dokumentech Wordu a zajistíme, že budete mít nástroje a znalosti pro snadnou správu dokumentů.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše potřebné:

- Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Měli byste mít nastavené vývojové prostředí, například Visual Studio.
- Základní znalost jazyka C#: Znalost programovacího jazyka C# a základních konceptů objektově orientovaného programování.
- Dokument Wordu: Dokument Wordu pro práci, nebo si jej můžete vytvořit během tutoriálu.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Ty nám poskytnou přístup ke třídám a metodám potřebným pro práci s dokumenty a tvary aplikace Word.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Nastavení adresáře dokumentů

Než začneme pracovat s tvary, musíme definovat cestu k adresáři s našimi dokumenty. Sem budeme ukládat upravené dokumenty.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvoření nového dokumentu

Vytvořme nový dokument Wordu, kde budeme vkládat a upravovat tvary.

```csharp
Document doc = new Document();
```

## Krok 3: Vložení vloženého tvaru

Začneme vložením vloženého tvaru do dokumentu bez sledování revizí. Vložený tvar je takový, který plynule kopíruje text.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Krok 4: Zahájení sledování revizí

Abychom mohli sledovat změny v našem dokumentu, musíme povolit sledování revizí. To je nezbytné pro identifikaci úprav provedených v obrazcích.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Krok 5: Vložení dalšího tvaru s revizemi

Nyní, když je sledování revizí povoleno, vložme další tvar. Tentokrát budou sledovány všechny změny.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Krok 6: Načtení a úprava tvarů

Můžeme načíst všechny tvary v dokumentu a podle potřeby je upravit. Zde načteme tvary a odstraníme první z nich.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Krok 7: Uložení dokumentu

Po provedení změn je třeba dokument uložit. Tím zajistíme, že budou uloženy všechny revize a úpravy.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Krok 8: Zpracování revizí přesunutí tvaru

Když je tvar přesunut, Aspose.Words to zaznamená jako revizi. To znamená, že budou existovat dvě instance tvaru: jedna v původním umístění a jedna v novém umístění.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Závěr

tady to máte! Úspěšně jste se naučili, jak zpracovávat revize tvarů v dokumentech Word pomocí Aspose.Words pro .NET. Ať už spravujete šablony dokumentů, automatizujete sestavy nebo jednoduše sledujete změny, tyto dovednosti jsou neocenitelné. Dodržováním tohoto podrobného návodu jste nejen zvládli základy, ale také získali vhled do pokročilejších technik práce s dokumenty.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, upravovat a převádět dokumenty Wordu pomocí C#.

### Mohu sledovat změny provedené v jiných prvcích v dokumentu Word?
Ano, Aspose.Words pro .NET podporuje sledování změn různých prvků, včetně textu, tabulek a dalších.

### Jak mohu získat bezplatnou zkušební verzi Aspose.Words pro .NET?
Můžete získat bezplatnou zkušební verzi Aspose.Words pro .NET [zde](https://releases.aspose.com/).

### Je možné programově přijmout nebo odmítnout revize?
Ano, Aspose.Words pro .NET poskytuje metody pro programově přijímání nebo odmítání revizí.

### Mohu používat Aspose.Words pro .NET s jinými jazyky .NET kromě C#?
Rozhodně! Aspose.Words pro .NET lze použít s jakýmkoli jazykem .NET, včetně VB.NET a F#.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
---
title: Revize tvaru
linktitle: Revize tvaru
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak zacházet s revizemi tvarů v dokumentech aplikace Word pomocí Aspose.Words for .NET, pomocí tohoto komplexního průvodce. Ovládněte sledování změn, vkládání tvarů a další.
weight: 10
url: /cs/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Revize tvaru

## Zavedení

Programové úpravy dokumentů Wordu mohou být skličující úkol, zejména pokud jde o manipulaci s tvary. Ať už vytváříte sestavy, navrhujete šablony nebo jednoduše automatizujete vytváření dokumentů, schopnost sledovat a spravovat revize tvarů je zásadní. Aspose.Words for .NET nabízí výkonné API, aby byl tento proces bezproblémový a efektivní. V tomto tutoriálu se ponoříme do specifik revizí tvarů v dokumentech aplikace Word a zajistíme, že budete mít nástroje a znalosti pro snadnou správu dokumentů.

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Měli byste mít nastavené vývojové prostředí, jako je Visual Studio.
- Základní porozumění C#: Seznámení s programovacím jazykem C# a základními pojmy objektově orientovaného programování.
- Dokument aplikace Word: Dokument aplikace Word, se kterým můžete pracovat, nebo jej můžete vytvořit během kurzu.

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

Než začneme pracovat s tvary, musíme definovat cestu k našemu adresáři dokumentů. Zde uložíme naše upravené dokumenty.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vytvoření nového dokumentu

Vytvořme nový dokument aplikace Word, do kterého budeme vkládat a upravovat tvary.

```csharp
Document doc = new Document();
```

## Krok 3: Vložení inline tvaru

Začneme vložením vloženého tvaru do našeho dokumentu bez sledování revizí. Vložený tvar je takový, který splývá s textem.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Krok 4: Zahájení sledování revizí

Abychom mohli sledovat změny v našem dokumentu, musíme povolit sledování revizí. To je nezbytné pro identifikaci provedených úprav tvarů.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Krok 5: Vložení jiného tvaru s revizemi

Nyní, když je povoleno sledování revizí, vložíme další tvar. Tentokrát budou všechny změny sledovány.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Krok 6: Načtení a úprava tvarů

Můžeme načíst všechny tvary v dokumentu a upravit je podle potřeby. Zde získáme tvary a odstraníme první.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Krok 7: Uložení dokumentu

Po provedení změn musíme dokument uložit. Tím je zajištěno uložení všech revizí a úprav.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Krok 8: Práce s revizemi přesunu tvaru

Když se tvar přesune, Aspose.Words to sleduje jako revizi. To znamená, že budou existovat dvě instance tvaru: jedna v původním umístění a druhá v novém umístění.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Závěr

A tady to máte! Úspěšně jste se naučili, jak zacházet s revizemi tvarů v dokumentech aplikace Word pomocí Aspose.Words for .NET. Ať už spravujete šablony dokumentů, automatizujete sestavy nebo jednoduše sledujete změny, tyto dovednosti jsou neocenitelné. Podle tohoto podrobného průvodce jste nejen zvládli základy, ale také získali přehled o pokročilejších technikách manipulace s dokumenty.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna, která umožňuje vývojářům vytvářet, upravovat a převádět dokumenty Wordu programově pomocí C#.

### Mohu sledovat změny provedené v jiných prvcích v dokumentu aplikace Word?
Ano, Aspose.Words for .NET podporuje sledování změn různých prvků, včetně textu, tabulek a dalších.

### Jak mohu získat bezplatnou zkušební verzi Aspose.Words pro .NET?
 Můžete získat bezplatnou zkušební verzi Aspose.Words pro .NET[zde](https://releases.aspose.com/).

### Je možné přijímat nebo odmítat revize programově?
Ano, Aspose.Words for .NET poskytuje metody pro programové přijetí nebo odmítnutí revizí.

### Mohu používat Aspose.Words pro .NET s jinými jazyky .NET kromě C#?
Absolutně! Aspose.Words for .NET lze použít s jakýmkoli jazykem .NET, včetně VB.NET a F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

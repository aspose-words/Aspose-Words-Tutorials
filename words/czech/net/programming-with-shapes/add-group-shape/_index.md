---
title: Přidat tvar skupiny
linktitle: Přidat tvar skupiny
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak přidávat tvary skupin do dokumentů aplikace Word pomocí Aspose.Words for .NET pomocí tohoto komplexního, podrobného kurzu.
weight: 10
url: /cs/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidat tvar skupiny

## Zavedení

Vytváření složitých dokumentů s bohatými vizuálními prvky může být někdy skličující úkol, zejména při práci se skupinovými tvary. Ale nebojte se! Aspose.Words for .NET tento proces zjednodušuje, takže je snadný jako facka. V tomto kurzu vás provedeme kroky pro přidávání skupinových tvarů do dokumentů aplikace Word. Jste připraveni se ponořit? Začněme!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words for .NET: Můžete si jej stáhnout z[Aspose stránku vydání](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
3. Základní znalost C#: Výhodou je znalost programování v C#.

## Importovat jmenné prostory

Abychom mohli začít, musíme do našeho projektu importovat potřebné jmenné prostory. Tyto jmenné prostory poskytují přístup ke třídám a metodám potřebným pro manipulaci s dokumenty aplikace Word pomocí Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Inicializujte dokument

Za prvé, pojďme inicializovat nový dokument aplikace Word. Berte to jako vytvoření prázdného plátna, kam budeme přidávat tvary skupiny.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Zde,`EnsureMinimum()` přidá minimální sadu uzlů požadovaných pro dokument.

## Krok 2: Vytvořte objekt GroupShape

 Dále musíme vytvořit a`GroupShape`objekt. Tento objekt bude sloužit jako kontejner pro další tvary, což nám umožní seskupit je dohromady.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Krok 3: Přidejte tvary do GroupShape

 Nyní k našim přidejte jednotlivé tvary`GroupShape` kontejner. Začneme tvarem ohraničení zvýrazněním a poté přidáme tvar akčního tlačítka.

### Přidání tvaru okraje s zvýrazněním

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Tento fragment kódu vytvoří tvar ohraničení zvýraznění o šířce a výšce 100 jednotek a přidá jej do`GroupShape`.

### Přidání tvaru akčního tlačítka

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 Zde vytvoříme tvar tlačítka akce, umístíme jej a přidáme do našeho`GroupShape`.

## Krok 4: Definujte rozměry GroupShape

 Aby naše tvary dobře zapadly do skupiny, musíme nastavit rozměry`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 To definuje šířku a výšku`GroupShape` jako 200 jednotek a podle toho nastaví velikost souřadnic.

## Krok 5: Vložte GroupShape do dokumentu

 Nyní vložíme naše`GroupShape` do dokumentu pomocí`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` poskytuje snadný způsob přidávání uzlů, včetně tvarů, do dokumentu.

## Krok 6: Uložte dokument

Nakonec dokument uložte do určeného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

tady to máte! Váš dokument se skupinovými tvary je připraven.

## Závěr

Přidání skupinových tvarů do dokumentů aplikace Word nemusí být složitý proces. S Aspose.Words for .NET můžete snadno vytvářet a manipulovat s tvary, díky čemuž budou vaše dokumenty vizuálně přitažlivější a funkčnější. Postupujte podle kroků uvedených v tomto tutoriálu a za chvíli budete profesionálem!

## FAQ

### Mohu do GroupShape přidat více než dva tvary?
 Ano, do a můžete přidat tolik tvarů, kolik potřebujete`GroupShape` . Stačí použít`AppendChild` metoda pro každý tvar.

### Je možné tvarovat tvary v rámci GroupShape?
 Absolutně! Každý tvar lze individuálně stylovat pomocí vlastností dostupných v`Shape` třída.

### Jak umístím GroupShape v dokumentu?
 Můžete umístit`GroupShape` nastavením jeho`Left` a`Top` vlastnosti.

### Mohu přidat text do obrazců v rámci GroupShape?
 Ano, k tvarům můžete přidat text pomocí`AppendChild` způsob přidání a`Paragraph` obsahující`Run` uzly s textem.

### Je možné seskupovat tvary dynamicky na základě vstupu uživatele?
Ano, můžete dynamicky vytvářet a seskupovat tvary na základě uživatelského vstupu tím, že odpovídajícím způsobem upravíte vlastnosti a metody.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

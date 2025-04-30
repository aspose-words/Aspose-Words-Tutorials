---
"description": "Naučte se, jak přidávat skupinové tvary do dokumentů Wordu pomocí Aspose.Words pro .NET v tomto komplexním návodu krok za krokem."
"linktitle": "Přidat tvar skupiny"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidat tvar skupiny"
"url": "/cs/net/programming-with-shapes/add-group-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidat tvar skupiny

## Zavedení

Vytváření složitých dokumentů s bohatými vizuálními prvky může být někdy náročný úkol, zejména při práci se skupinovými tvary. Ale nebojte se! Aspose.Words pro .NET tento proces zjednodušuje a dělá ho hračkou. V tomto tutoriálu vás provedeme kroky pro přidání skupinových tvarů do vašich dokumentů Wordu. Jste připraveni se do toho pustit? Pojďme na to!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Můžete si jej stáhnout z [Stránka s vydáním Aspose](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
3. Základní znalost C#: Znalost programování v C# je výhodou.

## Importovat jmenné prostory

Pro začátek musíme do našeho projektu importovat potřebné jmenné prostory. Tyto jmenné prostory poskytují přístup ke třídám a metodám potřebným pro manipulaci s dokumenty Wordu pomocí Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Inicializace dokumentu

Nejdříve si inicializujeme nový dokument Wordu. Představte si to jako vytvoření prázdného plátna, kam budeme přidávat tvary našich skupin.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

Zde, `EnsureMinimum()` přidává minimální sadu uzlů potřebných pro dokument.

## Krok 2: Vytvoření objektu GroupShape

Dále musíme vytvořit `GroupShape` objekt. Tento objekt bude sloužit jako kontejner pro další tvary, což nám umožní je seskupit.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Krok 3: Přidání tvarů do GroupShape

Nyní si k našemu přidáme jednotlivé tvary `GroupShape` kontejner. Začneme s tvarem zvýrazňujícího ohraničení a poté přidáme tvar akčního tlačítka.

### Přidání tvaru zvýrazňujícího okraje

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

Tento úryvek kódu vytvoří tvar zvýrazňujícího ohraničení o šířce a výšce 100 jednotek a přidá ho do `GroupShape`.

### Přidání tvaru tlačítka akce

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

Zde vytvoříme tvar akčního tlačítka, umístíme ho a přidáme ho do našeho `GroupShape`.

## Krok 4: Definování rozměrů GroupShape

Abychom zajistili, že naše tvary dobře zapadají do skupiny, musíme nastavit rozměry `GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

Toto definuje šířku a výšku `GroupShape` jako 200 jednotek a odpovídajícím způsobem nastaví velikost souřadnic.

## Krok 5: Vložení GroupShape do dokumentu

Nyní vložme naše `GroupShape` do dokumentu pomocí `DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` poskytuje snadný způsob, jak do dokumentu přidat uzly, včetně tvarů.

## Krok 6: Uložte dokument

Nakonec uložte dokument do vámi určeného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

A máte to! Váš dokument se skupinovými tvary je připraven.

## Závěr

Přidávání skupinových tvarů do dokumentů Wordu nemusí být složitý proces. S Aspose.Words pro .NET můžete snadno vytvářet a manipulovat s tvary, díky čemuž budou vaše dokumenty vizuálně atraktivnější a funkčnější. Postupujte podle kroků uvedených v tomto tutoriálu a stanete se profesionálem během chvilky!

## Často kladené otázky

### Mohu do GroupShape přidat více než dva tvary?
Ano, můžete přidat tolik tvarů, kolik potřebujete `GroupShape`Stačí použít `AppendChild` metoda pro každý tvar.

### Je možné upravovat tvary v rámci GroupShape?
Rozhodně! Každý tvar lze stylovat individuálně pomocí vlastností dostupných v `Shape` třída.

### Jak umístím GroupShape v dokumentu?
Můžete umístit `GroupShape` nastavením jeho `Left` a `Top` vlastnosti.

### Mohu přidat text k tvarům v rámci GroupShape?
Ano, text můžete do tvarů přidat pomocí `AppendChild` metoda pro přidání `Paragraph` obsahující `Run` uzly s textem.

### Je možné seskupovat tvary dynamicky na základě vstupu uživatele?
Ano, tvary můžete dynamicky vytvářet a seskupovat na základě uživatelského vstupu úpravou vlastností a metod odpovídajícím způsobem.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
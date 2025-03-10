---
title: Vložit tvar
linktitle: Vložit tvar
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vkládat a manipulovat s tvary v dokumentech aplikace Word pomocí Aspose.Words for .NET pomocí našeho podrobného průvodce.
weight: 10
url: /cs/net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit tvar

## Zavedení

Pokud jde o vytváření vizuálně přitažlivých a dobře strukturovaných dokumentů aplikace Word, tvary mohou hrát zásadní roli. Ať už přidáváte šipky, rámečky nebo dokonce složité vlastní tvary, možnost programově manipulovat s těmito prvky nabízí nesrovnatelnou flexibilitu. V tomto tutoriálu prozkoumáme, jak vkládat a manipulovat s tvary v dokumentech aplikace Word pomocí Aspose.Words for .NET.

## Předpoklady

Než se ponoříte do výukového programu, ujistěte se, že máte následující předpoklady:

1.  Aspose.Words for .NET: Stáhněte a nainstalujte nejnovější verzi z[Aspose stránku vydání](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vhodné vývojové prostředí .NET, jako je Visual Studio.
3. Základní znalost C#: Znalost programovacího jazyka C# a základních pojmů.

## Importovat jmenné prostory

Chcete-li začít, budete muset do svého projektu C# importovat potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Nastavte svůj projekt

Než budete moci začít vkládat tvary, musíte nastavit svůj projekt a přidat knihovnu Aspose.Words for .NET.

1. Vytvoření nového projektu: Otevřete Visual Studio a vytvořte nový projekt C# Console Application.
2. Přidat Aspose.Words for .NET: Nainstalujte knihovnu Aspose.Words for .NET prostřednictvím Správce balíčků NuGet.

```bash
Install-Package Aspose.Words
```

## Krok 2: Inicializujte dokument

Nejprve budete muset inicializovat nový dokument a tvůrce dokumentů, který vám pomůže při vytváření dokumentu.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inicializujte nový dokument
Document doc = new Document();

// Inicializujte DocumentBuilder, který vám pomůže vytvořit dokument
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložte tvar

Nyní do dokumentu vložíme tvar. Začneme přidáním jednoduchého textového pole.

```csharp
// Vložte do dokumentu tvar textového pole
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Otočte tvar
shape.Rotation = 30.0;
```

tomto příkladu vložíme na pozici (100, 100) textové pole o šířce a výšce 50 jednotek. Tvar také otočíme o 30 stupňů.

## Krok 4: Přidejte další tvar

Pojďme do dokumentu přidat další tvar, tentokrát bez určení pozice.

```csharp
// Přidejte další tvar textového pole
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Otočte tvar
secondShape.Rotation = 30.0;
```

Tento fragment kódu vloží další textové pole se stejnými rozměry a otočením jako první, ale bez určení jeho polohy.

## Krok 5: Uložte dokument

 Po přidání tvarů je posledním krokem uložení dokumentu. Použijeme`OoxmlSaveOptions` k určení formátu uložení.

```csharp
// Definujte možnosti uložení s dodržováním předpisů
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Uložte dokument
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Závěr

A tady to máte! Úspěšně jste vložili tvary a manipulovali s nimi v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tento výukový program pokryl základy, ale Aspose.Words nabízí mnoho pokročilejších funkcí pro práci s tvary, jako jsou vlastní styly, spojnice a tvary skupin.

 Pro podrobnější informace navštivte[Aspose.Words pro dokumentaci .NET](https://reference.aspose.com/words/net/).

## FAQ

### Jak vložím různé typy tvarů?
Můžete změnit`ShapeType` v`InsertShape` metoda pro vkládání různých typů tvarů, jako jsou kruhy, obdélníky a šipky.

### Mohu přidat text do tvarů?
 Ano, můžete použít`builder.Write` metoda pro přidání textu do tvarů po jejich vložení.

### Je možné tvary stylizovat?
 Ano, tvary můžete stylovat nastavením vlastností jako`FillColor`, `StrokeColor` a`StrokeWeight`.

### Jak umístím tvary vzhledem k ostatním prvkům?
 Použijte`RelativeHorizontalPosition` a`RelativeVerticalPosition` vlastnosti pro umístění tvarů vzhledem k ostatním prvkům v dokumentu.

### Mohu seskupit více tvarů dohromady?
 Ano, Aspose.Words for .NET umožňuje seskupovat tvary pomocí`GroupShape` třída.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

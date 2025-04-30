---
"description": "Naučte se, jak vkládat a manipulovat s tvary v dokumentech Wordu pomocí Aspose.Words pro .NET s naším podrobným návodem."
"linktitle": "Vložit tvar"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložit tvar"
"url": "/cs/net/programming-with-shapes/insert-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložit tvar

## Zavedení

Pokud jde o vytváření vizuálně přitažlivých a dobře strukturovaných dokumentů Wordu, tvary mohou hrát zásadní roli. Ať už přidáváte šipky, rámečky nebo dokonce složité vlastní tvary, možnost programově manipulovat s těmito prvky nabízí bezkonkurenční flexibilitu. V tomto tutoriálu se podíváme na to, jak vkládat a manipulovat s tvary v dokumentech Wordu pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíte do tutoriálu, ujistěte se, že máte následující předpoklady:

1. Aspose.Words pro .NET: Stáhněte a nainstalujte nejnovější verzi z [Stránka s vydáním Aspose](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vhodné vývojové prostředí pro .NET, například Visual Studio.
3. Základní znalost C#: Znalost programovacího jazyka C# a základních konceptů.

## Importovat jmenné prostory

Chcete-li začít, budete muset do svého projektu C# importovat potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Krok 1: Nastavení projektu

Než začnete vkládat tvary, musíte si nastavit projekt a přidat knihovnu Aspose.Words pro .NET.

1. Vytvoření nového projektu: Otevřete Visual Studio a vytvořte nový projekt konzolové aplikace C#.
2. Přidání Aspose.Words pro .NET: Nainstalujte knihovnu Aspose.Words pro .NET pomocí Správce balíčků NuGet.

```bash
Install-Package Aspose.Words
```

## Krok 2: Inicializace dokumentu

Nejprve budete muset inicializovat nový dokument a nástroj pro tvorbu dokumentů, který vám pomůže s jeho sestavením.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inicializace nového dokumentu
Document doc = new Document();

// Inicializujte DocumentBuilder, který pomůže sestavit dokument.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložení tvaru

Nyní vložíme do dokumentu tvar. Začneme přidáním jednoduchého textového pole.

```csharp
// Vložení tvaru textového pole do dokumentu
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Otočení tvaru
shape.Rotation = 30.0;
```

V tomto příkladu vložíme textové pole na pozici (100, 100) o šířce a výšce 50 jednotek. Také otočíme tvar o 30 stupňů.

## Krok 4: Přidání dalšího tvaru

Přidejme do dokumentu další tvar, tentokrát bez určení jeho polohy.

```csharp
// Přidat další tvar textového pole
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Otočení tvaru
secondShape.Rotation = 30.0;
```

Tento úryvek kódu vloží další textové pole se stejnými rozměry a otočením jako první, ale bez určení jeho pozice.

## Krok 5: Uložte dokument

Po přidání tvarů je posledním krokem uložení dokumentu. Použijeme `OoxmlSaveOptions` pro určení formátu uložení.

```csharp
// Definování možností ukládání s ohledem na dodržování předpisů
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Uložit dokument
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Závěr

tady to máte! Úspěšně jste vložili a upravili tvary v dokumentu Word pomocí Aspose.Words pro .NET. Tento tutoriál se zabýval základy, ale Aspose.Words nabízí mnoho pokročilejších funkcí pro práci s tvary, jako jsou vlastní styly, spojnice a seskupené tvary.

Pro podrobnější informace navštivte [Dokumentace k Aspose.Words pro .NET](https://reference.aspose.com/words/net/).

## Často kladené otázky

### Jak vkládám různé typy tvarů?
Můžete změnit `ShapeType` v `InsertShape` metoda pro vkládání různých typů tvarů, jako jsou kruhy, obdélníky a šipky.

### Mohu do tvarů přidat text?
Ano, můžete použít `builder.Write` metoda pro přidání textu dovnitř tvarů po jejich vložení.

### Je možné tvary stylovat?
Ano, tvary můžete upravovat nastavením vlastností, jako je `FillColor`, `StrokeColor`a `StrokeWeight`.

### Jak umístím tvary vzhledem k ostatním prvkům?
Použijte `RelativeHorizontalPosition` a `RelativeVerticalPosition` vlastnosti pro umístění tvarů vzhledem k ostatním prvkům v dokumentu.

### Mohu seskupit více tvarů dohromady?
Ano, Aspose.Words pro .NET umožňuje seskupovat tvary pomocí `GroupShape` třída.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
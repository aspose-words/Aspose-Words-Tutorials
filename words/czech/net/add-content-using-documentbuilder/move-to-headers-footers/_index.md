---
title: Přesunout do záhlaví zápatí v dokumentu aplikace Word
linktitle: Přesunout do záhlaví zápatí v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak přejít na záhlaví a zápatí v dokumentu aplikace Word pomocí Aspose.Words for .NET s naším podrobným průvodcem. Vylepšete své dovednosti při vytváření dokumentů.
weight: 10
url: /cs/net/add-content-using-documentbuilder/move-to-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přesunout do záhlaví zápatí v dokumentu aplikace Word

## Zavedení

Pokud jde o vytváření a správu dokumentů aplikace Word programově, Aspose.Words for .NET je výkonný nástroj, který vám může ušetřit spoustu času a úsilí. V tomto článku prozkoumáme, jak se přesunout do záhlaví a zápatí v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato funkce je nezbytná, když potřebujete přidat konkrétní obsah do části záhlaví nebo zápatí dokumentu. Ať už vytváříte sestavu, fakturu nebo jakýkoli dokument, který vyžaduje profesionální přístup, pochopení toho, jak zacházet se záhlavími a zápatím, je zásadní.

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte vše nastaveno:

1. **Aspose.Words for .NET** : Ujistěte se, že máte knihovnu Aspose.Words for .NET. Můžete si jej stáhnout z[Aspose stránku vydání](https://releases.aspose.com/words/net/).
2. **Development Environment**Potřebujete vývojové prostředí, jako je Visual Studio.
3. **Basic Knowledge of C#**: Pochopení základů programování v C# vám pomůže pokračovat.

## Importovat jmenné prostory

Chcete-li začít, budete muset importovat potřebné jmenné prostory. Tento krok je zásadní pro přístup ke třídám a metodám poskytovaným Aspose.Words pro .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System;
```

Pojďme si celý proces rozdělit do jednoduchých kroků. Každý krok bude jasně vysvětlen, aby vám pomohl pochopit, co kód dělá a proč.

## Krok 1: Inicializujte dokument

Prvním krokem je inicializace nového dokumentu a objektu DocumentBuilder. Třída DocumentBuilder vám umožňuje vytvářet a manipulovat s dokumentem.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 V tomto kroku vytvoříte novou instanci souboru`Document` třída a`DocumentBuilder` třída. The`dataDir` proměnná se používá k určení adresáře, kam chcete dokument uložit.

## Krok 2: Nakonfigurujte nastavení stránky

Dále musíme určit, že záhlaví a zápatí by se měly lišit pro první, sudé a liché stránky.

```csharp
//Určete, že chceme záhlaví a zápatí odlišovat pro první, sudé a liché stránky.
builder.PageSetup.DifferentFirstPageHeaderFooter = true;
builder.PageSetup.OddAndEvenPagesHeaderFooter = true;
```

Tato nastavení zajišťují, že můžete mít jedinečná záhlaví a zápatí pro různé typy stránek.

## Krok 3: Přejděte do záhlaví/zápatí a přidejte obsah

Nyní se přesuneme do sekce záhlaví a zápatí a přidáme nějaký obsah.

```csharp
// Vytvořte záhlaví.
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.Write("Header for the first page");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderEven);
builder.Write("Header for even pages");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);
builder.Write("Header for all other pages");
```

 V tomto kroku použijeme`MoveToHeaderFooter` metodu pro přechod do požadované sekce záhlaví nebo zápatí. The`Write` Metoda se pak použije k přidání textu do těchto sekcí.

## Krok 4: Přidejte obsah do těla dokumentu

Chcete-li předvést záhlaví a zápatí, přidejte do těla dokumentu nějaký obsah a vytvořte několik stránek.

```csharp
// Vytvořte v dokumentu dvě stránky.
builder.MoveToSection(0);
builder.Writeln("Page1");
builder.InsertBreak(BreakType.PageBreak);
builder.Writeln("Page2");
```

Zde do dokumentu přidáme text a vložíme konec stránky, abychom vytvořili druhou stránku.

## Krok 5: Uložte dokument

Nakonec dokument uložte do určeného adresáře.

```csharp
doc.Save(dataDir + "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx");
```

Tento řádek kódu uloží dokument s názvem "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx" do zadaného adresáře.

## Závěr

 Pomocí těchto kroků můžete snadno manipulovat se záhlavími a zápatími v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tento návod pokryl základy, ale Aspose.Words nabízí širokou škálu funkcí pro složitější manipulaci s dokumenty. Neváhejte prozkoumat[dokumentace](https://reference.aspose.com/words/net/) pro pokročilejší funkce.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je knihovna, která umožňuje vývojářům vytvářet, upravovat a převádět dokumenty Wordu programově pomocí C#.

### Mohu přidat obrázky do záhlaví a zápatí?
 Ano, můžete přidat obrázky do záhlaví a zápatí pomocí`DocumentBuilder.InsertImage` metoda.

### Je možné mít různá záhlaví a zápatí pro každou sekci?
 Absolutně! Můžete mít jedinečná záhlaví a zápatí pro každou sekci nastavením různých`HeaderFooterType` pro každou sekci.

### Jak vytvořím složitější rozvržení v záhlaví a zápatí?
vytváření složitých rozvržení můžete použít tabulky, obrázky a různé možnosti formátování, které poskytuje Aspose.Words.

### Kde najdu další příklady a návody?
 Podívejte se na[dokumentace](https://reference.aspose.com/words/net/) a[fórum podpory](https://forum.aspose.com/c/words/8) pro další příklady a podporu komunity.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

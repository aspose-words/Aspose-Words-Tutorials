---
title: Optimalizujte velikost PDF pomocí přeskočení vložených písem Arial & Times Roman
linktitle: Optimalizujte velikost PDF pomocí přeskočení vložených písem Arial & Times Roman
second_title: Aspose.Words API pro zpracování dokumentů
description: Optimalizujte velikost PDF přeskočením vložených písem Arial a Times Roman pomocí Aspose.Words pro .NET. Postupujte podle tohoto podrobného průvodce a zefektivněte své soubory PDF.
weight: 10
url: /cs/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Optimalizujte velikost PDF pomocí přeskočení vložených písem Arial & Times Roman

## Zavedení

Ocitli jste se někdy v situaci, kdy je váš soubor PDF příliš velký? Je to jako když se sbalíte na dovolenou a zjistíte, že váš kufr praská ve švech. Víte, že potřebujete shodit nějaké to kilo, ale co necháte jít? Při práci se soubory PDF, zejména se soubory převedenými z dokumentů aplikace Word, mohou vložená písma zvětšit velikost souboru. Naštěstí Aspose.Words for .NET poskytuje elegantní řešení, jak udržet vaše PDF štíhlé a průměrné. V tomto tutoriálu se ponoříme do toho, jak optimalizovat velikost PDF přeskočením vložených písem Arial a Times Roman. Začněme!

## Předpoklady

Než se vrhneme na to, co je v pořádku, je několik věcí, které budete potřebovat:
-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou tuto výkonnou knihovnu. Pokud ne, můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
- Základní porozumění C#: To vám pomůže sledovat úryvky kódu.
- Dokument aplikace Word: K demonstraci procesu použijeme vzorový dokument. 

## Importovat jmenné prostory

Nejprve se ujistěte, že máte importované potřebné jmenné prostory. Tím se připraví půda pro přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dobře, pojďme si proces rozebrat krok za krokem.

## Krok 1: Nastavte své prostředí

Chcete-li začít, musíte nastavit vývojové prostředí. Otevřete své oblíbené IDE C# (jako Visual Studio) a vytvořte nový projekt.

## Krok 2: Načtěte dokument aplikace Word

Dalším krokem je načtení dokumentu aplikace Word, který chcete převést do formátu PDF. Ujistěte se, že je dokument ve správném adresáři.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 V tomto úryvku nahraďte`"YOUR DOCUMENT DIRECTORY"` s cestou k adresáři s dokumenty.

## Krok 3: Nakonfigurujte možnosti uložení PDF

Nyní musíme nakonfigurovat možnosti uložení PDF, abychom řídili způsob vkládání písem. Ve výchozím nastavení jsou všechna písma vložena, což může zvětšit velikost souboru. Toto nastavení změníme.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## Krok 4: Uložte dokument jako PDF

Nakonec uložte dokument jako PDF se zadanými možnostmi uložení. Tady se děje kouzlo.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

Tento příkaz uloží váš dokument jako PDF s názvem "OptimizedPDF.pdf" do zadaného adresáře.

## Závěr

tady to máte! Právě jste se naučili, jak optimalizovat velikost souboru PDF přeskočením vkládání písem Arial a Times Roman pomocí Aspose.Words pro .NET. Tato jednoduchá úprava může výrazně zmenšit velikost souborů, což usnadňuje jejich sdílení a ukládání. Je to jako jít do posilovny pro soubory PDF, shodit zbytečnou váhu a přitom zachovat všechny náležitosti nedotčené.

## FAQ

### Proč bych měl přeskočit vkládání písem Arial a Times Roman?
Vynechání těchto běžných písem může snížit velikost souboru PDF, protože většina systémů již tato písma má nainstalovaná.

### Ovlivní to vzhled mého PDF?
Ne, nebude. Vzhledem k tomu, že Arial a Times Roman jsou standardní písma, zůstává vzhled konzistentní v různých systémech.

### Mohu přeskočit i vkládání jiných písem?
Ano, můžete nakonfigurovat možnosti uložení tak, aby se v případě potřeby vynechalo vkládání jiných písem.

### Je Aspose.Words for .NET zdarma?
 Aspose.Words for .NET nabízí bezplatnou zkušební verzi, kterou si můžete stáhnout[zde](https://releases.aspose.com/) , ale pro plný přístup je potřeba zakoupit licenci[zde](https://purchase.aspose.com/buy).

### Kde najdu další návody na Aspose.Words pro .NET?
Můžete najít komplexní dokumentaci a návody[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

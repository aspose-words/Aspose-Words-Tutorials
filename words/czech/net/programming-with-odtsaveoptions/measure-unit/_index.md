---
title: Jednotka měření
linktitle: Jednotka měření
second_title: Aspose.Words API pro zpracování dokumentů
description: Zjistěte, jak nakonfigurovat funkci měrných jednotek v Aspose.Words pro .NET pro zachování formátování dokumentu během převodu ODT.
weight: 10
url: /cs/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jednotka měření

## Zavedení

Stalo se vám někdy, že jste museli převádět dokumenty aplikace Word do různých formátů, ale potřebovali jste pro své rozvržení konkrétní měrnou jednotku? Ať už máte co do činění s palci, centimetry nebo body, je zásadní zajistit, aby si dokument během procesu převodu zachoval integritu. V tomto tutoriálu si projdeme, jak nakonfigurovat funkci jednotky měření v Aspose.Words pro .NET. Tato výkonná funkce zajišťuje, že při převodu do formátu ODT (Open Document Text) bude formátování vašeho dokumentu zachováno přesně tak, jak jej potřebujete.

## Předpoklady

Než se ponoříte do kódu, je několik věcí, které budete potřebovat:

1. Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou nejnovější verzi Aspose.Words pro .NET. Pokud ji ještě nemáte, můžete si ji stáhnout z[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: IDE jako Visual Studio pro psaní a spouštění vašeho kódu C#.
3. Základní znalost C#: Pochopení základů C# vám pomůže postupovat společně s výukovým programem.
4. Dokument aplikace Word: Připravte si vzorový dokument aplikace Word, který můžete použít pro převod.

## Importovat jmenné prostory

Než začneme kódovat, ujistěte se, že máme importované potřebné jmenné prostory. Přidejte je pomocí direktiv v horní části souboru kódu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavte adresář dokumentů

Nejprve musíte definovat cestu k adresáři dokumentů. Zde se nachází váš dokument aplikace Word a kam se uloží převedený soubor.

```csharp
// Cesta k adresáři vašich dokumentů
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Nahradit`"YOUR DOCUMENTS DIRECTORY"` se skutečnou cestou k vašemu adresáři. Tím zajistíte, že váš kód ví, kde má najít váš dokument aplikace Word.

## Krok 2: Načtěte dokument aplikace Word

 Dále musíte načíst dokument aplikace Word, který chcete převést. To se provádí pomocí`Document` třídy z Aspose.Words.

```csharp
// Načtěte dokument aplikace Word
Document doc = new Document(dataDir + "Document.docx");
```

Ujistěte se, že váš dokument aplikace Word s názvem "Document.docx" je přítomen v zadaném adresáři.

## Krok 3: Nakonfigurujte jednotku měření

 Nyní nakonfigurujme jednotku měření pro převod ODT. Tady se děje kouzlo. Nastavíme`OdtSaveOptions` používat palce jako měrnou jednotku.

```csharp
// Konfigurace možností zálohování pomocí funkce "Měrná jednotka".
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 V tomto příkladu nastavujeme jednotku měření na palce. Můžete si vybrat i jiné jednotky jako např`OdtSaveMeasureUnit.Centimeters` nebo`OdtSaveMeasureUnit.Points` v závislosti na vašich požadavcích.

## Krok 4: Převeďte dokument na ODT

 Nakonec převedeme dokument aplikace Word do formátu ODT pomocí nakonfigurovaného`OdtSaveOptions`.

```csharp
// Převeďte dokument na ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Tento řádek kódu uloží převedený dokument do určeného adresáře s aplikovanou novou měrnou jednotkou.

## Závěr

tady to máte! Podle těchto kroků můžete snadno nakonfigurovat funkci měrných jednotek v Aspose.Words for .NET, abyste zajistili, že rozložení vašeho dokumentu bude během převodu zachováno. Ať už pracujete s palci, centimetry nebo body, tento výukový program vám ukáže, jak snadno převzít kontrolu nad formátováním dokumentu.

## Nejčastější dotazy

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro programovou práci s dokumenty Wordu. Umožňuje vývojářům vytvářet, upravovat, převádět a zpracovávat dokumenty aplikace Word bez nutnosti aplikace Microsoft Word.

### Mohu použít jiné měrné jednotky než palce?
 Ano, Aspose.Words for .NET podporuje další jednotky měření, jako jsou centimetry a body. Požadovanou jednotku můžete určit pomocí`OdtSaveMeasureUnit` výčet.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi Aspose.Words for .NET z[zde](https://releases.aspose.com/).

### Kde najdu dokumentaci k Aspose.Words pro .NET?
 Kompletní dokumentaci k Aspose.Words pro .NET získáte na adrese[tento odkaz](https://reference.aspose.com/words/net/).

### Jak mohu získat podporu pro Aspose.Words pro .NET?
 Pro podporu můžete navštívit fórum Aspose.Words na adrese[tento odkaz](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

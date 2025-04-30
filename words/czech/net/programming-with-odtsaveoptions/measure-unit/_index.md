---
"description": "Naučte se, jak nakonfigurovat funkci měrných jednotek v Aspose.Words pro .NET pro zachování formátování dokumentu během převodu ODT."
"linktitle": "Měrná jednotka"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Měrná jednotka"
"url": "/cs/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Měrná jednotka

## Zavedení

Už jste někdy museli převést dokumenty Wordu do různých formátů, ale potřebovali jste pro rozvržení specifickou jednotku měření? Ať už pracujete s palci, centimetry nebo body, je klíčové zajistit, aby si dokument během procesu převodu zachoval svou integritu. V tomto tutoriálu si projdeme, jak nakonfigurovat funkci měrných jednotek v Aspose.Words pro .NET. Tato výkonná funkce zajišťuje, že formátování dokumentu bude při převodu do formátu ODT (Open Document Text) zachováno přesně tak, jak potřebujete.

## Předpoklady

Než se ponoříme do kódu, je potřeba zvážit několik věcí:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou nejnovější verzi Aspose.Words pro .NET. Pokud ji ještě nemáte, můžete si ji stáhnout z [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: IDE, podobné Visual Studiu, pro psaní a spouštění kódu v C#.
3. Základní znalost C#: Pochopení základů C# vám pomůže s plněním úkolů v tutoriálu.
4. Dokument Word: Mějte připravený vzorový dokument Word, který můžete použít k převodu.

## Importovat jmenné prostory

Než začneme s kódováním, ujistěme se, že máme importované potřebné jmenné prostory. Přidejte je pomocí direktiv na začátek souboru s kódem:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavení adresáře dokumentů

Nejprve je třeba definovat cestu k adresáři s dokumenty. Zde se nachází váš dokument Wordu a kam se uloží převedený soubor.

```csharp
// Cesta k adresáři s vašimi dokumenty
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Nahradit `"YOUR DOCUMENTS DIRECTORY"` se skutečnou cestou k vašemu adresáři. Tím zajistíte, že váš kód bude vědět, kde má najít váš dokument Wordu.

## Krok 2: Načtěte dokument Wordu

Dále je třeba načíst dokument Wordu, který chcete převést. To se provádí pomocí `Document` třída z Aspose.Words.

```csharp
// Načtěte dokument Wordu
Document doc = new Document(dataDir + "Document.docx");
```

Ujistěte se, že váš dokument aplikace Word s názvem „Document.docx“ je přítomen v zadaném adresáři.

## Krok 3: Konfigurace měrné jednotky

Nyní nakonfigurujme měrnou jednotku pro převod ODT. A tady se začne dít ta zázrak. Nastavíme `OdtSaveOptions` používat palce jako jednotku měření.

```csharp
// Konfigurace možností zálohování s funkcí „Měrná jednotka“
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

V tomto příkladu nastavujeme měrnou jednotku na palce. Můžete si také vybrat jiné jednotky, například `OdtSaveMeasureUnit.Centimeters` nebo `OdtSaveMeasureUnit.Points` v závislosti na vašich požadavcích.

## Krok 4: Převeďte dokument do formátu ODT

Nakonec převedeme dokument Word do formátu ODT pomocí nakonfigurovaného `OdtSaveOptions`.

```csharp
// Převést dokument do formátu ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Tento řádek kódu uloží převedený dokument do zadaného adresáře s použitou novou měrnou jednotkou.

## Závěr

tady to máte! Pomocí těchto kroků můžete snadno nakonfigurovat funkci měrných jednotek v Aspose.Words pro .NET, abyste zajistili zachování rozvržení dokumentu během převodu. Ať už pracujete s palci, centimetry nebo body, tento tutoriál vám ukázal, jak snadno ovládat formátování dokumentu.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro programovou práci s dokumenty Wordu. Umožňuje vývojářům vytvářet, upravovat, převádět a zpracovávat dokumenty Wordu bez nutnosti použití Microsoft Wordu.

### Mohu použít jiné měrné jednotky než palce?
Ano, Aspose.Words pro .NET podporuje i jiné měrné jednotky, jako jsou centimetry a body. Požadovanou jednotku můžete zadat pomocí `OdtSaveMeasureUnit` výčet.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
Ano, můžete si stáhnout bezplatnou zkušební verzi Aspose.Words pro .NET z [zde](https://releases.aspose.com/).

### Kde najdu dokumentaci k Aspose.Words pro .NET?
Komplexní dokumentaci k Aspose.Words pro .NET naleznete na adrese [tento odkaz](https://reference.aspose.com/words/net/).

### Jak mohu získat podporu pro Aspose.Words pro .NET?
Pro podporu můžete navštívit fórum Aspose.Words na adrese [tento odkaz](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
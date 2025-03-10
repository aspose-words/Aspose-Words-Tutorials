---
title: Napište všechna pravidla CSS do jednoho souboru
linktitle: Napište všechna pravidla CSS do jednoho souboru
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se převádět dokumenty Wordu do HTML pomocí Aspose.Words for .NET se všemi pravidly CSS v jediném souboru pro čistší kód a snadnější údržbu.
weight: 10
url: /cs/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Napište všechna pravidla CSS do jednoho souboru

## Zavedení

Stalo se vám, že jste se při převodu dokumentů Wordu do HTML zapletli do sítě pravidel CSS roztroušených všude možně? Nebojte se! Dnes se ponoříme do úhledné funkce Aspose.Words for .NET, která vám umožňuje psát všechna pravidla CSS do jednoho souboru. To nejen uklidí váš kód, ale také vám to usnadní život. Připoutejte se a vydejte se na cestu k čistšímu a efektivnějšímu výstupu HTML!

## Předpoklady

Než se ponoříme do hlíny, dáme si kachny do řady. Zde je to, co potřebujete, abyste mohli začít:

1.  Aspose.Words for .NET: Ujistěte se, že máte knihovnu Aspose.Words for .NET. Pokud ho ještě nemáte, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí .NET: Na svém počítači budete potřebovat vývojové prostředí .NET. Visual Studio je oblíbenou volbou.
3. Základní znalost C#: Základní znalost programování v C# bude užitečná.
4. Dokument aplikace Word: Připravte si dokument aplikace Word (.docx), který chcete převést.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory do vašeho projektu C#. To nám umožní snadný přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dobře, pojďme si tento proces rozdělit do snadno pochopitelných kroků. Každý krok vás provede konkrétní částí procesu, abyste zajistili, že vše proběhne hladce.

## Krok 1: Nastavte adresář dokumentů

Nejprve musíme definovat cestu k vašemu adresáři dokumentů. Zde je uložen váš dokument aplikace Word a kde bude uložen převedený HTML.

```csharp
// Přístupová cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Krok 2: Načtěte dokument aplikace Word

 Dále načteme dokument Word, který chcete převést do HTML. To se provádí pomocí`Document` třídy z knihovny Aspose.Words.

```csharp
// Načtěte dokument aplikace Word
Document doc = new Document(dataDir + "Document.docx");
```

## Krok 3: Nakonfigurujte možnosti uložení HTML

 Nyní musíme nakonfigurovat možnosti uložení HTML. Konkrétně chceme povolit funkci, která zapisuje všechna pravidla CSS do jednoho souboru. Toho je dosaženo nastavením`SaveFontFaceCssSeparately`majetek do`false`.

```csharp
// Nakonfigurujte možnosti zálohování pomocí funkce „Zapsat všechna pravidla CSS do jednoho souboru“.
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## Krok 4: Převeďte dokument do pevného HTML

Nakonec dokument uložíme jako soubor HTML pomocí nakonfigurovaných možností uložení. Tento krok zajistí, že všechna pravidla CSS budou zapsána do jednoho souboru.

```csharp
// Převést dokument do pevného HTML
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## Závěr

A tady to máte! Pomocí pouhých několika řádků kódu jste úspěšně převedli dokument Wordu do HTML se všemi pravidly CSS úhledně uspořádanými v jediném souboru. Tato metoda nejen zjednodušuje správu CSS, ale také zlepšuje udržovatelnost vašich HTML dokumentů. Takže až budete příště mít za úkol převést dokument aplikace Word, budete přesně vědět, jak udržet pořádek!

## FAQ

### Proč bych měl pro výstup HTML používat jeden soubor CSS?
Použití jediného souboru CSS zjednodušuje správu a údržbu vašich stylů. Díky tomu bude vaše HTML čistší a efektivnější.

### Mohu v případě potřeby oddělit pravidla CSS pro vzhled písma?
 Ano, nastavením`SaveFontFaceCssSeparately` na`true`, můžete oddělit pravidla CSS pro vzhled písma do jiného souboru.

### Je Aspose.Words for .NET zdarma k použití?
 Aspose.Words nabízí bezplatnou zkušební verzi, kterou můžete[stáhnout zde](https://releases.aspose.com/) . Pro další používání zvažte zakoupení licence[zde](https://purchase.aspose.com/buy).

### Na jaké další formáty lze Aspose.Words for .NET převést?
Aspose.Words for .NET podporuje různé formáty včetně PDF, TXT a obrazových formátů jako JPEG a PNG.

### Kde najdu další zdroje na Aspose.Words pro .NET?
 Podívejte se na[dokumentace](https://reference.aspose.com/words/net/) pro komplexní průvodce a reference API.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

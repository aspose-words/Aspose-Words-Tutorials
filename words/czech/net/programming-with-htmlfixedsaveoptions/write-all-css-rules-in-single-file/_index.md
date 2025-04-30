---
"description": "Naučte se, jak převádět dokumenty Wordu do HTML pomocí Aspose.Words pro .NET se všemi pravidly CSS v jednom souboru pro čistší kód a snadnější údržbu."
"linktitle": "Zapsat všechna pravidla CSS do jednoho souboru"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zapsat všechna pravidla CSS do jednoho souboru"
"url": "/cs/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zapsat všechna pravidla CSS do jednoho souboru

## Zavedení

Už jste se někdy při převodu dokumentů Wordu do HTML zamotali v síti pravidel CSS rozházených všude možně? Nebojte se! Dnes se ponoříme do šikovné funkce Aspose.Words pro .NET, která vám umožňuje zapsat všechna pravidla CSS do jednoho souboru. To nejen zpřehlední váš kód, ale také vám to výrazně usnadní život. Připoutejte se a pojďme se na cestu k čistšímu a efektivnějšímu HTML výstupu!

## Předpoklady

Než se pustíme do detailů, pojďme si to rozebrat. Zde je to, co budete potřebovat k začátku:

1. Aspose.Words pro .NET: Ujistěte se, že máte knihovnu Aspose.Words pro .NET. Pokud ji ještě nemáte, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí .NET: Na svém počítači budete potřebovat nainstalované vývojové prostředí .NET. Visual Studio je oblíbenou volbou.
3. Základní znalost C#: Základní znalost programování v C# bude užitečná.
4. Dokument aplikace Word: Mějte připravený dokument aplikace Word (.docx), který chcete převést.

## Importovat jmenné prostory

Nejdříve si do vašeho projektu v C# importujme potřebné jmenné prostory. To nám umožní snadný přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dobře, rozdělme si proces na snadno sledovatelné kroky. Každý krok vás provede určitou částí procesu, aby vše proběhlo hladce.

## Krok 1: Nastavení adresáře dokumentů

Nejprve musíme definovat cestu k adresáři s vašimi dokumenty. Zde je uložen váš dokument Wordu a kam bude uložen převedený HTML kód.

```csharp
// Přístupová cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Krok 2: Načtěte dokument Wordu

Dále načteme dokument aplikace Word, který chcete převést do formátu HTML. To se provádí pomocí `Document` třída z knihovny Aspose.Words.

```csharp
// Načtěte dokument Wordu
Document doc = new Document(dataDir + "Document.docx");
```

## Krok 3: Konfigurace možností ukládání HTML

Nyní musíme nakonfigurovat možnosti ukládání HTML. Konkrétně chceme povolit funkci, která zapisuje všechna pravidla CSS do jednoho souboru. Toho dosáhneme nastavením `SaveFontFaceCssSeparately` majetek `false`.

```csharp
// Konfigurace možností zálohování pomocí funkce „Zapsat všechna pravidla CSS do jednoho souboru“
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## Krok 4: Převod dokumentu do pevného HTML

Nakonec dokument uložíme jako soubor HTML s použitím nakonfigurovaných možností ukládání. Tento krok zajistí, že všechna pravidla CSS budou zapsána v jednom souboru.

```csharp
// Převést dokument do pevného HTML
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## Závěr

A tady to máte! S pouhými několika řádky kódu jste úspěšně převedli dokument Word do HTML se všemi pravidly CSS úhledně uspořádanými v jednom souboru. Tato metoda nejen zjednodušuje správu CSS, ale také zlepšuje údržbu vašich dokumentů HTML. Takže až budete příště muset převést dokument Word, budete přesně vědět, jak na to!

## Často kladené otázky

### Proč bych měl pro svůj HTML výstup používat jeden CSS soubor?
Použití jednoho souboru CSS zjednodušuje správu a údržbu stylů. Díky tomu je váš HTML kód čistší a efektivnější.

### Mohu v případě potřeby oddělit pravidla CSS pro zobrazení písma?
Ano, nastavením `SaveFontFaceCssSeparately` na `true`, můžete oddělit pravidla CSS pro vzhled písma do samostatného souboru.

### Je Aspose.Words pro .NET zdarma k použití?
Aspose.Words nabízí bezplatnou zkušební verzi, kterou můžete [stáhnout zde](https://releases.aspose.com/)Pro další používání zvažte zakoupení licence. [zde](https://purchase.aspose.com/buy).

### Do jakých dalších formátů umí Aspose.Words pro .NET převést?
Aspose.Words pro .NET podporuje různé formáty včetně PDF, TXT a obrazových formátů, jako jsou JPEG a PNG.

### Kde najdu další zdroje o Aspose.Words pro .NET?
Podívejte se na [dokumentace](https://reference.aspose.com/words/net/) pro komplexní průvodce a reference API.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
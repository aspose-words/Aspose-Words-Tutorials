---
"description": "Zmenšete velikost PDF zakázáním vložených písem pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu a optimalizujte své dokumenty pro efektivní ukládání a sdílení."
"linktitle": "Zmenšení velikosti PDF zakázáním vložených písem"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zmenšení velikosti PDF zakázáním vložených písem"
"url": "/cs/net/programming-with-pdfsaveoptions/disable-embed-windows-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zmenšení velikosti PDF zakázáním vložených písem

## Zavedení

Zmenšení velikosti souborů PDF může být klíčové pro efektivní ukládání a rychlé sdílení. Jedním z účinných způsobů, jak toho dosáhnout, je zakázat vložená písma, zejména pokud jsou standardní písma již k dispozici na většině systémů. V tomto tutoriálu se podíváme na to, jak zmenšit velikost PDF zakázáním vložených písem pomocí Aspose.Words pro .NET. Projdeme si každý krok, abyste se ujistili, že to můžete snadno implementovat ve svých vlastních projektech.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si a nainstalujte si jej z [Odkaz ke stažení](https://releases.aspose.com/words/net/).
- Vývojové prostředí .NET: Visual Studio je oblíbenou volbou.
- Ukázkový dokument aplikace Word: Mějte připravený soubor DOCX, který chcete převést do formátu PDF.

## Importovat jmenné prostory

Pro začátek se ujistěte, že máte do projektu importovány potřebné jmenné prostory. To vám umožní přístup ke třídám a metodám potřebným pro náš úkol.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Rozdělme si proces na jednoduché a snadno zvládnutelné kroky. Každý krok vás provede úkolem a zajistí, že budete rozumět tomu, co se v každém okamžiku děje.

## Krok 1: Inicializace dokumentu

Nejprve musíme načíst dokument Wordu, který chcete převést do formátu PDF. Zde začíná vaše cesta.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Zde, `dataDir` je zástupný symbol pro adresář, kde se nachází váš dokument. Nahraďte `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou.

## Krok 2: Konfigurace možností ukládání PDF

Dále nastavíme možnosti ukládání PDF. Zde určíme, že nechceme vkládat standardní písma Windows.

```csharp
// Výstupní PDF bude uložen bez vložení standardních fontů systému Windows.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedNone
};
```

Nastavením `FontEmbeddingMode` na `EmbedNone`, dáváme pokyn Aspose.Words, aby tyto fonty do PDF souboru nezahrnoval, čímž se zmenší velikost souboru.

## Krok 3: Uložte dokument jako PDF

Nakonec dokument uložíme jako PDF pomocí nakonfigurovaných možností ukládání. Toto je okamžik pravdy, kdy se váš DOCX transformuje do kompaktního PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DisableEmbedWindowsFonts.pdf", saveOptions);
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` s vaší skutečnou cestou k adresáři. Výstupní PDF bude nyní uložen do zadaného adresáře bez vložených standardních písem.

## Závěr

Dodržováním těchto kroků můžete výrazně zmenšit velikost souborů PDF. Zakázání vložených písem je jednoduchý, ale efektivní způsob, jak zesvětlit a snáze sdílet dokumenty. Aspose.Words pro .NET tento proces usnadňuje a zajišťuje, že můžete optimalizovat své soubory s minimálním úsilím.

## Často kladené otázky

### Proč bych měl zakázat vložená písma v PDF?
Zakázání vložených písem může výrazně zmenšit velikost souboru PDF, což zefektivní jeho ukládání a urychlí jeho sdílení.

### Bude se PDF soubor zobrazovat správně i bez vložených písem?
Ano, pokud jsou fonty standardní a dostupné v systému, kde se PDF prohlíží, zobrazí se správně.

### Mohu do PDF selektivně vložit pouze určitá písma?
Ano, Aspose.Words pro .NET umožňuje přizpůsobit, která písma jsou vložena, což poskytuje flexibilitu při zmenšování velikosti souboru.

### Potřebuji Aspose.Words pro .NET k zakázání vložených písem v PDF?
Ano, Aspose.Words pro .NET poskytuje funkce potřebné ke konfiguraci možností vkládání písem do PDF.

### Jak získám podporu, pokud narazím na problémy?
Můžete navštívit [Fórum podpory](https://forum.aspose.com/c/words/8) pro pomoc s jakýmikoli problémy, se kterými se setkáte.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
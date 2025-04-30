---
"description": "Naučte se, jak sloučit dva dokumenty Wordu pomocí Aspose.Words pro .NET. Podrobný návod, jak vložit dokument pomocí DocumentBuilderu a zachovat formátování."
"linktitle": "Vložit dokument pomocí nástroje Builder"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložit dokument pomocí nástroje Builder"
"url": "/cs/net/join-and-append-documents/insert-document-with-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložit dokument pomocí nástroje Builder

## Zavedení

Takže máte dva dokumenty Wordu a chcete je sloučit do jednoho. Možná si říkáte: „Existuje nějaký snadný způsob, jak to udělat programově?“ Rozhodně! Dnes vás provedu procesem vkládání jednoho dokumentu do druhého pomocí knihovny Aspose.Words pro .NET. Tato metoda je velmi praktická, zejména když pracujete s velkými dokumenty nebo potřebujete proces automatizovat. Pojďme se na to rovnou pustit!

## Předpoklady

Než začneme, ujistěme se, že máte vše, co potřebujete:

1. Aspose.Words pro .NET: Pokud jste tak ještě neučinili, můžete si jej stáhnout z [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Ujistěte se, že máte nainstalované Visual Studio nebo jiné vhodné IDE.
3. Základní znalost C#: Trocha znalosti C# bude hodně užitečná.

## Importovat jmenné prostory

Nejdříve je potřeba importovat potřebné jmenné prostory pro přístup k funkcím knihovny Aspose.Words. Zde je návod, jak to udělat:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nyní, když máme splněny všechny předpoklady, pojďme si celý proces rozebrat krok za krokem.

## Krok 1: Nastavení adresáře dokumentů

Než začneme s kódováním, je třeba nastavit cestu k adresáři s vašimi dokumenty. Zde jsou uloženy vaše zdrojové a cílové dokumenty.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde se vaše dokumenty nacházejí. To programu pomůže vaše soubory snadno najít.

## Krok 2: Načtení zdrojových a cílových dokumentů

Dále musíme načíst dokumenty, se kterými chceme pracovat. V tomto příkladu máme zdrojový dokument a cílový dokument.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

Zde používáme `Document` třídu z knihovny Aspose.Words pro načtení našich dokumentů. Ujistěte se, že názvy souborů odpovídají názvům ve vašem adresáři.

## Krok 3: Vytvoření objektu DocumentBuilder

Ten/Ta/To `DocumentBuilder` Třída je mocný nástroj v knihovně Aspose.Words. Umožňuje nám navigaci a manipulaci s dokumentem.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

V tomto kroku jsme vytvořili `DocumentBuilder` objekt pro náš cílový dokument. To nám pomůže vložit obsah do dokumentu.

## Krok 4: Přesun na konec dokumentu

Před vložením zdrojového dokumentu musíme přesunout kurzor nástroje pro tvorbu na konec cílového dokumentu.

```csharp
builder.MoveToDocumentEnd();
```

Tím je zajištěno, že zdrojový dokument bude vložen na konec cílového dokumentu.

## Krok 5: Vložení zalomení stránky

Pro přehlednost přidáme před vložením zdrojového dokumentu zalomení stránky. Tím se obsah zdrojového dokumentu začne číst na nové stránce.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Zalomení stránky zajišťuje, že obsah zdrojového dokumentu začíná na nové stránce, díky čemuž sloučený dokument vypadá profesionálně.

## Krok 6: Vložení zdrojového dokumentu

A teď přichází ta vzrušující část – samotné vložení zdrojového dokumentu do cílového dokumentu.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

Použití `InsertDocument` metodou můžeme vložit celý zdrojový dokument do cílového dokumentu. `ImportFormatMode.KeepSourceFormatting` zajišťuje zachování formátování zdrojového dokumentu.

## Krok 7: Uložení sloučeného dokumentu

Nakonec uložme sloučený dokument. Tím se zdrojový a cílový dokument sloučí do jednoho souboru.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

Uložením dokumentu dokončíme proces sloučení obou dokumentů. Váš nový dokument je nyní připraven a uložen v zadaném adresáři.

## Závěr

A tady to máte! Úspěšně jste vložili jeden dokument do druhého pomocí Aspose.Words pro .NET. Tato metoda je nejen efektivní, ale také zachovává formátování obou dokumentů, což zajišťuje bezproblémové sloučení. Ať už pracujete na jednorázovém projektu, nebo potřebujete automatizovat zpracování dokumentů, Aspose.Words pro .NET vám s tím pomůže.

## Často kladené otázky

### Co je Aspose.Words pro .NET?  
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, upravovat, převádět a manipulovat s dokumenty Wordu.

### Mohu zachovat formátování zdrojového dokumentu?  
Ano, pomocí `ImportFormatMode.KeepSourceFormatting`formátování zdrojového dokumentu se zachová i při jeho vložení do cílového dokumentu.

### Potřebuji licenci k používání Aspose.Words pro .NET?  
Ano, Aspose.Words pro .NET vyžaduje pro plnou funkčnost licenci. Můžete si pořídit [dočasná licence](https://purchase.aspose.com/temporary-license/) pro hodnocení.

### Mohu tento proces automatizovat?  
Rozhodně! Popsanou metodu lze začlenit do větších aplikací pro automatizaci úloh zpracování dokumentů.

### Kde mohu najít další zdroje a podporu?  
Pro více informací se můžete podívat na [dokumentace](https://reference.aspose.com/words/net/)nebo navštivte [fórum podpory](https://forum.aspose.com/c/words/8) o pomoc.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
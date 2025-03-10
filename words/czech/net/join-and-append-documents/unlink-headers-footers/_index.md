---
title: Odpojit záhlaví a zápatí
linktitle: Odpojit záhlaví a zápatí
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak zrušit propojení záhlaví a zápatí v dokumentech aplikace Word pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce krok za krokem pro manipulaci s hlavním dokumentem.
weight: 10
url: /cs/net/join-and-append-documents/unlink-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Odpojit záhlaví a zápatí

## Zavedení

Ve světě zpracování dokumentů může být někdy problém udržet konzistentní záhlaví a zápatí. Ať už slučujete dokumenty nebo jen chcete mít různá záhlaví a zápatí pro různé sekce, vědět, jak je odpojit, je zásadní. Dnes se ponoříme do toho, jak toho můžete dosáhnout pomocí Aspose.Words pro .NET. Rozebereme to krok za krokem, abyste to mohli snadno sledovat. Jste připraveni zvládnout manipulaci s dokumenty? Začněme!

## Předpoklady

Než se pustíme do toho nejzákladnějšího, je tu několik věcí, které budete potřebovat:

-  Aspose.Words for .NET Library: Můžete si ji stáhnout z[Aspose stránku vydání](https://releases.aspose.com/words/net/).
- .NET Framework: Ujistěte se, že máte nainstalovaný kompatibilní .NET Framework.
- IDE: Visual Studio nebo jakékoli jiné integrované vývojové prostředí kompatibilní s .NET.
- Základní porozumění C#: Budete potřebovat základní znalosti programovacího jazyka C#.

## Importovat jmenné prostory

Chcete-li začít, nezapomeňte do projektu importovat potřebné jmenné prostory. To vám umožní přístup ke knihovně Aspose.Words a jejím funkcím.

```csharp
using Aspose.Words;
```

Pojďme si tento proces rozdělit na zvládnutelné kroky, které vám pomohou odpojit záhlaví a zápatí v dokumentech aplikace Word.

## Krok 1: Nastavte svůj projekt

Nejprve budete muset nastavit prostředí vašeho projektu. Otevřete své IDE a vytvořte nový projekt .NET. Přidejte odkaz na knihovnu Aspose.Words, kterou jste stáhli dříve.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Načtěte zdrojový dokument

Dále musíte načíst zdrojový dokument, který chcete upravit. Tento dokument bude mít odpojená záhlaví a zápatí.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Krok 3: Vložte cílový dokument

Nyní načtěte cílový dokument, kam připojíte zdrojový dokument po zrušení propojení jeho záhlaví a zápatí.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Krok 4: Odpojte záhlaví a zápatí

 Tento krok je zásadní. Chcete-li odpojit záhlaví a zápatí zdrojového dokumentu od záhlaví a zápatí cílového dokumentu, použijte`LinkToPrevious` metoda. Tato metoda zajišťuje, že se záhlaví a zápatí nepřenesou do připojeného dokumentu.

```csharp
// Chcete-li to zastavit, zrušte propojení záhlaví a zápatí ve zdrojovém dokumentu
//od pokračování v záhlaví a zápatí cílového dokumentu.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Krok 5: Připojte zdrojový dokument

 Po zrušení propojení záhlaví a zápatí můžete připojit zdrojový dokument k cílovému dokumentu. Použijte`AppendDocument` a nastavte režim formátu importu na`KeepSourceFormatting` zachovat původní formátování zdrojového dokumentu.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Krok 6: Uložte konečný dokument

Nakonec nově vytvořený dokument uložte. Tento dokument bude mít obsah zdrojového dokumentu připojený k cílovému dokumentu, přičemž záhlaví a zápatí nebudou propojena.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Závěr

A tady to máte! Pomocí těchto kroků jste úspěšně odpojili záhlaví a zápatí ve zdrojovém dokumentu a připojili je k cílovému dokumentu pomocí Aspose.Words for .NET. Tato technika může být zvláště užitečná, když pracujete se složitými dokumenty, které vyžadují různá záhlaví a zápatí pro různé sekce. Šťastné kódování!

## FAQ

### Co je Aspose.Words for .NET?  
Aspose.Words for .NET je výkonná knihovna pro práci s dokumenty Wordu v aplikacích .NET. Umožňuje vývojářům vytvářet, upravovat, převádět a tisknout dokumenty programově.

### Mohu odpojit záhlaví a zápatí pouze pro konkrétní sekce?  
 Ano, můžete odpojit záhlaví a zápatí pro konkrétní sekce přístupem k`HeadersFooters` vlastnost požadované sekce a pomocí`LinkToPrevious` metoda.

### Je možné zachovat původní formátování zdrojového dokumentu?  
 Ano, při přidávání zdrojového dokumentu použijte`ImportFormatMode.KeepSourceFormatting` možnost zachovat původní formátování.

### Mohu používat Aspose.Words pro .NET s jinými jazyky .NET kromě C#?  
Absolutně! Aspose.Words for .NET lze použít s jakýmkoli jazykem .NET, včetně VB.NET a F#.

### Kde najdu další dokumentaci a podporu pro Aspose.Words pro .NET?  
 Komplexní dokumentaci naleznete na[Stránka dokumentace Aspose.Words for .NET](https://reference.aspose.com/words/net/) a podpora je k dispozici na[Aspose fórum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

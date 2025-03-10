---
title: Odebrat zápatí zdrojových záhlaví
linktitle: Odebrat zápatí zdrojových záhlaví
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak odstranit záhlaví a zápatí v dokumentech aplikace Word pomocí Aspose.Words for .NET. Zjednodušte si správu dokumentů pomocí našeho podrobného průvodce.
weight: 10
url: /cs/net/join-and-append-documents/remove-source-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Odebrat zápatí zdrojových záhlaví

## Zavedení

V tomto komplexním průvodci se ponoříme do toho, jak efektivně odstranit záhlaví a zápatí z dokumentu aplikace Word pomocí Aspose.Words for .NET. Záhlaví a zápatí se běžně používají pro číslování stránek, názvy dokumentů nebo jiný opakující se obsah v dokumentech aplikace Word. Ať už slučujete dokumenty nebo čistíte formátování, zvládnutí tohoto procesu může zefektivnit vaše úkoly správy dokumentů. Pojďme prozkoumat proces krok za krokem, jak toho dosáhnout pomocí Aspose.Words for .NET.

## Předpoklady

Než se pustíte do výukového programu, ujistěte se, že máte nastaveny následující předpoklady:

1. Vývojové prostředí: Mějte nainstalované Visual Studio nebo jiné vývojové prostředí .NET.
2.  Aspose.Words for .NET: Ujistěte se, že jste si stáhli a nainstalovali Aspose.Words for .NET. Pokud ne, můžete to získat od[zde](https://releases.aspose.com/words/net/).
3. Základní znalosti: Znalost programování v C# a základy .NET frameworku.

## Importovat jmenné prostory

Než začnete kódovat, nezapomeňte importovat potřebné jmenné prostory do souboru C#:

```csharp
using Aspose.Words;
```

## Krok 1: Načtěte zdrojový dokument

 Nejprve musíte načíst zdrojový dokument, ze kterého chcete odstranit záhlaví a zápatí. Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k adresáři vašeho dokumentu, kde se nachází zdrojový dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Krok 2: Vytvořte nebo načtěte cílový dokument

 Pokud jste ještě nevytvořili cílový dokument, kam chcete umístit upravený obsah, můžete vytvořit nový`Document` objekt nebo načíst existující.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Krok 3: Vymažte záhlaví a zápatí ze sekcí

Iterujte každou sekci ve zdrojovém dokumentu (`srcDoc`) a vymažte jeho záhlaví a zápatí.

```csharp
foreach (Section section in srcDoc.Sections)
{
    section.ClearHeadersFooters();
}
```

## Krok 4: Správa nastavení LinkToPrevious

Chcete-li zabránit pokračování záhlaví a zápatí v cílovém dokumentu (`dstDoc` ), ujistěte se, že`LinkToPrevious` nastavení pro záhlaví a zápatí je nastaveno na`false`.

```csharp
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Krok 5: Připojte upravený dokument k cílovému dokumentu

Nakonec přidejte upravený obsah ze zdrojového dokumentu (`srcDoc`) do cílového dokumentu (`dstDoc`) při zachování formátování zdroje.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Krok 6: Uložte výsledný dokument

Uložte konečný dokument s odstraněnými záhlavími a zápatími do určeného adresáře.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.RemoveSourceHeadersFooters.docx");
```

## Závěr

Odstranění záhlaví a zápatí z dokumentu aplikace Word pomocí Aspose.Words for .NET je přímočarý proces, který může výrazně zlepšit úkoly správy dokumentů. Podle výše uvedených kroků můžete dokumenty efektivně vyčistit a získat tak uhlazený profesionální vzhled.

## FAQ

### Mohu odstranit záhlaví a zápatí pouze z určitých sekcí?
Ano, můžete iterovat sekcemi a podle potřeby selektivně smazat záhlaví a zápatí.

### Podporuje Aspose.Words for .NET odstranění záhlaví a zápatí ve více dokumentech?
Rozhodně můžete manipulovat se záhlavími a zápatími ve více dokumentech pomocí Aspose.Words for .NET.

###  Co se stane, když zapomenu nastavit`LinkToPrevious` to `false`?
Záhlaví a zápatí ze zdrojového dokumentu mohou pokračovat do cílového dokumentu.

### Mohu odstranit záhlaví a zápatí programově, aniž by to ovlivnilo jiné formátování?
Ano, Aspose.Words for .NET umožňuje odstranit záhlaví a zápatí při zachování zbytku formátování dokumentu.

### Kde najdu další zdroje a podporu pro Aspose.Words pro .NET?
 Navštivte[Aspose.Words pro dokumentaci .NET](https://reference.aspose.com/words/net/) pro podrobné API reference a příklady.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
"description": "Naučte se, jak odstranit záhlaví a zápatí v dokumentech Wordu pomocí Aspose.Words pro .NET. Zjednodušte si správu dokumentů s naším podrobným návodem."
"linktitle": "Odebrat záhlaví a zápatí zdroje"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Odebrat záhlaví a zápatí zdroje"
"url": "/cs/net/join-and-append-documents/remove-source-headers-footers/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Odebrat záhlaví a zápatí zdroje

## Zavedení

tomto komplexním průvodci se ponoříme do toho, jak efektivně odstranit záhlaví a zápatí z dokumentu Word pomocí Aspose.Words pro .NET. Záhlaví a zápatí se běžně používají k číslování stránek, názvům dokumentů nebo jinému opakujícímu se obsahu v dokumentech Word. Ať už slučujete dokumenty nebo čistíte formátování, zvládnutí tohoto procesu může zefektivnit vaše úkoly správy dokumentů. Pojďme se podívat na podrobný postup, jak toho dosáhnout pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíte do tutoriálu, ujistěte se, že máte nastaveny následující předpoklady:

1. Vývojové prostředí: Mějte nainstalované Visual Studio nebo jakékoli jiné vývojové prostředí .NET.
2. Aspose.Words pro .NET: Ujistěte se, že jste si stáhli a nainstalovali Aspose.Words pro .NET. Pokud ne, můžete si ho stáhnout z [zde](https://releases.aspose.com/words/net/).
3. Základní znalosti: Znalost programování v C# a základů .NET frameworku.

## Importovat jmenné prostory

Než začnete s kódováním, nezapomeňte importovat potřebné jmenné prostory do souboru C#:

```csharp
using Aspose.Words;
```

## Krok 1: Načtení zdrojového dokumentu

Nejprve je třeba načíst zdrojový dokument, ze kterého chcete odstranit záhlaví a zápatí. Nahraďte `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k adresáři dokumentů, kde se nachází zdrojový dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Krok 2: Vytvoření nebo načtení cílového dokumentu

Pokud jste ještě nevytvořili cílový dokument, kam chcete umístit upravený obsah, můžete vytvořit nový `Document` objekt nebo načíst existující.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Krok 3: Vymazání záhlaví a zápatí ze sekcí

Projděte si každou sekci ve zdrojovém dokumentu (`srcDoc`) a vymazat jeho záhlaví a zápatí.

```csharp
foreach (Section section in srcDoc.Sections)
{
    section.ClearHeadersFooters();
}
```

## Krok 4: Správa nastavení LinkToPrevious

Aby se zabránilo pokračování záhlaví a zápatí v cílovém dokumentu (`dstDoc`), zajistěte, aby `LinkToPrevious` nastavení záhlaví a zápatí je nastaveno na `false`.

```csharp
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Krok 5: Připojení upraveného dokumentu k cílovému dokumentu

Nakonec přidejte upravený obsah ze zdrojového dokumentu (`srcDoc`) do cílového dokumentu (`dstDoc`) při zachování formátování zdroje.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Krok 6: Uložte výsledný dokument

Uložte finální dokument s odstraněnými záhlavími a zápatími do vámi určeného adresáře.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.RemoveSourceHeadersFooters.docx");
```

## Závěr

Odstranění záhlaví a zápatí z dokumentu Word pomocí Aspose.Words pro .NET je jednoduchý proces, který může výrazně vylepšit úkoly správy dokumentů. Dodržením výše uvedených kroků můžete efektivně vyčistit dokumenty a dosáhnout uhlazeného a profesionálního vzhledu.

## Často kladené otázky

### Mohu odstranit záhlaví a zápatí pouze z konkrétních sekcí?
Ano, můžete procházet sekcemi a podle potřeby selektivně mazat záhlaví a zápatí.

### Podporuje Aspose.Words pro .NET odstraňování záhlaví a zápatí napříč více dokumenty?
Rozhodně můžete manipulovat se záhlavími a zápatími napříč více dokumenty pomocí Aspose.Words pro .NET.

### Co se stane, když zapomenu nastavit `LinkToPrevious` na `false`?
Záhlaví a zápatí ze zdrojového dokumentu mohou pokračovat do cílového dokumentu.

### Mohu programově odstranit záhlaví a zápatí, aniž by to ovlivnilo ostatní formátování?
Ano, Aspose.Words pro .NET umožňuje odstranit záhlaví a zápatí a zároveň zachovat zbytek formátování dokumentu.

### Kde najdu další zdroje a podporu pro Aspose.Words pro .NET?
Navštivte [Dokumentace k Aspose.Words pro .NET](https://reference.aspose.com/words/net/) pro podrobné reference a příklady API.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
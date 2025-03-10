---
title: Aktualizovat vlastnost posledního uloženého času
linktitle: Aktualizovat vlastnost posledního uloženého času
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak aktualizovat vlastnost posledního uloženého času v dokumentech aplikace Word pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce krok za krokem.
weight: 10
url: /cs/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktualizovat vlastnost posledního uloženého času

## Zavedení

Přemýšleli jste někdy, jak programově sledovat vlastnost posledního uloženého času v dokumentech aplikace Word? Pokud máte co do činění s více dokumenty a potřebujete zachovat jejich metadata, aktualizace vlastnosti posledního uloženého času může být docela užitečná. Dnes vás provedu tímto procesem pomocí Aspose.Words pro .NET. Tak se připoutejte a jdeme do toho!

## Předpoklady

Než se pustíme do podrobného průvodce, budete potřebovat několik věcí:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou aplikaci Aspose.Words for .NET. Pokud ne, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vývojové prostředí jako Visual Studio.
3. Základní znalost C#: Bude užitečné porozumět základům programování v C#.

## Importovat jmenné prostory

Nejprve se ujistěte, že jste do projektu importovali potřebné jmenné prostory. To vám umožní přístup ke třídám a metodám potřebným pro manipulaci s dokumenty aplikace Word.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nyní si celý proces rozdělíme do jednoduchých kroků. Každý krok vás provede procesem aktualizace poslední uložené vlastnosti času v dokumentu aplikace Word.

## Krok 1: Nastavte adresář dokumentů

Nejprve musíte zadat cestu k adresáři dokumentů. Zde je uložen váš stávající dokument a kam se uloží aktualizovaný dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři.

## Krok 2: Načtěte dokument aplikace Word

 Dále načtěte dokument aplikace Word, který chcete aktualizovat. Můžete to udělat vytvořením instance souboru`Document` třídy a předání cesty vašeho dokumentu.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

 Ujistěte se, že dokument s názvem`Document.docx` je přítomen v zadaném adresáři.

## Krok 3: Nakonfigurujte možnosti uložení

 Nyní vytvořte instanci souboru`OoxmlSaveOptions` třída. Tato třída umožňuje zadat možnosti pro uložení dokumentu ve formátu Office Open XML (OOXML). Zde nastavíte`UpdateLastSavedTimeProperty` na`true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Tím Aspose.Words sdělíte, že má aktualizovat vlastnost posledního uloženého času dokumentu.

## Krok 4: Uložte aktualizovaný dokument

 Nakonec dokument uložte pomocí`Save` metoda`Document` třídy, předáním cesty, kam chcete uložit aktualizovaný dokument, a možností uložení.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Tím se dokument uloží s aktualizovanou vlastností posledního uloženého času.

## Závěr

A tady to máte! Pomocí těchto kroků můžete snadno aktualizovat vlastnost posledního uloženého času vašich dokumentů Word pomocí Aspose.Words for .NET. To je užitečné zejména pro udržování přesných metadat ve vašich dokumentech, což může být klíčové pro systémy správy dokumentů a různé další aplikace.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro vytváření, úpravy a převod dokumentů aplikace Word v aplikacích .NET.

### Proč bych měl aktualizovat vlastnost posledního uloženého času?
Aktualizace vlastnosti posledního uloženého času pomáhá udržovat přesná metadata, která jsou nezbytná pro sledování a správu dokumentů.

### Mohu aktualizovat další vlastnosti pomocí Aspose.Words for .NET?
Ano, Aspose.Words for .NET umožňuje aktualizovat různé vlastnosti dokumentu, jako je název, autor a předmět.

### Je Aspose.Words for .NET zdarma?
 Aspose.Words for .NET nabízí bezplatnou zkušební verzi, ale pro plnou funkčnost je vyžadována licence. Můžete získat licenci[zde](https://purchase.aspose.com/buy).

### Kde najdu další návody na Aspose.Words pro .NET?
Můžete najít další návody a dokumentaci[zde](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
"description": "Naučte se, jak aktualizovat vlastnost času posledního uložení v dokumentech Wordu pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu krok za krokem."
"linktitle": "Aktualizovat vlastnost Čas posledního uloženého záznamu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Aktualizovat vlastnost Čas posledního uloženého záznamu"
"url": "/cs/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aktualizovat vlastnost Čas posledního uloženého záznamu

## Zavedení

Přemýšleli jste někdy, jak programově sledovat vlastnost posledního uloženého času v dokumentech Wordu? Pokud pracujete s více dokumenty a potřebujete uchovávat jejich metadata, aktualizace vlastnosti posledního uloženého času může být docela užitečná. Dnes vás tímto procesem provedu pomocí Aspose.Words pro .NET. Takže se připoutejte a pojďme se do toho pustit!

## Předpoklady

Než se pustíme do podrobného návodu, je několik věcí, které budete potřebovat:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovaný Aspose.Words pro .NET. Pokud ho nemáte, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vývojové prostředí, jako je Visual Studio.
3. Základní znalost C#: Pochopení základů programování v C# bude užitečné.

## Importovat jmenné prostory

Nejprve se ujistěte, že jste do projektu importovali potřebné jmenné prostory. To vám umožní přístup ke třídám a metodám potřebným pro manipulaci s dokumenty Wordu.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nyní si celý proces rozdělme na jednoduché kroky. Každý krok vás provede procesem aktualizace vlastnosti posledního uloženého času ve vašem dokumentu Word.

## Krok 1: Nastavení adresáře dokumentů

Nejprve je třeba zadat cestu k adresáři s dokumenty. Zde je uložen váš stávající dokument a kam bude uložen i aktualizovaný dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři.

## Krok 2: Načtěte dokument aplikace Word

Dále načtěte dokument Wordu, který chcete aktualizovat. Můžete to provést vytvořením instance `Document` třídu a předáním cesty k vašemu dokumentu.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

Ujistěte se, že dokument s názvem `Document.docx` je přítomen v zadaném adresáři.

## Krok 3: Konfigurace možností ukládání

Nyní vytvořte instanci `OoxmlSaveOptions` třída. Tato třída umožňuje zadat možnosti pro ukládání dokumentu ve formátu Office Open XML (OOXML). Zde nastavíte `UpdateLastSavedTimeProperty` na `true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Toto říká Aspose.Words, aby aktualizoval vlastnost času posledního uložení dokumentu.

## Krok 4: Uložte aktualizovaný dokument

Nakonec dokument uložte pomocí `Save` metoda `Document` třídu, předáním cesty, kam chcete uložit aktualizovaný dokument, a možností uložení.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Tím se dokument uloží s aktualizovanou vlastností času posledního uložení.

## Závěr

A tady to máte! Pomocí těchto kroků můžete snadno aktualizovat vlastnost času posledního uložení vašich dokumentů Word pomocí Aspose.Words pro .NET. To je obzvláště užitečné pro uchování přesných metadat v dokumentech, což může být klíčové pro systémy správy dokumentů a různé další aplikace.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro vytváření, úpravy a převod dokumentů Wordu v aplikacích .NET.

### Proč bych měl aktualizovat vlastnost posledního uloženého času?
Aktualizace vlastnosti času posledního uložení pomáhá udržovat přesná metadata, což je nezbytné pro sledování a správu dokumentů.

### Mohu aktualizovat další vlastnosti pomocí Aspose.Words pro .NET?
Ano, Aspose.Words pro .NET umožňuje aktualizovat různé vlastnosti dokumentu, jako je název, autor a předmět.

### Je Aspose.Words pro .NET zdarma?
Aspose.Words pro .NET nabízí bezplatnou zkušební verzi, ale pro plnou funkčnost je vyžadována licence. Licenci můžete získat [zde](https://purchase.aspose.com/buy).

### Kde najdu další tutoriály o Aspose.Words pro .NET?
Další návody a dokumentaci naleznete [zde](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
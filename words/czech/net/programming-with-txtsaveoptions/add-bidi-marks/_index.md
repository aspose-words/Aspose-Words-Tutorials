---
"description": "Naučte se v tomto průvodci, jak přidávat obousměrné (Bidi) značky do dokumentů Wordu pomocí Aspose.Words pro .NET. Zajistěte správný směr textu pro vícejazyčný obsah."
"linktitle": "Přidání oboustranných značek v dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidání oboustranných značek v dokumentu Word"
"url": "/cs/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidání oboustranných značek v dokumentu Word

## Zavedení

Ve světě zpracování dokumentů může být obousměrný (Bidi) text často poněkud složitý na správu. To platí zejména při práci s jazyky, které mají různé směry textu, jako je arabština nebo hebrejština. Naštěstí Aspose.Words pro .NET usnadňuje takové scénáře. V tomto tutoriálu si ukážeme, jak přidat značky Bidi do dokumentu Wordu pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Musíte mít nainstalovaný Aspose.Words pro .NET. Můžete si ho stáhnout z [Stránka ke stažení Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework nebo .NET Core: Ujistěte se, že máte nastavené kompatibilní prostředí .NET pro spuštění příkladů.
3. Základní znalost C#: Znalost programovacího jazyka C# a základních operací v .NET.

## Importovat jmenné prostory

Chcete-li začít, musíte importovat potřebné jmenné prostory. Zde je návod, jak je můžete zahrnout do svého projektu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Pojďme si rozebrat proces přidávání Bidi značek do dokumentu Wordu do jasných kroků. Každý krok vás provede kódem a jeho účelem.

## Krok 1: Nastavení dokumentu

Začněte vytvořením nové instance `Document` třída a `DocumentBuilder` pro přidání obsahu do dokumentu.

```csharp
// Cesta k adresáři s vašimi dokumenty
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Vytvořte dokument a přidejte obsah
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

V tomto kroku inicializujete nový dokument aplikace Word a nastavíte `DocumentBuilder` pro usnadnění vkládání obsahu.

## Krok 2: Přidání obsahu do dokumentu

Dále přidejte do dokumentu text. Zde přidáme text v různých jazycích pro ilustraci práce s oboustranným textem.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Zde nejprve přidáme standardní anglickou frázi. Poté povolíme formátování textu Bidi pro následující text, který je napsán v hebrejštině a arabštině. To ukazuje, jak začlenit obousměrný text.

## Krok 3: Konfigurace možností ukládání pro oboustranné značky

Aby se značky Bidi v dokumentu správně uložily, je třeba nakonfigurovat `TxtSaveOptions` a povolit `AddBidiMarks` volba.

```csharp
// Přidat bidi značky
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

V tomto kroku vytvoříme instanci `TxtSaveOptions` a nastavte `AddBidiMarks` majetek `true`Tím se zajistí, že při ukládání dokumentu jako textového souboru budou zahrnuty značky Bidi.

## Závěr

Přidání značek Bidi do dokumentů Wordu může být klíčovým krokem při práci s vícejazyčným obsahem, který zahrnuje jazyky s různými směry textu. S Aspose.Words pro .NET je tento proces přímočarý a efektivní. Dodržením výše uvedených kroků můžete zajistit, aby vaše dokumenty správně zobrazovaly text Bidi, což zvyšuje čitelnost a přesnost.

## Často kladené otázky

### Co jsou značky Bidi a proč jsou důležité?
Značky Bidi jsou speciální znaky používané k ovládání směru textu v dokumentech. Jsou nezbytné pro správné zobrazení jazyků, které se čtou zprava doleva, jako je arabština a hebrejština.

### Mohu použít Aspose.Words pro .NET k řešení jiných typů problémů se směrováním textu?
Ano, Aspose.Words pro .NET poskytuje komplexní podporu pro různé potřeby směrování a formátování textu, včetně jazyků s psaním zprava doleva a zleva doprava.

### Je možné použít formátování Bidi pouze na určité části dokumentu?
Ano, formátování Bidi můžete podle potřeby použít na konkrétní odstavce nebo části dokumentu.

### V jakých formátech mohu uložit dokument s oboustrannými značkami?
V uvedeném příkladu je dokument uložen jako textový soubor. Aspose.Words však také podporuje ukládání dokumentů v různých formátech se zachováním oboustranných znaků.

### Kde najdu více informací o Aspose.Words pro .NET?
Více informací o Aspose.Words pro .NET naleznete na [Dokumentace Aspose](https://reference.aspose.com/words/net/) a přístup k [Fórum podpory](https://forum.aspose.com/c/words/8) pro další pomoc.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
---
title: Přidejte Bidi značky do dokumentu Word
linktitle: Přidejte Bidi značky do dokumentu Word
second_title: Aspose.Words API pro zpracování dokumentů
description: V této příručce se dozvíte, jak přidat obousměrné (Bidi) značky do dokumentů aplikace Word pomocí Aspose.Words for .NET. Zajistěte správný směr textu pro vícejazyčný obsah.
weight: 10
url: /cs/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidejte Bidi značky do dokumentu Word

## Zavedení

Ve světě zpracování dokumentů může být správa obousměrného (Bidi) textu často trochu složitější. To platí zejména při práci s jazyky, které mají různé směry textu, jako je arabština nebo hebrejština. Naštěstí Aspose.Words for .NET usnadňuje zvládnutí takových scénářů. V tomto tutoriálu si projdeme, jak přidat značky Bidi do dokumentu aplikace Word pomocí Aspose.Words for .NET.

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte následující:

1. Aspose.Words for .NET: Musíte mít nainstalovanou aplikaci Aspose.Words for .NET. Můžete si jej stáhnout z[Stránka Aspose Downloads](https://releases.aspose.com/words/net/).
2. .NET Framework nebo .NET Core: Ujistěte se, že máte pro spouštění příkladů nastaveno kompatibilní prostředí .NET.
3. Základní znalost C#: Znalost programovacího jazyka C# a základních operací v .NET.

## Importovat jmenné prostory

Chcete-li začít, musíte importovat potřebné jmenné prostory. Zde je návod, jak je můžete zahrnout do svého projektu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Rozdělme si proces přidávání Bidi značek do dokumentu Wordu do jasných kroků. Každý krok vás provede kódem a jeho účelem.

## Krok 1: Nastavte svůj dokument

 Začněte vytvořením nové instance souboru`Document` třída a a`DocumentBuilder` pro přidání obsahu do dokumentu.

```csharp
// Cesta k adresáři vašich dokumentů
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Vytvořte dokument a přidejte obsah
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 V tomto kroku inicializujete nový dokument aplikace Word a nastavíte a`DocumentBuilder` pro usnadnění vkládání obsahu.

## Krok 2: Přidejte obsah do svého dokumentu

Dále do dokumentu přidejte nějaký text. Zde přidáme text v různých jazycích, abychom ilustrovali práci s textem Bidi.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Zde nejprve přidáme standardní anglickou frázi. Poté povolíme formátování textu Bidi pro následující text, který je napsán v hebrejštině a arabštině. To ukazuje, jak začlenit obousměrný text.

## Krok 3: Nakonfigurujte možnosti uložení pro značky Bidi

 Abyste zajistili správné uložení značek Bidi v dokumentu, musíte nakonfigurovat`TxtSaveOptions` a povolit`AddBidiMarks` volba.

```csharp
// Přidejte značky Bidi
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 V tomto kroku vytvoříme instanci`TxtSaveOptions` a nastavte`AddBidiMarks`majetek do`true`. Tím je zajištěno, že při ukládání dokumentu jako textového souboru budou zahrnuty značky Bidi.

## Závěr

Přidání značek Bidi do dokumentů aplikace Word může být zásadním krokem při práci s vícejazyčným obsahem, který zahrnuje jazyky s různými směry textu. S Aspose.Words pro .NET je tento proces přímočarý a efektivní. Dodržením výše uvedených kroků můžete zajistit, aby vaše dokumenty správně reprezentovaly text Bidi, čímž se zlepší čitelnost a přesnost.

## FAQ

### Co jsou značky Bidi a proč jsou důležité?
Bidi značky jsou speciální znaky používané k ovládání směru textu v dokumentech. Jsou nezbytné pro správné zobrazení jazyků, které se čtou zprava doleva, jako je arabština a hebrejština.

### Mohu použít Aspose.Words for .NET k řešení jiných typů problémů se směrováním textu?
Ano, Aspose.Words for .NET poskytuje komplexní podporu pro různé potřeby směrování textu a formátování, včetně jazyků psaných zprava doleva a zleva doprava.

### Je možné použít formátování Bidi pouze na určité části dokumentu?
Ano, formátování Bidi můžete podle potřeby použít na konkrétní odstavce nebo části dokumentu.

### V jakých formátech mohu uložit dokument se značkami Bidi?
V uvedeném příkladu je dokument uložen jako textový soubor. Aspose.Words však také podporuje ukládání dokumentů v různých formátech při zachování značek Bidi.

### Kde najdu další informace o Aspose.Words pro .NET?
 Můžete prozkoumat více o Aspose.Words pro .NET prostřednictvím[Aspose Documentation](https://reference.aspose.com/words/net/) a přístup k[Fórum podpory](https://forum.aspose.com/c/words/8) pro další pomoc.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

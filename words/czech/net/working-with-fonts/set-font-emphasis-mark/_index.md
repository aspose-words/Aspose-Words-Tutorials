---
title: Nastavte značku zvýraznění písma
linktitle: Nastavte značku zvýraznění písma
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit značky zvýraznění písma v dokumentech aplikace Word pomocí Aspose.Words for .NET pomocí tohoto podrobného průvodce krok za krokem. Ideální pro .NET vývojáře.
weight: 10
url: /cs/net/working-with-fonts/set-font-emphasis-mark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte značku zvýraznění písma

## Zavedení

dnešním tutoriálu se ponoříme do toho, jak nastavit značky zvýraznění písma v dokumentu aplikace Word pomocí Aspose.Words pro .NET. Ať už chcete podtrhnout konkrétní text jedinečným označením nebo jednoduše nechat vyniknout určitá slova, tento průvodce vám pomůže. Tak se připoutejte a můžeme začít!

## Předpoklady

Než se ponoříme do hrubších detailů, ujistěte se, že máte zaškrtnuté následující předpoklady:

-  Knihovna Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words for .NET. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Pracovní vývojové prostředí, jako je Visual Studio.
- .NET Framework: Ujistěte se, že máte nainstalované rozhraní .NET Framework.

## Importovat jmenné prostory

Chcete-li pracovat s Aspose.Words pro .NET, budete muset importovat potřebné jmenné prostory. Přidejte tyto v horní části souboru kódu:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si celý proces rozdělíme do jednoduchých kroků. Pečlivě proveďte každý krok a nastavte značky zvýraznění písma v dokumentu aplikace Word.

## Krok 1: Inicializujte Document a DocumentBuilder

Nejprve musíte inicializovat nový dokument a DocumentBuilder. Třída DocumentBuilder poskytuje metody pro vkládání textu a dalších prvků do dokumentu.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inicializujte nový dokument
Document document = new Document();

// Inicializujte DocumentBuilder s dokumentem
DocumentBuilder builder = new DocumentBuilder(document);
```

## Krok 2: Nastavte značku zvýraznění písma

S připraveným DocumentBuilderem můžete nyní nastavit značku zvýraznění písma. V tomto příkladu použijeme zvýrazněnou značku "UnderSolidCircle".

```csharp
// Nastavte značku zvýraznění písma
builder.Font.EmphasisMark = EmphasisMark.UnderSolidCircle;

// Napište text se značkou důrazu
builder.Write("Emphasis text");
builder.Writeln();
```

## Krok 3: Vymažte formátování a přidejte běžný text

Po nastavení značky zvýraznění možná budete chtít přidat nějaký běžný text bez jakéhokoli zvýraznění. K tomu je potřeba vymazat formátování.

```csharp
// Vymažte formátování písma
builder.Font.ClearFormatting();

// Napište běžný text
builder.Write("Simple text");
```

## Krok 4: Uložte dokument

Po přidání veškerého textu a formátování, které potřebujete, je posledním krokem uložení dokumentu. Zadejte cestu a název souboru, kam chcete dokument uložit.

```csharp
// Uložte dokument
document.Save(dataDir + "WorkingWithFonts.SetFontEmphasisMark.docx");
```

## Závěr

tady to máte! Nastavení značek zvýraznění písma v dokumentu aplikace Word pomocí Aspose.Words pro .NET je tak jednoduché. Pomocí několika řádků kódu můžete nechat svůj text vyniknout a dodat dokumentům profesionální vzhled. Neváhejte experimentovat s různými zdůrazňovacími značkami a styly, aby vyhovovaly vašim potřebám.

## FAQ

### Co jsou značky zvýraznění písma?

Značky zvýraznění písma jsou speciální symboly přidané do textu, aby vynikl. Mohou obsahovat tečky, kolečka a další dekorativní značky.

### Mohu s Aspose.Words pro .NET používat jiné zvýrazněné značky?

 Ano, Aspose.Words for .NET podporuje různé značky důrazu. Různé možnosti můžete prozkoumat odkazem na[dokumentace](https://reference.aspose.com/words/net/).

### Je Aspose.Words for .NET zdarma k použití?

 Aspose.Words for .NET vyžaduje licenci pro plnou funkčnost. Můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/) nebo zakoupit licenci[zde](https://purchase.aspose.com/buy).

### Jak mohu získat podporu pro Aspose.Words pro .NET?

 Můžete získat podporu od komunity Aspose a týmu podpory tím, že navštívíte jejich[fórum podpory](https://forum.aspose.com/c/words/8).

### Mohu používat Aspose.Words pro .NET s jinými frameworky .NET?

Ano, Aspose.Words for .NET je kompatibilní s různými .NET frameworky, včetně .NET Core a .NET 5/6.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

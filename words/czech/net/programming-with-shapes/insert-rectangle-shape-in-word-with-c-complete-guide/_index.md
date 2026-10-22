---
category: general
date: 2026-08-10
description: Vložte obdélníkový tvar do Wordu pomocí C#. Naučte se, jak skrýt tvar,
  jak skrýt tvar ve Wordu a jak vytvořit skrytý tvar pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: cs
lastmod: 2026-08-10
og_description: Vložte obdélníkový tvar do Wordu pomocí C#. Tento tutoriál vysvětluje,
  jak skrýt tvar, jak skrýt tvar ve Wordu a jak vytvořit skrytý tvar s kompletními
  ukázkami kódu.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Vložení obdélníkového tvaru do Wordu pomocí C# – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Vložení obdélníkového tvaru do Wordu pomocí C# – kompletní průvodce
url: /cs/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení obdélníkového tvaru ve Wordu pomocí C# – kompletní průvodce

Pokud potřebujete **vložit obdélníkový tvar** do dokumentu Word pomocí C#, tento průvodce vám ukáže přesné kroky. Také se naučíte **jak skrýt tvar**, aby se neobjevil v konečném souboru, což odpovídá častému dotazu **hide shape in Word** a ukazuje, jak **programově vytvořit skrytý tvar**.

Tutoriál pokrývá vše od nastavení Aspose.Words SDK až po ověření, že je tvar skrytý. Na konci článku budete mít znovupoužitelný úryvek kódu, který můžete vložit do libovolného projektu .NET.

## Požadavky

- .NET 6.0 nebo novější nainstalováno (kód také funguje s .NET Framework 4.6+)
- Platná licence Aspose.Words pro .NET nebo dočasný evaluační klíč
- Visual Studio 2022 (nebo jakékoli IDE podporující C#)
- Základní znalost syntaxe C# a Document Object Model (DOM) souborů Word

Kromě `Aspose.Words` nejsou vyžadovány žádné další balíčky NuGet.

## Krok 1: Vytvořte nový prázdný dokument a DocumentBuilder

Prvním krokem je vytvořit instanci objektu `Document`. `DocumentBuilder` poskytuje pohodlné API pro vkládání obsahu, jako jsou tvary, odstavce a tabulky.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Proč je to důležité:** `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` udržuje kurzor, který sleduje, kam bude umístěn další prvek. Inicializace obou objektů je základem pro jakýkoli úkol automatizace Wordu.

## Krok 2: Vložte obdélníkový tvar

Nyní vložíte obdélník. Metoda `InsertShape` vyžaduje typ tvaru a jeho rozměry v bodech (1 bod ≈ 1/72 palce). Velikost **200 × 100 bodů** vytvoří obdélník přibližně 2,78 × 1,39 palce.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Proč je to důležité:** Objekt `Shape`, který získáte, je plně konfigurovatelný – můžete měnit barvu, okraj, text i viditelnost před uložením dokumentu.

## Krok 3: Skryjte tvar

Aby se obdélník nezobrazoval ani netiskl, nastavte jeho vlastnost `Hidden` na `true`. Tato vlastnost přímo odpovídá atributu Wordu „Hidden“, který Word respektuje jak v režimu zobrazení, tak tisku.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Proč je to důležité:** Nastavení `Hidden` je standardní způsob, jak **hide shape in Word** bez odstranění tvaru ze struktury dokumentu. Tvar zůstává přístupný kódu, což umožňuje pozdější manipulace, jako je podmíněné formátování nebo přepínání viditelnosti na základě dat.

## Krok 4: Uložte dokument

Nakonec uložte dokument na disk. Vyberte libovolnou složku; příklad používá zástupnou cestu, kterou byste měli nahradit skutečnou.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Proč je to důležité:** Uložení dokončí soubor a zapíše příznak skrytí do podkladového Open XML. Když otevřete dokument v Microsoft Word, obdélník bude neviditelný, což potvrzuje, že jste úspěšně **created hidden shape**.

## Krok 5: Ověřte skrytý tvar

Otevřete vygenerovaný soubor `HiddenShape.docx` v Microsoft Word:

1. Přejděte na **File → Options → Display** a ujistěte se, že *„Show hidden text“* je **odškrtnuto**.  
2. Obdélník by neměl být na žádné stránce viditelný.  
3. Pro dvojí kontrolu povolte *„Show hidden text“*; obdélník se objeví s jemným tečkovaným obrysem, což dokazuje, že tvar existuje, ale je skrytý.

Pokud je obdélník stále viditelný, ověřte, že jste soubor uložili po nastavení `Hidden = true` a že otevíráte správný soubor.

## Kompletní spustitelný příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit přímo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Očekávaný výstup:** Konzole vypíše cestu k souboru a krátkou připomínku. Když je soubor otevřen ve Wordu, obdélník je neviditelný, pokud není povolený skrytý text.

## Časté otázky a okrajové případy

### Mohu skrýt pouze obrys, ale nechat výplň viditelnou?

Ano. Místo nastavení `Hidden = true` můžete nastavit `rectangle.LineFormat.Visible = false`, čímž skryjete okraj a ponecháte barvu výplně. Jedná se o variantu **how to hide shape**, která zachovává část vizuálního vzhledu.

### Funguje příznak skrytí ve starších verzích Wordu (2003, 2007)?

Atribut hidden je součástí specifikace Open XML zavedené s Word 2007. Dokumenty uložené ve starším binárním formátu `.doc` příznak neuchovají. Pro podporu starších formátů uložte dokument jako `.docx` a v případě potřeby jej později převedete pomocí `SaveFormat.Doc` z Aspose.Words.

### Co když potřebuji najednou skrýt více tvarů?

Procházejte kolekci `Document.GetChildNodes(NodeType.Shape, true)` a nastavte `Hidden = true` u každého tvaru, který splňuje vaše kritéria (např. konkrétní `ShapeType` nebo vlastní hodnotu `AlternativeText`).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Má skrytí tvarů dopad na výkon?

Příznak hidden přidává malý XML atribut; nemá vliv na rychlost vykreslování. Nicméně velmi velký počet skrytých objektů může mírně zvýšit velikost souboru. Odstraňte tvary, které nepotřebujete, aby byl dokument úsporný.

## Tipy a osvědčené postupy

- **Dejte tvaru smysluplný název** pomocí `rectangle.Name = "MyHiddenRectangle"`; to pomůže při pozdějším vyhledávání tvaru v DOM.
- **Nastavte `AlternativeText`** na vlastní značku (např. `"HiddenShape"`). To vám umožní najít tvar bez spoléhání se na jeho index.
- **Zabalte kód do bloku try‑catch** pro elegantní ošetření chyb licencování nebo I/O výjimek.
- **Uvolněte objekt Document** po uložení, pokud zpracováváte mnoho souborů v cyklu, aby se uvolnily neřízené prostředky: `document.Dispose();`.

## Závěr

Nyní víte, jak **insert rectangle shape** do dokumentu Word pomocí C#, jak **hide shape in Word**, a jak **create hidden shape**, který zůstává součástí struktury dokumentu, ale je neviditelný pro koncové uživatele. Kompletní, spustitelný příklad demonstruje celý postup, od vytvoření dokumentu až po ověření.

Dále můžete zkoumat **how to hide shape** na základě vstupu uživatele nebo kombinovat skryté tvary s ovládacími prvky obsahu pro dynamické generování dokumentů. Stejnou techniku můžete použít i na jiné typy tvarů, jako jsou elipsy, šipky nebo vlastní kresby.

Neváhejte experimentovat s různými rozměry, barvami a nastavením viditelnosti. Pokud narazíte na problémy, projděte si výše uvedené kroky nebo si prostudujte dokumentaci Aspose.Words pro podrobnější informace o API. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvoření obdélníkového tvaru ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Vytvoření obdélníkového tvaru ve Wordu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutoriál stínování tvaru Aspose.Words – Přidání stínu k tvaru ve Wordu v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
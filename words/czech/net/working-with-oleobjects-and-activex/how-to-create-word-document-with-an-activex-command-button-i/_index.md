---
category: general
date: 2026-09-05
description: Vytvořte dokument Word pomocí Aspose.Words C# a naučte se, jak vložit
  ActiveX příkazové tlačítko, nastavit velikost tlačítka a přidat interaktivní funkčnost
  tlačítka.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: cs
lastmod: 2026-09-05
og_description: Vytvořte dokument Word v C# a vložte tlačítko ActiveX. Tento tutoriál
  ukazuje, jak nastavit velikost tlačítka a přidat interaktivní funkce tlačítka.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Vytvořte Word dokument s ActiveX tlačítkem v C# – průvodce krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Jak vytvořit dokument Word s tlačítkem ActiveX v C#
url: /cs/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit Word dokument s ActiveX tlačítkem příkazu v C#

Pokud potřebujete **vytvořit Word dokument** programově a vložit klikací UI prvek, tento průvodce vám přesně ukáže jak. Pomocí Aspose.Words pro .NET můžete **vytvořit Word dokument**, **přidat tlačítko příkazu** a řídit jeho vzhled—bez otevření Microsoft Word.

Naučíte se **jak vložit ActiveX** ovládací prvky, **nastavit velikost tlačítka** a nechat tlačítko fungovat jako interaktivní UI komponenta. Předchozí zkušenost s COM nebo VBA není vyžadována; stačí .NET vývojové prostředí a knihovna Aspose.Words.

## Co dosáhnete

* **Vytvořit Word dokument** od nuly pomocí C#.
* **Vložit ActiveX tlačítko příkazu** (klasické ovládání “Click Me”).
* **Nastavit velikost tlačítka** a přesně umístit.
* Volitelně přidat jednoduchou **interactive button** logiku (např. placeholder makra).
* Uložit soubor jako `.docx`, který lze otevřít v Microsoft Word nebo v libovolném kompatibilním prohlížeči.

### Požadavky

| Požadavek | Důvod |
|-------------|--------|
| .NET 6.0 nebo novější | Poskytuje runtime pro C# kód. |
| Aspose.Words pro .NET (nejnovější verze) | Poskytuje API `Document`, `DocumentBuilder` a `Forms2OleControl` používané v příkladu. |
| Visual Studio 2022 (nebo jakékoli C# IDE) | Usnadňuje kompilaci a spuštění ukázky. |
| Základní znalost C# | Potřebná pro pochopení toku kódu. |

> **Tip:** Pokud používáte zkušební verzi Aspose.Words, ujistěte se, že nastavíte licenci před spuštěním kódu, aby se zabránilo vodoznakům z hodnocení.

## Jak vytvořit Word dokument – celkový pracovní postup

Proces se skládá ze čtyř logických kroků:

1. **Inicializovat nový dokument** a `DocumentBuilder` pro jeho úpravu.  
2. **Vložit ActiveX tlačítko příkazu** pomocí `InsertForms2OleControl`.  
3. **Konfigurovat tlačítko** – popisek, velikost a pozice.  
4. **Uložit** dokument na disk.

Každý krok je vysvětlen v samostatné sekci níže.

![Word dokument s ActiveX tlačítkem](/images/activex-button.png "Snímek obrazovky Word dokumentu, který obsahuje ActiveX tlačítko vytvořené v C#")

## Jak vložit ActiveX tlačítko příkazu

Část **jak vložit activex** začíná metodou `InsertForms2OleControl`. Tato metoda vytváří COM‑založený ovládací prvek, který Word považuje za ActiveX objekt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Proč to funguje:** `OleControlType.CommandButton` říká Aspose.Words, aby vytvořil klasické VB‑stylové tlačítko. Velikost a umístění jsou vyjádřeny v bodech (1 bod = 1/72 palce), což poskytuje přesnou kontrolu nad rozvržením.

## Jak přidat tlačítko příkazu a nastavit velikost tlačítka

Po vložení ovládacího prvku můžete upravit jeho vizuální vlastnosti. Krok **add command button** také zahrnuje **set button size**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Vysvětlení:**  

* `Caption` je popisek zobrazený na tlačítku.  
* `Width` a `Height` vám umožňují **nastavit velikost tlačítka** po počátečním vložení—užitečné, když velikost závisí na datech za běhu.  
* `Left` a `Top` přemístí ovládací prvek bez nutnosti znovu vytvářet dokument.

> **Běžná chyba:** Zapomenutí použít body místo pixelů způsobí, že tlačítko bude příliš malé nebo příliš velké. Vždy převádějte hodnoty pixelů (`px * 72 / DPI`), pokud vycházíte z měření na obrazovce.

## Jak přidat interaktivní tlačítko (volitelné)

ActiveX tlačítko může spustit makro po kliknutí, ale vkládání VBA kódu z C# není v rámci čistého workflow Aspose.Words. Místo toho můžete přidat vlastnost placeholder, kterou Word rozpozná jako název makra.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Když uživatel otevře vygenerovaný `.docx` ve Wordu, kliknutí na tlačítko se pokusí spustit `MyMacroName`. Pokud makro neexistuje, Word uživatele vyzve k jeho vytvoření.

**Proč byste to mohli použít:** Pro firemní formuláře, kde makro vyplňuje pole, C# kód potřebuje pouze umístit tlačítko; logika makra žije v VBA projektu dokumentu.

## Uložte dokument a ověřte výsledek

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Očekávaný výstup:** Otevření `CommandButton.docx` v Microsoft Word zobrazí tlačítko s popiskem **Click Me** umístěné 100 bodů od levého okraje a 120 bodů od horního okraje. Rozměry tlačítka jsou **200 bodů × 80 bodů**. Kliknutí na tlačítko spustí placeholder makra (pokud je přítomen).

## Kompletní funkční příklad

Níže je kompletní spustitelný program, který spojuje vše dohromady. Zkopírujte jej do nového projektu Console App, přidejte NuGet balíček Aspose.Words a spusťte.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Spusťte program, poté otevřete vygenerovaný soubor. Uvidíte **interaktivní tlačítko** připravené k dalším úpravám.

## Často kladené otázky

| Otázka | Odpověď |
|----------|--------|
| **Funguje to s .NET Core?** | Ano. Aspose.Words podporuje .NET Standard, takže stejný kód běží na .NET 5/6/7. |
| **Mohu použít jiné ActiveX ovládací prvky (např. CheckBox)?** | Rozhodně. Nahraďte `OleControlType.CommandButton` za `OleControlType.CheckBox`, `OleControlType.OptionButton` atd. |
| **Co když potřebuji větší tlačítko na na šířkové stránce?** | Upravte vlastnosti `Width`, `Height`, `Left` a `Top` úměrně. Pamatujte, že body zůstávají stejné bez ohledu na orientaci stránky. |
| **Je makro vyžadováno, aby bylo tlačítko klikatelné?** | Ne. Tlačítko je plně funkční jako UI prvek; makro pouze přidává vlastní chování po kliknutí. |

## Závěr

Nyní víte, jak **vytvořit Word dokument** pomocí Aspose.Words, **přidat tlačítko příkazu**, **nastavit velikost tlačítka** a volitelně propojit tlačítko s makrem pro chování **add interactive button**. Tento přístup vám umožní automatizovat tvorbu formulářů, generovat dynamické zprávy nebo vytvářet prototypy UI založené na Wordu přímo z C#.

Dále můžete zkoumat:

* **Jak vložit ActiveX zaškrtávací políčka** pro průzkumné formuláře.  
* **Jak přidat bohatý textový obsah** kolem tlačítka pomocí `DocumentBuilder`.  
* **Jak chránit dokument** a přitom zachovat funkčnost tlačítka.  

Neváhejte experimentovat s různými typy ovládacích prvků, velikostmi a názvy makr pro vaše konkrétní scénáře. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit Word dokument s Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Vložit vložený obrázek do Word dokumentu pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Vytvořit Word dokument s tabulkou pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
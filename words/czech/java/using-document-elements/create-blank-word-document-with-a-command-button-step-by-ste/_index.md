---
category: general
date: 2026-08-04
description: Vytvořte prázdný dokument Word a vložte příkazové tlačítko pomocí Aspose.Words.
  Naučte se nastavit velikost tlačítka a přidat klikatelné tlačítko v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: cs
lastmod: 2026-08-04
og_description: Vytvořte prázdný dokument Word pomocí Aspose.Words a vložte příkazové
  tlačítko. Tento návod ukazuje, jak nastavit velikost tlačítka, přidat klikatelné
  tlačítko a uložit soubor.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Vytvořte prázdný dokument Word a přidejte příkazové tlačítko – kompletní
  C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Vytvořte prázdný dokument Word pomocí tlačítka příkazu – krok za krokem
url: /cs/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření prázdného dokumentu Word s tlačítkem příkazu – krok za krokem průvodce

Pokud potřebujete **vytvořit prázdný dokument Word**, který obsahuje interaktivní tlačítko, tento tutoriál vám ukáže, jak to provést pomocí Aspose.Words pro .NET. Naučíte se **vložit tlačítko příkazu**, upravit jeho vzhled a učinit ho kliknutelným – vše během několika řádků C#.

Průvodce pokrývá vše od nastavení projektu až po uložení finálního souboru, takže můžete kompletní řešení zkopírovat a vložit do své vlastní aplikace. Během cesty také vysvětlíme, jak **přidat klikatelné tlačítko**, **nastavit velikost tlačítka** a **programově vytvořit tlačítko příkazu**.

## Prerequisites

Než začnete, ujistěte se, že máte:

* .NET 6.0 SDK nebo novější nainstalovaný.
* Visual Studio 2022 (nebo jakékoli IDE podporující .NET).
* NuGet balíček Aspose.Words pro .NET (`Aspose.Words` verze 23.12 nebo novější).
* Základní znalosti C# a objektově orientovaného programování.

Žádné další Office interop sestavy nejsou potřeba, protože Aspose.Words funguje zcela nezávisle na Microsoft Word.

## Step 1: Set up the .NET project

Vytvořte konzolovou aplikaci, která bude hostovat kód pro automatizaci Wordu.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Tento příkaz vytvoří novou složku `WordButtonDemo` s připraveným souborem `Program.cs` a přidá knihovnu Aspose.Words.

## Step 2: Create blank word document

Prvním krokem je **vytvořit prázdný dokument Word**. Aspose.Words poskytuje třídu `Document`, která představuje prázdný soubor Word přímo z krabice.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Vytvoření prázdného dokumentu vám poskytne čisté plátno, na které můžete přidávat odstavce, tabulky nebo, v tomto případě, OLE tlačítko příkazu.

## Step 3: Initialize DocumentBuilder

`DocumentBuilder` je pomocník, který vám umožní vkládat obsah do dokumentu. Musíte jej připojit k dokumentu, který jste právě vytvořili.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder udržuje aktuální pozici kurzoru, takže jakékoli následné vkládání proběhne přesně tam, kde chcete.

## Step 4: Insert command button

Nyní **vložíme tlačítko příkazu** (OLE `Forms2OleControl`) do dokumentu. Metoda `InsertForms2OleControl` vyžaduje tři argumenty:

1. ProgID OLE ovládacího prvku – `"CommandButton"` pro standardní tlačítko.
2. `Rectangle`, který definuje **nastavení velikosti tlačítka** a jeho pozici.
3. Popisek, který se zobrazí na tlačítku.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Když je dokument otevřen ve Wordu, tlačítko se chová jako jakýkoli nativní formulářový ovládací prvek – můžete na něj kliknout a Word spustí přiřazené makro (pokud existuje). Tím je splněna požadavek **přidat klikatelné tlačítko**.

### Why use Forms2OleControl?

`Forms2OleControl` vkládá OLE objekt přímo do souboru DOCX, zachovává vlastnosti ovládacího prvku bez potřeby Word Interop sestavy. Je to nejspolehlivější způsob, jak **vytvořit tlačítko příkazu**, které funguje napříč verzemi Wordu.

## Step 5: Customize the button (optional)

Možná budete chtít **nastavit velikost tlačítka** přesněji nebo změnit další vlastnosti, jako je písmo či barva pozadí. Aspose.Words umožňuje přístup k podkladovému OLE objektu, což umožňuje další úpravy.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Pokud potřebujete jinou velikost, jednoduše upravte hodnoty `Rectangle` v kroku 4. Souřadnice jsou měřeny v bodech (1 pt = 1/72 palce), takže `120` odpovídá přibližně 1,67 palce na šířku.

## Step 6: Save the document

Nakonec dokument zapíšeme na disk. Výsledný soubor obsahuje **prázdný dokument Word** s plně funkčním tlačítkem příkazu.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Když otevřete `CommandButtonDemo.docx` v Microsoft Word, uvidíte tlačítko s popiskem „Click Me“. Kliknutí na tlačítko zobrazí výchozí dialog makra, pokud k němu nepřipojíte vlastní makro.

## Complete source code

Níže je celý program, který můžete zkopírovat do `Program.cs`. Obsahuje všechny výše popsané kroky a kompiluje se bez úprav.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Expected result

Spuštěním programu vznikne soubor `CommandButtonDemo.docx`. Otevřením souboru ve Wordu se zobrazí:

* Jedna stránka obsahující tlačítko s popiskem **Click Me**.
* Tlačítko respektuje **nastavení velikosti tlačítka** (120 × 30 bodů).
* Kliknutí na tlačítko spustí výchozí chování tlačítka ve Wordu, což potvrzuje úspěšné provedení operace **přidat klikatelné tlačítko**.

## Common questions and edge cases

| Otázka | Odpověď |
|----------|--------|
| **Funguje to i s .doc soubory?** | Ano. Změňte příponu souboru v `doc.Save("file.doc")`. OLE ovládací prvek je uložen i v legacy binárním formátu. |
| **Co když potřebuji více tlačítek?** | Volajte `InsertForms2OleControl` opakovaně a upravujte `Rectangle` pro každé nové tlačítko, aby nedocházelo k překrytí. |
| **Mohu k tlačítku připojit makro?** | Tlačítko samo neobsahuje kód makra. Makro musíte přidat do dokumentu ručně nebo přes kolekci `Modules` objektu `Document`. |
| **Je tlačítko viditelné při exportu do PDF?** | Při exportu DOCX do PDF pomocí Aspose.Words je tlačítko vykresleno jako statický obrázek, nikoli jako interaktivní ovládací prvek. |
| **Jaké verze Wordu jsou podporovány?** | OLE tlačítko příkazu funguje ve Word 2007 a novějších, protože vychází ze standardní specifikace Forms2.0. |

## Conclusion

Nyní víte, jak **vytvořit prázdný dokument Word**, **vložit tlačítko příkazu**, **přidat klikatelné tlačítko** a **nastavit velikost tlačítka** pomocí Aspose.Words pro .NET. Kompletní příklad demonstruje workflow **vytvořit tlačítko příkazu** od začátku až po konec a poskytuje solidní základ pro pokročilejší úlohy automatizace Wordu.

## Next steps

* Prozkoumejte další OLE ovládací prvky (např. `CheckBox`, `ListBox`) změnou ProgID v `InsertForms2OleControl`.
* Spojte tlačítko s VBA makrem, aby po kliknutí provedlo vlastní akce.
* Použijte `DocumentBuilder` od Aspose.Words k přidání dalšího obsahu, jako jsou tabulky, obrázky nebo poznámky pod čarou, před vložením tlačítka.
* Experimentujte s hodnotami **nastavení velikosti tlačítka**, aby odpovídaly požadavkům rozvržení vašeho dokumentu.

Šťastné programování a užívejte si tvorbu bohatších dokumentů Word s interaktivními ovládacími prvky!

## What Should You Learn Next?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným krok‑za‑krokem vysvětlením, které vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
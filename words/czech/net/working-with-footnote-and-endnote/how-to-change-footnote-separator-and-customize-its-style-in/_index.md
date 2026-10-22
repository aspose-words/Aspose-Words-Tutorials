---
category: general
date: 2026-10-13
description: Jak změnit oddělovač poznámky pod čarou ve Word dokumentu pomocí Aspose.Words.
  Naučte se programově změnit barvu písma ve Word dokumentu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: cs
lastmod: 2026-10-13
og_description: Jak změnit oddělovač poznámek pod čarou v dokumentu Word pomocí Aspose.Words.
  Tento tutoriál vám ukáže, jak změnit barvu písma v dokumentu Word pomocí C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Jak změnit oddělovač poznámky pod čarou v dokumentu Word – krok za krokem
  průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Jak změnit oddělovač poznámek pod čarou a přizpůsobit jeho styl v dokumentu
  Word
url: /cs/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak změnit oddělovač poznámky pod čarou a přizpůsobit jeho styl ve Word dokumentu

Pokud potřebujete **how to change footnote separator** ve Word dokumentu, tento průvodce vám poskytne kompletní, připravené řešení. Pomocí Aspose.Words pro .NET můžete také **change font color in Word document** prvky, jako jsou oddělovače poznámek pod čarou a koncových poznámek, aby výsledný soubor odpovídal vaší značce nebo stylové příručce.

Autoři dokumentů se často ptají: *Proč vypadá výchozí oddělovač poznámky pod čarou obyčejně, a jak ho mohu zvýraznit?* Odpověď je přímo přistoupit k objektům odstavců oddělovače, upravit jejich vlastnosti písma a výsledek uložit. Tento tutoriál vás provede každým krokem, od načtení souboru .docx až po uložení stylovaného výstupu.

Naučíte se, jak:

* Načíst Word soubor, který již obsahuje poznámky pod čarou a koncové poznámky.  
* Najít odstavce oddělovačů poznámek pod čarou a koncových poznámek.  
* Změnit barvu písma každého oddělovače (červená pro poznámky pod čarou, modrá pro koncové poznámky).  
* Uložit upravený dokument bez ztráty jakéhokoli existujícího obsahu.

K provedení nejsou potřeba žádné externí nástroje kromě knihovny Aspose.Words a .NET vývojového prostředí.

## Požadavky

* .NET 6.0 SDK nebo novější (kód také funguje s .NET Framework 4.7+).  
* Visual Studio 2022, Rider nebo jakýkoli C# editor, který preferujete.  
* Aspose.Words for .NET NuGet balíček (`Aspose.Words`).  
* Ukázkový Word soubor (`Footnotes.docx`), který obsahuje alespoň jednu poznámku pod čarou a jednu koncovou poznámku.

> **Pro tip:** Pokud nemáte ukázkový soubor, vytvořte nový Word dokument, vložte poznámku pod čarou (`References → Insert Footnote`) a koncovou poznámku (`References → Insert Endnote`). Uložte jej jako `Footnotes.docx` do složky, na kterou můžete odkazovat z kódu.

## Jak změnit oddělovač poznámky pod čarou pomocí Aspose.Words

Jádrem úkolu je získat speciální odstavce, které Aspose.Words vystavuje jako *separator* uzly. Tyto uzly jsou typu `Paragraph` a lze je formátovat jako jakýkoli jiný odstavec.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Proč je každý řádek důležitý

* **Loading the document** (`new Document`) vám poskytuje paměťovou reprezentaci, kterou může Aspose.Words manipulovat.  
* **`GetChild` with `ParagraphNodeType.FootnoteSeparator`** vrací skrytý odstavec, který Word používá k vykreslení čáry oddělující poznámky pod čarou od hlavního textu. Stejná metoda funguje i pro oddělovač koncových poznámek.  
* **Changing `Font.Color`** přímo ovlivňuje vzhled čáry, protože Word vykresluje oddělovač jako odstavec s jediným znakem “‑”. Nastavení barvy na `Color.Red` (nebo jakoukoli `System.Drawing.Color`) aktualizuje vizuální styl.  
* **Saving** zapíše změny zpět do souboru .docx, který může otevřít jakýkoli textový procesor.

### Očekávaný výstup

Když otevřete `FootnoteSeparatorsStyled.docx` v Microsoft Word:

* Čára oddělovače poznámky pod čarou se zobrazí **červeně**.  
* Čára oddělovače koncové poznámky se zobrazí **modře**.  

Veškerý původní obsah poznámek pod čarou i koncových poznámek zůstane nedotčen.

## Změna barvy písma ve Word dokumentu pomocí C#

Operace demonstrovaná výše je konkrétním případem širší schopnosti: **change font color in Word document** programově. Jakmile máte `Paragraph`, `Run` nebo jakýkoli `Node`, který obsahuje text, můžete upravit jeho vlastnost `Font.Color`.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Tento úryvek prochází každý odstavec, kontroluje, zda používá styl `Heading 1`, a nastavuje barvu písma.  
* Podmínku můžete upravit tak, aby cílila na poznámky pod čarou, tabulky nebo jakýkoli jiný typ uzlu.

## Postup krok za krokem

### 1. Instalace Aspose.Words

Otevřete terminál ve složce projektu a spusťte:

```bash
dotnet add package Aspose.Words
```

Balíček obsahuje všechny sestavy potřebné pro kód uvedený výše.

### 2. Připravte vstupní soubor

Umístěte `Footnotes.docx` do známého adresáře (např. `C:\Docs`). Ujistěte se, že soubor obsahuje alespoň jednu poznámku pod čarou a jednu koncovou poznámku, aby existovaly uzly oddělovačů.

### 3. Napište C# program

Vytvořte nový konzolový projekt (`dotnet new console -n FootnoteStyler`) a nahraďte vygenerovaný `Program.cs` úplným blokem kódu ze sekce **Jak změnit oddělovač poznámky pod čarou**. Nezapomeňte upravit cesty k souborům tak, aby odpovídaly vašemu prostředí.

### 4. Spusťte a ověřte

Spusťte program:

```bash
dotnet run
```

Po dokončení běhu otevřete `FootnoteSeparatorsStyled.docx`. Měli byste vidět červené a modré čáry oddělovačů, jak je popsáno.

### 5. Rozšíření řešení

* **Different colors:** Použijte libovolnou hodnotu `System.Drawing.Color`, např. `Color.FromArgb(255, 128, 0)` pro oranžovou.  
* **Custom line style:** Místo změny barvy můžete upravit vlastnosti `ParagraphFormat`, jako jsou `LineSpacing`, `Shading`, nebo dokonce nahradit znak oddělovače.  
* **Multiple documents:** Zabalte logiku do metody, která přijímá vstupní a výstupní cesty, a poté ji volejte v cyklu pro hromadné zpracování.

## Časté problémy a jak se jim vyhnout

| Symptom | Příčina | Oprava |
|---------|----------|--------|
| `GetChild` returns `null` | Zdrojový dokument nemá oddělovač poznámky pod čarou/koncové poznámky (např. žádné poznámky pod čarou). | Přidejte alespoň jednu poznámku pod čarou nebo koncovou poznámku, nebo před přístupem k `Font` zkontrolujte, zda není `null`. |
| Color change not visible | Oddělovač je v některých verzích Wordu vykreslen jako čára místo znaku. | Nastavte `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` a `ParagraphFormat.LineSpacing = 1`, aby se vynutil viditelný znak. |
| Runtime exception `FileNotFoundException` | Nesprávná cesta k souboru. | Používejte absolutní cesty nebo `Path.Combine` s `Environment.CurrentDirectory`. |

## Kompletní, spustitelný příklad

Níže je celý program, který můžete zkopírovat a vložit do konzolové aplikace. Obsahuje ošetření chyb a komentáře vysvětlující každou operaci.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Spuštěním tohoto programu vznikne Word soubor, kde je čára oddělovače poznámky pod čarou červená a čára oddělovače koncové poznámky modrá, čímž splňuje požadavek **how to change footnote separator** a zároveň demonstruje **change font color in word document**.

## Závěr

Nyní víte, **jak změnit oddělovač poznámky pod čarou** ve Word dokumentu pomocí Aspose.Words pro .NET a jak **změnit barvu písma ve Word dokumentu** programově. Přístup je:

1. Načtěte dokument.  
2. Získejte skryté odstavce oddělovačů.  
3. Nastavte jejich vlastnost `Font.Color`.  
4. Uložte upravený soubor.

Od této chvíle můžete zkoumat pokročilejší stylování – úpravu tloušťky čáry, aplikaci různých písem nebo automatizaci procesu napříč mnoha soubory. Ovládnutí těchto technik vám poskytne detailní kontrolu nad vzhledem Word dokumentů přímo z C# kódu.

---


## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-02-21
description: Skrýt řádek v tabulce pomocí C# a Aspose.Words. Naučte se, jak skrýt
  řádek, jak skrýt řádek ve Wordu a jak rychle a bezpečně odstranit řádek z tabulky.
draft: false
keywords:
- hide row in table
- how to hide row
- remove row from table
- hide row in word
- hide row c#
language: cs
og_description: Skrýt řádek v tabulce pomocí C# a Aspose.Words. Tento návod ukazuje,
  jak skrýt řádek, odstranit řádek z tabulky a skrýt řádek ve Wordových dokumentech.
og_title: Skrytí řádku v tabulce pomocí C# – rychlá, spolehlivá metoda
tags:
- C#
- Aspose.Words
- Word Automation
title: Skrytí řádku v tabulce pomocí C# – Jednoduchý návod na odstraňování řádků v
  tabulce
url: /cs/net/programming-with-tables/hide-row-in-table-with-c-simple-guide-to-removing-table-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skrytí řádku v tabulce – Kompletní tutoriál C#

Už jste někdy potřebovali **hide row in table** při programovém generování dokumentu Word? Nejste jediní — vývojáři se neustále ptají, *how to hide row* bez narušení rozvržení. Dobrá zpráva? S několika řádky C# a výkonnou knihovnou Aspose.Words můžete řádek skrýt, čímž jej efektivně odstraníte z finálního výstupu, a udržet kód přehledný.

V tomto průvodci projdeme celý proces: načtení `.docx`, výběr konkrétního řádku, nastavení jeho vlastnosti `Hidden` a uložení výsledku. Na konci přesně budete vědět, jak hide row in Word, jak remove row from table, pokud dáváte přednost smazání, a budete mít připravený úryvek kódu, který můžete vložit do libovolného .NET projektu. Nejsou potřeba žádné externí odkazy — jen kód a jasná vysvětlení.

**Co získáte**  
- Podrobný průvodce krok za krokem C# API.  
- Úplný, spustitelný kód (včetně importů).  
- Tipy pro okrajové případy, jako jsou skryté řádky ve sloučených buňkách.  
- Profesionální tipy, kdy použít *hide row* vs. *remove row from table*.

> **Předpoklad:** Visual Studio (nebo jakékoli C# IDE) a NuGet balíček Aspose.Words pro .NET (verze 23.9 nebo novější). Pokud jste noví v Aspose.Words, knihovna je čistě spravované řešení — není potřeba instalace Office.

---

## Skrytí řádku v tabulce – Krok za krokem implementace

Níže je kompletní, samostatný příklad. Ukazuje **primary** úkol — *hide row in table* — a také jak můžete *remove row from table*, pokud se rozhodnete řádek smazat.

![Hide row in table example](hide-row-in-table.png "Screenshot showing a Word table with the third row hidden")

### 1. Načtení zdrojového dokumentu  

Nejprve musíme načíst soubor Word do paměti. Třída `Document` představuje celý soubor.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*Proč je to důležité:* Načtení dokumentu vám poskytuje přístup k sekcím, tělům a tabulkám. Bez tohoto kroku nemůžete řádky vůbec manipulovat.

### 2. Vyhledání požadované tabulky  

Pro jednoduchost získáme první tabulku v první sekci, ale můžete vyhledávat podle indexu, názvu nebo dokonce obsahu.

```csharp
// Step 2: Get the first table in the document body
Table table = doc.FirstSection.Body.Tables[0];
```

> **Tip:** Pokud má váš dokument více tabulek, iterujte `doc.GetChildNodes(NodeType.Table, true)` a vyberte tu, kterou potřebujete.

### 3. Vyberte řádek, který chcete skrýt  

Zde cílíme na třetí řádek (index od nuly `2`). Můžete také použít `Rows.Count` k ověření, že index existuje.

```csharp
// Step 3: Choose the row you want to hide (third row, index 2)
Row rowToHide = table.Rows[2];
```

*Proč je to důležité:* Výběr správného řádku je jádrem **how to hide row**. Špatný index skryje nesprávný obsah.

### 4. Skrytí vybraného řádku  

Nastavení `Hidden = true` říká Aspose.Words, aby při ukládání dokumentu řádek vynechal. Řádek stále existuje v objektovém modelu, takže jej můžete později odkrýt, pokud bude potřeba.

```csharp
// Step 4: Hide the selected row – it will be omitted from the output
rowToHide.Hidden = true;
```

> **Pro tip:** Pokud opravdu chcete *remove row from table* místo skrytí, zavolejte `table.Rows.Remove(rowToHide);`. Skrytí zachovává metadata řádku, což může být užitečné pro podmíněné formátování.

### 5. Uložení aktualizovaného dokumentu  

Nakonec zapíšete změny zpět na disk.

```csharp
// Step 5: Save the document with the hidden row applied
doc.Save(@"C:\MyDocs\output.docx");
```

Když otevřete `output.docx` ve Wordu, třetí řádek bude neviditelný — přesně to, co **hide row in word** znamená v praxi.

---

## Jak skrýt řádek – Běžné varianty a okrajové případy

### Skrytí více řádků  

Pokud potřebujete skrýt několik řádků, projděte kolekci ve smyčce:

```csharp
int[] rowsToHide = { 1, 3, 5 }; // zero‑based indexes
foreach (int i in rowsToHide)
{
    table.Rows[i].Hidden = true;
}
```

### Práce se sloučenými buňkami  

Skrytý řádek, který obsahuje vertikálně sloučenou buňku, může způsobit varování rozvržení. Bezpečný postup je rozdělit sloučení před skrytím:

```csharp
Cell mergedCell = rowToHide.Cells[0];
if (mergedCell.CellFormat.VerticalMerge != CellMerge.None)
{
    // Break the merge to avoid Word warnings
    mergedCell.CellFormat.VerticalMerge = CellMerge.None;
}
rowToHide.Hidden = true;
```

### Kompatibilita se staršími verzemi Wordu  

Aspose.Words zapisuje atribut `w:hideMark`, který rozumí Word 2007+ a LibreOffice. Pokud cílíte na Word 97‑2003 (`.doc`), skrytý řádek bude stále vynechán, ale složité tabulky se mohou vykreslovat odlišně. Pro předvídatelné výsledky používejte `.docx`.

### Kdy *Hide Row* vs. *Remove Row from Table*  

- **Hide Row** – Zachovat řádek pro pozdější odkrývání, zachovat výšku řádku pro výpočty zalomení stránky.  
- **Remove Row** – Snížit velikost souboru, trvale smazat data. Použijte `table.Rows.Remove(row)`, pokud jste si jisti, že řádek už nebude potřeba.

---

## Profesionální tipy a úskalí

- **Pro tip:** Vždy zkontrolujte `table.Rows.Count` před přístupem k indexu, abyste se vyhnuli `ArgumentOutOfRangeException`.  
- **Dejte pozor na:** Skryté řádky stále participují na výpočtech tabulky, jako je celková výška. Pokud zaznamenáte neočekávané mezery, zvažte nastavení `row.Height = 0` po skrytí.  
- **Výkon:** Skrytí řádků je levné; odstranění řádků spouští přepočet celé tabulky, což může být pomalejší u velkých dokumentů.  
- **Testování:** Otevřete uložený soubor ve Wordu a použijte **Reveal Formatting** (`Shift+F1`) k ověření, že je nastaven příznak `Hidden` řádku.

---

## Kompletní funkční příklad (připravený ke kopírování)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;

class HideRowInTableDemo
{
    static void Main()
    {
        // Load the source document (ensure the path exists)
        Document doc = new Document(@"C:\MyDocs\input.docx");

        // Get the first table – adapt if you have multiple tables
        Table table = doc.FirstSection.Body.Tables[0];

        // Verify we have at least three rows
        if (table.Rows.Count < 3)
        {
            Console.WriteLine("The table doesn't have a third row to hide.");
            return;
        }

        // Choose the third row (index 2) and hide it
        Row rowToHide = table.Rows[2];
        rowToHide.Hidden = true; // This hides the row in the output document

        // Save the modified document
        doc.Save(@"C:\MyDocs\output.docx");
        Console.WriteLine("Row hidden successfully. Check output.docx.");
    }
}
```

**Očekávaný výsledek:** Otevřete `output.docx` a uvidíte, že tabulka postrádá třetí řádek, zatímco zbytek obsahu zůstane nedotčen. Skrytý řádek je stále součástí modelu dokumentu, takže jej můžete později nastavit `row.Hidden = false`, aby byl opět viditelný.

---

## Závěr

Právě jsme pokryli **how to hide row** v tabulce Word pomocí C#. Načtením dokumentu, vyhledáním tabulky, výběrem cílového řádku, označením jako skrytý a uložením dosáhnete čisté operace *hide row in table* bez mazání dat. Stejný vzor vám umožní *remove row from table*, pokud potřebujete trvalou změnu, a další tipy vám pomohou vyhnout se běžným úskalím při práci se sloučenými buňkami nebo staršími verzemi Wordu.

Jste připraveni na další výzvu? Zkuste kombinovat tuto techniku s podmíněnou logikou — skrývejte řádky na základě vstupu uživatele nebo generujte dynamické reporty, kde některé sekce zmizí automaticky. Můžete také prozkoumat **hide row in word** pro záhlaví, zápatí nebo dokonce celé sekce.

Máte otázky ohledně *hide row c#* nebo potřebujete pomoc s integrací do většího workflow? Zanechte komentář níže nebo si prohlédněte naše související tutoriály o **manipulating tables in Word with Aspose.Words**. Šťastné kódování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
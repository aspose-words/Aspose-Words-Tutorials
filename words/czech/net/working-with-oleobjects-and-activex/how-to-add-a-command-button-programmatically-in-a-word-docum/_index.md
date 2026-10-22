---
category: general
date: 2026-10-13
description: Naučte se, jak programově přidat příkazové tlačítko pomocí Aspose.Words.
  Tento průvodce také ukazuje, jak vytvořit tlačítko ve Word dokumentu s kompletním
  C# kódem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: cs
lastmod: 2026-10-13
og_description: Přidejte programově příkazové tlačítko do dokumentu Word pomocí Aspose.Words.
  Postupujte podle tohoto kompletního tutoriálu a vytvořte tlačítko v dokumentu Word
  pomocí C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Přidání tlačítka příkazu programově do dokumentu Word – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak programově přidat tlačítko příkazu v dokumentu Word
url: /cs/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak programově přidat tlačítko příkazu v dokumentu Word  

Pokud potřebujete **programově přidat tlačítko příkazu**, Aspose.Words poskytuje čisté API, které vám umožní vložit OLE ovládací prvky formuláře přímo do souboru .docx. Tento tutoriál vás provede všemi kroky potřebnými k **vytvoření tlačítka v dokumentu Word**, které se chová jako běžné tlačítko formuláře při otevření dokumentu v Microsoft Word.  

Naučíte se, jak nastavit vývojové prostředí, vložit tlačítko, nakonfigurovat jeho vlastnosti a ověřit výsledek. Nejsou vyžadovány žádné externí nástroje – stačí .NET projekt a knihovna Aspose.Words pro .NET.  

## Prerequisites  

Před zahájením se ujistěte, že máte:  

* .NET 6.0 SDK nebo novější nainstalovaný.  
* Aktuální verzi Aspose.Words pro .NET (příklady používají 23.12, ale funguje jakákoli verze 22.x+).  
* IDE, např. Visual Studio 2022 nebo Visual Studio Code.  

Kód běží na Windows, macOS a Linuxu, protože Aspose.Words je platformově nezávislý.  

## Step 1: Set up the project and reference Aspose.Words  

1. Vytvořte nový konzolový projekt:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Přidejte NuGet balíček Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Otevřete **Program.cs** a nahraďte jeho obsah šablonou uvedenou v následujících krocích.  

Takové nastavení projektu zajistí, že kompilátor najde jmenné prostory `Aspose.Words` a `Aspose.Words.Drawing.Forms` potřebné pro ovládací prvky formuláře.  

## Step 2: Initialize a blank document and a DocumentBuilder  

`Document` třída představuje celý soubor Word, zatímco `DocumentBuilder` poskytuje plynulé API pro přidávání obsahu.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Proč je tento krok důležitý* – Bez `DocumentBuilder` nemůžete tlačítko přesně umístit na stránku. Builder také respektuje aktuální pozici kurzoru, což usnadňuje pozdější vkládání více ovládacích prvků.  

## Step 3: Insert the command button OLE control  

Aspose.Words zachází s tlačítkem příkazu jako s OLE ovládacím prvkem typu `ControlType.CommandButton`. Jeho umístění a velikost definujete pomocí `RectangleF` měřeného v bodech (1 bod = 1/72 palce).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Klíčové body**  

* Počátek obdélníku (X, Y) je relativní k levému hornímu rohu stránky.  
* Změna `Width` nebo `Height` upravuje vizuální velikost tlačítka.  
* `InsertForms2OleControl` vrací objekt `Forms2OleControl`, který můžete dále konfigurovat.  

## Step 4: Configure the button’s name and caption  

**Název** používá makro engine Wordu k identifikaci ovládacího prvku, zatímco **popisek** je text, který uživatel vidí.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Pokud plánujete později přidat VBA makra, použijte popisný název, protože záznamník makra ve Wordu odkazuje na tuto vlastnost.  

## Step 5: (Optional) Save the document and verify the result  

Uložení souboru vám umožní otevřít jej v Microsoft Word a potvrdit, že tlačítko se zobrazí a funguje.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Když otevřete *CommandButtonDemo.docx* ve Wordu, měli byste vidět tlačítko označené **Submit**, umístěné přibližně 1,4 palce od levého okraje a 2,1 palce od horní části stránky. Kliknutí na tlačítko standardně nic neprovede, protože není připojeno žádné makro, ale vizuální ovládací prvek je plně funkční.  

## Step 6: Edge cases and common pitfalls  

| Situace | Na co si dát pozor | Doporučené řešení |
|-----------|-------------------|-----------------|
| **Tlačítko překrývá existující text** | Obdélník může protínat odstavec, což způsobí problémy s rozvržením. | Vložte tlačítko po volání `builder.Writeln()`, aby se kurzor přesunul na nový řádek, nebo upravte souřadnici `Y`. |
| **Dokument se otevře s varováním** | Některé verze Wordu označují OLE ovládací prvky, které nemají připojený program. | Ujistěte se, že typ ovládacího prvku je `CommandButton`; Word jej považuje za standardní prvek formuláře a nevyžaduje externí program. |
| **Běh na Linuxu v headless prostředí** | Word nelze spustit k testování UI, ale soubor zůstává platný. | Použijte unit test, který načte vlastnosti ovládacího prvku (`commandButton.Name`, `commandButton.Caption`) a ověří, že byly nastaveny správně. |
| **Potřeba více tlačítek** | Opakované použití stejného `DocumentBuilder` bez posunutí kurzoru přidá tlačítko na vrchol předchozího. | Zavolejte `builder.MoveToDocumentEnd()` nebo upravte hodnotu `Y` obdélníku před každým vložením. |

Řešení těchto okrajových případů včas šetří čas při rozšiřování řešení na kompletní formuláře s desítkami ovládacích prvků.  

## Step 7: Full, runnable example  

Níže je samostatný program, který můžete zkopírovat, vložit a spustit bez úprav (kromě obnovení NuGet balíčků).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Očekávaný výstup**  

Spuštěním programu se vytiskne cesta podobná:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Otevřením vygenerovaného *CommandButtonDemo.docx* se zobrazí jediné tlačítko **Submit** umístěné na souřadnicích definovaných v kódu. Žádné další UI prvky se neobjeví, což potvrzuje úspěšnost workflow **add command button programmatically**.  

## Conclusion  

Nyní víte, jak **programově přidat tlačítko příkazu** do dokumentu Word pomocí Aspose.Words, a také rozumíte, jak **vytvořit tlačítko v dokumentu Word**, které lze později propojit s VBA makry nebo externími automatizačními nástroji. Proces se skládá z inicializace dokumentu, vložení OLE ovládacího prvku `CommandButton`, konfigurace jeho vlastností a uložení souboru.  

Zde můžete:  

* Přidat další ovládací prvky (zaškrtávací políčka, textová pole) opakováním kroku 3 s různými hodnotami `ControlType`.  
* Připojit VBA makra k tlačítku pro provádění akcí, jako je uložení formuláře nebo odeslání e‑mailu.  
* Dynamicky generovat celé formuláře pomocí smyčky přes datově řízenou kolekci definic polí.  

Experimentujte s koordináty obdélníku a popiskem tlačítka, aby odpovídaly vašemu UI designu. Šťastné programování!  

## What Should You Learn Next?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Přidat rozbalovací seznam (Combo Box) jako formulářové pole do dokumentu Word s Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Přidat zaškrtávací políčko jako formulářové pole do dokumentu Word s Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Vytvořit prázdný dokument Word s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
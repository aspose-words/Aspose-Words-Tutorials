---
category: general
date: 2026-11-18
description: Vytvořte prázdný dokument Word a vložte ActiveX tlačítko pomocí C#. Naučte
  se, jak přidat ovládací prvek, nastavit popisek tlačítka a uložit soubor.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: cs
lastmod: 2026-11-18
og_description: Vytvořte prázdný dokument Word a vložte pomocí C# tlačítko ActiveX.
  Postupujte podle tohoto kompletního tutoriálu, abyste přidali ovládací prvek, nastavili
  popisek tlačítka a uložili výsledek.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Vytvořte prázdný dokument Word a vložte tlačítko ActiveX – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Vytvořte prázdný dokument Word a vložte ActiveX tlačítko
url: /cs/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word a vložte ActiveX tlačítko

Pokud potřebujete **vytvořit prázdný dokument Word** a umístit do něj interaktivní ActiveX tlačítko, tento návod vám přesně ukáže, jak to provést pomocí Aspose.Words pro .NET. Uvidíte kompletní kód, pochopíte, proč je každý řádek důležitý, a naučíte se, jak **nastavit popisek tlačítka**, aby ovládací prvek vypadal připravený k interakci uživatele.

Kromě hlavního cíle se podíváme na **jak vložit ActiveX**, kroky **jak přidat ovládací prvek** do souboru Word a nuance **vložení ActiveX tlačítka** s vlastním popiskem. Na konci budete mít znovupoužitelný vzor pro jakýkoli scénář automatizace dokumentů, který vyžaduje vložené UI prvky.

## Co se naučíte

* Jak **vytvořit prázdný dokument Word** programově.  
* Přesné API volání potřebné k **vložením ActiveX tlačítka** a konfiguraci jeho vlastností.  
* Jak **nastavit popisek tlačítka**, aby ovládací prvek zobrazoval požadovaný text.  
* Tipy pro uložení souboru na vámi zvolené místo a řešení běžných úskalí.

### Požadavky

* .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.6+).  
* Aspose.Words pro .NET nainstalovaný (`Install-Package Aspose.Words`).  
* Základní znalost C# a Visual Studio nebo jakéhokoli IDE kompatibilního s .NET.

---

## Vytvořte prázdný dokument Word pomocí Aspose.Words

Prvním krokem je vytvořit prázdný objekt `Document`. Tento objekt představuje soubor Word, který neobsahuje žádný obsah, dokud něco nepřidáte.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Proč je to důležité*: Prázdný `Document` vám poskytuje čisté plátno. Později můžete přidávat odstavce, tabulky nebo ovládací prvky, aniž byste se museli starat o existující formátování.

---

## Inicializujte DocumentBuilder pro práci s dokumentem

`DocumentBuilder` je pomocná třída, která vám umožní vkládat obsah na aktuální pozici kurzoru. Automaticky sleduje, kde se v dokumentu nacházíte.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Proč je to důležité*: Bez `DocumentBuilder` byste museli ručně manipulovat se stromem uzlů na nízké úrovni. Builder zjednodušuje vkládání textu, obrázků a ActiveX ovládacích prvků.

---

## Jak vložit ActiveX tlačítko (insert activex button)

Nyní použijeme `InsertForms2OleControl` k vložení ActiveX ovládacího prvku. Metoda vyžaduje tři argumenty:

1. Typ ovládacího prvku (`OleControlType.CommandButton`).  
2. Interní název ovládacího prvku (používaný VBA nebo makro kódem).  
3. `RectangleF`, který určuje pozici a velikost na stránce.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Proč je to důležité*: Toto je jádro **jak vložit activex** do dokumentu Word. Souřadnice obdélníku jsou vyjádřeny v bodech (1 bod = 1/72 palce). Upravením těchto hodnot umístíte tlačítko tam, kde jej potřebujete.

### Tip

Pokud potřebujete, aby se tlačítko objevilo na konkrétní stránce, nejprve přesuňte kurzor builderu:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Jak nastavit popisek tlačítka (set button caption)

Po umístění ovládacího prvku můžete upravit jeho vlastnosti. Nejviditelnější vlastností je `Caption`, která určuje text zobrazený na tlačítku.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Proč je to důležité*: Uživatelé vidí popisek, ne interní název. Změna popisku dává tlačítku smysl v konečném dokumentu.

---

## Uložte dokument obsahující tlačítko

Nakonec zapíšeme dokument na disk. Můžete zvolit libovolný podporovaný formát (`.docx`, `.pdf`, atd.). Zde ukládáme jako dokument Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Proč je to důležité*: Uložení souboru vám umožní otevřít jej v Microsoft Word a otestovat tlačítko. Po otevření dokumentu se tlačítko zobrazí s popiskem „Press“.

### Očekávaný výsledek

Otevření `with_button.docx` ve Wordu zobrazí prázdnou stránku s obdélníkovým tlačítkem označeným **Press**. Kliknutí na tlačítko nic neprovede, protože není připojeno žádné VBA makro, ale ovládací prvek je plně funkční a lze jej později propojit s kódem.

---

## Jak přidat ovládací prvek do konkrétního odstavce (how to add control)

Někdy chcete tlačítko uvnitř konkrétního odstavce, například po nějakém instrukčním textu. Použijte `MoveTo` k umístění builderu před vložením ovládacího prvku.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Proč je to důležité*: Tento vzor ukazuje **jak přidat ovládací prvek** v kontextu, čímž zajišťuje logické uspořádání dokumentu.

---

## Časté úskalí a jak se jim vyhnout

| Problém | Proč se to stane | Řešení |
|-------|----------------|-----|
| Tlačítko se zobrazuje mimo stránku | Souřadnice obdélníku jsou mimo okraje stránky | Použijte `builder.PageSetup` k získání rozměrů stránky a vypočítejte bezpečný `RectangleF`. |
| Popisek se nezobrazuje | `Caption` nastaven před úplnou inicializací ovládacího prvku | Nastavte `Caption` **po** volání `InsertForms2OleControl`, jak je ukázáno v kroku 4. |
| Dokument se uloží bez tlačítka | Kurzor builderu byl po vložení přesunut bez potvrzení změn | Nechte builder na stejné stránce nebo zavolejte `builder.Document.UpdatePageLayout()` před uložením. |

---

## Kompletní spustitelný příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit. Vytvoří prázdný soubor Word, vloží ActiveX tlačítko, nastaví jeho popisek a výsledek uloží.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Výstup**: Po spuštění programu otevřete `C:\Temp\with_button.docx` v Microsoft Word. Uvidíte jedinou stránku s textem „Below is an ActiveX button created programmatically:“ následovaným tlačítkem označeným **Press**.

---

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **vložit ActiveX tlačítko**, **nastavit popisek tlačítka** a **uložit** výsledek pomocí Aspose.Words pro .NET. Stejný vzor lze rozšířit i na další ActiveX ovládací prvky (zaškrtávací políčka, seznamy atd.) změnou `OleControlType`.  

Dále můžete zkoumat **jak vložit ActiveX tlačítko** události pomocí VBA, nebo **jak přidat ovládací prvek** do existujících dokumentů, které již obsahují obsah. Obě témata staví přímo na konceptech zde představených.

Šťastné programování a nebojte se experimentovat s různými velikostmi, pozicemi a popisky, aby vyhovovaly UI požadavkům vaší aplikace!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [How to create Word document C# with an ActiveX command button](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
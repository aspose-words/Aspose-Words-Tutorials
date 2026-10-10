---
category: general
date: 2026-10-10
description: Nastavte text tlačítka a přidejte ActiveX tlačítko v C# pomocí Aspose.Words.
  Naučte se, jak vložit tlačítko, vytvořit ovládací prvek tlačítka a přizpůsobit popisek
  ve Word dokumentu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: cs
lastmod: 2026-10-10
og_description: Nastavte text tlačítka a přidejte ActiveX tlačítko v C# s Aspose.Words.
  Postupujte podle tohoto krok‑za‑krokem průvodce pro vložení tlačítka, vytvoření
  ovládacího prvku tlačítka a úpravu jeho popisku.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Nastavte text tlačítka a přidejte tlačítko ActiveX v C# – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Nastavte text tlačítka a přidejte ActiveX tlačítko v C#
url: /cs/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení textu tlačítka a přidání ActiveX tlačítka v C#

Pokud potřebujete **nastavit text tlačítka** na ActiveX tlačítku uvnitř dokumentu Word, tento průvodce vám přesně ukáže, jak na to. Na konci tutoriálu budete schopni **vložit tlačítko**, vytvořit **ovládací prvek tlačítka** a přizpůsobit jeho popisek pomocí několika řádků kódu v C#.

Práce s ActiveX ovládacími prvky je běžná, když chcete v aplikaci Word interaktivní formuláře – ať už vytváříte šablonu smlouvy, průzkum nebo interní nástroj. Příklad používá Aspose.Words pro .NET, knihovnu, která umožňuje manipulovat se soubory Word bez nainstalovaného Microsoft Office.

## Požadavky

* .NET 6.0 SDK nebo novější nainstalovaný  
* Visual Studio 2022 (nebo jakékoli IDE podporující C#)  
* Licence Aspose.Words pro .NET (bezplatná zkušební verze stačí pro výuku)  

Také potřebujete odkaz na NuGet balíček `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## Jak vložit tlačítko do dokumentu Word

Prvním krokem je vytvořit nový `Document` a `DocumentBuilder`. Builder je vstupním bodem pro přidávání obsahu, včetně ActiveX ovládacích prvků.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité:** `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` poskytuje vysoce‑úrovňové metody jako `InsertParagraph` a `InsertFormField`. Začátek s čistým dokumentem zajišťuje, že se tlačítko objeví přesně tam, kde ho chcete.

## Vytvoření ovládacího prvku tlačítka pomocí Forms2OleControl

Nyní vytvoříme skutečný ovládací prvek tlačítka. `Forms2OleControl` je třída, kterou Aspose.Words používá pro všechny ActiveX objekty, a typ `COMMANDBUTTON` se v aplikaci Word zobrazuje jako klikatelné tlačítko.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Vysvětlení:**  
* `InsertForms2OleControl` umístí ovládací prvek na přesné souřadnice, které zadáte.  
* Velikost je definována v bodech (1 bod = 1/72 palce). Přizpůsobte tato čísla tak, aby odpovídala vašemu rozvržení.

## Přidání ActiveX ovládacího prvku a přiřazení jedinečného názvu

Každý ActiveX objekt by měl mít jedinečný název, aby jej bylo možné později odkazovat (například při zpracování událostí ve VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tip:** Vyhněte se mezerám nebo speciálním znakům v názvu; Word zachází s názvem jako s identifikátorem ve svém interním modelu formulářů.

## Nastavení textu tlačítka (popisku) na ActiveX tlačítku

Zde vstupuje do hry hlavní klíčové slovo **set button text**. Vlastnost `Caption` určuje popisek, který uživatelé na tlačítku vidí.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Popisek můžete změnit kdykoli před uložením dokumentu. Pokud později potřebujete lokalizovat uživatelské rozhraní, stačí znovu zavolat `SetCaption` s jiným řetězcem.

## Uložení dokumentu a ověření výsledku

Nakonec zapíšete dokument na disk. Otevřením souboru v Microsoft Word uvidíte tlačítko s vlastním popiskem.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Očekávaný výstup:** Když otevřete *ActiveXButton.docx* ve Wordu, uvidíte tlačítko umístěné na zadaných souřadnicích, označené **Click Me**. Kliknutím na tlačítko spustíte výchozí chování příkazového tlačítka Wordu (které můžete později přizpůsobit pomocí VBA).

![Příklad nastavení textu tlačítka](https://example.com/activex-button.png){alt="Příklad nastavení textu tlačítka"}

## Přidání ActiveX tlačítka a zpracování událostí (volitelné)

Pokud potřebujete, aby tlačítko provádělo vlastní akci, můžete přidat VBA makro, které reaguje na událost `Click`. Makro lze vložit programově, ale to přesahuje rozsah tohoto tutoriálu. Důležitá část je, že tlačítko už je přítomno a jeho popisek je nastaven – připravené pro jakékoli zpracování událostí, které si zvolíte.

## Časté úskalí a jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|-------|----------------|-----|
| Tlačítko se zobrazuje nesprávně zarovnané | Souřadnice jsou v bodech, ne v pixelech | Převést hodnoty pixelů na body (`points = pixels * 72 / DPI`) |
| Popisek se po uložení nezmění | `SetCaption` voláno po `Save` | Vždy nastavte popisek **před** voláním `doc.Save` |
| Ovládací prvek není viditelný ve starších verzích Wordu | Některé starší verze Wordu postrádají plnou podporu ActiveX | Testujte na cílové verzi Wordu; zvažte použití `CheckBox` nebo `DropDownList` jako náhrady |
| Varování licence ve výstupu | Vyprší zkušební licence | Použijte platnou licenci Aspose.Words pomocí `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit. Obsahuje všechny potřebné `using` direktivy a ukazuje celý pracovní postup od vytvoření dokumentu po jeho uložení.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Spusťte program pomocí `dotnet run`. Po provedení otevřete *ActiveXButton.docx* a ověřte, že popisek tlačítka zní **Click Me**.

## Shrnutí toho, co jste se naučili

* Naučili jste se, jak **nastavit text tlačítka** na ActiveX tlačítku pomocí Aspose.Words.  
* Viděli jste přesné kroky, jak **vložit tlačítko**, **vytvořit ovládací prvek tlačítka** a **přidat ActiveX ovládací prvek** do dokumentu Word.  
* Nyní máte znovupoužitelný úryvek kódu, který můžete přizpůsobit pro jakýkoli projekt automatizace Wordu založený na formulářích.

## Další kroky

* Prozkoumejte další hodnoty `Forms2OleControlType`, jako jsou `CHECKBOX` nebo `LISTBOX`, pro vytvoření bohatších formulářů.  
* Kombinujte tlačítko s VBA makrem pro provádění výpočtů nebo validace dat.  
* Použijte API `FormField` z Aspose.Words k načtení vstupu uživatele po vyplnění dokumentu.

Neváhejte experimentovat s velikostí, pozicí a popiskem, aby odpovídaly vašim požadavkům na design. Pokud narazíte na jakékoli problémy, dokumentace Aspose.Words poskytuje podrobné odkazy na každou třídu použitou v tomto tutoriálu.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními krok za krokem, aby vám pomohly zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit prázdný dokument Word s Aspose.Words – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Přidat stín k tvaru ve Wordu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Přidat čísla stránek do zápatí dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
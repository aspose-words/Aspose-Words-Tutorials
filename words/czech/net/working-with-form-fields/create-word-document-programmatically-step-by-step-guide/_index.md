---
category: general
date: 2026-08-04
description: Vytvořte dokument Word programově pomocí C#. Naučte se, jak programově
  přidat příkazové tlačítko pomocí Aspose.Words během několika kroků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: cs
lastmod: 2026-08-04
og_description: Vytvořte programově dokument Word pomocí Aspose.Words. Tento průvodce
  ukazuje, jak programově přidat tlačítko příkazu, nakonfigurovat jej a uložit soubor.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Vytvořte Word dokument programově – kompletní C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Vytvořte Word dokument programově – krok za krokem
url: /cs/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu programově – kompletní C# tutoriál

Pokud potřebujete **create word document programmatically**, tento průvodce vám přesně ukáže, jak to provést pomocí Aspose.Words for .NET. Pouhých několik řádků C# vám umožní vygenerovat prázdný soubor `.docx`, **programmatically add command button** ovládací prvky, nastavit jejich vlastnosti a výsledek uložit.  

Níže uvedené kroky pokrývají vše od nastavení projektu až po zpracování okrajových případů, takže můžete kód zkopírovat do své vlastní aplikace a spustit jej bez úprav.

## Co dosáhnete

* Inicializujte nový Word dokument kompletně v paměti.  
* **Programmatically add command button** OLE ovládací prvky na libovolném místě a velikosti.  
* Nakonfigurujte popisek tlačítka, interní název a další OLE vlastnosti.  
* Uložte vygenerovaný dokument na disk nebo do proudu pro další zpracování.

### Předpoklady

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+).  
* Platná licence Aspose.Words for .NET (nebo bezplatná zkušební verze).  
* Základní znalost C# a Visual Studio (nebo libovolného IDE dle vašeho výběru).  

> **Tip:** Pokud spustíte ukázku bez licence, Aspose.Words přidá na první stránku malou zkušební vodoznak.

## Krok 1: Nastavte projekt a importujte požadované jmenné prostory

Vytvořte novou konzolovou aplikaci (nebo ji integrujte do existující služby) a přidejte balíček Aspose.Words NuGet:

```bash
dotnet add package Aspose.Words
```

Poté zahrňte nezbytné jmenné prostory na začátek vašeho `.cs` souboru:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Tyto importy vám poskytují přístup k `Document`, `DocumentBuilder`, `Forms2OleControl` a struktuře `RectangleF` používané pro umístění.

## Krok 2: Inicializujte nový Word dokument

První operací v jakémkoli workflow **create word document programmatically** je vytvořit objekt `Document`. Tento objekt existuje pouze v paměti, dokud jej výslovně neuložíte.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funguje jako kurzor, který sleduje, kam bude umístěn další prvek. Používání tohoto objektu udržuje kód stručný a napodobuje způsob, jakým byste psali přímo ve Wordu.

## Krok 3: Vložte OLE ovládací prvek command button

Aspose.Words poskytuje metodu `InsertForms2OleControl` pro vložení OLE objektů, jako jsou command buttony, zaškrtávací políčka nebo rozbalovací seznamy. Metoda vyžaduje tři argumenty:

1. Hodnota výčtu `ControlType` (zde `CommandButton`).  
2. `RectangleF`, který určuje X‑Y pozici a šířku‑výšku ovládacího prvku (měřeno v bodech, kde 72 pt = 1 inch).  
3. Volitelně další OLE vlastnosti (pro základní tlačítko nejsou potřeba).  

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Proč to funguje:** `InsertForms2OleControl` vytvoří v dokumentu OLE kontejner a vrátí obal `Forms2OleControl`. Tento obal vám umožní manipulovat s podkladovým OLE objektem (skutečným tlačítkem) aniž byste se museli zabývat nízkoúrovňovým COM interopem.

## Krok 4: Nakonfigurujte popisek a interní název tlačítka

Po vložení obvykle chcete tlačítku přiřadit uživatelsky viditelný popisek a interní identifikátor, na který může odkazovat vaše makro nebo doplněk.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` je text zobrazený na tlačítku v uživatelském rozhraní Wordu.  
* `Name` je programový identifikátor používaný VBA nebo externími automatizačními skripty.

### Volitelné: Přiřaďte makro tlačítku

Pokud plánujete spustit VBA makro při kliknutí na tlačítko, můžete přiřadit název makra:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Okrajový případ:** Když bude cílový dokument otevřen na počítači bez makra, Word zobrazí bezpečnostní varování. Vždy podepisujte svá makra nebo informujte uživatele o požadovaných nastaveních.

## Krok 5: Uložte dokument

Můžete soubor zapsat na disk, do `MemoryStream` nebo přímo do objektu odpovědi v webovém API. Nejjednodušší přístup pro konzolovou ukázku je uložit do lokální složky:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Výsledný `.docx` se otevře v Microsoft Wordu s funkčním tlačítkem, které zobrazuje „Click Me“. Kliknutím na tlačítko spustíte přiřazené makro (pokud existuje) nebo se zobrazí výchozí zpráva.

## Kompletní funkční příklad

Zkopírujte následující program do `Program.cs` a spusťte jej. Demonstruje celý **create word document programmatically** tok, včetně ošetření chyb.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Očekávaný výsledek:** Otevření `CommandButton.docx` ve Wordu zobrazí tlačítko označené „Click Me“. Přechodem myší nad tlačítkem se v panelu vlastností objeví název `cmdClickMe`.

## Časté otázky a řešení problémů

| Question | Answer |
|----------|--------|
| *Mohu přidat tlačítko do existujícího dokumentu?* | Ano. Načtěte soubor pomocí `new Document("Existing.docx")` a poté použijte stejný volání `InsertForms2OleControl`. |
| *Jaké jednotky používá `RectangleF`?* | Body (1 inch = 72 pt). Upravit hodnoty pro přesné umístění tlačítka. |
| *Bude tlačítko fungovat ve Wordu pro Mac?* | OLE ovládací prvky jsou podporovány pouze ve Wordu pro Windows. Na Macu se tlačítko zobrazí jako statický obrázek. |
| *Potřebuji licenci pro produkční použití?* | Komerční licence odstraňuje zkušební vodoznaky a odemyká plnou funkčnost. |
| *Jak mohu změnit velikost tlačítka po vložení?* | Upravte `commandButton.Width` a `commandButton.Height` nebo znovu vložte s novým `RectangleF`. |

## Rozšíření řešení

Nyní, když víte, jak **programmatically add command button** ovládací prvky, můžete prozkoumat tato související témata:

* **Insert other form controls** – použijte `ControlType.CheckBox`, `ControlType.OptionButton` atd. (pokrývá sekundární klíčové slovo *Aspose.Words InsertForms2OleControl*).  
* **Populate the document with dynamic data** – sloučte data z databáze do tabulek nebo polí hromadné korespondence.  
* **Export to PDF** – po přidání tlačítka zavolejte `doc.Save("output.pdf", SaveFormat.Pdf)` pro vytvoření PDF verze (relevantní k *C# Word automation*).  

## Závěr

Nyní máte kompletní, produkčně připravený vzor pro **create word document programmatically** a **programmatically add command button** pomocí Aspose.Words for .NET. Tutoriál pokryl nastavení projektu, inicializaci dokumentu, vložení OLE tlačítka, konfiguraci vlastností a uložení souboru. Klidně upravte kód pro vložení dalších formulářových ovládacích prvků, připojení maker nebo integraci logiky do webových služeb či úloh na pozadí.

Šťastné programování a užívejte si automatizaci Word dokumentů!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok za krokem vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvoření Word dokumentu s Aspose.Words – krok za krokem průvodce](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Vytvoření Word dokumentu s tabulkou pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Vytvoření skupinového tvaru ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
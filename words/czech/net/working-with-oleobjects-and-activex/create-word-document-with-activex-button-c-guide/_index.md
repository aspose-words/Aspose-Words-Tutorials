---
category: general
date: 2026-07-19
description: Vytvořte dokument Word pomocí Aspose.Words C# a naučte se, jak přidat
  ActiveX příkazové tlačítko, nastavit velikost tlačítka a vložit tlačítko programově.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: cs
lastmod: 2026-07-19
og_description: Vytvořte Word dokument pomocí Aspose.Words C# a během několika sekund
  vložte ActiveX příkazové tlačítko. Postupujte podle průvodce krok za krokem, jak
  snadno nastavit velikost tlačítka a vložit jej.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Vytvořte Word dokument s tlačítkem ActiveX – C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Vytvořte dokument Word s tlačítkem ActiveX – průvodce C#
url: /cs/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu s ActiveX tlačítkem – Kompletní průvodce v C#

Už jste se někdy zamysleli, jak **vytvořit Word dokument**, který obsahuje funkční ActiveX tlačítko? Možná automatizujete zprávu a potřebujete klikatelné ovládání „Schválit“ přímo v souboru. V tomto tutoriálu vás provedeme přesně tímto – pomocí Aspose.Words pro .NET přidáme ActiveX tlačítko příkazu, nastavíme jeho velikost a vložíme jej tam, kde jej potřebujete.

Pokud jste si někdy položili otázku *jak přidat activex* ovládací prvky bez ručního otevírání Wordu, jste na správném místě. Na konci budete mít spustitelný příklad, jasné vysvětlení každého kroku a tipy, jak se vypořádat s běžnými úskalími.

## Co se naučíte

- Jak nastavit Aspose.Words v C# projektu  
- Přesný kód pro **vytvoření Word dokumentu** a vložení ActiveX tlačítka příkazu  
- Způsoby, jak **nastavit velikost tlačítka** a přizpůsobit jeho popisek a název  
- Správná metoda pro **vložit tlačítko příkazu** a **jak vložit tlačítko** na libovolné místo v dokumentu  
- Úvahy o okrajových případech (verze Wordu, omezení platformy, bezpečnostní varování)

### Požadavky

- .NET 6.0 nebo novější (kód také funguje na .NET Framework 4.7+).  
- Platná licence Aspose.Words pro .NET (nebo bezplatný evaluační klíč).  
- Visual Studio 2022 (nebo jakékoli IDE dle vašeho výběru).  
- Základní znalost C# a objektově orientovaného programování.

Žádné další knihovny třetích stran nejsou vyžadovány.

---

## Krok 1: Vytvoření Word dokumentu – Nastavení projektu

Než budeme moci **vložit tlačítko příkazu**, potřebujeme prázdný Word soubor, se kterým budeme pracovat. Tento krok také ukazuje klasický vzor „vytvořit Word dokument“ pomocí Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Proč je to důležité:** `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` sleduje aktuální pozici kurzoru. Všechny následné vložení (včetně našeho ActiveX ovládacího prvku) se provádějí relativně k tomuto builderu.

## Krok 2: Jak přidat ActiveX – Vytvoření CommandButton ovládacího prvku

Nyní, když dokument existuje, pojďme se pustit do části **jak přidat activex**. Aspose.Words poskytuje třídu `Forms2OleControl` pro ActiveX objekty. Zde vytvoříme tlačítko příkazu a nakonfigurujeme jeho vlastnosti, včetně požadavku **nastavit velikost tlačítka**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Tip:** Velikost se měří v bodech (1 bod = 1/72 palce). Upravit hodnoty tak, aby vyhovovaly vašemu rozvržení; pro typické tlačítko na panelu nástrojů funguje dobře 120 × 30.

## Krok 3: Vložení tlačítka příkazu – Jádro **Insert Command Button**

S připraveným ovládacím prvkem nyní **vložíme tlačítko příkazu** do dokumentu na aktuální pozici builderu. Můžete builder přesunout kamkoli (např. za odstavec) před voláním této metody.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Pokud potřebujete **jak vložit tlačítko** na konkrétní záložku, stačí nejprve přesunout builder:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Co se děje v pozadí?** Aspose.Words zapisuje potřebné OLE objekty do balíčku .docx, takže Word může tlačítko vykreslit bez jakýchkoli dalších maker.

## Krok 4: Uložení dokumentu – Dokončení cyklu **Create Word Document**

Poslední krok je jednoduchý: uložit soubor na disk. Tím se dokončí celý proces **vytvoření Word dokumentu**, vložení ActiveX a uložení.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Otevřete výsledný soubor v Microsoft Word (pouze Windows). Měli byste vidět klikatelné tlačítko označené „Click Me“. Kliknutí spustí výchozí akci pro CommandButton – nic se nestane, pokud nepřipojíte VBA kód, ale ovládací prvek je plně funkční.

> **Očekávaný výstup:** Soubor .docx s jednou stránkou, tlačítkem uprostřed místa vložení, velikosti 120 × 30 pt, popiskem „Click Me“.  
> > ![ActiveX tlačítko vložené do Word dokumentu](placeholder-image.png)  
> > *Text alternativy obrázku:* **ActiveX tlačítko vložené do Word dokumentu pomocí C#** (matches `og_image_alt`).

## Krok 5: Okrajové případy, bezpečnost a osvědčené postupy

### Omezení platformy
- ActiveX ovládací prvky fungují pouze ve Windows verzi Wordu. Pokud vaše publikum zahrnuje uživatele macOS nebo Word Online, tlačítko se zobrazí jako statický obrázek.
- Některé firemní prostředí zakazují ActiveX z bezpečnostních důvodů; možná budete muset dokument podepsat nebo informovat uživatele, aby povolili obsah.

### Interakce s VBA (volitelné)
Pokud chcete, aby tlačítko spouštělo makro, budete muset po uložení do dokumentu přidat VBA projekt. Aspose.Words automaticky nevytváří VBA kód, ale můžete použít API `Document.VbaProject` k jeho vložení.

### Kolize názvů
Vždy přiřaďte každému ovládacímu prvku jedinečný `Name`. Opětovné použití stejného názvu může způsobit chyby za běhu, když Word bude snažit se rozpoznat ovládací prvek.

### Tip pro výkon
Při vkládání mnoha ovládacích prvků znovu použijte jedinou instanci `DocumentBuilder` a vyhněte se volání `doc.Save` uvnitř smyčky. Vkládejte hromadně a uložte jednou na konci.

## Kompletní funkční příklad

Spojením všeho dohromady zde máte kompletní program připravený ke zkopírování a vložení:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Spusťte program, otevřete uložený soubor a uvidíte tlačítko přesně tam, kde byl umístěn builder.

## Závěr

Právě jsme **vytvořili Word dokument** od nuly, naučili se **jak přidat activex** konfigurací `Forms2OleControl`, zvládli **nastavit velikost tlačítka** a ukázali správný způsob **vložit tlačítko příkazu** a **jak vložit tlačítko** na libovolné místo v souboru.

Z jediného ukázkového kódu nyní máte pevný základ pro pokročilejší automatizaci Wordu – ať už vytváříte šablony s interaktivními formuláři, generujete smlouvy vyžadující potvrzení uživatele, nebo jen rozmisťujete několik užitečných ovládacích prvků po celém reportu.

### Co dál?
- **Stylizovat tlačítko** – změnit písma, barvy nebo přidat obrázkové pozadí.  
- **Připojit VBA makra** – nechat tlačítko provádět výpočty nebo spouštět externí programy.  
- **Kombinovat s dalšími ovládacími prvky** – zaškrtávací políčka, seznamové pole nebo dokonce vložené listy Excelu.  

Nebojte se experimentovat, a pokud narazíte na problém, zanechte komentář níže. Šťastné kódování a užívejte si automatizaci Wordu s Aspose.Words!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-08-20
description: Naučte se, jak vytvořit ActiveX ovládací prvek, nastavit velikost tlačítka
  a přidat tlačítko do Wordu pomocí kompletního příkladu v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: cs
lastmod: 2026-08-20
og_description: Vytvořte ActiveX kontrolu v souboru Word pomocí C#. Tento tutoriál
  ukazuje, jak nastavit velikost tlačítka, přidat tlačítko do Wordu a vytvořit klikatelné
  tlačítko.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Vytvořte ActiveX ovládací prvek ve Wordu – krok za krokem průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Jak vytvořit ActiveX ovládací prvek v dokumentu Word pomocí C#
url: /cs/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit ActiveX kontrolu ve Word dokumentu pomocí C#

Pokud potřebujete **vytvořit ActiveX kontrolu** uvnitř souboru Microsoft Word, tento průvodce vám přesně ukáže, jak na to. Uvidíte, jak **přidat tlačítko do Wordu**, nastavit rozměry tlačítka a učinit kontrolu klikací — vše pomocí krátkého, samostatného C# programu.

V tomto tutoriálu se naučíte:

* Porozumět tomu, proč je ActiveX kontrola užitečná pro interaktivní Word dokumenty.  
* Zjistit přesný kód potřebný k **nastavení velikosti tlačítka** a přiřazení popisku.  
* Vidět, jak **vytvořit klikatelné tlačítko**, které lze později propojit s makrem nebo externí logikou.  

Kroky fungují s Aspose.Words .NET 23.12 nebo novějším a vyžadují pouze .NET vývojové prostředí.

> **Předpoklad** – Máte platnou licenci Aspose.Words (nebo používáte evaluační verzi) a Visual Studio 2022 nebo jakékoli C# IDE.

---

## Jak vytvořit ActiveX kontrolu ve Word dokumentu

Prvním krokem je vytvořit prázdný `Document` a `DocumentBuilder`. Builder poskytuje vysoce‑úrovňové API pro vkládání objektů, jako jsou ActiveX kontroly.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Metoda `InsertActiveXButton` (definovaná níže) obsahuje logiku **jak vložit tlačítko** a nakonfigurovat jej.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Spuštěním programu se vytvoří **ActiveXButton.docx**. Otevřením souboru ve Wordu se zobrazí tlačítko označené **Submit**. Kontrola je plně funkční — kliknutí vyvolá standardní událost `CommandButton_Click`, kterou můžete později svázat s VBA makrem.

### Proč to funguje

* `InsertForms2OleControl` říká Wordu, aby vložil OLE objekt typu **CommandButton**, což je klasická třída ActiveX tlačítka.  
* Argumenty šířky a výšky přímo **nastavují velikost tlačítka**; Word převádí hodnoty z bodů (1 pt ≈ 1/72 in).  
* Pojmenování kontroly (`Name = "btnSubmit"`) usnadňuje její nalezení z VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Nastavení velikosti tlačítka a popisku

Pokud potřebujete jiný vzhled, upravte číselné argumenty ve volání `InsertForms2OleControl`. Podpis metody je:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – programový identifikátor třídy ActiveX (`"CommandButton"` pro standardní tlačítko).  
* **width / height** – velikost v bodech. Pro tlačítko široké 2 cm použijte `width = 56.7` (2 cm ≈ 56.7 pt).  

Popisek můžete také změnit po vložení:

```csharp
commandButton.Caption = "Send Request";
```

Změna popisku neovlivňuje velikost, ale mění vizuální zpětnou vazbu pro uživatele.

### Pro tip

Pokud chcete čtvercové tlačítko, nastavte obě rozměry na stejnou hodnotu:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Přidat tlačítko do Wordu a učinit jej klikacím

Kód výše již **přidává tlačítko do Wordu**. Aby tlačítko vykonávalo akci, musíte napsat VBA makro, které zpracuje událost `Click`. Zde je minimální makro, které můžete vložit do editoru VBA ve Wordu (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Protože je kontrola pojmenována `btnSubmit`, Word automaticky mapuje událost `Click` na `btnSubmit_Click`. Toto je standardní způsob, jak **vytvořit klikatelné tlačítko** bez externích knihoven.

> **Poznámka:** Nastavení zabezpečení maker ve Wordu může blokovat ActiveX kontroly. Ujistěte se, že je vybráno „Enable all macros“ nebo „Enable VBA macros“ pro dokument, nebo makro digitálně podepište pro produkční použití.

---

## Časté otázky: jak vložit tlačítko a řešení problémů

### 1. Co když se tlačítko po uložení nezobrazí?

* Ověřte, že verze Aspose.Words podporuje `InsertForms2OleControl`. Verze před 22.5 tuto funkci nemají.  
* Ujistěte se, že cílový formát souboru je `.docx` nebo `.doc`. Starší formáty jako `.rtf` nemohou ukládat ActiveX objekty.

### 2. Mohu vložit tlačítko na konkrétní záložku?

Ano. Přesuňte builder na záložku před voláním `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Jak **nastavit velikost tlačítka** dynamicky na základě délky textu?

Vypočítejte požadovanou šířku pomocí metody `Graphics.MeasureString` (z `System.Drawing`) a převedete pixely na body (`points = pixels * 72 / DPI`). Pak předáte vypočtenou šířku do `InsertForms2OleControl`.

### 4. Existuje způsob, jak přidat více tlačítek ve smyčce?

Určitě. Zabalte logiku vložení do `for` smyčky a upravte vlastnosti `Left` a `Top` pro každou iteraci:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Očekávaný výstup

Po spuštění programu a otevření **ActiveXButton.docx**:

* Na první stránce se v levém horním rohu objeví jedno **Submit** tlačítko.  
* Velikost tlačítka odpovídá zadaným rozměrům (`100 pt × 30 pt`).  
* Pokud jste přidali VBA makro, kliknutí na tlačítko zobrazí zprávu: „You clicked the Submit button!“.

Úspěšně jste tedy **vytvořili ActiveX kontrolu**, **nastavili velikost tlačítka** a **přidali tlačítko do Wordu**, přičemž jste se naučili **jak vložit tlačítko** a **vytvořit klikatelné tlačítko** pro budoucí automatizační úlohy.

---

## Závěr

V tomto tutoriálu jste se naučili, jak **vytvořit ActiveX kontrolu** uvnitř Word dokumentu pomocí C#. Dodržením kroků můžete **nastavit velikost tlačítka**, přiřadit kontrole smysluplný název a **přidat tlačítko do Wordu**, aby se stalo **klikacím tlačítkem** spojeným s VBA makrem.  

Od semene můžete dále zkoumat:

* Propojení tlačítka s .NET COM add‑in místo VBA.  
* Použití dalších ActiveX tříd, jako je `CheckBox` nebo `ComboBox`.  
* Automatizaci tvorby kompletních formulářů s více kontrolami.

Neváhejte experimentovat s různými velikostmi


## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-08-07
description: Naučte se, jak přidat ActiveX ovládací prvek do dokumentu Word pomocí
  C#. Zahrnuje přiřazení makra k tlačítku a přidání klikatelného tlačítka s příklady
  ve Wordu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: cs
lastmod: 2026-08-07
og_description: Jak přidat ActiveX ovládací prvek do dokumentu Word pomocí Aspose.Words.
  Postupujte podle tohoto návodu pro vložení tlačítka, přiřazení makra k tlačítku
  a přidání klikatelného tlačítka do Wordu.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: jak přidat ActiveX ovládací prvek do Wordu – kompletní C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak přidat ActiveX ovládací prvek do Wordu s Aspose.Words – průvodce krok za
  krokem
url: /cs/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak přidat activex control in Word with Aspose.Words

Pokud potřebujete **how to add activex control** v souboru Microsoft Word programově, tento tutoriál vám ukáže přesné kroky pomocí Aspose.Words pro .NET. Uvidíte, jak vložit tlačítko příkazu, nastavit jeho popisek a **associate macro with button**, aby se ovládací prvek reagoval, když na něj uživatel klikne. Na konci budete mít makrem povolený soubor `.docm`, který obsahuje plně funkční tlačítko.

Přidání ActiveX tlačítka je běžná požadavka při tvorbě interaktivních šablon, jako jsou žádosti o půjčku, formuláře pro nástup nových zaměstnanců nebo automatizované zprávy. Tento průvodce prochází každý řádek kódu, vysvětluje **why** každý krok a pokrývá typické úskalí, na která můžete narazit.

## Požadavky

* .NET 6 (nebo .NET Core 3.1 / .NET Framework 4.8) nainstalován.  
* Platná licence Aspose.Words pro .NET nebo dočasný evaluační klíč.  
* Visual Studio 2022 (nebo jakékoli IDE podporující C#).  
* Základní znalost Word makr (VBA), pokud plánujete psát makro, které tlačítko spustí.  

> **Pro tip:** Když spustíte ukázku, uložte výstup do složky, do které máte oprávnění zápisu, jinak `doc.Save` vyhodí výjimku.

## Jak přidat ActiveX control in a Word document using Aspose.Words

Jádrem řešení je krátký C# program, který vytvoří nový dokument, vloží ActiveX **CommandButton** ovládací prvek a uloží soubor jako makrem povolený dokument (`.docm`). Kód je kompletní a připravený ke zkopírování.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Proč je každý řádek důležitý

| Line | Purpose |
|------|---------|
| `Document doc = new Document();` | Vytvoří novou Word balíček v paměti. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Poskytuje plynulé API pro vkládání obsahu, včetně ActiveX ovládacích prvků. |
| `InsertForms2OleControl` | Jediná metoda Aspose.Words, která vytváří ActiveX ovládací prvek; specifikujete typ ovládacího prvku (`CommandButton`) a jeho geometrii. |
| `commandButton.Caption = "Click Me";` | Nastavuje **add clickable button word**, který uživatel vidí. Bez popisku se tlačítko zobrazí prázdné. |
| `commandButton.OnAction = "MyMacro";` | **associate macro with button** – říká Wordu, které VBA makro spustit, když je ovládací prvek kliknut. |
| `doc.Save("CommandButton.docm");` | Ukládá dokument jako makrem povolený soubor; běžný `.docx` by odstranil ovládací prvek i makro. |

> **Note:** Souřadnice (levý, horní) jsou měřeny v bodech (1 pt ≈ 1/72 in). Upravit je tak, aby tlačítko bylo umístěno tam, kde jej potřebujete na stránce.

## Jak přiřadit makro k tlačítku

Vlastnost `OnAction` spojuje tlačítko s VBA makrem pojmenovaným `MyMacro`. Stále musíte toto makro vytvořit uvnitř Word souboru, buď ručně, nebo vložením VBA kódu programově (Aspose.Words neukládá VBA kód). Zde je minimální makro, které můžete přidat pomocí editoru **Developer → Visual Basic** ve Wordu:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Když uživatel otevře `CommandButton.docm` a klikne na tlačítko, Word spustí `MyMacro` a zobrazí zprávu. Pokud je zabezpečení makr nastaveno na **Disable all macros without notification**, tlačítko bude vypnuté. Poradte uživatelům, aby povolili makra pro dokument nebo podepsali makro důvěryhodným certifikátem.

### Běžné úskalí při přiřazování makra

* **Macro security settings** – Pokud je dokument otevřen na počítači s přísnými bezpečnostními politikami, makro může být zablokováno. Poskytněte instrukce, jak snížit úroveň zabezpečení nebo makro podepsat.  
* **Naming conflicts** – Název makra musí být jedinečný v rámci VBA projektu dokumentu; jinak Word vyvolá chybu “duplicate procedure name”.  
* **64‑bit vs 32‑bit Word** – ActiveX ovládací prvky fungují stejně, ale VBA editor může zobrazovat různé varovné zprávy v závislosti na verzi Office.  

## Jak přidat text klikatelného tlačítka do Word formuláře

Vlastnost `Caption` je to, co uživatelé vidí na tlačítku. Můžete ji dále přizpůsobit:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Pokud potřebujete, aby se popisek měnil dynamicky na základě vstupu uživatele, můžete později přistupovat k ovládacímu prvku přes objektový model Wordu:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Okrajový případ: Dlouhé popisky

Word zkracuje popisky, které přesahují šířku tlačítka. Aby se předešlo oříznutí, buď zvýšte argument šířky v `InsertForms2OleControl`, nebo text zkraťte. Testování s různými jazyky (např. němčina nebo japonština) se doporučuje, protože šířka znaků se liší.

## Jak přidat text příkazového tlačítka pro automatizaci formuláře

Mimo vizuální popisek, koncept **add command button word** zahrnuje programový název ovládacího prvku. Aspose.Words neexponuje přímou vlastnost `Name` pro ActiveX ovládací prvky, ale můžete nastavit pole `AltText`, které Word považuje za identifikátor ovládacího prvku:

```csharp
commandButton.AltText = "SubmitButton";
```

Později ve VBA můžete odkazovat na tlačítko pomocí jeho hodnoty `AltText`:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Tato technika je užitečná, když máte více tlačítek a potřebujete je programově rozlišovat.

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkompilovat a spustit jako konzolovou aplikaci. Obsahuje volitelné stylování, přiřazení makra a blok komentářů popisující každý krok.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** Otevření `SubmitForm.docm` v Microsoft Word zobrazí modře ohraničené tlačítko označené *Submit Form*. Kliknutím na tlačítko spustíte VBA makro `SubmitMacro` (pokud jste makro do dokumentu přidali). Tlačítko lze dále přesouvat, měnit jeho velikost nebo stylovat pomocí stejného objektu `Forms2OleControl`.

## Testování řešení

1. Sestavte a spusťte C# konzolovou aplikaci.  
2. Otevřete vygenerovaný `SubmitForm.docm` ve Wordu.  
3. Pokud se zobrazí výzva, povolte makra.  
4. Klikněte na tlačítko *Submit Form* – měli byste vidět zprávu definovanou v `SubmitMacro`.  

Pokud se tlačítko zobrazí, ale neprovádí nic, zkontrolujte dvakrát, že název makra přesně odpovídá (`SubmitMacro`) a že zabezpečení makr neblokuje provedení.

## Často kladené otázky

| Question | Answer |
|----------|--------|
| *Mohu přidat více než jedno ActiveX tlačítko?* | Ano. Zavolejte `InsertForms2OleControl` vícekrát s různými souřadnicemi. Použijte odlišné hodnoty `OnAction` a `AltText` k jejich rozlišení. |
| *Je ActiveX ovládací prvek viditelný ve Word Online?* | Ne. |

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Přidat obsah pomocí Document Builder v Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow tutoriál – Přidat stín k Word tvaru v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Přidat novou sekci do Word dokumentu | Aspose.Words pro .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
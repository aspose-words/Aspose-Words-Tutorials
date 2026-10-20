---
category: general
date: 2026-07-29
description: Přidejte tlačítko příkazu do dokumentu Word pomocí Aspose.Words. Naučte
  se, jak nastavit vlastnosti ActiveX ovládacího prvku a nastavit popisek tlačítka
  příkazu během několika snadných kroků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: cs
lastmod: 2026-07-29
og_description: Přidejte tlačítko příkazu do dokumentu Word pomocí Aspose.Words. Tento
  tutoriál ukazuje, jak rychle nastavit vlastnosti ActiveX ovládacího prvku a nastavit
  popisek tlačítka příkazu.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Přidání tlačítka příkazu do dokumentu Word – Aspose.Words krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Přidání tlačítka příkazu do dokumentu Word pomocí Aspose.Words – kompletní
  průvodce
url: /cs/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání tlačítka příkazu do Word dokumentu – Kompletní programovací průvodce

Už jste někdy potřebovali **add command button to word document**, ale nebyli jste si jisti, které volání API použít? Nejste v tom sami; mnoho vývojářů narazí na tuto překážku, když poprvé zkusí vložit interaktivní ovládací prvky do souboru DOCX. Dobrou zprávou je, že Aspose.Words to dělá překvapivě snadno. V tomto průvodci projdeme vytvoření ActiveX ovládacího prvku CommandButton, **set activex control properties** a **set command button caption** — vše pomocí čistého C# kódu, který můžete okamžitě zkopírovat a vložit.

Na konci tohoto tutoriálu budete mít plně funkční Word soubor, který obsahuje klikatelné tlačítko „Submit“, připravené k otevření v Microsoft Wordu. Žádné externí VBA skripty, žádné ruční úpravy UI — pouze čistě programová kontrola.

## Co se naučíte

* Jak vytvořit prázdný Word dokument a `DocumentBuilder`.
* Přesné volání metody pro **add command button to word document** pomocí Aspose.Words.
* Způsoby, jak **set activex control properties** jako velikost, pozice a název.
* Správná technika pro **set command button caption**, aby tlačítko zobrazovalo přesně to, co chcete.
* Tipy pro řešení okrajových případů, jako jsou různé typy tlačítek, škálování DPI a kompatibilita verzí Wordu.

> **Prerequisite:** Visual Studio (nebo jakékoli C# IDE) s nainstalovaným Aspose.Words pro .NET (NuGet balíček `Aspose.Words`). Předchozí zkušenost s ActiveX není vyžadována.

---

## Krok 1: Nastavení projektu a importování jmenných prostorů

Než budeme moci **add command button to word document**, potřebujeme C# projekt, který odkazuje na Aspose.Words. Vytvořte novou .NET konzolovou aplikaci a přidejte NuGet balíček:

```bash
dotnet add package Aspose.Words
```

Nyní přiveďte požadované jmenné prostory do svého zdrojového souboru:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Tyto tři `using` direktivy vám poskytují přístup ke třídám `Document`, `DocumentBuilder` a `Forms2OleControl`, které umožňují vkládání ActiveX ovládacích prvků.

*Pro tip:* Pokud používáte Visual Studio, IDE vám tyto direktivy navrhne automaticky, když napíšete názvy tříd.

---

## Krok 2: Vytvoření prázdného dokumentu a builderu

Čerstvý objekt `Document` představuje prázdný Word soubor. `DocumentBuilder` je naše praktická „pero“, které nám umožňuje kreslit, vkládat text a — co je klíčové — umisťovat ActiveX ovládací prvky.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

V tomto okamžiku je dokument jen prázdným plátnem — představte si čistý list papíru čekající na vaše tlačítko příkazu.

---

## Krok 3: Vložení ActiveX ovládacího prvku CommandButton

Nyní konečně **add command button to word document**. Aspose.Words poskytuje metodu `InsertForms2OleControl`, která přijímá typ ovládacího prvku a rozměry. Použijeme `Forms2OleControlType.CommandButton` a nastavíme šířku 150 bodů a výšku 30 bodů.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Metoda vrací instanci `Forms2OleControl`, kterou použijeme k **set activex control properties** v dalším kroku.

## Krok 4: Konfigurace ovládacího prvku – Název, popisek a pozice

### Nastavení popisku

Popisek je text, který se zobrazí přímo na tlačítku. Pro **set command button caption** stačí přiřadit řetězec k vlastnosti `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Můžete změnit `"Submit"` na cokoli — „Save“, „Export“, „Launch“ atd. — a Word zobrazí přesně tento text.

### Pojmenování ovládacího prvku

Dávat ovládacímu prvku smysluplný název usnadňuje pozdější odkazování (například při automatizaci Word maker). Nastavíme vlastnost `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Umístění na stránce

Word používá body (1/72 palce) pro rozvržení. Upravením vlastností `Left` a `Top` umístíte tlačítko tam, kde potřebujete:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Pokud potřebujete zarovnat tlačítko relativně k odstavci, nejprve posuňte kurzor builderu a pak vložte ovládací prvek; souřadnice budou relativní k této pozici.

*Edge case:* Na monitorech s vysokým DPI se vizuální velikost může v Wordu mírně lišit. Pro zachování fyzické velikosti tlačítka napříč zařízeními můžete body vypočítat na základě cílového DPI (obvykle 96 DPI pro Word).

## Krok 5: Uložení dokumentu

Po úplném nastavení tlačítka je uložení souboru jednorázovým příkazem:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Výsledný soubor `CommandButton.docx` obsahuje plně funkční ActiveX tlačítko. Otevřete jej v Microsoft Wordu a uvidíte tlačítko „Submit“ umístěné přesně tam, kam jste ho vložili.

### Očekávaný výsledek

1. Word dokument se otevře s jednou stránkou.  
2. Obdélníkové tlačítko s popiskem **Submit** se objeví na zadaných souřadnicích.  
3. Pokud kliknete pravým tlačítkem na tlačítko a vyberete **Properties**, uvidíte název `btnSubmit` a další nastavené vlastnosti.

## Krok 6: Pokročilé varianty a běžné úskalí

### Vkládání jiných typů ActiveX

Metoda `InsertForms2OleControl` není omezena jen na tlačítka příkazu. Můžete vložit zaškrtávací políčka, přepínače nebo i vlastní ActiveX objekty:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Stejný vzor **set activex control properties** se použije — stačí vyměnit typ enumu.

### Zpracování verzí Wordu

Starší verze Wordu (před 2007) používají binární formát `.doc`, který ukládá ActiveX ovládací prvky odlišně. Aspose.Words automaticky převádí ovládací prvek při uložení jako `.doc`, ale některé vlastnosti (např. přesné umístění) se mohou posunout. Pokud cílíte na starší formáty, otestujte výstup ve specifické verzi Wordu, kterou potřebujete.

### Nastavení zabezpečení

Word může na počítačích s přísným zabezpečením maker zakázat ActiveX ovládací prvky. Abyste se vyhnuli dialogu „Security Warning“, zvažte:

* Podepsání dokumentu důvěryhodným certifikátem.  
* Instrukce uživatelům, aby povolili ActiveX obsah pro dané umístění souboru.  
* Použití alternativy bez maker (např. běžné ovládací prvky obsahu), pokud je zabezpečení problém.

## Krok 7: Kompletní funkční příklad

Níže je kompletní, připravený k spuštění program, který zahrnuje všechny kroky, o kterých jsme mluvili. Zkopírujte jej do souboru `Program.cs`, upravte výstupní cestu podle potřeby a stiskněte **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Co tento kód dělá:**

* Začíná s novým dokumentem.  
* Vkládá tlačítko příkazu, **sets activex control properties**, a **sets command button caption**.  
* Přidá krátký vysvětlující odstavec.  
* Uloží soubor jako `CommandButton.docx`.

Spusťte program, otevřete vygenerovaný soubor a uvidíte tlačítko umístěné pod vysvětlujícím textem.

## Závěr

Právě jsme ukázali, jak **add command button to word document** pomocí Aspose.Words, jak **set activex control properties** a jak **set command button caption** — vše v stručném, produkčně připraveném C# úryvku. Přístup je škálovatelný: můžete změnit typ ovládacího prvku, upravit rozměry nebo v cyklu zpracovávat datový zdroj a automaticky vkládat desítky tlačítek.

Chcete jít dál? Vyzkoušejte:

* Propojení tlačítka s makrem, které spustí export dat.  
* Přidání obrázků nebo vlastních ikon do tlačítka pomocí vlastnosti `Picture`.  
* Vytvoření kompletního formuláře s více ActiveX ovládacími prvky (textová pole, rozbalovací seznamy atd.).

Experimentování je nejlepší cesta, jak si osvojit automatizaci Wordu. Pokud narazíte na problém, nezapomeňte zkontrolovat výpočty DPI a nastavení zabezpečení Wordu. Šťastné programování a ať jsou vaše dokumenty stále interaktivnější!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
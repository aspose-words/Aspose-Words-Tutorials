---
category: general
date: 2026-09-11
description: Naučte se, jak v kódu vytvořit forms2olecontrol pomocí Aspose.Words DocumentBuilder.
  Tento krok‑za‑krokem průvodce pokrývá vložení ActiveX tlačítka příkazu, použití setOleClassName a
  nastavení velikosti.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: cs
lastmod: 2026-09-11
og_description: Vytvořte forms2olecontrol v kódu pomocí Aspose.Words. Postupujte podle
  tohoto návodu k vložení ActiveX tlačítka příkazu, nastavení jeho názvu třídy a úpravě
  jeho velikosti.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Vytvořte forms2olecontrol v kódu – kompletní průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Jak vytvořit forms2olecontrol v kódu pomocí Aspose.Words
url: /cs/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit forms2olecontrol v kódu pomocí Aspose.Words

Pokud potřebujete **vytvořit forms2olecontrol v kódu**, tento průvodce vám ukáže přesně, jak to provést pomocí Aspose.Words .NET API. Ať už automatizujete šablonu, která vyžaduje ActiveX tlačítko příkazu, nebo jen chcete programově obohatit Word dokument, níže uvedené kroky pokrývají vše od vložení ovládacího prvku až po nastavení jeho vzhledu.

V tomto tutoriálu se naučíte, jak pomocí **Aspose.Words DocumentBuilder** vložit **ActiveX tlačítko příkazu**, nastavit jeho třídu metodou **setOleClassName** a upravit **velikost Forms2OleControl**. Nepotřebujete žádné externí nástroje – stačí .NET vývojové prostředí a knihovna Aspose.Words.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 nebo novější nainstalovaný (kód funguje také s .NET Framework 4.7+)
* Aktuální verzi NuGet balíčku Aspose.Words pro .NET
* Základní znalosti C# a konceptu ActiveX ovládacích prvků ve Word dokumentech

Pokud vám něco chybí, nainstalujte NuGet balíček pomocí:

```bash
dotnet add package Aspose.Words
```

## Co tento tutoriál pokrývá

* Vytvoření instance `DocumentBuilder`
* Vložení `Forms2OleControl` (objekt, který představuje ActiveX tlačítko příkazu)
* Přiřazení správného názvu třídy pomocí `setOleClassName`
* Nastavení vizuální šířky a výšky pomocí vlastností **Forms2OleControl size**
* Uložení dokumentu a ověření výsledku

Na konci průvodce budete mít plně funkční Word soubor obsahující klikatelné tlačítko, které můžete dále přizpůsobovat nebo propojit s VBA makry.

---

## Jak vytvořit forms2olecontrol v kódu – krok za krokem

### Krok 1: Inicializace DocumentBuilderu

Třída `DocumentBuilder` je vstupním bodem pro většinu úloh generování dokumentů v Aspose.Words. Poskytuje metody pro přidávání textu, obrázků, tabulek a, co je pro tento tutoriál podstatné, OLE ovládacích prvků.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité:**  
`DocumentBuilder` udržuje aktuální pozici kurzoru v dokumentu. Vytvořením brzy zajistíte, že jakékoli následné vložení – například **ActiveX tlačítko příkazu** – se objeví přesně tam, kde chcete.

### Krok 2: Vložení Forms2OleControl

Metoda `insertForms2OleControl` vrací objekt `Forms2OleControl`. Tento objekt představuje zástupný prvek OLE ovládacího prvku, který Word vykreslí jako ActiveX tlačítko.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Proč je to důležité:**  
Bez tohoto volání nemůžete manipulovat s vlastnostmi ovládacího prvku. Vrácený `Forms2OleControl` vám poskytuje plný přístup k metodě **setOleClassName**, atributům velikosti a dalším OLE‑specifickým nastavením.

### Krok 3: Specifikace třídy ActiveX pomocí setOleClassName

Word potřebuje vědět, jaký typ ActiveX ovládacího prvku má vykreslit. Název třídy pro standardní tlačítko příkazu je `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Proč je to důležité:**  
Metoda `setOleClassName` je mostem mezi obecnou OLE zástupnou značkou a konkrétním **ActiveX tlačítkem příkazu**. Použití nesprávného názvu třídy vede k prázdnému objektu nebo chybě při otevření dokumentu.

### Krok 4: Úprava velikosti Forms2OleControl

Tlačítko, které je příliš malé nebo příliš velké, vypadá neprofesionálně. Jeho rozměry můžete ovládat pomocí `setWidth` a `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Proč je to důležité:**  
Tyto vlastnosti tvoří **Forms2OleControl size**. Ovlivňují, jak tlačítko vypadá v uživatelském rozhraní Wordu, a zajišťují, že připojené makro má dostatek klikací plochy.

### Krok 5: Uložení dokumentu a testování

Po nastavení ovládacího prvku uložte dokument na vámi zvolené místo.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Otevřete `ActiveXButton.docx` v Microsoft Word. Měli byste vidět tlačítko s popiskem „CommandButton1“ (výchozí popisek). Kliknutí nic neprovede, pokud nepřidáte VBA makro, ale samotný ovládací prvek je plně funkční.

**Očekávaný výstup:**  

![Word dokument s vloženým ActiveX tlačítkem příkazu](/images/activeX-button.png "Snímek obrazovky Word dokumentu zobrazující nově vytvořené ActiveX tlačítko příkazu vložené pomocí kódu")

*Alt text obrázku obsahuje hlavní klíčové slovo pro přístupnost a SEO.*

---

## Pochopení třídy ActiveX Forms2OleControl

Třída `Forms2OleControl` obaluje nízkoúrovňovou OLE infrastrukturu, kterou Word používá pro ActiveX prvky. Dědí z `Shape`, což znamená, že na ni můžete také aplikovat typické formátování tvarů (např. okraje, otočení), pokud je to potřeba.

* **ActiveX tlačítko příkazu** – Nejčastější případ použití; můžete jej propojit s makrem pomocí vývojářských nástrojů Wordu.
* **setOleClassName metoda** – Určuje, kterou COM třídu Word načte; další platné hodnoty zahrnují `"Forms.TextBox.1"` a `"Forms.ComboBox.1"`.
* **Forms2OleControl size** – Řídí se pomocí `SetWidth`/`SetHeight`. Tyto metody přijímají body (1 pt = 1/72 in).

### Kdy použít Forms2OleControl vs. Content Controls

Pokud potřebujete jen jednoduchý vstup dat (např. obyčejné textové pole), vestavěné content controls ve Wordu jsou lehčí. Použijte `Forms2OleControl`, když vyžadujete plnou funkčnost ActiveX, jako je zpracování událostí nebo vlastní VBA interakce.

---

## Nastavení dalších vlastností (volitelné)

Zatímco základní kroky stačí k **vytvoření forms2olecontrol v kódu**, často chcete doladit vzhled nebo chování tlačítka.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Proč je to důležité:**  
`SetOleData` vám umožní zapsat libovolné hodnoty vlastností přímo do OLE proudu. To je nejflexibilnější způsob, jak přizpůsobit **ActiveX tlačítko příkazu** bez použití VBA.

---

## Časté problémy a řešení

| Příznak | Pravděpodobná příčina | Řešení |
|--------|-----------------------|--------|
| Tlačítko se zobrazuje jako šedý rámeček | Nesprávný název třídy předaný do `setOleClassName` | Ověřte, že řetězec je přesně `"Forms.CommandButton.1"` (rozlišuje velká a malá písmena) |
| Velikost se nezmění | Šířka/výška nastavena před vložením ovládacího prvku | Vždy volajte `SetWidth`/`SetHeight` **po** `InsertForms2OleControl` |
| Při otevření dokumentu se objeví chyba „OLE object not found“ | Chybí licence Aspose.Words (evaluační verze může omezovat OLE) | Aplikujte platnou licenci nebo použijte bezplatnou zkušební verzi s plnou podporou OLE |
| Popisek tlačítka zůstává „CommandButton1“ | `SetOleData` nebylo použito nebo makro nečte vlastnost | Použijte VBA makro k načtení vlastnosti `"Caption"` nebo nastavte popisek přes UI Wordu |

---

## Kompletní, spustitelný příklad

Níže je kompletní konzolová aplikace, kterou můžete zkopírovat, vložit a spustit. Demonstruje vše, co bylo v tomto tutoriálu probráno.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Vysvětlení jednotlivých částí**

* **Using directives** – Načítají jmenný prostor Aspose.Words potřebný pro `Document`, `DocumentBuilder` a `Forms2OleControl`.
* **Vytvoření dokumentu** – Instancuje prázdný Word soubor.
* **InsertForms2OleControl** – Umístí OLE ovládací prvek na aktuální pozici kurzoru builderu.
* **SetOleClassName** – Říká Wordu, že ovládací prvek je **ActiveX tlačítko příkazu**.
* **SetWidth / SetHeight** – Upravit **Forms2OleControl size** pro profesionální vzhled.
* **SetOleData (volitelné)** – Ukazuje, jak zapsat další vlastnosti, např. popisek.
* **Save** – Zapíše finální `.docx` soubor na disk.

Spusťte program (`dotnet run`) a otevřete `ActiveXButton.docx`. Uvidíte tlačítko, které můžete později propojit s makrem.

---

## Závěr

Nyní víte, jak **vytvořit forms2olecontrol v kódu** pomocí Aspose.Words, od inicializace `DocumentBuilder` až po konfiguraci **ActiveX tlačítka příkazu** pomocí `setOleClassName` a řízení **Forms2OleControl size**. Tento přístup vám umožní automatizovat složité Word dokumenty, vkládat interaktivní UI prvky a mít veškerou logiku uvnitř

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
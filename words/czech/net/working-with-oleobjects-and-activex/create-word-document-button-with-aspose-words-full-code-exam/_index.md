---
category: general
date: 2026-07-23
description: vytvořit tlačítko pro Word dokument pomocí Aspose.Words – krok za krokem
  průvodce vložením ActiveX CommandButton do souboru .docx
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: cs
lastmod: 2026-07-23
og_description: 'vytvořte tlačítko pro dokument Word s Aspose.Words: naučte se během
  několika minut vložit ActiveX CommandButton do souboru Word.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Tlačítko pro vytvoření Word dokumentu – kompletní průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Tlačítko pro vytvoření Word dokumentu s Aspose.Words – kompletní ukázka kódu
url: /cs/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# vytvořit tlačítko Word dokumentu s Aspose.Words – Kompletní programovací průvodce

Už jste někdy potřebovali **vytvořit tlačítko Word dokumentu**, ale nebyli jste si jisti, kterou API použít? Nejste sami — většina vývojářů narazí na překážku, když se snaží vložit interaktivní ovládací prvky do souboru .docx. Dobrá zpráva? S Aspose.Words pro .NET můžete vložit plně funkční ActiveX CommandButton do Word dokumentu během několika řádků kódu.

V tomto tutoriálu projdeme celý proces: od nastavení projektu, inicializace `DocumentBuilder`, vložení tlačítka pomocí `InsertForms2OleControl` a nakonec uložení souboru, aby Word rozpoznal ovládací prvek. Na konci budete mít připravený Word soubor, který obsahuje klikatelné tlačítko — bez nutnosti COM interop gymnastiky.

## Co budete potřebovat

- **.NET 6.0** nebo novější (kód funguje také s .NET Framework 4.6+).  
- **Aspose.Words for .NET** NuGet balíček (verze 23.9 nebo novější).  
- Základní znalost C# (syntaxi udržíme přívětivou pro začátečníky).  
- Visual Studio 2022 nebo jakékoli IDE, které preferujete.

To je vše — žádné další COM reference, žádný Office interop, jen čistý spravovaný kód.

---

## Krok 1: Nastavte Aspose.Words pro **vytvoření tlačítka Word dokumentu**

Nejprve přidejte balíček Aspose.Words do svého projektu:

```bash
dotnet add package Aspose.Words
```

Nebo pokud používáte Visual Studio NuGet UI, vyhledejte „Aspose.Words“ a klikněte na **Install**. Tento jediný řádek vám poskytne přístup k `Document`, `DocumentBuilder` a metodě `InsertForms2OleControl`, kterou později budeme potřebovat.

> **Tip:** Udržujte své NuGet balíčky aktuální; novější verze často obsahují opravy chyb pro práci s ActiveX.

## Krok 2: Inicializujte **DocumentBuilder** pro **ActiveX CommandButton**

Nyní vytvoříme nový Word dokument a spustíme `DocumentBuilder`. Představte si `DocumentBuilder` jako štětec, který vám umožní kreslit obsah na plátno.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Všimněte si, že importujeme `System.Drawing` — struct `Rectangle` určuje umístění a velikost tlačítka. Zde bude umístěn **ActiveX CommandButton**.

## Krok 3: Použijte **InsertForms2OleControl** k **přidání CommandButton**

Zde je jádro tutoriálu: vložení samotného tlačítka. Metoda `InsertForms2OleControl` přijímá tři argumenty — typ ovládacího prvku, `Rectangle` a volitelně název. Použijeme `OleControlType.CommandButton` k určení požadovaného ovládacího prvku.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Ten jediný volání udělá hodně:

1. **Vytvoří** OLE objekt uvnitř Word souboru.  
2. **Zaregistruje** jej jako ActiveX CommandButton, který Word zobrazí jako kliknutelný UI prvek.  
3. **Umístí** jej podle poskytnutého obdélníku.

Pokud potřebujete změnit popisek tlačítka nebo jiné vlastnosti, můžete tak učinit po vložení přístupem k podkladovému `OleFormat`. Ve většině scénářů je výchozí popisek („CommandButton1“) dostačující.

## Krok 4: Uložte Word dokument obsahující **CommandButton**

Ukládání je jednoduché — stačí zadat složku, do které máte právo zapisovat. Přípona souboru musí být `.docx`, aby tlačítko přežilo celý proces.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Když otevřete `CommandButton.docx` v Microsoft Word, uvidíte malé tlačítko v levém horním rohu první stránky. Kliknutí na něj nic neprovedne (to by vyžadovalo VBA), ale ovládací prvek je plně funkční a může být později napojen.

> **Proč to funguje:** Aspose.Words zapisuje OLE stream přímo do balíčku DOCX, čímž obchází potřebu, aby Word generoval ovládací prvek za běhu. To zaručuje, že se tlačítko objeví přesně tam, kam jste jej umístili.

## Krok 5: Ověřte tlačítko ve Wordu

1. Spusťte Microsoft Word.  
2. Přejděte na **File → Open** a vyberte `CommandButton.docx`.  
3. Měli byste vidět obdélníkové tlačítko označené „CommandButton1“.  

Pokud tlačítko nevidíte, ujistěte se, že je povolen **Design Mode** (Developer → Design Mode). Tím se přepne vizuální reprezentace ActiveX ovládacích prvků.

## Krok 6: Pokročilé možnosti — přizpůsobení **ActiveX CommandButton**

Níže jsou uvedeny některé rychlé úpravy, které vám mohou přijít vhod:

| Cíl | Ukázka kódu |
|------|--------------|
| Změnit popisek | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Nastavit název makra (vyžaduje podporu makra ve Word) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Změnit velikost po vložení | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Tyto úryvky ukazují flexibilitu `InsertForms2OleControl`. Můžete dokonce vložit jiné ActiveX ovládací prvky, jako `CheckBox` nebo `ListBox`, výměnou enumu `OleControlType`.

## Kompletní funkční příklad

Níže je kompletní, připravený program ke zkopírování, který **vytváří tlačítko Word dokumentu** od nuly:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Očekávaný výstup po spuštění programu:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Otevřete výsledný soubor a uvidíte tlačítko přesně tam, kde ho kód umístil.

## Časté úskalí a jak se jim vyhnout

- **Chybějící reference na `System.Drawing`** — struct `Rectangle` je zde; bez ní kompilátor vyhlásí chybu.  
- **Použití starší verze Aspose.Words** — starší vydání plně nepodporovala `InsertForms2OleControl`. Aktualizujte na nejnovější stabilní balíček.  
- **Ukládání jako `.doc` místo `.docx`** — OLE stream je v starším binárním formátu odstraněn, což způsobí, že tlačítko zmizí.  
- **Spouštění na serveru bez grafického rozhraní a bez nainstalovaného Wordu** — tlačítko bude stále v souboru, ale bez Wordu jej nemůžete zobrazit. To je v pořádku pro automatizované generování pipeline.

## Další kroky — rozšíření workflow **vytvoření tlačítka Word dokumentu**

Nyní, když ovládáte základy, zvažte následující pokročilé nápady:

- **Připojit VBA makra** k tlačítku pro vlastní obchodní logiku.  
- **Generovat více tlačítek** ve smyčce pro dynamické formuláře.  
- **Kombinovat s Aspose.PDF** pro export stejného dokumentu do PDF při zachování vizuálního rozvržení (tlačítko se v PDF stane statickým obrázkem).  
- **

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
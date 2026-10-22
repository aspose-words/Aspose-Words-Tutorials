---
category: general
date: 2026-09-27
description: Programově vytvořte dokument Word se skupinovým tvarem pomocí Aspose.Words
  v C#. Postupujte podle tohoto průvodce krok za krokem, abyste vygenerovali soubor
  a získali užitečné tipy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: cs
lastmod: 2026-09-27
og_description: Programově vytvořte dokument Word se skupinovým tvarem pomocí Aspose.Words.
  Tento tutoriál vás provede kompletním kódem v C#, vysvětlí každý krok a ukáže konečný
  výsledek.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Programaticky vytvořit dokument Word se skupinovým tvarem – průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Programově vytvořit dokument Word se skupinovým tvarem
url: /cs/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programaticky vytvořit Word dokument se skupinovým tvarem

Pokud potřebujete **programaticky vytvořit Word dokument**, který obsahuje seskupený výkres, tento průvodce vám přesně ukáže, jak to provést pomocí Aspose.Words pro .NET. Ať už vytváříte generátor smluv, nástroj pro tvorbu reportů nebo aplikaci pro vyplňování formulářů, naučíte se kompletní C# kód, proč je každé volání API důležité a jak řešit běžné okrajové případy.

Vytvoření seskupeného tvaru ve Wordu může být obtížné, protože model objektů Wordu zachází se skupinovými tvary jako s kontejnery pro jiné kreslicí objekty. Tento tutoriál nejen odpovídá na otázku **how to create group shape word** dokumentů, ale také ukazuje, jak vložit prostý textový StructuredDocumentTag (SDT) do skupiny, aby tvar mohl obsahovat editovatelný obsah.

## Co dosáhnete

- Inicializovat nový prázdný Word dokument pomocí `Document` a `DocumentBuilder`.
- Vložit `GroupShape` na aktuální pozici kurzoru.
- Přidat prostý textový `StructuredDocumentTag` (SDT) do skupinového tvaru.
- Uložit soubor jako `.docx`, který lze otevřít v Microsoft Word.
- Pochopit klíčové vlastnosti `GroupShape` a `StructuredDocumentTag` pro budoucí rozšíření.

### Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+).
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`).
- IDE pro C#, jako je Visual Studio 2022 nebo VS Code s rozšířením C#.

---

## Programaticky vytvořit Word dokument – nastavení projektu

1. **Vytvořte nový konzolový projekt**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Otevřete projekt ve svém IDE** a nahraďte obsah souboru `Program.cs` kódem uvedeným v následujících sekcích.

> **Pro tip:** Udržujte složku projektu čistou; Aspose.Words zapisuje výstupní soubor do pracovního adresáře, pokud neposkytnete absolutní cestu.

## Krok 1: Inicializace dokumentu a builderu

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Proč je to důležité:**  
`Document` představuje celý Word soubor, zatímco `DocumentBuilder` vám umožňuje umisťovat nové prvky bez ručního procházení stromu uzlů. Nastavením rozměrů stránky již na začátku zajistíte, že skupinový tvar nepřeteče stránku.

## Krok 2: Vložení GroupShape na aktuální pozici kurzoru

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Vysvětlení:**  
`GroupShape` je kreslicí objekt, který může obsahovat další tvary, obrázky nebo textová pole. Nastavením `Width`, `Height`, `Left` a `Top` určíte jeho přesné umístění na stránce. Metoda `InsertNode` umístí tvar do hlavního toku dokumentu a chová se jako plovoucí objekt.

## Krok 3: Přidání prostého textového StructuredDocumentTag (SDT) do skupiny

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Proč použít SDT?**  
StructuredDocumentTags jsou nativní ovládací prvky obsahu ve Wordu. Umožňují uživatelům přímo v uloženém dokumentu upravovat text a lze je programově později přistupovat pro extrakci dat. Umístění SDT uvnitř skupinového tvaru vám umožní kombinovat vizuální seskupení s editovatelným obsahem.

## Krok 4: Uložení dokumentu

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Výsledek:**  
Otevřením `GroupShapeDemo.docx` v Microsoft Word se zobrazí plovoucí obdélník (skupinový tvar) obsahující textový zástupce s textem „Enter text here“. Uživatelé mohou kliknout dovnitř tvaru a psát přímo.

### Očekávaný výstup (konceptuální)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Vnější rámeček je `GroupShape`; vnitřní šedá oblast je `StructuredDocumentTag`.

## Jak vytvořit group shape word – další úvahy

### Přidání dalších podřízených tvarů

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Řízení stylu obtékání

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Okrajový případ: Prázdný skupinový tvar

`GroupShape` bez podřízených objektů se vykreslí jako neviditelný zástupce. Vždy ověřte, že je přidán alespoň jeden podřízený (např. SDT nebo obrázek); jinak může Word během ukládání skupinu zahodit.

### Poznámka o kompatibilitě

Aspose.Words 23.10+ plně podporuje `GroupShape` a `StructuredDocumentTag`. Pokud cílíte na starší verze, metoda `AppendChild` se může chovat odlišně a může být nutné po uložení zavolat `UpdatePageLayout`.

## Kompletní spustitelný příklad

Zkopírujte celý úryvek níže do souboru `Program.cs` a spusťte projekt. Kód obsahuje všechny výše uvedené kroky v jednom samostatném programu.



## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Vytvořit skupinový tvar ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Vytvořit prázdný Word dokument s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
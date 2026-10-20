---
category: general
date: 2026-10-20
description: Naučte se, jak vytvořit prázdný dokument Word, seskupit tvary ve Wordu,
  nastavit barvu výplně tvaru a použít typ obtékání inline s kompletním příkladem
  v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: cs
lastmod: 2026-10-20
og_description: Vytvořte prázdný dokument Word, seskupte tvary ve Wordu a nastavte
  barvu výplně tvaru s typem obtékání inline pomocí Aspose.Words a C#. Postupujte
  podle kompletního tutoriálu.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Vytvořte prázdný dokument Word a seskupte tvary ve Wordu – krok za krokem
  průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vytvořit prázdný dokument Word a seskupit tvary ve Wordu pomocí Aspose.Words
url: /cs/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word a seskupit tvary ve Wordu

Pokud potřebujete **vytvořit prázdný dokument Word**, který obsahuje více tvarů fungujících jako jedna jednotka, tento návod vám přesně ukáže, jak na to. Uvidíte, jak **seskupit tvary ve Wordu**, nastavit barvu výplně tvaru a použít **wrap type inline** — vše pomocí stručného, spustitelného C# programu.

Tutoriál vás provede každým řádkem kódu, vysvětlí, proč je každý krok důležitý, a upozorní na běžné úskalí. Na konci budete mít soubor .docx, který zobrazuje obdélník a textové pole seskupené dohromady, připravené k dalšímu automatizování.

## Co se naučíte

* Jak inicializovat prázdný soubor Word pomocí Aspose.Words.
* Správný způsob vytvoření **GroupShape** a přidání podřízených tvarů.
* Techniky pro **set shape fill color** a řízení umístění.
* Použití **wrap type inline**, aby se skupina chovala jako jediný inline objekt.
* Jak uložit a ověřit výsledek.

Předchozí zkušenost s Aspose.Words není vyžadována, ale měli byste být obeznámeni se základní syntaxí C# a mít nainstalované Visual Studio (nebo jiné IDE).

## Požadavky

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 or later | Poskytuje runtime pro C# projekt. |
| Aspose.Words for .NET (latest version) | Poskytuje třídy `Document`, `DocumentBuilder` a třídy tvarů použité v příkladu. |
| A writable folder path | Volání `doc.Save` potřebuje platný adresář pro zápis výstupního souboru. |
| Basic C# knowledge | Umožňuje vám sledovat kód a upravovat jej pro vlastní scénáře. |

Nainstalujte Aspose.Words přes NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Krok 1: Vytvořit prázdný dokument Word

Prvním krokem je **vytvořit prázdný dokument Word**. Třída `Document` z Aspose.Words představuje Word soubor v paměti a `DocumentBuilder` poskytuje pohodlné API pro jeho úpravy.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité*: Začátek s čistým dokumentem zaručuje, že přidaný skupinový tvar bude jediným obsahem, což usnadňuje ověření.

## Krok 2: Definovat skupinový tvar s wrap type inline

**GroupShape** funguje jako kontejner pro další tvary. Nastavením jeho `WrapType` na `Inline` zajistíte, že skupina se bude chovat jako jediný inline objekt v toku odstavce.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Proč je to důležité*: Použití **wrap type inline** zabraňuje tomu, aby se skupina oddělila od okolního textu, což je nezbytné, pokud chcete, aby se skupina pohybovala jako jednotka.

## Krok 3: Přidat obdélník a nastavit barvu výplně tvaru

Obdélník je běžný vizuální prvek. Konstruktor `Shape` přijímá `ShapeType`; poté specifikujeme rozměry a barvu výplně.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Proč je to důležité*: Vlastnost `FillColor` ukazuje **set shape fill color** v praxi, přičemž obdélníku dává světle modré pozadí, které ve finálním dokumentu vyniká.

## Krok 4: Přidat textové pole – jak efektivně seskupit tvary

Textové pole poskytuje editovatelný text uvnitř skupiny. Umístěte jej relativně ke koordinátovému systému skupiny úpravou vlastnosti `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Proč je to důležité*: Tento krok odpovídá na otázku **how to group shapes** — přidáním každého podřízeného tvaru do stejné instance `GroupShape`. Posun `Top` zajišťuje, že se textové pole objeví pod obdélníkem, což demonstruje přesnou kontrolu rozvržení.

## Krok 5: Vložit dokončený skupinový tvar do dokumentu

Jakmile skupina obsahuje oba podřízené tvary, vložte ji na aktuální pozici builderu.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Proč je to důležité*: Vložení skupiny jako jediného uzlu zaručuje, že Word bude považovat obdélník a textové pole za jeden logický objekt, čímž zachová jejich relativní pozice během úprav.

## Krok 6: Uložit dokument a ověřit výstup

Nakonec zapište dokument na disk. Nahraďte `YOUR_DIRECTORY` skutečnou cestou na vašem počítači.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Když otevřete `GroupShape.docx` v Microsoft Word, měli byste vidět světle modrý obdélník s textovým polem označeným „Grouped text“, umístěným přímo pod ním. Výběrem kterékoli z forem vyberete celou skupinu, což potvrzuje, že **group shapes in Word** funguje podle očekávání.

### Očekávaný výsledek

* Soubor .docx obsahující jediný odstavec.
* V odstavci inline skupina, která vypadá jako jeden kompozitní objekt.
* Obdélník je vyplněn světle modrou barvou a textové pole zobrazuje „Grouped text“.

![Snímek obrazovky vygenerovaného dokumentu Word](grouped_shapes.png){.center width=600 alt="Snímek obrazovky prázdného dokumentu Word se seskupeným obdélníkem a textovým polem vytvořeným pomocí Aspose.Words"}

## Časté otázky a řešení okrajových případů

### Co když potřebuji, aby skupina plavala místo inline?

Nahraďte `WrapType.Inline` za `WrapType.TopBottom` (nebo jinou hodnotu výčtu `WrapType`). Plovoucí skupiny lze umístit nezávisle na toku odstavce, ale ztratí automatické inline zarovnání.

### Mohu přidat další tvary, například kruhy nebo obrázky?

Ano. Vytvořte další objekty `Shape` s `ShapeType.Ellipse` nebo `ShapeType.Image`, nakonfigurujte jejich vlastnosti a zavolejte `group.AppendChild(newShape)`. Skupina se automaticky rozšíří tak, aby zahrnovala nové ohraničení, pokud odpovídajícím způsobem aktualizujete `group.Bounds`.

### Jak změnit celkovou velikost skupiny po přidání podřízených tvarů?

Upravte `group.Bounds` po přidání všech podřízených tvarů, nebo programově vypočítejte sjednocení ohraničení podřízených tvarů. Tím zajistíte, že oblast pro testování zásahu skupiny odpovídá vizuálnímu obsahu.

### Co když výstupní složka neexistuje?

Aspose.Words vyhodí `DirectoryNotFoundException`. Nejprve vytvořte adresář:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Funguje to s .NET Framework místo .NET Core?

Všechny použité API (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) jsou k dispozici ve verzi Aspose.Words pro .NET Framework, takže stejný kód funguje beze změny.

## Profesionální tipy

* **Tip pro výkon** – Znovu použijte jedinou instanci `DocumentBuilder` při vkládání mnoha skupin; vytvoření nového builderu pro každou skupinu přidává režii.
* **Vizuelní konzistence** – Nastavte `rectangle.StrokeColor` tak, aby odpovídala `FillColor` pro plynulý vzhled, nebo nastavte `rectangle.LineWidth = 0`, aby se skryl okraj.
* **Ladění** – Zavolejte `doc.UpdatePageLayout()` před uložením, pokud měníte mnoho tvarů; tím přinutíte Word přepočítat rozvržení a můžete předejít neočekávanému oříznutí.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **seskupit tvary ve Wordu**, **nastavit barvu výplně tvaru** a použít **wrap type inline** pomocí Aspose.Words pro .NET. Kompletní příklad demonstruje standardní přístup k vytváření složených grafických prvků, které se ve Wordu chovají jako jeden objekt.

Zde můžete dále zkoumat:

* Přidání dalších tvarů, například obrázků nebo grafů.
* Experimentování s různými hodnotami `WrapType` pro plovoucí skupiny.
* Automatizace hromadného generování seskupených diagramů napříč více dokumenty.

Neváhejte přizpůsobit kód svým vlastním automatizačním scénářům a sdílet své výsledky v komentářích!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit skupinový tvar v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvořit prázdný dokument Word s Aspose.Words – krok za krokem průvodce](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Jak uložit PDF z Wordu s inline tvary – kompletní průvodce](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
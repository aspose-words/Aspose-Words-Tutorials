---
category: general
date: 2026-08-10
description: Vytvořte dokument Word programově pomocí Aspose.Words, naučte se seskupovat
  více tvarů ve Wordu, přidat obdélník do Wordu a vytvořit skupinový tvar v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: cs
lastmod: 2026-08-10
og_description: Vytvořte programově dokument Word pomocí Aspose.Words. Tento průvodce
  vám ukáže, jak seskupit více tvarů ve Wordu, přidat obdélník do Wordu a vložit ovládací
  prvek pro prostý text, vše v C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Vytvořte Word dokument programově – seskupte tvary v C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Vytvořit Word dokument programově a seskupit tvary v C#
url: /cs/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu programově a seskupení tvarů v C#

Pokud potřebujete **create word document programmatically**, tento tutoriál vám ukáže, jak vytvořit soubor DOCX pomocí Aspose.Words a **group multiple shapes word** dohromady. Také se podíváme na **add rectangle to word** a **how to create group shape**, které obsahuje jak obdélník, tak elipsu, plus prostý textový StructuredDocumentTag pro vstup uživatele.

Na konci získáte připravený Word soubor, který obsahuje seskupený tvar obdélník‑elipsa a ovládací prvek obsahu, kde uživatel může zadat jméno. Po spuštění kódu není potřeba žádná ruční úprava ve Wordu.

## Co budete potřebovat

- .NET 6.0 nebo novější (ukázka cílí na .NET 6, ale funguje jakákoli recentní verze .NET)
- Licence Aspose.Words pro .NET (bezplatná zkušební verze funguje pro testování)
- Visual Studio 2022 nebo jakékoli C# IDE, které preferujete
- Základní znalost syntaxe C#

## Vytvoření Word dokumentu programově – celkový pracovní postup

Proces se skládá ze tří logických fází:

1. **Initialize** `Document` a `DocumentBuilder` – základ pro jakýkoli Word soubor, který generujete.
2. **Build a group shape**, který obsahuje obdélník a elipsu – ukazuje **group multiple shapes word** a **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – prostý textový ovládací prvek, který umožňuje koncovým uživatelům vyplnit data, ilustrující **add rectangle to word** jako součást celkového rozvržení dokumentu.

Níže je kompletní spustitelný kód následovaný krok‑za‑krokem rozborem.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Krok 1 – Inicializace dokumentu a builderu
`Document` objekt představuje celý soubor DOCX, zatímco `DocumentBuilder` poskytuje pohodlné API pro přidávání obsahu. Jejich inicializace je první požadavek, kdykoli **create word document programmatically**.

> **Pro tip:** Pokud plánujete znovu použít stejný dokument v několika operacích, udržujte jedinou instanci `DocumentBuilder`, abyste se vyhnuli zbytečnému vytváření objektů.

### Krok 2 – Vytvoření kontejneru pro skupinový tvar
`Shape` s `ShapeType.Group` funguje jako plátno, které může obsahovat další tvary. Nastavení `Width` a `Height` definuje ohraničující rámeček pro skupinu. Toto je jádro **how to create group shape** v Aspose.Words.

> **Edge case:** Pokud je šířka skupiny menší než součet šířek jejích potomků, potomci budou oříznuti. Vždy zajistěte, aby byla skupina dostatečně velká pro všechny podřízené tvary.

### Krok 3 – Přidání obdélníku do Wordu
Obdélník je vytvořen pomocí `ShapeType.Rectangle`. Jeho vlastnosti `Left` a `Top` ho umisťují relativně k počátku skupiny. Tento krok demonstruje **add rectangle to word** a ukazuje, jak můžete řídit přesné umístění.

> **Common mistake:** Zapomenutí nastavit `Left`/`Top` způsobí, že se obdélník objeví na výchozím počátku skupiny (0,0), což může překrývat jiné potomky.

### Krok 4 – Přidání elipsy (kruhu) do skupiny
Elipsa je přidána stejným způsobem jako obdélník, ale s `ShapeType.Ellipse`. `Left = 210` ji posune vpravo od obdélníku, čímž vytvoří vizuálně odlišný pár tvarů ve stejné skupině.

> **Why use a group?** Seskupování vám umožní později přesunout, otočit nebo změnit velikost obou tvarů najednou jednou operací, zachovávajíc jejich relativní rozložení.

### Krok 5 – Vložení dokončeného skupinového tvaru do dokumentu
`builder.InsertNode(groupShape)` umístí celou skupinu na aktuální pozici kurzoru. Protože skupina již obsahuje své potomky, není potřeba další volání insert pro obdélník nebo elipsu.

### Krok 6 – Vytvoření prostého textového StructuredDocumentTag (SDT)
StructuredDocumentTag je ovládací prvek obsahu, který koncoví uživatelé mohou vyplnit při otevření dokumentu ve Wordu. Nastavení `Title = "CustomerName"` dává ovládacímu prvku smysluplný identifikátor, který je užitečný pro pozdější extrakci dat.

> **Why a plain‑text SDT?** Omezuje vstup na prostý text, čímž zabraňuje neúmyslnému formátování, které by mohlo narušit následné zpracování.

### Krok 7 – Uložení dokumentu
`doc.Save("GroupAndSDT.docx")` zapíše soubor na disk. Výsledný DOCX obsahuje seskupené tvary a SDT. Otevřením souboru v Microsoft Word se zobrazí obdélník vedle kruhu, oba vybratelné jako jeden objekt, následovaný zástupným textem „Enter name here …“.

#### Očekávaný výstup
- Soubor pojmenovaný **GroupAndSDT.docx** ve složce, kde se spouští.
- Ve Wordu: seskupený tvar (obdélník + elipsa), který můžete přesunout jako jednotku.
- Bezprostředně pod skupinou šedě zvýrazněný ovládací prvek, který vyzývá uživatele k zadání jména.

## Další varianty a osvědčené postupy

### Použití různých typů tvarů
Můžete nahradit `ShapeType.Rectangle` nebo `ShapeType.Ellipse` jakýmkoli jiným `ShapeType` (např. `ShapeType.Polygon`, `ShapeType.Line`). Logika seskupování zůstává stejná.

### Nastavení barvy výplně a okrajů
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Přidání výplně a obrysu zlepšuje vizuální odlišení, zejména když je dokument sdílen s netechnickými zainteresovanými stranami.

### Otočení celé skupiny
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Otočení skupiny je efektivnější než otáčení každého potomka zvlášť.

### Export do PDF
Pokud potřebujete PDF verzi, jednoduše zavolejte:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Všechny seskupené tvary a SDT (zobrazený jako textové pole) se objeví v PDF.

## Časté úskalí a jak se jim vyhnout

| Příznak | Příčina | Řešení |
|---------|-------|

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit skupinový tvar ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – Průvodce krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Vytvořit prázdný Word dokument se stínovaným obdélníkovým tvarem – Průvodce krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
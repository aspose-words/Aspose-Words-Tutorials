---
category: general
date: 2026-08-04
description: Uložte soubor DOCX programově při přidání obdélníkového tvaru a seskupení
  tvarů ve Wordu. Naučte se nastavit rozměry tvaru a vytvořit textové pole programově.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: cs
lastmod: 2026-08-04
og_description: Uložte soubor docx pomocí C# přidáním obdélníkového tvaru, seskupením
  tvarů ve Wordu, nastavením rozměrů tvaru a programovým vytvořením textového pole.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Uložení souboru docx se seskupenými tvary ve Wordu – krok za krokem v C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Uložit soubor docx se seskupenými tvary ve Wordu pomocí C#
url: /cs/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uložení souboru docx se seskupenými tvary ve Wordu pomocí C#

Pokud potřebujete **save docx file**, který obsahuje několik tvarů uspořádaných dohromady, tento průvodce vám ukáže, jak to provést v C#. Naučíte se, jak **add rectangle shape**, seskupit více tvarů v dokumentu Word, **set shape dimensions** a **create textbox programmatically**. Řešení funguje s nejnovější verzí Aspose.Words pro .NET a běží na .NET 6 nebo novějším.

Tutoriál vás provede každým krokem, od nastavení projektu až po finální volání `doc.Save`. Na konci budete mít znovupoužitelný úryvek kódu, který můžete vložit do libovolného konzolového nebo ASP.NET projektu. Nejsou vyžadovány žádné externí skripty ani ruční úpravy souboru DOCX.

## Požadavky

* .NET 6 SDK (nebo novější) nainstalován.
* Platná licence pro **Aspose.Words for .NET** (bezplatná zkušební verze funguje pro testování).
* Visual Studio 2022, VS Code nebo jakékoli IDE, které dokáže sestavit .NET projekty.

Kód používá pouze jmenný prostor Aspose.Words, takže nejsou potřeba žádné další balíčky NuGet.

## Uložení souboru docx se seskupenými tvary ve Wordu

Jádrem řešení je vytvoření `GroupShape`, který obsahuje obdélník a textové pole, následné vložení skupiny do dokumentu a volání `doc.Save`. Následující sekce rozdělují proces na zvládnutelné části.

### 1. Vytvoření nového dokumentu a builderu

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je tento krok důležitý* – Čerstvý objekt `Document` představuje prázdný soubor *.docx*. `DocumentBuilder` poskytuje vysoce‑úrovňové metody jako `InsertNode`, které použijeme k umístění skupinového tvaru.

### 2. Přidání obdélníkového tvaru do skupiny

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Proč je tento krok důležitý* – Operace **add rectangle shape** ukazuje, jak definovat vizuální prvek s přesnou velikostí a pozicí. Obdélník žije uvnitř `group`, takže pozdější přesun skupiny automaticky přesune i obdélník.

### 3. Seskupení tvarů v dokumentu Word

Třída `GroupShape` agreguje více kreslicích objektů. Seskupení je užitečné, když chcete zacházet s několika objekty jako s jednou jednotkou (např. přesouvat, otáčet nebo kopírovat je společně).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Proč seskupujeme* – Seskupení snižuje složitost rozvržení. Místo umisťování každého tvaru jednotlivě na stránku upravujete jednou `Left`, `Top`, `Width` a `Height` skupiny.

### 4. Nastavení rozměrů tvaru pro přesné rozvržení

Jak skupina, tak její podřízené tvary potřebují explicitní rozměry; jinak Word použije výchozí velikosti, které nemusí odpovídat vašemu návrhu.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Proč nastavujeme rozměry* – Přesné měření zajišťuje, že obdélník a textové pole se nebudou neúmyslně překrývat a že finální **save docx file** odpovídá zamýšlenému rozvržení.

### 5. Programové vytvoření textového pole uvnitř skupiny

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Proč je tento krok důležitý* – Segment **create textbox programmatically** ukazuje, jak vložit bohatý text do tvaru. Použití `Paragraph` a `Run` vám poskytuje plnou kontrolu nad formátováním později.

### 6. Vložení skupinového tvaru a **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Proč je tento poslední krok důležitý* – Volání `InsertNode` umístí seskupené tvary přesně tam, kde se nachází kurzor builderu. Metoda `doc.Save` provádí operaci **save docx file**, zapisuje plně funkční Word dokument na disk.

> **Výsledek:** Otevření *GroupShape.docx* v Microsoft Word zobrazí obdélník vlevo a textové pole vpravo, oba uzamčené dohromady v jedné skupině. Skupinu můžete přesunout jako celek, změnit její velikost nebo použít další formátování.

## Kompletní, spustitelný příklad

Zkopírujte níže uvedený kód do nového konzolového projektu (`dotnet new console`) a spusťte `dotnet run`. Program vytvoří `GroupShape.docx` ve výstupním adresáři projektu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Očekávaný výstup

* Soubor pojmenovaný **GroupShape.docx** se objeví ve výstupním adresáři.
* Otevření souboru zobrazí obdélníkový tvar vlevo a textové pole obsahující „Grouped text“ vpravo, oba uzamčené dohromady.
* Výběrem kterékoli z tvarů se přesune celá skupina, což potvrzuje, že funkčnost **group shapes word** funguje podle očekávání.

## Běžné varianty a okrajové případy

| Situace | Doporučení |
|-----------|----------------|
| Potřeba více než dvou tvarů | Přidejte další objekty `Shape` do `group` před voláním `builder.InsertNode`. |
| Chcete, aby se skupina objevila na konkrétní stránce | Posuňte kurzor builderu pomocí `builder.MoveToDocumentEnd()` nebo `builder.MoveToPage(pageNumber)`. |
| Požadujete jiné jednotky (např. centimetry) | Použijte `ConvertUtil.InchToPoint(1.0)` pro převod palců na body, jednotku, kterou Word očekává. |
| Chcete, aby textové pole obtékalo text | Nastavte `textBox.TextBoxWrap = TextBoxWrapType.Square` po vytvoření textového pole. |
| Práce se staršími verzemi .NET Framework | Stejné API funguje s .NET Framework 4.7+, ale ujistěte se, že odkazujete na správnou verzi Aspose.Words. |

**Tip:** Vždy nastavujte `Width` a `Height` skupiny *po* přidání všech podřízených tvarů. Tím zajistíte, že skupina plně obklopí svůj obsah a zabrání oříznutí při otevření dokumentu ve Wordu.

## Závěr

Nyní víte, jak **save docx file** při **add rectangle shape**, **group shapes word**, **set shape dimensions** a **create textbox programmatically** pomocí Aspose.Words pro .NET. Kompletní příklad ukazuje čistý, opakovatelný vzor, který můžete přizpůsobit složitějším rozvržením, jako jsou grafy, obrázky,

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich vlastních projektech.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
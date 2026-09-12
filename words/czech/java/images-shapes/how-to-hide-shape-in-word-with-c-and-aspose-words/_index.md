---
category: general
date: 2026-09-11
description: Naučte se, jak skrýt tvar ve Wordu pomocí C#. Tento průvodce také ukazuje,
  jak vložit obdélníkový tvar a vložit tvar do dokumentu Word pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: cs
lastmod: 2026-09-11
og_description: Jak skrýt tvar ve Wordu pomocí C# a Aspose.Words. Postupujte podle
  podrobného návodu k vložení obdélníkového tvaru a správě tvarů v dokumentu Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Jak skrýt tvar ve Wordu – kompletní průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Jak skrýt tvar ve Wordu pomocí C# a Aspose.Words
url: /cs/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak skrýt tvar ve Wordu pomocí C# a Aspose.Words

Pokud potřebujete ve Wordu skrýt tvar a zároveň zachovat tvar ve struktuře dokumentu, tento tutoriál vám přesně ukáže, jak na to. Pomocí Aspose.Words pro .NET můžete vložit obdélníkový tvar, skrýt jej a stále si zachovat jeho pozici pro pozdější zpracování.

Automatizace Wordu často vyžaduje jemnou kontrolu nad tvary — ať už generujete šablony, připravujete zprávy nebo budujete službu pro úpravu dokumentů. Na konci tohoto průvodce budete schopni:

* Vložit obdélníkový tvar do Word dokumentu (`insert rectangle shape`).
* Skrýt libovolný tvar bez jeho smazání (`how to hide shape in word`).
* Uložit výsledek a ověřit, že skrytý tvar se neobjeví v renderovaném pohledu (`insert shape into word document`).

Příklad funguje s Aspose.Words 24.10 nebo novějším a cílí na .NET 6.0+, ale koncepty platí i pro starší verze.

## Požadavky

* **Aspose.Words for .NET** ≥ 24.10. Bezplatnou dočasnou licenci můžete získat na webu Aspose.
* **.NET SDK** 6.0 nebo novější nainstalovaný na vašem počítači.
* Vývojové prostředí, například Visual Studio 2022, VS Code nebo Rider.
* Základní znalost C# a konceptu Word Open XML (volitelné, ale užitečné).

## Jak skrýt tvar ve Wordu pomocí Aspose.Words

Níže je kompletní, spustitelný program, který demonstruje celý workflow — od vytvoření dokumentu po vložení obdélníkového tvaru a jeho následné skrytí.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Vysvětlení každého kroku

1. **Create a new document** – `Document` represents the Word file in memory. `DocumentBuilder` provides a fluent API for inserting content.  
   **Vytvoření nového dokumentu** – `Document` představuje soubor Word v paměti. `DocumentBuilder` poskytuje plynulé API pro vkládání obsahu.

2. **Insert rectangle shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions are expressed in points (1 pt ≈ 1/72 in). This satisfies the `insert rectangle shape` requirement.  
   **Vložení obdélníkového tvaru** – `InsertShape` vytvoří kreslicí objekt typu `Rectangle`. Rozměry jsou vyjádřeny v bodech (1 pt ≈ 1/72 in). Tím je splněna požadavek `insert rectangle shape`.

3. **Hide the shape** – Setting `Shape.Hidden = true` marks the shape as hidden in the Word markup (`<w:hidden/>`). The shape remains part of the document tree, so you can later unhide it or reference it programmatically. This is the core of `how to hide shape in word`.  
   **Skrytí tvaru** – Nastavením `Shape.Hidden = true` označíte tvar jako skrytý v markup Wordu (`<w:hidden/>`). Tvar zůstává součástí stromu dokumentu, takže jej můžete později odskrýt nebo na něj odkazovat programově. Toto je jádro `how to hide shape in word`.

4. **Save the file** – The document is written to `output.docx`. When opened in Microsoft Word, the rectangle will not be visible, but it still exists in the XML and can be inspected with a ZIP viewer or the Open XML SDK.  
   **Uložení souboru** – Dokument je zapsán do `output.docx`. Po otevření v Microsoft Word nebude obdélník viditelný, ale stále existuje v XML a lze jej prozkoumat pomocí ZIP prohlížeče nebo Open XML SDK.

### Očekávaný výsledek

Otevřete `output.docx` v Microsoft Word:

* Dokument vypadá prázdně — žádný viditelný tvar.
* Pokud prozkoumáte podkladové XML (`word/document.xml`), najdete element `<w:pict>` s atributem `<w:hidden/>`, což potvrzuje, že tvar je přítomen, ale skrytý.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Skrytý tvar lze opět zobrazit nastavením `Hidden = false` a opětovným uložením dokumentu.

## Vložení obdélníkového tvaru do Word dokumentu

Ačkoliv je hlavním cílem skrýt tvar, mnoho scénářů začíná nejprve vložením tvaru. Metoda `InsertShape` podporuje mnoho hodnot `ShapeType`, včetně `Rectangle`, `Ellipse`, `Line` a vlastních obrázků.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Proč použít obdélník?**  
Obdélník poskytuje čistý, osově zarovnaný kontejner, který může obsahovat text, obrázky nebo jiné vnořené tvary. Často slouží jako zástupný prvek pro dynamický obsah, jako jsou tabulky nebo grafy. Vložením obdélníku jako první zachováte konzistenci rozvržení i po jeho pozdějším skrytí.

## Vkládání tvaru do Word dokumentu – osvědčené postupy

Když `insert shape into word document`, zvažte následující:

* **Set explicit dimensions** – Avoid relying on automatic sizing; specify width and height in points to ensure consistent layout across platforms.  
  **Nastavte explicitní rozměry** – Vyhněte se spoléhaní na automatické velikosti; uveďte šířku a výšku v bodech, aby byl rozvrh konzistentní napříč platformami.

* **Define positioning** – By default the shape is anchored to the current paragraph. Use `builder.MoveTo` or `builder.StartBookmark` to place it precisely.  
  **Definujte umístění** – Ve výchozím nastavení je tvar ukotven k aktuálnímu odstavci. Použijte `builder.MoveTo` nebo `builder.StartBookmark` pro přesné umístění.

* **Apply styling early** – Fill color, line style, and text wrapping affect the final appearance. Even hidden shapes benefit from proper styling because the markup remains unchanged.  
  **Aplikujte stylování brzy** – Barva výplně, styl čáry a obtékání textu ovlivňují konečný vzhled. I skryté tvary těží z řádného stylování, protože markup zůstává nezměněn.

* **Version compatibility** – The `Hidden` property is only available from Aspose.Words 24.10 onward. If you target an older version, you can manually add the `<w:hidden/>` attribute using the `Node` API.  
  **Kompatibilita verzí** – Vlastnost `Hidden` je dostupná až od Aspose.Words 24.10. Pokud cílíte na starší verzi, můžete ručně přidat atribut `<w:hidden/>` pomocí API `Node`.

### Manually adding the hidden attribute (fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Kompletní end‑to‑end příklad

Spojením všech částí získáte jeden program, který:

1. Vloží obdélníkový tvar.
2. Skryje tvar.
3. Vloží viditelnou elipsu pro kontrast.
4. Uloží dokument.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Spuštěním programu vznikne `demo_output.docx`. Po otevření uvidíte jen korálovou elipsu; zelený obdélník je přítomen v XML, ale skrytý v pohledu.

## Časté otázky a okrajové případy

**Q: Does hiding a shape affect pagination?**  
A: No. Hidden shapes are ignored by the layout engine, so they do not consume space. This is useful for placeholder content that should not affect page breaks.  
**Otázka: Ovlivňuje skrytí tvaru stránkování?**  
Odpověď: Ne. Skryté tvary jsou layoutovým enginem ignorovány, takže nezabírají místo. To je užitečné pro zástupný obsah, který by neměl ovlivňovat zalomení stránek.

**Q: Can I hide a shape that is part of a header or footer?**  
A: Yes. The same `Hidden` property works on shapes located anywhere in the document tree, including headers, footers, and even inside tables.  
**Otázka: Můžu skrýt tvar, který je součástí záhlaví nebo zápatí?**  
Odpověď: Ano. Stejná vlastnost `Hidden` funguje na tvarech umístěných kdekoliv ve stromu dokumentu, včetně záhlaví, zápatí a dokonce i uvnitř tabulek.

**Q: What if I need to hide multiple shapes at once?**  
A: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection and set `Hidden = true` for each target shape.  
**Otázka: Co když potřebuji najednou skrýt více tvarů?**  
Odpověď: Projděte kolekci `Document.GetChildNodes(NodeType.Shape, true)` a pro každý cílový tvar nastavte `Hidden = true`.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: Is the hidden attribute preserved when converting to PDF?**  
A: When converting to PDF, hidden shapes are omitted by default, matching Word’s rendering behavior. If you need them in the PDF, you must unhide them before conversion.  
**Otázka: Zachovává se skrytý atribut při konverzi do PDF?**  
Odpověď: Při konverzi do PDF jsou skryté tvary ve výchozím nastavení vynechány, což odpovídá chování Wordu. Pokud je potřebujete v PDF, musíte je před konverzí odskrýt.

## Tipy a úskalí

* **Pro tip:** Set `shape.WrapType = WrapType.None` before hiding if you later plan to unhide the shape without disturbing surrounding text.  
  **Pro tip:** Nastavte `shape.WrapType = WrapType.None` před skrytím, pokud plánujete tvar později odskrýt bez narušení okolního textu.

* **Watch out for older Aspose.Words versions:** The `Hidden` property throws `NotSupportedException` before 24.10. Use the manual XML approach in that case.  
  **Dejte pozor na starší verze Aspose.Words:** Vlastnost `Hidden` vyvolá `NotSupportedException` před verzí 24.10. V takovém případě použijte ruční přístup k XML.

* **Testing:** Always open the generated `.docx` in Word and use “Show XML markup” (Developer tab) to verify that the `<w:hidden/>` attribute is present.  
  **Testování:** Vždy otevřete vygenerovaný `.docx` ve Wordu a použijte „Show XML markup“ (karta Vývojář) k ověření, že atribut `<w:hidden/>` je přítomen.

## Závěr

Nyní víte, jak skrýt tvar ve Wordu pomocí C# a Aspose.Words, jak vložit obdélníkový tvar a jak vložit tvar do Word dokumentu s plnou kontrolou nad viditelností. Využitím vlastnosti `Hidden` můžete udržet tvary v modelu dokumentu pro pozdější zpracování a zároveň prezentovat čistý pohled koncovým uživatelům.

Dále prozkoumejte související témata, jako je **aktualizace vlastností tvaru za běhu**, **konverze skrytých tvarů na obrázky** nebo **použití Open XML SDK k přímé manipulaci se skrytými elementy**. Tyto rozšíření prohloubí vaše znalosti.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Vkládání tvarů do Word dokumentů pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvoření obdélníkového tvaru ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Vytvoření skupinového tvaru ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
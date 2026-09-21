---
category: general
date: 2026-09-21
description: Naučte se, jak seskupovat tvary ve Wordu pomocí Aspose.Words pro C#.
  Tento krok‑za‑krokem průvodce pokrývá vytváření, umisťování a ukládání seskupených
  tvarů.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: cs
lastmod: 2026-09-21
og_description: Seskupte tvary ve Wordu pomocí Aspose.Words pro C#. Postupujte podle
  tohoto stručného tutoriálu, abyste vytvořili, umístili a uložili seskupené tvary
  programově.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Skupinové tvary ve Wordu s Aspose.Words – kompletní průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak seskupit tvary ve Wordu pomocí Aspose.Words pro C#
url: /cs/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary ve Wordu pomocí Aspose.Words pro C#

Pokud potřebujete **seskupit tvary ve Wordu** programově, Aspose.Words to dělá jednoduchým způsobem. Tento tutoriál vám ukáže, jak vytvořit dva obdélníkové tvary, umístit je vedle sebe, spojit je do `GroupShape` a výsledek uložit jako soubor DOCX.

Uvidíte kompletní, spustitelný příklad, vysvětlení, proč je každý krok důležitý, a tipy pro řešení běžných okrajových případů, jako jsou překrývající se tvary nebo dynamické velikosti. Na konci tohoto průvodce budete schopni integrovat seskupování tvarů do libovolného projektu automatizace Wordu.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 (nebo novější) nainstalovaný – Aspose.Words podporuje .NET Standard 2.0+, .NET Core a .NET Framework.
* Platnou licenci Aspose.Words pro .NET (nebo dočasný evaluační klíč) – knihovna funguje i bez licence, ale přidá vodoznak.
* Visual Studio 2022 (nebo jakékoli C# IDE) pro kompilaci a spuštění ukázky.

Žádné další NuGet balíčky nejsou potřeba kromě `Aspose.Words`.

## Jak seskupit tvary ve Wordu pomocí Aspose.Words

Jádrem řešení je objekt **`GroupShape`**, který funguje jako kontejner pro jednotlivé tvary. Níže rozdělujeme proces do jasných kroků.

### Krok 1: Vytvořte prázdný dokument a `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč tento krok?*  
`Document` představuje celý soubor DOCX, zatímco `DocumentBuilder` poskytuje plynulé metody (např. `InsertShape`), které automaticky umísťují nové elementy na aktuální pozici kurzoru.

### Krok 2: Vložte první obdélníkový tvar

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Volání `InsertShape` přidá tvar do dokumentu a vrátí objekt `Shape`, který můžete dále konfigurovat (barvu, okraj atd.). Velikost je vyjádřena v bodech (1 pt ≈ 1/72 in).

### Krok 3: Vložte druhý obdélník a odsuňte jej

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Nastavení `Left` umisťuje tvar relativně k okraji stránky. Odsazení musí být větší než šířka prvního tvaru (100 pt), aby nedošlo k překrytí; použijeme 120 pt, abychom nechali malou mezeru.

### Krok 4: Vytvořte `GroupShape` dostatečně velký pro oba obdélníky

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` přijímá vlastnící `Document` a rozměry kontejneru. Šířka kontejneru by měla přesahovat pravý okraj nejvzdálenějšího tvaru; jinak by byl druhý tvar oříznut.

### Krok 5: Přidejte jednotlivé tvary do skupiny

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Přidání přesune tvary do interní kolekce skupiny. Po tomto volání už tvary nejsou samostatnými objekty ve stromu dokumentu – patří do skupiny.

### Krok 6: Vložte seskupený tvar zpět do dokumentu

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` umístí celý `GroupShape` tam, kde se momentálně nachází kurzor. Pokud potřebujete skupinu v konkrétním odstavci, nejprve přesuňte builder do tohoto odstavce.

### Krok 7: Uložte dokument

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Výsledný soubor obsahuje dva obdélníky, které se chovají jako jeden objekt – můžete je společně přesouvat, měnit jejich velikost nebo je mazat v Microsoft Wordu.

## Kompletní zdrojový kód

Spojením všech kroků získáte samostatně fungující program:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Očekávaný výstup:** Otevření *GroupedShapes.docx* v Microsoft Wordu zobrazí dva obdélníky vedle sebe, považované za jeden vybraný objekt. Přetažení skupiny přesune oba obdélníky najednou.

## Běžné varianty a okrajové případy

| Situace | Doporučená úprava |
|-----------|------------------------|
| **Více než dva tvary** | Vytvořte další objekty `Shape`, umístěte je podle potřeby a přidejte každý do stejného `GroupShape`. |
| **Dynamická velikost** | Vypočítejte šířku/výšku skupiny na základě maximálních hodnot `Right` a `Bottom` podřízených tvarů. |
| **Různé typy tvarů** | `ShapeType.Ellipse`, `ShapeType.Triangle` atd. lze vložit stejným způsobem; kontejner skupiny se na typ nezajímají. |
| **Otočené tvary** | Nastavte `shape.Rotation = 45;` před přidáním; otočení se zachová ve skupině. |
| **Uložení jako PDF** | Zavolejte `doc.Save("GroupedShapes.pdf");` – skupina zůstane zachována při renderování PDF. |

**Tip:** Po seskupení můžete stále upravovat jednotlivé tvary pomocí `group.GetChildNodes(NodeType.Shape, true)`. To je užitečné, když potřebujete změnit barvu výplně jednoho obdélníku, aniž byste rozbili skupinu.

## Jak ověřit seskupení programově

Pokud potřebujete potvrdit, že tvary jsou správně seskupeny (např. v unit testech), prozkoumejte hierarchii uzlů dokumentu:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Výstup by měl být:

```
Number of groups: 1
Children in first group: 2
```

Tím se ověří, že **seskupení tvarů ve Wordu** bylo vytvořeno podle očekávání.

## Závěr

Nyní víte, jak **seskupit tvary ve Wordu** pomocí Aspose.Words pro C#. Proces zahrnuje vytvoření jednotlivých tvarů, jejich umístění, zabalení do `GroupShape` a vložení skupiny zpět do dokumentu. S kompletním příkladem výše můžete techniku rozšířit na libovolný počet tvarů, různé typy nebo ji dokonce kombinovat s textovými poli a obrázky.

Dále prozkoumejte související témata, jako jsou **seskupování tvarů v Aspose.Words**, **manipulace tvarů ve Wordu v C#** a **vkládání tvarů pomocí DocumentBuilder** pro pokročilejší scénáře automatizace dokumentů. Experimentujte s dynamickým dimenzováním, podmíněným seskupováním a exportem do PDF, abyste plně využili sílu Aspose.Words.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Vkládání tvarů do dokumentů Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvoření obdélníkového tvaru ve Wordu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutoriál stínování tvarů v Aspose.Words – Přidání stínu k tvaru ve Wordu v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
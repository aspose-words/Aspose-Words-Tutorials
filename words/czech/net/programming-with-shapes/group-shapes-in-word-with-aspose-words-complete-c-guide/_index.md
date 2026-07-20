---
category: general
date: 2026-07-19
description: Seskupujte tvary ve Wordu pomocí Aspose.Words. Naučte se, jak přidat
  obdélníkový tvar, definovat eliptický tvar a vložit tvar do dokumentů Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: cs
lastmod: 2026-07-19
og_description: Seskupujte tvary ve Wordu pomocí Aspose.Words. Mistrovské přidání
  obdélníkového tvaru, definování eliptického tvaru a vložení tvaru do dokumentů Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Seskupování tvarů ve Wordu – krok za krokem C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Skupinové tvary ve Wordu s Aspose.Words – Kompletní průvodce C#
url: /cs/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skupinování tvarů ve Wordu – Kompletní průvodce C#

Už jste se někdy zamysleli, jak **skupinovat tvary ve Wordu** bez zbytečného mačkání UI? Nejste v tom sami. Ať už generujete smlouvy, letáky nebo diagramy programově, schopnost **přidat obdélníkový tvar**, **definovat eliptický tvar** a pak **skupinovat tvary ve Wordu** vám může ušetřit hodiny ruční práce.

V tomto tutoriálu projdeme reálným příkladem pomocí **Aspose.Words for .NET**. Na konci přesně budete vědět, jak **vložit tvar do Wordu**, kombinovat je a vytvořit vylepšený dokument, který můžete odeslat klientům nebo kolegům.

---

## Co budete potřebovat

- **Aspose.Words for .NET** (nejnovější verze, např. 24.9). Můžete jej získat z NuGet pomocí `Install-Package Aspose.Words`.
- Vývojové prostředí .NET (Visual Studio 2022 nebo VS Code s rozšířením C# funguje dobře).
- Základní znalost syntaxe C# – nic složitého, jen běžné `using` příkazy a vytváření objektů.

To je vše. Žádné další knihovny, žádné COM interop, jen čistý spravovaný kód.

---

## Jak skupinovat tvary ve Wordu pomocí Aspose.Words

Níže je podrobný krok‑za‑krokem rozpis, který odráží kód, který již máte. Každý krok vysvětluje **proč** to děláme, ne jen **co** řádek dělá, takže můžete přizpůsobit vzor libovolnému tvaru.

### Krok 1: Nastavení dokumentu a builderu

Začínáme vytvořením prázdného `Document` a `DocumentBuilder`. Builder je naše „pero“, které nám umožňuje vkládat obsah kamkoli potřebujeme.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Proč?** Objekt `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` poskytuje pohodlné API pro vkládání uzlů (např. tvarů) bez nutnosti pracovat s podkladovým stromem uzlů.

### Krok 2: Přidání obdélníkového tvaru (add rectangle shape)

Nyní **přidáme obdélníkový tvar** do dokumentu. Nastavíme jeho velikost, pozici a barvu výplně, aby vynikl.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Tip:** Můžete změnit `FillColor` na libovolnou `System.Drawing.Color`, kterou preferujete. To je užitečné, když potřebujete v reportu sekce kódované barvami.

### Krok 3: Definování eliptického tvaru (define ellipse shape)

Dále **definujeme eliptický tvar**. Všimněte si odlišného `ShapeType` a posunu (`Left = 120`), aby elipsa byla vedle obdélníku.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Proč je to důležité:** Explicitním umístěním tvarů řídíte, jak se zobrazí před jejich seskupením. Pokud se spolehnete na automatické rozvržení, seskupení může vypadat mimo střed.

### Krok 4: (Volitelné) Vložení jednotlivých tvarů pro náhled

Pokud chcete vidět každý tvar před seskupením, můžete **vložit tvar do Wordu** jednotlivě. Tento krok je volitelný, ale užitečný při ladění.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** Zakomentujte tyto dva řádky, jakmile budete mít jistotu, že tvary vypadají správně; jinak po seskupení skončíte s duplicitními vizuály.

### Krok 5: Jak seskupit tvary – Vytvoření GroupShape

Zde je jádro tutoriálu: **jak seskupit tvary**. Vytvoříme `GroupShape`, připojíme náš obdélník a elipsu a rozhodneme, jak se skupina chová vůči okolnímu textu.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Vysvětlení:** `GroupShape` je v podstatě mini‑plátno, které drží další tvary. Nastavením `WrapType` na `Inline` se celá skupina pohybuje jako jednotka při přidávání nebo mazání textu.

### Krok 6: Vložení seskupeného tvaru do dokumentu (insert shape into word)

Nyní **vložíme tvar do Wordu**—ale tentokrát jde o seskupený kontejner, ne o jednotlivé části.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **Co se děje pod kapotou?** Volání `InsertNode` přidá `GroupShape` do kolekce uzlů dokumentu. Protože skupina již obsahuje obdélník a elipsu, objeví se společně jako jeden objekt.

### Krok 7: Uložení dokumentu

Nakonec zapíšeme soubor na disk. Cestu můžete změnit podle struktury vašeho projektu.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Výsledek:** Otevřete `GroupShape.docx` v Microsoft Word a uvidíte světle modrý obdélník a korálovou elipsu spojené dohromady. Přetažení jednoho přesune druhý – přesně to, co „skupinovat tvary ve Wordu“ slibuje.

---

## Vizualizace

Níže je náhled toho, jak seskupené tvary vypadají uvnitř souboru Word.

![Snímek obrazovky seskupených tvarů v dokumentu Word vytvořeném pomocí Aspose.Words](grouped_shapes_placeholder.png "skupinovat tvary ve Wordu")

*Alt text obrázku obsahuje hlavní klíčové slovo pro přístupnost a SEO.*

---

## Časté otázky a okrajové případy

### Co když potřebuji více než dva tvary?

Stačí nadále volat `groupShape.AppendChild(yourNewShape);` před vložením skupiny. API neklade žádné omezení na počet podřízených tvarů.

### Můžu otáčet nebo měnit velikost celé skupiny?

Ano. `GroupShape` dědí z `Shape`, takže můžete nastavit vlastnosti jako `RotationAngle`, `Width` nebo `Height` přímo na skupině a všechny podřízené tvary se přizpůsobí.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Jak změním barvu pozadí skupiny?

Použijte `groupShape.FillColor`. Tím vyplníte neviditelný ohraničující rámeček; může být užitečné pro zvýraznění.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Funguje to se staršími formáty Wordu (.doc)?

`Aspose.Words` může také ukládat do formátu `.doc` – stačí v `Save` změnit příponu souboru. Nicméně některé pokročilé funkce tvarů (jako seskupování) jsou plně podporovány pouze ve formátu OOXML `.docx`.

---

## Kompletní funkční příklad

Zkopírujte a vložte následující blok do nové konzolové aplikace, abyste viděli celý proces v akci. Nechybí žádné části; jedná se o **kompletní, spustitelný příklad**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Očekávaný výstup:** Po otevření `GroupShape.docx` uvidíte jeden seskupený objekt sestávající ze světle modrého obdélníku a světle korálové elipsy, perfektně zarovnaných vedle sebe.

---

## Shrnutí

Právě jsme probrali vše, co potřebujete k **skupinování tvarů ve Wordu** s Aspose.Words:

1. Vytvořte dokument a builder.  
2. **Přidejte obdélníkový tvar** a **definujte eliptický tvar** s explicitními rozměry.  
3. (Volitelně) **vložit tvar do Wordu** pro rychlý náhled.  
4. Použijte `GroupShape` k **skupinování tvarů** – připojte každé dítě, nastavte obtékání a vložte.  
5. Uložte soubor a ověřte

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vkládání tvarů do dokumentů Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Vytvoření obdélníkového tvaru ve Wordu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutoriál stínování tvaru v Aspose.Words – Přidání stínu k tvaru ve Wordu v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
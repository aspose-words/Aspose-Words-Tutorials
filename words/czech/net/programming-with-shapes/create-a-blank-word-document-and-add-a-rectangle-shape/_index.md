---
category: general
date: 2026-09-05
description: Naučte se, jak vytvořit prázdný dokument Word a přidat obdélníkový tvar,
  který lze skrýt pomocí Aspose.Words v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: cs
lastmod: 2026-09-05
og_description: Vytvoření prázdného dokumentu Word a vložení skrytého obdélníkového
  tvaru pomocí Aspose.Words – krok za krokem průvodce pro vývojáře C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Vytvořte prázdný dokument Word se skrytým obdélníkovým tvarem
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Vytvořte prázdný dokument Word a přidejte obdélníkový tvar
url: /cs/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word a přidejte obdélníkový tvar

Pokud potřebujete vytvořit **prázdný dokument Word**, který také obsahuje tvar, který nechcete zobrazit v rozvržení, tento návod vám přesně ukáže, jak to provést pomocí Aspose.Words pro .NET. Uvidíte kompletní, spustitelný příklad, který vytvoří nový dokument, přidá obdélníkový tvar, tento tvar skryje a soubor uloží – bez nutnosti dalšího nástroje.

Návod pokrývá vše od nastavení projektu až po řešení běžných problémů. Na konci budete schopni vygenerovat soubor Word, který vypadá prázdně pro čtenáře, ale stále nese skrytou metadata, což je užitečné pro věci jako vodoznaky, vlastní úložiště XML nebo kotvy rozvržení.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 SDK nebo novější (kód také funguje s .NET Framework 4.7+)
* Visual Studio 2022 (nebo jakékoli IDE podporující C#)
* Aktivní licence **Aspose.Words** NuGet (bezplatná zkušební verze funguje pro testování)
* Základní znalost C# a konceptu uzlů dokumentu

Knihovnu můžete nainstalovat pomocí následujícího příkazu CLI:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Udržujte svou verzi Aspose.Words aktuální; API použité v tomto tutoriálu je stabilní od verze 23.10.

## Jak vytvořit prázdný dokument Word s Aspose.Words

Prvním krokem je vytvořit objekt `Document`. Čerstvý `Document` představuje prázdný **prázdný dokument Word** – žádné odstavce, žádné sekce, jen kontejner souboru.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Proč je to důležité:** Začátek s čistým dokumentem zajišťuje, že skrytý tvar, který později přidáte, nebude zasahovat do existujícího obsahu nebo stylů.

## Přidání obdélníkového tvaru do dokumentu

Dále vytvoříme obdélníkový tvar. V Aspose.Words je tvar uzel, který může být umístěn kdekoli ve stromu dokumentu a může být nakonfigurován s velikostí, výplní, stylem čáry a viditelností.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Výše uvedený kód vytváří viditelný obdélník. V tomto okamžiku byste jej mohli vložit do dokumentu pomocí `builder.InsertNode(rectangle)`. Protože však chceme, aby tvar zůstal skrytý, upravíme jeho vlastnost `Hidden` před vložením.

## Jak skrýt tvar v dokumentu Word

Word poskytuje atribut `Hidden` pro uzly tvarů. Když je nastaven na `true`, tvar se neobjeví v rozvržení stránky, ale zůstane součástí XML dokumentu. To je jádro požadavku **jak skrýt tvar**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Vysvětlení:** Nastavení `Hidden = true` přidá do XML tvaru atribut `<w:hide>`. Textové procesory tvar během vykreslování ignorují, přesto je tvar stále přístupný programově nebo přes XML pohled Wordu.

## Vložení skrytého tvaru do prázdného dokumentu

Nyní umístíme skrytý obdélník do stromu dokumentu. Protože je dokument stále prázdný, tvar se stane prvním uzlem v hlavním příběhu.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Pokud otevřete výsledný soubor v Microsoft Word, uvidíte zjevně prázdnou stránku. Tvar je tam, ale je neviditelný.

## Uložení dokumentu

Nakonec zapíšeme dokument na disk. Můžete zvolit libovolný podporovaný formát (`.docx`, `.pdf`, `.odt` atd.). Pro tento tutoriál použijeme moderní formát DOCX.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Očekávaný výsledek

Otevřete `HiddenRectangle.docx` ve Wordu:

* Dokument se jeví jako prázdný (žádné viditelné tvary ani text).
* Pokud soubor prozkoumáte pomocí nástroje jako **Open XML SDK** nebo **Word XML Viewer**, uvidíte element `<w:pict>` obsahující obdélník s atributem `hidden`.

![prázdný dokument Word s skrytým obdélníkovým tvarem](image.png){: .align-center alt="prázdný dokument Word s skrytým obdélníkovým tvarem"}

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do konzolové aplikace. Obsahuje všechny potřebné `using` direktivy, ošetření chyb a komentáře.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Spusťte program (`dotnet run`) a ověřte výstupní soubor. Konzole potvrdí umístění uložení.

## Časté otázky a okrajové případy

### Mohu skrýt více tvarů najednou?

Ano. Vytvořte každý tvar, nastavte `Hidden = true` a vložte je postupně. Příznak skrytí funguje na úrovni uzlu, takže kombinace skrytých a viditelných tvarů ve stejném dokumentu je podporována.

### Co když potřebuji tvar skrýt jen v náhledu tisku?

Word rozlišuje mezi **zobrazením** a **tiskem** pomocí vlastnosti `DisplayWhen`. Aspose.Words neexponuje přímé API pro tento příznak, ale můžete upravit podkladové XML:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Používejte to jen v případě, že potřebujete viditelnost pouze při tisku.

### Ovlivňuje skrytý tvar velikost souboru?

Skrytý tvar přidává stejný XML payload jako viditelný, takže nárůst velikosti souboru je identický. Nicméně, protože tvar

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy implementace ve vlastních projektech.

- [Vytvořit prázdný dokument Word se stínovaným obdélníkovým tvarem – krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutoriál stínování tvaru Aspose.Words – Přidat stín k tvaru Word v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
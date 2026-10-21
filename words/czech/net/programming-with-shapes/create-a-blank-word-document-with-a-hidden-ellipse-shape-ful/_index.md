---
category: general
date: 2026-07-29
description: Vytvořte prázdný dokument Word a naučte se, jak skrýt tvar, vytvořit
  skrytý objekt a vytvořit elipsový tvar pomocí Aspose.Words v C#. Krok‑za‑krokem
  je zahrnutý kód.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: cs
lastmod: 2026-07-29
og_description: Vytvořte prázdný dokument Word a okamžitě skryjte tvar. Naučte se
  vytvořit skrytý objekt a nakreslit elipsu pomocí Aspose.Words v C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Vytvořte prázdný dokument Word se skrytým eliptickým tvarem – C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Vytvořte prázdný dokument Word s ukrytým eliptickým tvarem – kompletní průvodce
  C#
url: /cs/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word s skrytým eliptickým tvarem – Kompletní průvodce v C#

Už jste někdy potřebovali vytvořit **prázdný dokument Word** a poté v něm skrýt tvar? Možná generujete šablonu, kde určité značky musí zůstat neviditelné až do pozdějšího kroku. V tomto tutoriálu vás provedeme přesně **jak skrýt tvar**, jak **vytvořit skrytý objekt** a dokonce **jak vytvořit eliptický tvar** pomocí Aspose.Words pro .NET. Na konci budete mít připravený C# úryvek, který vytvoří soubor DOCX obsahující neviditelný elips.

## Co se naučíte

- Inicializovat nový prázdný dokument Word pomocí Aspose.Words.  
- Vytvořit eliptický tvar, nastavit jeho rozměry a umístit jej na stránku.  
- Označit tvar jako skrytý, aby se nikdy nezobrazil na obrazovce ani při tisku.  
- Uložit výsledek na disk a ověřit, že skrytý objekt je skutečně neviditelný.  

Žádné externí knihovny kromě Aspose.Words nejsou potřeba a kód funguje s verzí 24.10 nebo novější (vlastnost `Hidden` byla zavedena v této verzi). Pojďme na to.

![Diagram skrytého elipsu uvnitř prázdného dokumentu Word](https://example.com/hidden-ellipse.png "Skrytý eliptický tvar vložený do prázdného dokumentu Word")

## Vytvořte prázdný dokument Word a vložte skrytý eliptický tvar

Prvním krokem je vytvořit zcela nový dokument. Představte si `Document` jako prázdné plátno; `DocumentBuilder` je váš štětec.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Proč začít s prázdným dokumentem?**  
> Čistý list zaručuje, že žádný předchozí obsah nezasahuje do skrytého tvaru, který se chystáte přidat. Také to usnadňuje příklad zkopírovat‑vložit do libovolného projektu.

## Jak skrýt tvar: nastavení vlastnosti Hidden

Aspose.Words 24.10 zavedl příznak `Hidden` na objektu `Shape`. Když je nastaven na `true`, Word zachází s tvarem jako s komentářem – zcela neviditelný v uživatelském rozhraní i při tisku.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Tip:** Pokud budete později potřebovat tvar programově odhalit, jednoduše přepněte `ellipseShape.Hidden = false;` a dokument znovu uložte.

## Vytvořte skrytý objekt: vložení tvaru do dokumentu

Nyní, když je elipsa připravena a skrytá, vložíme ji na aktuální pozici kurzoru builderu. Pozice builderu ve výchozím nastavení začíná na začátku prvního odstavce, což je ideální pro prázdný dokument.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **Co když potřebujete tvar na konkrétní stránce?**  
> Nejprve přesuňte builder na požadovanou stránku (`builder.MoveToDocumentEnd();` nebo `builder.MoveToPage(pageNumber);`) před voláním `InsertNode`.

## Uložte dokument obsahující skrytý tvar

Nakonec zapíšeme soubor na disk. Výstup bude standardní DOCX, který může otevřít jakýkoli procesor Word – kromě toho, že elipsa zůstane neviditelná.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Očekávaný výstup:** Otevřete `HiddenShape.docx` v Microsoft Word. Neuvidíte žádnou grafiku, ale velikost souboru bude mírně větší než u skutečně prázdného dokumentu, protože skrytá elipsa je uložena v XML.

## Ověřte skrytý elips programově (volitelné)

Pokud chcete dvojitě zkontrolovat, že je tvar skutečně skrytý, můžete načíst uložený soubor a prozkoumat vlastnost `Hidden` tvaru:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Spuštěním tohoto úryvku se vypíše `True`, což potvrzuje, že skrytý objekt přežil cyklus uložení‑načtení.

## Okrajové případy a časté otázky

### Co když cílová verze Wordu nepodporuje skryté tvary?

Příznak `Hidden` je součástí specifikace Office Open XML a respektují jej Word 2007+ a LibreOffice. Starší formáty (např. `.doc`) tento příznak ignorují, takže vždy ukládejte jako `.docx`, pokud potřebujete spolehlivé skrytí.

### Mohu skrýt jiné typy objektů (obrázky, tabulky)?

Ano. Každý uzel odvozený od `Shape` – včetně obrázků, textových polí a dokonce SmartArt – má vlastnost `Hidden`. Stačí ji nastavit na `true` před vložením.

### Ovlivňuje skrytí tvaru výkon dokumentu?

Nevýznamně. Tvar je uložen jako XML markup a Word během rozvržení přeskočí vykreslování skrytých objektů. Pokud vložíte mnoho skrytých objektů, velikost souboru poroste, ale vykreslování zůstane rychlé.

### Jak se to liší od použití záložky nebo komentáře jako značky?

Záložky jsou neviditelné z designu, ale slouží k navigaci, ne jako vizuální zástupci. Komentáře se zobrazují na okraji. Skrytý tvar vám poskytuje vizuální objekt (velikost, pozici), který můžete později odhalit nebo manipulovat, což je užitečné pro scénáře šablonování.

## Kompletní funkční příklad

Níže je kompletní, připravený k zkopírování a vložení program. Obsahuje všechny using direktivy, vytvoření skrytého elipsu a krok ověření.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Spuštěním programu se vytvoří `HiddenEllipse.docx` ve složce, odkud byl program spuštěn. Otevřete jej – uvidíte naprosto normální prázdnou stránku, přičemž skrytý elips tiše existuje uvnitř.

## Shrnutí

Probrali jsme, jak **vytvořit prázdný dokument Word**, **skrýt tvar**, **vytvořit skrytý objekt** a **vytvořit eliptický tvar** pomocí několika řádků C#. Klíčovým poznatkem je vlastnost `Hidden` na objektu `Shape`, která promění jakýkoli vizuální prvek na neviditelnou značku, aniž by narušila kompatibilitu s Wordem.

## Co dál?

- **Styling skrytého tvaru** (barva výplně, styl čáry), aby po odhalení vypadal přesně tak, jak má.  
- **Kombinovat skryté tvary se záložkami** pro tvorbu dynamických šablon, které lze zapínat a vypínat.  
- **Prozkoumat další typy tvarů** – obdélníky, šipky nebo dokonce vlastní SVG cesty – výměnou `ShapeType.Ellipse`.  

Neváhejte experimentovat: změňte velikost, posuňte pozici nebo vložte více skrytých elips. Stejný vzor funguje pro jakýkoli tvar Aspose.Words, který potřebujete mít mimo zrak.

Pokud narazíte na problém nebo máte nápady, jak tento vzor rozšířit, zanechte komentář níže. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Vytvořte prázdný dokument Word se stínovaným obdélníkovým tvarem – krok za krokem](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Vytvořte skupinový tvar v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vytvořte obdélníkový tvar ve Wordu s Aspose.Words – průvodce krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
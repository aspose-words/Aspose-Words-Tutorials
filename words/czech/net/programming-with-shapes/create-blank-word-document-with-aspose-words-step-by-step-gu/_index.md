---
category: general
date: 2026-02-23
description: Vytvořte prázdný dokument Word pomocí C# a Aspose.Words. Naučte se, jak
  přidat obdélníkový tvar, přidat stín a uložit dokument Word s tvarem během několika
  minut.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: cs
og_description: Rychle vytvořte prázdný dokument Word. Tento průvodce ukazuje, jak
  přidat obdélníkový tvar, přidat stín slova a uložit dokument Word s tvarem pomocí
  Aspose.Words.
og_title: Vytvořte prázdný dokument Word – Kompletní tutoriál C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Vytvořte prázdný dokument Word s Aspose.Words – krok za krokem
url: /cs/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

produce final output with all translations.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný Word dokument – Kompletní C# tutoriál

Už jste se někdy zamýšleli, jak **vytvořit prázdný Word dokument** programově bez otevření Microsoft Wordu? Nejste v tom sami. V mnoha automatizačních projektech potřebujeme čerstvý soubor .docx, vložit na něj tvar, dát tomuto tvaru pěkný stín a pak **uložit Word s tvarem** pro pozdější použití.  

V tomto průvodci vás provedeme přesně tímto—začneme prázdným dokumentem, **přidáme obdélníkový tvar**, nakonfigurujeme efekt **add shadow word**, a nakonec soubor uložíme. Na konci budete mít kompletní, spustitelný úryvek, který můžete vložit do libovolné .NET konzolové aplikace. Žádná záhada, žádné chybějící části.

## Co budete potřebovat

- **Aspose.Words for .NET** (jakákoli recentní verze, např. 24.10).  
- .NET 6 nebo novější (kód funguje také s .NET Framework 4.7+).  
- Základní C# IDE—Visual Studio, Rider nebo dokonce VS Code s rozšířením C#.  

To je vše. Žádné další NuGet balíčky kromě Aspose.Words a není potřeba instalace Wordu.

---

## Krok 1: Vytvořte prázdný Word dokument

První věc, kterou uděláte, když chcete **vytvořit prázdný Word dokument**, je vytvořit instanci třídy `Document`. Považujte ji za čisté plátno, které vám poskytuje Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Proč je to důležité:** Objekt `Document` obsahuje všechny sekce, odstavce a tvary. Začátek s prázdnou instancí vám zaručuje kontrolu nad každým prvkem, který bude později přidán.

---

## Krok 2: Přidejte do dokumentu obdélníkový tvar

Nyní, když máme čistý dokument, pojďme **přidat obdélníkový tvar**. Obdélník je jednoduchý `Shape` s `ShapeType.Rectangle`. Samozřejmě můžete zvolit jiné typy, ale obdélník je pro demonstraci skvělý.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Tip:** Pokud se někdy zamyslíte **jak přidat tvar**, který není obdélník, stačí změnit `ShapeType.Rectangle` na jakoukoli jinou hodnotu výčtu, například `ShapeType.Ellipse` nebo `ShapeType.Polygon`. Zbytek kódu zůstane stejný.

---

## Krok 3: Nakonfigurujte vlastní stín pro tvar

Jednoduchý obdélník vypadá trochu nudně, takže **přidáme stín** (add shadow word), aby vynikl. Aspose.Words poskytuje objekt `ShadowFormat` s mnoha vlastnostmi.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Proč je to důležité:** Stín poskytuje jemný dojem hloubky, zejména když je dokument zobrazován na obrazovce. Upravit `OffsetX`, `OffsetY` a `BlurRadius` podle vašeho designu.

---

## Krok 4: Vložte tvar do dokumentu

S připraveným tvarem jej musíme někam umístit. Nejjednodušší místo je první odstavec první sekce. Pokud dokument ještě nemá žádné odstavce, Aspose automaticky vytvoří jeden.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Okrajový případ:** Pokud plánujete vložit tvar na konkrétní místo (např. za určitý nadpis), najděte cílový `Paragraph` pomocí `document.GetChildNodes(NodeType.Paragraph, true)` a použijte `InsertAfter` nebo `InsertBefore` podle potřeby.

---

## Krok 5: Uložte Word dokument s tvarem

Nakonec **uložíme Word s tvarem** na disk. Metoda `Save` automaticky určuje formát podle přípony souboru.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **Co uvidíte:** Otevřete `shadowedRectangle.docx` ve Wordu (nebo v jakémkoli kompatibilním prohlížeči) a uvidíte šedý obdélník s jemným stínem umístěný v horní části první stránky.

---

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkopírovat a vložit do konzolové aplikace. Obsahuje všechny using direktivy, komentáře a přesné kroky, které jsme probírali.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Spusťte program, přejděte do `YOUR_DIRECTORY` a otevřete vygenerovaný soubor `shadow.docx`. Měli byste vidět obdélník s jemným šedým stínem—přesně to, co jsme chtěli dosáhnout.

---

## Často kladené otázky a tipy

### Jak změním barvu tvaru?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Stačí nastavit `FillColor` před přidáním tvaru.

### Co když potřebuji na stejné stránce více tvarů?
Vytvořte další objekty `Shape` a přidejte je do stejného odstavce nebo do různých odstavců. Rozvržení můžete také řídit pomocí `WrapType` a `RelativeHorizontalPosition`.

### Můžu exportovat do PDF a zachovat stín?
Rozhodně. Použijte `document.Save("output.pdf")`—Aspose.Words zachová efekt stínu při konverzi do PDF.

### Funguje to na .NET Core?
Ano. Aspose.Words je multiplatformní; stejný kód běží na .NET Core, .NET 5+ a .NET Framework.

### Jak přidat tvar bez odstavce?
Můžete přidat tvar přímo do `Run` nebo do `Story`. Pro přesnější umístění nastavte `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` a upravte vlastnosti `Left`/`Top`.

---

## Vizuální výsledek

![Obdélníkový tvar se šedým stínem ve Word dokumentu – příklad add shadow word](https://example.com/placeholder-image.png "příklad add shadow word")

*Alt text obrázku obsahuje sekundární klíčové slovo **add shadow word** pro SEO.*

---

## Závěr

Právě jsme ukázali, jak **vytvořit prázdný Word dokument**, **přidat obdélníkový tvar**, aplikovat efekt **add shadow word** a nakonec **uložit Word s tvarem** pomocí Aspose.Words pro .NET. Proces je jednoduchý: vytvořit instanci `Document`, vytvořit `Shape`, upravit jeho `ShadowFormat`, vložit jej a zavolat `Save`.  

Odtud můžete experimentovat—vyzkoušet různé typy tvarů, hrát si s barvami nebo vrstvit více tvarů. Pokud potřebujete sloučit tento dokument s existujícím obsahem, stačí načíst existující soubor pomocí `new Document("existing.docx")` a postupovat podle stejných kroků.  

Máte další otázky? Zanechte komentář a šťastné programování!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
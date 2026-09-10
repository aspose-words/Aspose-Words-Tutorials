---
category: general
date: 2026-01-13
description: Vytvořte dokument Word pomocí Aspose.Words a naučte se, jak vložit obdélníkový
  tvar, jak přidat stín a jak přidat stín tvaru v C#. Kompletní příklad je zahrnut.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: cs
og_description: Vytvořte dokument Word pomocí Aspose.Words, podívejte se, jak vložit
  obdélníkový tvar a jak přidat stín. Sledujte kompletní příklad v C#.
og_title: Vytvořte Word dokument s obdélníkem se stínem – kompletní návod
tags:
- Aspose.Words
- C#
- Document Automation
title: Vytvořte dokument Word se stínovaným obdélníkem – krok za krokem
url: /cs/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu s obdélníkem se stínem – krok za krokem průvodce

Už jste někdy potřebovali **create word document**, který obsahuje pěkně zbarvený obdélník, ale nebyli jste si jisti, kde začít? Nejste jediní — mnoho vývojářů narazí na stejnou překážku, když poprvé pracují s Aspose.Words.  

V tomto tutoriálu vás provedeme vším, co potřebujete k **create word document** programově, **insert rectangle shape**, a ukážeme **how to add shadow**, aby tvar opravdu vynikl. Na konci budete mít připravený spustitelný úryvek C#, který můžete vložit do libovolného .NET projektu.

## Co se naučíte

- Přesný kód k **how to insert shape** (obdélník) do souboru Word.  
- Vlastnosti, které musíte upravit pro **add shape shadow** a ovládat jeho vzhled.  
- Jak uložit výsledek a ověřit, že je stín viditelný.  
- Několik praktických tipů a poznámek o okrajových případech, které vám později ušetří bolesti hlavy.

Žádná externí dokumentace není potřeba — vše je zde.

## Požadavky

Než se ponoříme, ujistěte se, že máte:

1. **.NET 6.0** (nebo jakoukoli novější verzi .NET) nainstalovanou.  
2. **license** pro Aspose.Words pro .NET, nebo můžete použít režim bezplatného hodnocení pro testování.  
3. Vývojové prostředí — Visual Studio 2022 funguje skvěle, ale jakýkoli editor, který dokáže kompilovat C#, bude stačit.

To je vše. Žádné další NuGet balíčky kromě `Aspose.Words` nejsou potřeba.

## Krok 1 – Nastavení projektu a odkaz na Aspose.Words

Nejprve vytvořte novou konzolovou aplikaci a přidejte balíček Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Tip:** Pokud používáte bezplatnou zkušební verzi, nezapomeňte zavolat `License.SetLicense` s vaším licenčním souborem; jinak knihovna přidá vodoznak.

## Krok 2 – Inicializace Document Builderu

Nyní zahájíme skutečný proces **create word document**. Třída `Document` nám poskytuje prázdné plátno a `DocumentBuilder` nám umožňuje na něj malovat.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Proč potřebujeme builder? Abstrahuje nízkoúrovňové detaily OpenXML, takže se můžete soustředit na *co* chcete, místo na *jak je soubor strukturován. To je jádro **how to insert shape** rychle.

## Krok 3 – Vložení obdélníkového tvaru

Zde skutečně **insert rectangle shape**. Obdélník bude mít 150 × 100 bodů (přibližně 2 palce × 1,3 palce).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Metoda `InsertShape` vrací objekt `Shape`, který můžeme dále přizpůsobit. V tuto chvíli je obdélník jen pevná bílá krabice — stín zatím chybí.

## Krok 4 – Jak přidat stín (Add Shape Shadow)

Přidání stínu je překvapivě jednoduché, jakmile víte, které vlastnosti upravit. Objekt `ShadowFormat` řídí viditelnost, barvu, rozostření, posun a velikost.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Tento blok odpovídá na **how to add shadow** v prostém anglickém jazyce: zapněte ho, vyberte barvu, upravte průhlednost, posun, rozostření a velikost. Můžete experimentovat s těmito čísly, abyste získali těžký vržený stín nebo jemný, sotva patrný.

### Běžné varianty

- **Různé barvy:** Použijte `Color.Black` pro klasický vržený stín, nebo `Color.BlueViolet` pro stylizovaný efekt.  
- **Nulové rozostření:** Nastavte `BlurRadius = 0` pro ostrý, čistý okraj.  
- **Větší posuny:** Zvyšte `OffsetX`/`OffsetY`, aby se stín posunul dál od tvaru.

## Krok 5 – Uložení dokumentu a ověření

Nakonec zapíšete dokument na disk. Soubor bude standardní `.docx`, který může otevřít jakýkoli moderní procesor Word.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Otevřete vzniklý *ShadowRectangle.docx* v Microsoft Word. Měli byste vidět obdélník s měkkým šedým stínem posunutým dolů a doprava — přesně to, co kód určil.

> **Očekávaný výstup:** Jednostránkový Word soubor obsahující 150 × 100‑bodový obdélník s 30 % průhledným šedým stínem, posunutým o 5 bodů, rozostřeným o 4 body a velikostním poměrem 75 % tvaru.

## Kompletní funkční příklad

Spojením všeho dohromady, zde je kompletní, připravený k spuštění program:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Spusťte program (`dotnet run`) a získáte nový Word soubor s pěkně stínovaným obdélníkem — ideální pro zprávy, certifikáty nebo jakýkoli vizuální prvek, který potřebujete.

## Často kladené otázky (FAQ)

**Q: Mohu vložit jiné tvary (elipsu, hvězdu) a stále použít stejný kód pro stín?**  
A: Rozhodně. Metoda `InsertShape` přijímá libovolnou hodnotu výčtu `ShapeType`. Jakmile máte instanci `Shape`, vlastnosti `ShadowFormat` fungují stejně, takže **how to add shadow** je nezávislé na tvaru.

**Q: Co když potřebuji stín na obou stranách tvaru?**  
A: Aspose.Words podporuje pouze jeden vržený stín na tvar. Pro simulaci dvojstranného efektu duplikujte tvar, každou kopii posuňte jinak a nastavte `ShadowFormat.Visible` jedné na `false`, zatímco u druhé ponecháte stín viditelný.

**Q: Funguje to na .NET Framework 4.8?**  
A: Ano. API je verze‑agnostické; stačí odkazovat na odpovídající Aspose.Words DLL pro váš cílový framework.

## Tipy a úskalí

- **Nezapomeňte nastavit `Visible = true`** — vlastnosti stínu jsou jinak ignorovány.  
- **Hodnoty průhlednosti jsou v rozmezí 0.0 (neprůhledné) až 1.0 (zcela průhledné).** Častá chyba je použití `30` místo `0.3`.  
- **Ukládání do složky jen pro čtení vyvolá výjimku.** Ujistěte se, že výstupní adresář je zapisovatelný.

## Další kroky

Nyní, když znáte **how to insert shape**, **add shape shadow** a **create word document** s Aspose.Words, můžete chtít prozkoumat:

- Přidání **textu uvnitř obdélníku** pomocí `builder.InsertParagraph()` před vložením tvaru.  
- Použití **gradientových výplní** nebo **vzorkovaných okrajů** pro bohatší vizuální styl.  
- Automatizace generování více stránek, každé s jiným stínovaným tvarem, pro tvorbu dynamických zpráv.

Neváhejte experimentovat — změna barvy, rozostření nebo velikosti stínu může dramaticky změnit vzhled vašeho dokumentu.

*Připravení nasadit do produkce? Vezměte kód, upravte parametry a sledujte, jak vaše Word soubory získají profesionální lesk během několika sekund.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
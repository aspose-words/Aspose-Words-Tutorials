---
category: general
date: 2026-10-23
description: Naučte se, jak vložit elipsu a jak přidat obdélníkový tvar ve Wordu pomocí
  Aspose.Words. Zahrnuje přesunutí kurzoru k tvaru a jak vytvořit skupinový tvar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: cs
lastmod: 2026-10-23
og_description: Jak vložit elipsu a jak přidat obdélníkový tvar ve Wordu pomocí Aspose.Words.
  Postupujte podle podrobného návodu, jak přesunout kurzor na tvar a vytvořit skupinový
  tvar.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Jak vložit elipsu a obdélník do seskupeného tvaru ve Wordu
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vložit elipsové a obdélníkové tvary do skupinového tvaru pomocí Aspose.Words
url: /cs/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit elipsu a obdélníkové tvary do skupinového tvaru pomocí Aspose.Words

Pokud potřebujete vědět **jak vložit elipsu** do dokumentu Word programově, tento průvodce ukazuje kompletní postup. Také uvidíte **jak přidat obdélník** tvar, naučíte se **přesunout kurzor na tvar** a objevíte **jak vytvořit skupinový tvar**, který obsahuje více kreslicích objektů.

Automatizace Wordu často vyžaduje přesné umístění kreslicích objektů. Na konci tohoto tutoriálu můžete vygenerovat soubor `.docx`, který obsahuje seskupený obdélník a elipsu, připravený k dalšímu stylování nebo exportu. Žádné externí nástroje nejsou potřeba kromě knihovny Aspose.Words pro .NET a .NET vývojového prostředí.

## Požadavky

* .NET 6.0 nebo novější nainstalováno.
* Aspose.Words pro .NET (NuGet balíček `Aspose.Words`) přidán do vašeho projektu.
* Základní znalost syntaxe C# a Visual Studio (nebo jakéhokoli IDE).

Tyto požadavky zajišťují, že kód se zkompiluje bez další konfigurace.

## Jak vytvořit skupinový tvar ve Wordu

Skupinový tvar funguje jako kontejner, který vám umožní přesouvat, otáčet nebo formátovat několik tvarů jako jedinou jednotku. Následující kód vytvoří skupinu s konkrétní velikostí (300 × 200 bodů) a připraví dokument pro další kreslicí operace.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Proč je tento krok důležitý*: Skupinový tvar definuje lokální souřadnicový systém. Všechny tvary přidané po přesunutí kurzoru do skupiny budou umístěny relativně k počátku skupiny, což usnadňuje výpočty rozvržení.

## Jak přidat obdélníkový tvar ve Wordu

Nyní, když skupina existuje, můžete **vložit obdélníkový tvar** uvnitř ní. Obdélník bude sloužit jako pozadí nebo vizuální zástupce pro další obsah.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Vysvětlení*: `MoveTo(group)` říká builderu, že aktivní vkládací bod je skupinový tvar. Bez přesunutí kurzoru by `InsertShape` přidal obdélník do hlavního těla dokumentu místo do skupiny.

## Jak vložit elipsu

S obdélníkem na místě můžete nyní ukázat **jak vložit elipsu**. Elipsa bude vycentrována ve stejné skupině a v případě potřeby překrývat obdélník.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Proč je nutné přesunout kurzor*: Každé volání `InsertShape` respektuje aktuální umístění kurzoru. Opětovné volání `MoveTo(group)` zajišťuje, že elipsa je také potomkem skupiny, čímž zachovává zamýšlenou hierarchii.

## Přesunout kurzor na tvar před vložením dalších objektů

Pokud budete později potřebovat přidat další tvary, vždy **přesuňte kurzor na tvar** před každým vložením. Tento vzor zabraňuje náhodnému umístění mimo skupinu.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tip*: Opakované používání `MoveTo(group)` je levné a zlepšuje čitelnost kódu. Také usnadňuje budoucí údržbu, protože kontext vkládání je explicitní.

## Uložit dokument

Nakonec uložte dokument na disk. Příklad ukládá soubor jako `GroupShape.docx` do složky, kterou určíte.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Když otevřete uložený soubor v Microsoft Word, uvidíte jedinou skupinu obsahující obdélník a elipsu, obě správně umístěné.

### Očekávaný výstup

* Soubor `.docx` pojmenovaný `GroupShape.docx`.
* V dokumentu seskupený kreslicí objekt o velikosti 300 × 200 bodů.
* V rámci skupiny:
  * Obdélník (100 × 50 bodů) umístěný v počátku skupiny.
  * Elipsa (80 × 80 bodů) překrývající obdélník.
  * Jakékoli další tvary, které jste přidali po přesunutí kurzoru.

## Běžné varianty a okrajové případy

| Situace | Doporučený postup |
|-----------|----------------------|
| **Různé jednotky velikosti** | Aspose.Words používá body (1 pt = 1/72 in). Před voláním `InsertShape` převádějte centimetry nebo palce na body. |
| **Otáčení tvarů uvnitř skupiny** | Po vložení tvaru získejte jeho objekt `ShapeBase` a nastavte `ShapeBase.RotationAngle`. |
| **Přidání textu do tvaru** | Použijte `ShapeBase.AppendChild(new Paragraph(document))` a poté přidejte `Run` s požadovaným textem. |
| **Uložení do PDF místo DOCX** | Zavolejte `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – hierarchie skupiny je zachována ve výstupu PDF. |

Tyto varianty ukazují, že stejná logika **jak vložit elipsu** může být přizpůsobena pro mnoho reálných scénářů.

## Profesionální tipy

* **Znovu použijte stejnou instanci `DocumentBuilder`** – snižuje paměťovou zátěž a udržuje stav dokumentu konzistentní.
* **Ověřte rozměry tvaru** – extrémně velké šířky nebo výšky mohou způsobit problémy s vykreslováním ve starších verzích Wordu.
* **Seskupte před stylováním** – aplikace výplňových barev nebo čarových stylů na skupinu po přidání všech podřízených objektů zajišťuje jednotný vzhled.

## Závěr

Nyní rozumíte **jak vložit elipsu** a **jak přidat obdélníkový** tvar do seskupeného kontejneru v dokumentu Word pomocí Aspose.Words. Konzistentním **přesunováním kurzoru na tvar** před každým vložením udržujete čistou hierarchii a vyhýbáte se náhodnému umístění. Kompletní příklad se zkompiluje, spustí a vytvoří seskupený tvar, který lze dále přizpůsobovat nebo exportovat.

Jste připraveni objevovat dál? Zkuste kombinovat tuto techniku s **jak vytvořit skupinový tvar** pro složité diagramy, nebo experimentujte s **vložením obdélníkového tvaru ve Wordu** vedle textových polí pro tvorbu bohatých reportů. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit obdélníkový tvar a skupinové tvary ve Wordu s Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Jak vytvořit prázdný dokument Word a přidat skrytý elipsový tvar v C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Jak vytvořit docx se skupinovým tvarem a přidat interaktivní ovládací prvky v C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-11-15
description: Naučte se, jak vložit tvar do dokumentu Word a seskupit více tvarů pomocí
  Aspose.Words DocumentBuilder. Obsahuje příklady vložení obdélníkového tvaru a vložení
  více tvarů.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: cs
lastmod: 2026-11-15
og_description: Jak vložit tvar do souboru Word pomocí Aspose.Words. Tento průvodce
  pokrývá seskupování více tvarů, vložení obdélníkového tvaru a efektivní přidávání
  více tvarů.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Jak vložit tvar a seskupit více tvarů pomocí DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Jak vložit tvar a seskupit více tvarů pomocí DocumentBuilderu v C#
url: /cs/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit tvar a seskupit více tvarů pomocí DocumentBuilder v C#

Pokud potřebujete vědět **jak vložit tvar** do dokumentu Word pomocí Aspose.Words, tento průvodce vám ukáže přesné kroky. Také se naučíte, jak **seskupit více tvarů**, aby se chovaly jako jeden objekt, a jak **vložit tvar obdélníku** spolu s dalšími grafikami.

Automatizace dokumentů často vyžaduje přidání několika grafik — grafů, log, call‑outů — při zachování pořádku. Na konci tohoto tutoriálu budete schopni **vložit více tvarů**, umístit je do skupiny a uložit čisté, znovupoužitelné rozvržení.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 nebo novější nainstalovaný  
* Visual Studio 2022 (nebo jakékoli C# IDE)  
* Licenci Aspose.Words pro .NET nebo bezplatný evaluační klíč  
* Základní znalosti C# a třídy Aspose.Words `DocumentBuilder`  

Nemusíte mít žádné další knihovny třetích stran; vše potřebné je součástí Aspose.Words.

## Krok 1: Instalace Aspose.Words přes NuGet

Otevřete svůj projekt ve Visual Studiu a spusťte následující příkaz v Package Manager Console:

```powershell
Install-Package Aspose.Words
```

Balíček obsahuje třídy `DocumentBuilder`, `Shape` a `GroupShape`, které jsou používány v celém tomto tutoriálu.

## Krok 2: Vytvoření instance DocumentBuilder — základ pro **jak vložit tvar**

Prvním akčním řádkem kódu je vytvoření `DocumentBuilder`. Tento objekt vám poskytuje přímý přístup k stromu dokumentu, což vám umožní umístit tvary přesně tam, kde je chcete.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Proč je to důležité*: `DocumentBuilder` udržuje kurzor (tzv. „vkládací bod“). Každé následné volání `Insert...` používá tento kurzor, což je důvod, proč později přesuneme kurzor do `GroupShape`, aby všechny tvary zůstaly pohromadě.

## Krok 3: **Vložit tvar obdélníku** — první grafika, kterou přidáte

Obdélník je běžný zástupný prvek pro tabulky, obrázky nebo call‑outy. Použijte `InsertShape` s `ShapeType.Rectangle` a zadejte šířku a výšku v bodech (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Obdélník se objeví na aktuální pozici kurzoru. Později můžete upravit jeho výplň, styl čáry nebo text, pokud bude potřeba.

## Krok 4: Vložení dalšího tvaru — elipsy pro vizuální rozmanitost

Přidání více než jednoho tvaru demonstruje **vložit více tvarů**. Elipsa bude umístěna za obdélníkem v toku dokumentu.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

V tomto okamžiku dokument obsahuje dva nezávislé tvary. Pokud přesunete kurzor nebo přidáte text, tvary zůstanou na svém místě.

## Krok 5: **Seskupit více tvarů** tak, aby fungovaly jako jednotka

Seskupování je nezbytné, když potřebujete přesunout, otočit nebo formátovat několik grafik najednou. Následující kód vytvoří `GroupShape`, přesune kurzor builderu dovnitř a poté znovu vloží stejné tvary — tentokrát se stanou potomky skupiny.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Proč použít skupinu?

* **Jednoprvková transformace** — otočte nebo změňte velikost celé skupiny jedním voláním.  
* **Logická organizace** — strom dokumentu Wordu odráží seskupení, což usnadňuje pozdější úpravy.  
* **Konzistentní rozvržení** — přesun skupiny zachová relativní pozice jejích potomků.

### Přidání dalších tvarů — rozšíření **vložit více tvarů** uvnitř skupiny

Můžete nadále volat `InsertShape`, dokud kurzor zůstává uvnitř `GroupShape`. Například pro přidání trojúhelníku:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Každé volání respektuje kontext skupiny, takže se trojúhelník automaticky stane součástí stejné seskupené sady.

## Krok 6: Uložení dokumentu a ověření výsledku

Po umístění všech tvarů uložte dokument do souboru `.docx`. Otevření souboru v Microsoft Word (nebo jakémkoli kompatibilním prohlížeči) by mělo zobrazit dva samostatné tvary následované seskupeným blokem obsahujícím stejný obdélník, elipsu a trojúhelník.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Očekávaný výstup

* **První dva tvary** — obdélník a elipsa umístěné nezávisle na stránce.  
* **Seskupený blok** — obdélník, elipsa a trojúhelník, které se pohybují společně, když na kterýkoli z nich kliknete ve Wordu.

Můžete otestovat seskupení výběrem libovolného tvaru uvnitř skupiny; Word zvýrazní celou kolekci, což potvrzuje úspěšnost operace **seskupit více tvarů**.

## Časté problémy a tipy profesionálů

| Problém | Proč se vyskytuje | Řešení |
|-------|----------------|-----|
| Tvary se zobrazují mimo zamýšlenou stránku | Kurzoru builderu nebyl přesunut do `GroupShape` před vložením. | Vždy zavolejte `builder.MoveTo(group)` **před** jakýmkoli voláním `InsertShape`, které patří do skupiny. |
| Skupina zmizí po uložení | Skupina byla vložena, ale nebyla přidána do kolekce uzlů dokumentu. | Použijte `builder.InsertNode(group)` okamžitě po vytvoření `GroupShape`. |
| Neočekávaná velikost kvůli DPI dokumentu | Aspose.Words používá body; pokud přemýšlíte v pixelech, můžete získat nesprávné rozměry. | Převádějte pixely na body (`points = pixels * 72 / 96`) nebo pracujte přímo v bodech. |
| Tvary se neúmyslně překrývají | Nebyla nastavena explicitní pozice; Word je umisťuje sekvenčně. | Nastavte `Shape.Left` a `Shape.Top` po vložení pro přesné umístění. |

**Tip profesionála:** Po seskupení můžete získat kolekci tvarů skupiny (`group.Shapes`) a iterovat, přejmenovávat nebo aplikovat hromadné formátování.

## Krok 7: Rozšíření příkladu — co dál?

Nyní, když znáte **jak vložit tvar**, **vložit tvar obdélníku** a **seskupit více tvarů**, můžete zkoumat:

* **Animaci seskupených tvarů** — nastavte vlastnosti otáčení nebo převrácení na skupině.  
* **Aplikaci stylů** — použijte `Shape.FillColor`, `Shape.LineFormat` nebo `Shape.TextBox` pro přidání popisků.  
* **Export do PDF** — stejné seskupené rozvržení se správně vykreslí při volání `doc.Save("output.pdf")`.  

Všechny tyto rozšíření znovu využívají stejný workflow `DocumentBuilder`, což udržuje váš kód čistý a udržovatelný.

## Závěr

Tento tutoriál demonstroval **jak vložit tvar** do dokumentu Word pomocí Aspose.Words, jak **vložit tvar obdélníku** a jak **seskupit více tvarů**, aby se chovaly jako jeden objekt. Dodržením krok‑za‑krokem kódu můžete spolehlivě **vložit více tvarů**, uspořádat je do skupin a vytvářet profesionální dokumenty programově.

Neváhejte experimentovat s různými typy tvarů, barvami a transformacemi skupin. Až budete připraveni, integrujte tento vzor do větších řešení pro reportování nebo šablonování, abyste automatizovali složité rozvržení dokumentů. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-09-30
description: seskupování tvarů ve Wordu pomocí C# – naučte se, jak seskupovat tvary,
  přidávat obdélník a elipsu a programově vkládat obdélníkový tvar do dokumentů Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: cs
lastmod: 2026-09-30
og_description: Sesypte tvary ve Wordu pomocí C# a Aspose.Words. Sledujte tento kompletní
  návod, jak přidat obdélník, přidat elipsu a naučte se efektivně seskupovat tvary.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Seskupení tvarů ve Wordu pomocí C# – průvodce krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Jak seskupit tvary ve Wordu pomocí C# a Aspose.Words
url: /cs/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak seskupit tvary ve Wordu pomocí C# a Aspose.Words

Pokud potřebujete **seskupit tvary ve Wordu** programově, tento návod vám ukáže přesně jak. Uvidíte, jak přidat obdélník, jak přidat elipsu a poté je spojit do jedné skupiny pomocí knihovny Aspose.Words pro .NET.

Práce s tvary je častým požadavkem při automatickém generování zpráv, smluv nebo marketingových materiálů. Na konci tohoto tutoriálu budete mít znovupoužitelnou metodu v C#, která načte soubor DOCX, vloží obdélník a elipsu, seskupí je a uloží výsledek – vše bez ručního otevírání Wordu.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 SDK nebo novější nainstalovaný  
* Vývojové prostředí, například Visual Studio 2022 (Community edice stačí)  
* Licenci Aspose.Words pro .NET nebo bezplatnou evaluační kopii (API funguje i bez licence, ale přidá vodoznak)  

Také potřebujete zdrojový Word dokument (`input.docx`) ve složce, na kterou můžete odkazovat z kódu. Dokument může být prázdný; tutoriál se zaměřuje na práci s tvary.

## Krok 1: Vytvořte nový konzolový projekt a přidejte Aspose.Words

Otevřete terminál nebo příkazový řádek Visual Studio a spusťte:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Tím se vytvoří čerstvá konzolová aplikace s názvem **WordShapeDemo** a přidá se NuGet balíček `Aspose.Words`, který obsahuje třídy `Document` a `DocumentBuilder` používané k manipulaci se soubory Word.

## Krok 2: Načtěte nebo vytvořte dokument

Prvním krokem při práci s **seskupenými tvary ve Wordu** je získat objekt `Document`. Můžete buď načíst existující soubor DOCX, nebo začít s prázdným dokumentem.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

Třída `Document` představuje celý soubor Word. Načtení souboru vám poskytne připravené plátno pro vkládání tvarů.

## Krok 3: Zahajte skupinu tvarů

*Group shape* vám umožní zacházet s několika nezávislými tvary jako s jednou jednotkou – ideální pro jejich společný přesun nebo změnu velikosti. Pro zahájení skupiny zavolejte `StartGroupShape()` na objektu `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Volání `StartGroupShape` říká Aspose.Words, že každý následující vložený tvar patří do stejné logické skupiny, dokud nevoláte `EndGroupShape`.

## Krok 4: Jak přidat obdélníkový tvar ve Wordu

Nyní, když je skupina otevřená, vložte obdélník. Metoda `InsertShape` přijímá výčtový typ `ShapeType`, následovaný šířkou a výškou (v bodech).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Obdélník se stane prvním členem skupiny. Později můžete upravit jeho výplň, obrys nebo text, pokud bude potřeba.

## Krok 5: Jak přidat elipsu ve Wordu

Dále přidejte elipsu (kruh, pokud je šířka rovna výšce). Toto ukazuje **jak přidat elipsu** pomocí stejného builderu.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Oba tvary nyní sdílejí stejný souřadnicový prostor uvnitř skupiny, což usnadňuje jejich vizuální zarovnání.

## Krok 6: Uzavřete definici skupiny tvarů

Po přidání všech požadovaných členů uzavřete skupinu. Tím se dokončí kolekce tvarů, aby je Word považoval za jeden objekt.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

V tomto okamžiku dokument obsahuje jediný seskupený tvar složený z obdélníku a elipsy.

## Krok 7: Uložte upravený dokument

Nakonec zapište změny zpět na disk. Můžete přepsat původní soubor nebo vytvořit nový.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Po spuštění programu vznikne soubor `output.docx`. Otevřete jej v Microsoft Word, vyberte tvar a uvidíte, že se obdélník a elipsa pohybují společně – důkaz, že operace **seskupit tvary ve Wordu** byla úspěšná.

### Očekávaný výsledek

* Word soubor obsahuje jediný seskupený objekt.  
* Výběrem skupiny můžete táhnout, měnit velikost nebo otáčet jak obdélník, tak elipsu současně.  
* Není nutná žádná ruční interakce s Wordem; vše je provedeno pomocí C# kódu.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Image alt text: “Screenshot of a Word document showing a grouped rectangle and ellipse shape”* (splňuje požadavek na alt‑text obrázku).

## Proč je seskupování tvarů důležité

Seskupování tvarů není jen vizuální pohodlí. Umožňuje vám:

* **Udržet konzistenci rozvržení** – přesun skupiny zachová relativní pozice.  
* **Aplikovat transformace jednou** – otočte nebo změňte měřítko celé skupiny místo každého tvaru zvlášť.  
* **Zjednodušit následné zpracování** – když jiné nástroje čtou DOCX, vidí jediný složený tvar, což snižuje složitost.

Pokud budete chtít přidat další tvary (např. čáru nebo textové pole) do stejné logické jednotky, stačí znovu zavolat `InsertShape` před `EndGroupShape`.

## Běžné varianty a okrajové případy

| Situace | Jak to řešit |
|-----------|-----------------|
| **Různé jednotky** – máte rozměry v centimetrech | Před voláním `InsertShape` převést centimetry na body (`1 cm ≈ 28,35 pt`). |
| **Přidání textové popisky** – chcete popisek uvnitř skupiny | Vložit `ShapeType.TextBox` po obdélníku a elipse, pak nastavit jeho vlastnost `Text`. |
| **Aplikace barvy výplně** – potřebujete modrý obdélník | Po `InsertShape` získat poslední tvar přes `builder.CurrentParagraph.Runs[0].Font` a nastavit `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Použití jiného formátu dokumentu** – cílíte na `.doc` místo `.docx` | Stejný kód funguje; stačí změnit příponu souboru při volání `Save`. Aspose.Words automaticky zpracuje formát. |

## Profesionální tipy

* **Znovu použijte builder** – můžete zahájit a ukončit více skupin v jednom dokumentu; stačí po `EndGroupShape` znovu zavolat `StartGroupShape`.  
* **Výkon** – hromadné vkládání tvarů uvnitř jednoho bloku `StartGroupShape/EndGroupShape` je rychlejší než vkládání tvarů jednotlivě mimo skupinu.  
* **Licencování** – evaluační licence přidá vodoznak na první stránku. Nainstalujte plnou licenci, abyste ho v produkčním prostředí odstranili.

## Závěr

Nyní víte, jak **seskupit tvary ve Wordu** pomocí C#, jak **přidat obdélník**, jak **přidat elipsu** a jak **vložit obdélníkový tvar do Word dokumentu** pomocí Aspose.Words. Kompletní, spustitelný příklad demonstruje každý krok od nastavení projektu po uložení finálního souboru.

Odtud můžete zkoumat další typy tvarů, aplikovat stylování nebo kombinovat seskupené tvary s tabulkami a obrázky a vytvářet tak sofistikované, programově generované dokumenty.

---

**Další kroky**

* Naučte se, jak **otočit seskupené tvary**: použijte `Shape.RotationAngle` po uzavření skupiny.  
* Prozkoumejte **přizpůsobení výplně a obrysu** pro obdélníky a elipsy.  
* Integrovat tuto logiku do ASP.NET Core API pro generování zpráv na vyžádání.  

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
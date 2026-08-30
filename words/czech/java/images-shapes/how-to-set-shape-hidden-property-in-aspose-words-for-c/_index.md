---
category: general
date: 2026-08-20
description: Naučte se, jak nastavit vlastnost skrytí tvaru v Aspose.Words pro C#.
  Tento průvodce ukazuje, jak vložit obrázek a skrýt tvar tak, aby se nikdy neobjevil
  v uživatelském rozhraní ani v tisku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: cs
lastmod: 2026-08-20
og_description: Nastavte skrytou vlastnost tvaru v Aspose.Words pomocí C#. Vložte
  obrázek, skryjte tvar a zajistěte, aby se nikdy nezobrazoval v uživatelském rozhraní
  ani v tisku.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Nastavte skrytou vlastnost tvaru v Aspose.Words – kompletní průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Jak nastavit skrytou vlastnost tvaru v Aspose.Words pro C#
url: /cs/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit vlastnost skrytí tvaru v Aspose.Words pro C#

Pokud potřebujete **nastavit vlastnost skrytí tvaru** v dokumentu Word, tento tutoriál vám ukáže přesné kroky pomocí Aspose.Words pro .NET. Ať už vytváříte šablonový engine, generujete zprávy nebo vkládáte logo, které má zůstat neviditelné, naučíte se, jak vložit obrázek a skrýt tvar, aby se nikdy neobjevil v uživatelském rozhraní ani v tisku.

V tomto průvodci také pokrýváme **vložení obrázku do dokumentu**, vysvětlujeme, proč je skrytí tvaru důležité pro tisk, a procházíme kompletním spustitelným kódem. Nejsou potřeba žádné externí odkazy – stačí zkopírovat, vložit a spustit.

## Požadavky

* .NET 6.0 nebo novější (nejnovější verze Aspose.Words cílí na .NET 6+)
* Platná licence Aspose.Words pro .NET (nebo použijte režim bezplatného hodnocení)
* Visual Studio 2022 nebo jakékoli C# IDE, které preferujete
* Soubor s obrázkem (např. `logo.png`) umístěný ve složce, na kterou můžete odkazovat z kódu

## Krok 1: Vytvořte nový Document a DocumentBuilder

`DocumentBuilder` třída je vstupním bodem pro programové vytváření obsahu Word. Umožňuje vkládat odstavce, tabulky a tvary jako obrázky.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč tento krok?*  
Vytvoření `Document` vám poskytuje paměťovou reprezentaci souboru .docx, zatímco `DocumentBuilder` poskytuje plynulé API pro vkládání objektů. Bez těchto objektů nemůžete do dokumentu umístit tvar.

## Krok 2: Vložte obrázek jako tvar

Aspose.Words zachází s každým obrázkem jako s `Shape`. Metoda `InsertImage` vrací tuto instanci `Shape`, kterou můžete později upravovat.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Proč tento krok?*  
Použití `InsertImage` nejen přidá obrázek do toku textu, ale také vám poskytne referenci (`picture`), kterou můžete konfigurovat. To je nezbytné pro **vlastnost skrytí tvaru v C#**, kterou nastavíme dále.

## Krok 3: Nastavte vlastnost skrytí tvaru

Vlastnost `Hidden` řídí, zda se tvar podílí na uživatelském rozhraní a tisku. Nastavením na `true` se tvar stane neviditelným v UI Wordu a zaručuje, že nebude vytištěn.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Proč tento krok?*  
Když je tvar označen jako skrytý, Word ho zachází jako komentář – je přítomen ve struktuře dokumentu, ale nikdy se nezobrazí. To je podstata **nastavení vlastnosti skrytí tvaru**.

## Krok 4: Uložte dokument

Nakonec zapište dokument na disk. Můžete zvolit libovolný formát podporovaný Aspose.Words (`.docx`, `.pdf`, `.html` atd.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Proč tento krok?*  
Uložení dokončuje změny v paměti. Otevření výsledného `.docx` v Microsoft Wordu nezobrazí žádný viditelný obrázek a export do PDF potvrzuje, že se tvar nikdy neobjeví ve výstupu tisku.

## Kompletní, spustitelný příklad

Spojením všeho dohromady je zde kompletní program, který můžete zkompilovat a spustit:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Očekávaný výstup**

* Otevření `HiddenImageDocument.docx` v Microsoft Wordu nezobrazí žádný viditelný obrázek.
* Exportování nebo tisk dokumentu (nebo otevření PDF) také nezobrazí žádný obrázek.
* Skrytý tvar stále existuje v XML dokumentu, což můžete ověřit otevřením `.docx` jako zip a prohlížením `word/document.xml` – uvidíte element `<w:pict>` s atributem `w:hidden="true"`.

## Běžné varianty a okrajové případy

| Situace | Co dělat | Proč je to důležité |
|-----------|------------|----------------|
| **Chybějící soubor obrázku** | Zabalte `InsertImage` do `try/catch` a ošetřete `FileNotFoundException`. | Zabrání zhroucení aplikace a umožní zaznamenat jasnou chybu. |
| **Více skrytých tvarů** | Zavolejte `picture.Hidden = true` pro každý `Shape`, který vložíte, nebo iterujte přes `doc.GetChildNodes(NodeType.Shape, true)`. | Zajišťuje, že každý nežádoucí vizuální prvek zůstane neviditelný. |
| **Potřeba, aby byl tvar viditelný jen v režimu úprav** | Nastavte `picture.Hidden = false` po úpravách, pak před uložením znovu přepněte. | Umožňuje pracovat s tvarem v UI, zatímco finální výstup zůstane čistý. |
| **Tisk na starších verzích Wordu** | Ověřte dokument ve Wordu 2010 nebo novějším; příznak hidden je podporován ve všech moderních verzích. | Zajišťuje kompatibilitu napříč uživatelskou základnou. |
| **Použití jiného formátu souboru (např. přímo PDF)** | Příznak `Hidden` funguje stejně; Aspose.Words jej respektuje během konverze do PDF. | Potvrzuje, že **zabránit tvaru v tisku** funguje pro všechny cílové exporty. |

## Pro tip: Ověřte příznak hidden programově

Pokud potřebujete před uložením potvrdit, že je tvar skrytý, můžete zkontrolovat vlastnost:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Tato jednoduchá kontrola je užitečná v automatizovaných pipelinech, kde musíte garantovat soulad s politikami generování dokumentů.

## Závěr

Nyní víte, jak **nastavit vlastnost skrytí tvaru** v Aspose.Words pro C#. Vložením obrázku, nastavením `picture.Hidden = true` a uložením dokumentu zůstane tvar mimo UI a nikdy se neobjeví ve výstupu tisku. Tato technika je nezbytná, když potřebujete zástupné znaky, vodoznaky nebo brandingové prvky, které mají zůstat neviditelné pro koncové uživatele.

### Co dál?

* Prozkoumejte další vlastnosti tvaru, jako jsou `picture.WrapType`, `picture.Rotation` a `picture.RelativeHorizontalPosition`.
* Naučte se, jak **skrýt tvar v Aspose.Words** podmíněně na základě vstupu uživatele nebo konfigurace.
* Kombinujte skryté tvary s cykly **vložení obrázku do dokumentu** pro generování dynamických, neviditelných značek pro pozdější zpracování (např. pole hromadné korespondence).

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořte obdélníkový tvar ve Wordu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Vytvořte skupinový tvar v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vložte inline obrázek do dokumentu Word pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
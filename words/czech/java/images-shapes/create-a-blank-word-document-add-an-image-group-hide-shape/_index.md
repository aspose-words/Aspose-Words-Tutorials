---
category: general
date: 2026-10-10
description: Vytvořte prázdný dokument Word, vložte obrázek do Wordu, přidejte skupinu
  obrázků a skryjte tvar v uloženém souboru. Postupujte podle tohoto návodu krok za
  krokem.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: cs
lastmod: 2026-10-10
og_description: Vytvořte prázdný dokument Word, vložte do něj obrázek, přidejte skupinu
  obrázků a skryjte tvar. Tento návod ukazuje kompletní kód v C#.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Vytvořte prázdný dokument Word, přidejte skupinu obrázků, skryjte tvar
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Vytvořte prázdný dokument Word, přidejte skupinu obrázků, skryjte tvar
url: /cs/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word, přidejte skupinu obrázků, skryjte tvar

Pokud potřebujete **vytvořit prázdný dokument Word** a později skrýt vizuální prvky, tento tutoriál vám ukáže přesně jak. Naučíte se vložit obrázek do Wordu, přidat skupinu obrázků a skrýt tvar v dokumentu Word pomocí jedné znovupoužitelné C# rutiny.

Použijeme knihovnu Aspose.Words pro .NET, která umožňuje manipulovat se soubory .docx bez nainstalovaného Microsoft Wordu. Na konci tohoto průvodce budete mít spustitelný program, který vytvoří soubor Word obsahující skrytou skupinu obrázků, připravenou pro další zpracování nebo podmíněné zobrazení.

## Požadavky

- .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.6+)
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)
- Složka na disku, kde můžete číst soubor s obrázkem a zapisovat výstupní dokument
- Základní znalost C# a Visual Studio (nebo libovolného IDE, které preferujete)

## Vytvoření prázdného dokumentu Word pomocí Aspose.Words

Prvním krokem je **vytvořit prázdný dokument Word**. Aspose.Words poskytuje třídu `Document`, která představuje Word soubor v paměti. Vytvoření instance bez argumentů vám dá prázdný dokument připravený pro obsah.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité:* Začátek s prázdným dokumentem zajišťuje, že žádné skryté formátování nebo zbylé sekce nebudou rušit tvar, který později přidáte.

## Vložení obrázku do Wordu pomocí DocumentBuilder

Dále **vložíme obrázek do Wordu** tak, že nejprve vytvoříme skupinový tvar, který bude obrázek držet. Skupinové tvary vám umožňují zacházet s několika kreslicími objekty jako s jednou jednotkou, což je užitečné, když je později chcete skrýt nebo přesunout najednou.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

Metoda `InsertGroupShape` vytvoří prázdný kontejner. Rozměry jsou v bodech (1 bod = 1/72 palce). Přizpůsobte velikost tak, aby odpovídala rozlišení obrázku, který chcete vložit.

## Přidání skupiny obrázků do dokumentu

Nyní **přidáme skupinu obrázků** tím, že přesuneme kurzor builderu dovnitř nově vytvořené skupiny a vložíme obrázek. Všechny následující vložení budou součástí této skupiny.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Tip:* Použijte absolutní nebo správně escapovanou relativní cestu; jinak `InsertImage` vyhodí `FileNotFoundException`.

## Skrytí tvaru v dokumentu Word

Nakonec **skryjeme tvar v dokumentu Word** nastavením vlastnosti `Hidden` skupiny na `true`. Skryté tvary se při otevření dokumentu ve Wordu nezobrazí, ale zůstávají v souboru a lze je později programově odhalit.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Když otevřete *GroupHidden.docx* v Microsoft Word, uvidíte zcela prázdnou stránku, protože skupina obrázků je skrytá. Soubor stále obsahuje data obrázku, která můžete později odkrýt pomocí `group.Hidden = false`, pokud bude potřeba.

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do nového konzolového projektu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Očekávaný výstup**

- Soubor pojmenovaný `GroupHidden.docx` se objeví v `YOUR_DIRECTORY`.
- Otevření souboru ve Wordu zobrazí prázdnou stránku.
- Skrytý obrázek lze odhalit změnou `group.Hidden = false` a opětovným uložením.

## Časté varianty a okrajové případy

| Situace | Jak upravit kód |
|-----------|----------------------|
| **Více obrázků** | Vložte další volání `InsertImage` po `builder.MoveTo(group)`. Všechny obrázky zůstanou ve stejné skupině a sdílejí skrytý příznak. |
| **Různé formáty obrázků** | Aspose.Words podporuje PNG, JPEG, BMP, GIF, TIFF. Stačí změnit příponu souboru; není potřeba měnit kód. |
| **Podmíněná viditelnost** | Uložte vlastní proměnnou dokumentu (`doc.Variables.Add("ShowImages", "true")`) a přepínejte `group.Hidden` podle její hodnoty za běhu. |
| **Velké dokumenty** | Vytvořte skupinu na konkrétní stránce (`builder.InsertBreak(BreakType.PageBreak)`) před vložením skupiny, aby nedošlo k posunu rozvržení. |
| **Kompatibilita se staršími verzemi Wordu** | Uložte jako `doc.Save("output.doc", SaveFormat.Doc)`, pokud potřebujete starý formát `.doc`; skryté tvary se chovají stejně. |

**Profesionální tip:** Vždy nastavujte `group.Hidden = true` *po* vložení všech podřízených elementů. Změna příznaku před přidáním obsahu může způsobit, že některé elementy budou v starších verzích Wordu vykresleny neočekávaně.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **vložit obrázek do Wordu**, **přidat skupinu obrázků** a **skrýt tvar v dokumentu Word** pomocí Aspose.Words pro .NET. Kompletní příklad ukazuje každý krok od inicializace dokumentu až po uložení souboru, který obsahuje skrytou skupinu obrázků.

Dále můžete zkoumat:

- Přidání textových polí nebo grafů do stejné skupiny
- Použití `DocumentBuilder.StartBookmark` / `EndBookmark` k označení skrytých sekcí
- Programové přepínání viditelnosti na základě vstupu uživatele nebo proměnných dokumentu

Nebojte se experimentovat s různými tvary, velikostmi a pravidly viditelnosti, aby vyhovovaly vašemu automatizačnímu scénáři. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-10-13
description: Seskupování tvarů ve Wordu pomocí C# – naučte se, jak seskupovat tvary
  a přidávat tvary do skupiny pomocí Aspose.Words během několika snadných kroků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: cs
lastmod: 2026-10-13
og_description: Seskupování tvarů ve Wordu pomocí C# a Aspose.Words. Postupujte podle
  tohoto návodu a naučte se, jak seskupovat tvary a přidávat tvary do skupiny v dokumentu
  Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Seskupování tvarů ve Wordu pomocí C# – krok za krokem průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Seskupení tvarů ve Wordu pomocí C# – kompletní programovací průvodce
url: /cs/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skupinování tvarů ve Wordu pomocí C# – kompletní programovací průvodce

Pokud potřebujete **skupinovat tvary ve Wordu** programově, tento průvodce vám ukáže přesně jak. Po přečtení prvních dvou vět budete znát požadovaný kód, důvody pro každý krok a jak **přidat tvary do skupiny** bez překvapení.

Probereme vše od načtení souboru `.docx` až po uložení aktualizovaného dokumentu. Tutoriál předpokládá základní znalosti C# a odkaz na knihovnu Aspose.Words pro .NET. Žádná externí dokumentace není potřeba – stačí zkopírovat, vložit a spustit.

## Požadavky

- .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.7+)
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)
- Word dokument (`input.docx`), který již obsahuje alespoň dva tvary (např. obrázky, AutoShape)

> **Tip:** Pokud testujete, vytvořte jednoduchý Word soubor se dvěma obdélníky pomocí uživatelského rozhraní Wordu. Uložte jej jako `input.docx` do složky, kterou ovládáte.

## Skupinování tvarů ve Wordu – krok za krokem

Níže rozdělujeme proces do pěti logických kroků. Každý krok obsahuje přesný C# kód, vysvětlení *proč* je řádek potřeba a krátkou poznámku o častých úskalích.

### Krok 1: Načtení Word dokumentu

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Proč:** `Document` je vstupní bod pro jakoukoli manipulaci s Wordem. Poskytnutí úplné cesty k souboru načte dokument do paměti, což nám umožní dotazovat se na jeho strom uzlů a měnit jej.

**Úskalí:** Použití relativní cesty může selhat, pokud se pracovní adresář liší. Použijte absolutní cestu nebo `Path.Combine` s `AppContext.BaseDirectory`.

### Krok 2: Získání tvarů, které chcete seskupit

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Proč:** `GetChild` prochází strom dokumentu a vrací *n‑tý* uzel požadovaného typu. Nastavením `isDeep` na `true` prohledává celý dokument, ne jen aktuální sekci.

**Hraniční případ:** Pokud dokument obsahuje méně než dva tvary, `firstShape` nebo `secondShape` bude `null` a při pokusu o přetypování dojde k výjimce. Ošetřete to:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Krok 3: Vytvoření nového kontejneru `GroupShape`

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Proč:** `GroupShape` funguje jako rodičovský uzel, který může držet více objektů `Shape`. Dědí z `Shape`, takže jej lze vložit kamkoli, kde je povolen běžný tvar (např. do odstavce).

### Krok 4: Přidání jednotlivých tvarů do skupiny

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Proč:** `AppendChild` přesune tvary z jejich původních míst do nové skupiny. Po tomto volání původní tvary již neexistují jako samostatné uzly; stávají se součástí `groupShape`.

**Tip:** Skupinování automaticky upravuje relativní pozice podřízených tvarů. Pokud potřebujete konkrétní rozložení, nastavte vlastnost `GroupShape.Bounds` *před* přidáním podřízených uzlů.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Krok 5: Vložení skupinového tvaru do těla dokumentu

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Proč:** `GroupShape` musí být umístěn uvnitř odstavce (nebo buňky tabulky), aby byl vykreslen. Připojením k prvnímu odstavci zajistíme viditelné umístění bez narušení existujícího rozvržení.

### Krok 6: Uložení upraveného dokumentu

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Proč:** `Save` zapíše změny v paměti zpět do souboru `.docx`. Můžete také uložit do proudu nebo do PDF změnou přetížení.

**Ověření výsledku:** Otevřete `output.docx` v Microsoft Wordu. Měli byste vidět dva původní tvary nyní sloučené do jednoho seskupeného objektu. Výběrem skupiny se zobrazí standardní ovládací úchyty Wordu.

## Jak programově seskupovat tvary – podrobnější pohled

- **Vlastnictví uzlů:** Když zavoláte `AppendChild`, reference `ParentNode` tvaru se automaticky změní. Tím se zabrání „sirotkům“, kteří by mohli dokument poškodit.
- **Zachování formátování:** Skupinování **nepřichází** o žádné formátování tvaru (barvu výplně, styl čáry apod.). Všechny podřízené tvary si zachovají své původní vlastnosti.
- **Vnořené skupiny:** `GroupShape` může obsahovat další objekty `GroupShape`, což umožňuje víceúrovňové hierarchie. Vnitřní skupinu zacházejte jako s libovolným jiným tvarem.

## Přidání tvarů do skupiny a jejich pozdější správa

Pokud potřebujete po vytvoření první skupiny přidat další tvary, můžete znovu použít stejnou instanci `GroupShape`:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Když později potřebujete rozskupit, projděte `groupShape.GetChildNodes(NodeType.Shape, true)` a znovu vložte každý podřízený uzel tam, kde jej chcete mít.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Proč je to důležité:** Některé pracovní postupy vyžadují dočasné seskupení (např. zarovnání více objektů) a následné rozskupení pro další individuální úpravy.

## Kompletní spustitelný příklad

Níže je samostatný program, který můžete zkompilovat a spustit tak, jak je. Nahraďte `YOUR_DIRECTORY` skutečnou cestou k adresáři na vašem počítači.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Očekávaný výstup:** Po otevření `output.docx` se dva původní tvary objeví jako jeden seskupený objekt. Výběrem skupiny se zobrazí známé ovládací úchyty Wordu, které umožňují přesun, změnu velikosti nebo rotaci celého souboru najednou.

## Závěr

Nyní víte, jak **skupinovat tvary ve Wordu** pomocí C# a Aspose.Words, a viděli jste přesné kroky k **přidání tvarů do skupiny** a jejich následné manipulaci nebo rozskupení. Tato technika je ideální pro automatizaci rozvržení reportů, tvorbu složených diagramů nebo přípravu Word šablon, které vyžadují přesné umístění více objektů.

Dále prozkoumejte související témata, jako je **jak seskupovat tvary** s různými typy ukotvení, aplikace **pokročilého formátování** na seskupené objekty nebo export seskupeného výsledku do PDF. Experimentujte s vnořenými skupinami a vytvářejte tak komplexní grafiku programově.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Shadow Effect to Word Shapes – Complete C# Guide](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
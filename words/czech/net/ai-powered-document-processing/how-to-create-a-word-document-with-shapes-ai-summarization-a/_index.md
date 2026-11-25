---
category: general
date: 2026-11-25
description: Naučte se, jak vytvořit dokument Word, přidat obdélníkový tvar, shrnout
  dokument pomocí AI, přeložit text pomocí AI a uložit dokument jako DOCX pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: cs
lastmod: 2026-11-25
og_description: Vytvořte dokument Word, přidejte obdélníkový tvar, shrňte dokument
  pomocí AI, přeložte text pomocí AI a uložte dokument jako DOCX – vše v jednom C#
  tutoriálu.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Vytvořte dokument Word se tvary, AI shrnutím a překladem v C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Jak vytvořit dokument Word s tvary, AI shrnutím a překladem v C#
url: /cs/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit Word dokument s tvary, AI shrnutím a překladem v C#

Pokud potřebujete **vytvořit Word dokument** programově, tento průvodce vám přesně ukáže jak. Pomocí Aspose.Words pro .NET se naučíte **přidat obdélníkový tvar**, zavolat AI službu k **shrnutí dokumentu pomocí AI**, přeložit odstavec pomocí **translate text using AI**, a nakonec **uložit dokument jako DOCX**.

Mnoho vývojářů má potíže s propojením automatizace dokumentů a moderních AI funkcí. Na konci tohoto tutoriálu budete mít jediný, samostatný C# projekt, který vytvoří plně formátovaný *.docx* soubor, kompletní s vizuálním tvarem, AI‑generovaným shrnutím a vícejazyčným obsahem.

## Požadavky

- .NET 6.0 SDK nebo novější nainstalováno  
- Visual Studio 2022 (nebo jakékoli C# IDE)  
- Licence Aspose.Words pro .NET (nebo bezplatný evaluační klíč)  
- Přístup k internetu pro volání AI shrnutí a překladu  

Žádné další NuGet balíčky nejsou potřeba kromě `Aspose.Words` a `Aspose.Words.AI`.

## Krok 1: Nastavte projekt a přidejte požadované balíčky

Vytvořte nový konzolový projekt a přidejte knihovny Aspose.Words.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Tip:** Pokud plánujete použít evaluační režim, zavolejte `Aspose.Words.License.SetLicense("Aspose.Words.lic");` brzy v `Main`, aby se předešlo vodoznakům.

## Krok 2: Inicializujte dokument – jádro **create word document**

První spustitelný řádek kódu vytvoří nový objekt **Word document**. Tento objekt je plátnem pro všechny následné operace.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` usnadňuje vkládání textu, tvarů a ovládacích prvků, aniž byste museli ručně manipulovat se stromem nízkoúrovňových uzlů.

## Krok 3: **Add rectangle shape** do dokumentu

Obdélníkový tvar může sloužit jako vizuální zástupný prvek, pozadí popisku nebo jednoduchá grafika. Nejprve vytvoříme `GroupShape`, poté do něj vložíme `Rectangle`.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

Obdélník má šířku 100 bodů a výšku 50 bodů. Protože je uvnitř `GroupShape`, můžete později přidávat další prvky (např. textová pole) aniž byste se museli obávat kolizí rozvržení.

## Krok 4: Vložte plain‑text StructuredDocumentTag (SDT)

Objekty StructuredDocumentTag jsou užitečné pro ovládací prvky obsahu, které lze později svázat s datovými zdroji.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

Příznak `true` označuje značku jako **repeating** ovládací prvek, což je praktické pro šablony.

## Krok 5: Přidejte ActiveX CommandButton ovládací prvek (volitelné UI)

Pokud bude vygenerovaný dokument používán v prostředí, které podporuje ActiveX, můžete vložit tlačítko.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Tento krok je volitelný; můžete jej odstranit, pokud vaše cílové publikum nikdy neinteraguje s dokumentem ve Windows prostředí.

## Krok 6: **Summarize document with AI**

Aspose.Words.AI poskytuje pohodlný wrapper kolem služeb velkých jazykových modelů. Zde voláme `DocumentSummarizer.Summarize` s backendem OpenAI.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

Metoda analyzuje aktuální strom uzlů, extrahuje nejrelevantnější věty a vrátí stručný odstavec. Toto je jádro funkčnosti **summarize document with AI**.

## Krok 7: **Translate text using AI**

Dále ukážeme, jak přeložit ukázkový řetězec z angličtiny do francouzštiny. Metoda `Translator.Translate` interně volá model Google AI.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Můžete nahradit `Language.French` libovolnou podporovanou hodnotou výčtu jazyka, což umožňuje generování vícejazyčných dokumentů za běhu.

## Krok 8: **Save document as DOCX**

Nakonec uložte upravený dokument na disk. Metoda `Save` automaticky zapíše soubor *.docx*, pokud zadáte příponu `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

Soubor `Result.docx` nyní obsahuje:

- Obdélníkový tvar uvnitř skupinového tvaru  
- Plain‑textový ovládací prvek obsahu (SDT)  
- ActiveX CommandButton (pokud jste ponechali Krok 5)  
- AI‑generovaný souhrnný odstavec  
- Francouzský překlad „Hello world“

Soubor můžete otevřít v Microsoft Word a ověřit každý prvek.

## Kompletní zdrojový kód

Níže je kompletní, připravený k spuštění program. Zkopírujte jej do `Program.cs` a spusťte `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Očekávaný výstup

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Když otevřete `Result.docx`, uvidíte obdélníkový tvar poblíž horní části, SDT zástupný prvek, tlačítko, souhrnný odstavec a francouzský překlad vložený jako plain text.

## Závěr

Nyní víte, jak **vytvořit Word dokument** od nuly, **přidat obdélníkový tvar**, **shrnout dokument pomocí AI**, **přeložit text pomocí AI** a **uložit dokument jako DOCX** — vše pomocí několika stručných řádků C#. Tento vzor je škálovatelný: můžete nahradit pevně zakódované řetězce dynamickými daty, přidat další tvary nebo grafy a změnit poskytovatele AI úpravou parametrů `SummarizerOptions` nebo `Translator`.

### Co dál?

- Prozkoumejte varianty **add rectangle shape**: změňte barvu výplně, styl čáry nebo přidejte text uvnitř tvaru.  
- Použijte **summarize document with AI** na větších dokumentech k automatickému generování výkonných souhrnů.  
- Rozšiřte **translate text using AI** pro dávkové zpracování celých odstavců nebo tabulek pro vícejazyčné zprávy.  
- Kombinujte Aspose.Words charting API pro vložení vizualizací dat vedle AI‑generovaných poznatků.  

Neváhejte experimentovat a sdílet své výsledky v komentářích nebo na GitHubu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit prázdný word dokument a přidat obdélníkový tvar](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Vytvořit Group Shape v Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Přidat textový vodoznak do Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
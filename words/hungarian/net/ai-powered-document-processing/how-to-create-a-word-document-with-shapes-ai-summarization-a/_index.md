---
category: general
date: 2026-11-25
description: Tanulja meg, hogyan hozzon létre Word-dokumentumot, adjon hozzá téglalap
  alakzatot, összefoglalja a dokumentumot AI segítségével, fordítsa le a szöveget
  AI-val, és mentse a dokumentumot DOCX formátumban az Aspose.Words használatával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: hu
lastmod: 2026-11-25
og_description: Hozzon létre egy Word‑dokumentumot, adjon hozzá téglalap alakzatot,
  összefoglalja a dokumentumot AI‑val, lefordítja a szöveget AI‑val, és DOCX formátumban
  menti a dokumentumot – mindezt egyetlen C# oktatóanyagon belül.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Word-dokumentum létrehozása alakzatokkal, AI‑összefoglalóval és fordítással
  C#‑ban
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
title: Hogyan hozzunk létre Word-dokumentumot alakzatokkal, AI összefoglalóval és
  fordítással C#-ban
url: /hu/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre Word dokumentumot alakzatokkal, AI‑összefoglalóval és fordítással C#‑ban

Ha **programozottan szeretnél Word dokumentumot létrehozni**, ez az útmutató pontosan megmutatja, hogyan. Az Aspose.Words for .NET segítségével megtanulod, hogyan **adj hozzá téglalap alakzatot**, hogyan hívj meg egy AI‑szolgáltatást a **dokumentum AI‑összefoglalásához**, hogyan **fordíts szöveget AI‑val**, és végül hogyan **mentsd el a dokumentumot DOCX‑ként**.

Sok fejlesztő nehezen tudja összehangolni a dokumentum‑automatizálást a modern AI‑funkciókkal. A tutorial végére egy önálló C# projekted lesz, amely egy teljesen formázott *.docx* fájlt állít elő, benne egy vizuális alakzattal, AI‑által generált összefoglalóval és többnyelvű tartalommal.

## Előkövetelmények

Mielőtt elkezdenéd, győződj meg róla, hogy a következők telepítve vannak:

- .NET 6.0 SDK vagy újabb  
- Visual Studio 2022 (vagy bármely C# IDE)  
- Aspose.Words for .NET licenc (vagy ingyenes értékelő kulcs)  
- Internetkapcsolat az AI‑összefoglaló és fordítási hívásokhoz  

A `Aspose.Words` és `Aspose.Words.AI` könyvtárakon kívül nincs szükség további NuGet csomagokra.

## 1. lépés: Projekt létrehozása és a szükséges csomagok hozzáadása

Hozz létre egy új konzolos projektet, és húzd be az Aspose.Words könyvtárakat.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tipp:** Ha értékelő módban dolgozol, hívd meg a `Aspose.Words.License.SetLicense("Aspose.Words.lic");` hívást már a `Main` elején, hogy elkerüld a vízjelek megjelenését.

## 2. lépés: A dokumentum inicializálása – a **create word document** magja

Az első végrehajtható kódsor egy friss **Word dokumentum** objektumot hoz létre. Ez az objektum a vászon minden további művelethez.

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

A `DocumentBuilder` leegyszerűsíti a szöveg, alakzatok és vezérlők beszúrását anélkül, hogy alacsony szintű csomópontfákat kellene kézzel kezelni.

## 3. lépés: **Add rectangle shape** a dokumentumhoz

A téglalap alakzat használható vizuális helykitöltőként, címke háttérként vagy egyszerű grafikaként. Először egy `GroupShape`‑t hozunk létre, majd egy `Rectangle`‑t helyezünk bele.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

A téglalap 100 pont széles és 50 pont magas. Mivel egy `GroupShape`‑ben él, később további elemeket (pl. szövegdobozok) adhatsz hozzá anélkül, hogy a elrendezés ütközne.

## 4. lépés: Egyszerű szöveges StructuredDocumentTag (SDT) beszúrása

A StructuredDocumentTag objektumok hasznosak olyan tartalomvezérlőkhez, amelyeket később adatforrásokhoz lehet kötni.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

A `true` jelző azt jelöli, hogy a címke **ismétlődő** vezérlő, ami sablonok esetén kényelmes.

## 5. lépés: ActiveX CommandButton vezérlő hozzáadása (opcionális UI)

Ha a generált dokumentumot olyan környezetben használják, amely támogatja az ActiveX‑et, beágyazhatsz egy gombot.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Ez a lépés opcionális; eltávolíthatod, ha a célközönség soha nem interakcióba lép a dokumentummal Windows környezetben.

## 6. lépés: **Summarize document with AI**

Az Aspose.Words.AI egy kényelmes burkot biztosít a nagy nyelvi modellek szolgáltatásai köré. Itt a `DocumentSummarizer.Summarize` metódust hívjuk meg az OpenAI backenddel.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

A metódus elemzi a jelenlegi csomópontfát, kiválasztja a legrelevánsabb mondatokat, és egy tömör bekezdést ad vissza. Ez a **summarize document with AI** funkció magja.

## 7. lépés: **Translate text using AI**

Ezután bemutatjuk, hogyan fordítsunk egy mintaszöveget angolról franciára. A `Translator.Translate` metódus belsőleg egy Google AI modellt hív meg.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

A `Language.French` helyett bármely támogatott nyelvi enum értéket használhatsz, így a dokumentum generálása során könnyedén többnyelvűvé teheted.

## 8. lépés: **Save document as DOCX**

Végül mentsd el a szerkesztett dokumentumot a lemezre. A `Save` metódus automatikusan *.docx* fájlt hoz létre, ha a `.docx` kiterjesztést adod meg.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

A `Result.docx` fájl most a következőket tartalmazza:

- Egy téglalap alakzat egy csoport alakzaton belül  
- Egy egyszerű szöveges tartalomvezérlő (SDT)  
- Egy ActiveX CommandButton (ha megtartottad az 5. lépést)  
- Egy AI‑által generált összefoglaló bekezdés  
- A “Hello world” francia fordítása

Megnyithatod a fájlt a Microsoft Word‑ben, hogy ellenőrizd az egyes elemeket.

## Teljes forráskód

Az alábbi kódrészlet a teljes, azonnal futtatható program. Másold be a `Program.cs` fájlba, és futtasd a `dotnet run` parancsot.

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

### Várt kimenet

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Amikor megnyitod a `Result.docx` fájlt, a tetején látható lesz a téglalap alakzat, az SDT helykitöltő, a gomb, az összefoglaló bekezdés és a francia fordítás egyszerű szövegként beillesztve.

## Összegzés

Most már tudod, hogyan **hozz létre Word dokumentumot** a semmiből, hogyan **adj hozzá téglalap alakzatot**, hogyan **összefoglalj dokumentumot AI‑val**, hogyan **fordíts szöveget AI‑val**, és hogyan **mentsd el a dokumentumot DOCX‑ként** – mindezt néhány tömör C# sorral. Ez a minta skálázható: a keménykódolt szövegeket dinamikus adatokkal helyettesítheted, további alakzatokat vagy diagramokat adhatsz hozzá, és az AI‑szolgáltatót a `SummarizerOptions` vagy a `Translator` paraméterek módosításával cserélheted.

### Mi a következő?

- Fedezd fel a **add rectangle shape** variációkat: változtasd a kitöltőszínt, vonalstílust, vagy adj szöveget a alakzatba.  
- Használd a **summarize document with AI** funkciót nagyobb dokumentumokon, hogy automatikusan generálj vezetői összefoglalókat.  
- Bővítsd a **translate text using AI** megoldást, hogy egész bekezdéseket vagy táblázatokat batch‑feldolgozz többnyelvű jelentésekhez.  
- Kombináld az Aspose.Words diagram API‑kat, hogy adatvizualizációkat ágyazz be az AI‑által generált betekintések mellé.  

Kísérletezz nyugodtan, és oszd meg eredményeidet a kommentekben vagy a GitHub‑on. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek további API‑funkciók elsajátításában és alternatív megvalósítási megközelítések felfedezésében saját projektjeidben.

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
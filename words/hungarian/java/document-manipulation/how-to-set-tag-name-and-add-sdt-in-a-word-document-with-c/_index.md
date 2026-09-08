---
category: general
date: 2026-09-08
description: Állítsa be a címke nevét, és hozzon létre egy tartalomvezérlőt (SDT)
  egy Word-dokumentumban C#-ban. Tanulja meg, hogyan adjon hozzá SDT-t, írjon szöveget
  a címkébe, és módosítsa a dokumentumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: hu
lastmod: 2026-09-08
og_description: Állíts be címkenevet, és hozz létre egy tartalomvezérlőt (SDT) egy
  Word-dokumentumban C#-val. Kövesd ezt a lépésről‑lépésre útmutatót az SDT hozzáadásához,
  a címkébe szöveg írásához és a dokumentum módosításához.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Címke nevének beállítása és SDT hozzáadása Word-dokumentumban – C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hogyan állítsuk be a címke nevét és adjunk hozzá SDT-t egy Word-dokumentumban
  C#-val
url: /hu/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan állítsuk be a címke nevét és adjunk hozzá SDT-t egy Word dokumentumban C#-al

Ha **címke nevet** kell **beállítania** egy StructuredDocumentTag (SDT) számára Word fájlokkal dolgozva, ez az útmutató pontosan megmutatja, hogyan. Egy teljes, futtatható példát fog látni, amely **létrehozza a tartalomvezérlőt**, szöveget ír a címkébe, és **módosítja a Word dokumentumot** vég‑től‑végig.

A fejlesztők gyakran kérdezik: *„hogyan adhatunk sdt‑t* egy meglévő .docx-hez, majd *írhatunk szöveget a címkébe*?” – a válasz az Aspose.Words for .NET API használatában rejlik. A tutorial végére képes lesz megnyitni egy Word fájlt, beszúrni egy egyszerű szöveges SDT-t, beállítani a címke nevét, feltölteni tartalommal, és elmenteni a módosításokat anélkül, hogy elhagyott erőforrások maradnának.

## Előkövetelmények

* .NET 6.0 vagy újabb telepítve.
* Érvényes Aspose.Words for .NET licenc (vagy a kiértékelési verzióval is dolgozhat).
* Visual Studio 2022 (vagy bármely C#-ot támogató IDE).
* Egy bemeneti Word dokumentum (`input.docx`), amely egy mappában van, ahonnan a kódból hivatkozhat.

## 1. lépés: A projekt beállítása és a névterek importálása

Hozzon létre egy új Console App projektet, és adja hozzá az Aspose.Words NuGet csomagot:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Ezután adja hozzá a szükséges `using` direktívákat a `Program.cs` tetejéhez:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Ezek a névterek hozzáférést biztosítanak a `Document`, `DocumentBuilder` és a `StructuredDocumentTag` osztályhoz, amelyek elengedhetetlenek a **Word dokumentum módosításához**.

## 2. lépés: A meglévő Word dokumentum betöltése

Az első művelet a szerkeszteni kívánt fájl betöltése. Ez a lépés minden olyan esetben szükséges, amikor **Word dokumentum** tartalmát módosítja.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Miért töltjük be először a dokumentumot** – A `Document` objektum a teljes .docx csomagot reprezentálja a memóriában. Csak a betöltés után tud biztonságosan új csomópontokat, például egy SDT-t beszúrni.

## 3. lépés: StructuredDocumentTag (SDT) beszúrása és a címke nevének beállítása

Most megválaszoljuk a lényeges kérdést: **hogyan adhatunk sdt‑t** és **állíthatunk be címke nevet**. A `DocumentBuilder.InsertStructuredDocumentTag` metódust használjuk `SdtType.PlainText` értékkel. A második argumentum a címke neve, amelyet később programozottan vagy a Word felhasználói felületén keresztül hivatkozhat.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Magyarázat** – Az `InsertStructuredDocumentTag` egy `StructuredDocumentTag` példányt ad vissza. A `"MyTag"` átadásával **beállítjuk a címke nevét** közvetlenül a létrehozáskor. Ha később meg kell változtatni, új értéket adhat a `sdt.Tag`-nek.

## 4. lépés: Szöveg írása az újonnan létrehozott címkébe

Miután az SDT létezik, általában **szöveget szeretnénk írni a címkébe**, hogy a végfelhasználók lássák a helyőrző vagy alapértelmezett tartalmat. A `SetText` metódus pontosan ezt teszi.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Miért használjuk a SetText-et** – A `Text` tulajdonság közvetlen beállítása felülírná az egész csomópont-hierarchiát. A `SetText` biztonságosan frissíti a tartalomvezérlő belső szövegét, miközben megőrzi a struktúráját.

## 5. lépés: A módosított dokumentum mentése

Végül mentse el a változtatásokat egy új fájlba. Ez befejezi a **Word dokumentum módosítása** munkafolyamatot.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Amikor megnyitja a `output.docx` fájlt a Microsoft Wordben, egy egyszerű szöveges tartalomvezérlőt lát, amely **MyTag** felirattal rendelkezik, és a „Sample content” szöveget tartalmazza. A vezérlő manuálisan szerkeszthető, és a címke neve továbbra is elérhető a Word fejlesztői eszközein keresztül.

## Teljes forráskód

Az alábbiakban a teljes, önálló program látható. Másolja be a `Program.cs` fájlba, és futtassa; további kódrészletek nem szükségesek.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Várt kimenet a konzolon

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Hogyan néz ki a létrehozott Word fájl

![Word dokumentum, amely egy MyTag nevű tartalomvezérlőt mutat a „Sample content” szöveggel](/images/word-sdt-example.png){: .img-fluid alt="Címke nevének beállítása példa egy Word dokumentumban"}

*A képernyőkép bemutatja az SDT-t, amelynek **címke neve** *MyTag*, és a beágyazott szöveg látható.*

## Gyakori variációk és szélhelyzetek

| Helyzet | Hogyan kezeljük |
|-----------|------------------|
| **Rich‑text SDT létrehozása** | Használja az `SdtType.RichText`-et a `PlainText` helyett. |
| **Eltérő címke név beállítása a beszúrás után** | `sdt.Tag = "NewTag";` – a címke nevet bármikor újra beállíthatja. |
| **Az SDT hozzáadása egy adott bekezdésbe** | Mozgassa a builder kurzorát (`builder.MoveToParagraph(index)`) az `InsertStructuredDocumentTag` hívása előtt. |
| **Több SDT ugyanabban a dokumentumban** | Ismételje meg a 3‑4. lépéseket minden vezérlőnél; mindegyiknek egyedi címke neve lehet. |
| **Védett dokumentumok kezelése** | Győződjön meg róla, hogy a dokumentum nincs védve (`doc.Unprotect()`) az SDT beszúrása előtt. |

## Pro tippek a robusztus Word automatizáláshoz

* **Licenc korai beállítása** – Hívja meg a `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` kódot a `Main` elején, hogy elkerülje a kiértékelési vízjelek megjelenését.
* **Objektumok felszabadítása** – Tegye a `Document`-et egy `using` blokkba, ha .NET Framework-öt céloz, hogy garantálja a fájlkezelők felszabadítását.
* **Címke létezésének ellenőrzése** – Dokumentum későbbi olvasásakor használja a `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` metódust a `Tag` tulajdonság alapján történő címkék megtalálásához.
* **Teljesítmény** – Nagy dokumentumok esetén csak a szükséges szakaszokat töltse be a `LoadOptions` használatával, `LoadFormat.Docx` és `LoadFormat.Auto` beállításokkal.  

## Következtetés

Most már tudja, hogyan **állítsa be a címke nevét**, **hozzon létre egy tartalomvezérlőt**, **írjon szöveget a címkébe**, és **módosítson egy Word dokumentumot** C#-al. A teljes példa bemutatja a szokásos mintát a **hogyan adhatunk sdt‑t** és a változások biztonságos mentésére.  

Innen tovább

## Mit érdemes most tanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Tartalom hozzáadása a Document Builder segítségével az Aspose.Words for .NET-ben](/words/english/net/add-content-using-document-builder/)
- [Word dokumentum – Hogyan távolítsunk el tartalmat](/words/english/net/remove-content/)
- [Word dokumentum létrehozása az Aspose.Words segítségével – Lépésről‑lépésre útmutató](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
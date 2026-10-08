---
category: general
date: 2026-10-07
description: Tanulja meg, hogyan illesszen be OLE parancsgombot egy Word dokumentumba
  az Aspose.Words C# segítségével. Lépésről‑lépésre útmutató a DocumentBuilder, a
  tulajdonságok és a fájl mentése témakörökben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: hu
lastmod: 2026-10-07
og_description: OLE parancsgomb beszúrása egy Word dokumentumba C#-vel. Kövesse ezt
  a tömör útmutatót, hogy hozzáadjon, konfiguráljon és elmentse a funkcionális CommandButton-t
  az Aspose.Words segítségével.
og_image_alt: Insert OLE command button example in Word document
og_title: OLE parancsgomb beszúrása Word-be C#-val – teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Hogyan szúrjunk be OLE parancsgombot egy Word-dokumentumba C#-ban
url: /hu/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szúrjunk be OLE parancsgombot egy Word dokumentumba C#-ban

Ha programozott módon **OLE parancsgombot** kell beillesztenie egy Word fájlba, ez az útmutató pontosan megmutatja, hogyan teheti ezt meg az Aspose.Words for .NET segítségével. Akár egy űrlappal kitöltött jelentést készít, akár egy felhasználói interakciót igénylő sablont automatizál, az alábbi lépések egy teljes, futtatható megoldást nyújtanak.

Megtanulja, hogyan hozzon létre egy üres dokumentumot, használja a `DocumentBuilder`-t egy `Forms2OleControl` elhelyezéséhez, állítsa be a gomb feliratát és nevét, majd végül mentse el a `.docx`-et. Az Aspose.Words könyvtáron kívül nincs szükség külső eszközökre.

## Előfeltételek

* .NET 6.0 vagy újabb (a kód .NET Framework 4.7+ verzióval is működik)
* Érvényes Aspose.Words for .NET licenc vagy egy ingyenes értékelő kulcs
* Visual Studio 2022 (vagy bármelyik kedvelt C# IDE)
* Alapvető ismeretek a C# szintaxisról és a Word OLE koncepciókról

> **Pro tipp:** Ha az ingyenes értékelő verziót használja, a generált dokumentum egy kis vízjelet tartalmazni fog. Egy licencelt verzió automatikusan eltávolítja azt.

## 1. lépés: Aspose.Words telepítése

Adja hozzá az Aspose.Words csomagot a projektjéhez a NuGet-en keresztül:

```bash
dotnet add package Aspose.Words
```

A csomag tartalmazza az OLE vezérlőkhöz szükséges `Aspose.Words.Drawing` és `Aspose.Words.Drawing.Ole` névtér(eket).

## 2. lépés: OLE parancsgomb beillesztése a DocumentBuilder-rel

A tutorial központi része az `InsertForms2OleControl` metódus. Ez egy **Forms2 OLE CommandButton**-t hoz létre egy adott helyen és méretben.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Miért működik ez

* `DocumentBuilder` az elsődleges API a Word dokumentumok programozott építéséhez.  
* `InsertForms2OleControl` azt mondja az Aspose.Words-nak, hogy ágyazzon be egy **Forms2 OLE vezérlőt**, amely a régi Word űrlap technológia, és támogatja a parancsgombokat, jelölőnégyzeteket stb.  
* Az `OleControlType.CommandButton` enum érték meghatározza, hogy a beillesztett vezérlő egy **parancsgomb** – pontosan az a típus, amelyet akkor kért, amikor **OLE parancsgombot** akart beilleszteni.  
* A `Rectangle` határozza meg a vizuális elhelyezést. Állítsa be az X/Y koordinátákat vagy a szélességet/magasságot, hogy illeszkedjen a layoutjához.

## 3. lépés: A dokumentum mentése

A gomb beállítása után írja a dokumentumot a lemezre. Bármely, az Aspose.Words által támogatott formátumot választhatja (`.docx`, `.pdf`, `.odt`, …). Ebben a tutorialban Word dokumentumként mentünk.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Amikor megnyitja a `CommandButton.docx`-et a Microsoft Wordben, egy **Click Me** feliratú kattintható gombot lát. A gomb megnyomása a Wordben az alapértelmezett „Makró futtatása” párbeszédablakot indítja, mivel a gomb egy OLE űrlapvezérlő; később makrót vagy VBA kódot is csatolhat, ha szükséges.

## 4. lépés: Az eredmény ellenőrzése (várt kimenet)

Nyissa meg a generált fájlt:

1. A gomb a megadott koordinátákon jelenik meg (kb. 1,4 hüvelyk a bal és a felső oldalról).  
2. A felirat **Click Me**.  
3. A név tulajdonság (`cmdSubmit`) látható a Word **Fejlesztő → Tulajdonságok** panelen, ami hasznos, ha VBA-ból kell hivatkozni a vezérlőre.

![OLE parancsgomb beillesztésének példája Word dokumentumban](insert-ole-button.png)

*Kép alternatív szöveg*: **OLE parancsgomb beillesztésének példája Word dokumentumban** (tartalmazza a fő kulcsszót a hozzáférhetőség és SEO érdekében).

## Szélsőséges esetek és gyakori kérdések

### 1. Mi van, ha a gomb nem a várt helyen jelenik meg?

* A Word pontokat (points) használ, nem pixeleket. A képernyő pixeljeit pontokra kell konvertálni (`points = pixels * 72 / DPI`).  
* Győződjön meg arról, hogy a téglalap nem metszi az oldal margóit; ellenkező esetben a Word eltolhatja a vezérlőt.

### 2. Beszúrhatom a gombot egy meglévő dokumentumba?

Igen. Töltse be a dokumentumot a `new Document("Existing.docx")` segítségével, és használja ugyanazt a `DocumentBuilder` munkafolyamatot. Ne felejtse el a builder kurzorát áthelyezni (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, stb.) az `InsertForms2OleControl` hívása előtt.

### 3. Hogyan csatolhatok makrót a gombhoz?

Aspose.Words nem hoz létre VBA kódot, de a dokumentum generálása után beágyazhat egy makrót:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Működik ez .NET Core-on Linuxon?

Az OLE vezérlő egy Windows‑specifikus funkció, mivel a COM-ra támaszkodik. Linuxon a gomb be lesz szúrva, de statikus képként jelenik meg interaktív viselkedés nélkül. Keresztplatformos interaktív űrlapokhoz fontolja meg a tartalomvezérlők (`StructuredDocumentTag`) használatát.

### 5. Mi van, ha más méretre vagy több gombra van szükségem?

Hozzon létre további `Rectangle` objektumokat egyedi koordinátákkal, és ismételje meg az `InsertForms2OleControl` hívást. Minden gombnak saját `Caption` és `Name` értéke lehet.

## Teljes működő példa

Az alábbiakban a teljes program található, amelyet beilleszthet egy konzolalkalmazásba. Tartalmazza az összes szükséges `using` direktívát, a hibakezelést és a megjegyzéseket.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Futtassa a programot, nyissa meg a generált `CommandButton.docx`-et, és láthatja a **Click Me** gombot, amely készen áll a további testreszabásra.

## Következtetés

Most már tudja, hogyan **OLE parancsgombot** szúrjon be egy Word dokumentumba C# és Aspose.Words segítségével. A tutorial a következőket fedte le:

* Az Aspose.Words csomag telepítése  
* `DocumentBuilder.InsertForms2OleControl` használata `OleControlType.CommandButton`-nal  
* A gomb tulajdonságainak beállítása (`Caption`, `Name`)  
* A kimenet mentése és ellenőrzése  

Innen tovább felfedezheti a kapcsolódó témákat, például a **Aspose.Words OLE control**-t jelölőnégyzetekhez, kombinált listákhoz vagy teljes Excel munkafüzetek beágyazásához. Kísérletezhet a **Word OLE parancsgomb** automatizálásával nagyobb sablonokban, vagy lecserélheti az OLE vezérlőket modern **tartalomvezérlőkre** a jobb keresztplatformos támogatás érdekében.

Nyugodtan módosítsa a rectangle értékeket, adjon hozzá több gombot, vagy csatoljon VBA makrókat, hogy megfeleljen alkalmazása igényeinek. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [OLE objektum beszúrása Word dokumentumba](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [OLE objektum beszúrása Word dokumentumba ikonként](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [OLE objektum beszúrása Word-be OLE csomaggal](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
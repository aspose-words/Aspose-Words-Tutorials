---
category: general
date: 2026-09-11
description: Tartalomvezérlő hozzáadása Word-dokumentumba az Aspose.Words használatával.
  Kövesse ezt a lépésről‑lépésre útmutatót, hogy programozottan beszúrjon egy egyszerű
  szöveges Strukturált Dokumentum Címkét (SDT).
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: hu
lastmod: 2026-09-11
og_description: Tartalomvezérlő hozzáadása Word-dokumentumhoz az Aspose.Words segítségével.
  Ez az útmutató megmutatja, hogyan szúrhat be programozottan egy egyszerű szöveges
  struktúrált dokumentumcímkét (SDT) és testreszabhatja azt.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Tartalomvezérlő hozzáadása Word-dokumentumba – teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: Tartalomvezérlő hozzáadása Word-dokumentumhoz az Aspose.Words segítségével
url: /hu/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tartalomvezérlő hozzáadása Word dokumentumban az Aspose.Words segítségével

Ha programozott módon **tartalomvezérlő hozzáadása Word dokumentumban**-ot kell hozzáadnia egy Word dokumentumhoz, ez a bemutató pontosan megmutatja, hogyan teheti ezt meg az Aspose.Words for .NET segítségével. Akár dokumentum‑generálási szolgáltatást épít, akár űrlapkészítést automatizál, megtanulja, hogyan szúrjon be egy egyszerű szöveges Structured Document Tag (SDT) elemet, és adjon neki egy jelentős címet.

Ebben az útmutatóban egy teljes, futtatható példát láthat, amely lefedi az összes szükséges importálást, elmagyarázza, miért fontos minden API hívás, és bemutatja, hogyan ellenőrizze az eredményt. Külső hivatkozásokra nincs szükség – egyszerűen másolja a kódot, futtassa, és nyissa meg a generált *.docx* fájlt.

## Előfeltételek

* .NET 6.0 SDK vagy újabb telepítve  
* Visual Studio 2022 (vagy bármely C# IDE)  
* Aspose.Words for .NET 23.5 vagy újabb – ingyenes próbaverziót a NuGet csomagból szerezhet  

Ezek az elemek alkotják a minimális környezetet az Aspose.Words segítségével történő **word automation**-hez.

## 1. lépés: A projekt beállítása és névterek importálása

Hozzon létre egy új konzolos projektet, és adja hozzá az Aspose.Words csomagot:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Most nyissa meg a `Program.cs` fájlt, és adja hozzá a szükséges `using` direktívákat:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

Ezek a névterek hozzáférést biztosítanak a `DocumentBuilder`, `StructuredDocumentTag` és más alapvető típusokhoz, amelyek szükségesek a **tartalomvezérlő hozzáadása Word dokumentumban**-hoz.

## 2. lépés: Új dokumentum és DocumentBuilder létrehozása

`DocumentBuilder` az elsődleges belépési pont a Word fájlok építéséhez. Egy kurzort tart, amely nyomon követi, hová kerül a következő elem beszúrásra.

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Miért fontos*: A `Document` objektum a teljes Word fájlt képviseli, míg a `DocumentBuilder` egyszerűsíti a bekezdések, táblázatok és **content controls** (például Structured Document Tag-ek) beszúrását.

## 3. lépés: Egyszerű szöveges Structured Document Tag (SDT) beszúrása

A megoldásunk központja az `insertStructuredDocumentTag` metódus. Létrehoz egy **content control**-t, amely egyszerű szöveget, dátumokat, legördülő listákat stb. tartalmazhat. Itt a `SdtType.PLAIN_TEXT` enum értéket használjuk.

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*Miért fontos*: A `true` beállítása miatt a vezérlő világosszürke helyőrzőként jelenik meg, ami jelzi a felhasználóknak, hogy töltsék ki a mezőt.

## 4. lépés: Adjunk a SDT-nek címet a későbbi azonosításhoz

A cím (vagy címke) lehetővé teszi, hogy később megtalálja a vezérlőt, például amikor programozott módon kell cserélni a tartalmát.

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

A cím nem jelenik meg a dokumentum felhasználói felületén, de az alapul szolgáló XML-ben tárolódik, és lekérdezhető az Aspose.Words API-n keresztül.

## 5. lépés: Helyőrző szöveg hozzáadása az SDT-be

A vezérlő felhasználóbarátabbá tétele érdekében szúrjon be egy alapértelmezett run-t, amely megmondja a felhasználónak, mit kell beírni.

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*Miért fontos*: A `Run` objektum egy szövegrészt képvisel. Ha hozzáfűzi az SDT-hez, látható tippet hoz létre, amely a felhasználó elkezd gépelni, eltűnik.

## 6. lépés: Dokumentum mentése

Végül írja a dokumentumot a lemezre, hogy megnyithassa a Microsoft Wordben.

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

Amikor megnyitja a `ContentControlExample.docx` fájlt, egy szürke árnyalatú tartalomvezérlőt fog látni **CustomerName** címmel és a *Enter name here* helyőrző szöveggel.

## Teljes működő példa

Az alábbiakban a teljes program látható, amelyet beilleszthet a `Program.cs` fájlba. Tartalmazza az összes lépést, megjegyzést és a szükséges hibakezelést.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Várható kimenet

A program futtatása a következőt írja ki:

```
Document saved to ContentControlExample.docx
```

A generált fájl Wordben való megnyitása egyetlen tartalomvezérlőt mutat a szürke helyőrzővel **Enter name here**. A vezérlő szerkeszthető, törölhető, vagy később programozottan elérhető a *CustomerName* címke segítségével.

## Gyakori változatok és szélsőséges esetek

| Scenario | How to adapt the code |
|----------|----------------------|
| **Több tartalomvezérlő** | Hívja többször a `InsertStructuredDocumentTag`-et, minden alkalommal egy egyedi `Title` értéket adva. |
| **Rich‑text tartalomvezérlő** | `SdtType.RichText` használata a `PlainText` helyett. |
| **Dátumválasztó vezérlő** | `SdtType.Date` használata, és opcionálisan a `sdt.DateDisplayFormat` beállítása. |
| **A vezérlő zárolása** | `sdt.LockContentControl = true` beállítása a felhasználók eltávolításának megakadályozásához. |
| **Vezérlő későbbi megtalálása** | `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` használata, majd szűrés `Title` alapján. |

Ezek a változatok szemléltetik az **Aspose.Words** rugalmasságát, amikor **tartalomvezérlő hozzáadása Word dokumentumban**-ra van szükség különböző űrlapkitöltési forgatókönyvekhez.

## Profi tippek

* **Performance** – Ha sok dokumentumot generál egy ciklusban, használja újra ugyanazt a `DocumentBuilder` példányt, és minden iterációhoz hívja a `doc.Clone()`-t, hogy elkerülje az objektumok többszöri létrehozását.  
* **Styling** – Alkalmazhat `ParagraphFormat` vagy `Font` beállítást a helyőrző `Run`-ra, hogy illeszkedjen a dokumentum vizuális témájához.  
* **Validation** – A vezérlő beszúrása után ellenőrizheti a `sdt.IsShowingPlaceholderText` értékét, hogy megerősítse, a helyőrző helyesen jelenik meg.  

## Összegzés

Most már tudja, hogyan **tartalomvezérlő hozzáadása Word dokumentumban** az Aspose.Words segítségével, a `DocumentBuilder` létrehozásától a egyszerű szöveges `StructuredDocumentTag` beszúrásáig, cím hozzárendeléséig és helyőrző szöveg hozzáadásáig. A teljes példa kiterjeszthető más SDT típusokra, több vezérlőre, valamint fejlett zárolási vagy stílusbeállítási lehetőségekre.

Ready to go further? Explore these related topics:

* **Working with tables inside content controls** – használja a `DocumentBuilder.InsertTable`-t az SDT után.  
* **Extracting data from filled controls** – szerezze meg a `Sdt` csomópontot cím alapján, és olvassa el a `Text` tulajdonságát.  
* **Using OpenXML SDK** – alternatív megközelítés, ha egy ingyenes, Microsoft‑támogatott könyvtárat részesít előnyben.

Kísérletezzen a kóddal, igazítsa saját űrlap‑generálási munkafolyamatához, és élvezze a programozott Word automatizálás erejét.

## Mit érdemes legközelebb megtanulni?

A következő bemutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Tartalom hozzáadása Document Builder-rel az Aspose.Words for .NET-ben](/words/english/net/add-content-using-document-builder/)
- [Beágyazott kép beszúrása Word dokumentumba az Aspose.Words használatával](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Word dokumentum létrehozása táblázattal az Aspose.Words segítségével](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-08-14
description: Hogyan adjon hozzá gyorsan SDT-t az Aspose.Words segítségével. Tanulja
  meg, hogyan hozzon létre Word helyőrzőt, és hogyan szúrjon be egyszerű szövegvezérlőt
  egy .docx fájlba.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: hu
lastmod: 2026-08-14
og_description: Hogyan adhatunk hozzá SDT-t C#-ban az Aspose.Words használatával.
  Kövesse ezt az útmutatót, hogy szóhelyőrzőt hozzon létre, és egyszerű szövegvezérlőt
  szúrjon be dinamikus dokumentumokhoz.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Hogyan adhatunk hozzá SDT‑t C#‑ban – lépésről‑lépésre Word helyőrző útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Hogyan adjunk hozzá SDT-t C#‑ban – teljes útmutató a Word helyőrzőkhöz
url: /hu/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjon hozzá SDT-t C#-ban – teljes útmutató a Word helyőrzőkhöz

Ha **how to add sdt**-t szeretne egy Word fájlba, ez a tutorial megmutatja a pontos lépéseket az Aspose.Words for .NET használatával. A útmutató végére képes lesz **create word placeholder** címkéket létrehozni, amelyek lehetővé teszik a végfelhasználók számára, hogy közvetlenül a dokumentumba gépeljenek, és megérti, hogyan kell **insert plain text control**-t megbízhatóan beilleszteni.

A Structured Document Tag-ek (SDT-k) használata megszünteti a manuális űrlapmezők szükségességét, és tiszta, programozott módot biztosít dinamikus szerződések, jelentések vagy levelek létrehozásához. Az alábbi példa mindent lefed a projekt beállításától a végső .docx fájl mentéséig, így a kódot egyszerűen másolás‑beillesztéssel beillesztheti a saját megoldásába anélkül, hogy bármilyen függőséget kihagyna.

## Előkövetelmények

- .NET 6.0 vagy újabb (a kód .NET Framework 4.6+‑vel is működik)
- Visual Studio 2022 vagy bármelyik kedvenc C# IDE
- Aspose.Words for .NET licenc (egy ingyenes ideiglenes licenc teszteléshez is működik)
- Alapvető ismeretek a C# szintaxisról és az SDT-k koncepciójáról

> **Pro tipp:** Ha a generált dokumentumokat terjeszteni szeretné, ágyazzon be egy licencfájlt, hogy elkerülje a kiértékelési vízjelet.

## 1. lépés: A projekt beállítása és az Aspose.Words importálása

Hozzon létre egy új konzolos alkalmazást, és adja hozzá az Aspose.Words NuGet csomagot:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Ezek a `using` direktívák hozzáférést biztosítanak a `Document`, `DocumentBuilder` és `StructuredDocumentTag` osztályokhoz, amelyek a **insert plain text control** műveletekhez szükségesek.

## 2. lépés: A dokumentum és a builder inicializálása

Az első kódrészlet egy üres Word dokumentumot és egy `DocumentBuilder`-t hoz létre, amely lehetővé teszi, hogy tartalmat írjon bele.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` úgy működik, mint egy kurzor; minden későbbi hívás a jelenlegi pozícióba ad hozzá tartalmat. A dokumentum inicializálása minden **how to add sdt** szcenárió alapja, mivel az SDT-nek egy élő `Document` példányhoz kell tartoznia.

## 3. lépés: Plain‑text Structured Document Tag (SDT) beszúrása

Most **insert plain text control**-t szúrunk be, amely helyőrzőként működik, ahol a felhasználó nevet, dátumot vagy bármilyen egyedi értéket beírhat.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` azt mondja az Aspose.Words-nak, hogy egyszerű szövegmezőt hozzon létre.
- `SdtAppearanceTags.Default` a címkének a szabványos Word vizuális stílust adja (árnyékolt doboz, amikor a dokumentumot Wordben nyitják meg).

## 4. lépés: Az SDT konfigurálása címkével és helyőrző szöveggel

Egy jól elnevezett SDT önmagában érthetővé teszi a dokumentumot a végfelhasználók számára. Itt **create word placeholder** metaadatot hozunk létre, és beállítjuk a mezőben megjelenő tippet.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` a belső azonosító, amelyet később a programozott értékek kinyerésére vagy frissítésére használhat.
- `PlaceholderName` a Wordben megjelenő szürkés tipp, amely tájékoztatja a felhasználót, mit kell beírni.

## 5. lépés: Környező tartalom hozzáadása

Egy dokumentum ritkán csak egyetlen SDT‑ből áll. Általában szükség van normál bekezdésekre a helyőrző előtt és után. Használja a builder `WriteLine` metódusát statikus szöveg hozzáadásához.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

Az `InsertNode` hívás pontosan oda helyezi a korábban létrehozott SDT‑t, ahol szükség van rá, megőrizve a környező szövegfolyamot.

## 6. lépés: A dokumentum mentése .docx fájlba

Végül mentse a dokumentumot a lemezre. Az útvonal lehet abszolút vagy a projekt mappához relatív.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

`SDT.docx` megnyitása a Microsoft Wordben egy szürke helyőrzőt mutat, amely a **Enter name here** szöveget tartalmazza. A felhasználók rákattinthatnak a mezőre, beírhatnak egy értéket, és a dokumentum megőrzi azt a következő mentéskor.

## Teljes, futtatható példa

Az összes részlet egyesítése egy önálló programot eredményez, amelyet azonnal futtathat:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Várható kimenet** a program futtatásakor:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

A generált `SDT.docx` megnyitása a következőt mutatja:

```
Dear [Enter name here],
After the SDT
```

A szögletes zárójelek közötti szöveg a **insert plain text control** helyőrző, amelyet a felhasználók cserélhetnek.

## Gyakori variációk és szélhelyzetek

| Szituáció | Hogyan kell módosítani a kódot |
|-----------|-------------------------------|
| **Több helyőrző** | Call `InsertStructuredDocumentTag` repeatedly and give each tag a unique `Title`. |
| **Rich‑text SDT** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **A helyőrző zárolása** | Set `plainTextTag.LockContentControl = true;` to prevent users from deleting the field. |
| **Előre kitöltés értékkel** | Assign `plainTextTag.Text = "John Doe";` before saving. |
| **Feltételes megjelenés** | Use `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` for a tick‑box control. |

Ezek a variációk lehetővé teszik, hogy **create word placeholder** struktúrákat hozzon létre, amelyek szinte bármilyen űrlapszerű szituációnak megfelelnek.

## Hibaelhárítási tippek

- **Placeholder not visible** – Győződjön meg arról, hogy a fájlt a Microsoft Wordben (vagy egy kompatibilis megjelenítőben) nyitja meg. Néhány könnyűsúlyú szerkesztő elrejti az SDT‑ket.
- **License warning** – Ha kiértékelési vízjelet lát, ellenőrizze, hogy a licencfájl megfelelően be van-e töltve (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – SDT beszúrása után a builder kurzora a *tag* után marad. Ha szöveget kell hozzáadni a *tag* belsejébe, használja a `builder.MoveTo(plainTextTag);` parancsot írás előtt.

## Következtetés

Most már tudja, hogyan kell **how to add sdt**-t egy Word dokumentumba az Aspose.Words for .NET használatával, hogyan kell **create word placeholder** címkéket létrehozni, és hogyan kell **insert plain text control**-t beilleszteni, amelyet a felhasználók közvetlenül a Wordben szerkeszthetnek. A teljes példa bemutatja az inicializálást, a címke beszúrását, a konfigurációt, a környező tartalmat és a mentést – mindezt egyetlen, futtatható programban.

Ezután fedezze fel a kapcsolódó témákat, például **insert rich text control**, **populate SDTs from a database**, vagy **convert the final document to PDF**. Mindegyik ugyanazokra az alapokra épül, amelyeket itt bemutattunk, így magabiztosan bővítheti automatizálási folyamatát.

Boldog kódolást, és nyugodtan kísérletezzen különböző SDT típusokkal, hogy megfeleljenek dokumentumautomatizálási igényeinek!

## Mit érdemes legközelebb megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Hogyan hozzunk létre űrlapmezőket és adjunk hozzá tartalmat a DocumentBuilder használatával az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hogyan hozzunk létre szerkeszthető tartományokat csak olvasható dokumentumokban az Aspose.Words for Java használatával](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Könyvjelzők hozzáadása Word-hez az Aspose.Words for Java segítségével – Beszúrás, frissítés, törlés](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
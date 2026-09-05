---
category: general
date: 2026-09-05
description: Ismerje meg, hogyan hozhat létre csoportos alakzatot docx-ben, szúrjon
  be ActiveX parancsgombot, és töltsön be Markdownot egy Word-dokumentumba egy teljes
  C# példával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: hu
lastmod: 2026-09-05
og_description: Hozzon létre csoport alakzatot docx-ben, szúrjon be ActiveX parancsgombot,
  és töltse be a Markdown-et egy Word dokumentumba C#-al. Kövesse ezt a lépésről‑lépésre
  útmutatót.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Csoportos alakzat létrehozása docx-ben és ActiveX vezérlők beágyazása –
  C# útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Hogyan hozhatunk létre csoportos alakzatot docx-ben, és adhatunk interaktív
  vezérlőket C#‑ban.
url: /hu/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre csoportos alakzatú docx fájlt és adjunk interaktív vezérlőket C#-ban

Ha programozott módon kell **create group shape docx** fájlokat létrehozni, ez az útmutató pontosan megmutatja, hogyan. Emellett láthatod, hogyan **insert ActiveX command button** vezérlőket és **load Markdown into a Word document**-ot szúrj be anélkül, hogy elveszítenéd az aláhúzott formázást. A tutorial végére egy teljesen funkcionális `.docx`-et kapsz, amely vektorgrafikát, interaktív UI elemeket és markdown‑alapú tartalmat kombinál.

Ez a tutorial feltételezi, hogy van egy alap C# fejlesztői környezeted és az Aspose.Words for .NET könyvtár telepítve van. Nem szükséges külső eszköz – minden egy szabványos .NET konzol vagy asztali alkalmazáson belül fut.

## Előfeltételek

- .NET 6.0 SDK vagy újabb (a kód .NET Framework 4.7+‑vel is működik)
- Aspose.Words for .NET (NuGet csomag `Aspose.Words`)
- Érvényes X.509 tanúsítvány (`.pfx`), ha a aláírási lépést tesztelni szeretnéd
- Egy képfájl (pl. `logo.png`) és egy markdown fájl (`sample.md`) egy ismert mappában

> **Pro tip:** Tartsd az összes bemeneti fájlt egyetlen *resources* mappában a relatív útvonalak egyszerűsítése érdekében.

## 1. lépés: A projekt beállítása és a névterek importálása

Hozz létre egy új konzolprojektet és add hozzá a szükséges `using` direktívákat. Ez a blokk azt is bemutatja, hogyan hivatkozz az Aspose.Words osztályokra, amelyeket később használni fogsz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

A `using` utasítások közvetlen hozzáférést biztosítanak a `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` és a tutorial során használt egyéb típusokhoz.

## 2. lépés: **Create group shape docx** – csoportos alakzat hozzáadása gyermekelemekkel

Egy *group shape* lehetővé teszi, hogy több rajzobjektumot egy egységként kezelj. Ez hasznos a kapcsolódó grafikák együttes mozgatásához vagy átméretezéséhez.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Miért csoportos alakzat?**  
A csoportosítás biztosítja, hogy a téglalap és az ellipszis egy vonalban maradjon, amikor a felhasználó áthúzza őket Wordben. Emellett egyszerűsíti a későbbi műveleteket, például közös keret alkalmazását vagy a teljes grafika programozott mozgatását.

## 3. lépés: Egyszerű szöveges tartalomvezérlő beszúrása (helyőrző a felhasználói bemenethez)

A tartalomvezérlők strukturált területet biztosítanak a végfelhasználók számára a szöveg beírásához. A helyőrző szöveg eltűnik, amint a felhasználó elkezd gépelni.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

A `PlaceholderName` tulajdonság az, amit a Word világosszürke jelzésként mutat. A felhasználók saját szövegükkel helyettesíthetik, miközben az alatta lévő XML jól formázott marad.

## 4. lépés: **Insert ActiveX command button** – interaktív UI hozzáadása a dokumentumhoz

Az ActiveX vezérlők még mindig támogatottak a modern Word fájlokban, és makrókat vagy külső automatizálást indíthatnak. Az alábbiakban egy *command button*-t adunk hozzá és beállítjuk a feliratát.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Mikor használjunk ActiveX gombot?**  
Ha a dokumentumot egy vállalati környezetben terjeszted, amely VBA makrókra támaszkodik, egy ActiveX gomb elindíthat egy makrót vagy egy külső alkalmazást. Tiszta HTML‑alapú interaktivitáshoz fontold meg a *content controls* használatát *Office.js*-szel.

## 5. lépés: Rejtett kép beszúrása (pl. logó) márkaépítéshez vagy későbbi szkript hozzáféréshez

A rejtett alakzatok nem jelennek meg a nyomtatott dokumentumban, de megmaradnak az XML-ben, így később programozottan lekérhetők.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## 6. lépés: **Load markdown into a Word document** aláhúzott formázás megőrzése közben

Az Aspose.Words közvetlenül importálhat Markdown‑ot. Az `ImportUnderlineFormatting` engedélyezése biztosítja, hogy a markdown aláhúzások (`<u>` vagy `__text__`) Word aláhúzott stílusokká alakuljanak, nem egyszerű szöveggé.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Szélsőséges eset:** Ha a markdown fájl táblázatokat tartalmaz, azok automatikusan Word‑táblázatokká konvertálódnak. Ha egyedi táblázat‑stílusra van szükséged, alkalmazz egy `DocumentBuilder`‑t a beszúrás után.

## 7. lépés: A dokumentum aláírása XAdES‑EPES-szel (opcionális biztonsági lépés)

A digitális aláírások garantálják a dokumentum integritását. Az alábbi kód az **create group shape docx** fájlt egy XAdES‑EPES profil segítségével írja alá.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Biztonsági megjegyzés:** Tartsd a tanúsítvány jelszavát a forráskódban kívül. Használj környezeti változókat vagy biztonságos tárolót éles környezetben.

## Teljes futtatható példa

Az összes lépés egyesítése egy önálló programot eredményez. Mentsd a fájlt `Program.cs` néven és futtasd a parancssorból.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

A program futtatása létrehozza a `CompleteGroupShape.docx` fájlt, amely:

- Egy csoportosított téglalap + ellipszis (a **create group shape docx** magja)
- Egy egyszerű szöveges tartalomvezérlő helyőrző szöveggel
- Egy **insert ActiveX command button** „Click Me” felirattal
- Egy rejtett logó kép
- Markdown tartalom megőrzött aláhúzásokkal
- Egy XAdES‑EPES digitális aláírás (ha tanúsítvány meg van adva)

## Gyakori kérdések és hibaelhárítás

| Kérdés | Válasz |
|---|---|
| **Működni fog-e az ActiveX gomb macOS Word‑ben?** | A macOS Word nem támogatja az ActiveX vezérlőket. A gomb statikus képként jelenik meg. Használj tartalomvezérlőket Office.js‑szel a platformközi interaktivitáshoz. |
| **Mi van, ha a markdown fájl egyedi CSS‑t tartalmaz?** | Az Aspose.Words figyelmen kívül hagyja a CSS‑t; csak a szabványos markdown szintaxis kerül feldolgozásra. A CSS‑stílusú elemeket manuálisan kell Word‑stílusokká konvertálni az importálás után. |
| **Később hozzáadhatok-e további alakzatokat ugyanahhoz a csoporthoz?** | Igen. Szerezd meg a `GroupShape`‑t a neve vagy indexe alapján, majd hívd meg az `AppendChild(newShape)` metódust. Ne felejtsd el újra menteni a dokumentumot a módosítások után. |
| **Hogyan változtathatom meg az aláírás algoritmusát?** | Állítsd be a `signature.SignatureAlgorithm`‑t a `Sign` hívása előtt. Alapértelmezés szerint a SHA‑256 van beállítva, ami a legtöbb megfelelőségi követelménynek megfelel. |
| **Látható-e a rejtett kép a Word felhasználói felületén?** | Nem, de megjeleníthető a *Show hidden text* (Rejtett szöveg megjelenítése) opció bekapcsolásával a Word beállításaiban. Ez hasznos metaadatok tárolására anélkül, hogy a layoutot zsúfolná. |

## Következő lépések

Most, hogy **create group shape docx**, **insert ActiveX command button**, és **load markdown into a Word document** tudsz, érdemes továbbfejleszteni:

- **VBA makrók beágyazása**, amelyek reagálnak az ActiveX gomb kattintására.
- **Egyedi stílusok alkalmazása** a markdown‑generált bekezdésekre.
- **PDF‑k generálása** ugyanabból a dokumentumból a `doc.Save("output.pdf", SaveFormat.Pdf)` használatával.
- **Kötegelt feldolgozás automatizálása** több markdown fájl egyetlen összeállított jelentéssé alakításához.

Ezek a kiegészítések lehetővé teszik, hogy teljesen automatizált dokumentum‑csővezetékeket építs, amelyek gazdag grafikát, interaktív vezérlőket és markdown‑alapú szerzői munkát kombinálnak – mindezt C#‑ból.

*Boldog kódolást! Ha hasznosnak találtad ezt az útmutatót


## Mit érdemes legközelebb megtanulni?


Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek az API további funkcióinak elsajátításában és alternatív megvalósítási megközelítések felfedezésében a saját projektjeidben.

- [Csoport alakzat létrehozása Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Téglalap alakzat létrehozása Word-ben C#-al – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Markdown létrehozása Word-ből – Teljes C# útmutató](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
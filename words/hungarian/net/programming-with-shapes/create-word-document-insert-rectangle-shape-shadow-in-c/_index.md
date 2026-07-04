---
category: general
date: 2026-05-26
description: Word dokumentum létrehozása C#-ban az Aspose.Words használatával, téglalap
  alakzat beszúrása, kitöltőszín beállítása és árnyékhatás hozzáadása – lépésről lépésre
  útmutató.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: hu
og_description: Word dokumentum létrehozása C#-ban az Aspose.Words segítségével. Tanulja
  meg, hogyan szúrjon be egy téglalap alakzatot, állítsa be a kitöltőszínét, és adjon
  hozzá árnyékhatást.
og_title: Word-dokumentum létrehozása – Téglalap alakzat és árnyék beszúrása C#‑ban
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Word-dokumentum létrehozása – Téglalap alakzat és árnyék beszúrása C#‑ban
url: /hu/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása – Téglalap alakzat és árnyék beszúrása C#‑ban

Gondolkodtál már azon, hogyan **hozhatsz létre Word dokumentumot** programozottan anélkül, hogy megnyitnád a Microsoft Word‑et? Nem vagy egyedül. Sok automatizálási szituációban – gondolj csak a számlákra, szerződésekre vagy tömeges jelentéskészítésre – megbízható módra van szükség, amellyel .docx fájlt generálhatsz, belehelyezheted az alakzatot, színezheted, sőt akár árnyékot is adhatunk neki a profi megjelenésért.

Ebben az útmutatóban pontosan ezt mutatjuk be: az Aspose.Words for .NET használatával **Word dokumentum létrehozása**, **téglalap alakzat beszúrása**, kitöltés alkalmazása, és **árnyék hozzáadása**. A végére egy menthető fájlt kapsz, amelyet bármilyen további munkafolyamatba beilleszthetsz.  

Röviden áttekintjük, **hogyan szúrjunk be alakzatot** rugalmas módon, és miért fontos a **kitöltés beállítása** a vizuális konzisztencia érdekében. Nincs felesleges szöveg, csak a másolható‑beilleszthető kód.

## Előfeltételek

Mielőtt belevágnánk, győződj meg róla, hogy a következők telepítve vannak:

- .NET 6+ (vagy .NET Framework 4.7+)  
- Érvényes Aspose.Words for .NET licenc (vagy ideiglenes értékelő kulcs)  
- Visual Studio, Rider vagy bármelyik kedvenc C# IDE  
- Alapvető C# szintaxis ismeret – semmi különleges nem kell

Rendben? Akkor kezdjünk is bele.

## 1. lépés – Word dokumentum létrehozása

Az első dolog, amire szükséged van, egy üres dokumentumobjektum. Ez lesz a vászon, ahol minden más megjelenik.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

A `Document` a .docx fájlt reprezentálja a memóriában, míg a `DocumentBuilder` kényelmes API‑t biztosít szöveg, táblázat és alakzat beszúrásához. **Word dokumentum létrehozása** így azonnali – nincs UI, nincs COM interop, csak tiszta .NET.

## 2. lépés – Téglalap alakzat beszúrása

Most, hogy van egy dokumentumunk, **szúrjunk be egy téglalap alakzatot**. Az `InsertShape` metódus egy `ShapeType` enum‑ot, szélességet és magasságot (pontban) vár. Egy 150 × 80 pont méretű téglalapot használunk, ami nagyjából 2 × 1 hüvelyknek felel meg.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

A háttérben az Aspose egy `Shape` objektumot hoz létre, hozzáadja az aktuális bekezdéshez, és visszaad egy hivatkozást, amelyet stílusozhatsz. Ez a **hogyan szúrjunk be alakzatot** magja – egyetlen sor kóddal, de hihetetlenül erőteljes.

## 3. lépés – Kitöltés beállítása

Egy alakzat kitöltés nélkül láthatatlan a fehér oldalon. Adjunk neki egy kellemes világoskék hátteret.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Használhatsz gradienseket, textúrákat vagy akár képet is kitöltésként, de egy egyszínű szín egyszerűvé teszi a példát. Ez mutatja be, **hogyan állítsuk be a kitöltést** bármely létrehozott alakzatra, biztosítva a kívánt vizuális jelzést.

## 4. lépés – Árnyék hozzáadása

Az árnyékok mélységet adnak, és kiemelik az alakzatot. Az Aspose.Words egy `ShadowFormat` objektumot biztosít, ahol beállíthatod a láthatóságot, színt, valamint a elmosódás, távolság és szög finomhangolását.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Miért ezek az értékek? A 45°‑os szög természetes jobb‑felső fényforrást szimulál, a mérsékelt elmosódás finom árnyékot eredményez, a rövid távolság pedig megakadályozza, hogy az alakzat elváljon a szövegtől. Nyugodtan kísérletezz – például a szög 135°‑ra állítása az árnyékot bal‑alsó irányba helyezi.

## 5. lépés – Dokumentum mentése

Minden elkészült, most írjuk a fájlt a lemezre. Válassz bármilyen útvonalat, csak győződj meg róla, hogy a mappa létezik.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Amikor megnyitod a `ShadowShape.docx` fájlt a Microsoft Word‑ben, egy világoskék téglalapot látsz egy lágy szürke árnyékkal – pontosan úgy, ahogy a kódban leírtuk.

## Teljes működő példa

Az összes lépést egyben, egy másolás‑beillesztés‑kész programként:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Várt eredmény

- Megjelenik egy **ShadowShape.docx** nevű fájl a célmappában.  
- A Word‑ben megnyitva egy világoskék téglalap látható az első oldal közepén.  
- A téglalap egy 45°‑os szögű szürke árnyékot vet, amely finom 3‑D hatást kölcsönöz.

## Gyakori kérdések és széljegyek

**Mi van, ha más alakzatra van szükségem?**  
Cseréld le a `ShapeType.Rectangle`‑t bármely más enum‑értékre (`Ellipse`, `Star`, `Arrow` stb.). A többi kód változatlan marad.

**Tudok-e szöveget elhelyezni az alakzatban?**  
Igen – az alakzat létrehozása után hívd meg a `shape.AppendChild(new Paragraph(doc))`‑t, majd szúrj be egy `Run`‑t a szöveggel. Ha szövegcsomagolást szeretnél, állítsd be a `shape.TextBox` tulajdonságait.

**Mi a helyzet a DPI‑val vagy a mértékegységekkel?**  
Az Aspose pontokban dolgozik (1 pt = 1/72 inch). Ha centimétert szeretnél, szorozd meg 28,35‑tel (mivel 1 cm ≈ 28,35 pt).

**Szükség van licencre a működéshez?**  
Az értékelő verzió az első oldalra vízjelet helyez. Egy érvényes licenc eltávolítja azt, és feloldja a teljes API‑t.

## Tippek és buktatók

- **Pro tipp:** Hívd meg a `builder.MoveToDocumentEnd()`‑et alakzat beszúrása előtt, ha a dokumentum végére szeretnéd helyezni.  
- **Vigyázz:** Írásvédett mappába mentés `UnauthorizedAccessException`‑t dob. Biztosíts írási jogosultságot az alkalmazásodnak.  
- **Teljesítmény:** Tömeges generálás (százak dokumentum) esetén használj egyetlen `Document` példányt sablonként, és klónozd `doc.Clone(true)`‑val, hogy elkerüld az ismételt inicializációt.

## Összegzés

Most már tudod, hogyan **hozz létre Word dokumentumot**, **szúrj be téglalap alakzatot**, **állítsd be a kitöltést**, és **adj hozzá árnyékot** az Aspose.Words for .NET segítségével. A fenti kódrészlet önálló megoldás, amely bármely C# projektbe beilleszthető – legyen az konzolalkalmazás, web‑API vagy háttérszolgáltatás.

Innen tovább fejlesztheted:

- Több alakzat hozzáadása változó színekkel.  
- Gradiens vagy képkitöltés használata (`shape.FillColor = …` → `shape.FillPattern`).  
- Alakzatok kombinálása táblázatokkal összetett jelentéselrendezésekhez.

Próbáld ki, módosítsd a paramétereket, és figyeld meg, hogyan válnak automatizált Word fájljaid professzionálisabbá néhány kódsorral. Jó kódolást!

## Kapcsolódó oktatóanyagok

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
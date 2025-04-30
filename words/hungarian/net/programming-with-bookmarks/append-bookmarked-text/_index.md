---
"description": "Tanuld meg, hogyan fűzhetsz hozzá könyvjelzővel ellátott szöveget egy Word-dokumentumhoz az Aspose.Words for .NET használatával ebből a lépésről lépésre szóló útmutatóból. Tökéletes fejlesztők számára."
"linktitle": "Könyvjelzővel ellátott szöveg hozzáfűzése a Word dokumentumban"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Könyvjelzővel ellátott szöveg hozzáfűzése a Word dokumentumban"
"url": "/hu/net/programming-with-bookmarks/append-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Könyvjelzővel ellátott szöveg hozzáfűzése a Word dokumentumban

## Bevezetés

Sziasztok! Próbáltatok már szöveget hozzáfűzni egy Word-dokumentum könyvjelzővel ellátott szakaszából, és bonyolultnak találtátok? Szerencsétek van! Ez az oktatóanyag végigvezet a folyamaton az Aspose.Words for .NET használatával. Egyszerű lépésekre bontjuk, hogy könnyen követhessétek. Vágjunk bele, és fűzzük hozzá a könyvjelzővel ellátott szöveget profi módon!

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy minden megvan, amire szükséged van:

- Aspose.Words .NET-hez: Győződjön meg róla, hogy telepítve van. Ha nem, akkor megteheti [töltsd le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Bármely .NET fejlesztői környezet, például a Visual Studio.
- C# alapismeretek: A C# programozási alapfogalmak ismerete hasznos lesz.
- Word-dokumentum könyvjelzőkkel: Egy Word-dokumentum beállított könyvjelzőkkel, amelyből szöveget fogunk hozzáfűzni.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez biztosítja, hogy minden szükséges eszköz kéznél legyen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Bontsuk le a példát részletes lépésekre.

## 1. lépés: A dokumentum betöltése és a változók inicializálása

Rendben, kezdjük a Word dokumentum betöltésével és a szükséges változók inicializálásával.

```csharp
// Töltse be a forrás- és céldokumentumokat.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicializálja a dokumentumimportálót.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Keresd meg a könyvjelzőt a forrásdokumentumban.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## 2. lépés: A kezdő és a záró bekezdések azonosítása

Most keressük meg a könyvjelző kezdetét és végét jelentő bekezdéseket. Ez kulcsfontosságú, mivel a szöveget ezeken a határokon belül kell kezelnünk.

```csharp
// Ez a bekezdés tartalmazza a könyvjelző elejét.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Ez a bekezdés tartalmazza a könyvjelző végét.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## 3. lépés: Bekezdésszülők ellenőrzése

Biztosítanunk kell, hogy a kezdő és a befejező bekezdések szülője megegyezzen. Ez egy egyszerű forgatókönyv az egyszerűség kedvéért.

```csharp
// Szűkítsük magunkat egy viszonylag egyszerű forgatókönyvre.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## 4. lépés: A leállítandó csomópont azonosítása

Ezután meg kell határoznunk azt a csomópontot, ahol abbahagyjuk a szöveg másolását. Ez lesz a befejező bekezdés utáni csomópont.

```csharp
// Az összes bekezdést át akarjuk másolni a kezdő bekezdéstől a befejező bekezdésig (beleértve azt is).
// tehát a csomópont, amelynél megállunk, egyel a befejező bekezdés után található.
Node endNode = endPara.NextSibling;
```

## 5. lépés: Könyvjelzővel ellátott szöveg hozzáfűzése a céldokumentumhoz

Végül menjünk végig a csomópontokon a kezdő bekezdéstől a záró bekezdés utáni csomópontig, és fűzzük hozzá őket a céldokumentumhoz.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Ez létrehozza az aktuális csomópont másolatát, és importálja (érvényessé teszi) a kontextusban.
    // a céldokumentumban. Az importálás a stílusok és a listaazonosítók helyes beállítását jelenti.
    Node newNode = importer.ImportNode(curNode, true);

    // Fűzze hozzá az importált csomópontot a céldokumentumhoz.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Mentse el a céldokumentumot a hozzáfűzött szöveggel.
dstDoc.Save("appended_document.docx");
```

## Következtetés

És tessék! Sikeresen hozzáfűztél szöveget egy Word-dokumentum könyvjelzővel ellátott szakaszából az Aspose.Words for .NET segítségével. Ez a hatékony eszköz gyerekjátékká teszi a dokumentumok kezelését, és most már van még egy trükk a tarsolyodban. Jó programozást!

## GYIK

### Hozzáfűzhetek szöveget több könyvjelzőből egyszerre?
Igen, megismételheti a folyamatot minden könyvjelzőnél, és ennek megfelelően fűzheti hozzá a szöveget.

### Mi van, ha a kezdő és a befejező bekezdéseknek különböző szülőik vannak?
A jelenlegi példa feltételezi, hogy ugyanaz a szülőjük. Különböző szülők esetén összetettebb kezelésre van szükség.

### Megtarthatom a hozzáfűzött szöveg eredeti formázását?
Abszolút! A `ImportFormatMode.KeepSourceFormatting` biztosítja az eredeti formázás megőrzését.

### Lehetséges szöveget hozzáfűzni egy adott pozícióhoz a céldokumentumban?
Igen, a szöveget bármely pozícióhoz hozzáfűzheti a céldokumentumban a kívánt csomópontra navigálva.

### Mi van, ha egy könyvjelzőből kell szöveget hozzáfűznöm egy új szakaszhoz?
Létrehozhat egy új szakaszt a céldokumentumban, és oda fűzheti hozzá a szöveget.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
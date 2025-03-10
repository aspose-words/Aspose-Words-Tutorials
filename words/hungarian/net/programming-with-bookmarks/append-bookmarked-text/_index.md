---
title: Könyvjelzővel ellátott szöveg hozzáfűzése a Word-dokumentumhoz
linktitle: Könyvjelzővel ellátott szöveg hozzáfűzése a Word-dokumentumhoz
second_title: Aspose.Words Document Processing API
description: Ebből a lépésről lépésre szóló útmutatóból megtudhatja, hogyan fűzhet hozzá könyvjelzővel ellátott szöveget egy Word-dokumentumhoz az Aspose.Words for .NET használatával. Tökéletes fejlesztőknek.
weight: 10
url: /hu/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Könyvjelzővel ellátott szöveg hozzáfűzése a Word-dokumentumhoz

## Bevezetés

Szia! Próbált már szöveget hozzáfűzni egy Word-dokumentum könyvjelzővel ellátott szakaszából, és trükkösnek találta? szerencséd van! Ez az oktatóanyag végigvezeti a folyamaton az Aspose.Words for .NET használatával. Egyszerű lépésekre bontjuk, hogy könnyen követhesse. Merüljünk el, és fűzzük hozzá a könyvjelzővel ellátott szöveget, mint egy profi!

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy rendelkezik-e mindennel, amire szüksége van:

-  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van. Ha nem, akkor megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Bármely .NET fejlesztői környezet, például a Visual Studio.
- Alapvető C# ismerete: Az alapvető C# programozási fogalmak megértése segít.
- Word-dokumentum könyvjelzőkkel: Word-dokumentum könyvjelzőkkel, amelyekből szöveget fűzünk hozzá.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez biztosítja, hogy minden szükséges eszköz kéznél legyen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Bontsuk le a példát részletes lépésekre.

## 1. lépés: Töltse be a dokumentumot és inicializálja a változókat

Rendben, kezdjük a Word dokumentumunk betöltésével és a szükséges változók inicializálásával.

```csharp
// Töltse be a forrás- és céldokumentumot.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicializálja a dokumentumimportőrt.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Keresse meg a könyvjelzőt a forrásdokumentumban.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## 2. lépés: Határozza meg a kezdő és záró bekezdéseket

Most keressük meg azokat a bekezdéseket, ahol a könyvjelző kezdődik és végződik. Ez döntő fontosságú, mivel a szöveget ezeken a határokon belül kell kezelnünk.

```csharp
// Ez az a bekezdés, amely a könyvjelző elejét tartalmazza.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Ez az a bekezdés, amely a könyvjelző végét tartalmazza.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## 3. lépés: A bekezdésszülők érvényesítése

Biztosítanunk kell, hogy a kezdő és a záró bekezdésnek ugyanaz a szülője legyen. Ez egy egyszerű forgatókönyv, hogy a dolgok egyértelműek legyenek.

```csharp
// Korlátozzuk magunkat egy ésszerűen egyszerű forgatókönyvre.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## 4. lépés: Határozza meg a leállítandó csomópontot

Ezután meg kell határoznunk azt a csomópontot, ahol leállítjuk a szöveg másolását. Ez lesz a csomópont közvetlenül a záró bekezdés után.

```csharp
// Minden bekezdést át akarunk másolni a kezdő bekezdéstől a záró bekezdésig (beleértve),
// ezért a csomópont, amelynél megállunk, egy a bekezdés végének után van.
Node endNode = endPara.NextSibling;
```

## 5. lépés: Könyvjelzővel ellátott szöveg hozzáfűzése a céldokumentumhoz

Végül görgessük át a csomópontokat a kezdő bekezdéstől a záró bekezdés utáni csomópontig, és fűzzük hozzá őket a céldokumentumhoz.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Ez létrehozza az aktuális csomópont másolatát, és importálja (érvényessé teszi) a kontextusba
    // a rendeltetési okmány. Az importálás a stílusok és a listaazonosítók helyes beállítását jelenti.
    Node newNode = importer.ImportNode(curNode, true);

    // Az importált csomópont hozzáfűzése a céldokumentumhoz.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Mentse el a céldokumentumot a hozzáfűzött szöveggel.
dstDoc.Save("appended_document.docx");
```

## Következtetés

És megvan! Sikeresen hozzáfűzte egy Word-dokumentum könyvjelzővel ellátott szakaszának szövegét az Aspose.Words for .NET segítségével. Ezzel a hatékony eszközzel gyerekjáték a dokumentumkezelés, és most még egy trükk vár a kezedre. Boldog kódolást!

## GYIK

### Hozzáfűzhetek szöveget több könyvjelzőből egyszerre?
Igen, megismételheti a folyamatot minden könyvjelzőnél, és ennek megfelelően fűzheti hozzá a szöveget.

### Mi van akkor, ha a kezdő és a záró bekezdésnek különböző szülője van?
jelenlegi példa azt feltételezi, hogy ugyanaz a szülő. A különböző szülők esetében összetettebb kezelésre van szükség.

### Megtarthatom a hozzáfűzött szöveg eredeti formázását?
 Teljesen! A`ImportFormatMode.KeepSourceFormatting` biztosítja az eredeti formázás megőrzését.

### Lehetséges-e szöveget hozzáfűzni a céldokumentum egy adott helyéhez?
Igen, a szöveget tetszőleges pozícióhoz hozzáfűzheti, ha a kívánt csomóponthoz navigál a céldokumentumban.

### Mi a teendő, ha egy könyvjelzőből szöveget kell hozzáfűznem egy új szakaszhoz?
Létrehozhat egy új szakaszt a céldokumentumban, és hozzáfűzheti a szöveget.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
title: Tartsa együtt az asztalt
linktitle: Tartsa együtt az asztalt
second_title: Aspose.Words Document Processing API
description: Ebből a lépésenkénti útmutatóból megtudhatja, hogyan akadályozhatja meg, hogy a táblázatok oldalakra törjenek az Aspose.Words for .NET használatával. Gondoskodjon rendezett, professzionális megjelenésű Word-dokumentumokról
weight: 10
url: /hu/net/join-and-append-documents/keep-source-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tartsa együtt az asztalt

## Bevezetés

A táblázatok sok Word-dokumentum elengedhetetlen részét képezik, de néha előfordulhat, hogy olyan helyzetbe kerülhet, hogy a táblázat két oldalra tör. Ez megzavarhatja a dokumentum áramlását és befolyásolhatja annak olvashatóságát. Nem lenne jó, ha az egész táblázatot egy oldalon tartanák? Nos, az Aspose.Words for .NET segítségével egyszerű megoldást kínál erre a problémára! Ebben az oktatóanyagban végigvezetjük, hogyan akadályozhatja meg a táblázatok oldalakra való szétválását, így biztosítva, hogy a dokumentuma ügyes és professzionális megjelenést biztosítson.

## Előfeltételek

Mielőtt belevágnánk az oktatóanyagba, győződjünk meg arról, hogy mindennel rendelkezel, ami a zökkenőmentes követéshez szükséges.

### Aspose.Words for .NET Library

Először is telepítenie kell az Aspose.Words for .NET programot. Ez az a hatékony könyvtár, amely lehetővé teszi a Word-dokumentumok programozott kezelését.

- [Töltse le az Aspose.Words for .NET programot](https://releases.aspose.com/words/net/)

### Fejlesztési környezet

A C# kód futtatásához be kell állítani egy fejlesztői környezetet, például:

- Visual Studio (bármely újabb verzió)
- .NET-keretrendszer 2.0 vagy újabb

### Word dokumentum táblázattal

 Szüksége lesz egy táblázatot tartalmazó Word dokumentumra. Ebben az oktatóanyagban egy mintadokumentummal fogunk dolgozni`"Table spanning two pages.docx"`. Ez a fájl egy táblázatot tartalmaz, amely jelenleg két oldalt ölel fel.

### Ideiglenes engedély (opcionális)

 Míg az Aspose.Words ingyenes próbaverzióval rendelkezik, érdemes lehet a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) hogy kibontakoztassa a könyvtárban rejlő lehetőségeket.

## Csomagok importálása

Mielőtt bármilyen kódot írnánk, importálnunk kell az Aspose.Words for .NET használatához szükséges névtereket. Adja hozzá a következő importálásokat a kódfájl tetejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

 Ezek a névterek hozzáférést biztosítanak olyan osztályokhoz, mint a`Document`, `Table`, `Cell`, és mások, amelyeket ebben az oktatóanyagban fogunk használni.

## 1. lépés: Töltse be a dokumentumot

 Az első dolog, amit tennünk kell, hogy betöltsük a táblázatot tartalmazó Word dokumentumot. Ehhez használjuk a`Document` osztály Aspose-tól.Words. Ez az osztály lehetővé teszi Word-fájlok programozott megnyitását és kezelését.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

 Ebben a kódrészletben megadjuk a dokumentumunk helyét. Cserélje ki`"YOUR DOCUMENTS DIRECTORY"` azzal a könyvtárral, ahol a dokumentumot tárolják.

## 2. lépés: Nyissa meg a táblázatot

A dokumentum betöltése után a következő lépés az egyben tartani kívánt táblázat elérése. Ebben a példában feltételezzük, hogy a tábla a dokumentum első táblája.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

 Ez a kódsor megtalálja a dokumentum első táblázatát. A`GetChild` módszer egy adott típusú csomópontot kér le, amely ebben az esetben az`NodeType.Table` . A`0` azt jelzi, hogy szeretnénk az első táblázatot, és a`true`flag biztosítja, hogy rekurzívan keressünk az összes gyermek csomóponton.

## 3. lépés: Hurok át a táblázat celláin

Most végig kell lépnünk a táblázat minden celláján. Mivel egy táblázat több sort tartalmaz, és minden sor több cellát tartalmaz, minden cellát végig fogunk iterálni, és gondoskodunk arról, hogy ne törjenek oldalakra.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

 Itt,`GetChildNodes` lekéri a táblázat összes celláját, és mindegyiken végigfutunk. A`EnsureMinimum()` A metódus gondoskodik arról, hogy minden cellában legyen legalább egy bekezdés, mivel az üres cella később problémákat okozhat.

## 4. lépés: Állítsa be a KeepWithNext tulajdonságot

 Ahhoz, hogy a táblázat ne törjön oldalakra, be kell állítanunk a`KeepWithNext` tulajdonság a táblázat minden bekezdéséhez. Ez a tulajdonság biztosítja, hogy a bekezdés a következő bekezdéssel maradjon, hatékonyan megakadályozva az oldaltöréseket közöttük.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

 Ez a ciklus minden cellán belül minden bekezdést ellenőriz. A feltétel biztosítja, hogy ne alkalmazzuk a`KeepWithNext`tulajdonság az utolsó sor utolsó bekezdéséig. Ellenkező esetben a tulajdonságnak nem lenne hatása, mivel nincs következő bekezdés.

## 5. lépés: Mentse el a dokumentumot

 Végül alkalmazása után a`KeepWithNext` tulajdonságot, el kell mentenünk a módosított dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Ez a sor új néven menti a frissített dokumentumot, megőrzi az eredeti fájlt. Most megnyithatja a kapott fájlt, és láthatja, hogy a táblázat már nincs két oldalra osztva!

## Következtetés

És megvan! Ha követi ezeket az egyszerű lépéseket, az Aspose.Words for .NET segítségével könnyedén megakadályozhatja, hogy a táblázatok oldalakra törjenek a Word dokumentumokban. Legyen szó jelentésekről, szerződésekről vagy egyéb dokumentumokról, a táblázatok érintetlen megőrzése még kifinomultabb, professzionálisabb megjelenést biztosít.

Az Aspose.Words szépsége a rugalmasságban és a könnyű használatban rejlik, amely lehetővé teszi a Word-dokumentumok programozott kezelését anélkül, hogy a Microsoft Word programot telepítenie kellene a gépére. Most, hogy rájött a táblázatok egyben tartására, fedezze fel a könyvtár egyéb funkcióit, hogy dokumentumfeldolgozási készségeit a következő szintre emelje!

## GYIK

### Miért törik a táblázatom továbbra is oldalakra a kód használata után?

 Ha az asztal még mindig törik, győződjön meg arról, hogy alkalmazta a`KeepWithNext` tulajdonát helyesen. Ellenőrizze még egyszer, hogy az utolsó bekezdés kivételével az összes bekezdés rendelkezik-e ezzel a tulajdonsággal.

### Csak meghatározott sorokat tarthatok együtt?

 Igen, szelektíven alkalmazhatja a`KeepWithNext` tulajdonságot a táblázat adott soraihoz vagy bekezdéseihez, hogy szabályozza, mely részek maradjanak együtt.

### Működik ez a módszer nagy asztaloknál?

Nagyon nagy táblázatok esetén a Word továbbra is feloszthatja azokat oldalakra, ha nincs elég hely ahhoz, hogy a teljes táblázat egy oldalon elférjen. Fontolja meg a táblázat formázásának vagy margóinak módosítását a nagyobb táblázatok elhelyezéséhez.

### Használhatom ezt a módszert más dokumentumformátumokkal?

Igen! Az Aspose.Words for .NET számos formátumot támogat, például DOC, DOCX, PDF és más formátumokat. Ugyanez a módszer minden táblázatot támogató formátumban működik.

### Az Aspose.Words for .NET ingyenes könyvtár?

 Az Aspose.Words for .NET ingyenes próbaverziót kínál, de az összes funkcióhoz való teljes hozzáféréshez licencet kell vásárolnia. Az engedélyezési lehetőségeket a[Aspose vásárlási oldal](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

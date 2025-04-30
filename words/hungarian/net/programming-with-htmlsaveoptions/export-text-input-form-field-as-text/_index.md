---
"description": "Tanuld meg, hogyan exportálhatsz szövegbeviteli űrlapmezőket egyszerű szövegként az Aspose.Words for .NET használatával ebből az átfogó, lépésről lépésre haladó útmutatóból."
"linktitle": "Szövegbeviteli űrlapmező exportálása szövegként"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Szövegbeviteli űrlapmező exportálása szövegként"
"url": "/hu/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Szövegbeviteli űrlapmező exportálása szövegként

## Bevezetés

Szóval, belemerülsz az Aspose.Words for .NET világába? Remek választás! Ha szeretnéd megtanulni, hogyan exportálhatsz egy szövegbeviteli űrlapmezőt szövegként, jó helyen jársz. Akár most kezded, akár csak frissíted a tudásodat, ez az útmutató végigvezet mindenen, amit tudnod kell. Kezdjük is, jó?

## Előfeltételek

Mielőtt belevágnánk a lényegbe, győződjünk meg róla, hogy minden a rendelkezésedre áll a zökkenőmentes végrehajtáshoz:

- Aspose.Words .NET-hez: Töltse le és telepítse a legújabb verziót innen: [itt](https://releases.aspose.com/words/net/).
- IDE: Visual Studio vagy bármilyen C# fejlesztői környezet.
- C# alapismeretek: A C# alapvető szintaxisának és objektumorientált programozási koncepcióinak ismerete.
- Dokumentum: Egy minta Word-dokumentum (`Rendering.docx`) szövegbeviteli űrlapmezőket.

## Névterek importálása

Először is importálnod kell a szükséges névtereket. Ezek olyanok, mint az építőelemek, amelyek biztosítják a zökkenőmentes működést.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Rendben, most, hogy készen vannak a névtereink, vágjunk bele a műveletbe!

## 1. lépés: A projekt beállítása

Mielőtt belemennénk a kódba, ellenőrizzük, hogy a projektünk megfelelően van-e beállítva.

## A projekt létrehozása

1. Nyissa meg a Visual Studio-t: Kezdje a Visual Studio vagy a kívánt C# fejlesztői környezet megnyitásával.
2. Új projekt létrehozása: Navigálás ide `File > New > Project`Válasszon `Console App (.NET Core)` vagy bármely más releváns projekttípus.
3. Nevezd el a projektedet: Adj a projektednek egy értelmes nevet, például `AsposeWordsExportExample`.

## Aspose.Words hozzáadása

1. NuGet-csomagok kezelése: Kattintson a jobb gombbal a projektre a Megoldáskezelőben, és válassza a lehetőséget. `Manage NuGet Packages`.
2. Aspose.Words keresése: A NuGet csomagkezelőben keresse meg a következőt: `Aspose.Words`.
3. Aspose.Words telepítése: Kattintson ide `Install` az Aspose.Words könyvtár projekthez való hozzáadásához.

## 2. lépés: Töltse be a Word dokumentumot

Most, hogy a projektünk beállítva van, töltsük be a szövegbeviteli űrlapmezőket tartalmazó Word dokumentumot.

1. Dokumentumkönyvtár megadása: Adja meg a dokumentum tárolási könyvtárának elérési útját.
2. A dokumentum betöltése: Használja a `Document` osztály a Word dokumentum betöltéséhez.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Az exportkönyvtár előkészítése

Exportálás előtt győződjünk meg róla, hogy az exportkönyvtárunk készen áll. Ide fogjuk menteni a HTML-fájlt és a képeket.

1. Exportkönyvtár meghatározása: Adja meg az exportált fájlok mentési útvonalát.
2. Könyvtár ellenőrzése és törlése: Győződjön meg arról, hogy a könyvtár létezik és üres.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## 4. lépés: Mentési beállítások konfigurálása

Itt történik a varázslat. Be kell állítanunk a mentési beállításokat, hogy a szövegbeviteli űrlapmezőt egyszerű szövegként exportáljuk.

1. Létrehozási mentési beállítások: Új inicializálása `HtmlSaveOptions` objektum.
2. Exportálási szöveg beállítása: Konfigurálja a `ExportTextInputFormFieldAsText` ingatlan `true`.
3. Képek mappa beállítása: Adja meg a mappát, ahová a képek mentésre kerülnek.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## 5. lépés: Mentse el a dokumentumot HTML formátumban

Végül mentsük el a Word dokumentumot HTML fájlként a beállított mentési beállításokkal.

1. Kimeneti útvonal meghatározása: Adja meg azt az útvonalat, ahová a HTML-fájl mentésre kerül.
2. Dokumentum mentése: Használja a `Save` a módszer `Document` osztály a dokumentum exportálásához.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Következtetés

És íme! Sikeresen exportáltál egy szövegbeviteli űrlapmezőt egyszerű szövegként az Aspose.Words for .NET segítségével. Ez az útmutató világos, lépésről lépésre bemutatja a feladat elvégzését. Ne feledd, a gyakorlat teszi a mestert, ezért kísérletezz folyamatosan a különböző lehetőségekkel és beállításokkal, hogy lásd, mit tehetsz még az Aspose.Words segítségével.

## GYIK

### Exportálhatok más típusú űrlapmezőket ugyanazzal a módszerrel?

Igen, más típusú űrlapmezőket is exportálhat a különböző tulajdonságok konfigurálásával. `HtmlSaveOptions` osztály.

### Mi van, ha a dokumentumom képeket tartalmaz?

A képek a megadott képmappába lesznek mentve. Győződjön meg róla, hogy beállította a `ImagesFolder` ingatlan a `HtmlSaveOptions`.

### Szükségem van licencre az Aspose.Words-höz?

Igen, kérhetsz ingyenes próbaverziót [itt](https://releases.aspose.com/) vagy vásároljon licencet [itt](https://purchase.aspose.com/buy).

### Testreszabhatom az exportált HTML-t?

Abszolút! Az Aspose.Words számos lehetőséget kínál a HTML-kimenet testreszabására. Lásd a [dokumentáció](https://reference.aspose.com/words/net/) további részletekért.

### Kompatibilis az Aspose.Words a .NET Core-ral?

Igen, az Aspose.Words kompatibilis a .NET Core-ral, a .NET Frameworkkel és más .NET platformokkal.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
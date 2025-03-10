---
title: Szövegbeviteli űrlapmező exportálása szövegként
linktitle: Szövegbeviteli űrlapmező exportálása szövegként
second_title: Aspose.Words Document Processing API
description: Ebből az átfogó, lépésenkénti útmutatóból megtudhatja, hogyan exportálhatja a szövegbeviteli űrlapmezőket egyszerű szövegként az Aspose.Words for .NET segítségével.
weight: 10
url: /hu/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Szövegbeviteli űrlapmező exportálása szövegként

## Bevezetés

Tehát az Aspose.Words for .NET világába merül? Csodálatos választás! Ha szeretné megtanulni, hogyan exportálhat szövegbeviteli űrlapmezőt szövegként, akkor jó helyen jár. Akár csak most kezdi, akár fejleszti képességeit, ez az útmutató végigvezeti Önt mindenen, amit tudnia kell. Kezdjük, jó?

## Előfeltételek

Mielőtt belevetnénk magunkat a finomságokba, győződjünk meg arról, hogy minden megvan, ami a zökkenőmentes követéshez szükséges:

-  Aspose.Words for .NET: Töltse le és telepítse a legújabb verziót innen[itt](https://releases.aspose.com/words/net/).
- IDE: Visual Studio vagy bármilyen C# fejlesztői környezet.
- Alapvető C# ismeretek: Az alapvető C# szintaxis és objektumorientált programozási fogalmak megértése.
- Dokumentum: minta Word dokumentum (`Rendering.docx`) szövegbeviteli űrlapmezőkkel.

## Névterek importálása

Először is importálnia kell a szükséges névtereket. Ezek olyanok, mint az építőelemek, amelyektől minden zökkenőmentesen működik.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Rendben, most, hogy elkészültek a névtereink, ugorjunk bele a cselekvésbe!

## 1. lépés: Állítsa be a projektet

Mielőtt belevágnánk a kódba, győződjünk meg arról, hogy projektünk megfelelően van beállítva.

## A Projekt létrehozása

1. A Visual Studio megnyitása: Kezdje a Visual Studio vagy a kívánt C# fejlesztői környezet megnyitásával.
2.  Új projekt létrehozása: Navigáljon ide`File > New > Project` . Válassza ki`Console App (.NET Core)` vagy bármely más releváns projekttípus.
3.  Nevezze el projektjét: Adjon értelmes nevet a projektjének, valami ilyesmit`AsposeWordsExportExample`.

## Aspose.Words hozzáadása

1.  NuGet-csomagok kezelése: Kattintson a jobb gombbal a projektre a Solution Explorerben, és válassza a lehetőséget`Manage NuGet Packages`.
2.  Aspose.Words keresése: A NuGet Package Managerben keressen rá`Aspose.Words`.
3.  Az Aspose.Words telepítése: Kattintson a gombra`Install` hogy hozzáadja az Aspose.Words könyvtárat a projekthez.

## 2. lépés: Töltse be a Word-dokumentumot

Most, hogy a projektünk be van állítva, töltsük be a szövegbeviteli űrlapmezőket tartalmazó Word dokumentumot.

1. Adja meg a dokumentumkönyvtárat: Határozza meg annak a könyvtárnak az elérési útját, ahol a dokumentumot tárolja.
2.  A dokumentum betöltése: Használja a`Document` osztályba a Word-dokumentum betöltéséhez.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Készítse elő az exportálási címtárat

Mielőtt exportálnánk, győződjön meg arról, hogy az exportálási könyvtárunk készen áll. Ide kerül mentésre a HTML-fájlunk és a képeink.

1. Határozza meg az exportálási könyvtárat: Adja meg az exportált fájlok mentési útvonalát.
2. Ellenőrizze és tisztítsa meg a könyvtárat: Győződjön meg arról, hogy a könyvtár létezik és üres.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## 4. lépés: Konfigurálja a mentési beállításokat

Itt történik a varázslat. Be kell állítanunk mentési beállításainkat, hogy a szövegbeviteli űrlapmezőt egyszerű szövegként exportálhassuk.

1.  Mentés opciók létrehozása: Új inicializálása`HtmlSaveOptions` objektum.
2.  Szöveg exportálási opció beállítása: Konfigurálja a`ExportTextInputFormFieldAsText`tulajdonát`true`.
3. Képek mappa beállítása: Adja meg a mappát, ahová a képeket menteni szeretné.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## 5. lépés: Mentse el a dokumentumot HTML-ként

Végül mentsük el a Word-dokumentumot HTML-fájlként a beállított mentési opcióink segítségével.

1. Határozza meg a kimeneti útvonalat: Adja meg a HTML-fájl mentési útvonalát.
2.  A dokumentum mentése: Használja a`Save` módszere a`Document`osztályt a dokumentum exportálásához.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Következtetés

És megvan! Sikeresen exportált egy szövegbeviteli űrlapmezőt egyszerű szövegként az Aspose.Words for .NET használatával. Ennek az útmutatónak világos, lépésről lépésre történő megközelítést kellett volna adnia ennek a feladatnak az eléréséhez. Ne feledje, a gyakorlat teszi a mestert, ezért folytassa a kísérletezést a különböző opciókkal és beállításokkal, hogy megtudja, mit tehet még az Aspose.Words segítségével.

## GYIK

### Exportálhatok más típusú űrlapmezőket ugyanezzel a módszerrel?

 Igen, más típusú űrlapmezőket is exportálhat a különböző tulajdonságainak konfigurálásával`HtmlSaveOptions` osztály.

### Mi van, ha a dokumentumom képeket tartalmaz?

 A képek a megadott képek mappába kerülnek mentésre. Ügyeljen arra, hogy beállítsa a`ImagesFolder` ingatlan a`HtmlSaveOptions`.

### Szükségem van engedélyre az Aspose.Words használatához?

 Igen, ingyenes próbaverziót kaphat[itt](https://releases.aspose.com/) vagy vásároljon licencet[itt](https://purchase.aspose.com/buy).

### Testreszabhatom az exportált HTML-t?

 Teljesen! Az Aspose.Words különféle lehetőségeket kínál a HTML-kimenet testreszabásához. Lásd a[dokumentáció](https://reference.aspose.com/words/net/) további részletekért.

### Az Aspose.Words kompatibilis a .NET Core-al?

Igen, az Aspose.Words kompatibilis a .NET Core, a .NET Framework és más .NET platformokkal.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

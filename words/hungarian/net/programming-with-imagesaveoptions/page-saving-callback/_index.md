---
title: Oldal mentése Visszahívás
linktitle: Oldal mentése Visszahívás
second_title: Aspose.Words Document Processing API
description: Részletes, lépésenkénti útmutatónkkal megtudhatja, hogyan mentheti el a Word-dokumentum minden oldalát külön PNG-képként az Aspose.Words for .NET segítségével.
weight: 10
url: /hu/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Oldal mentése Visszahívás

## Bevezetés

Szia! Érezte már valaha, hogy egy Word-dokumentum minden oldalát külön képként kell elmentenie? Lehet, hogy egy nagy jelentést szeretne könnyen emészthető látványelemekre bontani, vagy bélyegképeket kell létrehoznia az előnézethez. Bármi is legyen az ok, az Aspose.Words for .NET használatával ez a feladat gyerekjáték. Ebben az útmutatóban végigvezetjük az oldalmentő visszahívás beállításának folyamatán, amellyel a dokumentum minden oldalát egyedi PNG-képként mentheti el. Egyből merüljünk bele!

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Words for .NET: Ha még nem tette meg, töltse le és telepítse a webhelyről[itt](https://releases.aspose.com/words/net/).
2. Visual Studio: Bármelyik verziónak működnie kell, de ehhez az útmutatóhoz a Visual Studio 2019-et fogom használni.
3. Alapvető C# ismerete: A követéshez alapszintű C# ismeretekre lesz szüksége.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ez segít nekünk elérni a szükséges osztályokat és metódusokat anélkül, hogy minden alkalommal beírnánk a teljes névteret.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Rendben, kezdjük a dokumentumkönyvtár elérési útjának meghatározásával. Ez az a hely, ahol a bevitt Word-dokumentum található, és ahol a kimeneti képek mentésre kerülnek.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Töltse be a dokumentumot

Ezután betöltjük a feldolgozni kívánt dokumentumot. Győződjön meg arról, hogy a dokumentum ("Rendering.docx") a megadott könyvtárban van.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Állítsa be a képmentési beállításokat

Konfigurálnunk kell a képek mentési beállításait. Ebben az esetben az oldalakat PNG-fájlként mentjük.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Itt,`PageSet` megadja a menteni kívánt oldalak tartományát, és`PageSavingCallback` rámutat az egyéni visszahívási osztályunkra.

## 4. lépés: Végezze el az Oldalmentés visszahívását

Most pedig valósítsuk meg a visszahívási osztályt, amely kezeli az egyes oldalak mentését.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Ez az osztály valósítja meg a`IPageSavingCallback` felületen, és azon belül`PageSaving` módszerrel minden mentett oldalhoz meghatározzuk az elnevezési mintát.

## 5. lépés: Mentse el a dokumentumot képekként

Végül elmentjük a dokumentumot a beállított opciókkal.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Következtetés

És megvan! Sikeresen beállított egy oldalmentő visszahívást, amellyel egy Word-dokumentum minden oldalát külön PNG-képként mentheti az Aspose.Words for .NET segítségével. Ez a technika hihetetlenül hasznos a különböző alkalmazásokhoz, az oldal-előnézetek létrehozásától a jelentésekhez készített egyedi oldalképekig. 

Boldog kódolást!

## GYIK

### Menthetek oldalakat a PNG-től eltérő formátumban?  
 Igen, mentheti az oldalakat különböző formátumokban, például JPEG, BMP és TIFF formátumban, ha módosítja a`SaveFormat` be`ImageSaveOptions`.

### Mi a teendő, ha csak bizonyos oldalakat akarok menteni?  
 A menteni kívánt oldalakat a gomb beállításával adhatja meg`PageSet` paraméter be`ImageSaveOptions`.

### Testreszabható a képminőség?  
 Teljesen! Olyan tulajdonságokat állíthat be, mint pl`ImageSaveOptions.JpegQuality` a kimeneti képek minőségének szabályozására.

### Hogyan kezelhetem hatékonyan a nagyméretű dokumentumokat?  
Nagyméretű dokumentumok esetén fontolja meg az oldalak kötegelt feldolgozását a memóriahasználat hatékony kezelése érdekében.

### Hol találhatok további információt az Aspose.Words for .NET-ről?  
 Nézze meg a[dokumentáció](https://reference.aspose.com/words/net/) átfogó útmutatókért és példákért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

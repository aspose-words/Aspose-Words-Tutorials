---
"description": "Tanuld meg, hogyan mentheted el egy Word-dokumentum minden oldalát külön PNG-képként az Aspose.Words for .NET segítségével részletes, lépésről lépésre haladó útmutatónkkal."
"linktitle": "Oldalmentés visszahívása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Oldalmentés visszahívása"
"url": "/hu/net/programming-with-imagesaveoptions/page-saving-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Oldalmentés visszahívása

## Bevezetés

Sziasztok! Éreztetek már úgy, hogy egy Word-dokumentum minden oldalát külön képként kell menteni? Talán egy nagy jelentést szeretnétek könnyen emészthető vizuális elemekre bontani, vagy esetleg előnézeti képeket kell létrehoznotok. Bármi is legyen az oka, az Aspose.Words for .NET használatával ez a feladat gyerekjáték. Ebben az útmutatóban végigvezetünk azon, hogyan állíthattok be egy oldalmentési visszahívást, amely a dokumentum minden oldalát külön PNG-képként menti. Vágjunk bele!

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy a következőkkel rendelkezünk:

1. Aspose.Words .NET-hez: Ha még nem tette meg, töltse le és telepítse innen: [itt](https://releases.aspose.com/words/net/).
2. Visual Studio: Bármelyik verziónak működnie kell, de ehhez az útmutatóhoz a Visual Studio 2019-et fogom használni.
3. C# alapismeretek: A haladáshoz C# alapismeretekre lesz szükséged.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ez segít abban, hogy a szükséges osztályokat és metódusokat anélkül érjük el, hogy minden alkalommal be kellene írnunk a teljes névteret.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Dokumentumkönyvtár beállítása

Rendben, kezdjük a dokumentumkönyvtár elérési útjának meghatározásával. Itt található a bemeneti Word-dokumentum, és itt lesznek mentve a kimeneti képek.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Töltse be a dokumentumot

Ezután betöltjük a feldolgozni kívánt dokumentumot. Győződjön meg róla, hogy a dokumentum ("Rendering.docx") a megadott könyvtárban van.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Képmentési beállítások konfigurálása

Be kell állítanunk a képek mentésének beállításait. Ebben az esetben PNG fájlként mentjük az oldalakat.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

Itt, `PageSet` megadja a mentendő oldalak tartományát, és `PageSavingCallback` az egyéni visszahívó osztályunkra mutat.

## 4. lépés: Az oldalmentő visszahívás megvalósítása

Most implementáljuk a visszahívó osztályt, amely kezeli az egyes oldalak mentésének módját.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

Ez az osztály megvalósítja a `IPageSavingCallback` felületen belül, `PageSaving` metódussal definiáljuk az egyes mentett oldalak elnevezési mintáját.

## 5. lépés: Mentse el a dokumentumot képként

Végül a beállított beállításokkal mentjük el a dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Következtetés

És íme! Sikeresen beállítottál egy oldalmentési visszahívást, amely a Word-dokumentum minden oldalát külön PNG-képként menti az Aspose.Words for .NET használatával. Ez a technika hihetetlenül hasznos különféle alkalmazásokhoz, az oldal előnézeteinek létrehozásától kezdve az egyes oldalképek jelentésekhez történő előállításáig. 

Jó kódolást!

## GYIK

### Menthetek oldalakat PNG-től eltérő formátumban?  
Igen, az oldalakat különböző formátumokban, például JPEG, BMP és TIFF formátumban mentheti a `SaveFormat` ban `ImageSaveOptions`.

### Mi van, ha csak bizonyos oldalakat szeretnék menteni?  
A menteni kívánt oldalakat a beállítások módosításával adhatja meg. `PageSet` paraméter `ImageSaveOptions`.

### Lehetséges a képminőség testreszabása?  
Természetesen! Beállíthatsz olyan tulajdonságokat, mint `ImageSaveOptions.JpegQuality` a kimeneti képek minőségének szabályozására.

### Hogyan kezelhetem hatékonyan a nagyméretű dokumentumokat?  
Nagy dokumentumok esetén érdemes kötegelt oldalakat feldolgozni a memóriahasználat hatékony kezelése érdekében.

### Hol találok további információt az Aspose.Words for .NET-ről?  
Nézd meg a [dokumentáció](https://reference.aspose.com/words/net/) átfogó útmutatókért és példákért.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
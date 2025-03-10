---
title: Csökkentse a PDF méretét a Wmf betűtípusok átméretezésével metafájl méretre
linktitle: Csökkentse a PDF méretét a Wmf betűtípusok átméretezésével metafájl méretre
second_title: Aspose.Words Document Processing API
description: Útmutató lépésről lépésre a PDF méretének csökkentéséhez wmf-betűtípusok átméretezésével metafájl méretre, ha az Aspose.Words for .NET segítségével PDF-be konvertál.
weight: 10
url: /hu/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Csökkentse a PDF méretét a Wmf betűtípusok átméretezésével metafájl méretre

## Bevezetés

Amikor PDF fájlokkal dolgozik, különösen a WMF (Windows Metafile) grafikát tartalmazó Word-dokumentumokból előállítottakkal, a méretkezelés a dokumentumkezelés kulcsfontosságú szempontjává válhat. A PDF-méret szabályozásának egyik módja a WMF-betűtípusok dokumentumon belüli megjelenítésének módosítása. Ebben az oktatóanyagban megvizsgáljuk, hogyan csökkenthetjük a PDF-méretet a WMF-betűkészletek metafájl méretére skálázásával az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt belemerülne a lépésekbe, győződjön meg arról, hogy rendelkezik a következőkkel:

1. Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van az Aspose.Words könyvtár. Ha nem, akkor megteheti[töltse le itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Ez az oktatóanyag feltételezi, hogy be van állítva egy .NET fejlesztői környezet (például a Visual Studio), ahol írhat és futtathat C# kódot.
3. A .NET programozás alapjai: Hasznos lesz az alapvető .NET programozási fogalmak és a C# szintaxis ismerete.
4. Word dokumentum WMF grafikával: Szüksége lesz egy WMF grafikát tartalmazó Word dokumentumra. Használhatja saját dokumentumát, vagy létrehozhat egyet teszteléshez.

## Névterek importálása

Először is importálnia kell a szükséges névtereket a C# projektbe. Ez hozzáférést biztosít az Aspose.Words használatához szükséges osztályokhoz és metódusokhoz.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Töltse be a Word-dokumentumot

 A kezdéshez töltse be a WMF grafikát tartalmazó Word dokumentumot. Ez a`Document` osztály Aspose-tól.Words.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Töltse be a dokumentumot
Document doc = new Document(dataDir + "WMF with text.docx");
```

 Itt,`dataDir` a dokumentumkönyvtár elérési útjának helyőrzője. Létrehozunk egy példányt a`Document` osztályt a Word fájl elérési útjának átadásával. Ezzel a dokumentum betöltődik a memóriába, és készen áll a további feldolgozásra.

## 2. lépés: Konfigurálja a metafájl megjelenítési beállításait

 Ezután konfigurálnia kell a metafájl megjelenítési beállításait. Pontosabban állítsa be a`ScaleWmfFontsToMetafileSize`tulajdonát`false`. Ez szabályozza, hogy a WMF-betűkészletek a metafájl méretéhez igazodjanak-e.

```csharp
// Hozzon létre egy új MetafileRenderingOptions példányt
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 A`MetafileRenderingOptions` osztály lehetőséget biztosít a metafájlok (például a WMF) megjelenítésére. Beállítás által`ScaleWmfFontsToMetafileSize` hogy`false`, akkor utasítja az Aspose.Words-t, hogy ne méretezze át a betűtípusokat a metafájl méretének megfelelően, ami segíthet a PDF teljes méretének csökkentésében.

## 3. lépés: Állítsa be a PDF mentési beállításokat

Most állítsa be a PDF-mentési beállításokat az imént beállított metafájl-megjelenítési beállítások használatához. Ez megmondja az Aspose.Words számára, hogyan kezelje a metafájlokat a dokumentum PDF formátumban történő mentésekor.

```csharp
// Hozzon létre egy új PdfSaveOptions példányt
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 A`PdfSaveOptions` osztály lehetővé teszi különböző beállítások megadását a dokumentum PDF formátumban történő mentéséhez. A korábban konfigurált hozzárendelésével`MetafileRenderingOptions` a`MetafileRenderingOptions` tulajdona`PdfSaveOptions`, biztosítja, hogy a dokumentum a kívánt metafájl-megjelenítési beállításoknak megfelelően kerüljön mentésre.

## 4. lépés: Mentse el a dokumentumot PDF formátumban

Végül mentse a Word-dokumentumot PDF-ként a konfigurált mentési beállításokkal. Ez az összes beállítást alkalmazza a kimeneti PDF-re, beleértve a metafájl-megjelenítési beállításokat is.


```csharp
// Mentse el a dokumentumot PDF formátumban
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 Ebben a lépésben a`Save` módszere a`Document` osztályt használják a dokumentum PDF-fájlba való exportálására. Meg van adva a PDF mentési útvonala, valamint a`PdfSaveOptions` amelyek tartalmazzák a metafájl megjelenítési beállításait.

## Következtetés

WMF-betűkészletek metafájl méretre skálázásával jelentősen csökkentheti a Word dokumentumokból előállított PDF-fájlok méretét. Ez a technika segít a dokumentumok tárolásának és terjesztésének optimalizálásában a vizuális tartalom minőségének veszélyeztetése nélkül. A fent vázolt lépések követése biztosítja, hogy PDF-fájljai könnyebben kezelhetőek és hatékonyabbak legyenek.

## GYIK

### Mi az a WMF, és miért fontos a PDF méretéhez?

A WMF (Windows Metafile) a Microsoft Windows rendszerben használt grafikus formátum. Tartalmazhat vektoros és bittérképes adatokat is. Mivel a vektoradatok méretezhetők és manipulálhatók, fontos, hogy megfelelően kezeljük őket, hogy elkerüljük a szükségtelenül nagy PDF-fájlokat.

### Hogyan befolyásolja a PDF-et a WMF-betűtípusok metafájl méretre skálázása?

A WMF-betűtípusok metafájlméretre méretezésével csökkenthető a PDF teljes mérete azáltal, hogy elkerülhető a nagy felbontású betűkészlet-megjelenítés, amely növelheti a fájlméretet.

### Használhatok más metafájlformátumokat az Aspose.Words-ben?

Igen, az Aspose.Words különféle metafájlformátumokat támogat, beleértve az EMF-et (Enhanced Metafile) a WMF mellett.

### Alkalmazható ez a technika minden típusú Word dokumentumra?

Igen, ez a technika minden olyan Word dokumentumra alkalmazható, amely WMF grafikát tartalmaz, így segít optimalizálni a generált PDF méretét.

### Hol találhatok több információt az Aspose.Words-ről?

 Az Aspose.Wordsről többet megtudhat a[Aspose.Words Dokumentáció](https://reference.aspose.com/words/net/) . Letöltésekért, próbaverziókért és támogatásért keresse fel a[Aspose.Words letöltési oldal](https://releases.aspose.com/words/net/), [Vásároljon Aspose.Words-t](https://purchase.aspose.com/buy), [Ingyenes próbaverzió](https://releases.aspose.com/), [Ideiglenes jogosítvány](https://purchase.aspose.com/temporary-license/) , és[Támogatás](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

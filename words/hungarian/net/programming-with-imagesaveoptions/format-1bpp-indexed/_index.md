---
title: Formátum 1Bpp Indexelt
linktitle: Formátum 1Bpp Indexelt
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan alakíthat át Word-dokumentumot 1 Bpp indexelt képpé az Aspose.Words for .NET használatával. Kövesse lépésenkénti útmutatónkat az egyszerű átalakítás érdekében.
weight: 10
url: /hu/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formátum 1Bpp Indexelt

## Bevezetés

Gondolkozott már azon, hogyan menthet el egy Word-dokumentumot fekete-fehér képként, mindössze néhány sornyi kóddal? Nos, szerencséd van! Ma egy ügyes kis trükkben merülünk el az Aspose.Words for .NET használatával, amely lehetővé teszi dokumentumainak 1 Bpp indexelt képekké alakítását. Ez a formátum tökéletes bizonyos típusú digitális archiváláshoz, nyomtatáshoz, vagy amikor helyet takarít meg. Az egyes lépéseket lebontjuk, hogy olyan egyszerű legyen, mint a pite. Készen áll az indulásra? Merüljünk el!

## Előfeltételek

Mielőtt bemocskolnánk a kezünket, néhány dolgot meg kell tennie:

-  Aspose.Words for .NET: Győződjön meg arról, hogy a könyvtár telepítve van. Megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- .NET fejlesztői környezet: A Visual Studio jó választás, de bármilyen olyan környezetet használhat, amelyben kényelmes.
- Alapvető C# ismeretek: Ne aggódjon, mi lesz egyszerű, de egy kis C# ismerete segít.
- Word-dokumentum: Készítsen egy minta Word-dokumentumot a konvertálásra.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ez döntő fontosságú, mivel lehetővé teszi számunkra, hogy hozzáférjünk a szükséges osztályokhoz és metódusokhoz az Aspose.Words-ből.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Meg kell adnia a dokumentumkönyvtár elérési útját. Ez az a hely, ahol a Word dokumentumot tárolja, és ahol a konvertált kép mentésre kerül.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Töltse be a Word-dokumentumot

 Most töltsük be a Word dokumentumot egy Aspose.Words-be`Document` objektum. Ez az objektum a Word-fájlt képviseli, és lehetővé teszi annak kezelését.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Állítsa be a képmentési beállításokat

 Ezután be kell állítanunk a`ImageSaveOptions`Itt történik a varázslat. Úgy konfiguráljuk, hogy a képet PNG formátumban, 1 Bpp indexelt színmóddal mentse.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Ez adja meg, hogy a dokumentumot PNG képként szeretnénk menteni.
- PageSet(1): Ez azt jelzi, hogy csak az első oldalt konvertáljuk.
- ImageColorMode.BlackAndWhite: Fekete-fehérre állítja a képet.
- ImagePixelFormat.Format1bppIndexed: A képformátumot 1 Bpp indexeltre állítja.

## 4. lépés: Mentse el a dokumentumot képként

 Végül a dokumentumot képként mentjük el a`Save` módszere a`Document` objektum.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Következtetés

És megvan! Néhány sornyi kóddal a Word-dokumentumot 1 Bpp indexelt képpé alakította az Aspose.Words for .NET segítségével. Ez a módszer hihetetlenül hasznos nagy kontrasztú, helytakarékos képek készítéséhez a dokumentumokból. Most ezt könnyedén integrálhatja projektjeibe és munkafolyamataiba. Boldog kódolást!

## GYIK

### Mi az 1 Bpp indexelt kép?
Az 1 Bpp (1 Bit Per Pixel) indexelt kép egy fekete-fehér képformátum, amelyben minden képpont egyetlen bittel (0 vagy 1) jelenik meg. Ez a formátum rendkívül helytakarékos.

### Konvertálhatok egy Word-dokumentum több oldalát egyszerre?
 Igen, megteheti. Módosítsa a`PageSet` ingatlan a`ImageSaveOptions` hogy több oldalt vagy a teljes dokumentumot tartalmazza.

### Szükségem van licencre az Aspose.Words for .NET használatához?
 Igen, az Aspose.Words for .NET szolgáltatáshoz licenc szükséges a teljes funkcionalitáshoz. Kaphatsz a[ideiglenes engedély itt](https://purchase.aspose.com/temporary-license/).

### Milyen más képformátumokba konvertálhatom a Word dokumentumomat?
 Az Aspose.Words különféle képformátumokat támogat, beleértve a JPEG-et, BMP-t és TIFF-et. Egyszerűen változtassa meg a`SaveFormat` a`ImageSaveOptions`.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?
 Részletes dokumentációt találhat a[Aspose.Words for .NET dokumentációs oldal](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

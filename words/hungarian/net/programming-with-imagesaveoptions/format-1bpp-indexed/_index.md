---
"description": "Tanuld meg, hogyan konvertálhatsz egy Word-dokumentumot 1 Bpp-s indexelt képpé az Aspose.Words for .NET segítségével. Kövesd lépésről lépésre szóló útmutatónkat az egyszerű konverzióhoz."
"linktitle": "Formátum&#58; 1Bpp Indexelt"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Formátum&#58; 1Bpp Indexelt"
"url": "/hu/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formátum: 1Bpp Indexelt

## Bevezetés

Elgondolkodtál már azon, hogyan menthetsz el egy Word dokumentumot fekete-fehér képként mindössze néhány sornyi kóddal? Nos, szerencséd van! Ma egy ügyes kis trükkel fogunk elmerülni az Aspose.Words for .NET használatával, amely lehetővé teszi a dokumentumok 1 Bpp indexelt képekké konvertálását. Ez a formátum tökéletes bizonyos típusú digitális archiváláshoz, nyomtatáshoz, vagy ha helyet kell megtakarítanod. Lebontjuk az egyes lépéseket, hogy a lehető legegyszerűbb legyen. Készen állsz a kezdésre? Vágjunk bele!

## Előfeltételek

Mielőtt belekezdenénk, van néhány dolog, amire oda kell figyelnünk:

- Aspose.Words .NET-hez: Győződjön meg róla, hogy telepítve van a könyvtár. Megteheti [töltsd le itt](https://releases.aspose.com/words/net/).
- .NET fejlesztői környezet: A Visual Studio jó választás, de bármilyen olyan környezetet használhatsz, amellyel jól érzed magad.
- C# alapismeretek: Ne aggódj, egyszerűen fogjuk csinálni, de egy kis C# ismeretség sokat segít.
- Word-dokumentum: Készítsen elő egy minta Word-dokumentumot az átalakításhoz.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ez azért kulcsfontosságú, mert lehetővé teszi számunkra, hogy hozzáférjünk a szükséges osztályokhoz és metódusokhoz az Aspose.Words-ből.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Dokumentumkönyvtár beállítása

Meg kell adnia a dokumentum könyvtárának elérési útját. Ez az a hely, ahol a Word-dokumentum tárolódik, és ahová a konvertált kép mentésre kerül.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Töltse be a Word dokumentumot

Most töltsük be a Word dokumentumot egy Aspose.Words fájlba. `Document` objektum. Ez az objektum a Word-fájlt jelöli, és lehetővé teszi annak kezelését.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 3. lépés: Képmentési beállítások konfigurálása

Ezután be kell állítanunk a `ImageSaveOptions`Itt történik a varázslat. Úgy fogjuk beállítani, hogy a képet PNG formátumban, 1Bpp indexelt színmódban mentse el.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Ez meghatározza, hogy PNG képként szeretnénk menteni a dokumentumot.
- PageSet(1): Ez azt jelzi, hogy csak az első oldalt konvertáljuk.
- ImageColorMode.BlackAndWhite: Ez fekete-fehérre állítja a képet.
- ImagePixelFormat.Format1bppIndexed: Ez a képformátumot 1Bpp indexeltre állítja.

## 4. lépés: Mentse el a dokumentumot képként

Végül képként mentjük el a dokumentumot a `Save` a módszer `Document` objektum.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Következtetés

És íme! Mindössze néhány sornyi kóddal átalakítottad a Word-dokumentumot egy 1 Bpp-s indexelt képpé az Aspose.Words for .NET segítségével. Ez a módszer hihetetlenül hasznos nagy kontrasztú, helytakarékos képek létrehozásához a dokumentumokból. Mostantól könnyedén integrálhatod ezt a projektjeidbe és munkafolyamataidba. Jó kódolást!

## GYIK

### Mi az az 1Bpp indexelt kép?
Az 1Bpp (1 bit pixelenként) indexelt kép egy fekete-fehér képformátum, ahol minden pixelt egyetlen bit, 0 vagy 1 jelöl. Ez a formátum rendkívül helytakarékos.

### Konvertálhatok egyszerre több oldalt egy Word dokumentumból?
Igen, módosíthatja. `PageSet` ingatlan a `ImageSaveOptions` több oldal vagy a teljes dokumentum belefoglalása.

### Szükségem van licencre az Aspose.Words for .NET használatához?
Igen, az Aspose.Words for .NET teljes funkcionalitásához licenc szükséges. Szerezhet egyet [ideiglenes jogosítvány itt](https://purchase.aspose.com/temporary-license/).

### Milyen más képformátumokba konvertálhatom a Word-dokumentumomat?
Az Aspose.Words számos képformátumot támogat, beleértve a JPEG, BMP és TIFF formátumokat. Egyszerűen módosítsa a `SaveFormat` a `ImageSaveOptions`.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?
Részletes dokumentációt találhat a [Aspose.Words .NET dokumentációs oldal](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
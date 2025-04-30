---
"description": "Tanuld meg, hogyan használhatod a célgépről származó betűtípusokat a Word-dokumentumaidban az Aspose.Words for .NET segítségével. Kövesd lépésről lépésre szóló útmutatónkat a betűtípusok zökkenőmentes integrációjához."
"linktitle": "Használja a célgép betűtípusát"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Használja a célgép betűtípusát"
"url": "/hu/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Használja a célgép betűtípusát

## Bevezetés

Készen állsz, hogy belemerülj az Aspose.Words for .NET lenyűgöző világába? Csatold be a csatodat, mert egy utazásra viszünk a betűtípusok varázslatos birodalmába. Ma arra összpontosítunk, hogyan használhatod a célgép betűtípusait Word dokumentumokkal való munka közben. Ez az ügyes funkció biztosítja, hogy a dokumentumod pontosan úgy nézzen ki, ahogyan szeretnéd, függetlenül attól, hogy hol tekinted meg. Kezdjük is!

## Előfeltételek

Mielőtt belemennénk a részletekbe, győződjünk meg róla, hogy minden szükséges dolog megvan:

1. Aspose.Words for .NET: Győződjön meg róla, hogy telepítve van az Aspose.Words for .NET könyvtár. Ha még nem tette meg, letöltheti. [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Rendelkeznie kell egy beállított .NET fejlesztői környezettel, például a Visual Studio-val.
3. Dolgozandó dokumentum: Készíts elő egy Word-dokumentumot a teszteléshez. Egy „Felsorolásjelek alternatív betűtípussal.docx” nevű dokumentumot fogunk használni.

Most, hogy áttekintettük az alapokat, lássuk a kódot!

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ez a projektünk gerince, amely összeköti az összes pontot.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Töltse be a Word dokumentumot

Az oktatóanyagunk első lépése a Word dokumentum betöltése. Itt kezdődik minden. A következőt fogjuk használni: `Document` osztályt az Aspose.Words könyvtárból ennek eléréséhez.

### 1.1. lépés: A dokumentum elérési útjának meghatározása

Kezdjük a dokumentumok könyvtárának elérési útjának meghatározásával. Itt található a Word-dokumentum.

```csharp
// A dokumentumok könyvtárának elérési útja
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

### 1.2. lépés: A dokumentum betöltése

Most betöltjük a dokumentumot a következővel: `Document` osztály.

```csharp
// Töltsd be a Word dokumentumot
Document doc = new Document(dataDir + "Bullet points with alternative font.docx");
```

## 2. lépés: Mentési beállítások konfigurálása

Ezután konfigurálnunk kell a mentési beállításokat. Ez a lépés kulcsfontosságú, mivel biztosítja, hogy a dokumentumban használt betűtípusok a célgépről származzanak.

Létrehozunk egy példányt a következőből: `HtmlFixedSaveOptions` és állítsa be a `UseTargetMachineFonts` ingatlan `true`.

```csharp
// Biztonsági mentési beállítások konfigurálása a „Célgépről származó betűtípusok használata” funkcióval
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions
{
    UseTargetMachineFonts = true
};
```

## 3. lépés: Mentse el a dokumentumot

Végül rögzített HTML fájlként mentjük el a dokumentumot. Itt történik a varázslat!

Használni fogjuk a `Save` módszer a dokumentum mentésére a konfigurált mentési beállításokkal.

```csharp
// Dokumentum konvertálása fix HTML-re
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
```

## 4. lépés: Ellenőrizze a kimenetet

Végül, de nem utolsósorban, mindig jó ötlet ellenőrizni a kimenetet. Nyisd meg a mentett HTML fájlt, és ellenőrizd, hogy a betűtípusok helyesen vannak-e alkalmazva a célgépen.

Navigálj abba a könyvtárba, ahová a HTML fájlt mentetted, és nyisd meg egy webböngészőben.

```csharp
// A kimenet ellenőrzéséhez nyissa meg a HTML fájlt.
System.Diagnostics.Process.Start(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html");
```

És íme! Sikeresen használtad a célgép betűtípusait a Word-dokumentumodban az Aspose.Words for .NET használatával.

## Következtetés

célgépről származó betűtípusok használata biztosítja, hogy a Word-dokumentumok egységes és professzionális megjelenésűek legyenek, függetlenül attól, hogy hol tekintik meg őket. Az Aspose.Words for .NET egyszerűvé és hatékonnyá teszi ezt a folyamatot. Az oktatóanyag követésével megtanultad, hogyan tölthetsz be egy dokumentumot, hogyan konfigurálhatod a mentési beállításokat, és hogyan mentheted el a dokumentumot a kívánt betűtípus-beállításokkal. Jó kódolást!

## GYIK

### Használhatom ezt a módszert más dokumentumformátumokkal?
Igen, az Aspose.Words for .NET különféle dokumentumformátumokat támogat, és hasonló mentési beállításokat konfigurálhat a különböző formátumokhoz.

### Mi van, ha a célgépen nincsenek meg a szükséges betűtípusok?
Ha a célgépen nincsenek meg a szükséges betűtípusok, előfordulhat, hogy a dokumentum nem a kívánt módon jelenik meg. Mindig érdemes betűtípusokat beágyazni, ha szükséges.

### Hogyan ágyazhatok be betűtípusokat egy dokumentumba?
A betűtípusok beágyazása a következővel végezhető el: `FontSettings` osztály az Aspose.Words .NET-hez. Lásd a [dokumentáció](https://reference.aspose.com/words/net/) további részletekért.

### Van mód a dokumentum előnézetének megtekintésére mentés előtt?
Igen, használhatod a `DocumentRenderer` osztályt a dokumentum mentés előtti előnézetéhez. Nézd meg az Aspose.Words .NET-hez készült verzióját. [dokumentáció](https://reference.aspose.com/words/net/) további információkért.

### Testreszabhatom tovább a HTML kimenetet?
Abszolút! A `HtmlFixedSaveOptions` osztály különféle tulajdonságokat biztosít a HTML-kimenet testreszabásához. Fedezze fel a [dokumentáció](https://reference.aspose.com/words/net/) az összes elérhető opcióhoz.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
---
"description": "Ismerje meg, hogyan engedélyezheti vagy tilthatja le a betűtípus-helyettesítést a Word-dokumentumokban az Aspose.Words for .NET használatával. Gondoskodjon arról, hogy dokumentumai minden platformon egységesen jelenjenek meg."
"linktitle": "Betűtípus-helyettesítés engedélyezése/letiltása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Betűtípus-helyettesítés engedélyezése/letiltása"
"url": "/hu/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus-helyettesítés engedélyezése/letiltása

## Bevezetés

Találkoztál már olyan helyzettel, hogy egy Word-dokumentumban a gondosan kiválasztott betűtípusokat egy másik számítógépen nézve lecserélik? Idegesítő, ugye? Ez a betűtípus-helyettesítés miatt történik, amely folyamat során a rendszer egy hiányzó betűtípust egy elérhetővel helyettesít. De ne aggódj! Az Aspose.Words for .NET segítségével könnyedén kezelheted és szabályozhatod a betűtípus-helyettesítést. Ebben az oktatóanyagban végigvezetünk a Word-dokumentumokban a betűtípus-helyettesítés engedélyezésének vagy letiltásának lépésein, biztosítva, hogy a dokumentumok mindig pontosan úgy nézzenek ki, ahogyan szeretnéd.

## Előfeltételek

Mielőtt belevágnánk a lépésekbe, győződjünk meg róla, hogy minden szükséges eszköz a rendelkezésünkre áll:

- Aspose.Words .NET-hez: Töltse le a legújabb verziót [itt](https://releases.aspose.com/words/net/).
- Visual Studio: Bármely .NET-et támogató verzió.
- C# alapismeretek: Ez segít majd követni a kódolási példákat.

## Névterek importálása

Első lépésként győződjön meg arról, hogy importálta a szükséges névtereket a projektjébe. Adja hozzá ezeket a C# fájl elejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Most pedig bontsuk le a folyamatot egyszerű, könnyen követhető lépésekre.

## 1. lépés: A projekt beállítása

Először is hozz létre egy új projektet a Visual Studioban, és adj hozzá egy hivatkozást az Aspose.Words for .NET könyvtárhoz. Ha még nem tetted meg, töltsd le innen: [Aspose weboldal](https://releases.aspose.com/words/net/).

## 2. lépés: Töltse be a dokumentumot

Ezután töltse be a dokumentumot, amellyel dolgozni szeretne. Így teheti meg:

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Csere `"YOUR DOCUMENT DIRECTORY"` a dokumentumkönyvtár tényleges elérési útjával. Ez a kód betölti a dokumentumot a memóriába, így azt módosítani lehet.

## 3. lépés: Betűtípus-beállítások konfigurálása

Most pedig hozzunk létre egy `FontSettings` objektum a betűtípus-helyettesítési beállítások kezeléséhez:

```csharp
FontSettings fontSettings = new FontSettings();
```

## 4. lépés: Alapértelmezett betűtípus-helyettesítés beállítása

Állítsd be az alapértelmezett betűtípus-helyettesítést egy tetszőleges betűtípusra. Ez a betűtípus lesz használva, ha az eredeti betűtípus nem érhető el:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

Ebben a példában az Arial betűtípust használjuk alapértelmezettként.

## 5. lépés: A betűtípus-információ helyettesítésének letiltása

A betűtípus-információ helyettesítésének letiltásához, amely megakadályozza, hogy a rendszer a hiányzó betűtípusokat elérhető betűtípusokkal helyettesítse, használja a következő kódot:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## 6. lépés: Betűtípus-beállítások alkalmazása a dokumentumra

Most alkalmazza ezeket a beállításokat a dokumentumára:

```csharp
doc.FontSettings = fontSettings;
```

## 7. lépés: Mentse el a dokumentumot

Végül mentse el a módosított dokumentumot. Bármilyen formátumban mentheti. Ebben az oktatóanyagban PDF formátumban fogjuk menteni:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Következtetés

És íme! A következő lépéseket követve könnyedén szabályozhatod a betűtípus-helyettesítést a Word-dokumentumaidban az Aspose.Words for .NET segítségével. Ez biztosítja, hogy a dokumentumok megtartsák a kívánt megjelenést és érzetet, függetlenül attól, hogy hol tekintik meg őket.

## GYIK

### Használhatok az Arialtól eltérő betűtípusokat helyettesítésre?

Természetesen! A rendszeren elérhető bármelyik betűtípust megadhatja a betűtípus nevének módosításával a `DefaultFontName` ingatlan.

### Mi történik, ha a megadott alapértelmezett betűtípus nem érhető el?

Ha az alapértelmezett betűtípus nem érhető el, az Aspose.Words egy rendszer által használt tartalék mechanizmust fog használni a megfelelő helyettesítő megtalálásához.

### Újra engedélyezhetem a betűtípus-helyettesítést a letiltás után?

Igen, át lehet kapcsolni a `Enabled` tulajdona `FontInfoSubstitution` vissza a `true` ha újra engedélyezni szeretné a betűtípus-helyettesítést.

### Van mód ellenőrizni, hogy mely betűtípusokat helyettesíti a rendszer?

Igen, az Aspose.Words metódusokat biztosít a betűtípus-helyettesítés naplózására és nyomon követésére, lehetővé téve, hogy lásd, mely betűtípusokat cserélik le.

### Használhatom ezt a módszert a DOCX-en kívül más dokumentumformátumokhoz is?

Határozottan! Az Aspose.Words számos formátumot támogat, és ezeket a betűtípus-beállításokat bármelyik támogatott formátumra alkalmazhatod.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
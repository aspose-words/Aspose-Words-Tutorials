---
title: Engedélyezze a Betűtípus-csere letiltását
linktitle: Engedélyezze a Betűtípus-csere letiltását
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan engedélyezheti vagy tilthatja le a betűtípusok helyettesítését Word-dokumentumokban az Aspose.Words for .NET használatával. Gondoskodjon arról, hogy dokumentumai minden platformon egységesek legyenek.
weight: 10
url: /hu/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Engedélyezze a Betűtípus-csere letiltását

## Bevezetés

Előfordult már, hogy olyan helyzetbe került, amikor egy Word-dokumentumban az aprólékosan kiválasztott betűtípusokat egy másik számítógépen való megtekintéskor lecserélik? Idegesítő, igaz? Ez a betűkészlet-csere miatt következik be, amely folyamat során a rendszer a hiányzó betűtípust egy elérhetőre cseréli. De ne aggódj! Az Aspose.Words for .NET segítségével egyszerűen kezelheti és szabályozhatja a betűtípusok helyettesítését. Ebben az oktatóanyagban végigvezetjük a betűtípus-helyettesítés engedélyezésének vagy letiltásának lépésein a Word-dokumentumokban, így biztosítva, hogy a dokumentumok mindig úgy nézzenek ki, ahogyan szeretné.

## Előfeltételek

Mielőtt belevágna a lépésekbe, győződjön meg arról, hogy mindennel rendelkezik, amire szüksége van:

-  Aspose.Words for .NET: Töltse le a legújabb verziót[itt](https://releases.aspose.com/words/net/).
- Visual Studio: Bármely .NET-et támogató verzió.
- C# alapismeretek: Ez segít a kódolási példák követésében.

## Névterek importálása

A kezdéshez győződjön meg arról, hogy a szükséges névtereket importálta a projektbe. Adja hozzá ezeket a C# fájl tetejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Most bontsuk le a folyamatot egyszerű, kezelhető lépésekre.

## 1. lépés: Állítsa be projektjét

Először állítson be egy új projektet a Visual Studióban, és adjon hozzá hivatkozást az Aspose.Words for .NET könyvtárra. Ha még nem tette meg, töltse le a[Aspose honlapja](https://releases.aspose.com/words/net/).

## 2. lépés: Töltse be a dokumentumot

Ezután töltse be azt a dokumentumot, amellyel dolgozni szeretne. Íme, hogyan kell csinálni:

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a dokumentumkönyvtár tényleges elérési útjával. Ez a kód betölti a dokumentumot a memóriába, így Ön módosíthatja azt.

## 3. lépés: Konfigurálja a betűtípus-beállításokat

 Most hozzunk létre egy`FontSettings` objektum a betűtípus helyettesítési beállításainak kezelésére:

```csharp
FontSettings fontSettings = new FontSettings();
```

## 4. lépés: Állítsa be az alapértelmezett betűtípus-helyettesítést

Állítsa be az alapértelmezett betűtípus-helyettesítést az Ön által választott betűtípusra. Ezt a betűtípust használja a rendszer, ha az eredeti betűtípus nem érhető el:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

Ebben a példában az Arial-t használjuk alapértelmezett betűtípusként.

## 5. lépés: Kapcsolja ki a betűtípus-információ helyettesítését

A betűtípus-információk helyettesítésének letiltásához, amely megakadályozza, hogy a rendszer a hiányzó betűtípusokat elérhetőre cserélje, használja a következő kódot:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## 6. lépés: Alkalmazza a Betűtípus-beállításokat a dokumentumra

Most alkalmazza ezeket a beállításokat a dokumentumra:

```csharp
doc.FontSettings = fontSettings;
```

## 7. lépés: Mentse el a dokumentumot

Végül mentse el a módosított dokumentumot. Bármilyen formátumban elmentheti. Ehhez az oktatóanyaghoz PDF formátumban mentjük:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Következtetés

És megvan! Ha követi ezeket a lépéseket, az Aspose.Words for .NET segítségével egyszerűen szabályozhatja a betűtípusok helyettesítését a Word-dokumentumokban. Ez biztosítja, hogy a dokumentumok megőrizzék eredeti megjelenésüket, függetlenül attól, hogy hol tekintik meg őket.

## GYIK

### Használhatok az Arialtól eltérő betűtípusokat helyettesítésre?

 Teljesen! A rendszeren elérhető bármely betűtípust megadhatja a betűtípus nevének megváltoztatásával a`DefaultFontName` ingatlan.

### Mi történik, ha a megadott alapértelmezett betűtípus nem érhető el?

Ha az alapértelmezett betűtípus nem érhető el, az Aspose.Words a rendszer tartalék mechanizmusát használja a megfelelő csere megtalálásához.

### A letiltást követően újra engedélyezhetem a betűtípus helyettesítését?

 Igen, átkapcsolhatod a`Enabled` tulajdona`FontInfoSubstitution` vissza`true` ha ismét engedélyezni szeretné a betűtípus helyettesítését.

### Van mód annak ellenőrzésére, hogy mely betűtípusok vannak helyettesítve?

Igen, az Aspose.Words módszereket biztosít a betűtípusok helyettesítésének naplózására és nyomon követésére, lehetővé téve, hogy megnézze, mely betűtípusok kerülnek lecserélésre.

### Használhatom ezt a módszert a DOCX-en kívül más dokumentumformátumokhoz is?

Határozottan! Az Aspose.Words különféle formátumokat támogat, és ezeket a betűtípus-beállításokat bármilyen támogatott formátumra alkalmazhatja.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
title: Állítsa be a relatív vízszintes vagy függőleges pozíciót
linktitle: Állítsa be a relatív vízszintes vagy függőleges pozíciót
second_title: Aspose.Words Document Processing API
description: Ebből a lépésről lépésre szóló útmutatóból megtudhatja, hogyan állíthat be relatív vízszintes és függőleges pozíciókat a Word-dokumentumok táblázataihoz az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a relatív vízszintes vagy függőleges pozíciót

## Bevezetés

Elakadt már azzal kapcsolatban, hogyan helyezze el a táblázatokat a kívánt módon a Word-dokumentumokban? Nos, nem vagy egyedül. Akár professzionális jelentést, akár stílusos brosúrát készít, a táblázatok igazítása világot hozhat. Itt jön jól az Aspose.Words for .NET. Ez az oktatóanyag lépésről lépésre végigvezeti Önt a Word-dokumentumok táblázatainak relatív vízszintes vagy függőleges helyzetének beállításához. Merüljünk el!

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Words for .NET: Ha még nem tette meg, letöltheti[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Visual Studio vagy bármely más .NET-kompatibilis IDE.
3. Alapvető C# ismerete: Ez az oktatóanyag feltételezi, hogy ismeri a C# programozás alapjait.

## Névterek importálása

Először is importálnia kell a szükséges névtereket. Ez elengedhetetlen az Aspose.Words funkciók eléréséhez.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 1. lépés: Töltse be a dokumentumot

A kezdéshez be kell töltenie a Word dokumentumot a programba. A következőképpen teheti meg:

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Ez a kódrészlet beállítja a dokumentumkönyvtár elérési útját, és betölti az adott dokumentumot, amelyen dolgozni szeretne. Győződjön meg arról, hogy a dokumentum elérési útja helyes, hogy elkerülje a betöltési problémákat.

## 2. lépés: Nyissa meg a táblázatot

Ezután el kell érnünk a dokumentumon belüli táblázatot. Általában a törzsrész első táblázatával szeretne dolgozni.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Ez a kódsor lekéri az első táblázatot a dokumentum törzséből. Ha a dokumentum több táblázatot tartalmaz, ennek megfelelően módosíthatja az indexet.

## 3. lépés: Állítsa be a vízszintes pozíciót

Most állítsuk be a táblázat vízszintes helyzetét egy adott elemhez képest. Ebben a példában az oszlophoz viszonyítva helyezzük el.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

 Beállításával a`HorizontalAnchor` hogy`RelativeHorizontalPosition.Column`, akkor azt mondja a táblázatnak, hogy vízszintesen igazodjon ahhoz az oszlophoz, amelyben található.

## 4. lépés: Állítsa be a függőleges pozíciót

A vízszintes pozicionáláshoz hasonlóan a függőleges helyzetet is beállíthatja. Itt az oldalhoz viszonyítva helyezzük el.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

 Beállítása a`VerticalAnchor` hogy`RelativeVerticalPosition.Page` biztosítja, hogy a táblázat az oldalnak megfelelően függőlegesen legyen igazítva.

## 5. lépés: Mentse el a dokumentumot

Végül mentse a módosításokat egy új dokumentumba. Ez egy döntő lépés a változtatások megőrzéséhez.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Ez a parancs új néven menti a módosított dokumentumot, biztosítva, hogy ne írja felül az eredeti fájlt.

## Következtetés

És megvan! Sikeresen beállította egy táblázat relatív vízszintes és függőleges helyzetét egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ezzel az újonnan megismert képességgel javíthatja dokumentumai elrendezését és olvashatóságát, így azok professzionálisabbnak és kifinomultabbnak tűnnek. Kísérletezzen tovább a különböző pozíciókkal, és nézze meg, hogy mi a legmegfelelőbb az Ön igényeinek.

## GYIK

### Elhelyezhetem a táblázatokat más elemekhez képest?  
Igen, az Aspose.Words lehetővé teszi a táblázatok különböző elemekhez, például margókhoz, oldalakhoz, oszlopokhoz és egyebekhez való viszonyítását.

### Szükségem van licencre az Aspose.Words for .NET használatához?  
 Igen, vásárolhat licencet[itt](https://purchase.aspose.com/buy) vagy ideiglenes engedélyt szerezni[itt](https://purchase.aspose.com/temporary-license/).

### Létezik ingyenes próbaverzió az Aspose.Words for .NET számára?  
 Teljesen! Letölthet egy ingyenes próbaverziót[itt](https://releases.aspose.com/).

### Használhatom az Aspose.Words programot más programozási nyelvekkel?  
Az Aspose.Words elsősorban .NET-hez készült, de vannak verziók Java, Python és más platformokra is.

### Hol találok részletesebb dokumentációt?  
Részletesebb információkért tekintse meg az Aspose.Words dokumentációját[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

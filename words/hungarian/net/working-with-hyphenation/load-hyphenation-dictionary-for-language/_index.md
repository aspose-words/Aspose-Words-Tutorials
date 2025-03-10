---
title: Elválasztási szótár betöltése a nyelvhez
linktitle: Elválasztási szótár betöltése a nyelvhez
second_title: Aspose.Words Document Processing API
description: Ebből az átfogó, lépésenkénti oktatóanyagból megtudhatja, hogyan tölthet be elválasztási szótárt bármely nyelvhez az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/working-with-hyphenation/load-hyphenation-dictionary-for-language/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Elválasztási szótár betöltése a nyelvhez

## Bevezetés

Küszködött már ezekkel a bosszantó elválasztási problémákkal a Word-dokumentumaiban? Nos, nem vagy egyedül. Az elválasztás megzavarhatja vagy megzavarhatja a szöveg olvashatóságát, különösen az összetett elválasztási szabályokkal rendelkező nyelveken. Ne félj! Az Aspose.Words for .NET gondoskodik róla. Ez az oktatóanyag végigvezeti Önt egy adott nyelvhez tartozó elválasztási szótár betöltésének folyamatán, így biztosítva, hogy a dokumentumok kidolgozottnak és professzionálisnak tűnjenek. Merüljünk el!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

- A Visual Studio telepítve van a számítógépére.
- .NET keretrendszer telepítve.
-  Aspose.Words a .NET könyvtárhoz. Ha még nem telepítette, letöltheti innen[itt](https://releases.aspose.com/words/net/).
- Elválasztási szótárfájl a célnyelvhez. Ebben az oktatóanyagban egy német elválasztási szótárt fogunk használni (`hyph_de_CH.dic`).
- Word dokumentum minta a célnyelven. nevű dokumentumot fogunk használni`German text.docx`.

## Névterek importálása

Először is importálnia kell a szükséges névtereket a projektbe. Íme, hogyan kell csinálni:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Hyphenation;
```

Most bontsuk le a folyamatot könnyen követhető lépésekre.

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Mielőtt elkezdené, meg kell adnia azt a könyvtárat, ahol a dokumentum és az elválasztási szótár található. Ez segít megőrizni a projektet, és a kódot tisztán tartani.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a fájlokat tartalmazó könyvtár elérési útjával.

## 2. lépés: Töltse be a dokumentumot

 Ezután töltse be a feldolgozni kívánt Word-dokumentumot. Ez a`Document` osztály Aspose-tól.Words.

```csharp
Document doc = new Document(dataDir + "German text.docx");
```

 Ez a kódsor inicializál egy újat`Document` objektumot, és betölti a fájlt`German text.docx` a megadott könyvtárból.

## 3. lépés: Nyissa meg az Elválasztási szótárt

 Most meg kell nyitnia az elválasztási szótár fájlt. Használjuk a`File.OpenRead` módszer a szótárfájl adatfolyamként történő olvasásához.

```csharp
Stream stream = File.OpenRead(dataDir + "hyph_de_CH.dic");
```

 Ez a sor megnyitja az elválasztási szótár fájlt`hyph_de_CH.dic` és patakba olvassa.

## 4. lépés: Regisztrálja az Elválasztási szótárt

 A szótárfájl megnyitása után a következő lépés az Aspose.Words-ben való használatra való regisztráció. Ez a`Hyphenation.RegisterDictionary` módszer.

```csharp
Hyphenation.RegisterDictionary("de-CH", stream);
```

Itt regisztráljuk az elválasztási szótárt a`de-CH` (svájci német) nyelv.

## 5. lépés: Mentse el a dokumentumot

Végül mentse el a feldolgozott dokumentumot. Bármelyik formátumot kiválaszthatja, de ehhez az oktatóanyaghoz PDF formátumban mentjük el.

```csharp
doc.Save(dataDir + "ProcessingByBreakingWithDictionary.pdf");
```

 Ez a sor menti a dokumentumot a megadott könyvtárba a fájlnévvel`ProcessingByBreakingWithDictionary.pdf`.

## Következtetés

Megvan! Sikeresen betöltött egy elválasztási szótárt egy adott nyelvhez az Aspose.Words for .NET használatával. Ez a kicsi, de nagy teljesítményű funkció jelentősen javíthatja dokumentumai olvashatóságát és professzionalizmusát. Most pedig próbálja ki különböző nyelveken, és nézze meg a varázslatot saját szemével!

## GYIK

### Mi az az elválasztási szótár?

Az elválasztási szótár olyan fájl, amely szabályokat tartalmaz a szavak megfelelő pontokon történő törésére, a szöveg elrendezésének és olvashatóságának javítására.

### Hol találok elválasztási szótárakat?

Az interneten található elválasztási szótárak, amelyeket gyakran nyelvi vagy nyílt forráskódú szervezetek biztosítanak. Győződjön meg arról, hogy az Aspose.Words formátummal kompatibilis formátumban vannak.

### Használhatom ezt a módszert más nyelvekhez?

Igen, a megfelelő nyelvi kód és szótárfájl megadásával regisztrálhat elválasztási szótárakat különböző nyelvekhez.

### Milyen fájlformátumokba mentheti az Aspose.Words?

Az Aspose.Words támogatja a dokumentumok különböző formátumokba, köztük PDF, DOCX, DOC, HTML és sok más formátumba történő mentését.

### Szükségem van engedélyre az Aspose.Words használatához?

 Igen, az Aspose.Words teljes funkcióihoz licenc szükséges. Vásárolhat licencet[itt](https://purchase.aspose.com/buy) vagy ideiglenes engedélyt szerezni[itt](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

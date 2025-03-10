---
title: Szöveg vízjel hozzáadása meghatározott beállításokkal
linktitle: Szöveg vízjel hozzáadása meghatározott beállításokkal
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan adhat szöveges vízjelet meghatározott beállításokkal Word-dokumentumaihoz az Aspose.Words for .NET használatával. Egyszerűen testreszabhatja a betűtípust, a méretet, a színt és az elrendezést.
weight: 10
url: /hu/net/programming-with-watermark/add-text-watermark-with-specific-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Szöveg vízjel hozzáadása meghatározott beállításokkal

## Bevezetés

vízjelek stílusos és funkcionális kiegészítői lehetnek a Word-dokumentumoknak, a dokumentumok bizalmasként való megjelölésétől a személyre szabott megjelenésig. Ebben az oktatóanyagban megvizsgáljuk, hogyan adhatunk szöveges vízjelet Word-dokumentumokhoz az Aspose.Words for .NET használatával. Megvizsgáljuk a konfigurálható konkrét beállításokat, például a betűcsaládot, a betűméretet, a színt és az elrendezést. A végére személyre szabhatja a dokumentum vízjelét, hogy megfeleljen az Ön igényeinek. Tehát fogd a kódszerkesztőt, és kezdjük is!

## Előfeltételek

Mielőtt elkezdenénk a görgetést, győződjön meg arról, hogy a következők vannak a helyükön:

1.  Aspose.Words for .NET Library: telepítenie kell az Aspose.Words könyvtárat. Ha még nem tette meg, letöltheti a webhelyről[Aspose.Words letöltési link](https://releases.aspose.com/words/net/).
2. A C# alapvető ismerete: Ez az oktatóanyag a C#-t fogja használni programozási nyelvként. A C# szintaxis alapvető ismerete hasznos lesz.
3. .NET fejlesztői környezet: Győződjön meg arról, hogy be van állítva egy fejlesztői környezet (például a Visual Studio), ahol létrehozhatja és futtathatja .NET-alkalmazásait.

## Névterek importálása

Az Aspose.Words használatához a szükséges névtereket bele kell foglalnia a projektbe. A következőket kell importálnia:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## 1. lépés: Állítsa be a dokumentumot

 Először is be kell töltenie azt a dokumentumot, amellyel dolgozni szeretne. Ehhez az oktatóanyaghoz egy mintadokumentumot fogunk használni, melynek neve`Document.docx`. Győződjön meg arról, hogy ez a dokumentum létezik a megadott könyvtárban.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 Ebben a lépésben meghatározza azt a könyvtárat, amelyben a dokumentum található, és betölti a dokumentum példányába`Document` osztály.

## 2. lépés: Konfigurálja a vízjel beállításait

Ezután konfigurálja a szöveges vízjel beállításait. Különféle szempontokat testre szabhat, például a betűcsaládot, a betűméretet, a színt és az elrendezést. Állítsuk be ezeket az opciókat.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Az egyes opciók működése a következő:
- `FontFamily`: Megadja a vízjel szövegének betűtípusát.
- `FontSize`: Beállítja a vízjel szövegének méretét.
- `Color`: Meghatározza a vízjel szövegének színét.
- `Layout`Meghatározza a vízjel tájolását (vízszintes vagy átlós).
- `IsSemitrasparent`: Beállítja, hogy a vízjel félig átlátszó legyen-e.

## 3. lépés: Adja hozzá a vízjel szövegét

Most alkalmazza a vízjelet a dokumentumra a korábban beállított beállításokkal. Ebben a lépésben a vízjel szövegét „Teszt” értékre állítja, és alkalmazza a megadott beállításokat.

```csharp
doc.Watermark.SetText("Test", options);
```

Ez a kódsor hozzáadja a „Teszt” szövegű vízjelet a dokumentumhoz, a megadott beállítások alkalmazásával.

## 4. lépés: Mentse el a dokumentumot

Végül mentse el a dokumentumot az új vízjellel. Elmentheti új néven, hogy elkerülje az eredeti dokumentum felülírását.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Ez a kódrészlet ugyanabba a könyvtárba menti a módosított dokumentumot új fájlnévvel.

## Következtetés

Szöveges vízjel hozzáadása a Word-dokumentumokhoz az Aspose.Words for .NET használatával egyszerű folyamat, ha kezelhető lépésekre bontja. Az oktatóanyag követésével megtanulta, hogyan konfigurálhat különféle vízjel-beállításokat, beleértve a betűtípust, a méretet, a színt, az elrendezést és az átlátszóságot. Ezekkel a készségekkel most személyre szabhatja dokumentumait, hogy jobban megfeleljenek igényeinek, vagy olyan alapvető információkat tartalmazzon, mint például a titoktartás vagy a márkaépítés.

 Ha bármilyen kérdése van, vagy további segítségre van szüksége, bátran nézze meg a[Aspose.Words Dokumentáció](https://reference.aspose.com/words/net/) vagy látogassa meg a[Aspose támogatási fórum](https://forum.aspose.com/c/words/8) további segítségért.

## GYIK

### Használhatok különböző betűtípusokat a vízjelhez?

 Igen, a rendszerre telepített bármely betűtípust kiválaszthatja a`FontFamily` ingatlan a`TextWatermarkOptions`.

### Hogyan változtathatom meg a vízjel színét?

 A vízjel színét a beállításával módosíthatja`Color` ingatlan a`TextWatermarkOptions` bármelyikhez`System.Drawing.Color` érték.

### Lehetséges több vízjelet hozzáadni egy dokumentumhoz?

Az Aspose.Words egyszerre támogatja egy vízjel hozzáadását. Több vízjel hozzáadásához egymás után kell létrehoznia és alkalmaznia azokat.

### Beállíthatom a vízjel helyzetét?

 A`WatermarkLayout`tulajdonság határozza meg a tájolást, de a pontos pozicionálási beállítások közvetlenül nem támogatottak. Előfordulhat, hogy a pontos elhelyezéshez más technikákat kell alkalmaznia.

### Mi a teendő, ha félig átlátszó vízjelre van szükségem?

 Állítsa be a`IsSemitrasparent`tulajdonát`true` hogy a vízjel félig átlátszó legyen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

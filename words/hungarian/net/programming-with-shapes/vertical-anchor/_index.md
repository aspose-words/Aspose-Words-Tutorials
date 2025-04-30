---
"description": "Tanuld meg, hogyan állíthatsz be függőleges horgonypontokat a szövegdobozokhoz Word dokumentumokban az Aspose.Words for .NET segítségével. Egyszerű, lépésről lépésre útmutató mellékelve."
"linktitle": "Függőleges horgony"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Függőleges horgony"
"url": "/hu/net/programming-with-shapes/vertical-anchor/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Függőleges horgony

## Bevezetés

Előfordult már veled, hogy pontosan szabályoznod kellett, hol jelenjen meg a szöveg egy Word-dokumentum szövegdobozában? Talán azt szeretnéd, hogy a szöveg a szövegdoboz tetejére, közepére vagy aljára legyen lehorgonyozva? Ha igen, akkor jó helyen jársz! Ebben az oktatóanyagban megvizsgáljuk, hogyan használható az Aspose.Words for .NET a Word-dokumentumok szövegdobozainak függőleges horgonya beállításához. A függőleges horgonyzásra úgy gondolj, mint egy varázspálcára, amely pontosan oda pozicionálja a szöveget, ahová szeretnéd a tárolóban. Készen állsz a belevágni? Kezdjük is!

## Előfeltételek

Mielőtt belemerülnénk a függőleges rögzítés részleteibe, néhány dolgot tisztáznunk kell:

1. Aspose.Words for .NET: Győződjön meg róla, hogy telepítve van az Aspose.Words for .NET könyvtár. Ha még nem telepítette, megteheti [töltsd le itt](https://releases.aspose.com/words/net/).
2. Visual Studio: Ez az oktatóanyag feltételezi, hogy Visual Studio-t vagy más .NET IDE-t használsz kódoláshoz.
3. C# alapismeretek: A C# és a .NET ismerete segít majd a gördülékeny haladásban.

## Névterek importálása

A kezdéshez importálnod kell a szükséges névtereket a C# kódodba. Itt tudod megadni az alkalmazásodnak, hogy hol találja a használandó osztályokat és metódusokat. Így csináld:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Ezek a névterek biztosítják azokat az osztályokat, amelyekre szükséged lesz a dokumentumokkal és alakzatokkal való munkához.

## 1. lépés: A dokumentum inicializálása

Először is létre kell hoznod egy új Word-dokumentumot. Gondolj erre úgy, mintha előkészítenéd a vászonodat, mielőtt elkezdenél festeni.

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Itt, `Document` az üres vászon, és `DocumentBuilder` az ecseted, amellyel formákat és szöveget adhatsz hozzá.

## 2. lépés: Szövegdoboz alakzat beszúrása

Most adjunk hozzá egy szövegdobozt a dokumentumunkhoz. Ide fog kerülni a szöveg. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

Ebben a példában `ShapeType.TextBox` megadja a kívánt formát, és `200, 200` a szövegdoboz szélessége és magassága pontokban megadva.

## 3. lépés: A függőleges horgony beállítása

Itt történik a varázslat! Beállíthatod a szöveg függőleges igazítását a szövegdobozban. Ez meghatározza, hogy a szöveg a szövegdoboz tetejéhez, közepéhez vagy aljához legyen-e rögzítve.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

Ebben az esetben `TextBoxAnchor.Bottom` biztosítja, hogy a szöveg a szövegdoboz aljához legyen rögzítve. Ha középre vagy felülre szeretné igazítani, akkor a következőt kell használnia: `TextBoxAnchvagy.Center` or `TextBoxAnchor.Top`, rendre.

## 4. lépés: Szöveg hozzáadása a szövegmezőhöz

Most itt az ideje, hogy tartalmat adj a szövegdobozodhoz. Gondolj erre úgy, mintha az utolsó simításokkal kitöltenéd a vásznat.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

Itt, `MoveTo` biztosítja, hogy a szöveg bekerüljön a szövegmezőbe, és `Write` hozzáadja a tényleges szöveget.

## 5. lépés: A dokumentum mentése

Az utolsó lépés a dokumentum mentése. Ez olyan, mintha a kész festményt bekereteznéd.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Következtetés

És tessék! Most megtanultad, hogyan szabályozhatod a szöveg függőleges igazítását egy Word dokumentum szövegdobozában az Aspose.Words for .NET segítségével. Akár felülre, középre vagy alulra rögzíted a szöveget, ez a funkció pontos irányítást biztosít a dokumentum elrendezése felett. Így legközelebb, amikor módosítanod kell a dokumentum szövegének elhelyezését, pontosan tudni fogod, mit kell tenned!

## GYIK

### Mi a függőleges horgonyzás egy Word dokumentumban?
A függőleges horgonyzás szabályozza a szöveg elhelyezkedését a szövegdobozban, például felülre, középre vagy alulra igazítást.

### Használhatok más alakzatokat is a szövegdobozokon kívül?
Igen, más alakzatokkal is használhat függőleges lehorgonyzást, bár a szövegdobozok a leggyakoribb felhasználási eset.

### Hogyan tudom megváltoztatni a horgonypontot a szövegdoboz létrehozása után?
A rögzítési pontot a következő beállítással módosíthatja: `VerticalAnchor` tulajdonság a szövegdoboz alakú objektumon.

### Lehetséges szöveget a szövegdoboz közepére horgonyozni?
Feltétlenül! Csak használd `TextBoxAnchor.Center` szöveg függőleges középre igazítása a szövegmezőn belül.

### Hol találok további információt az Aspose.Words for .NET-ről?
Nézd meg a [Aspose.Words dokumentáció](https://reference.aspose.com/words/net/) további részletekért és útmutatókért.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
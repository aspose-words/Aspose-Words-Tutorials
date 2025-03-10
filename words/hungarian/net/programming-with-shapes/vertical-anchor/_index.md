---
title: Függőleges horgony
linktitle: Függőleges horgony
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan állíthat be függőleges rögzítési pozíciókat a Word dokumentumok szövegdobozaihoz az Aspose.Words for .NET használatával. Könnyű, lépésről lépésre útmutatót tartalmaz.
weight: 10
url: /hu/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Függőleges horgony

## Bevezetés

Előfordult már, hogy szüksége van arra, hogy pontosan szabályozza, hol jelenjen meg a szöveg egy Word-dokumentum szövegdobozában? Talán azt szeretné, hogy a szöveg a szövegdoboz tetejéhez, közepéhez vagy aljához rögzítve legyen? Ha igen, akkor jó helyen jársz! Ebben az oktatóanyagban megvizsgáljuk, hogyan használható az Aspose.Words for .NET a Word dokumentumok szövegdobozainak függőleges rögzítésére. A függőleges rögzítést úgy képzelje el, mint egy varázspálcát, amely pontosan oda helyezi a szöveget a tárolójában, ahol szeretné. Készen állsz a merülésre? Kezdjük is!

## Előfeltételek

Mielőtt belemerülnénk a függőleges rögzítés anyáiba és csavarjaiba, néhány dolgot a helyére kell tennie:

1.  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van az Aspose.Words for .NET könyvtár. Ha még nincs meg, megteheti[töltse le itt](https://releases.aspose.com/words/net/).
2. Visual Studio: Ez az oktatóanyag azt feltételezi, hogy Visual Studiót vagy egy másik .NET IDE-t használ a kódoláshoz.
3. Alapvető C# ismerete: A C# és a .NET ismerete segít a zökkenőmentes követésben.

## Névterek importálása

kezdéshez importálnia kell a szükséges névtereket a C# kódba. Itt adja meg az alkalmazásának, hogy hol találja meg a használni kívánt osztályokat és metódusokat. Íme, hogyan kell csinálni:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Ezek a névterek biztosítják a dokumentumokkal és alakzatokkal való munkavégzéshez szükséges osztályokat.

## 1. lépés: Inicializálja a dokumentumot

Először is létre kell hoznia egy új Word-dokumentumot. Gondoljon erre úgy, mint a vászon felállítására a festés megkezdése előtt.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Itt,`Document` az üres vászon, és`DocumentBuilder` az ecset, amely lehetővé teszi formák és szövegek hozzáadását.

## 2. lépés: Szúrjon be egy szövegdoboz alakzatot

Most adjunk hozzá egy szövegdobozt a dokumentumunkhoz. Itt fog élni a szöveged. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 Ebben a példában`ShapeType.TextBox` megadja a kívánt alakzatot, és`200, 200` a szövegdoboz szélessége és magassága pontokban.

## 3. lépés: Állítsa be a függőleges horgonyt

Itt történik a varázslat! A szövegmezőn belül beállíthatja a szöveg függőleges igazítását. Ez határozza meg, hogy a szöveg a szövegdoboz tetejéhez, közepéhez vagy aljához van-e rögzítve.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 Ebben az esetben`TextBoxAnchor.Bottom`biztosítja, hogy a szöveg a szövegdoboz aljához rögzítve legyen. Ha azt szeretné, hogy középre vagy a tetejére igazodjon, akkor használja`TextBoxAnchor.Center` vagy`TextBoxAnchor.Top`, ill.

## 4. lépés: Szöveg hozzáadása a szövegdobozhoz

Itt az ideje, hogy egy kis tartalmat adjon a szövegdobozhoz. Tekintsd úgy, mintha az utolsó simításokkal kitöltenéd a vásznodat.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Itt,`MoveTo` biztosítja, hogy a szöveg bekerüljön a szövegdobozba, és`Write` hozzáadja a tényleges szöveget.

## 5. lépés: Mentse el a dokumentumot

Az utolsó lépés a dokumentum mentése. Ez olyan, mintha a kész festményt egy keretbe helyezné.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Következtetés

És megvan! Most tanulta meg, hogyan szabályozhatja a szöveg függőleges igazítását egy Word-dokumentum szövegdobozában az Aspose.Words for .NET segítségével. Függetlenül attól, hogy felül, középen vagy alul rögzíti a szöveget, ezzel a funkcióval pontosan szabályozhatja a dokumentum elrendezését. Így ha legközelebb módosítania kell a dokumentum szövegének elhelyezésén, tudni fogja, mit kell tennie!

## GYIK

### Mit jelent a függőleges rögzítés egy Word-dokumentumban?
Függőleges rögzítési vezérlők, ahol a szöveg a szövegmezőn belül helyezkedik el, például felső, középső vagy alsó igazítás.

### Használhatok más alakzatokat a szövegdobozokon kívül?
Igen, használhat függőleges rögzítést más alakzatokkal is, bár a szövegdobozok a leggyakoribb felhasználási esetek.

### Hogyan változtathatom meg a rögzítési pontot a szövegdoboz létrehozása után?
 A rögzítési pontot a beállításával módosíthatja`VerticalAnchor` tulajdonság a szövegdoboz alakzat objektumon.

### Lehet-e szöveget a szövegdoboz közepéhez rögzíteni?
 Teljesen! Csak használd`TextBoxAnchor.Center` hogy a szöveget függőlegesen középre állítsa a szövegdobozban.

### Hol találhatok további információt az Aspose.Words for .NET-ről?
 Nézze meg a[Aspose.Words Dokumentáció](https://reference.aspose.com/words/net/) további részletekért és útmutatókért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

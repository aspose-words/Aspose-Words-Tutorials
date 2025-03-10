---
title: Beágyazott mezők beszúrása
linktitle: Beágyazott mezők beszúrása
second_title: Aspose.Words Document Processing API
description: lépésenkénti útmutatónkból megtudhatja, hogyan illeszthet be beágyazott mezőket Word dokumentumokba az Aspose.Words for .NET használatával. Tökéletes azoknak a fejlesztőknek, akik automatizálják a dokumentumkészítést.
weight: 10
url: /hu/net/working-with-fields/insert-nested-fields/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Beágyazott mezők beszúrása

## Bevezetés

Előfordult már, hogy beágyazott mezőket kell programozottan beszúrnia Word-dokumentumaiba? Esetleg az oldalszám alapján szeretne feltételesen különböző szövegeket megjeleníteni? Nos, szerencséd van! Ez az oktatóanyag végigvezeti a beágyazott mezők beszúrásának folyamatán az Aspose.Words for .NET használatával. Merüljünk el!

## Előfeltételek

Mielőtt elkezdenénk, van néhány dolog, amire szüksége lesz:

1.  Aspose.Words for .NET: Győződjön meg arról, hogy rendelkezik az Aspose.Words for .NET könyvtárral. Letöltheti innen[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Egy IDE, mint a Visual Studio.
3. C# alapismeretek: C# programozási nyelv ismerete.

## Névterek importálása

Először győződjön meg róla, hogy importálja a szükséges névtereket a projektbe. Ezek a névterek olyan osztályokat tartalmaznak, amelyekre szüksége lesz az Aspose.Words használatához.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.HeaderFooter;
```

## 1. lépés: Inicializálja a dokumentumot

Az első lépés egy új dokumentum és egy DocumentBuilder objektum létrehozása. A DocumentBuilder osztály segít a Word dokumentumok létrehozásában és módosításában.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Hozza létre a dokumentumot és a DocumentBuildert.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Oldaltörések beszúrása

Ezután beszúrunk néhány oldaltörést a dokumentumba. Ez lehetővé teszi számunkra, hogy hatékonyan demonstráljuk a beágyazott mezőket.

```csharp
// Oldaltörések beszúrása.
for (int i = 0; i < 5; i++)
{
    builder.InsertBreak(BreakType.PageBreak);
}
```

## 3. lépés: Lépjen a láblécre

Az oldaltörések beszúrása után a dokumentum láblécére kell lépnünk. Ide szúrjuk be a beágyazott mezőnket.

```csharp
// Ugrás a láblécre.
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);
```

## 4. lépés: Szúrja be a Beágyazott mezőt

Most illesszük be a beágyazott mezőt. Az IF mezőt használjuk a szöveg feltételes megjelenítésére az aktuális oldalszám alapján.

```csharp
// Beágyazott mező beszúrása.
Field field = builder.InsertField(@"IF ");
builder.MoveTo(field.Separator);
builder.InsertField("PAGE");
builder.Write(" <> ");
builder.InsertField("NUMPAGES");
builder.Write(" \"See next page\" \"Last page\" ");
```

Ebben a lépésben először beszúrjuk az IF mezőt, áttérünk az elválasztójára, majd beillesztjük a PAGE és NUMPAGES mezőket. A HA mező ellenőrzi, hogy az aktuális oldalszám (PAGE) nem egyenlő-e az összes oldalszámmal (NUMPAGES). Ha igaz, akkor megjelenik a „Lásd a következő oldalt”, ellenkező esetben az „Utolsó oldal”.

## 5. lépés: Frissítse a mezőt

Végül frissítjük a mezőt, hogy a megfelelő szöveget jelenítse meg.

```csharp
// Frissítse a mezőt.
field.Update();
```

## 6. lépés: Mentse el a dokumentumot

Az utolsó lépés a dokumentum mentése a megadott könyvtárba.

```csharp
doc.Save(dataDir + "InsertNestedFields.docx");
```

## Következtetés

És megvan! Sikeresen beszúrta a beágyazott mezőket egy Word-dokumentumba az Aspose.Words for .NET használatával. Ez a nagy teljesítményű könyvtár hihetetlenül egyszerűvé teszi a Word-dokumentumok programozott kezelését. Akár jelentéseket készít, akár sablonokat hoz létre, vagy automatizálja a dokumentum-munkafolyamatokat, az Aspose.Words mindent megtesz.

## GYIK

### Mi az a beágyazott mező a Word dokumentumokban?
A beágyazott mező olyan mező, amely más mezőket tartalmaz. Bonyolultabb és feltételes tartalmat tesz lehetővé a dokumentumokban.

### Használhatok más mezőket az IF mezőn belül?
Igen, dinamikus tartalom létrehozásához különféle mezőket, például DÁTUM, IDŐ és SZERZŐ ágyazhat be a HA mezőbe.

### Az Aspose.Words for .NET ingyenes?
 Az Aspose.Words for .NET egy kereskedelmi könyvtár, de beszerezheti a[ingyenes próbaverzió](https://releases.aspose.com/) hogy kipróbáljam.

### Használhatom az Aspose.Words programot más .NET nyelvekkel?
Igen, az Aspose.Words támogatja az összes .NET nyelvet, beleértve a VB.NET-et és az F#-t is.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?
 Részletes dokumentációt találhat[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

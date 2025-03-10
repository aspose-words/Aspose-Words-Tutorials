---
title: A jelölőnégyzet jelenlegi állapota
linktitle: A jelölőnégyzet jelenlegi állapota
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan kezelheti a jelölőnégyzeteket a Word dokumentumokban az Aspose.Words for .NET segítségével. Ez az útmutató a jelölőnégyzetek programozott beállításával, frissítésével és mentésével foglalkozik.
weight: 10
url: /hu/net/programming-with-sdt/current-state-of-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# A jelölőnégyzet jelenlegi állapota

## Bevezetés

Ebben az oktatóanyagban végigvezetjük a Word-dokumentumok jelölőnégyzeteinek kezelését. Megmutatjuk, hogyan lehet elérni egy jelölőnégyzetet, meghatározni az állapotát, és ennek megfelelően frissíteni. Akár olyan űrlapot fejleszt, amely ellenőrizhető opciókat igényel, akár automatizálja a dokumentummódosításokat, ez az útmutató szilárd alapot nyújt Önnek.

## Előfeltételek

Mielőtt belevágnánk az oktatóanyagba, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:

1.  Aspose.Words for .NET Library: Győződjön meg arról, hogy telepítve van az Aspose.Words könyvtár. Ha még nem tette meg, letöltheti a webhelyről[Aspose honlapja](https://releases.aspose.com/words/net/).

2. Visual Studio: A kód fordításához és futtatásához .NET fejlesztői környezetre lesz szükség, mint például a Visual Studio.

3. Alapvető C# ismerete: A C# programozás ismerete segít megérteni és követni a példákat.

4. Word-dokumentum jelölőnégyzetekkel: Ehhez az oktatóanyaghoz szüksége lesz egy Word dokumentumra, amely jelölőnégyzetes űrlapmezőket tartalmaz. Ezt a dokumentumot a jelölőnégyzetek programozott kezelésének bemutatására fogjuk használni.

## Névterek importálása

Az Aspose.Words for .NET használatának megkezdéséhez importálnia kell a szükséges névtereket. A C# fájl elejére írja be a következőket direktívák használatával:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Ezek a névterek lehetővé teszik az Aspose.Words API elérését és használatát, valamint a strukturált dokumentumcímkék kezelését, beleértve a jelölőnégyzeteket is.

## 1. lépés: A dokumentum elérési útjának beállítása

 Először is meg kell adnia a Word-dokumentum elérési útját. Az Aspose.Words itt keresi a fájlt a műveletek végrehajtásához. Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a tényleges elérési úttal, ahol a dokumentumot tárolják.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: A dokumentum betöltése

 Ezután töltse be a Word dokumentumot a`Document` osztály. Ez az osztály kódban jeleníti meg a Word-dokumentumot, és különféle módszereket kínál a kezeléséhez.

```csharp
Document doc = new Document(dataDir + "Structured document tags.docx");
```

 Itt,`"Structured document tags.docx"` le kell cserélni a Word fájl nevére.

## 3. lépés: A jelölőnégyzet űrlapmezőjének elérése

Egy adott jelölőnégyzet eléréséhez le kell kérnie azt a dokumentumból. Az Aspose.Words a jelölőnégyzeteket strukturált dokumentumcímkeként kezeli. A következő kód lekéri a dokumentum első strukturált dokumentumcímkéjét, és ellenőrzi, hogy az egy jelölőnégyzet-e.

```csharp
//Szerezze be az első tartalomvezérlőt a dokumentumból.
StructuredDocumentTag sdtCheckBox =
    (StructuredDocumentTag) doc.GetChild(NodeType.StructuredDocumentTag, 0, true);
```

## 4. lépés: A jelölőnégyzet állapotának ellenőrzése és frissítése

 Ha egyszer megvan a`StructuredDocumentTag` Például ellenőrizheti a típusát és frissítheti az állapotát. Ez a példa a jelölőnégyzetet bejelölve állítja be, ha valóban jelölőnégyzet.

```csharp
if (sdtCheckBox.SdtType == SdtType.Checkbox)
    sdtCheckBox.Checked = true;
```

## 5. lépés: A dokumentum mentése

Végül mentse a módosított dokumentumot egy új fájlba. Ez lehetővé teszi az eredeti dokumentum megőrzését és a frissített verzió használatát.

```csharp
doc.Save(dataDir + "WorkingWithSdt.CurrentStateOfCheckBox.docx");
```

 Ebben a példában`"WorkingWithSdt.CurrentStateOfCheckBox.docx"` annak a fájlnak a neve, amelybe a módosított dokumentum mentésre kerül.

## Következtetés

Ebben az oktatóanyagban bemutattuk, hogyan kezelheti a jelölőnégyzet űrlapmezőit a Word dokumentumokban az Aspose.Words for .NET használatával. Megvizsgáltuk, hogyan állíthatjuk be a dokumentum elérési útját, tölthetjük be a dokumentumot, hogyan lehet hozzáférni a jelölőnégyzetekhez, frissíteni az állapotukat és menteni a változtatásokat. Ezekkel a készségekkel most már több interaktív és dinamikus Word-dokumentumot hozhat létre programozottan.

## GYIK

### Milyen típusú dokumentumelemeket kezelhetek az Aspose.Words for .NET segítségével?
Az Aspose.Words for .NET lehetővé teszi különféle dokumentumelemek, köztük bekezdések, táblázatok, képek, fejlécek, láblécek és strukturált dokumentumcímkék, például jelölőnégyzetek kezelését.

### Hogyan kezelhetek több jelölőnégyzetet egy dokumentumban?
Több jelölőnégyzet kezeléséhez át kell tekintenie a strukturált dokumentumcímkék gyűjteményét, és mindegyiket be kell jelölnie, hogy eldöntse, jelölőnégyzet-e.

### Használhatom az Aspose.Words for .NET alkalmazást új jelölőnégyzetek létrehozására egy Word-dokumentumban?
 Igen, létrehozhat új jelölőnégyzeteket a típusú strukturált dokumentumcímkék hozzáadásával`SdtType.Checkbox` a dokumentumához.

### Kiolvasható egy jelölőnégyzet állapota egy dokumentumból?
 Teljesen. A jelölőnégyzet állapotát a`Checked` tulajdona a`StructuredDocumentTag` ha olyan típusú`SdtType.Checkbox`.

### Hogyan szerezhetek ideiglenes licencet az Aspose.Words for .NET-hez?
 Ideiglenes engedélyt szerezhet a[Aspose vásárlási oldal](https://purchase.aspose.com/temporary-license/), amely lehetővé teszi a könyvtár teljes funkcionalitásának értékelését.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
title: Indítsa újra a lista számát
linktitle: Indítsa újra a lista számát
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan indíthatja újra a listaszámokat a Word dokumentumokban az Aspose.Words for .NET használatával. Ez a részletes, 2000 szavas útmutató mindent tartalmaz, amit tudnia kell, a beállítástól a speciális testreszabásig.
weight: 10
url: /hu/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Indítsa újra a lista számát

## Bevezetés

Szeretné elsajátítani a listakezelés művészetét Word-dokumentumaiban az Aspose.Words for .NET használatával? Nos, jó helyen jársz! Ebben az oktatóanyagban a listaszámok újraindításába fogunk belemerülni, egy remek funkcióba, amely a dokumentumautomatizálási készségeit a következő szintre emeli. Kapcsold be, és kezdjük is!

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjünk meg arról, hogy mindennel rendelkezik, amire szüksége van:

1.  Aspose.Words for .NET: Az Aspose.Words for .NET-re telepítve kell lennie. Ha még nem telepítette, megteheti[töltse le itt](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Győződjön meg arról, hogy megfelelő fejlesztői környezettel rendelkezik, például a Visual Studio.
3. Alapvető C# ismerete: A C# alapvető ismerete segít az oktatóanyag követésében.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ezek kulcsfontosságúak az Aspose.Words funkciók eléréséhez.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Most bontsuk le a folyamatot könnyen követhető lépésekre. A lista létrehozásától a számozás újraindításáig mindenre kiterjedünk.

## 1. lépés: Állítsa be a dokumentumot és a Buildert

Mielőtt elkezdené a listák kezelését, szüksége van egy dokumentumra és egy DocumentBuilderre. A DocumentBuilder egy olyan eszköz, amellyel tartalmat adhat a dokumentumhoz.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Az első lista létrehozása és testreszabása

Ezután létrehozunk egy listát egy sablon alapján, és testreszabjuk a megjelenését. Ebben a példában az arab számformátumot használjuk zárójelekkel.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Itt a betűszínt pirosra állítottuk, és a szöveget jobbra igazítottuk.

## 3. lépés: Tételek hozzáadása az első listához

 A lista elkészültével ideje hozzáadni néhány elemet. A DocumentBuilder`ListFormat.List` tulajdonság segít a listaformátum alkalmazásában a szövegben.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## 4. lépés: Indítsa újra a listaszámozást

A lista újrafelhasználásához és a számozás újraindításához létre kell hoznia egy másolatot az eredeti listáról. Ez lehetővé teszi az új lista önálló módosítását.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

Ebben a példában az új lista a 10-es számmal kezdődik.

## 5. lépés: Tételek hozzáadása az új listához

Csakúgy, mint korábban, adjon hozzá elemeket az új listához. Ez azt mutatja, hogy a lista újraindul a megadott számmal.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## 6. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Következtetés

A listaszámok újraindítása a Word dokumentumokban az Aspose.Words for .NET használatával egyszerű és hihetetlenül hasznos. Akár jelentéseket készít, akár strukturált dokumentumokat hoz létre, vagy egyszerűen csak jobb irányításra van szüksége a listák felett, ez a technika megfelel Önnek.

## GYIK

### Használhatok más listasablonokat a NumberArabicParenthesis mellett?

Teljesen! Az Aspose.Words különféle listasablonokat kínál, például golyókat, betűket, római számokat stb. Kiválaszthatja az igényeinek leginkább megfelelőt.

### Hogyan változtathatom meg a lista szintjét?

 A lista szintjét módosíthatja a`ListLevels` ingatlan. Például,`list1.ListLevels[1]` a lista második szintjére utalna.

### Bármely számnál újraindíthatom a számozást?

 Igen, a kezdő számot tetszőleges egész számra állíthatja a gombbal`StartAt` listaszint tulajdonsága.

### Lehetséges-e különböző formázás a különböző listaszintekhez?

Valóban! Minden listaszintnek saját formázási beállításai lehetnek, például betűtípus, igazítás és számozási stílus.

### Mi a teendő, ha az újraindítás helyett folytatni szeretném a számozást egy korábbi listáról?

Ha folytatni szeretné a számozást, nem kell másolatot készítenie a listáról. Egyszerűen folytassa az elemek hozzáadását az eredeti listához.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

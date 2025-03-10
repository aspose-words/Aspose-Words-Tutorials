---
title: Kétirányú jelek hozzáadása a Word dokumentumhoz
linktitle: Kétirányú jelek hozzáadása a Word dokumentumhoz
second_title: Aspose.Words Document Processing API
description: Ebből az útmutatóból megtudhatja, hogyan adhat kétirányú (kétirányú) jelöléseket Word-dokumentumokhoz az Aspose.Words for .NET használatával. Gondoskodjon a többnyelvű tartalom megfelelő szövegirányáról.
weight: 10
url: /hu/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kétirányú jelek hozzáadása a Word dokumentumhoz

## Bevezetés

A dokumentumfeldolgozás világában a kétirányú (Bidi) szöveg kezelése gyakran kissé körülményes lehet. Ez különösen igaz, ha olyan nyelvekkel foglalkozunk, amelyeknek különböző szövegirányai vannak, mint például az arab vagy a héber. Szerencsére az Aspose.Words for .NET megkönnyíti az ilyen helyzetek kezelését. Ebben az oktatóanyagban végigvezetjük, hogyan adhatunk kétirányú jeleket egy Word-dokumentumhoz az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy rendelkezik a következőkkel:

1. Aspose.Words for .NET: Az Aspose.Words for .NET-re telepítve kell lennie. Letöltheti a[Aspose Letöltések oldal](https://releases.aspose.com/words/net/).
2. .NET Framework vagy .NET Core: Győződjön meg arról, hogy a példák futtatásához kompatibilis .NET-környezet van beállítva.
3. Alapszintű C# ismerete: C# programozási nyelv és alapvető műveletek ismerete .NET-ben.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket. A következőképpen veheti fel őket a projektjébe:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Bontsuk le a kétirányú jelölések Word-dokumentumban történő hozzáadásának folyamatát egyértelmű lépésekre. Minden lépés végigvezeti Önt a kódon és annak célján.

## 1. lépés: Állítsa be a dokumentumot

 Kezdje azzal, hogy hozzon létre egy új példányt a`Document` osztály és a`DocumentBuilder` tartalom hozzáadásához a dokumentumhoz.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Hozzon létre egy dokumentumot, és adjon hozzá tartalmat
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ebben a lépésben inicializál egy új Word-dokumentumot, és beállítja a`DocumentBuilder` a tartalom beillesztésének megkönnyítése érdekében.

## 2. lépés: Adjon hozzá tartalmat a dokumentumhoz

Ezután adjon hozzá szöveget a dokumentumhoz. Itt különböző nyelvű szövegeket adunk hozzá a kétirányú szövegkezelés illusztrálására.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Itt először hozzáadunk egy szabványos angol kifejezést. Ezután engedélyezzük a kétirányú szövegformázást a következő, héber és arab nyelven írt szöveghez. Ez bemutatja, hogyan lehet kétirányú szöveget beépíteni.

## 3. lépés: Konfigurálja a Bidi Marks mentési beállításait

 Annak érdekében, hogy a kétirányú jelölések helyesen legyenek elmentve a dokumentumban, konfigurálnia kell a`TxtSaveOptions` és engedélyezze a`AddBidiMarks` opció.

```csharp
// Adjon hozzá kétirányú jeleket
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 Ebben a lépésben létrehozunk egy példányt`TxtSaveOptions` és állítsa be a`AddBidiMarks`tulajdonát`true`. Ez biztosítja, hogy a kétirányú jelek szerepeljenek a dokumentum szöveges fájlként történő mentésekor.

## Következtetés

A kétirányú jelölések hozzáadása a Word-dokumentumokhoz döntő lépés lehet olyan többnyelvű tartalom kezelésekor, amely különböző szövegirányokkal rendelkező nyelveket tartalmaz. Az Aspose.Words for .NET segítségével ez a folyamat egyszerű és hatékony. A fent vázolt lépések követésével biztosíthatja, hogy dokumentumai helyesen jelenítsenek meg kétirányú szöveget, javítva az olvashatóságot és a pontosságot.

## GYIK

### Mik azok a bidi jelek és miért fontosak?
A kétirányú jelek speciális karakterek, amelyek a szöveg irányának szabályozására szolgálnak a dokumentumokban. Elengedhetetlenek a jobbról balra olvasó nyelvek, például az arab és a héber megfelelő megjelenítéséhez.

### Használhatom az Aspose.Words for .NET-et más típusú szövegirányítási problémák kezelésére?
Igen, az Aspose.Words for .NET átfogó támogatást nyújt a különféle szövegirány- és formázási igényekhez, beleértve a jobbról balra és balról jobbra író nyelveket is.

### Lehetséges-e a kétirányú formázást csak a dokumentum bizonyos részeire alkalmazni?
Igen, szükség szerint alkalmazhatja a kétirányú formázást a dokumentum adott bekezdéseire vagy szakaszaira.

### Milyen formátumokba menthetem a dokumentumot kétirányú jelekkel?
A megadott példában a dokumentum szöveges fájlként van elmentve. Az Aspose.Words azonban támogatja a dokumentumok különféle formátumokban történő mentését is, miközben megőrzi a kétirányú jeleket.

### Hol találhatok további információt az Aspose.Words for .NET-ről?
 Az Aspose.Words for .NET-ről többet megtudhat a következőn keresztül[Aspose Dokumentáció](https://reference.aspose.com/words/net/) és elérje a[Támogatási fórum](https://forum.aspose.com/c/words/8) további segítségért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

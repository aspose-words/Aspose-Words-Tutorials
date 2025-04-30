---
"description": "Tanulja meg, hogyan szúrhat be TOA mezőt dokumentumszerkesztő használata nélkül az Aspose.Words for .NET programban. Kövesse lépésről lépésre szóló útmutatónkat a jogi hivatkozások hatékony kezeléséhez."
"linktitle": "TOA mező beszúrása dokumentumszerkesztő nélkül"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "TOA mező beszúrása dokumentumszerkesztő nélkül"
"url": "/hu/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# TOA mező beszúrása dokumentumszerkesztő nélkül

## Bevezetés

Egy hivatkozásjegyzék (TOA) mező létrehozása egy Word-dokumentumban egy összetett kirakós darab összerakásának tűnhet. Az Aspose.Words for .NET segítségével azonban a folyamat zökkenőmentessé és egyértelművé válik. Ebben a cikkben végigvezetjük Önt a TOA mező dokumentumszerkesztő használata nélküli beszúrásának lépésein, így könnyedén kezelheti az idézeteit és jogi hivatkozásait a Word-dokumentumokban.

## Előfeltételek

Mielőtt belevágnánk az oktatóanyagba, nézzük át a szükséges alapvető dolgokat:

- Aspose.Words .NET-hez: Győződjön meg róla, hogy telepítve van a legújabb verzió. Letöltheti innen: [Aspose weboldal](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Egy .NET-kompatibilis IDE, mint például a Visual Studio.
- C# alapismeretek: A C# alapvető szintaxisának és fogalmainak ismerete hasznos lesz.
- Minta Word-dokumentum: Hozzon létre vagy készítsen elő egy mintadokumentumot oda, ahová be szeretné szúrni a TOA mezőt.

## Névterek importálása

A kezdéshez importálnod kell a szükséges névtereket az Aspose.Words könyvtárból. Ez a beállítás biztosítja, hogy hozzáférj a dokumentumkezeléshez szükséges összes osztályhoz és metódushoz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Bontsuk le a folyamatot egyszerű, könnyen követhető lépésekre. Végigvezetünk minden szakaszon, elmagyarázva, hogy mit csinálnak az egyes kódrészletek, és hogyan járulnak hozzá a TOA mező létrehozásához.

## 1. lépés: A dokumentum inicializálása

Először is létre kell hoznod egy példányt a `Document` osztály. Ez az objektum azt a Word-dokumentumot jelöli, amelyen éppen dolgozik.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Ez a kód inicializál egy új Word-dokumentumot. Úgy is felfoghatod, mintha egy üres vászon lenne, amire majd hozzáadod a tartalmat.

## 2. lépés: A TA mező létrehozása és konfigurálása

Ezután hozzáadunk egy TA (hivatkozások jegyzéke) mezőt. Ez a mező jelöli a TOA-ban megjelenő bejegyzéseket.

```csharp
Paragraph para = new Paragraph(doc);

// A következőhöz hasonló TA és TOA mezőket szeretnénk beszúrni:
// { TA \c 1 \l "Érték 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Íme egy részletezés:
- Bekezdés para = new Bekezdés(doc);: Új bekezdést hoz létre a dokumentumon belül.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: TA mezőt ad a bekezdéshez. A `FieldType.FieldTOAEntry` meghatározza, hogy ez egy TOA beviteli mező.
- fieldTA.EntryCategory = "1";: Beállítja a bejegyzés kategóriáját. Ez hasznos a különböző típusú bejegyzések kategorizálásához.
- fieldTA.LongCitation = "Érték 0";: Megadja a hosszú hivatkozási szöveget. Ez a szöveg fog megjelenni a TOA-ban.
- doc.FirstSection.Body.AppendChild(para);: Hozzáfűzi a TA mezőt tartalmazó bekezdést a dokumentum törzséhez.

## 3. lépés: TOA mező hozzáadása

Most beillesztjük a tényleges TOA mezőt, amely az összes TA bejegyzést egy táblázatba gyűjti.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

Ebben a lépésben:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: TOA mezőt ad a bekezdéshez.
- fieldToa.EntryCategory = "1";: Szűri a bejegyzéseket, hogy csak az "1" kategóriával jelölteket tartalmazzák.

## 4. lépés: A TOA mező frissítése

A TOA mező beillesztése után frissíteni kell, hogy a legújabb bejegyzéseket tükrözze.

```csharp
fieldToa.Update();
```

Ez a parancs frissíti a TOA mezőt, biztosítva, hogy minden megjelölt bejegyzés helyesen jelenjen meg a táblázatban.

## 5. lépés: A dokumentum mentése

Végül mentse el a dokumentumot az újonnan hozzáadott TOA mezővel.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Ez a kódsor a megadott könyvtárba menti a dokumentumot. Ügyeljen arra, hogy a következőt cserélje ki: `"YOUR DOCUMENT DIRECTORY"` a fájl tényleges mentési útvonalával.

## Következtetés

És íme! Sikeresen hozzáadott egy TOA mezőt egy Word-dokumentumhoz dokumentumszerkesztő használata nélkül. A következő lépéseket követve hatékonyan kezelheti a hivatkozásokat, és átfogó hivatkozásjegyzékeket hozhat létre jogi dokumentumaiban. Az Aspose.Words for .NET zökkenőmentessé és hatékonnyá teszi ezt a folyamatot, eszközöket biztosítva az összetett dokumentumfeladatok egyszerű kezeléséhez.

## GYIK

### Hozzáadhatok több TA mezőt különböző kategóriákkal?
Igen, több TA mezőt is hozzáadhat különböző kategóriákkal a beállítással. `EntryCategory` ingatlan ennek megfelelően.

### Hogyan tudom testreszabni a TOA megjelenését?
A TOA megjelenését testreszabhatja a TOA mező tulajdonságainak, például a bejegyzés formázásának és a kategóriacímkéknek a módosításával.

### Lehetséges a TOA mező automatikus frissítése?
Bár manuálisan frissítheti a TOA mezőt a `Update` Az Aspose.Words metódus jelenleg nem támogatja az automatikus frissítéseket a dokumentummódosítások esetén.

### Hozzáadhatok TA mezőket programozottan a dokumentum bizonyos részeihez?
Igen, hozzáadhat TA mezőket adott helyeken a kívánt bekezdésekbe vagy szakaszokba való beszúrással.

### Hogyan kezelhetek több TOA mezőt egyetlen dokumentumban?
Több TOA mezőt is kezelhet különböző hozzárendelésekkel. `EntryCategory` értékeket, és biztosítsa, hogy minden TOA mező a kategóriája alapján szűrje a bejegyzéseket.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
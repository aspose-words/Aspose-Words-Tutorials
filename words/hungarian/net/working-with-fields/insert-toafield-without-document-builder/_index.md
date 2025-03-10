---
title: TOA mező beszúrása Dokumentumkészítő nélkül
linktitle: TOA mező beszúrása Dokumentumkészítő nélkül
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan szúrhat be TOA-mezőt dokumentumkészítő használata nélkül az Aspose.Words for .NET-ben. Kövesse lépésenkénti útmutatónkat a jogi idézetek hatékony kezeléséhez.
weight: 10
url: /hu/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# TOA mező beszúrása Dokumentumkészítő nélkül

## Bevezetés

A Table of Authorities (TOA) mező létrehozása egy Word-dokumentumban olyan érzés lehet, mint egy összetett rejtvény összerakása. Az Aspose.Words for .NET segítségével azonban a folyamat zökkenőmentessé és egyszerűvé válik. Ebben a cikkben végigvezetjük a TOA-mezők dokumentumkészítő használata nélkül történő beszúrásának lépésein, megkönnyítve ezzel az idézetek és jogi hivatkozások kezelését a Word-dokumentumokban.

## Előfeltételek

Mielőtt belevágna az oktatóanyagba, nézzük meg a legfontosabb tudnivalókat, amelyekre szüksége lesz:

-  Aspose.Words for .NET: Győződjön meg arról, hogy a legújabb verzió van telepítve. Letöltheti a[Aspose honlapja](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: .NET-kompatibilis IDE, mint a Visual Studio.
- Alapvető C# ismeretek: Hasznos lesz az alapvető C# szintaxis és fogalmak megértése.
- Word-dokumentum minta: Hozzon létre vagy készítsen egy mintadokumentumot oda, ahová be szeretné szúrni a TOA mezőt.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket az Aspose.Words könyvtárból. Ez a beállítás biztosítja, hogy hozzáférjen a dokumentumkezeléshez szükséges összes osztályhoz és metódushoz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Bontsuk le a folyamatot egyszerű, könnyen követhető lépésekre. Végigvezetjük az egyes szakaszokon, elmagyarázva, hogy az egyes kódrészletek mit csinálnak, és hogyan járulnak hozzá a TOA mező létrehozásához.

## 1. lépés: Inicializálja a dokumentumot

 Először is létre kell hoznia egy példányt a`Document` osztály. Ez az objektum azt a Word-dokumentumot képviseli, amelyen éppen dolgozik.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Ez a kód inicializál egy új Word-dokumentumot. Ezt úgy képzelheti el, mint egy üres vászon létrehozását, amelyhez hozzáadja a tartalmat.

## 2. lépés: A TA mező létrehozása és konfigurálása

Ezután hozzáadunk egy TA (Table of Authorities) mezőt. Ez a mező jelöli a TOA-ban megjelenő bejegyzéseket.

```csharp
Paragraph para = new Paragraph(doc);

// Ilyen TA és TOA mezőket szeretnénk beszúrni:
// { TA \c 1 \l "Érték 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Íme egy bontás:
- Bekezdés para = új Bekezdés(doc);: Új bekezdést hoz létre a dokumentumon belül.
-  FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: TA mezőt ad a bekezdéshez. A`FieldType.FieldTOAEntry` meghatározza, hogy ez egy TOA beviteli mező.
- fieldTA.EntryCategory = "1";: Beállítja a bejegyzés kategóriáját. Ez hasznos a különböző típusú bejegyzések kategorizálásához.
- fieldTA.LongCitation = "Érték 0";: Megadja a hosszú idézet szövegét. Ez az a szöveg fog megjelenni a TOA-ban.
- doc.FirstSection.Body.AppendChild(para);: A TA mezőt tartalmazó bekezdést hozzáfűzi a dokumentum törzséhez.

## 3. lépés: Adja hozzá a TOA mezőt

Most beszúrjuk a tényleges TOA mezőt, amely az összes TA bejegyzést egy táblázatba fordítja.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

Ebben a lépésben:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: TOA mezőt ad a bekezdéshez.
- fieldToa.EntryCategory = "1";: Szűri a bejegyzéseket, hogy csak az "1" kategóriával jelölteket tartalmazza.

## 4. lépés: Frissítse a TOA mezőt

A TOA mező beillesztése után frissítenie kell, hogy a legfrissebb bejegyzéseket tükrözze.

```csharp
fieldToa.Update();
```

Ez a parancs frissíti a TOA mezőt, biztosítva, hogy minden megjelölt bejegyzés helyesen jelenjen meg a táblázatban.

## 5. lépés: Mentse el a dokumentumot

Végül mentse el a dokumentumot az újonnan hozzáadott TOA mezővel.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

 Ez a kódsor a dokumentumot a megadott könyvtárba menti. Ügyeljen arra, hogy cserélje ki`"YOUR DOCUMENT DIRECTORY"` azzal a tényleges elérési úttal, ahová menteni szeretné a fájlt.

## Következtetés

És megvan! Sikeresen hozzáadott egy TOA mezőt egy Word-dokumentumhoz, dokumentumkészítő használata nélkül. Ha követi ezeket a lépéseket, hatékonyan kezelheti az idézeteket, és átfogó jogosultsági táblázatokat hozhat létre jogi dokumentumaiban. Az Aspose.Words for .NET zökkenőmentessé és hatékonnyá teszi ezt a folyamatot, és eszközöket biztosít az összetett dokumentumfeladatok egyszerű kezeléséhez.

## GYIK

### Hozzáadhatok több TA mezőt különböző kategóriákkal?
 Igen, több TA mezőt is felvehet különböző kategóriákkal a`EntryCategory`tulajdon ennek megfelelően.

### Hogyan szabhatom testre a TOA megjelenését?
Testreszabhatja a TOA megjelenését a TOA mező tulajdonságainak, például a bejegyzés formázásának és a kategóriacímkék módosításával.

### Lehetséges a TOA mező automatikus frissítése?
 Míg manuálisan frissítheti a TOA mezőt a`Update` módszerrel az Aspose.Words jelenleg nem támogatja a dokumentummódosítások automatikus frissítését.

### Hozzáadhatok-e programozottan TA mezőket a dokumentum bizonyos részeihez?
Igen, adott helyeken hozzáadhat TA mezőket, ha beilleszti őket a kívánt bekezdésekbe vagy szakaszokba.

### Hogyan kezelhetek több TOA mezőt egyetlen dokumentumban?
 Több TOA-mezőt is kezelhet különböző hozzárendelésével`EntryCategory` értékeket, és gondoskodni kell arról, hogy minden TOA mező a kategóriája alapján szűrje a bejegyzéseket.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

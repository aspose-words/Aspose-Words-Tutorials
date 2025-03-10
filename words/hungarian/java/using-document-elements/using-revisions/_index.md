---
title: Az Aspose.Words for Java verzióinak használata
linktitle: Revíziók használata
second_title: Aspose.Words Java Document Processing API
description: Tanulja meg hatékonyan használni az Aspose.Words for Java változatát. Lépésről lépésre útmutató fejlesztőknek. Optimalizálja dokumentumkezelését.
weight: 22
url: /hu/java/using-document-elements/using-revisions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Az Aspose.Words for Java verzióinak használata


Ha Ön Java-fejlesztő, aki dokumentumokkal szeretne dolgozni, és revízió-vezérlőket szeretne megvalósítani, az Aspose.Words for Java hatékony eszközkészletet biztosít a revíziók hatékony kezeléséhez. Ebben az oktatóanyagban lépésről lépésre végigvezetjük az Aspose.Words for Java revízióján. 

## 1. Az Aspose.Words for Java bemutatása

Az Aspose.Words for Java egy robusztus Java API, amely lehetővé teszi Word dokumentumok létrehozását, módosítását és kezelését Microsoft Word nélkül. Ez különösen akkor hasznos, ha revíziót kell végrehajtania a dokumentumokon belül.

## 2. Fejlesztői környezet beállítása

Mielőtt belemerülnénk az Aspose.Words for Java használatába, be kell állítania fejlesztői környezetét. Győződjön meg arról, hogy telepítve van a szükséges Java fejlesztőeszközök és az Aspose.Words for Java könyvtár.

## 3. Új dokumentum létrehozása

Kezdjük egy új Word-dokumentum létrehozásával az Aspose.Words for Java használatával. A következőképpen teheti meg:

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4. Tartalom hozzáadása a dokumentumhoz

Most, hogy van egy üres dokumentuma, tartalmat adhat hozzá. Ebben a példában három bekezdést adunk hozzá:

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. Revíziókövetés indítása

A dokumentum módosításainak nyomon követéséhez a következő kódot használhatja:

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. Módosítások készítése

Végezzünk átdolgozást egy másik bekezdés hozzáadásával:

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. Változások elfogadása és elutasítása

Az Aspose.Words for Java használatával elfogadhatja vagy elutasíthatja a dokumentum módosításait. A változatok a dokumentum létrehozása után könnyen kezelhetők a Microsoft Word alkalmazásban.

## 8. Revíziókövetés leállítása

A változatok követésének leállításához használja a következő kódot:

```java
doc.stopTrackRevisions();
```

## 9. A dokumentum mentése

Végül mentse el a dokumentumot:

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. Következtetés

Ebben az oktatóanyagban az Aspose.Words for Java revíziójának használatának alapjait ismertetjük. Megtanulta, hogyan hozhat létre dokumentumot, hogyan adhat hozzá tartalmat, hogyan indíthatja el és állíthatja le a revíziókövetést, valamint hogyan mentheti el a dokumentumot.

Mostantól rendelkezésre állnak azok az eszközök, amelyekre szükség van a Java-alkalmazások felülvizsgálatainak hatékony kezeléséhez az Aspose.Words for Java használatával.

## Teljes forráskód
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
// Adjon hozzá szöveget az első bekezdéshez, majd adjon hozzá még két bekezdést.
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
// Három paragrafusunk van, amelyek közül egyiket sem vették nyilvántartásba bármilyen típusú revízióként
// Ha a revíziók nyomon követése közben bármilyen tartalmat hozzáadunk/eltávolítunk a dokumentumból,
// ilyen formában jelennek meg a dokumentumban, és elfogadhatók/elutasíthatók.
doc.startTrackRevisions("John Doe", new Date());
// Ez a bekezdés egy átdolgozás, és a megfelelő "IsInsertRevision" jelző lesz beállítva.
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
// Szerezze be a dokumentum bekezdésgyűjteményét, és távolítsa el a bekezdést.
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
// Mivel a revíziókat nyomon követjük, a bekezdés továbbra is létezik a dokumentumban, és az "IsDeleteRevision" lesz beállítva
// és változatként jelenik meg a Microsoft Wordben, amíg el nem fogadjuk vagy el nem utasítjuk az összes revíziót.
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
// A revízió törlése bekezdés eltávolításra kerül, ha elfogadjuk a változtatásokat.
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //volt.Üres
// A revíziók követésének leállításával ez a szöveg normál szövegként jelenik meg.
// revíziókat a rendszer nem veszi figyelembe a dokumentum megváltoztatásakor.
doc.stopTrackRevisions();
// Mentse el a dokumentumot.
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## GYIK

### 1. Használhatom az Aspose.Words for Java-t más programozási nyelvekkel?

Nem, az Aspose.Words for Java kifejezetten Java fejlesztéshez készült.

### 2. Az Aspose.Words for Java kompatibilis a Microsoft Word összes verziójával?

Igen, az Aspose.Words for Java szoftvert úgy tervezték, hogy kompatibilis legyen a Microsoft Word különféle verzióival.

### 3. Nyomon követhetem a revíziókat a meglévő Word dokumentumokban?

Igen, az Aspose.Words for Java segítségével nyomon követheti a meglévő Word-dokumentumok revízióit.

### 4. Vannak-e licenckövetelmények az Aspose.Words for Java használatához?

 Igen, licencet kell szereznie az Aspose.Words for Java használatához projektjeiben. Megteheti[itt szerezheti be a licencet](https://purchase.aspose.com/buy).

### 5. Hol találok támogatást az Aspose.Words for Java számára?

 Bármilyen kérdés vagy probléma esetén keresse fel a[Aspose.Words for Java támogatási fórum](https://forum.aspose.com/).

Kezdje el az Aspose.Words for Java használatát még ma, és egyszerűsítse dokumentumkezelési folyamatait.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

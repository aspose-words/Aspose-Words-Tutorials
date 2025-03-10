---
title: Dokumentumok összehasonlítása a különbségekért
linktitle: Dokumentumok összehasonlítása a különbségekért
second_title: Aspose.Words Java Document Processing API
description: Tanulja meg, hogyan hasonlíthatja össze a dokumentumokat a különbségek szempontjából az Aspose.Words használatával Java nyelven. Lépésről lépésre bemutatott útmutatónk biztosítja a pontos dokumentumkezelést.
weight: 12
url: /hu/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok összehasonlítása a különbségekért

## Bevezetés

Gondolkozott már azon, hogyan lehet észrevenni minden különbséget két Word-dokumentum között? Lehet, hogy éppen egy dokumentumot dolgoz át, vagy egy együttműködő által végrehajtott változtatásokat próbál keresni. A kézi összehasonlítás fárasztó és hibára hajlamos lehet, de az Aspose.Words for Java-val ez gyerekjáték! Ez a könyvtár lehetővé teszi a dokumentumok összehasonlításának automatizálását, a revíziók kiemelését és a változtatások egyszerű összevonását.

## Előfeltételek

Mielőtt belevágna a kódba, győződjön meg arról, hogy készen áll a következőkre:  
1. Java Development Kit (JDK) telepítve a rendszerére.  
2.  Aspose.Words for Java könyvtár. Megteheti[töltse le itt](https://releases.aspose.com/words/java/).  
3. Olyan fejlesztői környezet, mint az IntelliJ IDEA vagy az Eclipse.  
4. Java programozási alapismeretek.  
5.  Érvényes Aspose engedély. Ha nincs ilyened, szerezz be a[ideiglenes engedély itt](https://purchase.aspose.com/temporary-license/).

## Csomagok importálása

Az Aspose.Words használatához importálnia kell a szükséges osztályokat. Alább láthatók a szükséges importok:

```java
import com.aspose.words.*;
import java.util.Date;
```

Győződjön meg arról, hogy ezek a csomagok megfelelően vannak hozzáadva a projektfüggőségekhez.


Ebben a részben a folyamatot egyszerű lépésekre bontjuk.


## 1. lépés: Állítsa be a dokumentumokat

kezdéshez két dokumentumra van szüksége: az egyik az eredetit, a másik pedig a szerkesztett változatot. Így hozhatja létre őket:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

 Ez két dokumentumot hoz létre a memóriában alapvető tartalommal. A meglévő Word dokumentumokat is betöltheti a használatával`new Document("path/to/document.docx")`.


## 2. lépés: Ellenőrizze a meglévő változatokat

A Word-dokumentumok változatai nyomon követett változásokat jelentenek. Az összehasonlítás előtt győződjön meg arról, hogy egyik dokumentum sem tartalmaz már meglévő változatokat:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Ha vannak változatok, érdemes lehet elfogadni vagy elutasítani azokat a folytatás előtt.


## 3. lépés: Hasonlítsa össze a dokumentumokat

 Használja a`compare` módszer a különbségek megtalálására. Ez a módszer összehasonlítja a céldokumentumot (`doc2`) a forrásdokumentummal (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Itt:
- A AuthorName a módosításokat végrehajtó személy neve.
- A dátum az összehasonlítás időbélyege.


## 4. lépés: Változások feldolgozása

Az összehasonlítás után az Aspose.Words revíziókat generál a forrásdokumentumban (`doc1`). Elemezzük ezeket a revíziókat:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Ez a ciklus részletes információkat tartalmaz az egyes változatokról, például a változtatás típusáról és az érintett szövegről.


## 5. lépés: Minden módosítás elfogadása

Ha szeretné a forrásdokumentumot (`doc1`) hogy megfeleljen a céldokumentumnak (`doc2`), fogadjon el minden módosítást:

```java
doc1.getRevisions().acceptAll();
```

 Ez a frissítés`doc1` hogy tükrözze az összes változtatást`doc2`.


## 6. lépés: Mentse el a frissített dokumentumot

Végül mentse a frissített dokumentumot lemezre:

```java
doc1.save("Document.Compare.docx");
```

A módosítások megerősítéséhez töltse be újra a dokumentumot, és ellenőrizze, hogy nincsenek-e fennmaradó változatok:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## 7. lépés: Ellenőrizze a dokumentumok egyenlőségét

A dokumentumok azonosságának biztosításához hasonlítsa össze a szövegüket:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Ha a szövegek megegyeznek, gratulálunk – sikeresen összehasonlította és szinkronizálta a dokumentumokat!


## Következtetés

dokumentum-összehasonlítás az Aspose.Words for Java-nak köszönhetően már nem munka. Néhány sornyi kóddal pontosan meghatározhatja a különbségeket, feldolgozhatja a revíziókat, és biztosíthatja a dokumentumok konzisztenciáját. Akár egy közös írási projektet kezel, akár jogi dokumentumokat auditál, ez a funkció megváltoztatja a helyzetet.

## GYIK

### Összehasonlíthatom a dokumentumokat képekkel és táblázatokkal?  
Igen, az Aspose.Words támogatja az összetett dokumentumok összehasonlítását, beleértve a képeket, táblázatokat és formázásokat is.

### Szükségem van licencre a funkció használatához?  
 Igen, a teljes funkcionalitáshoz licenc szükséges. Szerezd meg a[ideiglenes engedély itt](https://purchase.aspose.com/temporary-license/).

### Mi történik, ha vannak már meglévő változatok?  
Az ütközések elkerülése érdekében a dokumentumok összehasonlítása előtt el kell fogadnia vagy el kell utasítania őket.

### Kiemelhetem a módosításokat a dokumentumban?  
Igen, az Aspose.Words lehetővé teszi a változatok megjelenítési módjának testreszabását, például a változtatások kiemelését.

### Elérhető ez a funkció más programozási nyelveken?  
Igen, az Aspose.Words több nyelvet is támogat, beleértve a .NET-et és a Python-t.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

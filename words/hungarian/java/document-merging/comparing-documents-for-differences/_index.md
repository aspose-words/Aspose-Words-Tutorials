---
"description": "Tanuld meg, hogyan hasonlíthatod össze a dokumentumokat az Aspose.Words segítségével Java nyelven. Lépésről lépésre útmutatónk biztosítja a pontos dokumentumkezelést."
"linktitle": "Dokumentumok összehasonlítása a különbségek szempontjából"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok összehasonlítása a különbségek szempontjából"
"url": "/hu/java/document-merging/comparing-documents-for-differences/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok összehasonlítása a különbségek szempontjából

## Bevezetés

Elgondolkodott már azon, hogyan lehet minden egyes különbséget észrevenni két Word-dokumentum között? Talán egy dokumentumot módosít, vagy egy munkatárs által végrehajtott módosításokat próbál megkeresni. A manuális összehasonlítások unalmasak és hibalehetőségekkel teliek lehetnek, de az Aspose.Words for Java segítségével ez gyerekjáték! Ez a könyvtár lehetővé teszi a dokumentumok összehasonlításának automatizálását, a módosítások kiemelését és a változtatások erőfeszítés nélküli egyesítését.

## Előfeltételek

Mielőtt belevágnál a kódba, győződj meg róla, hogy a következők készen állnak:  
1. Java fejlesztőkészlet (JDK) telepítve van a rendszerére.  
2. Aspose.Words Java könyvtárhoz. Meg tudod csinálni [töltsd le itt](https://releases.aspose.com/words/java/).  
3. Fejlesztői környezet, mint például az IntelliJ IDEA vagy az Eclipse.  
4. Alapvető jártasság a Java programozásban.  
5. Érvényes Aspose licenc. Ha nincs, szerezzen be egyet. [ideiglenes jogosítvány itt](https://purchase.aspose.com/temporary-license/).

## Csomagok importálása

Az Aspose.Words használatához importálni kell a szükséges osztályokat. Az alábbiakban a szükséges importálási elemek láthatók:

```java
import com.aspose.words.*;
import java.util.Date;
```

Győződjön meg arról, hogy ezek a csomagok megfelelően vannak hozzáadva a projekt függőségeihez.


Ebben a részben egyszerű lépésekre bontjuk a folyamatot.


## 1. lépés: Dokumentumok beállítása

Kezdéshez két dokumentumra van szükséged: az egyik az eredetit, a másik a szerkesztett verziót ábrázolja. Így hozhatod létre őket:

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

Ez két dokumentumot hoz létre a memóriában alapvető tartalommal. A meglévő Word-dokumentumokat is betöltheti a következővel: `new Document("path/to/document.docx")`.


## 2. lépés: Létező verziók ellenőrzése

A Word-dokumentumokban a módosítások követett változtatásokat jelentenek. Összehasonlítás előtt győződjön meg arról, hogy egyik dokumentum sem tartalmaz korábbi módosításokat:

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

Ha vannak módosítások, érdemes lehet elfogadni vagy elutasítani azokat a folytatás előtt.


## 3. lépés: Hasonlítsa össze a dokumentumokat

Használd a `compare` módszer a különbségek keresésére. Ez a módszer összehasonlítja a céldokumentumot (`doc2`) a forrásdokumentummal (`doc1`):

```java
doc1.compare(doc2, "AuthorName", new Date());
```

Itt:
- Az AuthorName a módosításokat végző személy neve.
- A dátum az összehasonlítás időbélyege.


## 4. lépés: A folyamat felülvizsgálata

Az összehasonlítás után az Aspose.Words módosításokat generál a forrásdokumentumban (`doc1`). Elemezzük ezeket a módosításokat:

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

Ez a ciklus részletes információkat nyújt az egyes módosításokról, például a módosítás típusáról és az érintett szövegről.


## 5. lépés: Az összes módosítás elfogadása

Ha a forrásdokumentumot szeretnéd (`doc1`) a céldokumentumnak való megfelelés érdekében (`doc2`), fogadja el az összes módosítást:

```java
doc1.getRevisions().acceptAll();
```

Ez a frissítés `doc1` hogy tükrözze az összes végrehajtott változtatást `doc2`.


## 6. lépés: Mentse el a frissített dokumentumot

Végül mentse el a frissített dokumentumot lemezre:

```java
doc1.save("Document.Compare.docx");
```

A módosítások megerősítéséhez töltse be újra a dokumentumot, és ellenőrizze, hogy nincsenek-e megmaradt módosítások:

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## 7. lépés: A dokumentumok egyenrangúságának ellenőrzése

A dokumentumok azonosságának biztosítása érdekében hasonlítsa össze a szövegüket:

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

Ha a szövegek egyeznek, gratulálunk – sikeresen összehasonlította és szinkronizálta a dokumentumokat!


## Következtetés

dokumentumok összehasonlítása már nem nyűg az Aspose.Words for Java segítségével. Mindössze néhány sornyi kóddal meghatározhatja a különbségeket, feldolgozhatja a javításokat és biztosíthatja a dokumentumok egységességét. Akár egy közös írásbeli projektet kezel, akár jogi dokumentumokat auditál, ez a funkció gyökeresen megváltoztatja a játékszabályokat.

## GYIK

### Összehasonlíthatom a dokumentumokat képekkel és táblázatokkal?  
Igen, az Aspose.Words támogatja az összetett dokumentumok összehasonlítását, beleértve a képeket, táblázatokat és formázást tartalmazókat is.

### Szükségem van licencre a funkció használatához?  
Igen, a teljes funkcionalitáshoz licenc szükséges. Szerezzen be egy [ideiglenes jogosítvány itt](https://purchase.aspose.com/temporary-license/).

### Mi történik, ha vannak már meglévő módosítások?  
A dokumentumok összehasonlítása előtt el kell fogadnia vagy el kell utasítania azokat az ütközések elkerülése érdekében.

### Kiemelhetem a dokumentumban található módosításokat?  
Igen, az Aspose.Words lehetővé teszi a módosítások megjelenítésének testreszabását, például a változtatások kiemelését.

### Ez a funkció más programozási nyelvekben is elérhető?  
Igen, az Aspose.Words több nyelvet is támogat, beleértve a .NET-et és a Pythont.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
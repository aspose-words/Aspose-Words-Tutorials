---
date: 2026-01-11
description: Tanulja meg, hogyan jeleníthetőek meg és rejthetőek el a könyvjelzők,
  valamint hogyan hozhat létre könyvjelzőt Java-ban az Aspose.Words for Java segítségével
  a hatékony dokumentumnavigáció és -manipuláció érdekében.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Könyvjelzők megjelenítése és elrejtése az Aspose.Words for Java-val
url: /hu/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Könyvjelzők megjelenítése és elrejtése az Aspose.Words for Java-val

## Bevezetés a könyvjelzők használatába az Aspose.Words for Java-ban

A könyvjelzők egy erőteljes funkció az Aspose.Words for Java-ban, amely lehetővé teszi, hogy **create bookmark java**, navigáljon a konkrét tartalomhoz, és akár **show hide bookmarks** is, amikor különböző dokumentumverziókat kell generálni. Ebben a lépésről‑lépésre útmutatóban végigvezetjük a könyvjelzők létrehozásán, elérésén, frissítésén, másolásán és láthatóságuk váltásán, teljes irányítást biztosítva a dokumentumműveletek felett.

## Gyors válaszok
- **What is the primary purpose of bookmarks?** A dokumentum bizonyos részeinek megjelölésére és későbbi visszakeresésére szolgál.  
- **Can I hide bookmark markers in the final output?** Igen—használja a show/hide API-t a láthatóságuk váltásához.  
- **How do I create a bookmark inside a table cell?** A könyvjelzőt a `DocumentBuilder`‑rel indítsa és fejezze be, miközben a kurzor a cellán belül van.  
- **Is it possible to copy bookmarked text to another document?** Természetesen—használja a `NodeImporter`‑t a formázás megőrzéséhez.  
- **What version of Aspose.Words is required?** Bármelyik friss kiadás; a kód a legújabb 2026-os builddel működik.

## Mi az a „show hide bookmarks”?

A **show hide bookmarks** funkció lehetővé teszi, hogy programozottan megjelenítse vagy elrejtse a könyvjelző elválasztókat a mentett dokumentumban. Ez akkor hasznos, amikor tiszta kimenetet szeretne generálni a végfelhasználók számára, miközben a könyvjelző adatokat belső feldolgozáshoz megőrzi.

## Miért használjunk könyvjelzőket a Java dokumentumautomatizálásban?

- **Efficient navigation** – Ugrás közvetlenül a szakaszokra a teljes fájl átvizsgálása nélkül.  
- **Dynamic content generation** – Szöveg beszúrása, cseréje vagy eltávolítása, amely egy könyvjelzőhöz van kötve.  
- **Conditional visibility** – A könyvjelző jelölők megjelenítése vagy elrejtése a felhasználói beállítások vagy a kimeneti formátum alapján.  
- **Reusability** – Könyvjelzővel ellátott szakaszok másolása dokumentumok között a stílusok megőrzésével.

## Előfeltételek
- Java Development Kit (JDK) 8 vagy újabb.  
- Aspose.Words for Java könyvtár hozzáadva a projekthez (Maven/Gradle vagy JAR).  
- Alapvető ismeretek a `Document` és `DocumentBuilder` osztályokról.

## Lépés‑ről‑lépésre útmutató

### 1. lépés: Könyvjelző létrehozása (create bookmark java)

A könyvjelző hozzáadásához először elindítja, beírja a tartalmat, majd befejezi. Ez a példa egy egyszerű, **My Bookmark** nevű könyvjelzőt hoz létre.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### 2. lépés: Könyvjelzők elérése (access bookmarks java)

A könyvjelzők lekérhetők a nullától induló index vagy a név alapján. Az alábbi kód mindkét megközelítést bemutatja.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### 3. lépés: Könyvjelző adat frissítése (update bookmark text)

Átnevezhet egy könyvjelzőt vagy cserélheti a szövegtartalmát. Ez hasznos, ha az alapdokumentum változik.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### 4. lépés: Munka a könyvjelzővel ellátott szöveggel (copy bookmarked text)

A könyvjelzővel ellátott szakasz másolása egy másik dokumentumba az eredeti formázás megtartásával egyszerű a `NodeImporter` segítségével.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### 5. lépés: Könyvjelzők megjelenítése és elrejtése (show hide bookmarks)

Az alábbi kódrészlet bemutatja, hogyan lehet elrejteni egy könyvjelző jelölőit a mentett fájlban. A `false` érték elrejt, a `true` érték megjelenít.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### 6. lépés: Sor könyvjelzők feloldása (bookmark table cell)

Amikor a könyvjelzők táblázatsorokat fednek le, összegabalyodhatnak. Az alábbi segédfüggvények feloldják őket, és lehetővé teszik egy adott sor törlését a könyvjelzője alapján.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Gyakori problémák és megoldások

| Issue | Solution |
|-------|----------|
| **Bookmark nem található** | Ellenőrizze, hogy a könyvjelző neve pontosan (kis‑nagybetű érzékenyen) egyezik, és hogy a dokumentum a létrehozás után lett mentve. |
| **Másolt szöveg elveszíti a formázást** | Használja a `ImportFormatMode.KEEP_SOURCE_FORMATTING`-t a `NodeImporter`-rel, ahogy a 4. lépésben látható. |
| **Show/hide nem befolyásolja a kimenetet** | Győződjön meg róla, hogy a `showHideBookmarkedContent` **előtt** hívja meg a dokumentum mentése előtt. |
| **Bookmark a táblázat cellájában figyelmen kívül marad** | Helyezze a start/end hívásokat, miközben a builder kurzor a célcellán belül van. |

## Gyakran feltett kérdések

**Q: Hogyan hozhatok létre könyvjelzőt egy táblázat cellájában?**  
A: Használja a `DocumentBuilder`-t a kurzor a kívánt cellába mozgatásához, majd hívja a `startBookmark` és `endBookmark` metódusokat a cella tartalma körül.

**Q: Másolhatok egy könyvjelzőt egy másik dokumentumba?**  
A: Igen—használja a `NodeImporter` osztályt (lásd a 4. lépést) a könyvjelzővel ellátott csomópont importálásához, miközben megőrzi az eredeti formázást.

**Q: Hogyan törölhetek egy sort a könyvjelzője alapján?**  
A: Először keresse meg azt a sort, amely a könyvjelzőt tartalmazza, majd hívja a `remove` metódust a sor csomóponton (ahogy a 6. lépésben bemutatjuk).

**Q: Mik a könyvjelzők gyakori felhasználási esetei?**  
A: Tartalomjegyzék generálása, specifikus szakaszok kinyerése jelentéshez, valamint a dokumentum összeállításának automatizálása a felhasználói választások alapján.

**Q: Hol találhatok további információkat az Aspose.Words for Java-ról?**  
A: Részletes dokumentációért és letöltésekért látogassa meg a [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) oldalt.

**Legutóbb frissítve:** 2026-01-11  
**Tesztelve ezzel:** Aspose.Words for Java 24.11 (2026)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
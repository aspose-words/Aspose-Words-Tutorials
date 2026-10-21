---
category: general
date: 2026-08-23
description: Készítsen üres Word-dokumentumot az Aspose.Words for Java segítségével,
  tanulja meg, hogyan csoportosítsa az alakzatokat, színezze a téglalap alakzatot,
  és mentse a dokumentumot docx formátumban percek alatt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: hu
lastmod: 2026-08-23
og_description: Hozzon létre üres Word-dokumentumot az Aspose.Words for Java segítségével,
  majd tekintse meg, hogyan csoportosíthatók az alakzatok, színezhető a téglalap alakzat,
  és hogyan menthető a dokumentum hatékonyan docx formátumban.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Üres Word-dokumentum létrehozása és alakzatok csoportosítása Java-ban –
  lépésről‑lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Üres Word-dokumentum létrehozása és alakzatok csoportosítása Java-ban
url: /hu/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása és alakzatok csoportosítása Java-ban

Ha programozott módon **üres Word dokumentumot** kell létrehoznod, az Aspose.Words for Java egyszerűvé teszi ezt. Ez az útmutató pontosan megmutatja, hogyan **hozz létre üres Word dokumentumot**, hogyan szúrj be egy **csoportosított alakzatot Word-ben**, hogyan alkalmazz **színes téglalap alakzatot**, és végül hogyan **mentsd a dokumentumot docx**. A végére egy újrahasználható kódrészletet kapsz, amelyet bármely Java projektbe beilleszthetsz.

Megtanulod:

* A szükséges Maven/Gradle függőség az Aspose.Words-hez.
* Hogyan példányosítsunk egy üres dokumentumot és egy `DocumentBuilder`-t.
* A pontos lépéseket, hogyan **csoportosítsuk az alakzatokat** egy `GroupShape`-ben.
* Hogyan állítsuk be a kitöltő színeket a téglalap alakzatokon.
* A legjobb gyakorlat a **dokumentum docx formátumban való mentéséhez** és hogy hol található a kimeneti fájl.

Nem feltételezünk előzetes tapasztalatot az Aspose.Words használatában, de kényelmesen kell tudnod a Java alapvető fejlesztését, és legyen telepítve JDK 8 vagy újabb.

---

## Előkövetelmények

| Követelmény | Verzió / Részlet |
|-------------|-------------------|
| Java Fejlesztői Készlet | 8 vagy újabb |
| Építőeszköz | Maven 3+ vagy Gradle 6+ |
| Aspose.Words for Java | 23.12 vagy újabb (az írás időpontjában legújabb verzió) |
| IDE (opcionális) | IntelliJ IDEA, Eclipse, VS Code, vagy bármely Java‑kompatibilis szerkesztő |

---

## 1. lépés: Add Aspose.Words a projektedhez

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Ha vállalati proxy-t használsz, konfiguráld a Maven/Gradle-t, hogy a csomagot az Aspose tárolóból töltse le, ahogyan azt a hivatalos dokumentáció leírja.

---

## 2. lépés: **Create blank Word document** egy builderrel

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A `Document` konstruktor egy üres `.docx` tárolót hoz létre a memóriában. A `DocumentBuilder` egy folyékony API-t biztosít a tartalom, köztük az alakzatok hozzáadásához.

---

## 3. lépés: Insert a **group shapes in Word** konténer

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

A `GroupShape` úgy működik, mint egy mini‑vászon. Az összes hozzáadott alakzat együtt mozog, ami pontosan **how to group shapes** a layout konzisztencia érdekében.

---

## 4. lépés: Add the first **color rectangle shape** (red)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

A `ShapeType.RECTANGLE` konstans egy egyszerű téglalapot hoz létre. A `getFill().setForeColor(...)` hívásával szabályozhatod a **color rectangle shape**-t. A `java.awt.Color.RED` helyett bármely `java.awt.Color` konstans vagy egyedi RGB érték használható.

---

## 5. lépés: Add the second **color rectangle shape** (green) and position it

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

A `setLeft` (vagy `setTop`) beállítása a alakzatot a **group shapes in Word** konténer bal‑felső sarkához képest mozgatja. Ez bemutatja, hogyan **how to group shapes** pontos pozicionálással.

---

## 6. lépés: **Save document as docx** és ellenőrizd az eredményt

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

A `save` metódus automatikusan egy `.docx` fájlt ír, mivel a fájlkiterjesztés `.docx`. Ha más formátumra van szükséged (pl. PDF), add meg a megfelelő `SaveFormat` enum-ot.

> **Tip:** Győződj meg róla, hogy a célkönyvtár (`output/` ebben a példában) létezik, vagy hozd létre programozottan a `new File("output").mkdirs();` segítségével.

---

## Teljes forráskód gyors másoláshoz

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Várható kimenet:** A `GroupShapeDemo.docx` megnyitása a Microsoft Wordben egyetlen oldalt mutat, amely két színes téglalapot tartalmaz (balra piros, jobbra zöld), amelyek együtt mozognak, amikor kiválasztod a csoportot.

---

## Gyakori kérdések és szél‑eset kezelése

| Kérdés | Válasz |
|----------|--------|
| *Hozzáadhatok több mint két alakzatot ugyanahhoz a csoporthoz?* | Igen. Hívja a `groupShape.appendChild(yourShape)`-t minden további alakzatra. A csoport automatikusan átméreteződik, hogy befogadja a legkülső határokat, vagy manuálisan állíthatja a szélességét/magasságát. |
| *Mi van, ha más alakzat típust (pl. ellipszis) kell használnom?* | Cseréld le a `ShapeType.RECTANGLE`-t `ShapeType.ELLIPSE`-re. Ugyanez a kitöltő‑szín logika érvényes. |
| *Szükséges-e felszabadítani a `Document` objektumot?* | Az Aspose.Words belsőleg kezeli a natív erőforrásokat. Amikor a JVM kilép, az erőforrások felszabadulnak. Hosszú futású alkalmazásoknál hívd a `doc.dispose();`-t, ha a **Aspose.Words for Java (Native)** verziót használod. |
| *Hogyan változtathatom meg a Z‑sorrendet, hogy egy téglalap felül jelenjen?* | Használd a `groupShape.insertAfter(shape, referenceShape);` vagy `groupShape.insertBefore(shape, referenceShape);` metódusokat a csoporton belüli gyermekek átrendezéséhez. |
| *Csoportosíthatok-e alakzatokat különböző szakaszok között?* | Nem. A `GroupShape`-nek egyetlen bekezdésen vagy alakzat konténeren belül kell lennie. Szakaszok közötti csoportosításhoz hozz létre külön csoportokat minden szakaszban. |

---

## Következtetés

Most már tudod, hogyan **create blank Word document** az Aspose.Words for Java-val, hogyan **group shapes in Word**, hogyan alkalmazz **color rectangle shape** stílusokat, és hogyan **save document as docx**. Ez a minta skálázható összetettebb elrendezésekhez – csak adj hozzá további alakzatokat, állítsd be az eltolásokat, és opcionálisan helyezz el szöveget, képeket vagy hiperhivatkozásokat a csoporton belül.

**Next steps** you might explore:

* Használd a **group shapes in Word**-t folyamatábrák vagy UI makettek építéséhez.
* Kísérletezz a **save document as docx**-el kombinálva a PDF konverzióval (`doc.save("out.pdf")`).
* Alkalmazz színátmeneteket vagy mintákat a **color rectangle shape**-re a gazdagabb vizuális tervezés érdekében.
* Kombináld a csoportosított alakzatokat táblázatokkal vagy diagramokkal fejlett jelentésdokumentumokhoz.

Nyugodtan módosítsd a méreteket, színeket vagy alakzat típusokat, hogy megfeleljenek a projekted arculatának. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Hogyan mentsd a dokumentumot pdf formátumba az Aspose.Words for Java-val](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Dokumentum alakzatok használata az Aspose.Words for Java-ban](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
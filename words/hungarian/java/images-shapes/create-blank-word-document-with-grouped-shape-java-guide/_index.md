---
category: general
date: 2026-07-20
description: Üres Word-dokumentum létrehozása Java-ban az Aspose.Words segítségével.
  Tanulja meg, hogyan hozhat létre csoportot, szúrjon be téglalap alakzatot, és ágyazzon
  be képet az alakzatba.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: hu
lastmod: 2026-07-20
og_description: Üres Word-dokumentum létrehozása Java-ban az Aspose.Words segítségével.
  Ez az útmutató bemutatja, hogyan hozhatunk létre csoportot, szúrhatunk be téglalap
  alakzatot, és ágyazhatunk be képet az alakzatba dinamikus Word-fájlokhoz.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Üres Word-dokumentum létrehozása csoportosított alakzattal – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Üres Word-dokumentum létrehozása csoportosított alakzattal – Java útmutató
url: /hu/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása csoportos alakzattal – Java útmutató

Gondolkodtál már azon, hogyan **hozz létre üres Word dokumentumot**, amely már egy szépen csoportosított alakzatot tartalmaz? Lehet, hogy jelentés sablont építesz, vagy egy logó és felirat helyőrzőre van szükséged. Bármi is legyen az ok, a probléma gyakori: egy üres fájllal kezded, majd hozzá kell adnod egy csoportot, egy téglalapot helyezni bele, és végül beágyazni egy képet – mindezt programozottan.

Ebben az útmutatóban végigvezetünk egy teljes, azonnal futtatható Java példán, amely pontosan ezt csinálja. Megtanulod, hogyan **hozz létre csoportot**, **helyezz be téglalap alakzatot**, és **adj hozzá képet a Word dokumentumhoz** ugyanabban a csoportban. A végére egy olyan Word fájlt kapsz, amely egy kifinomult sablonnak tűnik, készen áll a további testreszabásra.

> **Mit kapsz:** egy teljesen működőképes Java osztályt, lépésről‑lépésre magyarázatokat, tippeket a fájlútvonalak kezeléséhez, és egy előnézetet a várt kimenetről. Nem szükséges külső dokumentáció – minden, amire szükséged van, itt van.

---

## Üres Word dokumentum létrehozása – Lépésről‑lépésre áttekintés

Az első dolog, amire szükségünk van, egy valóban üres Word fájl. Az Aspose.Words ezt egyszerűvé teszi: csak példányosítsd a `Document` osztályt az alapértelmezett konstruktorával. Ez egy tiszta vászonként szolgál, ami megegyezik azzal, amikor megnyitod a Wordöt és a **New → Blank document** (Új → Üres dokumentum) lehetőségre kattintasz.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Miért kezdj egy üres dokumentummal?**  
> Egy üres dokumentum garantálja, hogy semmilyen rejtett stílus vagy szakasz ne zavarja a később hozzáadott alakzatokat. Emellett minimálisra tartja a fájlméretet, ami hasznos, ha egy kötegelt feladat során tucatnyi fájlt generálsz.

---

## Hogyan hozhatunk létre csoportot és adhatunk hozzá alakzatokat

A **group shape** (csoportos alakzat) lényegében egy tároló, amely több gyermek alakzatot is tartalmazhat – gondolj rá, mint egy mappára a rajzobjektumok számára. Csoportosítással egyetlen paranccsal mozgathatod, átméretezheted vagy elforgathatod az egész halmazt.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

Az `insertGroupShape` metódus egy `GroupShape` objektumot ad vissza, amelyet a téglalap és a kép szülőjeként fogunk használni. A méret pontokban van megadva (1 pont = 1/72 hüvelyk), így a 200 pont körülbelül egy 2,78 × 2,78 hüvelykes dobozt jelent.

> **Pro tipp:** Ha a csoportnak átlátszónak kell lennie, a létrehozás után állítsd be a `group.setFillColor(Color.getWhite());` értéket.

Miután a csoport létezik, meg kell mondanunk a buildernek, hogy hová helyezze a következő alakzatokat. A builder kurzorát a csoport első bekezdésén belül kell elhelyezni.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Téglalap alakzat beszúrása a csoportba

A téglalapot gyakran használják szöveghelyőrzőként vagy vizuális jelzésként. A csoport **első gyermekeként** hozzáadva biztosítja, hogy a későbbi képek mögött helyezkedjen el.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

A téglalap örökli a csoport koordináta‑rendszerét, így az 100 × 50‑pont mérete alapértelmezés szerint középre kerül. Tovább is formázhatod – hozzáadhatsz keretet, megváltoztathatod a kitöltő színt, vagy árnyékot alkalmazhatsz – a visszaadott `Shape` objektum elérésével.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Kép hozzáadása Word dokumentumhoz – kép beágyazása alakzatba

Most jön a szórakoztató rész: **kép beágyazása alakzatba**. Egy JPEG képet fogunk beszúrni a csoport második gyermekeként. Mivel a kurzor még mindig a csoporton belül van, a kép automatikusan gyermek csomóponttá válik.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Ha a kép fájl nem található, az Aspose.Words `FileNotFoundException`‑t dob. Ennek elkerülése érdekében helyezd a `sample.jpg` fájlt a projekt munkakönyvtárába, vagy használj abszolút elérési utat.

> **Mi van, ha más képformátumra van szükséged?**  
> Az Aspose.Words támogatja a PNG, BMP, GIF, TIFF és még az SVG formátumokat is. Csak módosítsd a fájl kiterjesztését, és a könyvtár elvégzi a konverziót.

---

## A dokumentum mentése és az eredmény megtekintése

Végül a memóriában lévő dokumentumot lemezre mentjük. A keletkezett `.docx` egyetlen oldalt fog tartalmazni egy csoportos alakzattal, amely a téglalapot és a képet is magában foglalja.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Amikor megnyitod a `output.docx` fájlt a Microsoft Wordben, a bal‑felső sarokban egy 200 × 200‑pont méretű csoportot kell látnod. A csoporton belül egy világosszürke téglalap helyezkedik el a tetején, és közvetlenül alatta a megadott kép jelenik meg, tökéletesen igazítva.

![Grouped shape example](grouped-shape.png){:alt="Egy üres Word dokumentum képernyőképe, amely egy csoportos alakzatot tartalmaz, benne egy téglalappal és egy beágyazott képpel"}

---

## Gyakori variációk és szélső esetek kezelése

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **Különböző csoportméret** | Állítsd be az `insertGroupShape(width, height)` paramétereit | A nagyobb csoportok összetettebb elrendezéseket képesek befogadni. |
| **Több kép** | Hívd meg többször a `builder.insertImage()`‑t, miután minden alkalommal a csoport bekezdésére léptél | Minden hívás új gyermeket ad hozzá; a `Shape.setLeft()` / `setTop()` segítségével is pozicionálhatod őket. |
| **Dinamikus képútvonalak** | Használd a `String.format("images/%s.jpg", imageName)` kifejezést | Újrafelhasználhatóvá teszi a kódot kötegelt feldolgozáshoz. |
| **Mentés PDF‑ként** | Cseréld le a `doc.save("output.pdf")`‑t | Az Aspose.Words helyben tud konvertálni, így közvetlenül PDF‑eket generálhatsz. |
| **A csoport forgatása** | `group.setRotation(45);` | Hasznos díszítő vízjelekhez vagy stilizált fejlécekhez. |

---

## Várt kimenet és ellenőrzés

Az osztály futtatása után:

1. `output.docx` megjelenik a projekt mappájában.  
2. A fájl megnyitása egyetlen oldalt mutat egy csoportos alakzattal.  
3. A csoporton belül a téglalap a bal‑felső sarokban helyezkedik el, a kép pedig közvetlenül alatta.  
4. A csoport kiválasztása a Wordben mindkét gyermekobjektust kiemeli, ezzel megerősítve, hogy valóban csoportosítva vannak.

Ha bármelyik lépés nem sikerül, ellenőrizd újra a kép útvonalát, és győződj meg arról, hogy az Aspose.Words JAR a classpath‑on van.

---

## Összegzés

Most már tudod, hogyan **hozz létre üres Word dokumentumot**, és hogyan gazdagíthatod egy csoportos alakzattal, amely egy téglalapot és egy beágyazott képet tartalmaz. A **csoport létrehozásának**, a **téglalap alakzat beszúrásának**, és a **kép hozzáadásának a Word dokumentumhoz** elsajátításával teljesen kódból építhetsz kifinomult Word sablonokat – manuális finomhangolás nélkül.

Készen állsz a következő kihívásra? Próbálj meg szövegdobozokat hozzáadni ugyanabban a csoportban, vagy kísérletezz különböző alakzatstílusokkal, hogy megfeleljenek a vállalati arculatnak. Sőt, akár egy teljes jelentéskönyvtárat is generálhatsz, ahol minden dokumentum ezzel a pontos elrendezéssel kezdődik.

Boldog kódolást, és nyugodtan oszd meg saját variációidat a lenti kommentekben!

## Mit érdemes legközelebb megtanulni?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
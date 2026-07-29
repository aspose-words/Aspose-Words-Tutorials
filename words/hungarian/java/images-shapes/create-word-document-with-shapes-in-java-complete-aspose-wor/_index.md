---
category: general
date: 2026-07-29
description: Word dokumentum létrehozása Java-ban az Aspose.Words használatával. Tanulja
  meg, hogyan szúrjon be téglalap alakzatot, csoportosítson alakzatokat a Wordben,
  és mentse a dokumentumot gyorsan docx formátumban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: hu
lastmod: 2026-07-29
og_description: Word dokumentum létrehozása Java-ban az Aspose.Words segítségével.
  Téglalap alakzat beszúrása, alakzatok csoportosítása Word-ben, és a dokumentum docx
  formátumban való mentése percek alatt.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Word dokumentum létrehozása alakzatokkal – Java Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Word-dokumentum létrehozása alakzatokkal Java-ban – Teljes Aspose.Words útmutató
url: /hu/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása alakzatokkal Java-ban – Teljes Aspose.Words útmutató

Gondolkodtál már azon, hogyan **create word document** programozottan, és egyedi grafikákkal díszítve? Nem vagy egyedül. Akár egy kiemelt szakaszokkal ellátott jelentést kell generálnod, akár egy szórólapot kell gyorsan megtervezned, a Word alakzatkezelésének elsajátítása órákat spórolhat meg a kézi munkában.

Ebben az útmutatóban végigvezetünk a pontos lépéseken, hogy **create word document** Aspose.Words for Java használatával, **insert rectangle shape**, **group shapes in Word**, és végül **save document as docx**. A végére egy teljesen futtatható példát kapsz, amelyet bármely projektbe beilleszthetsz.

## Mit fogsz elsajátítani

- Egy friss Word fájl, amely teljesen Java kódból generálódik.  
- Két különálló alakzat (egy téglalap és egy ellipszis) hozzáadva az oldalhoz.  
- Az alakzatok együttesen a **group shapes in word** API-val vannak csoportosítva, így egyetlen objektumként viselkednek.  
- A fájl standard `.docx` formátumban kerül a lemezre, amely hibamentesen megnyílik a Microsoft Wordben.  

Nincs külső eszköz, nincs bonyolult XML trükk – csak tiszta, típusos Java és Aspose.Words.

---

## Előfeltételek

Mielőtt belevágnánk, győződj meg róla, hogy a következőkkel rendelkezel:

1. **Java Development Kit (JDK) 8 vagy újabb** – a kód Java 8+ célra íródott.  
2. **Aspose.Words for Java** JAR (a legújabb verziót a Maven Central tárolóból szerezheted be).  
3. Egy egyszerű IDE (IntelliJ IDEA, Eclipse, vagy akár egy egyszerű szövegszerkesztő).  

Ha ezek megvannak, nagyszerű – kezdjünk bele.

---

## Lépés‑ről‑lépésre megvalósítás

Alább a folyamatot kisebb lépésekre bontjuk. Minden lépés tartalmaz egy kódrészletet, egy rövid magyarázatot és egy tippet, amit a hivatalos dokumentációban nem biztos, hogy megtalálsz.

### ## Word dokumentum létrehozása alakzatokkal Aspose.Words használatával

Az első dolog, amire szükséged van, egy üres Word fájl, amivel dolgozhatsz. Az Aspose.Words ezt egyetlen sorra redukálja.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Miért fontos ez:**  
`Document` a konténer mindenhez – szöveg, táblázatok, képek és alakzatok. `DocumentBuilder` a barátságos segítő, amely lehetővé teszi a tartalom hozzáadását anélkül, hogy alacsony szintű objektumokkal kellene küzdened. Olyan, mint egy toll, amely közvetlenül a lapra ír.

> **Pro tipp:** Ha sablonnal szeretnél kezdeni (pl. céges fejléccel), cseréld le a `new Document()`-et `new Document("template.docx")`-re.

### ## Insert Rectangle Shape and Other Shapes

Most hozzáadunk egy kék téglalapot és egy zöld ellipszist. A téglalap bemutatja a **insert rectangle shape** kulcsszót, míg az ellipszis azt mutatja, hogy szabadon keverheted az alakzat típusokat.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**Mi történik a háttérben?**  
Minden `insertShape` hívás egy `Shape` objektumot hoz létre, és automatikusan hozzáadja az aktuális bekezdéshez. A `setLeft`/`setTop` metódusok a lap margójához viszonyítva pozícionálják az alakzatot, pontokban mérve (1 pt = 1/72 in). Ezeknek a számoknak a finomhangolásával bárhová elhelyezheted az alakzatokat.

> **Gyakori kérdés:** *Hozzáadhatok képet a szilárd szín helyett?*  
> Természetesen – csak cseréld le a kitöltő színt egy képre a `shape.getFill().setImage("path/to/image.png")` használatával.

### ## Group Shapes in Word for Easy Manipulation

Két különálló objektum rendben van, de gyakran szeretnéd őket együtt mozgatni. Itt jön képbe a **group shapes in word**.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Miért csoportosítsuk?**  
Amikor az alakzatok csoportosítva vannak, bármely átalakítás – mozgatás, forgatás, átméretezés – az egész gyűjteményre vonatkozik. Ez tükrözi azt a viselkedést, amit akkor kapsz, amikor a Word felületén több alakzatot választasz ki, és a *Group* gombot nyomod meg. Emellett egyszerűsíti a későbbi kódot, mivel csak egy objektumot kell módosítanod a sok helyett.

> **Szélsőséges eset:** Ha később fel kell bontani a csoportot, hívd a `group.getParentNode().removeChild(group)`-ot, és illeszd be a gyermekeket egyenként.

### ## Save Document as DOCX and Verify Output

Végül elmentjük a fájlt. Ez a lépés teljesíti a **save document as docx** követelményt.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Mi várható:**  
Nyisd meg a generált `GroupShapeExample.docx`-et a Microsoft Wordben. Látnod kell egy kék téglalapot és egy zöld ellipszist, szép módon csoportosítva. Húzd a csoportot – mindkét alakzat együtt mozog, pontosan úgy, ahogy a felhasználói felületen is várnád.

> **Tipp:** Használd a `SaveFormat.PDF`-et, ha PDF verzióra van szükséged; ugyanaz a kód változtatás nélkül működik.

### ## Full Working Example and Common Pitfalls

Az alábbiakban a teljes, készen álló Java osztályt láthatod. Másold be a projektedbe, állítsd be a kimeneti mappát, és indítsd el a *Run* parancsot.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Gyakori hibák és hogyan kerüld el őket

| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| **`NullPointerException` on `builder`** | A `DocumentBuilder` példányosításának elhagyása a `Document` létrehozása után. | Győződj meg róla, hogy a `new DocumentBuilder(doc)` lefut a bármilyen alakzat beszúrása előtt. |
| **Az alakzatok az oldalról kívül jelennek meg** | Pixel értékek használata pontok helyett, vagy a margók figyelmen kívül hagyása. | Ne feledd, hogy az Aspose.Words pontokat vár; 72 pt = 1 in. Ennek megfelelően állítsd be a `setLeft`/`setTop` értékeket. |
| **A csoport a mentés után eltűnik** | Alakzatok hozzáadása a csoporthoz a mentés *után*. | Mindig csoportosíts a `doc.save()` hívása előtt. |
| **Fájl nem található mentéskor** | A kimeneti könyvtár nem létezik. | Hozd létre a könyvtárat programozottan (`new File("output").mkdirs();`) vagy használj egy már létező útvonalat. |

---

## Következtetés

Most már **create word document**-ot hoztunk létre a semmiből, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, és végül **save document as docx** – mindezt néhány Java sorral. Az Aspose.Words ereje a tiszta objektummodelljében rejlik; úgy kezelheted a Word fájlt, mint egy vásznat, rajzolhatsz rá alakzatokkal, majd exportálhatod, ahová csak szükséged van.

Kíváncsi vagy a további lehetőségekre? Próbáld ki a téglalap helyett egy csillag használatát, adj szöveget az alakzatok belsejébe a `Shape.getTextBox()` segítségével, vagy kísérletezz a forgatással (`shape.setRotationAngle(45)`). Az API gazdag, és a lehetőségek gyakorlatilag végtelenek.

Van kérdésed összetettebb szituációkkal kapcsolatban – például alakzatok összekapcsolása könyvjelzőkkel vagy PDF exportálás beágyazott betűtípusokkal? Írj egy megjegyzést alább, és együtt mélyedünk el benne. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépés‑ről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Csoport alakzat létrehozása Word dokumentumban Aspose.Words for .NET használatával](/words/english/net/working-with-shapes/add-group-shape/)
- [Téglalap alakzat létrehozása Word-ben Aspose.Words használatával – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
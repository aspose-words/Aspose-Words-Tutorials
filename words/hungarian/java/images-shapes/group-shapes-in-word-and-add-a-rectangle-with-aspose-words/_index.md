---
category: general
date: 2026-09-11
description: Csoportosítsa a formákat a Wordben, és adjon hozzá egy téglalap alakzatot
  az Aspose.Words for Java használatával. Ismerje meg, hogyan állíthatja be a forma
  méretét, csoportosíthatja az objektumokat, és mentheti a dokumentumot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: hu
lastmod: 2026-09-11
og_description: Csoportosítsa az alakzatokat a Wordben, és adjon hozzá egy téglalap
  alakzatot az Aspose.Words for Java segítségével. Ez az útmutató bemutatja, hogyan
  állítható be az alakzat mérete, hogyan csoportosíthatók az alakzatok, és hogyan
  exportálható a dokumentum.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Csoportos alakzatok a Wordben – téglalap hozzáadása az Aspose.Words segítségével
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Alakzatok csoportosítása a Wordben és téglalap hozzáadása az Aspose.Words segítségével
url: /hu/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Csoportosítsa a formákat a Word-ben, és adjon hozzá egy téglalapot az Aspose.Words segítségével

Ha **csoportosítja a formákat a Word-ben**, miközben programozottan ad egy téglalapot, ez az útmutató egy teljes, azonnal futtatható megoldást nyújt. Megmutatja pontosan, hogyan szúrjon be egy csoportos alakzatot, adjon hozzá egy téglalap alakzatot, állítsa be az alakzat méretét, és végül mentse a dokumentumot, hogy azonnal megtekinthesse az eredményt.

A Word-dokumentumokkal való munka gyakran azt jelenti, hogy több objektumot—képeket, diagramokat vagy egyszerű geometriai alakzatokat—rendezzünk egyetlen logikai egységbe. Az objektumok csoportosítása megkönnyíti azok mozgatását, forgatását vagy stílusozását együtt. Ebben az útmutatóban azt is bemutatjuk, hogyan **adjunk hozzá téglalap** alakzatokat és hogyan **állítsuk be az alakzat méretét** a tökéletes elrendezés-vezérléshez.

## Mit fog megtanulni

* Hogyan hozzon létre egy új Word-dokumentumot az Aspose.Words for Java segítségével.  
* **Hogyan csoportosítsa a formákat**, hogy egyetlen objektumként viselkedjenek.  
* **Téglalap alakzat hozzáadása** egy csoporthoz, és egy kép beszúrása ugyanabba a csoportba.  
* **Az alakzat méretének beállítása** a téglalap és a kép számára.  
* Mentse a dokumentumot, és nyissa meg a Microsoft Wordben az eredmény ellenőrzéséhez.  

### Előfeltételek

* Telepített Java 17 vagy újabb.  
* Maven vagy Gradle a függőségek kezeléséhez.  
* Érvényes Aspose.Words for Java licenc (vagy egy ingyenes értékelő kulcs).  
* Egy képfájl (`sample.png`) egy ismert könyvtárban elhelyezve (cserélje le a `YOUR_DIRECTORY`-t a saját útvonalára).  

---

## Hogyan csoportosítsa a formákat a Word-ben az Aspose.Words segítségével

Az első lépés egy `Document` és egy `DocumentBuilder` létrehozása. A builder kényelmes API-t biztosít a formák, szöveg és egyéb elemek beszúrásához.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Miért fontos:** A `DocumentBuilder` közvetlenül az alatta lévő `Document` objektummal dolgozik, lehetővé téve a formák beszúrását anélkül, hogy manuálisan kellene kezelni az alacsony szintű csomópont-gyűjteményeket.

### Csoportos alakzat hozzáadása

A csoportos alakzat egy tároló, amely más alakzatokat tartalmazhat. Tekintse úgy, mint egy mappát a rajzobjektumok számára.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Az `insertGroupShape()` metódus létrehoz egy `GroupShape` csomópontot, és visszaadja azt, hogy később gyermek alakzatokat fűzhessen hozzá.

---

## Téglalap alakzat hozzáadása a csoporthoz

Most **téglalap alakzatot adunk hozzá** az előzőleg létrehozott csoporthoz. A téglalap háttérként vagy keretként szolgál a képhez.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Tipp:** A `FillColor` és `StrokeColor` beállítása láthatóvá teszi a téglalapot a végső dokumentumban. Ha kihagyja ezeket a tulajdonságokat, az alakzat átlátszónak tűnhet.

### Hogyan adjon hozzá téglalapot

A fenti kód bemutatja, hogyan **adjunk hozzá téglalapot** egy `Shape` példány létrehozásával, amelynek a `ShapeType.RECTANGLE` típusa van, majd azt a `GroupShape`-hez fűzi. Ez a minta bármely más alakzat típusára is működik (pl. `ELLIPSE`, `POLYLINE`).

---

## Az alakzat méretének beállítása a téglalaphoz és a képhez

A megfelelő méretezés biztosítja, hogy a téglalap és a kép helyesen igazodjon. Itt továbbá **beállítjuk az alakzat méretét** a következőként beszúrandó képre.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

A téglalap és a kép most ugyanazokkal a méretekkel rendelkezik (100 × 50 pont). Mivel ugyanahhoz a csoporthoz tartoznak, a csoport mozgatása vagy forgatása mindkét alakzatot együtt érinti.

> **Miért egyezzenek a méretek?** A dimenziók igazítása garantálja, hogy a kép tisztán a téglalap belsejében helyezkedjen el, így létrehozva egy tiszta „keretezett kép” hatást.

---

## Dokumentum mentése és az eredmény megtekintése

Végül a dokumentumot lemezre írjuk. A fájl megnyitása a Microsoft Wordben a csoportosított alakzatokat egyetlen kiválasztható objektumként jeleníti meg.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Amikor megnyitja a `output.docx` fájlt, egy téglalapot fog látni a benne lévő képpel. A forma kattintásával mind a téglalap, mind a kép ki lesz jelölve, mivel **csoportosítva** vannak.

![csoportosított formák Word példája](https://example.com/images/group-shapes-word.png "csoportosított formák Word példája")

*Kép alternatív szövege:* *csoportosított formák Word példája* – egy Word-dokumentum, amely egy csoportosított téglalapot és képet mutat.

---

## Gyakori kérdések és szélsőséges esetek kezelése

| Kérdés | Válasz |
|----------|--------|
| **Mi van, ha a képnek más méretre van szükségem?** | A beszúrás után állítsa be a `picture.setWidth()` és `picture.setHeight()` értékeket. A téglalap megtarthatja eredeti méretét, vagy azt is átméretezheti, hogy egyezzen. |
| **Hozzáadhatok további alakzatokat ugyanahhoz a csoporthoz?** | Igen. Hívja a `group.appendChild(newShape)` metódust bármely további `Shape` objektumhoz. |
| **Hogyan forgatom el a teljes csoportot?** | Használja a `group.setRotationAngle(double angleInRadians)` metódust. A forgatás minden gyermek alakzatra érvényes. |
| **Mi van, ha a képfájl hiányzik?** | Az `insertImage` `FileNotFoundException`-t dob. A hívást tekerje try‑catch blokkba, és adjon meg egy tartalék helyőrző alakzatot. |
| **Lehet később felbontani a csoportot?** | Hívja a `group.removeAllChildren()` metódust a gyermekek leválasztásához, majd szúrja be őket egyenként a dokumentumba. |

---

## Következtetés

Most már egy teljes, futtatható példával rendelkezik, amely bemutatja, hogyan **csoportosítsa a formákat a Word-ben**, hogyan **adjon hozzá téglalap alakzatot**, hogyan **állítsa be az alakzat méretét**, és hogyan **mentse** a dokumentumot az Aspose.Words for Java használatával. A téglalap és a kép csoportosításával egy egységként mozgathatja, átméretezheti vagy forgathatja őket – pontosan azt, amire számos dokumentum‑automatizálási forgatókönyvnek szüksége van.

Innen tovább felfedezheti:

* Szövegdobozok hozzáadása ugyanahhoz a csoporthoz (`how to add rectangle`‑stílusú szöveg).  
* Különböző kitöltési minták vagy színátmenetek alkalmazása (`set shape size` kombinálva a stílusokkal).  
* Ugyanazon technika használata diagramok, táblázatok vagy SmartArt csoportosításához (`how to group shapes` más objektumtípusok között).  

Nyugodtan kísérletezzen más alakzat típusokkal, színekkel és elrendezési beállításokkal. Boldog kódolást!

## Mit érdemes következőként megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeiben.

- [Word-dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Űrlapmezők létrehozása és tartalom hozzáadása a DocumentBuilder segítségével az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word PDF‑re konvertálása az Aspose.Words for Java használatával](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
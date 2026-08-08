---
category: general
date: 2026-08-07
description: Üres Word-dokumentum létrehozása csoportosított alakzatokkal Java-ban
  az Aspose.Words segítségével. Ismerje meg, hogyan csoportosíthat alakzatokat, állíthatja
  be az alakzat méretét, és adhat hozzá alakzatokat a Word dokumentumhoz.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: hu
lastmod: 2026-08-07
og_description: Készíts üres Word dokumentumot csoportosított alakzatokkal Java-ban.
  Kövesd ezt az útmutatót az alakzat méretének beállításához, alakzatok Word-be való
  hozzáadásához, és a csoportosítás elsajátításához.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Üres Word-dokumentum létrehozása csoportosított alakzatokkal – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Üres Word-dokumentum létrehozása csoportosított alakzatokkal Java-ban
url: /hu/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása csoportosított alakzatokkal Java-ban

Ha **üres Word dokumentumot** szeretnél **létrehozni**, amely több alakzatot tartalmaz egy egységként, ez a bemutató pontosan megmutatja, hogyan. Látni fogsz egy teljes, futtatható példát, amely bemutatja, **hogyan csoportosítsuk** az alakzat‑objektumokat, módosítsuk a méreteiket, és **alakzatokat adjunk hozzá a Wordhöz** az Aspose.Words for Java segítségével.

Az útmutató minden lépést végigvezet – a projekt beállításától a végleges .docx fájl mentéséig – így a kódot közvetlenül beillesztheted a saját alkalmazásodba. Külső hivatkozásokra nincs szükség, a megoldás az Aspose.Words 23.9 vagy újabb verzióval működik.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következők rendelkezésre állnak:

* Java 17 (vagy bármely támogatott JDK)
* Maven vagy Gradle a függőségkezeléshez
* Aspose.Words for Java licenc (vagy ideiglenes értékelő kulcs)
* Egy minta képállomány (pl. `sample.jpg`) egy ismert könyvtárban

Ha valamelyik hiányzik, telepítsd előbb; a továbbiakban a környezet már készen áll.

## 1. lépés: Aspose.Words hozzáadása a projekthez

Add hozzá az Aspose.Words függőséget a `pom.xml`‑hez (Maven) vagy a `build.gradle`‑hez (Gradle). Ez a könyvtár biztosítja a később használt `Document`, `DocumentBuilder`, `GroupShape` és `Shape` osztályokat.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Miért fontos:** A könyvtár nélkül a Word‑feldolgozó API‑k nem érhetők el, és **nem hozhatsz létre programból üres Word dokumentumot**.

## 2. lépés: Üres Word dokumentum létrehozása

Az első konkrét művelet egy `Document` objektum példányosítása, amely a memóriában **üres Word dokumentumot** képvisel.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* egy **üres Word dokumentumot** hoz létre alapértelmezett beállításokkal (A4 oldal, alapértelmezett margók). A mellékelt `DocumentBuilder` lehetővé teszi, hogy tartalmat illessz be az aktuális kurzorpozícióba.

## 3. lépés: Csoportos alakzat beszúrása (hogyan csoportosítsunk alakzatot)

Egy *csoportos alakzat* más alakzatok számára tárolóként működik. Ebben a lépésben megtanulod, **hogyan csoportosítsd** az alakzat‑objektumokat, hogy együtt mozogjanak.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Az `insertGroupShape` metódus a tárolót a builder kurzorpozíciójába helyezi. A csoportosítás elengedhetetlen, ha több rajzot szeretnél egyetlen entitásként kezelni – ez a **group shapes word** funkció központja.

## 4. lépés: Téglalap létrehozása és méretének beállítása

Most adjunk egy téglalapot a csoporthoz. Ez bemutatja a **set shape size** műveletet, amely a pontos elrendezéshez szükséges.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Miért állítsuk be a méreteket?* Az `setWidth` és `setHeight` explicit hívása garantálja, hogy a téglalap pontosan úgy jelenjen meg, ahogy szeretnéd, függetlenül a dokumentum alapértelmezett alakzat‑stílusaitól.

## 5. lépés: Kép beszúrása és a csoporthoz adása

Kép hozzáadása egy másik gyakori felhasználási esetet mutat be a **add shapes to word** művelethez. A kép a csoport része lesz, és együtt mozog a téglalappal.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Ha a képállomány hiányzik, az Aspose.Words kivételt dob. Egy praktikus tipp: ellenőrizd előre az elérési utat:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## 6. lépés: A csoportos alakzatokat tartalmazó dokumentum mentése

Végül mentsd el a **üres Word dokumentumot** (most már csoportos alakzatokkal feltöltve) a lemezre.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Amikor megnyitod a `GroupShapeDemo.docx` fájlt a Microsoft Wordben, egyetlen csoportos objektumot látsz, amely egy téglalapot és egy képet tartalmaz. A csoport bármely részének kiválasztása az egész tárolót mozgatja, ezzel megerősítve, hogy az alakzatok helyesen **csoportosítva** lettek.

### Várt kimenet

* Egy `GroupShapeDemo.docx` nevű fájl a megadott könyvtárban.
* A fájl megnyitásakor egy 300 × 200 pont méretű tárolót látsz, amely:
  * Egy 100 × 50 pont méretű téglalapot tartalmaz a (20, 20) pozícióban.
  * Egy képet a (150, 30) pozícióban ugyanabban a tárolóban.

## Szélsőséges esetek és variációk

| Helyzet | Kezelési mód |
|-----------|-----------------|
| **Eltérő oldalméret** | Hívjuk a `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);`‑t a csoport beszúrása előtt. |
| **Több csoport** | Ismételjük meg a 3‑5. lépéseket egy új `GroupShape` példánnyal; minden csoport önállóan pozicionálható. |
| **Alakzatok forgatása** | Használjuk a `shape.setRotationAngle(45.0);`‑t a téglalap vagy kép forgatásához a csoporthoz való hozzáadás előtt. |
| **Nem‑képes alakzatok** | Hozzunk létre `Shape` objektumokat `ShapeType.ELLIPSE`, `ShapeType.LINE` stb. típusokkal, és adjuk hozzájuk ugyanúgy, mint a téglalapot. |
| **Nagy képek** | Méretezzük a képet a `picture.setWidth(80.0); picture.setHeight(60.0);` segítségével, hogy a csoport az eredeti határokon belül maradjon. |

Ezek a variációk lehetővé teszik, hogy a központi mintát különféle dokumentum‑generálási forgatókönyvekhez igazítsd.

## Gyakorlati tippek tapasztalatból

* **Pro tipp:** Állítsd be a csoport `RelativeHorizontalPosition` és `RelativeVerticalPosition` értékét `RelativeHorizontalPosition.PAGE`‑re és `RelativeVerticalPosition.PAGE`‑re, ha azt szeretnéd, hogy a csoport az oldalhoz legyen rögzítve, ne a kurzorhoz.
* **Vigyázz:** Ha olyan alakzatot adsz hozzá, amely meghaladja a csoport méretét, az alakzat Wordben levágásra kerül. Ennek elkerülése érdekében állítsd be a csoport méretét a `group.setWidth()` és `group.setHeight()` hívásokkal.
* **Teljesítményjegyzet:** Ha sok dokumentumot generálsz egy ciklusban, használd újra ugyanazt a `DocumentBuilder` példányt, és hívd a `doc.clone()`‑t az objektum‑létrehozási terhelés csökkentéséhez.

## Összegzés

Most már tudod, hogyan **hozz létre üres Word dokumentumot**, amely csoportos alakzatgyűjteményt tartalmaz az Aspose.Words for Java segítségével. A bemutató lefedte a teljes munkafolyamatot: a könyvtár beállítása, a dokumentum létrehozása, csoport beszúrása, **set shape size**, **add shapes to word**, és a végeredmény mentése.

Innen tovább felfedezheted a fejlettebb funkciókat, például diagramok csoportosítását, egyedi stílusok alkalmazását az alakzatokra, vagy a dokumentum PDF‑be exportálását. Mindegyik téma az itt bemutatott alapelveken épül.

---


## Mit tanulj meg legközelebb?


Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy könnyedén elsajátíthasd az API további funkcióit, és alternatív megvalósítási megközelítéseket is kipróbálhass a saját projektjeidben.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
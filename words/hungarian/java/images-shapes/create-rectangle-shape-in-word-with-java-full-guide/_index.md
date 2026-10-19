---
category: general
date: 2026-02-10
description: Hozzon létre téglalap alakzatot egy Word dokumentumban az Aspose.Words
  for Java segítségével. Tanulja meg, hogyan állíthatja be az árnyék színét, hogyan
  adhat hozzá árnyékot, és hogyan hozhat létre Word dokumentumot programozottan.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: hu
og_description: Hozzon létre téglalap alakzatot egy Word dokumentumban az Aspose.Words
  for Java használatával. Kövesse ezt a lépésről‑lépésre útmutatót az árnyékszín beállításához,
  árnyék hozzáadásához és a Word dokumentum létrehozásához.
og_title: Téglalap alakzat létrehozása a Wordben Java-val – Teljes útmutató
tags:
- Aspose.Words
- Java
- Document Automation
title: Téglalap alakzat létrehozása Wordben Java-val – Teljes útmutató
url: /hu/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Wordben Java‑val – Teljes útmutató

Valaha is szükséged volt **téglalap alakzat** létrehozására egy Word‑dokumentumban, de nem tudtad, hol kezdjed? Nem vagy egyedül — sok fejlesztő ütközik ebbe a falba, amikor először próbál programozottan grafikát rajzolni Wordben. A jó hír? Az Aspose.Words for Java‑val könnyedén elhelyezhetsz egy téglalapot az oldalon, szép árnyékot adhatsz hozzá, és néhány másodperc alatt elmentheted a fájlt. Ebben a tutorialban pontosan végigvezetünk **hogyan adhatunk árnyékot**, **hogyan állítható be az árnyék színe**, és **hogyan hozhatunk létre Word‑dokumentumot** nulláról.  

Mindent lefedünk, amire szükséged lesz: a szükséges könyvtárakat, minden kódsort, hogy miért fontosak bizonyos beállítások, és néhány trükköt, amit a hivatalos dokumentációban nem találhatsz. A végére egy kész, futtatható példát kapsz, amely egy téglalap alakzatot hoz létre lágy szürke árnyékkal, és *Shadow.docx* néven menti el.

## Előfeltételek – Amit a kezdés előtt szükséges

Mielőtt a kódba merülnénk, győződj meg róla, hogy a következőkkel rendelkezel:

| Követelmény | Indoklás |
|-------------|----------|
| Java Development Kit (JDK) 8 vagy újabb | Az Aspose.Words bármely modern JDK‑n fut. |
| Maven vagy Gradle (opcionális) | Egyszerűsíti az Aspose.Words függőség hozzáadását. |
| Aspose.Words for Java licenc (vagy ingyenes próba) | A könyvtár kereskedelmi, a próba verzió tesztelésre elegendő. |
| IDE (IntelliJ IDEA, Eclipse, VS Code, stb.) | Segít gyorsan futtatni és hibakeresni a példát. |

Ha már van egy Java projekted, csak add hozzá a Maven koordinátát:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Semmi bonyolult beállítás nincs – egy egyszerű `public static void main` metódus is elegendő.

![create rectangle shape example](https://example.com/rectangle-shadow.png "create rectangle shape with shadow in Word")

*Kép alt szöveg: téglalap alakzat példa, amely egy cián színű téglalapot mutat szürke árnyékkal.*

## 1. lépés – Új Word‑dokumentum létrehozása

Az első teendő egy üres dokumentum felpörgetése. Gondolj rá úgy, mint egy friss Word‑fájl megnyitására, amelyre később festeni fogsz.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Miért kezdünk egy üres `Document`‑tel? Mert az Aspose.Words a `Document` osztályt tekinti a vászonnak minden további művelethez — bekezdések, táblázatok vagy alakzatok hozzáadásához. Ha kihagyod ezt a lépést, már a legelső beszúráskor `NullPointerException`-t kapsz.

## 2. lépés – DocumentBuilder beállítása

A `DocumentBuilder` a barátságos tollad, amely a `Document`‑be ír. Ez az ajánlott mód a tartalom hozzáadására, mivel automatikusan kezeli a kurzor pozícióját.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Lehet, hogy azt kérdezed: „Miért ne manipulálnám közvetlenül a dokumentumot?” A válasz: a builder elrejti az alacsony szintű részleteket, például a szekciókezelést, így a kód tisztább és kevésbé hibára hajlamos.

## 3. lépés – Téglalap alakzat beszúrása

Most jön a szórakoztató rész — **hogyan hozzunk létre alakzatot**. Beszúrunk egy 100 × 50 pont méretű téglalapot, és cián kitöltést adunk neki, hogy látható legyen.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Néhány megjegyzés:

* `ShapeType.RECTANGLE` azt mondja az Aspose‑nak, hogy téglalapot akarunk; helyettesíthető `OVAL`, `LINE`, stb. értékekkel.
* A méretek pontban vannak megadva (1 pt ≈ 1/72 in). Igazítsd őket a saját elrendezésedhez.
* Kitöltőszín nélkül az alakzat láthatatlan maradna a fehér oldalon — ezért használunk ciánt.

## 4. lépés – Árnyék hozzáadása és **árnyék szín beállítása**

Itt válaszolunk a **hogyan adhatunk árnyékot** kérdésre. A `ShadowFormat` objektum vezérli az árnyék minden vizuális aspektusát, a színtől a elmosódási sugáron át.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Miért ezek az értékek?

* **Láthatóság** – `setVisible(true)` nélkül a többi beállítás figyelmen kívül marad.
* **Szín** – A szürke semleges választás, amely mind világos, mind sötét háttéren jól működik. Nyugodtan cseréld le a `java.awt.Color.GRAY`‑t bármely `java.awt.Color`‑ra, amit szeretnél.
* **Elmosódási sugár** – Az `5.0` érték enyhe szárnyas hatást ad; nagyobb számok diffúzabbá teszik az árnyékot.
* **OffsetX/Y** – Az eltolások jobbra és lejjebb tolják az árnyékot, mintha a fényforrás a bal‑felső sarokból jönne.
* **Átlátszóság** – Egy félig átlátszó árnyék jobban beleolvad az oldalba, különösen nyomtatáskor.

Ha élesebb megjelenést szeretnél, állítsd a blur radius‑t `0`‑ra, és növeld az offsetet. Kísérletezés ajánlott — az árnyékok erősen vizuális elemek, és a megfelelő beállítások a dokumentumod dizájnjától függenek.

## 5. lépés – Dokumentum mentése

Végül mindent elmentünk egy `.docx` fájlba. Bármilyen útvonalat választhatsz, csak győződj meg róla, hogy a könyvtár létezik.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Amikor megnyitod a *Shadow.docx*-t a Microsoft Word‑ben, egy cián téglalapot látsz egy finom szürke árnyékkal, amely 4 pt‑rel jobbra és lejjebb helyezkedik el. Ez a teljes **create word document** munkafolyamat.

### Várt eredmény

| Elem | Megjelenés |
|------|------------|
| Téglalap | Cián kitöltés, 100 × 50 pt méret |
| Árnyék | Szürke, 30 % átlátszó, 5 pt blur, eltolás (4, 4) |
| Fájl | `Shadow.docx` a megadott útvonalon tárolva |

Ha az alakzat nem jelenik meg, ellenőrizd, hogy a kitöltőszín nem egyezik-e az oldal háttérszínével, és hogy az árnyék látható‑re van‑állítva.

## Profi tippek és gyakori buktatók

* **Pro tip:** Használd a `rectangle.setStrokeColor(java.awt.Color.BLACK);`‑t, ha szegélyt szeretnél az alakzatra. Ez jobban kiemeli a téglalapot nyomtatott oldalon.
* **Vigyázz:** Írás egy csak‑olvasható mappába `IOException`‑t dob. Válassz írható helyet, vagy módosítsd a fájlengedélyeket.
* **Szélhelyzet:** Ha átlátszó kitöltést (nincs szín) akarsz, hívd a `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`‑t. Az alakzat továbbra is vet árnyékot, ami vízjel‑stílusú grafikáknál hasznos lehet.
* **Teljesítmény:** Több száz alakzat hozzáadása egy ciklusban növelheti a memóriahasználatot. A `document.save`‑t csak egyszer hívd meg, miután az összes alakzatot beszúrtad.

## Teljes működő példa

Az alábbiakban az egész programot láthatod, amelyet egyszerűen bemásolhatsz egy `ShadowDemo` nevű Java‑osztályba. Fordítható és futtatható (ha az Aspose.Words JAR a classpath‑on van).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Futtasd a programot, nyisd meg a keletkezett *Shadow.docx*-t, és a leírtaknak megfelelően megjelenik a téglalap árnyékkal.

## Mit tegyünk, ha több alakzatot szeretnénk?

Lehet, hogy azt kérdezed: „Létrehozhatok‑e **téglalap alakzatot** többször, vagy használhatok‑e más alakzatokat?” Természetesen. Csak ismételd meg a beszúrási kódot egy ciklusban, és állítsd be a koordinátákat a `builder.moveTo` vagy a `builder.insertParagraph` segítségével. Ugyanazokat az árnyékbeállításokat újra‑felhasználhatod egy segédmetódusba kiemelve:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Hívd meg az `applyStandardShadow(rectangle);`‑t minden alakzat beszúrása után, hogy a kód DRY (Don’t Repeat Yourself) maradjon.

## Következő lépések – Túl a alapokon

Most, hogy tudod **hogyan adjunk árnyékot**, érdemes megismerned ezeket a kapcsolódó témákat:

* **Hogyan állítható be az árnyék színe** szövegrészekhez – finom emelést ad a címeknek.
* **Create word document** táblázatokkal és képekkel – kombináld az alakzatokat más tartalommal.
* **Hogyan hozható létre alakzat** animáció a Word beépített lehetőségeivel

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
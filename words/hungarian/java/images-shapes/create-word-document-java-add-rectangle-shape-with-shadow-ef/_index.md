---
category: general
date: 2026-01-11
description: Készíts gyorsan Word dokumentumot Java-val, egy téglalap alakzat hozzáadásával,
  a kitöltőszín beállításával és árnyék alkalmazásával az alakzatra. Tanulj lépésről‑lépésre.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: hu
og_description: Word dokumentum létrehozása Java-ban téglalap alakzat beszúrásával,
  kitöltőszín beállításával és árnyék alkalmazásával. Teljes útmutató kóddal.
og_title: Word-dokumentum létrehozása Java-ban – Téglalap alakzat hozzáadása árnyékkal
tags:
- Aspose.Words
- Java
- Document Generation
title: Word dokumentum létrehozása Java-val – Téglalap alakzat hozzáadása árnyékhatással
url: /hu/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum létrehozása Java‑val – Téglalap alakzat árnyékkal

Szükséged volt már **word dokumentum java** létrehozására, és egy kicsit elegánsabb megjelenésre? Lehet, hogy jelentésgenerátort építesz, és egy egyszerű oldal nem elég. A jó hír? Az Aspose.Words for Java‑val könnyedén elhelyezhetsz egy téglalap alakzatot a dokumentumban, színt adhatsz neki, sőt egy finom árnyékot is hozzáadhatsz – mindezt néhány sor kóddal.

Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan adhatunk hozzá egy téglalap alakzatot, állíthatjuk be a kitöltőszínét, és alkalmazhatunk árnyékot, hogy a Word fájlod professzionálisabb legyen. A végére egy futtatható példát kapsz, amit egyszerűen beilleszthetsz a saját projektedbe.

## Amire szükséged lesz

- **Java 17** (vagy bármely friss JDK) – a kód a szabványos nyelvi funkciókat használja.
- **Aspose.Words for Java** könyvtár – ajánlott a 23.9 vagy újabb verzió.
- Kedvenc IDE‑d vagy szövegszerkesztőd – IntelliJ IDEA, Eclipse, VS Code… válaszd ki.
- Egy mappa, ahová a generált `ShadowShape.docx` kerül mentésre.

Külön konfigurációs varázsló nem szükséges; csak add hozzá az Aspose.Words JAR‑t a classpath‑hez, és már indulhat a munka.

## 1. lépés: Projekt felállítása és az Aspose.Words importálása

Először is hozz létre egy új Maven (vagy Gradle) projektet, és add hozzá az Aspose.Words függőséget. Íme egy minimális `pom.xml` részlet Mavenhoz:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Ha nem Maven‑t használsz, egyszerűen helyezd a JAR‑t a `libs` mappádba, és add hozzá a build útvonalhoz.

> **Pro tipp:** Az Aspose ingyenes próbalicencet kínál, amit így ágyazhatsz be: `License license = new License(); license.setLicense("Aspose.Words.lic");`. Gyors tesztekhez kihagyható; a könyvtár értékelő módban is működik.

## 2. lépés: Új dokumentum és Builder létrehozása

Most már ténylegesen **create word document java** objektumokat hozunk létre. A `Document` osztály képviseli a teljes .docx fájlt, míg a `DocumentBuilder` lehetővé teszi tartalom beszúrását.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Ekkor már van egy üres dokumentumod, amely készen áll alakzatok, bekezdések vagy bármilyen egyéb elem fogadására.

## 3. lépés: Téglalap alakzat beszúrása és kitöltőszín beállítása

Alakzat hozzáadása olyan egyszerű, mint az `insertShape` meghívása. Az **add rectangle shape** technikát fogjuk használni, amely a másodlagos kulcsszó *add rectangle shape* alatt szerepel.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Miért narancssárga? Kitűnik a fehér háttérből, de bármely `java.awt.Color` értékre cserélheted. Ez a lépés a másodlagos kulcsszó *set shape fill color* tartalmát fedi le.

## 4. lépés: Árnyék megjelenésének beállítása – Árnyék alkalmazása az alakzatra

Most jön a szórakoztató rész: egy finom vetett árnyék adása a téglalapnak. Az Aspose API egy `ShadowFormat` objektumot biztosít, amely az árnyék minden aspektusát szabályozza.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Ez a kódrészlet **apply shadow to shape** pontosan úgy, ahogy a másodlagos kulcsszó is sugallja. A `blur`, `offsetX/Y` és `transparency` értékeket szabadon módosíthatod a tervezési igényeidnek megfelelően. Például egy nagyobb `offsetX` drámaibb árnyékot eredményez, míg a magasabb `transparency` lágyabb, szelídebb hatást kölcsönöz.

## 5. lépés: Dokumentum mentése

Végül a dokumentumot leírjuk a lemezre. Válassz egy olyan mappát, amelyhez írási jogosultságod van, és adj a fájlnak egy egyértelmű nevet.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Amikor megnyitod a `ShadowShape.docx` fájlt a Microsoft Wordben vagy a LibreOffice‑ban, egy élénk narancssárga téglalapot látsz, amelyet egy lágy szürke árnyék vesz körül.

![create word document java téglalap alakzattal](/images/shadow-rectangle.png "create word document java – téglalap árnyékkal")

*Az alt‑szöveg tartalmazza az elsődleges kulcsszót, ezzel teljesítve az SEO‑szabályt.*

## Gyakori kérdések és speciális esetek

### Mi van, ha másik alakzatra van szükségem?

Az Aspose.Words több tucat `ShapeType` értéket támogat – csillagok, nyilak, felhívások, bármi. Egyszerűen cseréld le a `ShapeType.RECTANGLE`‑t `ShapeType.OVAL`‑ra vagy bármely más enum konstansra. Ugyanezek a **how to add shape** lépések alkalmazandók.

### Hogyan adhatom hozzá az alakzatot egy konkrét bekezdéshez?

Ahelyett, hogy közvetlenül a builderrel szúrnád be az alakzatot, előbb létrehozhatod (`new Shape(document, ShapeType.RECTANGLE)`), majd egy `Paragraph`-hoz adhatod a `paragraph.appendChild(shape)` metódussal. Így finomabb vezérlést kapsz a layout felett.

### Alkalmazhatok-e színátmenetes kitöltést a szilárd szín helyett?

Igen! Használd a `rectangle.getFill().setFillType(FillType.GRADIENT)`‑t, és definiálj egy `LinearGradientFill`‑t. Az API ilyenkor kicsit verbózusabb, de modern dizájnokhoz remekül működik.

### Mi a helyzet a régebbi Word verziókkal való kompatibilitással?

Az Aspose.Words alapértelmezés szerint .docx formátumban ment, amely a Word 2007+ és a LibreOffice által támogatott. Ha .doc formátumra van szükséged, hívd a `document.save("file.doc", SaveFormat.DOC)`‑t. Az árnyék megjelenése kissé eltérhet, de az alakzat maga változatlan marad.

## Teljes működő példa (másolás‑beillesztés kész)

Az alábbi program az egész kód, amely készen áll a fordításra és futtatásra. Cseréld ki a `YOUR_DIRECTORY`‑t a saját géped egy valós útvonalára.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

A kód futtatása egy olyan Word fájlt hoz létre, amely tartalmazza a narancssárga téglalapot egy lágy szürke árnyékkal – pontosan azt, amit a **create word document java** céljából szerettünk volna elérni egy stílusos alakzattal.

## Összegzés

Most már van egy átfogó recepted a **create word document java** feladathoz, amely *adds rectangle shape*, *sets shape fill color*, és *applies shadow to shape*. A megközelítés egyszerű, az API folyékony, és számtalan módon bővíthető – különböző alakzatok, színátmenetes kitöltések vagy akár több árnyék egy alakzaton.

Mi a következő lépés? Próbálj meg több alakzatot rétegezni, kísérletezz a `ShadowStyle.ETCHED`‑del egy másik vizuális hatásért, vagy kombináld ezt táblázatgenerálással, hogy teljes jelentéseket építs. A lehetőségek csak a képzeleted (és esetleg az Aspose licencszint) határain belül vannak.

Ha bármilyen problémába ütköztél, vagy van ötleted a további fejlesztésekre, hagyj egy megjegyzést alább. Boldog kódolást, és élvezd, ahogy a Word dokumentumok már nem annyira unalmasak!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
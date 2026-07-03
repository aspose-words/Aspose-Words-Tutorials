---
category: general
date: 2026-07-03
description: Hozzon létre téglalap alakzatot Java-ban, és tanulja meg, hogyan adjon
  árnyékot az alakzathoz, alkalmazzon árnyékhatást, állítsa be az alakzat átlátszóságát,
  valamint gyorsan hozzon létre üres dokumentumot.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: hu
og_description: Készítsen téglalap alakzatot Java-ban árnyékkal, átlátszósággal és
  egy üres dokumentummal. Kövesse ezt az útmutatót, hogy elsajátítsa az alakzatkezelést.
og_title: Téglalap alak létrehozása Java-ban – Teljes programozási útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Téglalap alak létrehozása Java-ban – Teljes lépésről‑lépésre útmutató
url: /hu/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Java‑ban – Teljes lépésről‑lépésre útmutató

Gondolkodtál már azon, hogyan **hozz létre téglalap alakzatot** egy Word‑dokumentumban Java‑val? Nem vagy egyedül – a fejlesztők gyakran keresnek gyors megoldást geometriai grafikák hozzáadására, majd egy finom árnyékot adnak nekik, hogy a megjelenés kifinomultabb legyen. Ebben a tutorialban végigvezetünk a teljes folyamaton: a **blank dokumentum létrehozásától** a **árnyék hozzáadásáig**, az **árnyék effektus alkalmazásáig**, sőt a **alakzat átlátszóságának beállításáig** a professzionális hatás érdekében.

Az alábbi kódrészlet egy teljesen működő példa, amelyet egyszerűen beilleszthetsz a projektedbe. Nem szükséges külső dokumentáció – csak kövesd a lépéseket, értsd meg a „miért” kérdést, és néhány másodperc alatt árnyékolt téglalapokat generálhatsz.

## Mit fogsz megtanulni

- Hogyan **hozz létre téglalap alakzatot** programozottan az Aspose.Words for Java‑val.
- A pontos hívásokat, amelyekkel **árnyékot adsz az alakzathoz** és konfigurálod a vizuális tulajdonságait.
- Módokat az **árnyék effektus alkalmazására** és a paraméterek, például eltolás, elmosódási sugár és szín finomhangolására.
- Technikákat a **alakzat átlátszóságának beállításához** a visszafogottabb megjelenés érdekében.
- Hogyan **hozz létre üres dokumentumot**, szúrd be az alakzatot, és mentsd el az eredményt.

> **Pro tipp:** Mindez egyetlen `Document` példányon történik, ami azt jelenti, hogy láncolhatod őket anélkül, hogy köztes fájl‑I/O‑ra kellene gondolnod.

## Előfeltételek

Mielőtt belevágnánk, győződj meg róla, hogy a következők telepítve vannak:

- Java 17 (vagy bármely friss JDK) a gépeden.
- Aspose.Words for Java könyvtár hozzáadva a projekthez (Maven koordináták: `com.aspose:aspose-words:23.12`).
- Java IDE vagy egyszerű szövegszerkesztő – semmi különleges, csak egy hely a fordításhoz és a futtatáshoz.

Ha valamelyik hiányzik, töltsd le a JDK‑t az Oracle‑tól, és húzd be az Aspose függőséget Maven‑nel vagy Gradle‑lel. Ha ez megvan, már készen állsz a munkára.

## 1. lépés: **Blank dokumentum létrehozása** – a vászon mindenhez

Az első dolog, amire szükséged van, egy üres `Document` objektum. Gondolj rá úgy, mint egy friss papírra; nélküle nincs hova helyezned a téglalapot.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Miért kezdünk egy üres dokumentummal? Mert minden alakzat egy `Section`‑en belül él, és egy újonnan példányosított `Document` már tartalmaz egy alapértelmezett szekciót egy testtel, amely készen áll a node‑ok fogadására. Ennek kihagyása azt jelentené, hogy később manuálisan kell szekciókat létrehoznod, ami felesleges bonyodalmat okoz.

## 2. lépés: **Téglalap alakzat létrehozása** és méretének meghatározása

Most, hogy megvan a vászon, **hozzunk létre egy téglalap alakzatot**. A `Shape` osztály a dokumentum referenciáját és egy `ShapeType`‑ot vár. Itt a `RECTANGLE`‑t választjuk, és a szélességet/magasságot pontban állítjuk be (1 pt ≈ 1/72 inch).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Miért állítjuk be a `WrapType.INLINE`‑t? Az inline csomagolás azt eredményezi, hogy az alakzat úgy viselkedik, mint egy karakter a bekezdésben, biztosítva, hogy a környező szöveggel együtt mozogjon. Ha lebegő viselkedésre van szükséged, válts `WrapType.SQUARE`‑ra vagy `WrapType.TOP_BOTTOM`‑ra.

## 3. lépés: **Árnyék effektus alkalmazása** – mélység a téglalapnak

Egy lapos téglalap… nos, lapos. Egy árnyék hozzáadása életre kelti. **Árnyék effektust** úgy alkalmazzuk, hogy létrehozunk egy `ShadowEffect` példányt, majd finomhangoljuk a vizuális tulajdonságait.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Nézzük meg részletesen:

- **Color** – a `Color.getGray(0.5)` 50 % szürke árnyalatot ad, ami semleges és a legtöbb háttérrel jól működik.
- **OffsetX/Y** – Pozitív értékek jobbra és lejjebb tolják az árnyékot; negatív értékek balra/felé mozgatnák.
- **BlurRadius** – Nagyobb értékek lágyabb, szórtabb árnyékot eredményeznek.
- **Transparency** – 0‑tól 1‑ig terjed (0 = átlátszatlan, 1 = teljesen átlátszó). Itt a `0.3`‑at választottuk egy visszafogott hatáshoz.

## 4. lépés: **Árnyék hozzáadása az alakzathoz** – az effektus kötése

Az effektus létrehozása önmagában nem elég; **árnyékot kell adni az alakzathoz** a `ShadowEffect` objektum hozzárendelésével a téglalaphoz.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

A háttérben ez a hívás frissíti a Word által használt OpenXML markup‑ot (`<w:shdw>`), amely az árnyékok megjelenítéséért felel. Ha megnézed a mentett `.docx`‑et, láthatod a `<w:effect>` elemet a beállított paraméterekkel.

## 5. lépés: **Alakzat átlátszóságának beállítása** – opcionális, de gyakran hasznos

Néha szeretnéd, ha a téglalap maga is részben átlátszó lenne, hogy a háttérben lévő szöveg látható maradjon. A `Shape` osztály a `setFillColor` és a `setFillTransparency` metódusokat kínálja. Íme egy gyors példa, amely a téglalapot 40 % átlátszóvá teszi:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Miért lehet erre szükség? Képzeld el egy vízjelet vagy egy kiemelt megjegyzést, ahol a mögöttes tartalomnak olvashatónak kell maradnia. Állítsd a transparencia értékét a tervezési stílusodnak megfelelően.

## 6. lépés: Az alakzat beszúrása a dokumentumba

Már felépítettük a téglalapot, hozzáadtuk az árnyékot, és (opcionálisan) beállítottuk az átlátszóságát. Az utolsó lépés, hogy **az alakzatot hozzáadjuk a dokumentum első szekciójához**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Az alakzat a testhez való hozzáfűzése a első bekezdés végére helyezi. Ha konkrét beillesztési pontot szeretnél, szerezd be a cél `Paragraph`‑t, és használd az `insertBefore` vagy `insertAfter` metódusokat.

## 7. lépés: Dokumentum mentése – az eredmény megtekintése

Minden munka egyetlen `save` hívásban csúcsosodik. Válassz egy olyan útvonalat, amely a környezetednek megfelel.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Nyisd meg a keletkezett `ShadowShape.docx`‑et a Microsoft Word‑ben vagy a LibreOffice‑ban, és egy tiszta téglalapot látsz egy enyhe szürke árnyékkal, amely opcionálisan átlátszó, ha az előző lépést alkalmaztad. A vizuális megjelenés megegyezik a programból definiált paraméterekkel.

---

![create rectangle shape with shadow in a Word document](https://example.com/images/rectangle-shadow.png "create rectangle shape with shadow")

*Kép alternatív szövege:* **téglalap alakzat létrehozása árnyékkal** – a végső kimenet vizuális ábrázolása.

## Gyakori kérdések és széljegyek

### Mi van, ha más árnyék színt szeretnék?

Egyszerűen módosítsd a `setColor` hívást:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Ne feledd, hogy a túl élénk árnyékok professzionálisan nem hatnak; a visszafogott tónusok általában a legjobbak.

### Alkalmazhatom ugyanazt az árnyékot több alakzatra?

Igen. Hozz létre egy `ShadowEffect` példányt, konfiguráld, majd használd újra:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Csak kerüld el a `ShadowEffect` módosítását miután már más alakzatokhoz is hozzárendelted, hacsak nem akarod, hogy mindegyik frissüljön.

### Hogyan változtathatom dinamikusan az árnyék elmosódását?

Készíts egy UI csúszkát, amely a `setBlurRadius`‑ra map‑el. A `2` és `12` közötti értékek tipikusak; nagyobb számok „glow” hatást adnak a tiszta árnyék helyett.

### Mi a teendő, ha az alakzatnak lebegőnek kell lennie, nem inline?

Cseréld le a wrap típust:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

A lebegő alakzatok nagyobb elrendezési szabadságot biztosítanak, de extra pozicionálási logikát igényelnek.

## Teljes működő példa

Az alábbi program teljesen másolható‑beilleszthető kód, amely tartalmazza a korábban bemutatott összes lépést. Futtasd egyszerű Java‑alkalmazásként.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Várható kimenet:** Amikor megnyitod a `ShadowShape.docx`‑et, egy fehér téglalapot látsz, 200 × 100 pt mérettel, a első bekezdés közepén, közepes‑szürke árnyékkal, amely 5 pt‑el el van tolva, 8‑as sugárral elmosódott, és 30 % átlátszó. A téglalap maga 40 % átlátszó, így az alatta lévő szöveg részben látható.

## Összegzés

Most már **téglalap alakzatot hoztunk létre** a semmiből, **árnyékot adtunk az alakzathoz**, **árnyék effektust alkalmaztunk**, sőt **beállítottuk az alakzat átlátszóságát** – mindezt egy **blank dokumentum** alapjával. A megközelítés egyszerű, az Aspose.Words folyékony API‑jára épül, és könnyen kiterjeszthető körökre, csillagokra vagy egyedi sokszögekre.

Mi legyen a következő lépés a tervben? Próbáld ki a `ShapeType.RECTANGLE` helyett a `ShapeType.OVAL`‑t, hogy árnyékolt köröket generálj, vagy kísérletezz gradient kitöltésekkel.

## Mit tanulj meg legközelebb?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy további API‑funkciókat saját projektjeidben is elsajátíthasd és alternatív megvalósítási módokat felfedezhess.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
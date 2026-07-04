---
category: general
date: 2026-05-26
description: Hozzon létre egy téglalap alakzatot egy Java Word dokumentumban, és alkalmazzon
  árnyékhatást. Tanulja meg, hogyan adjon hozzá alakzati árnyékot, állítsa be az árnyék
  távolságát, és mentse el a fájlt.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: hu
og_description: Hozzon létre egy téglalap alakzatot egy Java Word dokumentumban, alkalmazzon
  árnyékhatást, adjon hozzá árnyékot az alakzathoz, és állítsa be az árnyék távolságát
  az Aspose.Words segítségével.
og_title: Téglalap alakzat létrehozása Java Word dokumentumban – Teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Téglalap alakzat létrehozása Java Word dokumentumban – Teljes lépésről‑lépésre
  útmutató
url: /hu/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Java Word dokumentumban – Teljes lépésről‑lépésre útmutató

Valaha is szükséged volt **téglalap alakzat létrehozására** egy Java Word dokumentumban, de nem tudtad, hol kezdjed? Nem vagy egyedül – sok fejlesztő ütközik ebbe a problémába, amikor programozottan generál jelentéseket vagy számlákat. Ebben az útmutatóban pontosan bemutatjuk, hogyan **téglalap alakzat létrehozása**, alkalmazz egy kifinomult árnyékot, és finomhangold az árnyék távolságát, hogy a végeredmény professzionális legyen.

Az Aspose.Words for Java-t fogjuk használni, egy robusztus könyvtárat, amely lehetővé teszi a Word fájlok manipulálását anélkül, hogy a Microsoft Office telepítve lenne. A útmutató végére képes leszel **create word document java** projekteket készíteni, amelyek **add shape shadow**, **apply shadow effect**, és **set shadow distance** néhány kódsorral.

---

## Amit építeni fogsz

- Egy új `.docx` fájl, amely egy cián színű téglalapot tartalmaz.
- Egy valósághű vetett árnyék, amely elmosott, szögelt és részben átlátszó.
- Teljes irányítás az árnyék alakzattól való távolsága felett.
- Egy azonnal futtatható Java osztály, amelyet bármely Maven vagy Gradle projektbe beilleszthetsz.

Nincs külső eszköz, nincs manuális UI lépés – csak tiszta kód.

---

## Előfeltételek

- Java 8 vagy újabb (a kód működik Java 11, Java 17 stb. verziókon).
- Aspose.Words for Java könyvtár (elérhető a Maven Centralon).
- Egy kedvenc IDE vagy szövegszerkesztő (IntelliJ IDEA, Eclipse, VS Code …).
- Alapvető ismeretek a Java szintaxisról.

Ha még sosem adtál hozzá Maven függőséget, itt egy gyors kódrészlet:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Most merüljünk el.

---

## 1. lépés: Téglalap alakzat létrehozása Word dokumentumban

Az első dolog, amire szükségünk van, egy üres dokumentum és egy `DocumentBuilder`. Tekintsd a buildert egy tollra, amely a dokumentumba ír. Miután megvan, egyetlen metódushívással **create rectangle shape**-t hozhatunk létre.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Miért fontos:** Az `insertShape` metódus nem csak a geometriát hozza létre, hanem hozzáadja az alakzatot a dokumentum belső gyűjteményéhez is, így azonnal elkezdheted formázni azt.

---

## 2. lépés: Árnyékhatás alkalmazása az alakzatra

Miután a téglalap a lapon megjelenik, **apply shadow effect**-et fogunk alkalmazni. Az árnyékok mélységet adnak, az alakzatot úgy érzik, mintha a lapról kiemelkedne – egy finom UI fejlesztés, amely javíthatja a jelentések olvashatóságát.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Pro tipp:** A `5.0` elmosás természetesnek tűnik a legtöbb képernyőn megjelenített dokumentumnál. Ha nyomtatod, érdemes egy kicsit alacsonyabb értéket választani, hogy elkerüld a homályos megjelenést.

---

## 3. lépés: Árnyék távolság beállítása – Finomhangolás

Az árnyékok nem csak az elmosásról szólnak; a megfelelő eltolásra is szükség van. Itt jön képbe a **set shadow distance**. A `7.0` pont távolság mérsékelt eltolást eredményez, amely észrevehető, de nem túl erőteljes.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **Mi van, ha nagyobb eltolásra van szükséged?** Növeld az értéket; csökkentsd, ha szorosabb megjelenést szeretnél. Ne feledd, a távolság az szöggel együtt határozza meg az árnyék helyzetét.

---

## 4. lépés: Dokumentum mentése – A munka mentése

Végül a dokumentumot leírjuk a lemezre. Módosítsd az elérési utat arra a helyre, ahol a fájlt tárolni szeretnéd.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

Az osztály futtatása létrehozza a `shadow.docx` fájlt, amely Microsoft Wordben vagy LibreOffice‑ban megnyitva egy cián téglalapot mutat egy lágy szürke árnyékkal, 45°‑os szöggel és 7 pont eltolással.

---

## Teljes működő példa

Az alábbiakban a teljes, másolás‑és‑beillesztésre készen álló kód található. Tartalmazza az összes importot, megjegyzést és a végső `save` hívást.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Várható kimenet:** Nyisd meg a `shadow.docx` fájlt → egy cián téglalapot látsz az első oldal közepén, amely egy finom szürke árnyékot vet, amely enyhén a jobb‑alsó sarok felé van eltolva. Az árnyék elmosása és átlátszósága természetes fényhatást kölcsönöz.

---

## Gyakori kérdések és speciális esetek

### „Használhatok másik alakzatot?”

Természetesen. Cseréld le a `ShapeType.RECTANGLE`-t `ShapeType.OVAL`, `ShapeType.LINE` vagy bármely más támogatott enumra. A többi árnyék kód változatlan marad.

### „Mi van, ha több árnyékra van szükségem?”

Az Aspose.Words csak egy árnyékot támogat alakzatonként. Több árnyék szimulálásához duplikáld az alakzatot, minden másolatot eltolva, és állítsd be az átlátszóságot.

### „Látható az árnyék a LibreOffice‑ban?”

Igen – az Aspose.Words szabványos OOXML-et ír, amelyet a LibreOffice helyesen értelmez. Az árnyék kissé másként jelenhet meg a renderelő motorok miatt, de a hatás megmarad.

### „Hogyan változtassam meg az árnyék színét a márkámhoz igazodva?”

Egyszerűen cseréld le a `java.awt.Color.GRAY`-t bármely általad preferált `java.awt.Color`-ra, például `new java.awt.Color(0, 120, 215)`-ra egy vállalati kékhez.

---

## Kép illusztráció

![create rectangle shape in Java Word document](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** illusztráció, amely egy cián téglalapot mutat szürke vetett árnyékkal egy Word dokumentumban.

---

## Összefoglalás és következő lépések

Áttekintettük, hogyan kell **create rectangle shape**, **apply shadow effect**, **add shape shadow**, és **set shadow distance** az Aspose.Words for Java segítségével. A kód önálló, bármely modern JDK-n fut, és egy kifinomult `.docx` fájlt állít elő, amely készen áll a terjesztésre.

Szeretnél tovább menni? Próbáld ki:

- Szöveg hozzáadása a téglalap belsejébe a `builder.moveTo(rectangleShape.getAbsolutePosition())` segítségével.
- Alakzatok táblázatának létrehozása egy diagram felépítéséhez.
- A dokumentum PDF‑be exportálása (`doc.save("output.pdf", SaveFormat.PDF);`).

Ezek mind a most megismert alapokra épülnek, így magabiztosan tudod bővíteni a példát.

---

## Záró gondolatok

A **create word document java** feladatok, például az alakzatok és árnyékok elsajátítása óriási előnyt jelent a jelentések, szerződések vagy marketing anyagok automatizálásában. A bemutatott megközelítés tiszta, karbantartható, és – ami a legfontosabb – könnyen testreszabható bármilyen vizuális stílushoz.

Próbáld ki a kódot, állítsd be az elmosást, a szöget és a távolságot, és nézd, ahogy a dokumentumaid a közönségesből a kifinomulttá változnak. Ha elakadsz, hagyj megjegyzést alul; szívesen segítek.

Boldog kódolást!

## Kapcsolódó oktatóanyagok

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Űrlapmezők létrehozása és tartalom hozzáadása DocumentBuilderrel az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [PDF létrehozása Wordből vonalkód generálással – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
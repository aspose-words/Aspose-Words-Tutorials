---
category: general
date: 2026-02-15
description: Hozzon létre téglalap alakzatot egy Word dokumentumban Java használatával.
  Tanulja meg, hogyan adjon hozzá alakzati árnyékot, mentse a Word dokumentumot, és
  adjon hozzá téglalap alakzatot az Aspose.Words segítségével.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: hu
og_description: Hozzon létre téglalap alakzatot egy Word-fájlban Java-val. Ez az útmutató
  bemutatja, hogyan adjon árnyékot az alakzathoz, mentse el a Word-dokumentumot, és
  lépésről lépésre adjon hozzá téglalap alakzatot.
og_title: Téglalap alakzat létrehozása – Java Aspose.Words útmutató
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

# Téglalap alakzat létrehozása Word-ben Java-val – Teljes útmutató

Valaha szükséged volt **téglalap alakzat** létrehozására egy Word fájlban, de nem tudtad, hol kezdj? Nem vagy egyedül – sok fejlesztő szembesül ezzel a problémával jelentések vagy számlák automatizálásakor. A jó hír? Az Aspose.Words for Java segítségével néhány sorban létrehozhatsz egy téglalapot, adhatod hozzá egy szép árnyékot, és elmentheted a Word dokumentumot.

Ebben az útmutatóban mindent végigvezetünk, amire szükséged van: egy üres dokumentum inicializálásától, az árnyék beállításáig, egészen a fájl mentéséig. A végére megtudod, **hogyan árnyékolj alakzatot**, hogyan **adj hozzá alakzat árnyékot**, és hogyan **adj hozzá téglalap alakzatot** bármely általad generált Word dokumentumhoz. Nincs szükség külső dokumentumokra – csak tiszta, futtatható kód.

## Prerequisites

- Java 8 vagy újabb (az API Java 11+ verzióval is működik).  
- Aspose.Words for Java könyvtár (23.9 vagy újabb verzió).  
- IDE, például IntelliJ IDEA vagy Eclipse – bármelyik megfelel.  
- Alapvető ismeretek a Java szintaxisában.

> **Pro tip:** Ha Maven-t használsz, add hozzá az Aspose.Words függőséget a `pom.xml`-hez, és hagyd, hogy az IDE a többit kezelje.

---

## Step 1: Initialize a New Document – How to **create rectangle shape**  

Először is szükséged van egy tiszta vászonra. Az Aspose.Words-ben ez a vászon egy `Document` objektum.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

A `Document` osztály képviseli a teljes .docx fájlt. Gondolj rá úgy, mint egy jegyzetfüzetre, ahová később **téglalap alakzatot** és annak árnyékát fogod **hozzáadni**.

## Step 2: Build the Rectangle – **Add rectangle shape**  

Most ténylegesen felépítjük a téglalapot. Beállítjuk a méretét, elrendezését és kitöltőszínét.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Miért `INLINE` csomagolás? Mert azt akarjuk, hogy az alakzat úgy viselkedjen, mint egy bekezdés – tökéletes egyszerű jelentésekhez. Később, ha szöveget szeretnél körülfolyatni az alakzat körül, átállíthatod `TOPBOTTOM`-ra.

## Step 3: Apply a Shadow – **How to shadow shape**  

Egy lapos téglalap kissé unalmas. Az árnyék hozzáadása mélységet kölcsönöz, és a dokumentumot kifinomultabbá teszi. Itt válaszolunk a “**hogyan árnyékolj alakzatot**” kérdésre a gyakorlatban.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Minden tulajdonság valami konkrétat csinál:

- `setVisible(true)` bekapcsolja az árnyékot.  
- `setColor` egy sötétszürke színt választ a finom hatáshoz.  
- `setBlurRadius` szabályozza, mennyire lágyak a szélek.  
- `setOffsetX/Y` jobbra és lefele mozgatja az árnyékot, egy fényforrást utánozva.  
- `setTransparency` enyhén átlátszóvá teszi, így a forma marad a főszereplő.

> **Note:** Ha színes árnyékra van szükséged, egyszerűen adj át egy másik `java.awt.Color` értéket a `setColor`-nek.

## Step 4: Insert the Shape into the Document  

A téglalap és az árnyéka készen áll, most beillesztjük a dokumentum első szakaszába.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

A testhez való hozzáfűzés azt a helyet teszi az alakzatot, ahol egy új bekezdés lenne. Ha a téglalapot egy konkrét helyre szeretnéd, használhatod a `insertBefore`-t vagy manipulálhatod a `Paragraph` gyűjteményt.

## Step 5: **Save Word document** – Persist Your Work  

Az utolsó lépés a fájl lemezre írása. Ez az a pillanat, amikor ténylegesen **Word dokumentumot mentünk**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Cseréld le a `YOUR_DIRECTORY`-t a gépeden lévő abszolút vagy relatív útvonalra. A program futtatása után nyisd meg a `ShadowShape.docx`-et a Microsoft Wordben – egy világosszürke téglalapot kell látnod egy lágy sötét árnyékkal.

![Diagram, amely egy Aspose.Words segítségével létrehozott téglalap alakzatot árnyékkal mutat](https://example.com/rectangle-shadow.png "téglalap alakzat létrehozása árnyékkal")

---

## Common Questions & Edge Cases  

### Mi van, ha több téglalapra van szükségem?  

Csak ismételd meg **Step 2**-t és **Step 3**-at egy ciklusban, minden iterációban állítva a `setWidth`, `setHeight` vagy `setFillColor` értékét. Ne felejts egyedi változóneveket adni minden alakzatnak, vagy tárold őket egy listában.

### Exportálhatok PDF-be a DOCX helyett?  

Természetesen. Az alakzat hozzáadása után hívd meg a `document.save("output.pdf")` metódust. Az Aspose.Words elvégzi a konverziót, megőrizve az árnyékot.

### Mi a helyzet a régebbi Word verziókkal?  

Használd a `document.save("file.doc", SaveFormat.DOC)` túlterhelést. Az API automatikusan lejjebb verzióra konvertálja a funkciókat, de vedd figyelembe, hogy egyes árnyékstílusok kissé eltérhetnek a régi formátumokban.

### Hogyan változtathatom meg az árnyék irányát?  

Manipuláld a `setOffsetX` és `setOffsetY` értékeket. Pozitív X jobbra, negatív balra mozgatja az árnyékot. Pozitív Y lefelé, negatív felfelé. Kísérletezz ezekkel a számokkal, hogy bármilyen szögből származó fényforrást szimulálj.

---

## Tips for Working with Shapes  

- **Group shapes**: Ha a téglalap mellett címkét is szeretnél, hozz létre egy `GroupShape`-et, és add hozzá mind a téglalapot, mind egy `TextBox`-ot.  
- **Z‑order matters**: Használd a `shape.moveToFront()` vagy `shape.moveToBack()` metódusokat, hogy szabályozd, melyik alakzat jelenik meg felül.  
- **Performance**: Több száz alakzat hozzáadása lassú lehet. Csoportosítsd őket egyetlen szakaszba, majd a végén egyszer hívd meg a `document.updatePageLayout()`-ot.

---

## Recap  

Áttekintettük, hogyan **téglalap alakzatot** hozhatsz létre egy Word dokumentumban Java-val, hogyan **adj hozzá alakzat árnyékot**, és hogyan **Word dokumentumot mentünk** az eredménnyel. A teljes, futtatható kód a fenti snippet-ekben található, és most már érted a tulajdonságok „miértjét” – így színeket, elmosódást és eltolásokat tetszés szerint módosíthatsz bármilyen dizájnhoz.

Készen állsz a következő kihívásra? Próbáld meg kombinálni a téglalapot egy diagrammal, vagy exportáld a fájlt PDF-be, és nézd meg, hogyan jelenik meg az árnyék. Érdemes lehet **téglalap alakzatot** táblázatokon belül is felfedezni a látványos jelentéselrendezésekhez.

Boldog kódolást, és legyenek a dokumentumaid mindig olyan élesek, mint a kódod!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
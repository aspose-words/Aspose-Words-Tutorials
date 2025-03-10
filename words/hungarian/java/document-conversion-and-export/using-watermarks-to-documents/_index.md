---
title: Vízjelek használata dokumentumokhoz az Aspose.Words for Java programban
linktitle: Vízjelek használata dokumentumokhoz
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan adhat vízjeleket a dokumentumokhoz az Aspose.Words for Java programban. Testreszabhatja a szöveges és képi vízjeleket a professzionális megjelenésű dokumentumokhoz.
weight: 15
url: /hu/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vízjelek használata dokumentumokhoz az Aspose.Words for Java programban


## Bevezetés a vízjelek hozzáadásához a dokumentumokhoz az Aspose.Words for Java programban

Ebben az oktatóanyagban megvizsgáljuk, hogyan adhatunk vízjeleket a dokumentumokhoz az Aspose.Words for Java API használatával. A vízjelek hasznos módot jelentenek a dokumentumok szöveges vagy grafikai címkézésére, amelyek jelzik állapotukat, bizalmasságukat vagy egyéb releváns információkat. Ebben az útmutatóban a szöveges és képi vízjelekre is kitérünk.

## Az Aspose.Words for Java beállítása

Mielőtt elkezdenénk vízjeleket adni a dokumentumokhoz, be kell állítanunk az Aspose.Words for Java programot. A kezdéshez kövesse az alábbi lépéseket:

1.  Az Aspose.Words for Java letöltése innen[itt](https://releases.aspose.com/words/java/).
2. Adja hozzá az Aspose.Words for Java könyvtárat a Java projekthez.
3. Importálja a szükséges osztályokat a Java kódjába.

Most, hogy a könyvtárat beállítottuk, folytassuk a vízjelek hozzáadásával.

## Szöveg vízjelek hozzáadása

A szöveges vízjelek gyakori választások, ha szöveges információkat kívánnak hozzáadni a dokumentumokhoz. A következőképpen adhat hozzá szöveges vízjelet az Aspose.Words for Java használatával:

```java
// Hozzon létre egy dokumentumpéldányt
Document doc = new Document("Document.docx");

// Adja meg a TextWatermark Options beállításait
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//Állítsa be a vízjel szövegét és beállításait
doc.getWatermark().setText("Test", options);

// Mentse el a dokumentumot vízjellel
doc.save("DocumentWithWatermark.docx");
```

## Kép vízjelek hozzáadása

A szöveges vízjelek mellett képes vízjeleket is hozzáadni a dokumentumokhoz. A következőképpen adhat hozzá vízjelet a képhez:

```java
// Hozzon létre egy dokumentumpéldányt
Document doc = new Document("Document.docx");

// Töltse be a képet a vízjelhez
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Állítsa be a vízjel méretét és helyzetét
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Adja hozzá a vízjelet a dokumentumhoz
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Mentse el a dokumentumot vízjellel
doc.save("DocumentWithImageWatermark.docx");
```

## Vízjelek testreszabása

Testreszabhatja a vízjeleket megjelenésük és helyzetük módosításával. Szöveges vízjeleknél módosíthatja a betűtípust, a méretet, a színt és az elrendezést. A képi vízjelek méretét és helyzetét az előző példákban bemutatott módon módosíthatja.

## Vízjelek eltávolítása

A vízjelek dokumentumból való eltávolításához a következő kódot használhatja:

```java
// Hozzon létre egy dokumentumpéldányt
Document doc = new Document("DocumentWithWatermark.docx");

// Távolítsa el a vízjelet
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Mentse el a dokumentumot vízjel nélkül
doc.save("DocumentWithoutWatermark.docx");
```


## Következtetés

Ebben az oktatóanyagban megtanultuk, hogyan adhatunk vízjeleket dokumentumokhoz az Aspose.Words for Java használatával. Akár szöveges, akár képi vízjeleket kell hozzáadnia, az Aspose.Words eszközöket biztosít azok hatékony testreszabásához és kezeléséhez. A vízjeleket is eltávolíthatja, amikor már nincs rájuk szükség, így biztosítva, hogy dokumentumai tiszták és professzionálisak legyenek.

## GYIK

### Hogyan változtathatom meg a szöveges vízjel betűtípusát?

 A szöveges vízjel betűtípusának módosításához módosítsa a`setFontFamily` ingatlan a`TextWatermarkOptions`. Például:

```java
options.setFontFamily("Times New Roman");
```

### Hozzáadhatok több vízjelet egyetlen dokumentumhoz?

 Igen, több vízjelet is hozzáadhat egy dokumentumhoz, ha több vízjelet hoz létre`Shape` objektumokat különböző beállításokkal, és hozzáadjuk őket a dokumentumhoz.

### Lehetséges a vízjel elforgatása?

 Igen, elforgathatja a vízjelet a beállításával`setRotation` ingatlan a`Shape` objektum. A pozitív értékek az óramutató járásával megegyező, a negatív értékek pedig az óramutató járásával ellentétes irányba forgatják el a vízjelet.

### Hogyan lehet a vízjelet félig átlátszóvá tenni?

 A vízjel félig átlátszóvá tételéhez állítsa be a`setSemitransparent`tulajdonát`true` a`TextWatermarkOptions`.

### Hozzáadhatok vízjelet a dokumentum bizonyos részeihez?

Igen, hozzáadhat vízjelet a dokumentum bizonyos részeihez úgy, hogy a szakaszokon áthalad, és vízjelet ad a kívánt részekhez.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
"description": "Tanuld meg, hogyan adhatsz hozzá vízjeleket dokumentumokhoz az Aspose.Words for Java programban. Testreszabhatod a szöveges és képes vízjeleket professzionális megjelenésű dokumentumokhoz."
"linktitle": "Vízjelek használata dokumentumokon"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Vízjelek használata dokumentumokon az Aspose.Words for Java programban"
"url": "/hu/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vízjelek használata dokumentumokon az Aspose.Words for Java programban


## Bevezetés a vízjelek dokumentumokhoz való hozzáadásába az Aspose.Words for Java programban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan adhatunk hozzá vízjeleket dokumentumokhoz az Aspose.Words for Java API segítségével. A vízjelek hasznos módja annak, hogy szöveggel vagy grafikával címkézzük fel a dokumentumokat, jelezve azok állapotát, bizalmas jellegét vagy más releváns információkat. Ebben az útmutatóban mind a szöveges, mind a képes vízjeleket tárgyaljuk.

## Az Aspose.Words beállítása Java-hoz

Mielőtt elkezdenénk vízjeleket hozzáadni a dokumentumokhoz, be kell állítanunk az Aspose.Words Java-t. A kezdéshez kövesd az alábbi lépéseket:

1. Töltsd le az Aspose.Words programot Java-hoz innen: [itt](https://releases.aspose.com/words/java/).
2. Add hozzá az Aspose.Words for Java könyvtárat a Java projektedhez.
3. Importálja a szükséges osztályokat a Java kódjába.

Most, hogy beállítottuk a könyvtárat, folytassuk a vízjelek hozzáadásával.

## Szöveges vízjelek hozzáadása

A szöveges vízjelek gyakori választás, ha szöveges információkat szeretne hozzáadni a dokumentumokhoz. Így adhat hozzá szöveges vízjelet az Aspose.Words for Java használatával:

```java
// Dokumentumpéldány létrehozása
Document doc = new Document("Document.docx");

// TextWatermarkOptions definiálása
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Állítsa be a vízjel szövegét és beállításait
doc.getWatermark().setText("Test", options);

// Mentse el a dokumentumot vízjellel együtt
doc.save("DocumentWithWatermark.docx");
```

## Kép vízjelek hozzáadása

A szöveges vízjelek mellett képi vízjeleket is hozzáadhat a dokumentumaihoz. Így adhat hozzá képi vízjelet:

```java
// Dokumentumpéldány létrehozása
Document doc = new Document("Document.docx");

// Töltsd be a vízjel képét
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Állítsa be a vízjel méretét és pozícióját
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Vízjel hozzáadása a dokumentumhoz
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Mentse el a dokumentumot vízjellel együtt
doc.save("DocumentWithImageWatermark.docx");
```

## Vízjelek testreszabása

vízjeleket testreszabhatja megjelenésük és pozíciójuk módosításával. Szöveges vízjelek esetén módosíthatja a betűtípust, a méretet, a színt és az elrendezést. Képes vízjelek esetén módosíthatja a méretüket és a pozíciójukat, ahogy az az előző példákban látható.

## Vízjelek eltávolítása

A vízjelek dokumentumból való eltávolításához a következő kódot használhatja:

```java
// Dokumentumpéldány létrehozása
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

Ebben az oktatóanyagban megtanultuk, hogyan adhatunk hozzá vízjeleket dokumentumokhoz az Aspose.Words for Java segítségével. Akár szöveges, akár képes vízjeleket kell hozzáadnunk, az Aspose.Words eszközöket biztosít a testreszabásukhoz és hatékony kezelésükhöz. A vízjeleket el is távolíthatjuk, amikor már nincs rájuk szükségünk, így biztosítva, hogy dokumentumaink tiszták és professzionálisak legyenek.

## GYIK

### Hogyan tudom megváltoztatni egy szöveges vízjel betűtípusát?

A szöveges vízjel betűtípusának módosításához módosítsa a `setFontFamily` ingatlan a `TextWatermarkOptions`Például:

```java
options.setFontFamily("Times New Roman");
```

### Hozzáadhatok több vízjelet egyetlen dokumentumhoz?

Igen, több vízjelet is hozzáadhat egy dokumentumhoz több vízjel létrehozásával `Shape` objektumok különböző beállításokkal, és azok hozzáadása a dokumentumhoz.

### Lehetséges elforgatni egy vízjelet?

Igen, elforgathatja a vízjelet a beállítással. `setRotation` ingatlan a `Shape` objektum. A pozitív értékek az óramutató járásával megegyezően, a negatív értékek pedig az óramutató járásával ellentétesen forgatják a vízjelet.

### Hogyan tehetek félig átlátszóvá egy vízjelet?

A vízjel félig átlátszóvá tételéhez állítsa be a `setSemitransparent` ingatlan `true` a `TextWatermarkOptions`.

### Hozzáadhatok vízjelet egy dokumentum bizonyos részeihez?

Igen, hozzáadhat vízjeleket a dokumentum adott szakaszaihoz úgy, hogy végigmegy a szakaszokon, és a kívánt szakaszokhoz adja hozzá a vízjelet.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
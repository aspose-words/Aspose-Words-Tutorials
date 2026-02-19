---
date: 2026-02-19
description: Ismerje meg, hogyan hozhat létre vízjeles dokumentumot az Aspose.Words
  for Java segítségével, és hogyan adhat hozzá képi vízjelet Java-ban a professzionális
  megjelenésű dokumentumokhoz.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Dokumentum létrehozása vízjellel az Aspose.Words for Java segítségével
url: /hu/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

.

Also note "For Hungarian, ensure proper RTL formatting if needed" - Hungarian is LTR, ignore.

Now produce final answer.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentum létrehozása vízjellel az Aspose.Words for Java használatával

Ebben az oktatóanyagban **dokumentumot hoz létre vízjellel** az Aspose.Words for Java API segítségével. A vízjelek—legyenek azok szövegesek vagy képek—segítenek egy fájlt titkosnak, tervezetnek vagy jóváhagyottnak jelölni, és programozottan alkalmazhatók bármely Word dokumentumra. Lépésről lépésre bemutatjuk a könyvtár beállítását, a szöveges és képes vízjelek hozzáadását, megjelenésük testreszabását, valamint azok eltávolítását, ha már nincs rájuk szükség.

## Gyors válaszok
- **Mi a vízjel funkciója?** Szöveget vagy képet helyez el minden oldalon, hogy állapotot vagy márkát jelezzen.  
- **Melyik könyvtár ad hozzá vízjeleket Java-ban?** Az Aspose.Words for Java beépített vízjel‑támogatást biztosít.  
- **Hozzáadhatok képes vízjelet?** Igen—használja a `Shape` osztályt és az `add image watermark java` megközelítést.  
- **A vízjel félig átlátszó?** A szöveges vízjelek esetén az átlátszóságot a `setSemitransparent` segítségével szabályozhatja.  
- **Szükségem van licencre?** A ingyenes próbaverzió teszteléshez megfelelő; a termeléshez kereskedelmi licenc szükséges.

## Mi a vízjel és miért használjuk?

A vízjel egy halvány átfedés—szöveges vagy grafikus—amely minden dokumentumoldalra kerül. Általában a **titoktartás**, **tervezet állapot** vagy **márka** jelzésére használják anélkül, hogy a tartalmat módosítaná. A vízjelek programozott hozzáadása biztosítja a konzisztenciát nagy mennyiségű fájl esetén, és időt takarít meg a kézi szerkesztéshez képest.

## Az Aspose.Words for Java beállítása

Mielőtt elkezdenénk a vízjelek hozzáadását, győződjön meg róla, hogy a könyvtár készen áll a projektben:

1. Töltse le az Aspose.Words for Java-t innen: [here](https://releases.aspose.com/words/java/).  
2. Adja hozzá a letöltött JAR-t (vagy Maven/Gradle függőséget) a projekt classpath-jához.  
3. Importálja a szükséges osztályokat a Java forrásfájlban:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Miután a könyvtár be van állítva, merüljünk el a tényleges vízjelkódba.

## Hogyan adjunk hozzá szöveges vízjelet

A szöveges vízjelek ideálisak egy dokumentum „CONFIDENTIAL” vagy „DRAFT” jelzésére. Az alábbi kódrészlet egy tiszta módot mutat a **dokumentum létrehozása vízjellel** a `TextWatermarkOptions` használatával.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### A szöveges vízjel testreszabása
- **Betűtípus és méret** – módosítsa a `setFontFamily` és `setFontSize` értékeket.  
- **Szín** – használjon bármilyen `java.awt.Color`-t.  
- **Elrendezés** – válassza a `HORIZONTAL`, `DIAGONAL` stb.  
- **Átlátszóság** – kapcsolja be a `setSemitransparent(true)`-t a könnyebb megjelenéshez.

## Hogyan adjunk hozzá képes vízjelet (add image watermark java)

A képes vízjelek tökéletesek logók vagy egyedi grafikák számára. Az alábbi **add image watermark java** példa egy PNG-t helyez el minden oldal közepén.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### Tippek a képes vízjelekhez
- **Átméretezés** a `setWidth` / `setHeight` használatával, hogy illeszkedjen az oldalhoz.  
- **Pozíció** középre vagy bármely margóhoz igazítható a `RelativeHorizontalPosition` / `RelativeVerticalPosition` segítségével.  
- **Átlátszóság** a kép alfa csatornájának beállításával alkalmazható betöltés előtt.

## Hogyan távolítsuk el a vízjeleket

Ha egy dokumentumnak már nincs szüksége a vízjelre, programozottan törölheti azt. Az alábbi kód végigiterál az összes alakzaton, és eltávolítja azokat, amelyek nevében szerepel a „Watermark”.

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Gyakori hibák és hibaelhárítás

- **Hiányzó vízjel mentés után** – győződjön meg róla, hogy a vízjel beállítása után meghívja a `doc.save()`-t.  
- **A kép nem jelenik meg** – ellenőrizze, hogy a kép útvonala helyes, és a fájl támogatott formátumú (PNG, JPEG, BMP).  
- **Az átlátszóság nem alkalmazódik** – a `setSemitransparent(true)` csak szöveges vízjelekre működik; képek esetén szerkessze a PNG alfa csatornáját.  
- **Több szakasz** – ha a dokumentumnak több szekciója van, adja hozzá a vízjelet minden szakasz testhez, vagy használja a `doc.getWatermark().setText(...)`-t, amely globálisan alkalmazza.

## Gyakran Ismételt Kérdések

**K: Hogyan változtathatom meg egy szöveges vízjel betűtípusát?**  
Válasz: Módosítsa a `setFontFamily` tulajdonságot a `TextWatermarkOptions`-ben, például `options.setFontFamily("Times New Roman");`.

**K: Hozzáadhatok több vízjelet egy dokumentumhoz?**  
Válasz: Igen. Hozzon létre több `Shape` objektumot (képekhez), vagy hívja meg a `doc.getWatermark().setText(...)`-t különböző opciókkal minden vízjelhez.

**K: Lehetőség van a vízjel elforgatására?**  
Válasz: Képes vízjelek esetén állítsa be a forgatást a `Shape` objektumon a `watermark.setRotation(angle)` használatával. Szöveges vízjelekhez használja a `setLayout` tulajdonságot (pl. `WatermarkLayout.DIAGONAL`).

**K: Hogyan tehetem a vízjelet félig átlátszóvá?**  
Válasz: Állítsa be a `options.setSemitransparent(true)`-t a `TextWatermarkOptions`-ben. Képek esetén állítsa be a kép átlátszóságát betöltés előtt.

**K: Hozzáadhatok vízjeleket a dokumentum egyes szakaszaihoz?**  
Válasz: Igen. Iteráljon a `doc.getSections()`-en, és csak a kívánt szakaszokhoz adja hozzá a vízjelet.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-02-19  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose
---
date: 2026-10-23
description: Tanulja meg, hogyan készítsen QR code Java címkéket az Aspose.Words segítségével.
  Ez a lépésről‑lépésre útmutató megmutatja, hogyan ágyazzon be barcodes a Word documentsba,
  és testreszabja a size, colors és formatot.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Egyedi Barcode címkék generálása
og_description: Tanulja meg, hogyan készítsen QR code Java címkéket az Aspose.Words
  segítségével. Ez az útmutató bemutatja a barcode beágyazását, a size szabályozását
  és a color testreszabását a Word documentsban.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Hogyan készítsünk QR code Java címkéket az Aspose.Words segítségével
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Hogyan készítsünk QR code Java címkéket az Aspose.Words segítségével
url: /hu/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre QR kód Java címkéket az Aspose.Words segítségével

A vonalkódok elengedhetetlenek a modern alkalmazásokban – legyen szó készletkezelésről, jegyek nyomtatásáról vagy személyi igazolványok készítéséről. Ebben az útmutatóban **create QR code Java** címkéket hozunk létre, és közvetlenül egy Word dokumentumba ágyazzuk be az `IBarcodeGenerator` interfész segítségével. Lépésről lépésre végigvezetünk a környezet beállításától a vonalkód kép beillesztéséig, így azonnal használhatod a vonalkódokat Java projektjeidben.

## Gyors válaszok
- **Mit tanít ez az útmutató?** Hogyan hozzunk létre QR kód Java címkéket, és ágyazzuk be őket egy Word fájlba az Aspose.Words for Java segítségével.  
- **Melyik vonalkód típust használja a példa?** QR kód (bármelyik, a 20+ támogatott típus közül cserélhető).  
- **Szükségem van licencre?** Ideiglenes licenc szükséges a fejlesztés során korlátlan hozzáféréshez.  
- **Milyen Java verzió szükséges?** JDK 8 vagy újabb.  
- **Módosíthatom a vonalkód méretét vagy színeit?** Igen – módosítsa a `BarcodeParameters` és `BarcodeGenerator` beállításait.

## Mi az a create QR code Java?
`create QR code Java` arra utal, hogy QR‑kód képet generálunk programozottan egy Java környezetben, és beillesztjük egy dokumentumba vagy UI komponensbe. Az Aspose.Words for Java az Aspose.BarCode-dal együtt lehetővé teszi a kép teljes memóriában történő előállítását, elkerülve az ideiglenes fájlokat.

## Miért generáljunk egyedi vonalkód címkéket az Aspose.Words segítségével?
Az Aspose.Words **35+ bemeneti és kimeneti formátumot** támogat, és **500 oldalas dokumentumokat 3 másodperc alatt** képes feldolgozni szabványos szerverhardveren. A memóriában történő vonalkód generálásával teljes kontrollt kapsz a típus, méret és színek felett, miközben a munkafolyamat teljesen Java‑központú és platform‑független marad.

## Előkövetelmények

- Java Development Kit (JDK): 8-as vagy újabb verzió.  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse vagy bármely kedvelt IDE.  
- Temporary License: Szerezzen be egy [temporary license](https://purchase.aspose.com/temporary-license/) licencet a korlátlan hozzáféréshez.

## Csomagok importálása

Az Aspose.Words és Aspose.BarCode könyvtárakat fogjuk használni. Importálja a következő csomagokat a projektbe:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Ezek az importok hozzáférést biztosítanak a vonalkód generálás API-hoz és a szükséges Word dokumentum osztályokhoz.

## 1. lépés: segédosztály létrehozása a vonalkód műveletekhez

A segédosztály újrahasználható segédfüggvényeket tartalmaz, például **convert twips to pixels** és **hex‑color conversion**.  
A `CustomBarcodeGeneratorUtils` osztály statikus metódusokat biztosít az egységkonverzióhoz és a színkezeléshez.

### Code

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Magyarázat**  
- `twipsToPixels` – A Word a méreteket **twips**‑ben méri; ez a metódus átkonvertálja őket képernyőpixelekre, ami akkor hasznos, ha pontosan kell méretezni a vonalkód képet.  
- `convertColor` – Hexadecimális karakterláncot (pl. `"FF0000"` a piroshoz) `java.awt.Color` objektummá alakít, lehetővé téve, hogy **add barcode to Word document** egyedi előtér‑ és háttérszínekkel.

## 2. lépés: az egyedi vonalkód generátor implementálása

Most implementáljuk az `IBarcodeGenerator` interfészt. Ez az osztály felelős a **generate QR code Java**‑stílusú képek előállításáért, amelyeket az Aspose.Words be tud ágyazni.  
Az `IBarcodeGenerator` interfész egyetlen metódust definiál, amely egy `BufferedImage`‑et ad vissza, ami a vonalkódot ábrázolja.

### Code

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Magyarázat**  
- `getBarcodeImage` példányosít egy `BarcodeGenerator`‑t, a `BarcodeParameters`‑ben megadott színeket alkalmazza, majd visszaad egy `BufferedImage`‑et.  
- A metódus hibák esetén is elegánsan kezeli a helyzetet, egy helyőrző képet ad vissza, így a Word dokumentum létrehozása nem omlik össze.

## Hogyan ágyazzuk be a vonalkódot a Word dokumentumba az Aspose.Words segítségével?

Töltsük be a Word fájlt a `new Document("template.docx")` (vagy hozzunk létre egy új `Document`) segítségével, majd hívjuk meg a `builder.insertImage`‑t a generátor által visszaadott vonalkód képpel. Ez a kétlépéses minta közvetlenül beágyazza a vonalkódot anélkül, hogy köztes fájlt írna a lemezre. A kép méreteinek pixelben történő megadásával vagy a Word twips‑ek pixelre konvertálásával pontosan szabályozhatja a vonalkód méretét és elhelyezését a dokumentumban, biztosítva a professzionális elrendezést, amely minden nyomtatón helyesen nyomtat.

## 3. lépés: vonalkód generálása és beágyazása a Word dokumentumba

A generátor készen áll, most előállíthatunk egy vonalkód képet és **insert it into a Word document**.

### Code

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Magyarázat**  

1. **Document initialization** – Létrehoz egy új `Document`‑et (vagy betölthet egy meglévő sablont).  
2. **Barcode parameters** – Meghatározza a vonalkód típusát (`QR`), a kódolandó értéket, valamint az előtér‑ és háttérszíneket.  
3. **Image insertion** – A `builder.insertImage` a generált vonalkódot a kívánt méretben (200 × 200 pixel) helyezi el. Ez a **how to embed barcode in Word** központi része.  
4. **Saving** – A végleges dokumentum, `CustomBarcodeLabels.docx`, tartalmazza a beágyazott vonalkódot, készen áll a nyomtatásra vagy terjesztésre.

## Gyakori problémák és hibaelhárítás

| Tünet | Valószínű ok | Megoldás |
|---------|--------------|-----|
| Barcode appears blank | `BarcodeParameters` színek azonosak (pl. fekete a feketével) | Ellenőrizze a `foregroundColor` és `backgroundColor` értékeket. |
| Image is distorted | Helytelen pixelméretek lettek megadva az `insertImage`‑nek | Állítsa be a szélesség/magasság argumentumokat, vagy használja a `twipsToPixels` konverziót a pontos méretezéshez. |
| Unsupported barcode type error | Olyan típus használata, amelyet a `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` nem ismer | Győződjön meg róla, hogy a vonalkód típus karakterlánca egyezik a támogatott `EncodeTypes` egyikével (pl. `"QR"`, `"CODE128"`). |

## Gyakran ismételt kérdések

**Q: Használhatom az Aspose.Words for Java‑t licenc nélkül?**  
A: Igen, de korlátozott értékelési funkciókkal rendelkezik. Szerezzen be egy [temporary license](https://purchase.aspose.com/temporary-license/) licencet a teljes funkcionalitáshoz.

**Q: Milyen típusú vonalkódokat generálhatok?**  
A: Az Aspose.BarCode támogatja a QR, Code 128, EAN‑13, DataMatrix, PDF417 és sok más formátumot – összesen több mint 20 szimbólumot. Tekintse meg a [documentation](https://reference.aspose.com/words/java/)‑t a teljes listáért.

**Q: Hogyan változtathatom meg a vonalkód méretét?**  
A: Állítsa be a szélesség és magasság argumentumokat a `builder.insertImage`‑nél, vagy számolja ki a pontos Word twips‑eket a `twipsToPixels` használatával a pixel‑tökéletes kontroll érdekében.

**Q: Lehet-e egyedi betűtípusokat használni a vonalkód szövegéhez?**  
A: Igen, a `CodeTextParameters` tulajdonságon keresztül testreszabhatja a szöveg betűtípusát a `BarcodeGenerator`‑ben.

**Q: Hol kaphatok segítséget, ha problémába ütközöm?**  
A: Látogassa meg a [support forum](https://forum.aspose.com/c/words/8/)‑ot, ahol az Aspose közösség és mérnökök segítenek.

## Következtetés

A fenti lépések követésével most már tudja, hogyan **create QR code Java** képeket készítsen, és hogyan **embed barcode in Word** dokumentumokat használja az Aspose.Words for Java‑val. Ez a technika elég rugalmas készletcímkék, eseményjegyek vagy bármely olyan eset számára, ahol a vonalkódnak része kell lennie a generált dokumentumnak. Kísérletezzen különböző vonalkód típusokkal, színekkel és méretbeállításokkal, hogy megfeleljen a saját üzleti igényeinek.

---

**Last Updated:** 2026-10-23  
**Tested With:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Author:** Aspose

## Kapcsolódó útmutatók

- [Create PDF from Word with Barcode Generation – Aspose.Words for Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Save Word As Pdf With Aspose Words Step By Step Java Guide](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Create Blank Word Document In Java With Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
---
category: general
date: 2026-02-18
description: Tanulja meg, hogyan konvertálja a DOCX-et PDF-be, és mentse a Word dokumentumot
  PDF-ként, miközben megőrzi a lebegő alakzatokat. Ez az útmutató megmutatja, hogyan
  exportálja helyesen az alakzatokat.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: hu
og_description: Konvertálja a DOCX-et PDF-re, és tanulja meg, hogyan exportálja az
  alakzatokat. Kövesse ezt a teljes útmutatót, hogy a Word dokumentumot megfelelő
  címkézéssel PDF-be mentse.
og_title: DOCX konvertálása PDF-re – Beágyazott alakzat exportálási útmutató
tags:
- Aspose.Words
- Java
- PDF conversion
title: DOCX konvertálása PDF-re beágyazott alakzat exportálással – Lépésről‑lépésre
  útmutató
url: /hu/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX konvertálása PDF‑re – Beágyazott alakzatok exportálási útmutató

Szükséged volt már **DOCX PDF‑re konvertálására**, de attól tartottál, hogy a lebegő képek vagy szövegdobozok eltűnnek vagy elmozdulnak? Nem vagy egyedül. Sok projektben – gondolj az automatikus jelentésgenerátorokra vagy a kötegelt feldolgozási csővezetékekre – a Word‑dokumentum pontos elrendezésének megőrzése elengedhetetlen.

A jó hír? Néhány kódsorral **Word‑et menthetsz PDF‑ként**, és szabályozhatod, hogy a lebegő alakzatok beágyazott címkék legyenek vagy blokkszintű elemek maradjanak. Az alábbiakban pontosan **hogyan exportálj alakzatokat** a kívánt módon, valamint néhány tippet találsz, amelyek megakadályozzák a gyakori buktatókat.

---

## Mit fogsz megtanulni

* `.docx` fájl betöltése lemezről.  
* `PdfSaveOptions` konfigurálása úgy, hogy a lebegő alakzatok beágyazott címkék legyenek.  
* A keletkezett PDF mentése a kívánt mappába.  
* Megérteni, miért fontos a `setExportFloatingShapesAsInlineTag` kapcsoló, és mikor érdemes átállítani.

Nincs külső szolgáltatás, nincs varázslatos „kattints‑letöltés” UI – csak tiszta Java kód, amely bármely Maven vagy Gradle projektbe beilleszthető.

---

## Előfeltételek

| Követelmény | Miért fontos |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 vagy újabb) | Biztosítja a példában használt `Document` és `PdfSaveOptions` osztályokat. |
| **JDK 8+** | A könyvtár Java 8-ra és újabbra van lefordítva; régebbi futtatókörnyezet `UnsupportedClassVersionError`‑t dob. |
| **Egy DOCX fájl** legalább egy lebegő alakzattal (kép, szövegdoboz, WordArt) | Az alakzat‑exportálási opció hatásának megtekintéséhez szükség van olyan dokumentumra, amely ténylegesen tartalmaz lebegő objektumokat. |

Ha már megvannak ezek a darabok, nagyszerű – vágjunk bele.

---

## 1. lépés – Forrásdokumentum betöltése  

Először létrehozunk egy `Document` példányt, amely a konvertálni kívánt `.docx` fájlra mutat. A konstruktor beolvassa a fájlt a memóriába, feldolgozza az OpenXML csomagot, és előkészíti a belső objektummodellt.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Pro tipp:** Ha sok fájlt dolgozol fel egy ciklusban, egyetlen `Document` objektumot csak akkor használj újra, ha már meghívtad a `doc.close()`‑t (vagy hagyod, hogy a szemétgyűjtő gondoskodjon róla). Ez megakadályozza a fájl‑kezelő szivárgásokat Windows rendszeren.

---

## 2. lépés – PDF mentési beállítások konfigurálása az alakzatok exportálásához  

A tutorial szíve itt található. A `PdfSaveOptions` lehetővé teszi, hogy meghatározd a konverzió viselkedését. A `setExportFloatingShapesAsInlineTag(true)` beállítás minden lebegő alakzatot *beágyazott* elemként kezel a PDF címkeszerkezetében. Ez azt jelenti, hogy a képernyőolvasók az alakzatot a környező szöveg sorrendjében olvassák, ami gyakran szükséges a hozzáférhetőségi megfeleléshez.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**Mikor állítanád `false`‑ra?**  
Ha a PDF csak nyomtatási célra készül, és szeretnéd, hogy az alakzatok megtartsák eredeti pozíciójukat anélkül, hogy befolyásolnák a logikai olvasási sorrendet, előnyösebb lehet a blokkszintű címkézés. Alapértelmezés szerint `false`, ezért ebben a tutorialban kifejezetten engedélyezzük a beágyazott viselkedést.

---

## 3. lépés – Dokumentum mentése PDF‑ként  

Miután a beállítások készen állnak, hívd meg a `save`‑t a célfájlnévvel és a beállításobjektummal. A könyvtár elvégzi a nehéz munkát: elrendezésmotor, betűtípus beágyazás és címkék generálása.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

A hívás befejezése után a megadott mappában megtalálod a `shapes.pdf` fájlt. Nyisd meg Adobe Acrobatban vagy bármely PDF‑olvasóban, amely megjeleníti a címkéket (általában **File → Properties → Tags** alatt), és láthatod, hogy a lebegő alakzat beágyazott címkeként jelenik meg.

---

## Teljes, futtatható példa  

Összevonva, itt egy önálló Java osztály, amelyet lefordíthatsz és futtathatsz. Ügyelj arra, hogy az Aspose.Words JAR a classpath‑on legyen.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Várható eredmény:**  
- A PDF fájl ugyanazt a szöveges tartalmat tartalmazza, mint az eredeti DOCX.  
- Minden lebegő kép vagy szövegdoboz most *beágyazott* címkével rendelkezik, vagyis az olvasási sorrendben jelenik meg, nem különálló blokként.  
- Ha megnyitod a PDF **Tags** paneljét, láthatod, hogy egy `<Figure>` elem egy `<Paragraph>`‑on belül van – pontosan azt, amit a `setExportFloatingShapesAsInlineTag(true)` garantál.

---

## Gyakran ismételt kérdések és speciális esetek  

### 1️⃣ Működik ez jelszóval védett DOCX fájlokkal?  
Igen – csak add meg a jelszót a betöltés előtt:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ Mi a helyzet az SVG vagy EMF képekkel a Word fájlban?  
Az Aspose.Words automatikusan rasterizálja a vektorgrafikákat PDF‑re mentéskor. Ha vektorként szeretnéd megtartani őket, állítsd be:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ Hogyan őrizhetem meg a hiperhivatkozásokat a konvertálás során?  
A linkek alapértelmezés szerint megmaradnak. Azonban, ha letiltod a címkéket (`pdfOptions.setSaveFormat(SaveFormat.PDF)` opciók nélkül), elveszítheted a logikai struktúrát. Tartsd meg a `PdfSaveOptions` objektumot, hogy a címkék és a linkek egyaránt megmaradjanak.

### 4️⃣ Képes vagyok egy mappában lévő DOCX fájlokat kötegelt feldolgozni?  
Természetesen. Csomagold a `DocxToPdfWithShapes` logikát egy ciklusba, amely iterál a `Files.list(Paths.get("YOUR_DIRECTORY"))` elemein. Ne felejtsd el a kivételeket fájlonként kezelni, hogy egy rossz dokumentum ne állítsa le az egész futást.

---

## Praktikus tippek a frontvonalról  

* **Figyelj a hiányzó betűtípusokra.** Ha a forrás DOCX egy egyedi betűtípust használ, amely nincs telepítve a szerveren, a PDF egy helyettesítő betűtípust fog használni, ami eltorzíthatja az elrendezést. Használd a `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)`‑t a betűtípusok kényszerített beágyazásához.  
* **Hozzáférhetőség tesztelése.** A konvertálás után futtasd le az Acrobat **Accessibility Checker**‑ét. A beágyazott címkézés általában javítja a pontszámot, de előfordulhat, hogy a képekhez manuálisan kell alternatív szöveget hozzáadni.  
* **Teljesítmény tipp:** Nagy dokumentumok (100+ oldal) esetén engedélyezd a `pdfOptions.setMemoryOptimization(true)`‑t a heap használat csökkentése érdekében.

---

## Vizuális megerősítés  

Az alábbi gyors képernyőkép egy PDF‑et mutat megnyitva Adobe Acrobatban, ahol a beágyazott címkével ellátott alakzat ki van emelve a **Tags** panelen.

![Convert DOCX to PDF example output](image.png)

*Alt text: convert docx to pdf example output showing inline shape tags.*

---

## Összegzés  

Most már tudod, **hogyan konvertálj DOCX‑et PDF‑re**, miközben szabályozod a lebegő objektumok exportálásának módját. A `setExportFloatingShapesAsInlineTag` átkapcsolásával eldöntheted, hogy az alakzatok a olvasási sorrend részei legyenek vagy független blokkok maradjanak – ez kulcsfontosságú mind a hozzáférhetőség, mind a vizuális hűség szempontjából.

Innen tovább:

* **Word mentése PDF‑ként** kötegelt archiváláshoz.  
* Kísérletezz más `PdfSaveOptions` beállításokkal, például `setCompliance(PdfCompliance.PDF_A_1B)`‑vel a hosszú távú megőrzéshez.  
* Mélyedj el a **alakzatok exportálásának** részleteiben az Aspose.Words teljes dokumentációjában, vagy próbáld ki a `setExportDocumentStructure(true)` kapcsolót a gazdagabb címkefákért.

Próbáld ki, finomhangold a beállításokat, és hagyd, hogy a PDF‑ek pontosan úgy nézzenek ki, ahogy szeretnéd. Boldog kódolást!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
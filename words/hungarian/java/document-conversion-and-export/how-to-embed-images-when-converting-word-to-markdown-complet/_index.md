---
category: general
date: 2026-02-28
description: Tanulja meg, hogyan ágyazhat be képeket a dokumentum markdown formátumba
  konvertálása során. Exportálja a markdown-t képekkel, és szerezzen beágyazott képeket
  a markdown-ban Java használatával.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: hu
og_description: Fedezze fel, hogyan ágyazhat be képeket a Word-dokumentum Markdown
  formátumba konvertálása során. Ez az útmutató megmutatja, hogyan exportálhatja a
  markdown-t képekkel, és hogyan tarthatja azokat beágyazottan.
og_title: Hogyan ágyazzunk be képeket a Word Markdown formátumba konvertálásakor
tags:
- markdown
- java
- Aspose.Words
- image handling
title: Hogyan ágyazz be képeket a Wordből Markdownba konvertáláskor – Teljes útmutató
url: /hu/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan ágyazzunk be képeket Word‑ról Markdown‑ra konvertáláskor – Teljes útmutató

Gondolkodtál már azon, **hogyan ágyazzunk be képeket** egy Markdown fájlba, amelyet egy Word dokumentumból generálsz? Lehet, hogy gyors exportot próbáltál, csak hogy egy csomó lebegő képfájl és törött hivatkozás maradt. Ez egy gyakori fájdalomforrás – különösen, ha egyetlen, hordozható `.md` fájlra van szükséged, amelyet beilleszthetsz egy statikus weboldal generátorba vagy egy GitHub README‑ba.

A jó hír? Azt mondhatod az exportálónak, hogy minden képet Base64‑kódolt karakterláncként ágyazzon be, így a kapott Markdown önálló lesz. Ebben az útmutatóban lépésről lépésre végigmegyünk, megmutatjuk a teljes Java kódot, és elmagyarázzuk, miért fontos minden részlet. A végére **konvertálni tudod a doc‑ot markdown‑ra** beágyazott képekkel, és azt is látni fogod, hogyan finomíthatod a folyamatot más helyzetekben, például „markdown export képekkel” vagy „képek beágyazása markdown‑ba”.

## Mit fogsz megtanulni

- A szükséges könyvtárak és egy minimális projektbeállítás.
- Hogyan konfiguráljuk a `MarkdownSaveOptions`‑t, hogy a képek Base64 adat‑URI‑kká váljanak.
- Miért a `ResourceSavingCallback` használata a legkönnyebb módja a képek kezelésének.
- Hogyan ellenőrizheted, hogy a Markdown fájl valóban tartalmazza a beágyazott képeket.
- Tippek szélsőséges esetekhez (nagy képek, különböző MIME‑típusok és teljesítménybeli szempontok).

Nem szükséges előzetes tapasztalat az Aspose.Words‑szal; egy alap Java háttér elegendő.

---

## Előfeltételek

Mielőtt a kódba merülnénk, győződj meg róla, hogy rendelkezel:

| Követelmény | Miért fontos |
|-------------|----------------|
| **Java 17+** (vagy bármely friss JDK) | Az Aspose.Words for Java API a Java 8+‑ra céloz, de a legújabb JDK használata biztosítja a beépített `Base64` segédeszközöket. |
| **Aspose.Words for Java** (legújabb verzió) | Ez a könyvtár biztosítja a `MarkdownSaveOptions`‑t és a callback infrastruktúrát, amelyet használni fogunk. |
| **Word dokumentum** (`.docx`), amely legalább egy képet tartalmaz | Szükségünk van valamire a konvertáláshoz; a példa egy `sample.docx` nevű fájlt feltételez. |
| **IDE vagy szövegszerkesztő** (IntelliJ, VS Code, stb.) | A minta gyors fordításához és futtatásához. |

Add the Aspose dependency to your `pom.xml` (Maven) vagy `build.gradle` (Gradle). Itt a Maven részlet:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

Ha a Gradle‑t részesíted előnyben:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tipp:** Az Aspose ingyenes 30‑napos próbaidőszakot kínál. Szerezz be egy ideiglenes licenckulcsot, és regisztráld korán, hogy elkerüld a vízjel üzeneteket.

---

## 1. lépés: Hozd létre a Markdown Save Options‑t

Az első dolog, amit teszünk, hogy példányosítjuk a `MarkdownSaveOptions`‑t. Ez az objektum megmondja az Aspose‑nak, hogyan szeretnénk, hogy a konverzió viselkedjen – betűkészlet kezelése, lista formázása, és számunkra a legfontosabb, a képek kezelése.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

Java‑ban a szintaxis azonos; csak cseréld le a `csharp` kulcsszót `java`‑ra a későbbi kódrészletben.  
Miért fontos: az opciók testreszabása nélkül az Aspose minden képet egy külön fájlba ír a `.md` mellé. Az opcióobjektum előkészítésével most egy horgot adunk magunknak, hogy elfogjuk ezt az alapértelmezett viselkedést.

---

## 2. lépés: Kép erőforrások elfogása és Base64‑kódolása

Az Aspose minden alkalommal, amikor erőforrást (képet, CSS‑t stb.) akar írni, meghív egy callback‑et. Az `IResourceSavingCallback` megvalósításával eldönthetjük, mi történjen az egyes erőforrásokkal. Az alábbi kódrészlet ellenőrzi, hogy az erőforrás kép‑e‑e, törli a fájlnevet (így nem jön létre külső fájl), Base64‑ra kódolja a bináris adatot, és beállítja a megfelelő MIME‑típust.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**Mi történik a háttérben?**

1. `args.getResourceType()` – Az Aspose minden kimenő blob‑ot osztályoz. Nekünk csak a `ResourceType.IMAGE` érdekes.  
2. `args.setResourceFileName(null)` – A fájlnév null‑ra állításával azt mondjuk a könyvtárnak, *ne* írjon fizikai fájlt.  
3. `Base64.getEncoder().encodeToString(...)` – A nyers bájt tömb szöveges karakterlánccá alakul, amely biztonságosan elhelyezhető egy Markdown adat‑URI‑ban.  
4. `args.setResourceContentType("image/png")` – Ez biztosítja, hogy a generált Markdown címke így nézzen ki: `![alt](data:image/png;base64,…)`. Ha a forrásdokumentum JPEG‑eket tartalmaz, ellenőrizheted az eredeti bájtokat, és helyette `"image/jpeg"`‑t választhatsz.

> **Miért Base64?**  
> A data URI‑kat értő Markdown feldolgozók közvetlenül megjelenítik a képet, és a kapott fájl hordozható marad – nincs extra eszköz másolásra. Különösen hasznos GitHub README‑k vagy dokumentációs oldalak esetén, amelyek nem engedélyezik a külső erőforrásokat.

---

## 3. lépés: A konverzió végrehajtása

Miután az opciók készen állnak, egyszerűen töltsd be a Word dokumentumot, és hívd a `save`‑t. A megadott útvonal lesz a generált Markdown fájl helye.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

Ennyi – csak két sor a tényleges konverziós kódból. A nehéz munka (DOCX olvasása, képek kinyerése, bekezdések konvertálása) teljesen az Aspose feladata.

---

## 4. lépés: Az eredmény ellenőrzése – Beágyazott képek megjelennek

Nyisd meg a `output/doc.md` fájlt bármely szövegszerkesztőben. Valami ilyesmit kell látnod:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Ha a Markdown‑ot egy olyan nézőbe illeszted, amely támogatja a data URI‑kat (GitHub, VS Code előnézet vagy egy statikus weboldal generátor), a kép megjelenik extra fájlok nélkül.

**Gyors ellenőrzés**:

- **Keress `data:image/`** – Ha néhány hosszú karakterláncot találsz, a beágyazás sikeres.  
- **Számold meg a `![](` mintákat** – Ezeknek meg kell egyezniük az eredeti Word fájlban lévő képek számával.

---

## Szélsőséges esetek kezelése

### Nagy képek

A Base64 körülbelül **33 %**‑kal növeli az eredeti méretet. Nagyon nagy képek (pl. nagy felbontású fényképek) esetén a Markdown fájl nehezen kezelhetővé válhat. Fontold meg ezeket a stratégiákat:

| Stratégia | Mikor használjuk |
|----------|--------------|
| **Átméretezés konverzió előtt** – Használd a `java.awt.Image`‑t a méretezéshez. | Amikor a forrásdokumentum nagy felbontású eszközöket tartalmaz, amelyekre nincs szükség teljes méretben. |
| **Váltás JPEG‑re** – Módosítsd `args.setResourceContentType("image/jpeg")`‑t. | Fényképek esetén, ahol a PNG veszteségmentes formátuma túlzott. |
| **A dokumentum darabolása** – Oszd fel a Word fájlt szakaszokra, és exportáld őket külön-külön. | Amikor a Markdown fájlt egy bizonyos méretkorláton belül kell tartani (pl. a GitHub 10 MB‑os fájlkorlát). |

### Nem PNG képek

Ha a Word dokumentum vegyes formátumokat tartalmaz, dinamikusan felismerheted a MIME‑típust:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Az Aspose már kitölti a `ResourceContentType`‑t, így gyakran nincs szükség a `"image/png"` kézi megadására.

### Teljesítmény tippek

- **Használj egyetlen `Base64.Encoder` példányt** ciklusban több kép konvertálásához.  
- **Engedélyezd a `markdownSaveOptions.setExportImagesAsBase64(true)`‑t** (ha az API verzió támogatja), hogy teljesen elkerüld a callback‑et.  
- **Futtasd a konverziót háttérszálon** nagy mennyiségű dokumentum szerver környezetben történő feldolgozásakor.

---

## Teljes működő példa (mind együtt)

Az alábbiakban egy másolás‑beillesztésre kész Java programot találsz, amely tartalmazza az importokat, a hibakezelést és a teljes folyamatot, amelyet megbeszéltünk.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Várt kimenet**: egyetlen `doc.md` fájl, amely beágyazott Base64 képeket tartalmaz, készen áll bármely Markdown‑tudó eszközhöz.

---

## Gyakran ismételt kérdések

**Q1: Működik ez az Aspose.Words régebbi verzióival?**  
*Általában igen.* A callback API a 19‑es verzió óta stabil. Azonban a `setExportImagesAsBase64` gyorsgomb későbbi kiadásokban jelent meg, így ha régebbi buildet használsz, a fenti explicit callback‑ra lesz szükséged.

**Q2: Mi van, ha GitHub Flavored Markdown‑ra (GFM) kell exportálni?**  
Az Aspose `MarkdownSaveOptions` már GFM‑kompatibilis szintaxist generál. Az egyetlen extra lépés, hogy biztosítsd, a repository renderelő motorja támogatja a data URI‑kat – a GitHub igen.

**Q3: Használható ez a megközelítés más formátumokra, például HTML‑re?**  
Természetesen. ugyanaz a `ResourceSavingCallback` működik `HtmlSaveOptions`‑nél is. Csak cseréld ki az opció osztályt, és tartsd meg a Base64 logikát.

## 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
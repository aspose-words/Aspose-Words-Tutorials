---
category: general
date: 2026-10-20
description: Állítsa be a LoadOptions kódolását Java-ban a dokumentumok helyes beolvasásához,
  és változtassa meg a dokumentum kódolását UTF-8-ra az Aspose.Words segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: hu
lastmod: 2026-10-20
og_description: Állítsa be a LoadOptions kódolását Java-ban a helyes karakterkezelés
  biztosítása érdekében, és tanulja meg, hogyan változtathatja meg a dokumentum kódolását
  UTF-8-ra az Aspose.Words segítségével.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: LoadOptions kódolás konfigurálása Java-ban – teljes útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Hogyan konfiguráljuk a LoadOptions kódolását Java-ban
url: /hu/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan konfiguráljuk a LoadOptions kódolását Java-ban

Ha Java-ban **konfigurálnod kell a LoadOptions kódolást**, ez az útmutató megmutatja, hogyan állítsd be a megfelelő karakterkészletet, majd **a dokumentum kódolását UTF-8-ra változtasd** az Aspose.Words használatával. A helyes kódolás megakadályozza a torz szöveget, amikor olyan fájlokat töltünk be, amelyek örökölt kódlapokat használnak, például Big5, Shift_JIS vagy Windows‑1252.

Megtanulod, hogyan:

* hozz létre egy `LoadOptions` példányt egy adott kódolással,
* tölts be egy forrásdokumentumot, amely ezt a kódolást használja,
* mentsd a dokumentumot másik kódolásban (UTF‑8) adatvesztés nélkül,
* ellenőrizd, hogy a konverzió sikeres volt-e.

Az útmutató feltételezi, hogy van egy alapvető Java fejlesztői környezeted és egy érvényes Aspose.Words for Java licenc. Külső eszközök nem szükségesek.

## Előfeltételek

| Követelmény | Miért fontos |
|-------------|----------------|
| Java 17 vagy újabb | Modern nyelvi funkciókat és hosszú távú támogatást biztosít. |
| Aspose.Words for Java (v23.9 vagy újabb) | A `LoadOptions` osztály ebben a könyvtárban található. |
| Egy örökölt kódlappal kódolt forrásdokumentum (pl. Big5) | Bemutatja az egyedi kódolás szükségességét. |
| IDE vagy build eszköz (Maven/Gradle) | Egyszerűvé teszi a példa lefordítását és futtatását. |

Add the Aspose.Words dependency to your `pom.xml` if you use Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Configure LoadOptions encoding

Az első lépés, hogy megmondjuk az Aspose.Words-nak, milyen karakterkészletet várjon a fájl olvasásakor. Ezt a `LoadOptions` objektum konfigurálásával tesszük.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**Miért fontos:** Amikor egy dokumentumot örökölt kódolással mentenek, az alapértelmezett betöltő UTF‑8-at feltételez. A kódolás explicit beállításával elkerülöd a mojibake-et (torz karakterek) és megőrzöd az eredeti szöveget.

### Pro tipp
Ha nem vagy biztos benne, hogy milyen kódolást használ egy fájl, ellenőrizheted a byte‑order mark (BOM) jelét, vagy megkérdezheted a dokumentum szolgáltatóját. Gyakori örökölt kódolások: `Big5`, `Shift_JIS` és `Windows-1252`.

## Load the document with the configured options

Most, hogy a `LoadOptions` készen áll, töltsd be a forrásfájlt. Az a konstruktor, amely fájlútvonalat és egy `LoadOptions` példányt fogad, biztosítja, hogy az egyedi kódolás alkalmazásra kerüljön.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**Miért fontos:** A `Document` objektum most pontosan úgy tartalmazza a szöveget, ahogy az az eredeti fájlban megjelenik, mert a betöltő tiszteletben tartotta a megadott Big5 kódlapot.

## Change document encoding to UTF-8

Az Aspose.Words belsőleg Unicode-ként tárolja a szöveget, így a dokumentum mentése határozza meg a külső kódolást. Ahhoz, hogy UTF‑8 fájlt kapj, egyszerűen ments anélkül, hogy további kódolást adna meg – az UTF‑8 az alapértelmezett a modern Office Open XML formátumoknál. Az egyértelműség kedvéért azonban kifejezetten is beállítható.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

Ha plain‑text (például `.txt`) ábrázolást kell előállítanod UTF‑8 kódolással, adj át egy `SaveOptions` objektumot:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**Miért fontos:** UTF‑8‑ként mentve garantálod, hogy bármely downstream rendszer – webszolgáltatások, adatbázisok vagy modern szerkesztők – képes legyen a fájlt további konverzió nélkül beolvasni.

## Verify the conversion

Gyors módja annak, hogy megerősítsd, a kódolásváltás sikeres volt, ha visszaolvasod a mentett fájlt egy UTF‑8 olvasóval, és kiírsz néhány karaktert.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

Ha a kimenet olvasható karaktereket jelenít meg (nincsenek � szimbólumok), a konverzió a várt módon működött.

## Full runnable example

Alább egy önálló program látható, amely az összes lépést egyben tartalmazza. Cseréld le a fájlútvonalakat a saját helyeidre.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Várható kimenet**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

Ha a karakterek helyesen jelennek meg, sikeresen **konfiguráltad a LoadOptions kódolását** és **UTF‑8-ra változtattad a dokumentum kódolását**.

## Common pitfalls and how to avoid them

| Tünet | Ok | Megoldás |
|---------|-------|-----|
| Torz karakterek a betöltés után | `LoadOptions` nincs beállítva vagy rossz karakterkészlet neve | Győződj meg róla, hogy `loadOptions.setEncoding(Charset.forName("Big5"))` megegyezik a forrásfájl kódlapjával. |
| `UnsupportedEncodingException` | Elgépelés a karakterkészlet nevében | Használd a `Charset.availableCharsets()`‑ben felsorolt pontos nevet. |
| A kimeneti fájl még mindig mojibake-et mutat | Örökölt formátumban mentve (pl. `.rtf`) UTF‑8 opciók nélkül | Használd a `TxtSaveOptions`‑t a `setEncoding("UTF-8")` beállítással vagy ments `.docx`‑ként. |
| Teljesítménycsökkenés nagy fájloknál | `LoadOptions` újra létrehozása minden dokumentumhoz | Használd újra ugyanazt a `LoadOptions` példányt, ha sok fájlt dolgozol fel ugyanazzal a forráskódolással. |

## Conclusion

Most már tudod, hogyan **konfiguráld a LoadOptions kódolását** Java-ban, hogy örökölt kódolású dokumentumokat olvass, és hogyan **változtasd a dokumentum kódolását UTF‑8-ra** a biztonságos downstream felhasználás érdekében. A megközelítés bármely, a Java `Charset` osztálya által támogatott kódlapra alkalmazható, így rugalmas megoldást nyújt többnyelvű alkalmazásokhoz.

A következőket is felfedezheted:

* **Kötegelt konverzió** – egy mappában lévő dokumentumok bejárása és ugyanazon kódolási logika alkalmazása.
* **Kódolásdetektálás** – olyan könyvtárak használata, mint a juniversalchardet, a forrás karakterkészlet automatikus felismeréséhez a `LoadOptions` beállítása előtt.
* **Formázás megőrzése** – kísérletezz a PDF vagy HTML formátumba mentéssel, miközben az UTF‑8 megfelelőséget fenntartod.

Nyugodtan igazítsd a kódot a projekted architektúrájához, és hagyd, hogy a robusztus Aspose.Words API végezze a nehéz dokumentumműveleteket.

![Code snippet showing configuration of LoadOptions encoding and document save](/images/encoding-demo.png){: .align-center alt="LoadOptions kódolás konfigurálása Java kódrészletben"}

## What Should You Learn Next?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/) → **Hogyan állítsuk be a LoadOptions‑t az Aspose.Words for Java‑ban**
- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/) → **Hogyan konvertáljunk RTF szöveget UTF‑8 kódolással Java‑ban az Aspose.Words használatával**
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/) → **Hogyan állítsuk helyre a sérült DOCX Word dokumentumot az Aspose.Words LoadOptions használatával – Java útmutató**

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
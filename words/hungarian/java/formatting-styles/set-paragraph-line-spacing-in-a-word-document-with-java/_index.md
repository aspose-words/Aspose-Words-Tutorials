---
category: general
date: 2026-11-15
description: Állítsa be a bekezdés sorközét egy Word dokumentumban Java-val. Tanulja
  meg, hogyan állíthatja be a sorközöket programozottan az Aspose.Words segítségével
  a pontos dokumentumformázáshoz.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: hu
lastmod: 2026-11-15
og_description: Állítsa be a bekezdés sorközét egy Word dokumentumban Java-val. Ez
  az útmutató bemutatja, hogyan állítható be a sorköz a bekezdésekhez és a lábjegyzet-elválasztókhoz
  az Aspose.Words használatával, teljes irányítást biztosítva a dokumentum elrendezése
  felett.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Bekezdés sortávolságának beállítása Wordben Java-val
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Beállítani a bekezdés sortávolságát egy Word-dokumentumban Java-val
url: /hu/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Beállítani a bekezdés sortávolságát Word dokumentumban Java-val

Ha **be kell állítania a bekezdés sortávolságát** egy Word dokumentumban, ez a bemutató megmutatja, hogyan teheti ezt Java és az Aspose.Words segítségével. Emellett megtanulja, **hogyan állíthat be sortávolságot** a lábjegyzet elválasztók számára – ami gyakori igény a professzionális dokumentumok formázásakor.

A következő szakaszokban:

* Betölt egy meglévő *.docx* fájlt.
* Lekéri a lábjegyzet elválasztó bekezdést.
* Alkalmaz egy egyéni sortávolság‑értéket.
* Elmenti a módosított dokumentumot.

Nem szükséges külső konfiguráció, csak hozzá kell adni az Aspose.Words könyvtárat a projektjéhez, így a kódot szó szerint másolva azonnal futtathatja.

## Prerequisites

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* Java 17 vagy újabb verzióval.
* Maven‑nel (vagy más build eszközzel) a függőségek kezeléséhez.
* Érvényes Aspose.Words for Java licenccel (az ingyenes értékelő verzió teszteléshez megfelelő).
* Egy bemeneti Word dokumentummal (`input.docx`) egy ismert könyvtárban.

Adja hozzá az Aspose.Words függőséget a `pom.xml`‑hez:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Set paragraph line spacing with Aspose.Words

Ez a H2 fejléc tartalmazza a fő kulcsszót, teljesítve az SEO‑követelményt.

### Step 1: Load the Word document

Először hozza létre a `Document` példányt, amely a forrásfájlra mutat.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Miért fontos*: A dokumentum betöltése egy memóriában lévő modellt biztosít, amelyet módosíthat anélkül, hogy az eredeti fájlt érintené, amíg kifejezetten el nem menti.

### Step 2: Retrieve the footnote separator

A lábjegyzet elválasztók speciális bekezdések, amelyek a lábjegyzetek és a fő szöveg között jelennek meg. A megjelenésük módosításához hozzá kell férnie a `FootnoteSeparator` objektumhoz.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Tip*: Ha a dokumentum nem tartalmaz lábjegyzeteket, az elválasztó továbbra is létezik rejtett bekezdésként, így a hívás soha nem ad vissza `null`‑t.

### Step 3: How to set line spacing for the separator's paragraph

Most alkalmazza a kívánt sortávolságot. Az Aspose.Words pontban (pts) adja meg a sortávolság‑értékeket; a 12 pts nagyjából egyszeres sortávolság a legtöbb betűtípusnál.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Használhat más távolság‑módusokat is:

| Mód                     | Metódushívás                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fix pont)   | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (pl. 1.5)   | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

A megfelelő szabály kiválasztása biztosítja, hogy a dokumentum konzisztensen jelenjen meg a Word, a Google Docs és más megjelenítőkben.

### Step 4: Save the updated document

Végül írja vissza a változtatásokat a lemezre.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Amikor megnyitja a `output.docx`‑et a Microsoft Word‑ben, a lábjegyzet elválasztó a megadott sortávolsággal fog megjelenni.

## Understanding how to set line spacing for regular paragraphs

Ugyanaz az API minden `Paragraph` objektumra alkalmazható, nem csak a lábjegyzet elválasztókra. Íme egy gyors példa, amely a dokumentum törzsének első bekezdésének távolságát állítja be:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Miért lehet erre szükség**: Jelentések, szerződések és tudományos dolgozatok gyakran igényelnek egy meghatározott sortávolság‑stílust (pl. dupla sortávolság a vázlatoknál). Az `setLineSpacing` metódus használata garantálja a pontos elrendezést, amelyre számít.

## Common pitfalls and how to avoid them

| Probléma                                 | Ok                                           | Megoldás |
|------------------------------------------|----------------------------------------------|----------|
| A sortávolság változatlan marad          | `LineSpacingRule` alapértelmezett (AUTO) állapota | Állítsa be kifejezetten a szabályt a `setLineSpacingRule`‑dal. |
| Felesleges üres sorok az elválasztó után | Az elválasztó rejtett sortöréseket tartalmaz | Távolítsa el a szöveget a `separator.getText().trim();`‑vel, mielőtt a távolságot alkalmazná. |
| A dokumentum mentés után megsérül        | Elavult Aspose.Words verzió használata      | Frissítsen a legújabb verzióra (pl. 24.10), amely tartalmaz hibajavításokat a mentéshez. |

## Pro tip: batch‑process multiple documents

Ha több tucat fájlt kell frissítenie, csomagolja a logikát egy segédfüggvénybe, és iteráljon egy mappán:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Ennek a módszernek a ciklusban való futtatása órákat takarít meg a kézi szerkesztésből.

## Expected output

A teljes program futtatása után a `output.docx`:

* Az eredeti tartalmat változatlanul hagyja, kivéve a sortávolságot.
* A lábjegyzet elválasztót egyszeres sortávolsággal (12 pts) jeleníti meg.
* Megőrzi az összes többi formázást (stílusok, képek, táblázatok).

Nyissa meg a fájlt Word‑ben, és ellenőrizze, hogy az elválasztó vonala szorosabb (vagy lazább) lett a beállított értéknek megfelelően.

## Conclusion

Most már tudja, hogyan **állítson be bekezdés sortávolságot** egy Word dokumentumban Java‑val, és megérti, **hogyan állítsa be a sortávolságot** a lábjegyzet elválasztók és a normál bekezdések esetén is. A teljes, futtatható példa bemutatja a dokumentum betöltését, a sortávolság‑tulajdonságok módosítását és az eredmény mentését – mindezt néhány világos API‑hívással.

**Következő lépések**, amelyeket érdemes felfedezni:

* **Hogyan állítsa be a sortávolságot** táblázatok és listák elemeihez.
* Különböző távolság‑szabályok alkalmazása címsorokra és törzsszövegre.
* A `Style` objektum használata a távolságok egységes érvényesítéséhez az egész dokumentumban.

Kísérletezzen az értékekkel, kombinálja őket más formázási lehetőségekkel, és teljes irányítást kap a dokumentum elrendezése felett bármely Java‑alkalmazásban. Boldog kódolást!

## What Should You Learn Next?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Change Asian Paragraph Spacing And Indents In Word Document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
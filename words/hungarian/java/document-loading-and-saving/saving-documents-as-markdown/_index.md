---
date: 2026-02-24
description: Ismerje meg, hogyan konvertálhatja a Word dokumentumot markdown formátumba
  az Aspose.Words for Java segítségével. Ez az útmutató a táblázatok igazítását, a
  képek kezelését és a dokumentum markdownként való mentését tárgyalja.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Word konvertálása Markdown formátumba az Aspose.Words for Java segítségével
url: /hu/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word konvertálása Markdown-re az Aspose.Words for Java segítségével

## Bevezetés a Word Markdown-re konvertálásához az Aspose.Words for Java segítségével

Ebben a lépésről‑lépésre útmutatóban megtanulja, **hogyan konvertálja a Word dokumentumot Markdown‑re** a hatékony Aspose.Words for Java API használatával. A Markdown egy könnyűsúlyú jelölőnyelv, amelyre sok fejlesztő és tartalomplatform támaszkodik a tiszta, olvasható dokumentáció érdekében. A útmutató végére képes lesz bármelyik `.docx` fájlt átalakítani, megőrizve a táblázatokat, képeket és formázást, és exportálni azt `.md` fájlként, amely készen áll statikus weboldalkészítőkhöz, GitHub README‑khez vagy bármely markdown‑barát munkafolyamathoz.

## Gyors válaszok
- **Milyen könyvtárra van szükségem?** Aspose.Words for Java (`aspose-words.jar`).
- **Testreszabhatom a táblázat igazítását?** Igen – használja a `TableContentAlignment`-ot a `MarkdownSaveOptions`-ban.
- **Hogyan kezelődnek a képek?** Állítson be egy képmappát a `setImagesFolder()` segítségével; a könyvtár relatív hivatkozásokat hoz létre.
- **Szükség van licencre a termeléshez?** Kereskedelmi licenc szükséges a nem‑próba használathoz.
- **Kompatibilis a Java 17-tel?** Igen, a könyvtár támogatja a Java 8‑at és újabbat.

## Mi a Word Markdown-re konvertálása?

A Word Markdown-re konvertálása azt jelenti, hogy a Microsoft Word dokumentum gazdag formázását egyszerű szöveges markdown szintaxisra fordítjuk. Ez a folyamat megőrzi a címsorokat, listákat, táblázatokat és képhivatkozásokat, miközben eltávolítja a bináris formázást, így a tartalom hordozható és verziókezelő‑barát lesz.

## Miért használja az Aspose.Words for Java-t a dokumentum markdown‑ként mentéséhez?

* **Teljes hűség** – táblázatok, képek és összetett elrendezések megmaradnak.
* **Finomhangolt vezérlés** – testreszabhatja a táblázat igazítását, a képek útvonalát és egyebeket.
* **Nincs külső függőség** – a könyvtár azonnal használható, Office telepítése nélkül.
* **Keresztplatformos** – Windows, Linux és macOS rendszereken működik bármely Java futtatókörnyezettel.

## Előfeltételek

- Java Development Kit (JDK) telepítve a rendszerén.
- Aspose.Words for Java könyvtár. Letöltheti [innen](https://releases.aspose.com/words/java/).

## Lépésről‑lépésre útmutató

### 1. lépés: Hozzon létre egy Word dokumentumot, amelyet konvertálni fogunk

Először egy egyszerű Word dokumentumot építünk, amely egy kétsoros táblázatot tartalmaz. Ez a példa bemutatja, hogyan tisztelik a bekezdés igazítását a táblázatcellákban, amikor később **a dokumentumot markdown‑ként mentjük**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

### 2. lépés: Testreszabja a táblázat tartalom igazítását

Az Aspose.Words for Java lehetővé teszi, hogy szabályozza, hogyan igazodnak a táblázatcellák a generált markdownban. Használja a `TableContentAlignment` tulajdonságot a **táblázat igazításának testreszabásához** balra, jobbra, középre, vagy hagyja, hogy a könyvtár automatikusan döntsön az egyes oszlopok első bekezdése alapján.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

A beállítás váltogatásával **a Word táblázatokat markdown‑ként exportálhatja** a pontos igazítással, amelyre a downstream renderelő motoroknak szüksége van.

### 3. lépés: Képek kezelése a konvertálás során

Ha a forrás Word dokumentum képeket tartalmaz, meg kell adnia az Aspose.Words‑nek, hogy hová helyezze az exportált képfájlokat. A `setImagesFolder` metódus a `MarkdownSaveOptions`‑on definiálja azt a mappát, amely a képeszközöket tárolja, és a markdown relatív hivatkozásokat tartalmaz majd ezekre a fájlokra.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Cserélje le a `"document_with_images.docx"`‑t a forrásfájl útvonalára, és a `"images_folder/"`‑t a kívánt kimeneti képmappára.

### Teljes forráskód minden szcenárióhoz

Az alábbiakban egy összegző példa látható, amely megmutatja, hogyan **automatikus táblázat igazítás**, **igazítás testreszabása**, és **képmappa beállítása** valósítható meg egy metódusban. Ez a kódrészlet tükrözi az eredeti oktatóanyag kódját, és változtatás nélkül működik.

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Gyakori problémák és megoldások

| Probléma | Ok | Megoldás |
|----------|----|----------|
| A képek törött hivatkozásként jelennek meg | `setImagesFolder` nincs beállítva vagy a mappa útvonala helytelen | Ellenőrizze, hogy a mappa útvonala helyes és a mappa írható |
| A táblázat igazítása hibás | Helytelen `TableContentAlignment` érték | Használja a `TableContentAlignment.AUTO`-t, hogy az első bekezdés döntse el, vagy állítsa be explicit módon LEFT/RIGHT/CENTER értékre |
| A kimeneti fájl üres | A mentési beállítások nincsenek átadva a `doc.save()`-nek | Győződjön meg róla, hogy a `MarkdownSaveOptions` példányt átadja a `save` metódusnak |
| Nem támogatott Word funkciók (pl. SmartArt) | A Markdown nem képes néhány összetett objektum ábrázolására | Alakítsa ezeket az elemeket képekké a mentés előtt, vagy egyszerűsítse a forrásdokumentumot |

## Gyakran Ismételt Kérdések

**Q: Hogyan telepíthetem az Aspose.Words for Java‑t?**  
A: Az Aspose.Words for Java telepíthető a könyvtár Java projektbe való beillesztésével. Letöltheti a könyvtárat [innen](https://releases.aspose.com/words/java/) és kövesse a dokumentációban megadott telepítési útmutatót.

**Q: Konvertálhatok-e összetett Word dokumentumokat táblázatokkal és képekkel Markdown‑re?**  
A: Igen, az Aspose.Words for Java támogatja összetett Word dokumentumok táblázatokkal, képekkel és különféle formázási elemekkel való konvertálását Markdown‑re. Testreszabhatja a Markdown kimenetet a dokumentum összetettsége szerint.

**Q: Hogyan kezelhetem a képeket a Markdown fájlokban?**  
A: A képek beillesztéséhez a Markdown fájlokba állítsa be a képmappa útvonalát a `setImagesFolder` metódussal a `MarkdownSaveOptions`‑ban. Győződjön meg róla, hogy a kép fájlok a megadott mappában vannak, és az Aspose.Words for Java ennek megfelelően kezeli a képhivatkozásokat.

**Q: Elérhető-e próbaverzió az Aspose.Words for Java‑ból?**  
A: Igen, az Aspose weboldaláról letölthet egy próbaverziót az Aspose.Words for Java‑ból. A próbaverzió lehetővé teszi a könyvtár képességeinek értékelését licenc vásárlása előtt.

**Q: Hol találok további példákat és dokumentációt?**  
A: További példákért, dokumentációért és részletes információkért az Aspose.Words for Java‑ról kérjük, látogasson el a [dokumentációhoz](https://reference.aspose.com/words/java/).

## Összegzés

Ebben az útmutatóban mindent lefedtünk, ami szükséges a **Word markdown‑re konvertálásához** az Aspose.Words for Java segítségével: forrásdokumentum létrehozása, **táblázat igazításának testreszabása**, és a képek megfelelő mappakonfigurációval történő kezelése. Ezekkel a technikákkal megbízhatóan exportálhatja a Word tartalmat markdown‑ként blogokhoz, dokumentációs oldalakhoz vagy bármely markdown‑t fogyasztó platformhoz.

---

**Legutóbb frissítve:** 2026-02-24  
**Tesztelve a következővel:** Aspose.Words for Java 24.12 (legújabb a kiadás időpontjában)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
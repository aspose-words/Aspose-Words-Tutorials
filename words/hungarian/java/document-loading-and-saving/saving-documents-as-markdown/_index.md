---
date: 2025-12-22
description: Ismerje meg, hogyan exportálhatja a markdown-t a Word dokumentumok Markdown
  formátumba konvertálásával az Aspose.Words for Java segítségével. Ez a lépésről‑lépésre
  útmutató a táblázatok igazítását, a képek kezelését és még sok mást lefedi.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Hogyan exportáljunk Markdown-et az Aspose.Words for Java segítségével
url: /hu/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan exportáljunk Markdown-t az Aspose.Words for Java-val

## Bevezetés a Markdown exportálásába az Aspose.Words for Java-ban

Ebben a lépésről‑lépésre útmutatóban **meg fogod tanulni, hogyan exportálj markdown‑t** Word dokumentumokból az Aspose.Words for Java segítségével. A Markdown egy könnyű jelölőnyelv, amely tökéletes dokumentációhoz, statikus weboldalkészítőkhöz és számos kiadási platformhoz. A útmutató végére képes leszel **Word‑t markdown‑ra konvertálni**, testre szabni a táblázat igazítását, és **képeket markdown‑ban kezelni** könnyedén.

## Gyors válaszok
- **Mi a fő osztály a Markdown mentéséhez?** `MarkdownSaveOptions`
- **Beágyazhatók automatikusan a képek?** Igen – állítsd be a képek mappáját a `setImagesFolder` segítségével.
- **Hogyan szabályozhatom a táblázat igazítását?** Használd a `TableContentAlignment`‑t (LEFT, RIGHT, CENTER, AUTO).
- **Mik a minimális követelmények?** JDK 8+ és az Aspose.Words for Java könyvtár.
- **Elérhető próba verzió?** Igen, töltsd le az Aspose weboldaláról.

## Mi az a „hogyan exportáljunk markdown-t”?
A markdown exportálása azt jelenti, hogy egy gazdag szöveges Word dokumentumot (`.docx`) átalakítunk egy egyszerű szöveges `.md` fájlra, amely megőrzi a címsorokat, táblázatokat és képeket Markdown szintaxisban.

## Miért használjuk az Aspose.Words for Java-t docx képekkel való konvertálásra?
Az Aspose.Words képes a komplex elrendezések, beágyazott képek és táblázatszerkezetek kezelésére anélkül, hogy a hűség elveszne. Emellett finomhangolt vezérlést biztosít a Markdown kimenet felett, például a táblázat igazítását és a képmappa kezelését.

## Előfeltételek

- Java Development Kit (JDK) telepítve a rendszereden.
- Aspose.Words for Java könyvtár. Letöltheted [itt](https://releases.aspose.com/words/java/).

## 1. lépés: Hozz létre egy egyszerű Word dokumentumot

Először egy kis dokumentumot építünk, amely tartalmaz egy táblázatot. Ez lehetővé teszi, hogy később **testre szabjuk a táblázat igazítását**.

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

A fenti kódrészletben:

1. Hozz létre egy új `Document`‑ot.
2. Használd a `DocumentBuilder`‑t egy kétcellás táblázat beszúrásához.
3. Alkalmazd a **right** és **center** bekezdésigazítást minden cellában.
4. Mentsd a fájlt Markdown formátumban a `MarkdownSaveOptions` segítségével.

## 2. lépés: Testre szabni a táblázat tartalom igazítását

Az Aspose.Words lehetővé teszi, hogy meghatározd, hogyan jelenjenek meg a táblázat cellái a végső Markdown‑ban. Kényszerítheted a bal, jobb, közép igazítást, vagy hagyhatod, hogy a könyvtár automatikusan döntsön az első bekezdés alapján minden oszlopban.

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

A `TableContentAlignment` tulajdonság váltásával szabályozhatod a **táblázat igazításának testreszabását** a Markdown kimenetben.

## 3. lépés: Képek kezelése markdown exportálásakor

Amikor egy dokumentum képeket tartalmaz, szeretnéd, hogy ezek a képek helyesen jelenjenek meg a generált `.md` fájlban. Állítsd be azt a mappát, ahová az Aspose.Words kiírja a kinyert képeket.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Cseréld le a `"document_with_images.docx"`‑t a forrásfájlod elérési útjára, és a `"images_folder/"`‑t arra a helyre, ahol a képeket tárolni szeretnéd. A keletkező Markdown képlinkeket tartalmaz majd erre a mappára mutatva, lehetővé téve a **képek markdown‑ban történő kezelését** zökkenőmentesen.

## Teljes forráskód a dokumentumok Markdown‑ként mentéséhez az Aspose.Words for Java-ban

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

| Probléma | Megoldás |
|----------|----------|
| A képek nem jelennek meg a `.md` fájlban | Ellenőrizd, hogy a `setImagesFolder` egy írható könyvtárra mutat‑e, és hogy a mappa helyesen van‑e hivatkozva a generált Markdown‑ban. |
| A táblázat igazítása hibásnak tűnik | Használd a `TableContentAlignment.AUTO`‑t, hogy az Aspose.Words a legjobb igazítást határozza meg az egyes oszlopok első bekezdése alapján. |
| A kimeneti fájl üres | Győződj meg róla, hogy a `Document` objektum ténylegesen tartalmaz tartalmat a `save` hívása előtt. |

## Gyakran Ismételt Kérdések

**K: Hogyan telepíthetem az Aspose.Words for Java‑t?**  
V: Az Aspose.Words for Java telepíthető a könyvtár Java projektbe való beillesztésével. Letöltheted a könyvtárat [itt](https://releases.aspose.com/words/java/) és kövesd a dokumentációban leírt telepítési útmutatót.

**K: Tudok összetett Word dokumentumokat táblázatokkal és képekkel Markdown‑ba konvertálni?**  
V: Igen, az Aspose.Words for Java támogatja az összetett Word dokumentumok táblázatokkal, képekkel és különféle formázási elemekkel történő konvertálását Markdown‑ba. Testre szabhatod a Markdown kimenetet a dokumentum összetettsége szerint.

**K: Hogyan kezelhetem a képeket Markdown fájlokban?**  
V: Állítsd be a képek mappájának útvonalát a `setImagesFolder` metódus segítségével a `MarkdownSaveOptions`‑ban. Győződj meg róla, hogy a képfájlok a megadott mappában vannak; az Aspose.Words a megfelelő Markdown képlinkeket generálja.

**K: Elérhető próba verzió az Aspose.Words for Java‑hoz?**  
V: Igen, a próba verziót az Aspose weboldaláról szerezheted be. A próba verzió lehetővé teszi a könyvtár képességeinek értékelését a licenc vásárlása előtt.

**K: Hol találok további példákat és dokumentációt?**  
V: További példákért, dokumentációért és részletes információkért az Aspose.Words for Java‑ról kérjük, látogasd meg a [documentation](https://reference.aspose.com/words/java/) oldalt.

---

**Utolsó frissítés:** 2025-12-22  
**Tesztelve ezzel:** Aspose.Words for Java 24.12 (a legújabb a írás időpontjában)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
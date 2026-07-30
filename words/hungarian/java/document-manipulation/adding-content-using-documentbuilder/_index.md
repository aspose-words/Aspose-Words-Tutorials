---
date: 2026-01-01
description: Ismerje meg, hogyan hozhat létre űrlapmezőket, és adhat hozzá szöveget,
  táblázatokat, képeket, hiperhivatkozásokat és egyebeket az Aspose.Words for Java
  DocumentBuilder segítségével. Lépésről‑lépésre útmutató fejlesztőknek.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Hogyan hozhatunk létre űrlapmezőket és adhatunk hozzá tartalmat a DocumentBuilder
  segítségével az Aspose.Words for Java-ban
url: /hu/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tartalom hozzáadása a DocumentBuilder segítségével az Aspose.Words for Java-ban

## Bevezetés a tartalom hozzáadásához a DocumentBuilder segítségével az Aspose.Words for Java-ban

Ebben a lépésről‑lépésre útmutatóban **űrlapmezőket hozol létre**, és különféle tartalmakat — szöveget, táblázatokat, vízszintes vonalakat, HTML‑t, hiperhivatkozásokat, képeket és még sok mást — adsz hozzá egy Word dokumentumhoz az Aspose.Words for Java segítségével. Akár jelentést, szerződésmintát vagy interaktív űrlapot építesz, a `DocumentBuilder` osztály finomhangolt vezérlést biztosít minden elem felett. Merüljünk el benne!

## Gyors válaszok
- **Hogyan hozhatok létre űrlapmezőket?** Használd az `insertTextInput`, `insertCheckBox` vagy `insertComboBox` metódusokat egy `DocumentBuilder`‑en.
- **Melyik metódus ad hozzá egyszerű szöveget?** Hívd a `builder.write("Your text")` vagy a `builder.writeln("Your text")` metódust.
- **Beilleszthetek vízszintes vonalat?** Igen — a `builder.insertHorizontalRule()` egy vonalválasztót ad hozzá.
- **Hogyan ágyazhatok be HTML‑t?** Használd a `builder.insertHtml("<p>HTML content</p>")` metódust.
- **Hogyan adhatok hozzá beágyazott képet?** A `builder.insertImage("path/to/image.png")` a képet a szövegfolyamban helyezi el.

## Mi az a DocumentBuilder, és miért használjuk űrlapmezők létrehozására?

A `DocumentBuilder` az Aspose.Words folyékony API-ja a Word dokumentumok programozott létrehozásához és szerkesztéséhez. Elrejti az alacsony szintű OpenXML struktúrát, így a *mit* szeretnéd hozzáadni — például **űrlapmezőket** — a *hogyan* XML‑ként néz ki helyett koncentrálhatsz. Ez ideálissá teszi dinamikus űrlapok, szerződések vagy bármely felhasználói interakciót igénylő dokumentum generálásához.

## Előkövetelmények

Mielőtt elkezdenéd, győződj meg róla, hogy a projektedben telepítve van az Aspose.Words for Java könyvtár. Letöltheted [innen](https://releases.aspose.com/words/java/).

## Tartalom hozzáadása (szöveg hozzáadása)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Táblázatok hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Vízszintes vonal hozzáadása (add horizontal rule)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Űrlapmezők hozzáadása (create form fields)

### Szövegbeviteli űrlapmező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Jelölőnégyzet űrlapmező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Legördülő lista űrlapmező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## HTML hozzáadása (insert html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Hiperhivatkozások hozzáadása (how to add hyperlink)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Tartalomjegyzék hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Képek hozzáadása

### Beágyazott kép (insert inline image)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Lebegő kép

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Bekezdések hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## A kurzor mozgatása (Step 10)

A kurzor pozícióját a dokumentumban a `moveToParagraph`, `moveToCell` stb. metódusokkal szabályozhatod.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Ezek néhány gyakori művelet, amelyet az Aspose.Words for Java `DocumentBuilder`‑jével végezhetsz. Fedezd fel a könyvtár dokumentációját a fejlettebb funkciók és testreszabási lehetőségek megismeréséhez. Boldog dokumentumkészítést!

## Összegzés

Ebben az átfogó útmutatóban bemutattuk, hogyan **hozhatsz létre űrlapmezőket**, és hogyan adhatod hozzá a különféle tartalomtípusokat — szöveget, táblázatokat, vízszintes vonalakat, HTML‑t, hiperhivatkozásokat, tartalomjegyzéket, képeket, formázott bekezdéseket és kurzor navigációt — az Aspose.Words for Java `DocumentBuilder` segítségével. Most már szilárd alapokkal rendelkezel a dinamikus, interaktív Word dokumentumok programozott generálásához.

## Gyakran Ismételt Kérdések

### Q: Mi az az Aspose.Words for Java?

A: Az Aspose.Words for Java egy Java könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, módosítsanak és manipuláljanak Microsoft Word dokumentumokat. Széles körű funkciókat kínál a dokumentumgeneráláshoz, formázáshoz és tartalom beszúrásához.

### Q: Hogyan adhatok hozzá tartalomjegyzéket a dokumentumomhoz?

A: Tartalomjegyzék hozzáadásához használd a `DocumentBuilder`‑t egy TOC mező beszúrásához, majd a tartalom hozzáadása után hívd meg a `doc.updateFields()` metódust.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Hogyan illeszthetek be képeket egy dokumentumba az Aspose.Words for Java segítségével?

A: Képeket, akár beágyazott, akár lebegő formában, a `DocumentBuilder`‑rel illeszthetsz be.

#### Beágyazott kép:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Lebegő kép:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Formázhatok szöveget és bekezdéseket a tartalom hozzáadása során?

A: Igen, a `DocumentBuilder`‑rel formázhatod a szöveget és a bekezdéseket. A tartalom írása előtt állíts be betűtípus‑tulajdonságokat, bekezdés‑igazítást, behúzást és egyebeket.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: Hogyan mozgathatom a kurzort egy adott helyre a dokumentumban?

A: Használd a `moveToParagraph`, `moveToCell` stb. metódusokat a kurzor pozicionálásához új tartalom beszúrása előtt.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Ezek a válaszok lefedik a leggyakoribb szituációkat az Aspose.Words for Java `DocumentBuilder` használatakor. További részletekért tekintsd meg a [könyvtár dokumentációját](https://reference.aspose.com/words/java/) vagy csatlakozz az Aspose.Words közösséghez támogatásért.

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
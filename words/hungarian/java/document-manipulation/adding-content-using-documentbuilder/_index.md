---
"description": "Dokumentumkészítés mestere az Aspose.Words segítségével Java-ban. Lépésről lépésre útmutató szöveg, táblázatok, képek és egyebek hozzáadásához. Készítsen lenyűgöző Word-dokumentumokat könnyedén."
"linktitle": "Tartalom hozzáadása a DocumentBuilder használatával"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Tartalom hozzáadása a DocumentBuilder használatával az Aspose.Words for Java programban"
"url": "/hu/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tartalom hozzáadása a DocumentBuilder használatával az Aspose.Words for Java programban


## Bevezetés a DocumentBuilder használatával történő tartalom hozzáadásához Aspose.Words for Java nyelven

Ebben a lépésről lépésre bemutatott útmutatóban bemutatjuk, hogyan használható az Aspose.Words Java DocumentBuilderéhez különféle típusú tartalmak Word-dokumentumokhoz való hozzáadásához. Áttekintjük a szöveg, táblázatok, vízszintes vonalak, űrlapmezők, HTML, hiperhivatkozások, tartalomjegyzék, beágyazott és lebegő képek, bekezdések és egyebek beszúrását. Kezdjük is!

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy az Aspose.Words for Java könyvtár telepítve van a projektedben. Letöltheted innen: [itt](https://releases.aspose.com/words/java/).

## Szöveg hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Egyszerű szöveges bekezdés beszúrása
builder.write("This is a simple text paragraph.");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Táblázatok hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Táblázat indítása
Table table = builder.startTable();

// Cellák és tartalom beszúrása
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// A táblázat vége
builder.endTable();

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Vízszintes vonal hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Vízszintes vonal beszúrása
builder.insertHorizontalRule();

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Űrlapmezők hozzáadása

### Szövegbeviteli űrlap mező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szövegbeviteli űrlapmező beszúrása
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

### Jelölőnégyzet űrlapmező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Jelölőnégyzet űrlapmező beszúrása
builder.insertCheckBox("CheckBox", true, true, 0);

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

### Kombinált lista űrlapmező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Elemek definiálása a kombinált listához
String[] items = { "Option 1", "Option 2", "Option 3" };

// Kombinált lista űrlapmező beszúrása
builder.insertComboBox("DropDown", items, 0);

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## HTML hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// HTML-tartalom beszúrása
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Hiperhivatkozások hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Hivatkozás beszúrása
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", hamis);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Tartalomjegyzék hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Tartalomjegyzék beszúrása
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Dokumentumtartalom hozzáadása
// ...

// Tartalomjegyzék frissítése
doc.updateFields();

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Képek hozzáadása

### Beágyazott kép

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Beszúr egy beágyazott képet
builder.insertImage("path/to/your/image.png");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

### Lebegő kép

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Lebegő kép beszúrása
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Bekezdések hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Bekezdésformázás beállítása
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

// Bekezdés beszúrása
builder.writeln("This is a formatted paragraph.");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## 10. lépés: A kurzor mozgatása

A kurzor pozícióját a dokumentumon belül többféleképpen is szabályozhatja, például `moveToParagraph`, `moveToCell`és még sok más. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Kurzor áthelyezése egy adott bekezdésre
builder.moveToParagraph(2, 0);

// Tartalom hozzáadása az új kurzorpozícióhoz
builder.writeln("This is the 3rd paragraph.");
```

Íme néhány gyakori művelet, amelyet az Aspose.Words for Java DocumentBuilder segítségével végezhet el. A könyvtár dokumentációjában további speciális funkciókat és testreszabási lehetőségeket talál. Jó dokumentumkészítést!


## Következtetés

Ebben az átfogó útmutatóban az Aspose.Words for Java DocumentBuilder funkcióit vizsgáltuk meg, amelyekkel különféle típusú tartalmakat lehet Word dokumentumokhoz hozzáadni. Áttekintettük a szöveget, táblázatokat, vízszintes vonalakat, űrlapmezőket, HTML-t, hiperhivatkozásokat, tartalomjegyzéket, képeket, bekezdéseket és a kurzor mozgatását.

## GYIK

### K: Mi az Aspose.Words Java-hoz?

A: Az Aspose.Words for Java egy Java könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, módosítsanak és manipuláljanak Microsoft Word dokumentumokat. Széleskörű funkciókat kínál a dokumentumok generálásához, formázásához és tartalom beszúrásához.

### K: Hogyan adhatok hozzá tartalomjegyzéket a dokumentumomhoz?

A: Tartalomjegyzék hozzáadásához használja a `DocumentBuilder` tartalomjegyzék mező beszúrásához a dokumentumba. A tartalomjegyzék feltöltéséhez a tartalomjegyzéket frissítse a dokumentum mezőinek frissítésével. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Tartalomjegyzék mező beszúrása
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Dokumentumtartalom hozzáadása
// ...

// Tartalomjegyzék frissítése
doc.updateFields();
```

### K: Hogyan szúrhatok be képeket egy dokumentumba az Aspose.Words for Java használatával?

A: Képeket beszúrhat, mind beágyazottan, mind lebegően, a következő használatával: `DocumentBuilder`Íme mindkettőre példa:

#### Beágyazott kép:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Beszúr egy beágyazott képet
builder.insertImage("path/to/your/image.png");
```

#### Lebegő kép:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Lebegő kép beszúrása
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### K: Formázhatom a szöveget és a bekezdéseket tartalom hozzáadásakor?

V: Igen, a szöveget és a bekezdéseket formázhatja a `DocumentBuilder`Beállíthatja a betűtípus tulajdonságait, a bekezdések igazítását, a behúzást és egyebeket. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Betűtípus és bekezdésformázás beállítása
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

// Formázott bekezdés beszúrása
builder.writeln("This is a formatted paragraph.");
```

### K: Hogyan tudom a kurzort a dokumentumon belül egy adott helyre mozgatni?

A: A kurzor pozícióját olyan módszerekkel szabályozhatja, mint például `moveToParagraph`, `moveToCell`és még sok más. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Kurzor áthelyezése egy adott bekezdésre
builder.moveToParagraph(2, 0);

// Tartalom hozzáadása az új kurzorpozícióhoz
builder.writeln("This is the 3rd paragraph.");
```

Íme néhány gyakori kérdés és válasz, amelyek segíthetnek az Aspose.Words használatának elkezdésében a Java DocumentBuilderhez. Ha további kérdései vannak, vagy további segítségre van szüksége, tekintse meg a következőt: [a könyvtár dokumentációja](https://reference.aspose.com/words/java/) vagy kérjen segítséget az Aspose.Words közösségtől és a támogatási forrásoktól.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
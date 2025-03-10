---
title: Tartalom hozzáadása az Aspose.Words for Java DocumentBuilder használatával
linktitle: Tartalom hozzáadása a DocumentBuilder segítségével
second_title: Aspose.Words Java Document Processing API
description: Fődokumentumkészítés az Aspose.Words for Java segítségével. Útmutató lépésről lépésre szövegek, táblázatok, képek és egyebek hozzáadásához. Lenyűgöző Word dokumentumokat készíthet könnyedén.
weight: 26
url: /hu/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tartalom hozzáadása az Aspose.Words for Java DocumentBuilder használatával


## Bevezetés a tartalom hozzáadásához az Aspose.Words for Java DocumentBuilder használatával

Ebben a lépésenkénti útmutatóban megvizsgáljuk, hogyan használhatjuk az Aspose.Words for Java DocumentBuilder alkalmazását különféle típusú tartalom hozzáadására egy Word-dokumentumhoz. Kitérünk a szöveg beszúrására, táblázatokra, vízszintes szabályokra, űrlapmezőkre, HTML-re, hiperhivatkozásokra, tartalomjegyzékre, szövegközi és lebegő képekre, bekezdésekre és egyebekre. Kezdjük is!

## Előfeltételek

 Mielőtt elkezdené, győződjön meg arról, hogy a projektben be van állítva az Aspose.Words for Java könyvtár. Letöltheti innen[itt](https://releases.aspose.com/words/java/).

## Szöveg hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy egyszerű szöveges bekezdést
builder.write("This is a simple text paragraph.");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Táblázatok hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//Indíts el egy asztalt
Table table = builder.startTable();

// Cellák és tartalom beszúrása
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Vége az asztalnak
builder.endTable();

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Vízszintes szabály hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy vízszintes szabályt
builder.insertHorizontalRule();

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Űrlapmezők hozzáadása

### Szövegbeviteli űrlapmező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szövegbeviteli űrlapmező beszúrása
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

### Jelölőnégyzet Űrlapmező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Helyezzen be egy jelölőnégyzetet az űrlapmezőbe
builder.insertCheckBox("CheckBox", true, true, 0);

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

### Kombinált doboz űrlapmező

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Határozzon meg elemeket a kombinált mezőhöz
String[] items = { "Option 1", "Option 2", "Option 3" };

// Szúrjon be egy kombinált űrlapmezőt
builder.insertComboBox("DropDown", items, 0);

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## HTML hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// HTML tartalom beszúrása
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Hiperhivatkozások hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy hiperhivatkozást
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Tartalomjegyzék hozzáadása

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Helyezzen be egy tartalomjegyzéket
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Dokumentumtartalom hozzáadása
// ...

// Frissítse a tartalomjegyzéket
doc.updateFields();

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## Képek hozzáadása

### Inline kép

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy soros képet
builder.insertImage("path/to/your/image.png");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

### Lebegő kép

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy lebegő képet
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

// Szúrjon be egy bekezdést
builder.writeln("This is a formatted paragraph.");

// Mentse el a dokumentumot
doc.save("path/to/your/document.docx");
```

## 10. lépés: A kurzor mozgatása

 Különféle módszerekkel szabályozhatja a kurzor pozícióját a dokumentumon belül`moveToParagraph`, `moveToCell`és még sok más. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Mozgassa a kurzort egy adott bekezdésre
builder.moveToParagraph(2, 0);

// Tartalom hozzáadása az új kurzorpozícióhoz
builder.writeln("This is the 3rd paragraph.");
```

Íme néhány gyakori művelet, amelyet az Aspose.Words for Java DocumentBuilder használatával hajthat végre. Fedezze fel a könyvtár dokumentációját a fejlettebb funkciók és testreszabási lehetőségek megtekintéséhez. Boldog dokumentumkészítést!


## Következtetés

Ebben az átfogó útmutatóban feltártuk az Aspose.Words for Java DocumentBuilder képességeit, amellyel különféle típusú tartalmakat adhatunk Word dokumentumokhoz. Lefedtük a szöveget, a táblázatokat, a vízszintes szabályokat, az űrlapmezőket, a HTML-t, a hiperhivatkozásokat, a tartalomjegyzéket, a képeket, a bekezdéseket és a kurzormozgást.

## GYIK

### K: Mi az Aspose.Words for Java?

V: Az Aspose.Words for Java egy Java-könyvtár, amely lehetővé teszi a fejlesztők számára Microsoft Word dokumentumok programozott létrehozását, módosítását és kezelését. A funkciók széles skáláját kínálja a dokumentumok generálásához, formázásához és tartalombeillesztéséhez.

### K: Hogyan adhatok hozzá tartalomjegyzéket a dokumentumomhoz?

V: Tartalomjegyzék hozzáadásához használja a`DocumentBuilder` tartalomjegyzék mező beszúrásához a dokumentumba. Ügyeljen arra, hogy a tartalom hozzáadása után frissítse a dokumentum mezőit a tartalomjegyzék feltöltéséhez. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy tartalomjegyzék mezőt
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Dokumentumtartalom hozzáadása
// ...

// Frissítse a tartalomjegyzéket
doc.updateFields();
```

### K: Hogyan illeszthetek be képeket egy dokumentumba az Aspose.Words for Java használatával?

 V: Beszúrhat képeket, mind soron belül, mind lebegőben, a`DocumentBuilder`. Íme mindkettőre példa:

#### Soron belüli kép:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy soros képet
builder.insertImage("path/to/your/image.png");
```

#### Lebegő kép:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Szúrjon be egy lebegő képet
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### K: Formázhatok szöveget és bekezdéseket tartalom hozzáadásakor?

 V: Igen, formázhatja a szöveget és a bekezdéseket a`DocumentBuilder`. Beállíthatja a betűtípus tulajdonságait, a bekezdésigazítást, a behúzást stb. Íme egy példa:

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

// Szúrjon be egy formázott bekezdést
builder.writeln("This is a formatted paragraph.");
```

### K: Hogyan mozgathatom a kurzort egy adott helyre a dokumentumon belül?

 V: A kurzor pozícióját olyan módszerekkel szabályozhatja, mint pl`moveToParagraph`, `moveToCell`és még sok más. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Mozgassa a kurzort egy adott bekezdésre
builder.moveToParagraph(2, 0);

// Tartalom hozzáadása az új kurzorpozícióhoz
builder.writeln("This is the 3rd paragraph.");
```

Íme néhány gyakori kérdés és válasz, amelyek segítenek az Aspose.Words for Java DocumentBuilder használatában. Ha további kérdése van, vagy további segítségre van szüksége, tekintse meg a[könyvtár dokumentációja](https://reference.aspose.com/words/java/) vagy kérjen segítséget az Aspose.Words közösségtől és támogatási forrásoktól.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

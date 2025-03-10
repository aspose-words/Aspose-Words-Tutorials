---
title: Szöveg keresése és cseréje az Aspose.Words for Java programban
linktitle: Szöveg keresése és cseréje
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan kereshet és cserélhet szöveget Word dokumentumokban az Aspose.Words for Java segítségével. Útmutató lépésről lépésre kódpéldákkal. Javítsa Java dokumentumkezelési készségeit.
weight: 15
url: /hu/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Szöveg keresése és cseréje az Aspose.Words for Java programban


## Bevezetés a szöveg keresésébe és cseréjébe az Aspose.Words for Java programban

Az Aspose.Words for Java egy hatékony Java API, amely lehetővé teszi a Word dokumentumok programozott kezelését. A Word dokumentumok kezelése során az egyik gyakori feladat a szöveg keresése és cseréje. Akár frissítenie kell a helyőrzőket a sablonokban, akár összetettebb szövegmanipulációkat kell végrehajtania, az Aspose.Words for Java segíthet céljai hatékony elérésében.

## Előfeltételek

Mielőtt belemerülnénk a szöveg keresésének és cseréjének részleteibe, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

- Java fejlesztői környezet
- Aspose.Words for Java könyvtár
- Egy minta Word dokumentum, amellyel dolgozni

 Az Aspose.Words for Java könyvtárat innen töltheti le[itt](https://releases.aspose.com/words/java/).

## Egyszerű szöveg keresése és cseréje

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy DocumentBuilder programot
DocumentBuilder builder = new DocumentBuilder(doc);

// Szöveg keresése és cseréje
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

 Ebben a példában betöltünk egy Word dokumentumot, létrehozunk a`DocumentBuilder` , és használja a`replace` módszer a "régi szöveg" megkeresésére és az "új szöveg" szövegre cseréjére a dokumentumban.

## Reguláris kifejezések használata

A reguláris kifejezések hatékony mintaillesztési lehetőségeket biztosítanak a szövegkereséshez és -cseréhez. Az Aspose.Words for Java támogatja a reguláris kifejezéseket a fejlettebb keresési és csereműveletekhez.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy DocumentBuilder programot
DocumentBuilder builder = new DocumentBuilder(doc);

// Szöveg kereséséhez és cseréjéhez használjon reguláris kifejezéseket
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ebben a példában reguláris kifejezésmintát használunk a dokumentumon belüli szöveg megkeresésére és cseréjére.

## mezők belsejében lévő szöveg figyelmen kívül hagyása

Beállíthatja, hogy az Aspose.Words figyelmen kívül hagyja a mezőkben lévő szöveget a keresési és csereműveletek végrehajtásakor.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy FindReplaceOptions példányt, és állítsa az IgnoreFields értéket igazra
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Szöveg lecserélésekor használjon opciókat
doc.getRange().replace("text-to-replace", "new-text", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ez akkor hasznos, ha ki akarja zárni a mezőkön belüli szöveget, például az egyesített mezőket, a lecserélésből.

## Szöveg figyelmen kívül hagyása a változatok törlésében

Beállíthatja, hogy az Aspose.Words figyelmen kívül hagyja a revíziók törlésén belüli szöveget a keresési és csereműveletek során.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy FindReplaceOptions példányt, és állítsa az IgnoreDeleted értéket true értékre
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Szöveg lecserélésekor használjon opciókat
doc.getRange().replace("text-to-replace", "new-text", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ez lehetővé teszi, hogy kizárja a nyomon követett változtatásokban törlésre megjelölt szövegek cseréjét.

## Szöveg figyelmen kívül hagyása a beillesztési változatokon belül

Beállíthatja, hogy az Aspose.Words figyelmen kívül hagyja a szöveg beszúrását a revíziókon belül a keresési és csereműveletek során.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy FindReplaceOptions példányt, és állítsa az IgnoreInserted értéket igazra
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Szöveg lecserélésekor használjon opciókat
doc.getRange().replace("text-to-replace", "new-text", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ez lehetővé teszi, hogy kizárja a nyomon követett változtatásokba beszúrtként megjelölt szöveget a lecserélésből.

## Szöveg lecserélése HTML-re

Az Aspose.Words for Java segítségével szöveget HTML-tartalommal helyettesíthet.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy FindReplaceOptions példányt egyéni helyettesítő visszahívással
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Szöveg lecserélésekor használjon opciókat
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

 Ebben a példában egyénit használunk`ReplaceWithHtmlEvaluator` szöveget HTML tartalomra cserélni.

## Szöveg cseréje a fejlécekben és láblécekben

A Word-dokumentum fejlécében és láblécében szöveget találhat és cserélhet.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Szerezze be a fejlécek és láblécek gyűjteményét
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Válassza ki a fejléc vagy lábléc típusát, amelyben le szeretné cserélni a szöveget (pl. HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Hozzon létre egy FindReplaceOptions példányt, és alkalmazza a lábléc tartományára
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ez lehetővé teszi a szövegek cseréjét kifejezetten a fejlécekben és a láblécekben.

## Változások megjelenítése a fejléc- és láblécsorrendeknél

Az Aspose.Words használatával megjelenítheti a fejléc- és lábléc-sorrend változásait a dokumentumban.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Szerezd meg az első részt
Section firstPageSection = doc.getFirstSection();

//Hozzon létre egy FindReplaceOptions példányt, és alkalmazza a dokumentum tartományára
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Cserélje le a fejléc- és láblécsorrendet befolyásoló szöveget
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ez lehetővé teszi a fejléc- és láblécsorrendekkel kapcsolatos változások megjelenítését a dokumentumban.

## Szöveg cseréje mezőkkel

A szöveget mezőkkel helyettesítheti az Aspose.Words for Java használatával.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy FindReplaceOptions példányt, és állítson be egyéni helyettesítő visszahívást a mezőkhöz
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Szöveg lecserélésekor használjon opciókat
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

 Ebben a példában a szöveget mezőkre cseréljük, és megadjuk a mező típusát (pl.`FieldType.FIELD_MERGE_FIELD`).

## Csere értékelővel

Egyéni kiértékelő segítségével dinamikusan meghatározhatja a helyettesítő szöveget.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy FindReplaceOptions példányt, és állítson be egyéni helyettesítő visszahívást
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Szöveg lecserélésekor használjon opciókat
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ebben a példában egyéni kiértékelőt (`MyReplaceEvaluator`) szöveg cseréjéhez.

## Csere Regexre

Az Aspose.Words for Java lehetővé teszi a szöveg reguláris kifejezésekkel történő cseréjét.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Szöveg kereséséhez és cseréjéhez használjon reguláris kifejezéseket
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ebben a példában reguláris kifejezésmintát használunk a dokumentumon belüli szöveg megkeresésére és cseréjére.

## Felismerés és helyettesítések a helyettesítési mintákon belül

Az Aspose.Words for Java segítségével felismerheti és helyettesítheti a helyettesítési mintákat.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy FindReplaceOptions-példányt a UseSubstitutions igaz értékre állítva
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Használjon opciókat, ha szöveget mintával cserél le
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ez lehetővé teszi a helyettesítések végrehajtását a helyettesítési mintákon belül a fejlettebb cserék érdekében.

## Csere karakterláncra

A szöveget lecserélheti egy egyszerű karakterláncra az Aspose.Words for Java használatával.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Cserélje ki a szöveget egy karakterláncra
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ebben a példában a „csereszöveg” szót „új karakterlánc”-ra cseréljük a dokumentumban.

## Legacy Order használata

Használhatja az örökölt sorrendet a keresési és csereműveletek végrehajtásakor.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Hozzon létre egy FindReplaceOptions példányt, és állítsa a UseLegacyOrder értéket true értékre
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Szöveg lecserélésekor használjon opciókat
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ez lehetővé teszi az örökölt sorrend használatát a keresési és csereműveletekhez.

## Szöveg cseréje a táblázatban

A Word-dokumentum táblázataiban szöveget kereshet és cserélhet.

```java
// Töltse be a dokumentumot
Document doc = new Document("your-document.docx");

// Egy adott táblázat beszerzése (pl. az első táblázat)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//Használja a FindReplaceOptions funkciót a táblázat szövegének cseréjéhez
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Mentse el a módosított dokumentumot
doc.save("modified-document.docx");
```

Ez lehetővé teszi szövegcserék végrehajtását kifejezetten a táblázatokon belül.

## Következtetés

Az Aspose.Words for Java átfogó lehetőségeket kínál a Word dokumentumok szövegének megkeresésére és cseréjére. Akár egyszerű szövegcseréket, akár fejlettebb műveleteket kell végrehajtania reguláris kifejezések, mezőmanipulációk vagy egyéni kiértékelők használatával, az Aspose.Words for Java mindent megtesz. Feltétlenül fedezze fel az Aspose által biztosított kiterjedt dokumentációt és példákat, hogy kiaknázhassa a nagy teljesítményű Java-könyvtárban rejlő lehetőségeket.

## GYIK

### Hogyan tölthetem le az Aspose.Words for Java programot?

 Az Aspose.Words for Java programot letöltheti a webhelyről, ha ellátogat a webhelyre[ezt a linket](https://releases.aspose.com/words/java/).

### Használhatok reguláris kifejezéseket a szöveg helyettesítésére?

Igen, használhat reguláris kifejezéseket a szöveg cseréjéhez az Aspose.Words for Java programban. Ez lehetővé teszi, hogy fejlettebb és rugalmasabb keresési és csereműveleteket hajtson végre.

### Hogyan hagyhatom figyelmen kívül a mezőkben lévő szöveget a csere során?

 mezőkben lévő szöveg figyelmen kívül hagyásához a csere során beállíthatja a`IgnoreFields` tulajdona a`FindReplaceOptions` hogy`true`. Ez biztosítja, hogy a mezőkön belüli szöveg, például az összevont mezők ne kerüljön ki a helyettesítésből.

### Cserélhetem a fejléceken és lábléceken belüli szöveget?

 Igen, lecserélheti a Word-dokumentum fejlécében és láblécében lévő szöveget. Egyszerűen nyissa meg a megfelelő fejlécet vagy láblécet, és használja a`replace` módszerrel a kívánt`FindReplaceOptions`.

### Mire jó a UseLegacyOrder opció?

 A`UseLegacyOrder` opció be`FindReplaceOptions` lehetővé teszi az örökölt sorrend használatát a keresési és csereműveletek végrehajtásakor. Ez hasznos lehet bizonyos forgatókönyvekben, amikor az örökölt rendelési viselkedés kívánatos.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

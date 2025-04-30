---
"description": "Tanuld meg, hogyan szúrhatsz be tartalomjegyzéket Wordben az Aspose.Words for .NET segítségével. Kövesd lépésről lépésre szóló útmutatónkat a zökkenőmentes dokumentumnavigációhoz."
"linktitle": "Tartalomjegyzék beszúrása Word dokumentumba"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Tartalomjegyzék beszúrása Word dokumentumba"
"url": "/hu/net/add-content-using-documentbuilder/insert-table-of-contents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tartalomjegyzék beszúrása Word dokumentumba

## Bevezetés
Ebben az oktatóanyagban megtanulod, hogyan adhatsz hatékonyan tartalomjegyzéket (TOC) Word-dokumentumaidhoz az Aspose.Words for .NET segítségével. Ez a funkció elengedhetetlen a hosszú dokumentumok rendszerezéséhez és navigálásához, az olvashatóság javításához és a dokumentum szakaszainak gyors áttekintéséhez.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következőkkel rendelkezik:

- C# és .NET keretrendszer alapismeretek.
- Visual Studio telepítve a gépedre.
- Aspose.Words .NET könyvtárhoz. Ha még nem telepítetted, letöltheted innen: [itt](https://releases.aspose.com/words/net/).

## Névterek importálása

Kezdéshez importáld a szükséges névtereket a C# projektedbe:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

Bontsuk le a folyamatot világos lépésekre:

## 1. lépés: Az Aspose.Words dokumentum és a DocumentBuilder inicializálása

Először inicializálj egy új Aspose.Words függvényt `Document` tárgy és egy `DocumentBuilder` együtt dolgozni:

```csharp
// Dokumentum és DocumentBuilder inicializálása
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Tartalomjegyzék beillesztése

Most illessze be a tartalomjegyzéket a `InsertTableOfContents` módszer:

```csharp
// Tartalomjegyzék beszúrása
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## 3. lépés: Dokumentumtartalom indítása új oldalon

A megfelelő formázás biztosítása érdekében a dokumentum tartalmát új oldalon kezdje:

```csharp
// Oldaltörés beszúrása
builder.InsertBreak(BreakType.PageBreak);
```

## 4. lépés: A dokumentum strukturálása címsorokkal

Rendszerezze a dokumentum tartalmát megfelelő címsorstílusok használatával:

```csharp
// Címsorstílusok beállítása
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## 5. lépés: A tartalomjegyzék frissítése és feltöltése

Frissítse a tartalomjegyzéket a dokumentum szerkezetének megfelelően:

```csharp
// A tartalomjegyzék mezőinek frissítése
doc.UpdateFields();
```

## 6. lépés: A dokumentum mentése

Végül mentse el a dokumentumot egy megadott könyvtárba:

```csharp
// Mentse el a dokumentumot
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## Következtetés

Tartalomjegyzék hozzáadása az Aspose.Words for .NET segítségével egyszerűen elvégezhető, és jelentősen javítja a dokumentumok használhatóságát. A következő lépéseket követve hatékonyan rendszerezheti és navigálhat összetett dokumentumokban.

## GYIK

### Testreszabhatom a tartalomjegyzék megjelenését?
Igen, testreszabhatja a tartalomjegyzék megjelenését és viselkedését az Aspose.Words for .NET API-k használatával.

### Az Aspose.Words támogatja a mezők automatikus frissítését?
Igen, az Aspose.Words lehetővé teszi a mezők, például a tartalomjegyzék dinamikus frissítését a dokumentum változásai alapján.

### Létrehozhatok több tartalomjegyzéket egyetlen dokumentumban?
Az Aspose.Words támogatja több tartalomjegyzék létrehozását különböző beállításokkal egyetlen dokumentumon belül.

### Kompatibilis az Aspose.Words a Microsoft Word különböző verzióival?
Igen, az Aspose.Words biztosítja a kompatibilitást a Microsoft Word formátumok különböző verzióival.

### Hol találok további segítséget és támogatást az Aspose.Words-höz?
További segítségért látogassa meg a [Aspose.Words Fórum](https://forum.aspose.com/c/words/8) vagy nézd meg a [hivatalos dokumentáció](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
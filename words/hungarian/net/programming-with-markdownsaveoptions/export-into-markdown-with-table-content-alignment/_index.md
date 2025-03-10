---
title: Exportálás a Markdown-ba a táblázattartalom igazításával
linktitle: Exportálás a Markdown-ba a táblázattartalom igazításával
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan exportálhat Word-dokumentumokat a Markdownba igazított táblázatokkal az Aspose.Words for .NET használatával. Kövesse lépésről lépésre útmutatónkat a tökéletes Markdown táblázatokhoz.
weight: 10
url: /hu/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportálás a Markdown-ba a táblázattartalom igazításával

## Bevezetés

Szia! Gondolkozott már azon, hogyan exportálhatja Word-dokumentumát Markdown formátumba tökéletesen igazított táblázatokkal? Függetlenül attól, hogy Ön fejlesztő a dokumentáción, vagy csak valaki, aki szereti a Markdownt, ez az útmutató az Ön számára készült. Elmerülünk az Aspose.Words for .NET használatával ennek eléréséhez. Készen áll arra, hogy Word-táblázatait szépen igazított Markdown-táblázatokká alakítsa? Kezdjük is!

## Előfeltételek

Mielőtt belemerülnénk a kódba, néhány dolgot meg kell határoznia:

1.  Aspose.Words for .NET Library: Győződjön meg arról, hogy rendelkezik az Aspose.Words for .NET könyvtárral. Letöltheti a[Az Aspose kiadási oldala](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Állítsa be fejlesztői környezetét. A Visual Studio népszerű választás .NET-fejlesztéshez.
3. Alapvető C# ismerete: A C# megértése elengedhetetlen, mivel ezen a nyelven fogunk kódot írni.
4. Word-dokumentum minta: Legyen egy Word-dokumentum, amelyet teszteléshez használhat.

## Névterek importálása

A kódolás megkezdése előtt importáljuk a szükséges névtereket. Ezek hozzáférést biztosítanak számunkra az Aspose.Words osztályokhoz és metódusokhoz, amelyeket használni fogunk.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuilder-t

Először is létre kell hoznunk egy új Word-dokumentumot, és inicializálnunk kell a`DocumentBuilder` tiltakozik a dokumentumunk elkészítésének megkezdése ellen.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Hozzon létre egy új dokumentumot.
Document doc = new Document();

// Inicializálja a DocumentBuilder programot.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Cellák beszúrása és tartalom igazítása

Ezután beszúrunk néhány cellát a dokumentumunkba, és beállítjuk az igazításukat. Ez döntő fontosságú annak biztosításához, hogy a Markdown export megtartja a megfelelő igazítást.

```csharp
// Szúrjon be egy cellát, és állítsa az igazítást jobbra.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Szúrjon be egy másik cellát, és állítsa az igazítást középre.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## 3. lépés: Állítsa be a táblázattartalom igazítását a Markdown exportáláshoz

 Most itt az ideje konfigurálni a`MarkdownSaveOptions` az exportált Markdown fájl táblázattartalmának igazításának szabályozására. Elmentjük a dokumentumot különböző igazítási beállításokkal, hogy megnézzük, hogyan működik.

```csharp
// MarkdownSaveOptions objektum létrehozása.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Dokumentum mentése balra igazítással.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Módosítsa az igazítást jobbra, és mentse.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Módosítsa az igazítást középre, és mentse.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## 4. lépés: Használja az automatikus táblázattartalom-igazítást

 A`Auto`Az igazítás opció a megfelelő táblázatoszlop első bekezdéséből veszi az igazítást. Ez akkor lehet hasznos, ha vegyes igazításokat tartalmaz egyetlen táblázatban.

```csharp
// Állítsa az igazítást Automatikusra.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Dokumentum mentése automatikus igazítással.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Következtetés

És megvan! A Word dokumentumok exportálása a Markdownba igazított táblázatokkal az Aspose.Words for .NET használatával gyerekjáték, ha már tudja, hogyan kell ezt megtenni. Ez a nagy teljesítményű könyvtár megkönnyíti a táblázatok formázásának és igazításának szabályozását, biztosítva, hogy a Markdown-dokumentumok úgy nézzenek ki, ahogyan szeretné. Boldog kódolást!

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, módosítását, konvertálását és exportálását.

### Beállíthatok különböző igazításokat ugyanazon táblázat különböző oszlopaihoz?
 Igen, a`Auto` igazítás opciót, akkor az egyes oszlopok első bekezdése alapján különböző igazításokat végezhet.

### Szükségem van licencre az Aspose.Words for .NET használatához?
 Igen, az Aspose.Words for .NET szolgáltatáshoz licenc szükséges a teljes funkcionalitáshoz. Kaphatsz a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) értékeléshez.

### Lehetséges más dokumentumelemeket exportálni a Markdownba az Aspose.Words használatával?
Igen, az Aspose.Words támogatja a különféle elemek, például a címsorok, listák és képek Markdown formátumba exportálását.

### Hol kaphatok támogatást, ha problémákba ütközöm?
 Támogatást kaphat a[Aspose.Words támogatási fórum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
title: Hozzon létre fejléc láblécet
linktitle: Hozzon létre fejléc láblécet
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan adhat hozzá és testreszabhat fejlécet és láblécet Word-dokumentumokhoz az Aspose.Words for .NET használatával. Ez a lépésenkénti útmutató biztosítja a professzionális dokumentumformázást.
weight: 10
url: /hu/net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hozzon létre fejléc láblécet

## Bevezetés

Fejlécek és láblécek hozzáadása a dokumentumokhoz javíthatja azok professzionalizmusát és olvashatóságát. Az Aspose.Words for .NET segítségével egyszerűen létrehozhat és testreszabhat fejlécet és láblécet Word-dokumentumaihoz. Ebben az oktatóanyagban lépésről lépésre végigvezetjük a folyamaton, így biztosítva, hogy ezeket a funkciókat zökkenőmentesen tudja megvalósítani.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:

-  Aspose.Words for .NET: Töltse le és telepítse a[letöltési link](https://releases.aspose.com/words/net/).
- Fejlesztési környezet: például a Visual Studio, a kód írásához és futtatásához.
- C# alapismeretek: C# és .NET keretrendszer ismerete.
- Mintadokumentum: Mintadokumentum a fejlécek és láblécek alkalmazásához, vagy új létrehozásához az oktatóanyagban látható módon.

## Névterek importálása

Először is importálnia kell a szükséges névtereket az Aspose.Words osztályok és metódusok eléréséhez.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## 1. lépés: Határozza meg a dokumentumkönyvtárat

Határozza meg a könyvtárat, ahová a dokumentumot menteni szeretné. Ez segít az útvonal hatékony kezelésében.

```csharp
// A dokumentumok könyvtárának elérési útja
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## 2. lépés: Hozzon létre egy új dokumentumot

 Hozzon létre egy új dokumentumot, és a`DocumentBuilder` tartalom hozzáadásának megkönnyítése érdekében.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Az oldalbeállítás konfigurálása

Adja meg az oldalbeállításokat, beleértve azt is, hogy az első oldal legyen-e más fejléc/lábléc.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## 4. lépés: Adjon hozzá fejlécet az első oldalhoz

Lépjen az első oldal fejlécére, és állítsa be a fejléc szövegét.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## 5. lépés: Adjon hozzá egy elsődleges fejlécet

Lépjen az elsődleges fejléc részre, és szúrjon be egy képet és szöveget.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Szúrjon be egy képet a fejlécbe
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## 6. lépés: Adjon hozzá egy elsődleges láblécet

Lépjen az elsődleges lábléc részre, és hozzon létre egy táblázatot a lábléc tartalmának formázásához.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Oldalszámozás hozzáadása
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## 7. lépés: Tartalom és oldaltörés hozzáadása

Lépjen a dokumentum végére, adjon meg egy oldaltörést, és hozzon létre egy új szakaszt különböző oldalbeállításokkal.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## 8. lépés: Másolja ki a fejléceket és lábléceket az előző részből

Ha egy korábbi szakasz fejléceit és lábléceit szeretné újra felhasználni, másolja ki őket, és hajtsa végre a szükséges módosításokat.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Következtetés

Ha követi ezeket a lépéseket, az Aspose.Words for .NET segítségével hatékonyan hozzáadhat és testreszabhat fejlécet és láblécet Word-dokumentumaihoz. Ez javítja a dokumentum megjelenését és professzionalizmusát, így olvashatóbbá és vonzóbbá teszi.

## GYIK

### Mi az Aspose.Words for .NET?

Az Aspose.Words for .NET egy olyan könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, szerkesztését és konvertálását .NET-alkalmazásokon belül.

### Hozzáadhatok képeket a fejléchez vagy lábléchez?

 Igen, egyszerűen hozzáadhat képeket a fejléchez vagy lábléchez a`DocumentBuilder.InsertImage` módszer.

### Hogyan állíthatok be különböző fejlécet és láblécet az első oldalhoz?

 Különböző fejléceket és lábléceket állíthat be az első oldalhoz a segítségével`DifferentFirstPageHeaderFooter` tulajdona a`PageSetup` osztály.

### Hol találok további dokumentációt az Aspose.Wordsről?

 Részletes dokumentációt találhat a[Aspose.Words API dokumentációs oldal](https://reference.aspose.com/words/net/).

### Van-e támogatás az Aspose.Words számára?

 Igen, az Aspose támogatást nyújt rajtuk keresztül[támogatási fórum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
"description": "Ismerje meg, hogyan adhat hozzá és szabhat testre fejléceket és lábléceket Word-dokumentumokban az Aspose.Words for .NET segítségével. Ez a lépésről lépésre szóló útmutató professzionális dokumentumformázást biztosít."
"linktitle": "Fejléc és lábléc létrehozása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Fejléc és lábléc létrehozása"
"url": "/hu/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Fejléc és lábléc létrehozása

## Bevezetés

Fejlécek és láblécek hozzáadása a dokumentumokhoz növelheti azok professzionalizmusát és olvashatóságát. Az Aspose.Words for .NET segítségével könnyedén létrehozhat és testreszabhat fejléceket és lábléceket Word-dokumentumaihoz. Ebben az oktatóanyagban lépésről lépésre végigvezetjük a folyamaton, biztosítva, hogy zökkenőmentesen megvalósíthassa ezeket a funkciókat.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következőkkel rendelkezik:

- Aspose.Words .NET-hez: Töltse le és telepítse a következő címről: [letöltési link](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Például a Visual Studio, a kód írásához és futtatásához.
- C# alapismeretek: A C# és a .NET keretrendszer ismerete.
- Mintadokumentum: Mintadokumentum a fejlécek és láblécek alkalmazásához, vagy egy új létrehozásához az oktatóanyagban látható módon.

## Névterek importálása

Először is importálnod kell a szükséges névtereket az Aspose.Words osztályok és metódusok eléréséhez.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## 1. lépés: A dokumentumkönyvtár meghatározása

Adja meg a könyvtárat, ahová a dokumentumot menteni szeretné. Ez segít az elérési út hatékony kezelésében.

```csharp
// A dokumentumok könyvtárának elérési útja
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## 2. lépés: Új dokumentum létrehozása

Hozz létre egy új dokumentumot és egy `DocumentBuilder` a tartalom hozzáadásának megkönnyítése érdekében.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Oldalbeállítás konfigurálása

Állítsa be az oldalbeállításokat, beleértve azt is, hogy az első oldalon eltérő fejléc/lábléc legyen-e.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## 4. lépés: Fejléc hozzáadása az első oldalhoz

Lépjen az első oldal fejléc szakaszába, és konfigurálja a fejléc szövegét.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## 5. lépés: Elsődleges fejléc hozzáadása

Lépjen az elsődleges fejléc szakaszba, és illesszen be egy képet és szöveget.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Kép beszúrása a fejlécbe
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## 6. lépés: Elsődleges lábléc hozzáadása

Lépjen az elsődleges lábléc szakaszba, és hozzon létre egy táblázatot a lábléc tartalmának formázásához.

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

## 7. lépés: Tartalom és oldaltörések hozzáadása

Ugrás a dokumentum végére, oldaltörés hozzáadása, és egy új szakasz létrehozása eltérő oldalbeállításokkal.

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

## 8. lépés: Fejlécek és láblécek másolása az előző szakaszból

Ha egy korábbi szakasz fejléceit és lábléceit szeretné újra felhasználni, másolja ki őket, és alkalmazza a szükséges módosításokat.

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

A következő lépéseket követve hatékonyan adhatsz hozzá és szabhatsz testre fejléceket és lábléceket a Word-dokumentumaidban az Aspose.Words for .NET segítségével. Ez javítja a dokumentum megjelenését és professzionalizmusát, így olvashatóbbá és lebilincselőbbé válik.

## GYIK

### Mi az Aspose.Words .NET-hez?

Az Aspose.Words for .NET egy olyan függvénytár, amely lehetővé teszi a fejlesztők számára, hogy Word dokumentumokat hozzanak létre, szerkesszenek és konvertáljanak programozottan a .NET alkalmazásokon belül.

### Hozzáadhatok képeket a fejléchez vagy a lábléchez?

Igen, könnyedén hozzáadhatsz képeket a fejléchez vagy a lábléchez a `DocumentBuilder.InsertImage` módszer.

### Hogyan tudok különböző fejléceket és lábléceket beállítani az első oldalra?

Az első oldalhoz különböző fejléceket és lábléceket állíthat be a `DifferentFirstPageHeaderFooter` a tulajdona `PageSetup` osztály.

### Hol találok további dokumentációt az Aspose.Words-ről?

Átfogó dokumentációt találhat a [Aspose.Words API dokumentációs oldal](https://reference.aspose.com/words/net/).

### Van elérhető támogatás az Aspose.Words-höz?

Igen, az Aspose támogatást nyújt a következőn keresztül: [támogatási fórum](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
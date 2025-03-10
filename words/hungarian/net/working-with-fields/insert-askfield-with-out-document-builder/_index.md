---
title: Az ASKField beszúrása Dokumentumkészítő nélkül
linktitle: Az ASKField beszúrása Dokumentumkészítő nélkül
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan szúrhat be ASK mezőt a Document Builder használata nélkül az Aspose.Words for .NET-ben. Kövesse ezt az útmutatót a Word-dokumentumok dinamikus javításához.
weight: 10
url: /hu/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Az ASKField beszúrása Dokumentumkészítő nélkül

## Bevezetés

Szeretné elsajátítani a dokumentumautomatizálást az Aspose.Words for .NET segítségével? Jó helyre jöttél! Ma végigvezetjük, hogyan szúrhat be egy ASK mezőt Dokumentumkészítő használata nélkül. Ez egy remek funkció, amikor azt szeretné, hogy a dokumentuma konkrét bevitelre kérje a felhasználókat, így a Word-dokumentumok interaktívabbak és dinamikusabbak. Tehát merüljünk bele, és tegyük okosabbá dokumentumainkat!

## Előfeltételek

Mielőtt bepiszkítanánk a kezünket egy kóddal, győződjünk meg arról, hogy mindent beállítottunk:

1.  Aspose.Words for .NET: Győződjön meg arról, hogy ez a könyvtár telepítve van. Ha nem, letöltheti innen[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: megfelelő IDE, mint a Visual Studio.
3. .NET-keretrendszer: Győződjön meg arról, hogy telepítve van a .NET-keretrendszer.

Nagy! Most, hogy készen vagyunk, kezdjük a szükséges névterek importálásával.

## Névterek importálása

Először is importálnunk kell az Aspose.Words névteret az Aspose.Words for .NET összes funkciójának eléréséhez. Íme, hogyan kell csinálni:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## 1. lépés: Hozzon létre egy új dokumentumot

Mielőtt beszúrhatnánk egy ASK mezőt, szükségünk van egy dokumentumra, amellyel dolgozni kell. A következőképpen hozhat létre új dokumentumot:

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Dokumentumkészítés.
Document doc = new Document();
```

Ez a kódrészlet létrehoz egy új Word-dokumentumot, amelyhez hozzáadjuk az ASK mezőt.

## 2. lépés: Lépjen be a bekezdéscsomóponthoz

A Word-dokumentumban a tartalom csomópontokba rendeződik. El kell érnünk az első bekezdés csomópontját, ahová beillesztjük az ASK mezőt:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Ez a kódsor lekéri a dokumentum első bekezdését, készen áll az ASK mező beszúrására.

## 3. lépés: Illessze be az ASK mezőt

Most pedig térjünk rá a fő eseményre – az ASK mező beillesztésére. Ez a mező a dokumentum megnyitásakor kéri a felhasználót a bevitelre.

```csharp
// Írja be az ASK mezőt.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Itt egy ASK mezőt fűzünk a bekezdéshez. Egyszerű, igaz?

## 4. lépés: Állítsa be az ASK mezőt

Be kell állítanunk néhány tulajdonságot az ASK mező viselkedésének meghatározásához. Konfiguráljuk a könyvjelző nevét, a prompt szöveget, az alapértelmezett választ és a körlevél viselkedését:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: Az ASK mező egyedi azonosítója.
- PromptText: Az a szöveg, amely a felhasználót bevitelre kéri.
- DefaultResponse: Az előre kitöltött válasz, amelyet a felhasználó módosíthat.
- PromptOnceOnMailMerge: Meghatározza, hogy a prompt csak egyszer jelenjen-e meg a körlevélkészítés során.

## 5. lépés: Frissítse a mezőt

Az ASK mező konfigurálása után frissítenünk kell, hogy biztosítsuk az összes beállítás helyes alkalmazását:

```csharp
field.Update();
```

Ez a parancs biztosítja, hogy az ASK mező készen áll, és megfelelően be van állítva a dokumentumban.

## 6. lépés: Mentse el a dokumentumot

Végül mentsük a dokumentumot a megadott könyvtárunkba:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Ez a sor menti a dokumentumot a beszúrt ASK mezővel. És itt van – a dokumentuma mostantól dinamikus ASK mezővel van felszerelve!

## Következtetés

Gratulálok! Éppen most adott hozzá egy ASK mezőt egy Word-dokumentumhoz az Aspose.Words for .NET használatával a Document Builder nélkül. Ez a funkció jelentősen javíthatja a felhasználói interakciót a dokumentumokkal, rugalmasabbá és felhasználóbarátabbá téve azokat. Kísérletezzen tovább a különböző mezőkkel és tulajdonságokkal, hogy kiaknázza az Aspose.Words teljes potenciálját. Boldog kódolást!

## GYIK

### Mi az ASK mező az Aspose.Words-ben?
Az Aspose.Words ASK mezője egy olyan mező, amely a dokumentum megnyitásakor konkrét bevitelt kér a felhasználótól, lehetővé téve a dinamikus adatbevitelt.

### Használhatok több ASK mezőt egyetlen dokumentumban?
Igen, egy dokumentumba több ASK mezőt is beilleszthet, amelyek mindegyike egyedi kérdésekkel és válaszokkal rendelkezik.

###  Mi a célja a`PromptOnceOnMailMerge` property?
 A`PromptOnceOnMailMerge` tulajdonság határozza meg, hogy az ASK prompt csak egyszer jelenik-e meg a körlevél-művelet során, vagy minden alkalommal.

### Frissítenem kell az ASK mezőt a tulajdonságainak beállítása után?
Igen, az ASK mező frissítése biztosítja, hogy minden tulajdonság megfelelően kerül alkalmazásra, és a mező a várt módon működik.

### Testreszabhatom a prompt szöveget és az alapértelmezett választ?
Teljesen! Beállíthat egyéni prompt szöveget és alapértelmezett válaszokat, hogy az ASK mezőt az Ön egyedi igényeihez igazítsa.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

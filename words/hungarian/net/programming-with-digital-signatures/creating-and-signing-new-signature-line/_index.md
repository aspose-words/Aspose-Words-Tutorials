---
"description": "Tanuld meg, hogyan hozhatsz létre és írhatsz digitálisan alá aláírási sort egy Word-dokumentumban az Aspose.Words for .NET használatával ebből a lépésről lépésre szóló oktatóanyagból. Tökéletes dokumentumautomatizáláshoz."
"linktitle": "Új aláírási sor létrehozása és aláírása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Új aláírási sor létrehozása és aláírása"
"url": "/hu/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Új aláírási sor létrehozása és aláírása

## Bevezetés

Szia! Szóval, van egy Word-dokumentumod, és hozzá kell adnod egy aláírási sort, majd digitálisan alá kell írnod. Bonyolultan hangzik? Egyáltalán nem! Az Aspose.Words for .NET-nek köszönhetően ezt zökkenőmentesen elérheted mindössze néhány sor kóddal. Ebben az oktatóanyagban végigvezetünk a teljes folyamaton, a környezet beállításától kezdve a dokumentum vadonatúj aláírással történő mentéséig. Készen állsz? Vágjunk bele!

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjünk meg róla, hogy minden szükséges dolog megvan:
1. Aspose.Words .NET-hez - Meg tudod csinálni [töltsd le itt](https://releases.aspose.com/words/net/).
2. Egy .NET fejlesztői környezet - Visual Studio - erősen ajánlott.
3. Aláírandó dokumentum – Hozzon létre egy egyszerű Word-dokumentumot, vagy használjon egy meglévőt.
4. Tanúsítványfájl – Erre digitális aláírásokhoz van szükség. Használhat egy `.pfx` fájl.
5. Aláírás sor képei – Opcionálisan egy képfájl az aláíráshoz.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ez a lépés kulcsfontosságú, mivel ez állítja be a környezetet az Aspose.Words funkciók használatához.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## 1. lépés: A dokumentumkönyvtár beállítása

Minden projekthez jó kezdés szükséges. Állítsuk be a dokumentumkönyvtár elérési útját. Ide lesznek mentve és lekérhetők a dokumentumok.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Új dokumentum létrehozása

Most hozzunk létre egy új Word dokumentumot az Aspose.Words használatával. Ez lesz a vászon, ahová az aláírási sort fogjuk beilleszteni.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Az aláírás sor beszúrása

Itt történik a varázslat. Aláírási sort illesztünk be a dokumentumunkba a következő segítségével: `DocumentBuilder` osztály.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## 4. lépés: A dokumentum mentése az aláírássorral

Miután az aláírási sor a helyén van, mentenünk kell a dokumentumot. Ez egy köztes lépés, mielőtt folytatnánk az aláírását.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## 5. lépés: Aláírási beállítások megadása

Most állítsuk be a dokumentum aláírásának beállításait. Ez magában foglalja az aláírási sor azonosítójának és a használandó képnek a megadását.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## 6. lépés: A tanúsítvány betöltése

A digitális aláírásokhoz tanúsítvány szükséges. Itt betöltjük a tanúsítványfájlt, amelyet a dokumentum aláírásához fogunk használni.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## 7. lépés: A dokumentum aláírása

Ez az utolsó lépés. A következőt használjuk: `DigitalSignatureUtil` osztály a dokumentum aláírásához. Az aláírt dokumentum új néven kerül mentésre.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Következtetés

És íme! Ezekkel a lépésekkel sikeresen létrehoztál egy új Word-dokumentumot, hozzáadtál egy aláírási sort, és digitálisan aláírtad az Aspose.Words for .NET segítségével. Ez egy hatékony eszköz, amely gyerekjátékká teszi a dokumentumautomatizálást. Akár szerződésekkel, megállapodásokkal vagy bármilyen hivatalos dokumentummal van dolgod, ez a módszer biztosítja azok biztonságos aláírását és hitelesítését.

## GYIK

### Használhatok más képformátumokat az aláírássorhoz?
Igen, különféle képformátumokat használhat, például PNG, JPG, BMP stb.

### Szükséges-e használni egy `.pfx` fájl a tanúsítványhoz?
Igen, egy `.pfx` A fájl egy elterjedt formátum kriptográfiai információk, például tanúsítványok és privát kulcsok tárolására.

### Hozzáadhatok több aláírási sort egyetlen dokumentumhoz?
Természetesen! Több aláírási sort is beszúrhat a beszúrási lépés megismétlésével minden aláírásnál.

### Mi van, ha nincs digitális tanúsítványom?
Digitális tanúsítványt kell beszereznie egy megbízható hitelesítésszolgáltatótól, vagy létre kell hoznia egyet olyan eszközökkel, mint az OpenSSL.

### Hogyan tudom ellenőrizni a dokumentumban lévő digitális aláírást?
Megnyithatja az aláírt dokumentumot a Wordben, és az aláírás részleteinél ellenőrizheti az aláírás hitelességét és integritását.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
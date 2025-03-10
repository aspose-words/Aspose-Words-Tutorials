---
title: Új aláírási sor létrehozása és aláírása
linktitle: Új aláírási sor létrehozása és aláírása
second_title: Aspose.Words Document Processing API
description: Ebből a lépésről lépésre mutató oktatóanyagból megtudhatja, hogyan hozhat létre és digitálisan írhat alá aláírási sort egy Word-dokumentumban az Aspose.Words for .NET használatával. Ideális dokumentumautomatizáláshoz.
weight: 10
url: /hu/net/programming-with-digital-signatures/creating-and-signing-new-signature-line/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Új aláírási sor létrehozása és aláírása

## Bevezetés

Szia! Tehát van egy Word-dokumentuma, és hozzá kell adnia egy aláírási sort, majd digitálisan alá kell írnia. Trükkösnek hangzik? Egyáltalán nem! Az Aspose.Words for .NET-nek köszönhetően ezt zökkenőmentesen elérheti néhány sornyi kóddal. Ebben az oktatóanyagban végigvezetjük a teljes folyamaton a környezet beállításától a dokumentum csillogó új aláírással történő mentéséig. Kész? Merüljünk el!

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjünk meg arról, hogy mindennel rendelkezik, amire szüksége van:
1.  Aspose.Words for .NET – Megteheti[töltse le itt](https://releases.aspose.com/words/net/).
2. A .NET fejlesztői környezet – Visual Studio erősen ajánlott.
3. Aláírandó dokumentum – Hozzon létre egy egyszerű Word-dokumentumot, vagy használjon egy meglévőt.
4.  Tanúsítványfájl – Ez a digitális aláírásokhoz szükséges. Használhatja a`.pfx` fájlt.
5. Képek az aláírássorhoz – opcionálisan egy képfájl az aláíráshoz.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ez a lépés kulcsfontosságú, mivel beállítja az Aspose.Words funkciók használatának környezetét.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## 1. lépés: A dokumentumkönyvtár beállítása

Minden projekthez jó kezdés szükséges. Állítsuk be a dokumentumkönyvtár elérési útját. Ez az a hely, ahol a dokumentumok mentése és visszakeresése történik.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Új dokumentum létrehozása

Most hozzunk létre egy új Word-dokumentumot az Aspose.Words használatával. Ez lesz a vásznunk, ahol hozzáadjuk az aláírási sort.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3. lépés: Az aláírási sor beszúrása

 Itt történik a varázslat. A dokumentumunkba egy aláírási sort szúrunk be a`DocumentBuilder` osztály.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## 4. lépés: A dokumentum mentése az aláírási sorral

Miután az aláírási sor a helyére került, el kell mentenünk a dokumentumot. Ez egy közbülső lépés az aláírás előtt.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## 5. lépés: Az aláírási lehetőségek beállítása

Most állítsuk be a dokumentum aláírásának lehetőségeit. Ez magában foglalja az aláírási sor azonosítójának és a használandó kép megadását.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf")
};
```

## 6. lépés: A tanúsítvány betöltése

A digitális aláírásokhoz tanúsítvány szükséges. Itt betöltjük a tanúsítványfájlt, amely a dokumentum aláírására szolgál.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## 7. lépés: A dokumentum aláírása

 Ez az utolsó lépés. Használjuk a`DigitalSignatureUtil`osztályt aláírni a dokumentumot. Az aláírt dokumentum új néven kerül mentésre.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.NewSignatureLine.docx", certHolder, signOptions);
```

## Következtetés

És megvan! Ezekkel a lépésekkel sikeresen létrehozott egy új Word-dokumentumot, hozzáadott egy aláírási sort, és digitálisan aláírta az Aspose.Words for .NET használatával. Ez egy hatékony eszköz, amely a dokumentumautomatizálást gyerekjátékká teszi. Legyen szó szerződésekről, megállapodásokról vagy bármilyen hivatalos dokumentumról, ez a módszer biztosítja azok biztonságos aláírását és hitelesítését.

## GYIK

### Használhatok más képformátumokat az aláírási sorhoz?
Igen, különféle képformátumokat használhat, például PNG, JPG, BMP stb.

###  Szükséges-e használni a`.pfx` file for the certificate?
 Igen, a`.pfx` fájl egy elterjedt formátum a kriptográfiai információk, köztük a tanúsítványok és privát kulcsok tárolására.

### Hozzáadhatok több aláírási sort egyetlen dokumentumhoz?
Teljesen! Több aláírási sort is beszúrhat úgy, hogy minden aláírásnál megismétli a beszúrási lépést.

### Mi a teendő, ha nincs digitális tanúsítványom?
Be kell szereznie egy digitális tanúsítványt egy megbízható tanúsító hatóságtól, vagy létre kell hoznia egyet olyan eszközökkel, mint az OpenSSL.

### Hogyan ellenőrizhetem a digitális aláírást a dokumentumban?
Megnyithatja az aláírt dokumentumot a Wordben, és az aláírás részleteihez lépve ellenőrizheti az aláírás hitelességét és integritását.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

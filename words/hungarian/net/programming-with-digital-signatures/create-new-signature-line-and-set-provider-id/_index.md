---
title: Hozzon létre új aláírási sort és állítsa be a szolgáltatói azonosítót
linktitle: Hozzon létre új aláírási sort és állítsa be a szolgáltatói azonosítót
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan hozhat létre új aláírási sort, és hogyan állíthatja be a szolgáltatói azonosítót a Word dokumentumokban az Aspose.Words for .NET használatával. Lépésről lépésre útmutató.
weight: 10
url: /hu/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hozzon létre új aláírási sort és állítsa be a szolgáltatói azonosítót

## Bevezetés

Sziasztok, a technika szerelmesei! Gondolkozott már azon, hogyan lehet programozottan aláírássort hozzáadni a Word-dokumentumokhoz? Nos, ma éppen ebben merülünk el az Aspose.Words for .NET használatával. Ez az útmutató végigvezeti Önt minden lépésen, így egyszerűen létrehozhat egy új aláírási sort, és beállíthatja a szolgáltatói azonosítót a Word-dokumentumokban. Akár automatizálja a dokumentumfeldolgozást, akár csak a munkafolyamat egyszerűsítését szeretné elérni, ez az oktatóanyag mindenre kiterjed.

## Előfeltételek

Mielőtt bemocskolnánk a kezünket, győződjünk meg arról, hogy mindennel rendelkezünk, amire szükségünk van:

1.  Aspose.Words for .NET: Ha még nem tette meg, töltse le[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Visual Studio vagy bármely más C# fejlesztői környezet.
3. .NET-keretrendszer: Győződjön meg arról, hogy telepítve van a .NET-keretrendszer.
4. PFX-tanúsítvány: A dokumentumok aláírásához PFX-tanúsítványra lesz szüksége. Megbízható hitelesítésszolgáltatótól szerezhet be egyet.

## Névterek importálása

Először is importáljuk a szükséges névtereket a C# projektbe:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Rendben, térjünk a lényegre. Itt található az új aláírási sor létrehozásához és a szolgáltatói azonosító beállításához szükséges lépések részletes lebontása.

## 1. lépés: Hozzon létre egy új dokumentumot

A kezdéshez létre kell hoznunk egy új Word dokumentumot. Ez lesz a vászon az aláírási sorunkhoz.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ebben a részletben egy újat inicializálunk`Document` és a`DocumentBuilder` . A`DocumentBuilder` segít elemeket hozzáadni a dokumentumunkhoz.

## 2. lépés: Adja meg az aláírási sor beállításait

Ezután meghatározzuk az aláírási sorunk beállításait. Ez magában foglalja az aláíró nevét, beosztását, e-mail-címét és egyéb adatait.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Ezek a lehetőségek személyre szabják az aláírási vonalat, egyértelművé és professzionálissá téve azt.

## 3. lépés: Illessze be az aláírási sort

A beállított opciókkal már beilleszthetjük az aláírási sort a dokumentumba.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Itt, a`InsertSignatureLine` metódus hozzáadja az aláírási sort, és egyedi szolgáltatói azonosítót rendelünk hozzá.

## 4. lépés: Mentse el a dokumentumot

Az aláírási sor beszúrása után mentsük el a dokumentumot.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Ezzel elmenti a dokumentumot az újonnan hozzáadott aláírási sorral.

## 5. lépés: Az aláírási beállítások beállítása

Most be kell állítanunk a dokumentum aláírásának lehetőségeit. Ez magában foglalja az aláírási sor azonosítóját, a szolgáltató azonosítóját, a megjegyzéseket és az aláírási időt.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Ezek az opciók biztosítják, hogy a dokumentumot a megfelelő adatokkal írják alá.

## 6. lépés: Hozzon létre tanúsítványtulajdonost

A dokumentum aláírásához PFX tanúsítványt használunk. Hozzunk létre egy tanúsítvány tulajdonost hozzá.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Ügyeljen arra, hogy cserélje ki`"morzal.pfx"` a tényleges tanúsítványfájljával és`"aw"` a tanúsítvány jelszavával.

## 7. lépés: Aláírja a dokumentumot

Végül a digitális aláírási segédprogrammal aláírjuk a dokumentumot.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Ez aláírja a dokumentumot, és új fájlként menti.

## Következtetés

És megvan! Sikeresen létrehozott egy új aláírási sort, és beállította a szolgáltatói azonosítót egy Word-dokumentumban az Aspose.Words for .NET használatával. Ez a nagy teljesítményű könyvtár hihetetlenül egyszerűvé teszi a dokumentumfeldolgozási feladatok kezelését és automatizálását. Próbálja ki, és nézze meg, hogyan tudja egyszerűsíteni a munkafolyamatot.

## GYIK

### Testreszabhatom az aláírássor megjelenését?
 Teljesen! Különféle lehetőségeket módosíthat a`SignatureLineOptions`hogy megfeleljen az Ön igényeinek.

### Mi a teendő, ha nincs PFX tanúsítványom?
Be kell szereznie egyet egy megbízható tanúsító hatóságtól. Ez elengedhetetlen a dokumentumok digitális aláírásához.

### Hozzáadhatok több aláírási sort egy dokumentumhoz?
Igen, tetszőleges számú aláírási sort hozzáadhat a beillesztési folyamat különböző opciókkal történő megismétlésével.

### Az Aspose.Words for .NET kompatibilis a .NET Core-al?
Igen, az Aspose.Words for .NET támogatja a .NET Core-t, így sokoldalúan használható különböző fejlesztői környezetekben.

### Mennyire biztonságosak a digitális aláírások?
Az Aspose.Words segítségével létrehozott digitális aláírások rendkívül biztonságosak, feltéve, hogy érvényes és megbízható tanúsítványt használ.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
"description": "Ismerje meg, hogyan hozhat létre új aláírási sort és állíthat be szolgáltatói azonosítót Word-dokumentumokban az Aspose.Words for .NET használatával. Lépésről lépésre útmutató."
"linktitle": "Új aláírási sor létrehozása és szolgáltató azonosítójának beállítása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Új aláírási sor létrehozása és szolgáltató azonosítójának beállítása"
"url": "/hu/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Új aláírási sor létrehozása és szolgáltató azonosítójának beállítása

## Bevezetés

Sziasztok, tech-rajongók! Elgondolkodtatok már azon, hogyan lehet programozottan aláírássort hozzáadni a Word-dokumentumaitokhoz? Nos, ma pontosan ebbe fogunk belevágni az Aspose.Words for .NET használatával. Ez az útmutató végigvezet minden lépésen, így gyerekjáték létrehozni egy új aláírássort és beállítani a szolgáltató azonosítóját a Word-dokumentumaitokban. Akár automatizáljátok a dokumentumfeldolgozást, akár csak egyszerűsíteni szeretnétek a munkafolyamatotokat, ez az oktatóanyag segít nektek.

## Előfeltételek

Mielőtt belevágnánk, nézzük meg, hogy mindenünk megvan-e, amire szükségünk van:

1. Aspose.Words .NET-hez: Ha még nem tetted meg, töltsd le [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Visual Studio vagy bármilyen más C# fejlesztői környezet.
3. .NET-keretrendszer: Győződjön meg arról, hogy telepítve van a .NET-keretrendszer.
4. PFX tanúsítvány: Dokumentumok aláírásához PFX tanúsítványra lesz szüksége. Ilyet egy megbízható hitelesítésszolgáltatótól szerezhet be.

## Névterek importálása

Először is, importáljuk a szükséges névtereket a C# projektedbe:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Rendben, térjünk a lényegre. Íme egy részletes leírás az új aláírási sor létrehozásának és a szolgáltatói azonosító beállításának lépéseiről.

## 1. lépés: Új dokumentum létrehozása

Kezdésként létre kell hoznunk egy új Word-dokumentumot. Ez lesz az aláírási sorunk alapja.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ebben a kódrészletben egy újat inicializálunk `Document` és egy `DocumentBuilder`. A `DocumentBuilder` segít elemeket hozzáadni a dokumentumunkhoz.

## 2. lépés: Aláírási sor beállításainak meghatározása

Ezután meghatározzuk az aláírás sor beállításait. Ez magában foglalja az aláíró nevét, beosztását, e-mail címét és egyéb adatokat.

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

Ezek a beállítások személyre szabják az aláírási sort, így az világos és professzionális.

## 3. lépés: Az aláírás sor beillesztése

A beállítások megadásával most már beilleszthetjük az aláírás sort a dokumentumba.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

Itt a `InsertSignatureLine` A metódus hozzáadja az aláírási sort, és hozzárendelünk egy egyedi szolgáltatói azonosítót.

## 4. lépés: A dokumentum mentése

Az aláírás sor beillesztése után mentsük el a dokumentumot.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Ez a dokumentumot az újonnan hozzáadott aláírássorral menti.

## 5. lépés: Aláírási beállítások megadása

Most be kell állítanunk a dokumentum aláírásának beállításait. Ez magában foglalja az aláírási sor azonosítóját, a szolgáltató azonosítóját, a megjegyzéseket és az aláírás időpontját.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Ezek a beállítások biztosítják, hogy a dokumentum a megfelelő adatokkal legyen aláírva.

## 6. lépés: Tanúsítványtulajdonos létrehozása

A dokumentum aláírásához egy PFX tanúsítványt fogunk használni. Hozzunk létre hozzá egy tanúsítványtulajdonost.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

Mindenképpen cserélje ki `"morzal.pfx"` a tényleges tanúsítványfájloddal és `"aw"` a tanúsítványod jelszavával.

## 7. lépés: A dokumentum aláírása

Végül a digitális aláírás segédprogrammal aláírjuk a dokumentumot.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Ez aláírja a dokumentumot, és új fájlként menti el.

## Következtetés

És íme! Sikeresen létrehoztál egy új aláírássort és beállítottad a szolgáltatói azonosítót egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ez a hatékony függvénykönyvtár hihetetlenül egyszerűvé teszi a dokumentumfeldolgozási feladatok kezelését és automatizálását. Próbáld ki, és nézd meg, hogyan egyszerűsítheti a munkafolyamatodat.

## GYIK

### Testreszabhatom az aláírássor megjelenését?
Természetesen! Különböző beállításokat módosíthatsz a `SignatureLineOptions` hogy megfeleljen az igényeidnek.

### Mi van, ha nincs PFX tanúsítványom?
Megbízható hitelesítésszolgáltatótól kell beszereznie egyet. Ez elengedhetetlen a dokumentumok digitális aláírásához.

### Hozzáadhatok több aláírási sort egy dokumentumhoz?
Igen, annyi aláírási sort adhat hozzá, amennyire szüksége van, a beszúrási folyamat különböző beállításokkal történő megismétlésével.

### Kompatibilis az Aspose.Words for .NET a .NET Core-ral?
Igen, az Aspose.Words for .NET támogatja a .NET Core-t, így sokoldalúan használható különböző fejlesztési környezetekben.

### Mennyire biztonságosak a digitális aláírások?
Az Aspose.Words segítségével létrehozott digitális aláírások rendkívül biztonságosak, feltéve, hogy érvényes és megbízható tanúsítványt használ.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
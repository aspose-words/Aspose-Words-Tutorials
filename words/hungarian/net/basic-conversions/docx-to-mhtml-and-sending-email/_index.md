---
"description": "Tanuld meg, hogyan konvertálhatsz DOCX fájlokat MHTML-lé, és hogyan küldhetsz e-maileket az Aspose.Words for .NET segítségével ebben a lépésről lépésre szóló útmutatóban. Növeld a termelékenységedet egyszerű automatizálással."
"linktitle": "Docx konvertálása Mhtml-be és e-mail küldése"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Docx konvertálása Mhtml-be és e-mail küldése"
"url": "/hu/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Docx konvertálása Mhtml-be és e-mail küldése

## Bevezetés

mai digitális korban a dokumentumok egyik formátumból a másikba konvertálása és e-mailben történő elküldése gyakori feladat. Ez a cikk végigvezeti Önt egy DOCX fájl MHTML formátumba konvertálásának folyamatán, majd az Aspose.Words for .NET segítségével e-mailben történő elküldésének folyamatán. Minden lépést részletesen, könnyen követhető útmutatóban ismertetünk, biztosítva, hogy az elejétől a végéig megértse a folyamatot. Vágjunk bele!

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

1. Aspose.Words .NET-hez: Töltse le és telepítse az Aspose.Words .NET-hez könyvtárat a következő helyről: [Aspose kiadási oldal](https://releases.aspose.com/words/net/).
2. Aspose.Email .NET-hez: Töltse le és telepítse az Aspose.Email .NET-hez könyvtárat a következő helyről: [Aspose kiadási oldal](https://releases.aspose.com/email/net/).
3. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a gépén.
4. SMTP-kiszolgáló: E-mailek küldéséhez hozzáférésre van szükség egy SMTP-kiszolgálóhoz.

## Névterek importálása

Az Aspose.Words és az Aspose.Email használatához a projektedben importálnod kell a szükséges névtereket. Add hozzá a következőket a C# fájlod elejéhez direktívák használatával:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Bontsuk a folyamatot több lépésre, hogy biztosan minden egyes részt világosan megértsünk.

## 1. lépés: Töltse be a DOCX dokumentumot

Először is be kell töltened a konvertálni kívánt DOCX dokumentumot. Használd a `Document` osztály az Aspose.Words fájlból a DOCX fájl betöltéséhez.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## 2. lépés: Mentse el a dokumentumot MHTML formátumban

Ezután mentse el a betöltött dokumentumot MHTML fájlként. Ezt a következővel teheti meg: `Save` a módszer `Document` osztály.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Tekerd vissza a streamet az elejére, hogy az Aspose.Email el tudja olvasni.
stream.Position = 0;
```

## 3. lépés: E-mail üzenet létrehozása

Most hozz létre egy e-mail üzenetet az MHTML-folyamból az Aspose.Email használatával. Használni fogod a `MailMessage` osztály erre a célra.

```csharp
// Hozz létre egy Aspose.Email MIME e-mail üzenetet a streamből.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## 4. lépés: Küldd el az e-mailt

Végül küldje el az e-mailt egy SMTP kliens segítségével. Konfigurálja az SMTP klienst az SMTP szerver adataival, és használja a `Send` módszer az üzenet elküldésére.

```csharp
// Küldd el az üzenetet az Aspose.Email használatával.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Következtetés

Gratulálunk! Sikeresen konvertáltál egy DOCX dokumentumot MHTML formátumba, és elküldted e-mailben az Aspose.Words for .NET segítségével. Ez a folyamat magában foglalja a dokumentum betöltését, MHTML formátumba konvertálását, egy e-mail üzenet létrehozását és elküldését egy SMTP klienssel. Ezekkel a lépésekkel könnyedén automatizálhatod a dokumentumok konvertálását és e-mailben küldését az alkalmazásaidban.

## GYIK

### Használhatom ezt a módszert más dokumentumformátumok konvertálására?
Igen, az Aspose.Words különféle formátumokat támogat, és olyan dokumentumokat konvertálhatsz MHTML-re, mint a DOC, DOCX, RTF és egyebek.

### Hogyan tudok mellékleteket hozzáadni az e-mailhez?
Használhatod a `Attachments` a tulajdona `MailMessage` osztály mellékletek hozzáadásához az e-mailhez.

### Kompatibilis az Aspose.Words a .NET Core-ral?
Igen, az Aspose.Words kompatibilis a .NET Core-ral. .NET Core alkalmazásokban is használható.

### Szükségem van licencre az Aspose.Words és az Aspose.Email alkalmazásokhoz?
Igen, mindkét könyvtárhoz licenc szükséges. Ideiglenes licencet szerezhet be a [Aspose vásárlási oldal](https://purchase.aspose.com/temporary-license/) értékelési célokra.

### Hol találok további dokumentációt?
Az Aspose.Words részletes dokumentációját itt találod. [itt](https://reference.aspose.com/words/net/) és az Aspose.Email számára [itt](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
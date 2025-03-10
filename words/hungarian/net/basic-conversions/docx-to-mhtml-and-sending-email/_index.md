---
title: A Docx konvertálása Mhtml-re és e-mail küldése
linktitle: A Docx konvertálása Mhtml-re és e-mail küldése
second_title: Aspose.Words Document Processing API
description: Ebből a lépésről lépésre szóló útmutatóból megtudhatja, hogyan konvertálhat DOCX-et MHTML-re, és hogyan küldhet e-maileket az Aspose.Words for .NET használatával. Növelje termelékenységét az egyszerű automatizálással.
weight: 10
url: /hu/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# A Docx konvertálása Mhtml-re és e-mail küldése

## Bevezetés

mai digitális korban gyakori feladat a dokumentumok egyik formátumból a másikba konvertálása és e-mailben történő elküldése. Ez a cikk végigvezeti a DOCX-fájlok MHTML formátumba konvertálásának folyamatán, majd az Aspose.Words for .NET használatával e-mailben történő elküldésén. Az egyes lépéseket egy részletes, könnyen követhető útmutatóban részletezzük, biztosítva, hogy az elejétől a végéig megértse a folyamatot. Merüljünk el!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

1.  Aspose.Words for .NET: Töltse le és telepítse az Aspose.Words for .NET könyvtárat a[Az Aspose kiadási oldala](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET: Töltse le és telepítse az Aspose.Email for .NET könyvtárat a[Az Aspose kiadási oldala](https://releases.aspose.com/email/net/).
3. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a számítógépen.
4. SMTP-szerver: E-mailek küldéséhez hozzá kell férnie egy SMTP-kiszolgálóhoz.

## Névterek importálása

Az Aspose.Words és az Aspose.Email használatához a projektben importálnia kell a szükséges névtereket. Adja hozzá a következőket a C# fájl tetején található direktívák használatával:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Bontsuk le a folyamatot több lépésre, hogy biztosan megértse az egyes részeket.

## 1. lépés: Töltse be a DOCX-dokumentumot

 Először is be kell töltenie a konvertálni kívánt DOCX dokumentumot. Használja a`Document` osztályt az Aspose.Words webhelyről a DOCX fájl betöltéséhez.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## 2. lépés: Mentse el a dokumentumot MHTML-ként

 Ezután mentse a betöltött dokumentumot MHTML-fájlként. Ez a`Save` módszere a`Document` osztály.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Tekerje vissza az adatfolyamot az elejére, hogy az Aspose.Email elolvashassa.
stream.Position = 0;
```

## 3. lépés: Hozzon létre egy e-mail üzenetet

 Most hozzon létre egy e-mail üzenetet az MHTML-folyamból az Aspose.Email segítségével. Használni fogod a`MailMessage` osztályt erre a célra.

```csharp
// Hozzon létre egy Aspose.Email MIME e-mail üzenetet az adatfolyamból.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## 4. lépés: Küldje el az e-mailt

 Végül küldje el az e-mailt egy SMTP-kliens segítségével. Konfigurálja az SMTP-klienst az SMTP-kiszolgáló adataival, és használja a`Send` az üzenet küldésének módja.

```csharp
// Küldje el az üzenetet az Aspose.Email használatával.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Következtetés

Gratulálok! Sikeresen konvertált egy DOCX-dokumentumot MHTML-re, és elküldte e-mailben az Aspose.Words for .NET használatával. Ez a folyamat magában foglalja a dokumentum betöltését, MHTML formátumba konvertálását, e-mail üzenet létrehozását és SMTP kliens segítségével történő elküldését. Ezekkel a lépésekkel egyszerűen automatizálhatja az alkalmazásokban található dokumentumok konvertálását és e-mailben történő elküldését.

## GYIK

### Használhatom ezt a módszert más dokumentumformátumok konvertálására?
Igen, az Aspose.Words különféle formátumokat támogat, és olyan dokumentumokat konvertálhat MHTML formátumba, mint a DOC, DOCX, RTF és egyebek.

### Hogyan adhatok mellékleteket az e-mailhez?
 Használhatja a`Attachments` tulajdona a`MailMessage` osztályt, hogy mellékleteket adjon az e-mailekhez.

### Az Aspose.Words kompatibilis a .NET Core-al?
Igen, az Aspose.Words kompatibilis a .NET Core-al. Használhatja .NET Core alkalmazásokban is.

### Szükségem van licencre az Aspose.Words és az Aspose.Email használatához?
 Igen, mindkét könyvtárhoz licenc szükséges. Ideiglenes jogosítványt kaphat a[Aspose vásárlási oldal](https://purchase.aspose.com/temporary-license/) értékelési célokra.

### Hol találok további dokumentációt?
 Az Aspose.Words részletes dokumentációja megtalálható[itt](https://reference.aspose.com/words/net/) és az Aspose.Email számára[itt](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

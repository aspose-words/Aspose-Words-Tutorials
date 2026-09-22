---
date: 2025-12-20
description: Ismerje meg, hogyan lehet HTML-t betölteni és HTML-t DOCX formátumba
  konvertálni az Aspose.Words for Java segítségével. A lépésről‑lépésre útmutató bemutatja,
  hogyan lehet DOCX fájlokat menteni és strukturált dokumentumcímkéket használni.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Hogyan töltsünk be HTML-t és mentsük DOCX formátumban az Aspose.Words for Java
  segítségével
url: /hu/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# HTML betöltése és DOCX-be mentése Aspose.Words for Java használatával

## Bevezetés a HTML dokumentumok betöltésébe és mentésébe az Aspose.Words for Java segítségével

Ebben a cikkben megvizsgáljuk, hogyan **töltsünk be HTML-t** és mentsük el DOCX fájlként az Aspose.Words for Java könyvtár segítségével. Az Aspose.Words egy erőteljes API, amely lehetővé teszi a Word dokumentumok programozott manipulálását, és robusztus támogatást nyújt a HTML importáláshoz/exportáláshoz. Végigvezetünk a teljes folyamaton, a betöltési beállítások konfigurálásától a végeredmény Word dokumentumként történő mentéséig.

## Gyors válaszok
- **Mi a fő osztály a HTML betöltéséhez?** `Document` együtt a `HtmlLoadOptions`-szal.
- **Melyik opció engedélyezi a Structured Document Tag-eket?** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Átalakíthatom a HTML-t DOCX-be egy lépésben?** Igen – töltsd be a HTML-t és hívd meg a `doc.save(...".docx")`-t.
- **Szükségem van licencre a fejlesztéshez?** Egy ingyenes próba verzió teszteléshez elegendő; a termeléshez kereskedelmi licenc szükséges.
- **Milyen Java verzió szükséges?** A Java 8 vagy újabb támogatott.

## Mi jelent a „hogyan töltsünk be HTML-t” az Aspose.Words kontextusában?

A HTML betöltése azt jelenti, hogy egy HTML karakterláncot vagy fájlt beolvasunk, és átalakítjuk egy Aspose.Words `Document` objektummá. Ez az objektum ezután szerkeszthető, formázható, vagy elmenthető bármely, az API által támogatott formátumba, például DOCX, PDF vagy RTF.

## Miért használjuk az Aspose.Words-ot HTML‑ból‑DOCX konverzióhoz?
- **Megőrzi az elrendezést** – a táblázatok, listák és képek változatlanul maradnak.
- **Támogatja a Structured Document Tag-eket** – ideális tartalomvezérlők létrehozásához a Wordben.
- **Nem szükséges a Microsoft Office** – bármilyen szerveren vagy felhő környezetben működik.
- **Magas teljesítmény** – nagy HTML fájlokat gyorsan dolgoz fel.

## Előfeltételek

1. **Aspose.Words for Java könyvtár** – töltsd le innen: [here](https://releases.aspose.com/words/java/).
2. **Java fejlesztői környezet** – JDK 8+ telepítve és konfigurálva.
3. **Alapvető ismeretek a Java I/O-val** – a `ByteArrayInputStream`-et használjuk a HTML karakterlánc betáplálásához.

## HTML dokumentumok betöltése

Az alábbiakban egy tömör példa látható, amely bemutatja egy HTML részlet betöltését, miközben engedélyezi a **structured document tag** funkciót.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Magyarázat**

- Létrehozunk egy `HTML` karakterláncot, amely egy egyszerű `<select>` vezérlőt tartalmaz.
- A `HtmlLoadOptions` lehetővé teszi, hogy megadjuk, hogyan értelmezze a HTML-t. A preferált vezérlő típus `STRUCTURED_DOCUMENT_TAG`-ra állítása azt mondja az Aspose.Words-nak, hogy a HTML űrlapvezérlőket Word tartalomvezérlőkké konvertálja.
- A `Document` konstruktor a `ByteArrayInputStream`-ből olvassa be a HTML-t UTF‑8 kódolással.

## Mentés DOCX formátumba (HTML‑ból‑DOCX konverzió)

Miután a HTML be lett töltve egy `Document` objektumba, a DOCX fájlba mentése egyszerű:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Cseréld le a `"Your Directory Path"`-t a tényleges mappára, ahová a kimeneti fájlt szeretnéd menteni.

## Teljes forráskód a HTML dokumentumok betöltéséhez és mentéséhez

Az alábbiakban a teljes, azonnal futtatható példa látható, amely egyesíti a betöltési és mentési lépéseket. Nyugodtan másold be a saját IDE-dbe.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Gyakori buktatók és tippek

| Issue | Why it Happens | How to Fix |
|-------|----------------|------------|
| **Hiányzó betűtípusok** | A HTML olyan betűtípusokra hivatkozik, amelyek nincsenek telepítve a szerveren. | `FontSettings` használatával ágyazd be a betűtípusokat a DOCX-be, vagy biztosítsd, hogy a szükséges betűtípusok elérhetők legyenek. |
| **Képek nem jelennek meg** | A relatív képelérési útvonalak nem oldhatók fel. | Használj abszolút URL-eket, vagy töltsd be a képeket egy `MemoryStream`-be, és állítsd be a `HtmlLoadOptions.setImageSavingCallback`-et. |
| **A vezérlő típusa nem konvertálódik** | `setPreferredControlType` nincs beállítva, vagy rossz enum értékre van állítva. | Ellenőrizd, hogy a `HtmlControlType.STRUCTURED_DOCUMENT_TAG`-et használod. |
| **Kódolási problémák** | A HTML karakterlánc más karakterkódolással van kódolva. | Mindig a `StandardCharsets.UTF_8`-et használd a karakterlánc bájtokká konvertálásakor. |

## Gyakran Ismételt Kérdések

### Hogyan telepíthetem az Aspose.Words for Java-t?
Az Aspose.Words for Java letölthető innen: [here](https://releases.aspose.com/words/java/). Kövesd a letöltési oldal telepítési útmutatóját, hogy a JAR fájlokat a projekted osztályútvonalához add.

### Betölthetek összetett HTML dokumentumokat az Aspose.Words segítségével?
Igen, az Aspose.Words for Java képes kezelni összetett HTML-t, beleértve a beágyazott táblázatokat, CSS stílusokat és a JavaScript‑mentes interaktív elemeket. Állítsd be a `HtmlLoadOptions`-t (pl. `setLoadImages` vagy `setCssStyleSheetFileName`) a import finomhangolásához.

### Milyen egyéb dokumentumformátumokat támogat az Aspose.Words?
Az Aspose.Words támogatja a DOC, DOCX, RTF, HTML, PDF, EPUB, XPS és még sok más formátumot. Az API egyetlen soros mentést tesz lehetővé bármelyik formátumba.

### Az Aspose.Words alkalmas vállalati szintű dokumentumautomatizálásra?
Teljesen. Nagy vállalatok használják automatizált jelentéskészítésre, tömeges dokumentumkonverzióra és szerver‑oldali dokumentumfeldolgozásra a Microsoft Office függőségei nélkül.

### Hol találok további dokumentációt és példákat az Aspose.Words for Java-hoz?
A teljes API referencia és további oktatóanyagok megtalálhatók az Aspose.Words for Java dokumentációs oldalon: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Last Updated:** 2025-12-20  
**Tesztelve:** Aspose.Words for Java 24.12 (legújabb a írás időpontjában)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
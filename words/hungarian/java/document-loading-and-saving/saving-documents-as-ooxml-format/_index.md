---
date: 2026-01-09
description: Ismerje meg, hogyan lehet jelszóval titkosítani a docx fájlokat, és módosítani
  a tömörítési szintet a dokumentumok OOXML formátumban történő mentésekor az Aspose.Words
  for Java használatával.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: DOCX titkosítása jelszóval – OOXML mentés Aspose.Words Java-val
url: /hu/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# DOCX titkosítása jelszóval – OOXML mentés Aspose.Words Java-val

## Bevezetés a dokumentumok OOXML formátumban mentésébe az Aspose.Words for Java segítségével

Ebben az útmutatóban megtanulja, hogyan **encrypt docx with password** és hogyan mentse a dokumentumokat OOXML formátumban az Aspose.Words for Java használatával. Az OOXML (Office Open XML) a modern fájlformátum, amelyet a Microsoft Word és számos más irodai alkalmazás használ. Áttekintjük a leggyakoribb beállításokat – jelszóvédelem, megfelelőségi szintek, tulajdonságfrissítések, örökölt vezérlőkarakterek kezelése és **hogyan változtassuk meg a tömörítési szintet** – hogy a kimenetet pontosan az igényeihez igazíthassa.

## Gyors válaszok
- **Hogyan védhetek le egy Word fájlt?** Használja az `OoxmlSaveOptions.setPassword("yourPassword")` metódust a mentés előtt.  
- **Melyik OOXML megfelelőségi szintet válasszam?** ISO 29500 2008 Strict a legnagyobb kompatibilitásért a modern Office verziókkal.  
- **Megőrizhetem az örökölt vezérlőkaraktereket?** Igen, engedélyezze a `setKeepLegacyControlChars(true)` beállítást.  
- **Hogyan változtassam meg a tömörítési szintet?** Állítsa be a `setCompressionLevel(CompressionLevel.SUPER_FAST)` vagy `MAXIMUM` értéket a kívánt módon.  
- **Ezek a beállítások befolyásolják a fájlméretet?** A tömörítési szint és az örökölt karakterek kezelése jelentősen változtathatja a végső .docx méretét.

## Mi az a „encrypt docx with password”?
A DOCX fájl titkosítása azt jelenti, hogy a dokumentum AES‑256 titkosítással kerül mentésre, és jelszó szükséges a megnyitásához Wordben vagy bármely kompatibilis megjelenítőben. Ez elengedhetetlen a bizalmas információk védelméhez, amikor a fájlokat e‑mailen, felhőalapú tárolón vagy intranet portálon keresztül osztják meg.

## Miért használjunk OOXML mentési beállításokat?
- **Biztonság:** A jelszóvédelem megakadályozza az illetéktelen hozzáférést.  
- **Kompatibilitás:** A megfelelőségi beállítások biztosítják, hogy a fájl különböző Word verziókban is működjön.  
- **Teljesítmény:** A tömörítés módosítása felgyorsíthatja a mentést vagy csökkentheti a fájlméretet.  
- **Megőrzés:** Az örökölt vezérlőkarakterek megtartása hűséges átalakítást biztosít régebbi dokumentumok esetén.

## Előkövetelmények
- Aspose.Words for Java könyvtár hozzáadva a projekthez (Maven/Gradle vagy manuális JAR).  
- Java 8 vagy újabb.  
- Egy forrásdokumentum (`.docx` vagy `.doc`), amelyet feldolgozni szeretne.

## Dokumentum mentése jelszóval titkosítva

Titkosíthatja a dokumentumot jelszóval, miközben OOXML formátumban menti. Így teheti:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Pro tipp:** Válasszon erős jelszót, és tárolja biztonságosan; a jelszó nem állítható helyreállításra a titkosított fájlból.

## OOXML megfelelőség beállítása

Megadhatja az OOXML megfelelőségi szintet a dokumentum mentésekor. Például beállíthatja ISO 29500:2008 (Strict) szintre. Így:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## „Last Saved Time” tulajdonság frissítése

A mentéskor kiválaszthatja a dokumentum „Last Saved Time” (Utolsó mentés időpontja) tulajdonságának frissítését. Így:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Örökölt vezérlőkarakterek megtartása

Ha a dokumentuma tartalmaz örökölt vezérlőkaraktereket, megőrizheti őket a mentés során. Így:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Tömörítési szint módosítása OOXML mentéskor

A mentéskor módosíthatja a tömörítési szintet. Például beállíthatja a `SUPER_FAST` értéket minimális tömörítéshez vagy a `MAXIMUM` értéket a legkisebb fájlmérethez. Így:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Ezek a legfontosabb opciók és beállítások, amelyeket az OOXML formátumban történő dokumentummentéshez használhat az Aspose.Words for Java segítségével. Fedezze fel a további lehetőségeket, és testreszabhatja a dokumentum‑mentési folyamatot igényei szerint.

## Teljes forráskód OOXML formátumban történő dokumentummentéshez Aspose.Words for Java-val

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Összegzés

Ebben az átfogó útmutatóban bemutattuk, hogyan **encrypt docx with password** és hogyan menthet dokumentumokat OOXML formátumban az Aspose.Words for Java segítségével. Akár a fájlok védelméről, a szigorú OOXML megfelelőség biztosításáról, a dokumentumtulajdonságok frissítéséről, az örökölt vezérlőkarakterek megőrzéséről vagy a **tömörítési szint módosításáról** van szó, az Aspose.Words sokoldalú eszközkészletet kínál a követelmények teljesítéséhez.

## Gyakran Ismételt Kérdések

**Q: Hogyan távolíthatom el a jelszóvédelmet egy jelszóval védett dokumentumból?**  
A: Nyissa meg a dokumentumot a helyes jelszóval, majd mentse el jelszó megadása nélkül az `OoxmlSaveOptions` használata nélkül. Így egy védettség nélküli másolat jön létre.

**Q: Beállíthatok egyéni tulajdonságokat OOXML formátumban történő mentéskor?**  
Igen. Használja a `BuiltInDocumentProperties` és `CustomDocumentProperties` objektumokat a `Document` példányon, mielőtt meghívná a `save()` metódust.

**Q: Mi a alapértelmezett tömörítési szint OOXML formátumban történő mentéskor?**  
Az alapértelmezett a `CompressionLevel.NORMAL`. A `SUPER_FAST` gyorsabb mentést, a `MAXIMUM` pedig a legkisebb fájlméretet eredményezi.

**Q: A `keepLegacyControlChars` engedélyezése befolyásolja a modern Word verziókkal való kompatibilitást?**  
A modern Word meg tud nyitni az örökölt vezérlőkaraktereket tartalmazó fájlokat, de egyes régi funkciók másként jelenhetnek meg. Ezt a beállítást csak akkor használja, ha a pontos eredeti tartalom megőrzése szükséges.

**Q: Lehet-e több mentési opciót (pl. jelszó + tömörítés) egyetlen hívásban kombinálni?**  
Természetesen. Állítsa be a kívánt összes tulajdonságot egyetlen `OoxmlSaveOptions` példányon, majd adja át a `doc.save()` metódusnak.

---

**Utoljára frissítve:** 2026-01-09  
**Tesztelve:** Aspose.Words for Java 24.12  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
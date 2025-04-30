---
"description": "Tanuld meg, hogyan menthetsz dokumentumokat OOXML formátumban az Aspose.Words for Java segítségével. Biztosítsd, optimalizáld és szabd testre fájljaidat könnyedén."
"linktitle": "Dokumentumok mentése OOXML formátumban"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok mentése OOXML formátumban az Aspose.Words for Java programban"
"url": "/hu/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok mentése OOXML formátumban az Aspose.Words for Java programban


## Bevezetés a dokumentumok OOXML formátumban történő mentéséhez az Aspose.Words for Java programban

Ebben az útmutatóban azt vizsgáljuk meg, hogyan menthetünk dokumentumokat OOXML formátumban az Aspose.Words for Java segítségével. Az OOXML (Office Open XML) egy fájlformátum, amelyet a Microsoft Word és más irodai alkalmazások használnak. Áttekintjük a dokumentumok OOXML formátumban történő mentésének különböző lehetőségeit és beállításait.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg róla, hogy az Aspose.Words for Java könyvtár be van állítva a projektedben.

## Dokumentum mentése jelszóval titkosítva

A dokumentumot jelszóval titkosíthatja, miközben OOXML formátumban menti. Így teheti meg:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Töltse be a dokumentumot
Document doc = new Document("Document.docx");

// Hozz létre OoxmlSaveOptions-t és állítsd be a jelszót
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Mentse el a dokumentumot titkosítással
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXML-megfelelőség beállítása

A dokumentum mentésekor megadhatja az OOXML megfelelőségi szintet. Beállíthatja például az ISO 29500:2008 (Szigorú) szabványt. Így teheti meg:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Töltse be a dokumentumot
Document doc = new Document("Document.docx");

// Optimalizálás a Word 2016-hoz
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Hozz létre OoxmlSaveOptions beállításokat és állítsd be a megfelelőségi szintet
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Dokumentum mentése megfelelőségi beállításokkal
doc.save("ComplianceDoc.docx", saveOptions);
```

## Utolsó mentés időpontja tulajdonság frissítése

A dokumentum mentésekor frissítheti a „Utolsó mentés időpontja” tulajdonságot. Így teheti meg:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Töltse be a dokumentumot
Document doc = new Document("Document.docx");

// Hozz létre OoxmlSaveOptions objektumokat, és engedélyezd a Legutóbbi mentés időpontja tulajdonság frissítését
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Mentse el a dokumentumot a frissített tulajdonsággal
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## A Legacy vezérlőkarakterek megtartása

Ha a dokumentum régebbi vezérlőkaraktereket tartalmaz, akkor mentéskor megtarthatja azokat. Így teheti meg:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Dokumentum betöltése korábbi vezérlőkarakterekkel
Document doc = new Document("LegacyControlChars.doc");

// Hozz létre OoxmlSaveOptions objektumokat FLAT_OPC formátumban, és engedélyezd a korábbi vezérlőkarakterek megtartását.
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Dokumentum mentése korábbi vezérlőkarakterekkel
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Tömörítési szint beállítása

A dokumentum mentése során módosíthatja a tömörítési szintet. Például beállíthatja SUPER_FAST értékre a minimális tömörítéshez. Így teheti meg:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Töltse be a dokumentumot
Document doc = new Document("Document.docx");

// Hozz létre OoxmlSaveOptions-t és állítsd be a tömörítési szintet
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Mentse el a dokumentumot a megadott tömörítési szinttel
doc.save("FastCompressionDoc.docx", saveOptions);
```

Íme néhány kulcsfontosságú opció és beállítás, amelyet az Aspose.Words for Java használatával OOXML formátumban történő dokumentumok mentésekor használhat. Nyugodtan fedezzen fel további lehetőségeket, és szükség szerint szabja testre a dokumentummentési folyamatot.

## Teljes forráskód dokumentumok OOXML formátumban történő mentéséhez Aspose.Words for Java-ban

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

## Következtetés

Ebben az átfogó útmutatóban azt vizsgáltuk meg, hogyan menthetünk dokumentumokat OOXML formátumban az Aspose.Words for Java segítségével. Akár jelszavakkal kell titkosítania dokumentumait, akár biztosítania kell a megfelelőséget bizonyos OOXML szabványoknak, frissítenie kell a dokumentum tulajdonságait, meg kell őriznie a régi vezérlőkaraktereket, vagy módosítania kell a tömörítési szinteket, az Aspose.Words sokoldalú eszközkészletet kínál az Ön igényeinek kielégítésére.

## GYIK

### Hogyan távolíthatom el a jelszóvédelmet egy jelszóval védett dokumentumról?

Jelszóval védett dokumentum jelszavas védelmének eltávolításához nyissa meg a dokumentumot a megfelelő jelszóval, majd mentse el jelszó megadása nélkül a mentési beállításokban. Ez jelszóvédelem nélkül menti a dokumentumot.

### Beállíthatok egyéni tulajdonságokat egy dokumentum OOXML formátumban történő mentésekor?

Igen, beállíthat egyéni tulajdonságokat egy dokumentumhoz, mielőtt OOXML formátumban mentené. Használja a `BuiltInDocumentProperties` és `CustomDocumentProperties` osztályok különféle tulajdonságok, például szerző, cím, kulcsszavak és egyéni tulajdonságok beállításához.

### Mi az alapértelmezett tömörítési szint OOXML formátumú dokumentum mentésekor?

Az alapértelmezett tömörítési szint OOXML formátumú dokumentum mentésekor az Aspose.Words for Java használatával: `NORMAL`A tömörítési szintet a következőre módosíthatja: `SUPER_FAST` vagy `MAXIMUM` szükség szerint.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
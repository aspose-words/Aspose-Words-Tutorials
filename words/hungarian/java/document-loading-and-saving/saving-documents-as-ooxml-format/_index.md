---
title: Dokumentumok mentése OOXML formátumban az Aspose.Words for Java programban
linktitle: Dokumentumok mentése OOXML formátumban
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan menthet dokumentumokat OOXML formátumban az Aspose.Words for Java segítségével. Könnyedén biztonságossá teheti, optimalizálhatja és testreszabhatja fájljait.
weight: 20
url: /hu/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok mentése OOXML formátumban az Aspose.Words for Java programban


## Bevezetés a dokumentumok OOXML formátumban történő mentésébe az Aspose.Words for Java programban

Ebben az útmutatóban megvizsgáljuk, hogyan lehet dokumentumokat menteni OOXML formátumban az Aspose.Words for Java használatával. Az OOXML (Office Open XML) a Microsoft Word és más irodai alkalmazások által használt fájlformátum. Leírjuk a dokumentumok OOXML formátumban történő mentésének különféle lehetőségeit és beállításait.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a projektben be van állítva az Aspose.Words for Java könyvtár.

## Dokumentum mentése jelszavas titkosítással

dokumentumot jelszóval titkosíthatja, miközben OOXML formátumban menti. A következőképpen teheti meg:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Töltse be a dokumentumot
Document doc = new Document("Document.docx");

// Hozzon létre OoxmlSaveOptions-t, és állítsa be a jelszót
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Mentse el a dokumentumot titkosítással
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXML-kompatibilitás beállítása

A dokumentum mentésekor megadhatja az OOXML megfelelőségi szintet. Például beállíthatja ISO 29500:2008 (szigorú) értékre. Íme, hogyan:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Töltse be a dokumentumot
Document doc = new Document("Document.docx");

// Optimalizálás Word 2016-ra
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Hozzon létre OoxmlSaveOptions-t, és állítsa be a megfelelőségi szintet
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Mentse el a dokumentumot megfelelőségi beállítással
doc.save("ComplianceDoc.docx", saveOptions);
```

## Utolsó megtakarított idő tulajdonság frissítése

Mentéskor választhatja a dokumentum "Utolsó mentett idő" tulajdonságának frissítését. Íme, hogyan:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Töltse be a dokumentumot
Document doc = new Document("Document.docx");

// Hozzon létre OoxmlSaveOptions-t, és engedélyezze a Last Saved Time tulajdonság frissítését
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Mentse el a dokumentumot a frissített tulajdonsággal
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Az örökölt vezérlőkarakterek megtartása

Ha a dokumentum örökölt vezérlőkaraktereket tartalmaz, dönthet úgy, hogy megtartja őket a mentés során. Íme, hogyan:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Töltsön be egy régi vezérlőkaraktereket tartalmazó dokumentumot
Document doc = new Document("LegacyControlChars.doc");

// Hozzon létre OoxmlSaveOptions-t a FLAT_OPC formátummal, és engedélyezze a régi vezérlőkarakterek megtartását
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Mentse el a dokumentumot örökölt vezérlőkarakterekkel
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## A tömörítési szint beállítása

A tömörítési szintet a dokumentum mentésekor állíthatja be. Beállíthatja például SUPER_FAST értékre a minimális tömörítés érdekében. Íme, hogyan:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Töltse be a dokumentumot
Document doc = new Document("Document.docx");

// Hozzon létre OoxmlSaveOptions-t, és állítsa be a tömörítési szintet
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Mentse el a dokumentumot a megadott tömörítési szinttel
doc.save("FastCompressionDoc.docx", saveOptions);
```

Íme néhány kulcsfontosságú opció és beállítás, amelyet akkor használhat, ha dokumentumokat ment el OOXML formátumban az Aspose.Words for Java használatával. Nyugodtan fedezhet fel további lehetőségeket, és szükség szerint testreszabhatja dokumentummentési folyamatát.

## Teljes forráskód a dokumentumok OOXML formátumban történő mentéséhez az Aspose.Words for Java programban

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

Ebben az átfogó útmutatóban megvizsgáltuk, hogyan lehet dokumentumokat menteni OOXML formátumban az Aspose.Words for Java használatával. Függetlenül attól, hogy jelszavakkal kell titkosítania dokumentumait, biztosítania kell az egyes OOXML-szabványoknak való megfelelést, frissítenie kell a dokumentum tulajdonságait, meg kell őriznie az örökölt vezérlőkaraktereket, vagy módosítania kell a tömörítési szinteket, az Aspose.Words sokoldalú eszközkészletet kínál az Ön igényeinek kielégítésére.

## GYIK

### Hogyan távolíthatom el a jelszavas védelmet egy jelszóval védett dokumentumról?

A jelszóval védett dokumentum jelszavas védelmének eltávolításához megnyithatja a dokumentumot a megfelelő jelszóval, majd elmentheti anélkül, hogy jelszót adna meg a mentési beállításokban. Ezzel jelszavas védelem nélkül menti el a dokumentumot.

### Beállíthatok egyéni tulajdonságokat egy dokumentum OOXML formátumban való mentésekor?

 Igen, beállíthat egyéni tulajdonságokat egy dokumentumhoz, mielőtt OOXML formátumba menti. Használja a`BuiltInDocumentProperties` és`CustomDocumentProperties` osztályok különböző tulajdonságok, például szerző, cím, kulcsszavak és egyéni tulajdonságok beállításához.

### Mi az alapértelmezett tömörítési szint egy dokumentum OOXML formátumban történő mentésekor?

 A dokumentum Aspose.Words for Java használatával OOXML formátumba mentésekor az alapértelmezett tömörítési szint`NORMAL` . A tömörítési szintet erre módosíthatja`SUPER_FAST` vagy`MAXIMUM` szükség szerint.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---
date: 2025-12-29
description: Ismerje meg, hogyan titkosíthatja a docx fájlokat jelszóval az Aspose.Words
  for Java mentési beállításai segítségével. Biztonságosan, optimalizáltan és könnyedén
  testreszabhatja OOXML fájljait.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Hogyan titkosítsuk a DOCX-et jelszóval az Aspose.Words for Java használatával
url: /hu/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan titkosítsuk a DOCX fájlt jelszóval az Aspose.Words for Java segítségével

Ebben az útmutatóban megtudja, **hogyan titkosítsa a docx fájlt jelszóval**, miközben OOXML formátumban menti a dokumentumokat az Aspose.Words for Java használatával. Akár bizalmas jelentéseket szeretne védeni, akár szerződésvázlatokat biztosítani, az alábbi lépések pontosan megmutatják, hogyan alkalmazzon jelszóvédelmet, és hogyan finomhangolja a többi OOXML mentési beállítást.

## Gyors válaszok
- **Titkosíthatok-e egy DOCX fájlt jelszóval?** Igen, használd az `OoxmlSaveOptions.setPassword()` metódust a mentés előtt.  
- **Melyik osztály vezérli az OOXML mentési beállításokat?** `OoxmlSaveOptions` (az Aspose.Words része).  
- **Szükség van licencre a jelszóvédelemhez?** Érvényes Aspose.Words licenc szükséges a termelési környezetben.  
- **Kombinálhatom a titkosítást megfelelőségi beállításokkal?** Természetesen – állítsd be egyszerre a `setPassword` és a `setCompliance` metódusokat ugyanazon `OoxmlSaveOptions` példányon.  
- **Milyen tömörítési szintek érhetők el?** `NORMAL`, `SUPER_FAST` és `MAXIMUM` a `CompressionLevel` segítségével.

## Mi az a „encrypt docx with password”?
A DOCX fájl titkosítása azt jelenti, hogy a fájl tartalma titkosított formában van tárolva, és csak a helyes jelszó megadása után nyitható meg. Ez megvédi az érzékeny információkat a jogosulatlan hozzáféréstől, miközben a szokásos Word-eszközök továbbra is megnyithatják a fájlt, ha a jelszó meg van adva.

## Miért használjuk az Aspose.Words mentési beállításait a titkosításhoz?
Az Aspose.Words gazdag **aspose words save options** készletet kínál, amely lehetővé teszi nem csak a titkosítás, hanem a megfelelőségi szintek, a tömörítés és a régi karakterek kezelésének szabályozását is – mind Java kódból. Ez kiküszöböli a manuális utófeldolgozást vagy harmadik féltől származó eszközök használatát.

## Előfeltételek
- Java Development Kit (JDK 8 vagy újabb)  
- Aspose.Words for Java könyvtár hozzáadva a projekthez (Maven/Gradle vagy JAR)  
- Érvényes Aspose.Words licenc a termelési környezethez (opcionális értékeléshez)

## Dokumentum mentése jelszóval titkosítva

A dokumentumot titkosíthatja jelszóval, miközben OOXML formátumban menti. Íme, hogyan:

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

## OOXML megfelelőség beállítása

Megadhatja az OOXML megfelelőségi szintet a dokumentum mentésekor. Például beállíthatja ISO 29500:2008 (Strict) szintre. Így teheti:

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

A mentéskor kiválaszthatja, hogy frissítse-e a dokumentum „Last Saved Time” (Utolsó mentés időpontja) tulajdonságát. Így teheti:

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

## Régi vezérlőkarakterek megtartása

Ha a dokumentuma régi vezérlőkaraktereket tartalmaz, a mentéskor megtarthatja ezeket. Így teheti:

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

## Tömörítési szint beállítása

A dokumentum mentésekor beállíthatja a tömörítési szintet. Például beállíthatja **SUPER_FAST**-ra a minimális tömörítés érdekében. Így teheti:

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

Ezek a főbb opciók és beállítások, amelyeket az OOXML formátumban történő dokumentummentéskor használhat az Aspose.Words for Java segítségével. Fedezze fel a további lehetőségeket, és testreszabhatja a dokumentum mentési folyamatát igényei szerint.

## Teljes forráskód OOXML formátumban történő dokumentummentéshez Aspose.Words for Java használatával

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

Ebben az átfogó útmutatóban megvizsgáltuk, hogyan **encrypt docx with password**, és hogyan finomhangolhatjuk az OOXML mentési opciók széles skáláját az Aspose.Words for Java segítségével. Akár bizalmas tartalmat kell védenie, szigorú ISO megfelelőséget elérnie, régi karaktereket megőriznie, vagy a tömörítést szabályoznia, a könyvtár granuláris vezérlést biztosít ugyanazon `OoxmlSaveOptions` API-n keresztül.

## Gyakran ismételt kérdések

**Q: Hogyan távolíthatom el a jelszóvédelmet egy jelszóval védett dokumentumból?**  
A: Nyissa meg a dokumentumot a helyes jelszóval, majd mentse újra anélkül, hogy meghívná a `setPassword` metódust. Az új fájl már nem lesz védett.

**Q: Beállíthatok-e egyéni tulajdonságokat OOXML formátumban történő mentéskor?**  
A: Igen. Használja a `BuiltInDocumentProperties` vagy a `CustomDocumentProperties` osztályokat a `Document` objektumon, mielőtt meghívná a `save` metódust.

**Q: Mi a alapértelmezett tömörítési szint OOXML formátumban történő mentéskor?**  
A: Az alapértelmezett `NORMAL`. Átállíthatja `SUPER_FAST`-ra a sebességért vagy `MAXIMUM`-ra a kisebb fájlméretért.

**Q: Működnek-e az aspose words save options régebbi Word verziókkal?**  
A: Igen. A `MsWordVersion` és a megfelelőségi beállítások módosításával célozhatja a Word 2007‑2019 verziókat, és biztosíthatja a kompatibilitást.

**Q: Lehetséges-e több mentési opció egyidejű kombinálása?**  
A: Teljesen. Hozzon létre egy `OoxmlSaveOptions` példányt, állítsa be az összes kívánt tulajdonságot (jelszó, megfelelőség, tömörítés stb.), és adja át a `doc.save()` metódusnak.

---

**Last Updated:** 2025-12-29  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
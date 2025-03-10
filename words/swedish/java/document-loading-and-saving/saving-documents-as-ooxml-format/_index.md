---
title: Spara dokument som OOXML-format i Aspose.Words för Java
linktitle: Spara dokument som OOXML-format
second_title: Aspose.Words Java Document Processing API
description: Lär dig hur du sparar dokument i OOXML-format med Aspose.Words för Java. Säkra, optimera och anpassa dina filer utan ansträngning.
weight: 20
url: /sv/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som OOXML-format i Aspose.Words för Java


## Introduktion till att spara dokument som OOXML-format i Aspose.Words för Java

I den här guiden kommer vi att utforska hur man sparar dokument i OOXML-format med Aspose.Words för Java. OOXML (Office Open XML) är ett filformat som används av Microsoft Word och andra kontorsprogram. Vi tar upp olika alternativ och inställningar för att spara dokument i OOXML-format.

## Förutsättningar

Innan vi börjar, se till att du har Aspose.Words för Java-biblioteket inställt i ditt projekt.

## Spara ett dokument med lösenordskryptering

Du kan kryptera ditt dokument med ett lösenord samtidigt som du sparar det i OOXML-format. Så här kan du göra det:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Ladda dokumentet
Document doc = new Document("Document.docx");

// Skapa OoxmlSaveOptions och ställ in lösenordet
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Spara dokumentet med kryptering
doc.save("EncryptedDoc.docx", saveOptions);
```

## Ställa in OOXML-efterlevnad

Du kan ange OOXML-efterlevnadsnivån när du sparar dokumentet. Du kan till exempel ställa in den på ISO 29500:2008 (Strikt). Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Ladda dokumentet
Document doc = new Document("Document.docx");

// Optimera för Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Skapa OoxmlSaveOptions och ställ in efterlevnadsnivån
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Spara dokumentet med efterlevnadsinställning
doc.save("ComplianceDoc.docx", saveOptions);
```

## Uppdaterar egenskapen Senaste sparad tid

Du kan välja att uppdatera egenskapen "Senast sparad tid" för dokumentet när du sparar det. Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Ladda dokumentet
Document doc = new Document("Document.docx");

// Skapa OoxmlSaveOptions och aktivera uppdatering av egenskapen Last Saved Time
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Spara dokumentet med den uppdaterade egenskapen
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Behåller äldre kontrollkaraktärer

Om ditt dokument innehåller äldre kontrolltecken kan du välja att behålla dem medan du sparar. Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Ladda ett dokument med äldre kontrolltecken
Document doc = new Document("LegacyControlChars.doc");

// Skapa OoxmlSaveOptions med formatet FLAT_OPC och gör det möjligt att behålla äldre kontrolltecken
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Spara dokumentet med äldre kontrolltecken
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Ställa in kompressionsnivå

Du kan justera komprimeringsnivån när du sparar dokumentet. Du kan till exempel ställa in den på SUPER_FAST för minimal komprimering. Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Ladda dokumentet
Document doc = new Document("Document.docx");

// Skapa OoxmlSaveOptions och ställ in komprimeringsnivån
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Spara dokumentet med den angivna komprimeringsnivån
doc.save("FastCompressionDoc.docx", saveOptions);
```

Det här är några av de viktigaste alternativen och inställningarna du kan använda när du sparar dokument i OOXML-format med Aspose.Words för Java. Utforska gärna fler alternativ och anpassa din process för att spara dokument efter behov.

## Komplett källkod för att spara dokument som OOXML-format i Aspose.Words för Java

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

## Slutsats

den här omfattande guiden har vi utforskat hur man sparar dokument i OOXML-format med Aspose.Words för Java. Oavsett om du behöver kryptera dina dokument med lösenord, säkerställa överensstämmelse med specifika OOXML-standarder, uppdatera dokumentegenskaper, bevara äldre kontrolltecken eller justera komprimeringsnivåer, tillhandahåller Aspose.Words en mångsidig uppsättning verktyg för att möta dina krav.

## FAQ's

### Hur tar jag bort lösenordsskyddet från ett lösenordsskyddat dokument?

För att ta bort lösenordsskyddet från ett lösenordsskyddat dokument kan du öppna dokumentet med rätt lösenord och sedan spara det utan att ange ett lösenord i sparalternativen. Detta kommer att spara dokumentet utan lösenordsskydd.

### Kan jag ställa in anpassade egenskaper när jag sparar ett dokument i OOXML-format?

 Ja, du kan ställa in anpassade egenskaper för ett dokument innan du sparar det i OOXML-format. Använd`BuiltInDocumentProperties` och`CustomDocumentProperties` klasser för att ställa in olika egenskaper som författare, titel, nyckelord och anpassade egenskaper.

### Vilken är standardkomprimeringsnivån när du sparar ett dokument i OOXML-format?

 Standardkomprimeringsnivån när du sparar ett dokument i OOXML-format med Aspose.Words för Java är`NORMAL` . Du kan ändra komprimeringsnivån till`SUPER_FAST` eller`MAXIMUM` efter behov.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

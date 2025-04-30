---
"description": "Lär dig hur du sparar dokument i OOXML-format med Aspose.Words för Java. Säkra, optimera och anpassa dina filer utan ansträngning."
"linktitle": "Spara dokument som OOXML-format"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Spara dokument som OOXML-format i Aspose.Words för Java"
"url": "/sv/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som OOXML-format i Aspose.Words för Java


## Introduktion till att spara dokument som OOXML-format i Aspose.Words för Java

den här guiden ska vi utforska hur man sparar dokument i OOXML-format med hjälp av Aspose.Words för Java. OOXML (Office Open XML) är ett filformat som används av Microsoft Word och andra Office-program. Vi kommer att gå igenom olika alternativ och inställningar för att spara dokument i OOXML-format.

## Förkunskapskrav

Innan vi börjar, se till att du har Aspose.Words för Java-biblioteket konfigurerat i ditt projekt.

## Spara ett dokument med lösenordskryptering

Du kan kryptera ditt dokument med ett lösenord medan du sparar det i OOXML-format. Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Ladda dokumentet
Document doc = new Document("Document.docx");

// Skapa OoxmlSaveOptions och ange lösenordet
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Spara dokumentet med kryptering
doc.save("EncryptedDoc.docx", saveOptions);
```

## Ställa in OOXML-efterlevnad

Du kan ange OOXML-efterlevnadsnivån när du sparar dokumentet. Du kan till exempel ställa in den på ISO 29500:2008 (strikt). Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Ladda dokumentet
Document doc = new Document("Document.docx");

// Optimera för Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Skapa OoxmlSaveOptions och ange efterlevnadsnivån
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Spara dokumentet med efterlevnadsinställningen
doc.save("ComplianceDoc.docx", saveOptions);
```

## Uppdaterar egenskapen för senast sparade tid

Du kan välja att uppdatera egenskapen "Senast sparad tid" för dokumentet när du sparar det. Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Ladda dokumentet
Document doc = new Document("Document.docx");

// Skapa OoxmlSaveOptions och aktivera uppdatering av egenskapen Senaste sparade tid
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Spara dokumentet med den uppdaterade egenskapen
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Behålla äldre kontrollkaraktärer

Om ditt dokument innehåller äldre kontrolltecken kan du välja att behålla dem medan du sparar. Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Läs in ett dokument med äldre kontrolltecken
Document doc = new Document("LegacyControlChars.doc");

// Skapa OoxmlSaveOptions med FLAT_OPC-formatet och aktivera bevarande av äldre kontrolltecken
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Spara dokumentet med äldre kontrolltecken
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Inställning av komprimeringsnivå

Du kan justera komprimeringsnivån när du sparar dokumentet. Du kan till exempel ställa in den på SUPER_FAST för minimal komprimering. Så här gör du:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Ladda dokumentet
Document doc = new Document("Document.docx");

// Skapa OoxmlSaveOptions och ange komprimeringsnivån
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Spara dokumentet med den angivna komprimeringsnivån
doc.save("FastCompressionDoc.docx", saveOptions);
```

Det här är några av de viktigaste alternativen och inställningarna du kan använda när du sparar dokument i OOXML-format med Aspose.Words för Java. Utforska gärna fler alternativ och anpassa din dokumentsparningsprocess efter behov.

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

I den här omfattande guiden har vi utforskat hur man sparar dokument i OOXML-format med hjälp av Aspose.Words för Java. Oavsett om du behöver kryptera dina dokument med lösenord, säkerställa att specifika OOXML-standarder följs, uppdatera dokumentegenskaper, bevara äldre kontrolltecken eller justera komprimeringsnivåer, erbjuder Aspose.Words en mångsidig uppsättning verktyg för att möta dina behov.

## Vanliga frågor

### Hur tar jag bort lösenordsskyddet från ett lösenordsskyddat dokument?

För att ta bort lösenordsskyddet från ett lösenordsskyddat dokument kan du öppna dokumentet med rätt lösenord och sedan spara det utan att ange ett lösenord i sparalternativen. Detta sparar dokumentet utan lösenordsskydd.

### Kan jag ange anpassade egenskaper när jag sparar ett dokument i OOXML-format?

Ja, du kan ange anpassade egenskaper för ett dokument innan du sparar det i OOXML-format. Använd `BuiltInDocumentProperties` och `CustomDocumentProperties` klasser för att ange olika egenskaper som författare, titel, nyckelord och anpassade egenskaper.

### Vilken är standardkomprimeringsnivån när man sparar ett dokument i OOXML-format?

Standardkomprimeringsnivån när man sparar ett dokument i OOXML-format med Aspose.Words för Java är `NORMAL`Du kan ändra komprimeringsnivån till `SUPER_FAST` eller `MAXIMUM` efter behov.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
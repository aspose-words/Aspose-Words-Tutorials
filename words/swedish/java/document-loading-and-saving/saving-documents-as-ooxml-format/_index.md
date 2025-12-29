---
date: 2025-12-29
description: Lär dig hur du krypterar docx med lösenord med hjälp av Aspose.Words
  för Java sparalternativ. Säkerställ, optimera och anpassa dina OOXML‑filer utan
  ansträngning.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Hur man krypterar DOCX med lösenord med Aspose.Words för Java
url: /sv/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Så krypterar du DOCX med lösenord med Aspose.Words för Java

I den här guiden får du reda på **hur du krypterar docx med lösenord** när du sparar dokument i OOXML‑format med Aspose.Words för Java. Oavsett om du skyddar konfidentiella rapporter eller säkrar kontraktsutkast visar stegen nedan exakt hur du tillämpar lösenordsskydd och finjusterar andra OOXML‑sparalternativ.

## Snabba svar
- **Kan jag kryptera en DOCX-fil med ett lösenord?** Ja, använd `OoxmlSaveOptions.setPassword()` innan du sparar.  
- **Vilken klass styr OOXML‑sparinställningarna?** `OoxmlSaveOptions` (del av Aspose.Words).  
- **Behöver jag en licens för lösenordsskydd?** En giltig Aspose.Words‑licens krävs för produktionsanvändning.  
- **Kan jag kombinera kryptering med efterlevnadsinställningar?** Absolut – sätt både `setPassword` och `setCompliance` på samma `OoxmlSaveOptions`‑instans.  
- **Vilka komprimeringsnivåer finns tillgängliga?** `NORMAL`, `SUPER_FAST` och `MAXIMUM` via `CompressionLevel`.

## Vad betyder “encrypt docx with password”?
Att kryptera en DOCX‑fil innebär att filens innehåll lagras i krypterad form och bara kan öppnas efter att rätt lösenord har angetts. Detta skyddar känslig information från obehörig åtkomst samtidigt som standard‑Word‑verktyg kan öppna filen när lösenordet har angetts.

## Varför använda Aspose.Words sparalternativ för kryptering?
Aspose.Words erbjuder ett rikt urval av **aspose words save options** som låter dig kontrollera inte bara kryptering utan även efterlevnadsnivåer, komprimering och hantering av äldre tecken – allt från Java‑kod. Detta eliminerar behovet av manuell efterbehandling eller tredjepartsverktyg.

## Förutsättningar
- Java Development Kit (JDK 8 eller högre)  
- Aspose.Words för Java‑biblioteket tillagt i ditt projekt (Maven/Gradle eller JAR)  
- En giltig Aspose.Words‑licens för produktion (valfritt för utvärdering)

## Spara ett dokument med lösenordskryptering

Du kan kryptera ditt dokument med ett lösenord när du sparar det i OOXML‑format. Så här gör du:

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

## Ställa in OOXML‑efterlevnad

Du kan ange OOXML‑efterlevnadsnivå när du sparar dokumentet. Till exempel kan du sätta den till ISO 29500:2008 (Strict). Så här:

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

## Uppdatera egenskapen Senast sparad tid

Du kan välja att uppdatera egenskapen “Last Saved Time” i dokumentet när du sparar det. Så här:

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

## Behålla äldre kontrolltecken

Om ditt dokument innehåller äldre kontrolltecken kan du välja att behålla dem vid sparning. Så här:

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

## Ställa in komprimeringsnivå

Du kan justera komprimeringsnivån när du sparar dokumentet. Till exempel kan du sätta den till **SUPER_FAST** för minimal komprimering. Så här:

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

Detta är några av de viktigaste alternativen och inställningarna du kan använda när du sparar dokument i OOXML‑format med Aspose.Words för Java. Känn dig fri att utforska fler alternativ och anpassa din dokument‑sparprocess efter behov.

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

I den här omfattande guiden har vi gått igenom hur du **encrypt docx with password** och finjusterat en rad OOXML‑sparalternativ med Aspose.Words för Java. Oavsett om du behöver skydda konfidentiellt innehåll, uppfylla strikt ISO‑efterlevnad, bevara äldre tecken eller styra komprimering, ger biblioteket dig detaljerad kontroll via samma `OoxmlSaveOptions`‑API.

## Vanliga frågor

**Q: Hur tar jag bort lösenordsskyddet från ett lösenordsskyddat dokument?**  
A: Öppna dokumentet med rätt lösenord och spara sedan igen utan att anropa `setPassword`. Den nya filen blir oskyddad.

**Q: Kan jag ange anpassade egenskaper när jag sparar ett dokument i OOXML‑format?**  
A: Ja. Använd `BuiltInDocumentProperties` eller `CustomDocumentProperties` på `Document`‑objektet innan du anropar `save`.

**Q: Vad är standardkomprimeringsnivån när jag sparar ett dokument i OOXML‑format?**  
A: Standard är `NORMAL`. Du kan byta till `SUPER_FAST` för hastighet eller `MAXIMUM` för mindre filstorlek.

**Q: Fungerar aspose words save options med äldre Word‑versioner?**  
A: Ja. Genom att justera `MsWordVersion` och efterlevnadsinställningar kan du rikta in dig på Word 2007‑2019 och säkerställa kompatibilitet.

**Q: Är det möjligt att kombinera flera sparalternativ i en enda operation?**  
A: Absolut. Skapa en `OoxmlSaveOptions`‑instans, sätt alla önskade egenskaper (lösenord, efterlevnad, komprimering osv.) och skicka den till `doc.save()`.

---

**Last Updated:** 2025-12-29  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
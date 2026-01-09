---
date: 2026-01-09
description: Lär dig hur du krypterar docx med lösenord och ändrar komprimeringsnivå
  när du sparar dokument i OOXML-format med Aspose.Words för Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Kryptera docx med lösenord – OOXML‑spara med Aspose.Words Java
url: /sv/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kryptera docx med lösenord – OOXML‑spara med Aspose.Words Java

## Introduktion till att spara dokument som OOXML‑format i Aspose.Words för Java

I den här guiden lär du dig hur du **krypterar docx med lösenord** och sparar dokument i OOXML‑format med Aspose.Words för Java. OOXML (Office Open XML) är det moderna filformatet som används av Microsoft Word och många andra kontorsprogram. Vi går igenom de vanligaste alternativen – lösenordsskydd, efterlevnadsnivåer, egenskapsuppdateringar, hantering av äldre kontrolltecken och **hur du ändrar komprimeringsnivå** – så att du kan anpassa resultatet exakt efter dina behov.

## Snabba svar
- **Hur kan jag skydda en Word‑fil?** Använd `OoxmlSaveOptions.setPassword("yourPassword")` innan du sparar.  
- **Vilken OOXML‑efterlevnadsnivå ska jag välja?** ISO 29500 2008 Strict för maximal kompatibilitet med moderna Office‑versioner.  
- **Kan jag behålla äldre kontrolltecken?** Ja, aktivera `setKeepLegacyControlChars(true)`.  
- **Hur ändrar jag komprimeringsnivån?** Sätt `setCompressionLevel(CompressionLevel.SUPER_FAST)` eller `MAXIMUM` efter behov.  
- **Påverkar dessa alternativ filstorleken?** Komprimeringsnivå och hantering av äldre kontrolltecken kan märkbart förändra den slutliga .docx‑storleken.

## Vad betyder “encrypt docx with password”?
Att kryptera en DOCX‑fil innebär att dokumentet sparas med AES‑256‑kryptering och kräver ett lösenord för att öppnas i Word eller någon kompatibel visare. Detta är viktigt för att skydda konfidentiell information när filer delas via e‑post, molnlagring eller intranätportaler.

## Varför använda OOXML‑sparalternativ?
- **Säkerhet:** Lösenordsskydd hindrar obehörig åtkomst.  
- **Kompatibilitet:** Efterlevnadsinställningar säkerställer att filen fungerar i olika Word‑versioner.  
- **Prestanda:** Justering av komprimering kan snabba upp sparandet eller minska filstorleken.  
- **Bevarande:** Att behålla äldre kontrolltecken bevarar noggrannheten vid konvertering av äldre dokument.

## Förutsättningar
- Aspose.Words för Java‑biblioteket har lagts till i ditt projekt (Maven/Gradle eller manuellt JAR).  
- Java 8 eller högre.  
- Ett källdokument (`.docx` eller `.doc`) som du vill bearbeta.

## Spara ett dokument med lösenordskryptering

Du kan kryptera ditt dokument med ett lösenord samtidigt som du sparar det i OOXML‑format. Så här gör du:

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

> **Proffstips:** Välj ett starkt lösenord och förvara det säkert; lösenordet kan inte återställas från den krypterade filen.

## Ställa in OOXML‑efterlevnad

Du kan ange OOXML‑efterlevnadsnivå när du sparar dokumentet. Till exempel kan du sätta den till ISO 29500:2008 (Strict). Så här gör du:

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

## Uppdatera egenskapen “Last Saved Time”

Du kan välja att uppdatera egenskapen “Last Saved Time” i dokumentet när du sparar det. Så här gör du:

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

Om ditt dokument innehåller äldre kontrolltecken kan du välja att behålla dem vid sparning. Så här gör du:

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

## Hur du ändrar komprimeringsnivå vid sparning av OOXML

Du kan justera komprimeringsnivån när du sparar dokumentet. Till exempel kan du sätta den till `SUPER_FAST` för minimal komprimering eller `MAXIMUM` för minsta möjliga filstorlek. Så här gör du:

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

Detta är några av de viktigaste alternativen och inställningarna du kan använda när du sparar dokument i OOXML‑format med Aspose.Words för Java. Utforska gärna fler alternativ och anpassa din dokument‑sparprocess efter behov.

## Komplett källkod för att spara dokument som OOXML‑format i Aspose.Words för Java

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

I den här omfattande guiden har vi gått igenom hur du **krypterar docx med lösenord** och sparar dokument i OOXML‑format med Aspose.Words för Java. Oavsett om du behöver skydda dina filer, säkerställa strikt OOXML‑efterlevnad, uppdatera dokumentegenskaper, bevara äldre kontrolltecken eller **ändra komprimeringsnivå**, så erbjuder Aspose.Words ett mångsidigt verktygspaket för att möta dina krav.

## Vanliga frågor

**Q: Hur tar jag bort lösenordsskyddet från ett lösenordsskyddat dokument?**  
A: Öppna dokumentet med rätt lösenord och spara sedan utan att ange ett lösenord i `OoxmlSaveOptions`. Detta skapar en oskyddad kopia.

**Q: Kan jag ange anpassade egenskaper när jag sparar ett dokument i OOXML‑format?**  
A: Ja. Använd `BuiltInDocumentProperties` och `CustomDocumentProperties` på `Document`‑objektet innan du anropar `save()`.

**Q: Vad är standardkomprimeringsnivån när ett dokument sparas i OOXML‑format?**  
A: Standard är `CompressionLevel.NORMAL`. Du kan byta till `SUPER_FAST` för hastighet eller `MAXIMUM` för minsta möjliga filstorlek.

**Q: Påverkar aktivering av `keepLegacyControlChars` kompatibiliteten med moderna Word‑versioner?**  
A: Moderna Word‑versioner kan öppna filer med äldre kontrolltecken, men vissa äldre funktioner kan visas annorlunda. Använd detta alternativ endast när du behöver bevara exakt originalinnehåll.

**Q: Är det möjligt att kombinera flera sparalternativ (t.ex. lösenord + komprimering) i ett enda anrop?**  
A: Absolut. Konfigurera alla önskade egenskaper på en enda `OoxmlSaveOptions`‑instans innan du skickar den till `doc.save()`.

---

**Senast uppdaterad:** 2026-0109  
**Testad med:** Aspose.Words för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
---
date: 2025-12-29
description: Leer hoe u docx-bestanden met een wachtwoord kunt versleutelen met behulp
  van de opslaanopties van Aspose.Words voor Java. Beveilig, optimaliseer en pas uw
  OOXML-bestanden moeiteloos aan.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Hoe een DOCX te versleutelen met een wachtwoord met Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een DOCX versleutelen met wachtwoord met Aspose.Words voor Java

In deze gids ontdek je **hoe je een docx versleutelt met een wachtwoord** tijdens het opslaan van documenten in OOXML‑formaat met Aspose.Words voor Java. Of je nu vertrouwelijke rapporten beschermt of conceptcontracten veilig stelt, de onderstaande stappen laten precies zien hoe je wachtwoordbeveiliging toepast en andere OOXML‑opslaan‑opties fijnstemt.

## Snelle antwoorden
- **Kan ik een DOCX‑bestand versleutelen met een wachtwoord?** Ja, gebruik `OoxmlSaveOptions.setPassword()` vóór het opslaan.  
- **Welke klasse regelt de OOXML‑opslaan‑instellingen?** `OoxmlSaveOptions` (onderdeel van Aspose.Words).  
- **Heb ik een licentie nodig voor wachtwoordbeveiliging?** Een geldige Aspose.Words‑licentie is vereist voor productiegebruik.  
- **Kan ik versleuteling combineren met compliance‑instellingen?** Absoluut – stel zowel `setPassword` als `setCompliance` in op dezelfde `OoxmlSaveOptions`‑instantie.  
- **Welke compressieniveaus zijn beschikbaar?** `NORMAL`, `SUPER_FAST` en `MAXIMUM` via `CompressionLevel`.

## Wat betekent “encrypt docx with password”?
Een DOCX‑bestand versleutelen betekent dat de inhoud van het bestand in versleutelde vorm wordt opgeslagen en alleen kan worden geopend na invoer van het juiste wachtwoord. Dit beschermt gevoelige informatie tegen ongeautoriseerde toegang, terwijl standaard Word‑tools het bestand nog steeds kunnen openen zodra het wachtwoord is opgegeven.

## Waarom Aspose.Words‑opslaan‑opties gebruiken voor versleuteling?
Aspose.Words biedt een uitgebreide set **aspose words save options** waarmee je niet alleen versleuteling, maar ook compliance‑niveaus, compressie en de behandeling van legacy‑tekens kunt regelen – allemaal vanuit Java‑code. Dit elimineert de noodzaak voor handmatige post‑processing of externe tools.

## Vereisten
- Java Development Kit (JDK 8 of hoger)  
- Aspose.Words voor Java‑bibliotheek toegevoegd aan je project (Maven/Gradle of JAR)  
- Een geldige Aspose.Words‑licentie voor productie (optioneel voor evaluatie)

## Een document opslaan met wachtwoordversleuteling

Je kunt je document versleutelen met een wachtwoord terwijl je het opslaat in OOXML‑formaat. Zo doe je dat:

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

## OOXML‑compliance instellen

Je kunt het OOXML‑compliance‑niveau specificeren bij het opslaan van het document. Bijvoorbeeld, je kunt het instellen op ISO 29500:2008 (Strict). Zo doe je dat:

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

## Eigenschap “Last Saved Time” bijwerken

Je kunt ervoor kiezen de eigenschap “Last Saved Time” van het document bij het opslaan bij te werken. Zo doe je dat:

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

## Legacy‑besturingstekens behouden

Als je document legacy‑besturingstekens bevat, kun je ervoor kiezen deze te behouden tijdens het opslaan. Zo doe je dat:

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

## Compressieniveau instellen

Je kunt het compressieniveau aanpassen bij het opslaan van het document. Bijvoorbeeld, je kunt **SUPER_FAST** kiezen voor minimale compressie. Zo doe je dat:

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

Dit zijn enkele van de belangrijkste opties en instellingen die je kunt gebruiken bij het opslaan van documenten in OOXML‑formaat met Aspose.Words voor Java. Voel je vrij om meer opties te verkennen en je document‑opslaan‑proces naar wens aan te passen.

## Complete broncode voor het opslaan van documenten als OOXML‑formaat in Aspose.Words voor Java

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

## Conclusie

In deze uitgebreide gids hebben we onderzocht hoe je **docx versleutelt met een wachtwoord** en een reeks OOXML‑opslaan‑opties fijnstelt met Aspose.Words voor Java. Of je nu vertrouwelijke inhoud moet beschermen, strikte ISO‑compliance moet behalen, legacy‑tekens wilt behouden of compressie wilt regelen, de bibliotheek biedt gedetailleerde controle via dezelfde `OoxmlSaveOptions`‑API.

## Veelgestelde vragen

**Q: Hoe verwijder ik wachtwoordbeveiliging van een wachtwoord‑beveiligd document?**  
A: Open het document met het juiste wachtwoord en sla het vervolgens opnieuw op zonder `setPassword` aan te roepen. Het nieuwe bestand is onbeveiligd.

**Q: Kan ik aangepaste eigenschappen instellen bij het opslaan van een document in OOXML‑formaat?**  
A: Ja. Gebruik `BuiltInDocumentProperties` of `CustomDocumentProperties` op het `Document`‑object voordat je `save` aanroept.

**Q: Wat is het standaard compressieniveau bij het opslaan van een document in OOXML‑formaat?**  
A: Standaard is `NORMAL`. Je kunt overschakelen naar `SUPER_FAST` voor snelheid of `MAXIMUM` voor een kleinere bestandsgrootte.

**Q: Werken de aspose words save options met oudere Word‑versies?**  
A: Ja. Door `MsWordVersion` en compliance‑instellingen aan te passen, kun je richten op Word 2007‑2019 en compatibiliteit waarborgen.

**Q: Is het mogelijk meerdere opslaan‑opties te combineren in één bewerking?**  
A: Absoluut. Maak één `OoxmlSaveOptions`‑instantie, stel alle gewenste eigenschappen in (wachtwoord, compliance, compressie, enz.) en geef deze door aan `doc.save()`.

---

**Laatst bijgewerkt:** 2025-12-29  
**Getest met:** Aspose.Words voor Java 24.12  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
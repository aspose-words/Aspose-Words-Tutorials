---
date: 2026-01-09
description: Leer hoe u docx-bestanden kunt versleutelen met een wachtwoord en het
  compressieniveau kunt wijzigen bij het opslaan van documenten in OOXML-indeling
  met Aspose.Words voor Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Docx versleutelen met wachtwoord – OOXML opslaan met Aspose.Words Java
url: /nl/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Docx versleutelen met wachtwoord – OOXML opslaan met Aspose.Words Java

## Introductie tot het opslaan van documenten als OOXML-formaat in Aspose.Words voor Java

In deze gids leer je hoe je **docx versleutelt met wachtwoord** en documenten opslaat in OOXML-formaat met Aspose.Words voor Java. OOXML (Office Open XML) is het moderne bestandsformaat dat wordt gebruikt door Microsoft Word en vele andere kantoorapplicaties. We lopen de meest voorkomende opties door—wachtwoordbeveiliging, compliance-niveaus, eigenschapsupdates, handling van legacy-tekens, en **hoe je compressieniveau wijzigt**—zodat je de output kunt afstemmen op je exacte behoeften.

## Quick Answers
- **Hoe kan ik een Word‑bestand beveiligen?** Gebruik `OoxmlSaveOptions.setPassword("yourPassword")` vóór het opslaan.  
- **Welk OOXML‑compliance‑niveau moet ik kiezen?** ISO 29500 2008 Strict voor maximale compatibiliteit met moderne Office‑versies.  
- **Kan ik legacy‑control‑karakters behouden?** Ja, schakel `setKeepLegacyControlChars(true)` in.  
- **Hoe wijzig ik het compressieniveau?** Stel `setCompressionLevel(CompressionLevel.SUPER_FAST)` of `MAXIMUM` in, afhankelijk van de behoefte.  
- **Hebben deze opties invloed op de bestandsgrootte?** Het compressieniveau en de handling van legacy‑karakters kunnen de uiteindelijke .docx‑grootte merkbaar veranderen.

## Wat betekent “docx versleutelen met wachtwoord”?
Een DOCX‑bestand versleutelen betekent dat het document wordt opgeslagen met AES‑256‑versleuteling, waardoor een wachtwoord nodig is om het te openen in Word of een compatibele viewer. Dit is essentieel voor het beschermen van vertrouwelijke informatie wanneer bestanden worden gedeeld via e‑mail, cloudopslag of intranetportalen.

## Waarom OOXML‑opslaoptopties gebruiken?
- **Beveiliging:** Wachtwoordbeveiliging voorkomt ongeautoriseerde toegang.  
- **Compatibiliteit:** Compliance‑instellingen zorgen ervoor dat het bestand werkt in verschillende Word‑versies.  
- **Prestaties:** Het aanpassen van compressie kan het opslaan versnellen of de bestandsgrootte verkleinen.  
- **Behoud:** Legacy‑control‑karakters behouden behoudt de getrouwheid bij het converteren van oudere documenten.

## Vereisten
- Aspose.Words voor Java‑bibliotheek toegevoegd aan je project (Maven/Gradle of handmatige JAR).  
- Java 8 of hoger.  
- Een bron‑document (`.docx` of `.doc`) dat je wilt verwerken.

## Een document opslaan met wachtwoordversleuteling

Je kunt je document versleutelen met een wachtwoord tijdens het opslaan in OOXML‑formaat. Zo doe je dat:

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

> **Pro tip:** Kies een sterk wachtwoord en bewaar het veilig; het wachtwoord kan niet worden hersteld uit het versleutelde bestand.

## OOXML‑compliance instellen

Je kunt het OOXML‑compliance‑niveau opgeven bij het opslaan van het document. Bijvoorbeeld, je kunt het instellen op ISO 29500:2008 (Strict). Zo doe je dat:

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

Je kunt ervoor kiezen om de eigenschap "Last Saved Time" van het document bij het opslaan bij te werken. Zo doe je dat:

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

## Legacy‑control‑karakters behouden

Als je document legacy‑control‑karakters bevat, kun je ervoor kiezen ze te behouden bij het opslaan. Zo doe je dat:

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

## Hoe het compressieniveau wijzigen bij het opslaan van OOXML

Je kunt het compressieniveau aanpassen bij het opslaan van het document. Bijvoorbeeld, je kunt `SUPER_FAST` instellen voor minimale compressie of `MAXIMUM` voor de kleinste bestandsgrootte. Zo doe je dat:

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

Dit zijn enkele van de belangrijkste opties en instellingen die je kunt gebruiken bij het opslaan van documenten in OOXML‑formaat met Aspose.Words voor Java. Voel je vrij om meer opties te verkennen en je document‑opslaapproces naar behoefte aan te passen.

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

In deze uitgebreide gids hebben we onderzocht hoe je **docx versleutelt met wachtwoord** en documenten opslaat in OOXML‑formaat met Aspose.Words voor Java. Of je nu je bestanden wilt beschermen, strikte OOXML‑compliance wilt garanderen, documenteigenschappen wilt bijwerken, legacy‑control‑karakters wilt behouden, of **compressieniveau wilt wijzigen**, Aspose.Words biedt een veelzijdige set tools om aan je eisen te voldoen.

## Veelgestelde vragen

**Q: Hoe verwijder ik wachtwoordbeveiliging van een wachtwoord‑beveiligd document?**  
A: Open het document met het juiste wachtwoord en sla het vervolgens op zonder een wachtwoord op te geven in `OoxmlSaveOptions`. Dit maakt een onbeveiligde kopie.

**Q: Kan ik aangepaste eigenschappen instellen bij het opslaan van een document in OOXML‑formaat?**  
A: Ja. Gebruik `BuiltInDocumentProperties` en `CustomDocumentProperties` op het `Document`‑object voordat je `save()` aanroept.

**Q: Wat is het standaard compressieniveau bij het opslaan van een document in OOXML‑formaat?**  
A: Standaard is `CompressionLevel.NORMAL`. Je kunt overschakelen naar `SUPER_FAST` voor snelheid of `MAXIMUM` voor de kleinste bestandsgrootte.

**Q: Heeft het inschakelen van `keepLegacyControlChars` invloed op de compatibiliteit met moderne Word‑versies?**  
A: Moderne Word kan bestanden met legacy‑control‑karakters openen, maar sommige oudere functies kunnen anders worden weergegeven. Gebruik deze optie alleen wanneer je de exacte oorspronkelijke inhoud moet behouden.

**Q: Is het mogelijk om meerdere opslaoptopties te combineren (bijv. wachtwoord + compressie) in één aanroep?**  
A: Absoluut. Configureer alle gewenste eigenschappen op één `OoxmlSaveOptions`‑instantie voordat je deze doorgeeft aan `doc.save()`.

---

**Laatst bijgewerkt:** 2026-01-09  
**Getest met:** Aspose.Words for Java 24.12  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
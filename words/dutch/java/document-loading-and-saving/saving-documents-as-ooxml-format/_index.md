---
title: Documenten opslaan als OOXML-indeling in Aspose.Words voor Java
linktitle: Documenten opslaan als OOXML-indeling
second_title: Aspose.Words Java Documentverwerkings-API
description: Leer hoe u documenten in OOXML-formaat opslaat met Aspose.Words voor Java. Beveilig, optimaliseer en personaliseer uw bestanden moeiteloos.
weight: 20
url: /nl/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Documenten opslaan als OOXML-indeling in Aspose.Words voor Java


## Inleiding tot het opslaan van documenten als OOXML-indeling in Aspose.Words voor Java

In deze gids gaan we onderzoeken hoe u documenten in OOXML-formaat kunt opslaan met Aspose.Words voor Java. OOXML (Office Open XML) is een bestandsformaat dat wordt gebruikt door Microsoft Word en andere Office-applicaties. We bespreken verschillende opties en instellingen voor het opslaan van documenten in OOXML-formaat.

## Vereisten

Voordat we beginnen, moet u ervoor zorgen dat u de Aspose.Words voor Java-bibliotheek in uw project hebt ingesteld.

## Een document opslaan met wachtwoordversleuteling

kunt uw document versleutelen met een wachtwoord terwijl u het opslaat in OOXML-formaat. Dit is hoe u dat kunt doen:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Laad het document
Document doc = new Document("Document.docx");

// Maak OoxmlSaveOptions en stel het wachtwoord in
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Bewaar het document met encryptie
doc.save("EncryptedDoc.docx", saveOptions);
```

## OOXML-naleving instellen

U kunt het OOXML-nalevingsniveau opgeven bij het opslaan van het document. U kunt het bijvoorbeeld instellen op ISO 29500:2008 (Strikt). Dit doet u als volgt:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Laad het document
Document doc = new Document("Document.docx");

// Optimaliseren voor Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Maak OoxmlSaveOptions en stel het nalevingsniveau in
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Sla het document op met de nalevingsinstelling
doc.save("ComplianceDoc.docx", saveOptions);
```

## Laatst opgeslagen tijdeigenschap bijwerken

U kunt ervoor kiezen om de eigenschap "Last Saved Time" van het document bij te werken wanneer u het opslaat. Dit doet u als volgt:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Laad het document
Document doc = new Document("Document.docx");

// Maak OoxmlSaveOptions en schakel het bijwerken van de eigenschap Laatst opgeslagen tijd in
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Sla het document op met de bijgewerkte eigenschap
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Legacy Control-personages behouden

Als uw document legacy control-tekens bevat, kunt u ervoor kiezen deze te behouden tijdens het opslaan. Dit doet u als volgt:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Een document laden met oude besturingstekens
Document doc = new Document("LegacyControlChars.doc");

// Maak OoxmlSaveOptions met de FLAT_OPC-indeling en schakel het behoud van oude besturingstekens in
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Sla het document op met oude besturingstekens
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Compressieniveau instellen

U kunt het compressieniveau aanpassen wanneer u het document opslaat. U kunt het bijvoorbeeld instellen op SUPER_FAST voor minimale compressie. Dit doet u als volgt:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Laad het document
Document doc = new Document("Document.docx");

// Maak OoxmlSaveOptions en stel het compressieniveau in
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Sla het document op met het opgegeven compressieniveau
doc.save("FastCompressionDoc.docx", saveOptions);
```

Dit zijn enkele van de belangrijkste opties en instellingen die u kunt gebruiken bij het opslaan van documenten in OOXML-formaat met Aspose.Words voor Java. U kunt gerust meer opties verkennen en uw documentopslagproces naar wens aanpassen.

## Volledige broncode voor het opslaan van documenten als OOXML-indeling in Aspose.Words voor Java

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

In deze uitgebreide gids hebben we onderzocht hoe u documenten in OOXML-formaat kunt opslaan met Aspose.Words voor Java. Of u nu uw documenten wilt versleutelen met wachtwoorden, naleving van specifieke OOXML-standaarden wilt garanderen, documenteigenschappen wilt bijwerken, oude controletekens wilt behouden of compressieniveaus wilt aanpassen, Aspose.Words biedt een veelzijdige set tools om aan uw vereisten te voldoen.

## Veelgestelde vragen

### Hoe verwijder ik de wachtwoordbeveiliging van een met een wachtwoord beveiligd document?

Om de wachtwoordbeveiliging van een wachtwoordbeveiligd document te verwijderen, kunt u het document openen met het juiste wachtwoord en het vervolgens opslaan zonder een wachtwoord op te geven in de opslagopties. Hiermee wordt het document opgeslagen zonder wachtwoordbeveiliging.

### Kan ik aangepaste eigenschappen instellen bij het opslaan van een document in OOXML-indeling?

 Ja, u kunt aangepaste eigenschappen voor een document instellen voordat u het opslaat in OOXML-indeling. Gebruik de`BuiltInDocumentProperties` En`CustomDocumentProperties` klassen om verschillende eigenschappen in te stellen, zoals auteur, titel, trefwoorden en aangepaste eigenschappen.

### Wat is het standaardcompressieniveau bij het opslaan van een document in OOXML-formaat?

 Het standaardcompressieniveau bij het opslaan van een document in OOXML-formaat met behulp van Aspose.Words voor Java is`NORMAL` . U kunt het compressieniveau wijzigen naar`SUPER_FAST` of`MAXIMUM` indien nodig.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
